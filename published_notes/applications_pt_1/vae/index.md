---
layout: post
title: Variational Autoencoders
date: 2020-02-19 21:46:04
categories: jekyll css
---

Let's start off assuming we have a decoder; a reconstruction model in the form $P(x|z)$. We then have,

$$
\begin{equation}
    P(x|z) = \frac{P(z|x)P(x)}{P(z)}
\end{equation}
$$

$$
\begin{align}
    P(z|x) 
        &= \frac{P(x|z)P(z)}{P(x)} \\
        &= \frac{P(x|z)P(z)}{\int P(x|z)P(z) dz} 
\end{align}
$$

$$
\begin{align}
    P(z|x) 
        &= \frac{P(x,z)}{P(x)} \\
        &= \frac{P(x,z)}{\int P(x,z) dz}
\end{align}
$$

For the encoder, $$P(z|x)$$, we already have a problem - the denominator term $$P(x)= \frac{P(x|z)P(z)}{\int P(x|z)P(z) dz}$$ can be intractible due to having to be integrated over every variable of z as $$\int_{d_n} \dots \int_{dz1} P(x|z)P(z) dz1 \dots dz_n$$. We can instead look towards approximating $$P(z|x)$$ using  *variational inference*.

As noted previously, variational inference entails approximating $$P(z|x)$$ with a family of functions $$Q(z|x)$$. To measure the similarity between $$P(z|x)$$ and $$Q(z|x)$$, we can use the Kullback-Leibler Divergence (KL Divergence) as follows,

$$
\begin{align}
    KL \big [ Q(z|x)||P(z|x) \big ] 
        &= \sum Q(z|x) \frac{P(z|x)}{Q(z|x)} \\
        &= \sum Q(z|x) \log \frac{\frac{P(x,z)}{P(x)}}{Q(z|x)} \\
        &= \sum Q(z|x) \log \frac{P(x,z)}{Q(z|x) \log P(x)}   \\
        &= \sum Q(z|x) \bigg [ \log \frac{P(x,z)}{Q(z|x)} - \log P(x) \bigg ] \\
        &= \sum Q(z|x) \log \frac{P(x,z)}{Q(z|x)} - \log P(x)
\end{align}
$$


Rearraging this equation, we have the following,

$$
\begin{align}
    \log P(x)  
        &= \sum Q(z|x) \log \frac{P(x,z)}{Q(z|x)} - KL \big [ Q(z|x)||P(z|x) \big ] \\
        & = \text{ELBO} - KL \big [ Q(z|x)||P(z|x) \big ]
\end{align}
$$

Here, the left side of the equation, $$\log P(x)$$, is constant. On the right side of the equation, changing either one of the terms will cause the other to change as well. Furthermore, $$KL \big [ Q(z|x)||P(z|x) \big ] \geq 0$$, and so maximizing the first term $$\sum Q(z|x) \log \frac{P(x,z)}{Q(z|x)}$$ will cause the second KL Divergence term to minimize close to 0; we wanted to minimize the KL Divergence as close to zero anyway. Hence, we don't have to worry about the second KL Divergence term at all; it's intractable anyway. We call this first term that we actually minimize, the Evidence Lower BOund (ELBO) and can be futher manipulated as follows,

$$
\begin{align}
    \text{ELBO}
        &= \sum Q(z|x) \log \frac{P(x,z)}{Q(z|x)} \\
        &= \sum Q(z|x) \log \frac{P(x|z)P(z)}{Q(z|x)} \\
        &= \sum Q(z|x) \log P(x|z) + \sum Q(z|x) \log \frac{P(z)}{Q(z|x)} \\
        &= \mathbf{E}_{Q(z|x)}[\log P(x|z)] - KL[Q(z|x)||P(z)] \\
        &= \text{Reconstruction}(x,\hat{x}) - KL[Q(z|x)||P(z) \sim N(\mu, \Sigma) ]
\end{align}
$$

Here, $$\Sigma$ is diagonal because we are assuming Mean Field Inference, where $Q(z|x) = \prod_i Q(z_i|x)$

$$
\begin{align}
    \text{ELBO}
        &= \sum Q(z|x) \log P(x|z) + \sum Q(z|x) \log \frac{P(z)}{Q(z|x)} \\
        &= \mathbf{E}_{z \sim Q(z|x)}[\log P(x|z)] - KL[Q(z|x)||P(z)] \\
        &= \text{Reconstruction}(x,\hat{x}) - KL[Q(z|x)||P(z) \sim N(\mu, \Sigma) ]
\end{align}
$$



From the perspective of a model, we want to draw latent variables from a distribution $$P(z)$$, then reconstruct x by way of $$P(x|z)$$. This gives us the decoder model  $$P(x,z)=P(x|z)P(z)$$



[1] Jaan Altosaar. VAE. [Blog](https://jaan.io/what-is-variational-autoencoder-vae-tutorial/) \\
[2] Jeremy Jordan. VAE. [Blog](https://www.jeremyjordan.me/variational-autoencoders/)

<br/>

|[Index](../../../) |
