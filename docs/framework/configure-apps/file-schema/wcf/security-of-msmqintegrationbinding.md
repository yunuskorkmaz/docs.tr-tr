---
title: '&lt;msmqIntegrationBinding&gt; &lt;güvenliği&gt;'
ms.date: 03/30/2017
ms.assetid: ae5c68a8-14a2-4c6e-b9e0-3e94e3e9135e
author: BrucePerlerMS
ms.openlocfilehash: 3f0810a705b5f46ee68a891f9b4ced42efdcb757
ms.sourcegitcommit: 700b9003ea6bdd83a53458bbc436c9b5778344f1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/03/2018
ms.locfileid: "48262480"
---
# <a name="ltsecuritygt-of-ltmsmqintegrationbindinggt"></a><span data-ttu-id="99374-102">&lt;msmqIntegrationBinding&gt; &lt;güvenliği&gt;</span><span class="sxs-lookup"><span data-stu-id="99374-102">&lt;security&gt; of &lt;msmqIntegrationBinding&gt;</span></span>
<span data-ttu-id="99374-103">Message Queuing (MSMQ) tümleştirme kanal taşıma güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="99374-103">Defines the transport security settings for the Message Queuing (MSMQ) integration channel.</span></span>  
  
 <span data-ttu-id="99374-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="99374-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="99374-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="99374-105">\<bindings></span></span>  
<span data-ttu-id="99374-106">msmqIntegrationBinding</span><span class="sxs-lookup"><span data-stu-id="99374-106">msmqIntegrationBinding</span></span>  
<span data-ttu-id="99374-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="99374-107">\<binding></span></span>  
<span data-ttu-id="99374-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="99374-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99374-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="99374-109">Syntax</span></span>  
  
```xml  
<msmqIntegrationBinding>  
   <binding>   
       <security mode="None/Transport">  
         <transport msmqAuthenticationMode="None/Windows/Certificate"  
            msmqEncryptionAlgorithm="RC4Stream/AES"  
            msmqProtectionLevel="None/Sign/EncryptAndSign"  
            msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />  
          <message  algorithmSuite="Aes128/Aes192/Aes256/Rsa15Aes128/ Rsa15Aes256/TripleDes"  
                        clientCredentialType="None/Windows/UserName/Certificate/CardSpace"  
            defaultProtectionLevel="None/Sign/EncryptAndSign" />  
       </security>  
   </binding>  
</msmqIntegrationBinding>   
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="99374-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="99374-110">Attributes and Elements</span></span>  
 <span data-ttu-id="99374-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="99374-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="99374-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="99374-112">Attributes</span></span>  
  
|<span data-ttu-id="99374-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="99374-113">Attribute</span></span>|<span data-ttu-id="99374-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="99374-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="99374-115">mod</span><span class="sxs-lookup"><span data-stu-id="99374-115">mode</span></span>|<span data-ttu-id="99374-116">Güvenlik türü bu denetimleri bütünlüğü, gizlilik ve kimlik doğrulaması ile Message Queuing tümleştirme kanalı belirtir.</span><span class="sxs-lookup"><span data-stu-id="99374-116">Specifies the type of security that controls integrity, confidentiality and authentication with the Message Queuing integration channel.</span></span> <span data-ttu-id="99374-117">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="99374-117">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="99374-118">-Yok: Bu güvenlik devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="99374-118">-   None: This disables security.</span></span><br /><span data-ttu-id="99374-119">-Taşıma: Koruma ve kimlik doğrulaması taşıma tarafından sunulur.</span><span class="sxs-lookup"><span data-stu-id="99374-119">-   Transport: Protection and authentication are offered by the transport.</span></span> <span data-ttu-id="99374-120">Bu ileti güvenliği iki sıra yöneticileri arasında geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="99374-120">This applies to the message security between the two queue managers.</span></span> <span data-ttu-id="99374-121">Kuyruk Yöneticisi ve uygulama arasında sunulan güvenlik yoktur.</span><span class="sxs-lookup"><span data-stu-id="99374-121">There is no security offered between the application and queue manager.</span></span> <span data-ttu-id="99374-122">Msmq uygulamalara güvenlik modu bu tür işlevsel olarak eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="99374-122">Existing Msmq applications are functionally equivalent with this type of security mode.</span></span><br /><br /> <span data-ttu-id="99374-123">Varsayılan değer `Transport` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="99374-123">The default value is `Transport`.</span></span> <span data-ttu-id="99374-124">Bu öznitelik türünde <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="99374-124">This attribute is of type <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="99374-125">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="99374-125">Child Elements</span></span>  
  
|<span data-ttu-id="99374-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="99374-126">Element</span></span>|<span data-ttu-id="99374-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="99374-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="99374-128">\<taşıma ></span><span class="sxs-lookup"><span data-stu-id="99374-128">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-msmqintegrationbinding.md)|<span data-ttu-id="99374-129">Message Queuing tümleştirme taşıma güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="99374-129">Defines the security settings for the Message Queuing integration transport.</span></span> <span data-ttu-id="99374-130">Bu öğe türünde <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="99374-130">This element is of type <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="99374-131">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="99374-131">Parent Elements</span></span>  
  
|<span data-ttu-id="99374-132">Öğe</span><span class="sxs-lookup"><span data-stu-id="99374-132">Element</span></span>|<span data-ttu-id="99374-133">Açıklama</span><span class="sxs-lookup"><span data-stu-id="99374-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="99374-134">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="99374-134">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="99374-135">Bağlama öğesi [ \<MsmqIntegrationBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/msmqintegrationbinding.md).</span><span class="sxs-lookup"><span data-stu-id="99374-135">The binding element of the [\<msmqIntegrationBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/msmqintegrationbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="99374-136">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="99374-136">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.MsmqIntegrationSecurityElement>  
 <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.MsmqIntegrationBindingElement.Security%2A>  
 <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity>  
 [<span data-ttu-id="99374-137">WCF'de Kuyruklar</span><span class="sxs-lookup"><span data-stu-id="99374-137">Queues in WCF</span></span>](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)  
 [<span data-ttu-id="99374-138">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="99374-138">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="99374-139">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="99374-139">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="99374-140">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="99374-140">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="99374-141">Windows Communication Foundation Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma</span><span class="sxs-lookup"><span data-stu-id="99374-141">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="99374-142">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="99374-142">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)  
 [<span data-ttu-id="99374-143">\<MsmqIntegrationBinding ></span><span class="sxs-lookup"><span data-stu-id="99374-143">\<msmqIntegrationBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/msmqintegrationbinding.md)
