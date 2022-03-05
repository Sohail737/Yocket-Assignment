#Events APIs

##Endpoints
1. GET /events

    query params : 
    type: live | all | upcomming
    currentTime: current time in format "YYYY-MM-DD HH:mm:ss"

    response :{
        "success":true,
        "data":[
            {
                "name":string,
                "startTime":string,
                "duration:int,
                "createdAt":string,
                "updatedAt":string
            }
        ]
    }

    This endpoint get list of events

    1. All Events - Get all events by passing type=all
    eg: /events?type=all

    2. Upcomming events - Get list of all upcomming events by passing type=all and currentTime=YYYY-MM-DD HH:mm:ss
    eg: /events?type=upcomming&currentTime=2022-03-05 17:00:00

    3. Live events - Get list of live events by passing type=live and currentTime=YYYY-MM-DD HH:mm:ss
    Live events are only accessible before 10 min of their startTime and till before duration of event.
    A live event on 2022-03-05 17:00:00 for duration 60 mins is only accessible from 2022-03-05 16:50:00 to 2022-03-05 18:00:00
    eg: /events?type=live&currentTime=2022-03-05 17:00:00

2. GET /events/:id

    path params: 
    id: string

    response :{
        "success":true,
        "data":[
            {
                "name":string,
                "startTime":string,
                "duration:int,
                "createdAt":string,
                "updatedAt":string
            }
        ]
    }

    This endpoint gets a single event
    eg: /events/2

3. POST /events

    req body:{
        "name":string,
        "startTime":string,
        "duration":int
    }

    res: {
        "success": boolean,
        "data": {
            "id": int,
            "name": string,
            "startTime": string,
            "duration": int,
            "updatedAt": string,
            "createdAt": string
        }
    }

    eg. /events

    body:{
        "name":"Event99",
        "startTime":"2022-03-05 11:00:00",
        "duration":30
    }   

4. PUT /events/:id

    path params:
    id:string

    req body: {
        "name":string,
        "startTime":string,
        "duration":int
    }

    res:{
        "success": boolean,
        "data": {
            "id": int,
            "name": string,
            "startTime": string,
            "duration": int,
            "updatedAt": string,
            "createdAt": string
        }
    }

    eg: /events/2
    req body: {
        "name":string,
        "startTime":string,
        "duration":int
    }

5. DELETE /events/:id

    path params:
    id:string

    res: "record deleted successfully"

    eg: /events/2






