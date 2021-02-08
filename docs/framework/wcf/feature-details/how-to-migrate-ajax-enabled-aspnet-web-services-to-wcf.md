---
description: "Hakkında daha fazla bilgi edinin: nasıl yapılır: AJAX-Enabled ASP.NET Web Services 'ı WCF 'ye geçirme"
title: "Nasıl yapılır: AJAX Etkinleştirilmiş ASP.NET Web Hizmetlerini WCF'ye Taşıma"
ms.date: 03/30/2017
ms.assetid: 1428df4d-b18f-4e6d-bd4d-79ab3dd5147c
ms.openlocfilehash: fe79660f0ed8ef01a2607c94362d484cacc6a7b1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99793733"
---
# <a name="how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf"></a><span data-ttu-id="ee785-103">Nasıl yapılır: AJAX Etkinleştirilmiş ASP.NET Web Hizmetlerini WCF'ye Taşıma</span><span class="sxs-lookup"><span data-stu-id="ee785-103">How to: Migrate AJAX-Enabled ASP.NET Web Services to WCF</span></span>

<span data-ttu-id="ee785-104">Bu konuda, temel bir ASP.NET AJAX hizmetini eşdeğer bir AJAX özellikli Windows Communication Foundation (WCF) hizmetine geçirme yordamları özetlenmektedir.</span><span class="sxs-lookup"><span data-stu-id="ee785-104">This topic outlines procedures to migrate a basic ASP.NET AJAX service to an equivalent AJAX-enabled Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="ee785-105">Bir ASP.NET AJAX hizmetinin işlevsel WCF sürümünün nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ee785-105">It shows how to create a functionally equivalent WCF version of an ASP.NET AJAX service.</span></span> <span data-ttu-id="ee785-106">İki hizmet daha sonra yan yana kullanılabilir veya WCF hizmeti ASP.NET AJAX hizmetini değiştirmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ee785-106">The two services can then be used side by side, or the WCF service can be used to replace the ASP.NET AJAX service.</span></span>

 <span data-ttu-id="ee785-107">Mevcut bir ASP.NET AJAX hizmetini bir WCF AJAX hizmetine geçirmek aşağıdaki avantajları sağlar:</span><span class="sxs-lookup"><span data-stu-id="ee785-107">Migrating an existing ASP.NET AJAX service to a WCF AJAX service gives you the following benefits:</span></span>

- <span data-ttu-id="ee785-108">AJAX hizmetinizi, en az ek yapılandırmaya sahip bir SOAP hizmeti olarak kullanıma sunabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ee785-108">You can expose your AJAX service as a SOAP service with minimal extra configuration.</span></span>

- <span data-ttu-id="ee785-109">İzleme gibi WCF özelliklerinden faydalanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ee785-109">You can benefit from WCF features such as tracing, and so on.</span></span>

 <span data-ttu-id="ee785-110">Aşağıdaki yordamlarda, Visual Studio 2012 kullandığınızı varsayalım.</span><span class="sxs-lookup"><span data-stu-id="ee785-110">The following procedures assume that you are using Visual Studio 2012.</span></span>

 <span data-ttu-id="ee785-111">Bu konuda özetlenen yordamlardan kaynaklanan kod, yordamları izleyen örnekte verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="ee785-111">The code that results from the procedures outlined in this topic is provided in the example following the procedures.</span></span>

 <span data-ttu-id="ee785-112">Bir WCF hizmetini AJAX özellikli bir uç nokta aracılığıyla gösterme hakkında daha fazla bilgi için bkz. [nasıl yapılır: yapılandırma kullanımı ASP.NET AJAX uç noktası ekleme](how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md) konusu.</span><span class="sxs-lookup"><span data-stu-id="ee785-112">For more information about exposing a WCF service through an AJAX-enabled endpoint, see the [How to: Use Configuration to Add an ASP.NET AJAX Endpoint](how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md) topic.</span></span>

### <a name="to-create-and-test-the-aspnet-web-service-application"></a><span data-ttu-id="ee785-113">ASP.NET Web hizmeti uygulamasını oluşturmak ve test etmek için</span><span class="sxs-lookup"><span data-stu-id="ee785-113">To create and test the ASP.NET Web service application</span></span>

1. <span data-ttu-id="ee785-114">Visual Studio 2012 ' i açın.</span><span class="sxs-lookup"><span data-stu-id="ee785-114">Open Visual Studio 2012.</span></span>

