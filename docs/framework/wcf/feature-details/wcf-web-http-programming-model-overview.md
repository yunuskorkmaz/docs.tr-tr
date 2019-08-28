---
title: WCF Web HTTP Programlama Modeli Genel Bakış
ms.date: 03/30/2017
ms.assetid: 381fdc3a-6e6c-4890-87fe-91cca6f4b476
ms.openlocfilehash: 8c13ad943bf4ef272c28266e12e175a0a21d5d40
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045240"
---
# <a name="wcf-web-http-programming-model-overview"></a>WCF Web HTTP Programlama Modeli Genel Bakış
Windows Communication Foundation (WCF) WEB HTTP programlama modeli, WCF ile WEB HTTP Hizmetleri oluşturmak için gereken temel öğeleri sağlar. WCF WEB HTTP Hizmetleri, Web tarayıcıları dahil olmak üzere en geniş olası istemciler arasında erişilecek şekilde tasarlanmıştır ve aşağıdaki benzersiz gereksinimlere sahiptir:  
  
- URI **'ler ve URI işleme** URI 'Ler, WEB HTTP Hizmetleri tasarımında merkezi bir rol oynar. WCF Web http programlama modeli, <xref:System.UriTemplate> URI işleme özellikleri sağlamak için ve <xref:System.UriTemplateTable> sınıflarını kullanır.  
  
- **Get ve post işlemleri Için destek** WEB HTTP Hizmetleri, veri değişikliği ve uzaktan çağırma için çeşitli Invoke fiillerinin yanı sıra veri alımı için GET fiilini kullanır. WCF Web http programlama modeli, hizmet işlemlerini <xref:System.ServiceModel.Web.WebGetAttribute> put <xref:System.ServiceModel.Web.WebInvokeAttribute> , post ve DELETE gibi get ve diğer http yüklemleri ile ilişkilendirmek için ve kullanır.  
  
- **Birden çok veri biçimi** Web stili hizmetler, SOAP iletilerine ek olarak birçok türdeki veriyi işler. WCF Web http programlama modeli, XML belgeleri <xref:System.ServiceModel.WebHttpBinding> , <xref:System.ServiceModel.Description.WebHttpBehavior> JSON veri nesnesi ve görüntü, video dosyaları ya da düz metin gibi ikili içerik akışları gibi birçok farklı veri biçimini desteklemek için ve kullanır.  
  
 WCF WEB HTTP programlama modeli, WEB HTTP Hizmetleri, AJAX ve JSON Hizmetleri ve dağıtım (ATOM/RSS) akışlarını içeren Web stili senaryolarını kapsamak için WCF 'nin erişimini genişletir. AJAX ve JSON Hizmetleri hakkında daha fazla bilgi için bkz. [AJAX Tümleştirme ve JSON desteği](../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md). Dağıtım hakkında daha fazla bilgi için bkz. [WCF dağıtımı genel bakış](../../../../docs/framework/wcf/feature-details/wcf-syndication-overview.md).  
  
 WEB HTTP hizmetinden döndürülebilecek veri türlerinde ek kısıtlama yoktur. Herhangi bir serileştirilebilir tür, bir WEB HTTP hizmeti işleminden döndürülebilir. WEB HTTP hizmet işlemleri bir Web tarayıcısı tarafından çalıştırılabildiğinden, URL 'de hangi veri türlerinin belirtibileceği konusunda bir sınırlama vardır. Varsayılan olarak desteklenen türler hakkında daha fazla bilgi için aşağıdaki **UriTemplate sorgu dizesi parametreleri ve URL 'leri** bölümüne bakın. Varsayılan davranış, URL 'de belirtilen parametrelerin gerçek parametre türüne nasıl dönüştürüleceğini belirten kendi T:System.ServiceModel.Dispatcher.QueryStringConverter uygulamanız sağlanarak değiştirilebilir. Daha fazla bilgi için bkz.<xref:System.ServiceModel.Dispatcher.QueryStringConverter>  
  
