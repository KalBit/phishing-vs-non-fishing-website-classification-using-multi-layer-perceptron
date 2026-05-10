# Phishing Website Detection using MLP in Pytorch
Workflow to Classify Websites as legitimate or phishing using multi layer perceptron implemented with pytorch library

## Dataset 
Feature Columns: 

having_ip_address | url_length | shortining_service | having_at_symbol | double_slash_redirecting | prefix_suffix | having_sub_domain | sslfinal_state | domain_registration_length | favicon | port | https_token | request_url | url_of_anchor | links_in_tags | sfh | submitting_to_email | abnormal_url | redirect | on_mouseover | rightclick | popupwindow | iframe | age_of_domain | dnsrecord | web_traffic | page_rank | google_index | links_pointing_to_page |

### Class Distribution

<p align="center">
  <img src="./plots/class_dist.png" alt="Class Distribution" />
</p>

## Workflow
```mermaid
flowchart TB
    n1["Data Loading"] --> n2["Train, Validation and Test Split (0.8, 0.1, 0.1)"]
    n2 --> n3["Scaling<br>"]
    n3 --> n4["Train the model using Training set while evaluating on validation set<br>"]
    n4 --> n5["Determine the Number of Epochs to Train the Final Model"]
    n5 --> n6["Train the Final Model"]
    n6 --> n7["Evaluate the Final Model on Test Set"]

    n1@{ shape: rect}
    n5@{ shape: rounded}
```
## Model Architecture

<p align="center">
  <img src="./misc/MLP_diagram.png" alt="Model_Diagram" />
</p>

## Model Evaluation

Training loss, accuracy and Validation loss, accuracy over number of epochs.

<p align="center">
  <img src="./plots/loss_epoch.png" width="48%" alt="Loss Curve" />
  <img src="./plots/acc_epoch.png" width="48%" alt="Accuracy Curve" />
</p>

No improvement in the validation accuracy or loss after 47 epochs.Therefore final model was trained for 47 epochs.

Then the final model trained on combined train and validation set was evaluated on the unseen test data. The following results were obtained.

<div align="center">
  <table>
    <thead>
      <tr>
        <th>Metric</th>
        <th>Phishing (Class 0)</th>
        <th>Legitimate (Class 1)</th>
        <th>Overall Metrics</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td><b>Precision</b></td>
        <td>0.97</td>
        <td>0.96</td>
        <td rowspan="4" align="center">
          <b>Accuracy: 0.96</b><br>
          <hr>
          <b>Total Support: 2211</b>
        </td>
      </tr>
      <tr>
        <td><b>Recall</b></td>
        <td>0.94</td>
        <td>0.98</td>
      </tr>
      <tr>
        <td><b>F1-Score</b></td>
        <td>0.96</td>
        <td>0.97</td>
      </tr>
      <tr>
        <td><b>Support</b></td>
        <td>980</td>
        <td>1231</td>
      </tr>
    </tbody>
  </table>
</div>

confusion matrix for the test data is shown below,

<p align="center">
  <img src="./plots/cm.png" alt="Confusion_Matrix" />
</p>

## Conclusion

The Multi layer perceptron performs exceptionally well in classifying website into phishing and legitimate given the feature set. It has an overall 96% accuracy. The model identifies 98% of the websites that are safe to visit and 96% of the phishing websites are identified correctly. 94% recall for phishing depicts that around 6% of the phishing websites have been misclassified.

## Areas to Improve

- feature engineering
- Hyper parameter tuning

