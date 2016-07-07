import UIKit

class ViewController: UIViewController {

    @IBOutlet var CityName: UITextField!
    
    @IBOutlet var Resultlabel: UILabel!
    
    @IBAction func Find(sender: AnyObject) {
        
        var wasSuccesfull = false
        
        
        let attemptedurl = NSURL(string: "http://www.weather-forecast.com/locations/"+CityName.text!.stringByReplacingOccurrencesOfString(" ", withString: "-")+"/forecasts/latest")
        if let url = attemptedurl {
        
        
        let task = NSURLSession.sharedSession().dataTaskWithURL(url) { (data, response, error) in
            if let urlcontent = data
            {
                let webcontent = NSString(data: urlcontent, encoding: NSUTF8StringEncoding)
                let webarray = webcontent!.componentsSeparatedByString("3 Day Weather Forecast Summary:</b><span class=\"read-more-small\"><span class=\"read-more-content\"> <span class=\"phrase\">")
                
                if webarray.count > 1
                {
                    
                    let WeatherArray = webarray[1].componentsSeparatedByString("</span>")
                    
                if WeatherArray.count > 1
                {
                    
                    wasSuccesfull = true
                    let weathersummary = WeatherArray[0].stringByReplacingOccurrencesOfString("&deg;", withString: "º")
                    
                    dispatch_async(dispatch_get_main_queue(), {
                        self.Resultlabel.text = weathersummary
                    })
                    
                    
                    }
            
                }
                
                    
                }
            
            if wasSuccesfull == false
            {
                dispatch_async(dispatch_get_main_queue(), {
                    self.Resultlabel.text = "Enter Valid Data"
                    self.Resultlabel.shadowColor = UIColor.redColor()
                })
                
            }
            
            }
task.resume()
        }
        else
        {
            dispatch_async(dispatch_get_main_queue(), {
                self.Resultlabel.text = "Enter Correct City Name"
                self.Resultlabel.shadowColor = UIColor.redColor()
            })
            
        }
    
    }
    
    
        
        
        
    
    
    
    
    override func viewDidLoad() {
        super.viewDidLoad()
        // Do any additional setup after loading the view, typically from a nib.
    }

    override func didReceiveMemoryWarning() {
        super.didReceiveMemoryWarning()
        // Dispose of any resources that can be recreated.
    }


}