> [!CAUTION]
> WCF WEB HTTP programlama modeliyle yazılan hizmetler SOAP iletileri kullanmaz. SOAP kullanılmadığından, WCF tarafından sunulan güvenlik özellikleri kullanılamaz. Ancak, hizmetinizi HTTPS ile barındırarak aktarım tabanlı güvenlik kullanabilirsiniz. WCF güvenliği hakkında daha fazla bilgi için bkz. [Güvenliğe genel bakış](../../../../docs/framework/wcf/feature-details/security-overview.md)  
  
> [!WARNING]
> WebDAV uzantısının tüm PUT isteklerini işlemeye çalıştığı için, IIS için WebDAV uzantısını yüklemek Web HTTP hizmetlerinin HTTP 405 hatası döndürmesine neden olabilir. Bu sorunu geçici olarak çözmek için WebDAV uzantısını kaldırabilir veya Web siteniz için WebDAV uzantısını devre dışı bırakabilirsiniz. Daha fazla bilgi için bkz. [IIS ve WebDAV](https://learn.iis.net/page.aspx/357/webdav-for-iis-70/)  
  
## <a name="uri-processing-with-uritemplate-and-uritemplatetable"></a>UriTemplate ve UriTemplateTable ile URI Işleme  
 URI şablonları, yapısal olarak benzer URI 'lerin büyük kümelerini ifade etmek için etkili bir sözdizimi sağlar. Örneğin, aşağıdaki şablon, "a" ile başlayan ve ara segmentin değeri olmadan "c" ile biten üç kesimli tüm URI 'lerin kümesini ifade eder: a/{segment}/c  
  
 Bu şablon, aşağıdaki gibi URI 'Leri açıklar:  
  
- a/x/c  
  
- a/y/c  
  
- a/z/c  
  
- vb.  
  
 Bu şablonda, süslü ayraç gösterimi ("{segment}"), değişmez değer yerine bir değişken segmentini gösterir.  
  
 .NET Framework, adlı <xref:System.UriTemplate>URI şablonlarıyla ÇALıŞMAK için bir API sağlar. `UriTemplates`şunları yapmanıza izin verir:  
  
- Şablonla eşleşen *tam kapalı* bir URI `Bind` oluşturmak için bir parametre kümesiyle yöntemlerden birini çağırabilirsiniz. Bu, URI şablonundaki tüm değişkenlerin gerçek değerlerle değiştirildiği anlamına gelir.  
  
- Bir aday URI `Match`ile () çağırabilirsiniz. Bu, bir aday URI 'yi yapısal parçalara bölmek için şablon kullanır ve şablondaki değişkenlere göre etiketlendiği farklı URI parçalarını içeren bir sözlük döndürür.  
  
- `Bind`() ve `Match`(), ( `Bind`(x)) çağırabilmeniz `Match`ve ile başlattığınız aynı ortamla geri dönebilmeniz için ters ayarlanır.  
  
 Bir veri yapısında bulunan bir <xref:System.UriTemplate> nesne kümesinin her birini bağımsız olarak ele geçirebileceği birçok zaman (özellikle sunucuda, URI 'ye dayalı bir hizmet işlemine bir istek gönderen gereklidir) vardır. şablondan. <xref:System.UriTemplateTable>bir dizi URI şablonu temsil eder ve bir dizi şablon ve aday URI değeri verilen en iyi eşleşmeyi seçer. Bu, herhangi bir ağ yığını (WCF dahil) ile bağlantılı değildir, bu sayede gerektiğinde kullanabilirsiniz.  
  
 WCF hizmet modeli, hizmet işlemlerini bir <xref:System.UriTemplate> <xref:System.UriTemplate>tarafından <xref:System.UriTemplateTable> tanımlanan bir URI kümesiyle ilişkilendirmek için ve ' ı kullanır. <xref:System.ServiceModel.Web.WebGetAttribute> <xref:System.UriTemplate> Ya<xref:System.ServiceModel.Web.WebInvokeAttribute>da kullanılarak bir hizmet işlemi ile ilişkilendirilir. <xref:System.UriTemplate> Ve<xref:System.UriTemplateTable>hakkında daha fazla bilgi için bkz. [UriTemplate ve UriTemplateTable](../../../../docs/framework/wcf/feature-details/uritemplate-and-uritemplatetable.md)  
  
## <a name="webget-and-webinvoke-attributes"></a>WebGet ve Webvoke öznitelikleri  
 WCF WEB HTTP Hizmetleri, çeşitli Invoke fiillerine (örneğin, HTTP POST, PUT ve DELETE) ek olarak alma fiillerini (örneğin, HTTP GET) kullanır. WCF Web http programlama modeli, Service Developers 'in <xref:System.ServiceModel.Web.WebGetAttribute> ve <xref:System.ServiceModel.Web.WebInvokeAttribute>ile hizmet işlemleriyle ilişkili olan URI şablonunu ve fiilini denetlemesine olanak tanır. <xref:System.ServiceModel.Web.WebGetAttribute> Ve ,<xref:System.ServiceModel.Web.WebInvokeAttribute> tek tek işlemlerin URI 'lere ve bu URI 'ler ile ilişkili http yöntemlerine nasıl bağlandığını denetlemenize olanak tanır. Örneğin, aşağıdaki koda <xref:System.ServiceModel.Web.WebGetAttribute> ve <xref:System.ServiceModel.Web.WebInvokeAttribute> ekleme.  
  
```  
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
  
 Yukarıdaki kod, aşağıdaki HTTP isteklerini yapmanıza olanak sağlar.  
  
 `GET /GetCustomer`  
  
 `POST /UpdateCustomerName`  
  
 <xref:System.ServiceModel.Web.WebInvokeAttribute>Varsayılan olarak postala, ancak diğer fiiller için de kullanabilirsiniz.  
  
```  
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
  
 WCF Web http programlama modelini kullanan bir WCF hizmetinin tüm bir örneğini görmek için bkz [. nasıl yapılır: Temel bir WCF Web HTTP hizmeti oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-wcf-web-http-service.md)  
  
## <a name="uritemplate-query-string-parameters-and-urls"></a>UriTemplate sorgu dizesi parametreleri ve URL 'Leri  
 Web stili hizmetler bir Web tarayıcısından, bir hizmet işlemiyle ilişkili bir URL yazılarak çağrılabilir. Bu hizmet işlemleri, URL içindeki bir dize biçiminde belirtilmesi gereken sorgu dizesi parametreleri alabilir. Aşağıdaki tabloda bir URL ve kullanılan biçim içinde geçirilebilecek türler gösterilmektedir.  
  
|Tür|Biçimi|  
|----------|------------|  
|<xref:System.Byte>|0 - 255|  
|<xref:System.SByte>|-128 - 127|  
|<xref:System.Int16>|-32768 - 32767|  
|<xref:System.Int32>|-2,147,483,648 - 2,147,483,647|  
|<xref:System.Int64>|-9,223,372,036,854,775,808 - 9,223,372,036,854,775,807|  
|<xref:System.UInt16>|0 - 65535|  
|<xref:System.UInt32>|0 - 4,294,967,295|  
|<xref:System.UInt64>|0 - 18,446,744,073,709,551,615|  
|<xref:System.Single>|-3.402823 E38-3.402823 E38 (üs gösterimi gerekli değildir)|  
|<xref:System.Double>|-1.79769313486232 E308-1.79769313486232 E308 (üs gösterimi gerekli değildir)|  
|<xref:System.Char>|Herhangi bir tek karakter|  
|<xref:System.Decimal>|Standart gösterimdeki herhangi bir ondalık (üs yok)|  
|<xref:System.Boolean>|True veya false (büyük/küçük harf duyarsız)|  
|<xref:System.String>|Herhangi bir dize (null dize desteklenmez ve hiçbir kaçış yapılmaz)|  
|<xref:System.DateTime>|AA/GG/YYYY<br /><br /> AA/GG/YYYY HH: MM: SS [&#124;PM]<br /><br /> Ayın günü yılı<br /><br /> Ay günü yıl HH: MM: SS [&#124;PM]|  
|<xref:System.TimeSpan>|DD.HH:MM:SS<br /><br /> Burada gg = gün, SS = saat, MM = dakika, SS = saniye|  
|<xref:System.Guid>|Bir GUID, örneğin:<br /><br /> 936DA01F-9ABD-4d9d-80C7-02AF85C822A8|  
|<xref:System.DateTimeOffset>|AA/GG/YYYY SS: DD: SS MM: SS<br /><br /> Burada gg = gün, SS = saat, MM = dakika, SS = saniye|  
|Numaralandırmalar|Örneğin, aşağıdaki kodda gösterildiği gibi, numaralandırmayı tanımlayan sabit listesi değeri.<br /><br /> `public enum Days{ Sunday, Monday, Tuesday, Wednesday, Thursday, Friday, Saturday };`<br /><br /> Sorgu dizesinde her bir numaralandırma değeri (veya ilgili tamsayı değerleri) belirtilebilir.|  
|' A `TypeConverterAttribute` sahip olan türler, türü dize gösterimine ve öğesinden dönüştürebilir.|Tür Dönüştürücüne bağlıdır.|  
  
## <a name="formats-and-the-wcf-web-http-programming-model"></a>Biçimler ve WCF WEB HTTP programlama modeli  
 WCF WEB HTTP programlama modelinin birçok farklı veri biçiminde çalışmak için yeni özellikleri vardır. Bağlama katmanında <xref:System.ServiceModel.WebHttpBinding> , aşağıdaki farklı veri türlerini okuyup yazabilir:  
  
- XML  
  
- JSON  
  
- Donuk ikili akışlar  
  
 Bu, WCF WEB HTTP programlama modelinin herhangi bir türde veriyi işleyebileceği, ancak programlama yoluyla programlama <xref:System.IO.Stream>yapabileceği anlamına gelir.  
  
 [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)]JSON verileri (AJAX) ve dağıtım akışları (ATOM ve RSS dahil) için destek sağlar. Bu özellikler hakkında daha fazla bilgi için bkz. [WCF Web http biçimlendirme](../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md)[WCF dağıtımı genel bakış](../../../../docs/framework/wcf/feature-details/wcf-syndication-overview.md) ve [AJAX Tümleştirme ve JSON desteği](../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md).  
  
## <a name="wcf-web-http-programming-model-and-security"></a>WCF WEB HTTP programlama modeli ve güvenliği  
 WCF WEB HTTP programlama modeli WS-* protokollerini desteklemediğinden, bir WCF WEB HTTP hizmetini güvenli hale getirmenin tek yolu, Hizmeti SSL kullanarak HTTPS üzerinden kullanıma sunmasıdır. IIS 7,0 ile SSL ayarlama hakkında daha fazla bilgi için bkz. [IIS 'de SSL uygulama](https://go.microsoft.com/fwlink/?LinkId=131613)  
  
## <a name="troubleshooting-the-wcf-web-http-programming-model"></a>WCF WEB HTTP programlama modeli sorunlarını giderme  
 <xref:System.ServiceModel.Channels.ChannelFactoryBase%601> Bir kanal <xref:System.ServiceModel.EndpointAddress> <xref:System.ServiceModel.EndpointAddress> oluşturmak için bir kullanarak WCF Web HTTP Hizmetleri çağrılırken, farklı bir öğesine geçirilmiş <xref:System.ServiceModel.Channels.ChannelFactoryBase%601>olsa bile yapılandırma dosyasında kümesini kullanır.<xref:System.ServiceModel.Description.WebHttpBehavior>  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Dağıtımı](../../../../docs/framework/wcf/feature-details/wcf-syndication.md)
- [WCF Web HTTP Programlama Nesnesi Modeli](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-object-model.md)
- [WCF Web HTTP Programlama Modeli](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
