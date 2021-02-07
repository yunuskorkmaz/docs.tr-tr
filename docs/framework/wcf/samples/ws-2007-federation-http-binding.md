---
description: 'Daha fazla bilgi edinin: WS 2007 Federasyon HTTP bağlaması'
title: WS 2007 Federasyon HTTP Bağlama
ms.date: 03/30/2017
ms.assetid: 91c1b477-a96e-4bf5-9330-5e9312113371
ms.openlocfilehash: 12363abb1c8c503db8ec4aac9197276c8ec41c58
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99715060"
---
# <a name="ws-2007-federation-http-binding"></a><span data-ttu-id="14e90-103">WS 2007 Federasyon HTTP Bağlama</span><span class="sxs-lookup"><span data-stu-id="14e90-103">WS 2007 Federation HTTP Binding</span></span>

<span data-ttu-id="14e90-104">Bu örnek <xref:System.ServiceModel.WS2007FederationHttpBinding> , WS-Trust belirtiminin 1,3 sürümünü destekleyen federe senaryolar oluşturmak için kullanabileceğiniz standart bir bağlamanın kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="14e90-104">This sample demonstrates the use of <xref:System.ServiceModel.WS2007FederationHttpBinding>, a standard binding that you can use to build federated scenarios that support version 1.3 of the WS-Trust specification.</span></span>

> [!NOTE]
> <span data-ttu-id="14e90-105">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="14e90-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="14e90-106">Örnek, konsol tabanlı bir istemci programından (*Client.exe*), konsol tabanlı bir güvenlik belirteci hizmeti programından (*Securitytokenservice.exe*) ve konsol tabanlı bir hizmet programından (*Service.exe*) oluşur.</span><span class="sxs-lookup"><span data-stu-id="14e90-106">The sample consists of a console-based client program (*Client.exe*), a console-based security token service program (*Securitytokenservice.exe*), and a console-based service program (*Service.exe*).</span></span> <span data-ttu-id="14e90-107">Hizmet, istek/yanıt iletişim modelini tanımlayan bir sözleşme uygular.</span><span class="sxs-lookup"><span data-stu-id="14e90-107">The service implements a contract that defines a request/reply communication pattern.</span></span> <span data-ttu-id="14e90-108">Sözleşme, `ICalculator` matematik işlemlerini ( `Add` ,, `Subtract` `Multiply` ve) sunan arabirim tarafından tanımlanır `Divide` .</span><span class="sxs-lookup"><span data-stu-id="14e90-108">The contract is defined by the `ICalculator` interface, which exposes math operations (`Add`, `Subtract`, `Multiply`, and `Divide`).</span></span> <span data-ttu-id="14e90-109">İstemci, güvenlik belirteci hizmetinden (STS) bir güvenlik belirteci alır ve belirli bir matematik işlemi için hizmete zaman uyumlu istekler sağlar.</span><span class="sxs-lookup"><span data-stu-id="14e90-109">The client obtains a security token from the Security Token Service (STS) and makes synchronous requests to the service for a given math operation.</span></span> <span data-ttu-id="14e90-110">Hizmet daha sonra sonuçla yanıt verir.</span><span class="sxs-lookup"><span data-stu-id="14e90-110">The service then replies with the result.</span></span> <span data-ttu-id="14e90-111">İstemci etkinliği konsol penceresinde görünür.</span><span class="sxs-lookup"><span data-stu-id="14e90-111">Client activity is visible in the console window.</span></span>

<span data-ttu-id="14e90-112">Örnek, `ICalculator` sözleşmenin öğesini kullanarak kullanılabilir hale getirir `ws2007FederationHttpBinding` .</span><span class="sxs-lookup"><span data-stu-id="14e90-112">The sample makes the `ICalculator` contract available using the `ws2007FederationHttpBinding` element.</span></span> <span data-ttu-id="14e90-113">İstemci üzerindeki bu bağlamanın yapılandırması aşağıdaki kodda gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="14e90-113">The configuration of this binding on the client is shown in the following code:</span></span>

