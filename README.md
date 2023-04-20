# IT314 : Lab 8 - JUnit Testing

### Name        : Vishesh Patel
### Student ID  : 202001186


## Boa Class
```
package lab8;

//represents a boa constrictor
public class Boa {
	private String name;
	private int length; // the length of the boa, in feet
	private String favoriteFood;
	
	public Boa (String name, int length, String favoriteFood){
		this.name = name;
		this.length = length;
		this.favoriteFood = favoriteFood;
	}
	
	//returns true if this boa constrictor is healthy
	public boolean isHealthy(){
		return this.favoriteFood.equals("granola bars");
	}
	
	//returns true if the length of this boa constrictor is
	//less than the given cage length
	public boolean fitsInCage(int cageLength){
		return this.length < cageLength;	
	}
}

```


## BoaTest JUnit

`jen` and `ken` must be decalred as private `Boa` objects in the `BoaTest` class. The @Before annotation ensures that the setUp() method is run before each test method is executed, so the jen and ken objects will be available to all the test methods in the class.

```
package lab8;
import static org.junit.Assert.*;

import org.junit.Before;
import org.junit.Test;

public class BoaTest {
	
	private Boa jen;
	private Boa ken;
	
	@Before
	public void setUp() throws Exception {
		jen = new Boa("Jennifer", 2, "grapes");
		ken = new Boa ("Kenneth", 3, "granola bars");
	}

	@Test
	public void testIsHealthy() {
		assertTrue(ken.isHealthy());
		assertFalse(jen.isHealthy());
	}
	
	
	@Test
	public void testFitsInCage() {
		assertFalse(jen.fitsInCage(1));
		assertTrue(jen.fitsInCage(3));
		assertFalse(jen.fitsInCage(2));
	}
}
```
On running the above tests we get a green bar. All possibilities are tested in the testcases.

![image](https://user-images.githubusercontent.com/124247859/233326140-cd258680-3db0-4946-9856-0d0a9617023a.png)


## Adding New Method in Boa class

```
public int lengthInInches(){
  return this.length*12;
}
```

## Adding New Test in BoaTest class

```
@Test
public void testLengthInInches() {
  assertEquals(24, jen.lengthInInches());
  assertEquals(36, ken.lengthInInches());
}

```

## Test Results
![image](https://user-images.githubusercontent.com/124247859/233329904-91afe2ba-95d4-44e4-be4c-3a76daa231d4.png)

After running the tests, the JUnit pane displays a green bar indicating that all tests have passed.
