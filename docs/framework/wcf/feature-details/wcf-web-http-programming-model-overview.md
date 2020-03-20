---
title: WCF Web HTTP Programlama Modeli Genel Bakış
ms.date: 03/30/2017
ms.assetid: 381fdc3a-6e6c-4890-87fe-91cca6f4b476
ms.openlocfilehash: fb6ef0fdcefbc6ceec75ce30db3abf5896d85c61
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184179"
---
# <a name="wcf-web-http-programming-model-overview"></a>WCF Web HTTP Programlama Modeli Genel Bakış
Windows Communication Foundation (WCF) WEB HTTP programlama modeli, WCF ile WEB HTTP hizmetleri oluşturmak için gereken temel öğeleri sağlar. WCF WEB HTTP hizmetlerine, Web tarayıcıları da dahil olmak üzere mümkün olan en geniş müşteri yelpazesine erişilecek ve aşağıdaki benzersiz gereksinimlere sahip olacak şekilde tasarlanmıştır:  
  
- **ÜRBİ ve URI İşleme** URI'ler WEB HTTP hizmetlerinin tasarımında merkezi bir rol oynar. WCF WEB HTTP programlama modeli <xref:System.UriTemplate> <xref:System.UriTemplateTable> URI işleme yetenekleri sağlamak için ve sınıfları kullanır.  
  
- **GET ve POST operasyonlarına destek** WEB HTTP hizmetleri, veri modifikasyonu ve uzaktan çağırma için çeşitli invoke fiillerine ek olarak, veri alma için GET fiilini kullanır. WCF WEB HTTP programlama <xref:System.ServiceModel.Web.WebGetAttribute> modeli, <xref:System.ServiceModel.Web.WebInvokeAttribute> hizmet işlemlerini HEM GET hem de PUT, POST ve DELETE gibi diğer HTTP fiilleriyle ilişkilendirmek için kullanır.  
  
