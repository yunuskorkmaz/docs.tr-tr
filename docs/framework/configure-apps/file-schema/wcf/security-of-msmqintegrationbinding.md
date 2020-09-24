---
title: <security> / <msmqIntegrationBinding>
ms.date: 03/30/2017
ms.assetid: ae5c68a8-14a2-4c6e-b9e0-3e94e3e9135e
ms.openlocfilehash: be2f48f7d9c3be4ea0a5fe95436930b3f23c7551
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91170070"
---
# <a name="security-of-msmqintegrationbinding"></a><span data-ttu-id="d8ce0-102">\<security> / \<msmqIntegrationBinding></span><span class="sxs-lookup"><span data-stu-id="d8ce0-102">\<security> of \<msmqIntegrationBinding></span></span>

<span data-ttu-id="d8ce0-103">Message Queuing (MSMQ) tümleştirme kanalının taşıma güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d8ce0-103">Defines the transport security settings for the Message Queuing (MSMQ) integration channel.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<msmqIntegrationBinding>**](msmqintegrationbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="d8ce0-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="d8ce0-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d8ce0-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d8ce0-105">Attributes and Elements</span></span>  

 <span data-ttu-id="d8ce0-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d8ce0-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d8ce0-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d8ce0-107">Attributes</span></span>  
  
|<span data-ttu-id="d8ce0-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="d8ce0-108">Attribute</span></span>|<span data-ttu-id="d8ce0-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d8ce0-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d8ce0-110">mod</span><span class="sxs-lookup"><span data-stu-id="d8ce0-110">mode</span></span>|<span data-ttu-id="d8ce0-111">Message Queuing tümleştirme kanalı ile bütünlüğü, gizliliği ve kimlik doğrulamasını denetleyen güvenlik türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="d8ce0-111">Specifies the type of security that controls integrity, confidentiality and authentication with the Message Queuing integration channel.</span></span> <span data-ttu-id="d8ce0-112">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="d8ce0-112">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="d8ce0-113">-None: Bu, güvenliği devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="d8ce0-113">-   None: This disables security.</span></span><br /><span data-ttu-id="d8ce0-114">-Taşıma: koruma ve kimlik doğrulama, taşıma tarafından sunulur.</span><span class="sxs-lookup"><span data-stu-id="d8ce0-114">-   Transport: Protection and authentication are offered by the transport.</span></span> <span data-ttu-id="d8ce0-115">Bu, iki kuyruk yöneticisi arasındaki ileti güvenliği için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="d8ce0-115">This applies to the message security between the two queue managers.</span></span> <span data-ttu-id="d8ce0-116">Uygulama ve kuyruk Yöneticisi arasında bir güvenlik sunulmaz.</span><span class="sxs-lookup"><span data-stu-id="d8ce0-116">There is no security offered between the application and queue manager.</span></span> <span data-ttu-id="d8ce0-117">Mevcut MSMQ uygulamaları, bu tür güvenlik moduyla işlevsel olarak eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="d8ce0-117">Existing Msmq applications are functionally equivalent with this type of security mode.</span></span><br /><br /> <span data-ttu-id="d8ce0-118">Varsayılan değer: `Transport`.</span><span class="sxs-lookup"><span data-stu-id="d8ce0-118">The default value is `Transport`.</span></span> <span data-ttu-id="d8ce0-119">Bu öznitelik türü <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurityMode> .</span><span class="sxs-lookup"><span data-stu-id="d8ce0-119">This attribute is of type <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d8ce0-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d8ce0-120">Child Elements</span></span>  
  
|<span data-ttu-id="d8ce0-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="d8ce0-121">Element</span></span>|<span data-ttu-id="d8ce0-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d8ce0-122">Description</span></span>|  
|-------------|-----------------|  
|[\<transport>](transport-of-msmqintegrationbinding.md)|<span data-ttu-id="d8ce0-123">Message Queuing tümleştirme taşıması için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d8ce0-123">Defines the security settings for the Message Queuing integration transport.</span></span> <span data-ttu-id="d8ce0-124">Bu öğe türündedir <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement> .</span><span class="sxs-lookup"><span data-stu-id="d8ce0-124">This element is of type <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d8ce0-125">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d8ce0-125">Parent Elements</span></span>  
  
|<span data-ttu-id="d8ce0-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="d8ce0-126">Element</span></span>|<span data-ttu-id="d8ce0-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d8ce0-127">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="d8ce0-128">Öğesinin bağlama öğesi [\<msmqIntegrationBinding>](msmqintegrationbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="d8ce0-128">The binding element of the [\<msmqIntegrationBinding>](msmqintegrationbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d8ce0-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d8ce0-129">See also</span></span>

- <xref:System.ServiceModel.Configuration.MsmqIntegrationSecurityElement>
- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.MsmqIntegrationBindingElement.Security%2A>
- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity>
- [<span data-ttu-id="d8ce0-130">WCF'de Kuyruklar</span><span class="sxs-lookup"><span data-stu-id="d8ce0-130">Queues in WCF</span></span>](../../../wcf/feature-details/queues-in-wcf.md)
- [<span data-ttu-id="d8ce0-131">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="d8ce0-131">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="d8ce0-132">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="d8ce0-132">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="d8ce0-133">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="d8ce0-133">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="d8ce0-134">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="d8ce0-134">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
- [\<msmqIntegrationBinding>](msmqintegrationbinding.md)
