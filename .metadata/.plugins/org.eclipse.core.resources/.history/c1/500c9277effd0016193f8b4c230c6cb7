package test.edu.towson.cis.cosc442.project2.vendingmachine;

import static org.junit.Assert.*;

import org.junit.After;
import org.junit.Before;
import org.junit.Test;

import edu.towson.cis.cosc442.project2.vendingmachine.VendingMachineException;
import edu.towson.cis.cosc442.project2.vendingmachine.VendingMachineItem;

public class VendingMachineItemTest {
	VendingMachineItem vi;
	@Before
	public void setUp() throws Exception {
		vi = new VendingMachineItem("chips",9.99);
	}

	@After
	public void tearDown() throws Exception {
	}
	
	/**
	 * test constructing a vending machine item with valid arguments does not fail
	 */
	@Test
	public void testVendingMachineItem() {
		try{
			@SuppressWarnings("unused")
			VendingMachineItem localvi = new VendingMachineItem("coke",1.99);
		}catch (Exception e){
			fail(e.getMessage());
		}
	}
	
	/**
	 * Test precondition, price >=0
	 */
	@Test(expected=VendingMachineException.class)
	public void testVendingMachineItem_negPrice(){
		new VendingMachineItem("steak",-0.01);
	}
	
	/**
	 * Tests getName returns the right name
	 */
	@Test
	public void testGetName() {
		assertEquals("chips",vi.getName());
	}

	/**
	 * Test getPrice returns the right price
	 */
	@Test
	public void testGetPrice() {
		assertEquals(9.99,vi.getPrice(),0.00);
	}

}
