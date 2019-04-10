---
title: WS Güvenilir Oturum
ms.date: 03/30/2017
helpviewer_keywords:
- Reliable session
ms.assetid: 86e914f2-060b-432b-bd17-333695317745
ms.openlocfilehash: c682db98ac72019d434e06ae79d87b69c85c275e
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59310297"
---
# <a name="ws-reliable-session"></a><span data-ttu-id="5b41c-102">WS Güvenilir Oturum</span><span class="sxs-lookup"><span data-stu-id="5b41c-102">WS Reliable Session</span></span>
<span data-ttu-id="5b41c-103">Bu örnek, güvenilir oturumlar kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="5b41c-103">This sample demonstrates the use of reliable sessions.</span></span> <span data-ttu-id="5b41c-104">Güvenilir oturumlar, güvenilir Mesajlaşma ve oturumlar için destek sağlıyor.</span><span class="sxs-lookup"><span data-stu-id="5b41c-104">Reliable sessions provide support for reliable messaging and sessions.</span></span> <span data-ttu-id="5b41c-105">Güvenilir Mesajlaşma iletişimi hatasında yeniden deneme sayısı ve teslim Güvenceleri gibi iletilerin sıralı varış belirtilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="5b41c-105">Reliable messaging retries communication on failure and allows delivery assurances to be specified, such as in-order arrival of messages.</span></span> <span data-ttu-id="5b41c-106">Oturumlarının çağrıları arasında istemcilerin zachovat stav relace</span><span class="sxs-lookup"><span data-stu-id="5b41c-106">Sessions maintain state for clients between calls.</span></span> <span data-ttu-id="5b41c-107">Örnek oturumları, istemci durum koruma için uygular ve sıralı teslim Güvenceleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="5b41c-107">The sample implements sessions for maintaining client state and specifies in-order delivery assurances.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="5b41c-108">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="5b41c-108">The samples may already be installed on your machine.</span></span> <span data-ttu-id="5b41c-109">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="5b41c-109">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="5b41c-110">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="5b41c-110">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5b41c-111">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="5b41c-111">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\wsReliableSession`  
  
 <span data-ttu-id="5b41c-112">Bu örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md) hesaplayıcı hizmet uygulayan.</span><span class="sxs-lookup"><span data-stu-id="5b41c-112">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="5b41c-113">Güvenilir oturum özellikleri etkin ve uygulama yapılandırma dosyalarında istemci ve hizmet için yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="5b41c-113">The reliable session features are enabled and configured in the application configuration files for the client and service.</span></span>  
  
 <span data-ttu-id="5b41c-114">Bu örnekte, Internet Information Services (IIS) barındırılan hizmetin ve bir konsol uygulaması (.exe) istemcidir.</span><span class="sxs-lookup"><span data-stu-id="5b41c-114">In this sample, the service is hosted in Internet Information Services (IIS) and the client is a console application (.exe).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5b41c-115">Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="5b41c-115">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="5b41c-116">Örnek kullanır `wsHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="5b41c-116">The sample uses the `wsHttpBinding`.</span></span> <span data-ttu-id="5b41c-117">Hem istemci hem de hizmet yapılandırma dosyalarında bağlama belirtildi.</span><span class="sxs-lookup"><span data-stu-id="5b41c-117">The binding is specified in the configuration files for both the client and service.</span></span> <span data-ttu-id="5b41c-118">Uç nokta öğenin belirtilen bağlama türü `binding` özniteliği aşağıdaki örnek yapılandırmada gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="5b41c-118">The binding type is specified in the endpoint element’s `binding` attribute as shown in the following sample configuration.</span></span>  
  
```xml  
<endpoint address=""  
          binding="wsHttpBinding"  
          bindingConfiguration="Binding1"   
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 <span data-ttu-id="5b41c-119">Uç nokta içeren bir `bindingConfiguration` bağlama yapılandırması başvuran öznitelik adında "Binding1."</span><span class="sxs-lookup"><span data-stu-id="5b41c-119">The endpoint contains a `bindingConfiguration` attribute that references a binding configuration named "Binding1."</span></span> <span data-ttu-id="5b41c-120">Bağlama yapılandırması güvenli oturumlar ayarlayarak sağlar `enabled` özniteliği [ \<reliableSession >](../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md) için `true`.</span><span class="sxs-lookup"><span data-stu-id="5b41c-120">The binding configuration enables reliable sessions by setting the `enabled` attribute of the [\<reliableSession>](../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md) to `true`.</span></span> <span data-ttu-id="5b41c-121">Sıralı oturumlar için teslim Güvenceleri sıralı özniteliğini tarafından denetlenen `true` veya `false`.</span><span class="sxs-lookup"><span data-stu-id="5b41c-121">Delivery assurances for ordered sessions are controlled by setting the ordered attribute to `true` or `false`.</span></span> <span data-ttu-id="5b41c-122">Varsayılan, `true` değeridir.</span><span class="sxs-lookup"><span data-stu-id="5b41c-122">The default is `true`.</span></span>  
  
```xml  
<bindings>  
    <wsHttpBinding>  
        <binding name="Binding1">  
            <reliableSession enabled="true" />  
        </binding>  
    </wsHttpBinding>  
</bindings>  
```  
  
 <span data-ttu-id="5b41c-123">Hizmet uygulaması sınıf uygulayan <xref:System.ServiceModel.InstanceContextMode.PerSession> örneklemesini aşağıdaki örnek kodda gösterildiği gibi her istemci için ayrı bir sınıf örneğinin korumak için.</span><span class="sxs-lookup"><span data-stu-id="5b41c-123">The service implementation class implements <xref:System.ServiceModel.InstanceContextMode.PerSession> instancing to maintain a separate class instance for each client, as shown in the following sample code.</span></span>  

```csharp
[ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)] public class CalculatorService : ICalculator  
{  
    ...  
}  
```
  
 <span data-ttu-id="5b41c-124">Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="5b41c-124">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="5b41c-125">İstemci bilgisayarı için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="5b41c-125">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="5b41c-126">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="5b41c-126">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="5b41c-127">Yükleme [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aşağıdaki komutu kullanarak 4.0.</span><span class="sxs-lookup"><span data-stu-id="5b41c-127">Install [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 using the following command.</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. <span data-ttu-id="5b41c-128">Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5b41c-128">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3. <span data-ttu-id="5b41c-129">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5b41c-129">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="5b41c-130">Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5b41c-130">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
