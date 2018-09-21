---
title: 'Nasıl yapılır: ASP.NET AJAX Uç Noktaları için HTTP POST ve HTTP GET İstekleri Arasında Seçim Yapma'
ms.date: 03/30/2017
ms.assetid: b47de82a-4c92-4af6-bceb-a5cb8bb8ede9
ms.openlocfilehash: 5cebdf0bae937d84ec23ed97a5d2feca24fff473
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/20/2018
ms.locfileid: "46473057"
---
# <a name="how-to-choose-between-http-post-and-http-get-requests-for-aspnet-ajax-endpoints"></a><span data-ttu-id="da688-102">Nasıl yapılır: ASP.NET AJAX Uç Noktaları için HTTP POST ve HTTP GET İstekleri Arasında Seçim Yapma</span><span class="sxs-lookup"><span data-stu-id="da688-102">How to: Choose between HTTP POST and HTTP GET requests for ASP.NET AJAX Endpoints</span></span>

<span data-ttu-id="da688-103">Windows Communication Foundation (WCF), istemci Web sitesinde JavaScript'ten çağrılabilen bir ASP.NET AJAX etkinleştirilmiş bir uç nokta hizmetidir oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="da688-103">Windows Communication Foundation (WCF) allows you to create a service that exposes an ASP.NET AJAX-enabled endpoint that can be called from JavaScript on a client Web site.</span></span> <span data-ttu-id="da688-104">Bu hizmetler oluşturmaya yönelik temel yordamları ele alınmıştır [nasıl yapılır: ASP.NET AJAX uç noktası eklemek için yapılandırma kullan](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md) ve [nasıl yapılır: bir ASP.NET AJAX uç noktası olmadan kullanarak Yapılandırması Ekle](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="da688-104">The basic procedures for building such services is discussed in [How to: Use Configuration to Add an ASP.NET AJAX Endpoint](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md) and [How to: Add an ASP.NET AJAX Endpoint Without Using Configuration](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).</span></span>  
  
 <span data-ttu-id="da688-105">ASP.NET AJAX varsayılan olan HTTP POST ile HTTP POST ve GET HTTP fiilleri kullanan işlemleri destekler.</span><span class="sxs-lookup"><span data-stu-id="da688-105">ASP.NET AJAX supports operations that use the HTTP POST and HTTP GET verbs, with HTTP POST being the default.</span></span> <span data-ttu-id="da688-106">Bir işlem oluşturma yan etkileri varsa ve nadiren bağlanan veya hiç değişen verileri döndürür, HTTP GET bunun yerine kullanın.</span><span class="sxs-lookup"><span data-stu-id="da688-106">When creating an operation that has no side effects and returns data that rarely or never changes, use HTTP GET instead.</span></span> <span data-ttu-id="da688-107">GET işlemleri sonuçlarını, aynı işlemi birden çok çağrı hizmetinize tek bir istekte neden olabilir yani önbelleğe alınabilir.</span><span class="sxs-lookup"><span data-stu-id="da688-107">Results of GET operations can be cached, which means that multiple calls to the same operation may result in only one request to your service.</span></span> <span data-ttu-id="da688-108">WCF tarafından belirtilmez ancak (tarayıcıda bir kullanıcının, bir ara sunucu ve diğer düzeylere.) herhangi bir düzeyde gerçekleştirilebildiği önbelleğe alma Önbelleğe alma hizmeti performansını artırmak istiyorsanız verileri sık sık değişiyorsa kabul edilebilir olmayabilir ancak veya işlem bir eylem gerçekleştirirse avantajlıdır.</span><span class="sxs-lookup"><span data-stu-id="da688-108">The caching is not done by WCF but can take place at any level (in a user's browser, on a proxy server, and other levels.) Caching is advantageous if you want to increase service performance, but may not be acceptable if data changes frequently or if the operation performs some action.</span></span>  
  
 <span data-ttu-id="da688-109">Örneğin, bir kullanıcının Müzik Kitaplığı yönetmek için hizmeti tasarlıyorsanız, Al kullanarak bir albüm başlık avantajları göre sanatçının arayan bir işlem ancak albüm kullanıcının kişisel koleksiyonuna ekler. bir işlem sonrası kullanmalısınız.</span><span class="sxs-lookup"><span data-stu-id="da688-109">For example, if you are designing service to manage a user's music library, an operation that looks up the artist based on an album's title benefits from using GET, but an operation that adds an album to the user's personal collection must use POST.</span></span>  
  
 <span data-ttu-id="da688-110">Önbellek ömrünü denetlemek için kullanın <xref:System.ServiceModel.Web.OutgoingWebResponseContext> türü.</span><span class="sxs-lookup"><span data-stu-id="da688-110">To control the lifetime of the cache, use the <xref:System.ServiceModel.Web.OutgoingWebResponseContext> type.</span></span> <span data-ttu-id="da688-111">Örneğin, hava durumu tahminleri saatlik güncelleştirildi, kullanacağınız döndüren bir hizmet tasarlarken ALIR ancak hizmet kullanıcıları, eski veri erişimini engellemek için bir saat veya daha az önbellek süresi sınırlayın.</span><span class="sxs-lookup"><span data-stu-id="da688-111">For example, when designing a service that returns weather forecasts updated hourly, you would use GET but limit the cache duration to an hour or less to prevent the users of the service from accessing stale data.</span></span>  
  
 <span data-ttu-id="da688-112">Betik Manager denetim kullanan hizmetler bir ASP.NET AJAX sayfasından kullanırken, işlemin kullandığı GET veya POST - betik manager mekanizması doğru istek türü verilmesi sağlanır olup olmadığını yönelttiğiniz fark etmez.</span><span class="sxs-lookup"><span data-stu-id="da688-112">When using services from an ASP.NET AJAX page that use the Script Manager control, it makes no difference whether the operation uses GET or POST - the script manager mechanism ensures that the correct request type is issued.</span></span>  
  
 <span data-ttu-id="da688-113">HTTP GET işlemleri, karmaşık veri anlaşması türleri dahil olmak üzere sonrası işlemleri tarafından desteklenen tüm giriş parametrelerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="da688-113">HTTP GET operations use any input parameters supported by POST operations, including complex data contract types.</span></span> <span data-ttu-id="da688-114">Ancak, çoğu durumda bu çok fazla parametre veya önbellek verimliliğini azaltır çünkü GET işlemleri çok karmaşık parametreler önlemek için önerilir.</span><span class="sxs-lookup"><span data-stu-id="da688-114">However, in most cases it is recommended to avoid too many parameters or parameters that are too complex in GET operations because it reduces caching efficiency.</span></span>  
  
 <span data-ttu-id="da688-115">Bu konuda GET ve POST ekleyerek arasında seçim yapmayı gösteren <xref:System.ServiceModel.Web.WebGetAttribute> veya <xref:System.ServiceModel.Web.WebInvokeAttribute> öznitelikleri hizmet sözleşmesindeki ilgili işlemler.</span><span class="sxs-lookup"><span data-stu-id="da688-115">This topic demonstrates how to select between GET and POST by adding the <xref:System.ServiceModel.Web.WebGetAttribute> or <xref:System.ServiceModel.Web.WebInvokeAttribute> attributes to the relevant operations in the service contract.</span></span> <span data-ttu-id="da688-116">Çalışan hizmeti almak için gereken (uygulama, yapılandırın ve hizmeti barındırmak için) diğer adımları tüm ASP.NET AJAX WCF hizmeti tarafından kullanılan benzerdir.</span><span class="sxs-lookup"><span data-stu-id="da688-116">The other steps (to implement, configure and host the service) that are required to get the service running are similar to those used by any ASP.NET AJAX service in WCF.</span></span>  
  
 <span data-ttu-id="da688-117">Bir işlem ile işaretlenen <xref:System.ServiceModel.Web.WebGetAttribute> her zaman bir GET isteği kullanır.</span><span class="sxs-lookup"><span data-stu-id="da688-117">An operation marked with the <xref:System.ServiceModel.Web.WebGetAttribute> always uses a GET request.</span></span> <span data-ttu-id="da688-118">Bir işlem ile işaretlenen <xref:System.ServiceModel.Web.WebInvokeAttribute>, veya değil herhangi bir iki özniteliği ile işaretlenmiş, bir POST isteği kullanır.</span><span class="sxs-lookup"><span data-stu-id="da688-118">An operation marked with the <xref:System.ServiceModel.Web.WebInvokeAttribute>, or not marked with any of the two attributes, uses a POST request.</span></span> <span data-ttu-id="da688-119"><xref:System.ServiceModel.Web.WebInvokeAttribute> Diğer HTTP fiilleri, diğer alın ve sonrası (PUT ve DELETE gibi) kullanımına izin verdiği <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="da688-119">The <xref:System.ServiceModel.Web.WebInvokeAttribute> allows the use of other HTTP verbs, other than GET and POST (such as PUT and DELETE) through the <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> property.</span></span> <span data-ttu-id="da688-120">Ancak, bu Eylemler, ASP.NET AJAX tarafından desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="da688-120">However, these verbs are not supported by ASP.NET AJAX.</span></span> <span data-ttu-id="da688-121">ASP.NET sayfaları komut Yöneticisi denetimini kullanarak hizmetinden kullanmak istiyorsanız, kullanmayın <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="da688-121">If you intend to use the service from ASP.NET pages using the Script Manager control, do not use the <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> property.</span></span>  
  
 <span data-ttu-id="da688-122">GET için geçiş, çalışan bir örnek için bkz: [temel AJAX hizmeti](../../../../docs/framework/wcf/samples/basic-ajax-service.md) örnek.</span><span class="sxs-lookup"><span data-stu-id="da688-122">For a working example of switching to GET, see the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md) sample.</span></span>  
  
 <span data-ttu-id="da688-123">POST kullanan bir örnek için bkz. [hizmet HTTP POST kullanan AJAX](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md) örnek.</span><span class="sxs-lookup"><span data-stu-id="da688-123">For a sample that uses POST, see the [AJAX Service Using HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md) sample.</span></span>  
  
