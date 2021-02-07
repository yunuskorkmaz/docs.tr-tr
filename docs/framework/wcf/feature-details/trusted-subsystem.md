---
description: 'Daha fazla bilgi edinin: güvenilir alt sistem'
title: Güvenilir Alt Sistem
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1f5ce46b-e259-4bc9-a0b9-89d06fc9341c
ms.openlocfilehash: 41c2943c7794206dba06ef8b5bbee762931ce0c0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99733053"
---
# <a name="trusted-subsystem"></a><span data-ttu-id="47fa4-103">Güvenilir Alt Sistem</span><span class="sxs-lookup"><span data-stu-id="47fa4-103">Trusted Subsystem</span></span>

<span data-ttu-id="47fa4-104">İstemci bir ağ üzerinde dağıtılan bir veya daha fazla Web hizmetine erişir.</span><span class="sxs-lookup"><span data-stu-id="47fa4-104">A client accesses one or more Web services that are distributed across a network.</span></span> <span data-ttu-id="47fa4-105">Web Hizmetleri, ek kaynaklara erişimin (veritabanları veya diğer Web Hizmetleri gibi) Web hizmetinin iş mantığıyla kapsüllenmesi için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="47fa4-105">The Web services are designed so that access to additional resources (such as databases or other Web services) is encapsulated in the business logic of the Web service.</span></span> <span data-ttu-id="47fa4-106">Bu kaynakların yetkisiz erişime karşı korunması gerekir.</span><span class="sxs-lookup"><span data-stu-id="47fa4-106">These resources must be protected against unauthorized access.</span></span> <span data-ttu-id="47fa4-107">Aşağıdaki çizimde, güvenilir bir alt sistem işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="47fa4-107">The following illustration depicts a trusted subsystem process.</span></span>  
  
 <span data-ttu-id="47fa4-108">![Güvenilen alt sistem](media/wcfc-trustedsubsystemc.gif "wcfc_TrustedSubsystemc")</span><span class="sxs-lookup"><span data-stu-id="47fa4-108">![Trusted subsystem](media/wcfc-trustedsubsystemc.gif "wcfc_TrustedSubsystemc")</span></span>  
  
 <span data-ttu-id="47fa4-109">Aşağıdaki adımlar gösterildiği gibi güvenilir alt sistem işlemini anlatmaktadır:</span><span class="sxs-lookup"><span data-stu-id="47fa4-109">The following steps describe the trusted subsystem process as illustrated:</span></span>  
  
1. <span data-ttu-id="47fa4-110">İstemci, kimlik bilgileriyle birlikte güvenilen alt sisteme bir istek gönderir.</span><span class="sxs-lookup"><span data-stu-id="47fa4-110">The client submits a request to the trusted subsystem, along with credentials.</span></span>  
  
2. <span data-ttu-id="47fa4-111">Güvenilen alt sistem, kullanıcının kimliğini doğrular ve yetkilendirir.</span><span class="sxs-lookup"><span data-stu-id="47fa4-111">The trusted subsystem authenticates and authorizes the user.</span></span>  
  
3. <span data-ttu-id="47fa4-112">Güvenilen alt sistem, uzak kaynağa bir istek iletisi gönderir.</span><span class="sxs-lookup"><span data-stu-id="47fa4-112">The trusted subsystem sends a request message to the remote resource.</span></span> <span data-ttu-id="47fa4-113">Bu isteğe, güvenilen alt sistem (veya güvenilir alt sistem işleminin yürütüldüğü hizmet hesabı) için kimlik bilgileri eşlik eder.</span><span class="sxs-lookup"><span data-stu-id="47fa4-113">This request is accompanied by the credentials for the trusted subsystem (or the service account under which the trusted subsystem process is being executed).</span></span>  
  
4. <span data-ttu-id="47fa4-114">Arka uç kaynağı, güvenilen alt sistemi doğrular ve yetkilendirir.</span><span class="sxs-lookup"><span data-stu-id="47fa4-114">The back-end resource authenticates and authorizes the trusted subsystem.</span></span> <span data-ttu-id="47fa4-115">Ardından, isteği işler ve güvenilir alt sisteme yanıt verir.</span><span class="sxs-lookup"><span data-stu-id="47fa4-115">It then processes the request and issues a response to the trusted subsystem.</span></span>  
  
5. <span data-ttu-id="47fa4-116">Güvenilen alt sistem yanıtı işler ve istemciye kendi yanıtını verir.</span><span class="sxs-lookup"><span data-stu-id="47fa4-116">The trusted subsystem processes the response and issues its own response to the client.</span></span>  
  
