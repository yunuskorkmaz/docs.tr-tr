---
title: WCF Web HTTP Hizmetleri için Önbelleğe Alma Desteği
ms.date: 03/30/2017
ms.assetid: 7f8078e0-00d9-415c-b8ba-c1b6d5c31799
ms.openlocfilehash: 8272ece5fcaf395b0ec8191afae8eabc998c7f8b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33496831"
---
# <a name="caching-support-for-wcf-web-http-services"></a>WCF Web HTTP Hizmetleri için Önbelleğe Alma Desteği
[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] WCF Web HTTP hizmetlerinizi ASP.NET zaten mevcut bir bildirim temelli önbelleğe alma mekanizması kullanmanıza olanak sağlar. Bu, önbelleği yanıtlarını WCF Web HTTP hizmeti işlemlerinden sağlar. Bir kullanıcı bir HTTP GET hizmetinize önbelleğe alma işlemi için yapılandırılmış gönderdiğinde, ASP.NET önbelleğe alınmış bir yanıtı geri gönderir ve hizmet yöntemi çağrılmaz. Önbellek, bir kullanıcı bir HTTP GET gönderir sonraki süresi dolduğunda, hizmeti yöntemi olarak adlandırılır ve yanıt yine önbelleğe alınır. ASP.NET önbelleğe alma hakkında daha fazla bilgi için bkz: [ASP.NET önbelleğe alma genel bakış](http://go.microsoft.com/fwlink/?LinkId=152534)  
  
## <a name="basic-web-http-service-caching"></a>Temel Web HTTP hizmeti önbelleğe alma  
 WEB HTTP etkinleştirmek için önbelleğe alma hizmeti ilk ASP.NET uyumluluğu uygulayarak etkinleştirmelisiniz <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> hizmet ayarına <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute.RequirementsMode%2A> için <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed> veya <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Required>.  
  
 [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)] adlı yeni bir öznitelik tanıtır <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> önbellek profili adını belirtmenize olanak verir. Bu öznitelik, bir hizmet işlemi uygulanır. Aşağıdaki örnek uygular <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> ASP.NET uyumluluğu sağlamak için bir hizmet ve yapılandırır `GetCustomer` önbelleğe alma işlemi. <!--zz<xref:System.ServiceModel.Activation.AspNetCacheProfileAttribute>--> `System.ServiceModel.Activation.AspNetCacheProfileAttribute` Özniteliği kullanılacak önbellek ayarları içeren bir önbellek profili belirtir.  
  
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
  
 Aşağıdaki örnekte gösterildiği gibi Web.config dosyasında ASP.NET uyumluluğu modunu etkinleştirmelisiniz.  
  
```xml
<system.serviceModel>
  <serviceHostingEnvironment aspNetCompatibilityEnabled="true" />
</system.serviceModel>
```
  
> [!WARNING]
>  ASP.NET uyumluluğu modu açık değilse ve <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> kullanılan bir özel durum.  
  
 Belirtilen önbellek profili adı <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> Web.config yapılandırma dosyasına eklenen bir önbellek profili tanımlar. Önbellek profili ile tanımlanan bir <`outputCacheSetting`> aşağıdaki yapılandırma örnekte gösterildiği gibi öğesi.  
  
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
  
 ASP.NET uygulamaları için kullanılabilir aynı yapılandırma öğesi budur. ASP.NET önbellek profilleri hakkında daha fazla bilgi için bkz: <xref:System.Web.Configuration.OutputCacheProfile>. Web HTTP Hizmetleri için önbellek profili en önemli öznitelikleri şunlardır: `cacheDuration` ve `varyByParam`. Bu öznitelikler her ikisi de gereklidir. `cacheDuration` saniye cinsinden bir yanıt önbelleğe alınması gereken süre miktarını ayarlar. `varyByParam` Önbellek yanıtlar için kullanılan sorgu dizesi parametresi belirtmenize olanak tanır. Farklı sorgu dizesi parametre değerleri ile yapılan tüm istekleri ayrı ayrı önbelleğe alınır. Örneğin, ilk istek yapıldığında http://MyServer/MyHttpService/MyOperation?param=10 (önbellek süresi değil geçti sürece) aynı URI ile yapılan tüm sonraki istekleri önbelleğe alınan yanıtın döndürülür. Yanıtlar aynıdır, ancak parametre sorgu dizesi parametresi için farklı bir değere sahip benzer bir istek için ayrı olarak önbelleğe alınır. Bu ayrı önbelleğe alma davranışını istemiyorsanız ayarlamak `varyByParam` "none".  
  
## <a name="sql-cache-dependency"></a>SQL önbellek bağımlılığı  
 Web HTTP hizmeti yanıtlar ile SQL önbellek bağımlılığı önbelleğe alınabilir. Bir SQL veritabanında depolanan veriler, WCF Web HTTP hizmeti bağlıdır, hizmetin yanıt önbelleğe alma ve verileri SQL veritabanı tablosu değişiklikleri zaman önbelleğe alınan yanıtın geçersiz kılmak isteyebilirsiniz. Bu davranış, Web.config dosyasında tamamen yapılandırılır. Bir bağlantı dizesi ilk tanımlamanız gerekir <`connectionStrings`> öğesi.  
  
