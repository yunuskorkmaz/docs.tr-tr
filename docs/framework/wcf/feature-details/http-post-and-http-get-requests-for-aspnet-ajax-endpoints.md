---
title: 'Nasıl yapılır: ASP.NET AJAX Uç Noktaları için HTTP POST ve HTTP GET İstekleri Arasında Seçim Yapma'
ms.date: 03/30/2017
ms.assetid: b47de82a-4c92-4af6-bceb-a5cb8bb8ede9
ms.openlocfilehash: 0f7a221d1fd14b4a978683f008858e35cbd2df19
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184751"
---
# <a name="how-to-choose-between-http-post-and-http-get-requests-for-aspnet-ajax-endpoints"></a><span data-ttu-id="b5d16-102">Nasıl yapılır: ASP.NET AJAX Uç Noktaları için HTTP POST ve HTTP GET İstekleri Arasında Seçim Yapma</span><span class="sxs-lookup"><span data-stu-id="b5d16-102">How to: Choose between HTTP POST and HTTP GET requests for ASP.NET AJAX Endpoints</span></span>

<span data-ttu-id="b5d16-103">Windows Communication Foundation (WCF), istemci Web sitesinde JavaScript'ten çağrılabilen AJAX özellikli ASP.NET bir bitiş noktasını ortaya çıkaran bir hizmet oluşturmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="b5d16-103">Windows Communication Foundation (WCF) allows you to create a service that exposes an ASP.NET AJAX-enabled endpoint that can be called from JavaScript on a client Web site.</span></span> <span data-ttu-id="b5d16-104">Bu tür hizmetleri oluşturmak için temel yordamlar [nasıl tartışılır: ASP.NET bir AJAX Bitiş Noktası Eklemek için Yapılandırmayı Kullanın](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md) ve Nasıl [Yapılır: Yapılandırmayı Kullanmadan ASP.NET bir AJAX Bitiş Noktası Ekleyin.](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="b5d16-104">The basic procedures for building such services is discussed in [How to: Use Configuration to Add an ASP.NET AJAX Endpoint](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md) and [How to: Add an ASP.NET AJAX Endpoint Without Using Configuration](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).</span></span>  
  
 <span data-ttu-id="b5d16-105">ASP.NET AJAX, HTTP POST ve HTTP GET fiillerini kullanan işlemleri destekler ve http post varsayılan dır.</span><span class="sxs-lookup"><span data-stu-id="b5d16-105">ASP.NET AJAX supports operations that use the HTTP POST and HTTP GET verbs, with HTTP POST being the default.</span></span> <span data-ttu-id="b5d16-106">Hiçbir yan etkisi olmayan ve nadiren veya hiç değişmeyen verileri döndüren bir işlem oluştururken, bunun yerine HTTP GET'i kullanın.</span><span class="sxs-lookup"><span data-stu-id="b5d16-106">When creating an operation that has no side effects and returns data that rarely or never changes, use HTTP GET instead.</span></span> <span data-ttu-id="b5d16-107">GET işlemlerinin sonuçları önbelleğe alınabilir, bu da aynı işlemi birden çok aramanın hizmetinize yalnızca bir istekle sonuçlanabileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="b5d16-107">Results of GET operations can be cached, which means that multiple calls to the same operation may result in only one request to your service.</span></span> <span data-ttu-id="b5d16-108">Önbelleğe alma WCF tarafından yapılmaz, ancak herhangi bir düzeyde (kullanıcının tarayıcısında, proxy sunucusunda ve diğer düzeylerde) gerçekleşebilir. Hizmet performansını artırmak istiyorsanız önbelleğe alma avantajlıdır, ancak veriler sık sık değişirse veya işlem bazı eylemlergerçekleştirirse kabul edilebilir olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="b5d16-108">The caching is not done by WCF but can take place at any level (in a user's browser, on a proxy server, and other levels.) Caching is advantageous if you want to increase service performance, but may not be acceptable if data changes frequently or if the operation performs some action.</span></span>  
  
 <span data-ttu-id="b5d16-109">Örneğin, bir kullanıcının müzik kitaplığını yönetmek için hizmet tasarlıyorsanız, bir albümün başlığına göre sanatçıyı arayan bir işlem GET'i kullanmanın avantajlarından yararlanır, ancak kullanıcının kişisel koleksiyonuna albüm ekleyen bir işlem POST'u kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b5d16-109">For example, if you are designing service to manage a user's music library, an operation that looks up the artist based on an album's title benefits from using GET, but an operation that adds an album to the user's personal collection must use POST.</span></span>  
  
 <span data-ttu-id="b5d16-110">Önbelleğin kullanım ömrünü denetlemek <xref:System.ServiceModel.Web.OutgoingWebResponseContext> için türü kullanın.</span><span class="sxs-lookup"><span data-stu-id="b5d16-110">To control the lifetime of the cache, use the <xref:System.ServiceModel.Web.OutgoingWebResponseContext> type.</span></span> <span data-ttu-id="b5d16-111">Örneğin, hava durumu tahminlerini saatlik olarak güncelleştiren bir hizmet tasarlarken, HIZMET kullanıcılarının eski verilere erişmesini önlemek için GET'i ancak önbellek süresini bir saat veya daha az ile sınırlandırırsınız.</span><span class="sxs-lookup"><span data-stu-id="b5d16-111">For example, when designing a service that returns weather forecasts updated hourly, you would use GET but limit the cache duration to an hour or less to prevent the users of the service from accessing stale data.</span></span>  
  
 <span data-ttu-id="b5d16-112">Komut Dosyası Yöneticisi denetimini kullanan ASP.NET bir AJAX sayfasından gelen hizmetleri kullanırken, işlemin GET veya POST'u kullanıp kullanmadığı fark etmez - komut dosyası yöneticisi mekanizması doğru istek türünün verilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="b5d16-112">When using services from an ASP.NET AJAX page that use the Script Manager control, it makes no difference whether the operation uses GET or POST - the script manager mechanism ensures that the correct request type is issued.</span></span>  
  
 <span data-ttu-id="b5d16-113">HTTP GET işlemleri, karmaşık veri sözleşmesi türleri de dahil olmak üzere POST işlemleri tarafından desteklenen tüm giriş parametrelerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="b5d16-113">HTTP GET operations use any input parameters supported by POST operations, including complex data contract types.</span></span> <span data-ttu-id="b5d16-114">Ancak, çoğu durumda önbelleğe alma verimliliğini azalttığı için GET işlemlerinde çok karmaşık olan çok fazla parametre veya parametreden kaçınmak önerilir.</span><span class="sxs-lookup"><span data-stu-id="b5d16-114">However, in most cases it is recommended to avoid too many parameters or parameters that are too complex in GET operations because it reduces caching efficiency.</span></span>  
  
 <span data-ttu-id="b5d16-115">Bu konu, hizmet sözleşmesindeki ilgili işlemlere <xref:System.ServiceModel.Web.WebGetAttribute> <xref:System.ServiceModel.Web.WebInvokeAttribute> veya öznitelikleri ekleyerek GET ve POST arasında nasıl seçim yapılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b5d16-115">This topic demonstrates how to select between GET and POST by adding the <xref:System.ServiceModel.Web.WebGetAttribute> or <xref:System.ServiceModel.Web.WebInvokeAttribute> attributes to the relevant operations in the service contract.</span></span> <span data-ttu-id="b5d16-116">Hizmeti çalıştırmak için gereken diğer adımlar (hizmeti uygulamak, yapılandırmak ve barındırmak için), WCF'deki herhangi bir ASP.NET AJAX hizmeti tarafından kullanılanlara benzer.</span><span class="sxs-lookup"><span data-stu-id="b5d16-116">The other steps (to implement, configure and host the service) that are required to get the service running are similar to those used by any ASP.NET AJAX service in WCF.</span></span>  
  
 <span data-ttu-id="b5d16-117"><xref:System.ServiceModel.Web.WebGetAttribute> Her zaman GET isteği yle işaretlenmiş bir işlem kullanır.</span><span class="sxs-lookup"><span data-stu-id="b5d16-117">An operation marked with the <xref:System.ServiceModel.Web.WebGetAttribute> always uses a GET request.</span></span> <span data-ttu-id="b5d16-118"><xref:System.ServiceModel.Web.WebInvokeAttribute>'ile işaretlenmiş veya iki özetmenle işaretlenmemiş bir işlem, bir POST isteği kullanır.</span><span class="sxs-lookup"><span data-stu-id="b5d16-118">An operation marked with the <xref:System.ServiceModel.Web.WebInvokeAttribute>, or not marked with any of the two attributes, uses a POST request.</span></span> <span data-ttu-id="b5d16-119">Özellik <xref:System.ServiceModel.Web.WebInvokeAttribute> aracılığıyla <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> GET ve POST (PUT ve DELETE gibi) dışındaki diğer HTTP fiillerinin kullanımına izin verir.</span><span class="sxs-lookup"><span data-stu-id="b5d16-119">The <xref:System.ServiceModel.Web.WebInvokeAttribute> allows the use of other HTTP verbs, other than GET and POST (such as PUT and DELETE) through the <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> property.</span></span> <span data-ttu-id="b5d16-120">Ancak bu fiiller ASP.NET AJAX tarafından desteklenmemektedir.</span><span class="sxs-lookup"><span data-stu-id="b5d16-120">However, these verbs are not supported by ASP.NET AJAX.</span></span> <span data-ttu-id="b5d16-121">Komut Dosyası Yöneticisi denetimini kullanarak ASP.NET sayfadaki hizmeti kullanmak <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> istiyorsanız, özelliği kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="b5d16-121">If you intend to use the service from ASP.NET pages using the Script Manager control, do not use the <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> property.</span></span>  
  
 <span data-ttu-id="b5d16-122">GET'e geçiş için çalışan bir örnek için [Temel AJAX Hizmeti](../../../../docs/framework/wcf/samples/basic-ajax-service.md) örneğine bakın.</span><span class="sxs-lookup"><span data-stu-id="b5d16-122">For a working example of switching to GET, see the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md) sample.</span></span>  
  
 <span data-ttu-id="b5d16-123">POST kullanan bir örnek [için, HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md) örneğini kullanarak AJAX Hizmeti'ne bakın.</span><span class="sxs-lookup"><span data-stu-id="b5d16-123">For a sample that uses POST, see the [AJAX Service Using HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md) sample.</span></span>  
  
