---
title: Windows Kimlik Doğrulama ile Taşıma Güvenliği
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 96dd26e2-46e7-4de0-9a29-4fcb05bf187b
author: BrucePerlerMS
ms.openlocfilehash: babafe369ee9f5c9261e3b5c8bc749d3d1d39ec4
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48778522"
---
# <a name="transport-security-with-windows-authentication"></a><span data-ttu-id="7e196-102">Windows Kimlik Doğrulama ile Taşıma Güvenliği</span><span class="sxs-lookup"><span data-stu-id="7e196-102">Transport Security with Windows Authentication</span></span>
<span data-ttu-id="7e196-103">Aşağıdaki senaryoda, bir Windows Communication Foundation (WCF) istemci ve hizmet Windows güvenlik güvenli gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="7e196-103">The following scenario shows a Windows Communication Foundation (WCF) client and service secured by Windows security.</span></span> <span data-ttu-id="7e196-104">Programlama hakkında daha fazla bilgi için bkz. [nasıl yapılır: Windows kimlik bilgileri ile bir hizmeti güvenli hale getirme](../../../../docs/framework/wcf/how-to-secure-a-service-with-windows-credentials.md).</span><span class="sxs-lookup"><span data-stu-id="7e196-104">For more information about programming, see [How to: Secure a Service with Windows Credentials](../../../../docs/framework/wcf/how-to-secure-a-service-with-windows-credentials.md).</span></span>  
  
 <span data-ttu-id="7e196-105">Bir intranet Web hizmeti, İnsan Kaynakları bilgileri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="7e196-105">An intranet Web service displays human resources information.</span></span> <span data-ttu-id="7e196-106">İstemci, bir Windows formu uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="7e196-106">The client is a Windows Form application.</span></span> <span data-ttu-id="7e196-107">Uygulama etki alanında etki alanını güvenli hale getirme Kerberos denetleyiciyle dağıtılır.</span><span class="sxs-lookup"><span data-stu-id="7e196-107">The application is deployed in a domain with a Kerberos controller securing the domain.</span></span>  
  
 <span data-ttu-id="7e196-108">![Aktarım güvenliği Windows kimlik doğrulaması ile](../../../../docs/framework/wcf/feature-details/media/securedbywindows.gif "SecuredByWindows")</span><span class="sxs-lookup"><span data-stu-id="7e196-108">![Transport security with Windows authentication](../../../../docs/framework/wcf/feature-details/media/securedbywindows.gif "SecuredByWindows")</span></span>  
  
|<span data-ttu-id="7e196-109">Özelliği</span><span class="sxs-lookup"><span data-stu-id="7e196-109">Characteristic</span></span>|<span data-ttu-id="7e196-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7e196-110">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="7e196-111">Güvenlik modu</span><span class="sxs-lookup"><span data-stu-id="7e196-111">Security Mode</span></span>|<span data-ttu-id="7e196-112">Taşıma</span><span class="sxs-lookup"><span data-stu-id="7e196-112">Transport</span></span>|  
|<span data-ttu-id="7e196-113">Birlikte Çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="7e196-113">Interoperability</span></span>|<span data-ttu-id="7e196-114">Yalnızca WCF</span><span class="sxs-lookup"><span data-stu-id="7e196-114">WCF only</span></span>|  
|<span data-ttu-id="7e196-115">Kimlik doğrulaması (sunucu)</span><span class="sxs-lookup"><span data-stu-id="7e196-115">Authentication (Server)</span></span><br /><br /> <span data-ttu-id="7e196-116">Kimlik doğrulaması (istemci)</span><span class="sxs-lookup"><span data-stu-id="7e196-116">Authentication (Client)</span></span>|<span data-ttu-id="7e196-117">Evet (Windows tümleşik kimlik doğrulaması kullanarak)</span><span class="sxs-lookup"><span data-stu-id="7e196-117">Yes (using Windows integrated authentication)</span></span><br /><br /> <span data-ttu-id="7e196-118">Evet (Windows tümleşik kimlik doğrulaması kullanarak)</span><span class="sxs-lookup"><span data-stu-id="7e196-118">Yes (using Windows integrated authentication)</span></span>|  
|<span data-ttu-id="7e196-119">Bütünlüğü</span><span class="sxs-lookup"><span data-stu-id="7e196-119">Integrity</span></span>|<span data-ttu-id="7e196-120">Evet</span><span class="sxs-lookup"><span data-stu-id="7e196-120">Yes</span></span>|  
|<span data-ttu-id="7e196-121">Gizliliği</span><span class="sxs-lookup"><span data-stu-id="7e196-121">Confidentiality</span></span>|<span data-ttu-id="7e196-122">Evet</span><span class="sxs-lookup"><span data-stu-id="7e196-122">Yes</span></span>|  
|<span data-ttu-id="7e196-123">Taşıma</span><span class="sxs-lookup"><span data-stu-id="7e196-123">Transport</span></span>|<span data-ttu-id="7e196-124">NET. TCP</span><span class="sxs-lookup"><span data-stu-id="7e196-124">NET.TCP</span></span>|  
|<span data-ttu-id="7e196-125">Bağlama</span><span class="sxs-lookup"><span data-stu-id="7e196-125">Binding</span></span>|<xref:System.ServiceModel.NetTcpBinding>|  
  
