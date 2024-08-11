# Model Card

See the [example Google model cards](https://modelcards.withgoogle.com/model-reports) for inspiration. 

## Model Description

**Input:**

### Features and Target Description

- **year**
  - **Type**: Numerical
  - **Description**: The year in which the event occurred. This feature could capture temporal trends or changes over years.

- **month_sin**
  - **Type**: Numerical (Sine transformed)
  - **Description**: The sine of the month. This is a cyclical feature representing the position of the month within the year, transformed to reflect periodicity.

- **month_cos**
  - **Type**: Numerical (Cosine transformed)
  - **Description**: The cosine of the month. Similar to `month_sin`, this represents the cyclical nature of the month.

- **day_sin**
  - **Type**: Numerical (Sine transformed)
  - **Description**: The sine of the day of the month. This feature captures the cyclical nature of the days within a month.

- **day_cos**
  - **Type**: Numerical (Cosine transformed)
  - **Description**: The cosine of the day of the month. This complements `day_sin` to reflect the periodicity of days.

- **hour_sin**
  - **Type**: Numerical (Sine transformed)
  - **Description**: The sine of the hour of the day. Represents the cyclical pattern of hours in a day.

- **hour_cos**
  - **Type**: Numerical (Cosine transformed)
  - **Description**: The cosine of the hour of the day. Complements `hour_sin` to capture the periodicity of hours.

- **minute_sin**
  - **Type**: Numerical (Sine transformed)
  - **Description**: The sine of the minute of the hour. Reflects the cyclical nature of minutes within an hour.

- **minute_cos**
  - **Type**: Numerical (Cosine transformed)
  - **Description**: The cosine of the minute of the hour. Complements `minute_sin` for capturing periodicity.

- **weekday_sin**
  - **Type**: Numerical (Sine transformed)
  - **Description**: The sine of the weekday. This feature captures the cyclical pattern of weekdays in a week.

- **weekday_cos**
  - **Type**: Numerical (Cosine transformed)
  - **Description**: The cosine of the weekday. Complements `weekday_sin` to reflect the periodic nature of weekdays.

- **latitude**
  - **Type**: Numerical
  - **Description**: The geographical latitude where the event occurred. Represents the north-south position on the Earth's surface.

- **longitude**
  - **Type**: Numerical
  - **Description**: The geographical longitude where the event occurred. Represents the east-west position on the Earth's surface.

- **depth**
  - **Type**: Numerical
  - **Description**: The depth at which the event occurred, typically measured in kilometers. This feature is relevant for geological or seismic events.


**Output:** Describe the output(s) of your model

### Target (Label)

- **magnitude**
  - **Type**: Numerical
  - **Description**: The magnitude of the event. This is the target variable the Random Forest model aims to predict based on the input features.

**Model Architecture:** The earthquake prediction model is based on the __Random Forest Regressor__ and is configured with __300 trees__ and __no maximum depth__ constraint, allowing each tree to fully learn from the data. This architecture aims to achieve a robust prediction by using multiple decision trees, each trained on different subsets of the data and features, and averaging their predictions to provide the final output. Also, it's ensemble nature makes it less prone to overfitting.

## Performance

Give a summary graph or metrics of how the model performs. Remember to include how you are measuring the performance and what data you analysed it on. 

The metrics suggest that the Random Forest model performs reasonably well in predicting earthquake magnitudes, with relatively low error values.

* __Mean Squared Error on Test Set__: 0.31840750547315205
* __Root Mean Squared Error on Test Set__: 0.5642760897585083
* __Mean Absolute Error on Test Set__: 0.43429063805436335

MSE (0.3184) and RMSE (0.5643) show that the model’s predictions are reasonably close to the actual values, with errors being fairly small on average. However, RMSE is often preferred because it’s in the same unit as the target variable. MAE (0.4343) also indicates that the average error is relatively small, providing a clear view of the average magnitude of errors without squaring them.

## Limitations

*__Feature Dependence__: The model relies on cyclical features (e.g., sine and cosine transformations) to capture temporal patterns. If these transformations do not adequately reflect the underlying patterns of earthquake magnitudes, the model’s performance could be compromised.

*__Geographical Variability__: While latitude and longitude are included as features, the model may not fully account for regional variations or other geographical factors that can influence earthquake magnitudes.

*__Depth Impact__: The model includes depth as a feature, but the relationship between depth and magnitude can be complex. The model might not capture all nuances of this relationship effectively.

*__Underestimation of High Magnitudes__: For higher earthquake magnitudes, the model can sometimes underestimate the values. This limitation may arise from the distribution of training data or the model’s learning capacity.

*__Extrapolation to Future Dates__: The model may produce values that tend towards the mean of the training data (approximately 4) when predicting for dates far into the future. This is because the model's performance diminishes for extrapolation beyond the range of the training data, making it less effective for long-term forecasting.

## Trade-offs

*__Model Complexity vs. Interpretability__: While the Random Forest model is robust and capable of capturing complex patterns, its ensemble nature makes it difficult to interpret how individual features impact predictions. This complexity can hinder understanding of the model’s decision-making process.

*__Performance vs. Training Time__: Increasing the number of trees in the Random Forest can enhance performance but also requires more training time and computational resources. There is a trade-off between achieving higher accuracy and managing computational efficiency.

*__Accuracy vs. Long-term Predictions__: The model performs well on the historical range of data but may struggle with long-term predictions. As dates move further from the training data's time range, the model tends to output values close to the average of the training set, reducing its effectiveness for forecasting future magnitudes accurately.