|<span data-ttu-id="47fa4-117">Özellik</span><span class="sxs-lookup"><span data-stu-id="47fa4-117">Characteristic</span></span>|<span data-ttu-id="47fa4-118">Description</span><span class="sxs-lookup"><span data-stu-id="47fa4-118">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="47fa4-119">Güvenlik modu</span><span class="sxs-lookup"><span data-stu-id="47fa4-119">Security Mode</span></span>|<span data-ttu-id="47fa4-120">İleti</span><span class="sxs-lookup"><span data-stu-id="47fa4-120">Message</span></span>|  
|<span data-ttu-id="47fa4-121">Birlikte çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="47fa4-121">Interoperability</span></span>|<span data-ttu-id="47fa4-122">Yalnızca Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="47fa4-122">Windows Communication Foundation (WCF) only.</span></span>|  
|<span data-ttu-id="47fa4-123">Kimlik doğrulaması (hizmet)</span><span class="sxs-lookup"><span data-stu-id="47fa4-123">Authentication (service)</span></span>|<span data-ttu-id="47fa4-124">Güvenlik belirteci hizmeti, istemcilerin kimliğini doğrular ve yetkilendirir.</span><span class="sxs-lookup"><span data-stu-id="47fa4-124">Security token service authenticates and authorizes clients.</span></span>|  
|<span data-ttu-id="47fa4-125">Kimlik doğrulaması (istemci)</span><span class="sxs-lookup"><span data-stu-id="47fa4-125">Authentication (client)</span></span>|<span data-ttu-id="47fa4-126">Güvenilen alt sistem istemcinin kimliğini doğrular ve kaynak, güvenilen alt sistem hizmetinin kimliğini doğrular.</span><span class="sxs-lookup"><span data-stu-id="47fa4-126">The trusted subsystem authenticates the client and the resource authenticates the trusted subsystem service.</span></span>|  
|<span data-ttu-id="47fa4-127">Bütünlük</span><span class="sxs-lookup"><span data-stu-id="47fa4-127">Integrity</span></span>|<span data-ttu-id="47fa4-128">Yes</span><span class="sxs-lookup"><span data-stu-id="47fa4-128">Yes</span></span>|  
|<span data-ttu-id="47fa4-129">Gizlilik</span><span class="sxs-lookup"><span data-stu-id="47fa4-129">Confidentiality</span></span>|<span data-ttu-id="47fa4-130">Yes</span><span class="sxs-lookup"><span data-stu-id="47fa4-130">Yes</span></span>|  
|<span data-ttu-id="47fa4-131">Aktarım</span><span class="sxs-lookup"><span data-stu-id="47fa4-131">Transport</span></span>|<span data-ttu-id="47fa4-132">İstemci ile güvenilen alt sistem hizmeti arasında HTTP.</span><span class="sxs-lookup"><span data-stu-id="47fa4-132">HTTP between client and the trusted subsystem service.</span></span><br /><br /> <span data-ttu-id="47fa4-133">NET. Güvenilen alt sistem hizmeti ve kaynak (arka uç hizmeti) arasında TCP.</span><span class="sxs-lookup"><span data-stu-id="47fa4-133">NET.TCP between trusted subsystem service and the resource (back-end service).</span></span>|  
|<span data-ttu-id="47fa4-134">Bağlama</span><span class="sxs-lookup"><span data-stu-id="47fa4-134">Binding</span></span>|<span data-ttu-id="47fa4-135"><xref:System.ServiceModel.WSHttpBinding> ' <xref:System.ServiceModel.NetTcpBinding>[\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="47fa4-135"><xref:System.ServiceModel.WSHttpBinding> and <xref:System.ServiceModel.NetTcpBinding>[\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md)</span></span>|  
  
## <a name="resource-back-end-service"></a><span data-ttu-id="47fa4-136">Kaynak (arka uç hizmeti)</span><span class="sxs-lookup"><span data-stu-id="47fa4-136">Resource (Back-End Service)</span></span>  
  
