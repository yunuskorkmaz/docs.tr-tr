---
title: BasicBinding
ms.date: 03/30/2017
ms.assetid: 86fbeb87-4d89-4b61-9577-867e0ac12945
ms.openlocfilehash: 91ebef7ec985d3da6dc563ddbaa277d25f3172cd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33500200"
---
# <a name="basicbinding"></a><span data-ttu-id="ebbeb-102">BasicBinding</span><span class="sxs-lookup"><span data-stu-id="ebbeb-102">BasicBinding</span></span>
<span data-ttu-id="ebbeb-103">Bu örnek kullanımını gösteren `basicHttpBinding` , HTTP iletişimi ve maksimum birlikte çalışabilirliği ilk - ve second - generation ile Web hizmetleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="ebbeb-103">This sample demonstrates the use of `basicHttpBinding` that provides HTTP communication and maximum interoperability with first- and second-generation Web services.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ebbeb-104">Kurulum yordam ve yapılandırma yönergeleri Bu örneği için bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="ebbeb-104">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ebbeb-105">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="ebbeb-105">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ebbeb-106">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="ebbeb-106">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="ebbeb-107">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="ebbeb-107">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ebbeb-108">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="ebbeb-108">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Basic\Http`  
  
## <a name="sample-details"></a><span data-ttu-id="ebbeb-109">Örnek Ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="ebbeb-109">Sample Details</span></span>  
 <span data-ttu-id="ebbeb-110">Bu örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md) hesap makinesi hizmetinin uygular.</span><span class="sxs-lookup"><span data-stu-id="ebbeb-110">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span>  
  
 <span data-ttu-id="ebbeb-111">Temel bağlama varsayılan davranışı ile kullanmak için yalnızca bağlama bölüm adı gereklidir.</span><span class="sxs-lookup"><span data-stu-id="ebbeb-111">To use the basic binding with default behavior, only the binding section name is required.</span></span> <span data-ttu-id="ebbeb-112">Temel bağlama yapılandırmak ve bazı ayarlarını değiştirmek istiyorsanız, bir bağlama yapılandırması tanımlamak gereklidir.</span><span class="sxs-lookup"><span data-stu-id="ebbeb-112">If you want to configure the basic binding and change some of its settings, it is necessary to define a binding configuration.</span></span> <span data-ttu-id="ebbeb-113">Uç nokta bağlama yapılandırması adıyla kullanarak başvurmalıdır `bindingConfiguration` özniteliği <`endpoint`> Aşağıdaki örnek kodda gösterildiği gibi öğesi.</span><span class="sxs-lookup"><span data-stu-id="ebbeb-113">The endpoint must reference the binding configuration by name by using the `bindingConfiguration` attribute of the <`endpoint`> element, as shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="ebbeb-114">Bu örnekte, bağlama Yapılandırması adlı `"Binding1"` ve aşağıdaki kod örneğinde gösterildiği gibi tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="ebbeb-114">In this sample, the binding configuration is named `"Binding1"` and is defined as shown in the following code example.</span></span>  
  
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
  
 <span data-ttu-id="ebbeb-115">Bağlama öğesi, ana bilgisayar adı karşılaştırma modu, maksimum ileti boyutu, proxy seçenekleri, zaman aşımı, ileti kodlama ve diğer seçenekleri ayarlamak için öznitelikleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="ebbeb-115">The binding element provides attributes for setting the host name comparison mode, maximum message size, proxy options, timeouts, message encoding, and other options.</span></span>  
  
 <span data-ttu-id="ebbeb-116">Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="ebbeb-116">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="ebbeb-117">İstemcisi penceresinde istemciyi aşağı kapatmak için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="ebbeb-117">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ebbeb-118">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="ebbeb-118">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="ebbeb-119">Yükleme [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aşağıdaki komutu kullanarak 4.0.</span><span class="sxs-lookup"><span data-stu-id="ebbeb-119">Install [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 using the following command.</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  <span data-ttu-id="ebbeb-120">Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ebbeb-120">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3.  <span data-ttu-id="ebbeb-121">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ebbeb-121">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="ebbeb-122">Tek veya çapraz makine yapılandırmada örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ebbeb-122">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebbeb-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ebbeb-123">See Also</span></span>
