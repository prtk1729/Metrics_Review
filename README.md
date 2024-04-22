# Dataset Curation and Evaluation Metrics
Ideas on how to create Ny's style-based-test-set and evaluation metrics

[![maintained by dataroots](https://img.shields.io/badge/maintained%20by-dataroots-%2300b189)](https://dataroots.io)
[![PythonVersion](https://img.shields.io/pypi/pyversions/gino_admin)](https://img.shields.io/pypi/pyversions/gino_admin)
[![Codecov](https://codecov.io/github/datarootsio/ml-skeleton-py/badge.svg?branch=master&service=github)](https://github.com/datarootsio/ml-skeleton-py/actions)
[![Code style: black](https://img.shields.io/badge/code%20style-black-000000.svg)](https://github.com/psf/black)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=flat-square)](http://makeapullrequest.com)
![](https://scontent.fbru1-1.fna.fbcdn.net/v/t1.0-9/94305647_112517570431823_3318660558911176704_o.png?_nc_cat=111&_nc_sid=e3f864&_nc_ohc=-spbrtnzSpQAX_qi7iI&_nc_ht=scontent.fbru1-1.fna&oh=483d147a29972c72dfb588b91d57ac3c&oe=5F99368A "Logo")



### Objective

`To develop
 - Novel/Already present Evaluation metrics on comparison of relative ordering of 2 sequences
 - Method to render and annotate anchor:suggestive datapoints`

### Evaluation metrics

#### NDCG

#### Kendall Tau




####
import ipywidgets as widgets
from IPython.display import display, clear_output
import pandas as pd

image_urls = [
    "path/to/image1.jpg",
    "path/to/image2.jpg",
    "path/to/image3.jpg",
    # Add all 20 image paths
]


# Create a DataFrame to store image URLs upon button clicks
saved_urls = pd.DataFrame(columns=['Image URL'])

def save_url_and_hide(button):
    # Retrieve the image URL from the button's 'image_url' attribute
    image_url = button.image_url
    
    # Append the URL to the DataFrame
    global saved_urls
    saved_urls = saved_urls.append({'Image URL': image_url}, ignore_index=True)
    
    # Hide the image and button
    button.layout.visibility = 'hidden'
    button.image_widget.layout.visibility = 'hidden'
    
    # Save the DataFrame to a CSV file
    saved_urls.to_csv('/dbfs/FileStore/my_folder/saved_image_urls.csv', index=False)

# Create a list to hold all widgets for display
widgets_list = []

for url in image_urls:
    # Create the image widget
    image_widget = widgets.Image(value=open(url, "rb").read(), format='jpg', width=150, height=150)
    
    # Create the button widget
    button = widgets.Button(description="Save URL")
    
    # Set custom attributes for ease of access
    button.image_url = url
    button.image_widget = image_widget
    
    # Set the on_click event
    button.on_click(save_url_and_hide)
    
    # Append to the list
    widgets_list.append(widgets.VBox([image_widget, button]))

# Display all widgets
display(widgets.VBox(widgets_list))






`In the embedding space after applying Fashion-CLIP (FCLIP) on the products, the choice between curating a dataset with the top 20 recommendations that are close-by to the anchor's embedding vector or spread-out depends on the specific goals of your evaluation.


- Close-by Recommendations:

Goal: Evaluate the model's precision in recommending stylistically similar products.
Reasoning: By selecting recommendations that are close to the anchor in the embedding space, you focus on assessing the model's ability to identify products with a high degree of stylistic similarity. This approach is useful if your primary objective is to test the model's precision in capturing fine-grained style nuances.


- Spread-out Recommendations:

Goal: Evaluate the model's diversity in recommending a variety of stylistically relevant products.
Reasoning: By selecting recommendations that are spread out in the embedding space, you can assess the model's ability to capture a diverse range of stylistically relevant products. This approach is useful for understanding the model's capacity to explore different facets of style while still maintaining relevance to the anchor.


- Hybrid Approach:

Goal: Balance precision and diversity in recommendations.
Reasoning: A hybrid approach, where you select some recommendations that are close-by and some that are spread-out, allows you to evaluate both the precision and diversity of the model's recommendations. This approach provides a more comprehensive understanding of the model's performance.
`





### Affiliations
* Ny.com
  
> Author(s)
  * `Prateek Pani` (`prateek.pani@ny.com`)

