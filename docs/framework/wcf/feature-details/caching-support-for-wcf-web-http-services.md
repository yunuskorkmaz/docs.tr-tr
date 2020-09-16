---
title: WCF Web HTTP Hizmetleri için Önbelleğe Alma Desteği
ms.date: 03/30/2017
ms.assetid: 7f8078e0-00d9-415c-b8ba-c1b6d5c31799
ms.openlocfilehash: 0445f0214f90873dad4241789db270c9b6f4a2f6
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90559421"
---
# <a name="caching-support-for-wcf-web-http-services"></a><span data-ttu-id="4f3ae-102">WCF Web HTTP Hizmetleri için Önbelleğe Alma Desteği</span><span class="sxs-lookup"><span data-stu-id="4f3ae-102">Caching Support for WCF Web HTTP Services</span></span>

[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] <span data-ttu-id="4f3ae-103">WCF Web HTTP hizmetinizdeki ASP.NET ' de zaten kullanılabilir olan bildirime dayalı önbelleğe alma mekanizmasını kullanmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="4f3ae-103">enables you to use the declarative caching mechanism already available in ASP.NET in your WCF Web HTTP services.</span></span> <span data-ttu-id="4f3ae-104">Bu, WCF Web HTTP hizmet işlemlerinizin yanıtlarını önbelleğe almanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="4f3ae-104">This allows you to cache responses from your WCF Web HTTP service operations.</span></span> <span data-ttu-id="4f3ae-105">Bir kullanıcı hizmetinize önbelleğe alma için yapılandırılmış bir HTTP Al gönderdiğinde, ASP.NET önbelleğe alınan yanıtı geri gönderir ve hizmet yöntemi çağrılmaz.</span><span class="sxs-lookup"><span data-stu-id="4f3ae-105">When a user sends an HTTP GET to your service that is configured for caching, ASP.NET sends back the cached response and the service method is not called.</span></span> <span data-ttu-id="4f3ae-106">Önbelleğin süresi dolarsa, bir Kullanıcı bir sonraki HTTP GET gönderdiğinde, hizmet yönteminiz çağrılır ve yanıt yeniden önbelleğe alınır.</span><span class="sxs-lookup"><span data-stu-id="4f3ae-106">When the cache expires, the next time a user sends an HTTP GET, your service method is called and the response is once again cached.</span></span> <span data-ttu-id="4f3ae-107">ASP.NET önbelleğe alma hakkında daha fazla bilgi için bkz. [ASP.net Caching Overview](/previous-versions/aspnet/ms178597(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="4f3ae-107">For more information about ASP.NET caching, see [ASP.NET Caching Overview](/previous-versions/aspnet/ms178597(v=vs.100)).</span></span>  
  
## <a name="basic-web-http-service-caching"></a><span data-ttu-id="4f3ae-108">Temel Web HTTP hizmeti önbelleğe alma</span><span class="sxs-lookup"><span data-stu-id="4f3ae-108">Basic Web HTTP Service Caching</span></span>  

  <span data-ttu-id="4f3ae-109">WEB HTTP hizmeti önbelleğe alma özelliğini etkinleştirmek için, önce hizmet ayarını veya ' a uygulayarak ASP.NET uyumluluğunu etkinleştirmeniz gerekir <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute.RequirementsMode%2A> <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed> <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Required> .</span><span class="sxs-lookup"><span data-stu-id="4f3ae-109">To enable WEB HTTP service caching, you must first enable ASP.NET compatibility by applying the <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> to the service setting <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute.RequirementsMode%2A> to <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed> or <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Required>.</span></span>  
  
 <span data-ttu-id="4f3ae-110">.NET Framework 4 <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> , bir önbellek profili adı belirtmenize olanak tanıyan adlı yeni bir özniteliği tanıtır.</span><span class="sxs-lookup"><span data-stu-id="4f3ae-110">.NET Framework 4 introduces a new attribute called <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> that allows you to specify a cache profile name.</span></span> <span data-ttu-id="4f3ae-111">Bu öznitelik bir hizmet işlemine uygulanır.</span><span class="sxs-lookup"><span data-stu-id="4f3ae-111">This attribute is applied to a service operation.</span></span> <span data-ttu-id="4f3ae-112">Aşağıdaki örnek, <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> ASP.net uyumluluğunu etkinleştirmek için bir hizmete uygular ve `GetCustomer` işlemi önbelleğe alma için yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="4f3ae-112">The following example applies the <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> to a service to enable ASP.NET compatibility and configures the `GetCustomer` operation for caching.</span></span> <span data-ttu-id="4f3ae-113"><xref:System.ServiceModel.Web.AspNetCacheProfileAttribute>Özniteliği, kullanılacak önbellek ayarlarını içeren bir önbellek profili belirtir.</span><span class="sxs-lookup"><span data-stu-id="4f3ae-113">The <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> attribute specifies a cache profile that contains the cache settings to be used.</span></span>  
  
