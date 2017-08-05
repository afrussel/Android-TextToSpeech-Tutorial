# Android TextToSpeech Tutorial for more than 4000 characters

We'll develop a project with `TextToSpeech` class to speak out text. Generally `TextToSpeech` engine doesn't support more than 4000 characters text at a time.
But this project it will work fine for more than 4K characters.

Initialization the basic of `textToSpeech` object:

```java
textToSpeech = new TextToSpeech(this, new TextToSpeech.OnInitListener() {
    @Override
    public void onInit(int status) {
        if(status == TextToSpeech.SUCCESS){
            textToSpeech.setLanguage(Locale.ENGLISH);
            textToSpeech.setSpeechRate((float) 1.25); 
            //1.0 is normal. lower value decrease the speed and upper value increase
        }
    }
});
```

Now let's call `.speak()` method to listen the text:

```java
HashMap<String, String> map = new HashMap<>();
map.put(TextToSpeech.Engine.KEY_PARAM_UTTERANCE_ID, "speak");

for(int i=0; i<paragraphList.length; i++) {
    textToSpeech.speak(paragraphList[i], TextToSpeech.QUEUE_ADD, map);
    textToSpeech.playSilence(250, TextToSpeech.QUEUE_ADD, null);
}
```
Here `paragraphList` is an array of `String`. I split my long article into some chunks. `paragraphList` array contains all chunks of paragraph.
`TextToSpeech` engine speak them one by one.

For more understanding clone the project and run.
