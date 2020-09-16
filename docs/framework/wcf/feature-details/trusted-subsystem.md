---
title: Güvenilir Alt Sistem
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1f5ce46b-e259-4bc9-a0b9-89d06fc9341c
ms.openlocfilehash: 29ac26616313ec8bd7661cb92c42f726ec051cd7
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90542893"
---
# <a name="trusted-subsystem"></a><span data-ttu-id="1abae-102">Güvenilir Alt Sistem</span><span class="sxs-lookup"><span data-stu-id="1abae-102">Trusted Subsystem</span></span>
<span data-ttu-id="1abae-103">İstemci bir ağ üzerinde dağıtılan bir veya daha fazla Web hizmetine erişir.</span><span class="sxs-lookup"><span data-stu-id="1abae-103">A client accesses one or more Web services that are distributed across a network.</span></span> <span data-ttu-id="1abae-104">Web Hizmetleri, ek kaynaklara erişimin (veritabanları veya diğer Web Hizmetleri gibi) Web hizmetinin iş mantığıyla kapsüllenmesi için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="1abae-104">The Web services are designed so that access to additional resources (such as databases or other Web services) is encapsulated in the business logic of the Web service.</span></span> <span data-ttu-id="1abae-105">Bu kaynakların yetkisiz erişime karşı korunması gerekir.</span><span class="sxs-lookup"><span data-stu-id="1abae-105">These resources must be protected against unauthorized access.</span></span> <span data-ttu-id="1abae-106">Aşağıdaki çizimde, güvenilir bir alt sistem işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1abae-106">The following illustration depicts a trusted subsystem process.</span></span>  
  
 <span data-ttu-id="1abae-107">![Güvenilen alt sistem](media/wcfc-trustedsubsystemc.gif "wcfc_TrustedSubsystemc")</span><span class="sxs-lookup"><span data-stu-id="1abae-107">![Trusted subsystem](media/wcfc-trustedsubsystemc.gif "wcfc_TrustedSubsystemc")</span></span>  
  
 <span data-ttu-id="1abae-108">Aşağıdaki adımlar gösterildiği gibi güvenilir alt sistem işlemini anlatmaktadır:</span><span class="sxs-lookup"><span data-stu-id="1abae-108">The following steps describe the trusted subsystem process as illustrated:</span></span>  
  
1. <span data-ttu-id="1abae-109">İstemci, kimlik bilgileriyle birlikte güvenilen alt sisteme bir istek gönderir.</span><span class="sxs-lookup"><span data-stu-id="1abae-109">The client submits a request to the trusted subsystem, along with credentials.</span></span>  
  
2. <span data-ttu-id="1abae-110">Güvenilen alt sistem, kullanıcının kimliğini doğrular ve yetkilendirir.</span><span class="sxs-lookup"><span data-stu-id="1abae-110">The trusted subsystem authenticates and authorizes the user.</span></span>  
  
3. <span data-ttu-id="1abae-111">Güvenilen alt sistem, uzak kaynağa bir istek iletisi gönderir.</span><span class="sxs-lookup"><span data-stu-id="1abae-111">The trusted subsystem sends a request message to the remote resource.</span></span> <span data-ttu-id="1abae-112">Bu isteğe, güvenilen alt sistem (veya güvenilir alt sistem işleminin yürütüldüğü hizmet hesabı) için kimlik bilgileri eşlik eder.</span><span class="sxs-lookup"><span data-stu-id="1abae-112">This request is accompanied by the credentials for the trusted subsystem (or the service account under which the trusted subsystem process is being executed).</span></span>  
  
4. <span data-ttu-id="1abae-113">Arka uç kaynağı, güvenilen alt sistemi doğrular ve yetkilendirir.</span><span class="sxs-lookup"><span data-stu-id="1abae-113">The back-end resource authenticates and authorizes the trusted subsystem.</span></span> <span data-ttu-id="1abae-114">Ardından, isteği işler ve güvenilir alt sisteme yanıt verir.</span><span class="sxs-lookup"><span data-stu-id="1abae-114">It then processes the request and issues a response to the trusted subsystem.</span></span>  
  
5. <span data-ttu-id="1abae-115">Güvenilen alt sistem yanıtı işler ve istemciye kendi yanıtını verir.</span><span class="sxs-lookup"><span data-stu-id="1abae-115">The trusted subsystem processes the response and issues its own response to the client.</span></span>  
  
