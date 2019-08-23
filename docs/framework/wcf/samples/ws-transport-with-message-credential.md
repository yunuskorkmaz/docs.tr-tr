---
title: İleti Kimlik Bilgileri ile WS Aktarma
ms.date: 03/30/2017
ms.assetid: 0d092f3a-b309-439b-920b-66d8f46a0e3c
ms.openlocfilehash: a2eade01ff3397d8f7ea790558909111c43b131d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69959788"
---
# <a name="ws-transport-with-message-credential"></a><span data-ttu-id="5f54c-102">İleti Kimlik Bilgileri ile WS Aktarma</span><span class="sxs-lookup"><span data-stu-id="5f54c-102">WS Transport With Message Credential</span></span>
<span data-ttu-id="5f54c-103">Bu örnek, iletide yürütülen istemci kimlik bilgileri ile birlikte SSL Aktarım güvenliği kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="5f54c-103">This sample demonstrates the use of SSL transport security in combination with client credential being carried in the message.</span></span> <span data-ttu-id="5f54c-104">Bu örnek, `wsHttpBinding` bağlamayı kullanır.</span><span class="sxs-lookup"><span data-stu-id="5f54c-104">This sample uses the `wsHttpBinding` binding.</span></span>  
  
 <span data-ttu-id="5f54c-105">Varsayılan olarak, `wsHttpBinding` bağlama http iletişimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="5f54c-105">By default, the `wsHttpBinding` binding provides HTTP communication.</span></span> <span data-ttu-id="5f54c-106">Aktarım güvenliği için yapılandırıldığında bağlama, HTTPS iletişimini destekler.</span><span class="sxs-lookup"><span data-stu-id="5f54c-106">When configured for transport security, the binding supports HTTPS communication.</span></span> <span data-ttu-id="5f54c-107">HTTPS, tel üzerinden iletilen iletiler için Gizlilik ve bütünlük koruması sağlar.</span><span class="sxs-lookup"><span data-stu-id="5f54c-107">HTTPS provides confidentiality and integrity protection for the messages that are transmitted over the wire.</span></span> <span data-ttu-id="5f54c-108">Ancak, hizmette istemcinin kimliğini doğrulamak için kullanılabilen kimlik doğrulama mekanizmaları kümesi, HTTPS aktarımının desteklediği ile sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="5f54c-108">However the set of authentication mechanisms that can be used to authenticate the client to the service is limited to what the HTTPS transport supports.</span></span> <span data-ttu-id="5f54c-109">Windows Communication Foundation (WCF), bu `TransportWithMessageCredential` kısıtlamayı aşmak için tasarlanan bir güvenlik modu sağlar.</span><span class="sxs-lookup"><span data-stu-id="5f54c-109">Windows Communication Foundation (WCF) offers a `TransportWithMessageCredential` security mode that is designed to overcome this limitation.</span></span> <span data-ttu-id="5f54c-110">Bu güvenlik modu yapılandırıldığında, aktarım güvenliği, iletilen iletiler için Gizlilik ve bütünlük sağlamak ve hizmet kimlik doğrulamasını gerçekleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5f54c-110">When this security mode is configured, the transport security is used to provide confidentiality and integrity for the transmitted messages and to perform the service authentication.</span></span> <span data-ttu-id="5f54c-111">Ancak istemci kimlik doğrulaması, istemci kimlik bilgisi doğrudan iletiye yerleştirilerek gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="5f54c-111">However, the client authentication is performed by putting the client credential directly in the message.</span></span> <span data-ttu-id="5f54c-112">Bu, aktarım güvenliği modunun performans avantajını korurken istemci kimlik doğrulaması için ileti güvenliği modu tarafından desteklenen herhangi bir kimlik bilgisi türünü kullanmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="5f54c-112">This allows you to use any credential type that is supported by the message security mode for the client authentication while keeping the performance benefit of transport security mode.</span></span>  
  
 <span data-ttu-id="5f54c-113">Bu örnekte, istemcinin kimliğini `UserName` doğrulamak için bir kimlik bilgisi türü kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5f54c-113">In this sample, a `UserName` credential type is used to authenticate the client to the service.</span></span>  
  
 <span data-ttu-id="5f54c-114">Bu örnek, bir Hesaplayıcı hizmeti uygulayan [kullanmaya](../../../../docs/framework/wcf/samples/getting-started-sample.md) Başlarken hizmetini temel alır.</span><span class="sxs-lookup"><span data-stu-id="5f54c-114">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="5f54c-115">`wsHttpBinding` Bağlama belirtilir ve istemci ve hizmet için uygulama yapılandırma dosyalarında yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="5f54c-115">The `wsHttpBinding` binding is specified and configured in the application configuration files for the client and service.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5f54c-116">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="5f54c-116">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="5f54c-117">Örnekteki program kodu, [kullanmaya](../../../../docs/framework/wcf/samples/getting-started-sample.md) başlama hizmetindekilerle neredeyse aynıdır.</span><span class="sxs-lookup"><span data-stu-id="5f54c-117">The program code in the sample is almost identical to that of the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) service.</span></span> <span data-ttu-id="5f54c-118">Hizmet sözleşmesi `GetCallerIdentity`tarafından sağlanmış bir ek işlem vardır.</span><span class="sxs-lookup"><span data-stu-id="5f54c-118">There is one additional operation provided by the service contract - `GetCallerIdentity`.</span></span> <span data-ttu-id="5f54c-119">Bu işlem, arayanın kimliğinin adını çağırana döndürür.</span><span class="sxs-lookup"><span data-stu-id="5f54c-119">This operation returns the name of the caller's identity to the caller.</span></span>  

