---
title: WS 2007 Federasyon HTTP Bağlama
ms.date: 03/30/2017
ms.assetid: 91c1b477-a96e-4bf5-9330-5e9312113371
ms.openlocfilehash: bf61e64733859d96adf42fbacf08266eca1f5b45
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183179"
---
# <a name="ws-2007-federation-http-binding"></a><span data-ttu-id="38017-102">WS 2007 Federasyon HTTP Bağlama</span><span class="sxs-lookup"><span data-stu-id="38017-102">WS 2007 Federation HTTP Binding</span></span>

<span data-ttu-id="38017-103">Bu örnek, WS-Trust belirtiminin <xref:System.ServiceModel.WS2007FederationHttpBinding>sürüm 1.3'ü destekleyen federe senaryolar oluşturmak için kullanabileceğiniz standart bir bağlayıcının kullanımını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="38017-103">This sample demonstrates the use of <xref:System.ServiceModel.WS2007FederationHttpBinding>, a standard binding that you can use to build federated scenarios that support version 1.3 of the WS-Trust specification.</span></span>

> [!NOTE]
> <span data-ttu-id="38017-104">Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="38017-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="38017-105">Örnek bir konsol tabanlı istemci programı *(Client.exe),* konsol tabanlı bir güvenlik belirteç hizmet programı *(Securitytokenservice.exe)* ve konsol tabanlı bir hizmet programı *(Service.exe)* oluşur.</span><span class="sxs-lookup"><span data-stu-id="38017-105">The sample consists of a console-based client program (*Client.exe*), a console-based security token service program (*Securitytokenservice.exe*), and a console-based service program (*Service.exe*).</span></span> <span data-ttu-id="38017-106">Hizmet, istek/yanıt iletişimi deseni tanımlayan bir sözleşme uygular.</span><span class="sxs-lookup"><span data-stu-id="38017-106">The service implements a contract that defines a request/reply communication pattern.</span></span> <span data-ttu-id="38017-107">Sözleşme, matematik işlemlerini `ICalculator` ortaya çıkaran arayüz tarafından`Add` `Subtract`tanımlanır `Multiply`( `Divide`, , , ve .</span><span class="sxs-lookup"><span data-stu-id="38017-107">The contract is defined by the `ICalculator` interface, which exposes math operations (`Add`, `Subtract`, `Multiply`, and `Divide`).</span></span> <span data-ttu-id="38017-108">İstemci, Güvenlik Belirteci Hizmeti'nden (STS) bir güvenlik belirteci alır ve belirli bir matematik işlemi için hizmete eşzamanlı istekte bulunmayı sağlar.</span><span class="sxs-lookup"><span data-stu-id="38017-108">The client obtains a security token from the Security Token Service (STS) and makes synchronous requests to the service for a given math operation.</span></span> <span data-ttu-id="38017-109">Hizmet daha sonra sonucu yanıtlar.</span><span class="sxs-lookup"><span data-stu-id="38017-109">The service then replies with the result.</span></span> <span data-ttu-id="38017-110">İstemci etkinliği konsol penceresinde görünür.</span><span class="sxs-lookup"><span data-stu-id="38017-110">Client activity is visible in the console window.</span></span>

<span data-ttu-id="38017-111">Örnek, öğeyi kullanarak `ICalculator` `ws2007FederationHttpBinding` sözleşmeyi kullanılabilir hale getirir.</span><span class="sxs-lookup"><span data-stu-id="38017-111">The sample makes the `ICalculator` contract available using the `ws2007FederationHttpBinding` element.</span></span> <span data-ttu-id="38017-112">İstemci için bu bağlama yapılandırması aşağıdaki kodda gösterilir:</span><span class="sxs-lookup"><span data-stu-id="38017-112">The configuration of this binding on the client is shown in the following code:</span></span>

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

