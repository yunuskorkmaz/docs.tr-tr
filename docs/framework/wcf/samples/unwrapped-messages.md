---
title: Açılmamış İletiler
ms.date: 03/30/2017
ms.assetid: 019657bd-1f9b-4315-ad74-eaa4e7551ff6
ms.openlocfilehash: ea90a6355f63d5fffd0cc3c5d350f83e395c31c5
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84591091"
---
# <a name="unwrapped-messages"></a><span data-ttu-id="5b41e-102">Açılmamış İletiler</span><span class="sxs-lookup"><span data-stu-id="5b41e-102">Unwrapped Messages</span></span>
<span data-ttu-id="5b41e-103">Bu örnek sarmalanmamış iletileri gösterir.</span><span class="sxs-lookup"><span data-stu-id="5b41e-103">This sample demonstrates unwrapped messages.</span></span> <span data-ttu-id="5b41e-104">Varsayılan olarak, ileti gövdesi bir hizmet işlemine ait parametrelerin sarmalanması için biçimlendirilir.</span><span class="sxs-lookup"><span data-stu-id="5b41e-104">By default, the message body is formatted such that the parameters to a service operation are wrapped.</span></span> <span data-ttu-id="5b41e-105">Aşağıdaki örnek, `Add` `ICalculator` Sarmalanan modda hizmete bir istek iletisi gösterir.</span><span class="sxs-lookup"><span data-stu-id="5b41e-105">The following sample shows an `Add` request message to the `ICalculator` service in wrapped mode.</span></span>  
  
```xml  
<s:Envelope
    xmlns:s="http://www.w3.org/2003/05/soap-envelope"  
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
  
 <span data-ttu-id="5b41e-106">`<Add>`İleti gövdesindeki öğesi `n1` ve parametrelerini sarmalar `n2` .</span><span class="sxs-lookup"><span data-stu-id="5b41e-106">The `<Add>` element in the message body wraps the `n1` and `n2` parameters.</span></span> <span data-ttu-id="5b41e-107">Buna karşılık aşağıdaki örnek, sarmalanmamış moddaki denk iletiyi gösterir.</span><span class="sxs-lookup"><span data-stu-id="5b41e-107">In contrast, the following sample shows the equivalent message in the unwrapped mode.</span></span>  
  
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
```  
  
 <span data-ttu-id="5b41e-108">Sarmalanmamış ileti, `n1` ve `n2` parametrelerini kapsayan bir öğede sarmalamaz, bunlar soap body öğesinin doğrudan alt öğesidir.</span><span class="sxs-lookup"><span data-stu-id="5b41e-108">The unwrapped message does not wrap the `n1` and `n2` parameters in a containing element, they are direct children of the soap body element.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5b41e-109">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="5b41e-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="5b41e-110">Bu örnekte, <xref:System.ServiceModel.MessageContractAttribute> Aşağıdaki örnek kodda gösterildiği gibi hizmet işlemi parametre türüne ve dönüş değeri türüne uygulanarak sarmalanmamış bir ileti oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="5b41e-110">In this sample, an unwrapped message is created by applying the <xref:System.ServiceModel.MessageContractAttribute> to the service operation parameter type and return value type as shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="5b41e-111">Gönderilen ve alınan iletileri görmenizi sağlamak için bu örnek izleme kullanır.</span><span class="sxs-lookup"><span data-stu-id="5b41e-111">To allow you to see the messages being sent and received, this sample uses tracing.</span></span> <span data-ttu-id="5b41e-112">Buna ek olarak, <xref:System.ServiceModel.WSHttpBinding> günlüğe kaydettiği ileti sayısını azaltmak için güvenlik olmadan yapılandırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="5b41e-112">In addition, the <xref:System.ServiceModel.WSHttpBinding> has been configured without security, to reduce the number of messages it logs.</span></span>  
  
 <span data-ttu-id="5b41e-113">Elde edilen izleme günlüğü (c:\logs\Message.log), [hizmet Izleme Görüntüleyicisi Aracı (SvcTraceViewer. exe)](../service-trace-viewer-tool-svctraceviewer-exe.md)kullanılarak görüntülenebilir.</span><span class="sxs-lookup"><span data-stu-id="5b41e-113">The resulting trace log (c:\logs\Message.log) can be viewed by using the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md).</span></span> <span data-ttu-id="5b41e-114">İleti içeriğini görüntülemek için, hizmet Izleme Görüntüleyicisi aracının sol ve sağ bölmelerinde **iletiler** ' i seçin.</span><span class="sxs-lookup"><span data-stu-id="5b41e-114">To view message contents, select **Messages** in both the left and the right panes of the Service Trace Viewer tool.</span></span> <span data-ttu-id="5b41e-115">Bu örnekteki izleme günlükleri C:\LOGS klasöründe oluşturulacak şekilde yapılandırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="5b41e-115">Trace logs in this sample are configured to be generated into the C:\LOGS folder.</span></span> <span data-ttu-id="5b41e-116">Örneği çalıştırmadan önce bu klasörü oluşturun ve bu dizin için Kullanıcı ağ hizmetine yazma izinleri verin.</span><span class="sxs-lookup"><span data-stu-id="5b41e-116">Create this folder before running the sample and give the user Network Service write permissions for this directory.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="5b41e-117">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="5b41e-117">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="5b41e-118">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="5b41e-118">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="5b41e-119">İletileri günlüğe kaydetmek için bir C:\LOGS dizini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="5b41e-119">Create a C:\LOGS directory for logging messages.</span></span> <span data-ttu-id="5b41e-120">Bu dizin için Kullanıcı ağ hizmetine yazma izinleri verin.</span><span class="sxs-lookup"><span data-stu-id="5b41e-120">Give the user Network Service write permissions for this directory.</span></span>  
  
3. <span data-ttu-id="5b41e-121">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="5b41e-121">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="5b41e-122">Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="5b41e-122">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="5b41e-123">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="5b41e-123">The samples may already be installed on your machine.</span></span> <span data-ttu-id="5b41e-124">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="5b41e-124">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="5b41e-125">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="5b41e-125">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5b41e-126">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="5b41e-126">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\Unwrapped`  
