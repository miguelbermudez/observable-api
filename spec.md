

  API
    √ has property request$: Observable
    √ has method createEndpoint()
    Endpoint
      √ has property request$: Observable
      √ has property response$: Observable
      √ has property fetching$: Observable
      √ has method fetch()
      provided URI is function
        √ calls URI function with params, data
        √ defaultParams & defaultData is used
        √ return value is api url
      fetch(params, data)
        √ calls XHR client with url, method, params, data
        √ always forces new request
      request$
        √ error should not terminate request$
        first subscription
          √ invokes fetch(defaultParam, defaultData)
        later subscriptions
          √ does not invoke fetch()
        subscribers count 1 => 0 => 1
          √ does not calls fetch() again
          √ new observer receives latest request
        observer
          √ receives request: {url, method, params, data, response}
      response$
        observer
          √ invokes request if it's first
          √ receives response onNext
          √ receives only latest request response (38ms)
          √ does not receive errors
      error$
        observer
          √ invokes request if it's first
          √ receives error onNext
      fetching$
        observer
          √ invokes request if it's first
          √ receives bool onNext


  25 passing (300ms)
