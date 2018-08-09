---
title: HTTPS Üzerinden Özel Bağlama Güvenli Oturum
ms.date: 03/30/2017
ms.assetid: 16aaa80d-3ffe-47c4-8b16-ec65c4d25f8d
ms.openlocfilehash: d470a4e0af655a8a7895c1db6c2699796f3db933
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33502953"
---
# <a name="custom-binding-reliable-session-over-https"></a><span data-ttu-id="d0511-102">HTTPS Üzerinden Özel Bağlama Güvenli Oturum</span><span class="sxs-lookup"><span data-stu-id="d0511-102">Custom Binding Reliable Session over HTTPS</span></span>
<span data-ttu-id="d0511-103">Bu örnek güvenilir oturumlar ile taşıma güvenliği SSL kullanımını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="d0511-103">This sample demonstrates the use of SSL transport security with Reliable Sessions.</span></span> <span data-ttu-id="d0511-104">Güvenilir oturumlar WS güvenilir Mesajlaşma Protokolü uygular.</span><span class="sxs-lookup"><span data-stu-id="d0511-104">Reliable Sessions implements the WS-Reliable Messaging protocol.</span></span> <span data-ttu-id="d0511-105">WS güvenliği güvenilir oturumlar oluşturma tarafından güvenli bir güvenilir oturum olabilir.</span><span class="sxs-lookup"><span data-stu-id="d0511-105">You can have a secure reliable session by composing WS-Security over Reliable Sessions.</span></span> <span data-ttu-id="d0511-106">Ancak bazı durumlarda, HTTP taşıma güvenliği SSL ile kullanmayı tercih edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d0511-106">But sometimes, you may choose to instead use HTTP transport security with SSL.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d0511-107">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="d0511-107">The samples may already be installed on your machine.</span></span> <span data-ttu-id="d0511-108">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="d0511-108">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="d0511-109">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="d0511-109">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d0511-110">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="d0511-110">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Custom\ReliableSessionOverHttps`  
  
## <a name="sample-details"></a><span data-ttu-id="d0511-111">Örnek Ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="d0511-111">Sample Details</span></span>  
 <span data-ttu-id="d0511-112">SSL paketleri korumalıdır sağlar.</span><span class="sxs-lookup"><span data-stu-id="d0511-112">SSL ensures that the packets themselves are secured.</span></span> <span data-ttu-id="d0511-113">WS-güvenli konuşma kullanarak güvenilir oturum güvenliğini sağlamaktan farklı olduğunu dikkate almak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="d0511-113">It is important to note that this is different from securing the reliable session using WS-Secure Conversation.</span></span>  
  
 <span data-ttu-id="d0511-114">Güvenilir oturum HTTPS üzerinden kullanmak için özel bağlama oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d0511-114">To use reliable session over HTTPS, you must create a custom binding.</span></span> <span data-ttu-id="d0511-115">Bu örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md) hesap makinesi hizmetinin uygular.</span><span class="sxs-lookup"><span data-stu-id="d0511-115">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="d0511-116">Özel bağlama güvenilir oturum bağlama öğesi kullanılarak oluşturulur ve [ \<httpsTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/httpstransport.md).</span><span class="sxs-lookup"><span data-stu-id="d0511-116">A custom binding is created using the reliable session binding element and the [\<httpsTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/httpstransport.md).</span></span> <span data-ttu-id="d0511-117">Özel bağlama yapılandırmasıdır.</span><span class="sxs-lookup"><span data-stu-id="d0511-117">The following configuration is of the custom binding.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service   
          name="Microsoft.ServiceModel.Samples.CalculatorService"  
          behaviorConfiguration="CalculatorServiceBehavior">  
        <!-- use base address provided by host -->  
        <endpoint address=""  
                  binding="customBinding"  
                  bindingConfiguration="reliableSessionOverHttps"   
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />  
        <!-- the mex endpoint is exposed as http://localhost/servicemodelsamples/service.svc/mex-->  
        <endpoint address="mex"  
                  binding="mexHttpBinding"  
                  contract="IMetadataExchange"/>  
      </service>  
    </services>  
  
    <bindings>  
      <customBinding>  
        <binding name="reliableSessionOverHttps">  
          <reliableSession />  
          <httpsTransport />  
        </binding>  
      </customBinding>  
    </bindings>  
  
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="CalculatorServiceBehavior">  
          <serviceMetadata httpGetEnabled="true" />  
          <serviceDebug includeExceptionDetailInFaults="False" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  
  </system.serviceModel>  
  