```xml
<bindings>
  <ws2007FederationHttpBinding>
    <binding name="ServiceFed" >
      <security mode ="Message">
        <message issuedKeyType ="SymmetricKey"
                 issuedTokenType ="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1" >
          <!-- Endpoint address and binding for Security Token Service -->
          <issuer address ="http://localhost:8000/sts/windows"
                  binding ="ws2007HttpBinding" />
        </message>
      </security>
    </binding>
  </ws2007FederationHttpBinding>
</bindings>
```

<span data-ttu-id="14e90-114">Üzerinde, [\<security>](../../configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md) `security` değeri hangi güvenlik modunun kullanılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="14e90-114">On the [\<security>](../../configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md), the `security` value specifies which security mode should be used.</span></span> <span data-ttu-id="14e90-115">Bu örnekte, `message` güvenlik, ' ın içinde belirtilmesinin nedeni olan güvenlik kullanılır [\<message>](../../configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) [\<security>](../../configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="14e90-115">In this sample, `message` security is used, which is why the [\<message>](../../configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) is specified inside the [\<security>](../../configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md).</span></span> <span data-ttu-id="14e90-116">[\<issuer>](../../configure-apps/file-schema/wcf/issuer.md)İçindeki öğesi, istemcinin [\<message>](../../configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) hizmette kimlik doğrulaması yapabilmesi için istemciye bir güvenlik BELIRTECI veren STS için adresi ve bağlamayı belirtir `ICalculator` .</span><span class="sxs-lookup"><span data-stu-id="14e90-116">The [\<issuer>](../../configure-apps/file-schema/wcf/issuer.md) element inside the [\<message>](../../configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) specifies the address and binding for the STS that issues a security token to the client so that the client can authenticate to the `ICalculator` service.</span></span>
  
<span data-ttu-id="14e90-117">Hizmette Bu bağlamanın yapılandırması aşağıdaki kodda gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="14e90-117">The configuration of this binding on the service is shown in the following code:</span></span>

```xml
<bindings>
  <ws2007FederationHttpBinding>
    <binding name="ServiceFed" >
      <security mode ="Message">
        <message issuedKeyType ="SymmetricKey"
                 issuedTokenType ="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1" >
          <!-- Metadata address for Security Token Service -->
          <issuerMetadata address ="http://localhost:8000/sts/mex" >
            <identity>
              <certificateReference storeLocation ="CurrentUser"
                                    storeName="TrustedPeople"
                                    x509FindType ="FindBySubjectDistinguishedName"
                                    findValue ="CN=STS" />
            </identity>
          </issuerMetadata>
        </message>
      </security>
    </binding>
  </ws2007FederationHttpBinding>
</bindings>
```

<span data-ttu-id="14e90-118">Üzerinde, [\<security>](../../configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md) `security` değeri hangi güvenlik modunun kullanılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="14e90-118">On the [\<security>](../../configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md), the `security` value specifies which security mode should be used.</span></span> <span data-ttu-id="14e90-119">Bu örnekte, `message` güvenlik, ' ın içinde belirtilmesinin nedeni olan güvenlik kullanılır [\<message>](../../configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) [\<security>](../../configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="14e90-119">In this sample, `message` security is used, which is why the [\<message>](../../configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) is specified inside the [\<security>](../../configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md).</span></span> <span data-ttu-id="14e90-120">[\<issuerMetadata>](../../configure-apps/file-schema/wcf/issuermetadata.md)İçindeki öğesi, `ws2007FederationHttpBinding` [\<message>](../../configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) STS için meta verileri almak üzere kullanılabilecek bir uç nokta için adresi ve kimliği belirtir.</span><span class="sxs-lookup"><span data-stu-id="14e90-120">The [\<issuerMetadata>](../../configure-apps/file-schema/wcf/issuermetadata.md) element of `ws2007FederationHttpBinding` inside the [\<message>](../../configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) specifies the address and identity for an endpoint that can be used to retrieve metadata for the STS.</span></span>

<span data-ttu-id="14e90-121">Hizmetin davranışı aşağıdaki kodda gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="14e90-121">The behavior for the service is shown in the following code:</span></span>

