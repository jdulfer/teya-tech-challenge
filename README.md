# Overall Readme
### Running the ledger
The two micro-services that make up this ledger are built using Ktor, a Kotlin webapp framework, and can be run using Java 17 either through `./gradlew run` or through the `main()` function in `Application.kt`. Both need be run at the same time for the ledger to function, by default the AccountAPI runs on port `8080` and the TransactionAPI runs on `8081`.

### Why are there two services?
For the purposes of this tech task, I could have easily been build in one service which was responsible for managing the state of the Accounts and the Transactions. However, I thought that it would be more interesting to build a system that more accurately mimicked what a real world micro-service's environment would look like. Therefore, the AccountAPI is only responsible for Account's data and the TransactionsAPI is only responsible for the Transactions data.

### Further information
Each API has it's own README containing some information on that micro-service, it's responsibilities and it's API resources. All requirements listed in assessment doc can be satisfied through endpoints in the AccountAPI. 
### Assumptions 
- I'm handling transactions on an account level, not a user level
	- As a result this API won't care if multiple accounts are owned by the same user as there is no concept of a User
- Everything is a single currency (just to cut down on scope)
### Improvements
These are things that I could improve upon but I decided not to implement either due to time or scope
- Error handling is ok but not perfect. Most errors will return a 500 to the AccountAPI, even if the logs provide a nicer error message
- Tests
	- As the APIs are built with Koin (a Kotlin dependancy injection tool) it is very easy to add unit tests and mock out the appropriate services/DAOs
	- Similarly, E2E tests would be easy to implement because I can inject a mock engine with pre-determined responses for external services
	- However, writing extensive tests across the two services simply would have taken too long and so I have tested these services manually for now
