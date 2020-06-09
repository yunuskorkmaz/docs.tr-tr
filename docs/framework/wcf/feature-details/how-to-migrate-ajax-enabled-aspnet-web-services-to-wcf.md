---
title: "Nasıl yapılır: AJAX Etkinleştirilmiş ASP.NET Web Hizmetlerini WCF'ye Taşıma"
ms.date: 03/30/2017
ms.assetid: 1428df4d-b18f-4e6d-bd4d-79ab3dd5147c
ms.openlocfilehash: 6f356f47922945218e02271371d9ddea36ecc5a2
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597013"
---
# <a name="how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf"></a>Nasıl yapılır: AJAX Etkinleştirilmiş ASP.NET Web Hizmetlerini WCF'ye Taşıma
Bu konuda, temel bir ASP.NET AJAX hizmetini eşdeğer bir AJAX özellikli Windows Communication Foundation (WCF) hizmetine geçirme yordamları özetlenmektedir. Bir ASP.NET AJAX hizmetinin işlevsel WCF sürümünün nasıl oluşturulacağını gösterir. İki hizmet daha sonra yan yana kullanılabilir veya WCF hizmeti ASP.NET AJAX hizmetini değiştirmek için kullanılabilir.

 Mevcut bir ASP.NET AJAX hizmetini bir WCF AJAX hizmetine geçirmek aşağıdaki avantajları sağlar:

- AJAX hizmetinizi, en az ek yapılandırmaya sahip bir SOAP hizmeti olarak kullanıma sunabilirsiniz.

- İzleme gibi WCF özelliklerinden faydalanabilirsiniz.

 Aşağıdaki yordamlarda, Visual Studio 2012 kullandığınızı varsayalım.

 Bu konuda özetlenen yordamlardan kaynaklanan kod, yordamları izleyen örnekte verilmiştir.

 Bir WCF hizmetini AJAX özellikli bir uç nokta aracılığıyla gösterme hakkında daha fazla bilgi için bkz. [nasıl yapılır: yapılandırma kullanımı ASP.NET AJAX uç noktası ekleme](how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md) konusu.

### <a name="to-create-and-test-the-aspnet-web-service-application"></a>ASP.NET Web hizmeti uygulamasını oluşturmak ve test etmek için

1. Visual Studio 2012 ' i açın.

2. **Dosya** menüsünde **Yeni**' yi ve ardından **Proje**' yi seçin ve ardından **ASP.NET Web hizmeti uygulaması** **' nı seçin**.

3. Projeyi adlandırın `ASPHello` ve **Tamam**' a tıklayın.

4. `System.Web.Script.Services.ScriptService]`Bu hizmet IÇIN Ajax 'ı etkinleştirmek üzere içeren Service1.asmx.cs dosyasındaki satırın açıklamasını kaldırın.

5. **Build** menüsünde **Build Solution**' ı seçin.

6. **Hata Ayıkla** menüsünden **Hata Ayıklama Olmadan Başlat**’ı seçin.

7. Oluşturulan Web sayfasında `HelloWorld` işlemi seçin.

