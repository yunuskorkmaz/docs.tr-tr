---
title: <security> / <wsDualHttpBinding>
ms.date: 03/30/2017
ms.assetid: 869c05e7-4ebe-467d-95ab-c8f8de4e6b9e
ms.openlocfilehash: bed7f4ce325e0d5e387e310ca15a3b72ac93f18e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936552"
---
# <a name="security-of-wsdualhttpbinding"></a><span data-ttu-id="b090d-102">\<\<WSDualHttpBinding > Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="b090d-102">\<security> of \<wsDualHttpBinding></span></span>
<span data-ttu-id="b090d-103">[ \<WSDualHttpBinding >](wsdualhttpbinding.md)'nin güvenlik yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b090d-103">Defines the security capabilities of the [\<wsDualHttpBinding>](wsdualhttpbinding.md).</span></span>  
  
 <span data-ttu-id="b090d-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="b090d-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="b090d-105">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="b090d-105">\<bindings></span></span>  
<span data-ttu-id="b090d-106">\<wsDualHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="b090d-106">\<wsDualHttpBinding></span></span>  
<span data-ttu-id="b090d-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="b090d-107">\<binding></span></span>  
<span data-ttu-id="b090d-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="b090d-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b090d-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b090d-109">Syntax</span></span>  
  
```xml  
<security mode="Message/None">
  <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           clientCredentialType="Certificate/IssuedToken/None/UserName/Windows"
           negotiateServiceCredential="Boolean"/>
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b090d-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="b090d-110">Attributes and Elements</span></span>  
 <span data-ttu-id="b090d-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b090d-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b090d-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b090d-112">Attributes</span></span>  
  
|<span data-ttu-id="b090d-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="b090d-113">Attribute</span></span>|<span data-ttu-id="b090d-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b090d-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b090d-115">mod</span><span class="sxs-lookup"><span data-stu-id="b090d-115">mode</span></span>|<span data-ttu-id="b090d-116">Seçim.</span><span class="sxs-lookup"><span data-stu-id="b090d-116">-   Optional.</span></span> <span data-ttu-id="b090d-117">Uygulanan güvenlik türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="b090d-117">Specifies the type of security that is applied.</span></span> <span data-ttu-id="b090d-118">Varsayılan değer `Message` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="b090d-118">The default value is `Message`.</span></span> <span data-ttu-id="b090d-119">Bu öznitelik türü <xref:System.ServiceModel.WSDualHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="b090d-119">This attribute is of type <xref:System.ServiceModel.WSDualHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="b090d-120">Mode özniteliği</span><span class="sxs-lookup"><span data-stu-id="b090d-120">Mode Attribute</span></span>  
  
|<span data-ttu-id="b090d-121">Değer</span><span class="sxs-lookup"><span data-stu-id="b090d-121">Value</span></span>|<span data-ttu-id="b090d-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b090d-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b090d-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="b090d-123">None</span></span>|<span data-ttu-id="b090d-124">Güvenlik devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="b090d-124">Security is disabled.</span></span>|  
|<span data-ttu-id="b090d-125">`Message`</span><span class="sxs-lookup"><span data-stu-id="b090d-125">Message</span></span>|<span data-ttu-id="b090d-126">Güvenlik, SOAP iletisi güvenliği kullanılarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="b090d-126">Security is provided using SOAP message security.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b090d-127">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="b090d-127">Child Elements</span></span>  
  
|<span data-ttu-id="b090d-128">Öğe</span><span class="sxs-lookup"><span data-stu-id="b090d-128">Element</span></span>|<span data-ttu-id="b090d-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b090d-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b090d-130">\<ileti ></span><span class="sxs-lookup"><span data-stu-id="b090d-130">\<message></span></span>](message-of-wsdualhttpbinding.md)|<span data-ttu-id="b090d-131">İleti düzeyinde güvenlik için ayarları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b090d-131">Defines the settings for the message-level security.</span></span> <span data-ttu-id="b090d-132">Bu öğe türündedir <xref:System.ServiceModel.MessageSecurityOverHttp>.</span><span class="sxs-lookup"><span data-stu-id="b090d-132">This element is of type <xref:System.ServiceModel.MessageSecurityOverHttp>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b090d-133">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="b090d-133">Parent Elements</span></span>  
  
|<span data-ttu-id="b090d-134">Öğe</span><span class="sxs-lookup"><span data-stu-id="b090d-134">Element</span></span>|<span data-ttu-id="b090d-135">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b090d-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b090d-136">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="b090d-136">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="b090d-137">WSDualHttpBinding > Tüm bağlama yeteneklerini [ \<](wsdualhttpbinding.md)tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b090d-137">Defines all binding capabilities of the [\<wsDualHttpBinding>](wsdualhttpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b090d-138">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b090d-138">Remarks</span></span>  
 <span data-ttu-id="b090d-139">İkili bağlama, istemcinin IP adresini hizmete gösterir.</span><span class="sxs-lookup"><span data-stu-id="b090d-139">A dual binding exposes the IP address of the client to the service.</span></span> <span data-ttu-id="b090d-140">İstemci, yalnızca güvendiği hizmetlere bağlanmasını sağlamak için güvenliği kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b090d-140">The client should use security to ensure that it only connects to services it trusts.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b090d-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b090d-141">See also</span></span>

- <xref:System.ServiceModel.WSDualHttpSecurity>
- <xref:System.ServiceModel.BasicHttpSecurity>
- [<span data-ttu-id="b090d-142">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="b090d-142">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="b090d-143">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="b090d-143">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="b090d-144">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="b090d-144">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="b090d-145">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="b090d-145">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="b090d-146">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="b090d-146">\<binding></span></span>](../../../misc/binding.md)