## <a name="to-create-a-wcf-service-that-responds-to-http-get-or-http-post-requests"></a><span data-ttu-id="b5d16-124">HTTP GET veya HTTP POST isteklerine yanıt veren bir WCF hizmeti oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="b5d16-124">To create a WCF service that responds to HTTP GET or HTTP POST requests</span></span>
  
1. <span data-ttu-id="b5d16-125">Öznitelik ile işaretlenmiş bir arabirim ile <xref:System.ServiceModel.ServiceContractAttribute> temel bir WCF hizmet sözleşmesi tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="b5d16-125">Define a basic WCF service contract with an interface marked with the <xref:System.ServiceModel.ServiceContractAttribute> attribute.</span></span> <span data-ttu-id="b5d16-126">Her işlemi <xref:System.ServiceModel.OperationContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="b5d16-126">Mark each operation with the <xref:System.ServiceModel.OperationContractAttribute>.</span></span> <span data-ttu-id="b5d16-127"><xref:System.ServiceModel.Web.WebGetAttribute> Bir işlemin HTTP GET isteklerine yanıt vermesi gerektiğini şart koşturacak özniteliği ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b5d16-127">Add the <xref:System.ServiceModel.Web.WebGetAttribute> attribute to stipulate that an operation should respond to HTTP GET requests.</span></span> <span data-ttu-id="b5d16-128">Ayrıca, HTTP <xref:System.ServiceModel.Web.WebInvokeAttribute> POST'u açıkça belirtmek için öznitelik ekleyebilir veya HTTP POST varsayılan bir öznitelik belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="b5d16-128">You can also add the <xref:System.ServiceModel.Web.WebInvokeAttribute> attribute to explicitly specify HTTP POST, or not specify an attribute, which defaults to HTTP POST.</span></span>
  
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
  
