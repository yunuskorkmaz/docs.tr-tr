---
title: 'Nasıl yapılır: ASP.NET AJAX Uç Noktaları için HTTP POST ve HTTP GET İstekleri Arasında Seçim Yapma'
ms.date: 03/30/2017
ms.assetid: b47de82a-4c92-4af6-bceb-a5cb8bb8ede9
ms.openlocfilehash: c74b1acdf3802ab680123cd9d676919fe47236e8
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: tr-TR
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051590"
---
# <a name="how-to-choose-between-http-post-and-http-get-requests-for-aspnet-ajax-endpoints"></a><span data-ttu-id="0ac28-102">Nasıl yapılır: ASP.NET AJAX Uç Noktaları için HTTP POST ve HTTP GET İstekleri Arasında Seçim Yapma</span><span class="sxs-lookup"><span data-stu-id="0ac28-102">How to: Choose between HTTP POST and HTTP GET requests for ASP.NET AJAX Endpoints</span></span>

<span data-ttu-id="0ac28-103">Windows Communication Foundation (WCF), istemci Web sitesinde JavaScript 'ten çağrılabilen ASP.NET AJAX özellikli bir uç nokta sunan bir hizmet oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="0ac28-103">Windows Communication Foundation (WCF) allows you to create a service that exposes an ASP.NET AJAX-enabled endpoint that can be called from JavaScript on a client Web site.</span></span> <span data-ttu-id="0ac28-104">Bu tür hizmetleri oluşturmaya yönelik temel yordamlar, [nasıl yapılır: ASP.NET AJAX uç noktası eklemek Için yapılandırma kullanma](how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md) ve [nasıl yapılır: yapılandırma kullanmadan ASP.NET AJAX uç noktası ekleme](how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md)konusunda ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="0ac28-104">The basic procedures for building such services is discussed in [How to: Use Configuration to Add an ASP.NET AJAX Endpoint](how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md) and [How to: Add an ASP.NET AJAX Endpoint Without Using Configuration](how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).</span></span>  
  
 <span data-ttu-id="0ac28-105">ASP.NET AJAX, HTTP POST ve HTTP GET fiillerini kullanan işlemleri destekler, varsayılan olarak HTTP POST.</span><span class="sxs-lookup"><span data-stu-id="0ac28-105">ASP.NET AJAX supports operations that use the HTTP POST and HTTP GET verbs, with HTTP POST being the default.</span></span> <span data-ttu-id="0ac28-106">Yan etkileri olmayan ve nadiren veya hiç değişmesiz verileri döndüren bir işlem oluştururken bunun yerine HTTP GET kullanın.</span><span class="sxs-lookup"><span data-stu-id="0ac28-106">When creating an operation that has no side effects and returns data that rarely or never changes, use HTTP GET instead.</span></span> <span data-ttu-id="0ac28-107">ALMA işlemlerinin sonuçları önbelleğe alınabilir. Bu, aynı işleme yapılan birden çok çağrının hizmetinize yalnızca bir istek oluşmasına neden olabileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="0ac28-107">Results of GET operations can be cached, which means that multiple calls to the same operation may result in only one request to your service.</span></span> <span data-ttu-id="0ac28-108">Önbelleğe alma, WCF tarafından yapılmaz, ancak herhangi bir düzeyde (bir kullanıcının tarayıcısında, bir ara sunucuda ve diğer düzeylerde) gerçekleşebilir. Hizmet performansını artırmak istiyorsanız önbelleğe alma avantajlıdır, ancak veriler sık sık değişirse veya işlem bazı eylemler gerçekleştirdiğinde kabul edilebilir olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="0ac28-108">The caching is not done by WCF but can take place at any level (in a user's browser, on a proxy server, and other levels.) Caching is advantageous if you want to increase service performance, but may not be acceptable if data changes frequently or if the operation performs some action.</span></span>  
  
 <span data-ttu-id="0ac28-109">Örneğin, bir kullanıcının müzik kitaplığını yönetmek için hizmet tasarlıyorsanız, sanatçı 'yı kullanarak bir albümün başlık avantajına bağlı olarak sanatçıların bulunduğu bir işlem, ancak kullanıcının kişisel koleksiyonuna bir albüm ekleyen bir işlemin POST kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="0ac28-109">For example, if you are designing service to manage a user's music library, an operation that looks up the artist based on an album's title benefits from using GET, but an operation that adds an album to the user's personal collection must use POST.</span></span>  
  
 <span data-ttu-id="0ac28-110">Önbelleğin ömrünü denetlemek için <xref:System.ServiceModel.Web.OutgoingWebResponseContext> türü kullanın.</span><span class="sxs-lookup"><span data-stu-id="0ac28-110">To control the lifetime of the cache, use the <xref:System.ServiceModel.Web.OutgoingWebResponseContext> type.</span></span> <span data-ttu-id="0ac28-111">Örneğin, hava durumu tahminlerini saat olarak güncelleştiren bir hizmet tasarlarken, hizmet kullanıcılarının eski verilere erişmesini engellemek için önbellek süresini bir saat veya daha az olacak şekilde Al ' ı kullanın.</span><span class="sxs-lookup"><span data-stu-id="0ac28-111">For example, when designing a service that returns weather forecasts updated hourly, you would use GET but limit the cache duration to an hour or less to prevent the users of the service from accessing stale data.</span></span>  
  
 <span data-ttu-id="0ac28-112">Betik Yöneticisi denetimini kullanan bir ASP.NET AJAX sayfasından hizmetleri kullanırken, komut dosyası Yöneticisi mekanizması işlemin GET veya POST işlemini kullanıp kullanmadığını fark etmeksizin, doğru istek türünün verilmemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="0ac28-112">When using services from an ASP.NET AJAX page that use the Script Manager control, it makes no difference whether the operation uses GET or POST - the script manager mechanism ensures that the correct request type is issued.</span></span>  
  
 <span data-ttu-id="0ac28-113">HTTP GET işlemleri, karmaşık veri sözleşmesi türleri de dahil olmak üzere POST işlemleri tarafından desteklenen tüm giriş parametrelerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="0ac28-113">HTTP GET operations use any input parameters supported by POST operations, including complex data contract types.</span></span> <span data-ttu-id="0ac28-114">Ancak çoğu durumda, alma işlemleri için çok karmaşık olan çok fazla parametre veya parametre kullanmaktan kaçınmak, çünkü önbelleğe alma verimliliğini düşürür.</span><span class="sxs-lookup"><span data-stu-id="0ac28-114">However, in most cases it is recommended to avoid too many parameters or parameters that are too complex in GET operations because it reduces caching efficiency.</span></span>  
  
 <span data-ttu-id="0ac28-115">Bu konu başlığı altında, <xref:System.ServiceModel.Web.WebGetAttribute> <xref:System.ServiceModel.Web.WebInvokeAttribute> hizmet sözleşmesindeki ilgili işlemlere veya ÖZNITELIKLERINI ekleyerek al ve postala arasında nasıl seçim yapılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="0ac28-115">This topic demonstrates how to select between GET and POST by adding the <xref:System.ServiceModel.Web.WebGetAttribute> or <xref:System.ServiceModel.Web.WebInvokeAttribute> attributes to the relevant operations in the service contract.</span></span> <span data-ttu-id="0ac28-116">Hizmeti çalıştırmak için gerekli diğer adımlar (hizmeti uygulamak, yapılandırmak ve barındırmak), WCF 'de herhangi bir ASP.NET AJAX hizmeti tarafından kullanılanlarla benzerdir.</span><span class="sxs-lookup"><span data-stu-id="0ac28-116">The other steps (to implement, configure and host the service) that are required to get the service running are similar to those used by any ASP.NET AJAX service in WCF.</span></span>  
  
 <span data-ttu-id="0ac28-117">İle işaretlenen bir işlem, <xref:System.ServiceModel.Web.WebGetAttribute> her zaman BIR get isteği kullanır.</span><span class="sxs-lookup"><span data-stu-id="0ac28-117">An operation marked with the <xref:System.ServiceModel.Web.WebGetAttribute> always uses a GET request.</span></span> <span data-ttu-id="0ac28-118">Ya da iki özniteliği ile işaretlenmemiş bir işlem, <xref:System.ServiceModel.Web.WebInvokeAttribute> BIR post isteği kullanır.</span><span class="sxs-lookup"><span data-stu-id="0ac28-118">An operation marked with the <xref:System.ServiceModel.Web.WebInvokeAttribute>, or not marked with any of the two attributes, uses a POST request.</span></span> <span data-ttu-id="0ac28-119">, <xref:System.ServiceModel.Web.WebInvokeAttribute> Özelliği aracılığıyla al ve postala (put ve DELETE gibi) dışında DIĞER http fiillerinin kullanılmasına izin verir <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> .</span><span class="sxs-lookup"><span data-stu-id="0ac28-119">The <xref:System.ServiceModel.Web.WebInvokeAttribute> allows the use of other HTTP verbs, other than GET and POST (such as PUT and DELETE) through the <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> property.</span></span> <span data-ttu-id="0ac28-120">Ancak, bu fiiller ASP.NET AJAX tarafından desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="0ac28-120">However, these verbs are not supported by ASP.NET AJAX.</span></span> <span data-ttu-id="0ac28-121">Hizmeti betik Yöneticisi denetimini kullanarak ASP.NET sayfalarından kullanmayı düşünüyorsanız, <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> özelliğini kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="0ac28-121">If you intend to use the service from ASP.NET pages using the Script Manager control, do not use the <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> property.</span></span>  
  
 <span data-ttu-id="0ac28-122">GET 'e geçiş yapma örneği için bkz. [Temel AJAX Hizmeti](../samples/basic-ajax-service.md) örneği.</span><span class="sxs-lookup"><span data-stu-id="0ac28-122">For a working example of switching to GET, see the [Basic AJAX Service](../samples/basic-ajax-service.md) sample.</span></span>  
  
 <span data-ttu-id="0ac28-123">POST kullanan bir örnek için bkz. [http post örneği kullanılarak AJAX Hizmeti](../samples/ajax-service-using-http-post.md) .</span><span class="sxs-lookup"><span data-stu-id="0ac28-123">For a sample that uses POST, see the [AJAX Service Using HTTP POST](../samples/ajax-service-using-http-post.md) sample.</span></span>  
  
## <a name="to-create-a-wcf-service-that-responds-to-http-get-or-http-post-requests"></a><span data-ttu-id="0ac28-124">HTTP GET veya HTTP POST isteklerine yanıt veren bir WCF hizmeti oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="0ac28-124">To create a WCF service that responds to HTTP GET or HTTP POST requests</span></span>
  
1. <span data-ttu-id="0ac28-125">Özniteliği ile işaretlenmiş bir arabirimle birlikte temel bir WCF hizmeti sözleşmesi tanımlayın <xref:System.ServiceModel.ServiceContractAttribute> .</span><span class="sxs-lookup"><span data-stu-id="0ac28-125">Define a basic WCF service contract with an interface marked with the <xref:System.ServiceModel.ServiceContractAttribute> attribute.</span></span> <span data-ttu-id="0ac28-126">Her işlemi ile işaretleyin <xref:System.ServiceModel.OperationContractAttribute> .</span><span class="sxs-lookup"><span data-stu-id="0ac28-126">Mark each operation with the <xref:System.ServiceModel.OperationContractAttribute>.</span></span> <span data-ttu-id="0ac28-127"><xref:System.ServiceModel.Web.WebGetAttribute>Bir işlemin http get isteklerine yanıt vermesi gereken belirtmek özniteliğini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="0ac28-127">Add the <xref:System.ServiceModel.Web.WebGetAttribute> attribute to stipulate that an operation should respond to HTTP GET requests.</span></span> <span data-ttu-id="0ac28-128">Ayrıca, http post <xref:System.ServiceModel.Web.WebInvokeAttribute> ' ı varsayılan olarak belirtmek için özniteliğini veya bir özniteliği belirtmeyeceğinizi de ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0ac28-128">You can also add the <xref:System.ServiceModel.Web.WebInvokeAttribute> attribute to explicitly specify HTTP POST, or not specify an attribute, which defaults to HTTP POST.</span></span>
  
    ```csharp
    [ServiceContract]  
    public interface IMusicService  
    {  
        //This operation uses a GET method.  
        [OperationContract]  
        [WebGet]  
        string LookUpArtist(string album);  
  
        //This operation will use a POST method.  
        [OperationContract]  
        [WebInvoke]  
        void AddAlbum(string user, string album);  
  
        //This operation will use POST method by default  
        //since nothing else is explicitly specified.  
        [OperationContract]  
        string[] GetAlbums(string user);  
  
        //Other operations omitted…  
  
    }  
    ```  
  
2. <span data-ttu-id="0ac28-129">`IMusicService`Hizmet sözleşmesini bir ile uygulayın `MusicService` .</span><span class="sxs-lookup"><span data-stu-id="0ac28-129">Implement the `IMusicService` service contract with a `MusicService`.</span></span>
  
    ```csharp
    public class MusicService : IMusicService  
    {  
        public void AddAlbum(string user, string album)  
        {  
            //Add implementation here.  
        }  
  
         //Other operations omitted…  
    }  
    ```  
  
3. <span data-ttu-id="0ac28-130">Uygulamada. svc uzantısıyla yeni bir dosya adlı hizmet oluşturun.</span><span class="sxs-lookup"><span data-stu-id="0ac28-130">Create a new file named service with a .svc extension in the application.</span></span> <span data-ttu-id="0ac28-131">Hizmet için uygun [ \@ ServiceHost](../../configure-apps/file-schema/wcf-directive/servicehost.md) yönergesi bilgilerini ekleyerek bu dosyayı düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="0ac28-131">Edit this file by adding the appropriate [\@ServiceHost](../../configure-apps/file-schema/wcf-directive/servicehost.md) directive information for the service.</span></span> <span data-ttu-id="0ac28-132"><xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>ASP.NET AJAX uç noktasını otomatik olarak yapılandırmak için [ \@ ServiceHost](../../configure-apps/file-schema/wcf-directive/servicehost.md) yönergesinde kullanılacağını belirtin.</span><span class="sxs-lookup"><span data-stu-id="0ac28-132">Specify that the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> is to be used in the [\@ServiceHost](../../configure-apps/file-schema/wcf-directive/servicehost.md) directive to automatically configure an ASP.NET AJAX endpoint.</span></span>  
  
    ```aspx-csharp
    <%@ServiceHost
        language=c#
        Debug="true"
        Service="Microsoft.Ajax.Samples.MusicService"  
        Factory=System.ServiceModel.Activation.WebScriptServiceHostFactory  
    %>  
    ```  
  
## <a name="to-call-the-service"></a><span data-ttu-id="0ac28-133">Hizmeti çağırmak için</span><span class="sxs-lookup"><span data-stu-id="0ac28-133">To call the service</span></span>  
  
1. <span data-ttu-id="0ac28-134">Hizmetini, tarayıcıyı kullanarak, herhangi bir istemci kodu olmadan hizmetinizin Al işlemlerini test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0ac28-134">You can test your service's GET operations without any client code, by using the browser.</span></span> <span data-ttu-id="0ac28-135">Örneğin, hizmetiniz `http://example.com/service.svc` adreste yapılandırılmışsa, `http://example.com/service.svc/LookUpArtist?album=SomeAlbum` tarayıcı adres çubuğuna yazarak hizmeti çağırır ve yanıt İndirilme veya görüntülenmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="0ac28-135">For example, if your service is configured at the `http://example.com/service.svc` address, then typing `http://example.com/service.svc/LookUpArtist?album=SomeAlbum` into the browser address bar invokes the service and causes the response to be downloaded or displayed.</span></span>
  
2. <span data-ttu-id="0ac28-136">GET Operations ile hizmetleri diğer ASP.NET AJAX hizmetleriyle aynı şekilde kullanabilirsiniz. hizmet URL 'sini ASP.NET AJAX betik Yöneticisi denetiminin betikler koleksiyonuna girerek.</span><span class="sxs-lookup"><span data-stu-id="0ac28-136">You can use services with GET operations in the same way as any other ASP.NET AJAX services - by entering the service URL into the Scripts collection of the ASP.NET AJAX Script Manager control.</span></span> <span data-ttu-id="0ac28-137">Bir örnek için bkz. [Temel AJAX Hizmeti](../samples/basic-ajax-service.md).</span><span class="sxs-lookup"><span data-stu-id="0ac28-137">For an example, see the [Basic AJAX Service](../samples/basic-ajax-service.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="0ac28-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0ac28-138">See also</span></span>

- [<span data-ttu-id="0ac28-139">ASP.NET AJAX için WCF Hizmetleri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="0ac28-139">Creating WCF Services for ASP.NET AJAX</span></span>](creating-wcf-services-for-aspnet-ajax.md)
- [<span data-ttu-id="0ac28-140">Nasıl yapılır: AJAX Etkinleştirilmiş ASP.NET Web Hizmetlerini WCF'ye Taşıma</span><span class="sxs-lookup"><span data-stu-id="0ac28-140">How to: Migrate AJAX-Enabled ASP.NET Web Services to WCF</span></span>](how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
