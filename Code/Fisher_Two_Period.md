# The Fisher Two-Period Optimal Consumption Problem

This model analyzes the optimization problem of a consumer who faces **no uncertainty** and lives for two periods.

```R

# Define parameters 

ui <- fluidPage(
  sliderInput("R", "Return Factor 'R'", min = 1, max = 10, value = 1),
  sliderInput("B", "Time Preference Factor 'B'", min = 0, max = 1, value = 0.5),
  sliderInput("p", "Risk Aversion Factor 'p'", min = 1, max = 30, value = 1),
  plotOutput("fisher_plot")
)

# Define the server

server <- function(input, output) {
  output$fisher_plot <- renderPlot({
  R <- input$R
  B <- input$B
  p <- input$p
  C_1 <- seq(0, 100, by = 5)
  C_2 <- ((R * B)^(1/p)) * C_1
  plot(C_1, C_2, type = "l", xlab = "Period 1 consumption", ylab = "Period 2 consumption", main = "Fisher 2-period Model")
  })
}

shinyApp(ui, server)
```
