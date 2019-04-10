---
title: "Nasıl yapılır: AJAX Etkinleştirilmiş ASP.NET Web Hizmetlerini WCF'ye Taşıma"
ms.date: 03/30/2017
ms.assetid: 1428df4d-b18f-4e6d-bd4d-79ab3dd5147c
ms.openlocfilehash: 6114fa90b10a5d0cacb60a7ad40f63fae776e174
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59337428"
---
# <a name="how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf"></a><span data-ttu-id="39d8c-102">Nasıl yapılır: AJAX Etkinleştirilmiş ASP.NET Web Hizmetlerini WCF'ye Taşıma</span><span class="sxs-lookup"><span data-stu-id="39d8c-102">How to: Migrate AJAX-Enabled ASP.NET Web Services to WCF</span></span>
<span data-ttu-id="39d8c-103">Bu konu, temel bir ASP.NET AJAX hizmeti eşdeğer bir AJAX etkinleştirilmiş Windows Communication Foundation (WCF) hizmetine geçirme yordamları özetler.</span><span class="sxs-lookup"><span data-stu-id="39d8c-103">This topic outlines procedures to migrate a basic ASP.NET AJAX service to an equivalent AJAX-enabled Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="39d8c-104">Bu, bir ASP.NET AJAX Hizmeti işlevsel olarak eşdeğer bir WCF sürümü oluşturma işlemini gösterir.</span><span class="sxs-lookup"><span data-stu-id="39d8c-104">It shows how to create a functionally equivalent WCF version of an ASP.NET AJAX service.</span></span> <span data-ttu-id="39d8c-105">İki hizmeti daha sonra bir yan yana kullanılabilir veya WCF hizmetini ASP.NET AJAX hizmeti değiştirmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="39d8c-105">The two services can then be used side by side, or the WCF service can be used to replace the ASP.NET AJAX service.</span></span>

 <span data-ttu-id="39d8c-106">Mevcut bir ASP.NET AJAX geçiş hizmetine bir WCF AJAX hizmeti aşağıdaki faydaları sağlar:</span><span class="sxs-lookup"><span data-stu-id="39d8c-106">Migrating an existing ASP.NET AJAX service to a WCF AJAX service gives you the following benefits:</span></span>

-   <span data-ttu-id="39d8c-107">AJAX hizmetinizi en az bir ek yapılandırma ile bir SOAP hizmet olarak kullanıma sunabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="39d8c-107">You can expose your AJAX service as a SOAP service with minimal extra configuration.</span></span>

-   <span data-ttu-id="39d8c-108">WCF izleme gibi özelliklerinden yararlanmak ve benzeri.</span><span class="sxs-lookup"><span data-stu-id="39d8c-108">You can benefit from WCF features such as tracing, and so on.</span></span>

 <span data-ttu-id="39d8c-109">Aşağıdaki yordamlar, Visual Studio 2012 kullandığınızı varsayar.</span><span class="sxs-lookup"><span data-stu-id="39d8c-109">The following procedures assume that you are using Visual Studio 2012.</span></span>

 <span data-ttu-id="39d8c-110">Bu konu başlığında açıklanan yordamları oluşur kodu prosedürleri izliyorsanız örnekte sağlanır.</span><span class="sxs-lookup"><span data-stu-id="39d8c-110">The code that results from the procedures outlined in this topic is provided in the example following the procedures.</span></span>

 <span data-ttu-id="39d8c-111">WCF hizmet AJAX etkinleştirilmiş bir uç nokta aracılığıyla kullanıma sunma hakkında daha fazla bilgi için bkz. [nasıl yapılır: ASP.NET AJAX uç noktası eklemek için yapılandırma kullanma](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md) konu.</span><span class="sxs-lookup"><span data-stu-id="39d8c-111">For more information about exposing a WCF service through an AJAX-enabled endpoint, see the [How to: Use Configuration to Add an ASP.NET AJAX Endpoint](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md) topic.</span></span>

### <a name="to-create-and-test-the-aspnet-web-service-application"></a><span data-ttu-id="39d8c-112">Oluşturma ve ASP.NET Web hizmeti uygulamasını test etmek için</span><span class="sxs-lookup"><span data-stu-id="39d8c-112">To create and test the ASP.NET Web service application</span></span>

1. <span data-ttu-id="39d8c-113">Visual Studio 2012'yi açın.</span><span class="sxs-lookup"><span data-stu-id="39d8c-113">Open Visual Studio 2012.</span></span>

