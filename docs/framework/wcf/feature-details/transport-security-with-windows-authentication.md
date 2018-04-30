---
title: Windows Kimlik Doğrulama ile Taşıma Güvenliği
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 96dd26e2-46e7-4de0-9a29-4fcb05bf187b
caps.latest.revision: 17
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload:
- dotnet
ms.openlocfilehash: 5effb18435241b00c3036fd23e15ef5ce485b646
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/30/2018
---
# <a name="transport-security-with-windows-authentication"></a><span data-ttu-id="08ea4-102">Windows Kimlik Doğrulama ile Taşıma Güvenliği</span><span class="sxs-lookup"><span data-stu-id="08ea4-102">Transport Security with Windows Authentication</span></span>
<span data-ttu-id="08ea4-103">Aşağıdaki senaryoda gösterildiği bir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Windows security tarafından korunan hizmet ve istemci.</span><span class="sxs-lookup"><span data-stu-id="08ea4-103">The following scenario shows a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] client and service secured by Windows security.</span></span> <span data-ttu-id="08ea4-104">Programlama hakkında daha fazla bilgi için bkz: [nasıl yapılır: Windows kimlik bilgileri olan bir hizmeti güvenli](../../../../docs/framework/wcf/how-to-secure-a-service-with-windows-credentials.md).</span><span class="sxs-lookup"><span data-stu-id="08ea4-104">For more information about programming, see [How to: Secure a Service with Windows Credentials](../../../../docs/framework/wcf/how-to-secure-a-service-with-windows-credentials.md).</span></span>  
  
 <span data-ttu-id="08ea4-105">Bir intranet Web hizmeti, İnsan Kaynakları bilgilerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="08ea4-105">An intranet Web service displays human resources information.</span></span> <span data-ttu-id="08ea4-106">İstemci, bir Windows formu uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="08ea4-106">The client is a Windows Form application.</span></span> <span data-ttu-id="08ea4-107">Uygulama etki alanında etki alanı güvenliğini sağlama Kerberos denetleyicisiyle dağıtılır.</span><span class="sxs-lookup"><span data-stu-id="08ea4-107">The application is deployed in a domain with a Kerberos controller securing the domain.</span></span>  
  
 <span data-ttu-id="08ea4-108">![Taşıma güvenliği Windows kimlik doğrulaması ile](../../../../docs/framework/wcf/feature-details/media/securedbywindows.gif "SecuredByWindows")</span><span class="sxs-lookup"><span data-stu-id="08ea4-108">![Transport security with Windows authentication](../../../../docs/framework/wcf/feature-details/media/securedbywindows.gif "SecuredByWindows")</span></span>  
  
