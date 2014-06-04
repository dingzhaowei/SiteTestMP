# Add Test Data #

To add new test case, you can click the 'New' button on the Web Console's 'TestData' tab, and input necessary information.

* *Name* - the unique identifier of the test data.
* *Properties* - the json representation of the data properties.
* *Parent* - the parent data from which the properties are inherited.
* *Tags* - the groups to which the test data belongs.

# Data Hierarchy #

For automation code, the test data usually maps to the data model in the developer's code. Inheritance replationship exists between base model and sub models. In the real world, it's also true that many data share some properties, while having sepcial values to the other. TestMP takes such hierarchy into account when storing the test data, and facilitates the usage by merging the data and its parent automatically.

# Use Test Data #

It's very easy to use the test data in test case:

	// Get test data by name
	TestData td = TestData.get("test data name");

	// Get property value
	Object prop = td.getPropertyValue("property name");

	// Get all properties
	Map<String, Object> props = td.getProperties();

	// Convert test data to the instance of class T
	T o = td.convertTo(T.class);

	// Get a list of test data belonging to some groups
	String[] includedTags = new String[] { "tag1", "tag2" };
	List<TestData> dataList1 = TestData.get(includedTags);

	String excludedTags = new String[] { "tags" };
	List<TestData> dataList2 = TestData.get(includedTags, excludedTags);
