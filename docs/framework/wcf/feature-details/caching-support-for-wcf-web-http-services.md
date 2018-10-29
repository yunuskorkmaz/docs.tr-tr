---
title: WCF Web HTTP Hizmetleri için Önbelleğe Alma Desteği
ms.date: 03/30/2017
ms.assetid: 7f8078e0-00d9-415c-b8ba-c1b6d5c31799
ms.openlocfilehash: 6c601b19a0b3b9b3eddbd686c316ce7e2cdf7778
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2018
ms.locfileid: "50196810"
---
# <a name="caching-support-for-wcf-web-http-services"></a>WCF Web HTTP Hizmetleri için Önbelleğe Alma Desteği
[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] WCF Web HTTP hizmetlerinizi ASP.NET'te zaten kullanılabilen bildirim temelli önbelleğe alma mekanizması kullanmanıza olanak sağlar. Bu, önbellek yanıtları WCF Web HTTP hizmet işlemlerinizi sağlar. Bir kullanıcı bir HTTP GET önbelleğe almak üzere yapılandırıldığında hizmetinize gönderdiğinde, ASP.NET, önbelleğe alınan yanıtı geri gönderir ve hizmet yöntemi çağrılmadı. Önbellek, bir kullanıcının bir HTTP GET gönderdiği sonraki süresi dolduğunda, hizmet yönteminiz olarak adlandırılır ve yanıt yine önbelleğe alınır. ASP.NET önbelleğe alma hakkında daha fazla bilgi için bkz. [ASP.NET önbelleğe alma genel bakış](https://go.microsoft.com/fwlink/?LinkId=152534)  
  
## <a name="basic-web-http-service-caching"></a>Temel Web HTTP hizmeti, önbelleğe alma  
 WEB HTTP etkinleştirmek için önbellek hizmeti ilk ASP.NET uyumluluk uygulayarak etkinleştirmelisiniz <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> hizmet ayarına <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute.RequirementsMode%2A> için <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed> veya <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Required>.  
  
 [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)] adlı yeni bir öznitelik tanıtır <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> önbellek profili adını belirtmenize olanak verir. Bu öznitelik, bir hizmet işlemine uygulanır. Aşağıdaki örnek geçerli <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> ASP.NET uyumluluk sağlamak için bir hizmete ve yapılandırır `GetCustomer` önbelleğe alma işlemi. <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> Kullanılması için önbellek ayarlarını içeren bir önbellek profili özniteliğini belirtir.  
  
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
  
 Ayrıca aşağıdaki örnekte gösterildiği gibi Web.config dosyasına ASP.NET uyumluluk modunda açmanız gerekir.  
  
```xml
<system.serviceModel>
  <serviceHostingEnvironment aspNetCompatibilityEnabled="true" />
</system.serviceModel>
```
  
> [!WARNING]
>  ASP.NET uyumluluk modunun açık değilse ve <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> kullanılan bir özel durum oluşturulur.  
  
 Tarafından belirtilen önbellek profili adı <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> Web.config yapılandırma dosyasına eklenen bir önbellek profili tanımlar. Önbellek profili ile tanımlanan bir <`outputCacheSetting`> yapılandırma aşağıdaki örnekte gösterildiği gibi bir öğe.  
  
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
  
 ASP.NET uygulamaları için kullanılabilir olan aynı yapılandırma öğesi budur. ASP.NET önbellek profilleri hakkında daha fazla bilgi için bkz. <xref:System.Web.Configuration.OutputCacheProfile>. Web HTTP Hizmetleri için önbellek profili en önemli öznitelikleri şunlardır: `cacheDuration` ve `varyByParam`. Bu öznitelikleri ikisi de gereklidir. `cacheDuration` saniyeler içinde bir yanıt önbelleğe alınması gereken süre miktarını ayarlar. `varyByParam` Önbellek yanıtları için kullanılan bir sorgu dizesi parametresi belirlemenize olanak tanır. Farklı bir sorgu dizesi parametre değerleriniz ile yapılan tüm istekleri ayrı olarak önbelleğe alınır. Örneğin, bir ilk istek için yapıldıktan sonra `http://MyServer/MyHttpService/MyOperation?param=10`, (önbelleğe alma süresi değil geçen sürece) aynı URI ile yapılan tüm sonraki istekleri önbelleğe alınan yanıt döndürülür. Yanıtlar aynı ancak farklı bir değer parametresi sorgu dizesi parametresi için benzer bir istek için ayrı olarak önbelleğe alınır. Bu ayrı önbelleğe alma davranışı istemiyorsanız ayarlamak `varyByParam` "none".  
  
## <a name="sql-cache-dependency"></a>SQL önbellek bağımlılığı  
 Web HTTP hizmeti yanıtlarını olan SQL önbellek bağımlılık önbelleğe alınabilir. Bir SQL veritabanı'nda depolanan veriler, WCF Web HTTP hizmeti bağımlı olması durumunda, hizmetin yanıt önbelleğe alma ve tablosu değişiklikleri verileri SQL veritabanı, önbelleğe alınan yanıtın geçersiz kılmak isteyebilirsiniz. Bu davranış, Web.config dosyasının içinde tamamen yapılandırılır. Önce bir bağlantı dizesinde tanımlamanız gerekir <`connectionStrings`> öğesi.  
  