### <a name="code"></a><span data-ttu-id="47fa4-137">Kod</span><span class="sxs-lookup"><span data-stu-id="47fa4-137">Code</span></span>  

 <span data-ttu-id="47fa4-138">Aşağıdaki kod, TCP Aktarım Protokolü üzerinden aktarım güvenliği kullanan kaynak için bir hizmet uç noktası oluşturmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="47fa4-138">The following code shows how to create a service endpoint for the resource, which uses transport security over the TCP transport protocol.</span></span>  
  
 [!code-csharp[TrustedSubSystemsResource#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/trustedsubsystemsresource/cs/source.cs#1)]
 [!code-vb[TrustedSubSystemsResource#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/trustedsubsystemsresource/vb/source.vb#1)]  
  
### <a name="configuration"></a><span data-ttu-id="47fa4-139">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="47fa4-139">Configuration</span></span>  

 <span data-ttu-id="47fa4-140">Aşağıdaki yapılandırma, yapılandırmayı kullanarak aynı uç noktayı ayarlar.</span><span class="sxs-lookup"><span data-stu-id="47fa4-140">The following configuration sets up the same endpoint using configuration.</span></span>  
  
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
  
## <a name="trusted-subsystem"></a><span data-ttu-id="47fa4-141">Güvenilir Alt Sistem</span><span class="sxs-lookup"><span data-stu-id="47fa4-141">Trusted Subsystem</span></span>  
  
### <a name="code"></a><span data-ttu-id="47fa4-142">Kod</span><span class="sxs-lookup"><span data-stu-id="47fa4-142">Code</span></span>  

 <span data-ttu-id="47fa4-143">Aşağıdaki kod, HTTP protokolü üzerinde ileti güvenliği ve kimlik doğrulaması için bir Kullanıcı adı ve parola kullanan güvenilir alt sistem için bir hizmet uç noktası oluşturmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="47fa4-143">The following code shows how to create a service endpoint for the trusted subsystem that uses message security over the HTTP protocol and a user name and password for authentication.</span></span>  
  
 [!code-csharp[TrustedSubSystems#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/trustedsubsystems/cs/source.cs#1)]
 [!code-vb[TrustedSubSystems#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/trustedsubsystems/vb/source.vb#1)]  
  
 <span data-ttu-id="47fa4-144">Aşağıdaki kod, TCP Aktarım Protokolü üzerinden aktarım güvenliği kullanarak bir arka uç hizmetiyle iletişim kuran güvenilir bir alt sistemdeki hizmeti gösterir.</span><span class="sxs-lookup"><span data-stu-id="47fa4-144">The following code shows a service in a trusted subsystem that communicates with a back-end service using transport security over the TCP transport protocol.</span></span>  
  
 [!code-csharp[TrustedSubSystems#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/trustedsubsystems/cs/source.cs#2)]
 [!code-vb[TrustedSubSystems#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/trustedsubsystems/vb/source.vb#2)]  
  
### <a name="configuration"></a><span data-ttu-id="47fa4-145">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="47fa4-145">Configuration</span></span>  

 <span data-ttu-id="47fa4-146">Aşağıdaki yapılandırma, yapılandırmayı kullanarak aynı uç noktayı ayarlar.</span><span class="sxs-lookup"><span data-stu-id="47fa4-146">The following configuration sets up the same endpoint using configuration.</span></span> <span data-ttu-id="47fa4-147">İki bağlamayı aklınızda bulunan bir tane, güvenilen alt sistemde barındırılan hizmetin güvenliğini sağlar ve diğer güvenilen alt sistem ile arka uç hizmeti arasında iletişim kurar.</span><span class="sxs-lookup"><span data-stu-id="47fa4-147">Note the two bindings: One secures the service hosted in the trusted subsystem and the other communicates between the trusted subsystem and the back-end service.</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="47fa4-148">İstemci</span><span class="sxs-lookup"><span data-stu-id="47fa4-148">Client</span></span>  
  
### <a name="code"></a><span data-ttu-id="47fa4-149">Kod</span><span class="sxs-lookup"><span data-stu-id="47fa4-149">Code</span></span>  

 <span data-ttu-id="47fa4-150">Aşağıdaki kod, HTTP protokolü üzerinden ileti güvenliği ve kimlik doğrulaması için bir Kullanıcı adı ve parola kullanarak güvenilir alt sistemle iletişim kuran istemcinin nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="47fa4-150">The following code shows how to create the client that communicates with the trusted subsystem by using message security over the HTTP protocol and a user name and password for authentication.</span></span>  
  
 [!code-csharp[TrustedSubSystemsClient#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/trustedsubsystemsclient/cs/source.cs#1)]
 [!code-vb[TrustedSubSystemsClient#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/trustedsubsystemsclient/vb/source.vb#1)]  
  
### <a name="configuration"></a><span data-ttu-id="47fa4-151">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="47fa4-151">Configuration</span></span>  

 <span data-ttu-id="47fa4-152">Aşağıdaki kod, istemcisini HTTP protokolü ve kimlik doğrulaması için bir Kullanıcı adı ve parola üzerinden ileti güvenliği kullanacak şekilde yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="47fa4-152">The following code configures the client to use message security over the HTTP protocol and a user name and password for authentication.</span></span> <span data-ttu-id="47fa4-153">Kullanıcı adı ve parola yalnızca kod kullanılarak belirtilebilir (yapılandırılabilir değildir).</span><span class="sxs-lookup"><span data-stu-id="47fa4-153">The user name and password can only be specified using code (it is not configurable).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="47fa4-154">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="47fa4-154">See also</span></span>

- [<span data-ttu-id="47fa4-155">Güvenliğe genel bakış</span><span class="sxs-lookup"><span data-stu-id="47fa4-155">Security Overview</span></span>](security-overview.md)
- <span data-ttu-id="47fa4-156">[Windows Server App Fabric için güvenlik modeli](/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="47fa4-156">[Security Model for Windows Server App Fabric](/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
