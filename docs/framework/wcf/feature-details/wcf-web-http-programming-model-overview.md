---
title: WCF Web HTTP Programlama Modeli Genel Bakış
ms.date: 03/30/2017
ms.assetid: 381fdc3a-6e6c-4890-87fe-91cca6f4b476
ms.openlocfilehash: 64428eb209d8ab4e708640ed1418765e16b4577a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54577743"
---
# <a name="wcf-web-http-programming-model-overview"></a>WCF Web HTTP Programlama Modeli Genel Bakış
Windows Communication Foundation (WCF) WEB HTTP programlama modeli ile WCF WEB HTTP Hizmetleri oluşturmak için gereken temel öğeleri sağlar. WCF WEB HTTP Hizmetleri yelpazedeki Web tarayıcıları dahil olmak üzere, olası istemcileri tarafından erişilecek şekilde tasarlanmıştır ve aşağıdaki benzersiz gereksinimleri vardır:  
  
-   **URI ve URI İşleme** URI'ler, WEB HTTP Hizmetleri tasarımında merkezi bir rol oynar. WCF WEB HTTP programlama modeli kullanan <xref:System.UriTemplate> ve <xref:System.UriTemplateTable> URI işleme özelliklerini sağlayan sınıflar.  
  
-   **GET ve POST işlemleri desteği** WEB HTTP Hizmetleri GET fiili kullanımı için veri alma, çeşitli ek olarak veri değişikliği ve Uzaktan çağırma fiilleri çağırma. WCF WEB HTTP programlama modeli kullanan <xref:System.ServiceModel.Web.WebGetAttribute> ve <xref:System.ServiceModel.Web.WebInvokeAttribute> hizmet işlemleri hem GET hem de diğer HTTP fiilleri gibi PUT, POST ilişkilendirmek ve SİLEBİLİRSİNİZ.  
  
-   **Birden çok veri biçimini** Web stili Hizmetleri'ni pek çok SOAP iletilerini yanı sıra veri işleme. WCF WEB HTTP programlama modeli kullanan <xref:System.ServiceModel.WebHttpBinding> ve <xref:System.ServiceModel.Description.WebHttpBehavior> XML belgeleri, JSON veri nesnesi ve ikili içerik görüntü, video dosyaları veya düz metin gibi akışları dahil olmak üzere birçok farklı veri biçimleri desteklemek için.  
  
 WCF WEB HTTP programlama modeli ulaşma WCF WEB HTTP Hizmetleri, AJAX ve JSON Hizmetleri ve dağıtım (ATOM/RSS) akışlarını Web stili senaryoları kapsayacak şekilde genişletir. AJAX ve JSON hizmetleri hakkında daha fazla bilgi için bkz. [AJAX tümleştirme ve JSON desteği](../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md). Dağıtım hakkında daha fazla bilgi için bkz: [WCF dağıtımı genel bakış](../../../../docs/framework/wcf/feature-details/wcf-syndication-overview.md).  
  
 Bir WEB HTTP hizmetinden döndürülen veri türleri hakkında ek kısıtlama yoktur. Bir WEB HTTP hizmeti işleminin serializable bir tür döndürülebilir. Hangi veri türlerini URL'de belirtilebilir bir sınırlama yoktur bir web tarayıcısı tarafından WEB HTTP hizmeti işlemleri olabileceğinden çağırın. Varsayılan olarak desteklenen hangi türleri hakkında daha fazla bilgi için bkz. **UriTemplate sorgu dizesi parametreleri ve URL'leri** bölümüne bakın. Gerçek parametre türü için bir URL içinde belirtilen parametreleri nasıl dönüştürme yapılacağını belirten kendi T:System.ServiceModel.Dispatcher.QueryStringConverter uygulamanız sağlayarak varsayılan davranış değiştirilebilir. Daha fazla bilgi için bkz. <xref:System.ServiceModel.Dispatcher.QueryStringConverter>  
  
> [!CAUTION]
>  WCF WEB HTTP programlama modeli ile yazılmış hizmetler SOAP iletilerini kullanmayın. SOAP kullanılmadığından WCF tarafından sağlanan güvenlik özellikleri kullanılamaz. Ancak taşıma tabanlı güvenlik hizmetiniz HTTPS ile barındırarak kullanabilirsiniz. WCF güvenlik hakkında daha fazla bilgi için bkz: [güvenliğine genel bakış](../../../../docs/framework/wcf/feature-details/security-overview.md)  
  
