---
title: "Nasıl yapılır: AJAX Etkinleştirilmiş ASP.NET Web Hizmetlerini WCF'ye Taşıma"
ms.date: 03/30/2017
ms.assetid: 1428df4d-b18f-4e6d-bd4d-79ab3dd5147c
ms.openlocfilehash: f492efe9e364195dce6b73a14e9ca5fa34a6df25
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972298"
---
# <a name="how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf"></a>Nasıl yapılır: AJAX Etkinleştirilmiş ASP.NET Web Hizmetlerini WCF'ye Taşıma
Bu konuda, temel bir ASP.NET AJAX hizmetini eşdeğer bir AJAX özellikli Windows Communication Foundation (WCF) hizmetine geçirme yordamları özetlenmektedir. Bir ASP.NET AJAX hizmetinin işlevsel WCF sürümünün nasıl oluşturulacağını gösterir. İki hizmet daha sonra yan yana kullanılabilir veya WCF hizmeti ASP.NET AJAX hizmetini değiştirmek için kullanılabilir.

 Mevcut bir ASP.NET AJAX hizmetini bir WCF AJAX hizmetine geçirmek aşağıdaki avantajları sağlar:

- AJAX hizmetinizi, en az ek yapılandırmaya sahip bir SOAP hizmeti olarak kullanıma sunabilirsiniz.

- İzleme gibi WCF özelliklerinden faydalanabilirsiniz.

 Aşağıdaki yordamlarda, Visual Studio 2012 kullandığınızı varsayalım.

 Bu konuda özetlenen yordamlardan kaynaklanan kod, yordamları izleyen örnekte verilmiştir.

 Bir WCF hizmetini Ajax özellikli bir uç nokta aracılığıyla gösterme hakkında daha fazla bilgi için bkz [. nasıl yapılır: ASP.NET AJAX uç noktası](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md) konu başlığı eklemek için yapılandırma kullanın.

### <a name="to-create-and-test-the-aspnet-web-service-application"></a>ASP.NET Web hizmeti uygulamasını oluşturmak ve test etmek için

1. Visual Studio 2012 ' i açın.

2. **Dosya** menüsünde **Yeni**' yi ve ardından **Proje**' yi seçin ve ardından **ASP.NET Web hizmeti uygulaması** **' nı seçin**.

3. Projeyi `ASPHello` adlandırın ve **Tamam**' a tıklayın.

4. Bu hizmet için AJAX 'ı etkinleştirmek üzere içeren `System.Web.Script.Services.ScriptService]` Service1.asmx.cs dosyasındaki satırın açıklamasını kaldırın.

5. **Build** menüsünde **Build Solution**' ı seçin.

6. **Hata Ayıkla** menüsünden **hata ayıklama olmadan Başlat**' ı seçin.

7. Oluşturulan Web sayfasında `HelloWorld` işlemi seçin.

