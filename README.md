# SwiftBasicDemo1
My first github project
hello how are you?


JsonParsing

  let headers = [
            "x-api": "TWl0ZXNoUGF0ZWwtRGlhYmV0ZXNBcHAtOS0xLTIwMTg",
            "access_token": "2135bfaf6e1c1a237e1b7309fc37400d1524028482",
            "id": "1",
            "user_type": "user",
            "cache-control": "no-cache",
            "Postman-Token": "f2b2354e-5429-430e-a977-0736bf9c8b08"
        ]
        
        let request = NSMutableURLRequest(url: NSURL(string: "http://13.228.37.135/kneebu/public/api/category")! as URL,
                                          cachePolicy: .useProtocolCachePolicy,
                                          timeoutInterval: 10.0)
        request.httpMethod = "POST"
        request.allHTTPHeaderFields = headers
        
        let session = URLSession.shared
        let dataTask = session.dataTask(with: request as URLRequest, completionHandler: { (data, response, error) -> Void in
            if (error != nil) {
                print(error)
            } else {
                let httpResponse = response as? HTTPURLResponse
                print(httpResponse)
                
                let statusCode = httpResponse?.statusCode
                
                if(statusCode == 200)
                {
                    do {
                        let jsonResponse = try JSONSerialization.jsonObject(with: data!, options: .mutableContainers) as! [String : Any]
//                        print(jsonResponse as! [String : Any])
                        print(jsonResponse["data"])

                        
                    }
                    catch let error
                    {
                        print(error)
                    }
                }
            }
        })
        
        dataTask.resume()