```csharp
[ServiceContract]
[AspNetCompatibilityRequirements(RequirementsMode=AspNetCompatibilityRequirementsMode.Allowed)]
public class Service
{
    [WebGet(UriTemplate = "{id}")]
    [AspNetCacheProfile("CacheFor60Seconds")]
    public Customer GetCustomer(string id)
    {
        // ...
    }
}
```  
  
<span data-ttu-id="4f3ae-114">Ayrıca, aşağıdaki örnekte gösterildiği gibi Web.config dosyasında ASP.NET uyumluluk modunu açın.</span><span class="sxs-lookup"><span data-stu-id="4f3ae-114">Also turn on ASP.NET compatibility mode in the Web.config file as shown in the following example.</span></span>  
  
```xml
<system.serviceModel>
  <serviceHostingEnvironment aspNetCompatibilityEnabled="true" />
</system.serviceModel>
```
  
> [!WARNING]
> <span data-ttu-id="4f3ae-115">ASP.NET uyumluluk modu açık değilse ve <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> bir özel durum kullanılırsa, bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="4f3ae-115">If ASP.NET compatibility mode is not turned on and the <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> is used an exception is thrown.</span></span>  
  
 <span data-ttu-id="4f3ae-116">Tarafından belirtilen önbellek profili adı, <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> Web.config yapılandırma dosyanıza eklenen bir önbellek profilini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4f3ae-116">The cache profile name specified by the <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> identifies a cache profile that is added to your Web.config configuration file.</span></span> <span data-ttu-id="4f3ae-117">Önbellek profili, `outputCacheSetting` aşağıdaki yapılandırma örneğinde gösterildiği gibi bir <> öğesi ile tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="4f3ae-117">The cache profile is defined with in a <`outputCacheSetting`> element as shown in the following configuration example.</span></span>  
  
```xml
<!-- ...  -->
<system.web>  
   <caching>  
      <outputCacheSettings>  
         <outputCacheProfiles>  
            <add name="CacheFor60Seconds" duration="60" varyByParam="none" sqlDependency="MyTestDatabase:MyTable"/>  
         </outputCacheProfiles>  
      </outputCacheSettings>  
   </caching>  
   <!-- ... -->  
</system.web>  
```  
  
 <span data-ttu-id="4f3ae-118">Bu, ASP.NET uygulamaları için kullanılabilen yapılandırma öğesidir.</span><span class="sxs-lookup"><span data-stu-id="4f3ae-118">This is the same configuration element that is available to ASP.NET applications.</span></span> <span data-ttu-id="4f3ae-119">ASP.NET önbellek profilleri hakkında daha fazla bilgi için bkz <xref:System.Web.Configuration.OutputCacheProfile> ..</span><span class="sxs-lookup"><span data-stu-id="4f3ae-119">For more information about ASP.NET cache profiles, see <xref:System.Web.Configuration.OutputCacheProfile>.</span></span> <span data-ttu-id="4f3ae-120">Web HTTP Hizmetleri için önbellek profilindeki en önemli öznitelikler şunlardır: `cacheDuration` ve `varyByParam` .</span><span class="sxs-lookup"><span data-stu-id="4f3ae-120">For Web HTTP services, the most important attributes in the cache profile are: `cacheDuration` and `varyByParam`.</span></span> <span data-ttu-id="4f3ae-121">Bu özniteliklerin her ikisi de gereklidir.</span><span class="sxs-lookup"><span data-stu-id="4f3ae-121">Both of these attributes are required.</span></span> <span data-ttu-id="4f3ae-122">`cacheDuration` yanıtın saniye cinsinden önbelleğe alınması gereken süreyi ayarlar.</span><span class="sxs-lookup"><span data-stu-id="4f3ae-122">`cacheDuration` sets the amount of time a response should be cached in seconds.</span></span> <span data-ttu-id="4f3ae-123">`varyByParam` yanıtları önbelleğe almak için kullanılan bir sorgu dizesi parametresi belirtmenize izin verir.</span><span class="sxs-lookup"><span data-stu-id="4f3ae-123">`varyByParam` allows you to specify a query string parameter that is used to cache responses.</span></span> <span data-ttu-id="4f3ae-124">Farklı sorgu dizesi parametre değerleriyle yapılan tüm istekler ayrı olarak önbelleğe alınır.</span><span class="sxs-lookup"><span data-stu-id="4f3ae-124">All requests made with different query string parameter values are cached separately.</span></span> <span data-ttu-id="4f3ae-125">Örneğin, bir başlangıç isteği yapıldıktan sonra `http://MyServer/MyHttpService/MyOperation?param=10` , aynı URI ile yapılan sonraki tüm istekler önbelleğe alınan yanıtı (önbellek süresi geçene kadar uzun) döndürür.</span><span class="sxs-lookup"><span data-stu-id="4f3ae-125">For example, once an initial request is made to `http://MyServer/MyHttpService/MyOperation?param=10`, all subsequent requests made with the same URI would be returned the cached response (so long as the cache duration has not elapsed).</span></span> <span data-ttu-id="4f3ae-126">Benzer bir istek için aynı ancak parametre sorgu dizesi parametresi için farklı bir değere sahip yanıtlar ayrı olarak önbelleğe alınır.</span><span class="sxs-lookup"><span data-stu-id="4f3ae-126">Responses for a similar request that is the same but has a different value for the parameter query string parameter are cached separately.</span></span> <span data-ttu-id="4f3ae-127">Bu ayrı önbelleğe alma davranışını istemiyorsanız, `varyByParam` "none" olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="4f3ae-127">If you do not want this separate caching behavior, set `varyByParam` to "none".</span></span>  
  