2. <span data-ttu-id="ee785-115">**Dosya** menüsünde **Yeni**' yi ve ardından **Proje**' yi seçin ve ardından **ASP.NET Web hizmeti uygulaması** **' nı seçin**.</span><span class="sxs-lookup"><span data-stu-id="ee785-115">From the **File** menu, select **New**, then **Project**, then **Web**, and then select **ASP.NET Web Service Application**.</span></span>

3. <span data-ttu-id="ee785-116">Projeyi adlandırın `ASPHello` ve **Tamam**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="ee785-116">Name the project `ASPHello` and click **OK**.</span></span>

4. <span data-ttu-id="ee785-117">`System.Web.Script.Services.ScriptService]`Bu hizmet IÇIN Ajax 'ı etkinleştirmek üzere içeren Service1.asmx.cs dosyasındaki satırın açıklamasını kaldırın.</span><span class="sxs-lookup"><span data-stu-id="ee785-117">Uncomment the line in the Service1.asmx.cs file that contains `System.Web.Script.Services.ScriptService]` to enable AJAX for this service.</span></span>

5. <span data-ttu-id="ee785-118">**Build** menüsünde **Build Solution**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="ee785-118">From the **Build** menu, select **Build Solution**.</span></span>

6. <span data-ttu-id="ee785-119">**Hata Ayıkla** menüsünden **Hata Ayıklama Olmadan Başlat**’ı seçin.</span><span class="sxs-lookup"><span data-stu-id="ee785-119">From the **Debug** menu, select **Start Without Debugging**.</span></span>

7. <span data-ttu-id="ee785-120">Oluşturulan Web sayfasında `HelloWorld` işlemi seçin.</span><span class="sxs-lookup"><span data-stu-id="ee785-120">On the Web page generated, select the `HelloWorld` operation.</span></span>

