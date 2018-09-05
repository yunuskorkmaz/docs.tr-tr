---
title: WS 2007 Federasyon HTTP Bağlama
ms.date: 03/30/2017
ms.assetid: 91c1b477-a96e-4bf5-9330-5e9312113371
ms.openlocfilehash: 53f2cb893476cdfa0517bd6586f38951dff1f2af
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43513068"
---
# <a name="ws-2007-federation-http-binding"></a><span data-ttu-id="8936d-102">WS 2007 Federasyon HTTP Bağlama</span><span class="sxs-lookup"><span data-stu-id="8936d-102">WS 2007 Federation HTTP Binding</span></span>
<span data-ttu-id="8936d-103">Bu örnek, kullanımını gösterir. <xref:System.ServiceModel.WS2007FederationHttpBinding>, WS-Güven belirtimini destek sürümünün 1.3 Federasyon senaryolarında oluşturmak için kullanabileceğiniz bağlama standart.</span><span class="sxs-lookup"><span data-stu-id="8936d-103">This sample demonstrates the use of <xref:System.ServiceModel.WS2007FederationHttpBinding>, a standard binding that you can use to build federated scenarios that support version 1.3 of the WS-Trust specification.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8936d-104">Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="8936d-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="8936d-105">Örnek bir konsol tabanlı istemci programını (Client.exe), bir konsol tabanlı güvenlik belirteci hizmeti program (Securitytokenservice.exe) ve konsol tabanlı hizmet programı (Service.exe) oluşur.</span><span class="sxs-lookup"><span data-stu-id="8936d-105">The sample consists of a console-based client program (Client.exe), a console-based security token service program (Securitytokenservice.exe), and a console-based service program (Service.exe).</span></span> <span data-ttu-id="8936d-106">Hizmet istek/yanıt iletişim deseni tanımlayan bir sözleşme uygular.</span><span class="sxs-lookup"><span data-stu-id="8936d-106">The service implements a contract that defines a request/reply communication pattern.</span></span> <span data-ttu-id="8936d-107">Anlaşma tarafından tanımlanan `ICalculator` matematik işlemlerinden sunan arabirimi (`Add`, `Subtract`, `Multiply`, ve `Divide`).</span><span class="sxs-lookup"><span data-stu-id="8936d-107">The contract is defined by the `ICalculator` interface, which exposes math operations (`Add`, `Subtract`, `Multiply`, and `Divide`).</span></span> <span data-ttu-id="8936d-108">İstemci güvenlik belirteci hizmeti (STS) gelen bir güvenlik belirteci alır ve hizmet verilen matematik işlemi için zaman uyumlu istekleri yapar.</span><span class="sxs-lookup"><span data-stu-id="8936d-108">The client obtains a security token from the Security Token Service (STS) and makes synchronous requests to the service for a given math operation.</span></span> <span data-ttu-id="8936d-109">Hizmet ardından sonucu, yanıt.</span><span class="sxs-lookup"><span data-stu-id="8936d-109">The service then replies with the result.</span></span> <span data-ttu-id="8936d-110">İstemci etkinliği konsol penceresinde görünür.</span><span class="sxs-lookup"><span data-stu-id="8936d-110">Client activity is visible in the console window.</span></span>  
  
 <span data-ttu-id="8936d-111">Örnek yapar `ICalculator` sözleşme aracılığıyla kullanılabilir `ws2007FederationHttpBinding` öğesi.</span><span class="sxs-lookup"><span data-stu-id="8936d-111">The sample makes the `ICalculator` contract available using the `ws2007FederationHttpBinding` element.</span></span> <span data-ttu-id="8936d-112">Bu bağlamanın istemcide yapılandırma aşağıdaki kodda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="8936d-112">The configuration of this binding on the client is shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="8936d-113">Üzerinde [ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md), `security` hangi güvenlik modunda kullanılması gereken bir değer belirtir.</span><span class="sxs-lookup"><span data-stu-id="8936d-113">On the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md), the `security` value specifies which security mode should be used.</span></span> <span data-ttu-id="8936d-114">Bu örnekte `message` güvenlik kullanılır, neden olduğu [ \<ileti >](../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) içinde belirtilen [ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="8936d-114">In this sample, `message` security is used, which is why the [\<message>](../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) is specified inside the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md).</span></span> <span data-ttu-id="8936d-115">[ \<Veren >](../../../../docs/framework/configure-apps/file-schema/wcf/issuer.md) öğe içinde [ \<ileti >](../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) STS için istemciye bir güvenlik belirteci verir ve böylece istemci için bağlamasını ve adresini belirtir. kimlik doğrulaması `ICalculator` hizmeti.</span><span class="sxs-lookup"><span data-stu-id="8936d-115">The [\<issuer>](../../../../docs/framework/configure-apps/file-schema/wcf/issuer.md) element inside the [\<message>](../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) specifies the address and binding for the STS that issues a security token to the client so that the client can authenticate to the `ICalculator` service.</span></span>  
  
 <span data-ttu-id="8936d-116">Bu bağlamanın hizmet yapılandırma aşağıdaki kodda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="8936d-116">The configuration of this binding on the service is shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="8936d-117">Üzerinde [ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md), `security` hangi güvenlik modunda kullanılması gereken bir değer belirtir.</span><span class="sxs-lookup"><span data-stu-id="8936d-117">On the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md), the `security` value specifies which security mode should be used.</span></span> <span data-ttu-id="8936d-118">Bu örnekte `message` güvenlik kullanılır, neden olduğu [ \<ileti >](../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) içinde belirtilen [ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="8936d-118">In this sample, `message` security is used, which is why the [\<message>](../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) is specified inside the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md).</span></span> <span data-ttu-id="8936d-119">[ \<İssuedtokenparameters >](../../../../docs/framework/configure-apps/file-schema/wcf/issuermetadata.md) öğesinin `ws2007FederationHttpBinding` içinde [ \<ileti >](../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) almak için kullanılan bir uç nokta için kimlik ve adresini belirtir STS meta verileri.</span><span class="sxs-lookup"><span data-stu-id="8936d-119">The [\<issuerMetadata>](../../../../docs/framework/configure-apps/file-schema/wcf/issuermetadata.md) element of `ws2007FederationHttpBinding` inside the [\<message>](../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) specifies the address and identity for an endpoint that can be used to retrieve metadata for the STS.</span></span>  
  
 <span data-ttu-id="8936d-120">Hizmet davranışı, aşağıdaki kodda gösterilir.</span><span class="sxs-lookup"><span data-stu-id="8936d-120">The behavior for the service is shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="8936d-121">[ \<ServiceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)> Hizmet istemcileri kimlik doğrulaması sırasında sunmak veren belirteçleri kısıtlamaları belirlemenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="8936d-121">The [\<issuedTokenAuthentication>](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)> allows the service to specify constraints on the tokens it allows clients to present during authentication.</span></span> <span data-ttu-id="8936d-122">Bu yapılandırma, belirteçleri CN konu adı olan bir sertifika tarafından imzalanmış belirtir = STS hizmeti tarafından kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="8936d-122">This configuration specifies that tokens signed by a certificate whose subject name is CN=STS are accepted by the service.</span></span>  
  
 <span data-ttu-id="8936d-123">STS kullanımınıza tek bir uç nokta standardını kullanarak <xref:System.ServiceModel.WS2007HttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="8936d-123">STS makes a single endpoint available using the standard <xref:System.ServiceModel.WS2007HttpBinding>.</span></span> <span data-ttu-id="8936d-124">Belirteçler için istemcilerden hizmet isteklerine yanıt verir.</span><span class="sxs-lookup"><span data-stu-id="8936d-124">The service responds to requests from clients for tokens.</span></span> <span data-ttu-id="8936d-125">İstemci bir Windows hesabı kullanarak kimlik doğrulaması gerekiyorsa, hizmeti bir talep olarak istemcinin kullanıcı adını içeren bir belirteç verir.</span><span class="sxs-lookup"><span data-stu-id="8936d-125">If the client is authenticated using a Windows account, the service issues a token that contains the client's user name as a claim.</span></span> <span data-ttu-id="8936d-126">Belirteç, STS işaretleri CN ile ilişkili özel anahtarı kullanarak belirteci oluşturma işleminin parçası olarak STS sertifikasını =.</span><span class="sxs-lookup"><span data-stu-id="8936d-126">As part of creating the token, STS signs the token using the private key associated with the CN=STS certificate.</span></span> <span data-ttu-id="8936d-127">Ayrıca, bir simetrik anahtar oluşturur ve CN ile ilişkili bir ortak anahtar kullanarak şifreler = localhost sertifikasına.</span><span class="sxs-lookup"><span data-stu-id="8936d-127">In addition, it creates a symmetric key and encrypts it using the public key associated with the CN=localhost certificate.</span></span> <span data-ttu-id="8936d-128">Belirteci istemciye göndermeden, STS, simetrik anahtarı da döndürür.</span><span class="sxs-lookup"><span data-stu-id="8936d-128">In returning the token to the client, STS also returns the symmetric key.</span></span> <span data-ttu-id="8936d-129">İstemci için verilen belirtecin sunar `ICalculator` hizmet ve bunu simetrik anahtarı bu anahtarla ileti açarak bilen kanıtlar.</span><span class="sxs-lookup"><span data-stu-id="8936d-129">The client presents the issued token to the `ICalculator` service and proves that it knows the symmetric key by signing the message with that key.</span></span>  
  
 <span data-ttu-id="8936d-130">Örneği çalıştırdığında, güvenlik belirteci isteği STS konsol penceresinde gösterilir.</span><span class="sxs-lookup"><span data-stu-id="8936d-130">When you run the sample, the request for the security token is shown in the STS console window.</span></span> <span data-ttu-id="8936d-131">İşlem istekleri ve yanıtları istemci ve hizmet Konsolu pencerelerinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="8936d-131">The operation's requests and responses are displayed in the client and service console windows.</span></span> <span data-ttu-id="8936d-132">Uygulamayı kapatın, herhangi bir windows konsol ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="8936d-132">Press ENTER in any of the console windows to shut down the application.</span></span>  

