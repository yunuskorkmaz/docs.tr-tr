---
title: WS Taşıma Güvenliği
ms.date: 03/30/2017
ms.assetid: 33a20358-5e1b-458a-a6a9-15753bc7b99b
ms.openlocfilehash: 5023e5a0233906a0766eb307f35094768ee372a4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942157"
---
# <a name="ws-transport-security"></a><span data-ttu-id="74e2e-102">WS Taşıma Güvenliği</span><span class="sxs-lookup"><span data-stu-id="74e2e-102">WS Transport Security</span></span>
<span data-ttu-id="74e2e-103">Bu örnek, <xref:System.ServiceModel.WSHttpBinding> bağlamakla SSL Aktarım güvenliği kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="74e2e-103">This sample demonstrates the use of SSL transport security with the <xref:System.ServiceModel.WSHttpBinding> binding.</span></span> <span data-ttu-id="74e2e-104">Varsayılan olarak, `wsHttpBinding` bağlama http iletişimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="74e2e-104">By default, the `wsHttpBinding` binding provides HTTP communication.</span></span> <span data-ttu-id="74e2e-105">Aktarım güvenliği için yapılandırıldığında bağlama, HTTPS iletişimini destekler.</span><span class="sxs-lookup"><span data-stu-id="74e2e-105">When configured for transport security, the binding supports HTTPS communication.</span></span> <span data-ttu-id="74e2e-106">Bu örnek, bir Hesaplayıcı hizmeti uygulayan [kullanmaya](../../../../docs/framework/wcf/samples/getting-started-sample.md) Başlarken hizmetini temel alır.</span><span class="sxs-lookup"><span data-stu-id="74e2e-106">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="74e2e-107">, `wsHttpBinding` İstemci ve hizmet için uygulama yapılandırma dosyalarında belirtilir ve yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="74e2e-107">The `wsHttpBinding` is specified and configured in the application configuration files for the client and service.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="74e2e-108">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="74e2e-108">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="74e2e-109">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="74e2e-109">The samples may already be installed on your machine.</span></span> <span data-ttu-id="74e2e-110">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="74e2e-110">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="74e2e-111">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ' e gidin.</span><span class="sxs-lookup"><span data-stu-id="74e2e-111">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="74e2e-112">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="74e2e-112">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\wsTransportSecurity`  
  
 <span data-ttu-id="74e2e-113">Örnekteki program kodu, [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md) hizmetindekilerle aynıdır.</span><span class="sxs-lookup"><span data-stu-id="74e2e-113">The program code in the sample is identical to that of the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) service.</span></span> <span data-ttu-id="74e2e-114">Örneği oluşturmadan önce bir sertifika oluşturmalı ve Web sunucusu Sertifika sihirbazını kullanarak atamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="74e2e-114">You must create a certificate and assign it by using the Web Server Certificate Wizard before building and running the sample.</span></span> <span data-ttu-id="74e2e-115">Yapılandırma dosyası ayarlarındaki uç nokta tanımı ve bağlama tanımı, istemci için `Transport` aşağıdaki örnek yapılandırmada gösterildiği gibi güvenlik modunu etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="74e2e-115">The endpoint definition and binding definition in the configuration file settings enable `Transport` security mode, as shown in the following sample configuration for the client.</span></span>  
  
```xml  
<system.serviceModel>  
  
    <client>  
      <!-- this endpoint has an https: address -->  
      <endpoint address="https://localhost/servicemodelsamples/service.svc" binding="wsHttpBinding" bindingConfiguration="Binding1" contract="Microsoft.Samples.TransportSecurity.ICalculator"/>  
    </client>  
  
    <bindings>  
      <wsHttpBinding>  
        <!-- configure wsHttpbinding with Transport security mode  
                   and clientCredentialType as None -->  
        <binding name="Binding1">  
          <security mode="Transport">  
            <transport clientCredentialType="None"/>  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
  
  </system.serviceModel>  
```  
  
 <span data-ttu-id="74e2e-116">Belirtilen adres https://düzenini kullanır.</span><span class="sxs-lookup"><span data-stu-id="74e2e-116">The address specified uses the https:// scheme.</span></span> <span data-ttu-id="74e2e-117">Bağlama yapılandırması güvenlik modunu olarak `Transport`ayarlar.</span><span class="sxs-lookup"><span data-stu-id="74e2e-117">The binding configuration sets the security mode to `Transport`.</span></span> <span data-ttu-id="74e2e-118">Hizmetin Web. config dosyasında aynı güvenlik modu belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="74e2e-118">The same security mode must be specified in the service's Web.config file.</span></span>  
  
 <span data-ttu-id="74e2e-119">Bu örnekte kullanılan sertifika, MakeCert. exe ile oluşturulmuş bir test sertifikasıdır çünkü, tarayıcınızla, gibi bir https: adresine https://localhost/servicemodelsamples/service.svc erişmeye çalıştığınızda bir güvenlik uyarısı görünür.</span><span class="sxs-lookup"><span data-stu-id="74e2e-119">Because the certificate used in this sample is a test certificate created with Makecert.exe, a security alert appears when you try to access an https: address, such as https://localhost/servicemodelsamples/service.svc, from your browser.</span></span> <span data-ttu-id="74e2e-120">Windows Communication Foundation (WCF) istemcisinin bir test sertifikasıyla çalışmasına izin vermek için, güvenlik uyarısını bastırmak üzere istemciye bazı ek kodlar eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="74e2e-120">To allow the Windows Communication Foundation (WCF) client to work with a test certificate in place, some additional code has been added to the client to suppress the security alert.</span></span> <span data-ttu-id="74e2e-121">Üretim sertifikaları kullanılırken bu kod ve eşlik eden sınıf gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="74e2e-121">This code, and the accompanying class, is not required when using production certificates.</span></span>  

```csharp
// This code is required only for test certificates like those created by Makecert.exe.  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```

 <span data-ttu-id="74e2e-122">Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="74e2e-122">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="74e2e-123">İstemcisini kapatmak için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="74e2e-123">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="74e2e-124">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="74e2e-124">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="74e2e-125">Aşağıdaki komutu kullanarak ASP.NET 4,0 ' ü yükler.</span><span class="sxs-lookup"><span data-stu-id="74e2e-125">Install ASP.NET 4.0 using the following command.</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. <span data-ttu-id="74e2e-126">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="74e2e-126">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3. <span data-ttu-id="74e2e-127">[Internet Information Services (IIS) sunucu sertifikası yükleme yönergelerini](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="74e2e-127">Ensure that you have performed the [Internet Information Services (IIS) Server Certificate Installation Instructions](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md).</span></span>  
  
4. <span data-ttu-id="74e2e-128">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="74e2e-128">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
5. <span data-ttu-id="74e2e-129">Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="74e2e-129">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