2. <span data-ttu-id="39d8c-114">Gelen **dosya** menüsünde **yeni**, ardından **proje**, ardından **Web**ve ardından **ASP.NET Web hizmeti uygulaması** .</span><span class="sxs-lookup"><span data-stu-id="39d8c-114">From the **File** menu, select **New**, then **Project**, then **Web**, and then select **ASP.NET Web Service Application**.</span></span>

3. <span data-ttu-id="39d8c-115">Projeyi adlandırın `ASPHello` tıklatıp **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="39d8c-115">Name the project `ASPHello` and click **OK**.</span></span>

4. <span data-ttu-id="39d8c-116">Service1.asmx.cs dosyasındaki içeren satırı açıklamadan çıkarın `System.Web.Script.Services.ScriptService]` bu hizmet için AJAX etkinleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="39d8c-116">Uncomment the line in the Service1.asmx.cs file that contains `System.Web.Script.Services.ScriptService]` to enable AJAX for this service.</span></span>

5. <span data-ttu-id="39d8c-117">Gelen **derleme** menüsünde **Çözümü Derle**.</span><span class="sxs-lookup"><span data-stu-id="39d8c-117">From the **Build** menu, select **Build Solution**.</span></span>

6. <span data-ttu-id="39d8c-118">Gelen **hata ayıklama** menüsünde **hata ayıklama olmadan Başlat**.</span><span class="sxs-lookup"><span data-stu-id="39d8c-118">From the **Debug** menu, select **Start Without Debugging**.</span></span>

7. <span data-ttu-id="39d8c-119">Oluşturulan Web sayfası üzerinde seçmek `HelloWorld` işlemi.</span><span class="sxs-lookup"><span data-stu-id="39d8c-119">On the Web page generated, select the `HelloWorld` operation.</span></span>

