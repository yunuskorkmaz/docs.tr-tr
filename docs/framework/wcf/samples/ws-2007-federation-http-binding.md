---
title: WS 2007 Federasyon HTTP Bağlama
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 91c1b477-a96e-4bf5-9330-5e9312113371
caps.latest.revision: 23
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b7126e4c0c293bfbf78cecf97cc13ea91e6c0c62
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2018
---
# <a name="ws-2007-federation-http-binding"></a><span data-ttu-id="48f8c-102">WS 2007 Federasyon HTTP Bağlama</span><span class="sxs-lookup"><span data-stu-id="48f8c-102">WS 2007 Federation HTTP Binding</span></span>
<span data-ttu-id="48f8c-103">Bu örnek kullanımını gösteren <xref:System.ServiceModel.WS2007FederationHttpBinding>, WS-Trust belirtimine destek sürümünün 1.3 Federasyon senaryoları oluşturmak için kullanabileceğiniz bağlama standart.</span><span class="sxs-lookup"><span data-stu-id="48f8c-103">This sample demonstrates the use of <xref:System.ServiceModel.WS2007FederationHttpBinding>, a standard binding that you can use to build federated scenarios that support version 1.3 of the WS-Trust specification.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="48f8c-104">Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="48f8c-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="48f8c-105">Örnek bir konsol tabanlı istemci programını (Client.exe), bir konsol tabanlı güvenlik belirteci hizmeti programı (Securitytokenservice.exe) ve konsol tabanlı hizmet programı (Service.exe) oluşur.</span><span class="sxs-lookup"><span data-stu-id="48f8c-105">The sample consists of a console-based client program (Client.exe), a console-based security token service program (Securitytokenservice.exe), and a console-based service program (Service.exe).</span></span> <span data-ttu-id="48f8c-106">Hizmet istek/yanıt iletişim deseni tanımlayan bir sözleşme uygular.</span><span class="sxs-lookup"><span data-stu-id="48f8c-106">The service implements a contract that defines a request/reply communication pattern.</span></span> <span data-ttu-id="48f8c-107">Anlaşma tarafından tanımlanan `ICalculator` matematik işlemleri kullanıma sunan arabirim (`Add`, `Subtract`, `Multiply`, ve `Divide`).</span><span class="sxs-lookup"><span data-stu-id="48f8c-107">The contract is defined by the `ICalculator` interface, which exposes math operations (`Add`, `Subtract`, `Multiply`, and `Divide`).</span></span> <span data-ttu-id="48f8c-108">İstemci güvenlik belirteci hizmeti (STS) bir güvenlik belirteci alır ve hizmet verilen matematik işlemi için zaman uyumlu istekleri yapar.</span><span class="sxs-lookup"><span data-stu-id="48f8c-108">The client obtains a security token from the Security Token Service (STS) and makes synchronous requests to the service for a given math operation.</span></span> <span data-ttu-id="48f8c-109">Hizmet ardından sonucu, yanıt.</span><span class="sxs-lookup"><span data-stu-id="48f8c-109">The service then replies with the result.</span></span> <span data-ttu-id="48f8c-110">İstemci etkinliği konsol penceresinde görünür olur.</span><span class="sxs-lookup"><span data-stu-id="48f8c-110">Client activity is visible in the console window.</span></span>  
  
 <span data-ttu-id="48f8c-111">Örnek yapar `ICalculator` sözleşme kullanılabilir kullanarak `ws2007FederationHttpBinding` öğesi.</span><span class="sxs-lookup"><span data-stu-id="48f8c-111">The sample makes the `ICalculator` contract available using the `ws2007FederationHttpBinding` element.</span></span> <span data-ttu-id="48f8c-112">Bu bağlama istemcide yapılandırmasını aşağıdaki kodda gösterilir.</span><span class="sxs-lookup"><span data-stu-id="48f8c-112">The configuration of this binding on the client is shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="48f8c-113">Üzerinde [ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md), `security` değeri belirten hangi güvenlik modunda kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="48f8c-113">On the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md), the `security` value specifies which security mode should be used.</span></span> <span data-ttu-id="48f8c-114">Bu örnekte `message` güvenlik kullanılır, neden olduğu [ \<ileti >](../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) içinde belirtilen [ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="48f8c-114">In this sample, `message` security is used, which is why the [\<message>](../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) is specified inside the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md).</span></span> <span data-ttu-id="48f8c-115">[ \<Veren >](../../../../docs/framework/configure-apps/file-schema/wcf/issuer.md) öğesi içinde [ \<ileti >](../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) STS için istemciye bir güvenlik belirteci verir ve böylece istemci için bağlama ve adresini belirtir kimlik doğrulaması `ICalculator` hizmet.</span><span class="sxs-lookup"><span data-stu-id="48f8c-115">The [\<issuer>](../../../../docs/framework/configure-apps/file-schema/wcf/issuer.md) element inside the [\<message>](../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) specifies the address and binding for the STS that issues a security token to the client so that the client can authenticate to the `ICalculator` service.</span></span>  
  
 <span data-ttu-id="48f8c-116">Bu bağlama hizmetinin yapılandırmasını aşağıdaki kodda gösterilir.</span><span class="sxs-lookup"><span data-stu-id="48f8c-116">The configuration of this binding on the service is shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="48f8c-117">Üzerinde [ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md), `security` değeri belirten hangi güvenlik modunda kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="48f8c-117">On the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md), the `security` value specifies which security mode should be used.</span></span> <span data-ttu-id="48f8c-118">Bu örnekte `message` güvenlik kullanılır, neden olduğu [ \<ileti >](../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) içinde belirtilen [ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="48f8c-118">In this sample, `message` security is used, which is why the [\<message>](../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) is specified inside the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md).</span></span> <span data-ttu-id="48f8c-119">[ \<İssuedtokenparameters >](../../../../docs/framework/configure-apps/file-schema/wcf/issuermetadata.md) öğesinin `ws2007FederationHttpBinding` içinde [ \<ileti >](../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) almak için kullanılan bir uç nokta için kimlik ve adresini belirtir STS meta veriler.</span><span class="sxs-lookup"><span data-stu-id="48f8c-119">The [\<issuerMetadata>](../../../../docs/framework/configure-apps/file-schema/wcf/issuermetadata.md) element of `ws2007FederationHttpBinding` inside the [\<message>](../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) specifies the address and identity for an endpoint that can be used to retrieve metadata for the STS.</span></span>  
  
 <span data-ttu-id="48f8c-120">Hizmeti için davranış aşağıdaki kodda gösterilir.</span><span class="sxs-lookup"><span data-stu-id="48f8c-120">The behavior for the service is shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="48f8c-121">[ \<İssuedTokenAuthentication >](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)> kimlik doğrulaması sırasında sunmak istemcileri veren belirteçleri kısıtlamaları belirtmek hizmet sağlar.</span><span class="sxs-lookup"><span data-stu-id="48f8c-121">The [\<issuedTokenAuthentication>](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)> allows the service to specify constraints on the tokens it allows clients to present during authentication.</span></span> <span data-ttu-id="48f8c-122">Bu yapılandırma belirteçleri konu adı olan CN sertifika tarafından imzalanan belirtir = STS hizmeti tarafından kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="48f8c-122">This configuration specifies that tokens signed by a certificate whose subject name is CN=STS are accepted by the service.</span></span>  
  
 <span data-ttu-id="48f8c-123">STS kullanılabilir hale getirir tek bir uç nokta standart kullanarak <xref:System.ServiceModel.WS2007HttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="48f8c-123">STS makes a single endpoint available using the standard <xref:System.ServiceModel.WS2007HttpBinding>.</span></span> <span data-ttu-id="48f8c-124">Hizmet belirteçleri istemcilerden gelen isteklere yanıt verir.</span><span class="sxs-lookup"><span data-stu-id="48f8c-124">The service responds to requests from clients for tokens.</span></span> <span data-ttu-id="48f8c-125">Bir Windows hesabı kullanarak istemcinin kimliğinin, hizmeti bir talep olarak istemcinin kullanıcı adını içeren bir belirteç verir.</span><span class="sxs-lookup"><span data-stu-id="48f8c-125">If the client is authenticated using a Windows account, the service issues a token that contains the client's user name as a claim.</span></span> <span data-ttu-id="48f8c-126">STS işaretlerini belirtecin CN ile ilişkili özel anahtarı kullanarak belirteci oluşturma bir parçası olarak STS sertifikası =.</span><span class="sxs-lookup"><span data-stu-id="48f8c-126">As part of creating the token, STS signs the token using the private key associated with the CN=STS certificate.</span></span> <span data-ttu-id="48f8c-127">Ayrıca, bir simetrik anahtar oluşturur ve CN ile ilişkilendirilmiş ortak anahtar kullanarak şifreler localhost sertifika =.</span><span class="sxs-lookup"><span data-stu-id="48f8c-127">In addition, it creates a symmetric key and encrypts it using the public key associated with the CN=localhost certificate.</span></span> <span data-ttu-id="48f8c-128">Belirteç istemciye döndürmeden içinde STS, simetrik anahtar da döndürür.</span><span class="sxs-lookup"><span data-stu-id="48f8c-128">In returning the token to the client, STS also returns the symmetric key.</span></span> <span data-ttu-id="48f8c-129">Verilen belirteç istemci sunar `ICalculator` hizmet ve bunu simetrik anahtar bu anahtarla ileti imzalayarak bilen kanıtlar.</span><span class="sxs-lookup"><span data-stu-id="48f8c-129">The client presents the issued token to the `ICalculator` service and proves that it knows the symmetric key by signing the message with that key.</span></span>  
  
 <span data-ttu-id="48f8c-130">Örneği çalıştırdığınızda, güvenlik belirteci isteği STS konsol penceresinde gösterilir.</span><span class="sxs-lookup"><span data-stu-id="48f8c-130">When you run the sample, the request for the security token is shown in the STS console window.</span></span> <span data-ttu-id="48f8c-131">İşlem istekleri ve yanıtları istemci ve hizmet Konsolu pencerelerinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="48f8c-131">The operation's requests and responses are displayed in the client and service console windows.</span></span> <span data-ttu-id="48f8c-132">Herhangi bir windows konsol uygulamasını kapatmak için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="48f8c-132">Press ENTER in any of the console windows to shut down the application.</span></span>  

