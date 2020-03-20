---
title: WS Güvenilir Oturum
ms.date: 03/30/2017
helpviewer_keywords:
- Reliable session
ms.assetid: 86e914f2-060b-432b-bd17-333695317745
ms.openlocfilehash: 8898dfedc6ba7deceb5a6e6856b7c7e6ad79d047
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143505"
---
# <a name="ws-reliable-session"></a><span data-ttu-id="e6c00-102">WS Güvenilir Oturum</span><span class="sxs-lookup"><span data-stu-id="e6c00-102">WS Reliable Session</span></span>
<span data-ttu-id="e6c00-103">Bu örnek, güvenilir oturumların kullanımını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="e6c00-103">This sample demonstrates the use of reliable sessions.</span></span> <span data-ttu-id="e6c00-104">Güvenilir oturumlar, güvenilir mesajlaşma ve oturumlar için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="e6c00-104">Reliable sessions provide support for reliable messaging and sessions.</span></span> <span data-ttu-id="e6c00-105">Güvenilir ileti, iletişimi başarısızlığa göre yeniden dener ve iletilerin sırayla gelmesi gibi teslimat güvencelerinin belirtilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="e6c00-105">Reliable messaging retries communication on failure and allows delivery assurances to be specified, such as in-order arrival of messages.</span></span> <span data-ttu-id="e6c00-106">Oturumlar, istemciler için aramalar arasındaki durumu korur.</span><span class="sxs-lookup"><span data-stu-id="e6c00-106">Sessions maintain state for clients between calls.</span></span> <span data-ttu-id="e6c00-107">Örnek, istemci durumunu korumak için oturumlar uygular ve sipariş içi teslimat güvencelerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e6c00-107">The sample implements sessions for maintaining client state and specifies in-order delivery assurances.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="e6c00-108">Numuneler makinenize zaten yüklenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="e6c00-108">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e6c00-109">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="e6c00-109">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="e6c00-110">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="e6c00-110">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e6c00-111">Bu örnek aşağıdaki dizinde yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="e6c00-111">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\wsReliableSession`  
  
 <span data-ttu-id="e6c00-112">Bu örnek, bir hesap makinesi hizmeti uygulayan [Başlarken'e](../../../../docs/framework/wcf/samples/getting-started-sample.md) dayanır.</span><span class="sxs-lookup"><span data-stu-id="e6c00-112">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="e6c00-113">Güvenilir oturum özellikleri etkinleştirilir ve istemci ve hizmet için uygulama yapılandırma dosyalarında yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="e6c00-113">The reliable session features are enabled and configured in the application configuration files for the client and service.</span></span>  
  
 <span data-ttu-id="e6c00-114">Bu örnekte, hizmet Internet Information Services (IIS) barındırılır ve istemci bir konsol uygulamasıdır (.exe).</span><span class="sxs-lookup"><span data-stu-id="e6c00-114">In this sample, the service is hosted in Internet Information Services (IIS) and the client is a console application (.exe).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e6c00-115">Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="e6c00-115">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="e6c00-116">Örnek `wsHttpBinding`kullanır.</span><span class="sxs-lookup"><span data-stu-id="e6c00-116">The sample uses the `wsHttpBinding`.</span></span> <span data-ttu-id="e6c00-117">Bağlama, hem istemci hem de hizmet için yapılandırma dosyalarında belirtilir.</span><span class="sxs-lookup"><span data-stu-id="e6c00-117">The binding is specified in the configuration files for both the client and service.</span></span> <span data-ttu-id="e6c00-118">Bağlama türü, aşağıdaki örnek yapılandırmada `binding` gösterildiği gibi uç nokta öğesi özniteliği belirtilir.</span><span class="sxs-lookup"><span data-stu-id="e6c00-118">The binding type is specified in the endpoint element’s `binding` attribute as shown in the following sample configuration.</span></span>  
  
```xml  
<endpoint address=""  
          binding="wsHttpBinding"  
          bindingConfiguration="Binding1"
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 <span data-ttu-id="e6c00-119">Uç nokta, `bindingConfiguration` "Binding1" adlı bağlayıcı yapılandırmaya başvuran bir öznitelik içerir.</span><span class="sxs-lookup"><span data-stu-id="e6c00-119">The endpoint contains a `bindingConfiguration` attribute that references a binding configuration named "Binding1."</span></span> <span data-ttu-id="e6c00-120">Bağlama `enabled` [ \<yapılandırması, güvenilir Session>](../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md) özniteliğini `true`'ne ayarlayarak güvenilir oturumlar sağlar.</span><span class="sxs-lookup"><span data-stu-id="e6c00-120">The binding configuration enables reliable sessions by setting the `enabled` attribute of the [\<reliableSession>](../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md) to `true`.</span></span> <span data-ttu-id="e6c00-121">Sipariş edilen oturumlar için teslimat güvenceleri, sipariş `true` edilen `false`özniteliği ayarlayarak veya .</span><span class="sxs-lookup"><span data-stu-id="e6c00-121">Delivery assurances for ordered sessions are controlled by setting the ordered attribute to `true` or `false`.</span></span> <span data-ttu-id="e6c00-122">Varsayılan değer: `true`.</span><span class="sxs-lookup"><span data-stu-id="e6c00-122">The default is `true`.</span></span>  
  
```xml  
<bindings>  
    <wsHttpBinding>  
        <binding name="Binding1">  
            <reliableSession enabled="true" />  
        </binding>  
    </wsHttpBinding>  
</bindings>  
```  
  
 <span data-ttu-id="e6c00-123">Hizmet uygulama sınıfı, <xref:System.ServiceModel.InstanceContextMode.PerSession> aşağıdaki örnek kodda gösterildiği gibi, her istemci için ayrı bir sınıf örneği korumak için instancing uygular.</span><span class="sxs-lookup"><span data-stu-id="e6c00-123">The service implementation class implements <xref:System.ServiceModel.InstanceContextMode.PerSession> instancing to maintain a separate class instance for each client, as shown in the following sample code.</span></span>  

```csharp
[ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)] public class CalculatorService : ICalculator  
{  
    ...  
}  
```
  
 <span data-ttu-id="e6c00-124">Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="e6c00-124">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="e6c00-125">İstemciyi kapatmak için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="e6c00-125">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="e6c00-126">Örneği ayarlamak, oluşturmak ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="e6c00-126">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="e6c00-127">Aşağıdaki komutu kullanarak 4.0 ASP.NET yükleyin.</span><span class="sxs-lookup"><span data-stu-id="e6c00-127">Install ASP.NET 4.0 using the following command.</span></span>  
  
    ```console  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. <span data-ttu-id="e6c00-128">Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.</span><span class="sxs-lookup"><span data-stu-id="e6c00-128">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3. <span data-ttu-id="e6c00-129">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak [için, Windows Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="e6c00-129">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="e6c00-130">Örneği tek veya çapraz makine yapılandırmasında çalıştırmak için, [Windows Communication Foundation Samples'ı çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="e6c00-130">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