2. <span data-ttu-id="b5d16-129">Bir `IMusicService` `MusicService`ile hizmet sözleşmesi uygulayın.</span><span class="sxs-lookup"><span data-stu-id="b5d16-129">Implement the `IMusicService` service contract with a `MusicService`.</span></span>
  
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
  
3. <span data-ttu-id="b5d16-130">Uygulamada .svc uzantısı bulunan hizmet adlı yeni bir dosya oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b5d16-130">Create a new file named service with a .svc extension in the application.</span></span> <span data-ttu-id="b5d16-131">Hizmet için uygun [ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) yönergesi bilgilerini ekleyerek bu dosyayı düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="b5d16-131">Edit this file by adding the appropriate [\@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive information for the service.</span></span> <span data-ttu-id="b5d16-132"><xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> ASP.NET bir AJAX bitiş noktasını otomatik olarak yapılandırmak için [ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) yönergesinde kullanılacağını belirtin.</span><span class="sxs-lookup"><span data-stu-id="b5d16-132">Specify that the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> is to be used in the [\@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive to automatically configure an ASP.NET AJAX endpoint.</span></span>  
  
    ```
    <%@ServiceHost
        language=c#
        Debug="true"
        Service="Microsoft.Ajax.Samples.MusicService"  
        Factory=System.ServiceModel.Activation.WebScriptServiceHostFactory  
    %>  
    ```  
  
