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
# <a name="caching-support-for-wcf-web-http-services"></a>WCF Web HTTP Hizmetleri için Önbelleğe Alma Desteği

[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]WCF Web HTTP hizmetlerinizde ASP.NET mevcut olan bildirimsel önbelleğe alma mekanizmasını kullanmanıza olanak tanır. Bu, WCF Web HTTP hizmet işlemlerinizden yanıtları önbelleğe alalet etmenizi sağlar. Bir kullanıcı önbelleğe almak üzere yapılandırılan bir HTTP GET hizmetinize gönderdiğinde, ASP.NET önbelleğe alınmış yanıtı geri gönderir ve hizmet yöntemi çağrılmaz. Önbelleğin süresi dolduğunda, bir sonraki kullanıcı BIR HTTP GET gönderdiğinde, hizmet yönteminiz çağrılır ve yanıt bir kez daha önbelleğe alır. ASP.NET önbelleğe alma hakkında daha fazla bilgi için, [ASP.NET Önbelleğe Alma Genel Bakış'a](https://docs.microsoft.com/previous-versions/aspnet/ms178597(v=vs.100))bakın.  
  
## <a name="basic-web-http-service-caching"></a>Temel Web HTTP Hizmet Önbelleğe Alma  

  WEB <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> HTTP hizmet önbelleğe almak için, <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute.RequirementsMode%2A> <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed> ASP.NET öncelikle hizmet ayarı veya <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Required>.  
  
 .NET Framework 4, önbellek <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> profil adı belirtmenize olanak tanıyan yeni bir öznitelik sunar. Bu öznitelik bir hizmet işlemine uygulanır. Aşağıdaki örnek, ASP.NET <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> uyumluluğunu etkinleştirmek için bir hizmete uygulanır ve önbelleğe alma işlemini `GetCustomer` yapılandırır. Öznitelik, <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> kullanılacak önbellek ayarlarını içeren bir önbellek profili belirtir.  
  
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
  
Ayrıca, aşağıdaki örnekte gösterildiği gibi Web.config dosyasındaki ASP.NET uyumluluk modunu da açın.  
  
```xml
<system.serviceModel>
  <serviceHostingEnvironment aspNetCompatibilityEnabled="true" />
</system.serviceModel>
```
  
> [!WARNING]
> uyumluluk modu ASP.NET açık değilse ve <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> kullanılırsa bir özel durum atılır.  
  
 Web.config yapılandırma dosyanıza eklenen önbellek profilini <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> tanımlar tarafından belirtilen önbellek profili adı. Önbellek profili, aşağıdaki yapılandırma `outputCacheSetting` örneğinde gösterildiği gibi <bir> öğesiile tanımlanır.  
  
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
  
 Bu, ASP.NET uygulamaları için kullanılabilen yapılandırma öğesidir. önbellek profilleri ASP.NET hakkında daha <xref:System.Web.Configuration.OutputCacheProfile>fazla bilgi için bkz. Web HTTP hizmetleri için önbellek profilindeki en `cacheDuration` önemli `varyByParam`öznitelikler şunlardır: ve. Bu özniteliklerin her ikisi de gereklidir. `cacheDuration`bir yanıtın saniyeler içinde önbelleğe alınması gereken süreyi ayarlar. `varyByParam`yanıtları önbelleğe almak için kullanılan bir sorgu dize parametresini belirtmenizi sağlar. Farklı sorgu dize parametre değerleri ile yapılan tüm istekler ayrı ayrı önbelleğe alınır. Örneğin, ilk istek yapıldıktan `http://MyServer/MyHttpService/MyOperation?param=10`sonra, aynı URI ile yapılan sonraki tüm istekler önbelleğe alınmış yanıtı döndürülür (önbellek süresi dolmadığı sürece). Parametre sorgusu dize parametresi parametresi için farklı bir değeri olan benzer bir isteğe yönelik yanıtlar ayrı olarak önbelleğe alınır. Bu ayrı önbelleğe alma davranışı `varyByParam` istemiyorsanız, "yok" olarak ayarlayın.  
  
## <a name="sql-cache-dependency"></a>SQL Önbellek Bağımlılığı  

  Web HTTP hizmet yanıtları da bir SQL önbellek bağımlılığı ile önbelleğe alınabilir. WCF Web HTTP hizmetiniz bir SQL veritabanında depolanan verilere bağlıysa, hizmetin yanıtını önbelleğe almak ve SQL veritabanı tablosundaki veriler değiştiğinde önbelleğe alınan yanıtı geçersiz kılabilir. Bu davranış tamamen Web.config dosyası içinde yapılandırılır. İlk olarak, <`connectionStrings`> öğesinde bir bağlantı dizesi tanımlayın.  
  
```xml
<connectionStrings>
  <add name="connectString"
       connectionString="Data Source=MyService;Initial Catalog=MyTestDatabase;Integrated Security=True"
       providerName="System.Data.SqlClient" />
</connectionStrings>
```  
  
 Daha sonra aşağıdaki config örneğinde `caching` gösterildiği gibi <`system.web`> öğesi içinde <bir> öğesi içinde SQL önbellek bağımlılığı etkinleştirmek gerekir.  
  
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
  
 Burada SQL önbellek bağımlılığı etkinleştirilir ve 1000 milisaniyelik bir yoklama süresi ayarlanır. Yoklama süresi her zaman veritabanı tablosu güncelleştirmeleri için denetlenir. Değişiklikler algılanırsa önbelleğin içeriği kaldırılır ve hizmet işlemi bir sonraki çağrıldığinde yeni bir yanıt önbelleğe alınır. <`sqlCacheDependency`> öğesi içinde veritabanları ekleyin ve aşağıdaki örnekte `databases` gösterildiği gibi <> öğesi içinde bağlantı dizeleri başvuru.  
  
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
  
 Daha sonra, aşağıdaki örnekte gösterildiği gibi `caching` <> öğesi içindeki çıktı önbelleği ayarlarını yapılandırmanız gerekir.  
  
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
  
 Burada önbellek süresi 60 saniye `varyByParam` olarak ayarlanır, hiçbiri `sqlDependency` olarak ayarlanır ve iki nokta üst üste ayrılmış veritabanı adı/tablo çiftleri yarı sütunlu sınırlı bir listeye ayarlanır. İçteki `MyTable` veriler değiştirildiğinde, hizmet işlemi için önbelleğe alınan yanıt kaldırılır ve işlem çağrıldığında yeni bir yanıt oluşturulur (hizmet işlemi çağırılarak), önbelleğe alınır ve istemciye döndürülür.  
  
> [!IMPORTANT]
> Bir SQL veritabanına erişmek için ASP.NET [için ASP.NET SQL Server Registration Tool'u](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms229862(v=vs.90))kullanmanız gerekir. Buna ek olarak, veritabanı na ve tabloya uygun kullanıcı hesabı erişimine izin vermelisiniz. Daha fazla bilgi için [bkz.](https://docs.microsoft.com/previous-versions/aspnet/ht43wsex(v=vs.100))  
  
## <a name="conditional-http-get-based-caching"></a>Koşullu HTTP GET Tabanlı Önbelleğe Alma  

  Web HTTP senaryolarında koşullu bir HTTP GET genellikle [http belirtiminde](https://www.w3.org/Protocols/rfc2616/rfc2616.html)açıklandığı gibi akıllı HTTP önbelleğe uygulamak için hizmetler tarafından kullanılır. Bunu yapmak için, hizmetIN HTTP yanıtındaki ETag üstbilginin değerini ayarlaması gerekir. Ayrıca, ETag belirtilenlerden herhangi birinin geçerli ETag ile eşleşip eşleşmediğini görmek için HTTP isteğindeki If-None-Match üstbilgisini de denetlemelidir.  
  
 GET ve HEAD <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> istekleri için bir ETag değeri alır ve isteğin If-None-Match üstbilgisi ile karşılaştırın. Üstbilgi varsa ve bir eşleşme varsa, <xref:System.ServiceModel.Web.WebFaultException> bir HTTP durum kodu 304 (Değiştirilmemiş) ile bir atılır ve eşleşen ETag ile yanıta bir ETag üstbilgisi eklenir.  
  
 Yöntemin <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> bir aşırı yüklemesi son değiştirilmiş bir tarih alır ve isteğin If-Modified-Since üstbilgisi ile karşılaştırın. Üstbilgi mevcutsa ve kaynak o zamandan beri <xref:System.ServiceModel.Web.WebFaultException> değiştirilmemişse, http durum kodu 304 (Değiştirilmemiş) ile bir a.ş. atılır.  
  
 PUT, POST ve DELETE <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> istekleri için kaynağın geçerli ETag değerini alır. Geçerli ETag değeri null ise, yöntem If-None- Match üstbilgisinin "*" değerine sahip olduğunu denetler.  Geçerli ETag değeri varsayılan bir değer değilse, yöntem geçerli ETag değerini isteğin If- Match üstbilgisi ile karşıya denetler. Her iki durumda da, <xref:System.ServiceModel.Web.WebFaultException> beklenen üstbilgi istekte yoksa veya değeri koşullu denetimi karşılamazsa ve geçerli ETag değerine yanıtın ETag üstbilgisini ayarlarsa, yöntem bir HTTP durum kodu 412 (Ön Koşul Başarısız) ile a atar.  
  
 Hem `CheckConditional` yöntem hem <xref:System.ServiceModel.Web.OutgoingWebResponseContext.SetETag%2A> de yöntem, yanıt başlığında ayarlanan ETag değerinin HTTP belirtimine göre geçerli bir ETag olmasını sağlar. Bu, eTag değerini çift tırnak içinde çevrelemeyi içerir, eğer zaten mevcut değillerse ve herhangi bir dahili çift tırnak karakterlerinden düzgün bir şekilde kaçıyorlarsa. Zayıf ETag karşılaştırması desteklenmez.  
  
 Aşağıdaki örnekte, bu yöntemlerin nasıl kullanılacağı gösterilmektedir.  
  
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
  
## <a name="security-considerations"></a>Güvenlikle İlgili Dikkat Edilmesi Gerekenler  
 Yetkilendirme önbellekten sunulduğunda yetkilendirme gerçekleştirilmediği için yetkilendirme gerektiren isteklerin yanıtlarının önbelleğe alınmaması gerekir.  Bu tür yanıtların önbelleğe alınmış bir şekilde önbelleğe alınmış bir güvenlik açığı na neden olur.  Genellikle, yetkilendirme gerektiren istekler kullanıcıya özgü veriler sağlar ve bu nedenle sunucu tarafı önbelleğe alma bile yararlı değildir.  Bu gibi durumlarda, istemci tarafı önbelleğe alma veya sadece hiç önbelleğe almamak daha uygun olacaktır.
