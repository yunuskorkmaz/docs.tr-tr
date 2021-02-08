---
description: 'Daha fazla bilgi edinin: karmaşık türler kullanan AJAX hizmeti örneği'
title: Karmaşık Türler Kullanan AJAX Hizmeti Örneği
ms.date: 03/30/2017
ms.assetid: 88242b99-4811-4cbe-8201-52ddf48fb174
ms.openlocfilehash: 438bceb91f10f5ba91d02272d2ba266a50a05f82
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99779133"
---
# <a name="ajax-service-using-complex-types-sample"></a><span data-ttu-id="ae7ee-103">Karmaşık Türler Kullanan AJAX Hizmeti Örneği</span><span class="sxs-lookup"><span data-stu-id="ae7ee-103">AJAX Service Using Complex Types Sample</span></span>

<span data-ttu-id="ae7ee-104">Bu örnek, karmaşık türlerin örneklerini oluşturan ve bunları JavaScript Nesne Gösterimi (JSON) olarak hizmet ve istemci arasında gönderen bir ASP.NET zaman uyumsuz JavaScript ve XML (AJAX) hizmeti oluşturmak için Windows Communication Foundation (WCF) öğesinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ae7ee-104">This sample demonstrates how to use Windows Communication Foundation (WCF) to create an ASP.NET Asynchronous JavaScript and XML (AJAX) service that creates instances of complex types and sends them between service and client as JavaScript Object Notation (JSON).</span></span> <span data-ttu-id="ae7ee-105">Bir Web tarayıcısı istemcisinden JavaScript kodu kullanarak bir AJAX hizmetine erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ae7ee-105">You can access an AJAX service by using JavaScript code from a Web browser client.</span></span> <span data-ttu-id="ae7ee-106">Bu örnek, [temel Ajax hizmet](basic-ajax-service.md) örneğinde oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="ae7ee-106">This sample builds on the [Basic AJAX Service](basic-ajax-service.md) sample.</span></span>

<span data-ttu-id="ae7ee-107">WCF 'de AJAX desteği, ASP.NET AJAX ile denetim aracılığıyla kullanılmak üzere iyileştirilmiştir <xref:System.Web.UI.ScriptManager> .</span><span class="sxs-lookup"><span data-stu-id="ae7ee-107">AJAX support in WCF is optimized for use with ASP.NET AJAX through the <xref:System.Web.UI.ScriptManager> control.</span></span> <span data-ttu-id="ae7ee-108">WCF 'yi ASP.NET AJAX ile kullanmayla ilgili bir örnek için bkz. [Ajax örnekleri](ajax.md).</span><span class="sxs-lookup"><span data-stu-id="ae7ee-108">For an example of using WCF with ASP.NET AJAX, see the [AJAX Samples](ajax.md).</span></span>

> [!NOTE]
> <span data-ttu-id="ae7ee-109">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="ae7ee-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="ae7ee-110">Aşağıdaki örnekteki hizmet, AJAX 'a özgü kod içermeyen bir WCF hizmetidir.</span><span class="sxs-lookup"><span data-stu-id="ae7ee-110">The service in the following sample is a WCF service with no AJAX-specific code.</span></span> <span data-ttu-id="ae7ee-111"><xref:System.ServiceModel.Web.WebGetAttribute>Özniteliği uygulanmadığından, varsayılan http fiili ("Post") kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ae7ee-111">Because the <xref:System.ServiceModel.Web.WebGetAttribute> attribute is not applied, the default HTTP verb ("POST") is used.</span></span> <span data-ttu-id="ae7ee-112">Hizmette, `DoMath` adlı bir karmaşık tür döndüren bir işlem vardır `MathResult` .</span><span class="sxs-lookup"><span data-stu-id="ae7ee-112">The service has one operation, `DoMath`, which returns a complex type named `MathResult`.</span></span> <span data-ttu-id="ae7ee-113">Karmaşık tür, AJAX 'a özgü kod içermeyen standart bir veri anlaşması türüdür.</span><span class="sxs-lookup"><span data-stu-id="ae7ee-113">The complex type is a standard data contract type, which also contains no AJAX-specific code.</span></span>

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

<span data-ttu-id="ae7ee-114">Temel AJAX hizmet örneğinde olduğu gibi, kullanarak hizmette bir AJAX uç noktası oluşturun <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> .</span><span class="sxs-lookup"><span data-stu-id="ae7ee-114">Create an AJAX endpoint on the service by using the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, just as in the Basic AJAX Service sample.</span></span>

<span data-ttu-id="ae7ee-115">ComplexTypeClientPage. aspx istemci Web sayfası, Kullanıcı sayfadaki **hesaplamayı gerçekleştir** düğmesine tıkladığında hizmeti çağırmak için ASP.net ve JavaScript kodunu içerir.</span><span class="sxs-lookup"><span data-stu-id="ae7ee-115">The client Web page ComplexTypeClientPage.aspx contains ASP.NET and JavaScript code to invoke the service when the user clicks the **Perform calculation** button on the page.</span></span> <span data-ttu-id="ae7ee-116">Hizmeti çağırmak için kod bir JSON gövdesi oluşturur ve http post örneği [kullanılarak Ajax hizmetine](ajax-service-using-http-post.md) benzer şekılde http post kullanarak gönderir.</span><span class="sxs-lookup"><span data-stu-id="ae7ee-116">The code to invoke the service constructs a JSON body and sends it using HTTP POST, similar to the [AJAX Service Using HTTP POST](ajax-service-using-http-post.md) sample.</span></span>

<span data-ttu-id="ae7ee-117">Hizmet çağrısı başarılı olduktan sonra, `sum` `difference` `product` `quotient` sonuçta elde edilen JavaScript nesnesine bireysel veri üyelerine (,, ve) erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ae7ee-117">After the service call succeeds, you can access the individual data members (`sum`, `difference`, `product` and `quotient`) on the resulting JavaScript object.</span></span>

```javascript
function onSuccess(mathResult){
     document.getElementById("sum").value = mathResult.sum;
     document.getElementById("difference").value = mathResult.difference;
     document.getElementById("product").value = mathResult.product;
     document.getElementById("quotient").value = mathResult.quotient;
}
```

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ae7ee-118">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="ae7ee-118">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="ae7ee-119">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="ae7ee-119">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="ae7ee-120">[Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)bölümünde açıklandığı gibi ComplexTypeAjaxService. sln çözümünü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ae7ee-120">Build the solution ComplexTypeAjaxService.sln as described in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

3. <span data-ttu-id="ae7ee-121">`http://localhost/ServiceModelSamples/ComplexTypeClientPage.aspx`(ComplexTypeClientPage. aspx ' i tarayıcıda proje dizininden açmayın) bölümüne gidin.</span><span class="sxs-lookup"><span data-stu-id="ae7ee-121">Navigate to `http://localhost/ServiceModelSamples/ComplexTypeClientPage.aspx` (do not open ComplexTypeClientPage.aspx in the browser from the project directory).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ae7ee-122">Örnekler bilgisayarınızda zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="ae7ee-122">The samples may already be installed on your computer.</span></span> <span data-ttu-id="ae7ee-123">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="ae7ee-123">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="ae7ee-124">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="ae7ee-124">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ae7ee-125">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="ae7ee-125">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\ComplexTypeAjaxService`

## <a name="see-also"></a><span data-ttu-id="ae7ee-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ae7ee-126">See also</span></span>

- [<span data-ttu-id="ae7ee-127">Temel AJAX Hizmeti</span><span class="sxs-lookup"><span data-stu-id="ae7ee-127">Basic AJAX Service</span></span>](basic-ajax-service.md)