## <a name="service"></a><span data-ttu-id="7e196-126">Hizmet</span><span class="sxs-lookup"><span data-stu-id="7e196-126">Service</span></span>  
 <span data-ttu-id="7e196-127">Aşağıdaki kod ve yapılandırma, bağımsız olarak çalışmaya yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="7e196-127">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="7e196-128">Aşağıdakilerden birini yapın:</span><span class="sxs-lookup"><span data-stu-id="7e196-128">Do one of the following:</span></span>  
  
-   <span data-ttu-id="7e196-129">Kod ile yapılandırma kullanarak tek başına bir hizmet oluşturun.</span><span class="sxs-lookup"><span data-stu-id="7e196-129">Create a stand-alone service using the code with no configuration.</span></span>  
  
-   <span data-ttu-id="7e196-130">Sağlanan Yapılandırması'nı kullanarak bir hizmet oluşturma, ancak tüm uç noktalar tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="7e196-130">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="7e196-131">Kod</span><span class="sxs-lookup"><span data-stu-id="7e196-131">Code</span></span>  
 <span data-ttu-id="7e196-132">Aşağıdaki kod, bir Windows Güvenlik kullanan bir hizmet uç noktası oluşturma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="7e196-132">The following code shows how to create a service endpoint that uses a Windows security.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#3)]
 [!code-vb[C_SecurityScenarios#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#3)]  
  
### <a name="configuration"></a><span data-ttu-id="7e196-133">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="7e196-133">Configuration</span></span>  
 <span data-ttu-id="7e196-134">Hizmet uç noktayı kurmak için kod yerine aşağıdaki yapılandırma kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="7e196-134">The following configuration can be used instead of the code to set up the service endpoint:</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="7e196-135">İstemci</span><span class="sxs-lookup"><span data-stu-id="7e196-135">Client</span></span>  
 <span data-ttu-id="7e196-136">Aşağıdaki kod ve yapılandırma, bağımsız olarak çalışmaya yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="7e196-136">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="7e196-137">Aşağıdakilerden birini yapın:</span><span class="sxs-lookup"><span data-stu-id="7e196-137">Do one of the following:</span></span>  
  
-   <span data-ttu-id="7e196-138">Bir tek başına istemci kodu (ve istemci kodu) kullanarak oluşturun.</span><span class="sxs-lookup"><span data-stu-id="7e196-138">Create a stand-alone client using the code (and client code).</span></span>  
  
-   <span data-ttu-id="7e196-139">Herhangi bir uç nokta adresi tanımlamıyor bir istemci oluşturun.</span><span class="sxs-lookup"><span data-stu-id="7e196-139">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="7e196-140">Bunun yerine, yapılandırma adı bağımsız değişkeni olarak alan İstemci Oluşturucu kullanın.</span><span class="sxs-lookup"><span data-stu-id="7e196-140">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="7e196-141">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="7e196-141">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="7e196-142">Kod</span><span class="sxs-lookup"><span data-stu-id="7e196-142">Code</span></span>  
 <span data-ttu-id="7e196-143">Aşağıdaki kod, istemci oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7e196-143">The following code creates the client.</span></span> <span data-ttu-id="7e196-144">Aktarım modu güvenliği TCP taşımasıyla ayarlamak için Windows istemci kimlik bilgileri türünü kullanmak için yapılandırılmış bir bağlama.</span><span class="sxs-lookup"><span data-stu-id="7e196-144">The binding is configured to use the Transport mode security, with the TCP transport, with the client credential type set to Windows.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#4)]
 [!code-vb[C_SecurityScenarios#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#4)]  
  
### <a name="configuration"></a><span data-ttu-id="7e196-145">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="7e196-145">Configuration</span></span>  
 <span data-ttu-id="7e196-146">Aşağıdaki yapılandırmayı kod yerine istemci oluşturmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7e196-146">The following configuration can be used instead of the code to create the client.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7e196-147">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7e196-147">See Also</span></span>  
 [<span data-ttu-id="7e196-148">Güvenliğe Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="7e196-148">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="7e196-149">Nasıl yapılır: Windows Kimlik Bilgileri ile Bir Hizmeti Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="7e196-149">How to: Secure a Service with Windows Credentials</span></span>](../../../../docs/framework/wcf/how-to-secure-a-service-with-windows-credentials.md)  
 [<span data-ttu-id="7e196-150">Windows Server AppFabric için güvenlik modeli</span><span class="sxs-lookup"><span data-stu-id="7e196-150">Security Model for Windows Server App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