```
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714
Press <ENTER> to terminate client.
```

 <span data-ttu-id="8936d-133">Bu örnekle dahil Setup.bat dosyasının, STS'ye ve sunucu şirket içinde barındırılan bir uygulamayı çalıştırmak için ilgili sertifikalarla yapılandırmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="8936d-133">The Setup.bat file included with this sample allows you to configure the server and STS with the relevant certificates to run a self-hosted application.</span></span> <span data-ttu-id="8936d-134">Toplu iş dosyasını iki sertifikalar LocalMachine/TrustedPeople sertifika deposunda oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8936d-134">The batch file creates two certificates in the LocalMachine/TrustedPeople certificate store.</span></span> <span data-ttu-id="8936d-135">İlk sertifikayı sahip bir konu adı CN = STS ve STS tarafından istemcinin verdiği güvenlik belirteçleri imzalamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8936d-135">The first certificate has a subject name of CN=STS and is used by STS to sign the security tokens that it issues to the client.</span></span> <span data-ttu-id="8936d-136">İkinci sertifikayı sahip bir konu adı CN = localhost ve STS tarafından bir anahtar hizmet şifresini çözebilir bir şekilde şifrelemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8936d-136">The second certificate has a subject name of CN=localhost and is used by STS to encrypt a key in a way that the service can decrypt.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="8936d-137">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="8936d-137">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="8936d-138">Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="8936d-138">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="8936d-139">Yönetici ayrıcalıklarına sahip bir Visual Studio komut istemi açın ve gerekli sertifikaları oluşturmak için Setup.bat dosyasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="8936d-139">Open a Visual Studio command prompt with administrator privileges and run the Setup.bat file to create the required certificates.</span></span>  
  
 <span data-ttu-id="8936d-140">Windows SDK'sı ile dağıtılmış Certmgr.exe ve Makecert.exe, bu toplu iş dosyası kullanır.</span><span class="sxs-lookup"><span data-stu-id="8936d-140">This batch file uses Certmgr.exe and Makecert.exe, which are distributed with the Windows SDK.</span></span> <span data-ttu-id="8936d-141">Ancak, bu araçları bulmak betik etkinleştirmek için Visual Studio komut istemi içinde gelen Setup.bat çalıştırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="8936d-141">However, you must run Setup.bat from within a Visual Studio  command prompt to enable the script to find these tools.</span></span>  
  
1.  <span data-ttu-id="8936d-142">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="8936d-142">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2.  <span data-ttu-id="8936d-143">Tek veya çoklu bilgisayar yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="8936d-143">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span> <span data-ttu-id="8936d-144">Kullanıyorsanız [!INCLUDE[windowsver](../../../../includes/windowsver-md.md)]SecurityTokenService.exe ile yükseltilmiş ayrıcalıklar ve Service.exe, Client.exe, çalıştırmanız gerekir (dosyaları sağ tıklayın ve ardından **yönetici olarak çalıştır**).</span><span class="sxs-lookup"><span data-stu-id="8936d-144">If you are using [!INCLUDE[windowsver](../../../../includes/windowsver-md.md)], you must run Service.exe, Client.exe, and SecurityTokenService.exe with elevated privileges (right-click the files and then click **Run as administrator**).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="8936d-145">Örnekler, bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="8936d-145">The samples may already be installed on your computer.</span></span> <span data-ttu-id="8936d-146">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="8936d-146">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="8936d-147">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="8936d-147">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="8936d-148">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="8936d-148">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\WS2007FederationHttp`  
  
## <a name="see-also"></a><span data-ttu-id="8936d-149">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8936d-149">See Also</span></span>