```
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714
Press <ENTER> to terminate client.
```

 <span data-ttu-id="48f8c-133">Bu örnekle dahil Setup.bat dosya sunucusu ve STS kendini barındıran bir uygulamayı çalıştırmak için ilgili sertifikalarla yapılandırmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="48f8c-133">The Setup.bat file included with this sample allows you to configure the server and STS with the relevant certificates to run a self-hosted application.</span></span> <span data-ttu-id="48f8c-134">Toplu iş dosyası LocalMachine/TrustedPeople sertifika deposunda iki sertifikaları oluşturur.</span><span class="sxs-lookup"><span data-stu-id="48f8c-134">The batch file creates two certificates in the LocalMachine/TrustedPeople certificate store.</span></span> <span data-ttu-id="48f8c-135">İlk sertifika CN bir konu adına sahip STS = ve STS tarafından istemcinin verdiği güvenlik belirteçleri imzalamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="48f8c-135">The first certificate has a subject name of CN=STS and is used by STS to sign the security tokens that it issues to the client.</span></span> <span data-ttu-id="48f8c-136">İkinci sertifikanın CN bir konu adına sahip localhost = ve STS tarafından hizmet şifresini çözebilir şekilde anahtarı şifrelemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="48f8c-136">The second certificate has a subject name of CN=localhost and is used by STS to encrypt a key in a way that the service can decrypt.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="48f8c-137">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="48f8c-137">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="48f8c-138">Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="48f8c-138">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="48f8c-139">Yönetici ayrıcalıklarına sahip bir Visual Studio komut istemi açın ve gerekli sertifikaları oluşturmak için Setup.bat dosyasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="48f8c-139">Open a Visual Studio command prompt with administrator privileges and run the Setup.bat file to create the required certificates.</span></span>  
  
 <span data-ttu-id="48f8c-140">Bu toplu iş dosyası Windows SDK ile birlikte dağıtılmış Certmgr.exe ve Makecert.exe, kullanır.</span><span class="sxs-lookup"><span data-stu-id="48f8c-140">This batch file uses Certmgr.exe and Makecert.exe, which are distributed with the Windows SDK.</span></span> <span data-ttu-id="48f8c-141">Ancak, bu araçları bulmak betik etkinleştirmek için Visual Studio komut istemi içinde Setup.bat gelen çalıştırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="48f8c-141">However, you must run Setup.bat from within a Visual Studio  command prompt to enable the script to find these tools.</span></span>  
  
