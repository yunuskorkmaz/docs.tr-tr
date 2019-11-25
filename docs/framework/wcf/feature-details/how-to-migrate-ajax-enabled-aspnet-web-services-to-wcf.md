---
title: "Nasıl yapılır: AJAX Etkinleştirilmiş ASP.NET Web Hizmetlerini WCF'ye Taşıma"
ms.date: 03/30/2017
ms.assetid: 1428df4d-b18f-4e6d-bd4d-79ab3dd5147c
ms.openlocfilehash: 60e3088b9075464176c328af1f52676a69c4990f
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976138"
---
# <a name="how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf"></a><span data-ttu-id="00ae5-102">Nasıl yapılır: AJAX Etkinleştirilmiş ASP.NET Web Hizmetlerini WCF'ye Taşıma</span><span class="sxs-lookup"><span data-stu-id="00ae5-102">How to: Migrate AJAX-Enabled ASP.NET Web Services to WCF</span></span>
<span data-ttu-id="00ae5-103">Bu konuda, temel bir ASP.NET AJAX hizmetini eşdeğer bir AJAX özellikli Windows Communication Foundation (WCF) hizmetine geçirme yordamları özetlenmektedir.</span><span class="sxs-lookup"><span data-stu-id="00ae5-103">This topic outlines procedures to migrate a basic ASP.NET AJAX service to an equivalent AJAX-enabled Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="00ae5-104">Bir ASP.NET AJAX hizmetinin işlevsel WCF sürümünün nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="00ae5-104">It shows how to create a functionally equivalent WCF version of an ASP.NET AJAX service.</span></span> <span data-ttu-id="00ae5-105">İki hizmet daha sonra yan yana kullanılabilir veya WCF hizmeti ASP.NET AJAX hizmetini değiştirmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="00ae5-105">The two services can then be used side by side, or the WCF service can be used to replace the ASP.NET AJAX service.</span></span>

 <span data-ttu-id="00ae5-106">Mevcut bir ASP.NET AJAX hizmetini bir WCF AJAX hizmetine geçirmek aşağıdaki avantajları sağlar:</span><span class="sxs-lookup"><span data-stu-id="00ae5-106">Migrating an existing ASP.NET AJAX service to a WCF AJAX service gives you the following benefits:</span></span>

- <span data-ttu-id="00ae5-107">AJAX hizmetinizi, en az ek yapılandırmaya sahip bir SOAP hizmeti olarak kullanıma sunabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="00ae5-107">You can expose your AJAX service as a SOAP service with minimal extra configuration.</span></span>

- <span data-ttu-id="00ae5-108">İzleme gibi WCF özelliklerinden faydalanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="00ae5-108">You can benefit from WCF features such as tracing, and so on.</span></span>

 <span data-ttu-id="00ae5-109">Aşağıdaki yordamlarda, Visual Studio 2012 kullandığınızı varsayalım.</span><span class="sxs-lookup"><span data-stu-id="00ae5-109">The following procedures assume that you are using Visual Studio 2012.</span></span>

 <span data-ttu-id="00ae5-110">Bu konuda özetlenen yordamlardan kaynaklanan kod, yordamları izleyen örnekte verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="00ae5-110">The code that results from the procedures outlined in this topic is provided in the example following the procedures.</span></span>

 <span data-ttu-id="00ae5-111">Bir WCF hizmetini AJAX özellikli bir uç nokta aracılığıyla gösterme hakkında daha fazla bilgi için bkz. [nasıl yapılır: yapılandırma kullanımı ASP.NET AJAX uç noktası ekleme](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md) konusu.</span><span class="sxs-lookup"><span data-stu-id="00ae5-111">For more information about exposing a WCF service through an AJAX-enabled endpoint, see the [How to: Use Configuration to Add an ASP.NET AJAX Endpoint](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md) topic.</span></span>

### <a name="to-create-and-test-the-aspnet-web-service-application"></a><span data-ttu-id="00ae5-112">ASP.NET Web hizmeti uygulamasını oluşturmak ve test etmek için</span><span class="sxs-lookup"><span data-stu-id="00ae5-112">To create and test the ASP.NET Web service application</span></span>

1. <span data-ttu-id="00ae5-113">Visual Studio 2012 ' i açın.</span><span class="sxs-lookup"><span data-stu-id="00ae5-113">Open Visual Studio 2012.</span></span>

