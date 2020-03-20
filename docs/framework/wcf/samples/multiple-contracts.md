---
title: Birden Fazla Sözleşme
ms.date: 03/30/2017
ms.assetid: 2bef319b-fe9c-4d49-ac6c-dfb23eb35099
ms.openlocfilehash: ed59803b867dfe7994aceea010aa656c53927a0c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144350"
---
# <a name="multiple-contracts"></a><span data-ttu-id="d76ab-102">Birden Fazla Sözleşme</span><span class="sxs-lookup"><span data-stu-id="d76ab-102">Multiple Contracts</span></span>
<span data-ttu-id="d76ab-103">Çoklu Sözleşmeler örneği, bir hizmette birden fazla sözleşmenin nasıl uygulanacağını ve uygulanan sözleşmelerin her biriyle iletişim kurmak için uç noktaların nasıl yapılandırılabildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="d76ab-103">The Multiple Contracts sample demonstrates how to implement more than one contract on a service and how to configure endpoints for communicating with each of the implemented contracts.</span></span> <span data-ttu-id="d76ab-104">Bu örnek [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md)dayanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d76ab-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span> <span data-ttu-id="d76ab-105">Hizmet, `ICalculator` sözleşme ve `ICalculatorSession` sözleşme olmak üzere iki sözleşmeyi tanımlamak üzere değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="d76ab-105">The service has been modified to define two contracts, the `ICalculator` contract and the `ICalculatorSession` contract.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d76ab-106">Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="d76ab-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="d76ab-107">Hizmet sınıfı hem sözleşmeleri `ICalculator` `ICalculatorSession` hem de sözleşmeleri uygular.</span><span class="sxs-lookup"><span data-stu-id="d76ab-107">The service class implements both the `ICalculator` and `ICalculatorSession` contracts.</span></span> <span data-ttu-id="d76ab-108">Sözleşmelerden biri oturum gerektirdiğinden, hizmet, <xref:System.ServiceModel.InstanceContextMode.PerSession> oturumun ömrü boyunca durumu korumak için örnek modunu kullanır.</span><span class="sxs-lookup"><span data-stu-id="d76ab-108">Because one of the contracts requires a session, the service uses the <xref:System.ServiceModel.InstanceContextMode.PerSession> instance mode to maintain the state over the lifetime of the session.</span></span>  
  
 <span data-ttu-id="d76ab-109">Hizmet yapılandırması, her sözleşmeyi ortaya çıkarmak için iki uç nokta tanımlamak üzere değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="d76ab-109">The service configuration has been modified to define two endpoints to expose each contract.</span></span> <span data-ttu-id="d76ab-110">Bitiş `ICalculator` noktası, temel adreste bir `basicHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="d76ab-110">The `ICalculator` endpoint is exposed at the base address using a `basicHttpBinding`.</span></span> <span data-ttu-id="d76ab-111">Bitiş `ICalculatorSession` noktası, aşağıdaki örnek yapılandırmada gösterildiği `wsHttpBinding` `bindingConfiguration` `BindingWithSession`gibi, öznitelik kümesine ayarlanmış bir öznitelik kullanılarak taban adreste/oturumda açığa gösterilir.</span><span class="sxs-lookup"><span data-stu-id="d76ab-111">The `ICalculatorSession` endpoint is exposed at the baseaddress/session using a `wsHttpBinding` with the `bindingConfiguration` attribute set to `BindingWithSession`, as shown in the following sample configuration.</span></span>  
  
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
  
 <span data-ttu-id="d76ab-112">Oluşturulan istemci kodu artık hem özgün `ICalculator` sözleşme hem de `ICalculatorSession` yeni sözleşme için bir istemci sınıfı içerir.</span><span class="sxs-lookup"><span data-stu-id="d76ab-112">The generated client code now includes a client class for both the original `ICalculator` contract and the new `ICalculatorSession` contract.</span></span> <span data-ttu-id="d76ab-113">İstemci yapılandırması ve kodu, her sözleşmeyle uygun hizmet bitiş noktasında iletişim kurmak için değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="d76ab-113">The client configuration and code have been modified to communicate with each contract at the appropriate service endpoint.</span></span>  
  
 <span data-ttu-id="d76ab-114">İstemci bir konsol windows uygulamasıdır (.exe).</span><span class="sxs-lookup"><span data-stu-id="d76ab-114">The client is a console windows application (.exe).</span></span> <span data-ttu-id="d76ab-115">Hizmet, Internet Information Services (IIS) tarafından barındırılır.</span><span class="sxs-lookup"><span data-stu-id="d76ab-115">The service is hosted by Internet Information Services (IIS).</span></span>  
  
 <span data-ttu-id="d76ab-116">İstemci konsol penceresi, her uç noktaya gönderilen işlemleri, önce temel bitiş noktasını ve ardından güvenli bitiş noktasını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="d76ab-116">The client console window displays the operations sent to each of the endpoints, first the basic endpoint, followed by the secure endpoint.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="d76ab-117">Örneği ayarlamak, oluşturmak ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="d76ab-117">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="d76ab-118">Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.</span><span class="sxs-lookup"><span data-stu-id="d76ab-118">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="d76ab-119">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak [için, Windows Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="d76ab-119">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="d76ab-120">Örneği tek veya çapraz makine yapılandırmasında çalıştırmak için, [Windows Communication Foundation Samples'ı çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="d76ab-120">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="d76ab-121">Numuneler makinenize zaten yüklenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="d76ab-121">The samples may already be installed on your machine.</span></span> <span data-ttu-id="d76ab-122">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="d76ab-122">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="d76ab-123">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="d76ab-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d76ab-124">Bu örnek aşağıdaki dizinde yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="d76ab-124">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\MultipleContracts`  
