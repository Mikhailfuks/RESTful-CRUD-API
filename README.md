// Define the base URL for the API
const apiBaseUrl = 'http://localhost:3000/api/v1';

// Function to get all resources
async function getAllResources() {
 try {
  const response = await fetch(`${apiBaseUrl}/resources`);
  const data = await response.json();
  // Handle the data, e.g., display in a table or list
  console.log(data);
 } catch (error) {
  console.error('Error fetching resources:', error);
 }
}

// Function to get a single resource by ID
async function getResourceById(id) {
 try {
  const response = await fetch(`${apiBaseUrl}/resources/${id}`);
  const data = await response.json();
  // Handle the data, e.g., display in a detail view
  console.log(data);
 } catch (error) {
  console.error('Error fetching resource:', error);
 }
}

// Function to create a new resource
async function createResource(data) {
 try {
  const response = await fetch(`${apiBaseUrl}/resources`, {
   method: 'POST',
   headers: {
    'Content-Type': 'application/json'
   },
   body: JSON.stringify(data)
  });
  if (response.ok) {
   // Resource created successfully
   console.log('Resource created successfully.');
  } else {
   // Handle error response
   console.error('Error creating resource:', response.status, response.statusText);
  }
 } catch (error) {
  console.error('Error creating resource:', error);
 }
}

// Function to update a resource
async function updateResource(id, data) {
 try {
  const response = await fetch(`${apiBaseUrl}/resources/${id}`, {
   method: 'PUT',
   headers: {
    'Content-Type': 'application/json'
   },
   body: JSON.stringify(data)
  });
  if (response.ok) {
   // Resource updated successfully
   console.log('Resource updated successfully.');
  } else {
   // Handle error response
   console.error('Error updating resource:', response.status, response.statusText);
  }
 } catch (error) {
  console.error('Error updating resource:', error);
 }
}

// Function to delete a resource
async function deleteResource(id) {
 try {
  const response = await fetch(`${apiBaseUrl}/resources/${id}`, {
   method: 'DELETE'
  });
  if (response.ok) {
   // Resource deleted successfully
   console.log('Resource deleted successfully.');
  } else {
   // Handle error response
   console.error('Error deleting resource:', response.status, response.statusText);
  }
 } catch (error) {
  console.error('Error deleting resource:', error);
 }
}

// Example usage:
getAllResources();
getResourceById(123);
createResource({ name: 'New Resource', description: 'This is a new resource' });
updateResource(456, { name: 'Updated Resource' });
deleteResource(789);