</configuration>  
```  
  
 <span data-ttu-id="d0511-118">Örnek program kodunda olarak aynıdır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md) hizmet.</span><span class="sxs-lookup"><span data-stu-id="d0511-118">The program code in the sample is identical to that of the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) service.</span></span> <span data-ttu-id="d0511-119">Bir sertifika oluşturun ve oluşturmaya ve örnek çalıştırmaya önce Web Sunucusu Sertifika Sihirbazı'nı kullanarak atamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d0511-119">You must create a certificate and assign it by using the Web Server Certificate Wizard before building and running the sample.</span></span> <span data-ttu-id="d0511-120">Yapılandırma dosyası ayarları bağlama tanımında ve uç nokta tanımı istemci için aşağıdaki örnek yapılandırma gösterildiği gibi özel bağlama kullanımını etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="d0511-120">The endpoint definition and binding definition in the configuration file settings enable the use of custom binding as shown in the following sample configuration for the client.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.serviceModel>  
  
    <client>  
      <!-- this endpoint has an https: address -->  
      <endpoint name=""  
                address="https://localhost/servicemodelsamples/service.svc"   
                binding="customBinding"   
                bindingConfiguration="reliableSessionOverHttps"   
                contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    </client>  
  
      <bindings>  
        <customBinding>  
          <binding name="reliableSessionOverHttps">  
            <reliableSession />  
            <httpsTransport />  
          </binding>  
        </customBinding>        
    </bindings>  
  
  </system.serviceModel>  
  
</configuration>  
```  
  
 <span data-ttu-id="d0511-121">Belirtilen adres https:// düzenini kullanır.</span><span class="sxs-lookup"><span data-stu-id="d0511-121">The address specified uses the https:// scheme.</span></span>  
  
 <span data-ttu-id="d0511-122">Bu örnekte kullanılan sertifikanın Makecert.exe ile oluşturulan bir test sertifikası olduğundan, bir https erişmeye çalıştığınızda bir güvenlik uyarısı görünür: gibi adres https://localhost/servicemodelsamples/service.svc, tarayıcınızdan.</span><span class="sxs-lookup"><span data-stu-id="d0511-122">Because the certificate used in this sample is a test certificate created with Makecert.exe, a security alert appears when you try to access an https: address, such as https://localhost/servicemodelsamples/service.svc, from your browser.</span></span> <span data-ttu-id="d0511-123">Bir test sertifikası yerinde çalışmak Windows Communication Foundation (WCF) istemcinin sağlamak için bazı ek kod güvenlik uyarıyı gizlemek için istemciye eklendi.</span><span class="sxs-lookup"><span data-stu-id="d0511-123">To allow the Windows Communication Foundation (WCF) client to work with a test certificate in place, some additional code has been added to the client to suppress the security alert.</span></span> <span data-ttu-id="d0511-124">Bu kod, eşlik eden sınıfı değil ve gerekli üretim sertifikalar kullanıldığında.</span><span class="sxs-lookup"><span data-stu-id="d0511-124">This code, and the accompanying class, is not required when using production certificates.</span></span>  

```csharp
// This code is required only for test certificates like those created by Makecert.exe.  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```

 <span data-ttu-id="d0511-125">Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="d0511-125">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="d0511-126">İstemcisi penceresinde istemciyi aşağı kapatmak için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="d0511-126">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="d0511-127">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="d0511-127">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="d0511-128">Yükleme [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aşağıdaki komutu kullanarak 4.0.</span><span class="sxs-lookup"><span data-stu-id="d0511-128">Install  [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 using the following command.</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  <span data-ttu-id="d0511-129">Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d0511-129">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3.  <span data-ttu-id="d0511-130">Gerçekleştirmiş emin olun [Internet Information Services (IIS) sunucu sertifikası yükleme yönergeleri](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md).</span><span class="sxs-lookup"><span data-stu-id="d0511-130">Ensure that you have performed the [Internet Information Services (IIS) Server Certificate Installation Instructions](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md).</span></span>  
  
4.  <span data-ttu-id="d0511-131">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d0511-131">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
5.  <span data-ttu-id="d0511-132">Tek veya çapraz makine yapılandırmada örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d0511-132">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0511-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d0511-133">See Also</span></span>
