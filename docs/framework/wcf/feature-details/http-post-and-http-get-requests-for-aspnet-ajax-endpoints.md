---
title: "Nasıl yapılır: ASP.NET AJAX Uç Noktaları için HTTP POST ve HTTP GET İstekleri Arasında Seçim Yapma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b47de82a-4c92-4af6-bceb-a5cb8bb8ede9
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fa8aceace03d1abb3bb83de1262331485f12ded3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-choose-between-http-post-and-http-get-requests-for-aspnet-ajax-endpoints"></a><span data-ttu-id="3e22f-102">Nasıl yapılır: ASP.NET AJAX Uç Noktaları için HTTP POST ve HTTP GET İstekleri Arasında Seçim Yapma</span><span class="sxs-lookup"><span data-stu-id="3e22f-102">How to: Choose between HTTP POST and HTTP GET requests for ASP.NET AJAX Endpoints</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="3e22f-103">JavaScript'ten bir istemci Web sitesinde çağrılabilen bir ASP.NET AJAX etkin bir uç nokta kullanıma sunan bir hizmet oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="3e22f-103"> allows you to create a service that exposes an ASP.NET AJAX-enabled endpoint that can be called from JavaScript on a client Web site.</span></span> <span data-ttu-id="3e22f-104">Bu tür hizmetlerin oluşturmak için temel yordamlar ele alınmıştır [nasıl yapılır: ASP.NET AJAX uç noktası eklemek için yapılandırma kullan](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md) ve [nasıl yapılır: ASP.NET AJAX uç nokta olmadan kullanarak yapılandırması eklemek](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="3e22f-104">The basic procedures for building such services is discussed in [How to: Use Configuration to Add an ASP.NET AJAX Endpoint](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md) and [How to: Add an ASP.NET AJAX Endpoint Without Using Configuration](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).</span></span>  
  
 <span data-ttu-id="3e22f-105">ASP.NET AJAX'ı varsayılan olan HTTP POST ile HTTP POST ve HTTP GET fiilleri kullanan işlemler destekler.</span><span class="sxs-lookup"><span data-stu-id="3e22f-105">ASP.NET AJAX supports operations that use the HTTP POST and HTTP GET verbs, with HTTP POST being the default.</span></span> <span data-ttu-id="3e22f-106">Bir işlem oluşturma hiçbir yan etkileri varsa ve nadiren bağlanan veya hiç değişen verileri döndürür, HTTP GET yerine kullanın.</span><span class="sxs-lookup"><span data-stu-id="3e22f-106">When creating an operation that has no side effects and returns data that rarely or never changes, use HTTP GET instead.</span></span> <span data-ttu-id="3e22f-107">GET işlemlerin sonuçlarını, yani aynı işlem için birden fazla çağrı hizmetiniz için yalnızca bir istekte sonuçlanabilir önbelleğe alınabilir.</span><span class="sxs-lookup"><span data-stu-id="3e22f-107">Results of GET operations can be cached, which means that multiple calls to the same operation may result in only one request to your service.</span></span> <span data-ttu-id="3e22f-108">Önbelleğe alma işlem [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ancak (tarayıcıda bir kullanıcının, bir proxy sunucusu ve diğer düzeylerdeki.) herhangi bir düzeyde yer alabilir Önbelleğe alma veriler sık değişiyorsa kabul edilebilir olmayabilir ancak veya hizmet performansını artırmak istiyorsanız işlemi bazı eylemler gerçekleştiriyorsa avantajlıdır.</span><span class="sxs-lookup"><span data-stu-id="3e22f-108">The caching is not done by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] but can take place at any level (in a user's browser, on a proxy server, and other levels.) Caching is advantageous if you want to increase service performance, but may not be acceptable if data changes frequently or if the operation performs some action.</span></span>  
  
 <span data-ttu-id="3e22f-109">Örneğin, bir kullanıcının Müzik Kitaplığı yönetmek için hizmeti tanımlıyorsanız, GET kullanarak bir albüm başlık avantajları göre sanatçı arayan bir işlem, ancak bir albümü kullanıcının kişisel koleksiyona ekler bir işlem sonrası kullanmalısınız.</span><span class="sxs-lookup"><span data-stu-id="3e22f-109">For example, if you are designing service to manage a user's music library, an operation that looks up the artist based on an album's title benefits from using GET, but an operation that adds an album to the user's personal collection must use POST.</span></span>  
  
 <span data-ttu-id="3e22f-110">Önbellek ömrünü denetlemek için kullandığı <xref:System.ServiceModel.Web.OutgoingWebResponseContext> türü.</span><span class="sxs-lookup"><span data-stu-id="3e22f-110">To control the lifetime of the cache, use the <xref:System.ServiceModel.Web.OutgoingWebResponseContext> type.</span></span> <span data-ttu-id="3e22f-111">Örneğin, döndürür hava tahminleri saatlik güncelleştirildi, kullanacağınız bir hizmet tasarlarken GET ancak hizmet kullanıcıların eski veri erişimini engellemek için önbelleğe alma süresi bir saat veya daha az sınırlamak.</span><span class="sxs-lookup"><span data-stu-id="3e22f-111">For example, when designing a service that returns weather forecasts updated hourly, you would use GET but limit the cache duration to an hour or less to prevent the users of the service from accessing stale data.</span></span>  
  
 <span data-ttu-id="3e22f-112">Komut dosyası Manager denetim kullanan hizmetler bir ASP.NET AJAX sayfasından kullanırken, işlemin kullandığı GET veya POST - komut dosyası manager mekanizması doğru istek türü verilmesi sağlanır olup olmadığını fark etmez.</span><span class="sxs-lookup"><span data-stu-id="3e22f-112">When using services from an ASP.NET AJAX page that use the Script Manager control, it makes no difference whether the operation uses GET or POST - the script manager mechanism ensures that the correct request type is issued.</span></span>  
  
 <span data-ttu-id="3e22f-113">HTTP GET işlemleri karmaşık veri sözleşme türleri dahil olmak üzere gönderme işlemleri tarafından desteklenen giriş parametreleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="3e22f-113">HTTP GET operations use any input parameters supported by POST operations, including complex data contract types.</span></span> <span data-ttu-id="3e22f-114">Ancak, çoğu durumda çok fazla parametreleri veya çünkü önbellek verimliliği azaltır, GET işlemlerinde çok karmaşık parametreleri önlemek için önerilir.</span><span class="sxs-lookup"><span data-stu-id="3e22f-114">However, in most cases it is recommended to avoid too many parameters or parameters that are too complex in GET operations because it reduces caching efficiency.</span></span>  
  
 <span data-ttu-id="3e22f-115">Bu konu, GET ve POST ekleyerek arasında seçmek gösterilmiştir <xref:System.ServiceModel.Web.WebGetAttribute> veya <xref:System.ServiceModel.Web.WebInvokeAttribute> hizmet sözleşmesi ilgili işlemlerinde özniteliklerini.</span><span class="sxs-lookup"><span data-stu-id="3e22f-115">This topic demonstrates how to select between GET and POST by adding the <xref:System.ServiceModel.Web.WebGetAttribute> or <xref:System.ServiceModel.Web.WebInvokeAttribute> attributes to the relevant operations in the service contract.</span></span> <span data-ttu-id="3e22f-116">Hizmet çalışıyor almak için gerekli olan (uygulamak, yapılandırma ve hizmet barındırmak için) diğer adımlar herhangi bir ASP.NET AJAX hizmeti tarafından kullanılan benzerdir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3e22f-116">The other steps (to implement, configure and host the service) that are required to get the service running are similar to those used by any ASP.NET AJAX service in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
 <span data-ttu-id="3e22f-117">Bir işlem olarak <xref:System.ServiceModel.Web.WebGetAttribute> her zaman bir GET isteği kullanır.</span><span class="sxs-lookup"><span data-stu-id="3e22f-117">An operation marked with the <xref:System.ServiceModel.Web.WebGetAttribute> always uses a GET request.</span></span> <span data-ttu-id="3e22f-118">Bir işlem olarak <xref:System.ServiceModel.Web.WebInvokeAttribute>, veya değil herhangi iki özniteliği ile işaretlenmiş, bir POST isteği kullanır.</span><span class="sxs-lookup"><span data-stu-id="3e22f-118">An operation marked with the <xref:System.ServiceModel.Web.WebInvokeAttribute>, or not marked with any of the two attributes, uses a POST request.</span></span> <span data-ttu-id="3e22f-119"><xref:System.ServiceModel.Web.WebInvokeAttribute> Üzerinden diğer HTTP fiillerini, diğer GET ve POST (koy ve Sil gibi) daha kullanılmasına izin verir <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="3e22f-119">The <xref:System.ServiceModel.Web.WebInvokeAttribute> allows the use of other HTTP verbs, other than GET and POST (such as PUT and DELETE) through the <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> property.</span></span> <span data-ttu-id="3e22f-120">Ancak, bu fiiller ASP.NET AJAX tarafından desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="3e22f-120">However, these verbs are not supported by ASP.NET AJAX.</span></span> <span data-ttu-id="3e22f-121">ASP.NET sayfaları komut dosyası Yöneticisi denetimini kullanarak hizmetinden kullanmak istiyorsanız, kullanmayın <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="3e22f-121">If you intend to use the service from ASP.NET pages using the Script Manager control, do not use the <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> property.</span></span>  
  
 <span data-ttu-id="3e22f-122">GET geçiş, çalışan bir örnek için bkz: [temel AJAX hizmeti](../../../../docs/framework/wcf/samples/basic-ajax-service.md) örnek.</span><span class="sxs-lookup"><span data-stu-id="3e22f-122">For a working example of switching to GET, see the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md) sample.</span></span>  
  
 <span data-ttu-id="3e22f-123">POST kullanan bir örnek için bkz: [AJAX hizmeti kullanarak HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md) örnek.</span><span class="sxs-lookup"><span data-stu-id="3e22f-123">For a sample that uses POST, see the [AJAX Service Using HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md) sample.</span></span>  
  
