---
title: "Nasıl yapılır: AJAX etkinleştirilmiş ASP.NET Web hizmetlerini WCF'ye taşıma"
ms.date: 03/30/2017
ms.assetid: 1428df4d-b18f-4e6d-bd4d-79ab3dd5147c
ms.openlocfilehash: 3c7052a67e756ae0c3fa1692c3ed746419384de4
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2019
ms.locfileid: "58410946"
---
# <a name="how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf"></a>Nasıl yapılır: AJAX etkinleştirilmiş ASP.NET Web hizmetlerini WCF'ye taşıma
Bu konu, temel bir ASP.NET AJAX hizmeti eşdeğer bir AJAX etkinleştirilmiş Windows Communication Foundation (WCF) hizmetine geçirme yordamları özetler. Bu, bir ASP.NET AJAX Hizmeti işlevsel olarak eşdeğer bir WCF sürümü oluşturma işlemini gösterir. İki hizmeti daha sonra bir yan yana kullanılabilir veya WCF hizmetini ASP.NET AJAX hizmeti değiştirmek için kullanılabilir.

 Mevcut bir ASP.NET AJAX geçiş hizmetine bir WCF AJAX hizmeti aşağıdaki faydaları sağlar:

-   AJAX hizmetinizi en az bir ek yapılandırma ile bir SOAP hizmet olarak kullanıma sunabilirsiniz.

-   WCF izleme gibi özelliklerinden yararlanmak ve benzeri.

 Aşağıdaki yordamlar, Visual Studio 2012 kullandığınızı varsayar.

 Bu konu başlığında açıklanan yordamları oluşur kodu prosedürleri izliyorsanız örnekte sağlanır.

 WCF hizmet AJAX etkinleştirilmiş bir uç nokta aracılığıyla kullanıma sunma hakkında daha fazla bilgi için bkz. [nasıl yapılır: ASP.NET AJAX uç noktası eklemek için yapılandırma kullanma](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md) konu.

### <a name="to-create-and-test-the-aspnet-web-service-application"></a>Oluşturma ve ASP.NET Web hizmeti uygulamasını test etmek için

1.  Visual Studio 2012'yi açın.

2.  Gelen **dosya** menüsünde **yeni**, ardından **proje**, ardından **Web**ve ardından **ASP.NET Web hizmeti uygulaması** .

3.  Projeyi adlandırın `ASPHello` tıklatıp **Tamam**.

4.  Service1.asmx.cs dosyasındaki içeren satırı açıklamadan çıkarın `System.Web.Script.Services.ScriptService]` bu hizmet için AJAX etkinleştirmek için.

5.  Gelen **derleme** menüsünde **Çözümü Derle**.

6.  Gelen **hata ayıklama** menüsünde **hata ayıklama olmadan Başlat**.

7.  Oluşturulan Web sayfası üzerinde seçmek `HelloWorld` işlemi.

8.  Tıklayın **Invoke** düğmesini `HelloWorld` test sayfası. Aşağıdaki XML yanıtı almanız gerekir.

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <string xmlns="http://tempuri.org/">Hello World</string>
    ```

9. Bu yanıt artık çalışan bir ASP.NET AJAX hizmeti olan ve özellikle hizmet, bir uç noktada yanıt için HTTP POST Service1.asmx/HelloWorld artık kullanıma ve istekleri XML döndürür, onaylar.

     Bir WCF AJAX hizmeti kullanmak için bu hizmetin dönüştürmek hazırsınız.

### <a name="to-create-an-equivalent-wcf-ajax-service-application"></a>Eşdeğer bir AJAX WCF hizmet uygulaması oluşturmak için

1.  Sağ **ASPHello** seçin ve proje **Ekle**, ardından **yeni öğe**, ardından **AJAX özellikli bir WCF Hizmeti**.

2.  Hizmet adı `WCFHello` tıklatıp **Ekle**.

3.  WCFHello.svc.cs dosyasını açın.

4.  Aşağıdaki uygulamasını service1.asmx.cs kopyalayın `HelloWorld` işlemi.

    ```
    public string HelloWorld()
    {
         return "Hello World";
    }
    ```

5.  Kopyalanan uygulaması Yapıştır `HelloWorld` WCFHello.svc.cs dosyasına aşağıdaki kodu yerine işlemi.

    ```
    public void DoWork()
    {
          // Add your operation implementation here
          return;
    }
    ```

6.  Belirtin `Namespace` özniteliğini <xref:System.ServiceModel.ServiceContractAttribute> olarak `WCFHello`.

    ```
    [ServiceContract(Namespace="WCFHello")]
    [AspNetCompatibilityRequirements(RequirementsMode=AspNetCompatibilityRequirementsMode.Required)]
    public class WCFHello
    { … }
    ```

7.  Ekleme <xref:System.ServiceModel.Web.WebInvokeAttribute> için `HelloWorld` işlemi ve kümesi <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A> dönmesini <xref:System.ServiceModel.Web.WebMessageFormat.Xml>. Ayarlanırsa, dönüş türü varsayılan değilse unutmayın <xref:System.ServiceModel.Web.WebMessageFormat.Json>.

    ```
    [OperationContract]
    [WebInvoke(ResponseFormat=WebMessageFormat.Xml)]
    public string HelloWorld()
    {
        return "Hello World";
    }
    ```

8.  Gelen **derleme** menüsünde **Çözümü Derle**.

9. WCFHello.svc dosyasını açın ve **hata ayıklama** menüsünde **hata ayıklama olmadan Başlat**.

10. Hizmet artık bir uç noktada kullanıma sunan `WCFHello.svc/HelloWorld`, HTTP POST istekleri için yanıt verir. Tarayıcısından HTTP POST istekleri sınanamıyor ancak uç noktası aşağıdaki XML XML döndürür.

    ```xml
    <string xmlns="http://schemas.microsoft.com/2003/10/Serialization/">Hello World</string>
    ```

11. `WCFHello.svc/HelloWorld` Ve `Service1.aspx/HelloWorld` noktalarıdır artık eşdeğer işleve sahiptir.

## <a name="example"></a>Örnek
 Bu konu başlığında açıklanan yordamları oluşur kodu, aşağıdaki örnekte sağlanır.

```csharp
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

 <xref:System.Xml.XmlDocument> Türü tarafından desteklenmiyor <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> tarafından seri hale getirilebilir olmadığından <xref:System.Xml.Serialization.XmlSerializer>. Kullanabilirsiniz bir <xref:System.Xml.Linq.XDocument> yazın veya serileştirmek <xref:System.Xml.XmlDocument.DocumentElement%2A> yerine.

 ASMX Web Hizmetleri yükseltilmekte olan ve WCF hizmetleri için yan yana geçişi, iki tür istemci üzerinde aynı ad eşleme kaçının. Aynı tür kullanılırsa bu bir özel durum seri hale getiricileri genişletme içinde neden bir <xref:System.Web.Services.WebMethodAttribute> ve <xref:System.ServiceModel.ServiceContractAttribute>:

