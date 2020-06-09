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
# <a name="how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf"></a><span data-ttu-id="0c72a-102">Nasıl yapılır: AJAX Etkinleştirilmiş ASP.NET Web Hizmetlerini WCF'ye Taşıma</span><span class="sxs-lookup"><span data-stu-id="0c72a-102">How to: Migrate AJAX-Enabled ASP.NET Web Services to WCF</span></span>
<span data-ttu-id="0c72a-103">Bu konuda, temel bir ASP.NET AJAX hizmetini eşdeğer bir AJAX özellikli Windows Communication Foundation (WCF) hizmetine geçirme yordamları özetlenmektedir.</span><span class="sxs-lookup"><span data-stu-id="0c72a-103">This topic outlines procedures to migrate a basic ASP.NET AJAX service to an equivalent AJAX-enabled Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="0c72a-104">Bir ASP.NET AJAX hizmetinin işlevsel WCF sürümünün nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="0c72a-104">It shows how to create a functionally equivalent WCF version of an ASP.NET AJAX service.</span></span> <span data-ttu-id="0c72a-105">İki hizmet daha sonra yan yana kullanılabilir veya WCF hizmeti ASP.NET AJAX hizmetini değiştirmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0c72a-105">The two services can then be used side by side, or the WCF service can be used to replace the ASP.NET AJAX service.</span></span>

 <span data-ttu-id="0c72a-106">Mevcut bir ASP.NET AJAX hizmetini bir WCF AJAX hizmetine geçirmek aşağıdaki avantajları sağlar:</span><span class="sxs-lookup"><span data-stu-id="0c72a-106">Migrating an existing ASP.NET AJAX service to a WCF AJAX service gives you the following benefits:</span></span>

- <span data-ttu-id="0c72a-107">AJAX hizmetinizi, en az ek yapılandırmaya sahip bir SOAP hizmeti olarak kullanıma sunabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0c72a-107">You can expose your AJAX service as a SOAP service with minimal extra configuration.</span></span>

- <span data-ttu-id="0c72a-108">İzleme gibi WCF özelliklerinden faydalanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0c72a-108">You can benefit from WCF features such as tracing, and so on.</span></span>

 <span data-ttu-id="0c72a-109">Aşağıdaki yordamlarda, Visual Studio 2012 kullandığınızı varsayalım.</span><span class="sxs-lookup"><span data-stu-id="0c72a-109">The following procedures assume that you are using Visual Studio 2012.</span></span>

 <span data-ttu-id="0c72a-110">Bu konuda özetlenen yordamlardan kaynaklanan kod, yordamları izleyen örnekte verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="0c72a-110">The code that results from the procedures outlined in this topic is provided in the example following the procedures.</span></span>

 <span data-ttu-id="0c72a-111">Bir WCF hizmetini AJAX özellikli bir uç nokta aracılığıyla gösterme hakkında daha fazla bilgi için bkz. [nasıl yapılır: yapılandırma kullanımı ASP.NET AJAX uç noktası ekleme](how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md) konusu.</span><span class="sxs-lookup"><span data-stu-id="0c72a-111">For more information about exposing a WCF service through an AJAX-enabled endpoint, see the [How to: Use Configuration to Add an ASP.NET AJAX Endpoint](how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md) topic.</span></span>

### <a name="to-create-and-test-the-aspnet-web-service-application"></a><span data-ttu-id="0c72a-112">ASP.NET Web hizmeti uygulamasını oluşturmak ve test etmek için</span><span class="sxs-lookup"><span data-stu-id="0c72a-112">To create and test the ASP.NET Web service application</span></span>

1. <span data-ttu-id="0c72a-113">Visual Studio 2012 ' i açın.</span><span class="sxs-lookup"><span data-stu-id="0c72a-113">Open Visual Studio 2012.</span></span>

2. <span data-ttu-id="0c72a-114">**Dosya** menüsünde **Yeni**' yi ve ardından **Proje**' yi seçin ve ardından **ASP.NET Web hizmeti uygulaması** **' nı seçin**.</span><span class="sxs-lookup"><span data-stu-id="0c72a-114">From the **File** menu, select **New**, then **Project**, then **Web**, and then select **ASP.NET Web Service Application**.</span></span>

3. <span data-ttu-id="0c72a-115">Projeyi adlandırın `ASPHello` ve **Tamam**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="0c72a-115">Name the project `ASPHello` and click **OK**.</span></span>

