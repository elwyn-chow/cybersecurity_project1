## Activity File: Exploring Kibana

* You are a DevOps professional and have set up monitoring for one of your web servers. You are collecting all sorts of web log data and it is your job to review the data regularly to make sure everything is running smoothly. 

* Today, you notice something strange in the logs and you want to take a closer look.

* Your task: Explore the web server logs to see if there's anything unusual. Specifically, you will:

:warning: **Heads Up**: These sample logs are specific to the time you view them. As such, your answers will be different from the answers provided in the solution file. 

---

### Instructions

1. Add the sample web log data to Kibana.

2. Answer the following questions:

    - In the last 7 days, how many unique visitors were located in India?
        247           
    - In the last 24 hours, of the visitors from China, how many were using Mac OSX?
        14
    - In the last 2 days, what percentage of visitors received 404 errors? How about 503 errors?
        404: 0%
        503: 5.882%
    - In the last 7 days, what country produced the majority of the traffic on the website?
        USA
    - Of the traffic that's coming from that country, what time of day had the highest amount of activity?
        10 to 11 am
    - List all the types of downloaded files that have been identified for the last 7 days, along with a short description of each file type (use Google if you aren't sure about a particular file type).
        * gz - gzipped compressed file
        * css - cascading style heet
        * zip - zip compressed file
        * deb - Debian installation package
        * rpm - Red Hat Linux installation package
        
3. Now that you have a feel for the data, Let's dive a bit deeper. Look at the chart that shows Unique Visitors Vs. Average Bytes.
     - Locate the time frame in the last 7 days with the most amount of bytes (activity).
        2021-05-17 12pm: 10735 bytes, 3 count
     - In your own words, is there anything that seems potentially strange about this activity?
        It's a remarkably small amount of data with a remarkably small number of users that's achieving the highest unique visitors vs average bytes.
        
4. Filter the data by this event.
     - What is the timestamp for this event?
     2021-05-17 12pm
     - What kind of file was downloaded?
     rpm and zip files
     - From what country did this activity originate?
     China, USA, and India
     - What HTTP response codes were encountered by this visitor?
        200
        
5. Switch to the Kibana Discover page to see more details about this activity.
     - What is the source IP address of this activity?
     - What are the geo coordinates of this activity?
     - What OS was the source machine running?
     - What is the full URL that was accessed?
     - From what website did the visitor's traffic originate?

| Source IP       | Geo Coordinates                            | OS    | URL access           | Origin Website                              |
|-----------------|--------------------------------------------|-------|----------------------|---------------------------------------------|
| 223.112.248.233 | CN "lat": 37.85008167, "lon": -83.84575194 | Linux | www.elastic.co       | http://nytimes.com/warning/georgi-beregovoi |
| 73.105.236.24   | US "lat": 42.99821222, "lon": -74.32955111 | Linux | artifacts.elastic.co | http://twitter.com/success/maksim-surayev   |
| 35.143.166.159  | IN  "lat": 43.34121,   "lon": -73.6103075  | Linux | artifacts.elastic.co | http://facebook.com/success/jay-c-buckey    |
	
6. Finish your investigation with a short overview of your insights. 

     - What do you think the user was doing?
     - Was the file they downloaded malicious? If not, what is the file used for?
     - Is there anything that seems suspicious about this activity?
     - Is any of the traffic you inspected potentially outside of compliance guidlines?

---
© 2020 Trilogy Education Services, a 2U, Inc. brand. All Rights Reserved.  
