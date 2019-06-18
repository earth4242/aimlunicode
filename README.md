# AIMLUnicode.js
AIMLUnicode is a module that allows you to parse AIML files and to find the correct answer to a given message (support non-English language)

**Installation**
```
$ npm install aimlunicode
```

**Dependencies**
```
fs
dom-js
```

**Description**<br />
AIMLUnicode for Node.js which supports non-English language (now it is only Thai) based on aimlinterpreter and aimlparser. This is the upgrade version of aimlparser. There are some bugs appeared in the latest version of AIMLIntepreter and AIMLParser but already fixed in this npm package.

**Latest AIMLIntepreter and AIMLParser bugs:**<br />
AIMLIntepreter appears a bug in *condition* AIML tag.
AIMLParser appears a bug in non-English Language Reading.
<br />

About **aimlinterpreter**
- https://www.npmjs.com/package/aimlinterpreter
- https://github.com/raethlein/AIML.js

About **aimlparser**
- https://www.npmjs.com/package/aimlaimlparser
- https://github.com/ingkwanv/aimlparser
<br />

**Example XML File:**
```
<?xml version="1.0" encoding="UTF-8"?>
<aiml version="2.0">
    <category>
        <pattern>สวัสดี</pattern>
        <template>สบายดีไหม</template>
    </category>

    <category>
        <pattern>Hello</pattern>
        <template>How Are You</template>
    </category>
</aiml>
```

**Example JS File:**
```
AIMLUnicode = require('./AIMLUnicode');
var aimlUnicode = new AIMLUnicode({name:'AIMLUnicode', age:'21'});
AIMLUnicode.loadAIMlFile(['./test.aiml.xml']);

var callback = function(answer, wildCardArray, input){
    console.log(answer + ' | ' + wildCardArray + ' | ' + input);
};

AIMLUnicode.findAnswer('What is your name?', callback);
AIMLUnicode.findAnswer('My name is Zeno.', callback);
AIMLUnicode.findAnswer('What is my name?', callback);
```

**Supported AIML tags:**
```
<bot name="NAME"/>
<get name="NAME"/>
<set name="NAME">TEXT</set>
<random><li>A</li><li>B</li><li>C</li></random>
<srai>PATTERN TEXT</srai>
<sr/>
<star/>
<that>TEXT</that>
<condition name="NAME" value="VALUE">TEXT</condition>
<condition><li name="NAME" value="VALUE">TEXT</li><li name="NAME" value="VALUE">TEXT</li><li>TEXT</li></condition>
<condition name="NAME"><li value="VALUE">TEXT</li><li value="VALUE">TEXT</li><li>TEXT</li></condition>
```