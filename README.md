vuejs-ace-editor
====================


[![npm](https://img.shields.io/npm/v/vuejs-ace-editor)](https://www.npmjs.com/package/vuejs-ace-editor)


A packaging of [ace](https://ace.c9.io/)

Demo here: https://github.com/chairuosen/vue-ace-editor-demo/tree/vue2

## How to use

1. Install

    ```
    npm install vuejs-ace-editor
    ```
    
2. Require it in `components` of Vue options

    ```js
    import AceEditor from 'vuejs-ace-editor';
    export default {
        ...
        components: {
            AceEditor
        },
        ...
    }
    ```
 
3. Require the editor's mode/theme module in custom methods
    
    ```js
    export default {
        ...
        methods: {
            dataSumit() {
                //code here
            },
            editorInit: function () {
                require('brace/ext/language_tools') //language extension prerequsite...
                require('brace/mode/html')                
                require('brace/mode/javascript')    //language
                require('brace/mode/less')
                require('brace/theme/monokai')
                require('brace/snippets/javascript') //snippet
            }
        },
        ...
    }
    ```
    
4. Use the component in template

    ```html
    <AceEditor 
        v-model="content" 
        @init="editorInit" 
        lang="javascript" 
        theme="monokai" 
        width="100%" 
        height="200px"
        :options="{
            enableBasicAutocompletion: true,
            enableLiveAutocompletion: true,
            fontSize: 14,
            highlightActiveLine: true,
            enableSnippets: true,
            showLineNumbers: true,
            tabSize: 2,
            showPrintMargin: false,
            showGutter: true,
        }"
        :commands="[
            {
                name: 'save',
                bindKey: { win: 'Ctrl-s', mac: 'Command-s' },
                exec: dataSumit,
                readOnly: true,
            },
        ]"
        />
    ```
    
    prop `v-model`  is required
    
    prop `lang` and `theme` is same as [ace-editor's doc](https://github.com/ajaxorg/ace)
    
    prop `height` and `width` could be one of these:  `200`, `200px`, `50%`

    
