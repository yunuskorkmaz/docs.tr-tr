---
title: Güvenilir Alt Sistem
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1f5ce46b-e259-4bc9-a0b9-89d06fc9341c
ms.openlocfilehash: 59c44609017ab18a176624b7ef6d409005151c3f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33500376"
---
# <a name="trusted-subsystem"></a><span data-ttu-id="d4429-102">Güvenilir Alt Sistem</span><span class="sxs-lookup"><span data-stu-id="d4429-102">Trusted Subsystem</span></span>
<span data-ttu-id="d4429-103">Bir istemci bir ağ üzerinden dağıtılan bir veya daha fazla Web Hizmetleri erişir.</span><span class="sxs-lookup"><span data-stu-id="d4429-103">A client accesses one or more Web services that are distributed across a network.</span></span> <span data-ttu-id="d4429-104">Web Hizmetleri, bu erişim için ek kaynaklar (örneğin, veritabanları veya diğer Web Hizmetleri) Web hizmeti iş mantığı kapsüllenir şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="d4429-104">The Web services are designed so that access to additional resources (such as databases or other Web services) is encapsulated in the business logic of the Web service.</span></span> <span data-ttu-id="d4429-105">Bu kaynakların yetkisiz erişime karşı korunması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d4429-105">These resources must be protected against unauthorized access.</span></span> <span data-ttu-id="d4429-106">Aşağıdaki çizimde bir güvenilir alt sistem işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="d4429-106">The following illustration depicts a trusted subsystem process.</span></span>  
  
 <span data-ttu-id="d4429-107">![Alt sistemi güvenilir](../../../../docs/framework/wcf/feature-details/media/wcfc-trustedsubsystemc.gif "wcfc_TrustedSubsystemc")</span><span class="sxs-lookup"><span data-stu-id="d4429-107">![Trusted subsystem](../../../../docs/framework/wcf/feature-details/media/wcfc-trustedsubsystemc.gif "wcfc_TrustedSubsystemc")</span></span>  
  
 <span data-ttu-id="d4429-108">Aşağıdaki adımlar, gösterildiği gibi güvenilir alt sistem işlemini açıklamaktadır:</span><span class="sxs-lookup"><span data-stu-id="d4429-108">The following steps describe the trusted subsystem process as illustrated:</span></span>  
  
1.  <span data-ttu-id="d4429-109">İstemci kimlik bilgileri ile birlikte güvenilir alt sistem için bir istek gönderir.</span><span class="sxs-lookup"><span data-stu-id="d4429-109">The client submits a request to the trusted subsystem, along with credentials.</span></span>  
  
2.  <span data-ttu-id="d4429-110">Güvenilir alt sistem kimliğini doğrular ve kullanıcı yetkilendirir.</span><span class="sxs-lookup"><span data-stu-id="d4429-110">The trusted subsystem authenticates and authorizes the user.</span></span>  
  
3.  <span data-ttu-id="d4429-111">Güvenilir alt sistem uzak kaynak için bir istek iletisi gönderir.</span><span class="sxs-lookup"><span data-stu-id="d4429-111">The trusted subsystem sends a request message to the remote resource.</span></span> <span data-ttu-id="d4429-112">Bu istek, güvenilir alt sistem (veya hizmet hesabı altında güvenilir alt sistem işlem yürütülmekte olan) için kimlik bilgilerini eşlik eder.</span><span class="sxs-lookup"><span data-stu-id="d4429-112">This request is accompanied by the credentials for the trusted subsystem (or the service account under which the trusted subsystem process is being executed).</span></span>  
  
4.  <span data-ttu-id="d4429-113">Arka uç kaynak kimliğini doğrular ve güvenilir alt sistem yetkilendirir.</span><span class="sxs-lookup"><span data-stu-id="d4429-113">The back-end resource authenticates and authorizes the trusted subsystem.</span></span> <span data-ttu-id="d4429-114">İsteği işler ve güvenilir alt sistem yanıt verir.</span><span class="sxs-lookup"><span data-stu-id="d4429-114">It then processes the request and issues a response to the trusted subsystem.</span></span>  
  
5.  <span data-ttu-id="d4429-115">Güvenilir alt sistem yanıt işler ve istemciye kendi yanıt verir.</span><span class="sxs-lookup"><span data-stu-id="d4429-115">The trusted subsystem processes the response and issues its own response to the client.</span></span>  
  
