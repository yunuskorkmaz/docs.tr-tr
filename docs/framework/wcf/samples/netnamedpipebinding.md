---
title: NetNamedPipeBinding
ms.date: 03/30/2017
helpviewer_keywords:
- Net Profile Named Pipe
ms.assetid: e78e845f-c325-46e2-927d-81616f97f7d5
ms.openlocfilehash: cd7e97559458a4415399488b0fdb96a850033c44
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59294840"
---
# <a name="netnamedpipebinding"></a><span data-ttu-id="4a361-102">NetNamedPipeBinding</span><span class="sxs-lookup"><span data-stu-id="4a361-102">NetNamedPipeBinding</span></span>
<span data-ttu-id="4a361-103">Bu örnek gösterir `netNamedPipeBinding` aynı makinede çapraz proses haberleşmesi sağlayan bağlama.</span><span class="sxs-lookup"><span data-stu-id="4a361-103">This sample demonstrates the `netNamedPipeBinding` binding, which provides cross-process communication on the same machine.</span></span> <span data-ttu-id="4a361-104">Adlandırılmış Kanallar makinelerde çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="4a361-104">Named pipes do not work across machines.</span></span> <span data-ttu-id="4a361-105">Bu örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md) hesaplayıcı hizmeti.</span><span class="sxs-lookup"><span data-stu-id="4a361-105">This sample is based on The [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) calculator service.</span></span>  
  
 <span data-ttu-id="4a361-106">Bu örnekte, hizmet kendiliğinden barındırılır.</span><span class="sxs-lookup"><span data-stu-id="4a361-106">In this sample, the service is self-hosted.</span></span> <span data-ttu-id="4a361-107">Hem istemci hem de hizmet Konsolu uygulamalardır.</span><span class="sxs-lookup"><span data-stu-id="4a361-107">Both the client and the service are console applications.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4a361-108">Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="4a361-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="4a361-109">İstemci ve hizmet yapılandırma dosyalarında bağlama belirtildi.</span><span class="sxs-lookup"><span data-stu-id="4a361-109">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="4a361-110">Bağlama türü belirtilen `binding` özniteliği [ \<uç noktası >](../../configure-apps/file-schema/wcf/endpoint-element.md) veya [ \<uç noktası >'ın \<istemci >](../../configure-apps/file-schema/wcf/endpoint-of-client.md) gösterildiği öğesi Aşağıdaki örnek yapılandırma:</span><span class="sxs-lookup"><span data-stu-id="4a361-110">The binding type is specified in the `binding` attribute of the [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-element.md) or [\<endpoint> of \<client>](../../configure-apps/file-schema/wcf/endpoint-of-client.md) element, as shown in the following sample configuration:</span></span>  
  
```xml  
<endpoint address="net.pipe://localhost/ServiceModelSamples/service"  
          binding="netNamedPipeBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 <span data-ttu-id="4a361-111">Önceki örneği kullanmak için bir uç nokta yapılandırma işlemi gösterilmektedir `netNamedPipeBinding` varsayılan ayarlarla bağlama.</span><span class="sxs-lookup"><span data-stu-id="4a361-111">The previous sample shows how to configure an endpoint to use the `netNamedPipeBinding` binding with the default settings.</span></span> <span data-ttu-id="4a361-112">Yapılandırmak istiyorsanız `netNamedPipeBinding` bağlama ve bazıları ayarlarını bağlama yapılandırması tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="4a361-112">If you want to configure the `netNamedPipeBinding` binding and change some of its settings, you must define a binding configuration.</span></span> <span data-ttu-id="4a361-113">Uç nokta adı ile bağlama yapılandırması başvurmalıdır bir `bindingConfiguration` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="4a361-113">The endpoint must reference the binding configuration by name with a `bindingConfiguration` attribute.</span></span>  
  
```xml  
<endpoint address="net.pipe://localhost/ServiceModelSamples/service"  
          binding="netNamedPipeBinding"  
          bindingConfiguration="Binding1"   
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 <span data-ttu-id="4a361-114">Bu örnekte, bağlama Yapılandırması adlı `Binding1` ve aşağıdaki tanımları içerir:</span><span class="sxs-lookup"><span data-stu-id="4a361-114">In this sample, the binding configuration is named `Binding1` and has the following definition:</span></span>  
  
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
  
 <span data-ttu-id="4a361-115">Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="4a361-115">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="4a361-116">İstemci bilgisayarı için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="4a361-116">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="4a361-117">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="4a361-117">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="4a361-118">Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4a361-118">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="4a361-119">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4a361-119">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="4a361-120">Tek makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4a361-120">To run the sample in a single machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4a361-121">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="4a361-121">The samples may already be installed on your machine.</span></span> <span data-ttu-id="4a361-122">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="4a361-122">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="4a361-123">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="4a361-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4a361-124">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="4a361-124">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\NamedPipe`  
