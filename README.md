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


