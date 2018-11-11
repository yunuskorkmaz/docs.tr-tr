---
title: Açılmamış İletiler
ms.date: 03/30/2017
ms.assetid: 019657bd-1f9b-4315-ad74-eaa4e7551ff6
ms.openlocfilehash: 835312101ba9e0daaa7986a78c9a0040535881b9
ms.sourcegitcommit: 5fd80619c760fa8c25d33a6f5661247cb65da465
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2018
ms.locfileid: "50743948"
---
# <a name="unwrapped-messages"></a><span data-ttu-id="84ec5-102">Açılmamış İletiler</span><span class="sxs-lookup"><span data-stu-id="84ec5-102">Unwrapped Messages</span></span>
<span data-ttu-id="84ec5-103">Açılmamış iletiler bu örnek gösterir.</span><span class="sxs-lookup"><span data-stu-id="84ec5-103">This sample demonstrates unwrapped messages.</span></span> <span data-ttu-id="84ec5-104">Varsayılan olarak, ileti gövdesi, bir hizmet işlemi parametreleri sarmalanmış şekilde biçimlendirilir.</span><span class="sxs-lookup"><span data-stu-id="84ec5-104">By default, the message body is formatted such that the parameters to a service operation are wrapped.</span></span> <span data-ttu-id="84ec5-105">Aşağıdaki örnekte gösterildiği bir `Add` istek iletisi `ICalculator` Sarmalanan modunda hizmet.</span><span class="sxs-lookup"><span data-stu-id="84ec5-105">The following sample shows an `Add` request message to the `ICalculator` service in wrapped mode.</span></span>  
  
```xml  
<s:Envelope   
    xmlns:s=http://www.w3.org/2003/05/soap-envelope  
    xmlns:a="http://schemas.xmlsoap.org/ws/2005/08/addressing">  
    <s:Header>  
        …  
    </s:Header>  
    <s:Body>  
      <Add xmlns="http://Microsoft.ServiceModel.Samples">  
        <n1>100</n1>  
        <n2>15.99</n2>  
      </Add>  
    </s:Body>  
</s:Envelope>  
```  
  
 <span data-ttu-id="84ec5-106">`<Add>` İleti gövdesinde öğesini sarmalar `n1` ve `n2` parametreleri.</span><span class="sxs-lookup"><span data-stu-id="84ec5-106">The `<Add>` element in the message body wraps the `n1` and `n2` parameters.</span></span> <span data-ttu-id="84ec5-107">Buna karşılık, aşağıdaki örnek sarmalanmış halden modunda eşdeğer iletiyi gösterir.</span><span class="sxs-lookup"><span data-stu-id="84ec5-107">In contrast, the following sample shows the equivalent message in the unwrapped mode.</span></span>  
  
```xml  
<s:Envelope   
    xmlns:s="http://www.w3.org/2003/05/soap-envelope"   
    xmlns:a="http://schemas.xmlsoap.org/ws/2005/08/addressing">  
    <s:Header>  
        ….  
    </s:Header>  
    <s:Body>  
      <n1 xmlns="http://Microsoft.ServiceModel.Samples">100</n1>  
      <n2 xmlns="http://Microsoft.ServiceModel.Samples">15.99</n2>  
    </s:Body>  
  </s:Envelope>  
</MessageLogTraceRecord>  
```  
  
 <span data-ttu-id="84ec5-108">Açılmış neden olan iletiyi değil sarmalamak `n1` ve `n2` parametreleri içeren bir öğesinde oldukları soap gövdesi öğesinin doğrudan alt öğeleri.</span><span class="sxs-lookup"><span data-stu-id="84ec5-108">The unwrapped message does not wrap the `n1` and `n2` parameters in a containing element, they are direct children of the soap body element.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="84ec5-109">Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="84ec5-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="84ec5-110">Bu örnekte, sarmalanmış halden iletisine uygulanarak oluşturulan <xref:System.ServiceModel.MessageContractAttribute> hizmet işlemi parametre türü ve aşağıdaki örnek kodda gösterildiği gibi dönüş değeri türü.</span><span class="sxs-lookup"><span data-stu-id="84ec5-110">In this sample, an unwrapped message is created by applying the <xref:System.ServiceModel.MessageContractAttribute> to the service operation parameter type and return value type as shown in the following sample code.</span></span>  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract]  
    ResponseMessage Add(RequestMessage request);  
    [OperationContract]  
    ResponseMessage Subtract(RequestMessage request);  
    [OperationContract]  
    ResponseMessage Multiply(RequestMessage request);  
    [OperationContract]  
    ResponseMessage Divide(RequestMessage request);  
}  
  