|<span data-ttu-id="1abae-116">Özellik</span><span class="sxs-lookup"><span data-stu-id="1abae-116">Characteristic</span></span>|<span data-ttu-id="1abae-117">Description</span><span class="sxs-lookup"><span data-stu-id="1abae-117">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="1abae-118">Güvenlik modu</span><span class="sxs-lookup"><span data-stu-id="1abae-118">Security Mode</span></span>|<span data-ttu-id="1abae-119">İleti</span><span class="sxs-lookup"><span data-stu-id="1abae-119">Message</span></span>|  
|<span data-ttu-id="1abae-120">Birlikte Çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="1abae-120">Interoperability</span></span>|<span data-ttu-id="1abae-121">Yalnızca Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="1abae-121">Windows Communication Foundation (WCF) only.</span></span>|  
|<span data-ttu-id="1abae-122">Kimlik doğrulaması (hizmet)</span><span class="sxs-lookup"><span data-stu-id="1abae-122">Authentication (service)</span></span>|<span data-ttu-id="1abae-123">Güvenlik belirteci hizmeti, istemcilerin kimliğini doğrular ve yetkilendirir.</span><span class="sxs-lookup"><span data-stu-id="1abae-123">Security token service authenticates and authorizes clients.</span></span>|  
|<span data-ttu-id="1abae-124">Kimlik doğrulaması (istemci)</span><span class="sxs-lookup"><span data-stu-id="1abae-124">Authentication (client)</span></span>|<span data-ttu-id="1abae-125">Güvenilen alt sistem istemcinin kimliğini doğrular ve kaynak, güvenilen alt sistem hizmetinin kimliğini doğrular.</span><span class="sxs-lookup"><span data-stu-id="1abae-125">The trusted subsystem authenticates the client and the resource authenticates the trusted subsystem service.</span></span>|  
|<span data-ttu-id="1abae-126">Bütünlük</span><span class="sxs-lookup"><span data-stu-id="1abae-126">Integrity</span></span>|<span data-ttu-id="1abae-127">Yes</span><span class="sxs-lookup"><span data-stu-id="1abae-127">Yes</span></span>|  
|<span data-ttu-id="1abae-128">Gizlilik</span><span class="sxs-lookup"><span data-stu-id="1abae-128">Confidentiality</span></span>|<span data-ttu-id="1abae-129">Yes</span><span class="sxs-lookup"><span data-stu-id="1abae-129">Yes</span></span>|  
|<span data-ttu-id="1abae-130">Aktarım</span><span class="sxs-lookup"><span data-stu-id="1abae-130">Transport</span></span>|<span data-ttu-id="1abae-131">İstemci ile güvenilen alt sistem hizmeti arasında HTTP.</span><span class="sxs-lookup"><span data-stu-id="1abae-131">HTTP between client and the trusted subsystem service.</span></span><br /><br /> <span data-ttu-id="1abae-132">NET. Güvenilen alt sistem hizmeti ve kaynak (arka uç hizmeti) arasında TCP.</span><span class="sxs-lookup"><span data-stu-id="1abae-132">NET.TCP between trusted subsystem service and the resource (back-end service).</span></span>|  
|<span data-ttu-id="1abae-133">Bağlama</span><span class="sxs-lookup"><span data-stu-id="1abae-133">Binding</span></span>|<span data-ttu-id="1abae-134"><xref:System.ServiceModel.WSHttpBinding> ' <xref:System.ServiceModel.NetTcpBinding>[\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="1abae-134"><xref:System.ServiceModel.WSHttpBinding> and <xref:System.ServiceModel.NetTcpBinding>[\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md)</span></span>|  
  
## <a name="resource-back-end-service"></a><span data-ttu-id="1abae-135">Kaynak (arka uç hizmeti)</span><span class="sxs-lookup"><span data-stu-id="1abae-135">Resource (Back-End Service)</span></span>  
  
