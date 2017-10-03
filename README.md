# API Gateway CORS configuration module for Terraform

This is a slim Terraform module which creates an OPTIONS method and applies a CORS configuration for a resource in API Gateway.

Example: 
```
#options
module "api_gateway_cors" {
  source = "git::ssh://git@github.nike.com/ngp/terraform-api-gateway-cors-module.git"
  resource_name = "greedy_path_resource"
  resource_id = "${aws_api_gateway_resource.greedy_path_resource.id}"
  rest_api_id = "${aws_api_gateway_rest_api.api_gateway_rest_api.id}"
}
```

### Note:
Be sure to also set the `response_parameters` values on each of your Method Responses and Integration Responses.
Example:
```
resource "aws_api_gateway_method_response" "DemoPostMethodResponse200" {
  rest_api_id = "${aws_api_gateway_rest_api.API.id}"
  resource_id = "${aws_api_gateway_resource.Demo.id}"
  http_method = "${aws_api_gateway_method.DemoPost.http_method}"
  status_code = "200"
  response_models = {
    "application/json" = "Empty"
  }
  response_parameters = { "method.response.header.Access-Control-Allow-Origin" = "*" }
}
```