## <a name="sql-cache-dependency"></a><span data-ttu-id="4f3ae-128">SQL önbellek bağımlılığı</span><span class="sxs-lookup"><span data-stu-id="4f3ae-128">SQL Cache Dependency</span></span>  

  <span data-ttu-id="4f3ae-129">Web HTTP hizmet yanıtları bir SQL önbellek bağımlılığı ile de önbelleğe alınabilir.</span><span class="sxs-lookup"><span data-stu-id="4f3ae-129">Web HTTP service responses can also be cached with a SQL cache dependency.</span></span> <span data-ttu-id="4f3ae-130">WCF Web HTTP hizmetiniz bir SQL veritabanında depolanan verilere bağımlıysa, SQL veritabanı tablosundaki veriler değiştiğinde hizmetin yanıtını önbelleğe almak ve önbelleğe alınmış yanıtı geçersiz kılmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4f3ae-130">If your WCF Web HTTP service depends on data stored in a SQL database, you may want to cache the service's response and invalidate the cached response when data in the SQL database table changes.</span></span> <span data-ttu-id="4f3ae-131">Bu davranış, Web.config dosyası içinde tamamen yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="4f3ae-131">This behavior is configured completely within the Web.config file.</span></span> <span data-ttu-id="4f3ae-132">İlk olarak, <> öğesinde bir bağlantı dizesi tanımlayın `connectionStrings` .</span><span class="sxs-lookup"><span data-stu-id="4f3ae-132">First, define a connection string in the <`connectionStrings`> element.</span></span>  
  
```xml
<connectionStrings>
  <add name="connectString"
       connectionString="Data Source=MyService;Initial Catalog=MyTestDatabase;Integrated Security=True"
       providerName="System.Data.SqlClient" />
</connectionStrings>
```  
  
 <span data-ttu-id="4f3ae-133">Daha sonra `caching` , `system.web` aşağıdaki yapılandırma örneğinde gösterildiği gibi <> öğesi içindeki bir <> öğesinde SQL önbellek bağımlılığını etkinleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="4f3ae-133">Then you must enable SQL cache dependency within a <`caching`> element within the <`system.web`> element as shown in the following config example.</span></span>  
  