### <a name="code"></a><span data-ttu-id="1abae-136">Kod</span><span class="sxs-lookup"><span data-stu-id="1abae-136">Code</span></span>  
 <span data-ttu-id="1abae-137">Aşağıdaki kod, TCP Aktarım Protokolü üzerinden aktarım güvenliği kullanan kaynak için bir hizmet uç noktası oluşturmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="1abae-137">The following code shows how to create a service endpoint for the resource, which uses transport security over the TCP transport protocol.</span></span>  
  
 [!code-csharp[TrustedSubSystemsResource#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/trustedsubsystemsresource/cs/source.cs#1)]
 [!code-vb[TrustedSubSystemsResource#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/trustedsubsystemsresource/vb/source.vb#1)]  
  
### <a name="configuration"></a><span data-ttu-id="1abae-138">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="1abae-138">Configuration</span></span>  
 <span data-ttu-id="1abae-139">Aşağıdaki yapılandırma, yapılandırmayı kullanarak aynı uç noktayı ayarlar.</span><span class="sxs-lookup"><span data-stu-id="1abae-139">The following configuration sets up the same endpoint using configuration.</span></span>  
  
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
  
## <a name="trusted-subsystem"></a><span data-ttu-id="1abae-140">Güvenilir Alt Sistem</span><span class="sxs-lookup"><span data-stu-id="1abae-140">Trusted Subsystem</span></span>  
  
### <a name="code"></a><span data-ttu-id="1abae-141">Kod</span><span class="sxs-lookup"><span data-stu-id="1abae-141">Code</span></span>  
 <span data-ttu-id="1abae-142">Aşağıdaki kod, HTTP protokolü üzerinde ileti güvenliği ve kimlik doğrulaması için bir Kullanıcı adı ve parola kullanan güvenilir alt sistem için bir hizmet uç noktası oluşturmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="1abae-142">The following code shows how to create a service endpoint for the trusted subsystem that uses message security over the HTTP protocol and a user name and password for authentication.</span></span>  
  
 [!code-csharp[TrustedSubSystems#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/trustedsubsystems/cs/source.cs#1)]
 [!code-vb[TrustedSubSystems#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/trustedsubsystems/vb/source.vb#1)]  
  
 <span data-ttu-id="1abae-143">Aşağıdaki kod, TCP Aktarım Protokolü üzerinden aktarım güvenliği kullanarak bir arka uç hizmetiyle iletişim kuran güvenilir bir alt sistemdeki hizmeti gösterir.</span><span class="sxs-lookup"><span data-stu-id="1abae-143">The following code shows a service in a trusted subsystem that communicates with a back-end service using transport security over the TCP transport protocol.</span></span>  
  
 [!code-csharp[TrustedSubSystems#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/trustedsubsystems/cs/source.cs#2)]
 [!code-vb[TrustedSubSystems#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/trustedsubsystems/vb/source.vb#2)]  
  
### <a name="configuration"></a><span data-ttu-id="1abae-144">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="1abae-144">Configuration</span></span>  
 <span data-ttu-id="1abae-145">Aşağıdaki yapılandırma, yapılandırmayı kullanarak aynı uç noktayı ayarlar.</span><span class="sxs-lookup"><span data-stu-id="1abae-145">The following configuration sets up the same endpoint using configuration.</span></span> <span data-ttu-id="1abae-146">İki bağlamayı aklınızda bulunan bir tane, güvenilen alt sistemde barındırılan hizmetin güvenliğini sağlar ve diğer güvenilen alt sistem ile arka uç hizmeti arasında iletişim kurar.</span><span class="sxs-lookup"><span data-stu-id="1abae-146">Note the two bindings: One secures the service hosted in the trusted subsystem and the other communicates between the trusted subsystem and the back-end service.</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="1abae-147">İstemci</span><span class="sxs-lookup"><span data-stu-id="1abae-147">Client</span></span>  
  
### <a name="code"></a><span data-ttu-id="1abae-148">Kod</span><span class="sxs-lookup"><span data-stu-id="1abae-148">Code</span></span>  
 <span data-ttu-id="1abae-149">Aşağıdaki kod, HTTP protokolü üzerinden ileti güvenliği ve kimlik doğrulaması için bir Kullanıcı adı ve parola kullanarak güvenilir alt sistemle iletişim kuran istemcinin nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="1abae-149">The following code shows how to create the client that communicates with the trusted subsystem by using message security over the HTTP protocol and a user name and password for authentication.</span></span>  
  
 [!code-csharp[TrustedSubSystemsClient#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/trustedsubsystemsclient/cs/source.cs#1)]
 [!code-vb[TrustedSubSystemsClient#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/trustedsubsystemsclient/vb/source.vb#1)]  
  
### <a name="configuration"></a><span data-ttu-id="1abae-150">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="1abae-150">Configuration</span></span>  
 <span data-ttu-id="1abae-151">Aşağıdaki kod, istemcisini HTTP protokolü ve kimlik doğrulaması için bir Kullanıcı adı ve parola üzerinden ileti güvenliği kullanacak şekilde yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="1abae-151">The following code configures the client to use message security over the HTTP protocol and a user name and password for authentication.</span></span> <span data-ttu-id="1abae-152">Kullanıcı adı ve parola yalnızca kod kullanılarak belirtilebilir (yapılandırılabilir değildir).</span><span class="sxs-lookup"><span data-stu-id="1abae-152">The user name and password can only be specified using code (it is not configurable).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1abae-153">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1abae-153">See also</span></span>

- [<span data-ttu-id="1abae-154">Güvenliğe genel bakış</span><span class="sxs-lookup"><span data-stu-id="1abae-154">Security Overview</span></span>](security-overview.md)
- <span data-ttu-id="1abae-155">[Windows Server App Fabric için güvenlik modeli](/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="1abae-155">[Security Model for Windows Server App Fabric](/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