- **Birden çok veri biçimi** Web tarzı hizmetler SOAP mesajlarına ek olarak birçok veri çeşidiyi işler. WCF WEB HTTP programlama <xref:System.ServiceModel.WebHttpBinding> modeli, <xref:System.ServiceModel.Description.WebHttpBehavior> XML belgeleri, JSON veri nesnesi ve görüntüler, video dosyaları veya düz metin gibi ikili içerik akışları da dahil olmak üzere birçok farklı veri biçimini destekler.  
  
 WCF WEB HTTP programlama modeli, WEB HTTP hizmetleri, AJAX ve JSON hizmetlerini ve Sendikasyon (ATOM/RSS) akışlarını içeren Web tarzı senaryoları kapsayacak şekilde WCF'nin erişimini genişletir. AJAX ve JSON hizmetleri hakkında daha fazla bilgi için [AJAX Entegrasyonu ve JSON Desteği'ne](../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md)bakın. Sendikasyon hakkında daha fazla bilgi için [WCF Sendikasyon Genel Bakış'a](../../../../docs/framework/wcf/feature-details/wcf-syndication-overview.md)bakın.  
  
 Bir WEB HTTP hizmetinden döndürülebilecek veri türleri üzerinde ek bir kısıtlama yoktur. Herhangi bir serializable türü bir WEB HTTP hizmet işleminden döndürülebilir. WEB HTTP hizmet işlemleri bir web tarayıcısı tarafından çağrılayabildiği için, bir URL'de hangi veri türlerinin belirtilebileceği konusunda bir sınırlama vardır. Varsayılan olarak hangi türlerin desteklendirilip desteklendirilenhakkında daha fazla bilgi için aşağıdaki **UriTemplate Query String Parametreleri ve URL'ler** bölümüne bakın. Varsayılan davranış, bir URL'de belirtilen parametrelerin gerçek parametre türüne nasıl dönüştürüleceğini belirten kendi T:System.ServiceModel.Dispatcher.QueryStringConverter uygulamanızı sağlayarak değiştirilebilir. Daha fazla bilgi için bkz. <xref:System.ServiceModel.Dispatcher.QueryStringConverter>.  
  
> [!CAUTION]
> WCF WEB HTTP programlama modeli ile yazılan hizmetler SOAP iletileri kullanmaz. SOAP kullanılmadığından, WCF tarafından sağlanan güvenlik özellikleri kullanılamaz. Ancak, hizmetinizi HTTPS ile barındırarak aktarım tabanlı güvenliği kullanabilirsiniz. WCF güvenliği hakkında daha fazla bilgi için Güvenlik [genel bakış](../../../../docs/framework/wcf/feature-details/security-overview.md)  
  
> [!WARNING]
> WebDAV uzantısı tüm PUT isteklerini işlemeye çalışırken, IIS için WebDAV uzantısının yüklenmesi Web HTTP hizmetlerinin bir HTTP 405 hatasını döndürmesine neden olabilir. Bu sorunu çözmek için WebDAV uzantısını kaldırabilir veya web sitenizin WebDAV uzantısını devre dışı kullanabilirsiniz. Daha fazla bilgi için Bkz. [IIS ve WebDav](https://learn.iis.net/page.aspx/357/webdav-for-iis-70/)  
  
## <a name="uri-processing-with-uritemplate-and-uritemplatetable"></a>UriTemplate ve UriTemplateTable ile URI İşleme  
 URI şablonları, yapısal olarak benzer OLAN BÜYÜK ÜRB'leri ifade etmek için etkili bir sözdizimi sağlar. Örneğin, aşağıdaki şablon, ara segmentin değerine bakılmaksızın "a" ile başlayan ve "c" ile biten üç segmentli URI kümesini ifade eder: a/{segment}/c  
  
 Bu şablon, URI'leri aşağıdaki gibi açıklar:  
  
- a/x/c  
  
- a/y/c  
  
- a/z/c  
  
- ve saire.  
  
 Bu şablonda, kıvırcık ayraç gösterimi ("{segment}") gerçek bir değer yerine değişken bir kesimi gösterir.  
  
 .NET Framework, URI şablonları adı verilen <xref:System.UriTemplate>bir API sağlar. `UriTemplates`aşağıdakileri yapmanıza olanak sağlar:  
  
- Şablonla `Bind` eşleşen *tam kapalı* bir URI üretmek için bir dizi parametreiçeren yöntemlerden birini arayabilirsiniz. Bu, URI şablonundaki tüm değişkenlerin gerçek değerlerle değiştirilmeleri anlamına gelir.  
  
- Aday URI'yi kurucu bölümlerine ayırmak için şablon kullanan ve şablondaki değişkenlere göre etiketlenmiş URI'nin farklı bölümlerini içeren bir sözlük döndüren bir aday URI ile () arayabilirsiniz. `Match`  
  
- `Bind`() `Match`ve () (x) numaralı `Match` `Bind`telefondan arayabilir ve başladığınız ortamla geri dönebilirsiniz.  
  
 İçerdiği şablonların her birini bağımsız olarak ele alabilecek bir veri yapısındaki <xref:System.UriTemplate> bir nesne kümesini izlemek istediğiniz birçok kez (özellikle URI'ye dayalı bir hizmet işlemine istek göndermenin gerekli olduğu sunucuda) vardır. <xref:System.UriTemplateTable>URI şablonları kümesini temsil eder ve bir şablon kümesi ve aday URI göz önüne alındığında en iyi eşleşmeyi seçer. Bu, herhangi bir ağ yığınına (WCF dahil) bağlı değildir, böylece gerektiğinde kullanabilirsiniz.  
  
 WCF Hizmet Modeli, <xref:System.UriTemplate> <xref:System.UriTemplateTable> hizmet işlemlerini bir . <xref:System.UriTemplate> Bir hizmet <xref:System.UriTemplate>işlemi, bir , <xref:System.ServiceModel.Web.WebGetAttribute> ya <xref:System.ServiceModel.Web.WebInvokeAttribute>da kullanarak ilişkilidir . Hakkında <xref:System.UriTemplate> daha fazla <xref:System.UriTemplateTable>bilgi için [UriTemplate ve UriTemplateTable](../../../../docs/framework/wcf/feature-details/uritemplate-and-uritemplatetable.md)  
  
## <a name="webget-and-webinvoke-attributes"></a>WebGet ve WebInvoke Öznitelikleri  
 WCF WEB HTTP hizmetleri, çeşitli çağrı fiillerine (örneğin HTTP POST, PUT ve DELETE) ek olarak alma fiillerini (örneğin HTTP GET) kullanır. WCF WEB HTTP programlama modeli, hizmet geliştiricilerin hem URI şablonu ve fiil <xref:System.ServiceModel.Web.WebGetAttribute> <xref:System.ServiceModel.Web.WebInvokeAttribute>ile hizmet işlemleri ile ilişkili kontrol sağlar ve . Ve <xref:System.ServiceModel.Web.WebGetAttribute> tek <xref:System.ServiceModel.Web.WebInvokeAttribute> tek operasyonların URI'lere ve bu URI'lerle ilişkili HTTP yöntemlerine nasıl bağlandığını kontrol etme olanağı sağlar. Örneğin, ekleme <xref:System.ServiceModel.Web.WebGetAttribute> <xref:System.ServiceModel.Web.WebInvokeAttribute> ve aşağıdaki kod.  
  
```csharp
[ServiceContract]  
interface ICustomer  
{  
  //"View It"  
  
  [WebGet]  
  Customer GetCustomer():  
  
  //"Do It"  
    [WebInvoke]  
  Customer UpdateCustomerName( string id,
                               string newName );  
}  
```  
  
 Önceki kod aşağıdaki HTTP isteklerini yapmanızı sağlar.  
  
 `GET /GetCustomer`  
  
 `POST /UpdateCustomerName`  
  
 <xref:System.ServiceModel.Web.WebInvokeAttribute>varsayılan post ama diğer fiiller için de kullanabilirsiniz.  
  
```csharp
[ServiceContract]  
interface ICustomer  
{  
  //"View It" -> HTTP GET  
    [WebGet( UriTemplate="customers/{id}" )]  
  Customer GetCustomer( string id ):  
  
  //"Do It" -> HTTP PUT  
  [WebInvoke( UriTemplate="customers/{id}", Method="PUT" )]  
  Customer UpdateCustomer( string id, Customer newCustomer );  
}  
```  
  
 WCF WEB HTTP programlama modelini kullanan bir WCF hizmetinin tam bir örneğini görmek [için bkz.](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-wcf-web-http-service.md)  
  
## <a name="uritemplate-query-string-parameters-and-urls"></a>UriTemplate Sorgu Dize Parametreleri ve URL'leri  
 Web tarzı hizmetler, bir hizmet işlemiyle ilişkili bir URL yazarak Web tarayıcısından çağrılabilir. Bu hizmet işlemleri, URL içinde bir dize formunda belirtilmesi gereken sorgu dize parametrelerini alabilir. Aşağıdaki tablo, bir URL içinde geçirilebilen türleri ve kullanılan biçimi gösterir.  
  
|Tür|Biçimlendir|  
|----------|------------|  
|<xref:System.Byte>|0 - 255|  
|<xref:System.SByte>|-128 - 127|  
|<xref:System.Int16>|-32768 - 32767|  
|<xref:System.Int32>|-2,147,483,648 - 2,147,483,647|  
|<xref:System.Int64>|-9,223,372,036,854,775,808 - 9,223,372,036,854,775,807|  
|<xref:System.UInt16>|0 - 65535|  
|<xref:System.UInt32>|0 - 4,294,967,295|  
|<xref:System.UInt64>|0 - 18,446,744,073,709,551,615|  
|<xref:System.Single>|-3.402823e38 - 3.402823e38 (üslü not ameç gerekli değildir)|  
|<xref:System.Double>|-1.79769313486232e308 - 1.79769313486232e308 (üslü notasyon gerekli değildir)|  
|<xref:System.Char>|Herhangi bir tek karakter|  
|<xref:System.Decimal>|Standart gösterimde herhangi bir ondalık (üs yok)|  
|<xref:System.Boolean>|Doğru veya Yanlış (büyük/küçük harf duyarsız)|  
|<xref:System.String>|Herhangi bir dize (null string desteklenmez ve kaçış yapılmaz)|  
|<xref:System.DateTime>|AA/GG/YYYY<br /><br /> MM/DD/YYYY HH:MM:SS [AM&#124;PM]<br /><br /> Ay Gün Yılı<br /><br /> Ay Gün Yıl HH:MM:SS [AM&#124;PM]|  
|<xref:System.TimeSpan>|Dd. HH:MM:SS<br /><br /> Nerede DD = Gün, HH = Saat, MM = dakika, SS = Saniye|  
|<xref:System.Guid>|Bir GUID, örneğin:<br /><br /> 936DA01F-9ABD-4d9d-80C7-02AF85C822A8|  
|<xref:System.DateTimeOffset>|MM/DD/YYYY HH:MM:SS MM:SS<br /><br /> Nerede DD = Gün, HH = Saat, MM = dakika, SS = Saniye|  
|Numaralandırmalar|Örneğin, aşağıdaki kodda gösterildiği gibi numaralandırmayı tanımlayan numaralandırma değeri.<br /><br /> `public enum Days{ Sunday, Monday, Tuesday, Wednesday, Thursday, Friday, Saturday };`<br /><br /> Sorgu dizesinde tek tek numaralandırma değerlerinden herhangi biri (veya bunların karşılık gelen tümsabu değerleri) belirtilebilir.|  
|Türü bir `TypeConverterAttribute` dize gösterimine dönüştürebilen bir türü olan türler.|Tip Dönüştürücü'ye bağlıdır.|  
  
## <a name="formats-and-the-wcf-web-http-programming-model"></a>Biçimleri ve WCF WEB HTTP Programlama Modeli  
 WCF WEB HTTP programlama modeli birçok farklı veri biçimleri ile çalışmak için yeni özelliklere sahiptir. Bağlama katmanında, <xref:System.ServiceModel.WebHttpBinding> aşağıdaki farklı türde verileri okuyabilir ve yazabilirsiniz:  
  
- XML  
  
- JSON  
  
- Opak ikili akarsular  
  
 Bu, WCF WEB HTTP programlama modelinin her türlü veriyi işleyebilir, ancak buna karşı <xref:System.IO.Stream>programlama yapıyor olabileceğiniz anlamına gelir.  
  
 .NET Framework 3.5, JSON verilerinin (AJAX) yanı sıra Sendikasyon akışları (ATOM ve RSS dahil) için destek sağlar. Bu özellikler hakkında daha fazla bilgi için [WCF Web HTTP Biçimlendirme](../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md)[WCF Sendikasyon Genel Bakış](../../../../docs/framework/wcf/feature-details/wcf-syndication-overview.md) ve AJAX Entegrasyonu ve [JSON Desteği'ne](../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md)bakın.  
  
## <a name="wcf-web-http-programming-model-and-security"></a>WCF WEB HTTP Programlama Modeli ve Güvenliği  

WCF WEB HTTP programlama modeli WS-* protokollerini desteklemediği için, bir WCF WEB HTTP hizmetini güvence altına almanın tek yolu Hizmeti SSL kullanarak HTTPS üzerinden ortaya çıkarmaktır. IIS 7.0 ile SSL kurulumu hakkında daha fazla bilgi için, [IIS'de SSL'nin nasıl uygulanacağını](https://support.microsoft.com/help/299875/how-to-implement-ssl-in-iis)öğrenin.
  
## <a name="troubleshooting-the-wcf-web-http-programming-model"></a>WCF WEB HTTP Programlama Modeli sorun giderme  
 Bir kanal oluşturmak için a <xref:System.ServiceModel.Channels.ChannelFactoryBase%601> kullanarak WCF <xref:System.ServiceModel.Description.WebHttpBehavior> WEB <xref:System.ServiceModel.EndpointAddress> HTTP hizmetlerini ararken, farklı <xref:System.ServiceModel.EndpointAddress> bir kanala geçse bile yapılandırma dosyasındaki kümeyi <xref:System.ServiceModel.Channels.ChannelFactoryBase%601>kullanır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Dağıtımı](../../../../docs/framework/wcf/feature-details/wcf-syndication.md)
- [WCF Web HTTP Programlama Nesnesi Modeli](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-object-model.md)
- [WCF Web HTTP Programlama Modeli](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