<span data-ttu-id="38017-113">Güvenlik>, `security` değer hangi güvenlik modunun kullanılması gerektiğini belirtir. [ \< ](../../configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="38017-113">On the [\<security>](../../configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md), the `security` value specifies which security mode should be used.</span></span> <span data-ttu-id="38017-114">Bu örnekte, güvenlik kullanılır, `message` bu nedenle [ \<ileti>](../../configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) [ \<güvenlik>](../../configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md)içinde belirtilir.</span><span class="sxs-lookup"><span data-stu-id="38017-114">In this sample, `message` security is used, which is why the [\<message>](../../configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) is specified inside the [\<security>](../../configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md).</span></span> <span data-ttu-id="38017-115">[ \<](../../configure-apps/file-schema/wcf/issuer.md) [İletinin \<](../../configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) içindeki>öğesi>, istemcinin `ICalculator` hizmete kimlik doğrulaması yapabilmesi için istemciye güvenlik belirteci veren STS adresini ve bağlamayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="38017-115">The [\<issuer>](../../configure-apps/file-schema/wcf/issuer.md) element inside the [\<message>](../../configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) specifies the address and binding for the STS that issues a security token to the client so that the client can authenticate to the `ICalculator` service.</span></span>
  
<span data-ttu-id="38017-116">Hizmet için bu bağlama yapılandırması aşağıdaki kodda gösterilir:</span><span class="sxs-lookup"><span data-stu-id="38017-116">The configuration of this binding on the service is shown in the following code:</span></span>

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

<span data-ttu-id="38017-117">Güvenlik>, `security` değer hangi güvenlik modunun kullanılması gerektiğini belirtir. [ \< ](../../configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="38017-117">On the [\<security>](../../configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md), the `security` value specifies which security mode should be used.</span></span> <span data-ttu-id="38017-118">Bu örnekte, güvenlik kullanılır, `message` bu nedenle [ \<ileti>](../../configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) [ \<güvenlik>](../../configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md)içinde belirtilir.</span><span class="sxs-lookup"><span data-stu-id="38017-118">In this sample, `message` security is used, which is why the [\<message>](../../configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) is specified inside the [\<security>](../../configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md).</span></span> <span data-ttu-id="38017-119">İleti [ \<](../../configure-apps/file-schema/wcf/issuermetadata.md) nin `ws2007FederationHttpBinding` [ \<](../../configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) içindeki meta veri>öğesi>, STS için meta verileri almak için kullanılabilecek bir bitiş noktasının adresini ve kimliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="38017-119">The [\<issuerMetadata>](../../configure-apps/file-schema/wcf/issuermetadata.md) element of `ws2007FederationHttpBinding` inside the [\<message>](../../configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) specifies the address and identity for an endpoint that can be used to retrieve metadata for the STS.</span></span>

<span data-ttu-id="38017-120">Hizmetin davranışı aşağıdaki kodda gösterilir:</span><span class="sxs-lookup"><span data-stu-id="38017-120">The behavior for the service is shown in the following code:</span></span>

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
  
<span data-ttu-id="38017-121">[>>verilen TokenAuthentication, hizmetin istemcilerin kimlik doğrulama sırasında sunmasına izin verdiği belirteçler üzerindeki kısıtlamaları belirtmesine olanak tanır. \<](../../configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)</span><span class="sxs-lookup"><span data-stu-id="38017-121">The [\<issuedTokenAuthentication>](../../configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)> allows the service to specify constraints on the tokens it allows clients to present during authentication.</span></span> <span data-ttu-id="38017-122">Bu yapılandırma, konu adı CN=STS olan bir sertifika tarafından imzalanan belirteçlerin hizmet tarafından kabul edildiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="38017-122">This configuration specifies that tokens signed by a certificate whose subject name is CN=STS are accepted by the service.</span></span>

<span data-ttu-id="38017-123">STS, standardı <xref:System.ServiceModel.WS2007HttpBinding>kullanarak tek bir uç noktayı kullanılabilir hale getirir.</span><span class="sxs-lookup"><span data-stu-id="38017-123">STS makes a single endpoint available using the standard <xref:System.ServiceModel.WS2007HttpBinding>.</span></span> <span data-ttu-id="38017-124">Hizmet, istemcilerin belirteçisteklerine yanıt verir.</span><span class="sxs-lookup"><span data-stu-id="38017-124">The service responds to requests from clients for tokens.</span></span> <span data-ttu-id="38017-125">İstemci bir Windows hesabı kullanılarak kimlik doğrulaması yapılırsa, hizmet talep olarak istemcinin kullanıcı adını içeren bir belirteç verir.</span><span class="sxs-lookup"><span data-stu-id="38017-125">If the client is authenticated using a Windows account, the service issues a token that contains the client's user name as a claim.</span></span> <span data-ttu-id="38017-126">Belirteci oluşturmanın bir parçası olarak, STS belirteci CN=STS sertifikası ile ilişkili özel anahtarı kullanarak imzalar.</span><span class="sxs-lookup"><span data-stu-id="38017-126">As part of creating the token, STS signs the token using the private key associated with the CN=STS certificate.</span></span> <span data-ttu-id="38017-127">Buna ek olarak, simetrik bir anahtar oluşturur ve CN=localhost sertifikası ile ilişkili ortak anahtarı kullanarak şifreler.</span><span class="sxs-lookup"><span data-stu-id="38017-127">In addition, it creates a symmetric key and encrypts it using the public key associated with the CN=localhost certificate.</span></span> <span data-ttu-id="38017-128">Belirteci istemciye döndürürken, STS simetrik anahtarı da döndürür.</span><span class="sxs-lookup"><span data-stu-id="38017-128">In returning the token to the client, STS also returns the symmetric key.</span></span> <span data-ttu-id="38017-129">İstemci verilen belirteci `ICalculator` hizmete sunar ve iletiyi bu anahtarla imzalayarak simetrik anahtarı bildiğini kanıtlar.</span><span class="sxs-lookup"><span data-stu-id="38017-129">The client presents the issued token to the `ICalculator` service and proves that it knows the symmetric key by signing the message with that key.</span></span>

<span data-ttu-id="38017-130">Örneği çalıştırdığınızda, güvenlik belirteci isteği STS konsol penceresinde gösterilir.</span><span class="sxs-lookup"><span data-stu-id="38017-130">When you run the sample, the request for the security token is shown in the STS console window.</span></span> <span data-ttu-id="38017-131">İşlemin istek ve yanıtları istemci ve servis konsolu pencerelerinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="38017-131">The operation's requests and responses are displayed in the client and service console windows.</span></span> <span data-ttu-id="38017-132">Uygulamayı kapatmak için konsol pencerelerinden herhangi birinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="38017-132">Press ENTER in any of the console windows to shut down the application.</span></span>

```console
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714
Press <ENTER> to terminate client.
```

<span data-ttu-id="38017-133">Bu örnekle birlikte bulunan *Setup.bat* dosyası, sunucuyu ve STS'yi kendi barındırılan bir uygulamayı çalıştırmak için ilgili sertifikalarla yapılandırmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="38017-133">The *Setup.bat* file included with this sample allows you to configure the server and STS with the relevant certificates to run a self-hosted application.</span></span> <span data-ttu-id="38017-134">Toplu iş dosyası, LocalMachine/TrustedPeople sertifika deposunda iki sertifika oluşturur.</span><span class="sxs-lookup"><span data-stu-id="38017-134">The batch file creates two certificates in the LocalMachine/TrustedPeople certificate store.</span></span> <span data-ttu-id="38017-135">İlk sertifika CN=STS özne adı vardır ve STS tarafından istemciye verdiği güvenlik belirteçlerini imzalamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="38017-135">The first certificate has a subject name of CN=STS and is used by STS to sign the security tokens that it issues to the client.</span></span> <span data-ttu-id="38017-136">İkinci sertifika CN=localhost özne adı vardır ve STS tarafından bir anahtarı hizmetin şifresini çözebileceği şekilde şifrelemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="38017-136">The second certificate has a subject name of CN=localhost and is used by STS to encrypt a key in a way that the service can decrypt.</span></span>

## <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="38017-137">Örneği ayarlamak, oluşturmak ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="38017-137">To set up, build, and run the sample</span></span>
  
1. <span data-ttu-id="38017-138">Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.</span><span class="sxs-lookup"><span data-stu-id="38017-138">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="38017-139">Yönetici ayrıcalıklarına sahip Visual Studio için bir Geliştirici Komut Komut Ustem'i açın ve gerekli sertifikaları oluşturmak için Setup.bat dosyasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="38017-139">Open a Developer Command Prompt for Visual Studio with administrator privileges and run the Setup.bat file to create the required certificates.</span></span>

 <span data-ttu-id="38017-140">Bu toplu işlem dosyası, Windows SDK ile dağıtılan *Certmgr.exe* ve Makecert.exe'yi kullanır.</span><span class="sxs-lookup"><span data-stu-id="38017-140">This batch file uses *Certmgr.exe* and Makecert.exe, which are distributed with the Windows SDK.</span></span> <span data-ttu-id="38017-141">Ancak, komut dosyasının bu araçları bulmasını sağlamak için Visual Studio komut istemi içinden *Setup.bat* çalıştırmalısınız.</span><span class="sxs-lookup"><span data-stu-id="38017-141">However, you must run *Setup.bat* from within a Visual Studio command prompt to enable the script to find these tools.</span></span>

1. <span data-ttu-id="38017-142">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak [için, Windows Communication Foundation Samples'i oluştururken](building-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="38017-142">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

2. <span data-ttu-id="38017-143">Örneği tek veya bilgisayar lar arası yapılandırmada çalıştırmak [için, Windows Communication Foundation Samples'ı çalıştıran](running-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="38017-143">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span> <span data-ttu-id="38017-144">Windows Vista kullanıyorsanız, *Service.exe,* *Client.exe*ve *SecurityTokenService.exe'yi* yüksek ayrıcalıklarla çalıştırmanız gerekir (dosyaları sağ tıklatın ve ardından **yönetici olarak Çalıştır'ı**tıklatın).</span><span class="sxs-lookup"><span data-stu-id="38017-144">If you are using Windows Vista, you must run *Service.exe*, *Client.exe*, and *SecurityTokenService.exe* with elevated privileges (right-click the files and then click **Run as administrator**).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="38017-145">Örnekler bilgisayarınıza zaten yüklenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="38017-145">The samples may already be installed on your computer.</span></span> <span data-ttu-id="38017-146">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin:</span><span class="sxs-lookup"><span data-stu-id="38017-146">Check for the following (default) directory before continuing:</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="38017-147">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="38017-147">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="38017-148">Bu örnek aşağıdaki dizinde yer alır:</span><span class="sxs-lookup"><span data-stu-id="38017-148">This sample is located in the following directory:</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\WS2007FederationHttp`
