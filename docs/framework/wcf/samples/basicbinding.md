---
title: BasicBinding
ms.date: 03/30/2017
ms.assetid: 86fbeb87-4d89-4b61-9577-867e0ac12945
ms.openlocfilehash: e98b1254710ebac2305fd7dd5d39a146d749ff44
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70990146"
---
# <a name="basicbinding"></a><span data-ttu-id="776e9-102">BasicBinding</span><span class="sxs-lookup"><span data-stu-id="776e9-102">BasicBinding</span></span>

<span data-ttu-id="776e9-103">Bu örnek, ilk ve ikinci `basicHttpBinding` nesil Web Hizmetleri ile HTTP iletişimi ve en fazla birlikte çalışabilirlik sağlayan öğesinin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="776e9-103">This sample demonstrates the use of `basicHttpBinding` that provides HTTP communication and maximum interoperability with first- and second-generation Web services.</span></span>

> [!NOTE]
> <span data-ttu-id="776e9-104">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="776e9-104">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="776e9-105">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="776e9-105">The samples may already be installed on your machine.</span></span> <span data-ttu-id="776e9-106">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="776e9-106">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="776e9-107">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ' e gidin.</span><span class="sxs-lookup"><span data-stu-id="776e9-107">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="776e9-108">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="776e9-108">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Basic\Http`

## <a name="sample-details"></a><span data-ttu-id="776e9-109">Örnek Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="776e9-109">Sample Details</span></span>

<span data-ttu-id="776e9-110">Bu örnek, bir Hesaplayıcı hizmeti uygulayan [kullanmaya](../../../../docs/framework/wcf/samples/getting-started-sample.md) Başlarken hizmetini temel alır.</span><span class="sxs-lookup"><span data-stu-id="776e9-110">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span>

<span data-ttu-id="776e9-111">Temel bağlamayı varsayılan davranışla kullanmak için yalnızca bağlama bölümünün adı gereklidir.</span><span class="sxs-lookup"><span data-stu-id="776e9-111">To use the basic binding with default behavior, only the binding section name is required.</span></span> <span data-ttu-id="776e9-112">Temel bağlamayı yapılandırmak ve bazı ayarlarını değiştirmek istiyorsanız, bir bağlama yapılandırması tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="776e9-112">If you want to configure the basic binding and change some of its settings, it is necessary to define a binding configuration.</span></span> <span data-ttu-id="776e9-113">Uç noktanın, aşağıdaki örnek kodda gösterildiği gibi < `bindingConfiguration` `endpoint`> öğesinin özniteliğini kullanarak bağlama yapılandırmasına adı ile başvurması gerekir.</span><span class="sxs-lookup"><span data-stu-id="776e9-113">The endpoint must reference the binding configuration by name by using the `bindingConfiguration` attribute of the <`endpoint`> element, as shown in the following sample code.</span></span>

```xml
<services>
    <service
        type="Microsoft.ServiceModel.Samples.CalculatorService"
        behaviorConfiguration="CalculatorServiceBehavior">
       <endpoint address=""
             binding="basicHttpBinding"
             bindingConfiguration="Binding1"
             contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </service>
</services>
```

<span data-ttu-id="776e9-114">Bu örnekte, bağlama yapılandırması adlandırılır `"Binding1"` ve aşağıdaki kod örneğinde gösterildiği gibi tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="776e9-114">In this sample, the binding configuration is named `"Binding1"` and is defined as shown in the following code example.</span></span>

```xml
<bindings>
   <basicHttpBinding>
      <binding name="Binding1"
               hostNameComparisonMode="StrongWildcard"
               receiveTimeout="00:10:00"
               sendTimeout="00:10:00"
               openTimeout="00:10:00"
               closeTimeout="00:10:00"
               maxMessageSize="65536"
               maxBufferSize="65536"
               maxBufferPoolSize="524288"
               transferMode="Buffered"
               messageEncoding="Text"
               textEncoding="utf-8"
               bypassProxyOnLocal="false"
               useDefaultWebProxy="true" >
         <security mode="None" />
      </binding>
   </basicHttpBinding>
</bindings>
```

<span data-ttu-id="776e9-115">Binding öğesi, konak adı karşılaştırma modunu, en büyük ileti boyutunu, ara sunucu seçeneklerini, zaman aşımlarını, ileti kodlamasını ve diğer seçenekleri ayarlamaya yönelik öznitelikler sağlar.</span><span class="sxs-lookup"><span data-stu-id="776e9-115">The binding element provides attributes for setting the host name comparison mode, maximum message size, proxy options, timeouts, message encoding, and other options.</span></span>

<span data-ttu-id="776e9-116">Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="776e9-116">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="776e9-117">İstemcisini kapatmak için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="776e9-117">Press ENTER in the client window to shut down the client.</span></span>

```console
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714

Press <ENTER> to terminate client.
```

#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="776e9-118">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="776e9-118">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="776e9-119">Aşağıdaki komutu kullanarak ASP.NET 4,0 ' ü yükler.</span><span class="sxs-lookup"><span data-stu-id="776e9-119">Install ASP.NET 4.0 using the following command.</span></span>

    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable
    ```

2. <span data-ttu-id="776e9-120">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="776e9-120">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

3. <span data-ttu-id="776e9-121">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="776e9-121">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

4. <span data-ttu-id="776e9-122">Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="776e9-122">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>