> [!WARNING]
>  WebDAV uzantısının yüklenmesi için IIS Web HTTP Hizmetleri tüm PUT isteklerini işlemek için uzantı çalışır WebDAV bir HTTP 405 hata döndürmek neden olabilir. Bu sorunu çözmek için WebDAV uzantısının kaldırın veya WebDAV uzantısının web siteniz için devre dışı bırakabilirsiniz. Daha fazla bilgi için [IIS ve WebDav](https://learn.iis.net/page.aspx/357/webdav-for-iis-70/)  
  
## <a name="uri-processing-with-uritemplate-and-uritemplatetable"></a>UriTemplate ve UriTemplateTable ile işleme URI'si  
 URI şablonları, yapısal olarak benzer bir URI'leri büyük kümesini ifade etmek için verimli bir söz dizimi sağlar. Örneğin, aşağıdaki şablon "a" ile başlayan ve "c" Ara kesiminin ile değer bakılmaksızın son üç segment URI'lerin kümesini ifade eder: bir / {/c segmentlere}  
  
 Bu şablon, URI aşağıdaki gibi açıklanmaktadır:  
  
-   a/x/c  
  
-   a/y/c  
  
-   a/z/c  
  
-   ve benzeri.  
  
 Bu şablonda değişmez değer yerine değişken bir segment kuşak gösterim ("{segment}") gösterir.  
  
 .NET framework URI şablonları ile çalışma adlı bir API sağlar <xref:System.UriTemplate>. `UriTemplates` aşağıdakileri yapmanıza olanak sağlar:  
  
-   Aşağıdakilerden birini çağırabilirsiniz `Bind` üretmek için parametreleri kümesini yöntemleriyle bir *tamamen-kapalı URI* şablonu ile eşleşen. Başka bir deyişle, tüm değişkenler için URI şablonu gerçek değerlerle değiştirilir.  
  
-   Çağırabilirsiniz `Match`() ile bir aday URI, kendi destekçi URI bölümleri ve şablon değişkenleri göre etiketli URI farklı kısımlarını içeren bir sözlüğü döndürür bir aday bölmeniz için bir şablon kullanır.  
  
-   `Bind`() ve `Match`(), böylece çağırabilirsiniz inverses olan `Match`( `Bind`(x)); başladığınız sürümle aynı ortamıyla geri dönün.  
  
 (Bir istek URİ'SİNDE tabanlı bir hizmet işlemi için gönderme olduğu gerekli özellikle sunucu üzerinde) birden çok kez olan bir dizi izlemek istediğiniz <xref:System.UriTemplate> ele bağımsız olarak içerdiği her bir veri yapısına nesneleri şablonları. <xref:System.UriTemplateTable> URI şablonları kümesini temsil eder ve verilen bir dizi şablonları ve bir aday URI en iyi eşleşmeyi seçer. Gerekli olan her yerde kullanabilirsiniz, böylece bu (WCF dahil) tüm belirli ağ yığınını ile ilişkili değildir.  
  
 WCF hizmet modeli kullanır <xref:System.UriTemplate> ve <xref:System.UriTemplateTable> hizmet işlemleri tarafından açıklanan bir URI'leri kümesi ile ilişkilendirmek için bir <xref:System.UriTemplate>. Bir hizmet işlemi ile ilişkili bir <xref:System.UriTemplate>, kullanarak <xref:System.ServiceModel.Web.WebGetAttribute> veya <xref:System.ServiceModel.Web.WebInvokeAttribute>. Hakkında daha fazla bilgi için <xref:System.UriTemplate> ve <xref:System.UriTemplateTable>, bkz: [UriTemplate ve UriTemplateTable](../../../../docs/framework/wcf/feature-details/uritemplate-and-uritemplatetable.md)  
  
## <a name="webget-and-webinvoke-attributes"></a>WebGet ve Webınvoke öznitelikleri  
 WCF WEB HTTP Hizmetleri alma fiiller (örneğin HTTP GET) ek olarak çeşitli kullanımını fiiller (örneğin HTTP POST, PUT ve DELETE) çağırır. WCF WEB HTTP programlama modeli sağlar denetimi hem URI şablonu ve hizmet işlemlerini ile ilişkili fiili hizmet geliştiricileri <xref:System.ServiceModel.Web.WebGetAttribute> ve <xref:System.ServiceModel.Web.WebInvokeAttribute>. <xref:System.ServiceModel.Web.WebGetAttribute> Ve <xref:System.ServiceModel.Web.WebInvokeAttribute> denetlemenize nasıl tek işlemler için bir URI'leri bağlanan ve HTTP yöntemleri bu bir URI'leri ile ilişkili izin verir. Örneğin, ekleme <xref:System.ServiceModel.Web.WebGetAttribute> ve <xref:System.ServiceModel.Web.WebInvokeAttribute> aşağıdaki kodda.  
  
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
  
 Yukarıdaki kod, aşağıdaki HTTP isteklerini yapmanızı sağlar.  
  
 `GET /GetCustomer`  
  
 `POST /UpdateCustomerName`  
  
 <xref:System.ServiceModel.Web.WebInvokeAttribute> POST, ancak varsayılan olarak, diğer fiiller için de kullanabilirsiniz.  
  
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
  
 WCF WEB HTTP programlama modeli kullanan bir WCF hizmeti için tam bir örnek görmek için bkz: [nasıl yapılır: Temel bir WCF Web HTTP hizmeti oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-wcf-web-http-service.md)  
  
## <a name="uritemplate-query-string-parameters-and-urls"></a>UriTemplate sorgu dizesi parametreleri ve URL'leri  
 Bir hizmet işlemi ile ilişkili olan bir URL yazarak Web stili hizmetler bir Web tarayıcısından çağrılabilir. Bu hizmet işlemleri URL'de bir dize biçiminde belirtilmelidir sorgu dizesi parametreleri alabilir. Aşağıdaki tabloda, bir URL ve kullanılan biçimi içinde geçirilebilir türleri gösterilmektedir.  
  
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
|<xref:System.Single>|-3.402823e38 - 3.402823e38 (üstel gösterim gerekli değildir)|  
|<xref:System.Double>|-1.79769313486232e308 - 1.79769313486232e308 (üstel gösterim gerekli değildir)|  
|<xref:System.Char>|Herhangi bir tek karakter|  
|<xref:System.Decimal>|Herhangi bir ondalık standart gösteriminde (üs yok)|  
|<xref:System.Boolean>|TRUE veya False (/ küçük harfe duyarlı durumda)|  
|<xref:System.String>|Herhangi bir dize (dize desteklenmez ve yok kaçış yapılır null)|  
|<xref:System.DateTime>|AA/GG/YYYY<br /><br /> AA/GG/YYYY SS [ÖÖ&AMP;#124;PM]<br /><br /> Ay gün/yıl<br /><br /> Ayın günü yıl ss [ÖÖ&#124;PM]|  
|<xref:System.TimeSpan>|DD.HH:MM:SS<br /><br /> Burada DD HH günler ve = = saat, dakika, SS aa = saniye =|  
|<xref:System.Guid>|Örneğin bir GUID:<br /><br /> 936DA01F-9ABD-4d9d-80C7-02AF85C822A8|  
|<xref:System.DateTimeOffset>|AA/GG/YYYY SS: DD: SS<br /><br /> Burada DD HH günler ve = = saat, dakika, SS aa = saniye =|  
|Numaralandırmalar|Numaralandırma değeri örneğin, aşağıdaki kodda gösterildiği gibi sabit listesi tanımlar.<br /><br /> `public enum Days{ Sunday, Monday, Tuesday, Wednesday, Thursday, Friday, Saturday };`<br /><br /> Herhangi bir tek numaralandırma değerlerinden (veya bunlara karşılık gelen bir tamsayı değerler), sorgu dizesinde belirtilebilir.|  
|Sahip türleri bir `TypeConverterAttribute` , türüne dönüştürebilir ve gelen bir dize gösterimi.|Tür dönüştürücü üzerinde bağlıdır.|  
  
## <a name="formats-and-the-wcf-web-http-programming-model"></a>Biçimleri ve WCF WEB HTTP programlama modeli  
 WCF WEB HTTP programlama modeli, birçok farklı veri biçimleri ile çalışmaya yeni özelliğe sahiptir. Bağlama katmanında <xref:System.ServiceModel.WebHttpBinding> okuyabilir ve aşağıdaki farklı türlerde veri yazabilirsiniz:  
  
-   XML  
  
-   JSON  
  
-   Donuk ikili akışlar  
  
 WCF WEB HTTP programlama modeli, her türden veriyi işleyebileceği ancak karşı programlama yani <xref:System.IO.Stream>.  
  
 [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] Destek için JSON verileri (AJAX) yanı sıra dağıtım akışlarını (ATOM ve RSS dahil) sağlar. Bu özellikler hakkında daha fazla bilgi için bkz. [WCF Web HTTP biçimlendirme](../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md)[WCF dağıtımı genel bakış](../../../../docs/framework/wcf/feature-details/wcf-syndication-overview.md) ve [AJAX tümleştirme ve JSON desteği](../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md).  
  
## <a name="wcf-web-http-programming-model-and-security"></a>WCF WEB HTTP programlama modeli ve güvenlik  
 WCF WEB HTTP programlama modeli WS - desteklemediği için * protokoller, güvenli bir WCF WEB HTTP hizmeti için tek yoludur hizmeti SSL ile HTTPS üzerinden göstermek için. SSL ile ayarlama hakkında daha fazla bilgi için [!INCLUDE[iisver](../../../../includes/iisver-md.md)], bkz: [IIS'te SSL uygulama](https://go.microsoft.com/fwlink/?LinkId=131613)  
  
## <a name="troubleshooting-the-wcf-web-http-programming-model"></a>WCF WEB HTTP programlama modeli sorunlarını giderme  
 Ne zaman çağırma WCF WEB HTTP Hizmetleri kullanarak bir <xref:System.ServiceModel.Channels.ChannelFactoryBase%601> bir kanal oluşturmak için <xref:System.ServiceModel.Description.WebHttpBehavior> kullanan <xref:System.ServiceModel.EndpointAddress> yapılandırma dosyasını çift ise farklı bir kümesi <xref:System.ServiceModel.EndpointAddress> geçirilir <xref:System.ServiceModel.Channels.ChannelFactoryBase%601>.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [WCF Dağıtımı](../../../../docs/framework/wcf/feature-details/wcf-syndication.md)
- [WCF Web HTTP Programlama Nesnesi Modeli](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-object-model.md)
- [WCF Web HTTP Programlama Modeli](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