```csharp
public string GetCallerIdentity()  
{  
    // Use ServiceSecurityContext.WindowsIdentity to get the name of the caller.  
    return ServiceSecurityContext.Current.WindowsIdentity.Name;  
}  
```

 <span data-ttu-id="5f54c-120">Örneği oluşturmadan önce bir sertifika oluşturmalı ve Web sunucusu Sertifika sihirbazını kullanarak atamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="5f54c-120">You must create a certificate and assign it by using the Web Server Certificate Wizard before building and running the sample.</span></span> <span data-ttu-id="5f54c-121">Yapılandırma dosyası ayarlarındaki uç nokta tanımı ve bağlama tanımı, istemci için `TransportWithMessageCredential` aşağıdaki örnek yapılandırmada gösterildiği gibi güvenlik modunu etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="5f54c-121">The endpoint definition and binding definition in the configuration file settings enable `TransportWithMessageCredential` security mode, as shown in the following sample configuration for the client.</span></span>  
  
```xml  
<system.serviceModel>  
  <client>  
    <endpoint name=""  
              address="https://localhost/servicemodelsamples/service.svc"   
              binding="wsHttpBinding"   
              bindingConfiguration="Binding1"   
              contract="Microsoft.ServiceModel.Samples.ICalculator" />  
  </client>  
  
  <bindings>  
    <wsHttpBinding>  
      <!--   
        This configuration defines the security mode as TransportWithMessageCredential.  
        and the clientCredentialType as UserName.  
        -->  
      <binding name="Binding1">  
        <security mode ="TransportWithMessageCredential">  
          <message clientCredentialType="UserName" />  
        </security>  
      </binding>  
    </wsHttpBinding>  
  </bindings>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="5f54c-122">Belirtilen adres https://düzenini kullanır.</span><span class="sxs-lookup"><span data-stu-id="5f54c-122">The address specified uses the https:// scheme.</span></span> <span data-ttu-id="5f54c-123">Bağlama yapılandırması güvenlik modunu olarak `TransportWithMessageCredential`ayarlar.</span><span class="sxs-lookup"><span data-stu-id="5f54c-123">The binding configuration sets the security mode to `TransportWithMessageCredential`.</span></span> <span data-ttu-id="5f54c-124">Hizmetin Web. config dosyasında aynı güvenlik modu belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="5f54c-124">The same security mode must be specified in the service's Web.config file.</span></span>  
  
 <span data-ttu-id="5f54c-125">Bu örnekte kullanılan sertifika, MakeCert. exe ile oluşturulmuş bir test sertifikasıdır çünkü, tarayıcınızla, gibi bir https: adresine `https://localhost/servicemodelsamples/service.svc`erişmeye çalıştığınızda bir güvenlik uyarısı görünür.</span><span class="sxs-lookup"><span data-stu-id="5f54c-125">Because the certificate used in this sample is a test certificate created with Makecert.exe, a security alert appears when you try to access an https: address, such as  `https://localhost/servicemodelsamples/service.svc`, from your browser.</span></span> <span data-ttu-id="5f54c-126">WCF istemcisinin yerinde bir test sertifikasıyla çalışmasına izin vermek için, güvenlik uyarısını bastırmak üzere istemciye bazı ek kodlar eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="5f54c-126">To allow the WCF client to work with a test certificate in place, some additional code has been added to the client to suppress the security alert.</span></span> <span data-ttu-id="5f54c-127">Üretim sertifikaları kullanılırken bu kod ve eşlik eden sınıf gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="5f54c-127">This code, and the accompanying class, is not required when using production certificates.</span></span>  

```csharp
// WARNING: This code is only needed for test certificates such as those created by makecert. It is   
// not recommended for production code.  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```
  
 <span data-ttu-id="5f54c-128">Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="5f54c-128">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="5f54c-129">İstemcisini kapatmak için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="5f54c-129">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Username authentication required.  
Provide a valid machine or domain account. [domain\\user]  
   Enter username:   
YourDomainName\YourAccountName  
   Enter password:   
********  
YourDomainName\YourAccountName  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="5f54c-130">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="5f54c-130">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="5f54c-131">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="5f54c-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="5f54c-132">[Internet Information Services (IIS) sunucu sertifikası yükleme yönergelerini](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="5f54c-132">Ensure that you have performed the [Internet Information Services (IIS) Server Certificate Installation Instructions](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md).</span></span>  
  
3. <span data-ttu-id="5f54c-133">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="5f54c-133">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="5f54c-134">Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="5f54c-134">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
