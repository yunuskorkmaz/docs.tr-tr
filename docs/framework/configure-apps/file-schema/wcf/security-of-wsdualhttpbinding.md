---
title: <security> , <wsDualHttpBinding>
ms.date: 03/30/2017
ms.assetid: 869c05e7-4ebe-467d-95ab-c8f8de4e6b9e
ms.openlocfilehash: 8bc35b3bc8f0cbe1a51ceab63d876d5859d6b325
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55270875"
---
# <a name="security-of-wsdualhttpbinding"></a><span data-ttu-id="6b779-102">\<Güvenlik >, \<wsDualHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="6b779-102">\<security> of \<wsDualHttpBinding></span></span>
<span data-ttu-id="6b779-103">Güvenlik yeteneklerini tanımlar [ \<wsDualHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="6b779-103">Defines the security capabilities of the [\<wsDualHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span></span>  
  
 <span data-ttu-id="6b779-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="6b779-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="6b779-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="6b779-105">\<bindings></span></span>  
<span data-ttu-id="6b779-106">\<wsDualHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="6b779-106">\<wsDualHttpBinding></span></span>  
<span data-ttu-id="6b779-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="6b779-107">\<binding></span></span>  
<span data-ttu-id="6b779-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="6b779-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b779-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6b779-109">Syntax</span></span>  
  
```xml  
<security mode="Message/None">
  <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           clientCredentialType="Certificate/IssuedToken/None/UserName/Windows"
           negotiateServiceCredential="Boolean"/>
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6b779-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="6b779-110">Attributes and Elements</span></span>  
 <span data-ttu-id="6b779-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6b779-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6b779-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="6b779-112">Attributes</span></span>  
  
|<span data-ttu-id="6b779-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="6b779-113">Attribute</span></span>|<span data-ttu-id="6b779-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6b779-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6b779-115">mod</span><span class="sxs-lookup"><span data-stu-id="6b779-115">mode</span></span>|<span data-ttu-id="6b779-116">-İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="6b779-116">-   Optional.</span></span> <span data-ttu-id="6b779-117">Uygulanan güvenlik türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="6b779-117">Specifies the type of security that is applied.</span></span> <span data-ttu-id="6b779-118">Varsayılan değer `Message` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="6b779-118">The default value is `Message`.</span></span> <span data-ttu-id="6b779-119">Bu öznitelik türünde <xref:System.ServiceModel.WSDualHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="6b779-119">This attribute is of type <xref:System.ServiceModel.WSDualHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="6b779-120">mod özniteliği</span><span class="sxs-lookup"><span data-stu-id="6b779-120">Mode Attribute</span></span>  
  
|<span data-ttu-id="6b779-121">Değer</span><span class="sxs-lookup"><span data-stu-id="6b779-121">Value</span></span>|<span data-ttu-id="6b779-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6b779-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6b779-123">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="6b779-123">None</span></span>|<span data-ttu-id="6b779-124">Güvenlik devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="6b779-124">Security is disabled.</span></span>|  
|<span data-ttu-id="6b779-125">İleti</span><span class="sxs-lookup"><span data-stu-id="6b779-125">Message</span></span>|<span data-ttu-id="6b779-126">SOAP ileti güveliği kullanarak güvenliği sağlanır.</span><span class="sxs-lookup"><span data-stu-id="6b779-126">Security is provided using SOAP message security.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6b779-127">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="6b779-127">Child Elements</span></span>  
  
|<span data-ttu-id="6b779-128">Öğe</span><span class="sxs-lookup"><span data-stu-id="6b779-128">Element</span></span>|<span data-ttu-id="6b779-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6b779-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6b779-130">\<İleti ></span><span class="sxs-lookup"><span data-stu-id="6b779-130">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wsdualhttpbinding.md)|<span data-ttu-id="6b779-131">İleti düzeyi güvenlik ayarları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6b779-131">Defines the settings for the message-level security.</span></span> <span data-ttu-id="6b779-132">Bu öğe türünde <xref:System.ServiceModel.MessageSecurityOverHttp>.</span><span class="sxs-lookup"><span data-stu-id="6b779-132">This element is of type <xref:System.ServiceModel.MessageSecurityOverHttp>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6b779-133">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="6b779-133">Parent Elements</span></span>  
  
|<span data-ttu-id="6b779-134">Öğe</span><span class="sxs-lookup"><span data-stu-id="6b779-134">Element</span></span>|<span data-ttu-id="6b779-135">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6b779-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6b779-136">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="6b779-136">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="6b779-137">Tüm bağlama yeteneklerini tanımlar [ \<wsDualHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="6b779-137">Defines all binding capabilities of the [\<wsDualHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6b779-138">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6b779-138">Remarks</span></span>  
 <span data-ttu-id="6b779-139">İkili bir bağlama hizmeti için istemci IP adresi sunar.</span><span class="sxs-lookup"><span data-stu-id="6b779-139">A dual binding exposes the IP address of the client to the service.</span></span> <span data-ttu-id="6b779-140">İstemci, yalnızca Hizmetleri güvenleri bağladığı emin olmak için güvenlik kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="6b779-140">The client should use security to ensure that it only connects to services it trusts.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b779-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6b779-141">See also</span></span>
- <xref:System.ServiceModel.WSDualHttpSecurity>
- <xref:System.ServiceModel.BasicHttpSecurity>
- [<span data-ttu-id="6b779-142">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="6b779-142">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="6b779-143">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="6b779-143">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="6b779-144">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="6b779-144">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="6b779-145">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="6b779-145">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="6b779-146">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="6b779-146">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
