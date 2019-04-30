---
title: <security> / <wsDualHttpBinding>
ms.date: 03/30/2017
ms.assetid: 869c05e7-4ebe-467d-95ab-c8f8de4e6b9e
ms.openlocfilehash: c6f9e34724ccc3a0d05da3e1886b4f0bcbaae064
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61670449"
---
# <a name="security-of-wsdualhttpbinding"></a><span data-ttu-id="89510-102">\<Güvenlik >, \<wsDualHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="89510-102">\<security> of \<wsDualHttpBinding></span></span>
<span data-ttu-id="89510-103">Güvenlik yeteneklerini tanımlar [ \<wsDualHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="89510-103">Defines the security capabilities of the [\<wsDualHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span></span>  
  
 <span data-ttu-id="89510-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="89510-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="89510-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="89510-105">\<bindings></span></span>  
<span data-ttu-id="89510-106">\<wsDualHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="89510-106">\<wsDualHttpBinding></span></span>  
<span data-ttu-id="89510-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="89510-107">\<binding></span></span>  
<span data-ttu-id="89510-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="89510-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89510-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="89510-109">Syntax</span></span>  
  
```xml  
<security mode="Message/None">
  <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           clientCredentialType="Certificate/IssuedToken/None/UserName/Windows"
           negotiateServiceCredential="Boolean"/>
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="89510-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="89510-110">Attributes and Elements</span></span>  
 <span data-ttu-id="89510-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="89510-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="89510-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="89510-112">Attributes</span></span>  
  
|<span data-ttu-id="89510-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="89510-113">Attribute</span></span>|<span data-ttu-id="89510-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="89510-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="89510-115">mod</span><span class="sxs-lookup"><span data-stu-id="89510-115">mode</span></span>|<span data-ttu-id="89510-116">-İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="89510-116">-   Optional.</span></span> <span data-ttu-id="89510-117">Uygulanan güvenlik türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="89510-117">Specifies the type of security that is applied.</span></span> <span data-ttu-id="89510-118">Varsayılan değer `Message` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="89510-118">The default value is `Message`.</span></span> <span data-ttu-id="89510-119">Bu öznitelik türünde <xref:System.ServiceModel.WSDualHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="89510-119">This attribute is of type <xref:System.ServiceModel.WSDualHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="89510-120">mod özniteliği</span><span class="sxs-lookup"><span data-stu-id="89510-120">Mode Attribute</span></span>  
  
|<span data-ttu-id="89510-121">Değer</span><span class="sxs-lookup"><span data-stu-id="89510-121">Value</span></span>|<span data-ttu-id="89510-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="89510-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="89510-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="89510-123">None</span></span>|<span data-ttu-id="89510-124">Güvenlik devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="89510-124">Security is disabled.</span></span>|  
|<span data-ttu-id="89510-125">İleti</span><span class="sxs-lookup"><span data-stu-id="89510-125">Message</span></span>|<span data-ttu-id="89510-126">SOAP ileti güveliği kullanarak güvenliği sağlanır.</span><span class="sxs-lookup"><span data-stu-id="89510-126">Security is provided using SOAP message security.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="89510-127">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="89510-127">Child Elements</span></span>  
  
|<span data-ttu-id="89510-128">Öğe</span><span class="sxs-lookup"><span data-stu-id="89510-128">Element</span></span>|<span data-ttu-id="89510-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="89510-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="89510-130">\<İleti ></span><span class="sxs-lookup"><span data-stu-id="89510-130">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wsdualhttpbinding.md)|<span data-ttu-id="89510-131">İleti düzeyi güvenlik ayarları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="89510-131">Defines the settings for the message-level security.</span></span> <span data-ttu-id="89510-132">Bu öğe türünde <xref:System.ServiceModel.MessageSecurityOverHttp>.</span><span class="sxs-lookup"><span data-stu-id="89510-132">This element is of type <xref:System.ServiceModel.MessageSecurityOverHttp>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="89510-133">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="89510-133">Parent Elements</span></span>  
  
|<span data-ttu-id="89510-134">Öğe</span><span class="sxs-lookup"><span data-stu-id="89510-134">Element</span></span>|<span data-ttu-id="89510-135">Açıklama</span><span class="sxs-lookup"><span data-stu-id="89510-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="89510-136">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="89510-136">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="89510-137">Tüm bağlama yeteneklerini tanımlar [ \<wsDualHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="89510-137">Defines all binding capabilities of the [\<wsDualHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="89510-138">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="89510-138">Remarks</span></span>  
 <span data-ttu-id="89510-139">İkili bir bağlama hizmeti için istemci IP adresi sunar.</span><span class="sxs-lookup"><span data-stu-id="89510-139">A dual binding exposes the IP address of the client to the service.</span></span> <span data-ttu-id="89510-140">İstemci, yalnızca Hizmetleri güvenleri bağladığı emin olmak için güvenlik kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="89510-140">The client should use security to ensure that it only connects to services it trusts.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89510-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="89510-141">See also</span></span>

- <xref:System.ServiceModel.WSDualHttpSecurity>
- <xref:System.ServiceModel.BasicHttpSecurity>
- [<span data-ttu-id="89510-142">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="89510-142">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="89510-143">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="89510-143">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="89510-144">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="89510-144">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="89510-145">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="89510-145">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="89510-146">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="89510-146">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