8. <span data-ttu-id="39d8c-120">Tıklayın **Invoke** düğmesini `HelloWorld` test sayfası.</span><span class="sxs-lookup"><span data-stu-id="39d8c-120">Click the **Invoke** button on the `HelloWorld` test page.</span></span> <span data-ttu-id="39d8c-121">Aşağıdaki XML yanıtı almanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="39d8c-121">You should receive the following XML response.</span></span>

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <string xmlns="http://tempuri.org/">Hello World</string>
    ```

9. <span data-ttu-id="39d8c-122">Bu yanıt artık çalışan bir ASP.NET AJAX hizmeti olan ve özellikle hizmet, bir uç noktada yanıt için HTTP POST Service1.asmx/HelloWorld artık kullanıma ve istekleri XML döndürür, onaylar.</span><span class="sxs-lookup"><span data-stu-id="39d8c-122">This response confirms that you now have a functioning ASP.NET AJAX service and, in particular, that the service has now exposed an endpoint at Service1.asmx/HelloWorld that responds to HTTP POST requests and returns XML.</span></span>

     <span data-ttu-id="39d8c-123">Bir WCF AJAX hizmeti kullanmak için bu hizmetin dönüştürmek hazırsınız.</span><span class="sxs-lookup"><span data-stu-id="39d8c-123">Now you are ready to convert this service to use a WCF AJAX service.</span></span>

### <a name="to-create-an-equivalent-wcf-ajax-service-application"></a><span data-ttu-id="39d8c-124">Eşdeğer bir AJAX WCF hizmet uygulaması oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="39d8c-124">To create an equivalent WCF AJAX service application</span></span>

1. <span data-ttu-id="39d8c-125">Sağ **ASPHello** seçin ve proje **Ekle**, ardından **yeni öğe**, ardından **AJAX özellikli bir WCF Hizmeti**.</span><span class="sxs-lookup"><span data-stu-id="39d8c-125">Right-click the **ASPHello** project and select **Add**, then **New Item**, and then **AJAX-enabled WCF Service**.</span></span>

2. <span data-ttu-id="39d8c-126">Hizmet adı `WCFHello` tıklatıp **Ekle**.</span><span class="sxs-lookup"><span data-stu-id="39d8c-126">Name the service `WCFHello` and click **Add**.</span></span>

3. <span data-ttu-id="39d8c-127">WCFHello.svc.cs dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="39d8c-127">Open the WCFHello.svc.cs file.</span></span>

4. <span data-ttu-id="39d8c-128">Aşağıdaki uygulamasını service1.asmx.cs kopyalayın `HelloWorld` işlemi.</span><span class="sxs-lookup"><span data-stu-id="39d8c-128">From Service1.asmx.cs, copy the following implementation of the `HelloWorld` operation.</span></span>

    ```
    public string HelloWorld()
    {
         return "Hello World";
    }
    ```

5. <span data-ttu-id="39d8c-129">Kopyalanan uygulaması Yapıştır `HelloWorld` WCFHello.svc.cs dosyasına aşağıdaki kodu yerine işlemi.</span><span class="sxs-lookup"><span data-stu-id="39d8c-129">Paste to copied implementation of the `HelloWorld` operation into the WCFHello.svc.cs file in place of the following code.</span></span>

    ```
    public void DoWork()
    {
          // Add your operation implementation here
          return;
    }
    ```

6. <span data-ttu-id="39d8c-130">Belirtin `Namespace` özniteliğini <xref:System.ServiceModel.ServiceContractAttribute> olarak `WCFHello`.</span><span class="sxs-lookup"><span data-stu-id="39d8c-130">Specify the `Namespace` attribute for <xref:System.ServiceModel.ServiceContractAttribute> as `WCFHello`.</span></span>

    ```
    [ServiceContract(Namespace="WCFHello")]
    [AspNetCompatibilityRequirements(RequirementsMode=AspNetCompatibilityRequirementsMode.Required)]
    public class WCFHello
    { … }
    ```

7. <span data-ttu-id="39d8c-131">Ekleme <xref:System.ServiceModel.Web.WebInvokeAttribute> için `HelloWorld` işlemi ve kümesi <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A> dönmesini <xref:System.ServiceModel.Web.WebMessageFormat.Xml>.</span><span class="sxs-lookup"><span data-stu-id="39d8c-131">Add the <xref:System.ServiceModel.Web.WebInvokeAttribute> to the `HelloWorld` operation and set the <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A> property to return <xref:System.ServiceModel.Web.WebMessageFormat.Xml>.</span></span> <span data-ttu-id="39d8c-132">Ayarlanırsa, dönüş türü varsayılan değilse unutmayın <xref:System.ServiceModel.Web.WebMessageFormat.Json>.</span><span class="sxs-lookup"><span data-stu-id="39d8c-132">Note that, if not set, the default return type is <xref:System.ServiceModel.Web.WebMessageFormat.Json>.</span></span>

    ```
    [OperationContract]
    [WebInvoke(ResponseFormat=WebMessageFormat.Xml)]
    public string HelloWorld()
    {
        return "Hello World";
    }
    ```

8. <span data-ttu-id="39d8c-133">Gelen **derleme** menüsünde **Çözümü Derle**.</span><span class="sxs-lookup"><span data-stu-id="39d8c-133">From the **Build** menu, select **Build Solution**.</span></span>

9. <span data-ttu-id="39d8c-134">WCFHello.svc dosyasını açın ve **hata ayıklama** menüsünde **hata ayıklama olmadan Başlat**.</span><span class="sxs-lookup"><span data-stu-id="39d8c-134">Open the WCFHello.svc file and from the **Debug** menu, select **Start Without Debugging**.</span></span>

10. <span data-ttu-id="39d8c-135">Hizmet artık bir uç noktada kullanıma sunan `WCFHello.svc/HelloWorld`, HTTP POST istekleri için yanıt verir.</span><span class="sxs-lookup"><span data-stu-id="39d8c-135">The service now exposes an endpoint at `WCFHello.svc/HelloWorld`, which responds to HTTP POST requests.</span></span> <span data-ttu-id="39d8c-136">Tarayıcısından HTTP POST istekleri sınanamıyor ancak uç noktası aşağıdaki XML XML döndürür.</span><span class="sxs-lookup"><span data-stu-id="39d8c-136">HTTP POST requests cannot be tested from the browser, but the endpoint returns XML following XML.</span></span>

    ```xml
    <string xmlns="http://schemas.microsoft.com/2003/10/Serialization/">Hello World</string>
    ```

11. <span data-ttu-id="39d8c-137">`WCFHello.svc/HelloWorld` Ve `Service1.aspx/HelloWorld` noktalarıdır artık eşdeğer işleve sahiptir.</span><span class="sxs-lookup"><span data-stu-id="39d8c-137">The `WCFHello.svc/HelloWorld` and the `Service1.aspx/HelloWorld` endpoints are now functionally equivalent.</span></span>

## <a name="example"></a><span data-ttu-id="39d8c-138">Örnek</span><span class="sxs-lookup"><span data-stu-id="39d8c-138">Example</span></span>
 <span data-ttu-id="39d8c-139">Bu konu başlığında açıklanan yordamları oluşur kodu, aşağıdaki örnekte sağlanır.</span><span class="sxs-lookup"><span data-stu-id="39d8c-139">The code that results from the procedures outlined in this topic is provided in the following example.</span></span>

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

 <span data-ttu-id="39d8c-140"><xref:System.Xml.XmlDocument> Türü tarafından desteklenmiyor <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> tarafından seri hale getirilebilir olmadığından <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="39d8c-140">The <xref:System.Xml.XmlDocument> type is not supported by the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> because it is not serializable by the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="39d8c-141">Kullanabilirsiniz bir <xref:System.Xml.Linq.XDocument> yazın veya serileştirmek <xref:System.Xml.XmlDocument.DocumentElement%2A> yerine.</span><span class="sxs-lookup"><span data-stu-id="39d8c-141">You can use either an <xref:System.Xml.Linq.XDocument> type, or serialize the <xref:System.Xml.XmlDocument.DocumentElement%2A> instead.</span></span>

 <span data-ttu-id="39d8c-142">ASMX Web Hizmetleri yükseltilmekte olan ve WCF hizmetleri için yan yana geçişi, iki tür istemci üzerinde aynı ad eşleme kaçının.</span><span class="sxs-lookup"><span data-stu-id="39d8c-142">If ASMX Web services are being upgraded and migrated side-by-side to WCF services, avoid mapping two types to the same name on the client.</span></span> <span data-ttu-id="39d8c-143">Aynı tür kullanılırsa bu bir özel durum seri hale getiricileri genişletme içinde neden bir <xref:System.Web.Services.WebMethodAttribute> ve <xref:System.ServiceModel.ServiceContractAttribute>:</span><span class="sxs-lookup"><span data-stu-id="39d8c-143">This causes an exception in serializers if the same type is used in a <xref:System.Web.Services.WebMethodAttribute> and a <xref:System.ServiceModel.ServiceContractAttribute>:</span></span>

-   <span data-ttu-id="39d8c-144">WCF Hizmeti önce eklediyseniz, özel durum ASMX Web hizmeti yönteminin çağrılması neden <xref:System.Web.UI.ObjectConverter.ConvertValue%28System.Object%2CSystem.Type%2CSystem.String%29> proxy sırayla WCF stil tanımını öncelikli olduğundan.</span><span class="sxs-lookup"><span data-stu-id="39d8c-144">If WCF service is added first, invoking the method on ASMX Web Service causes exception in <xref:System.Web.UI.ObjectConverter.ConvertValue%28System.Object%2CSystem.Type%2CSystem.String%29> because the WCF style definition of the order in the proxy takes precedence.</span></span>

-   <span data-ttu-id="39d8c-145">ASMX Web hizmeti önce eklediyseniz, WCF Hizmeti metodu çağrılırken özel durum neden <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> proxy sırayla Web hizmeti stil tanımını öncelikli olduğundan.</span><span class="sxs-lookup"><span data-stu-id="39d8c-145">If ASMX Web Service is added first, invoking method on WCF service causes exception in <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> because the Web Service style definition of the order in the proxy takes precedence.</span></span>

 <span data-ttu-id="39d8c-146">Davranış önemli farklılıkları vardır <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> ve ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer>.</span><span class="sxs-lookup"><span data-stu-id="39d8c-146">There are significant differences in behavior between the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> and the ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer>.</span></span> <span data-ttu-id="39d8c-147">Örneğin, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> bir sözlük ise anahtar/değer çiftleri dizisi olarak temsil eden ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer> bir sözlük gerçek bir JSON nesnesi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="39d8c-147">For example, the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> represents a dictionary as an array of key/value pairs, whereas the ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer> represents a dictionary as actual JSON objects.</span></span> <span data-ttu-id="39d8c-148">ASP.NET AJAX içinde gösterilen sözlüğe aşağıdaki nedenle.</span><span class="sxs-lookup"><span data-stu-id="39d8c-148">So the following is the dictionary represented in ASP.NET AJAX.</span></span>

```
Dictionary<string, int> d = new Dictionary<string, int>();
d.Add("one", 1);
d.Add("two", 2);
```

 <span data-ttu-id="39d8c-149">Bu sözlük, aşağıdaki listede gösterildiği gibi JSON nesnesi temsil edilir:</span><span class="sxs-lookup"><span data-stu-id="39d8c-149">This dictionary is represented in JSON objects as shown in the following list:</span></span>

-   <span data-ttu-id="39d8c-150">[{"Key": "Bir", "Value": 1}, {"Key": "İki", "Value": 2}] olarak</span><span class="sxs-lookup"><span data-stu-id="39d8c-150">[{"Key":"one","Value":1},{"Key":"two","Value":2}] by the</span></span> <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>

-   <span data-ttu-id="39d8c-151">{"bir": 1 "iki": 2} ASP.NET AJAX ile</span><span class="sxs-lookup"><span data-stu-id="39d8c-151">{"one":1,"two":2} by the ASP.NET AJAX</span></span> <xref:System.Web.Script.Serialization.JavaScriptSerializer>

 <span data-ttu-id="39d8c-152"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> , Anahtar türü dizesi olduğu sözlükleri işleyebilir anlamda daha güçlüdür ancak <xref:System.Web.Script.Serialization.JavaScriptSerializer> olamaz.</span><span class="sxs-lookup"><span data-stu-id="39d8c-152">The <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> is more powerful in the sense that it can handle dictionaries where the key type is not string, while the <xref:System.Web.Script.Serialization.JavaScriptSerializer> cannot.</span></span> <span data-ttu-id="39d8c-153">Ancak, daha kolay JSON ikincisidir.</span><span class="sxs-lookup"><span data-stu-id="39d8c-153">But the latter is more JSON-friendly.</span></span>

 <span data-ttu-id="39d8c-154">Bu seri hale getiricileri genişletme arasında önemli farklılıklar aşağıdaki tabloda özetlenmiştir.</span><span class="sxs-lookup"><span data-stu-id="39d8c-154">The significant differences between these serializers are summarized in the following table.</span></span>

|<span data-ttu-id="39d8c-155">Farklar kategorisi</span><span class="sxs-lookup"><span data-stu-id="39d8c-155">Category of Differences</span></span>|<span data-ttu-id="39d8c-156">DataContractJsonSerializer</span><span class="sxs-lookup"><span data-stu-id="39d8c-156">DataContractJsonSerializer</span></span>|<span data-ttu-id="39d8c-157">ASP.NET AJAX JavaScriptSerializer</span><span class="sxs-lookup"><span data-stu-id="39d8c-157">ASP.NET AJAX JavaScriptSerializer</span></span>|
|-----------------------------|--------------------------------|---------------------------------------|
|<span data-ttu-id="39d8c-158">Boş arabellek seri durumdan çıkarılırken (içine yeni byte[0]) <xref:System.Object> (veya <xref:System.Uri>, ya da diğer bazı sınıflar).</span><span class="sxs-lookup"><span data-stu-id="39d8c-158">Deserializing the empty buffer (new byte[0]) into <xref:System.Object> (or <xref:System.Uri>, or some other classes).</span></span>|<span data-ttu-id="39d8c-159">SerializationException</span><span class="sxs-lookup"><span data-stu-id="39d8c-159">SerializationException</span></span>|<span data-ttu-id="39d8c-160">null</span><span class="sxs-lookup"><span data-stu-id="39d8c-160">null</span></span>|
|<span data-ttu-id="39d8c-161">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="39d8c-161">Serialization of</span></span> <xref:System.DBNull.Value>|<span data-ttu-id="39d8c-162">{} (veya {"__type": "#System"})</span><span class="sxs-lookup"><span data-stu-id="39d8c-162">{} (or {"__type":"#System"})</span></span>|<span data-ttu-id="39d8c-163">Null</span><span class="sxs-lookup"><span data-stu-id="39d8c-163">Null</span></span>|
|<span data-ttu-id="39d8c-164">Özel üyelerin [Serializable] türlerin seri hale getirme.</span><span class="sxs-lookup"><span data-stu-id="39d8c-164">Serialization of the private members of [Serializable] types.</span></span>|<span data-ttu-id="39d8c-165">seri hale getirilmiş</span><span class="sxs-lookup"><span data-stu-id="39d8c-165">serialized</span></span>|<span data-ttu-id="39d8c-166">Serileştirilmiş değil</span><span class="sxs-lookup"><span data-stu-id="39d8c-166">not serialized</span></span>|
|<span data-ttu-id="39d8c-167">Genel özellikleri serileştirmek <xref:System.Runtime.Serialization.ISerializable> türleri.</span><span class="sxs-lookup"><span data-stu-id="39d8c-167">Serialization of the public properties of <xref:System.Runtime.Serialization.ISerializable> types.</span></span>|<span data-ttu-id="39d8c-168">Serileştirilmiş değil</span><span class="sxs-lookup"><span data-stu-id="39d8c-168">not serialized</span></span>|<span data-ttu-id="39d8c-169">seri hale getirilmiş</span><span class="sxs-lookup"><span data-stu-id="39d8c-169">serialized</span></span>|
|<span data-ttu-id="39d8c-170">JSON "uzantıları"</span><span class="sxs-lookup"><span data-stu-id="39d8c-170">"Extensions" of JSON</span></span>|<span data-ttu-id="39d8c-171">Üye adlarının nesne tekliflerinde gerektirir JSON belirtimi için uyar ({"a": "hello"}).</span><span class="sxs-lookup"><span data-stu-id="39d8c-171">Adheres to the JSON specification, which requires quotes on object member names ({"a":"hello"}).</span></span>|<span data-ttu-id="39d8c-172">Nesne üyeleri ({y: "hello"}) tırnak işaretleri olmadan adlarını destekler.</span><span class="sxs-lookup"><span data-stu-id="39d8c-172">Supports the names of object members without quotes ({a:"hello"}).</span></span>|
|<xref:System.DateTime> <span data-ttu-id="39d8c-173">Eşgüdümlü Evrensel Saat (UTC)</span><span class="sxs-lookup"><span data-stu-id="39d8c-173">Coordinated Universal Time (UTC)</span></span>|<span data-ttu-id="39d8c-174">Biçimini desteklemiyor "\\/Date(123456789U)\\/" veya "\\/tarih\\(\d+ (U&#124;(\\+\\-[\d{4}]))?\\) \\\\/)".</span><span class="sxs-lookup"><span data-stu-id="39d8c-174">Does not support format "\\/Date(123456789U)\\/" or "\\/Date\\(\d+(U&#124;(\\+\\-[\d{4}]))?\\)\\\\/)".</span></span>|<span data-ttu-id="39d8c-175">Destekler biçim "\\/Date(123456789U)\\/" ve "\\/tarih\\(\d+ (U&#124;(\\+\\-[\d{4}]))?\\) \\ \\/) "olarak DateTime değerleri.</span><span class="sxs-lookup"><span data-stu-id="39d8c-175">Supports format "\\/Date(123456789U)\\/" and "\\/Date\\(\d+(U&#124;(\\+\\-[\d{4}]))?\\)\\\\/)" as DateTime values.</span></span>|
|<span data-ttu-id="39d8c-176">Sözlükler temsili</span><span class="sxs-lookup"><span data-stu-id="39d8c-176">Representation of dictionaries</span></span>|<span data-ttu-id="39d8c-177">Bir dizi KeyValuePair\<K, V >, dize olmayan anahtar türünü işler.</span><span class="sxs-lookup"><span data-stu-id="39d8c-177">An array of KeyValuePair\<K,V>, handles key types that are not strings.</span></span>|<span data-ttu-id="39d8c-178">Gerçek JSON nesneleri - ancak dizelerdir yalnızca tanıtıcıları anahtar türleri.</span><span class="sxs-lookup"><span data-stu-id="39d8c-178">As actual JSON objects - but only handles key types that are strings.</span></span>|
|<span data-ttu-id="39d8c-179">Kaçan karakter</span><span class="sxs-lookup"><span data-stu-id="39d8c-179">Escaped characters</span></span>|<span data-ttu-id="39d8c-180">Her zaman bir kaçış ile eğik çizgi (/); ilet hiçbir zaman "\n" gibi kaçılmamış geçersiz JSON karaktere izin verilir.</span><span class="sxs-lookup"><span data-stu-id="39d8c-180">Always with an escape forward slash (/); never allows un-escaped invalid JSON characters, such as "\n".</span></span>|<span data-ttu-id="39d8c-181">Eğik çizgi (/) DateTime değerleri için bir kaçış ile iletin.</span><span class="sxs-lookup"><span data-stu-id="39d8c-181">With an escape forward slash (/) for DateTime values.</span></span>|

## <a name="see-also"></a><span data-ttu-id="39d8c-182">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="39d8c-182">See also</span></span>

- [<span data-ttu-id="39d8c-183">Nasıl yapılır: ASP.NET AJAX Uç Noktası Eklemek için Yapılandırma Kullanma</span><span class="sxs-lookup"><span data-stu-id="39d8c-183">How to: Use Configuration to Add an ASP.NET AJAX Endpoint</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md)
