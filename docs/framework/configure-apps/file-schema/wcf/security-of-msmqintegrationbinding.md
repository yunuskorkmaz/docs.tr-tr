---
title: "&lt;msmqIntegrationBinding&gt; &lt;güvenliği&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ae5c68a8-14a2-4c6e-b9e0-3e94e3e9135e
caps.latest.revision: "13"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 9bca2fea17ecb0a2acbafed9f6093b7103a1adc5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltsecuritygt-of-ltmsmqintegrationbindinggt"></a><span data-ttu-id="77b96-102">&lt;msmqIntegrationBinding&gt; &lt;güvenliği&gt;</span><span class="sxs-lookup"><span data-stu-id="77b96-102">&lt;security&gt; of &lt;msmqIntegrationBinding&gt;</span></span>
<span data-ttu-id="77b96-103">Message Queuing (MSMQ) tümleştirme kanal taşıma güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="77b96-103">Defines the transport security settings for the Message Queuing (MSMQ) integration channel.</span></span>  
  
 <span data-ttu-id="77b96-104">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="77b96-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="77b96-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="77b96-105">\<bindings></span></span>  
<span data-ttu-id="77b96-106">msmqIntegrationBinding</span><span class="sxs-lookup"><span data-stu-id="77b96-106">msmqIntegrationBinding</span></span>  
<span data-ttu-id="77b96-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="77b96-107">\<binding></span></span>  
<span data-ttu-id="77b96-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="77b96-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77b96-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="77b96-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="77b96-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="77b96-110">Attributes and Elements</span></span>  
 <span data-ttu-id="77b96-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="77b96-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="77b96-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="77b96-112">Attributes</span></span>  
  
|<span data-ttu-id="77b96-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="77b96-113">Attribute</span></span>|<span data-ttu-id="77b96-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="77b96-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="77b96-115">mod</span><span class="sxs-lookup"><span data-stu-id="77b96-115">mode</span></span>|<span data-ttu-id="77b96-116">Güvenlik türü bu denetimleri bütünlüğü, gizlilik ve kimlik doğrulama ile Message Queuing tümleştirme kanalı belirtir.</span><span class="sxs-lookup"><span data-stu-id="77b96-116">Specifies the type of security that controls integrity, confidentiality and authentication with the Message Queuing integration channel.</span></span> <span data-ttu-id="77b96-117">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="77b96-117">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="77b96-118">-Hiçbiri: Bu güvenlik devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="77b96-118">-   None: This disables security.</span></span><br /><span data-ttu-id="77b96-119">-Taşıma: Koruma ve kimlik aktarım tarafından sunulur.</span><span class="sxs-lookup"><span data-stu-id="77b96-119">-   Transport: Protection and authentication are offered by the transport.</span></span> <span data-ttu-id="77b96-120">Bu iki sıra yöneticileri arasında ileti güvenliği için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="77b96-120">This applies to the message security between the two queue managers.</span></span> <span data-ttu-id="77b96-121">Sıra yöneticisini ve uygulama arasında sunulan güvenlik yoktur.</span><span class="sxs-lookup"><span data-stu-id="77b96-121">There is no security offered between the application and queue manager.</span></span> <span data-ttu-id="77b96-122">Varolan Msmq uygulamalarının güvenlik modu bu tür işlevsel olarak eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="77b96-122">Existing Msmq applications are functionally equivalent with this type of security mode.</span></span><br /><br /> <span data-ttu-id="77b96-123">Varsayılan değer `Transport` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="77b96-123">The default value is `Transport`.</span></span> <span data-ttu-id="77b96-124">Bu öznitelik türünde <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="77b96-124">This attribute is of type <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="77b96-125">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="77b96-125">Child Elements</span></span>  
  
|<span data-ttu-id="77b96-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="77b96-126">Element</span></span>|<span data-ttu-id="77b96-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="77b96-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="77b96-128">\<taşıma ></span><span class="sxs-lookup"><span data-stu-id="77b96-128">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-msmqintegrationbinding.md)|<span data-ttu-id="77b96-129">Message Queuing tümleştirme taşıma için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="77b96-129">Defines the security settings for the Message Queuing integration transport.</span></span> <span data-ttu-id="77b96-130">Bu öğe türünde <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="77b96-130">This element is of type <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="77b96-131">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="77b96-131">Parent Elements</span></span>  
  
|<span data-ttu-id="77b96-132">Öğe</span><span class="sxs-lookup"><span data-stu-id="77b96-132">Element</span></span>|<span data-ttu-id="77b96-133">Açıklama</span><span class="sxs-lookup"><span data-stu-id="77b96-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="77b96-134">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="77b96-134">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="77b96-135">Bağlama öğesi [ \<MsmqIntegrationBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/msmqintegrationbinding.md).</span><span class="sxs-lookup"><span data-stu-id="77b96-135">The binding element of the [\<msmqIntegrationBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/msmqintegrationbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="77b96-136">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="77b96-136">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.MsmqIntegrationSecurityElement>  
 <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.MsmqIntegrationBindingElement.Security%2A>  
 <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity>  
 [<span data-ttu-id="77b96-137">Wcf'de kuyruklar</span><span class="sxs-lookup"><span data-stu-id="77b96-137">Queues in WCF</span></span>](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)  
 [<span data-ttu-id="77b96-138">Hizmetler ve istemcileri güvenli hale getirme</span><span class="sxs-lookup"><span data-stu-id="77b96-138">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="77b96-139">Bağlamaları</span><span class="sxs-lookup"><span data-stu-id="77b96-139">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="77b96-140">Sistem tarafından sağlanan bağlamaları yapılandırma</span><span class="sxs-lookup"><span data-stu-id="77b96-140">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="77b96-141">Windows Communication Foundation Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma</span><span class="sxs-lookup"><span data-stu-id="77b96-141">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="77b96-142">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="77b96-142">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)  
 [<span data-ttu-id="77b96-143">\<MsmqIntegrationBinding ></span><span class="sxs-lookup"><span data-stu-id="77b96-143">\<msmqIntegrationBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/msmqintegrationbinding.md)