```xml
<behaviors>
  <serviceBehaviors>
    <behavior name ="ServiceBehaviour" >
      <serviceDebug includeExceptionDetailInFaults ="true"/>
      <serviceMetadata httpGetEnabled ="true"/>
      <serviceCredentials>
        <issuedTokenAuthentication>
          <knownCertificates>
            <add storeLocation ="LocalMachine"
                 storeName="TrustedPeople"
                 x509FindType="FindBySubjectDistinguishedName"
                 findValue="CN=STS" />
          </knownCertificates>
        </issuedTokenAuthentication>
        <serviceCertificate storeLocation ="LocalMachine"
                            storeName ="My"
                            x509FindType ="FindBySubjectDistinguishedName"
                            findValue ="CN=localhost"/>
      </serviceCredentials>
    </behavior>
  </serviceBehaviors>
</behaviors>
```
  
<span data-ttu-id="14e90-122">[\<issuedTokenAuthentication>](../../configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)>, hizmetin kimlik doğrulaması sırasında istemcilerin sunmalarına izin verdiği belirteçlerde kısıtlamalar belirtmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="14e90-122">The [\<issuedTokenAuthentication>](../../configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)> allows the service to specify constraints on the tokens it allows clients to present during authentication.</span></span> <span data-ttu-id="14e90-123">Bu yapılandırma, konu adı CN = STS olan bir sertifika tarafından imzalanmış belirteçlerin hizmet tarafından kabul edildiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="14e90-123">This configuration specifies that tokens signed by a certificate whose subject name is CN=STS are accepted by the service.</span></span>

<span data-ttu-id="14e90-124">STS, standart kullanarak tek bir uç noktanın kullanılabilir olmasını sağlar <xref:System.ServiceModel.WS2007HttpBinding> .</span><span class="sxs-lookup"><span data-stu-id="14e90-124">STS makes a single endpoint available using the standard <xref:System.ServiceModel.WS2007HttpBinding>.</span></span> <span data-ttu-id="14e90-125">Hizmet, istemcilerden belirteç isteklerine yanıt verir.</span><span class="sxs-lookup"><span data-stu-id="14e90-125">The service responds to requests from clients for tokens.</span></span> <span data-ttu-id="14e90-126">İstemcinin kimliği bir Windows hesabı kullanılarak doğrulandıysa, hizmet istemcinin kullanıcı adını bir talep olarak içeren bir belirteç yayınlar.</span><span class="sxs-lookup"><span data-stu-id="14e90-126">If the client is authenticated using a Windows account, the service issues a token that contains the client's user name as a claim.</span></span> <span data-ttu-id="14e90-127">Belirteç oluşturmanın bir parçası olarak STS, CN = STS sertifikasıyla ilişkili özel anahtarı kullanarak belirteci imzalar.</span><span class="sxs-lookup"><span data-stu-id="14e90-127">As part of creating the token, STS signs the token using the private key associated with the CN=STS certificate.</span></span> <span data-ttu-id="14e90-128">Ayrıca, bir simetrik anahtar oluşturur ve CN = localhost sertifikasıyla ilişkili ortak anahtarı kullanarak şifreler.</span><span class="sxs-lookup"><span data-stu-id="14e90-128">In addition, it creates a symmetric key and encrypts it using the public key associated with the CN=localhost certificate.</span></span> <span data-ttu-id="14e90-129">Belirteci istemciye döndürmekte sonra STS simetrik anahtarı da döndürür.</span><span class="sxs-lookup"><span data-stu-id="14e90-129">In returning the token to the client, STS also returns the symmetric key.</span></span> <span data-ttu-id="14e90-130">İstemci verilen belirteci `ICalculator` hizmete sunar ve iletiyi bu anahtarla imzalayarak simetrik anahtarı bilir olduğunu kanıtlar.</span><span class="sxs-lookup"><span data-stu-id="14e90-130">The client presents the issued token to the `ICalculator` service and proves that it knows the symmetric key by signing the message with that key.</span></span>

<span data-ttu-id="14e90-131">Örneği çalıştırdığınızda, güvenlik belirteci isteği STS konsol penceresinde gösterilir.</span><span class="sxs-lookup"><span data-stu-id="14e90-131">When you run the sample, the request for the security token is shown in the STS console window.</span></span> <span data-ttu-id="14e90-132">İşlemin istekleri ve yanıtları istemci ve hizmet konsolu pencereleri içinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="14e90-132">The operation's requests and responses are displayed in the client and service console windows.</span></span> <span data-ttu-id="14e90-133">Uygulamayı kapatmak için konsol pencerelerinin herhangi birinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="14e90-133">Press ENTER in any of the console windows to shut down the application.</span></span>