## <a name="to-create-a-wcf-service-that-responds-to-http-get-or-http-post-requests"></a><span data-ttu-id="da688-124">Bir WCF hizmeti oluşturmak için HTTP GET veya POST HTTP isteklerine yanıt</span><span class="sxs-lookup"><span data-stu-id="da688-124">To create a WCF service that responds to HTTP GET or HTTP POST requests</span></span>
  
1. <span data-ttu-id="da688-125">İle işaretlenen arabirim ile temel bir WCF sözleşmesi tanımlayın. <xref:System.ServiceModel.ServiceContractAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="da688-125">Define a basic WCF service contract with an interface marked with the <xref:System.ServiceModel.ServiceContractAttribute> attribute.</span></span> <span data-ttu-id="da688-126">Her işlemi ile işaretle <xref:System.ServiceModel.OperationContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="da688-126">Mark each operation with the <xref:System.ServiceModel.OperationContractAttribute>.</span></span> <span data-ttu-id="da688-127">Ekleme <xref:System.ServiceModel.Web.WebGetAttribute> bir işlem HTTP GET isteklerine yanıt vermesini işleyebileceği için özniteliği.</span><span class="sxs-lookup"><span data-stu-id="da688-127">Add the <xref:System.ServiceModel.Web.WebGetAttribute> attribute to stipulate that an operation should respond to HTTP GET requests.</span></span> <span data-ttu-id="da688-128">Ayrıca ekleyebilirsiniz <xref:System.ServiceModel.Web.WebInvokeAttribute> HTTP POST açıkça belirtmek için özniteliği veya bir öznitelik varsayılan olarak HTTP POST belirtmeyin.</span><span class="sxs-lookup"><span data-stu-id="da688-128">You can also add the <xref:System.ServiceModel.Web.WebInvokeAttribute> attribute to explicitly specify HTTP POST, or not specify an attribute, which defaults to HTTP POST.</span></span>
  
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
  
