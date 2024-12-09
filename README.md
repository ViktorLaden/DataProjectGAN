# Data Projekt Wassterstein GAN-WP
Dette GitHub-repository er beregnet til brug i forbindelse med Data Projekteksamen på Aarhus Universitet. I denne readme vil vi kort beskrive projektet. 

I løbet af projektet har vi stødt på mange forskellige udfordringer. I starten af projektet skulle vi sætte os ind i den teoretiske matematik bag GAN og derefter i varianten Wasserstein GAN med Gradient Penalty, også kendt som WGAN-GP. Samtidig med at vi satte os ind i WGAN-GP, udførte vi også datarengøring af billederne. De billeder, vi fik tildelt af vores vejleder, Ruben Pauwels, havde en masse fejl, som også kort er beskrevet i projektbeskrivelsen.


Efter vi gik igennem teorien og data rengøringen, begyndte vi at implementere koden fra artiklen: “Improved Training of Wasserstein GANs” af Ishaan Gulrajani, Faruk Ahmed, Martin Arjovsky, Vincent Dumoulin, og Aaron Courville. ArXiv 2017”. Vi brugte hjælpe funktionen Gradient Penalty fra: https://github.com/aladdinpersson/Machine-Learning-Collection/tree/master/ML/Pytorch/GANs/4.%20WGAN-GP.
Heraf lavede vi forskellige generatorer og kritikere, hvilket skyldtes, at vores vejleder, Ruben, ønskede billeder i nogenlunde samme format som de oprindelige. Derfor forsøgte vi at lave et netværk, der kunne producere billeder i 16:9-aspektforhold, men dette mislykkedes, da vi brugte nogle kernels, der gjorde billederne slørede. Efterfølgende trænede vi to forskellige kvadratiske WGAN-GP'er; i det ene tilfælde tog vi de originale billeder og gjorde dem kvadratiske. Vi trænede på dette, men vores vejleder var ikke tilfreds med resultatet, da billederne blev sammenpressede og så “underlige” ud. En stor udfordring ved disse GAN'er er antallet af features, vi kan give vores model på grund af compute-begrænsninger og billeddetaljernes kompleksitet. Derfor anbefalede vores vejleder, at vi lavede et datasæt, der kun indeholdt billeder af tænderne, og derfra lavede et netværk, der kun genererede denne slags billeder. Håbet var, at kvaliteten ville stige, når GAN'en fokuserede på et mindre område, dog virkede det til, at det velkendte problem ved GAN’en opstod og vores generator stagnerede. 

Til dette projekt brugte vi Google Colab Pro+ som compute. Her kunne vi leje en A100 med 40 GB RAM. Dette er et stort grafikkort, men vi blev stadig begrænset af RAM'en, da antallet af features kun var 128, hvilket ideelt set burde have været dobbelt så stort. 

Projektet mundede ud i, at denne type netværk ikke er tilstrækkelig til at producere syntetiske billeder, der ligner ægte billeder. Herfra kan tandlægeinstituttet selv bygge videre på forskellige arkitekturer. Alt i alt vil vi beskrive denne “non-finding” som en succes.

## Results

### Generated Images

<div style="display: flex; justify-content: space-around; flex-wrap: wrap;">
  <div style="flex: 1; text-align: center; margin: 10px;">
    <img src="https://github.com/ViktorLaden/DataProjectGAN/assets/159600496/3cac0192-a8f3-42c3-a05f-28576d262b13" alt="Generated Image 1" width="300"/>
    <p>Figure 1: 512x512.</p>
  </div>
  <div style="flex: 1; text-align: center; margin: 10px;">
    <img src="https://github.com/ViktorLaden/DataProjectGAN/assets/159600496/ec8afdf6-3215-47f2-b609-8ca2f3a26cf3" alt="Generated Image 2" width="300"/>
    <p>Figure 2: 256x256.</p>
  </div>
  <div style="flex: 1; text-align: center; margin: 10px;">
    <img src="https://github.com/ViktorLaden/DataProjectGAN/assets/159600496/4bdf2d86-55c0-41b8-a1a9-431d2c55bc78" alt="Generated Image 3" width="300"/>
    <p>Figure 3: 508x287.</p>
  </div>
</div>






You can also visit following notebooks with corresponding data to reproduce the FID and t-SNE plots

FID Calculation: https://colab.research.google.com/drive/1vKUsFsdvzoa8S9Dp92_OHcuxvrlk3RCT?usp=sharing

t-SNE Plot: https://colab.research.google.com/drive/1UkKak_UiXC8s0FehuyONaPVDXjDZmskP?usp=sharing

SSIM (for exploration, not published): https://colab.research.google.com/drive/1V64iW8adqYuVohk41JnMNRGj-EATegHL?usp=sharing

Dataset we release:

- High Res images (2322) - 1024x1024 - https://drive.google.com/drive/folders/1bj5iFoxGcWjnaSgPf82Hz1ifFIUYEjvL?usp=drive_link

- Low Res images (2322) - 256x256 - https://drive.google.com/drive/folders/1Jaz67VPr-xqVLI3RQuzPKO-1c8I6g8Pq?usp=drive_link

- Observations Generated Images (100) - 256x256 - https://drive.google.com/drive/folders/1ne5NbYbfbwigaKF_yj83_L2W5TbJaM-q?usp=drive_link
