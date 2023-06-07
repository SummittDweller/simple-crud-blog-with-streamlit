# A Simple CRuD Blog with Streamlit

This project was built manually from code found at https://github.com/SummittDweller/Streamlit_DataScience_Apps/tree/master/Simple_CRuD_Blog_App_with_Streamlit.  Since that subdirectory is NOT a GitHub repo it could not simply be "cloned".  

## Building Locally

To build this project locally I suggest the following steps based on my [Proper Python](https://blog.summittdweller.com/proper-python/) approach.

```
cd ~/GitHub  
git clone https://github.com/SummittDweller/simple-CRuD-blog-with-streamlit.git  
cd simple-CRuD-blog-with-streamlit  
code .   # Everything below happens in the command window within VSCode  
python3 -m venv .venv  
source .venv/bin/activate  
pip install --upgrade pip  
pip3 install -r requirements.txt  
```

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

## Fixing the WordCloud Error

I wanted to see what the `app.py` script would do so I performed a `pip3 install wordcloud` after which the `streamlit run app.py` command is WORKING!  That app produces what looks like the same application as the `streamlit run blog_app\(unrefactored\).py` command.  

## Next Step... Deploy and Test in the Cloud (Azure?)

This is a big step forward but before taking it farther I'm going to push what I have to GitHub then see about deploying this to the cloud for testing, I'd love to see how it looks and behaves on a mobile device.  I'll probably be looking to Mackenzie and maybe the [Beginner Guide to Streamlit Deployment on Azure](https://towardsdatascience.com/beginner-guide-to-streamlit-deployment-on-azure-f6618eee1ba9) post.  

Whoa!  The guidance linked above uses _Conda_ for Python management and _Docker_ for building the app... IMHO that's wrong on both counts.  Let's try [Deploying Streamlit Applications with Azure App Services](https://benalexkeen.com/deploying-streamlit-applications-with-azure-app-services/) instead.  

Crap!  That looked like good guidance but using the Central US region no matter what else I select I get this...

```
{"code":"InvalidTemplateDeployment","details":[{"code":"ValidationForResourceFailed","message":"Validation failed for a resource. Check 'Error.Details[0]' for more information.","details":[{"code":"SubscriptionIsOverQuotaForSku","message":"This region has quota of 0 instances for your subscription. Try selecting different region or SKU."}]}],"message":"The template deployment 'Microsoft.Template-20230606215048' is not valid according to the validation procedure. The tracking id is '1956e93d-4d56-4f22-9a5e-7b1f0b6ef718'. See inner errors for details."}
```

And the explanation seems to be that Microsoft just doesn't provide Linux App Service in every region, and apparently none in the Central US.  8^(   Bummer.  

## Azure is NO GO, Let's Try DigitalOcean

Azure App Service failed miserably, so I went looking for a _DigitalOcean_ alternative, and found [SummittDweller/simple-crud-blog-app-with-streamlit](https://github.com/SummittDweller/simple-crud-blog-app-with-streamlit).  I'm going to try bringing some of Diego's repo parts into my mix to see what happens.  Wish me luck!  


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