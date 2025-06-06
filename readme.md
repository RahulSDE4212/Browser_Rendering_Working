## **How Browser Rendering Works**
- Browser is a simple software that can load some files from your computer(HDD/SSD) or it can load some files 
  from a remote (something which is not present with you) server.
                        |
                        |
    Then browser figures out how to display your content.

- **How Browser compute how to display any file??**
    - Browsers have an engine that decides algorithmically how to display content.
    - `Browser engines:`  is a simple piece of software that understands what it can display and algorithmically decides how it can display.
        - Ex: Geko, Blink, Webkit.

### **HOW BROWSER LOADS THE FILES???**
- 
    ```
        html------->|--------------------
        css ------->|                   |
        javascript->|     BROWSER       |
                    |-------------------|
                                           -------------
                                           | Html file |
                                           -------------
                                               |
                 Browser read this html file   |
                 in the form of bytes          |
                                               |
                                  ------------------------------------
                                  | Bytes are converted to character |
                                  ------------------------------------
                                               |
                                Tokenization   | Tokenization means breaking string into multiple    
                                using a parcer | tokens using separator.
                                               | In html file separator is <></> 
                                               |
                                  -------------------------------------  
                                  |  Browser converts token into nodes |
                                  --------------------------------------
                                               |
                Nodes is an object present/    | Every nodes is considered distinct
                stores in memory               |  with distinct properties.
                                               |
                                -------------------------------------------
                                |    Represent nodes in the form of tree.  |
                                --------------------------------------------
                                               |
                                               |
                                               |
                                 -------------------------------------   
                                 |   Dom tree (Document Object Model) |
                                 --------------------------------------
    ```

- Dom tree 

    ```
                                        html
                                         |
                     --------------------|----------------------
                   title                                      body
                     |                                         |
             --------|---------                 ---------------|-----------------
             |                |                 |              |                |
            link            meta             header          main            footer
    ```

- Just like DOM Tree there is `CSSOM (CSS object Model) Tree`
- `CSSOM` is the tree data structure, prepared by web browser like DOM Tree.
- **HOW BROWSER LOADS CSS FILE**
    ```
                           ---------------   
                           |   css bytes |
                           ---------------
                                 |
                                 |
                      ---------------------------          
                      |  converted to character |
                      ---------------------------
                                 |
                                 |
                            -------------     
                            | Tokenizer |
                            -------------
                                 |
                                 |
                            ----------
                            |  Nodes |
                            ----------
                                 |
                                 |
                            ----------
                            |  CSSOM |
                            ----------
    ```

- Before we draw the **render tree** on the browser viewport, one more step is involved called `layout`(also called as **reflow step**).
  In this step, browser calculates the sizes, position and other metric for each element.

- `Painting` : Now the broswer starts painting element.

### **JAVASCRIPT WITH HTML IS A COSTLY AFFAIR**
- we use  `script tag` in HTML to add **javascript file** into it.

- `script tag` : This tag interact with HTML as well as CSS.

- Dom construction is paused when browser hits a script tag.
- 
    ```
     Script tag ----------------> DOM Construction halts
                |
                ----------------> What about CSSOM?
                                         |
                               In most engine, javascript is halted until CSSOM is constructed.
    ```

                                        
