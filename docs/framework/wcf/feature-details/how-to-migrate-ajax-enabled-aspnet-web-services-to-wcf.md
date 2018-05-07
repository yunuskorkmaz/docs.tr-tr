---
title: "Nasıl yapılır: AJAX Etkinleştirilmiş ASP.NET Web Hizmetlerini WCF'ye Taşıma"
ms.date: 03/30/2017
ms.assetid: 1428df4d-b18f-4e6d-bd4d-79ab3dd5147c
ms.openlocfilehash: 048408adf8678c243a225a233cb1173c9b7f869f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf"></a>Nasıl yapılır: AJAX Etkinleştirilmiş ASP.NET Web Hizmetlerini WCF'ye Taşıma
Bu konu, temel ASP.NET AJAX hizmeti eşdeğer bir AJAX etkinleştirilmiş Windows Communication Foundation (WCF) hizmetine geçirme yordamları özetler. Bir ASP.NET AJAX Hizmeti işlevsel olarak eşdeğer bir WCF sürümü oluşturulacağını gösterir. İki hizmet daha sonra bir yan yana kullanılabilir veya WCF hizmeti, ASP.NET AJAX hizmeti değiştirmek için kullanılabilir.  
  
 Mevcut bir ASP.NET AJAX geçiş hizmetine bir WCF AJAX hizmeti, aşağıdaki avantajları sunar:  
  
-   Minimal ek yapılandırma ile SOAP hizmet olarak AJAX hizmetinizi getirebilir.  
  
-   İzleme gibi WCF özelliklerinden yararlanır ve benzeri.  
  
 Aşağıdaki yordamlar, kullandığınızı varsayar [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].  
  
 Bu konuda anlatılan yordamlar oluşur kod yordamları aşağıdaki örnekte sağlanır.  
  
 Bir WCF hizmeti bir AJAX etkinleştirilmiş uç nokta aracılığıyla gösterme hakkında daha fazla bilgi için bkz: [nasıl yapılır: ASP.NET AJAX uç noktası eklemek için yapılandırma kullan](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md) konu.  
  
### <a name="to-create-and-test-the-aspnet-web-service-application"></a>Oluşturmak ve ASP.NET Web hizmeti uygulamasını sınamak için  
  
1.  Açık [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].  
  
2.  Gelen **dosya** menüsünde, select **yeni**, ardından **proje**, ardından **Web**ve ardından **ASP.NET Web hizmeti uygulama** .  
  
3.  Proje adı `ASPHello` tıklatıp **Tamam**.  
  
4.  İçeren Service1.asmx.cs dosyasında satırı açıklamadan kaldırmasına `System.Web.Script.Services.ScriptService]` AJAX bu hizmeti etkinleştirmek için.  
  
5.  Gelen **yapı** menüsünde, select **yapı çözümü**.  
  
6.  Gelen **hata ayıklama** menüsünde, select **hata ayıklama olmadan Başlat**.  
  
7.  Oluşturulan Web sayfası üzerinde seçmek `HelloWorld` işlemi.  
  
