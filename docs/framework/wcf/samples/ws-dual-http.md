---
description: 'Daha fazla bilgi edinin: WS Dual http'
title: WS İkili Http
ms.date: 03/30/2017
ms.assetid: 9997eba5-29ec-48db-86f3-fa77b241fb1a
ms.openlocfilehash: 44245691a47982f427c82cf8ad81ac2dd8f0b557
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99715008"
---
# <a name="ws-dual-http"></a><span data-ttu-id="dff60-103">WS İkili Http</span><span class="sxs-lookup"><span data-stu-id="dff60-103">WS Dual Http</span></span>

<span data-ttu-id="dff60-104">Çift http örneği, bağlamanın nasıl yapılandırılacağını gösterir `WSDualHttpBinding` .</span><span class="sxs-lookup"><span data-stu-id="dff60-104">The Dual Http sample demonstrates how to configure the `WSDualHttpBinding` binding.</span></span> <span data-ttu-id="dff60-105">Bu örnek, Internet Information Services (IIS) tarafından barındırılan bir istemci konsol programından (. exe) ve hizmet kitaplığından (. dll) oluşur.</span><span class="sxs-lookup"><span data-stu-id="dff60-105">This sample consists of a client console program (.exe) and a service library (.dll) hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="dff60-106">Hizmet bir çift yönlü sözleşme uygular.</span><span class="sxs-lookup"><span data-stu-id="dff60-106">The service implements a duplex contract.</span></span> <span data-ttu-id="dff60-107">Sözleşme, `ICalculatorDuplex` matematik işlemlerini (ekleme, çıkarma, çarpma ve bölme) sunan arabirim tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="dff60-107">The contract is defined by the `ICalculatorDuplex` interface, which exposes math operations (Add, Subtract, Multiply, and Divide).</span></span> <span data-ttu-id="dff60-108">Bu örnekte `ICalculatorDuplex` arabirim, istemcinin, oturum üzerinde çalışan bir sonucu hesaplamak için matematik işlemleri gerçekleştirmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="dff60-108">In this sample, the `ICalculatorDuplex` interface allows the client to perform math operations, calculating a running result over the session.</span></span> <span data-ttu-id="dff60-109">Bağımsız olarak, hizmet sonuçları `ICalculatorDuplexCallback` arayüzde döndürür.</span><span class="sxs-lookup"><span data-stu-id="dff60-109">Independently, the service returns results on the `ICalculatorDuplexCallback` interface.</span></span> <span data-ttu-id="dff60-110">Bir çift yönlü sözleşme, istemci ve hizmet arasında gönderilen ileti kümesiyle ilişkilendirilmesi için bir bağlam kurulması gerektiğinden oturum gerektirir.</span><span class="sxs-lookup"><span data-stu-id="dff60-110">A duplex contract requires a session, because a context must be established to correlate the set of messages being sent between client and service.</span></span> <span data-ttu-id="dff60-111">`WSDualHttpBinding`Bağlama çift yönlü iletişimi destekler.</span><span class="sxs-lookup"><span data-stu-id="dff60-111">The `WSDualHttpBinding` binding supports duplex communication.</span></span>

> [!NOTE]
> <span data-ttu-id="dff60-112">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="dff60-112">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="dff60-113">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="dff60-113">The samples may already be installed on your machine.</span></span> <span data-ttu-id="dff60-114">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="dff60-114">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="dff60-115">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="dff60-115">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="dff60-116">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="dff60-116">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\DualHttp`

<span data-ttu-id="dff60-117">İle bir hizmet uç noktası yapılandırmak için `WSDualHttpBinding` , uç nokta yapılandırmasındaki bağlamayı gösterildiği gibi belirtin.</span><span class="sxs-lookup"><span data-stu-id="dff60-117">To configure a service endpoint with the `WSDualHttpBinding`, specify the binding in the endpoint configuration as shown.</span></span>

```xml
<endpoint address=""
         binding="wsDualHttpBinding"
         contract="Microsoft.ServiceModel.Samples.ICalculatorDuplex" />
