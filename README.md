# LTER_MicrobialNComp
This project organizes data files and code associated with a study evaluating the effect of soil C concentration in the relationship between net N mineralization and net nitrification across terrestrial Long Term Ecological Research (LTER) sites in North America. Data were aggregated from publically-available LTER databases. Replicated-averaged data and code to replicate figures and analyses in Gill et al. 2022. Soil carbon availability decouples net nitrogen mineralization and net nitrification across United States Long Term Ecological Research Site. *Biogeochemistry*.

## Methods associated with data assimilation and analysis
###*Database assembly*:
We searched public databases associated with all terrestrial North American LTER sites for datasets reporting soil net N mineralization (ug N g dry soil-1 day-1), soil net nitrification (ug N g dry soil-1 day-1), and total soil C concentration (% soil C). Mineralization and nitrification rates were measured using both laboratory incubations (56% of samples) and field-buried bag and core approaches (44% of samples). We targeted net N fluxes rather than gross N transformations because they are widely measured and thus allowed for the development of a dataset encompassing diverse soil types and ecosystems. Our dataset included: site latitude and longitude, mean annual temperature (MAT), mean annual precipitation (MAP), altitude, soil type, pH, and total soil N content, where available.  We used 30-year (1991-2020) average monthly air temperature data (Arguez et al. 2021) to calculate annual site potential evapotranspiration (PET) using the Thornthwaite model (Thornthwaite 1948) and expressed site water balance as MAP-PET (mm year-1). Data were transformed to common units (ug N g dry soil-1 day-1) and percent soil C. 
###*Statistical analyses*:
For plots containing soil cores taken over time or multiple sub-plot collections, we calculated a plot-level mean of the N mineralization rates, nitrification rates, and soil C concentrations since these cores were not statistically independent (2672 independent observations in final dataset of 19,271 total observations). We used mixed effects models to evaluate the relationship between soil C concentration (% soil C) and site meteorology (single main effect of MAT, MAP, or water balance; random effect = study). Soil C concentration was log-transformed to approximate normality. Soil pH was not regularly reported with the N cycling data, so it is not considered broadly in the analysis.
We used model selection to identify the combination of predictors that best explained variation in nitrification rates. We fit a global mixed-effects model relating net nitrification rate to a potential set of predictor variables including net N mineralization rate, soil C concentration (log-transformed), site MAT, site water balance (MAP-PET), and all two-way interactions with N mineralization (N mineralization*Soil C concentration; N mineralization*MAT; N mineralization*water balance) using the nlme R package (Pinhiero et al. 2019). MAP was excluded from the model selection due to strong correlation with site water balance (Pearson correlation = 0.86; Table S2). All remaining main effects maintained a variance inflation factor < 1.6 (car R package; Fox & Weisberg 2019) and thus were retained within the global model.  Predictors were centered and scaled by their mean and standard deviations, respectively (scale function in R). From each LTER site, data were derived from multiple studies run by separate investigators often with different models. Therefore, individual study was included as a random effect. We used the ‘dredge’ function to generate a full set of sub-models containing all combinations of main effects and interactions (MuMln R package; Nakagawa & Schielzeth 2013).
To separately compare the effect of MAT, MAP, and soil C concentration on the relationship between net N mineralization and nitrification, we fit three separate mixed effects models associating net nitrification rates to either 1) N mineralization*soil C concentration; 2) N mineralization*MAT; 3) N mineralization*water balance [MAP-PET] (R package nlme; Pinheiro et al. 2017). Soil C concentration was log-transformed to approximate normality, and variables were centered and scaled as described above. Individual study was included as a random effect. The three models allowed us to examine the strength of the individual and interactive effects on net nitrification. 
