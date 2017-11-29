---
title: "Sınırlama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- service behaviors, throttling sample
- Throttling Sample [Windows Communication Foundation]
ms.assetid: 40bb3582-8ae9-4410-96f0-6c515bfaf47c
caps.latest.revision: "18"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 33d7d3be7c28f5fb22bd50f7b57b041abd642c32
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="throttling"></a><span data-ttu-id="c179b-102">Sınırlama</span><span class="sxs-lookup"><span data-stu-id="c179b-102">Throttling</span></span>
<span data-ttu-id="c179b-103">Azaltma örnek azaltma denetimleri kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c179b-103">The Throttling sample demonstrates the use of throttling controls.</span></span> <span data-ttu-id="c179b-104">Azaltma denetimleri sınırlarını eşzamanlı çağrıları, örneği veya oturumları atlayarak kaynaklarının kullanımını engellemek için sayısına yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="c179b-104">Throttling controls place limits on the number of concurrent calls, instances, or sessions to prevent over-consumption of resources.</span></span> <span data-ttu-id="c179b-105">Davranış azaltma hizmet yapılandırma dosyası ayarları belirtilir.</span><span class="sxs-lookup"><span data-stu-id="c179b-105">Throttling behavior is specified in service configuration file settings.</span></span> <span data-ttu-id="c179b-106">Bu örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md) hesap makinesi hizmetinin uygular.</span><span class="sxs-lookup"><span data-stu-id="c179b-106">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span>  
  
 <span data-ttu-id="c179b-107">Bu örnekte, istemci bir konsol uygulaması (.exe) ve Internet Information Services (IIS) tarafından barındırılan hizmetindeki.</span><span class="sxs-lookup"><span data-stu-id="c179b-107">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c179b-108">Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="c179b-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="c179b-109">Hizmet yapılandırma dosyası azaltma denetimleri belirtiyor. bir [ \<serviceThrottling >](../../../../docs/framework/configure-apps/file-schema/wcf/servicethrottling.md), aşağıdaki örnek yapılandırmada gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="c179b-109">The service configuration file specifies throttling controls in a [\<serviceThrottling>](../../../../docs/framework/configure-apps/file-schema/wcf/servicethrottling.md), as shown in the following sample configuration.</span></span>  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="CalculatorServiceBehavior">  
      <serviceDebug includeExceptionDetailInFaults="False" />  
      <serviceMetadata httpGetEnabled="True"/>  
      <!-- Specify throttling behavior -->  
    <serviceThrottling maxConcurrentCalls="2"  
                       maxConcurrentInstances="10"/>  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 <span data-ttu-id="c179b-110">Yapılandırıldığı şekilde hizmet 2 ile 10 eşzamanlı örnek sayısı maksimum eşzamanlı çağrı sınırlar.</span><span class="sxs-lookup"><span data-stu-id="c179b-110">As configured, the service limits the maximum concurrent calls to 2, and the maximum number of concurrent instances to 10.</span></span>  
  
 <span data-ttu-id="c179b-111">Azaltma göstermek için size bir bekleme süresini hizmet yöntemleri gibi tanımlayın:</span><span class="sxs-lookup"><span data-stu-id="c179b-111">In order to demonstrate throttling we define a sleep time on the service methods as follows:</span></span>  
  
```  
public double Add(double n1, double n2)  
{  
    System.Threading.Thread.Sleep(2000);  
    return n1 + n2;  
}  
```  
  
 <span data-ttu-id="c179b-112">Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="c179b-112">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="c179b-113">Ekleme ve çıkarma yöntemleri eşzamanlı olarak yürütülen ve aynı anda en çok 2 yöntemleri aynı anda çalıştırılabilecek kanıtlama bölme yöntemleri ve Multiply yürütülen böylece azaltma gösterimi.</span><span class="sxs-lookup"><span data-stu-id="c179b-113">The Add and Subtract methods are executed concurrently and the Multiply and Divide methods are executed concurrently proving that not more than 2 methods can be executed concurrently thus demonstrating throttling.</span></span>  
  
```  
Press <ENTER> to terminate client.  
Add(100,15.99)  
Subtract(145,76.54)  
Multiply(9,81.25)  
Divide(22,7)  
  
Add Result: 115.99  
Subtract Result: 68.46  
Multiply Result: 731.25  
Divide Result: 3.14285714285714  
  
Press any key to continue . . .  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="c179b-114">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="c179b-114">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="c179b-115">Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c179b-115">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="c179b-116">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c179b-116">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="c179b-117">Tek veya çapraz makine yapılandırmada örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c179b-117">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c179b-118">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="c179b-118">The samples may already be installed on your machine.</span></span> <span data-ttu-id="c179b-119">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="c179b-119">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="c179b-120">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="c179b-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c179b-121">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="c179b-121">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Throttling`  
  
## <a name="see-also"></a><span data-ttu-id="c179b-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c179b-122">See Also</span></span>
