# Trello--API

The script integrates with the Trello API to retrieve the current status of Trello boards, lists, and cards. The libraries used in the script are Requests, JSON, and Pandas.

The process of the script is as follows:

The API URL is retrieved from Trello and the required data is specified. For example, if the details of a board are needed, the API for boards is used, and similarly for lists and cards.
The finalized URL is then sent using the Requests module to retrieve the response. If the response is successful, it should be a "200" status.
If the response is 200, the JSON object is unpacked using the JSON module.
The data is then structured and loaded from the JSON object based on the requirements.
Finally, the structured data is converted to a Pandas dataframe and saved in either an Excel sheet or a CSV file, depending on the requirement.