|<span data-ttu-id="d4429-116">Özelliği</span><span class="sxs-lookup"><span data-stu-id="d4429-116">Characteristic</span></span>|<span data-ttu-id="d4429-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d4429-117">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="d4429-118">Güvenlik modu</span><span class="sxs-lookup"><span data-stu-id="d4429-118">Security Mode</span></span>|<span data-ttu-id="d4429-119">İleti</span><span class="sxs-lookup"><span data-stu-id="d4429-119">Message</span></span>|  
|<span data-ttu-id="d4429-120">Birlikte Çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="d4429-120">Interoperability</span></span>|<span data-ttu-id="d4429-121">Windows Communication Foundation (WCF) yalnızca.</span><span class="sxs-lookup"><span data-stu-id="d4429-121">Windows Communication Foundation (WCF) only.</span></span>|  
|<span data-ttu-id="d4429-122">Kimlik doğrulaması (hizmeti)</span><span class="sxs-lookup"><span data-stu-id="d4429-122">Authentication (service)</span></span>|<span data-ttu-id="d4429-123">Güvenlik belirteci hizmeti kimliğini doğrular ve istemcilerin yetkilendirir.</span><span class="sxs-lookup"><span data-stu-id="d4429-123">Security token service authenticates and authorizes clients.</span></span>|  
|<span data-ttu-id="d4429-124">Kimlik doğrulaması (istemci)</span><span class="sxs-lookup"><span data-stu-id="d4429-124">Authentication (client)</span></span>|<span data-ttu-id="d4429-125">Güvenilir alt sistem istemcinin kimliğini doğrular ve güvenilir alt sistem hizmeti kaynak kimliğini doğrular.</span><span class="sxs-lookup"><span data-stu-id="d4429-125">The trusted subsystem authenticates the client and the resource authenticates the trusted subsystem service.</span></span>|  
|<span data-ttu-id="d4429-126">Bütünlük</span><span class="sxs-lookup"><span data-stu-id="d4429-126">Integrity</span></span>|<span data-ttu-id="d4429-127">Evet</span><span class="sxs-lookup"><span data-stu-id="d4429-127">Yes</span></span>|  
|<span data-ttu-id="d4429-128">Gizliliği</span><span class="sxs-lookup"><span data-stu-id="d4429-128">Confidentiality</span></span>|<span data-ttu-id="d4429-129">Evet</span><span class="sxs-lookup"><span data-stu-id="d4429-129">Yes</span></span>|  
|<span data-ttu-id="d4429-130">Taşıma</span><span class="sxs-lookup"><span data-stu-id="d4429-130">Transport</span></span>|<span data-ttu-id="d4429-131">HTTP istemci ve güvenilir alt sistem hizmeti arasında.</span><span class="sxs-lookup"><span data-stu-id="d4429-131">HTTP between client and the trusted subsystem service.</span></span><br /><br /> <span data-ttu-id="d4429-132">NET. Güvenilir alt sistem hizmeti ve kaynak (arka uç hizmeti) arasında TCP.</span><span class="sxs-lookup"><span data-stu-id="d4429-132">NET.TCP between trusted subsystem service and the resource (back-end service).</span></span>|  
|<span data-ttu-id="d4429-133">Bağlama</span><span class="sxs-lookup"><span data-stu-id="d4429-133">Binding</span></span>|<span data-ttu-id="d4429-134"><xref:System.ServiceModel.WSHttpBinding> ve <xref:System.ServiceModel.NetTcpBinding> [ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="d4429-134"><xref:System.ServiceModel.WSHttpBinding> and <xref:System.ServiceModel.NetTcpBinding>[\<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)</span></span>|  
  
## <a name="resource-back-end-service"></a><span data-ttu-id="d4429-135">Kaynak (arka uç hizmeti)</span><span class="sxs-lookup"><span data-stu-id="d4429-135">Resource (Back-End Service)</span></span>  
  
### <a name="code"></a><span data-ttu-id="d4429-136">Kod</span><span class="sxs-lookup"><span data-stu-id="d4429-136">Code</span></span>  
 <span data-ttu-id="d4429-137">Aşağıdaki kod bir hizmet uç noktası TCP Aktarım Protokolü üzerinden aktarım güvenliği kullanır kaynağın oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d4429-137">The following code shows how to create a service endpoint for the resource, which uses transport security over the TCP transport protocol.</span></span>  
  
 [!code-csharp[TrustedSubSystemsResource#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/trustedsubsystemsresource/cs/source.cs#1)]
 [!code-vb[TrustedSubSystemsResource#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/trustedsubsystemsresource/vb/source.vb#1)]  
  
### <a name="configuration"></a><span data-ttu-id="d4429-138">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="d4429-138">Configuration</span></span>  
 <span data-ttu-id="d4429-139">Aşağıdaki yapılandırma Yapılandırması'nı kullanarak aynı uç nokta ayarlamayı ayarlar.</span><span class="sxs-lookup"><span data-stu-id="d4429-139">The following configuration sets up the same endpoint using configuration.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service name="Microsoft.ServiceModel.Samples.BackendService"  
               behaviorConfiguration="BackendServiceBehavior">  
        <endpoint address="net.tcp://localhost.com:8001/BackendService"  
                  binding="customBinding"  
                  bindingConfiguration="Binding1"  
                  contract="Microsoft.ServiceModel.Samples.ICalculator"/>  
      </service>  
    </services>  
    <bindings>  
      <customBinding>  
        <binding name="Binding1">  
          <security authenticationMode="UserNameOverTransport"/>  
          <windowsStreamSecurity/>  
          <tcpTransport/>  
        </binding>  
      </customBinding>  
    </bindings>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="BackendServiceBehavior">  
          <serviceCredentials>  
            <userNameAuthentication userNamePasswordValidationMode="Custom"  
                                    customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.MyUserNamePasswordValidator, BackendService"/>  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="trusted-subsystem"></a><span data-ttu-id="d4429-140">Güvenilir Alt Sistem</span><span class="sxs-lookup"><span data-stu-id="d4429-140">Trusted Subsystem</span></span>  
  
### <a name="code"></a><span data-ttu-id="d4429-141">Kod</span><span class="sxs-lookup"><span data-stu-id="d4429-141">Code</span></span>  
 <span data-ttu-id="d4429-142">Aşağıdaki kodu için ileti güvenliği ve bir kullanıcı adı ve parola HTTP protokolü kimlik doğrulaması için kullandığı güvenilir alt sistem Hizmeti uç noktası oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d4429-142">The following code shows how to create a service endpoint for the trusted subsystem that uses message security over the HTTP protocol and a user name and password for authentication.</span></span>  
  
 [!code-csharp[TrustedSubSystems#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/trustedsubsystems/cs/source.cs#1)]
 [!code-vb[TrustedSubSystems#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/trustedsubsystems/vb/source.vb#1)]  
  
 <span data-ttu-id="d4429-143">Aşağıdaki kod bir hizmet TCP Aktarım Protokolü üzerinden aktarım güvenliği'ni kullanarak bir arka uç hizmeti ile iletişim kurar güvenilir bir alt sistem gösterir.</span><span class="sxs-lookup"><span data-stu-id="d4429-143">The following code shows a service in a trusted subsystem that communicates with a back-end service using transport security over the TCP transport protocol.</span></span>  
  
 [!code-csharp[TrustedSubSystems#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/trustedsubsystems/cs/source.cs#2)]
 [!code-vb[TrustedSubSystems#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/trustedsubsystems/vb/source.vb#2)]  
  
### <a name="configuration"></a><span data-ttu-id="d4429-144">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="d4429-144">Configuration</span></span>  
 <span data-ttu-id="d4429-145">Aşağıdaki yapılandırma Yapılandırması'nı kullanarak aynı uç nokta ayarlamayı ayarlar.</span><span class="sxs-lookup"><span data-stu-id="d4429-145">The following configuration sets up the same endpoint using configuration.</span></span> <span data-ttu-id="d4429-146">İki bağlamaları Not: bir güvenilir alt sisteminde barındırılan hizmete güvenliğini sağlar ve diğer güvenilir alt sistem ve arka uç hizmeti arasındaki iletişim kurar.</span><span class="sxs-lookup"><span data-stu-id="d4429-146">Note the two bindings: One secures the service hosted in the trusted subsystem and the other communicates between the trusted subsystem and the back-end service.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service name="Microsoft.ServiceModel.Samples.FacadeService"  
               behaviorConfiguration="FacadeServiceBehavior">  
        <host>  
          <baseAddresses>  
            <add baseAddress="http://localhost:8000/FacadeService"/>  
          </baseAddresses>  
        </host>  
        <endpoint address="http://localhost:8000/FacadeService"  
                  binding="wsHttpBinding"  
                  bindingConfiguration="Binding1"  
                  contract="Microsoft.ServiceModel.Samples.ICalculator"/>  
      </service>  
    </services>  
    <client>  
      <endpoint name=""   
                address="net.tcp://contoso.com:8001/BackendService"  
                binding="customBinding"  
                bindingConfiguration="ClientBinding"  
                contract="Microsoft.ServiceModel.Samples.ICalculator"/>  
    </client>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="Binding1">  
          <security mode="Message">  
            <message clientCredentialType="UserName"/>  
          </security>  
        </binding>  
      </wsHttpBinding>  
      <customBinding>  
        <binding name="ClientBinding">  
          <security authenticationMode="UserNameOverTransport"/>  
          <windowsStreamSecurity/>  
          <tcpTransport/>  
        </binding>  
      </customBinding>  
    </bindings>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="FacadeServiceBehavior">  
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceCredentials>  
            <serviceCertificate findValue="Contoso.com"  
                                storeLocation="LocalMachine"  
                                storeName="My"  
                                x509FindType="FindBySubjectName" />  
            <userNameAuthentication userNamePasswordValidationMode="Custom"  
                                    customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.MyUserNamePasswordValidator, FacadeService"/>  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a><span data-ttu-id="d4429-147">İstemci</span><span class="sxs-lookup"><span data-stu-id="d4429-147">Client</span></span>  
  
### <a name="code"></a><span data-ttu-id="d4429-148">Kod</span><span class="sxs-lookup"><span data-stu-id="d4429-148">Code</span></span>  
 <span data-ttu-id="d4429-149">Aşağıdaki kod istemcisi ile güvenilir alt sistem ve bir kullanıcı adı ve parola HTTP protokolü kimlik doğrulaması için ileti güvenliği kullanılarak oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d4429-149">The following code shows how to create the client that communicates with the trusted subsystem by using message security over the HTTP protocol and a user name and password for authentication.</span></span>  
  
 [!code-csharp[TrustedSubSystemsClient#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/trustedsubsystemsclient/cs/source.cs#1)]
 [!code-vb[TrustedSubSystemsClient#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/trustedsubsystemsclient/vb/source.vb#1)]  
  
### <a name="configuration"></a><span data-ttu-id="d4429-150">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="d4429-150">Configuration</span></span>  
 <span data-ttu-id="d4429-151">Aşağıdaki kod, ileti güvenliği ve bir kullanıcı adı ve parola HTTP protokolü kimlik doğrulaması için kullanmak üzere istemciyi yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="d4429-151">The following code configures the client to use message security over the HTTP protocol and a user name and password for authentication.</span></span> <span data-ttu-id="d4429-152">Kullanıcı adı ve parola yalnızca kodu (Kısım yapılandırılabilir değildir) kullanılarak belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="d4429-152">The user name and password can only be specified using code (it is not configurable).</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.serviceModel>  
    <client>  
        <endpoint name=""   
                  address="http://www.cohowinery.com:8000/FacadeService"  
                  binding="wsHttpBinding"  
                  bindingConfiguration="Binding1"  
                  behaviorConfiguration="ClientUserNameBehavior"  
                  contract="Microsoft.ServiceModel.Samples.ICalculator"/>  
    </client>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="Binding1">  
          <security mode="Message">  
            <message clientCredentialType="UserName"/>  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="ClientUserNameBehavior">  
          <clientCredentials>  
            <serviceCertificate>  
              <authentication certificateValidationMode="PeerOrChainTrust"/>  
            </serviceCertificate>  
          </clientCredentials>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d4429-153">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d4429-153">See Also</span></span>  
 [<span data-ttu-id="d4429-154">Güvenliğe Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="d4429-154">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="d4429-155">Windows Server App Fabric için güvenlik modeli</span><span class="sxs-lookup"><span data-stu-id="d4429-155">Security Model for Windows Server App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