8. Test sayfasındaki **çağır** düğmesine tıklayın `HelloWorld` . Aşağıdaki XML yanıtını almalısınız.

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <string xmlns="http://tempuri.org/">Hello World</string>
    ```

9. Bu yanıt artık çalışan bir ASP.NET AJAX hizmetine sahip olduğunuza ve özellikle de hizmetin, HTTP POST isteklerine yanıt veren ve XML döndüren Service1. asmx/HelloWorld yolunda bir uç nokta açığa çıkardığına onaylar.

     Artık bu hizmeti bir WCF AJAX hizmeti kullanmak üzere dönüştürmeye hazırsınız.

### <a name="to-create-an-equivalent-wcf-ajax-service-application"></a>Eşdeğer bir WCF AJAX hizmet uygulaması oluşturmak için

1. **ASPHello** projesine sağ tıklayın ve **Ekle**, **Yeni öğe**ve ardından **AJAX etkin WCF hizmeti**' ni seçin.

2. Hizmeti adlandırın `WCFHello` ve **Ekle**' ye tıklayın.

3. WCFHello.svc.cs dosyasını açın.

4. Service1.asmx.cs 'den, işlemin aşağıdaki uygulamasını kopyalayın `HelloWorld` .

    ```csharp
    public string HelloWorld()
    {
        return "Hello World";
    }
    ```

5. İşlemin kopyalanmış uygulamasına `HelloWorld` aşağıdaki kodun yerine WCFHello.svc.cs dosyasına yapıştırın.

    ```csharp
    public void DoWork()
    {
          // Add your operation implementation here
          return;
    }
    ```

6. `Namespace`İçin özniteliğini belirtin <xref:System.ServiceModel.ServiceContractAttribute> `WCFHello` .

    ```csharp
    [ServiceContract(Namespace="WCFHello")]
    [AspNetCompatibilityRequirements(RequirementsMode=AspNetCompatibilityRequirementsMode.Required)]
    public class WCFHello
    { … }
    ```

7. Öğesini <xref:System.ServiceModel.Web.WebInvokeAttribute> `HelloWorld` işleme ekleyin ve <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A> özelliği döndürecek şekilde ayarlayın <xref:System.ServiceModel.Web.WebMessageFormat.Xml> . Ayarlanmamışsa, varsayılan dönüş türünün olduğunu unutmayın <xref:System.ServiceModel.Web.WebMessageFormat.Json> .

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

10. Hizmet artık `WCFHello.svc/HelloWorld` http post isteklerine yanıt veren ' de bir uç nokta kullanıma sunuyor. HTTP POST istekleri tarayıcıdan test edilemez, ancak uç nokta XML 'den sonraki XML 'yi döndürüyor.

    ```xml
    <string xmlns="http://schemas.microsoft.com/2003/10/Serialization/">Hello World</string>
    ```

11. `WCFHello.svc/HelloWorld`Ve `Service1.aspx/HelloWorld` uç noktalar artık işlevsel olarak eşdeğerdir.

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

 <xref:System.Xml.XmlDocument>Türü <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> , tarafından seri hale getirilmediğinden tarafından desteklenmez <xref:System.Xml.Serialization.XmlSerializer> . Bir <xref:System.Xml.Linq.XDocument> tür kullanabilir veya bunun yerine seri hale getirebilirsiniz <xref:System.Xml.XmlDocument.DocumentElement%2A> .

 ASMX Web Hizmetleri yükseltilmekte ve yan yana WCF hizmetlerine geçiriliyorsa, iki türü istemcide aynı ada eşlemektan kaçının. Bu, bir ve ' de aynı tür kullanılıyorsa serileştiricde bir özel duruma neden olur <xref:System.Web.Services.WebMethodAttribute> <xref:System.ServiceModel.ServiceContractAttribute> :

- İlk olarak WCF hizmeti eklenirse, Web hizmetindeki <xref:System.Web.UI.ObjectConverter.ConvertValue%28System.Object%2CSystem.Type%2CSystem.String%29> SıRANıN WCF stil tanımı öncelikli olduğundan asmx Web hizmeti üzerindeki yöntemi çağırmak özel duruma neden olur.

- Önce ASMX Web hizmeti eklenirse, WCF hizmetinde çağırma yöntemi ' de özel durum oluşmasına neden olur <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> çünkü proxy 'deki sıranın Web hizmeti stil tanımı öncelik kazanır.

 Ve ASP.NET AJAX arasındaki davranışta önemli farklılıklar vardır <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> <xref:System.Web.Script.Serialization.JavaScriptSerializer> . Örneğin, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> bir sözlüğü anahtar/değer çiftleri dizisi olarak temsil ederken, ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer> bir sözlüğü gerçek JSON nesneleri olarak temsil eder. Bu nedenle, ASP.NET AJAX içinde temsil edilen sözlük aşağıda verilmiştir.

```csharp
Dictionary<string, int> d = new Dictionary<string, int>();
d.Add("one", 1);
d.Add("two", 2);
```

 Bu sözlük, aşağıdaki listede gösterildiği gibi JSON nesnelerinde temsil edilir:

- [{"Key": "One", "Value": 1}, {"Key": "iki", "Value": 2}],<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>

- {"One": 1, "iki": 2} ASP.NET AJAX tarafından<xref:System.Web.Script.Serialization.JavaScriptSerializer>

 , <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> Anahtar türünün dize olmadığı, ancak işleyememesi durumunda sözlüklerin işleyebileceği anlamda daha güçlüdür <xref:System.Web.Script.Serialization.JavaScriptSerializer> . Ancak ikincisi JSON kullanımı daha fazla.

 Bu serileştiriciler arasındaki önemli farklılıklar aşağıdaki tabloda özetlenmiştir.

|Farklar kategorisi|DataContractJsonSerializer|ASP.NET AJAX JavaScriptSerializer|
|-----------------------------|--------------------------------|---------------------------------------|
|Boş arabellek (yeni bayt [0]) içinde <xref:System.Object> (veya <xref:System.Uri> başka bir sınıfa) seri durumdan çıkarılamadı.|SerializationException|null|
|Serileştirme<xref:System.DBNull.Value>|{}(veya {"__type": "#System"})|Null|
|[Serializable] türlerinin özel üyelerinin serileştirilmesi.|metodu|serileştirilmedi|
|Türlerin ortak özelliklerinin serileştirilmesi <xref:System.Runtime.Serialization.ISerializable> .|serileştirilmedi|metodu|
|JSON "Extensions"|Nesne üye adlarında tırnak işareti gerektiren JSON belirtimine uyar ({"a": "Hello"}).|Tırnak işaretleri olmadan nesne üyelerinin adlarını destekler ({a: "Hello"}).|
|<xref:System.DateTime>Eşgüdümlü Evrensel Saat (UTC)|" \\ /Date (123456789U) \\ /" veya " \\ /date \\ (\d + (U&#124; ( \\ + \\ -[\d {4} ])) biçimini desteklemez mi? \\ ) \\ \\ /)".|" \\ /Date (123456789U) \\ /" ve " \\ /date \\ (\d + (U&#124; ( \\ + \\ -[\d {4} ])) biçimini destekler mi? \\ ) \\ \\ /) "değerini DateTime değerleri olarak.|
|Sözlüklerin temsili|Bir KeyValuePair dizisi \<K,V> , dizeler olmayan anahtar türlerini işler.|Gerçek JSON nesneleri olarak-ancak yalnızca dizeler olan anahtar türlerini işler.|
|Kaçan karakterler|Her zaman kaçış eğik çizgiyle (/); "\n" gibi, kaçırılmamış geçersiz JSON karakterlerinin hiçbir şekilde yapılmasına izin vermez.|Tarih/saat değerleri için çıkış ileri eğik çizgi (/) ile.|

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: ASP.NET AJAX Uç Noktası Eklemek için Yapılandırma Kullanma](how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md)