```

<span data-ttu-id="dff60-118">İstemcisinde, aşağıdaki örnek yapılandırmada gösterildiği gibi sunucunun istemciye bağlanmak için kullanabileceği bir adresi yapılandırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="dff60-118">On the client, you must configure an address that the server can use to connect to the client as shown in the following sample configuration.</span></span>

```xml
<system.serviceModel>
  <client>
    <endpoint address=
         "http://localhost/servicemodelsamples/service.svc"
         binding="wsDualHttpBinding"
         bindingConfiguration="Binding1"
         contract="Microsoft.ServiceModel.Samples.ICalculatorDuplex" />
  </client>

  <bindings>
    <!-- Configure a WSDualHttpBinding that supports duplex -->
    <!-- communication. -->
    <wsDualHttpBinding>
      <binding name="Binding1"
               clientBaseAddress="http://localhost:8000/myClient/"
               useDefaultWebProxy="true"
               bypassProxyOnLocal="false">
      </binding>
    </wsDualHttpBinding>
  </bindings>
</system.serviceModel>
```

<span data-ttu-id="dff60-119">Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="dff60-119">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="dff60-120">İstemcisini kapatmak için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="dff60-120">Press ENTER in the client window to shut down the client.</span></span>

```console
Press <ENTER> to terminate client once the output is displayed.

Result(100)
Result(50)
Result(882.5)
Result(441.25)
Equation(0 + 100 - 50 * 17.65 / 2 = 441.25)
```

<span data-ttu-id="dff60-121">Örneği çalıştırdığınızda, hizmetten gönderilen geri çağırma arabirimindeki istemciye döndürülen iletileri görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="dff60-121">When you run the sample, you see the messages returned to the client on the callback interface sent from the service.</span></span> <span data-ttu-id="dff60-122">Her ara sonuç görüntülenir ve tüm işlemler tamamlandıktan sonra denklemin tamamı gelir.</span><span class="sxs-lookup"><span data-stu-id="dff60-122">Each intermediate result is displayed, followed by the entire equation upon completion of all operations.</span></span> <span data-ttu-id="dff60-123">İstemcisini kapatmak için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="dff60-123">Press ENTER to shut down the client.</span></span>

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="dff60-124">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="dff60-124">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="dff60-125">Aşağıdaki komutu kullanarak ASP.NET 4,0 ' ü yükler.</span><span class="sxs-lookup"><span data-stu-id="dff60-125">Install ASP.NET 4.0 using the following command.</span></span>

    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable
    ```

2. <span data-ttu-id="dff60-126">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="dff60-126">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

3. <span data-ttu-id="dff60-127">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="dff60-127">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

4. <span data-ttu-id="dff60-128">Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="dff60-128">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="dff60-129">İstemciyi bir çapraz makine yapılandırmasında çalıştırırken, yerel `address` olarak hem öğenin özniteliğinde [ \<endpoint> \<client> hem de öğesi öğesinin](../../configure-apps/file-schema/wcf/endpoint-of-client.md) `clientBaseAddress` özniteliği [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) [\<wsDualHttpBinding>](../../configure-apps/file-schema/wcf/wsdualhttpbinding.md) gösterildiği gibi uygun makinenin adı ile aynı şekilde değiştirdiğinizden emin olun:</span><span class="sxs-lookup"><span data-stu-id="dff60-129">When running the client in a cross-machine configuration, be sure to replace localhost in both the `address` attribute of the [\<endpoint> of \<client>](../../configure-apps/file-schema/wcf/endpoint-of-client.md) element and the `clientBaseAddress` attribute of the [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element of the [\<wsDualHttpBinding>](../../configure-apps/file-schema/wcf/wsdualhttpbinding.md) element with the name of the appropriate machine, as shown:</span></span>

    ```xml
    <client>
        <endpoint name = ""
          address=
         "http://service_machine_name/servicemodelsamples/service.svc"
        />
    </client>
    ...
    <wsDualHttpBinding>
        <binding name="DuplexBinding" clientBaseAddress=
            "http://client_machine_name:8000/myClient/">
        </binding>
    </wsDualHttpBinding>
    ```
