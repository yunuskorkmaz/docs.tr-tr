---
title: "Nasıl yapılır: AJAX Etkinleştirilmiş ASP.NET Web Hizmetlerini WCF'ye Taşıma"
ms.date: 03/30/2017
ms.assetid: 1428df4d-b18f-4e6d-bd4d-79ab3dd5147c
ms.openlocfilehash: 048408adf8678c243a225a233cb1173c9b7f869f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33495557"
---
# <a name="how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf"></a><span data-ttu-id="48d0f-102">Nasıl yapılır: AJAX Etkinleştirilmiş ASP.NET Web Hizmetlerini WCF'ye Taşıma</span><span class="sxs-lookup"><span data-stu-id="48d0f-102">How to: Migrate AJAX-Enabled ASP.NET Web Services to WCF</span></span>
<span data-ttu-id="48d0f-103">Bu konu, temel ASP.NET AJAX hizmeti eşdeğer bir AJAX etkinleştirilmiş Windows Communication Foundation (WCF) hizmetine geçirme yordamları özetler.</span><span class="sxs-lookup"><span data-stu-id="48d0f-103">This topic outlines procedures to migrate a basic ASP.NET AJAX service to an equivalent AJAX-enabled Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="48d0f-104">Bir ASP.NET AJAX Hizmeti işlevsel olarak eşdeğer bir WCF sürümü oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="48d0f-104">It shows how to create a functionally equivalent WCF version of an ASP.NET AJAX service.</span></span> <span data-ttu-id="48d0f-105">İki hizmet daha sonra bir yan yana kullanılabilir veya WCF hizmeti, ASP.NET AJAX hizmeti değiştirmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="48d0f-105">The two services can then be used side by side, or the WCF service can be used to replace the ASP.NET AJAX service.</span></span>  
  
 <span data-ttu-id="48d0f-106">Mevcut bir ASP.NET AJAX geçiş hizmetine bir WCF AJAX hizmeti, aşağıdaki avantajları sunar:</span><span class="sxs-lookup"><span data-stu-id="48d0f-106">Migrating an existing ASP.NET AJAX service to a WCF AJAX service gives you the following benefits:</span></span>  
  
-   <span data-ttu-id="48d0f-107">Minimal ek yapılandırma ile SOAP hizmet olarak AJAX hizmetinizi getirebilir.</span><span class="sxs-lookup"><span data-stu-id="48d0f-107">You can expose your AJAX service as a SOAP service with minimal extra configuration.</span></span>  
  