8. `HelloWorld` Test sayfasındaki **çağır** düğmesine tıklayın. Aşağıdaki XML yanıtını almalısınız.

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <string xmlns="http://tempuri.org/">Hello World</string>
    ```

9. Bu yanıt artık çalışan bir ASP.NET AJAX hizmetine sahip olduğunuza ve özellikle de hizmetin, HTTP POST isteklerine yanıt veren ve XML döndüren Service1. asmx/HelloWorld yolunda bir uç nokta açığa çıkardığına onaylar.

     Artık bu hizmeti bir WCF AJAX hizmeti kullanmak üzere dönüştürmeye hazırsınız.

### <a name="to-create-an-equivalent-wcf-ajax-service-application"></a>Eşdeğer bir WCF AJAX hizmet uygulaması oluşturmak için

1. **ASPHello** projesine sağ tıklayın ve **Ekle**, **Yeni öğe**ve ardından **AJAX etkin WCF hizmeti**' ni seçin.

2. Hizmeti `WCFHello` adlandırın ve **Ekle**' ye tıklayın.

3. WCFHello.svc.cs dosyasını açın.

4. Service1.asmx.cs 'den, `HelloWorld` işlemin aşağıdaki uygulamasını kopyalayın.

    ```csharp
    public string HelloWorld()
    {
         return "Hello World";
    }
    ```

5. `HelloWorld` İşlemin kopyalanmış uygulamasına aşağıdaki kodun yerine WCFHello.svc.cs dosyasına yapıştırın.

    ```csharp
    public void DoWork()
    {
          // Add your operation implementation here
          return;
    }
    ```

6. `Namespace` İçin<xref:System.ServiceModel.ServiceContractAttribute>özniteliğini belirtin .`WCFHello`

    ```csharp
    [ServiceContract(Namespace="WCFHello")]
    [AspNetCompatibilityRequirements(RequirementsMode=AspNetCompatibilityRequirementsMode.Required)]
    public class WCFHello
    { … }
    ```

7. Öğesini işleme ekleyin <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A> ve özelliği döndürecek<xref:System.ServiceModel.Web.WebMessageFormat.Xml>şekildeayarlayın. <xref:System.ServiceModel.Web.WebInvokeAttribute> `HelloWorld` Ayarlanmamışsa, varsayılan dönüş türünün olduğunu <xref:System.ServiceModel.Web.WebMessageFormat.Json>unutmayın.

    ```csharp
    [OperationContract]
    [WebInvoke(ResponseFormat=WebMessageFormat.Xml)]
    public string HelloWorld()
    {
        return "Hello World";
    }
    ```

8. **Build** menüsünde **Build Solution**' ı seçin.

9. WCFHello. svc dosyasını açın ve **Hata Ayıkla** menüsünden **hata ayıklama olmadan Başlat**' ı seçin.

10. Hizmet artık http post isteklerine yanıt veren `WCFHello.svc/HelloWorld`' de bir uç nokta kullanıma sunuyor. HTTP POST istekleri tarayıcıdan test edilemez, ancak uç nokta XML 'den sonraki XML 'yi döndürüyor.

    ```xml
    <string xmlns="http://schemas.microsoft.com/2003/10/Serialization/">Hello World</string>
    ```

11. `WCFHello.svc/HelloWorld` Veuçnoktalar`Service1.aspx/HelloWorld` artık işlevsel olarak eşdeğerdir.

## <a name="example"></a>Örnek
 Bu konuda özetlenen yordamlardan kaynaklanan kod aşağıdaki örnekte verilmiştir.

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

 <xref:System.Xml.XmlDocument> Türü <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> , tarafından<xref:System.Xml.Serialization.XmlSerializer>seri hale getirilmediğinden tarafından desteklenmez. Bir <xref:System.Xml.Linq.XDocument> tür kullanabilir veya <xref:System.Xml.XmlDocument.DocumentElement%2A> bunun yerine seri hale getirebilirsiniz.

 ASMX Web Hizmetleri yükseltilmekte ve yan yana WCF hizmetlerine geçiriliyorsa, iki türü istemcide aynı ada eşlemektan kaçının. Bu, bir <xref:System.Web.Services.WebMethodAttribute> <xref:System.ServiceModel.ServiceContractAttribute>ve ' de aynı tür kullanılıyorsa serileştiricde bir özel duruma neden olur:

- İlk olarak WCF hizmeti eklenirse, Web hizmetindeki sıranın WCF stil tanımı öncelikli <xref:System.Web.UI.ObjectConverter.ConvertValue%28System.Object%2CSystem.Type%2CSystem.String%29> olduğundan asmx Web hizmeti üzerindeki yöntemi çağırmak özel duruma neden olur.

- Önce asmx Web hizmeti eklenirse, WCF hizmetinde çağırma yöntemi ' de <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> özel durum oluşmasına neden olur çünkü proxy 'deki sıranın Web hizmeti stil tanımı öncelik kazanır.

 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> Ve ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer>arasındaki davranışta önemli farklılıklar vardır. Örneğin <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> , bir sözlüğü anahtar/değer çiftleri dizisi olarak temsil ederken, ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer> bir sözlüğü gerçek JSON nesneleri olarak temsil eder. Bu nedenle, ASP.NET AJAX içinde temsil edilen sözlük aşağıda verilmiştir.

```csharp
Dictionary<string, int> d = new Dictionary<string, int>();
d.Add("one", 1);
d.Add("two", 2);
```

 Bu sözlük, aşağıdaki listede gösterildiği gibi JSON nesnelerinde temsil edilir:

- [{"Key": "One", "Value": 1}, {"Key": "iki", "Value": 2}],<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>

- {"One": 1, "iki": 2} ASP.NET AJAX tarafından<xref:System.Web.Script.Serialization.JavaScriptSerializer>

 , <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> Anahtar türünün dize olmadığı, <xref:System.Web.Script.Serialization.JavaScriptSerializer> ancak işleyememesi durumunda sözlüklerin işleyebileceği anlamda daha güçlüdür. Ancak ikincisi JSON kullanımı daha fazla.

 Bu serileştiriciler arasındaki önemli farklılıklar aşağıdaki tabloda özetlenmiştir.

|Farklar kategorisi|DataContractJsonSerializer|ASP.NET AJAX JavaScriptSerializer|
|-----------------------------|--------------------------------|---------------------------------------|
|Boş arabellek (yeni bayt [0]) içinde <xref:System.Object> (veya <xref:System.Uri>başka bir sınıfa) seri durumdan çıkarılamadı.|SerializationException|null|
|Serileştirme<xref:System.DBNull.Value>|{}(veya {"__type": "#System"})|Null|
|[Serializable] türlerinin özel üyelerinin serileştirilmesi.|metodu|serileştirilmedi|
|<xref:System.Runtime.Serialization.ISerializable> Türlerin ortak özelliklerinin serileştirilmesi.|serileştirilmedi|metodu|
|JSON "Extensions"|Nesne üye adlarında tırnak işareti gerektiren JSON belirtimine uyar ({"a": "Hello"}).|Tırnak işaretleri olmadan nesne üyelerinin adlarını destekler ({a: "Hello"}).|
|<xref:System.DateTime>Eşgüdümlü Evrensel Saat (UTC)|\\"\\/Date (123456789U)&#124;\\\\\\/" veya "\\/Date (\d + (U (+\\-[\d{4}])) biçimini desteklemez mi?) \\\\/)".|\\"\\/Date (123456789U)&#124;\\\\\\/" ve "\\/Date (\d + (U (+\\-[\d{4}])) biçimini destekler mi?) \\ /)"\\değerini DateTime değerleri olarak.|
|Sözlüklerin temsili|Bir KeyValuePair\<K, V > dizisi, dizeler olmayan anahtar türlerini işler.|Gerçek JSON nesneleri olarak-ancak yalnızca dizeler olan anahtar türlerini işler.|
|Kaçan karakterler|Her zaman kaçış eğik çizgiyle (/); "\n" gibi, kaçırılmamış geçersiz JSON karakterlerinin hiçbir şekilde yapılmasına izin vermez.|Tarih/saat değerleri için çıkış ileri eğik çizgi (/) ile.|

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: ASP.NET AJAX uç noktası eklemek için yapılandırma kullanma](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md)