2. <span data-ttu-id="00ae5-114">**Dosya** menüsünde **Yeni**' yi ve ardından **Proje**' yi seçin ve ardından **ASP.NET Web hizmeti uygulaması** **' nı seçin**.</span><span class="sxs-lookup"><span data-stu-id="00ae5-114">From the **File** menu, select **New**, then **Project**, then **Web**, and then select **ASP.NET Web Service Application**.</span></span>

3. <span data-ttu-id="00ae5-115">Projeyi `ASPHello` adlandırın ve **Tamam**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="00ae5-115">Name the project `ASPHello` and click **OK**.</span></span>

4. <span data-ttu-id="00ae5-116">Bu hizmet için AJAX 'ı etkinleştirmek üzere `System.Web.Script.Services.ScriptService]` içeren Service1.asmx.cs dosyasındaki satırın açıklamasını kaldırın.</span><span class="sxs-lookup"><span data-stu-id="00ae5-116">Uncomment the line in the Service1.asmx.cs file that contains `System.Web.Script.Services.ScriptService]` to enable AJAX for this service.</span></span>

5. <span data-ttu-id="00ae5-117">**Build** menüsünde **Build Solution**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="00ae5-117">From the **Build** menu, select **Build Solution**.</span></span>

6. <span data-ttu-id="00ae5-118">**Hata Ayıkla** menüsünden **hata ayıklama olmadan Başlat**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="00ae5-118">From the **Debug** menu, select **Start Without Debugging**.</span></span>

7. <span data-ttu-id="00ae5-119">Oluşturulan Web sayfasında `HelloWorld` işlemini seçin.</span><span class="sxs-lookup"><span data-stu-id="00ae5-119">On the Web page generated, select the `HelloWorld` operation.</span></span>

