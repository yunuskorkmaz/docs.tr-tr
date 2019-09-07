---
title: <security> / <msmqIntegrationBinding>
ms.date: 03/30/2017
ms.assetid: ae5c68a8-14a2-4c6e-b9e0-3e94e3e9135e
ms.openlocfilehash: e4f10ab994429c6cbb690caef38114b8340e6839
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399861"
---
# <a name="security-of-msmqintegrationbinding"></a><span data-ttu-id="2c4b4-102">\<\<MsmqIntegrationBinding > Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="2c4b4-102">\<security> of \<msmqIntegrationBinding></span></span>
<span data-ttu-id="2c4b4-103">Message Queuing (MSMQ) tümleştirme kanalının taşıma güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="2c4b4-103">Defines the transport security settings for the Message Queuing (MSMQ) integration channel.</span></span>  
  
<span data-ttu-id="2c4b4-104">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="2c4b4-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="2c4b4-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="2c4b4-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="2c4b4-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bağlama >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="2c4b4-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="2c4b4-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<MsmqIntegrationBinding >** ](msmqintegrationbinding.md)</span><span class="sxs-lookup"><span data-stu-id="2c4b4-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<msmqIntegrationBinding>**](msmqintegrationbinding.md)</span></span>\
<span data-ttu-id="2c4b4-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bağlama >** </span><span class="sxs-lookup"><span data-stu-id="2c4b4-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="2c4b4-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Güvenlik >**</span><span class="sxs-lookup"><span data-stu-id="2c4b4-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c4b4-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2c4b4-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2c4b4-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="2c4b4-111">Attributes and Elements</span></span>  
 <span data-ttu-id="2c4b4-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2c4b4-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2c4b4-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="2c4b4-113">Attributes</span></span>  
  
|<span data-ttu-id="2c4b4-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="2c4b4-114">Attribute</span></span>|<span data-ttu-id="2c4b4-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2c4b4-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2c4b4-116">mod</span><span class="sxs-lookup"><span data-stu-id="2c4b4-116">mode</span></span>|<span data-ttu-id="2c4b4-117">Message Queuing tümleştirme kanalı ile bütünlüğü, gizliliği ve kimlik doğrulamasını denetleyen güvenlik türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="2c4b4-117">Specifies the type of security that controls integrity, confidentiality and authentication with the Message Queuing integration channel.</span></span> <span data-ttu-id="2c4b4-118">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="2c4b4-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="2c4b4-119">Seçim Bu, güvenliği devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="2c4b4-119">-   None: This disables security.</span></span><br /><span data-ttu-id="2c4b4-120">Aktarım Koruma ve kimlik doğrulama, taşıma tarafından sunulur.</span><span class="sxs-lookup"><span data-stu-id="2c4b4-120">-   Transport: Protection and authentication are offered by the transport.</span></span> <span data-ttu-id="2c4b4-121">Bu, iki kuyruk yöneticisi arasındaki ileti güvenliği için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="2c4b4-121">This applies to the message security between the two queue managers.</span></span> <span data-ttu-id="2c4b4-122">Uygulama ve kuyruk Yöneticisi arasında bir güvenlik sunulmaz.</span><span class="sxs-lookup"><span data-stu-id="2c4b4-122">There is no security offered between the application and queue manager.</span></span> <span data-ttu-id="2c4b4-123">Mevcut MSMQ uygulamaları, bu tür güvenlik moduyla işlevsel olarak eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="2c4b4-123">Existing Msmq applications are functionally equivalent with this type of security mode.</span></span><br /><br /> <span data-ttu-id="2c4b4-124">Varsayılan değer `Transport` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="2c4b4-124">The default value is `Transport`.</span></span> <span data-ttu-id="2c4b4-125">Bu öznitelik türü <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="2c4b4-125">This attribute is of type <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2c4b4-126">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="2c4b4-126">Child Elements</span></span>  
  
|<span data-ttu-id="2c4b4-127">Öğe</span><span class="sxs-lookup"><span data-stu-id="2c4b4-127">Element</span></span>|<span data-ttu-id="2c4b4-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2c4b4-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2c4b4-129">\<Taşıma ></span><span class="sxs-lookup"><span data-stu-id="2c4b4-129">\<transport></span></span>](transport-of-msmqintegrationbinding.md)|<span data-ttu-id="2c4b4-130">Message Queuing tümleştirme taşıması için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="2c4b4-130">Defines the security settings for the Message Queuing integration transport.</span></span> <span data-ttu-id="2c4b4-131">Bu öğe türündedir <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="2c4b4-131">This element is of type <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2c4b4-132">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="2c4b4-132">Parent Elements</span></span>  
  
|<span data-ttu-id="2c4b4-133">Öğe</span><span class="sxs-lookup"><span data-stu-id="2c4b4-133">Element</span></span>|<span data-ttu-id="2c4b4-134">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2c4b4-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2c4b4-135">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="2c4b4-135">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="2c4b4-136">[ \<MsmqIntegrationBinding](msmqintegrationbinding.md)'in Binding öğesi >.</span><span class="sxs-lookup"><span data-stu-id="2c4b4-136">The binding element of the [\<msmqIntegrationBinding>](msmqintegrationbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2c4b4-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2c4b4-137">See also</span></span>

- <xref:System.ServiceModel.Configuration.MsmqIntegrationSecurityElement>
- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.MsmqIntegrationBindingElement.Security%2A>
- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity>
- [<span data-ttu-id="2c4b4-138">WCF'de Kuyruklar</span><span class="sxs-lookup"><span data-stu-id="2c4b4-138">Queues in WCF</span></span>](../../../wcf/feature-details/queues-in-wcf.md)
- [<span data-ttu-id="2c4b4-139">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="2c4b4-139">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="2c4b4-140">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="2c4b4-140">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="2c4b4-141">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="2c4b4-141">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="2c4b4-142">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="2c4b4-142">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="2c4b4-143">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="2c4b4-143">\<binding></span></span>](../../../misc/binding.md)
- [<span data-ttu-id="2c4b4-144">\<MsmqIntegrationBinding ></span><span class="sxs-lookup"><span data-stu-id="2c4b4-144">\<msmqIntegrationBinding></span></span>](msmqintegrationbinding.md)
