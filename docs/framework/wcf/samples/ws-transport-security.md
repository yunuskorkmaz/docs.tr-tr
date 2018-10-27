---
title: WS Taşıma Güvenliği
ms.date: 03/30/2017
ms.assetid: 33a20358-5e1b-458a-a6a9-15753bc7b99b
ms.openlocfilehash: 3bc9cf3700e79b62c54c335f838c7fa660d9e780
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50180919"
---
# <a name="ws-transport-security"></a><span data-ttu-id="0ed0c-102">WS Taşıma Güvenliği</span><span class="sxs-lookup"><span data-stu-id="0ed0c-102">WS Transport Security</span></span>
<span data-ttu-id="0ed0c-103">Bu örnek, SSL Aktarım güvenliği ile kullanımını gösterir. <xref:System.ServiceModel.WSHttpBinding> bağlama.</span><span class="sxs-lookup"><span data-stu-id="0ed0c-103">This sample demonstrates the use of SSL transport security with the <xref:System.ServiceModel.WSHttpBinding> binding.</span></span> <span data-ttu-id="0ed0c-104">Varsayılan olarak, `wsHttpBinding` bağlama, HTTP iletişimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="0ed0c-104">By default, the `wsHttpBinding` binding provides HTTP communication.</span></span> <span data-ttu-id="0ed0c-105">Aktarım güvenliği için yapılandırıldığında, bağlama HTTPS iletişimini destekler.</span><span class="sxs-lookup"><span data-stu-id="0ed0c-105">When configured for transport security, the binding supports HTTPS communication.</span></span> <span data-ttu-id="0ed0c-106">Bu örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md) hesaplayıcı hizmet uygulayan.</span><span class="sxs-lookup"><span data-stu-id="0ed0c-106">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="0ed0c-107">`wsHttpBinding` Belirtilen ve uygulama yapılandırma dosyalarında istemci ve hizmet için yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="0ed0c-107">The `wsHttpBinding` is specified and configured in the application configuration files for the client and service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0ed0c-108">Bu örnek için Kurulum yordamı ve derleme yönergeleri Bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="0ed0c-108">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="0ed0c-109">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="0ed0c-109">The samples may already be installed on your machine.</span></span> <span data-ttu-id="0ed0c-110">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="0ed0c-110">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="0ed0c-111">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="0ed0c-111">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="0ed0c-112">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="0ed0c-112">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\wsTransportSecurity`  
  
 <span data-ttu-id="0ed0c-113">Örnek program kodunda olarak aynıdır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md) hizmeti.</span><span class="sxs-lookup"><span data-stu-id="0ed0c-113">The program code in the sample is identical to that of the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) service.</span></span> <span data-ttu-id="0ed0c-114">Bir sertifika oluşturun ve bunu oluşturmak ve bu örneği çalıştırmadan önce Web sunucusu sertifikası Sihirbazı'nı kullanarak atamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="0ed0c-114">You must create a certificate and assign it by using the Web Server Certificate Wizard before building and running the sample.</span></span> <span data-ttu-id="0ed0c-115">Uç nokta tanımı ve bağlama tanımı yapılandırmadaki ayarları dosya `Transport` istemci için aşağıdaki örnek yapılandırma gösterildiği gibi güvenlik modu.</span><span class="sxs-lookup"><span data-stu-id="0ed0c-115">The endpoint definition and binding definition in the configuration file settings enable `Transport` security mode, as shown in the following sample configuration for the client.</span></span>  
  
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
  
 <span data-ttu-id="0ed0c-116">Belirtilen adresi https:// şeması kullanır.</span><span class="sxs-lookup"><span data-stu-id="0ed0c-116">The address specified uses the https:// scheme.</span></span> <span data-ttu-id="0ed0c-117">Bağlama yapılandırması güvenlik modunu ayarlar `Transport`.</span><span class="sxs-lookup"><span data-stu-id="0ed0c-117">The binding configuration sets the security mode to `Transport`.</span></span> <span data-ttu-id="0ed0c-118">Aynı güvenlik modu, hizmetin Web.config dosyasında belirtilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="0ed0c-118">The same security mode must be specified in the service's Web.config file.</span></span>  
  
 <span data-ttu-id="0ed0c-119">Bu örnekte kullanılan sertifika Makecert.exe ile oluşturulan bir test sertifikası olduğundan, bir https erişmeye çalıştığınızda bir güvenlik uyarısı görünür: adres gibi https://localhost/servicemodelsamples/service.svc, tarayıcınız üzerinden.</span><span class="sxs-lookup"><span data-stu-id="0ed0c-119">Because the certificate used in this sample is a test certificate created with Makecert.exe, a security alert appears when you try to access an https: address, such as https://localhost/servicemodelsamples/service.svc, from your browser.</span></span> <span data-ttu-id="0ed0c-120">Yerinde bir test sertifikası ile iş Windows Communication Foundation (WCF) istemci izin vermek için güvenlik uyarıyı gizlemek için istemci için bazı ek kod eklendi.</span><span class="sxs-lookup"><span data-stu-id="0ed0c-120">To allow the Windows Communication Foundation (WCF) client to work with a test certificate in place, some additional code has been added to the client to suppress the security alert.</span></span> <span data-ttu-id="0ed0c-121">Bu kod, eşlik eden sınıfı değil ve gerekli üretim sertifikalar kullanıldığında.</span><span class="sxs-lookup"><span data-stu-id="0ed0c-121">This code, and the accompanying class, is not required when using production certificates.</span></span>  

```csharp
// This code is required only for test certificates like those created by Makecert.exe.  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```

 <span data-ttu-id="0ed0c-122">Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="0ed0c-122">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="0ed0c-123">İstemci bilgisayarı için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="0ed0c-123">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="0ed0c-124">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="0ed0c-124">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="0ed0c-125">Yükleme [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aşağıdaki komutu kullanarak 4.0.</span><span class="sxs-lookup"><span data-stu-id="0ed0c-125">Install [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 using the following command.</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  <span data-ttu-id="0ed0c-126">Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="0ed0c-126">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3.  <span data-ttu-id="0ed0c-127">Gerçekleştirdiğinizden emin olmak [Internet Information Services (IIS) sunucu sertifikası yükleme yönergeleri](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md).</span><span class="sxs-lookup"><span data-stu-id="0ed0c-127">Ensure that you have performed the [Internet Information Services (IIS) Server Certificate Installation Instructions](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md).</span></span>  
  
4.  <span data-ttu-id="0ed0c-128">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="0ed0c-128">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
5.  <span data-ttu-id="0ed0c-129">Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="0ed0c-129">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ed0c-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0ed0c-130">See Also</span></span>
