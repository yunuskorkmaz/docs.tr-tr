---
title: "WCF Web HTTP Programlama Modeli Genel Bakış"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 381fdc3a-6e6c-4890-87fe-91cca6f4b476
caps.latest.revision: "45"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4ebc3c349e0eedcbe20f126f5252dadf8a6b8096
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="wcf-web-http-programming-model-overview"></a>WCF Web HTTP Programlama Modeli Genel Bakış
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] WEB HTTP programlama modeli sağlar WEB HTTP Hizmetleri oluşturmak için gereken temel öğeleri [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]WEB HTTP Hizmetleri yelpazedeki Web tarayıcıları gibi olası istemcileri tarafından erişilecek tasarlanmıştır ve aşağıdaki benzersiz gereksinimlere sahiptir:  
  
-   **URI ve URI İşleme** URI'ler WEB HTTP Hizmetleri tasarımında merkezi bir rol oynar. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WEB HTTP programlama modeli kullanır <xref:System.UriTemplate> ve <xref:System.UriTemplateTable> sınıfları URI işleme özellikleri sağlar.  
  
-   **GET ve POST işlemleri için destek** WEB HTTP Hizmetleri GET fiili kullanım çeşitli yanı sıra veri alma için veri değişikliği ve Uzaktan çağırma fiiller çağırma. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WEB HTTP programlama modeli kullanır <xref:System.ServiceModel.Web.WebGetAttribute> ve <xref:System.ServiceModel.Web.WebInvokeAttribute> hizmet işlemleri hem GET hem de diğer HTTP fiilleri gibi PUT, POST ilişkilendirmek ve silmek için.  
  
-   **Birden çok veri biçimleri** Web stili Hizmetleri'ni birçok tür SOAP iletilerine ek veri işleme. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WEB HTTP programlama modeli kullanır <xref:System.ServiceModel.WebHttpBinding> ve <xref:System.ServiceModel.Description.WebHttpBehavior> XML belgeleri, JSON veri nesnesi ve ikili içerik görüntü, video dosyaları veya düz metin gibi akışları da dahil olmak üzere birçok farklı veri biçimleri desteklemek için.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WEB HTTP programlama modeli genişletir ulaşabileceği [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WEB HTTP Hizmetleri, AJAX ve JSON Hizmetleri ve dağıtım (ATOM/RSS) akışları içeren Web stili senaryoları için. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]AJAX ve JSON Hizmetleri bkz [AJAX tümleştirme ve JSON desteği](../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md). [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Dağıtım, bkz: [WCF dağıtımı genel bakış](../../../../docs/framework/wcf/feature-details/wcf-syndication-overview.md).  
  
 Bir WEB HTTP hizmetinden döndürülen veri türleri hakkında ek bir kısıtlama yoktur. Bir WEB HTTP hizmeti işleminin serializable bir tür döndürülebilir. Hangi veri türleri bir URL belirtilebilir bir sınırlama yoktur bir web tarayıcısı tarafından WEB HTTP hizmeti işlemleri olabileceğinden çağırır. Varsayılan olarak desteklenen hangi türleri hakkında daha fazla bilgi için bkz: **UriTemplate sorgu dizesi parametreleri ve URL'leri** bölümüne bakın. Varsayılan davranış, gerçek parametre türü için bir URL içinde belirtilen parametreler dönüştürme belirten kendi T:System.ServiceModel.Dispatcher.QueryStringConverter uygulamasını sağlayarak değiştirilebilir. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<xref:System.ServiceModel.Dispatcher.QueryStringConverter>  
  