### <a name="to-create-a-wcf-service-that-responds-to-http-get-or-http-post-requests"></a><span data-ttu-id="3e22f-124">Bir WCF hizmeti oluşturma, HTTP GET veya HTTP POST isteklerini yanıtlar</span><span class="sxs-lookup"><span data-stu-id="3e22f-124">To create a WCF service that responds to HTTP GET or HTTP POST requests</span></span>  
  
1.  <span data-ttu-id="3e22f-125">Temel bir tanımlamak [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet sözleşmesini bir arabirim ile işaretlenmiş <xref:System.ServiceModel.ServiceContractAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="3e22f-125">Define a basic [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service contract with an interface marked with the <xref:System.ServiceModel.ServiceContractAttribute> attribute.</span></span> <span data-ttu-id="3e22f-126">Her işlemiyle işaretlemek <xref:System.ServiceModel.OperationContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="3e22f-126">Mark each operation with the <xref:System.ServiceModel.OperationContractAttribute>.</span></span> <span data-ttu-id="3e22f-127">Ekleme <xref:System.ServiceModel.Web.WebGetAttribute> bir işlem HTTP GET isteklerine yanıt vermesi gerektiğini iznine özniteliği.</span><span class="sxs-lookup"><span data-stu-id="3e22f-127">Add the <xref:System.ServiceModel.Web.WebGetAttribute> attribute to stipulate that an operation should respond to HTTP GET requests.</span></span> <span data-ttu-id="3e22f-128">Ayrıca ekleyebileceğiniz <xref:System.ServiceModel.Web.WebInvokeAttribute> HTTP POST açıkça belirtmek için öznitelik veya HTTP POST için varsayılan olarak bir öznitelik belirtmeyin.</span><span class="sxs-lookup"><span data-stu-id="3e22f-128">You can also add the <xref:System.ServiceModel.Web.WebInvokeAttribute> attribute to explicitly specify HTTP POST, or not specify an attribute, which defaults to HTTP POST.</span></span>  
  
    ```  
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
  
2.  <span data-ttu-id="3e22f-129">Uygulama `IMusicService` hizmet sözleşmesine bir `MusicService`.</span><span class="sxs-lookup"><span data-stu-id="3e22f-129">Implement the `IMusicService` service contract with a `MusicService`.</span></span>  
  
    ```  
    public class MusicService : IMusicService  
    {  
        public void AddAlbum(string user, string album)  
        {  
            //Add implementation here.  
        }  
  
         //Other operations omitted…  
    }  
    ```  
  
3.  <span data-ttu-id="3e22f-130">Hizmet uygulaması .svc uzantısıyla adlı yeni bir dosya oluşturun.</span><span class="sxs-lookup"><span data-stu-id="3e22f-130">Create a new file named service with a .svc extension in the application.</span></span> <span data-ttu-id="3e22f-131">Uygun ekleyerek bu dosyayı düzenlemek [ @ServiceHost ](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) hizmet için yönerge bilgileri.</span><span class="sxs-lookup"><span data-stu-id="3e22f-131">Edit this file by adding the appropriate [@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive information for the service.</span></span> <span data-ttu-id="3e22f-132">Belirtmek <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> kullanılacak olan [ @ServiceHost ](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) yönergesi ASP.NET AJAX uç noktası otomatik olarak yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="3e22f-132">Specify that the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> is to be used in the [@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive to automatically configure an ASP.NET AJAX endpoint.</span></span>  
  
    ```  
    <%@ServiceHost   
        language=c#   
        Debug="true"   
        Service="Microsoft.Ajax.Samples.MusicService"  
        Factory=System.ServiceModel.Activation.WebScriptServiceHostFactory  
    %>  
    ```  
  
### <a name="to-call-the-service"></a><span data-ttu-id="3e22f-133">Hizmeti çağırmak için</span><span class="sxs-lookup"><span data-stu-id="3e22f-133">To call the service</span></span>  
  
1.  <span data-ttu-id="3e22f-134">Tarayıcıyı kullanarak hizmetinizin GET işlemleri herhangi bir istemci kod olmadan test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3e22f-134">You can test your service's GET operations without any client code, by using the browser.</span></span> <span data-ttu-id="3e22f-135">Örneğin, hizmetiniz "http://example.com/service.svc" adresinde yapılandırdıysanız, ardından "http://example.com/service.svc/LookUpArtist?album=SomeAlbum" tarayıcınızın adres çubuğuna yazarak hizmet çağırır ve yanıt olması neden olur indirilen veya görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="3e22f-135">For example, if your service is configured at the "http://example.com/service.svc" address, then typing "http://example.com/service.svc/LookUpArtist?album=SomeAlbum" into the browser address bar invokes the service and causes the response to be downloaded or displayed.</span></span>  
  
2.  <span data-ttu-id="3e22f-136">Diğer bir ASP.NET AJAX Hizmetleri aynı şekilde GET işlemleriyle Hizmetleri'ni kullanabilirsiniz - hizmet girerek betikleri koleksiyona ASP.NET AJAX komut dosyası Yöneticisi'nin URL kontrol.</span><span class="sxs-lookup"><span data-stu-id="3e22f-136">You can use services with GET operations in the same way as any other ASP.NET AJAX services - by entering the service URL into the Scripts collection of the ASP.NET AJAX Script Manager control.</span></span> <span data-ttu-id="3e22f-137">Bir örnek için bkz: [temel AJAX hizmeti](../../../../docs/framework/wcf/samples/basic-ajax-service.md).</span><span class="sxs-lookup"><span data-stu-id="3e22f-137">For an example, see the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e22f-138">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3e22f-138">See Also</span></span>  
 [<span data-ttu-id="3e22f-139">ASP.NET AJAX için WCF Hizmetleri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="3e22f-139">Creating WCF Services for ASP.NET AJAX</span></span>](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)  
 [<span data-ttu-id="3e22f-140">Nasıl yapılır: AJAX Etkinleştirilmiş ASP.NET Web Hizmetlerini WCF'ye Taşıma</span><span class="sxs-lookup"><span data-stu-id="3e22f-140">How to: Migrate AJAX-Enabled ASP.NET Web Services to WCF</span></span>](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
