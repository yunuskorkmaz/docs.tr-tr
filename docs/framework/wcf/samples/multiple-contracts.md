---
description: 'Daha fazla bilgi edinin: birden çok sözleşme'
title: Birden Fazla Sözleşme
ms.date: 03/30/2017
ms.assetid: 2bef319b-fe9c-4d49-ac6c-dfb23eb35099
ms.openlocfilehash: b83a2d333cda05525fbe286f2eb6c385d7942092
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99752253"
---
# <a name="multiple-contracts"></a><span data-ttu-id="fff2f-103">Birden Fazla Sözleşme</span><span class="sxs-lookup"><span data-stu-id="fff2f-103">Multiple Contracts</span></span>

<span data-ttu-id="fff2f-104">Birden çok sözleşme örneği, bir hizmette birden fazla sözleşmenin nasıl uygulanacağını ve uygulanan sözleşmelerin her biriyle iletişim kurmak için uç noktaların nasıl yapılandırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="fff2f-104">The Multiple Contracts sample demonstrates how to implement more than one contract on a service and how to configure endpoints for communicating with each of the implemented contracts.</span></span> <span data-ttu-id="fff2f-105">Bu örnek, [Başlarken](getting-started-sample.md)' i temel alır.</span><span class="sxs-lookup"><span data-stu-id="fff2f-105">This sample is based on the [Getting Started](getting-started-sample.md).</span></span> <span data-ttu-id="fff2f-106">Hizmet iki sözleşme, `ICalculator` sözleşme ve sözleşme tanımlamak üzere değiştirilmiştir `ICalculatorSession` .</span><span class="sxs-lookup"><span data-stu-id="fff2f-106">The service has been modified to define two contracts, the `ICalculator` contract and the `ICalculatorSession` contract.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fff2f-107">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="fff2f-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="fff2f-108">Hizmet sınıfı hem hem de `ICalculator` sözleşmelerini uygular `ICalculatorSession` .</span><span class="sxs-lookup"><span data-stu-id="fff2f-108">The service class implements both the `ICalculator` and `ICalculatorSession` contracts.</span></span> <span data-ttu-id="fff2f-109">Sözleşmelerden biri bir oturum gerektirdiğinden hizmet, <xref:System.ServiceModel.InstanceContextMode.PerSession> oturumun kullanım ömrü boyunca durumu korumak için örnek modunu kullanır.</span><span class="sxs-lookup"><span data-stu-id="fff2f-109">Because one of the contracts requires a session, the service uses the <xref:System.ServiceModel.InstanceContextMode.PerSession> instance mode to maintain the state over the lifetime of the session.</span></span>  
  
 <span data-ttu-id="fff2f-110">Hizmet yapılandırması, her sözleşmeyi göstermek için iki uç nokta tanımlamak üzere değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="fff2f-110">The service configuration has been modified to define two endpoints to expose each contract.</span></span> <span data-ttu-id="fff2f-111">`ICalculator`Uç nokta, kullanarak temel adreste gösterilir `basicHttpBinding` .</span><span class="sxs-lookup"><span data-stu-id="fff2f-111">The `ICalculator` endpoint is exposed at the base address using a `basicHttpBinding`.</span></span> <span data-ttu-id="fff2f-112">`ICalculatorSession`Uç nokta, `wsHttpBinding` `bindingConfiguration` `BindingWithSession` Aşağıdaki örnek yapılandırmada gösterildiği gibi, özniteliği olarak ayarlanmış bir ile kullanılarak BaseAddress/Session üzerinde gösterilir.</span><span class="sxs-lookup"><span data-stu-id="fff2f-112">The `ICalculatorSession` endpoint is exposed at the baseaddress/session using a `wsHttpBinding` with the `bindingConfiguration` attribute set to `BindingWithSession`, as shown in the following sample configuration.</span></span>  
  
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
  
 <span data-ttu-id="fff2f-113">Oluşturulan istemci kodu artık özgün `ICalculator` sözleşme ve yeni sözleşme için bir istemci sınıfı içerir `ICalculatorSession` .</span><span class="sxs-lookup"><span data-stu-id="fff2f-113">The generated client code now includes a client class for both the original `ICalculator` contract and the new `ICalculatorSession` contract.</span></span> <span data-ttu-id="fff2f-114">İstemci yapılandırması ve kodu, uygun hizmet uç noktasındaki her bir sözleşmeyle iletişim kuracak şekilde değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="fff2f-114">The client configuration and code have been modified to communicate with each contract at the appropriate service endpoint.</span></span>  
  
 <span data-ttu-id="fff2f-115">İstemci bir konsol Windows uygulaması (. exe).</span><span class="sxs-lookup"><span data-stu-id="fff2f-115">The client is a console windows application (.exe).</span></span> <span data-ttu-id="fff2f-116">Hizmet, Internet Information Services (IIS) tarafından barındırılır.</span><span class="sxs-lookup"><span data-stu-id="fff2f-116">The service is hosted by Internet Information Services (IIS).</span></span>  
  
 <span data-ttu-id="fff2f-117">İstemci konsolu penceresinde, ilk uç nokta, ardından güvenli uç nokta gelen uç noktalara gönderilen işlemler görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="fff2f-117">The client console window displays the operations sent to each of the endpoints, first the basic endpoint, followed by the secure endpoint.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="fff2f-118">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="fff2f-118">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="fff2f-119">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="fff2f-119">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="fff2f-120">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="fff2f-120">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="fff2f-121">Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="fff2f-121">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="fff2f-122">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="fff2f-122">The samples may already be installed on your machine.</span></span> <span data-ttu-id="fff2f-123">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="fff2f-123">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="fff2f-124">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="fff2f-124">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="fff2f-125">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="fff2f-125">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\MultipleContracts`  