```xml  
<system.web>
  <caching>
    <sqlCacheDependency enabled="true" pollTime="1000">
      <databases>
        <add name="MyTestDatabase" connectionStringName="connectString" />
      </databases>
    </sqlCacheDependency>
    <!-- ... -->
  </caching>
  <!-- ... -->
</system.web>
```  
  
 <span data-ttu-id="4f3ae-134">Burada SQL önbellek bağımlılığı etkindir ve 1000 milisaniye bir yoklama süresi ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="4f3ae-134">Here SQL cache dependency is enabled and a polling time of 1000 milliseconds is set.</span></span> <span data-ttu-id="4f3ae-135">Yoklama süresi her geçtiğinde, veritabanı tablosunu güncelleştirme için denetlenir.</span><span class="sxs-lookup"><span data-stu-id="4f3ae-135">Each time the polling time elapses the database table is checked for updates.</span></span> <span data-ttu-id="4f3ae-136">Değişiklikler algılanırsa, önbelleğin içerikleri kaldırılır ve hizmet işleminin bir sonraki çağrılışında yeni bir yanıt önbelleğe alınır.</span><span class="sxs-lookup"><span data-stu-id="4f3ae-136">If changes are detected the contents of the cache are removed and the next time the service operation is invoked a new response is cached.</span></span> <span data-ttu-id="4f3ae-137"><`sqlCacheDependency`> öğesi içinde, aşağıdaki örnekte gösterildiği gibi veritabanlarını ekleyin ve <> öğesi içindeki bağlantı dizelerine başvurun `databases` .</span><span class="sxs-lookup"><span data-stu-id="4f3ae-137">Within the <`sqlCacheDependency`> element add the databases and reference the connection strings within the <`databases`> element as shown in the following example.</span></span>  
  
```xml  
<system.web>
  <caching>
    <sqlCacheDependency enabled="true" pollTime="1000">
      <databases>
        <add name="MyTestDatabase" connectionStringName="connectString" />
      </databases>  
    </sqlCacheDependency>  
    <!-- ... -->  
  </caching>  
  <!-- ... -->  
</system.web>  
```  
  
 <span data-ttu-id="4f3ae-138">Ardından, `caching` Aşağıdaki örnekte gösterildiği gibi <> öğesi içindeki çıktı önbelleği ayarlarını yapılandırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="4f3ae-138">Next you must configure the output cache settings within the <`caching`> element as shown in the following example.</span></span>  
  
```xml
<system.web>
  <caching>  
    <!-- ...  -->
    <outputCacheSettings>
      <outputCacheProfiles>
        <add name="CacheFor60Seconds" duration="60" varyByParam="none" sqlDependency="MyTestDatabase:MyTable" />
      </outputCacheProfiles>
    </outputCacheSettings>
  </caching>
  <!-- ... -->
</system.web>
```  
  
 <span data-ttu-id="4f3ae-139">Burada önbellek süresi 60 saniyeye ayarlanır, `varyByParam` None olarak ayarlanır ve `sqlDependency` iki nokta üst üste ile ayrılmış bir veritabanı adı/tablo çiftleri listesini noktalı virgülle ayrılmış bir liste olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="4f3ae-139">Here the cache duration is set to 60 seconds, `varyByParam` is set to none, and `sqlDependency` is set to a semicolon-delimited list of database name/table pairs separated by colons.</span></span> <span data-ttu-id="4f3ae-140">İçindeki veriler `MyTable` değiştirildiğinde, hizmet işlemi için önbelleğe alınmış yanıt kaldırılır ve işlem çağrıldığında yeni bir yanıt oluşturulur (hizmet işlemini çağırarak), önbelleğe alınır ve istemciye döndürülür.</span><span class="sxs-lookup"><span data-stu-id="4f3ae-140">When data in `MyTable` is changed the cached response for the service operation is removed and when the operation is invoked a new response is generated (by calling the service operation), cached, and returned to the client.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="4f3ae-141">ASP.NET 'in bir SQL veritabanına erişmesi için [ASP.NET SQL Server kayıt aracını](/previous-versions/dotnet/netframework-3.5/ms229862(v=vs.90))kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="4f3ae-141">For ASP.NET to access a SQL database, you must use the [ASP.NET SQL Server Registration Tool](/previous-versions/dotnet/netframework-3.5/ms229862(v=vs.90)).</span></span> <span data-ttu-id="4f3ae-142">Ayrıca, uygun Kullanıcı hesabının veritabanına ve tabloya erişimine izin vermeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="4f3ae-142">In addition you must allow the appropriate user account access to the database and table.</span></span> <span data-ttu-id="4f3ae-143">Daha fazla bilgi için bkz. [bir Web uygulamasından SQL Server erişme](/previous-versions/aspnet/ht43wsex(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="4f3ae-143">For more information, see [Accessing SQL Server from a Web Application](/previous-versions/aspnet/ht43wsex(v=vs.100)).</span></span>  
  
