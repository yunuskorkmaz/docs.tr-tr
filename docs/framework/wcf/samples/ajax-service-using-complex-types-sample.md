---
title: Karmaşık Türler Kullanan AJAX Hizmeti Örneği
ms.date: 03/30/2017
ms.assetid: 88242b99-4811-4cbe-8201-52ddf48fb174
ms.openlocfilehash: c284fbef36ee7f6dda725ba9a3db9b98fb1549ed
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33804085"
---
# <a name="ajax-service-using-complex-types-sample"></a><span data-ttu-id="b48b9-102">Karmaşık Türler Kullanan AJAX Hizmeti Örneği</span><span class="sxs-lookup"><span data-stu-id="b48b9-102">AJAX Service Using Complex Types Sample</span></span>
<span data-ttu-id="b48b9-103">Bu örnek, karmaşık türler örneklerini oluşturur ve bunları hizmeti ve istemci JavaScript nesne gösterimi (JSON) olarak arasındaki gönderen bir ASP.NET zaman uyumsuz JavaScript ve XML (AJAX) bir hizmet oluşturmak için Windows Communication Foundation (WCF) kullanımı gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="b48b9-103">This sample demonstrates how to use Windows Communication Foundation (WCF) to create an ASP.NET Asynchronous JavaScript and XML (AJAX) service that creates instances of complex types and sends them between service and client as JavaScript Object Notation (JSON).</span></span> <span data-ttu-id="b48b9-104">Bir AJAX hizmeti bir Web tarayıcısı istemciden JavaScript kodu kullanarak erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b48b9-104">You can access an AJAX service by using JavaScript code from a Web browser client.</span></span> <span data-ttu-id="b48b9-105">Bu örnek derlemeler [temel AJAX hizmeti](../../../../docs/framework/wcf/samples/basic-ajax-service.md) örnek.</span><span class="sxs-lookup"><span data-stu-id="b48b9-105">This sample builds on the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md) sample.</span></span>  
  
 <span data-ttu-id="b48b9-106">WCF AJAX desteği ASP.NET AJAX ile kullanmak için en iyisi olan <xref:System.Web.UI.ScriptManager> denetim.</span><span class="sxs-lookup"><span data-stu-id="b48b9-106">AJAX support in WCF is optimized for use with ASP.NET AJAX through the <xref:System.Web.UI.ScriptManager> control.</span></span> <span data-ttu-id="b48b9-107">WCF ile ASP.NET AJAX kullanılarak bir örnek için bkz: [AJAX örnekleri](http://msdn.microsoft.com/library/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e).</span><span class="sxs-lookup"><span data-stu-id="b48b9-107">For an example of using WCF with ASP.NET AJAX, see the [AJAX Samples](http://msdn.microsoft.com/library/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b48b9-108">Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="b48b9-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="b48b9-109">Aşağıdaki örnek hizmetinde bir AJAX özgü kod olmadan WCF hizmetidir.</span><span class="sxs-lookup"><span data-stu-id="b48b9-109">The service in the following sample is a WCF service with no AJAX-specific code.</span></span> <span data-ttu-id="b48b9-110">Çünkü <xref:System.ServiceModel.Web.WebGetAttribute> özniteliği uygulanmamış, varsayılan HTTP fiili ("POST") kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b48b9-110">Because the <xref:System.ServiceModel.Web.WebGetAttribute> attribute is not applied, the default HTTP verb ("POST") is used.</span></span> <span data-ttu-id="b48b9-111">Hizmet bir işlem var `DoMath`, adlandırılmış bir karmaşık tür döndüren `MathResult`.</span><span class="sxs-lookup"><span data-stu-id="b48b9-111">The service has one operation, `DoMath`, which returns a complex type named `MathResult`.</span></span> <span data-ttu-id="b48b9-112">Karmaşık türü de AJAX özgü kod içerir bir standart veri sözleşmesi türüdür.</span><span class="sxs-lookup"><span data-stu-id="b48b9-112">The complex type is a standard data contract type, which also contains no AJAX-specific code.</span></span>  

```csharp
[DataContract]  
public class MathResult  
{  
    [DataMember]  
    public double sum;  
    [DataMember]  
    public double difference;  
    [DataMember]  
    public double product;  
    [DataMember]  
    public double quotient;  
}  
```

 <span data-ttu-id="b48b9-113">Kullanarak hizmette bir AJAX uç noktası oluşturma <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, yalnızca temel AJAX hizmeti örneği olduğu gibi.</span><span class="sxs-lookup"><span data-stu-id="b48b9-113">Create an AJAX endpoint on the service by using the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, just as in the Basic AJAX Service sample.</span></span>  
  
 <span data-ttu-id="b48b9-114">İstemci Web sayfası ComplexTypeClientPage.aspx kullanıcı tıklattığında hizmetini çağırmak için ASP.NET ve JavaScript kodu içeren **hesaplamayı** sayfasında düğmesini.</span><span class="sxs-lookup"><span data-stu-id="b48b9-114">The client Web page ComplexTypeClientPage.aspx contains ASP.NET and JavaScript code to invoke the service when the user clicks the **Perform calculation** button on the page.</span></span> <span data-ttu-id="b48b9-115">Hizmetini çağırmak için kodu JSON gövdesi oluşturur ve HTTP POST, benzer şekilde kullanarak gönderir [AJAX hizmeti kullanarak HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md) örnek.</span><span class="sxs-lookup"><span data-stu-id="b48b9-115">The code to invoke the service constructs a JSON body and sends it using HTTP POST, similar to the [AJAX Service Using HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md) sample.</span></span>  
  
 <span data-ttu-id="b48b9-116">Hizmet çağrı başarılı olduktan sonra tek tek veri üyeleri erişebilir (`sum`, `difference`, `product` ve `quotient`) üzerinde elde edilen JavaScript nesne.</span><span class="sxs-lookup"><span data-stu-id="b48b9-116">After the service call succeeds, you can access the individual data members (`sum`, `difference`, `product` and `quotient`) on the resulting JavaScript object.</span></span>  

```javascript
function onSuccess(mathResult){  
     document.getElementById("sum").value = mathResult.sum;  
     document.getElementById("difference").value = mathResult.difference;  
     document.getElementById("product").value = mathResult.product;  
     document.getElementById("quotient").value = mathResult.quotient;  
}  
```

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="b48b9-117">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="b48b9-117">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="b48b9-118">Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b48b9-118">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="b48b9-119">Çözüm ComplexTypeAjaxService.sln açıklandığı gibi yapı [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b48b9-119">Build the solution ComplexTypeAjaxService.sln as described in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="b48b9-120">Gidin http://localhost/ServiceModelSamples/ComplexTypeClientPage.aspx (ComplexTypeClientPage.aspx proje dizininden tarayıcıda aç değil).</span><span class="sxs-lookup"><span data-stu-id="b48b9-120">Navigate to http://localhost/ServiceModelSamples/ComplexTypeClientPage.aspx (do not open ComplexTypeClientPage.aspx in the browser from the project directory).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b48b9-121">Örnekler, bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="b48b9-121">The samples may already be installed on your computer.</span></span> <span data-ttu-id="b48b9-122">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="b48b9-122">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="b48b9-123">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="b48b9-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b48b9-124">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="b48b9-124">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\ComplexTypeAjaxService`  
  
## <a name="see-also"></a><span data-ttu-id="b48b9-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b48b9-125">See Also</span></span>  
 [<span data-ttu-id="b48b9-126">Temel AJAX Hizmeti</span><span class="sxs-lookup"><span data-stu-id="b48b9-126">Basic AJAX Service</span></span>](../../../../docs/framework/wcf/samples/basic-ajax-service.md)