8. <span data-ttu-id="ee785-121">Test sayfasındaki **çağır** düğmesine tıklayın `HelloWorld` .</span><span class="sxs-lookup"><span data-stu-id="ee785-121">Click the **Invoke** button on the `HelloWorld` test page.</span></span> <span data-ttu-id="ee785-122">Aşağıdaki XML yanıtını almalısınız.</span><span class="sxs-lookup"><span data-stu-id="ee785-122">You should receive the following XML response.</span></span>

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <string xmlns="http://tempuri.org/">Hello World</string>
    ```

9. <span data-ttu-id="ee785-123">Bu yanıt artık çalışan bir ASP.NET AJAX hizmetine sahip olduğunuza ve özellikle de hizmetin, HTTP POST isteklerine yanıt veren ve XML döndüren Service1. asmx/HelloWorld yolunda bir uç nokta açığa çıkardığına onaylar.</span><span class="sxs-lookup"><span data-stu-id="ee785-123">This response confirms that you now have a functioning ASP.NET AJAX service and, in particular, that the service has now exposed an endpoint at Service1.asmx/HelloWorld that responds to HTTP POST requests and returns XML.</span></span>

     <span data-ttu-id="ee785-124">Artık bu hizmeti bir WCF AJAX hizmeti kullanmak üzere dönüştürmeye hazırsınız.</span><span class="sxs-lookup"><span data-stu-id="ee785-124">Now you are ready to convert this service to use a WCF AJAX service.</span></span>

### <a name="to-create-an-equivalent-wcf-ajax-service-application"></a><span data-ttu-id="ee785-125">Eşdeğer bir WCF AJAX hizmet uygulaması oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="ee785-125">To create an equivalent WCF AJAX service application</span></span>

1. <span data-ttu-id="ee785-126">**ASPHello** projesine sağ tıklayın ve **Ekle**, **Yeni öğe** ve ardından **AJAX etkin WCF hizmeti**' ni seçin.</span><span class="sxs-lookup"><span data-stu-id="ee785-126">Right-click the **ASPHello** project and select **Add**, then **New Item**, and then **AJAX-enabled WCF Service**.</span></span>

2. <span data-ttu-id="ee785-127">Hizmeti adlandırın `WCFHello` ve **Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="ee785-127">Name the service `WCFHello` and click **Add**.</span></span>

3. <span data-ttu-id="ee785-128">WCFHello.svc.cs dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="ee785-128">Open the WCFHello.svc.cs file.</span></span>

4. <span data-ttu-id="ee785-129">Service1.asmx.cs 'den, işlemin aşağıdaki uygulamasını kopyalayın `HelloWorld` .</span><span class="sxs-lookup"><span data-stu-id="ee785-129">From Service1.asmx.cs, copy the following implementation of the `HelloWorld` operation.</span></span>

    ```csharp
    public string HelloWorld()
    {
        return "Hello World";
    }
    ```

5. <span data-ttu-id="ee785-130">İşlemin kopyalanmış uygulamasına `HelloWorld` aşağıdaki kodun yerine WCFHello.svc.cs dosyasına yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="ee785-130">Paste to copied implementation of the `HelloWorld` operation into the WCFHello.svc.cs file in place of the following code.</span></span>

    ```csharp
    public void DoWork()
    {
          // Add your operation implementation here
          return;
    }
    ```

6. <span data-ttu-id="ee785-131">`Namespace`İçin özniteliğini belirtin <xref:System.ServiceModel.ServiceContractAttribute> `WCFHello` .</span><span class="sxs-lookup"><span data-stu-id="ee785-131">Specify the `Namespace` attribute for <xref:System.ServiceModel.ServiceContractAttribute> as `WCFHello`.</span></span>

    ```csharp
    [ServiceContract(Namespace="WCFHello")]
    [AspNetCompatibilityRequirements(RequirementsMode=AspNetCompatibilityRequirementsMode.Required)]
    public class WCFHello
    { … }
    ```

7. <span data-ttu-id="ee785-132">Öğesini <xref:System.ServiceModel.Web.WebInvokeAttribute> `HelloWorld` işleme ekleyin ve <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A> özelliği döndürecek şekilde ayarlayın <xref:System.ServiceModel.Web.WebMessageFormat.Xml> .</span><span class="sxs-lookup"><span data-stu-id="ee785-132">Add the <xref:System.ServiceModel.Web.WebInvokeAttribute> to the `HelloWorld` operation and set the <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A> property to return <xref:System.ServiceModel.Web.WebMessageFormat.Xml>.</span></span> <span data-ttu-id="ee785-133">Ayarlanmamışsa, varsayılan dönüş türünün olduğunu unutmayın <xref:System.ServiceModel.Web.WebMessageFormat.Json> .</span><span class="sxs-lookup"><span data-stu-id="ee785-133">Note that, if not set, the default return type is <xref:System.ServiceModel.Web.WebMessageFormat.Json>.</span></span>

    ```csharp
    [OperationContract]
    [WebInvoke(ResponseFormat=WebMessageFormat.Xml)]
    public string HelloWorld()
    {
        return "Hello World";
    }
    ```

8. <span data-ttu-id="ee785-134">**Build** menüsünde **Build Solution**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="ee785-134">From the **Build** menu, select **Build Solution**.</span></span>

9. <span data-ttu-id="ee785-135">WCFHello. svc dosyasını açın ve **Hata Ayıkla** menüsünden **hata ayıklama olmadan Başlat**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="ee785-135">Open the WCFHello.svc file and from the **Debug** menu, select **Start Without Debugging**.</span></span>

10. <span data-ttu-id="ee785-136">Hizmet artık `WCFHello.svc/HelloWorld` http post isteklerine yanıt veren ' de bir uç nokta kullanıma sunuyor.</span><span class="sxs-lookup"><span data-stu-id="ee785-136">The service now exposes an endpoint at `WCFHello.svc/HelloWorld`, which responds to HTTP POST requests.</span></span> <span data-ttu-id="ee785-137">HTTP POST istekleri tarayıcıdan test edilemez, ancak uç nokta XML 'den sonraki XML 'yi döndürüyor.</span><span class="sxs-lookup"><span data-stu-id="ee785-137">HTTP POST requests cannot be tested from the browser, but the endpoint returns XML following XML.</span></span>

    ```xml
    <string xmlns="http://schemas.microsoft.com/2003/10/Serialization/">Hello World</string>
    ```

11. <span data-ttu-id="ee785-138">`WCFHello.svc/HelloWorld`Ve `Service1.aspx/HelloWorld` uç noktalar artık işlevsel olarak eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="ee785-138">The `WCFHello.svc/HelloWorld` and the `Service1.aspx/HelloWorld` endpoints are now functionally equivalent.</span></span>

## <a name="example"></a><span data-ttu-id="ee785-139">Örnek</span><span class="sxs-lookup"><span data-stu-id="ee785-139">Example</span></span>

 <span data-ttu-id="ee785-140">Bu konuda özetlenen yordamlardan kaynaklanan kod aşağıdaki örnekte verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="ee785-140">The code that results from the procedures outlined in this topic is provided in the following example.</span></span>

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

 <span data-ttu-id="ee785-141"><xref:System.Xml.XmlDocument>Türü <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> , tarafından seri hale getirilmediğinden tarafından desteklenmez <xref:System.Xml.Serialization.XmlSerializer> .</span><span class="sxs-lookup"><span data-stu-id="ee785-141">The <xref:System.Xml.XmlDocument> type is not supported by the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> because it is not serializable by the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="ee785-142">Bir <xref:System.Xml.Linq.XDocument> tür kullanabilir veya bunun yerine seri hale getirebilirsiniz <xref:System.Xml.XmlDocument.DocumentElement%2A> .</span><span class="sxs-lookup"><span data-stu-id="ee785-142">You can use either an <xref:System.Xml.Linq.XDocument> type, or serialize the <xref:System.Xml.XmlDocument.DocumentElement%2A> instead.</span></span>

 <span data-ttu-id="ee785-143">ASMX Web Hizmetleri yükseltilmekte ve yan yana WCF hizmetlerine geçiriliyorsa, iki türü istemcide aynı ada eşlemektan kaçının.</span><span class="sxs-lookup"><span data-stu-id="ee785-143">If ASMX Web services are being upgraded and migrated side-by-side to WCF services, avoid mapping two types to the same name on the client.</span></span> <span data-ttu-id="ee785-144">Bu, bir ve ' de aynı tür kullanılıyorsa serileştiricde bir özel duruma neden olur <xref:System.Web.Services.WebMethodAttribute> <xref:System.ServiceModel.ServiceContractAttribute> :</span><span class="sxs-lookup"><span data-stu-id="ee785-144">This causes an exception in serializers if the same type is used in a <xref:System.Web.Services.WebMethodAttribute> and a <xref:System.ServiceModel.ServiceContractAttribute>:</span></span>

- <span data-ttu-id="ee785-145">İlk olarak WCF hizmeti eklenirse, Web hizmetindeki <xref:System.Web.UI.ObjectConverter.ConvertValue%28System.Object%2CSystem.Type%2CSystem.String%29> SıRANıN WCF stil tanımı öncelikli olduğundan asmx Web hizmeti üzerindeki yöntemi çağırmak özel duruma neden olur.</span><span class="sxs-lookup"><span data-stu-id="ee785-145">If WCF service is added first, invoking the method on ASMX Web Service causes exception in <xref:System.Web.UI.ObjectConverter.ConvertValue%28System.Object%2CSystem.Type%2CSystem.String%29> because the WCF style definition of the order in the proxy takes precedence.</span></span>

- <span data-ttu-id="ee785-146">Önce ASMX Web hizmeti eklenirse, WCF hizmetinde çağırma yöntemi ' de özel durum oluşmasına neden olur <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> çünkü proxy 'deki sıranın Web hizmeti stil tanımı öncelik kazanır.</span><span class="sxs-lookup"><span data-stu-id="ee785-146">If ASMX Web Service is added first, invoking method on WCF service causes exception in <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> because the Web Service style definition of the order in the proxy takes precedence.</span></span>

 <span data-ttu-id="ee785-147">Ve ASP.NET AJAX arasındaki davranışta önemli farklılıklar vardır <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> <xref:System.Web.Script.Serialization.JavaScriptSerializer> .</span><span class="sxs-lookup"><span data-stu-id="ee785-147">There are significant differences in behavior between the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> and the ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer>.</span></span> <span data-ttu-id="ee785-148">Örneğin, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> bir sözlüğü anahtar/değer çiftleri dizisi olarak temsil ederken, ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer> bir sözlüğü gerçek JSON nesneleri olarak temsil eder.</span><span class="sxs-lookup"><span data-stu-id="ee785-148">For example, the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> represents a dictionary as an array of key/value pairs, whereas the ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer> represents a dictionary as actual JSON objects.</span></span> <span data-ttu-id="ee785-149">Bu nedenle, ASP.NET AJAX içinde temsil edilen sözlük aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="ee785-149">So the following is the dictionary represented in ASP.NET AJAX.</span></span>

```csharp
Dictionary<string, int> d = new Dictionary<string, int>();
d.Add("one", 1);
d.Add("two", 2);
```

 <span data-ttu-id="ee785-150">Bu sözlük, aşağıdaki listede gösterildiği gibi JSON nesnelerinde temsil edilir:</span><span class="sxs-lookup"><span data-stu-id="ee785-150">This dictionary is represented in JSON objects as shown in the following list:</span></span>

- <span data-ttu-id="ee785-151">[{"Key": "One", "Value": 1}, {"Key": "iki", "Value": 2}], <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer></span><span class="sxs-lookup"><span data-stu-id="ee785-151">[{"Key":"one","Value":1},{"Key":"two","Value":2}] by the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer></span></span>

- <span data-ttu-id="ee785-152">{"One": 1, "iki": 2} ASP.NET AJAX tarafından <xref:System.Web.Script.Serialization.JavaScriptSerializer></span><span class="sxs-lookup"><span data-stu-id="ee785-152">{"one":1,"two":2} by the ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer></span></span>

 <span data-ttu-id="ee785-153">, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> Anahtar türünün dize olmadığı, ancak işleyememesi durumunda sözlüklerin işleyebileceği anlamda daha güçlüdür <xref:System.Web.Script.Serialization.JavaScriptSerializer> .</span><span class="sxs-lookup"><span data-stu-id="ee785-153">The <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> is more powerful in the sense that it can handle dictionaries where the key type is not string, while the <xref:System.Web.Script.Serialization.JavaScriptSerializer> cannot.</span></span> <span data-ttu-id="ee785-154">Ancak ikincisi JSON kullanımı daha fazla.</span><span class="sxs-lookup"><span data-stu-id="ee785-154">But the latter is more JSON-friendly.</span></span>

 <span data-ttu-id="ee785-155">Bu serileştiriciler arasındaki önemli farklılıklar aşağıdaki tabloda özetlenmiştir.</span><span class="sxs-lookup"><span data-stu-id="ee785-155">The significant differences between these serializers are summarized in the following table.</span></span>

|<span data-ttu-id="ee785-156">Farklar kategorisi</span><span class="sxs-lookup"><span data-stu-id="ee785-156">Category of Differences</span></span>|<span data-ttu-id="ee785-157">DataContractJsonSerializer</span><span class="sxs-lookup"><span data-stu-id="ee785-157">DataContractJsonSerializer</span></span>|<span data-ttu-id="ee785-158">ASP.NET AJAX JavaScriptSerializer</span><span class="sxs-lookup"><span data-stu-id="ee785-158">ASP.NET AJAX JavaScriptSerializer</span></span>|
|-----------------------------|--------------------------------|---------------------------------------|
|<span data-ttu-id="ee785-159">Boş arabellek (yeni bayt [0]) içinde <xref:System.Object> (veya <xref:System.Uri> başka bir sınıfa) seri durumdan çıkarılamadı.</span><span class="sxs-lookup"><span data-stu-id="ee785-159">Deserializing the empty buffer (new byte[0]) into <xref:System.Object> (or <xref:System.Uri>, or some other classes).</span></span>|<span data-ttu-id="ee785-160">SerializationException</span><span class="sxs-lookup"><span data-stu-id="ee785-160">SerializationException</span></span>|<span data-ttu-id="ee785-161">null</span><span class="sxs-lookup"><span data-stu-id="ee785-161">null</span></span>|
|<span data-ttu-id="ee785-162">Serileştirme <xref:System.DBNull.Value></span><span class="sxs-lookup"><span data-stu-id="ee785-162">Serialization of <xref:System.DBNull.Value></span></span>|<span data-ttu-id="ee785-163">{} (veya {"__type": "#System"})</span><span class="sxs-lookup"><span data-stu-id="ee785-163">{} (or {"__type":"#System"})</span></span>|<span data-ttu-id="ee785-164">Null</span><span class="sxs-lookup"><span data-stu-id="ee785-164">Null</span></span>|
|<span data-ttu-id="ee785-165">[Serializable] türlerinin özel üyelerinin serileştirilmesi.</span><span class="sxs-lookup"><span data-stu-id="ee785-165">Serialization of the private members of [Serializable] types.</span></span>|<span data-ttu-id="ee785-166">metodu</span><span class="sxs-lookup"><span data-stu-id="ee785-166">serialized</span></span>|<span data-ttu-id="ee785-167">serileştirilmedi</span><span class="sxs-lookup"><span data-stu-id="ee785-167">not serialized</span></span>|
|<span data-ttu-id="ee785-168">Türlerin ortak özelliklerinin serileştirilmesi <xref:System.Runtime.Serialization.ISerializable> .</span><span class="sxs-lookup"><span data-stu-id="ee785-168">Serialization of the public properties of <xref:System.Runtime.Serialization.ISerializable> types.</span></span>|<span data-ttu-id="ee785-169">serileştirilmedi</span><span class="sxs-lookup"><span data-stu-id="ee785-169">not serialized</span></span>|<span data-ttu-id="ee785-170">metodu</span><span class="sxs-lookup"><span data-stu-id="ee785-170">serialized</span></span>|
|<span data-ttu-id="ee785-171">JSON "Extensions"</span><span class="sxs-lookup"><span data-stu-id="ee785-171">"Extensions" of JSON</span></span>|<span data-ttu-id="ee785-172">Nesne üye adlarında tırnak işareti gerektiren JSON belirtimine uyar ({"a": "Hello"}).</span><span class="sxs-lookup"><span data-stu-id="ee785-172">Adheres to the JSON specification, which requires quotes on object member names ({"a":"hello"}).</span></span>|<span data-ttu-id="ee785-173">Tırnak işaretleri olmadan nesne üyelerinin adlarını destekler ({a: "Hello"}).</span><span class="sxs-lookup"><span data-stu-id="ee785-173">Supports the names of object members without quotes ({a:"hello"}).</span></span>|
|<span data-ttu-id="ee785-174"><xref:System.DateTime> Eşgüdümlü Evrensel Saat (UTC)</span><span class="sxs-lookup"><span data-stu-id="ee785-174"><xref:System.DateTime> Coordinated Universal Time (UTC)</span></span>|<span data-ttu-id="ee785-175">" \\ /Date (123456789U) \\ /" veya " \\ /date \\ (\d + (U&#124; ( \\ + \\ -[\d {4} ])) biçimini desteklemez mi? \\ ) \\ \\ /)".</span><span class="sxs-lookup"><span data-stu-id="ee785-175">Does not support format "\\/Date(123456789U)\\/" or "\\/Date\\(\d+(U&#124;(\\+\\-[\d{4}]))?\\)\\\\/)".</span></span>|<span data-ttu-id="ee785-176">" \\ /Date (123456789U) \\ /" ve " \\ /date \\ (\d + (U&#124; ( \\ + \\ -[\d {4} ])) biçimini destekler mi? \\ ) \\ \\ /) "değerini DateTime değerleri olarak.</span><span class="sxs-lookup"><span data-stu-id="ee785-176">Supports format "\\/Date(123456789U)\\/" and "\\/Date\\(\d+(U&#124;(\\+\\-[\d{4}]))?\\)\\\\/)" as DateTime values.</span></span>|
|<span data-ttu-id="ee785-177">Sözlüklerin temsili</span><span class="sxs-lookup"><span data-stu-id="ee785-177">Representation of dictionaries</span></span>|<span data-ttu-id="ee785-178">Bir KeyValuePair dizisi \<K,V> , dizeler olmayan anahtar türlerini işler.</span><span class="sxs-lookup"><span data-stu-id="ee785-178">An array of KeyValuePair\<K,V>, handles key types that are not strings.</span></span>|<span data-ttu-id="ee785-179">Gerçek JSON nesneleri olarak-ancak yalnızca dizeler olan anahtar türlerini işler.</span><span class="sxs-lookup"><span data-stu-id="ee785-179">As actual JSON objects - but only handles key types that are strings.</span></span>|
|<span data-ttu-id="ee785-180">Kaçan karakterler</span><span class="sxs-lookup"><span data-stu-id="ee785-180">Escaped characters</span></span>|<span data-ttu-id="ee785-181">Her zaman kaçış eğik çizgiyle (/); "\n" gibi, kaçırılmamış geçersiz JSON karakterlerinin hiçbir şekilde yapılmasına izin vermez.</span><span class="sxs-lookup"><span data-stu-id="ee785-181">Always with an escape forward slash (/); never allows un-escaped invalid JSON characters, such as "\n".</span></span>|<span data-ttu-id="ee785-182">Tarih/saat değerleri için çıkış ileri eğik çizgi (/) ile.</span><span class="sxs-lookup"><span data-stu-id="ee785-182">With an escape forward slash (/) for DateTime values.</span></span>|

## <a name="see-also"></a><span data-ttu-id="ee785-183">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ee785-183">See also</span></span>

- [<span data-ttu-id="ee785-184">Nasıl yapılır: ASP.NET AJAX Uç Noktası Eklemek için Yapılandırma Kullanma</span><span class="sxs-lookup"><span data-stu-id="ee785-184">How to: Use Configuration to Add an ASP.NET AJAX Endpoint</span></span>](how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md)
