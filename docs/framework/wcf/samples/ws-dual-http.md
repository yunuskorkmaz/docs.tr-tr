---
title: WS İkili Http
ms.date: 03/30/2017
ms.assetid: 9997eba5-29ec-48db-86f3-fa77b241fb1a
ms.openlocfilehash: 8141ee85fa1d38c3f190688981ce66a9dd9c88f4
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59306215"
---
# <a name="ws-dual-http"></a><span data-ttu-id="5a4f4-102">WS İkili Http</span><span class="sxs-lookup"><span data-stu-id="5a4f4-102">WS Dual Http</span></span>
<span data-ttu-id="5a4f4-103">İkili Http örnek nasıl yapılandırılacağını gösteren `WSDualHttpBinding` bağlama.</span><span class="sxs-lookup"><span data-stu-id="5a4f4-103">The Dual Http sample demonstrates how to configure the `WSDualHttpBinding` binding.</span></span> <span data-ttu-id="5a4f4-104">Bu örnek, bir istemci konsol program (.exe) ve Internet Information Services (IIS) tarafından barındırılan bir hizmet kitaplığı (.dll) oluşur.</span><span class="sxs-lookup"><span data-stu-id="5a4f4-104">This sample consists of a client console program (.exe) and a service library (.dll) hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="5a4f4-105">Hizmet, çift yönlü sözleşme uygular.</span><span class="sxs-lookup"><span data-stu-id="5a4f4-105">The service implements a duplex contract.</span></span> <span data-ttu-id="5a4f4-106">Anlaşma tarafından tanımlanan `ICalculatorDuplex` matematik işlemlerinden sunan arabirimi (ekleme, çıkarma, çarpma ve bölme).</span><span class="sxs-lookup"><span data-stu-id="5a4f4-106">The contract is defined by the `ICalculatorDuplex` interface, which exposes math operations (Add, Subtract, Multiply, and Divide).</span></span> <span data-ttu-id="5a4f4-107">Bu örnekte `ICalculatorDuplex` oturumu üzerinden çalışan bir sonuç hesaplama matematik işlemlerini gerçekleştirmek üzere istemci arabirimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="5a4f4-107">In this sample, the `ICalculatorDuplex` interface allows the client to perform math operations, calculating a running result over the session.</span></span> <span data-ttu-id="5a4f4-108">Bağımsız olarak, hizmet üzerinde sonuçları döndüren `ICalculatorDuplexCallback` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="5a4f4-108">Independently, the service returns results on the `ICalculatorDuplexCallback` interface.</span></span> <span data-ttu-id="5a4f4-109">Hizmet ve istemci arasında gönderilen ileti kümesini ilişkilendirmek için bir bağlamı yeniden kurulması için çift yönlü sözleşme bir oturumu gerektirir.</span><span class="sxs-lookup"><span data-stu-id="5a4f4-109">A duplex contract requires a session, because a context must be established to correlate the set of messages being sent between client and service.</span></span> <span data-ttu-id="5a4f4-110">`WSDualHttpBinding` Bağlama, çift yönlü iletişimi destekler.</span><span class="sxs-lookup"><span data-stu-id="5a4f4-110">The `WSDualHttpBinding` binding supports duplex communication.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5a4f4-111">Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="5a4f4-111">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="5a4f4-112">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="5a4f4-112">The samples may already be installed on your machine.</span></span> <span data-ttu-id="5a4f4-113">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="5a4f4-113">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="5a4f4-114">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="5a4f4-114">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5a4f4-115">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="5a4f4-115">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\DualHttp`  
  
 <span data-ttu-id="5a4f4-116">Bir hizmet uç noktası ile yapılandırmak için `WSDualHttpBinding`, gösterildiği gibi uç nokta yapılandırmasında bağlama belirtin.</span><span class="sxs-lookup"><span data-stu-id="5a4f4-116">To configure a service endpoint with the `WSDualHttpBinding`, specify the binding in the endpoint configuration as shown.</span></span>  
  
```xml  
<endpoint address=""  
         binding="wsDualHttpBinding"  
         contract="Microsoft.ServiceModel.Samples.ICalculatorDuplex" />  
```  
  
 <span data-ttu-id="5a4f4-117">İstemcide, sunucu istemciye aşağıdaki örnek yapılandırmada gösterildiği bağlanmak için kullanabileceği bir adresi yapılandırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="5a4f4-117">On the client, you must configure an address that the server can use to connect to the client as shown in the following sample configuration.</span></span>  
  
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
  
 <span data-ttu-id="5a4f4-118">Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="5a4f4-118">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="5a4f4-119">İstemci bilgisayarı için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="5a4f4-119">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Press <ENTER> to terminate client once the output is displayed.  
  
Result(100)  
Result(50)  
Result(882.5)  
Result(441.25)  
Equation(0 + 100 - 50 * 17.65 / 2 = 441.25)  
```  
  
 <span data-ttu-id="5a4f4-120">Örneği çalıştırdığında üzerinde istemciye döndürülen iletileri bkz hizmetinden gönderilen geri çağırma arabirimi.</span><span class="sxs-lookup"><span data-stu-id="5a4f4-120">When you run the sample, you see the messages returned to the client on the callback interface sent from the service.</span></span> <span data-ttu-id="5a4f4-121">Tüm işlemler tamamlandıktan sonra tüm denklemi ardından her ara sonuçlar görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="5a4f4-121">Each intermediate result is displayed, followed by the entire equation upon completion of all operations.</span></span> <span data-ttu-id="5a4f4-122">İstemciyi aşağı kapatmak için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="5a4f4-122">Press ENTER to shut down the client.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="5a4f4-123">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="5a4f4-123">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="5a4f4-124">Yükleme [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aşağıdaki komutu kullanarak 4.0.</span><span class="sxs-lookup"><span data-stu-id="5a4f4-124">Install [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 using the following command.</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. <span data-ttu-id="5a4f4-125">Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5a4f4-125">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3. <span data-ttu-id="5a4f4-126">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5a4f4-126">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="5a4f4-127">Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5a4f4-127">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="5a4f4-128">İstemci bir çapraz makine yapılandırmaya çalışırken, hem de localhost değiştirmeyi unutmayın `address` özniteliği [ \<uç noktası >'ın \<istemci >](../../configure-apps/file-schema/wcf/endpoint-of-client.md) öğesi ve `clientBaseAddress` öznitelik [ \<bağlama >](../../../../docs/framework/misc/binding.md) öğesinin [ \<wsDualHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md) öğesi ile gösterildiği gibi uygun makine adı:</span><span class="sxs-lookup"><span data-stu-id="5a4f4-128">When running the client in a cross-machine configuration, be sure to replace localhost in both the `address` attribute of the [\<endpoint> of \<client>](../../configure-apps/file-schema/wcf/endpoint-of-client.md) element and the `clientBaseAddress` attribute of the [\<binding>](../../../../docs/framework/misc/binding.md) element of the [\<wsDualHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md) element with the name of the appropriate machine, as shown:</span></span>  
  
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
