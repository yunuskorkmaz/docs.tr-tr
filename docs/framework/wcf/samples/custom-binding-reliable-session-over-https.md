---
title: HTTPS Üzerinden Özel Bağlama Güvenli Oturum
ms.date: 03/30/2017
ms.assetid: 16aaa80d-3ffe-47c4-8b16-ec65c4d25f8d
ms.openlocfilehash: 051e7f56662a2ca67018ae7dd29189ff50245fc8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183871"
---
# <a name="custom-binding-reliable-session-over-https"></a><span data-ttu-id="2fe34-102">HTTPS Üzerinden Özel Bağlama Güvenli Oturum</span><span class="sxs-lookup"><span data-stu-id="2fe34-102">Custom Binding Reliable Session over HTTPS</span></span>
<span data-ttu-id="2fe34-103">Bu örnek, Güvenilir Oturumlar ile SSL taşıma güvenliği kullanımını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="2fe34-103">This sample demonstrates the use of SSL transport security with Reliable Sessions.</span></span> <span data-ttu-id="2fe34-104">Güvenilir Oturumlar, WS-Güvenilir Mesajlaşma protokolünü uygular.</span><span class="sxs-lookup"><span data-stu-id="2fe34-104">Reliable Sessions implements the WS-Reliable Messaging protocol.</span></span> <span data-ttu-id="2fe34-105">Güvenilir Oturumlar üzerinden WS-Security oluşturarak güvenli ve güvenilir bir oturum alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2fe34-105">You can have a secure reliable session by composing WS-Security over Reliable Sessions.</span></span> <span data-ttu-id="2fe34-106">Ancak bazen, bunun yerine SSL ile HTTP aktarım güvenliğini kullanmayı seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2fe34-106">But sometimes, you may choose to instead use HTTP transport security with SSL.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="2fe34-107">Numuneler makinenize zaten yüklenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="2fe34-107">The samples may already be installed on your machine.</span></span> <span data-ttu-id="2fe34-108">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="2fe34-108">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="2fe34-109">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="2fe34-109">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="2fe34-110">Bu örnek aşağıdaki dizinde yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="2fe34-110">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Custom\ReliableSessionOverHttps`  
  
## <a name="sample-details"></a><span data-ttu-id="2fe34-111">Örnek Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="2fe34-111">Sample Details</span></span>  
 <span data-ttu-id="2fe34-112">SSL, paketlerin kendilerinin güvende olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="2fe34-112">SSL ensures that the packets themselves are secured.</span></span> <span data-ttu-id="2fe34-113">Bunun WS-Secure Conversation'ı kullanarak güvenilir oturumu güvence altına almaktan farklı olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="2fe34-113">It is important to note that this is different from securing the reliable session using WS-Secure Conversation.</span></span>  
  
 <span data-ttu-id="2fe34-114">HTTPS üzerinden güvenilir oturum kullanmak için özel bir bağlama oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="2fe34-114">To use reliable session over HTTPS, you must create a custom binding.</span></span> <span data-ttu-id="2fe34-115">Bu örnek, bir hesap makinesi hizmeti uygulayan [Başlarken'e](../../../../docs/framework/wcf/samples/getting-started-sample.md) dayanır.</span><span class="sxs-lookup"><span data-stu-id="2fe34-115">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="2fe34-116">Güvenilir oturum bağlama öğesi ve [ \<httpsTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/httpstransport.md)kullanılarak özel bir bağlama oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="2fe34-116">A custom binding is created using the reliable session binding element and the [\<httpsTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/httpstransport.md).</span></span> <span data-ttu-id="2fe34-117">Aşağıdaki yapılandırma özel bağlama dır.</span><span class="sxs-lookup"><span data-stu-id="2fe34-117">The following configuration is of the custom binding.</span></span>  
  
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
  
 <span data-ttu-id="2fe34-118">Örnekteki program kodu, [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md) hizmetiyle aynıdır.</span><span class="sxs-lookup"><span data-stu-id="2fe34-118">The program code in the sample is identical to that of the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) service.</span></span> <span data-ttu-id="2fe34-119">Örneği oluşturmadan ve çalıştırmadan önce Web Sunucusu Sertifika Sihirbazı'nı kullanarak bir sertifika oluşturmanız ve atamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="2fe34-119">You must create a certificate and assign it by using the Web Server Certificate Wizard before building and running the sample.</span></span> <span data-ttu-id="2fe34-120">Yapılandırma dosyası ayarlarındaki uç nokta tanımı ve bağlama tanımı, istemci için aşağıdaki örnek yapılandırmada gösterildiği gibi özel bağlama kullanımını sağlar.</span><span class="sxs-lookup"><span data-stu-id="2fe34-120">The endpoint definition and binding definition in the configuration file settings enable the use of custom binding as shown in the following sample configuration for the client.</span></span>  
  
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
  
 <span data-ttu-id="2fe34-121">Belirtilen adres https:// düzenini kullanır.</span><span class="sxs-lookup"><span data-stu-id="2fe34-121">The address specified uses the https:// scheme.</span></span>  
  
 <span data-ttu-id="2fe34-122">Bu örnekte kullanılan sertifika Makecert.exe ile oluşturulmuş bir test sertifikası olduğundan, tarayıcınızdan bir https adresine https://localhost/servicemodelsamples/service.svcerişmeye çalıştığınızda bir güvenlik uyarısı görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="2fe34-122">Because the certificate used in this sample is a test certificate created with Makecert.exe, a security alert appears when you try to access an https: address, such as https://localhost/servicemodelsamples/service.svc, from your browser.</span></span> <span data-ttu-id="2fe34-123">Windows Communication Foundation (WCF) istemcisinin yerinde bir test sertifikasıyla çalışmasına izin vermek için, istemciye güvenlik uyarısını bastırmak için bazı ek kodlar eklendi.</span><span class="sxs-lookup"><span data-stu-id="2fe34-123">To allow the Windows Communication Foundation (WCF) client to work with a test certificate in place, some additional code has been added to the client to suppress the security alert.</span></span> <span data-ttu-id="2fe34-124">Üretim sertifikaları kullanırken bu kod ve beraberindeki sınıf gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="2fe34-124">This code, and the accompanying class, is not required when using production certificates.</span></span>  

```csharp
// This code is required only for test certificates like those created by Makecert.exe.  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```

 <span data-ttu-id="2fe34-125">Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="2fe34-125">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="2fe34-126">İstemciyi kapatmak için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="2fe34-126">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="2fe34-127">Örneği ayarlamak, oluşturmak ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="2fe34-127">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="2fe34-128">Aşağıdaki komutu kullanarak 4.0 ASP.NET yükleyin.</span><span class="sxs-lookup"><span data-stu-id="2fe34-128">Install  ASP.NET 4.0 using the following command.</span></span>  
  
    ```console  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. <span data-ttu-id="2fe34-129">Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.</span><span class="sxs-lookup"><span data-stu-id="2fe34-129">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3. <span data-ttu-id="2fe34-130">Internet Information Services [(IIS) Server Certificate Kurulum Yönergesi'ni](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md)gerçekleştirdiğinizi belirtin.</span><span class="sxs-lookup"><span data-stu-id="2fe34-130">Ensure that you have performed the [Internet Information Services (IIS) Server Certificate Installation Instructions](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md).</span></span>  
  
4. <span data-ttu-id="2fe34-131">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak [için, Windows Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="2fe34-131">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
5. <span data-ttu-id="2fe34-132">Örneği tek veya çapraz makine yapılandırmasında çalıştırmak için, [Windows Communication Foundation Samples'ı çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="2fe34-132">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
