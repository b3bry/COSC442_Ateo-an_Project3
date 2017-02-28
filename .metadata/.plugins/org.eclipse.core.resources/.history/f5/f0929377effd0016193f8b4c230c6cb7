package test.edu.towson.cis.cosc442.project2.vendingmachine;

import static org.junit.Assert.*;

import org.junit.After;
import org.junit.Before;
import org.junit.Test;

import edu.towson.cis.cosc442.project2.vendingmachine.VendingMachine;
import edu.towson.cis.cosc442.project2.vendingmachine.VendingMachineException;
import edu.towson.cis.cosc442.project2.vendingmachine.VendingMachineItem;

public class VendingMachineTest {
	VendingMachine vm;
	VendingMachineItem chips;
	VendingMachineItem coke;
	@Before
	public void setUp() throws Exception {
		vm = new VendingMachine();
		chips = new VendingMachineItem("chips",9.99);
		coke = new VendingMachineItem("coke",1.99);
	}

	@After
	public void tearDown() throws Exception {
	}
	
	/**
	 * vanilla test of add item
	 * Verifies postcondition
	 * 
	 */
	@Test
	public void testAddItem() {
		vm.addItem(chips, "A");
		assertEquals("chips",vm.removeItem("A").getName());
	}
	
	/**
	 * Tests when an item is added into an occupied slot
	 * 
	 */
	@Test(expected=VendingMachineException.class)
	public void testAddItem_SameSlot(){
		vm.addItem(chips, "A");
		vm.addItem(coke, "A");
		
	}
	
	/**
	 * Tests when an item is added into a slot that doesn't exist
	 */
	@Test(expected=VendingMachineException.class)
	public void testAddItem_InvalidCodeNotExist(){
		vm.addItem(chips, "E");
	}
	
	/**
	 * Tests when an item is added into a slot that is not a letter
	 */
	@Test(expected=VendingMachineException.class)
	public void testAddItem_InvalidCodeNotLetter(){
		vm.addItem(chips, "0");
	}
	
	/**
	 * Tests when not slot is given
	 */
	@Test(expected=VendingMachineException.class)
	public void testAddItem_InvalidCodeEmpty(){
		vm.addItem(chips, "");
	}
	
	/**
	 * vanilla test case for remove item
	 */
	@Test
	public void testRemoveItem() {
		vm.addItem(coke, "C");
		assertEquals("coke",vm.removeItem("C").getName());
	}
	
	/**
	 * Test postcondition, the item is removed
	 */
	@Test
	public void testRemoveItem_isRemoved() {
		try{
			vm.addItem(chips, "D");
			vm.removeItem("D");
			vm.addItem(coke, "D"); // throws an exception if the slot is already occupied.
		}catch(Exception e){
			fail(e.getMessage());
		}
	}
	
	/**
	 * Tests when an empty slot is given
	 */
	@Test(expected=VendingMachineException.class)
	public void testRemoveItem_Empty(){
		vm.removeItem("B");
	}
	
	/**
	 * Tests when no slot is given
	 */
	@Test(expected=VendingMachineException.class)
	public void testRemoveItem_NoSlot(){
		vm.removeItem("");
	}
	
	/**
	 * Tests invalid slot
	 */
	@Test(expected=VendingMachineException.class)
	public void testRemoveItem_invalidSlot(){
		vm.removeItem("AA");
	}
	
	
	
	/**
	 * vanilla test case for insert money
	 * Inserting a valid amount
	 */
	@Test
	public void testInsertMoney() {
		double init_balance = vm.getBalance();
		vm.insertMoney(0.00);
		double cur_balance = vm.getBalance();
		
		assertEquals(0.00, cur_balance-init_balance,0.00);
	}
	
	/**
	 * 2nd vanilla test case for insert money
	 * Inserting a valid amount
	 */
	public void testInsertMoney_2ndVanilla(){
		double init_balance = vm.getBalance();
		vm.insertMoney(5.00);
		double cur_balance = vm.getBalance();
		
		assertEquals(5.00, cur_balance-init_balance,0.00);
	}
	
	/**
	 * Tests when a negative amount is given
	 */
	@Test(expected=VendingMachineException.class)
	public void testInsertMoney_NegativeAmount(){
		vm.insertMoney(-0.01);
	}
	
	/**
	 * Tests when an extremely large amount is given
	 * 
	 */
	@Test
	public void testInsertMoney_LargeAmount(){
		double init_balance = vm.getBalance();
		vm.insertMoney(Double.MAX_VALUE);
		double cur_balance = vm.getBalance();
		
		assertEquals(Double.MAX_VALUE, cur_balance-init_balance,0.00);
	}
	
	/**
	 * vanilla test case for getBalance
	 * Tests getting balance
	 */
	@Test
	public void testGetBalance() {
		vm.insertMoney(10.00);
		assertEquals(10.00,vm.getBalance(),0.00);
	}
	
	/**
	 * Tests precondition, vending machine should start with 0 balance.
	 */
	@Test
	public void testGetBalance_startBalance(){
		assertEquals(0.00,vm.getBalance(),0.00);
	}
	
	/**
	 * Tests postcondition, getBalance does not alter the balance
	 */
	@Test
	public void testGetBalance_noAlterBalance(){
		vm.insertMoney(10.00);
		vm.getBalance();
		assertEquals(10.00,vm.getBalance(),0.00);
	}
	
	/**
	 * vanilla test case for make Purchase
	 * tests making a purchase
	 */
	@Test
	public void testMakePurchase() {
		vm.insertMoney(9.99);
		vm.addItem(chips, "A");
		assertTrue(vm.makePurchase("A"));
	}
	
	/**
	 * Test postcondition, the item is purchased is removed
	 */
	@Test
	public void testMakePurchase_isItemRemoved(){
		vm.insertMoney(9.99);
		vm.addItem(chips, "A");
		vm.makePurchase("A");
		try{
			vm.addItem(coke, "A");
		}catch(Exception e){
			fail(e.getMessage());
		}
	}
	
	/**
	 * Test postcondition, the cost of the item is subtracted from the balance
	 */
	@Test
	public void testMakePurchase_costSubtracted(){
		vm.insertMoney(9.99);
		vm.addItem(chips, "A");
		vm.makePurchase("A");
		assertEquals(0.00,vm.getBalance(),0.00);
	}
	
	/**
	 * Test when the slot is empty but the balance is sufficient
	 */
	@Test
	public void testMakePurchase_emptySufficient(){
		vm.insertMoney(9.99);
		vm.makePurchase("D");
		assertFalse(vm.makePurchase("D"));
	}
	
	/**
	 * Test when the slot is filled but the balance is insufficient
	 */
	@Test
	public void testMakePurchase_filledNoSufficient(){
		vm.addItem(chips, "B");
		assertFalse(vm.makePurchase("B"));
	}
	
	/**
	 * Test when the slot is empty and the balance is insufficient
	 */
	@Test
	public void testMakePurchase_emptyNoSufficient(){
		assertFalse(vm.makePurchase("A"));
	}

	/**
	 * vanilla test case for return change
	 * 
	 */
	@Test
	public void testReturnChange() {
		vm.insertMoney(9.99);
		assertEquals(9.99,vm.returnChange(),0.00);
	}
	
	/**
	 * test postcondition, balance is 0
	 */
	@Test
	public void testReturnChange_afterBalance(){
		vm.insertMoney(9.99);
		vm.returnChange();
		assertEquals(0.00,vm.getBalance(),0.00);
	}

}
