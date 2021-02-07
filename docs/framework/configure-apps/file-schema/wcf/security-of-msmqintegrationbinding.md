---
description: 'Hakkında daha fazla bilgi <security> edinin: <msmqIntegrationBinding>'
title: <security> / <msmqIntegrationBinding>
ms.date: 03/30/2017
ms.assetid: ae5c68a8-14a2-4c6e-b9e0-3e94e3e9135e
ms.openlocfilehash: 4ad4cb89599198661d764cfeb985609be027c0eb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99683209"
---
# <a name="security-of-msmqintegrationbinding"></a><span data-ttu-id="1f167-103">\<security> / \<msmqIntegrationBinding></span><span class="sxs-lookup"><span data-stu-id="1f167-103">\<security> of \<msmqIntegrationBinding></span></span>

<span data-ttu-id="1f167-104">Message Queuing (MSMQ) tümleştirme kanalının taşıma güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="1f167-104">Defines the transport security settings for the Message Queuing (MSMQ) integration channel.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<msmqIntegrationBinding>**](msmqintegrationbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="1f167-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="1f167-105">Syntax</span></span>  
  
```xml  
<msmqIntegrationBinding>
  <binding>
    <security mode="None/Transport">
      <transport msmqAuthenticationMode="None/Windows/Certificate"
                 msmqEncryptionAlgorithm="RC4Stream/AES"
                 msmqProtectionLevel="None/Sign/EncryptAndSign"
                 msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />
      <message algorithmSuite="Aes128/Aes192/Aes256/Rsa15Aes128/ Rsa15Aes256/TripleDes"
               clientCredentialType="None/Windows/UserName/Certificate/CardSpace"
               defaultProtectionLevel="None/Sign/EncryptAndSign" />
    </security>
  </binding>
</msmqIntegrationBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1f167-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="1f167-106">Attributes and Elements</span></span>  

 <span data-ttu-id="1f167-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1f167-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1f167-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="1f167-108">Attributes</span></span>  
  
|<span data-ttu-id="1f167-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="1f167-109">Attribute</span></span>|<span data-ttu-id="1f167-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1f167-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1f167-111">mod</span><span class="sxs-lookup"><span data-stu-id="1f167-111">mode</span></span>|<span data-ttu-id="1f167-112">Message Queuing tümleştirme kanalı ile bütünlüğü, gizliliği ve kimlik doğrulamasını denetleyen güvenlik türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="1f167-112">Specifies the type of security that controls integrity, confidentiality and authentication with the Message Queuing integration channel.</span></span> <span data-ttu-id="1f167-113">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="1f167-113">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="1f167-114">-None: Bu, güvenliği devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="1f167-114">-   None: This disables security.</span></span><br /><span data-ttu-id="1f167-115">-Taşıma: koruma ve kimlik doğrulama, taşıma tarafından sunulur.</span><span class="sxs-lookup"><span data-stu-id="1f167-115">-   Transport: Protection and authentication are offered by the transport.</span></span> <span data-ttu-id="1f167-116">Bu, iki kuyruk yöneticisi arasındaki ileti güvenliği için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="1f167-116">This applies to the message security between the two queue managers.</span></span> <span data-ttu-id="1f167-117">Uygulama ve kuyruk Yöneticisi arasında bir güvenlik sunulmaz.</span><span class="sxs-lookup"><span data-stu-id="1f167-117">There is no security offered between the application and queue manager.</span></span> <span data-ttu-id="1f167-118">Mevcut MSMQ uygulamaları, bu tür güvenlik moduyla işlevsel olarak eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="1f167-118">Existing Msmq applications are functionally equivalent with this type of security mode.</span></span><br /><br /> <span data-ttu-id="1f167-119">`Transport` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="1f167-119">The default value is `Transport`.</span></span> <span data-ttu-id="1f167-120">Bu öznitelik türü <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurityMode> .</span><span class="sxs-lookup"><span data-stu-id="1f167-120">This attribute is of type <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1f167-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="1f167-121">Child Elements</span></span>  
  
|<span data-ttu-id="1f167-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="1f167-122">Element</span></span>|<span data-ttu-id="1f167-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1f167-123">Description</span></span>|  
|-------------|-----------------|  
|[\<transport>](transport-of-msmqintegrationbinding.md)|<span data-ttu-id="1f167-124">Message Queuing tümleştirme taşıması için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="1f167-124">Defines the security settings for the Message Queuing integration transport.</span></span> <span data-ttu-id="1f167-125">Bu öğe türündedir <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement> .</span><span class="sxs-lookup"><span data-stu-id="1f167-125">This element is of type <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1f167-126">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="1f167-126">Parent Elements</span></span>  
  
|<span data-ttu-id="1f167-127">Öğe</span><span class="sxs-lookup"><span data-stu-id="1f167-127">Element</span></span>|<span data-ttu-id="1f167-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1f167-128">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="1f167-129">Öğesinin bağlama öğesi [\<msmqIntegrationBinding>](msmqintegrationbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="1f167-129">The binding element of the [\<msmqIntegrationBinding>](msmqintegrationbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1f167-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1f167-130">See also</span></span>

- <xref:System.ServiceModel.Configuration.MsmqIntegrationSecurityElement>
- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.MsmqIntegrationBindingElement.Security%2A>
- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity>
- [<span data-ttu-id="1f167-131">WCF'de Kuyruklar</span><span class="sxs-lookup"><span data-stu-id="1f167-131">Queues in WCF</span></span>](../../../wcf/feature-details/queues-in-wcf.md)
- [<span data-ttu-id="1f167-132">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="1f167-132">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="1f167-133">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="1f167-133">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="1f167-134">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="1f167-134">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="1f167-135">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="1f167-135">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
- [\<msmqIntegrationBinding>](msmqintegrationbinding.md)
