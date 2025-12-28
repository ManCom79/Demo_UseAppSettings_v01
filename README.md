# UseAppSettings_v01

This is a core MVC application that is used to demo how variables from appsettings.json are called in the application.
Changes to the "boilerplate" app are:

1. The variable "MyVariable" is defined in appsettings.json file.

2. HomeController class holds the __configuration_ field that is used to read the application settings:
    
        private readonly IConfiguration _configuration;

        public HomeController(IConfiguration configuration)
        {
            _configuration = configuration;
        }

3. Injection of "MyVariable" value into ViewBag:

        public IActionResult Index()
        {
            ViewBag.MyVariable = _configuration["MyVariable"];
            return View();
        }

4. Usage of ViewBag value in the index.cshtml
        ```<h2>@ViewBag.MyVariable</h2>```
