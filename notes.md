## Steps to homework completion:

### IndexedDB, Web Manifest, Service-Worker WEEK 18 HOMEWORK

Purpose of this application was to add offline functionality

---

1. Added manifest.webmanifest file: configured icons, theme, and display: standalone.

2. Added service-worker.js file: configured FRONT END FILES_TO_CACHE. 

    Install, Activate, Fetch middleware

3. Added IndexedDB functionality and saveRecord(transaction) functionality. 

    Created db.js 

---

### Key Takeaways:

1. Connecting MongoDB to Heroku deployment: 

    Make sure process.env.MONGODB_URI and process.env.PORT is in server.js, and the LOCALHOST setting points to name of DB

`const PORT = process.env.PORT || 3000;`

`mongoose.connect(process.env.MONGODB_URI || "mongodb://localhost/budget_tracker", {
  useNewUrlParser: true,
  useFindAndModify: false
});`

2. Create OFFLINE saving functionality with saveRecord() function in the db.js

`function saveRecord(record) {`

  1. create a transaction on the pending db with readwrite access
  `const transaction = db.transaction(["pending"], "readwrite");`

  2. access your pending object store
  `const store = transaction.objectStore("pending");`

  3. add record to your store with add method.
 `store.add(record);}`
    
3. Connect the saveRecord() to your index.js, to save to the indexedDB if the DB is not online. 