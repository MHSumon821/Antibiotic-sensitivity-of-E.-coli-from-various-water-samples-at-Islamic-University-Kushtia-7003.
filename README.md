# Antibiotic-sensitivity-of-E.-coli-from-various-water-samples-at-Islamic-University-Kushtia-7003.
"Bacteriological Quality of Various Water Sources at Islamic University, Kushtia, Bangladesh" In this title project, we analyze the antimicrobial susceptibility test of the indicator organism, E. coli.
library(ggplot2)
# Sample data
data <- data.frame(
category = c("Ampicillin AMP(10µg)", "Chloramphenicol CHL(30µg)", "Ciprofloxacin CIP(5µg)", "Co-trimoxazole COT(25µg)", "Erythromycin E(15µg)", "Gentamicin GEN(10µg)", "Nalidixic Acid NAL(10µg)", "Penicillin PEN(10µg)", "Rifampicin RIF(5µg)", "Tetracycline TE(30µg)"),
segment1 = c(10, 15, 10, 10, 85, 5, 5, 35, 15, 60),
segment2 = c(40, 15, 20, 5, 15, 5, 10, 50, 20, 5),
segment3 = c(50, 70, 70, 85, 0, 90, 85, 15, 65, 35)
)
# Reshape data
library(tidyr)
data_long <- gather(data, key = "segment", value = "Antibiotics_profiling_pattern", -category)
# Convert category to factor
data_long$category <- factor(data_long$category, levels = rev(unique(data$category)))
# Create a horizontal stacked bar chart
ggplot(data_long, aes(x = Antibiotics_profiling_pattern, y = category, fill = segment)) +
geom_bar(stat = "identity") +
geom_text(aes(label = Antibiotics_profiling_pattern), position = position_stack(vjust = 0.5)) +
labs(title = "Comparison of antibiotics and their resistant pattern to E. coli",
x = "Antibiotics profiling pattern",
y = "Treated Antibiotics") +
scale_x_continuous(limits = c(0, 100)) +  # Set x-axis limits from 0 to 100
scale_fill_manual(values = c("red", "lightblue", "green"),
labels = c("Resistance", "Intermediate", "Susceptible")) + # Set legend labels
theme_minimal()