8. <span data-ttu-id="00ae5-120">`HelloWorld` test sayfasındaki **çağır** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="00ae5-120">Click the **Invoke** button on the `HelloWorld` test page.</span></span> <span data-ttu-id="00ae5-121">Aşağıdaki XML yanıtını almalısınız.</span><span class="sxs-lookup"><span data-stu-id="00ae5-121">You should receive the following XML response.</span></span>

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <string xmlns="http://tempuri.org/">Hello World</string>
    ```

9. <span data-ttu-id="00ae5-122">Bu yanıt artık çalışan bir ASP.NET AJAX hizmetine sahip olduğunuza ve özellikle de hizmetin, HTTP POST isteklerine yanıt veren ve XML döndüren Service1. asmx/HelloWorld yolunda bir uç nokta açığa çıkardığına onaylar.</span><span class="sxs-lookup"><span data-stu-id="00ae5-122">This response confirms that you now have a functioning ASP.NET AJAX service and, in particular, that the service has now exposed an endpoint at Service1.asmx/HelloWorld that responds to HTTP POST requests and returns XML.</span></span>

     <span data-ttu-id="00ae5-123">Artık bu hizmeti bir WCF AJAX hizmeti kullanmak üzere dönüştürmeye hazırsınız.</span><span class="sxs-lookup"><span data-stu-id="00ae5-123">Now you are ready to convert this service to use a WCF AJAX service.</span></span>

### <a name="to-create-an-equivalent-wcf-ajax-service-application"></a><span data-ttu-id="00ae5-124">Eşdeğer bir WCF AJAX hizmet uygulaması oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="00ae5-124">To create an equivalent WCF AJAX service application</span></span>

1. <span data-ttu-id="00ae5-125">**ASPHello** projesine sağ tıklayın ve **Ekle**, **Yeni öğe**ve ardından **AJAX etkin WCF hizmeti**' ni seçin.</span><span class="sxs-lookup"><span data-stu-id="00ae5-125">Right-click the **ASPHello** project and select **Add**, then **New Item**, and then **AJAX-enabled WCF Service**.</span></span>

2. <span data-ttu-id="00ae5-126">Hizmeti `WCFHello` adlandırın ve **Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="00ae5-126">Name the service `WCFHello` and click **Add**.</span></span>

3. <span data-ttu-id="00ae5-127">WCFHello.svc.cs dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="00ae5-127">Open the WCFHello.svc.cs file.</span></span>

4. <span data-ttu-id="00ae5-128">Service1.asmx.cs ' dan `HelloWorld` işleminin aşağıdaki uygulamasını kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="00ae5-128">From Service1.asmx.cs, copy the following implementation of the `HelloWorld` operation.</span></span>

    ```csharp
    public string HelloWorld()
    {
        return "Hello World";
    }
    ```

5. <span data-ttu-id="00ae5-129">`HelloWorld` işleminin kopyalanmış uygulamasına aşağıdaki kodun yerine WCFHello.svc.cs dosyasına yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="00ae5-129">Paste to copied implementation of the `HelloWorld` operation into the WCFHello.svc.cs file in place of the following code.</span></span>

    ```csharp
    public void DoWork()
    {
          // Add your operation implementation here
          return;
    }
    ```

6. <span data-ttu-id="00ae5-130"><xref:System.ServiceModel.ServiceContractAttribute> için `Namespace` özniteliğini `WCFHello`olarak belirtin.</span><span class="sxs-lookup"><span data-stu-id="00ae5-130">Specify the `Namespace` attribute for <xref:System.ServiceModel.ServiceContractAttribute> as `WCFHello`.</span></span>

    ```csharp
    [ServiceContract(Namespace="WCFHello")]
    [AspNetCompatibilityRequirements(RequirementsMode=AspNetCompatibilityRequirementsMode.Required)]
    public class WCFHello
    { … }
    ```

7. <span data-ttu-id="00ae5-131">`HelloWorld` işlemine <xref:System.ServiceModel.Web.WebInvokeAttribute> ekleyin ve <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A> özelliğini <xref:System.ServiceModel.Web.WebMessageFormat.Xml>döndürecek şekilde ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="00ae5-131">Add the <xref:System.ServiceModel.Web.WebInvokeAttribute> to the `HelloWorld` operation and set the <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A> property to return <xref:System.ServiceModel.Web.WebMessageFormat.Xml>.</span></span> <span data-ttu-id="00ae5-132">Ayarlanmamışsa, varsayılan dönüş türünün <xref:System.ServiceModel.Web.WebMessageFormat.Json>olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="00ae5-132">Note that, if not set, the default return type is <xref:System.ServiceModel.Web.WebMessageFormat.Json>.</span></span>

    ```csharp
    [OperationContract]
    [WebInvoke(ResponseFormat=WebMessageFormat.Xml)]
    public string HelloWorld()
    {
        return "Hello World";
    }
    ```

8. <span data-ttu-id="00ae5-133">**Build** menüsünde **Build Solution**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="00ae5-133">From the **Build** menu, select **Build Solution**.</span></span>

9. <span data-ttu-id="00ae5-134">WCFHello. svc dosyasını açın ve **Hata Ayıkla** menüsünden **hata ayıklama olmadan Başlat**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="00ae5-134">Open the WCFHello.svc file and from the **Debug** menu, select **Start Without Debugging**.</span></span>

10. <span data-ttu-id="00ae5-135">Hizmet artık HTTP POST isteklerine yanıt veren `WCFHello.svc/HelloWorld`bir uç nokta kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="00ae5-135">The service now exposes an endpoint at `WCFHello.svc/HelloWorld`, which responds to HTTP POST requests.</span></span> <span data-ttu-id="00ae5-136">HTTP POST istekleri tarayıcıdan test edilemez, ancak uç nokta XML 'den sonraki XML 'yi döndürüyor.</span><span class="sxs-lookup"><span data-stu-id="00ae5-136">HTTP POST requests cannot be tested from the browser, but the endpoint returns XML following XML.</span></span>

    ```xml
    <string xmlns="http://schemas.microsoft.com/2003/10/Serialization/">Hello World</string>
    ```

11. <span data-ttu-id="00ae5-137">`WCFHello.svc/HelloWorld` ve `Service1.aspx/HelloWorld` uç noktaları artık işlevsel olarak eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="00ae5-137">The `WCFHello.svc/HelloWorld` and the `Service1.aspx/HelloWorld` endpoints are now functionally equivalent.</span></span>

## <a name="example"></a><span data-ttu-id="00ae5-138">Örnek</span><span class="sxs-lookup"><span data-stu-id="00ae5-138">Example</span></span>
 <span data-ttu-id="00ae5-139">Bu konuda özetlenen yordamlardan kaynaklanan kod aşağıdaki örnekte verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="00ae5-139">The code that results from the procedures outlined in this topic is provided in the following example.</span></span>

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

 <span data-ttu-id="00ae5-140"><xref:System.Xml.Serialization.XmlSerializer>tarafından serileştirilebilir olmadığından <xref:System.Xml.XmlDocument> türü <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> tarafından desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="00ae5-140">The <xref:System.Xml.XmlDocument> type is not supported by the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> because it is not serializable by the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="00ae5-141"><xref:System.Xml.Linq.XDocument> türü kullanabilir veya bunun yerine <xref:System.Xml.XmlDocument.DocumentElement%2A> seri hale getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="00ae5-141">You can use either an <xref:System.Xml.Linq.XDocument> type, or serialize the <xref:System.Xml.XmlDocument.DocumentElement%2A> instead.</span></span>

 <span data-ttu-id="00ae5-142">ASMX Web Hizmetleri yükseltilmekte ve yan yana WCF hizmetlerine geçiriliyorsa, iki türü istemcide aynı ada eşlemektan kaçının.</span><span class="sxs-lookup"><span data-stu-id="00ae5-142">If ASMX Web services are being upgraded and migrated side-by-side to WCF services, avoid mapping two types to the same name on the client.</span></span> <span data-ttu-id="00ae5-143">Bu, <xref:System.Web.Services.WebMethodAttribute> ve <xref:System.ServiceModel.ServiceContractAttribute>aynı tür kullanılırsa serileştiriciler için bir özel duruma neden olur:</span><span class="sxs-lookup"><span data-stu-id="00ae5-143">This causes an exception in serializers if the same type is used in a <xref:System.Web.Services.WebMethodAttribute> and a <xref:System.ServiceModel.ServiceContractAttribute>:</span></span>

- <span data-ttu-id="00ae5-144">WCF hizmeti ilk eklendiyse,, proxy 'deki sıranın WCF stil tanımı öncelikli olduğundan ASMX Web hizmetindeki yöntemi çağırmak <xref:System.Web.UI.ObjectConverter.ConvertValue%28System.Object%2CSystem.Type%2CSystem.String%29> özel duruma neden olur.</span><span class="sxs-lookup"><span data-stu-id="00ae5-144">If WCF service is added first, invoking the method on ASMX Web Service causes exception in <xref:System.Web.UI.ObjectConverter.ConvertValue%28System.Object%2CSystem.Type%2CSystem.String%29> because the WCF style definition of the order in the proxy takes precedence.</span></span>

- <span data-ttu-id="00ae5-145">İlk olarak ASMX Web hizmeti eklendiyse, proxy 'deki sıranın Web hizmeti stil tanımı öncelikli olduğundan WCF hizmeti üzerinde yöntem çağırma <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> özel duruma neden olur.</span><span class="sxs-lookup"><span data-stu-id="00ae5-145">If ASMX Web Service is added first, invoking method on WCF service causes exception in <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> because the Web Service style definition of the order in the proxy takes precedence.</span></span>

 <span data-ttu-id="00ae5-146"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> ve ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer>arasındaki davranışlardan önemli farklılıklar vardır.</span><span class="sxs-lookup"><span data-stu-id="00ae5-146">There are significant differences in behavior between the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> and the ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer>.</span></span> <span data-ttu-id="00ae5-147">Örneğin, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> bir sözlüğü anahtar/değer çiftleri dizisi olarak temsil ederken, ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer> bir sözlüğü gerçek JSON nesneleri olarak temsil eder.</span><span class="sxs-lookup"><span data-stu-id="00ae5-147">For example, the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> represents a dictionary as an array of key/value pairs, whereas the ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer> represents a dictionary as actual JSON objects.</span></span> <span data-ttu-id="00ae5-148">Bu nedenle, ASP.NET AJAX içinde temsil edilen sözlük aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="00ae5-148">So the following is the dictionary represented in ASP.NET AJAX.</span></span>

```csharp
Dictionary<string, int> d = new Dictionary<string, int>();
d.Add("one", 1);
d.Add("two", 2);
```

 <span data-ttu-id="00ae5-149">Bu sözlük, aşağıdaki listede gösterildiği gibi JSON nesnelerinde temsil edilir:</span><span class="sxs-lookup"><span data-stu-id="00ae5-149">This dictionary is represented in JSON objects as shown in the following list:</span></span>

- <span data-ttu-id="00ae5-150">[{"Key": "bir", "Value": 1}, {"Key": "iki", "Value": 2}] <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer></span><span class="sxs-lookup"><span data-stu-id="00ae5-150">[{"Key":"one","Value":1},{"Key":"two","Value":2}] by the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer></span></span>

- <span data-ttu-id="00ae5-151">{"One": 1, "iki": 2} ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer></span><span class="sxs-lookup"><span data-stu-id="00ae5-151">{"one":1,"two":2} by the ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer></span></span>

 <span data-ttu-id="00ae5-152"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, anahtar türünün dize olmayan sözlüklerin işleyebileceği, <xref:System.Web.Script.Serialization.JavaScriptSerializer> işleyememesi açısından daha güçlüdür.</span><span class="sxs-lookup"><span data-stu-id="00ae5-152">The <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> is more powerful in the sense that it can handle dictionaries where the key type is not string, while the <xref:System.Web.Script.Serialization.JavaScriptSerializer> cannot.</span></span> <span data-ttu-id="00ae5-153">Ancak ikincisi JSON kullanımı daha fazla.</span><span class="sxs-lookup"><span data-stu-id="00ae5-153">But the latter is more JSON-friendly.</span></span>

 <span data-ttu-id="00ae5-154">Bu serileştiriciler arasındaki önemli farklılıklar aşağıdaki tabloda özetlenmiştir.</span><span class="sxs-lookup"><span data-stu-id="00ae5-154">The significant differences between these serializers are summarized in the following table.</span></span>

|<span data-ttu-id="00ae5-155">Farklar kategorisi</span><span class="sxs-lookup"><span data-stu-id="00ae5-155">Category of Differences</span></span>|<span data-ttu-id="00ae5-156">DataContractJsonSerializer</span><span class="sxs-lookup"><span data-stu-id="00ae5-156">DataContractJsonSerializer</span></span>|<span data-ttu-id="00ae5-157">ASP.NET AJAX JavaScriptSerializer</span><span class="sxs-lookup"><span data-stu-id="00ae5-157">ASP.NET AJAX JavaScriptSerializer</span></span>|
|-----------------------------|--------------------------------|---------------------------------------|
|<span data-ttu-id="00ae5-158">Boş arabelleğin (yeni bayt [0]) <xref:System.Object> (veya <xref:System.Uri>ya da başka bir sınıfa) serisi kaldırılırken.</span><span class="sxs-lookup"><span data-stu-id="00ae5-158">Deserializing the empty buffer (new byte[0]) into <xref:System.Object> (or <xref:System.Uri>, or some other classes).</span></span>|<span data-ttu-id="00ae5-159">SerializationException</span><span class="sxs-lookup"><span data-stu-id="00ae5-159">SerializationException</span></span>|<span data-ttu-id="00ae5-160">null</span><span class="sxs-lookup"><span data-stu-id="00ae5-160">null</span></span>|
|<span data-ttu-id="00ae5-161"><xref:System.DBNull.Value> serileştirilmesi</span><span class="sxs-lookup"><span data-stu-id="00ae5-161">Serialization of <xref:System.DBNull.Value></span></span>|<span data-ttu-id="00ae5-162">{} (veya {"__type": "#System"})</span><span class="sxs-lookup"><span data-stu-id="00ae5-162">{} (or {"__type":"#System"})</span></span>|<span data-ttu-id="00ae5-163">Null</span><span class="sxs-lookup"><span data-stu-id="00ae5-163">Null</span></span>|
|<span data-ttu-id="00ae5-164">[Serializable] türlerinin özel üyelerinin serileştirilmesi.</span><span class="sxs-lookup"><span data-stu-id="00ae5-164">Serialization of the private members of [Serializable] types.</span></span>|<span data-ttu-id="00ae5-165">metodu</span><span class="sxs-lookup"><span data-stu-id="00ae5-165">serialized</span></span>|<span data-ttu-id="00ae5-166">serileştirilmedi</span><span class="sxs-lookup"><span data-stu-id="00ae5-166">not serialized</span></span>|
|<span data-ttu-id="00ae5-167"><xref:System.Runtime.Serialization.ISerializable> türlerinin ortak özelliklerinin serileştirilmesi.</span><span class="sxs-lookup"><span data-stu-id="00ae5-167">Serialization of the public properties of <xref:System.Runtime.Serialization.ISerializable> types.</span></span>|<span data-ttu-id="00ae5-168">serileştirilmedi</span><span class="sxs-lookup"><span data-stu-id="00ae5-168">not serialized</span></span>|<span data-ttu-id="00ae5-169">metodu</span><span class="sxs-lookup"><span data-stu-id="00ae5-169">serialized</span></span>|
|<span data-ttu-id="00ae5-170">JSON "Extensions"</span><span class="sxs-lookup"><span data-stu-id="00ae5-170">"Extensions" of JSON</span></span>|<span data-ttu-id="00ae5-171">Nesne üye adlarında tırnak işareti gerektiren JSON belirtimine uyar ({"a": "Hello"}).</span><span class="sxs-lookup"><span data-stu-id="00ae5-171">Adheres to the JSON specification, which requires quotes on object member names ({"a":"hello"}).</span></span>|<span data-ttu-id="00ae5-172">Tırnak işaretleri olmadan nesne üyelerinin adlarını destekler ({a: "Hello"}).</span><span class="sxs-lookup"><span data-stu-id="00ae5-172">Supports the names of object members without quotes ({a:"hello"}).</span></span>|
|<span data-ttu-id="00ae5-173"><xref:System.DateTime> Eşgüdümlü Evrensel Saat (UTC)</span><span class="sxs-lookup"><span data-stu-id="00ae5-173"><xref:System.DateTime> Coordinated Universal Time (UTC)</span></span>|<span data-ttu-id="00ae5-174">"\\/Date (123456789U)\\/" veya "\\/Date\\(\d + (U&#124;(\\+\\-[\d{4}])) biçimini desteklemez mi?\\)\\\\/) ".</span><span class="sxs-lookup"><span data-stu-id="00ae5-174">Does not support format "\\/Date(123456789U)\\/" or "\\/Date\\(\d+(U&#124;(\\+\\-[\d{4}]))?\\)\\\\/)".</span></span>|<span data-ttu-id="00ae5-175">"\\/Date (123456789U)\\/" ve "\\/Date\\(\d + (U&#124;(\\+\\-[\d{4}])) biçimini destekler mi?\\) "\\/)"\\DateTime değerleri olarak.</span><span class="sxs-lookup"><span data-stu-id="00ae5-175">Supports format "\\/Date(123456789U)\\/" and "\\/Date\\(\d+(U&#124;(\\+\\-[\d{4}]))?\\)\\\\/)" as DateTime values.</span></span>|
|<span data-ttu-id="00ae5-176">Sözlüklerin temsili</span><span class="sxs-lookup"><span data-stu-id="00ae5-176">Representation of dictionaries</span></span>|<span data-ttu-id="00ae5-177">\<K, V > KeyValuePair dizisi dize olmayan anahtar türlerini işler.</span><span class="sxs-lookup"><span data-stu-id="00ae5-177">An array of KeyValuePair\<K,V>, handles key types that are not strings.</span></span>|<span data-ttu-id="00ae5-178">Gerçek JSON nesneleri olarak-ancak yalnızca dizeler olan anahtar türlerini işler.</span><span class="sxs-lookup"><span data-stu-id="00ae5-178">As actual JSON objects - but only handles key types that are strings.</span></span>|
|<span data-ttu-id="00ae5-179">Kaçan karakterler</span><span class="sxs-lookup"><span data-stu-id="00ae5-179">Escaped characters</span></span>|<span data-ttu-id="00ae5-180">Her zaman kaçış eğik çizgiyle (/); "\n" gibi, kaçırılmamış geçersiz JSON karakterlerinin hiçbir şekilde yapılmasına izin vermez.</span><span class="sxs-lookup"><span data-stu-id="00ae5-180">Always with an escape forward slash (/); never allows un-escaped invalid JSON characters, such as "\n".</span></span>|<span data-ttu-id="00ae5-181">Tarih/saat değerleri için çıkış ileri eğik çizgi (/) ile.</span><span class="sxs-lookup"><span data-stu-id="00ae5-181">With an escape forward slash (/) for DateTime values.</span></span>|

## <a name="see-also"></a><span data-ttu-id="00ae5-182">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="00ae5-182">See also</span></span>

- [<span data-ttu-id="00ae5-183">Nasıl yapılır: ASP.NET AJAX Uç Noktası Eklemek için Yapılandırma Kullanma</span><span class="sxs-lookup"><span data-stu-id="00ae5-183">How to: Use Configuration to Add an ASP.NET AJAX Endpoint</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md)
