---
title: Karmaşık Türler Kullanan AJAX Hizmeti Örneği
ms.date: 03/30/2017
ms.assetid: 88242b99-4811-4cbe-8201-52ddf48fb174
ms.openlocfilehash: 4227446e8844accd06490d8e7cf933da43d875a6
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84575920"
---
# <a name="ajax-service-using-complex-types-sample"></a><span data-ttu-id="ef9ee-102">Karmaşık Türler Kullanan AJAX Hizmeti Örneği</span><span class="sxs-lookup"><span data-stu-id="ef9ee-102">AJAX Service Using Complex Types Sample</span></span>

<span data-ttu-id="ef9ee-103">Bu örnek, karmaşık türlerin örneklerini oluşturan ve bunları JavaScript Nesne Gösterimi (JSON) olarak hizmet ve istemci arasında gönderen bir ASP.NET zaman uyumsuz JavaScript ve XML (AJAX) hizmeti oluşturmak için Windows Communication Foundation (WCF) öğesinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ef9ee-103">This sample demonstrates how to use Windows Communication Foundation (WCF) to create an ASP.NET Asynchronous JavaScript and XML (AJAX) service that creates instances of complex types and sends them between service and client as JavaScript Object Notation (JSON).</span></span> <span data-ttu-id="ef9ee-104">Bir Web tarayıcısı istemcisinden JavaScript kodu kullanarak bir AJAX hizmetine erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ef9ee-104">You can access an AJAX service by using JavaScript code from a Web browser client.</span></span> <span data-ttu-id="ef9ee-105">Bu örnek, [temel Ajax hizmet](basic-ajax-service.md) örneğinde oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="ef9ee-105">This sample builds on the [Basic AJAX Service](basic-ajax-service.md) sample.</span></span>

<span data-ttu-id="ef9ee-106">WCF 'de AJAX desteği, ASP.NET AJAX ile denetim aracılığıyla kullanılmak üzere iyileştirilmiştir <xref:System.Web.UI.ScriptManager> .</span><span class="sxs-lookup"><span data-stu-id="ef9ee-106">AJAX support in WCF is optimized for use with ASP.NET AJAX through the <xref:System.Web.UI.ScriptManager> control.</span></span> <span data-ttu-id="ef9ee-107">WCF 'yi ASP.NET AJAX ile kullanmayla ilgili bir örnek için bkz. [Ajax örnekleri](ajax.md).</span><span class="sxs-lookup"><span data-stu-id="ef9ee-107">For an example of using WCF with ASP.NET AJAX, see the [AJAX Samples](ajax.md).</span></span>

> [!NOTE]
> <span data-ttu-id="ef9ee-108">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="ef9ee-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="ef9ee-109">Aşağıdaki örnekteki hizmet, AJAX 'a özgü kod içermeyen bir WCF hizmetidir.</span><span class="sxs-lookup"><span data-stu-id="ef9ee-109">The service in the following sample is a WCF service with no AJAX-specific code.</span></span> <span data-ttu-id="ef9ee-110"><xref:System.ServiceModel.Web.WebGetAttribute>Özniteliği uygulanmadığından, varsayılan http fiili ("Post") kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ef9ee-110">Because the <xref:System.ServiceModel.Web.WebGetAttribute> attribute is not applied, the default HTTP verb ("POST") is used.</span></span> <span data-ttu-id="ef9ee-111">Hizmette, `DoMath` adlı bir karmaşık tür döndüren bir işlem vardır `MathResult` .</span><span class="sxs-lookup"><span data-stu-id="ef9ee-111">The service has one operation, `DoMath`, which returns a complex type named `MathResult`.</span></span> <span data-ttu-id="ef9ee-112">Karmaşık tür, AJAX 'a özgü kod içermeyen standart bir veri anlaşması türüdür.</span><span class="sxs-lookup"><span data-stu-id="ef9ee-112">The complex type is a standard data contract type, which also contains no AJAX-specific code.</span></span>

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

<span data-ttu-id="ef9ee-113">Temel AJAX hizmet örneğinde olduğu gibi, kullanarak hizmette bir AJAX uç noktası oluşturun <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> .</span><span class="sxs-lookup"><span data-stu-id="ef9ee-113">Create an AJAX endpoint on the service by using the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, just as in the Basic AJAX Service sample.</span></span>

<span data-ttu-id="ef9ee-114">ComplexTypeClientPage. aspx istemci Web sayfası, Kullanıcı sayfadaki **hesaplamayı gerçekleştir** düğmesine tıkladığında hizmeti çağırmak için ASP.net ve JavaScript kodunu içerir.</span><span class="sxs-lookup"><span data-stu-id="ef9ee-114">The client Web page ComplexTypeClientPage.aspx contains ASP.NET and JavaScript code to invoke the service when the user clicks the **Perform calculation** button on the page.</span></span> <span data-ttu-id="ef9ee-115">Hizmeti çağırmak için kod bir JSON gövdesi oluşturur ve http post örneği [kullanılarak Ajax hizmetine](ajax-service-using-http-post.md) benzer şekılde http post kullanarak gönderir.</span><span class="sxs-lookup"><span data-stu-id="ef9ee-115">The code to invoke the service constructs a JSON body and sends it using HTTP POST, similar to the [AJAX Service Using HTTP POST](ajax-service-using-http-post.md) sample.</span></span>

<span data-ttu-id="ef9ee-116">Hizmet çağrısı başarılı olduktan sonra, `sum` `difference` `product` `quotient` sonuçta elde edilen JavaScript nesnesine bireysel veri üyelerine (,, ve) erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ef9ee-116">After the service call succeeds, you can access the individual data members (`sum`, `difference`, `product` and `quotient`) on the resulting JavaScript object.</span></span>

```javascript
function onSuccess(mathResult){
     document.getElementById("sum").value = mathResult.sum;
     document.getElementById("difference").value = mathResult.difference;
     document.getElementById("product").value = mathResult.product;
     document.getElementById("quotient").value = mathResult.quotient;
}
```

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ef9ee-117">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="ef9ee-117">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="ef9ee-118">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="ef9ee-118">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="ef9ee-119">[Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)bölümünde açıklandığı gibi ComplexTypeAjaxService. sln çözümünü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ef9ee-119">Build the solution ComplexTypeAjaxService.sln as described in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

3. <span data-ttu-id="ef9ee-120">`http://localhost/ServiceModelSamples/ComplexTypeClientPage.aspx`(ComplexTypeClientPage. aspx ' i tarayıcıda proje dizininden açmayın) bölümüne gidin.</span><span class="sxs-lookup"><span data-stu-id="ef9ee-120">Navigate to `http://localhost/ServiceModelSamples/ComplexTypeClientPage.aspx` (do not open ComplexTypeClientPage.aspx in the browser from the project directory).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ef9ee-121">Örnekler bilgisayarınızda zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="ef9ee-121">The samples may already be installed on your computer.</span></span> <span data-ttu-id="ef9ee-122">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="ef9ee-122">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="ef9ee-123">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="ef9ee-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ef9ee-124">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="ef9ee-124">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\ComplexTypeAjaxService`

## <a name="see-also"></a><span data-ttu-id="ef9ee-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ef9ee-125">See also</span></span>

- [<span data-ttu-id="ef9ee-126">Temel AJAX Hizmeti</span><span class="sxs-lookup"><span data-stu-id="ef9ee-126">Basic AJAX Service</span></span>](basic-ajax-service.md)
