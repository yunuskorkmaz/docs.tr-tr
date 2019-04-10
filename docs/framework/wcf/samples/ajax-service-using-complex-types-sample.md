---
title: Karmaşık Türler Kullanan AJAX Hizmeti Örneği
ms.date: 03/30/2017
ms.assetid: 88242b99-4811-4cbe-8201-52ddf48fb174
ms.openlocfilehash: cde7e48d0f0c44d68266d60399ac197d322a42cc
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59342225"
---
# <a name="ajax-service-using-complex-types-sample"></a><span data-ttu-id="2c42a-102">Karmaşık Türler Kullanan AJAX Hizmeti Örneği</span><span class="sxs-lookup"><span data-stu-id="2c42a-102">AJAX Service Using Complex Types Sample</span></span>
<span data-ttu-id="2c42a-103">Bu örnek, Windows Communication Foundation (WCF) karmaşık türler örneklerini oluşturur ve bunları arasındaki hizmet ve istemci JavaScript nesne gösterimi (JSON) olarak gönderir, bir ASP.NET zaman uyumsuz JavaScript ve XML (AJAX) hizmet oluşturma için nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="2c42a-103">This sample demonstrates how to use Windows Communication Foundation (WCF) to create an ASP.NET Asynchronous JavaScript and XML (AJAX) service that creates instances of complex types and sends them between service and client as JavaScript Object Notation (JSON).</span></span> <span data-ttu-id="2c42a-104">JavaScript kodu bir Web tarayıcısı istemcisini kullanarak bir AJAX hizmete erişebilir.</span><span class="sxs-lookup"><span data-stu-id="2c42a-104">You can access an AJAX service by using JavaScript code from a Web browser client.</span></span> <span data-ttu-id="2c42a-105">Bu örnek yapılar [temel AJAX hizmeti](../../../../docs/framework/wcf/samples/basic-ajax-service.md) örnek.</span><span class="sxs-lookup"><span data-stu-id="2c42a-105">This sample builds on the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md) sample.</span></span>  
  
 <span data-ttu-id="2c42a-106">WCF AJAX desteği ASP.NET AJAX ile kullanım için optimize <xref:System.Web.UI.ScriptManager> denetimi.</span><span class="sxs-lookup"><span data-stu-id="2c42a-106">AJAX support in WCF is optimized for use with ASP.NET AJAX through the <xref:System.Web.UI.ScriptManager> control.</span></span> <span data-ttu-id="2c42a-107">ASP.NET AJAX ile WCF kullanan bir örnek için bkz: [AJAX örnekleri](ajax.md).</span><span class="sxs-lookup"><span data-stu-id="2c42a-107">For an example of using WCF with ASP.NET AJAX, see the [AJAX Samples](ajax.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2c42a-108">Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="2c42a-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="2c42a-109">Aşağıdaki örnekte bir WCF Hizmeti AJAX özgü kod olmadan hizmetidir.</span><span class="sxs-lookup"><span data-stu-id="2c42a-109">The service in the following sample is a WCF service with no AJAX-specific code.</span></span> <span data-ttu-id="2c42a-110">Çünkü <xref:System.ServiceModel.Web.WebGetAttribute> öznitelik uygulanmadı, varsayılan HTTP fiili ("POST") kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2c42a-110">Because the <xref:System.ServiceModel.Web.WebGetAttribute> attribute is not applied, the default HTTP verb ("POST") is used.</span></span> <span data-ttu-id="2c42a-111">Tek bir işlem hizmeti olan `DoMath`, adlı karmaşık bir tür döndüren `MathResult`.</span><span class="sxs-lookup"><span data-stu-id="2c42a-111">The service has one operation, `DoMath`, which returns a complex type named `MathResult`.</span></span> <span data-ttu-id="2c42a-112">Karmaşık tür AJAX özgü kod içeren bir standart veri anlaşması türü ' dir.</span><span class="sxs-lookup"><span data-stu-id="2c42a-112">The complex type is a standard data contract type, which also contains no AJAX-specific code.</span></span>  

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

 <span data-ttu-id="2c42a-113">Kullanarak, hizmette bir AJAX uç noktası oluşturma <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, yalnızca temel AJAX hizmeti örneği olduğu gibi.</span><span class="sxs-lookup"><span data-stu-id="2c42a-113">Create an AJAX endpoint on the service by using the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, just as in the Basic AJAX Service sample.</span></span>  
  
 <span data-ttu-id="2c42a-114">İstemci Web sayfası ComplexTypeClientPage.aspx kullanıcı tıkladığında hizmeti çağırmak için ASP.NET ve JavaScript kodu içeren **hesaplamayı** sayfasında düğme.</span><span class="sxs-lookup"><span data-stu-id="2c42a-114">The client Web page ComplexTypeClientPage.aspx contains ASP.NET and JavaScript code to invoke the service when the user clicks the **Perform calculation** button on the page.</span></span> <span data-ttu-id="2c42a-115">Hizmet çağırmak için kodu JSON gövdesi oluşturur ve benzer HTTP POST kullanarak gönderir [hizmet HTTP POST kullanan AJAX](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md) örnek.</span><span class="sxs-lookup"><span data-stu-id="2c42a-115">The code to invoke the service constructs a JSON body and sends it using HTTP POST, similar to the [AJAX Service Using HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md) sample.</span></span>  
  
 <span data-ttu-id="2c42a-116">Hizmet çağrısı başarılı olduktan sonra bireysel veri üyeleri erişebilir (`sum`, `difference`, `product` ve `quotient`) üzerinde oluşturulan JavaScript nesnesi.</span><span class="sxs-lookup"><span data-stu-id="2c42a-116">After the service call succeeds, you can access the individual data members (`sum`, `difference`, `product` and `quotient`) on the resulting JavaScript object.</span></span>  

```javascript
function onSuccess(mathResult){  
     document.getElementById("sum").value = mathResult.sum;  
     document.getElementById("difference").value = mathResult.difference;  
     document.getElementById("product").value = mathResult.product;  
     document.getElementById("quotient").value = mathResult.quotient;  
}  
```

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="2c42a-117">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="2c42a-117">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="2c42a-118">Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2c42a-118">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="2c42a-119">' % S'çözüm ComplexTypeAjaxService.sln açıklandığı gibi oluşturmak [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2c42a-119">Build the solution ComplexTypeAjaxService.sln as described in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="2c42a-120">Gidin `http://localhost/ServiceModelSamples/ComplexTypeClientPage.aspx` (ComplexTypeClientPage.aspx proje dizininden tarayıcıda aç değil).</span><span class="sxs-lookup"><span data-stu-id="2c42a-120">Navigate to `http://localhost/ServiceModelSamples/ComplexTypeClientPage.aspx` (do not open ComplexTypeClientPage.aspx in the browser from the project directory).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="2c42a-121">Örnekler, bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="2c42a-121">The samples may already be installed on your computer.</span></span> <span data-ttu-id="2c42a-122">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="2c42a-122">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="2c42a-123">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="2c42a-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="2c42a-124">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="2c42a-124">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\ComplexTypeAjaxService`  
  
## <a name="see-also"></a><span data-ttu-id="2c42a-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2c42a-125">See also</span></span>

- [<span data-ttu-id="2c42a-126">Temel AJAX Hizmeti</span><span class="sxs-lookup"><span data-stu-id="2c42a-126">Basic AJAX Service</span></span>](../../../../docs/framework/wcf/samples/basic-ajax-service.md)