```xml
<connectionStrings>
  <add name="connectString"
       connectionString="Data Source=MyService;Initial Catalog=MyTestDatabase;Integrated Security=True"
       providerName="System.Data.SqlClient" />
</connectionStrings>
```  
  
 SQL önbellek bağımlılığı içinde etkinleştirmelisiniz sonra bir <`caching`> öğesi içinde <`system.web`> aşağıdaki yapılandırma örnekte gösterildiği gibi öğesi.  
  
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
  
 SQL önbellek bağımlılığı burada etkinleştirildikten ve yoklama zaman 1000 milisaniye olarak ayarlanır. Veritabanı tablosunun yoklama süresi sona erdiğinde her zaman güncelleştirmeleri denetlenir. Değişiklikleri önbelleğinin içeriğini kaldırılır ve yeni bir yanıt hizmet işlemi başlatıldığında çağrılan algılanırsa, önbelleğe alınır. İçinde <`sqlCacheDependency`> öğesi veritabanlarını ekleyin ve bağlantı dizeleri içinde reference <`databases`> Aşağıdaki örnekte gösterildiği gibi öğesi.  
  
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
  
 Sonraki içinde çıktı önbellek ayarlarını yapılandırmanız gerekir <`caching`> Aşağıdaki örnekte gösterildiği gibi öğesi.  
  
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
  
 Önbellek süresi 60 saniye için burada ayarlanan `varyByParam` none olarak ayarlanmış ve `sqlDependency` noktalı virgülle ayrılmış listesini virgüllerle ayrılmış veritabanı adı/tablo çiftleri için ayarlanır. Zaman içinde veri `MyTable` önbelleğe alınan yanıtın hizmet işlemi kaldırılır ve işlem çağrıldığında yeni bir yanıt (hizmet işlemi çağırarak) oluşturulur, önbelleğe alınan ve istemciye döndürülen değiştirilir.  
  
> [!IMPORTANT]
>  Bir SQL veritabanına erişmek ASP.NET ile ilgili kullanmalısınız [ASP.NET SQL Server kayıt aracı](http://go.microsoft.com/fwlink/?LinkId=152536). Ayrıca veritabanı ve tablo uygun kullanıcı hesabı erişimi izni vermelidir. Daha fazla bilgi için bkz: [SQL Server'dan erişen bir Web uygulaması](http://go.microsoft.com/fwlink/?LinkId=178988).  
  
## <a name="conditional-http-get-based-caching"></a>Koşullu HTTP tabanlı önbelleğe alma  
 Web HTTP senaryolarda koşullu bir HTTP GET genellikle Hizmetleri tarafından akıllı HTTP önbelleğe alma açıklandığı gibi uygulamak için kullanılan [HTTP belirtimi](http://go.microsoft.com/fwlink/?LinkId=165800). Bu hizmet yapmak için ETag üstbilgi değerini HTTP yanıt olarak ayarlamanız gerekir. If-None-Match üst bilgisinde belirtilen ETag hiçbirini eşleşip eşleşmediğini geçerli ETag görmek için HTTP isteği da işaretlemeleri gerekir.  
  
 GET ve HEAD isteklerini <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> bir ETag değeri alır ve istek If-None-Match üstbilgisi karşı denetler. Üstbilgi bulunduğundan ve bir eşleşme varsa bir <xref:System.ServiceModel.Web.WebFaultException> ile bir HTTP durum kodu 304 (değişiklik) oluşturulur ve bir ETag üstbilgisi eşleşen ETag Yanıtla eklenir.  
  
 Bir aşırı yüklemesini <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> yöntemi son değiştirilme tarihini alır ve If-Modified-Since üstbilgisi isteği karşı denetler. Üstbilgi varsa ve bu yana, kaynak değiştirilmemiş bir <xref:System.ServiceModel.Web.WebFaultException> ile bir HTTP durum kodu 304 (değişiklik) oluşturulur.  
  
 PUT, POST ve DELETE isteklerini <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> bir kaynağın geçerli ETag değeri alır. Geçerli ETag değeri null ise, yöntem If-None-Match üst bilgisi değeri olup olmadığını denetler "*".  Geçerli ETag değeri varsayılan bir değer değil yöntemi geçerli ETag değeri istek IF - Match üstbilgisi karşı denetler. Her iki durumda da yöntemi atar bir <xref:System.ServiceModel.Web.WebFaultException> beklenen üstbilgisi istekte mevcut değilse veya değerini koşullu onay karşılamadığı ve yanıtın geçerli ETag için ETag üstbilgisini ayarlar 412 (önkoşul başarısız oldu) ile bir HTTP durum kodu değer.  
  
 Her iki `CheckConditional` yöntemleri ve <xref:System.ServiceModel.Web.OutgoingWebResponseContext.SetETag%2A> yöntemi yanıt üstbilgisi ayarlamak ETag değeri geçerli bir ETag göre HTTP belirtiminin olmasını sağlar. Bu, zaten yoksa, çift tırnak işareti ETag değeri çevreleyen ve düzgün şekilde herhangi bir iç çift tırnak karakteri kaçış içerir. Zayıf bir ETag karşılaştırma desteklenmiyor.  
  
 Aşağıdaki örnek, bu yöntemleri kullanmayı gösterir.  
  
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
 Yanıtı önbelleğinden sunulduğunda yetkilendirme yapılmaz çünkü yetkilendirme gerektiren isteklerinin yanıtlarını önbelleğe alınmış, olmalıdır.  Bu tür yanıtlarını önbelleğe alma ciddi güvenlik açığı tanıtır.  Genellikle, kullanıcıya özgü verileri yetkilendirme gerektiren isteklerinin sağlayın ve bu nedenle sunucu tarafı önbelleğe alma bile yararlı değildir.  Böyle durumlarda, istemci tarafı önbelleğe alma veya yalnızca hiç önbelleğe alma değil daha uygun olacaktır.