//setting IsWrapped to false means the n1 and n2  
//members will be direct children of the soap body element  
[MessageContract(IsWrapped = false)]  
public class RequestMessage  
{  
    [MessageBodyMember]  
    private double n1;  
    [MessageBodyMember]  
    private double n2;  
    //…  
}  
  
//setting IsWrapped to false means the result  
//member will be a direct child of the soap body element  
[MessageContract(IsWrapped = false)]  
public class ResponseMessage  
{  
    [MessageBodyMember]  
    private double result;  
    //…  
}  
```  
  
 <span data-ttu-id="84ec5-111">Gönderilen ve alınan iletileri görmek, izin vermek için bu örnek izlemeyi kullanır.</span><span class="sxs-lookup"><span data-stu-id="84ec5-111">To allow you to see the messages being sent and received, this sample uses tracing.</span></span> <span data-ttu-id="84ec5-112">Ayrıca, <xref:System.ServiceModel.WSHttpBinding> kaydeder iletilerin sayısını azaltmak için daha fazla güvenlik yapılandırıldı.</span><span class="sxs-lookup"><span data-stu-id="84ec5-112">In addition, the <xref:System.ServiceModel.WSHttpBinding> has been configured without security, to reduce the number of messages it logs.</span></span>  
  
 <span data-ttu-id="84ec5-113">Sonuçta elde edilen izleme günlüğü (c:\logs\Message.log) kullanılarak görüntülenebilir [hizmet izleme Görüntüleyicisi aracı (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).</span><span class="sxs-lookup"><span data-stu-id="84ec5-113">The resulting trace log (c:\logs\Message.log) can be viewed by using the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).</span></span> <span data-ttu-id="84ec5-114">İleti içeriği görüntülemek için seçin **iletileri** sol ve sağ bölmeleri hizmet izleme Görüntüleyicisi aracı.</span><span class="sxs-lookup"><span data-stu-id="84ec5-114">To view message contents, select **Messages** in both the left and the right panes of the Service Trace Viewer tool.</span></span> <span data-ttu-id="84ec5-115">Bu örnekte izleme günlükleri C:\LOGS klasöre oluşturulacak yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="84ec5-115">Trace logs in this sample are configured to be generated into the C:\LOGS folder.</span></span> <span data-ttu-id="84ec5-116">Bu klasör örneği çalıştırmadan önce oluşturun ve ağ hizmeti yazma izinleri bu dizin için kullanıcı verin.</span><span class="sxs-lookup"><span data-stu-id="84ec5-116">Create this folder before running the sample and give the user Network Service write permissions for this directory.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="84ec5-117">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="84ec5-117">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="84ec5-118">Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="84ec5-118">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="84ec5-119">Günlük iletileri için bir C:\LOGS dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="84ec5-119">Create a C:\LOGS directory for logging messages.</span></span> <span data-ttu-id="84ec5-120">Ağ hizmeti yazma izinleri bu dizin için kullanıcıya sağlayın.</span><span class="sxs-lookup"><span data-stu-id="84ec5-120">Give the user Network Service write permissions for this directory.</span></span>  
  
3.  <span data-ttu-id="84ec5-121">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="84ec5-121">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="84ec5-122">Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="84ec5-122">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="84ec5-123">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="84ec5-123">The samples may already be installed on your machine.</span></span> <span data-ttu-id="84ec5-124">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="84ec5-124">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="84ec5-125">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="84ec5-125">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="84ec5-126">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="84ec5-126">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\Unwrapped`  
  
## <a name="see-also"></a><span data-ttu-id="84ec5-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="84ec5-127">See Also</span></span>
