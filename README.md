# Data Projekt Wassterstein GAN-WP
Dette GitHub-repository er beregnet til brug i forbindelse med Data Projekteksamen på Aarhus Universitet. I denne readme vil vi kort beskrive projektet. 

I løbet af projektet har vi stødt på mange forskellige udfordringer. I starten af projektet skulle vi sætte os ind i den teoretiske matematik bag GAN og derefter i varianten Wasserstein GAN med Gradient Penalty, også kendt som WGAN-GP. Samtidig med at vi satte os ind i WGAN-GP, udførte vi også datarengøring af billederne. De billeder, vi fik tildelt af vores vejleder, Ruben Pauwels, havde en masse fejl, som også kort er beskrevet i projektbeskrivelsen.


Efter vi gik igennem teorien og data rengøringen, begyndte vi at implementere koden fra artiklen: “Improved Training of Wasserstein GANs” af Ishaan Gulrajani, Faruk Ahmed, Martin Arjovsky, Vincent Dumoulin, og Aaron Courville. ArXiv 2017”. Vi brugte hjælpe funktionen Gradient Penalty fra: https://github.com/aladdinpersson/Machine-Learning-Collection/tree/master/ML/Pytorch/GANs/4.%20WGAN-GP.
Heraf lavede vi forskellige generatorer og kritikere, hvilket skyldtes, at vores vejleder, Ruben, ønskede billeder i nogenlunde samme format som de oprindelige. Derfor forsøgte vi at lave et netværk, der kunne producere billeder i 16:9-aspektforhold, men dette mislykkedes, da vi brugte nogle kernels, der gjorde billederne slørede. Efterfølgende trænede vi to forskellige kvadratiske WGAN-GP'er; i det ene tilfælde tog vi de originale billeder og gjorde dem kvadratiske. Vi trænede på dette, men vores vejleder var ikke tilfreds med resultatet, da billederne blev sammenpressede og så “underlige” ud. En stor udfordring ved disse GAN'er er antallet af features, vi kan give vores model på grund af compute-begrænsninger og billeddetaljernes kompleksitet. Derfor anbefalede vores vejleder, at vi lavede et datasæt, der kun indeholdt billeder af tænderne, og derfra lavede et netværk, der kun genererede denne slags billeder. Håbet var, at kvaliteten ville stige, når GAN'en fokuserede på et mindre område, dog virkede det til, at det velkendte problem ved GAN’en opstod og vores generator stagnerede. 

Til dette projekt brugte vi Google Colab Pro+ som compute. Her kunne vi leje en A100 med 40 GB RAM. Dette er et stort grafikkort, men vi blev stadig begrænset af RAM'en, da antallet af features kun var 128, hvilket ideelt set burde have været dobbelt så stort. 

Projektet mundede ud i, at denne type netværk ikke er tilstrækkelig til at producere syntetiske billeder, der ligner ægte billeder. Herfra kan tandlægeinstituttet selv bygge videre på forskellige arkitekturer. Alt i alt vil vi beskrive denne “non-finding” som en succes.

![512x512](https://github.com/ViktorLaden/DataProjectGAN/assets/159600496/38955210-a57a-4795-ac55-c174ab01a347)


![image_67](https://github.com/ViktorLaden/DataProjectGAN/assets/159600496/ec8afdf6-3215-47f2-b609-8ca2f3a26cf3)
![image_50](https://github.com/ViktorLaden/DataProjectGAN/assets/159600496/4bdf2d86-55c0-41b8-a1a9-431d2c55bc78)