1.  <span data-ttu-id="48f8c-142">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="48f8c-142">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2.  <span data-ttu-id="48f8c-143">Tek veya çapraz bilgisayar yapılandırmasında örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="48f8c-143">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span> <span data-ttu-id="48f8c-144">Kullanıyorsanız [!INCLUDE[windowsver](../../../../includes/windowsver-md.md)]Service.exe, Client.exe, çalıştırmak ve SecurityTokenService.exe ile yükseltilmiş ayrıcalıklar (dosyaları sağ tıklatın ve ardından **yönetici olarak çalıştır**).</span><span class="sxs-lookup"><span data-stu-id="48f8c-144">If you are using [!INCLUDE[windowsver](../../../../includes/windowsver-md.md)], you must run Service.exe, Client.exe, and SecurityTokenService.exe with elevated privileges (right-click the files and then click **Run as administrator**).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="48f8c-145">Örnekler, bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="48f8c-145">The samples may already be installed on your computer.</span></span> <span data-ttu-id="48f8c-146">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="48f8c-146">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="48f8c-147">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="48f8c-147">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="48f8c-148">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="48f8c-148">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\WS2007FederationHttp`  
  
## <a name="see-also"></a><span data-ttu-id="48f8c-149">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="48f8c-149">See Also</span></span>
