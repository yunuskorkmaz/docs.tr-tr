---
title: Özel Bağlama Güvenilir Oturum
ms.date: 03/30/2017
ms.assetid: c5fcd409-246f-4f3e-b3f1-629506ca4c04
ms.openlocfilehash: 3ccf0c603c4710c3cdac1e0dd68a4a6a2e04c2d1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33500769"
---
# <a name="custom-binding-reliable-session"></a><span data-ttu-id="8a944-102">Özel Bağlama Güvenilir Oturum</span><span class="sxs-lookup"><span data-stu-id="8a944-102">Custom Binding Reliable Session</span></span>
<span data-ttu-id="8a944-103">Özel bağlama ayrık bağlama öğeleri sıralı bir listesi tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="8a944-103">A custom binding is defined by an ordered list of discrete binding elements.</span></span> <span data-ttu-id="8a944-104">Bu örnek özel bağlama çeşitli taşıma ve kodlama öğelerini, özellikle güvenilir oturumlar etkinleştirme ileti ile nasıl yapılandırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="8a944-104">This sample demonstrates how to configure a custom binding with various transport and message encoding elements, especially enabling reliable sessions.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="8a944-105">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="8a944-105">The samples may already be installed on your machine.</span></span> <span data-ttu-id="8a944-106">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="8a944-106">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="8a944-107">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="8a944-107">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="8a944-108">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="8a944-108">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Custom\ReliableSession`  
  
## <a name="sample-details"></a><span data-ttu-id="8a944-109">Örnek Ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="8a944-109">Sample Details</span></span>  
 <span data-ttu-id="8a944-110">Güvenilir oturumlar güvenilir Mesajlaşma ve oturumlar için özellikleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="8a944-110">Reliable sessions provide features for reliable messaging and sessions.</span></span> <span data-ttu-id="8a944-111">Güvenilir Mesajlaşma iletişim başarısızlığı yeniden deneme ve teslim Güvenceleri gibi sıralı varış belirtilmesi iletilerinin sağlar.</span><span class="sxs-lookup"><span data-stu-id="8a944-111">Reliable messaging retries communication on failure and allows delivery assurances such as in-order arrival of messages to be specified.</span></span> <span data-ttu-id="8a944-112">Oturum durumu çağrıları arasında istemcileri için korur.</span><span class="sxs-lookup"><span data-stu-id="8a944-112">Sessions maintain state for clients between calls.</span></span> <span data-ttu-id="8a944-113">Örnek istemci durumunu korumak için oturumları uygular ve sıralı teslim Güvenceleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="8a944-113">The sample implements sessions for maintaining client state and specifies in-order delivery assurances.</span></span> <span data-ttu-id="8a944-114">Örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md) hesap makinesi hizmetinin uygular.</span><span class="sxs-lookup"><span data-stu-id="8a944-114">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="8a944-115">Güvenilir oturum özellikleri etkinleştirilmiş ve uygulama yapılandırma dosyaları istemci ve hizmet için yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="8a944-115">The reliable session features are enabled and configured in the application configuration files for the client and service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8a944-116">Kurulum yordam ve yapılandırma yönergeleri Bu örneği için bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="8a944-116">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="8a944-117">Bağlama öğeleri sıralama her bir katman kanal yığınında olabilmesinden dolayı bir özel bağlama, tanımlamak önemlidir (bkz [özel bağlamalar](../../../../docs/framework/wcf/extending/custom-bindings.md)).</span><span class="sxs-lookup"><span data-stu-id="8a944-117">The ordering of binding elements is important in defining a custom binding, because each represents a layer in the channel stack (see [Custom Bindings](../../../../docs/framework/wcf/extending/custom-bindings.md)).</span></span>  
  
 <span data-ttu-id="8a944-118">Örnek hizmet yapılandırması, aşağıdaki kod örneğinde gösterildiği gibi tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="8a944-118">The service configuration for the sample is defined as shown in the following code example.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service   
          name="Microsoft.ServiceModel.Samples.CalculatorService"  
          behaviorConfiguration="CalculatorServiceBehavior">  
        <!-- This endpoint is exposed at the base address provided by host: http://localhost/servicemodelsamples/service.svc  -->  
        <!-- specify customBinding binding and a binding configuration to use -->  
        <endpoint address=""  
                  binding="customBinding"  
                  bindingConfiguration="Binding1"   
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />  
        <!-- The mex endpoint is exposed at http://localhost/servicemodelsamples/service.svc/mex -->  
        <endpoint address="mex"  
                  binding="mexHttpBinding"  
                  contract="IMetadataExchange" />  
      </service>  
    </services>  
  
    <!-- custom binding configuration - configures HTTP transport, reliable sessions -->  
    <bindings>  
      <customBinding>  
        <binding name="Binding1">  
          <reliableSession />  
          <security authenticationMode="SecureConversation"  
                     requireSecurityContextCancellation="true">  
          </security>  
          <compositeDuplex />  
          <oneWay />  
          <textMessageEncoding messageVersion="Soap12WSAddressing10" writeEncoding="utf-8" />  
          <httpTransport authenticationScheme="Anonymous" bypassProxyOnLocal="false"  
                        hostNameComparisonMode="StrongWildcard"   
                        proxyAuthenticationScheme="Anonymous" realm=""   
                        useDefaultWebProxy="true" />  
        </binding>  
      </customBinding>  
    </bindings>  
  
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="CalculatorServiceBehavior">  
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceDebug includeExceptionDetailInFaults="False" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  
  </system.serviceModel>  
  
</configuration>  
```  
  
 <span data-ttu-id="8a944-119">Makineler arası senaryoda çalıştırırken, istemcinin uç nokta adresi ana bilgisayar hizmetinin yansıtacak şekilde değiştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="8a944-119">When running in a cross-machine scenario, you must change client's endpoint address to reflect the host name of the service.</span></span>  
  
 <span data-ttu-id="8a944-120">Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="8a944-120">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="8a944-121">İstemcisi penceresinde istemciyi aşağı kapatmak için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="8a944-121">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="8a944-122">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="8a944-122">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="8a944-123">Yükleme [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 aşağıdaki komutu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="8a944-123">Install [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 using the following command:</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  <span data-ttu-id="8a944-124">Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="8a944-124">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3.  <span data-ttu-id="8a944-125">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="8a944-125">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="8a944-126">Tek veya çapraz makine yapılandırmada örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="8a944-126">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="8a944-127">İstemci makineler arası yapılandırmasında çalıştırırken, "localhost" hem de değiştirdiğinizden emin olun `address` özniteliği [ \<uç noktası >](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) öğesi ve `clientBaseAddress` özniteliği [ \<compositeDuplex >](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md) aşağıdaki örnekte gösterildiği gibi uygun makine adı.</span><span class="sxs-lookup"><span data-stu-id="8a944-127">When running the client in a cross-machine configuration, be sure to replace "localhost" in both the `address` attribute of the [\<endpoint>](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) element and the `clientBaseAddress` attribute of the [\<compositeDuplex>](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md) with the name of the appropriate machine, as shown in the following example.</span></span>  
  
    ```xml  
    <endpoint name = ""  
    address="http://service_machine_name/servicemodelsamples/service.svc"  
    ... />  
    <compositeDuplex clientBaseAddress="http://client_machine_name:8000/myClient/" />  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="8a944-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8a944-128">See Also</span></span>
