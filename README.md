# A Simple CRuD Blog with Streamlit

This project was built manually from code found at https://github.com/SummittDweller/Streamlit_DataScience_Apps/tree/master/Simple_CRuD_Blog_App_with_Streamlit.  Since that subdirectory is NOT a GitHub repo it could not simply be "cloned".  

I'm unable to successfully install `pysqlite3` with my Python 3.11 version, so I'm attempting to run without that just using the built-in `sqlite3` package.  Thus far I get the following results...

| Command | Outcome |
| ---     | ---     |
| `streamlit hello` | Produces the expected sample Streamlit app with no apparent errors. |
| `streamlit run app.py` | Produces a local browser window reporting the ModuleNotFoundError below. |
| `streamlit run blog_app\(unrefactored\).py` | Produces a local browser window reporting the OperationlError below. |


```
ModuleNotFoundError: No module named 'wordcloud'
Traceback:

File "/Users/mark/GitHub/simple-CRuD-blog-app-with-streamlit/.venv/lib/python3.11/site-packages/streamlit/runtime/scriptrunner/script_runner.py", line 552, in _run_script
    exec(code, module.__dict__)
File "/Users/mark/GitHub/simple-CRuD-blog-app-with-streamlit/app.py", line 12, in <module>
    from wordcloud import WordCloud, STOPWORDS, ImageColorGenerator
```

```
OperationalError: no such table: blogtable
Traceback:

File "/Users/mark/GitHub/simple-CRuD-blog-app-with-streamlit/.venv/lib/python3.11/site-packages/streamlit/runtime/scriptrunner/script_runner.py", line 552, in _run_script
    exec(code, module.__dict__)
File "/Users/mark/GitHub/simple-CRuD-blog-app-with-streamlit/blog_app(unrefactored).py", line 209, in <module>
    main()
File "/Users/mark/GitHub/simple-CRuD-blog-app-with-streamlit/blog_app(unrefactored).py", line 144, in main
    result = view_all_notes()
             ^^^^^^^^^^^^^^^^
File "/Users/mark/GitHub/simple-CRuD-blog-app-with-streamlit/blog_app(unrefactored).py", line 19, in view_all_notes
    c.execute('SELECT * FROM blogtable')
```

## Fixing the Database

The above **OperationlError** is perhaps due to the fact that I did NOT copy the project's _data.db_ file into this project.  Let's do that and try again...  **It Works!**  

## Next Step... Deploy and Test in the Cloud (Azure?)

This is a big step forward but before taking it farther I'm going to push what I have to GitHub then see about deploying this to the cloud for testing, I'd love to see how it looks and behaves on a mobile device.  I'll probably be looking to Mackenzie and maybe the [Beginner Guide to Streamlit Deployment on Azure](https://towardsdatascience.com/beginner-guide-to-streamlit-deployment-on-azure-f6618eee1ba9) post.  

---

| Attention! |
| ---        |
| All that follows is from the ORIGINAL README.md file. |

### A Simple CRuD Blog with Streamlit

#### Requirements
+ streamlit
+ sqlite3

#### NB: Most of the design for the UI is with
+ html and css
+ st.markdown()


#### Screenshots
+ Home
![](stblog_jcharistech01.png)


![](stblog_jcharistech03.png)

![](stblog_jcharistech04.png)


![](stblog_jcharistech08.png)


#### Limits
+ No login/logout/signup option
+ Clearing of entry input
+ Edit and Update


#### .
+ Thanks for your time
+ Jesus Saves @JCharisTech
+ Jesse E.Agbe(JCharis)