> [!CAUTION]
>  İle yazılmış Hizmetler [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WEB HTTP programlama modeli SOAP iletilerine kullanmayın. SOAP kullanılmadığı için güvenlik özellikleri tarafından sağlanan [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kullanılamaz. Ancak taşıma tabanlı güvenlik hizmetiniz HTTPS ile barındırarak kullanabilirsiniz. [!INCLUDE[crabout](../../../../includes/crabout-md.md)][!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] güvenlik, bkz: [güvenliğine genel bakış](../../../../docs/framework/wcf/feature-details/security-overview.md)  
  
> [!WARNING]
>  WebDAV uzantısının IIS yüklemek, tüm PUT isteklerini işlemek için uzantı çalışır WebDAV bir HTTP 405 hata dönmek Web HTTP Hizmetleri neden olabilir. Bu sorunu çözmek için WebDAV uzantısının kaldırın veya WebDAV uzantısı, web siteniz için devre dışı bırakabilirsiniz. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][IIS ve WebDav](http://learn.iis.net/page.aspx/357/webdav-for-iis-70/)  
  
## <a name="uri-processing-with-uritemplate-and-uritemplatetable"></a>UriTemplate ve UriTemplateTable işleme URI  
 URI şablonları, yapısal olarak benzer URI'ler büyük kümesini ifade etmek için verimli bir sözdizimi sağlar. Örneğin, aşağıdaki şablonu, "a" ile başlamalı ve bitmelidir "c" Ara kesiminin ile değeri dikkate almaksızın üç segment URI'ler kümesini ifade eder: bir / {/c segmentlere}  
  
 Bu şablon URI'ler aşağıdaki gibi açıklanmaktadır:  
  
-   a/x/c  
  
-   a/y/c  
  
-   a/z/c  
  
-   ve benzeri.  
  
 Bu şablonda değişmez değer yerine değişken kesimi kuşak gösterimi ("{segment}") gösterir.  
  
 .NET framework URI Şablonlarıyla Çalışma adlı bir API sağlar <xref:System.UriTemplate>. `UriTemplates`aşağıdakileri yapmanıza olanak sağlar:  
  
-   Aşağıdakilerden birini çağırabilirsiniz `Bind` üretmek için parametreleri kümesini yöntemleriyle bir *tamamen-kapalı URI* şablonu ile eşleşen. Başka bir deyişle, tüm değişkenler URI şablonunu gerçek değerlerle değiştirilir.  
  
-   Çağırabilirsiniz `Match`(bir aday kendi destekçi URI bölümleri ve şablondaki değişkenleri göre etiketli URI'ın farklı bölümleri içeren bir sözlüğü döndürür aday ayırmak için bir şablon kullanır URI ile).  
  
-   `Bind`() ve `Match`(), böylece çağırabilirsiniz inverses olan `Match`( `Bind`(x)) ve başlattığınız ile aynı ortamı geri dönün.  
  
 (Bir istek URİ'SİNDE tabanlı bir hizmet işlemi için gönderme olduğu gerekli özellikle sunucuda) birçok kez olan bir dizi izlemek istediğiniz <xref:System.UriTemplate> bağımsız olarak her kapsanan bir adresi bir veri yapısı nesneleri Şablonlar. <xref:System.UriTemplateTable>URI şablonları kümesini temsil eder ve bir dizi şablonları ve bir aday URI verilen en iyi eşleşmeyi seçer. Bu belirli ağ yığınını ile bağlı değil ([!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] dahil) için gerekli olan her yerde kullanabilirsiniz.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Hizmet modeli kullanır <xref:System.UriTemplate> ve <xref:System.UriTemplateTable> URI tarafından tanımlanan bir dizi hizmet işlemleri ilişkilendirmek üzere bir <xref:System.UriTemplate>. Bir hizmet işlemi ile ilişkili bir <xref:System.UriTemplate>, kullanarak <xref:System.ServiceModel.Web.WebGetAttribute> veya <xref:System.ServiceModel.Web.WebInvokeAttribute>. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<xref:System.UriTemplate> ve <xref:System.UriTemplateTable>, bkz: [UriTemplate ve UriTemplateTable](../../../../docs/framework/wcf/feature-details/uritemplate-and-uritemplatetable.md)  
  
## <a name="webget-and-webinvoke-attributes"></a>WebGet ve Webınvoke öznitelikleri  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]WEB HTTP Hizmetleri alma fiilleri (örneğin HTTP GET) ek olarak çeşitli kullanın (örneğin HTTP POST, PUT ve Sil) fiillerini çağırma. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WEB HTTP programlama modeli sağlayan hizmet geliştiricileri denetim hem URI şablonunu ve kendi hizmet işlemleriyle ilişkili fiil <xref:System.ServiceModel.Web.WebGetAttribute> ve <xref:System.ServiceModel.Web.WebInvokeAttribute>. <xref:System.ServiceModel.Web.WebGetAttribute> Ve <xref:System.ServiceModel.Web.WebInvokeAttribute> nasıl tek tek işlemleri denetlemenizi URI'ler için bağlanan ve HTTP yöntemleri bu URI ile ilişkili izin verir. Örneğin, ekleme <xref:System.ServiceModel.Web.WebGetAttribute> ve <xref:System.ServiceModel.Web.WebInvokeAttribute> aşağıdaki kodda.  
  
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
  
 Önceki kod, aşağıdaki HTTP isteklerini yapmanızı sağlar.  
  
 `GET /GetCustomer`  
  
 `POST /UpdateCustomerName`  
  
 <xref:System.ServiceModel.Web.WebInvokeAttribute>POST ancak varsayılanlara bunu diğer fiiller için de kullanabilirsiniz.  
  
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
  
 Tam bir örnek görmek için bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kullanan hizmet [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WEB HTTP programlama modeli, bkz: [nasıl yapılır: temel bir WCF Web HTTP hizmeti oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-wcf-web-http-service.md)  
  
## <a name="uritemplate-query-string-parameters-and-urls"></a>UriTemplate sorgu dizesi parametreleri ve URL'leri  
 Web stili Hizmetleri hizmet işlemle ilişkili bir URL yazarak bir Web tarayıcısından çağrılabilir. Bu hizmet işlemleri URL'de dize biçimindeki belirtilmelidir sorgu dizesi parametreleri sürebilir. Aşağıdaki tabloda bir URL ve kullanılan biçimi içinde geçirilen türleri gösterilmektedir.  
  
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
|<xref:System.Single>|-3.402823e38 - 3.402823e38 (üstel gösterimde gerekli değildir)|  
|<xref:System.Double>|-1.79769313486232e308 - 1.79769313486232e308 (üstel gösterimde gerekli değildir)|  
|<xref:System.Char>|Herhangi bir tek karakteri|  
|<xref:System.Decimal>|Tüm ondalık standart gösteriminde (üs yok)|  
|<xref:System.Boolean>|TRUE veya False (duyarsız büyük-küçük harf)|  
|<xref:System.String>|Herhangi bir dize (dize desteklenmez ve yok kaçış yapılır null)|  
|<xref:System.DateTime>|AA/GG/YYYY<br /><br /> AA/GG/YYYY SS: DD: [AM &#124; PM]<br /><br /> Ayın günü yıl<br /><br /> Ay gün yıl ss [AM &#124; PM]|  
|<xref:System.TimeSpan>|GG SS: DD:<br /><br /> Burada gg gün, ss = = saat, dd dakika, SS = = saniye|  
|<xref:System.Guid>|Örneğin bir GUID:<br /><br /> 936DA01F-9ABD-4d9d-80C7-02AF85C822A8|  
|<xref:System.DateTimeOffset>|AA/GG/YYYY SS: DD: SS: DD<br /><br /> Burada gg gün, ss = = saat, dd dakika, SS = = saniye|  
|Numaralandırmalar|Numaralandırma değeri örneğin, aşağıdaki kodda gösterildiği gibi numaralandırması tanımlayan.<br /><br /> `public enum Days{ Sunday, Monday, Tuesday, Wednesday, Thursday, Friday, Saturday };`<br /><br /> Tek tek numaralandırma değerlerini (ya da bunlara karşılık gelen tamsayı değerler) herhangi birini sorgu dizesinde belirtilen.|  
|Türleri bir `TypeConverterAttribute` , dönüştürebilir türü için ve bir dize gösterimi.|Tür dönüştürücü bağlıdır.|  
  
## <a name="formats-and-the-wcf-web-http-programming-model"></a>Biçimleri ve WCF WEB HTTP programlama modeli  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WEB HTTP programlama modeli birçok farklı veri biçimleri ile çalışmak için yeni özelliklere sahiptir. Bağlama katmanında <xref:System.ServiceModel.WebHttpBinding> okuma ve yazma aşağıdaki farklı veri türleri:  
  
-   XML  
  
-   JSON  
  
-   Donuk ikili akışlar  
  
 Yani [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WEB HTTP programlama modeli, istediğiniz türde veriyi işleyebilen ancak karşı programlama <xref:System.IO.Stream>.  
  
 [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)]JSON verilerini (AJAX) yanı sıra dağıtım akışlarını (ATOM ve RSS dahil) destekler. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Bu özellikler bkz [WCF Web HTTP biçimlendirme](../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md)[WCF dağıtımı genel bakış](../../../../docs/framework/wcf/feature-details/wcf-syndication-overview.md) ve [AJAX tümleştirme ve JSON desteği](../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md).  
  
## <a name="wcf-web-http-programming-model-and-security"></a>WCF WEB HTTP programlama modeli ve güvenlik  
 Çünkü [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WEB HTTP programlama modeli desteklemez WS-* protokoller, güvenli hale getirmek için tek yolu bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WEB HTTP hizmeti hizmeti SSL ile HTTPS üzerinden kullanıma etmektir. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]SSL ile ayarlama [!INCLUDE[iisver](../../../../includes/iisver-md.md)], bkz: [IIS'te SSL uygulama](http://go.microsoft.com/fwlink/?LinkId=131613)  
  
## <a name="troubleshooting-the-wcf-web-http-programming-model"></a>WCF WEB HTTP programlama modeli sorunlarını giderme  
 WCF WEB HTTP çağırma zaman Hizmetleri kullanarak bir <xref:System.ServiceModel.Channels.ChannelFactoryBase%601> bir kanal oluşturmak için <xref:System.ServiceModel.Description.WebHttpBehavior> kullanan <xref:System.ServiceModel.EndpointAddress> dosya olsa bile farklı bir ayarla <xref:System.ServiceModel.EndpointAddress> geçirilir <xref:System.ServiceModel.Channels.ChannelFactoryBase%601>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WCF dağıtımı](../../../../docs/framework/wcf/feature-details/wcf-syndication.md)  
 [WCF Web HTTP programlama nesnesi modeli](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-object-model.md)  
 [WCF Web HTTP programlama modeli](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