|<span data-ttu-id="08ea4-109">Özelliği</span><span class="sxs-lookup"><span data-stu-id="08ea4-109">Characteristic</span></span>|<span data-ttu-id="08ea4-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="08ea4-110">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="08ea4-111">Güvenlik modu</span><span class="sxs-lookup"><span data-stu-id="08ea4-111">Security Mode</span></span>|<span data-ttu-id="08ea4-112">Taşıma</span><span class="sxs-lookup"><span data-stu-id="08ea4-112">Transport</span></span>|  
|<span data-ttu-id="08ea4-113">Birlikte Çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="08ea4-113">Interoperability</span></span>|[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="08ea4-114"> yalnızca</span><span class="sxs-lookup"><span data-stu-id="08ea4-114"> only</span></span>|  
|<span data-ttu-id="08ea4-115">Kimlik doğrulaması (sunucu)</span><span class="sxs-lookup"><span data-stu-id="08ea4-115">Authentication (Server)</span></span><br /><br /> <span data-ttu-id="08ea4-116">Kimlik doğrulaması (istemci)</span><span class="sxs-lookup"><span data-stu-id="08ea4-116">Authentication (Client)</span></span>|<span data-ttu-id="08ea4-117">Evet (Windows tümleşik kimlik doğrulaması kullanarak)</span><span class="sxs-lookup"><span data-stu-id="08ea4-117">Yes (using Windows integrated authentication)</span></span><br /><br /> <span data-ttu-id="08ea4-118">Evet (Windows tümleşik kimlik doğrulaması kullanarak)</span><span class="sxs-lookup"><span data-stu-id="08ea4-118">Yes (using Windows integrated authentication)</span></span>|  
|<span data-ttu-id="08ea4-119">Bütünlük</span><span class="sxs-lookup"><span data-stu-id="08ea4-119">Integrity</span></span>|<span data-ttu-id="08ea4-120">Evet</span><span class="sxs-lookup"><span data-stu-id="08ea4-120">Yes</span></span>|  
|<span data-ttu-id="08ea4-121">Gizliliği</span><span class="sxs-lookup"><span data-stu-id="08ea4-121">Confidentiality</span></span>|<span data-ttu-id="08ea4-122">Evet</span><span class="sxs-lookup"><span data-stu-id="08ea4-122">Yes</span></span>|  
|<span data-ttu-id="08ea4-123">Taşıma</span><span class="sxs-lookup"><span data-stu-id="08ea4-123">Transport</span></span>|<span data-ttu-id="08ea4-124">NET. TCP</span><span class="sxs-lookup"><span data-stu-id="08ea4-124">NET.TCP</span></span>|  
|<span data-ttu-id="08ea4-125">Bağlama</span><span class="sxs-lookup"><span data-stu-id="08ea4-125">Binding</span></span>|<xref:System.ServiceModel.NetTcpBinding>|  
  
## <a name="service"></a><span data-ttu-id="08ea4-126">Hizmet</span><span class="sxs-lookup"><span data-stu-id="08ea4-126">Service</span></span>  
 <span data-ttu-id="08ea4-127">Aşağıdaki kod ve yapılandırma bağımsız olarak çalışmaya yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="08ea4-127">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="08ea4-128">Aşağıdakilerden birini yapın:</span><span class="sxs-lookup"><span data-stu-id="08ea4-128">Do one of the following:</span></span>  
  
-   <span data-ttu-id="08ea4-129">Kod yapılandırma gerektirmeden kullanarak tek başına bir hizmet oluşturun.</span><span class="sxs-lookup"><span data-stu-id="08ea4-129">Create a stand-alone service using the code with no configuration.</span></span>  
  
-   <span data-ttu-id="08ea4-130">Sağlanan yapılandırma kullanarak bir hizmet oluşturun, ancak uç tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="08ea4-130">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="08ea4-131">Kod</span><span class="sxs-lookup"><span data-stu-id="08ea4-131">Code</span></span>  
 <span data-ttu-id="08ea4-132">Aşağıdaki kod, bir Windows Güvenlik kullanan bir hizmet uç noktası oluşturma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="08ea4-132">The following code shows how to create a service endpoint that uses a Windows security.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#3)]
 [!code-vb[C_SecurityScenarios#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#3)]  
  
### <a name="configuration"></a><span data-ttu-id="08ea4-133">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="08ea4-133">Configuration</span></span>  
 <span data-ttu-id="08ea4-134">Hizmet uç nokta ayarlamayı kodu yerine aşağıdaki yapılandırma kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="08ea4-134">The following configuration can be used instead of the code to set up the service endpoint:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors />  
    <services>  
      <service behaviorConfiguration="" name="ServiceModel.Calculator">  
        <endpoint address="net.tcp://localhost:8008/Calculator"   
                  binding="netTcpBinding"  
          bindingConfiguration="WindowsClientOverTcp"   
                  name="WindowsClientOverTcp"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <netTcpBinding>  
        <binding name="WindowsClientOverTcp">  
          <security mode="Transport">  
            <transport clientCredentialType="Windows" />  
          </security>  
        </binding>  
      </netTcpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a><span data-ttu-id="08ea4-135">İstemci</span><span class="sxs-lookup"><span data-stu-id="08ea4-135">Client</span></span>  
 <span data-ttu-id="08ea4-136">Aşağıdaki kod ve yapılandırma bağımsız olarak çalışmaya yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="08ea4-136">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="08ea4-137">Aşağıdakilerden birini yapın:</span><span class="sxs-lookup"><span data-stu-id="08ea4-137">Do one of the following:</span></span>  
  
-   <span data-ttu-id="08ea4-138">Kod (ve istemci kodu) kullanan bir tek başına istemci oluşturun.</span><span class="sxs-lookup"><span data-stu-id="08ea4-138">Create a stand-alone client using the code (and client code).</span></span>  
  
-   <span data-ttu-id="08ea4-139">Herhangi bir uç nokta adresi tanımlamıyor bir istemci oluşturun.</span><span class="sxs-lookup"><span data-stu-id="08ea4-139">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="08ea4-140">Bunun yerine, yapılandırma adı bağımsız değişken olarak alan İstemci Oluşturucu kullanın.</span><span class="sxs-lookup"><span data-stu-id="08ea4-140">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="08ea4-141">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="08ea4-141">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="08ea4-142">Kod</span><span class="sxs-lookup"><span data-stu-id="08ea4-142">Code</span></span>  
 <span data-ttu-id="08ea4-143">Aşağıdaki kod istemci oluşturur.</span><span class="sxs-lookup"><span data-stu-id="08ea4-143">The following code creates the client.</span></span> <span data-ttu-id="08ea4-144">Bağlama aktarım modu güvenliği Windows kümesi istemci kimlik bilgisi türü ile TCP taşıma ile kullanmak için yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="08ea4-144">The binding is configured to use the Transport mode security, with the TCP transport, with the client credential type set to Windows.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#4)]
 [!code-vb[C_SecurityScenarios#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#4)]  
  
### <a name="configuration"></a><span data-ttu-id="08ea4-145">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="08ea4-145">Configuration</span></span>  
 <span data-ttu-id="08ea4-146">Aşağıdaki yapılandırma kodu yerine istemci oluşturmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="08ea4-146">The following configuration can be used instead of the code to create the client.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <netTcpBinding>  
        <binding name="NetTcpBinding_ICalculator" >  
          <security mode="Transport">  
            <transport clientCredentialType="Windows" />  
          </security>  
        </binding>  
      </netTcpBinding>  
    </bindings>  
    <client>  
      <endpoint address="net.tcp://localhost:8008/Calculator"   
                binding="netTcpBinding"            
                bindingConfiguration="NetTcpBinding_ICalculator"   
                contract="ICalculator"  
                name="NetTcpBinding_ICalculator">  
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="08ea4-147">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="08ea4-147">See Also</span></span>  
 [<span data-ttu-id="08ea4-148">Güvenliğe Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="08ea4-148">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="08ea4-149">Nasıl yapılır: Windows Kimlik Bilgileri ile Bir Hizmeti Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="08ea4-149">How to: Secure a Service with Windows Credentials</span></span>](../../../../docs/framework/wcf/how-to-secure-a-service-with-windows-credentials.md)  
 [<span data-ttu-id="08ea4-150">Windows Server App Fabric için güvenlik modeli</span><span class="sxs-lookup"><span data-stu-id="08ea4-150">Security Model for Windows Server App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