-   WCF Hizmeti önce eklediyseniz, özel durum ASMX Web hizmeti yönteminin çağrılması neden <xref:System.Web.UI.ObjectConverter.ConvertValue%28System.Object%2CSystem.Type%2CSystem.String%29> proxy sırayla WCF stil tanımını öncelikli olduğundan.

-   ASMX Web hizmeti önce eklediyseniz, WCF Hizmeti metodu çağrılırken özel durum neden <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> proxy sırayla Web hizmeti stil tanımını öncelikli olduğundan.

 Davranış önemli farklılıkları vardır <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> ve ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer>. Örneğin, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> bir sözlük ise anahtar/değer çiftleri dizisi olarak temsil eden ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer> bir sözlük gerçek bir JSON nesnesi temsil eder. ASP.NET AJAX içinde gösterilen sözlüğe aşağıdaki nedenle.

```
Dictionary<string, int> d = new Dictionary<string, int>();
d.Add("one", 1);
d.Add("two", 2);
```

 Bu sözlük, aşağıdaki listede gösterildiği gibi JSON nesnesi temsil edilir:

-   [{"Key": "Bir", "Value": 1}, {"Key": "İki", "Value": 2}] olarak <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>

-   {"bir": 1 "iki": 2} ASP.NET AJAX ile <xref:System.Web.Script.Serialization.JavaScriptSerializer>

 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> , Anahtar türü dizesi olduğu sözlükleri işleyebilir anlamda daha güçlüdür ancak <xref:System.Web.Script.Serialization.JavaScriptSerializer> olamaz. Ancak, daha kolay JSON ikincisidir.

 Bu seri hale getiricileri genişletme arasında önemli farklılıklar aşağıdaki tabloda özetlenmiştir.

|Farklar kategorisi|DataContractJsonSerializer|ASP.NET AJAX JavaScriptSerializer|
|-----------------------------|--------------------------------|---------------------------------------|
|Boş arabellek seri durumdan çıkarılırken (içine yeni byte[0]) <xref:System.Object> (veya <xref:System.Uri>, ya da diğer bazı sınıflar).|SerializationException|null|
|Serileştirme <xref:System.DBNull.Value>|{} (veya {"__type": "#System"})|Null|
|Özel üyelerin [Serializable] türlerin seri hale getirme.|seri hale getirilmiş|Serileştirilmiş değil|
|Genel özellikleri serileştirmek <xref:System.Runtime.Serialization.ISerializable> türleri.|Serileştirilmiş değil|seri hale getirilmiş|
|JSON "uzantıları"|Üye adlarının nesne tekliflerinde gerektirir JSON belirtimi için uyar ({"a": "hello"}).|Nesne üyeleri ({y: "hello"}) tırnak işaretleri olmadan adlarını destekler.|
|<xref:System.DateTime> Eşgüdümlü Evrensel Saat (UTC)|Biçimini desteklemiyor "\\/Date(123456789U)\\/" veya "\\/tarih\\(\d+ (U&#124;(\\+\\-[\d{4}]))?\\) \\\\/)".|Destekler biçim "\\/Date(123456789U)\\/" ve "\\/tarih\\(\d+ (U&#124;(\\+\\-[\d{4}]))?\\) \\ \\/) "olarak DateTime değerleri.|
|Sözlükler temsili|Bir dizi KeyValuePair\<K, V >, dize olmayan anahtar türünü işler.|Gerçek JSON nesneleri - ancak dizelerdir yalnızca tanıtıcıları anahtar türleri.|
|Kaçan karakter|Her zaman bir kaçış ile eğik çizgi (/); ilet hiçbir zaman "\n" gibi kaçılmamış geçersiz JSON karaktere izin verilir.|Eğik çizgi (/) DateTime değerleri için bir kaçış ile iletin.|

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: ASP.NET AJAX uç noktası eklemek için yapılandırma kullanma](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md)