4. <span data-ttu-id="0c72a-116">`System.Web.Script.Services.ScriptService]`Bu hizmet IÇIN Ajax 'ı etkinleştirmek üzere içeren Service1.asmx.cs dosyasındaki satırın açıklamasını kaldırın.</span><span class="sxs-lookup"><span data-stu-id="0c72a-116">Uncomment the line in the Service1.asmx.cs file that contains `System.Web.Script.Services.ScriptService]` to enable AJAX for this service.</span></span>

5. <span data-ttu-id="0c72a-117">**Build** menüsünde **Build Solution**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="0c72a-117">From the **Build** menu, select **Build Solution**.</span></span>

6. <span data-ttu-id="0c72a-118">**Hata Ayıkla** menüsünden **Hata Ayıklama Olmadan Başlat**’ı seçin.</span><span class="sxs-lookup"><span data-stu-id="0c72a-118">From the **Debug** menu, select **Start Without Debugging**.</span></span>

7. <span data-ttu-id="0c72a-119">Oluşturulan Web sayfasında `HelloWorld` işlemi seçin.</span><span class="sxs-lookup"><span data-stu-id="0c72a-119">On the Web page generated, select the `HelloWorld` operation.</span></span>

8. <span data-ttu-id="0c72a-120">Test sayfasındaki **çağır** düğmesine tıklayın `HelloWorld` .</span><span class="sxs-lookup"><span data-stu-id="0c72a-120">Click the **Invoke** button on the `HelloWorld` test page.</span></span> <span data-ttu-id="0c72a-121">Aşağıdaki XML yanıtını almalısınız.</span><span class="sxs-lookup"><span data-stu-id="0c72a-121">You should receive the following XML response.</span></span>

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <string xmlns="http://tempuri.org/">Hello World</string>
    ```

9. <span data-ttu-id="0c72a-122">Bu yanıt artık çalışan bir ASP.NET AJAX hizmetine sahip olduğunuza ve özellikle de hizmetin, HTTP POST isteklerine yanıt veren ve XML döndüren Service1. asmx/HelloWorld yolunda bir uç nokta açığa çıkardığına onaylar.</span><span class="sxs-lookup"><span data-stu-id="0c72a-122">This response confirms that you now have a functioning ASP.NET AJAX service and, in particular, that the service has now exposed an endpoint at Service1.asmx/HelloWorld that responds to HTTP POST requests and returns XML.</span></span>

     <span data-ttu-id="0c72a-123">Artık bu hizmeti bir WCF AJAX hizmeti kullanmak üzere dönüştürmeye hazırsınız.</span><span class="sxs-lookup"><span data-stu-id="0c72a-123">Now you are ready to convert this service to use a WCF AJAX service.</span></span>

### <a name="to-create-an-equivalent-wcf-ajax-service-application"></a><span data-ttu-id="0c72a-124">Eşdeğer bir WCF AJAX hizmet uygulaması oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="0c72a-124">To create an equivalent WCF AJAX service application</span></span>

1. <span data-ttu-id="0c72a-125">**ASPHello** projesine sağ tıklayın ve **Ekle**, **Yeni öğe**ve ardından **AJAX etkin WCF hizmeti**' ni seçin.</span><span class="sxs-lookup"><span data-stu-id="0c72a-125">Right-click the **ASPHello** project and select **Add**, then **New Item**, and then **AJAX-enabled WCF Service**.</span></span>

2. <span data-ttu-id="0c72a-126">Hizmeti adlandırın `WCFHello` ve **Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="0c72a-126">Name the service `WCFHello` and click **Add**.</span></span>

3. <span data-ttu-id="0c72a-127">WCFHello.svc.cs dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="0c72a-127">Open the WCFHello.svc.cs file.</span></span>

4. <span data-ttu-id="0c72a-128">Service1.asmx.cs 'den, işlemin aşağıdaki uygulamasını kopyalayın `HelloWorld` .</span><span class="sxs-lookup"><span data-stu-id="0c72a-128">From Service1.asmx.cs, copy the following implementation of the `HelloWorld` operation.</span></span>

    ```csharp
    public string HelloWorld()
    {
        return "Hello World";
    }
    ```

5. <span data-ttu-id="0c72a-129">İşlemin kopyalanmış uygulamasına `HelloWorld` aşağıdaki kodun yerine WCFHello.svc.cs dosyasına yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="0c72a-129">Paste to copied implementation of the `HelloWorld` operation into the WCFHello.svc.cs file in place of the following code.</span></span>

    ```csharp
    public void DoWork()
    {
          // Add your operation implementation here
          return;
    }
    ```

6. <span data-ttu-id="0c72a-130">`Namespace`İçin özniteliğini belirtin <xref:System.ServiceModel.ServiceContractAttribute> `WCFHello` .</span><span class="sxs-lookup"><span data-stu-id="0c72a-130">Specify the `Namespace` attribute for <xref:System.ServiceModel.ServiceContractAttribute> as `WCFHello`.</span></span>

    ```csharp
    [ServiceContract(Namespace="WCFHello")]
    [AspNetCompatibilityRequirements(RequirementsMode=AspNetCompatibilityRequirementsMode.Required)]
    public class WCFHello
    { … }
    ```

7. <span data-ttu-id="0c72a-131">Öğesini <xref:System.ServiceModel.Web.WebInvokeAttribute> `HelloWorld` işleme ekleyin ve <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A> özelliği döndürecek şekilde ayarlayın <xref:System.ServiceModel.Web.WebMessageFormat.Xml> .</span><span class="sxs-lookup"><span data-stu-id="0c72a-131">Add the <xref:System.ServiceModel.Web.WebInvokeAttribute> to the `HelloWorld` operation and set the <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A> property to return <xref:System.ServiceModel.Web.WebMessageFormat.Xml>.</span></span> <span data-ttu-id="0c72a-132">Ayarlanmamışsa, varsayılan dönüş türünün olduğunu unutmayın <xref:System.ServiceModel.Web.WebMessageFormat.Json> .</span><span class="sxs-lookup"><span data-stu-id="0c72a-132">Note that, if not set, the default return type is <xref:System.ServiceModel.Web.WebMessageFormat.Json>.</span></span>

    ```csharp
    [OperationContract]
    [WebInvoke(ResponseFormat=WebMessageFormat.Xml)]
    public string HelloWorld()
    {
        return "Hello World";
    }
    ```

8. <span data-ttu-id="0c72a-133">**Build** menüsünde **Build Solution**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="0c72a-133">From the **Build** menu, select **Build Solution**.</span></span>

9. <span data-ttu-id="0c72a-134">WCFHello. svc dosyasını açın ve **Hata Ayıkla** menüsünden **hata ayıklama olmadan Başlat**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="0c72a-134">Open the WCFHello.svc file and from the **Debug** menu, select **Start Without Debugging**.</span></span>

10. <span data-ttu-id="0c72a-135">Hizmet artık `WCFHello.svc/HelloWorld` http post isteklerine yanıt veren ' de bir uç nokta kullanıma sunuyor.</span><span class="sxs-lookup"><span data-stu-id="0c72a-135">The service now exposes an endpoint at `WCFHello.svc/HelloWorld`, which responds to HTTP POST requests.</span></span> <span data-ttu-id="0c72a-136">HTTP POST istekleri tarayıcıdan test edilemez, ancak uç nokta XML 'den sonraki XML 'yi döndürüyor.</span><span class="sxs-lookup"><span data-stu-id="0c72a-136">HTTP POST requests cannot be tested from the browser, but the endpoint returns XML following XML.</span></span>

    ```xml
    <string xmlns="http://schemas.microsoft.com/2003/10/Serialization/">Hello World</string>
    ```

11. <span data-ttu-id="0c72a-137">`WCFHello.svc/HelloWorld`Ve `Service1.aspx/HelloWorld` uç noktalar artık işlevsel olarak eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="0c72a-137">The `WCFHello.svc/HelloWorld` and the `Service1.aspx/HelloWorld` endpoints are now functionally equivalent.</span></span>

## <a name="example"></a><span data-ttu-id="0c72a-138">Örnek</span><span class="sxs-lookup"><span data-stu-id="0c72a-138">Example</span></span>
 <span data-ttu-id="0c72a-139">Bu konuda özetlenen yordamlardan kaynaklanan kod aşağıdaki örnekte verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="0c72a-139">The code that results from the procedures outlined in this topic is provided in the following example.</span></span>

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

 <span data-ttu-id="0c72a-140"><xref:System.Xml.XmlDocument>Türü <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> , tarafından seri hale getirilmediğinden tarafından desteklenmez <xref:System.Xml.Serialization.XmlSerializer> .</span><span class="sxs-lookup"><span data-stu-id="0c72a-140">The <xref:System.Xml.XmlDocument> type is not supported by the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> because it is not serializable by the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="0c72a-141">Bir <xref:System.Xml.Linq.XDocument> tür kullanabilir veya bunun yerine seri hale getirebilirsiniz <xref:System.Xml.XmlDocument.DocumentElement%2A> .</span><span class="sxs-lookup"><span data-stu-id="0c72a-141">You can use either an <xref:System.Xml.Linq.XDocument> type, or serialize the <xref:System.Xml.XmlDocument.DocumentElement%2A> instead.</span></span>

 <span data-ttu-id="0c72a-142">ASMX Web Hizmetleri yükseltilmekte ve yan yana WCF hizmetlerine geçiriliyorsa, iki türü istemcide aynı ada eşlemektan kaçının.</span><span class="sxs-lookup"><span data-stu-id="0c72a-142">If ASMX Web services are being upgraded and migrated side-by-side to WCF services, avoid mapping two types to the same name on the client.</span></span> <span data-ttu-id="0c72a-143">Bu, bir ve ' de aynı tür kullanılıyorsa serileştiricde bir özel duruma neden olur <xref:System.Web.Services.WebMethodAttribute> <xref:System.ServiceModel.ServiceContractAttribute> :</span><span class="sxs-lookup"><span data-stu-id="0c72a-143">This causes an exception in serializers if the same type is used in a <xref:System.Web.Services.WebMethodAttribute> and a <xref:System.ServiceModel.ServiceContractAttribute>:</span></span>

- <span data-ttu-id="0c72a-144">İlk olarak WCF hizmeti eklenirse, Web hizmetindeki <xref:System.Web.UI.ObjectConverter.ConvertValue%28System.Object%2CSystem.Type%2CSystem.String%29> SıRANıN WCF stil tanımı öncelikli olduğundan asmx Web hizmeti üzerindeki yöntemi çağırmak özel duruma neden olur.</span><span class="sxs-lookup"><span data-stu-id="0c72a-144">If WCF service is added first, invoking the method on ASMX Web Service causes exception in <xref:System.Web.UI.ObjectConverter.ConvertValue%28System.Object%2CSystem.Type%2CSystem.String%29> because the WCF style definition of the order in the proxy takes precedence.</span></span>

- <span data-ttu-id="0c72a-145">Önce ASMX Web hizmeti eklenirse, WCF hizmetinde çağırma yöntemi ' de özel durum oluşmasına neden olur <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> çünkü proxy 'deki sıranın Web hizmeti stil tanımı öncelik kazanır.</span><span class="sxs-lookup"><span data-stu-id="0c72a-145">If ASMX Web Service is added first, invoking method on WCF service causes exception in <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> because the Web Service style definition of the order in the proxy takes precedence.</span></span>

 <span data-ttu-id="0c72a-146">Ve ASP.NET AJAX arasındaki davranışta önemli farklılıklar vardır <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> <xref:System.Web.Script.Serialization.JavaScriptSerializer> .</span><span class="sxs-lookup"><span data-stu-id="0c72a-146">There are significant differences in behavior between the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> and the ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer>.</span></span> <span data-ttu-id="0c72a-147">Örneğin, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> bir sözlüğü anahtar/değer çiftleri dizisi olarak temsil ederken, ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer> bir sözlüğü gerçek JSON nesneleri olarak temsil eder.</span><span class="sxs-lookup"><span data-stu-id="0c72a-147">For example, the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> represents a dictionary as an array of key/value pairs, whereas the ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer> represents a dictionary as actual JSON objects.</span></span> <span data-ttu-id="0c72a-148">Bu nedenle, ASP.NET AJAX içinde temsil edilen sözlük aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="0c72a-148">So the following is the dictionary represented in ASP.NET AJAX.</span></span>

```csharp
Dictionary<string, int> d = new Dictionary<string, int>();
d.Add("one", 1);
d.Add("two", 2);
```

 <span data-ttu-id="0c72a-149">Bu sözlük, aşağıdaki listede gösterildiği gibi JSON nesnelerinde temsil edilir:</span><span class="sxs-lookup"><span data-stu-id="0c72a-149">This dictionary is represented in JSON objects as shown in the following list:</span></span>

- <span data-ttu-id="0c72a-150">[{"Key": "One", "Value": 1}, {"Key": "iki", "Value": 2}],<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer></span><span class="sxs-lookup"><span data-stu-id="0c72a-150">[{"Key":"one","Value":1},{"Key":"two","Value":2}] by the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer></span></span>

- <span data-ttu-id="0c72a-151">{"One": 1, "iki": 2} ASP.NET AJAX tarafından<xref:System.Web.Script.Serialization.JavaScriptSerializer></span><span class="sxs-lookup"><span data-stu-id="0c72a-151">{"one":1,"two":2} by the ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer></span></span>

 <span data-ttu-id="0c72a-152">, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> Anahtar türünün dize olmadığı, ancak işleyememesi durumunda sözlüklerin işleyebileceği anlamda daha güçlüdür <xref:System.Web.Script.Serialization.JavaScriptSerializer> .</span><span class="sxs-lookup"><span data-stu-id="0c72a-152">The <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> is more powerful in the sense that it can handle dictionaries where the key type is not string, while the <xref:System.Web.Script.Serialization.JavaScriptSerializer> cannot.</span></span> <span data-ttu-id="0c72a-153">Ancak ikincisi JSON kullanımı daha fazla.</span><span class="sxs-lookup"><span data-stu-id="0c72a-153">But the latter is more JSON-friendly.</span></span>

 <span data-ttu-id="0c72a-154">Bu serileştiriciler arasındaki önemli farklılıklar aşağıdaki tabloda özetlenmiştir.</span><span class="sxs-lookup"><span data-stu-id="0c72a-154">The significant differences between these serializers are summarized in the following table.</span></span>

|<span data-ttu-id="0c72a-155">Farklar kategorisi</span><span class="sxs-lookup"><span data-stu-id="0c72a-155">Category of Differences</span></span>|<span data-ttu-id="0c72a-156">DataContractJsonSerializer</span><span class="sxs-lookup"><span data-stu-id="0c72a-156">DataContractJsonSerializer</span></span>|<span data-ttu-id="0c72a-157">ASP.NET AJAX JavaScriptSerializer</span><span class="sxs-lookup"><span data-stu-id="0c72a-157">ASP.NET AJAX JavaScriptSerializer</span></span>|
|-----------------------------|--------------------------------|---------------------------------------|
|<span data-ttu-id="0c72a-158">Boş arabellek (yeni bayt [0]) içinde <xref:System.Object> (veya <xref:System.Uri> başka bir sınıfa) seri durumdan çıkarılamadı.</span><span class="sxs-lookup"><span data-stu-id="0c72a-158">Deserializing the empty buffer (new byte[0]) into <xref:System.Object> (or <xref:System.Uri>, or some other classes).</span></span>|<span data-ttu-id="0c72a-159">SerializationException</span><span class="sxs-lookup"><span data-stu-id="0c72a-159">SerializationException</span></span>|<span data-ttu-id="0c72a-160">null</span><span class="sxs-lookup"><span data-stu-id="0c72a-160">null</span></span>|
|<span data-ttu-id="0c72a-161">Serileştirme<xref:System.DBNull.Value></span><span class="sxs-lookup"><span data-stu-id="0c72a-161">Serialization of <xref:System.DBNull.Value></span></span>|<span data-ttu-id="0c72a-162">{}(veya {"__type": "#System"})</span><span class="sxs-lookup"><span data-stu-id="0c72a-162">{} (or {"__type":"#System"})</span></span>|<span data-ttu-id="0c72a-163">Null</span><span class="sxs-lookup"><span data-stu-id="0c72a-163">Null</span></span>|
|<span data-ttu-id="0c72a-164">[Serializable] türlerinin özel üyelerinin serileştirilmesi.</span><span class="sxs-lookup"><span data-stu-id="0c72a-164">Serialization of the private members of [Serializable] types.</span></span>|<span data-ttu-id="0c72a-165">metodu</span><span class="sxs-lookup"><span data-stu-id="0c72a-165">serialized</span></span>|<span data-ttu-id="0c72a-166">serileştirilmedi</span><span class="sxs-lookup"><span data-stu-id="0c72a-166">not serialized</span></span>|
|<span data-ttu-id="0c72a-167">Türlerin ortak özelliklerinin serileştirilmesi <xref:System.Runtime.Serialization.ISerializable> .</span><span class="sxs-lookup"><span data-stu-id="0c72a-167">Serialization of the public properties of <xref:System.Runtime.Serialization.ISerializable> types.</span></span>|<span data-ttu-id="0c72a-168">serileştirilmedi</span><span class="sxs-lookup"><span data-stu-id="0c72a-168">not serialized</span></span>|<span data-ttu-id="0c72a-169">metodu</span><span class="sxs-lookup"><span data-stu-id="0c72a-169">serialized</span></span>|
|<span data-ttu-id="0c72a-170">JSON "Extensions"</span><span class="sxs-lookup"><span data-stu-id="0c72a-170">"Extensions" of JSON</span></span>|<span data-ttu-id="0c72a-171">Nesne üye adlarında tırnak işareti gerektiren JSON belirtimine uyar ({"a": "Hello"}).</span><span class="sxs-lookup"><span data-stu-id="0c72a-171">Adheres to the JSON specification, which requires quotes on object member names ({"a":"hello"}).</span></span>|<span data-ttu-id="0c72a-172">Tırnak işaretleri olmadan nesne üyelerinin adlarını destekler ({a: "Hello"}).</span><span class="sxs-lookup"><span data-stu-id="0c72a-172">Supports the names of object members without quotes ({a:"hello"}).</span></span>|
|<span data-ttu-id="0c72a-173"><xref:System.DateTime>Eşgüdümlü Evrensel Saat (UTC)</span><span class="sxs-lookup"><span data-stu-id="0c72a-173"><xref:System.DateTime> Coordinated Universal Time (UTC)</span></span>|<span data-ttu-id="0c72a-174">" \\ /Date (123456789U) \\ /" veya " \\ /date \\ (\d + (U&#124; ( \\ + \\ -[\d {4} ])) biçimini desteklemez mi? \\ ) \\ \\ /)".</span><span class="sxs-lookup"><span data-stu-id="0c72a-174">Does not support format "\\/Date(123456789U)\\/" or "\\/Date\\(\d+(U&#124;(\\+\\-[\d{4}]))?\\)\\\\/)".</span></span>|<span data-ttu-id="0c72a-175">" \\ /Date (123456789U) \\ /" ve " \\ /date \\ (\d + (U&#124; ( \\ + \\ -[\d {4} ])) biçimini destekler mi? \\ ) \\ \\ /) "değerini DateTime değerleri olarak.</span><span class="sxs-lookup"><span data-stu-id="0c72a-175">Supports format "\\/Date(123456789U)\\/" and "\\/Date\\(\d+(U&#124;(\\+\\-[\d{4}]))?\\)\\\\/)" as DateTime values.</span></span>|
|<span data-ttu-id="0c72a-176">Sözlüklerin temsili</span><span class="sxs-lookup"><span data-stu-id="0c72a-176">Representation of dictionaries</span></span>|<span data-ttu-id="0c72a-177">Bir KeyValuePair dizisi \<K,V> , dizeler olmayan anahtar türlerini işler.</span><span class="sxs-lookup"><span data-stu-id="0c72a-177">An array of KeyValuePair\<K,V>, handles key types that are not strings.</span></span>|<span data-ttu-id="0c72a-178">Gerçek JSON nesneleri olarak-ancak yalnızca dizeler olan anahtar türlerini işler.</span><span class="sxs-lookup"><span data-stu-id="0c72a-178">As actual JSON objects - but only handles key types that are strings.</span></span>|
|<span data-ttu-id="0c72a-179">Kaçan karakterler</span><span class="sxs-lookup"><span data-stu-id="0c72a-179">Escaped characters</span></span>|<span data-ttu-id="0c72a-180">Her zaman kaçış eğik çizgiyle (/); "\n" gibi, kaçırılmamış geçersiz JSON karakterlerinin hiçbir şekilde yapılmasına izin vermez.</span><span class="sxs-lookup"><span data-stu-id="0c72a-180">Always with an escape forward slash (/); never allows un-escaped invalid JSON characters, such as "\n".</span></span>|<span data-ttu-id="0c72a-181">Tarih/saat değerleri için çıkış ileri eğik çizgi (/) ile.</span><span class="sxs-lookup"><span data-stu-id="0c72a-181">With an escape forward slash (/) for DateTime values.</span></span>|

## <a name="see-also"></a><span data-ttu-id="0c72a-182">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0c72a-182">See also</span></span>

- [<span data-ttu-id="0c72a-183">Nasıl yapılır: ASP.NET AJAX Uç Noktası Eklemek için Yapılandırma Kullanma</span><span class="sxs-lookup"><span data-stu-id="0c72a-183">How to: Use Configuration to Add an ASP.NET AJAX Endpoint</span></span>](how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md)