## <a name="conditional-http-get-based-caching"></a><span data-ttu-id="4f3ae-144">Koşullu HTTP alma tabanlı önbelleğe alma</span><span class="sxs-lookup"><span data-stu-id="4f3ae-144">Conditional HTTP GET Based Caching</span></span>  

  <span data-ttu-id="4f3ae-145">Web HTTP senaryolarında Koşullu HTTP GET, genellikle [http belirtiminde](https://www.w3.org/Protocols/rfc2616/rfc2616.html)açıklandığı gıbı akıllı http önbelleği uygulamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4f3ae-145">In Web HTTP scenarios a conditional HTTP GET is often used by services to implement intelligent HTTP caching as described in the [HTTP Specification](https://www.w3.org/Protocols/rfc2616/rfc2616.html).</span></span> <span data-ttu-id="4f3ae-146">Bunu yapmak için hizmet, HTTP yanıtında ETag üst bilgisinin değerini ayarlamış olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4f3ae-146">To do this, the service must set the value of the ETag header in the HTTP response.</span></span> <span data-ttu-id="4f3ae-147">Ayrıca, belirtilen ETag öğesinin geçerli ETag ile eşleşip eşleşmediğini görmek için HTTP isteğindeki If-None-Match üst bilgisini denetmelidir.</span><span class="sxs-lookup"><span data-stu-id="4f3ae-147">It also must check the If-None-Match header in the HTTP request to see whether any of the ETag specified matches the current ETag.</span></span>  
  
 <span data-ttu-id="4f3ae-148">GET ve HEAD istekleri için <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> bir ETag değeri alır ve Isteğin If-None-Match üst bilgisine karşı denetler.</span><span class="sxs-lookup"><span data-stu-id="4f3ae-148">For GET and HEAD requests, <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> takes an ETag value and checks it against the If-None-Match header of the request.</span></span> <span data-ttu-id="4f3ae-149">Üst bilgi varsa ve bir eşleşme varsa, <xref:System.ServiceModel.Web.WebFaultException> http durum kodu 304 (değiştirilmez) ile birlikte bir ETag üst bilgisi oluşturulur ve eşleşen ETag ile yanıta bir ETag üst bilgisi eklenir.</span><span class="sxs-lookup"><span data-stu-id="4f3ae-149">If the header is present and there is a match, a <xref:System.ServiceModel.Web.WebFaultException> with an HTTP status code 304 (Not Modified) is thrown and an ETag header is added to the response with the matching ETag.</span></span>  
  
 <span data-ttu-id="4f3ae-150">Metodun bir aşırı yüklemesi <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> son değiştirilme tarihi alır ve Isteğin If-Modified-Since üst bilgisine karşı denetler.</span><span class="sxs-lookup"><span data-stu-id="4f3ae-150">One overload of the <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> method takes a last modified date and checks it against the If-Modified-Since header of the request.</span></span> <span data-ttu-id="4f3ae-151">Üst bilgi varsa ve kaynak değiştirilmediyse, <xref:System.ServiceModel.Web.WebFaultException> http durum kodu 304 (değiştirilmez) içeren bir oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="4f3ae-151">If the header is present and the resource has not been modified since, a <xref:System.ServiceModel.Web.WebFaultException> with an HTTP status code 304 (Not Modified) is thrown.</span></span>  
  
 <span data-ttu-id="4f3ae-152">PUT, POST ve DELETE istekleri için <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> bir kaynağın geçerli ETag değerini alır.</span><span class="sxs-lookup"><span data-stu-id="4f3ae-152">For PUT, POST, and DELETE requests, <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> takes the current ETag value of a resource.</span></span> <span data-ttu-id="4f3ae-153">Geçerli ETag değeri null ise, yöntemi If-None-Match üst bilgisinin "\*" değeri olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="4f3ae-153">If the current ETag value is null, the method checks that the If-None- Match header has a value of "\*".</span></span>  <span data-ttu-id="4f3ae-154">Geçerli ETag değeri varsayılan bir değer değilse, yöntemi geçerli ETag değerini isteğin IF-Match üst bilgisine karşı denetler.</span><span class="sxs-lookup"><span data-stu-id="4f3ae-154">If the current ETag value is not a default value, then the method checks the current ETag value against the If- Match header of the request.</span></span> <span data-ttu-id="4f3ae-155">Her iki durumda da, <xref:System.ServiceModel.Web.WebFaultException> beklenen üst bilgi istekte yoksa ve değeri koşullu denetimi karşılamıyorsa ve yanıtın ETag üst bilgisini geçerli ETag değerine ayarlarsa, yöntem BIR http durum kodu 412 (Önkoşul başarısız) ile bir oluşturur.</span><span class="sxs-lookup"><span data-stu-id="4f3ae-155">In either case, the method throws a <xref:System.ServiceModel.Web.WebFaultException> with an HTTP status code 412 (Precondition Failed) if the expected header is not present in the request or its value does not satisfy the conditional check and sets the ETag header of the response to the current ETag value.</span></span>  
  
 <span data-ttu-id="4f3ae-156">Hem `CheckConditional` Yöntemler hem de <xref:System.ServiceModel.Web.OutgoingWebResponseContext.SetETag%2A> yöntemi, yanıt üstbilgisinde ayarlanan ETag değerinin http belirtimine göre geçerli bir ETag olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="4f3ae-156">Both the `CheckConditional` methods and the <xref:System.ServiceModel.Web.OutgoingWebResponseContext.SetETag%2A> method ensures that the ETag value set on the response header is a valid ETag according to the HTTP specification.</span></span> <span data-ttu-id="4f3ae-157">Bu, zaten mevcut değilse ve iç çift tırnak karakterlerini doğru bir şekilde kaçış durumunda ETag değerini çift tırnak içine çevreleyen bir kapsayıcı içerir.</span><span class="sxs-lookup"><span data-stu-id="4f3ae-157">This includes surrounding the ETag value in double quotes if they are not already present and properly escaping any internal double quote characters.</span></span> <span data-ttu-id="4f3ae-158">Zayıf ETag karşılaştırması desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="4f3ae-158">Weak ETag comparison is not supported.</span></span>  
  
 <span data-ttu-id="4f3ae-159">Aşağıdaki örnek, bu yöntemlerin nasıl kullanılacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="4f3ae-159">The following example shows how to use these methods.</span></span>  
  
```csharp
[WebGet(UriTemplate = "{id}"), Description("Returns the specified customer from customers collection. Returns NotFound if there is no such customer. Supports conditional GET.")]
public Customer GetCustomer(string id)
{
    lock (writeLock)
    {
        // return NotFound if there is no item with the specified id.
        object itemEtag = customerEtags[id];
        if (itemEtag == null)
        {
            throw new WebFaultException(HttpStatusCode.NotFound);
        }
  
        // return NotModified if the client did a conditional GET and the customer item has not changed
        // since when the client last retrieved it
        WebOperationContext.Current.IncomingRequest.CheckConditionalRetrieve((long)itemEtag);
        Customer result = this.customers[id] as Customer;

        // set the customer etag before returning the result
        WebOperationContext.Current.OutgoingResponse.SetETag((long)itemEtag);
        return result;
    }
}
```  
  
## <a name="security-considerations"></a><span data-ttu-id="4f3ae-160">Güvenlikle İlgili Dikkat Edilmesi Gerekenler</span><span class="sxs-lookup"><span data-stu-id="4f3ae-160">Security Considerations</span></span>  
 <span data-ttu-id="4f3ae-161">Yanıt önbellekten sunulduğunda yetkilendirme gerçekleştirilmediğinden, yetkilendirme gerektiren isteklerin yanıtları önbelleğe alınmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="4f3ae-161">Requests that require authorization should not have their responses cached, because the authorization is not performed when the response is served from the cache.</span></span>  <span data-ttu-id="4f3ae-162">Bu tür yanıtların önbelleğe alınması, ciddi bir güvenlik güvenlik açığı ortaya çıkarabilir.</span><span class="sxs-lookup"><span data-stu-id="4f3ae-162">Caching such responses would introduce a serious security vulnerability.</span></span>  <span data-ttu-id="4f3ae-163">Genellikle, yetkilendirme gerektiren istekler kullanıcıya özgü veriler sağlar ve bu nedenle sunucu tarafında önbelleğe alma da yararlı değildir.</span><span class="sxs-lookup"><span data-stu-id="4f3ae-163">Usually, requests that require authorization provide user-specific data and therefore server-side caching is not even beneficial.</span></span>  <span data-ttu-id="4f3ae-164">Bu gibi durumlarda, istemci tarafı önbelleğe alma veya yalnızca hiç önbelleğe alma işlemleri daha uygun olacaktır.</span><span class="sxs-lookup"><span data-stu-id="4f3ae-164">In such situations, client-side caching or simply not caching at all will be more appropriate.</span></span>
