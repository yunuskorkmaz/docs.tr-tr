---
title: WCF Web HTTP Programlama Modeli Genel Bakış
ms.date: 03/30/2017
ms.assetid: 381fdc3a-6e6c-4890-87fe-91cca6f4b476
ms.openlocfilehash: 4862ae0e5151177e74da0f94d06b5b39205ed4c0
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283299"
---
# <a name="wcf-web-http-programming-model-overview"></a>WCF Web HTTP Programlama Modeli Genel Bakış
Windows Communication Foundation (WCF) WEB HTTP programlama modeli, WCF ile WEB HTTP Hizmetleri oluşturmak için gereken temel öğeleri sağlar. WCF WEB HTTP Hizmetleri, Web tarayıcıları dahil olmak üzere en geniş olası istemciler arasında erişilecek şekilde tasarlanmıştır ve aşağıdaki benzersiz gereksinimlere sahiptir:  
  
- URI **'ler ve URI işleme** URI 'Ler, WEB HTTP Hizmetleri tasarımında merkezi bir rol oynar. WCF WEB HTTP programlama modeli, URI işleme özellikleri sağlamak için <xref:System.UriTemplate> ve <xref:System.UriTemplateTable> sınıflarını kullanır.  
  
- **Get ve post işlemleri Için destek** WEB HTTP Hizmetleri, veri değişikliği ve uzaktan çağırma için çeşitli Invoke fiillerinin yanı sıra veri alımı için GET fiilini kullanır. WCF WEB HTTP programlama modeli, hizmet işlemlerini PUT, POST ve DELETE gibi GET ve diğer HTTP yüklemleri ile ilişkilendirmek için <xref:System.ServiceModel.Web.WebGetAttribute> ve <xref:System.ServiceModel.Web.WebInvokeAttribute> kullanır.  
  
- **Birden çok veri biçimi** Web stili hizmetler, SOAP iletilerine ek olarak birçok türdeki veriyi işler. WCF WEB HTTP programlama modeli, XML belgeleri, JSON veri nesnesi ve görüntü, video dosyaları ya da düz metin gibi ikili içerik akışları gibi birçok farklı veri biçimini desteklemek için <xref:System.ServiceModel.WebHttpBinding> ve <xref:System.ServiceModel.Description.WebHttpBehavior> kullanır.  
  
 WCF WEB HTTP programlama modeli, WEB HTTP Hizmetleri, AJAX ve JSON Hizmetleri ve dağıtım (ATOM/RSS) akışlarını içeren Web stili senaryolarını kapsamak için WCF 'nin erişimini genişletir. AJAX ve JSON Hizmetleri hakkında daha fazla bilgi için bkz. [AJAX Tümleştirme ve JSON desteği](../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md). Dağıtım hakkında daha fazla bilgi için bkz. [WCF dağıtımı genel bakış](../../../../docs/framework/wcf/feature-details/wcf-syndication-overview.md).  
  
 WEB HTTP hizmetinden döndürülebilecek veri türlerinde ek kısıtlama yoktur. Herhangi bir serileştirilebilir tür, bir WEB HTTP hizmeti işleminden döndürülebilir. WEB HTTP hizmet işlemleri bir Web tarayıcısı tarafından çalıştırılabildiğinden, URL 'de hangi veri türlerinin belirtibileceği konusunda bir sınırlama vardır. Varsayılan olarak desteklenen türler hakkında daha fazla bilgi için aşağıdaki **UriTemplate sorgu dizesi parametreleri ve URL 'leri** bölümüne bakın. Varsayılan davranış, URL 'de belirtilen parametrelerin gerçek parametre türüne nasıl dönüştürüleceğini belirten kendi T:System.ServiceModel.Dispatcher.QueryStringConverter uygulamanız sağlanarak değiştirilebilir. Daha fazla bilgi için bkz. <xref:System.ServiceModel.Dispatcher.QueryStringConverter>  
  
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
  
 .NET Framework, <xref:System.UriTemplate>adlı URI şablonlarıyla çalışmak için bir API sağlar. `UriTemplates` aşağıdakileri yapmanıza izin verir:  
  
