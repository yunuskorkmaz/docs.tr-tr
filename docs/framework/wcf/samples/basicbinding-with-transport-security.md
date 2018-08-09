---
title: Taşıma Güvenliği ile BasicBinding
ms.date: 03/30/2017
ms.assetid: f49b1de6-0254-4362-8ef2-fccd8ff9688b
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 9591c3556bf38d1af288c2c3c4a465af2c0722eb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33502695"
---
# <a name="basicbinding-with-transport-security"></a><span data-ttu-id="a95e5-102">Taşıma Güvenliği ile BasicBinding</span><span class="sxs-lookup"><span data-stu-id="a95e5-102">BasicBinding with Transport Security</span></span>
<span data-ttu-id="a95e5-103">Bu örnek temel bağlama ile taşıma güvenliği SSL kullanımını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="a95e5-103">This sample demonstrates the use of SSL transport security with the basic binding.</span></span> <span data-ttu-id="a95e5-104">Bu örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md) hesap makinesi hizmetinin uygular.</span><span class="sxs-lookup"><span data-stu-id="a95e5-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a95e5-105">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="a95e5-105">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a95e5-106">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="a95e5-106">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="a95e5-107">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="a95e5-107">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a95e5-108">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="a95e5-108">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Basic\TransportSecurity`  
  
## <a name="sample-details"></a><span data-ttu-id="a95e5-109">Örnek Ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="a95e5-109">Sample Details</span></span>  
 <span data-ttu-id="a95e5-110">Varsayılan olarak, temel bağlama HTTP iletişimi destekler.</span><span class="sxs-lookup"><span data-stu-id="a95e5-110">By default, the basic binding supports HTTP communication.</span></span> <span data-ttu-id="a95e5-111">Örnek temel bağlama için taşıma güvenliğini etkinleştir gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="a95e5-111">The sample shows how to enable transport security for the basic binding.</span></span> <span data-ttu-id="a95e5-112">Örneği çalıştırmadan önce bir sertifika oluşturabilir ve Web Sunucusu Sertifika Sihirbazı'nı kullanarak atamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a95e5-112">Before you run the sample, you must create a certificate and assign it by using the Web Server Certificate Wizard.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a95e5-113">Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="a95e5-113">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="a95e5-114">Örnek program kodunda olarak aynıdır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md) hizmet.</span><span class="sxs-lookup"><span data-stu-id="a95e5-114">The program code in the sample is identical to that of the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) service.</span></span> <span data-ttu-id="a95e5-115">Yapılandırma dosyası ayarları bağlama tanımında ve uç nokta tanımı güvenli iletişim sağlamak için aşağıdaki örnek yapılandırmada gösterildiği şekilde değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="a95e5-115">The endpoint definition and binding definition in the configuration file settings are modified to enable secure communication, as shown in the following sample configuration.</span></span>  
  
```xml  
<system.serviceModel>  
  <services>  
    <service type="Microsoft.ServiceModel.Samples.CalculatorService"  
             behaviorConfiguration="CalculatorServiceBehavior">  
      <endpoint address=""  
                binding="basicHttpBinding"  
                bindingConfiguration="Binding1"   
                contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    </service>  
   </services>  
  <bindings>  
    <basicHttpBinding>  
      <!-- Configure basicHttpBinding with Transport security -- >  
      <!-- mode and clientCredentialType set to None.-->  
      <binding name="Binding1">  
        <security mode="Transport">  
          <transport clientCredentialType="None"/>  
        </security>  
      </binding>  
    </basicHttpBinding>  
  </bindings>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="a95e5-116">Bu örnekte kullanılan sertifikanın Makecert.exe ile oluşturulan bir test sertifikası olduğundan, bir HTTPS erişmeye çalıştığınızda bir güvenlik uyarısı görünür: tarayıcınızda gibi adres https://localhost/servicemodelsamples/service.svc.</span><span class="sxs-lookup"><span data-stu-id="a95e5-116">Because the certificate used in this sample is a test certificate created with Makecert.exe, a security alert appears when you try to access an HTTPS: address in your browser, such as https://localhost/servicemodelsamples/service.svc.</span></span> <span data-ttu-id="a95e5-117">Bir test sertifikası ile çalışmak Windows Communication Foundation (WCF) istemcinin sağlamak için bazı ek kod güvenlik uyarıyı gizlemek için istemciye eklenir.</span><span class="sxs-lookup"><span data-stu-id="a95e5-117">To allow the Windows Communication Foundation (WCF) client to work with a test certificate, some additional code is added to the client to suppress the security alert.</span></span> <span data-ttu-id="a95e5-118">Bu kod, eşlik eden sınıfı değil ve gerekli gerçek sertifikalar kullanıldığında.</span><span class="sxs-lookup"><span data-stu-id="a95e5-118">This code, and the accompanying class, is not necessary when using real certificates.</span></span>  

```csharp
// This code is required only for test certificates such as those   
// created by Makecert.exe.  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```

 <span data-ttu-id="a95e5-119">Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="a95e5-119">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="a95e5-120">İstemcisi penceresinde istemciyi aşağı kapatmak için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="a95e5-120">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="a95e5-121">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="a95e5-121">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="a95e5-122">Yükleme [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 aşağıdaki komutu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="a95e5-122">Install [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 using the following command:</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  <span data-ttu-id="a95e5-123">Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a95e5-123">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3.  <span data-ttu-id="a95e5-124">Gerçekleştirmiş emin olun [Internet Information Services (IIS) sunucu sertifikası yükleme yönergeleri](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md).</span><span class="sxs-lookup"><span data-stu-id="a95e5-124">Ensure that you have performed the [Internet Information Services (IIS) Server Certificate Installation Instructions](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md).</span></span>  
  
4.  <span data-ttu-id="a95e5-125">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a95e5-125">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
5.  <span data-ttu-id="a95e5-126">Tek veya çapraz makine yapılandırmada örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a95e5-126">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a95e5-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a95e5-127">See Also</span></span>