```xml
<connectionStrings>
  <add name="connectString"
       connectionString="Data Source=MyService;Initial Catalog=MyTestDatabase;Integrated Security=True"
       providerName="System.Data.SqlClient" />
</connectionStrings>
```  
  
 SQL önbellek bağımlılığı etkinleştirmelisiniz sonra bir <`caching`> öğesi içinde <`system.web`> yapılandırma aşağıdaki örnekte gösterildiği gibi bir öğe.  
  
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
  
 SQL önbellek bağımlılık burada etkinleştirildikten ve 1000 milisaniye cinsinden yoklama süresini ayarlayın. Yoklama süresi sona erdiğinde veritabanı tablosunun her zaman güncelleştirmeleri denetlenir. Önbelleğinin içeriğini kaldırılır ve yeni bir yanıt hizmet işlemi başlatıldığında çağrılır algılanırsa önbelleğe alınır. İçinde <`sqlCacheDependency`> öğesi veritabanlarını ekleyin ve bağlantı dizeleri içinde başvuru <`databases`> Aşağıdaki örnekte gösterildiği gibi bir öğe.  
  
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
  
 Ardından içinde çıktı önbellek ayarlarını yapılandırın <`caching`> Aşağıdaki örnekte gösterildiği gibi bir öğe.  
  
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
  
 Önbellek süresi 60 saniye Burada ayarlanan `varyByParam` hiçbiri olarak ayarlandı ve `sqlDependency` veritabanı adı/tablo çiftlerin virgülle ayırarak noktalı virgülle ayrılmış listesini ayarlanır. Zaman içinde veri `MyTable` önbelleğe alınan yanıtın hizmet işlemi kaldırılır ve işlem çağrıldığında yeni bir yanıt (hizmet işlemi çağırarak) oluşturulan, önbelleğe alınmış ve istemciye döndürülen değiştirilir.  
  
> [!IMPORTANT]
>  Bir SQL veritabanına erişmek ASP.NET için kullanmanız gereken [ASP.NET SQL Server kayıt aracı](https://go.microsoft.com/fwlink/?LinkId=152536). Ayrıca veritabanı ve tablo uygun kullanıcı hesabı erişimi izin vermeniz gerekir. Daha fazla bilgi için [SQL Server'dan erişen bir Web uygulaması](https://go.microsoft.com/fwlink/?LinkId=178988).  
  
## <a name="conditional-http-get-based-caching"></a>Koşullu HTTP tabanlı önbelleğe alma  
 Web HTTP senaryolarda koşullu bir HTTP GET genellikle Hizmetleri tarafından HTTP akıllı önbellek açıklandığı gibi uygulamak için kullanılan [HTTP belirtimini](https://go.microsoft.com/fwlink/?LinkId=165800). Hizmet Bunu yapmak için ETag üstbilgi değerini HTTP yanıtında ayarlamanız gerekir. If-None-Match üst bilgisinde belirtilen ETag hiçbirini eşleşip eşleşmediğini geçerli ETag görmek için HTTP isteği aynı zamanda teslim almanız gerekir.  
  
 GET ve HEAD isteklerini <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> bir ETag değeri alır ve isteğin If-None-Match üst bilgisi karşı denetler. Üst bilgi varsa ve bir eşleşme bir <xref:System.ServiceModel.Web.WebFaultException> 304 (değiştirilmedi) durum kodu ile HTTP oluşturulur ve bir ETag üstbilgi eşleşen ETag Yanıtla eklenir.  
  
 Bir aşırı yüklemesini <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> yöntemi son değiştirilme tarihi alır ve If-Modified-Since başlığı isteğin karşı denetler. Üst bilgi varsa ve bu yana, kaynak değiştirilmemiş bir <xref:System.ServiceModel.Web.WebFaultException> 304 (değiştirilmedi) durum kodu ile bir HTTP durum oluşturulur.  
  
 PUT, POST ve DELETE istekleri <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> kaynağın geçerli ETag değeri alır. Geçerli ETag değeri null ise, yöntem If-None-Match üst bilgisi değeri olup olmadığını denetler "*".  Geçerli ETag değeri, varsayılan bir değer değil, yöntem geçerli ETag değeri isteğin IF - Match üst karşı denetler. Her iki durumda da çağırılıyorsa yöntem bir <xref:System.ServiceModel.Web.WebFaultException> beklenen üst bilgi istekte mevcut değil veya değerini koşullu onay karşılamaz ve yanıtın geçerli ETag için ETag üstbilgisini ayarlar 412 (önkoşul başarısız) ile bir HTTP durum kodu değer.  
  
 Her iki `CheckConditional` yöntemleri ve <xref:System.ServiceModel.Web.OutgoingWebResponseContext.SetETag%2A> yöntemi yanıt üstbilgisi ayarlanan ETag değeri geçerli bir ETag HTTP belirtimine göre olmasını sağlar. Bu, zaten yoksa, çift tırnak ETag değeri çevreleyen ve düzgün şekilde herhangi bir iç çift tırnak işareti karakteri kaçış içerir. Zayıf bir ETag karşılaştırma desteklenmiyor.  
  
 Aşağıdaki örnek, bu yöntemlerin nasıl kullanılacağını gösterir.  
  
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
  
## <a name="security-considerations"></a>Güvenlik Değerlendirmeleri  
 Yetkilendirme gerektiren isteklerinin yanıt önbellekten sunulduğunda yetkilendirme gerçekleştirilmeyen çünkü yanıtlarını önbelleğe alınmış, sahip olmamalıdır.  Bu tür yanıtları önbelleğe alma ciddi bir güvenlik açığı tanıtır.  Genellikle, kullanıcıya özgü veriler yetkilendirme gerektiren isteklerinin sağlar ve bu nedenle sunucu tarafı önbelleğe alma bile yararlı değildir.  İstemci tarafı önbelleğe alma veya yalnızca tüm önbelleğe alma değil, bu gibi durumlarda, daha uygun olacaktır.
