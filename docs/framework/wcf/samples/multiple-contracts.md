---
title: Birden Fazla Sözleşme
ms.date: 03/30/2017
ms.assetid: 2bef319b-fe9c-4d49-ac6c-dfb23eb35099
ms.openlocfilehash: acced4bfc79571c78e868b31b0a4db6cfbdea76a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61989748"
---
# <a name="multiple-contracts"></a><span data-ttu-id="d61ef-102">Birden Fazla Sözleşme</span><span class="sxs-lookup"><span data-stu-id="d61ef-102">Multiple Contracts</span></span>
<span data-ttu-id="d61ef-103">Birden çok sözleşme örnek nasıl bir hizmet birden fazla sözleşmesini uygulama ve uç noktaları her uygulanan sözleşmelerin ile iletişim kurmak için yapılandırma gösterir.</span><span class="sxs-lookup"><span data-stu-id="d61ef-103">The Multiple Contracts sample demonstrates how to implement more than one contract on a service and how to configure endpoints for communicating with each of the implemented contracts.</span></span> <span data-ttu-id="d61ef-104">Bu örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="d61ef-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span> <span data-ttu-id="d61ef-105">Hizmet, iki sözleşmelerini tanımlamak için değiştirilmiş `ICalculator` sözleşme ve `ICalculatorSession` sözleşme.</span><span class="sxs-lookup"><span data-stu-id="d61ef-105">The service has been modified to define two contracts, the `ICalculator` contract and the `ICalculatorSession` contract.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d61ef-106">Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="d61ef-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="d61ef-107">Hizmet sınıfı her ikisini birden uygular `ICalculator` ve `ICalculatorSession` sözleşmeler.</span><span class="sxs-lookup"><span data-stu-id="d61ef-107">The service class implements both the `ICalculator` and `ICalculatorSession` contracts.</span></span> <span data-ttu-id="d61ef-108">Sözleşmeler birini oturum gerektirdiğinden, hizmetin kullandığı <xref:System.ServiceModel.InstanceContextMode.PerSession> oturumunun ömrü boyunca durumunu korumak üzere örnek modu.</span><span class="sxs-lookup"><span data-stu-id="d61ef-108">Because one of the contracts requires a session, the service uses the <xref:System.ServiceModel.InstanceContextMode.PerSession> instance mode to maintain the state over the lifetime of the session.</span></span>  
  
 <span data-ttu-id="d61ef-109">Her sözleşme kullanıma sunmak için iki uç nokta tanımlamak için hizmet yapılandırması değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="d61ef-109">The service configuration has been modified to define two endpoints to expose each contract.</span></span> <span data-ttu-id="d61ef-110">`ICalculator` Uç nokta Internet'e açık taban adresi kullanarak bir `basicHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="d61ef-110">The `ICalculator` endpoint is exposed at the base address using a `basicHttpBinding`.</span></span> <span data-ttu-id="d61ef-111">`ICalculatorSession` Uç nokta kullanarak baseaddress/oturum sırasında sunulan bir `wsHttpBinding` ile `bindingConfiguration` özniteliğini `BindingWithSession`aşağıdaki örnek yapılandırmada gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="d61ef-111">The `ICalculatorSession` endpoint is exposed at the baseaddress/session using a `wsHttpBinding` with the `bindingConfiguration` attribute set to `BindingWithSession`, as shown in the following sample configuration.</span></span>  
  
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
  
 <span data-ttu-id="d61ef-112">Oluşturulan istemci kodu artık istemci sınıfı hem özgün içerir `ICalculator` sözleşme ve yeni `ICalculatorSession` sözleşme.</span><span class="sxs-lookup"><span data-stu-id="d61ef-112">The generated client code now includes a client class for both the original `ICalculator` contract and the new `ICalculatorSession` contract.</span></span> <span data-ttu-id="d61ef-113">İstemci Yapılandırması ve kodu uygun hizmet uç noktasında her sözleşme ile iletişim kurmak için değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="d61ef-113">The client configuration and code have been modified to communicate with each contract at the appropriate service endpoint.</span></span>  
  
 <span data-ttu-id="d61ef-114">Bir konsol windows uygulaması (.exe) istemcisidir.</span><span class="sxs-lookup"><span data-stu-id="d61ef-114">The client is a console windows application (.exe).</span></span> <span data-ttu-id="d61ef-115">Hizmet, Internet Information Services (IIS) tarafından barındırılır.</span><span class="sxs-lookup"><span data-stu-id="d61ef-115">The service is hosted by Internet Information Services (IIS).</span></span>  
  
 <span data-ttu-id="d61ef-116">İlk gönderilen her uç nokta güvenli bir uç noktası tarafından izlenen temel uç nokta işlemleri istemci konsol penceresinde görüntüler.</span><span class="sxs-lookup"><span data-stu-id="d61ef-116">The client console window displays the operations sent to each of the endpoints, first the basic endpoint, followed by the secure endpoint.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="d61ef-117">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="d61ef-117">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="d61ef-118">Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d61ef-118">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="d61ef-119">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d61ef-119">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="d61ef-120">Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d61ef-120">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d61ef-121">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="d61ef-121">The samples may already be installed on your machine.</span></span> <span data-ttu-id="d61ef-122">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="d61ef-122">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="d61ef-123">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="d61ef-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d61ef-124">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="d61ef-124">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\MultipleContracts`  
