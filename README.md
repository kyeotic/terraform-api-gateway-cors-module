# API Gateway CORS configuration module for Terraform

This is a slim Terraform module which creates an OPTIONS method and applies a CORS configuration for a resource in API Gateway.

Example: 
```
#options
module "api_gateway_cors" {
  source      = "github.com/kyeotic/terraform-api-gateway-cors-module.git?ref=1.1"
  resource_id = aws_api_gateway_resource.gql.id
  rest_api_id = aws_api_gateway_rest_api.api.id
}
```

## Custom Headers

The `additional_headers` property will accept a list of headers to add to the default list of allowed headers.