- Şablonla eşleşen *tam kapalı bır URI* oluşturmak için `Bind` yöntemlerinden birini bir parametre kümesiyle çağırabilirsiniz. Bu, URI şablonundaki tüm değişkenlerin gerçek değerlerle değiştirildiği anlamına gelir.  
  
- Bir aday URI ile `Match`() öğesini çağırabilirsiniz. Bu, bir aday URI 'yi yapısal bölümlerine bölmek için şablon kullanır ve şablondaki değişkenlere göre etiketlendiği farklı URI parçalarını içeren bir sözlük döndürür.  
  
- `Bind`() ve `Match`(), `Match`(`Bind`(x)) çağırabilmeniz ve ile başlattığınız aynı ortamı geri dönebilmeniz için ters getirilir.  
  
 Bir veri yapısındaki <xref:System.UriTemplate> nesnelerinin her birini bağımsız olarak ele geçirebilen bir veri yapısında izlemek istediğiniz pek çok zaman vardır (özellikle sunucuda, URI 'ye dayalı bir hizmet işlemine bir istek gönderilirken gereklidir). <xref:System.UriTemplateTable> bir URI şablonları kümesini temsil eder ve bir dizi şablon ve aday URI verilen en iyi eşleşmeyi seçer. Bu, herhangi bir ağ yığını (WCF dahil) ile bağlantılı değildir, bu sayede gerektiğinde kullanabilirsiniz.  
  
 WCF hizmet modeli, hizmet işlemlerini bir <xref:System.UriTemplate>tarafından tanımlanan bir URI kümesiyle ilişkilendirmek için <xref:System.UriTemplate> ve <xref:System.UriTemplateTable> kullanımını sağlar. Bir hizmet işlemi, <xref:System.ServiceModel.Web.WebGetAttribute> veya <xref:System.ServiceModel.Web.WebInvokeAttribute>kullanarak bir <xref:System.UriTemplate>ilişkilendirilir. <xref:System.UriTemplate> ve <xref:System.UriTemplateTable>hakkında daha fazla bilgi için bkz. [UriTemplate ve UriTemplateTable](../../../../docs/framework/wcf/feature-details/uritemplate-and-uritemplatetable.md)  
  
## <a name="webget-and-webinvoke-attributes"></a>WebGet ve Webvoke öznitelikleri  
 WCF WEB HTTP Hizmetleri, çeşitli Invoke fiillerine (örneğin, HTTP POST, PUT ve DELETE) ek olarak alma fiillerini (örneğin, HTTP GET) kullanır. WCF WEB HTTP programlama modeli, hizmet geliştiricilerinin hem <xref:System.ServiceModel.Web.WebGetAttribute> hem de <xref:System.ServiceModel.Web.WebInvokeAttribute>hizmet işlemleriyle ilişkili URI şablonunu ve fiilini denetlemesine olanak tanır. <xref:System.ServiceModel.Web.WebGetAttribute> ve <xref:System.ServiceModel.Web.WebInvokeAttribute>, tek tek işlemlerin URI 'lere ve bu URI 'Ler ile ilişkili HTTP yöntemlerine nasıl bağlandığını denetlemenize olanak tanır. Örneğin, aşağıdaki kodda <xref:System.ServiceModel.Web.WebGetAttribute> ve <xref:System.ServiceModel.Web.WebInvokeAttribute> ekleme.  
  
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
  
 Yukarıdaki kod, aşağıdaki HTTP isteklerini yapmanıza olanak sağlar.  
  
 `GET /GetCustomer`  
  
 `POST /UpdateCustomerName`  
  
 <xref:System.ServiceModel.Web.WebInvokeAttribute> varsayılan olarak GÖNDERILECEK, ancak diğer fiiller için de kullanabilirsiniz.  
  
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
  
 WCF WEB HTTP programlama modelini kullanan bir WCF hizmetinin tüm bir örneğini görmek için bkz [. nasıl yapılır: Temel WCF Web http hizmeti oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-wcf-web-http-service.md)  
  
## <a name="uritemplate-query-string-parameters-and-urls"></a>UriTemplate sorgu dizesi parametreleri ve URL 'Leri  
 Web stili hizmetler bir Web tarayıcısından, bir hizmet işlemiyle ilişkili bir URL yazılarak çağrılabilir. Bu hizmet işlemleri, URL içindeki bir dize biçiminde belirtilmesi gereken sorgu dizesi parametreleri alabilir. Aşağıdaki tabloda bir URL ve kullanılan biçim içinde geçirilebilecek türler gösterilmektedir.  
  
|Type|Biçimi|  
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
|<xref:System.DateTime>|GG/AA/YYYY<br /><br /> AA/GG/YYYY HH: MM: SS [&#124;PM]<br /><br /> Ayın günü yılı<br /><br /> Ay günü yıl HH: MM: SS [&#124;PM]|  
|<xref:System.TimeSpan>|DD.HH:MM:SS<br /><br /> Burada gg = gün, SS = saat, MM = dakika, SS = saniye|  
|<xref:System.Guid>|Bir GUID, örneğin:<br /><br /> 936DA01F-9ABD-4d9d-80C7-02AF85C822A8|  
|<xref:System.DateTimeOffset>|AA/GG/YYYY SS: DD: SS MM: SS<br /><br /> Burada gg = gün, SS = saat, MM = dakika, SS = saniye|  
|Listelemeler|Örneğin, aşağıdaki kodda gösterildiği gibi, numaralandırmayı tanımlayan sabit listesi değeri.<br /><br /> `public enum Days{ Sunday, Monday, Tuesday, Wednesday, Thursday, Friday, Saturday };`<br /><br /> Sorgu dizesinde her bir numaralandırma değeri (veya ilgili tamsayı değerleri) belirtilebilir.|  
|Bir `TypeConverterAttribute` olan türler, türü dize gösterimine ve öğesinden dönüştürebilir.|Tür Dönüştürücüne bağlıdır.|  
  
## <a name="formats-and-the-wcf-web-http-programming-model"></a>Biçimler ve WCF WEB HTTP programlama modeli  
 WCF WEB HTTP programlama modelinin birçok farklı veri biçiminde çalışmak için yeni özellikleri vardır. Bağlama katmanında <xref:System.ServiceModel.WebHttpBinding>, aşağıdaki farklı veri türlerini okuyup yazabilir:  
  
- {1&gt;XML&lt;1}  
  
- JSON  
  
- Donuk ikili akışlar  
  
 Bu, WCF WEB HTTP programlama modelinin herhangi bir veri türünü işleyebileceği, ancak <xref:System.IO.Stream>karşı programlama yapabileceği anlamına gelir.  
  
 .NET Framework 3,5, JSON verileri (AJAX) ve dağıtım akışlarının yanı sıra (ATOM ve RSS dahil) destek sağlar. Bu özellikler hakkında daha fazla bilgi için bkz. [WCF Web http biçimlendirme](../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md)[WCF dağıtımı genel bakış](../../../../docs/framework/wcf/feature-details/wcf-syndication-overview.md) ve [AJAX Tümleştirme ve JSON desteği](../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md).  
  
## <a name="wcf-web-http-programming-model-and-security"></a>WCF WEB HTTP programlama modeli ve güvenliği  
 WCF WEB HTTP programlama modeli WS-* protokollerini desteklemediğinden, bir WCF WEB HTTP hizmetini güvenli hale getirmenin tek yolu, Hizmeti SSL kullanarak HTTPS üzerinden kullanıma sunmasıdır. IIS 7,0 ile SSL ayarlama hakkında daha fazla bilgi için bkz. [IIS 'de SSL uygulama](https://go.microsoft.com/fwlink/?LinkId=131613)  
  
## <a name="troubleshooting-the-wcf-web-http-programming-model"></a>WCF WEB HTTP programlama modeli sorunlarını giderme  
 Bir kanal oluşturmak için bir <xref:System.ServiceModel.Channels.ChannelFactoryBase%601> kullanarak WCF WEB HTTP hizmetlerini çağırırken <xref:System.ServiceModel.Description.WebHttpBehavior>, <xref:System.ServiceModel.Channels.ChannelFactoryBase%601>farklı bir <xref:System.ServiceModel.EndpointAddress> geçirilse bile yapılandırma dosyasında ayarlanan <xref:System.ServiceModel.EndpointAddress> kullanır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Dağıtımı](../../../../docs/framework/wcf/feature-details/wcf-syndication.md)
- [WCF Web HTTP Programlama Nesnesi Modeli](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-object-model.md)
- [WCF Web HTTP Programlama Modeli](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
