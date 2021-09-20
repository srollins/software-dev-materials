Software Testing
================

# Roles in Software #

First, a few words about jobs in the software industry and where the responsibility for testing lies.

### Developer/Software Development Engineer (SDE)
This is the role many CS undergrads desire when they complete a CS degree. In the beginning, you'll probably spend much of your time writing (and testing!) code. Software developers, however, spend much of their time discussing requirements with others in their organizations, communicating progress and problems, and performing other responsibilities such as interviewing possible new team mates. In most cases, in a short amount of time you'll go from mostly programming to more meetings and other interactions where you will be expected to define system architecture, identify new features, and so on. 

These links provide an interesting perspective:

- [Day in the Life of a Googler](http://matt-welsh.blogspot.com/2010/12/day-in-life-of-googler.html)
- [Day in the Life of a Google Manager](http://matt-welsh.blogspot.com/2015/01/day-in-life-of-google-manager.html)

Developers are expected to test code! The level of responsibility, however, depends on a variety of factors, including the size of the company. The smaller the company, the larger the burden on the developer.

### Quality Assurance Engineer (QA)

A more traditional "test" job is QA engineer. The QA engineer may or may not write much code, but is responsible for testing the end product. This may include using tools to facilitate automation, and may also require some domain-specific knowledge (e.g., understanding whether the product is giving the correct results or not). Generally, the software development team delivers the product to the QA team, who then identifies bugs that must be fixed before delivery.

### Software Development Engineer in Test (SDET)

Many larger companies also have SDETs. The goal of this role is to write the code to test the product. SDETs do write code, however their goal is to automate the process of identifying bugs.

# Testing 

### Unit Testing

[Unit tests](http://en.wikipedia.org/wiki/Unit_testing) examine individual components, for example methods. In this strategy, knowledge of the code and logic is exploited, which means that it falls under the category of [white-box testing](http://en.wikipedia.org/wiki/White-box_testing).

### Integration Testing

[Integration testing](http://en.wikipedia.org/wiki/Integration_testing) (also see [Fowler's thoughts on integration tests](https://martinfowler.com/bliki/IntegrationTest.html)) also falls under the category of white-box testing. Integration tests examines how modules integrate with each other. An integration test may test parameter passing between modules, or consider a specific workflow through the application. 

### System Testing

[System testing](http://en.wikipedia.org/wiki/System_testing) tests the entire, end-to-end system. System testing falls under the category of [black-box testing](http://en.wikipedia.org/wiki/Black-box_testing). Black-box testing advocates testing of the system without accessing the internal components. In other words, the system is treated like a black box and the tests explore whether the correct outputs are produced given appropriate inputs. No knowledge of the code or logic is exploited.

# Implementing Software Tests

[JUnit](http://junit.org/) is a common framework used for automated unit and integration testing, but it is certainly not the only testing framework. There is a lot of good information available on the [JUnit FAQ](https://github.com/junit-team/junit/wiki/FAQ).

### JUnit API

The [javadoc](https://junit.org/junit5/docs/current/api/overview-summary.html) is a helpful resource. 

**Annotations** are specified for methods in a JUnit test class. Section 3.1 of the [user guide](https://junit.org/junit5/docs/current/user-guide/) outlines the supported annotations, for example the following:

> ```@Test``` - Denotes that a method is a test method. Unlike JUnit 4’s @Test annotation, this annotation does not declare any attributes, since test extensions in JUnit Jupiter operate based on their own dedicated annotations. Such methods are inherited unless they are overridden.

> ```@BeforeEach``` - Denotes that the annotated method should be executed before each @Test, @RepeatedTest, @ParameterizedTest, or @TestFactory method in the current class; analogous to JUnit 4’s @Before. Such methods are inherited unless they are overridden.

In addition, test annotations may specify a timeout, after which the test will fail, as well as an exception expected by the test where appropriate.

***Assertions*** methods are used in each test to determine whether the conditions tested are met. These methods evaluate some condition, and may optionally take as input a message to be displayed in case the test fails. The assertion methods include the following: 

- ```assertTrue```
- ```assertNull```
- ```assertSame```
- ```assertEquals```
- ```assertFalse```
- ```assertNotNull```
- ```assertNotSame```
- ```assertArrayEquals```

### Writing Good Tests

Of course, arguably the most challenging element of testing is writing good tests. Writing good tests takes practice, but following a few guidelines to consider:

- **Test one thing per test** - A good unit test will test one condition. If it fails, you should be able to identify the very specific case that needs to be address.
- **Tests should be small** - A test should be small --- very few lines of code.
- **Test should be automated and repeatable** - Running tests should be easy and tests should be rerun anytime the code changes.
- **Tests should be intuitive** - It should be easy for another developer to understand the test.
- **Start with the easy cases** - Begin with tests that assume valid input.
- **Test corner cases** - This includes null values and input out of bounds.

**References**

- [http://www.christiaanverwijs.nl/post/2012/10/17/How-writing-Unit-Tests-force-you-to-write-Good-Code-And-6-bad-arguments-why-you-shouldnt.aspx](http://www.christiaanverwijs.nl/post/2012/10/17/How-writing-Unit-Tests-force-you-to-write-Good-Code-And-6-bad-arguments-why-you-shouldnt.aspx)
- [http://programmers.stackexchange.com/questions/21133/how-to-write-good-unit-tests](http://programmers.stackexchange.com/questions/21133/how-to-write-good-unit-tests)

### Other Notes

There are several [naming conventions](https://dzone.com/articles/7-popular-unit-test-naming) that are commonly used.

Often, the number of lines of test code will exceed the number of lines of code being tested. In some cases, you may see 5x more test code than non-test code. 

Writing tests helps to enforce better design. If you have a hard time writing good test cases, you may want to rethink your original code.

### Exercises

1. **Describe 3 unit tests for the following method:**

	```
	/**
	 * isSorted takes as input an array of int and returns true if the list is
	 * sorted and false otherwise.
	 */
	public boolean isSorted(int[] list);
	``` 

2. **A URL consists of the following parts:**

    ```
	    [protocol]://[domain]/[path]&[queryString]
	    http://www.google.com/search?q=computer
    ```

    In the example,

    - `http` is the protocol.
    - `www.google.com` is the domain. The domain must have at least a top-level domain (e.g., com) and a         host.
    - `/search` is the path. The path is optional.
    - `q=computer` is the query string. The query string is optional.

    Consider a class `URLParser` with the following components:

    - `URLParser(String urlString)`
    - `getProtocol`
    - `getDomain`
    - `getPath`
    - `getQueryString`
    - `isValid`

    Describe 10 unit tests for this class. Specify the test setup, input, and expected result. One example     follows:

    `testGetProtocol` - construct a URL with the String "http://www.google.com". `assertTrue` - `getProtocol` returns `http`.

3. **Describe one integration test for Project 1.**
4. **Describe one integration test for Project 2.**
5. **Describe one system test for Project 1 that you do not complete during interactive grading.**
6. **Describe one system test for Project 2.**