-   <span data-ttu-id="48d0f-108">İzleme gibi WCF özelliklerinden yararlanır ve benzeri.</span><span class="sxs-lookup"><span data-stu-id="48d0f-108">You can benefit from WCF features such as tracing, and so on.</span></span>  
  
 <span data-ttu-id="48d0f-109">Aşağıdaki yordamlar, kullandığınızı varsayar [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="48d0f-109">The following procedures assume that you are using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span></span>  
  
 <span data-ttu-id="48d0f-110">Bu konuda anlatılan yordamlar oluşur kod yordamları aşağıdaki örnekte sağlanır.</span><span class="sxs-lookup"><span data-stu-id="48d0f-110">The code that results from the procedures outlined in this topic is provided in the example following the procedures.</span></span>  
  
 <span data-ttu-id="48d0f-111">Bir WCF hizmeti bir AJAX etkinleştirilmiş uç nokta aracılığıyla gösterme hakkında daha fazla bilgi için bkz: [nasıl yapılır: ASP.NET AJAX uç noktası eklemek için yapılandırma kullan](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md) konu.</span><span class="sxs-lookup"><span data-stu-id="48d0f-111">For more information about exposing a WCF service through an AJAX-enabled endpoint, see the [How to: Use Configuration to Add an ASP.NET AJAX Endpoint](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md) topic.</span></span>  
  
### <a name="to-create-and-test-the-aspnet-web-service-application"></a><span data-ttu-id="48d0f-112">Oluşturmak ve ASP.NET Web hizmeti uygulamasını sınamak için</span><span class="sxs-lookup"><span data-stu-id="48d0f-112">To create and test the ASP.NET Web service application</span></span>  
  
1.  <span data-ttu-id="48d0f-113">Açık [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="48d0f-113">Open [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span></span>  
  
2.  <span data-ttu-id="48d0f-114">Gelen **dosya** menüsünde, select **yeni**, ardından **proje**, ardından **Web**ve ardından **ASP.NET Web hizmeti uygulama** .</span><span class="sxs-lookup"><span data-stu-id="48d0f-114">From the **File** menu, select **New**, then **Project**, then **Web**, and then select **ASP.NET Web Service Application**.</span></span>  
  
3.  <span data-ttu-id="48d0f-115">Proje adı `ASPHello` tıklatıp **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="48d0f-115">Name the project `ASPHello` and click **OK**.</span></span>  
  
4.  <span data-ttu-id="48d0f-116">İçeren Service1.asmx.cs dosyasında satırı açıklamadan kaldırmasına `System.Web.Script.Services.ScriptService]` AJAX bu hizmeti etkinleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="48d0f-116">Uncomment the line in the Service1.asmx.cs file that contains `System.Web.Script.Services.ScriptService]` to enable AJAX for this service.</span></span>  
  
5.  <span data-ttu-id="48d0f-117">Gelen **yapı** menüsünde, select **yapı çözümü**.</span><span class="sxs-lookup"><span data-stu-id="48d0f-117">From the **Build** menu, select **Build Solution**.</span></span>  
  
6.  <span data-ttu-id="48d0f-118">Gelen **hata ayıklama** menüsünde, select **hata ayıklama olmadan Başlat**.</span><span class="sxs-lookup"><span data-stu-id="48d0f-118">From the **Debug** menu, select **Start Without Debugging**.</span></span>  
  
7.  <span data-ttu-id="48d0f-119">Oluşturulan Web sayfası üzerinde seçmek `HelloWorld` işlemi.</span><span class="sxs-lookup"><span data-stu-id="48d0f-119">On the Web page generated, select the `HelloWorld` operation.</span></span>  
  
8.  <span data-ttu-id="48d0f-120">Tıklatın **Invoke** düğmesini `HelloWorld` test sayfası.</span><span class="sxs-lookup"><span data-stu-id="48d0f-120">Click the **Invoke** button on the `HelloWorld` test page.</span></span> <span data-ttu-id="48d0f-121">Aşağıdaki XML yanıtı almanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="48d0f-121">You should receive the following XML response.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <string xmlns="http://tempuri.org/">Hello World</string>  
    ```  
  
9. <span data-ttu-id="48d0f-122">Bu yanıt işlevsel bir ASP.NET AJAX hizmeti artık vardır ve özellikle, hizmet, bir HTTP POST yanıt Service1.asmx/HelloWorld uçta şimdi kullanıma ve istekleri XML döndürür, onaylar.</span><span class="sxs-lookup"><span data-stu-id="48d0f-122">This response confirms that you now have a functioning ASP.NET AJAX service and, in particular, that the service has now exposed an endpoint at Service1.asmx/HelloWorld that responds to HTTP POST requests and returns XML.</span></span>  
  
     <span data-ttu-id="48d0f-123">Artık bir WCF AJAX hizmeti kullanmak için bu hizmet dönüştürmek hazırsınız.</span><span class="sxs-lookup"><span data-stu-id="48d0f-123">Now you are ready to convert this service to use a WCF AJAX service.</span></span>  
  
### <a name="to-create-an-equivalent-wcf-ajax-service-application"></a><span data-ttu-id="48d0f-124">Bir eşdeğer WCF AJAX hizmet uygulaması oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="48d0f-124">To create an equivalent WCF AJAX service application</span></span>  
  
1.  <span data-ttu-id="48d0f-125">Sağ **ASPHello** proje ve seçin **Ekle**, ardından **yeni öğe**ve ardından **AJAX etkinleştirilmiş WCF Hizmeti**.</span><span class="sxs-lookup"><span data-stu-id="48d0f-125">Right-click the **ASPHello** project and select **Add**, then **New Item**, and then **AJAX-enabled WCF Service**.</span></span>  
  
2.  <span data-ttu-id="48d0f-126">Ad hizmeti `WCFHello` tıklatıp **Ekle**.</span><span class="sxs-lookup"><span data-stu-id="48d0f-126">Name the service `WCFHello` and click **Add**.</span></span>  
  
3.  <span data-ttu-id="48d0f-127">WCFHello.svc.cs dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="48d0f-127">Open the WCFHello.svc.cs file.</span></span>  
  
4.  <span data-ttu-id="48d0f-128">Aşağıdaki uygulanması service1.asmx.cs kopyalama `HelloWorld` işlemi.</span><span class="sxs-lookup"><span data-stu-id="48d0f-128">From Service1.asmx.cs, copy the following implementation of the `HelloWorld` operation.</span></span>  
  
    ```  
    public string HelloWorld()  
    {  
         return "Hello World";  
    }  
    ```  
  
5.  <span data-ttu-id="48d0f-129">Kopyalanan uyarlamasını Yapıştır `HelloWorld` WCFHello.svc.cs dosyasına aşağıdaki kodu yerine işlemi.</span><span class="sxs-lookup"><span data-stu-id="48d0f-129">Paste to copied implementation of the `HelloWorld` operation into the WCFHello.svc.cs file in place of the following code.</span></span>  
  
    ```  
    public void DoWork()  
    {  
          // Add your operation implementation here  
          return;  
    }  
    ```  
  
6.  <span data-ttu-id="48d0f-130">Belirtin `Namespace` için öznitelik <xref:System.ServiceModel.ServiceContractAttribute> olarak `WCFHello`.</span><span class="sxs-lookup"><span data-stu-id="48d0f-130">Specify the `Namespace` attribute for <xref:System.ServiceModel.ServiceContractAttribute> as `WCFHello`.</span></span>  
  
    ```  
    [ServiceContract(Namespace="WCFHello")]  
    [AspNetCompatibilityRequirements(RequirementsMode=AspNetCompatibilityRequirementsMode.Required)]  
    public class WCFHello  
    { … }  
    ```  
  
7.  <span data-ttu-id="48d0f-131">Ekleme <xref:System.ServiceModel.Web.WebInvokeAttribute> için `HelloWorld` işlemi ve kümesi <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A> dönmek için özellik <xref:System.ServiceModel.Web.WebMessageFormat.Xml>.</span><span class="sxs-lookup"><span data-stu-id="48d0f-131">Add the <xref:System.ServiceModel.Web.WebInvokeAttribute> to the `HelloWorld` operation and set the <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A> property to return <xref:System.ServiceModel.Web.WebMessageFormat.Xml>.</span></span> <span data-ttu-id="48d0f-132">Dönüş türü olan varsayılan ayarlanmış değilse unutmayın <xref:System.ServiceModel.Web.WebMessageFormat.Json>.</span><span class="sxs-lookup"><span data-stu-id="48d0f-132">Note that, if not set, the default return type is <xref:System.ServiceModel.Web.WebMessageFormat.Json>.</span></span>  
  
    ```  
    [OperationContract]  
    [WebInvoke(ResponseFormat=WebMessageFormat.Xml)]  
    public string HelloWorld()  
    {  
        return "Hello World";  
    }  
    ```  
  
8.  <span data-ttu-id="48d0f-133">Gelen **yapı** menüsünde, select **yapı çözümü**.</span><span class="sxs-lookup"><span data-stu-id="48d0f-133">From the **Build** menu, select **Build Solution**.</span></span>  
  
9. <span data-ttu-id="48d0f-134">WCFHello.svc dosyasını açın ve **hata ayıklama** menüsünde, select **hata ayıklama olmadan Başlat**.</span><span class="sxs-lookup"><span data-stu-id="48d0f-134">Open the WCFHello.svc file and from the **Debug** menu, select **Start Without Debugging**.</span></span>  
  
10. <span data-ttu-id="48d0f-135">Hizmet artık bir uç noktada kullanıma sunan `WCFHello.svc/HelloWorld`, HTTP POST isteklerine yanıt verir.</span><span class="sxs-lookup"><span data-stu-id="48d0f-135">The service now exposes an endpoint at `WCFHello.svc/HelloWorld`, which responds to HTTP POST requests.</span></span> <span data-ttu-id="48d0f-136">HTTP POST isteklerini tarayıcıdan sınanamıyor ancak uç nokta XML aşağıdaki XML döndürür.</span><span class="sxs-lookup"><span data-stu-id="48d0f-136">HTTP POST requests cannot be tested from the browser, but the endpoint returns XML following XML.</span></span>  
  
    ```xml  
    <string xmlns="http://schemas.microsoft.com/2003/10/Serialization/">Hello World</string>  
    ```  
  
11. <span data-ttu-id="48d0f-137">`WCFHello.svc/HelloWorld` Ve `Service1.aspx/HelloWorld` uç noktaları işlevsel olarak eşdeğer şimdi.</span><span class="sxs-lookup"><span data-stu-id="48d0f-137">The `WCFHello.svc/HelloWorld` and the `Service1.aspx/HelloWorld` endpoints are now functionally equivalent.</span></span>  
  
## <a name="example"></a><span data-ttu-id="48d0f-138">Örnek</span><span class="sxs-lookup"><span data-stu-id="48d0f-138">Example</span></span>  
 <span data-ttu-id="48d0f-139">Bu konuda anlatılan yordamlar oluşur kod, aşağıdaki örnekte sağlanır.</span><span class="sxs-lookup"><span data-stu-id="48d0f-139">The code that results from the procedures outlined in this topic is provided in the following example.</span></span>  
  
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
  
 <span data-ttu-id="48d0f-140"><xref:System.Xml.XmlDocument> Türü tarafından desteklenmiyor <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> tarafından seri hale getirilebilir olmadığından <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="48d0f-140">The <xref:System.Xml.XmlDocument> type is not supported by the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> because it is not serializable by the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="48d0f-141">Ya da kullanabileceğiniz bir <xref:System.Xml.Linq.XDocument> yazın veya seri <xref:System.Xml.XmlDocument.DocumentElement%2A> yerine.</span><span class="sxs-lookup"><span data-stu-id="48d0f-141">You can use either an <xref:System.Xml.Linq.XDocument> type, or serialize the <xref:System.Xml.XmlDocument.DocumentElement%2A> instead.</span></span>  
  
 <span data-ttu-id="48d0f-142">ASMX Web Hizmetleri yükseltilen ve yan yana WCF hizmetlerine geçirilir, istemcideki aynı adı için iki tür eşleme kaçının.</span><span class="sxs-lookup"><span data-stu-id="48d0f-142">If ASMX Web services are being upgraded and migrated side-by-side to WCF services, avoid mapping two types to the same name on the client.</span></span> <span data-ttu-id="48d0f-143">Aynı türde kullanılıyorsa bu bir özel durum serileştiricileri neden olan bir <xref:System.Web.Services.WebMethodAttribute> ve <xref:System.ServiceModel.ServiceContractAttribute>:</span><span class="sxs-lookup"><span data-stu-id="48d0f-143">This causes an exception in serializers if the same type is used in a <xref:System.Web.Services.WebMethodAttribute> and a <xref:System.ServiceModel.ServiceContractAttribute>:</span></span>  
  
-   <span data-ttu-id="48d0f-144">WCF Hizmeti önce eklediyseniz, özel durum ASMX Web hizmeti yöntemi çağırma neden <xref:System.Web.UI.ObjectConverter.ConvertValue%28System.Object%2CSystem.Type%2CSystem.String%29> proxy sırayla WCF stil tanımını öncelikli olduğundan.</span><span class="sxs-lookup"><span data-stu-id="48d0f-144">If WCF service is added first, invoking the method on ASMX Web Service causes exception in <xref:System.Web.UI.ObjectConverter.ConvertValue%28System.Object%2CSystem.Type%2CSystem.String%29> because the WCF style definition of the order in the proxy takes precedence.</span></span>  
  
-   <span data-ttu-id="48d0f-145">ASMX Web hizmeti önce eklediyseniz, WCF Hizmeti üzerinde yöntemi çağrılırken özel durum neden <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> proxy sırayla Web hizmeti stil tanımını öncelikli olduğundan.</span><span class="sxs-lookup"><span data-stu-id="48d0f-145">If ASMX Web Service is added first, invoking method on WCF service causes exception in <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> because the Web Service style definition of the order in the proxy takes precedence.</span></span>  
  
 <span data-ttu-id="48d0f-146">Davranış önemli farklılıkları vardır <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> ve ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer>.</span><span class="sxs-lookup"><span data-stu-id="48d0f-146">There are significant differences in behavior between the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> and the ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer>.</span></span> <span data-ttu-id="48d0f-147">Örneğin, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> bir sözlüğü ancak temsil eden bir anahtar/değer çiftleri dizisi olarak ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer> bir sözlük gerçek JSON nesnelerini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="48d0f-147">For example, the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> represents a dictionary as an array of key/value pairs, whereas the ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer> represents a dictionary as actual JSON objects.</span></span> <span data-ttu-id="48d0f-148">Aşağıdaki ASP.NET AJAX ' temsil sözlük gelir.</span><span class="sxs-lookup"><span data-stu-id="48d0f-148">So the following is the dictionary represented in ASP.NET AJAX.</span></span>  
  
```  
Dictionary<string, int> d = new Dictionary<string, int>();  
d.Add("one", 1);  
d.Add("two", 2);  
```  
  
 <span data-ttu-id="48d0f-149">Bu sözlük JSON nesneleri aşağıdaki listede gösterildiği gibi gösterilir:</span><span class="sxs-lookup"><span data-stu-id="48d0f-149">This dictionary is represented in JSON objects as shown in the following list:</span></span>  
  
-   <span data-ttu-id="48d0f-150">[{"Anahtarı": "Bir", "Value": 1}, {"Anahtarı": "İki", "Value": 2}] tarafından <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer></span><span class="sxs-lookup"><span data-stu-id="48d0f-150">[{"Key":"one","Value":1},{"Key":"two","Value":2}] by the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer></span></span>  
  
-   <span data-ttu-id="48d0f-151">{"bir": 1, "iki": 2} ASP.NET AJAX tarafından <xref:System.Web.Script.Serialization.JavaScriptSerializer></span><span class="sxs-lookup"><span data-stu-id="48d0f-151">{"one":1,"two":2} by the ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer></span></span>  
  
 <span data-ttu-id="48d0f-152"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> Bu anahtar türü dizesi olduğu sözlükler işleyebilir anlamda daha güçlüdür ancak <xref:System.Web.Script.Serialization.JavaScriptSerializer> olamaz.</span><span class="sxs-lookup"><span data-stu-id="48d0f-152">The <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> is more powerful in the sense that it can handle dictionaries where the key type is not string, while the <xref:System.Web.Script.Serialization.JavaScriptSerializer> cannot.</span></span> <span data-ttu-id="48d0f-153">Ancak ikinci daha JSON kolay.</span><span class="sxs-lookup"><span data-stu-id="48d0f-153">But the latter is more JSON-friendly.</span></span>  
  
 <span data-ttu-id="48d0f-154">Bu serileştiricileri arasında önemli farklılıklar aşağıdaki tabloda özetlenmiştir.</span><span class="sxs-lookup"><span data-stu-id="48d0f-154">The significant differences between these serializers are summarized in the following table.</span></span>  
  
|<span data-ttu-id="48d0f-155">Farkları kategorisi</span><span class="sxs-lookup"><span data-stu-id="48d0f-155">Category of Differences</span></span>|<span data-ttu-id="48d0f-156">DataContractJsonSerializer</span><span class="sxs-lookup"><span data-stu-id="48d0f-156">DataContractJsonSerializer</span></span>|<span data-ttu-id="48d0f-157">ASP.NET AJAX JavaScriptSerializer</span><span class="sxs-lookup"><span data-stu-id="48d0f-157">ASP.NET AJAX JavaScriptSerializer</span></span>|  
|-----------------------------|--------------------------------|---------------------------------------|  
|<span data-ttu-id="48d0f-158">Boş arabellek seri durumdan (içine yeni byte[0]) <xref:System.Object> (veya <xref:System.Uri>, ya da başka bir sınıf).</span><span class="sxs-lookup"><span data-stu-id="48d0f-158">Deserializing the empty buffer (new byte[0]) into <xref:System.Object> (or <xref:System.Uri>, or some other classes).</span></span>|<span data-ttu-id="48d0f-159">SerializationException</span><span class="sxs-lookup"><span data-stu-id="48d0f-159">SerializationException</span></span>|<span data-ttu-id="48d0f-160">null</span><span class="sxs-lookup"><span data-stu-id="48d0f-160">null</span></span>|  
|<span data-ttu-id="48d0f-161">Seri hale getirilmesi için <xref:System.DBNull.Value></span><span class="sxs-lookup"><span data-stu-id="48d0f-161">Serialization of <xref:System.DBNull.Value></span></span>|<span data-ttu-id="48d0f-162">{} (veya {"__type": "#System"})</span><span class="sxs-lookup"><span data-stu-id="48d0f-162">{} (or {"__type":"#System"})</span></span>|<span data-ttu-id="48d0f-163">Null</span><span class="sxs-lookup"><span data-stu-id="48d0f-163">Null</span></span>|  
|<span data-ttu-id="48d0f-164">Serileştirme [Serializable] türleri özel üyeleri.</span><span class="sxs-lookup"><span data-stu-id="48d0f-164">Serialization of the private members of [Serializable] types.</span></span>|<span data-ttu-id="48d0f-165">seri hale getirilmiş</span><span class="sxs-lookup"><span data-stu-id="48d0f-165">serialized</span></span>|<span data-ttu-id="48d0f-166">Serileştirilmiş değil</span><span class="sxs-lookup"><span data-stu-id="48d0f-166">not serialized</span></span>|  
|<span data-ttu-id="48d0f-167">Ortak özellikleri serileştirmek <xref:System.Runtime.Serialization.ISerializable> türleri.</span><span class="sxs-lookup"><span data-stu-id="48d0f-167">Serialization of the public properties of <xref:System.Runtime.Serialization.ISerializable> types.</span></span>|<span data-ttu-id="48d0f-168">Serileştirilmiş değil</span><span class="sxs-lookup"><span data-stu-id="48d0f-168">not serialized</span></span>|<span data-ttu-id="48d0f-169">seri hale getirilmiş</span><span class="sxs-lookup"><span data-stu-id="48d0f-169">serialized</span></span>|  
|<span data-ttu-id="48d0f-170">JSON "uzantılarını"</span><span class="sxs-lookup"><span data-stu-id="48d0f-170">"Extensions" of JSON</span></span>|<span data-ttu-id="48d0f-171">Nesne üyesi adlarını tekliflerinde gerektirir JSON belirtimi aynılarını ({"a": "hello"}).</span><span class="sxs-lookup"><span data-stu-id="48d0f-171">Adheres to the JSON specification, which requires quotes on object member names ({"a":"hello"}).</span></span>|<span data-ttu-id="48d0f-172">Nesne üyeleri tırnak işaretleri ({a: "hello"}) olmadan adlarını destekler.</span><span class="sxs-lookup"><span data-stu-id="48d0f-172">Supports the names of object members without quotes ({a:"hello"}).</span></span>|  
|<span data-ttu-id="48d0f-173"><xref:System.DateTime> Eşgüdümlü Evrensel Saat (UTC)</span><span class="sxs-lookup"><span data-stu-id="48d0f-173"><xref:System.DateTime> Coordinated Universal Time (UTC)</span></span>|<span data-ttu-id="48d0f-174">Biçim desteklemiyor "\\/Date(123456789U)\\/" veya "\\/Date\\(\d+ (U&#124;(\\+\\-[\d{4}]))?\\) \\\\/)".</span><span class="sxs-lookup"><span data-stu-id="48d0f-174">Does not support format "\\/Date(123456789U)\\/" or "\\/Date\\(\d+(U&#124;(\\+\\-[\d{4}]))?\\)\\\\/)".</span></span>|<span data-ttu-id="48d0f-175">Destekler biçimi "\\/Date(123456789U)\\/" ve "\\/Date\\(\d+ (U&#124;(\\+\\-[\d{4}]))?\\) \\ \\/) "DateTime değerleri olarak.</span><span class="sxs-lookup"><span data-stu-id="48d0f-175">Supports format "\\/Date(123456789U)\\/" and "\\/Date\\(\d+(U&#124;(\\+\\-[\d{4}]))?\\)\\\\/)" as DateTime values.</span></span>|  
|<span data-ttu-id="48d0f-176">Sözlük gösterimi</span><span class="sxs-lookup"><span data-stu-id="48d0f-176">Representation of dictionaries</span></span>|<span data-ttu-id="48d0f-177">Bir dizi KeyValuePair\<K, V >, dize olmayan anahtar türleri işler.</span><span class="sxs-lookup"><span data-stu-id="48d0f-177">An array of KeyValuePair\<K,V>, handles key types that are not strings.</span></span>|<span data-ttu-id="48d0f-178">Gerçek JSON nesnelerinin - ancak dizelerdir yalnızca tanıtıcıları anahtar türü.</span><span class="sxs-lookup"><span data-stu-id="48d0f-178">As actual JSON objects - but only handles key types that are strings.</span></span>|  
|<span data-ttu-id="48d0f-179">Kaçış karakterli karakterleri</span><span class="sxs-lookup"><span data-stu-id="48d0f-179">Escaped characters</span></span>|<span data-ttu-id="48d0f-180">Her zaman bir kaçış ile eğik çizgi (/); ilet hiçbir zaman "\n" gibi atlanmamış geçersiz JSON karaktere izin verilir.</span><span class="sxs-lookup"><span data-stu-id="48d0f-180">Always with an escape forward slash (/); never allows un-escaped invalid JSON characters, such as "\n".</span></span>|<span data-ttu-id="48d0f-181">Bir kaçış ile eğik çizgi (/) DateTime değerleri için iletin.</span><span class="sxs-lookup"><span data-stu-id="48d0f-181">With an escape forward slash (/) for DateTime values.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="48d0f-182">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="48d0f-182">See Also</span></span>  
 [<span data-ttu-id="48d0f-183">Nasıl yapılır: ASP.NET AJAX Uç Noktası Eklemek için Yapılandırma Kullanma</span><span class="sxs-lookup"><span data-stu-id="48d0f-183">How to: Use Configuration to Add an ASP.NET AJAX Endpoint</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md)
