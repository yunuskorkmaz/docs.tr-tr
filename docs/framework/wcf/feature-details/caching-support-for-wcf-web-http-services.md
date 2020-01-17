---
title: WCF Web HTTP Hizmetleri için Önbelleğe Alma Desteği
ms.date: 03/30/2017
ms.assetid: 7f8078e0-00d9-415c-b8ba-c1b6d5c31799
ms.openlocfilehash: b6247dd6c178b355fa4de271415b7cac12f6c629
ms.sourcegitcommit: ed3f926b6cdd372037bbcc214dc8f08a70366390
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/16/2020
ms.locfileid: "76116674"
---
# <a name="caching-support-for-wcf-web-http-services"></a>WCF Web HTTP Hizmetleri için Önbelleğe Alma Desteği

[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)], WCF Web HTTP hizmetinizdeki ASP.NET içinde zaten bulunan bildirime dayalı önbelleğe alma mekanizmasını kullanmanıza olanak sağlar. Bu, WCF Web HTTP hizmet işlemlerinizin yanıtlarını önbelleğe almanıza olanak sağlar. Bir kullanıcı hizmetinize önbelleğe alma için yapılandırılmış bir HTTP Al gönderdiğinde, ASP.NET önbelleğe alınan yanıtı geri gönderir ve hizmet yöntemi çağrılmaz. Önbelleğin süresi dolarsa, bir Kullanıcı bir sonraki HTTP GET gönderdiğinde, hizmet yönteminiz çağrılır ve yanıt yeniden önbelleğe alınır. ASP.NET önbelleğe alma hakkında daha fazla bilgi için bkz. [ASP.net Caching Overview](https://docs.microsoft.com/previous-versions/aspnet/ms178597(v=vs.100)).  
  
## <a name="basic-web-http-service-caching"></a>Temel Web HTTP hizmeti önbelleğe alma  

  WEB HTTP hizmeti önbelleğe almayı etkinleştirmek için, <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute.RequirementsMode%2A> <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed> veya <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Required>hizmet ayarına uygulayarak, önce ASP.NET uyumluluğunu etkinleştirmeniz gerekir.  
  
 .NET Framework 4, bir önbellek profili adı belirtmenize izin veren <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> adlı yeni bir öznitelik tanıtır. Bu öznitelik bir hizmet işlemine uygulanır. Aşağıdaki örnek, ASP.NET uyumluluğunu etkinleştirmek ve önbelleğe almak için `GetCustomer` işlemini yapılandıran bir hizmete <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> uygular. <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> özniteliği, kullanılacak önbellek ayarlarını içeren bir önbellek profili belirtir.  
  
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
  
Ayrıca, aşağıdaki örnekte gösterildiği gibi Web. config dosyasında ASP.NET uyumluluk modunu da açın.  
  
```xml
<system.serviceModel>
  <serviceHostingEnvironment aspNetCompatibilityEnabled="true" />
</system.serviceModel>
```
  
> [!WARNING]
> ASP.NET uyumluluk modu açık değilse ve <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> kullanılırsa bir özel durum oluşturulur.  
  
 <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> tarafından belirtilen önbellek profili adı, Web. config yapılandırma dosyanıza eklenen bir önbellek profilini tanımlar. Önbellek profili, aşağıdaki yapılandırma örneğinde gösterildiği gibi bir <`outputCacheSetting`> öğesi ile tanımlanır.  
  
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
  
 Bu, ASP.NET uygulamaları için kullanılabilen yapılandırma öğesidir. ASP.NET önbellek profilleri hakkında daha fazla bilgi için bkz. <xref:System.Web.Configuration.OutputCacheProfile>. Web HTTP Hizmetleri için önbellek profilindeki en önemli öznitelikler şunlardır: `cacheDuration` ve `varyByParam`. Bu özniteliklerin her ikisi de gereklidir. `cacheDuration`, bir yanıtın saniye cinsinden önbelleğe alınması gereken süreyi belirler. `varyByParam`, yanıtları önbelleğe almak için kullanılan bir sorgu dizesi parametresi belirtmenize izin verir. Farklı sorgu dizesi parametre değerleriyle yapılan tüm istekler ayrı olarak önbelleğe alınır. Örneğin, `http://MyServer/MyHttpService/MyOperation?param=10`için bir başlangıç isteği yapıldıktan sonra, aynı URI ile yapılan sonraki tüm istekler önbelleğe alınan yanıtı (önbellek süresi geçmediğinde uzun) döndürülür. Benzer bir istek için aynı ancak parametre sorgu dizesi parametresi için farklı bir değere sahip yanıtlar ayrı olarak önbelleğe alınır. Bu ayrı önbelleğe alma davranışını istemiyorsanız, `varyByParam` "none" olarak ayarlayın.  
  
## <a name="sql-cache-dependency"></a>SQL önbellek bağımlılığı  

  Web HTTP hizmet yanıtları bir SQL önbellek bağımlılığı ile de önbelleğe alınabilir. WCF Web HTTP hizmetiniz bir SQL veritabanında depolanan verilere bağımlıysa, SQL veritabanı tablosundaki veriler değiştiğinde hizmetin yanıtını önbelleğe almak ve önbelleğe alınmış yanıtı geçersiz kılmak isteyebilirsiniz. Bu davranış, Web. config dosyası içinde tamamen yapılandırılır. İlk olarak, <`connectionStrings`> öğesinde bir bağlantı dizesi tanımlayın.  
  
```xml
<connectionStrings>
  <add name="connectString"
       connectionString="Data Source=MyService;Initial Catalog=MyTestDatabase;Integrated Security=True"
       providerName="System.Data.SqlClient" />
</connectionStrings>
```  
  
 Daha sonra, aşağıdaki yapılandırma örneğinde gösterildiği gibi <`system.web`> öğesi içindeki bir <`caching`> öğesinde SQL önbellek bağımlılığını etkinleştirmeniz gerekir.  
  
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
  
 Burada SQL önbellek bağımlılığı etkindir ve 1000 milisaniye bir yoklama süresi ayarlanır. Yoklama süresi her geçtiğinde, veritabanı tablosunu güncelleştirme için denetlenir. Değişiklikler algılanırsa, önbelleğin içerikleri kaldırılır ve hizmet işleminin bir sonraki çağrılışında yeni bir yanıt önbelleğe alınır. `sqlCacheDependency`> öğesi içinde, aşağıdaki örnekte gösterildiği gibi veritabanlarını ekleyin ve <`databases`> öğesi içindeki bağlantı dizelerine başvurun.  
  
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
  
 Ardından, aşağıdaki örnekte gösterildiği gibi <`caching`> öğesi içindeki çıktı önbelleği ayarlarını yapılandırmanız gerekir.  
  
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
  
 Burada önbellek süresi 60 saniyeye ayarlanır, `varyByParam` None olarak ayarlanır ve `sqlDependency` noktalı virgülle ayrılmış veritabanı adı/tablo çiftleri listesini iki noktayla ayırarak ayarlar. `MyTable` veri değiştirildiğinde, hizmet işlemi için önbelleğe alınmış yanıt kaldırılır ve işlem çağrıldığında yeni bir yanıt oluşturulur (hizmet işlemini çağırarak), önbelleğe alınır ve istemciye döndürülür.  
  
> [!IMPORTANT]
> ASP.NET 'in bir SQL veritabanına erişmesi için [ASP.NET SQL Server kayıt aracını](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms229862(v=vs.90))kullanmanız gerekir. Ayrıca, uygun Kullanıcı hesabının veritabanına ve tabloya erişimine izin vermeniz gerekir. Daha fazla bilgi için bkz. [bir Web uygulamasından SQL Server erişme](https://docs.microsoft.com/previous-versions/aspnet/ht43wsex(v=vs.100)).  
  
## <a name="conditional-http-get-based-caching"></a>Koşullu HTTP alma tabanlı önbelleğe alma  

  Web HTTP senaryolarında Koşullu HTTP GET, genellikle [http belirtiminde](https://www.w3.org/Protocols/rfc2616/rfc2616.html)açıklandığı gıbı akıllı http önbelleği uygulamak için kullanılır. Bunu yapmak için hizmet, HTTP yanıtında ETag üst bilgisinin değerini ayarlamış olmalıdır. Ayrıca, belirtilen ETag öğesinin geçerli ETag ile eşleşip eşleşmediğini görmek için HTTP isteğindeki If-None-Match üst bilgisini denetmelidir.  
  
 GET ve HEAD istekleri için <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> bir ETag değeri alır ve isteğin If-None-Match üst bilgisine karşı denetler. Üst bilgi varsa ve bir eşleşme varsa, HTTP durum kodu 304 (değiştirilmez) ile bir <xref:System.ServiceModel.Web.WebFaultException> oluşturulur ve eşleşen ETag ile yanıta bir ETag üst bilgisi eklenir.  
  
 <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> yönteminin bir aşırı yüklemesi son değiştirilme tarihi alır ve isteğin If-Modified-Since üst bilgisine karşı denetler. Üst bilgi varsa ve kaynak değiştirilmediyse, HTTP durum kodu 304 (değiştirilmez) içeren bir <xref:System.ServiceModel.Web.WebFaultException> oluşturulur.  
  
 PUT, POST ve DELETE istekleri için <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> bir kaynağın geçerli ETag değerini alır. Geçerli ETag değeri null ise, yöntemi If-None-Match üst bilgisinin "*" değeri olup olmadığını denetler.  Geçerli ETag değeri varsayılan bir değer değilse, yöntemi geçerli ETag değerini isteğin IF-Match üst bilgisine karşı denetler. Her iki durumda da, beklenen üst bilgi istekte yoksa ve değeri koşullu denetimi karşılamıyorsa ve yanıtın ETag üstbilgisini geçerli ETag değerine ayarlarsa, yöntemi HTTP durum kodu 412 (Önkoşul başarısız) ile bir <xref:System.ServiceModel.Web.WebFaultException> oluşturur.  
  
 `CheckConditional` yöntemlerinin ve <xref:System.ServiceModel.Web.OutgoingWebResponseContext.SetETag%2A> yönteminin her ikisi de, yanıt üstbilgisinde ayarlanan ETag değerin HTTP belirtimine göre geçerli bir ETag olmasını sağlar. Bu, zaten mevcut değilse ve iç çift tırnak karakterlerini doğru bir şekilde kaçış durumunda ETag değerini çift tırnak içine çevreleyen bir kapsayıcı içerir. Zayıf ETag karşılaştırması desteklenmez.  
  
 Aşağıdaki örnek, bu yöntemlerin nasıl kullanılacağını göstermektedir.  
  
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
  
## <a name="security-considerations"></a>Güvenlik Konuları  
 Yanıt önbellekten sunulduğunda yetkilendirme gerçekleştirilmediğinden, yetkilendirme gerektiren isteklerin yanıtları önbelleğe alınmamalıdır.  Bu tür yanıtların önbelleğe alınması, ciddi bir güvenlik güvenlik açığı ortaya çıkarabilir.  Genellikle, yetkilendirme gerektiren istekler kullanıcıya özgü veriler sağlar ve bu nedenle sunucu tarafında önbelleğe alma da yararlı değildir.  Bu gibi durumlarda, istemci tarafı önbelleğe alma veya yalnızca hiç önbelleğe alma işlemleri daha uygun olacaktır.