8.  Tıklatın **Invoke** düğmesini `HelloWorld` test sayfası. Aşağıdaki XML yanıtı almanız gerekir.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <string xmlns="http://tempuri.org/">Hello World</string>  
    ```  
  
9. Bu yanıt işlevsel bir ASP.NET AJAX hizmeti artık vardır ve özellikle, hizmet, bir HTTP POST yanıt Service1.asmx/HelloWorld uçta şimdi kullanıma ve istekleri XML döndürür, onaylar.  
  
     Artık bir WCF AJAX hizmeti kullanmak için bu hizmet dönüştürmek hazırsınız.  
  
### <a name="to-create-an-equivalent-wcf-ajax-service-application"></a>Bir eşdeğer WCF AJAX hizmet uygulaması oluşturmak için  
  
1.  Sağ **ASPHello** proje ve seçin **Ekle**, ardından **yeni öğe**ve ardından **AJAX etkinleştirilmiş WCF Hizmeti**.  
  
2.  Ad hizmeti `WCFHello` tıklatıp **Ekle**.  
  
3.  WCFHello.svc.cs dosyasını açın.  
  
4.  Aşağıdaki uygulanması service1.asmx.cs kopyalama `HelloWorld` işlemi.  
  
    ```  
    public string HelloWorld()  
    {  
         return "Hello World";  
    }  
    ```  
  
5.  Kopyalanan uyarlamasını Yapıştır `HelloWorld` WCFHello.svc.cs dosyasına aşağıdaki kodu yerine işlemi.  
  
    ```  
    public void DoWork()  
    {  
          // Add your operation implementation here  
          return;  
    }  
    ```  
  
6.  Belirtin `Namespace` için öznitelik <xref:System.ServiceModel.ServiceContractAttribute> olarak `WCFHello`.  
  
    ```  
    [ServiceContract(Namespace="WCFHello")]  
    [AspNetCompatibilityRequirements(RequirementsMode=AspNetCompatibilityRequirementsMode.Required)]  
    public class WCFHello  
    { … }  
    ```  
  
7.  Ekleme <xref:System.ServiceModel.Web.WebInvokeAttribute> için `HelloWorld` işlemi ve kümesi <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A> dönmek için özellik <xref:System.ServiceModel.Web.WebMessageFormat.Xml>. Dönüş türü olan varsayılan ayarlanmış değilse unutmayın <xref:System.ServiceModel.Web.WebMessageFormat.Json>.  
  
    ```  
    [OperationContract]  
    [WebInvoke(ResponseFormat=WebMessageFormat.Xml)]  
    public string HelloWorld()  
    {  
        return "Hello World";  
    }  
    ```  
  
8.  Gelen **yapı** menüsünde, select **yapı çözümü**.  
  
9. WCFHello.svc dosyasını açın ve **hata ayıklama** menüsünde, select **hata ayıklama olmadan Başlat**.  
  
10. Hizmet artık bir uç noktada kullanıma sunan `WCFHello.svc/HelloWorld`, HTTP POST isteklerine yanıt verir. HTTP POST isteklerini tarayıcıdan sınanamıyor ancak uç nokta XML aşağıdaki XML döndürür.  
  
    ```xml  
    <string xmlns="http://schemas.microsoft.com/2003/10/Serialization/">Hello World</string>  
    ```  
  
11. `WCFHello.svc/HelloWorld` Ve `Service1.aspx/HelloWorld` uç noktaları işlevsel olarak eşdeğer şimdi.  
  
## <a name="example"></a>Örnek  
 Bu konuda anlatılan yordamlar oluşur kod, aşağıdaki örnekte sağlanır.  
  
```  
//This is the ASP.NET code in the Service1.asmx.cs file.  
  
using System;  
using System.Collections;  
using System.ComponentModel;  
using System.Data;  
using System.Linq;  
using System.Web;  
using System.Web.Services;  
using System.Web.Services.Protocols;  
using System.Xml.Linq;  
using System.Web.Script.Services;  
  
namespace ASPHello  
{  
    /// <summary>  
    /// Summary description for Service1.  
    /// </summary>  
    [WebService(Namespace = "http://tempuri.org/")]  
    [WebServiceBinding(ConformsTo = WsiProfiles.BasicProfile1_1)]  
    [ToolboxItem(false)]  
    // To allow this Web Service to be called from script, using ASP.NET AJAX, uncomment the following line.   
    [System.Web.Script.Services.ScriptService]  
    public class Service1 : System.Web.Services.WebService  
    {  
  
        [WebMethod]  
        public string HelloWorld()  
        {  
            return "Hello World";  
        }  
    }  
}   
  
//This is the WCF code in the WCFHello.svc.cs file.  
using System;  
using System.Linq;  
using System.Runtime.Serialization;  
using System.ServiceModel;  
using System.ServiceModel.Activation;  
using System.ServiceModel.Web;  
  
namespace ASPHello  
{  
    [ServiceContract(Namespace = "WCFHello")]  
    [AspNetCompatibilityRequirements(RequirementsMode = AspNetCompatibilityRequirementsMode.Allowed)]  
    public class WCFHello  
    {  
        // Add [WebInvoke] attribute to use HTTP GET.  
        [OperationContract]  
        [WebInvoke(ResponseFormat=WebMessageFormat.Xml)]  
        public string HelloWorld()  
        {  
            return "Hello World";  
        }  
  
