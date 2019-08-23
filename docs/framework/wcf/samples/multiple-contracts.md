---
title: Birden Fazla Sözleşme
ms.date: 03/30/2017
ms.assetid: 2bef319b-fe9c-4d49-ac6c-dfb23eb35099
ms.openlocfilehash: 39970f9f0aefa46c3d064b39c9b35d195ef22843
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69930357"
---
# <a name="multiple-contracts"></a><span data-ttu-id="f6ac4-102">Birden Fazla Sözleşme</span><span class="sxs-lookup"><span data-stu-id="f6ac4-102">Multiple Contracts</span></span>
<span data-ttu-id="f6ac4-103">Birden çok sözleşme örneği, bir hizmette birden fazla sözleşmenin nasıl uygulanacağını ve uygulanan sözleşmelerin her biriyle iletişim kurmak için uç noktaların nasıl yapılandırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="f6ac4-103">The Multiple Contracts sample demonstrates how to implement more than one contract on a service and how to configure endpoints for communicating with each of the implemented contracts.</span></span> <span data-ttu-id="f6ac4-104">Bu örnek, [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md)' i temel alır.</span><span class="sxs-lookup"><span data-stu-id="f6ac4-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span> <span data-ttu-id="f6ac4-105">Hizmet iki sözleşme, `ICalculator` sözleşme `ICalculatorSession` ve sözleşme tanımlamak üzere değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="f6ac4-105">The service has been modified to define two contracts, the `ICalculator` contract and the `ICalculatorSession` contract.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f6ac4-106">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="f6ac4-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="f6ac4-107">Hizmet sınıfı hem hem de `ICalculator` `ICalculatorSession` sözleşmelerini uygular.</span><span class="sxs-lookup"><span data-stu-id="f6ac4-107">The service class implements both the `ICalculator` and `ICalculatorSession` contracts.</span></span> <span data-ttu-id="f6ac4-108">Sözleşmelerden biri bir oturum gerektirdiğinden hizmet, oturumun kullanım ömrü boyunca durumu <xref:System.ServiceModel.InstanceContextMode.PerSession> korumak için örnek modunu kullanır.</span><span class="sxs-lookup"><span data-stu-id="f6ac4-108">Because one of the contracts requires a session, the service uses the <xref:System.ServiceModel.InstanceContextMode.PerSession> instance mode to maintain the state over the lifetime of the session.</span></span>  
  
 <span data-ttu-id="f6ac4-109">Hizmet yapılandırması, her sözleşmeyi göstermek için iki uç nokta tanımlamak üzere değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="f6ac4-109">The service configuration has been modified to define two endpoints to expose each contract.</span></span> <span data-ttu-id="f6ac4-110">Uç nokta, `basicHttpBinding`kullanarak temel adreste gösterilir. `ICalculator`</span><span class="sxs-lookup"><span data-stu-id="f6ac4-110">The `ICalculator` endpoint is exposed at the base address using a `basicHttpBinding`.</span></span> <span data-ttu-id="f6ac4-111">Uç nokta, aşağıdaki örnek yapılandırmada gösterildiği gibi `bindingConfiguration` , özniteliği olarak `wsHttpBinding` `BindingWithSession`ayarlanmış bir ile kullanılarak BaseAddress/Session üzerinde gösterilir. `ICalculatorSession`</span><span class="sxs-lookup"><span data-stu-id="f6ac4-111">The `ICalculatorSession` endpoint is exposed at the baseaddress/session using a `wsHttpBinding` with the `bindingConfiguration` attribute set to `BindingWithSession`, as shown in the following sample configuration.</span></span>  
  
```xml  
<service   
    name="Microsoft.ServiceModel.Samples.CalculatorService"  
    behaviorConfiguration="CalculatorServiceBehavior">  
  <!-- ICalculator endpoint is exposed using BasicBinding at the base  
       address provided by host:   
       http://localhost/servicemodelsamples/service.svc  -->  
  <endpoint address=""  
            binding="basicHttpBinding"  
            contract="Microsoft.ServiceModel.Samples.ICalculator" />  
  <!-- ICalculatorSession endpoint is exposed using BindingWithSession  
       at {baseaddress}/session:  
       http://localhost/servicemodelsamples/service.svc/session -->  
  <endpoint address="session"  
            binding="wsHttpBinding"  
            bindingConfiguration="BindingWithSession"   
           contract="Microsoft.ServiceModel.Samples.ICalculatorSession" />  
  ...  
</service>  
```  
  
 <span data-ttu-id="f6ac4-112">Oluşturulan istemci kodu artık özgün `ICalculator` sözleşme ve yeni `ICalculatorSession` sözleşme için bir istemci sınıfı içerir.</span><span class="sxs-lookup"><span data-stu-id="f6ac4-112">The generated client code now includes a client class for both the original `ICalculator` contract and the new `ICalculatorSession` contract.</span></span> <span data-ttu-id="f6ac4-113">İstemci yapılandırması ve kodu, uygun hizmet uç noktasındaki her bir sözleşmeyle iletişim kuracak şekilde değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="f6ac4-113">The client configuration and code have been modified to communicate with each contract at the appropriate service endpoint.</span></span>  
  
 <span data-ttu-id="f6ac4-114">İstemci bir konsol Windows uygulaması (. exe).</span><span class="sxs-lookup"><span data-stu-id="f6ac4-114">The client is a console windows application (.exe).</span></span> <span data-ttu-id="f6ac4-115">Hizmet, Internet Information Services (IIS) tarafından barındırılır.</span><span class="sxs-lookup"><span data-stu-id="f6ac4-115">The service is hosted by Internet Information Services (IIS).</span></span>  
  
 <span data-ttu-id="f6ac4-116">İstemci konsolu penceresinde, ilk uç nokta, ardından güvenli uç nokta gelen uç noktalara gönderilen işlemler görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="f6ac4-116">The client console window displays the operations sent to each of the endpoints, first the basic endpoint, followed by the secure endpoint.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="f6ac4-117">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="f6ac4-117">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="f6ac4-118">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="f6ac4-118">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="f6ac4-119">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="f6ac4-119">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="f6ac4-120">Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="f6ac4-120">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f6ac4-121">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="f6ac4-121">The samples may already be installed on your machine.</span></span> <span data-ttu-id="f6ac4-122">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="f6ac4-122">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="f6ac4-123">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ' e gidin.</span><span class="sxs-lookup"><span data-stu-id="f6ac4-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f6ac4-124">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="f6ac4-124">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\MultipleContracts`  
