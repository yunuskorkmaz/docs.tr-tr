---
title: "WS Güvenilir Oturum"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Reliable session
ms.assetid: 86e914f2-060b-432b-bd17-333695317745
caps.latest.revision: "30"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9f016cc075b98b03c17959280215f7aa64f44e24
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ws-reliable-session"></a><span data-ttu-id="4e5d5-102">WS Güvenilir Oturum</span><span class="sxs-lookup"><span data-stu-id="4e5d5-102">WS Reliable Session</span></span>
<span data-ttu-id="4e5d5-103">Bu örnek güvenilir oturumlar kullanımını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="4e5d5-103">This sample demonstrates the use of reliable sessions.</span></span> <span data-ttu-id="4e5d5-104">Güvenilir oturumlar güvenilir Mesajlaşma ve oturumlar için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="4e5d5-104">Reliable sessions provide support for reliable messaging and sessions.</span></span> <span data-ttu-id="4e5d5-105">Güvenilir Mesajlaşma iletişim başarısızlığı yeniden deneme ve teslim Güvenceleri gibi iletilerin sıralı varış belirtilmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="4e5d5-105">Reliable messaging retries communication on failure and allows delivery assurances to be specified, such as in-order arrival of messages.</span></span> <span data-ttu-id="4e5d5-106">Oturum durumu çağrıları arasında istemcileri için korur.</span><span class="sxs-lookup"><span data-stu-id="4e5d5-106">Sessions maintain state for clients between calls.</span></span> <span data-ttu-id="4e5d5-107">Örnek istemci durumunu korumak için oturumları uygular ve sıralı teslim Güvenceleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="4e5d5-107">The sample implements sessions for maintaining client state and specifies in-order delivery assurances.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4e5d5-108">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="4e5d5-108">The samples may already be installed on your machine.</span></span> <span data-ttu-id="4e5d5-109">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="4e5d5-109">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="4e5d5-110">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="4e5d5-110">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4e5d5-111">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="4e5d5-111">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\wsReliableSession`  
  
 <span data-ttu-id="4e5d5-112">Bu örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md) hesap makinesi hizmetinin uygular.</span><span class="sxs-lookup"><span data-stu-id="4e5d5-112">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="4e5d5-113">Güvenilir oturum özellikleri etkinleştirilmiş ve uygulama yapılandırma dosyaları istemci ve hizmet için yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="4e5d5-113">The reliable session features are enabled and configured in the application configuration files for the client and service.</span></span>  
  
 <span data-ttu-id="4e5d5-114">Bu örnekte, Internet Information Services (IIS) barındırılan hizmetindeki ve istemcinin bir konsol uygulaması (.exe).</span><span class="sxs-lookup"><span data-stu-id="4e5d5-114">In this sample, the service is hosted in Internet Information Services (IIS) and the client is a console application (.exe).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4e5d5-115">Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="4e5d5-115">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="4e5d5-116">Örnek kullanır `wsHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="4e5d5-116">The sample uses the `wsHttpBinding`.</span></span> <span data-ttu-id="4e5d5-117">Bağlama, hem istemci hem de hizmet yapılandırma dosyalarında belirtilir.</span><span class="sxs-lookup"><span data-stu-id="4e5d5-117">The binding is specified in the configuration files for both the client and service.</span></span> <span data-ttu-id="4e5d5-118">Uç nokta öğesinin belirtilen bağlama türü `binding` özniteliği aşağıdaki örnek yapılandırmada gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="4e5d5-118">The binding type is specified in the endpoint element’s `binding` attribute as shown in the following sample configuration.</span></span>  
  
```xml  
<endpoint address=""  
          binding="wsHttpBinding"  
          bindingConfiguration="Binding1"   
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 <span data-ttu-id="4e5d5-119">Uç nokta içeren bir `bindingConfiguration` adlı bir bağlama yapılandırması başvuran öznitelik "Binding1."</span><span class="sxs-lookup"><span data-stu-id="4e5d5-119">The endpoint contains a `bindingConfiguration` attribute that references a binding configuration named "Binding1."</span></span> <span data-ttu-id="4e5d5-120">Güvenilir oturumlar ayarlayarak bağlama yapılandırması sağlar `enabled` özniteliği [ \<reliableSession >](../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md) için `true`.</span><span class="sxs-lookup"><span data-stu-id="4e5d5-120">The binding configuration enables reliable sessions by setting the `enabled` attribute of the [\<reliableSession>](../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md) to `true`.</span></span> <span data-ttu-id="4e5d5-121">Sıralı oturumları için teslim Güvenceleri sıralı özniteliğini tarafından denetlenen `true` veya `false`.</span><span class="sxs-lookup"><span data-stu-id="4e5d5-121">Delivery assurances for ordered sessions are controlled by setting the ordered attribute to `true` or `false`.</span></span> <span data-ttu-id="4e5d5-122">Varsayılan, `true` değeridir.</span><span class="sxs-lookup"><span data-stu-id="4e5d5-122">The default is `true`.</span></span>  
  
```xml  
<bindings>  
    <wsHttpBinding>  
        <binding name="Binding1">  
            <reliableSession enabled="true" />  
        </binding>  
    </wsHttpBinding>  
</bindings>  
```  
  
 <span data-ttu-id="4e5d5-123">Hizmet uygulaması sınıfı uygulayan <xref:System.ServiceModel.InstanceContextMode.PerSession> örneklemesini aşağıdaki örnek kodda gösterildiği gibi her bir istemci için ayrı sınıf örneğinin korumak için.</span><span class="sxs-lookup"><span data-stu-id="4e5d5-123">The service implementation class implements <xref:System.ServiceModel.InstanceContextMode.PerSession> instancing to maintain a separate class instance for each client, as shown in the following sample code.</span></span>  
  
```  
[ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)] public class CalculatorService : ICalculator  
{  
    ...  
}  
```  
  
 <span data-ttu-id="4e5d5-124">Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="4e5d5-124">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="4e5d5-125">İstemcisi penceresinde istemciyi aşağı kapatmak için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="4e5d5-125">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="4e5d5-126">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="4e5d5-126">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="4e5d5-127">Yükleme [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aşağıdaki komutu kullanarak 4.0.</span><span class="sxs-lookup"><span data-stu-id="4e5d5-127">Install [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 using the following command.</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  <span data-ttu-id="4e5d5-128">Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4e5d5-128">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3.  <span data-ttu-id="4e5d5-129">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4e5d5-129">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="4e5d5-130">Tek veya çapraz makine yapılandırmada örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4e5d5-130">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e5d5-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4e5d5-131">See Also</span></span>