        // Add more operations here and mark them with [OperationContract].  
    }  
}  
```  
  
 <xref:System.Xml.XmlDocument> Türü tarafından desteklenmiyor <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> tarafından seri hale getirilebilir olmadığından <xref:System.Xml.Serialization.XmlSerializer>. Ya da kullanabileceğiniz bir <xref:System.Xml.Linq.XDocument> yazın veya seri <xref:System.Xml.XmlDocument.DocumentElement%2A> yerine.  
  
 ASMX Web Hizmetleri yükseltilen ve yan yana WCF hizmetlerine geçirilir, istemcideki aynı adı için iki tür eşleme kaçının. Aynı türde kullanılıyorsa bu bir özel durum serileştiricileri neden olan bir <xref:System.Web.Services.WebMethodAttribute> ve <xref:System.ServiceModel.ServiceContractAttribute>:  
  
-   WCF Hizmeti önce eklediyseniz, özel durum ASMX Web hizmeti yöntemi çağırma neden <xref:System.Web.UI.ObjectConverter.ConvertValue%28System.Object%2CSystem.Type%2CSystem.String%29> proxy sırayla WCF stil tanımını öncelikli olduğundan.  
  
-   ASMX Web hizmeti önce eklediyseniz, WCF Hizmeti üzerinde yöntemi çağrılırken özel durum neden <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> proxy sırayla Web hizmeti stil tanımını öncelikli olduğundan.  
  
 Davranış önemli farklılıkları vardır <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> ve ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer>. Örneğin, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> bir sözlüğü ancak temsil eden bir anahtar/değer çiftleri dizisi olarak ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer> bir sözlük gerçek JSON nesnelerini temsil eder. Aşağıdaki ASP.NET AJAX ' temsil sözlük gelir.  
  
```  
Dictionary<string, int> d = new Dictionary<string, int>();  
d.Add("one", 1);  
d.Add("two", 2);  
```  
  
 Bu sözlük JSON nesneleri aşağıdaki listede gösterildiği gibi gösterilir:  
  
-   [{"Anahtarı": "Bir", "Value": 1}, {"Anahtarı": "İki", "Value": 2}] tarafından <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>  
  
-   {"bir": 1, "iki": 2} ASP.NET AJAX tarafından <xref:System.Web.Script.Serialization.JavaScriptSerializer>  
  
 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> Bu anahtar türü dizesi olduğu sözlükler işleyebilir anlamda daha güçlüdür ancak <xref:System.Web.Script.Serialization.JavaScriptSerializer> olamaz. Ancak ikinci daha JSON kolay.  
  
 Bu serileştiricileri arasında önemli farklılıklar aşağıdaki tabloda özetlenmiştir.  
  
|Farkları kategorisi|DataContractJsonSerializer|ASP.NET AJAX JavaScriptSerializer|  
|-----------------------------|--------------------------------|---------------------------------------|  
|Boş arabellek seri durumdan (içine yeni byte[0]) <xref:System.Object> (veya <xref:System.Uri>, ya da başka bir sınıf).|SerializationException|null|  
|Seri hale getirilmesi için <xref:System.DBNull.Value>|{} (veya {"__type": "#System"})|Null|  
|Serileştirme [Serializable] türleri özel üyeleri.|seri hale getirilmiş|Serileştirilmiş değil|  
|Ortak özellikleri serileştirmek <xref:System.Runtime.Serialization.ISerializable> türleri.|Serileştirilmiş değil|seri hale getirilmiş|  
|JSON "uzantılarını"|Nesne üyesi adlarını tekliflerinde gerektirir JSON belirtimi aynılarını ({"a": "hello"}).|Nesne üyeleri tırnak işaretleri ({a: "hello"}) olmadan adlarını destekler.|  
|<xref:System.DateTime> Eşgüdümlü Evrensel Saat (UTC)|Biçim desteklemiyor "\\/Date(123456789U)\\/" veya "\\/Date\\(\d+ (U&#124;(\\+\\-[\d{4}]))?\\) \\\\/)".|Destekler biçimi "\\/Date(123456789U)\\/" ve "\\/Date\\(\d+ (U&#124;(\\+\\-[\d{4}]))?\\) \\ \\/) "DateTime değerleri olarak.|  
|Sözlük gösterimi|Bir dizi KeyValuePair\<K, V >, dize olmayan anahtar türleri işler.|Gerçek JSON nesnelerinin - ancak dizelerdir yalnızca tanıtıcıları anahtar türü.|  
|Kaçış karakterli karakterleri|Her zaman bir kaçış ile eğik çizgi (/); ilet hiçbir zaman "\n" gibi atlanmamış geçersiz JSON karaktere izin verilir.|Bir kaçış ile eğik çizgi (/) DateTime değerleri için iletin.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: ASP.NET AJAX Uç Noktası Eklemek için Yapılandırma Kullanma](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md)
