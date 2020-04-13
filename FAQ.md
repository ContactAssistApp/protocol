# FAQ

1. Should there only be one Area for one User Message?

    Match Message has the following structure:

    + MatchMessage *contains* AreaMatch[]
    + AreaMatch *contains* (Area[], UserMessage)



    A) MatchMessage contains many 'Area Matches' and 'Bluetooth Matches'.  The intention with  MatchMessage is that batches several match messages.  A single 'Area Match' message applies to many areas.  For example a health worker that does contact tracing finds many areas that are of interest in relation to a single contact trace.  This becomes one match message with a single AreaMatch.

2. Polling for bluetooth matches also supposed to yeild narrow-cast messages?

   A)  Yes.  This is my understanding of what is needed.  The message design reflects that.  For example if the app is deployed globally, narrow-casting would mean that a phone only recieves bluetooth matches in the coarse region around the phone.

3. GetMessages flow it is a bit confusing because a user_message exists in both the AreaMatch and the BluetoothMatch.  Should there be only one?  user_message in AreaMatch to be narrowcasted messages while the user_message in BluetoothMatch would be for exposure notifications?

    A) Earlier answer also applies here.  The intention with MatchMessage is to batch a number of "Area Matches" and "Bluetooth Matches" along with their relevant user messages.  For example in some cases, the advise to the user might be "Self quarantine and watch symptoms for 5 days".  In other cases, it might be "Seek immediate help".

    [Example of usage](https://github.com/TraceDefenseCollab/ClientMessageMatch/blob/3a1ce14ee8401c96ab1e15211546cb9cb1edae8f/js/buildScripts/srcServer.js#L77)