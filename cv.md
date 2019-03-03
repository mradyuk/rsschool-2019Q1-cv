
## Maria Radziuk

### Software engeneer 

#### Areas of Expertise
***

Processes\Methodologies:	**ITIL, Agile, TDD**

Programming languages:  **Java, JavaScript**

Database:  **MongoDB, MySql**

Build tools: **Maven**

Testing: **JUnit, Selenium**


Languages:   
* **Belarussian, Russian** - native  
* **English** – B2 (certified by Streamline language school)  
* **Polish**- B1 (certified by language school)  

#### Education & Certificates
***

|Year  | Course|
-------|-------------------------------------------------------------------

2013 | BSUR - Major 'Information technologies and networks in economics' 
-------|-------------------------------------------------------------------

2015 | BSUIR - Master 'Computer science' 
-------|-------------------------------------------------------------------

2015 | ITIL v3 Foundation certificate 
-------|-------------------------------------------------------------------

2016 | Coursera - Programming mobile applications for Android handheld systems (with Statement of Accomplishment)
-------|-------------------------------------------------------------------

2016 | MongoDB for DBAs & MongoDB for Java Developers (with Statement of Accomplishment)
-------|-------------------------------------------------------------------

2018 | Android Academy Minsk - Android Fundamentals
-------|-------------------------------------------------------------------

#### Work Experience
***

1. Project description: Custom sophisticated simulations to businesses.  
Position:  Remote part-time developer in testing  
Responsibilities:   
* Building a suite of API tests and Selenium regression tests to cover existing functionality.  
Technologies:  **Java, JUnit, Selenium, Maven, Eclipse**  


2. Project description: Idm customization and self-service interface for identity and access management.  
Position:  Developer  
Responsibilities:   
* Developing a front-end based on JSF (page templates, custom components, localization) and JQuery technologies.  
* Developing  business logic based on transactions with Tivoli IdM (Using ITIM Webservices Wrapper by IBM).  
* Covering functionality with unit tests and automated test scripts.  
* Collecting and analyzing requirements in constant interaction with onsite team members.  
* Developing design/technical documentation for project modules.  
* Providing support for new team members, managing micro-team.  
Technologies:  **Java, JSF, Hibernate, JQuery, HTML/CSS,TestNg, JUnit, Maven, Tivoli IdM, Websphere, Ldap**  

#### Code examples
***

```java
public class MovieActivity extends AppCompatActivity {

    private MovieRecyclerAdapter movieRecyclerAdapter;

    static final String BASE_URL = "http://omdbapi.com";


    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_movie);

        RecyclerView list = findViewById(R.id.movieList);

        Display display = ((WindowManager) getSystemService(WINDOW_SERVICE))
                .getDefaultDisplay();

        int orientation = display.getRotation();

        RecyclerView.LayoutManager layoutManager;
        if (orientation == Surface.ROTATION_90    || orientation == Surface.ROTATION_270) {
            layoutManager = new GridLayoutManager(getApplicationContext(), 4);
        } else {
            layoutManager = new GridLayoutManager(getApplicationContext(), 2);
        }

        list.setLayoutManager(layoutManager);

        movieRecyclerAdapter = new MovieRecyclerAdapter(MovieActivity.this, new ArrayList<>());
        list.setAdapter(movieRecyclerAdapter);

        EditText key = (EditText) findViewById(R.id.key);
        Button searchBtn = (Button) findViewById(R.id.searchBtn);

        searchBtn.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {


                Retrofit retrofit = new Retrofit.Builder()
                        .baseUrl(BASE_URL)
                        .addConverterFactory(GsonConverterFactory.create())
                        .client(buildHttpClient())
                        .build();

                OMDBService service = retrofit.create(OMDBService.class);
                Call<OMDBResponse> call = service.getMovies(key.getText().toString(), "57430b23");

                call.enqueue(new Callback<OMDBResponse>() {
                    @Override
                    public void onResponse(Call<OMDBResponse> call, Response<OMDBResponse> response) {

                        if (!response.isSuccessful()) {
                            return;
                        }

                        OMDBResponse omdbresponse = response.body();

                        List<Movie> movies = omdbresponse.getSearch();

                        movieRecyclerAdapter.setItems(movies);

                    }

                    @Override
                    public void onFailure(Call<OMDBResponse> call, Throwable t) {
                        Log.e("MOVIESERVICE", "exception", t);
                    }
                });
            }
        });
    }

    private OkHttpClient buildHttpClient() {
        return new OkHttpClient.Builder().build();
    }
}
```

#### Contacts
***

Skype: mary.radziuk  
mail: mariaradyuk@gmail.com  
[Github](https://github.com/mradyuk?tab=repositories)  


