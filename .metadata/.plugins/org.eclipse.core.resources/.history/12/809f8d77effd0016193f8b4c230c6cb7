package test.edu.towson.cis.cosc442.project2.vendingmachine;

import static org.junit.Assert.*;

import org.junit.After;
import org.junit.Before;
import org.junit.Test;

import edu.towson.cis.cosc442.project2.vendingmachine.VendingMachineException;

public class VendingMachineExceptionTest {

	@Before
	public void setUp() throws Exception {
	}

	@After
	public void tearDown() throws Exception {
	}

	/**
	 * Test using the default constructor
	 */
	@Test
	public void testVendingMachineException() {
		try{
			new VendingMachineException();
		}catch(Exception e){
			fail(e.getMessage());
		}
	}
	
	/**
	 * Test when a reason is given
	 */
	@Test
	public void testVendingMachineExceptionString() {
		try{
			new VendingMachineException("Praise the Sun");
		}catch(Exception e){
			fail(e.getMessage());
		}
	}

}
