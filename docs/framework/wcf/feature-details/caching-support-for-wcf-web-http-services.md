---
title: WCF Web HTTP Hizmetleri için Önbelleğe Alma Desteği
ms.date: 03/30/2017
ms.assetid: 7f8078e0-00d9-415c-b8ba-c1b6d5c31799
ms.openlocfilehash: 63c83cc1af9a3ccfdbdd79f8d0480e6c29eaf2f3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185427"
---
# <a name="caching-support-for-wcf-web-http-services"></a><span data-ttu-id="07f5f-102">WCF Web HTTP Hizmetleri için Önbelleğe Alma Desteği</span><span class="sxs-lookup"><span data-stu-id="07f5f-102">Caching Support for WCF Web HTTP Services</span></span>

[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]<span data-ttu-id="07f5f-103">WCF Web HTTP hizmetlerinizde ASP.NET mevcut olan bildirimsel önbelleğe alma mekanizmasını kullanmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="07f5f-103">enables you to use the declarative caching mechanism already available in ASP.NET in your WCF Web HTTP services.</span></span> <span data-ttu-id="07f5f-104">Bu, WCF Web HTTP hizmet işlemlerinizden yanıtları önbelleğe alalet etmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="07f5f-104">This allows you to cache responses from your WCF Web HTTP service operations.</span></span> <span data-ttu-id="07f5f-105">Bir kullanıcı önbelleğe almak üzere yapılandırılan bir HTTP GET hizmetinize gönderdiğinde, ASP.NET önbelleğe alınmış yanıtı geri gönderir ve hizmet yöntemi çağrılmaz.</span><span class="sxs-lookup"><span data-stu-id="07f5f-105">When a user sends an HTTP GET to your service that is configured for caching, ASP.NET sends back the cached response and the service method is not called.</span></span> <span data-ttu-id="07f5f-106">Önbelleğin süresi dolduğunda, bir sonraki kullanıcı BIR HTTP GET gönderdiğinde, hizmet yönteminiz çağrılır ve yanıt bir kez daha önbelleğe alır.</span><span class="sxs-lookup"><span data-stu-id="07f5f-106">When the cache expires, the next time a user sends an HTTP GET, your service method is called and the response is once again cached.</span></span> <span data-ttu-id="07f5f-107">ASP.NET önbelleğe alma hakkında daha fazla bilgi için, [ASP.NET Önbelleğe Alma Genel Bakış'a](https://docs.microsoft.com/previous-versions/aspnet/ms178597(v=vs.100))bakın.</span><span class="sxs-lookup"><span data-stu-id="07f5f-107">For more information about ASP.NET caching, see [ASP.NET Caching Overview](https://docs.microsoft.com/previous-versions/aspnet/ms178597(v=vs.100)).</span></span>  
  
## <a name="basic-web-http-service-caching"></a><span data-ttu-id="07f5f-108">Temel Web HTTP Hizmet Önbelleğe Alma</span><span class="sxs-lookup"><span data-stu-id="07f5f-108">Basic Web HTTP Service Caching</span></span>  

  <span data-ttu-id="07f5f-109">WEB <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> HTTP hizmet önbelleğe almak için, <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute.RequirementsMode%2A> <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed> ASP.NET öncelikle hizmet ayarı veya <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Required>.</span><span class="sxs-lookup"><span data-stu-id="07f5f-109">To enable WEB HTTP service caching, you must first enable ASP.NET compatibility by applying the <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> to the service setting <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute.RequirementsMode%2A> to <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed> or <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Required>.</span></span>  
  
 <span data-ttu-id="07f5f-110">.NET Framework 4, önbellek <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> profil adı belirtmenize olanak tanıyan yeni bir öznitelik sunar.</span><span class="sxs-lookup"><span data-stu-id="07f5f-110">.NET Framework 4 introduces a new attribute called <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> that allows you to specify a cache profile name.</span></span> <span data-ttu-id="07f5f-111">Bu öznitelik bir hizmet işlemine uygulanır.</span><span class="sxs-lookup"><span data-stu-id="07f5f-111">This attribute is applied to a service operation.</span></span> <span data-ttu-id="07f5f-112">Aşağıdaki örnek, ASP.NET <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> uyumluluğunu etkinleştirmek için bir hizmete uygulanır ve önbelleğe alma işlemini `GetCustomer` yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="07f5f-112">The following example applies the <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> to a service to enable ASP.NET compatibility and configures the `GetCustomer` operation for caching.</span></span> <span data-ttu-id="07f5f-113">Öznitelik, <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> kullanılacak önbellek ayarlarını içeren bir önbellek profili belirtir.</span><span class="sxs-lookup"><span data-stu-id="07f5f-113">The <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> attribute specifies a cache profile that contains the cache settings to be used.</span></span>  
  
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
  
<span data-ttu-id="07f5f-114">Ayrıca, aşağıdaki örnekte gösterildiği gibi Web.config dosyasındaki ASP.NET uyumluluk modunu da açın.</span><span class="sxs-lookup"><span data-stu-id="07f5f-114">Also turn on ASP.NET compatibility mode in the Web.config file as shown in the following example.</span></span>  
  
```xml
<system.serviceModel>
  <serviceHostingEnvironment aspNetCompatibilityEnabled="true" />
</system.serviceModel>
```
  
> [!WARNING]
> <span data-ttu-id="07f5f-115">uyumluluk modu ASP.NET açık değilse ve <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> kullanılırsa bir özel durum atılır.</span><span class="sxs-lookup"><span data-stu-id="07f5f-115">If ASP.NET compatibility mode is not turned on and the <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> is used an exception is thrown.</span></span>  
  
 <span data-ttu-id="07f5f-116">Web.config yapılandırma dosyanıza eklenen önbellek profilini <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> tanımlar tarafından belirtilen önbellek profili adı.</span><span class="sxs-lookup"><span data-stu-id="07f5f-116">The cache profile name specified by the <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> identifies a cache profile that is added to your Web.config configuration file.</span></span> <span data-ttu-id="07f5f-117">Önbellek profili, aşağıdaki yapılandırma `outputCacheSetting` örneğinde gösterildiği gibi <bir> öğesiile tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="07f5f-117">The cache profile is defined with in a <`outputCacheSetting`> element as shown in the following configuration example.</span></span>  
  
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
  
 <span data-ttu-id="07f5f-118">Bu, ASP.NET uygulamaları için kullanılabilen yapılandırma öğesidir.</span><span class="sxs-lookup"><span data-stu-id="07f5f-118">This is the same configuration element that is available to ASP.NET applications.</span></span> <span data-ttu-id="07f5f-119">önbellek profilleri ASP.NET hakkında daha <xref:System.Web.Configuration.OutputCacheProfile>fazla bilgi için bkz.</span><span class="sxs-lookup"><span data-stu-id="07f5f-119">For more information about ASP.NET cache profiles, see <xref:System.Web.Configuration.OutputCacheProfile>.</span></span> <span data-ttu-id="07f5f-120">Web HTTP hizmetleri için önbellek profilindeki en `cacheDuration` önemli `varyByParam`öznitelikler şunlardır: ve.</span><span class="sxs-lookup"><span data-stu-id="07f5f-120">For Web HTTP services, the most important attributes in the cache profile are: `cacheDuration` and `varyByParam`.</span></span> <span data-ttu-id="07f5f-121">Bu özniteliklerin her ikisi de gereklidir.</span><span class="sxs-lookup"><span data-stu-id="07f5f-121">Both of these attributes are required.</span></span> <span data-ttu-id="07f5f-122">`cacheDuration`bir yanıtın saniyeler içinde önbelleğe alınması gereken süreyi ayarlar.</span><span class="sxs-lookup"><span data-stu-id="07f5f-122">`cacheDuration` sets the amount of time a response should be cached in seconds.</span></span> <span data-ttu-id="07f5f-123">`varyByParam`yanıtları önbelleğe almak için kullanılan bir sorgu dize parametresini belirtmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="07f5f-123">`varyByParam` allows you to specify a query string parameter that is used to cache responses.</span></span> <span data-ttu-id="07f5f-124">Farklı sorgu dize parametre değerleri ile yapılan tüm istekler ayrı ayrı önbelleğe alınır.</span><span class="sxs-lookup"><span data-stu-id="07f5f-124">All requests made with different query string parameter values are cached separately.</span></span> <span data-ttu-id="07f5f-125">Örneğin, ilk istek yapıldıktan `http://MyServer/MyHttpService/MyOperation?param=10`sonra, aynı URI ile yapılan sonraki tüm istekler önbelleğe alınmış yanıtı döndürülür (önbellek süresi dolmadığı sürece).</span><span class="sxs-lookup"><span data-stu-id="07f5f-125">For example, once an initial request is made to `http://MyServer/MyHttpService/MyOperation?param=10`, all subsequent requests made with the same URI would be returned the cached response (so long as the cache duration has not elapsed).</span></span> <span data-ttu-id="07f5f-126">Parametre sorgusu dize parametresi parametresi için farklı bir değeri olan benzer bir isteğe yönelik yanıtlar ayrı olarak önbelleğe alınır.</span><span class="sxs-lookup"><span data-stu-id="07f5f-126">Responses for a similar request that is the same but has a different value for the parameter query string parameter are cached separately.</span></span> <span data-ttu-id="07f5f-127">Bu ayrı önbelleğe alma davranışı `varyByParam` istemiyorsanız, "yok" olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="07f5f-127">If you do not want this separate caching behavior, set `varyByParam` to "none".</span></span>  
  
## <a name="sql-cache-dependency"></a><span data-ttu-id="07f5f-128">SQL Önbellek Bağımlılığı</span><span class="sxs-lookup"><span data-stu-id="07f5f-128">SQL Cache Dependency</span></span>  

  <span data-ttu-id="07f5f-129">Web HTTP hizmet yanıtları da bir SQL önbellek bağımlılığı ile önbelleğe alınabilir.</span><span class="sxs-lookup"><span data-stu-id="07f5f-129">Web HTTP service responses can also be cached with a SQL cache dependency.</span></span> <span data-ttu-id="07f5f-130">WCF Web HTTP hizmetiniz bir SQL veritabanında depolanan verilere bağlıysa, hizmetin yanıtını önbelleğe almak ve SQL veritabanı tablosundaki veriler değiştiğinde önbelleğe alınan yanıtı geçersiz kılabilir.</span><span class="sxs-lookup"><span data-stu-id="07f5f-130">If your WCF Web HTTP service depends on data stored in a SQL database, you may want to cache the service's response and invalidate the cached response when data in the SQL database table changes.</span></span> <span data-ttu-id="07f5f-131">Bu davranış tamamen Web.config dosyası içinde yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="07f5f-131">This behavior is configured completely within the Web.config file.</span></span> <span data-ttu-id="07f5f-132">İlk olarak, <`connectionStrings`> öğesinde bir bağlantı dizesi tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="07f5f-132">First, define a connection string in the <`connectionStrings`> element.</span></span>  
  
```xml
<connectionStrings>
  <add name="connectString"
       connectionString="Data Source=MyService;Initial Catalog=MyTestDatabase;Integrated Security=True"
       providerName="System.Data.SqlClient" />
</connectionStrings>
```  
  
 <span data-ttu-id="07f5f-133">Daha sonra aşağıdaki config örneğinde `caching` gösterildiği gibi <`system.web`> öğesi içinde <bir> öğesi içinde SQL önbellek bağımlılığı etkinleştirmek gerekir.</span><span class="sxs-lookup"><span data-stu-id="07f5f-133">Then you must enable SQL cache dependency within a <`caching`> element within the <`system.web`> element as shown in the following config example.</span></span>  
  
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
  
 <span data-ttu-id="07f5f-134">Burada SQL önbellek bağımlılığı etkinleştirilir ve 1000 milisaniyelik bir yoklama süresi ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="07f5f-134">Here SQL cache dependency is enabled and a polling time of 1000 milliseconds is set.</span></span> <span data-ttu-id="07f5f-135">Yoklama süresi her zaman veritabanı tablosu güncelleştirmeleri için denetlenir.</span><span class="sxs-lookup"><span data-stu-id="07f5f-135">Each time the polling time elapses the database table is checked for updates.</span></span> <span data-ttu-id="07f5f-136">Değişiklikler algılanırsa önbelleğin içeriği kaldırılır ve hizmet işlemi bir sonraki çağrıldığinde yeni bir yanıt önbelleğe alınır.</span><span class="sxs-lookup"><span data-stu-id="07f5f-136">If changes are detected the contents of the cache are removed and the next time the service operation is invoked a new response is cached.</span></span> <span data-ttu-id="07f5f-137"><`sqlCacheDependency`> öğesi içinde veritabanları ekleyin ve aşağıdaki örnekte `databases` gösterildiği gibi <> öğesi içinde bağlantı dizeleri başvuru.</span><span class="sxs-lookup"><span data-stu-id="07f5f-137">Within the <`sqlCacheDependency`> element add the databases and reference the connection strings within the <`databases`> element as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="07f5f-138">Daha sonra, aşağıdaki örnekte gösterildiği gibi `caching` <> öğesi içindeki çıktı önbelleği ayarlarını yapılandırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="07f5f-138">Next you must configure the output cache settings within the <`caching`> element as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="07f5f-139">Burada önbellek süresi 60 saniye `varyByParam` olarak ayarlanır, hiçbiri `sqlDependency` olarak ayarlanır ve iki nokta üst üste ayrılmış veritabanı adı/tablo çiftleri yarı sütunlu sınırlı bir listeye ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="07f5f-139">Here the cache duration is set to 60 seconds, `varyByParam` is set to none, and `sqlDependency` is set to a semicolon-delimited list of database name/table pairs separated by colons.</span></span> <span data-ttu-id="07f5f-140">İçteki `MyTable` veriler değiştirildiğinde, hizmet işlemi için önbelleğe alınan yanıt kaldırılır ve işlem çağrıldığında yeni bir yanıt oluşturulur (hizmet işlemi çağırılarak), önbelleğe alınır ve istemciye döndürülür.</span><span class="sxs-lookup"><span data-stu-id="07f5f-140">When data in `MyTable` is changed the cached response for the service operation is removed and when the operation is invoked a new response is generated (by calling the service operation), cached, and returned to the client.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="07f5f-141">Bir SQL veritabanına erişmek için ASP.NET [için ASP.NET SQL Server Registration Tool'u](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms229862(v=vs.90))kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="07f5f-141">For ASP.NET to access a SQL database, you must use the [ASP.NET SQL Server Registration Tool](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms229862(v=vs.90)).</span></span> <span data-ttu-id="07f5f-142">Buna ek olarak, veritabanı na ve tabloya uygun kullanıcı hesabı erişimine izin vermelisiniz.</span><span class="sxs-lookup"><span data-stu-id="07f5f-142">In addition you must allow the appropriate user account access to the database and table.</span></span> <span data-ttu-id="07f5f-143">Daha fazla bilgi için [bkz.](https://docs.microsoft.com/previous-versions/aspnet/ht43wsex(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="07f5f-143">For more information, see [Accessing SQL Server from a Web Application](https://docs.microsoft.com/previous-versions/aspnet/ht43wsex(v=vs.100)).</span></span>  
  
## <a name="conditional-http-get-based-caching"></a><span data-ttu-id="07f5f-144">Koşullu HTTP GET Tabanlı Önbelleğe Alma</span><span class="sxs-lookup"><span data-stu-id="07f5f-144">Conditional HTTP GET Based Caching</span></span>  

  <span data-ttu-id="07f5f-145">Web HTTP senaryolarında koşullu bir HTTP GET genellikle [http belirtiminde](https://www.w3.org/Protocols/rfc2616/rfc2616.html)açıklandığı gibi akıllı HTTP önbelleğe uygulamak için hizmetler tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="07f5f-145">In Web HTTP scenarios a conditional HTTP GET is often used by services to implement intelligent HTTP caching as described in the [HTTP Specification](https://www.w3.org/Protocols/rfc2616/rfc2616.html).</span></span> <span data-ttu-id="07f5f-146">Bunu yapmak için, hizmetIN HTTP yanıtındaki ETag üstbilginin değerini ayarlaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="07f5f-146">To do this, the service must set the value of the ETag header in the HTTP response.</span></span> <span data-ttu-id="07f5f-147">Ayrıca, ETag belirtilenlerden herhangi birinin geçerli ETag ile eşleşip eşleşmediğini görmek için HTTP isteğindeki If-None-Match üstbilgisini de denetlemelidir.</span><span class="sxs-lookup"><span data-stu-id="07f5f-147">It also must check the If-None-Match header in the HTTP request to see whether any of the ETag specified matches the current ETag.</span></span>  
  
 <span data-ttu-id="07f5f-148">GET ve HEAD <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> istekleri için bir ETag değeri alır ve isteğin If-None-Match üstbilgisi ile karşılaştırın.</span><span class="sxs-lookup"><span data-stu-id="07f5f-148">For GET and HEAD requests, <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> takes an ETag value and checks it against the If-None-Match header of the request.</span></span> <span data-ttu-id="07f5f-149">Üstbilgi varsa ve bir eşleşme varsa, <xref:System.ServiceModel.Web.WebFaultException> bir HTTP durum kodu 304 (Değiştirilmemiş) ile bir atılır ve eşleşen ETag ile yanıta bir ETag üstbilgisi eklenir.</span><span class="sxs-lookup"><span data-stu-id="07f5f-149">If the header is present and there is a match, a <xref:System.ServiceModel.Web.WebFaultException> with an HTTP status code 304 (Not Modified) is thrown and an ETag header is added to the response with the matching ETag.</span></span>  
  
 <span data-ttu-id="07f5f-150">Yöntemin <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> bir aşırı yüklemesi son değiştirilmiş bir tarih alır ve isteğin If-Modified-Since üstbilgisi ile karşılaştırın.</span><span class="sxs-lookup"><span data-stu-id="07f5f-150">One overload of the <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> method takes a last modified date and checks it against the If-Modified-Since header of the request.</span></span> <span data-ttu-id="07f5f-151">Üstbilgi mevcutsa ve kaynak o zamandan beri <xref:System.ServiceModel.Web.WebFaultException> değiştirilmemişse, http durum kodu 304 (Değiştirilmemiş) ile bir a.ş. atılır.</span><span class="sxs-lookup"><span data-stu-id="07f5f-151">If the header is present and the resource has not been modified since, a <xref:System.ServiceModel.Web.WebFaultException> with an HTTP status code 304 (Not Modified) is thrown.</span></span>  
  
 <span data-ttu-id="07f5f-152">PUT, POST ve DELETE <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> istekleri için kaynağın geçerli ETag değerini alır.</span><span class="sxs-lookup"><span data-stu-id="07f5f-152">For PUT, POST, and DELETE requests, <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> takes the current ETag value of a resource.</span></span> <span data-ttu-id="07f5f-153">Geçerli ETag değeri null ise, yöntem If-None- Match üstbilgisinin "\*" değerine sahip olduğunu denetler.</span><span class="sxs-lookup"><span data-stu-id="07f5f-153">If the current ETag value is null, the method checks that the If-None- Match header has a value of "\*".</span></span>  <span data-ttu-id="07f5f-154">Geçerli ETag değeri varsayılan bir değer değilse, yöntem geçerli ETag değerini isteğin If- Match üstbilgisi ile karşıya denetler.</span><span class="sxs-lookup"><span data-stu-id="07f5f-154">If the current ETag value is not a default value, then the method checks the current ETag value against the If- Match header of the request.</span></span> <span data-ttu-id="07f5f-155">Her iki durumda da, <xref:System.ServiceModel.Web.WebFaultException> beklenen üstbilgi istekte yoksa veya değeri koşullu denetimi karşılamazsa ve geçerli ETag değerine yanıtın ETag üstbilgisini ayarlarsa, yöntem bir HTTP durum kodu 412 (Ön Koşul Başarısız) ile a atar.</span><span class="sxs-lookup"><span data-stu-id="07f5f-155">In either case, the method throws a <xref:System.ServiceModel.Web.WebFaultException> with an HTTP status code 412 (Precondition Failed) if the expected header is not present in the request or its value does not satisfy the conditional check and sets the ETag header of the response to the current ETag value.</span></span>  
  
 <span data-ttu-id="07f5f-156">Hem `CheckConditional` yöntem hem <xref:System.ServiceModel.Web.OutgoingWebResponseContext.SetETag%2A> de yöntem, yanıt başlığında ayarlanan ETag değerinin HTTP belirtimine göre geçerli bir ETag olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="07f5f-156">Both the `CheckConditional` methods and the <xref:System.ServiceModel.Web.OutgoingWebResponseContext.SetETag%2A> method ensures that the ETag value set on the response header is a valid ETag according to the HTTP specification.</span></span> <span data-ttu-id="07f5f-157">Bu, eTag değerini çift tırnak içinde çevrelemeyi içerir, eğer zaten mevcut değillerse ve herhangi bir dahili çift tırnak karakterlerinden düzgün bir şekilde kaçıyorlarsa.</span><span class="sxs-lookup"><span data-stu-id="07f5f-157">This includes surrounding the ETag value in double quotes if they are not already present and properly escaping any internal double quote characters.</span></span> <span data-ttu-id="07f5f-158">Zayıf ETag karşılaştırması desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="07f5f-158">Weak ETag comparison is not supported.</span></span>  
  
 <span data-ttu-id="07f5f-159">Aşağıdaki örnekte, bu yöntemlerin nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="07f5f-159">The following example shows how to use these methods.</span></span>  
  
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
  
## <a name="security-considerations"></a><span data-ttu-id="07f5f-160">Güvenlikle İlgili Dikkat Edilmesi Gerekenler</span><span class="sxs-lookup"><span data-stu-id="07f5f-160">Security Considerations</span></span>  
 <span data-ttu-id="07f5f-161">Yetkilendirme önbellekten sunulduğunda yetkilendirme gerçekleştirilmediği için yetkilendirme gerektiren isteklerin yanıtlarının önbelleğe alınmaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="07f5f-161">Requests that require authorization should not have their responses cached, because the authorization is not performed when the response is served from the cache.</span></span>  <span data-ttu-id="07f5f-162">Bu tür yanıtların önbelleğe alınmış bir şekilde önbelleğe alınmış bir güvenlik açığı na neden olur.</span><span class="sxs-lookup"><span data-stu-id="07f5f-162">Caching such responses would introduce a serious security vulnerability.</span></span>  <span data-ttu-id="07f5f-163">Genellikle, yetkilendirme gerektiren istekler kullanıcıya özgü veriler sağlar ve bu nedenle sunucu tarafı önbelleğe alma bile yararlı değildir.</span><span class="sxs-lookup"><span data-stu-id="07f5f-163">Usually, requests that require authorization provide user-specific data and therefore server-side caching is not even beneficial.</span></span>  <span data-ttu-id="07f5f-164">Bu gibi durumlarda, istemci tarafı önbelleğe alma veya sadece hiç önbelleğe almamak daha uygun olacaktır.</span><span class="sxs-lookup"><span data-stu-id="07f5f-164">In such situations, client-side caching or simply not caching at all will be more appropriate.</span></span>