2. <span data-ttu-id="da688-129">Uygulama `IMusicService` hizmet söyleşmesi bir `MusicService`.</span><span class="sxs-lookup"><span data-stu-id="da688-129">Implement the `IMusicService` service contract with a `MusicService`.</span></span>
  
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
  
3. <span data-ttu-id="da688-130">Uygulamada .svc uzantılı hizmeti adlı yeni bir dosya oluşturun.</span><span class="sxs-lookup"><span data-stu-id="da688-130">Create a new file named service with a .svc extension in the application.</span></span> <span data-ttu-id="da688-131">Uygun ekleyerek bu dosyayı Düzenle [ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) hizmeti yönerge bilgi.</span><span class="sxs-lookup"><span data-stu-id="da688-131">Edit this file by adding the appropriate [\@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive information for the service.</span></span> <span data-ttu-id="da688-132">Belirten <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> kullanılacak olan [ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) yönergesi, bir ASP.NET AJAX uç noktası otomatik olarak yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="da688-132">Specify that the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> is to be used in the [\@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive to automatically configure an ASP.NET AJAX endpoint.</span></span>  
  
    ```  
    <%@ServiceHost   
        language=c#   
        Debug="true"   
        Service="Microsoft.Ajax.Samples.MusicService"  
        Factory=System.ServiceModel.Activation.WebScriptServiceHostFactory  
    %>  
    ```  
  
## <a name="to-call-the-service"></a><span data-ttu-id="da688-133">Hizmeti çağırmak için</span><span class="sxs-lookup"><span data-stu-id="da688-133">To call the service</span></span>  
  
1. <span data-ttu-id="da688-134">Tarayıcıyı kullanarak herhangi bir istemci kod olmadan hizmetinizin GET işlemleri test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="da688-134">You can test your service's GET operations without any client code, by using the browser.</span></span> <span data-ttu-id="da688-135">Örneğin, hizmetiniz, yapılandırılması durumunda `http://example.com/service.svc` sonra yazarak adresi `http://example.com/service.svc/LookUpArtist?album=SomeAlbum` tarayıcı adres çubuğuna hizmeti çağırır ve indirdiğiniz ya da görüntülenen yanıt neden olur.</span><span class="sxs-lookup"><span data-stu-id="da688-135">For example, if your service is configured at the `http://example.com/service.svc` address, then typing `http://example.com/service.svc/LookUpArtist?album=SomeAlbum` into the browser address bar invokes the service and causes the response to be downloaded or displayed.</span></span>
  
2. <span data-ttu-id="da688-136">Diğer bir ASP.NET AJAX Hizmetleri aynı şekilde GET işlemleri ile Hizmetleri'ni kullanabilirsiniz - URL ASP.NET AJAX komut Yöneticisi'nin betikleri koleksiyonuna hizmet girerek denetim.</span><span class="sxs-lookup"><span data-stu-id="da688-136">You can use services with GET operations in the same way as any other ASP.NET AJAX services - by entering the service URL into the Scripts collection of the ASP.NET AJAX Script Manager control.</span></span> <span data-ttu-id="da688-137">Bir örnek için bkz. [temel AJAX hizmeti](../../../../docs/framework/wcf/samples/basic-ajax-service.md).</span><span class="sxs-lookup"><span data-stu-id="da688-137">For an example, see the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="da688-138">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="da688-138">See Also</span></span>  
 [<span data-ttu-id="da688-139">ASP.NET AJAX için WCF Hizmetleri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="da688-139">Creating WCF Services for ASP.NET AJAX</span></span>](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)  
 [<span data-ttu-id="da688-140">Nasıl yapılır: AJAX Etkinleştirilmiş ASP.NET Web Hizmetlerini WCF'ye Taşıma</span><span class="sxs-lookup"><span data-stu-id="da688-140">How to: Migrate AJAX-Enabled ASP.NET Web Services to WCF</span></span>](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
