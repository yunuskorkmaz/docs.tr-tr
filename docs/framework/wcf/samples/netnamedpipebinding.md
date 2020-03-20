---
title: NetNamedPipeBinding
ms.date: 03/30/2017
helpviewer_keywords:
- Net Profile Named Pipe
ms.assetid: e78e845f-c325-46e2-927d-81616f97f7d5
ms.openlocfilehash: da54a835fd32efe4f53a80701465d2d7d8adba7e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183471"
---
# <a name="netnamedpipebinding"></a><span data-ttu-id="824e3-102">NetNamedPipeBinding</span><span class="sxs-lookup"><span data-stu-id="824e3-102">NetNamedPipeBinding</span></span>
<span data-ttu-id="824e3-103">Bu örnek, `netNamedPipeBinding` aynı makinede çapraz proses iletişimi sağlayan bağlamayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="824e3-103">This sample demonstrates the `netNamedPipeBinding` binding, which provides cross-process communication on the same machine.</span></span> <span data-ttu-id="824e3-104">Adlandırılmış borular makineler arasında çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="824e3-104">Named pipes do not work across machines.</span></span> <span data-ttu-id="824e3-105">Bu örnek, [Başlangıç](../../../../docs/framework/wcf/samples/getting-started-sample.md) hesap makinesi hizmetine dayanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="824e3-105">This sample is based on The [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) calculator service.</span></span>  
  
 <span data-ttu-id="824e3-106">Bu örnekte, hizmet kendi kendine barındırılan.</span><span class="sxs-lookup"><span data-stu-id="824e3-106">In this sample, the service is self-hosted.</span></span> <span data-ttu-id="824e3-107">Hem istemci hem de hizmet konsol uygulamalarıdır.</span><span class="sxs-lookup"><span data-stu-id="824e3-107">Both the client and the service are console applications.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="824e3-108">Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="824e3-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="824e3-109">Bağlama istemci ve hizmet için yapılandırma dosyalarında belirtilir.</span><span class="sxs-lookup"><span data-stu-id="824e3-109">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="824e3-110">Bağlama türü, aşağıdaki `binding` örnek yapılandırmada gösterildiği gibi, [ \<istemci \<>öğesinin](../../configure-apps/file-schema/wcf/endpoint-of-client.md) [ \<bitiş noktası>](../../configure-apps/file-schema/wcf/endpoint-element.md) veya bitiş noktası> özniteliği içinde belirtilir:</span><span class="sxs-lookup"><span data-stu-id="824e3-110">The binding type is specified in the `binding` attribute of the [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-element.md) or [\<endpoint> of \<client>](../../configure-apps/file-schema/wcf/endpoint-of-client.md) element, as shown in the following sample configuration:</span></span>  
  
```xml  
<endpoint address="net.pipe://localhost/ServiceModelSamples/service"  
          binding="netNamedPipeBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 <span data-ttu-id="824e3-111">Önceki örnekte, varsayılan ayarlarla bağlamayı `netNamedPipeBinding` kullanmak için bir bitiş noktasının nasıl yapılandırılabildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="824e3-111">The previous sample shows how to configure an endpoint to use the `netNamedPipeBinding` binding with the default settings.</span></span> <span data-ttu-id="824e3-112">Bağlamayı `netNamedPipeBinding` yapılandırmak ve bazı ayarlarını değiştirmek istiyorsanız, bağlayıcı bir yapılandırma tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="824e3-112">If you want to configure the `netNamedPipeBinding` binding and change some of its settings, you must define a binding configuration.</span></span> <span data-ttu-id="824e3-113">Bitiş noktası, öznitelik ile `bindingConfiguration` ada göre bağlama yapılandırmabaşvurugerekir.</span><span class="sxs-lookup"><span data-stu-id="824e3-113">The endpoint must reference the binding configuration by name with a `bindingConfiguration` attribute.</span></span>  
  
```xml  
<endpoint address="net.pipe://localhost/ServiceModelSamples/service"  
          binding="netNamedPipeBinding"  
          bindingConfiguration="Binding1"
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 <span data-ttu-id="824e3-114">Bu örnekte, bağlama yapılandırması adlandırılır `Binding1` ve aşağıdaki tanımı vardır:</span><span class="sxs-lookup"><span data-stu-id="824e3-114">In this sample, the binding configuration is named `Binding1` and has the following definition:</span></span>  
  
```xml  
<bindings>  
  <!--   
        Following is the expanded configuration section for a NetNamedPipeBinding.  
        Each property is configured with the default value.  
     -->  
  <netNamedPipeBinding>  
    <binding name="Binding1"
             closeTimeout="00:01:00"  
             openTimeout="00:01:00"
             receiveTimeout="00:10:00"
             sendTimeout="00:01:00"  
             transactionFlow="false"
             transferMode="Buffered"
             transactionProtocol="OleTransactions"  
             hostNameComparisonMode="StrongWildcard"
             maxBufferPoolSize="524288"  
             maxBufferSize="65536"
             maxConnections="10"
             maxReceivedMessageSize="65536">  
      <security mode="Transport">  
        <transport protectionLevel="EncryptAndSign" />  
      </security>  
    </binding>  
  </netNamedPipeBinding>  
</bindings>  
```  
  
 <span data-ttu-id="824e3-115">Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="824e3-115">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="824e3-116">İstemciyi kapatmak için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="824e3-116">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="824e3-117">Örneği ayarlamak, oluşturmak ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="824e3-117">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="824e3-118">Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.</span><span class="sxs-lookup"><span data-stu-id="824e3-118">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="824e3-119">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak [için, Windows Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="824e3-119">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="824e3-120">Örneği tek bir makine yapılandırmasında çalıştırmak [için, Windows Communication Foundation Samples'i çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="824e3-120">To run the sample in a single machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="824e3-121">Numuneler makinenize zaten yüklenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="824e3-121">The samples may already be installed on your machine.</span></span> <span data-ttu-id="824e3-122">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="824e3-122">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="824e3-123">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="824e3-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="824e3-124">Bu örnek aşağıdaki dizinde yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="824e3-124">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\NamedPipe`  