## <a name="to-call-the-service"></a><span data-ttu-id="b5d16-133">Hizmeti aramak için</span><span class="sxs-lookup"><span data-stu-id="b5d16-133">To call the service</span></span>  
  
1. <span data-ttu-id="b5d16-134">Tarayıcıyı kullanarak hizmetinizin GET işlemlerini herhangi bir istemci kodu olmadan test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b5d16-134">You can test your service's GET operations without any client code, by using the browser.</span></span> <span data-ttu-id="b5d16-135">Örneğin, hizmetiniz `http://example.com/service.svc` adreste yapılandırılırsa, `http://example.com/service.svc/LookUpArtist?album=SomeAlbum` tarayıcı adresi çubuğuna yazmak hizmeti çağırır ve yanıtın indirilmesine veya görüntülenmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="b5d16-135">For example, if your service is configured at the `http://example.com/service.svc` address, then typing `http://example.com/service.svc/LookUpArtist?album=SomeAlbum` into the browser address bar invokes the service and causes the response to be downloaded or displayed.</span></span>
  
2. <span data-ttu-id="b5d16-136">GET işlemlerindeki hizmetleri, ASP.NET AJAX Script Manager denetiminin Scripts koleksiyonuna hizmet URL'sini girerek, diğer ASP.NET AJAX hizmetleriyle aynı şekilde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b5d16-136">You can use services with GET operations in the same way as any other ASP.NET AJAX services - by entering the service URL into the Scripts collection of the ASP.NET AJAX Script Manager control.</span></span> <span data-ttu-id="b5d16-137">Örneğin, [Temel AJAX Hizmeti'ne](../../../../docs/framework/wcf/samples/basic-ajax-service.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="b5d16-137">For an example, see the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="b5d16-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b5d16-138">See also</span></span>

- [<span data-ttu-id="b5d16-139">ASP.NET AJAX için WCF Hizmetleri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="b5d16-139">Creating WCF Services for ASP.NET AJAX</span></span>](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)
- [<span data-ttu-id="b5d16-140">Nasıl yapılır: AJAX Etkinleştirilmiş ASP.NET Web Hizmetlerini WCF'ye Taşıma</span><span class="sxs-lookup"><span data-stu-id="b5d16-140">How to: Migrate AJAX-Enabled ASP.NET Web Services to WCF</span></span>](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
