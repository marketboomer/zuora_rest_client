# ZuoraRestClient

This is a simple Zuora client for Ruby.  It mainly consists of methods that 
wrap the operations described in the Zuora API Reference 
(https://www.zuora.com/developer/api-reference), as well as a few helper methods.

Most of the methods take either the query parameters and/or a hash representing the JSON
request body as arguments.  The methods return a `ZuoraRestClient::Result` object which
represents ths JSON response.

## Installation

Add this line to your application's Gemfile:

```ruby
gem 'zuora_rest_client'
```

And then execute:

    $ bundle

Or install it yourself as:

    $ gem install zuora_rest_client

## Usage

First, construct a client object:
```ruby
username = 'zuora_username@example.com'
password = 'mypassword'
client = ZuoraRestClient::Client.new(username, password)  # Create a production client
```

For a sandbox tenant, you can specify the following:
```ruby
client = ZuoraRestClient::Client.new(username, password, :api_sandbox)  # Create an api sandbox client
```

Call one of the client methods.  For example, to create an account:
```ruby
account_to_create = {
    Batch: 'Batch1',
    BillCycleDay: 15,
    Currency: 'USD',
    Name: 'Test Account',
    PaymentTerm: 'Due Upon Receipt',
    Status: 'Draft' }
result = client.create_account_object(account_to_create) # Returns an object representation of the JSON response
```

## Contributing

Bug reports and pull requests are welcome on GitHub at https://github.com/FronteraConsulting/zuora_rest_client.