```console
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714
Press <ENTER> to terminate client.
```

<span data-ttu-id="14e90-134">Bu örneğe eklenen *Setup.bat* dosyası, şirket içinde barındırılan bir uygulamayı çalıştırmak için sunucuyu ve STS 'yi ilgili sertifikalarla yapılandırmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="14e90-134">The *Setup.bat* file included with this sample allows you to configure the server and STS with the relevant certificates to run a self-hosted application.</span></span> <span data-ttu-id="14e90-135">Toplu iş dosyası, LocalMachine/Trustedkişileri sertifika deposunda iki sertifika oluşturur.</span><span class="sxs-lookup"><span data-stu-id="14e90-135">The batch file creates two certificates in the LocalMachine/TrustedPeople certificate store.</span></span> <span data-ttu-id="14e90-136">İlk sertifika, CN = STS 'nin konu adına sahiptir ve STS tarafından, istemciye verdiği güvenlik belirteçlerini imzalamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="14e90-136">The first certificate has a subject name of CN=STS and is used by STS to sign the security tokens that it issues to the client.</span></span> <span data-ttu-id="14e90-137">İkinci sertifika, CN = localhost konu adına sahiptir ve STS tarafından hizmetin şifresini çözebilmesi için bir anahtar şifrelemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="14e90-137">The second certificate has a subject name of CN=localhost and is used by STS to encrypt a key in a way that the service can decrypt.</span></span>

## <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="14e90-138">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="14e90-138">To set up, build, and run the sample</span></span>
  
1. <span data-ttu-id="14e90-139">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="14e90-139">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="14e90-140">Yönetici ayrıcalıklarına sahip bir Visual Studio Geliştirici Komut İstemi açın ve gerekli sertifikaları oluşturmak için Setup.bat dosyasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="14e90-140">Open a Developer Command Prompt for Visual Studio with administrator privileges and run the Setup.bat file to create the required certificates.</span></span>

 <span data-ttu-id="14e90-141">Bu toplu iş dosyası, Windows SDK dağıtılan *Certmgr.exe* ve Makecert.exe kullanır.</span><span class="sxs-lookup"><span data-stu-id="14e90-141">This batch file uses *Certmgr.exe* and Makecert.exe, which are distributed with the Windows SDK.</span></span> <span data-ttu-id="14e90-142">Ancak, bu araçları bulmak için komut dosyasını etkinleştirmek üzere bir Visual Studio komut istemi içinden *Setup.bat* çalıştırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="14e90-142">However, you must run *Setup.bat* from within a Visual Studio command prompt to enable the script to find these tools.</span></span>

1. <span data-ttu-id="14e90-143">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="14e90-143">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

2. <span data-ttu-id="14e90-144">Örneği tek veya bir çoklu bilgisayar yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="14e90-144">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span> <span data-ttu-id="14e90-145">Windows Vista kullanıyorsanız, yükseltilmiş ayrıcalıklarla *Service.exe*, *Client.exe* ve *SecurityTokenService.exe* çalıştırmanız gerekir (dosyalara sağ tıklayıp **yönetici olarak çalıştır**' a tıklayın).</span><span class="sxs-lookup"><span data-stu-id="14e90-145">If you are using Windows Vista, you must run *Service.exe*, *Client.exe*, and *SecurityTokenService.exe* with elevated privileges (right-click the files and then click **Run as administrator**).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="14e90-146">Örnekler bilgisayarınızda zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="14e90-146">The samples may already be installed on your computer.</span></span> <span data-ttu-id="14e90-147">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin:</span><span class="sxs-lookup"><span data-stu-id="14e90-147">Check for the following (default) directory before continuing:</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="14e90-148">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="14e90-148">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="14e90-149">Bu örnek aşağıdaki dizinde bulunur:</span><span class="sxs-lookup"><span data-stu-id="14e90-149">This sample is located in the following directory:</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\WS2007FederationHttp`
