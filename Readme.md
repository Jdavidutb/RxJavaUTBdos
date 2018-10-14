# Programacion Reactiva (RxJava) 


Teniendo en cuenta las indicaciones de requirimientos de la profesora, se procede a realiar un proyecto, el cual consiste como 
principal objetico, aplicar el uso de programacion reactiva para acceso a una base de datos de libros 

para el proyecto se toma como lenguaje de programacion Java y se trabaja en entorno android con su aeditor adroit estudio

nuestra fuente se trata de una API tomada como json, que nos proporciona la informacion de los libros.

se utiliza la libreria Rxandroid y el metodo retrofit para abtener los datos
Nuestra API se tomada desde una generador de basos de datos en linea llamado firebase , la cuel nos proporciona los recursos

public class RestClient {

    protected interface HNService {

        @GET("/item/{itemId}.json")
        public Observable<HNItem> getItem(@Path("itemId") String Articulo);

        @GET("/newstories.json")

        public Observable<nuevosLibros> getLibros();
    }

    private static HNService hnService;

    public static HNService getHNService() {
        if (RestClient.hnService == null) {
            RestAdapter retrofit = new RestAdapter.Builder()
                    .setEndpoint("https://hacker-news.firebaseio.com/v0")
                    .build();

            RestClient.hnService = retrofit.create(HNService.class);
        }

        return RestClient.hnService;
        
        
    }
    Este es nuestro metodo principal donde se solicita los datos de las revistas a la API rest

