---
title: "Açılmamış İletiler"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 019657bd-1f9b-4315-ad74-eaa4e7551ff6
caps.latest.revision: "22"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 99aa1d00c2992842a7019d4f4fc4aa98c25f644a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="unwrapped-messages"></a><span data-ttu-id="37f58-102">Açılmamış İletiler</span><span class="sxs-lookup"><span data-stu-id="37f58-102">Unwrapped Messages</span></span>
<span data-ttu-id="37f58-103">Bu örnek açılmamış iletiler gösterir.</span><span class="sxs-lookup"><span data-stu-id="37f58-103">This sample demonstrates unwrapped messages.</span></span> <span data-ttu-id="37f58-104">Bir hizmet işlemi parametreleri kaydırılmış şekilde varsayılan olarak, ileti gövdesi olarak biçimlendirilir.</span><span class="sxs-lookup"><span data-stu-id="37f58-104">By default, the message body is formatted such that the parameters to a service operation are wrapped.</span></span> <span data-ttu-id="37f58-105">Aşağıdaki örnekte gösterildiği bir `Add` İstek iletisini `ICalculator` Sarmalanan modda hizmet.</span><span class="sxs-lookup"><span data-stu-id="37f58-105">The following sample shows an `Add` request message to the `ICalculator` service in wrapped mode.</span></span>  
  
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
  
 <span data-ttu-id="37f58-106">`<Add>` İleti gövdesi öğesinde sarmalar `n1` ve `n2` parametreleri.</span><span class="sxs-lookup"><span data-stu-id="37f58-106">The `<Add>` element in the message body wraps the `n1` and `n2` parameters.</span></span> <span data-ttu-id="37f58-107">Buna karşılık, aşağıdaki örnek, sarmalanmamış modunda eşdeğer iletisi gösterir.</span><span class="sxs-lookup"><span data-stu-id="37f58-107">In contrast, the following sample shows the equivalent message in the unwrapped mode.</span></span>  
  
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
  
 <span data-ttu-id="37f58-108">Sarmalanmamış iletiyi sarmalamak değil `n1` ve `n2` parametreleri içeren bir öğesinde oldukları soap gövdesi öğenin doğrudan alt öğeleri.</span><span class="sxs-lookup"><span data-stu-id="37f58-108">The unwrapped message does not wrap the `n1` and `n2` parameters in a containing element, they are direct children of the soap body element.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="37f58-109">Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="37f58-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="37f58-110">Bu örnekte, sarmalanmamış bir ileti uygulanarak oluşturulan <xref:System.ServiceModel.MessageContractAttribute> hizmet işlemi parametresi türü ve aşağıdaki örnek kodda gösterildiği gibi dönüş değeri türü.</span><span class="sxs-lookup"><span data-stu-id="37f58-110">In this sample, an unwrapped message is created by applying the <xref:System.ServiceModel.MessageContractAttribute> to the service operation parameter type and return value type as shown in the following sample code.</span></span>  
  
```  
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
  
 <span data-ttu-id="37f58-111">Gönderilen ve alınan iletileri görmenize olanak sağlamak için bu örnek izleme kullanır.</span><span class="sxs-lookup"><span data-stu-id="37f58-111">To allow you to see the messages being sent and received, this sample uses tracing.</span></span> <span data-ttu-id="37f58-112">Ayrıca, <xref:System.ServiceModel.WSHttpBinding> Bu günlükleri iletilerin sayısını azaltmak için güvenlik yapılandırıldı.</span><span class="sxs-lookup"><span data-stu-id="37f58-112">In addition, the <xref:System.ServiceModel.WSHttpBinding> has been configured without security, to reduce the number of messages it logs.</span></span>  
  
 <span data-ttu-id="37f58-113">Sonuçta elde edilen izleme günlüğü (c:\logs\Message.log) kullanarak görüntülenebilir [hizmet izleme Görüntüleyicisi aracı (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).</span><span class="sxs-lookup"><span data-stu-id="37f58-113">The resulting trace log (c:\logs\Message.log) can be viewed by using the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).</span></span> <span data-ttu-id="37f58-114">İleti içeriğini görüntülemek için seçin **iletileri** sol ve sağ bölmeleri hizmet izleme Görüntüleyicisi aracı.</span><span class="sxs-lookup"><span data-stu-id="37f58-114">To view message contents, select **Messages** in both the left and the right panes of the Service Trace Viewer tool.</span></span> <span data-ttu-id="37f58-115">Bu örnekte izleme günlükleri C:\LOGS klasörüne oluşturulacak şekilde yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="37f58-115">Trace logs in this sample are configured to be generated into the C:\LOGS folder.</span></span> <span data-ttu-id="37f58-116">Örneği çalıştırmadan önce bu klasörü oluşturun ve kullanıcının ağ hizmeti yazmasına bu dizin için izin verin.</span><span class="sxs-lookup"><span data-stu-id="37f58-116">Create this folder before running the sample and give the user Network Service write permissions for this directory.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="37f58-117">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="37f58-117">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="37f58-118">Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="37f58-118">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="37f58-119">Günlük iletileri için C:\LOGS dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="37f58-119">Create a C:\LOGS directory for logging messages.</span></span> <span data-ttu-id="37f58-120">Ağ hizmeti yazma izinleri bu dizin için kullanıcı verin.</span><span class="sxs-lookup"><span data-stu-id="37f58-120">Give the user Network Service write permissions for this directory.</span></span>  
  
3.  <span data-ttu-id="37f58-121">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="37f58-121">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="37f58-122">Tek veya çapraz makine yapılandırmada örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="37f58-122">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="37f58-123">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="37f58-123">The samples may already be installed on your machine.</span></span> <span data-ttu-id="37f58-124">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="37f58-124">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="37f58-125">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="37f58-125">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="37f58-126">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="37f58-126">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\Unwrapped`  
  
## <a name="see-also"></a><span data-ttu-id="37f58-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="37f58-127">See Also</span></span>
