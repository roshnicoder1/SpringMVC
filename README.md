# SpringMVC



![MVC](https://user-images.githubusercontent.com/37985023/165590806-64ec2819-ee13-46a9-8e9b-fbf5173dc070.PNG)


* @Controller
* @GetMapping(value= "/")
* @RequestMapping(value="/saveCustomer",method=RequestMethod.POST)
* @Validated
* @ModelAttribute(
* @RequestParam("custno")
* @RequestMapping("/hello")  

# @Controller annotation is an annotation used in Spring MVC framework (the component of Spring Framework used to implement Web Application).
The @Controller annotation indicates that a particular class serves the role of a controller. The @Controller annotation acts as a stereotype for the annotated class, indicating its role. The dispatcher scans such annotated classes for mapped methods and detects @RequestMapping annotations.

# @ModelAttribute binds form data to the object 
Note - The value passed with the @ModelAttribute annotation should be the same to the modelAttribute value present in the view page.
 ``` 
  @RequestMapping("/submitForm")  
    public String submitForm(@ModelAttribute("reservation") Reservation res)  
{  
    return "confirmation-page";  
} 
```
in the view page

 <form:form action="submitForm" modelAttribute="reservation">  
 </form>
 

```
public String addNewCustomer(@Validated @ModelAttribute("Customer")Customer customer,ModelMap map)
	{
		LocalDateTime dt=LocalDateTime.now();
		customer.setCreatedAt(dt);
		custRepObj.addCust(customer);
		List list=(List) custRepObj.getAllCustomer();
		map.put("custList",list);
		return "index";	
	}
  
  ```
  
  
  # @RequestParam and @PathVariable can both be used to extract values from the request URI, but they are a bit different.
  While @RequestParams extract values from the query string, @PathVariables extract values from the URI path:

```
@GetMapping("/foos/{id}")
@ResponseBody
public String getFooById(@PathVariable String id) {
    return "ID: " + id;
}
```
Then we can map based on the path:

http://localhost:8080/spring-mvc-basics/foos/abc
----
ID: abc
And for @RequestParam, it will be:

```
@GetMapping("/foos")
@ResponseBody
public String getFooByIdUsingQueryParam(@RequestParam String id) {
    return "ID: " + id;
}
```
which would give us the same response, just a different URI:

http://localhost:8080/spring-mvc-basics/foos?id=abc
----
ID: abc

# https://www.baeldung.com/spring-valid-vs-validated
# https://reflectoring.io/bean-validation-with-spring-boot/

  
