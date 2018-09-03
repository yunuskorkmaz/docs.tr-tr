---
title: '&lt;wsDualHttpBinding&gt; &lt;güvenliği&gt;'
ms.date: 03/30/2017
ms.assetid: 869c05e7-4ebe-467d-95ab-c8f8de4e6b9e
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 023e0dd2a89c005928625cf95f3de61af81c7b6b
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43465005"
---
# <a name="ltsecuritygt-of-ltwsdualhttpbindinggt"></a><span data-ttu-id="9bccd-102">&lt;wsDualHttpBinding&gt; &lt;güvenliği&gt;</span><span class="sxs-lookup"><span data-stu-id="9bccd-102">&lt;security&gt; of &lt;wsDualHttpBinding&gt;</span></span>
<span data-ttu-id="9bccd-103">Güvenlik yeteneklerini tanımlar [ \<wsDualHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="9bccd-103">Defines the security capabilities of the [\<wsDualHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span></span>  
  
 <span data-ttu-id="9bccd-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="9bccd-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="9bccd-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="9bccd-105">\<bindings></span></span>  
<span data-ttu-id="9bccd-106">\<wsDualHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="9bccd-106">\<wsDualHttpBinding></span></span>  
<span data-ttu-id="9bccd-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="9bccd-107">\<binding></span></span>  
<span data-ttu-id="9bccd-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="9bccd-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9bccd-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9bccd-109">Syntax</span></span>  
  
```xml  
<security mode="Message/None">  
   <message  
      algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
      clientCredentialType="Certificate/IssuedToken/None/UserName/Windows"  
      negotiateServiceCredential="Boolean"/>  
</security>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9bccd-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="9bccd-110">Attributes and Elements</span></span>  
 <span data-ttu-id="9bccd-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9bccd-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9bccd-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="9bccd-112">Attributes</span></span>  
  
|<span data-ttu-id="9bccd-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="9bccd-113">Attribute</span></span>|<span data-ttu-id="9bccd-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9bccd-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9bccd-115">mod</span><span class="sxs-lookup"><span data-stu-id="9bccd-115">mode</span></span>|<span data-ttu-id="9bccd-116">-İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="9bccd-116">-   Optional.</span></span> <span data-ttu-id="9bccd-117">Uygulanan güvenlik türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="9bccd-117">Specifies the type of security that is applied.</span></span> <span data-ttu-id="9bccd-118">Varsayılan değer `Message` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="9bccd-118">The default value is `Message`.</span></span> <span data-ttu-id="9bccd-119">Bu öznitelik türünde <xref:System.ServiceModel.WSDualHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="9bccd-119">This attribute is of type <xref:System.ServiceModel.WSDualHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="9bccd-120">mod özniteliği</span><span class="sxs-lookup"><span data-stu-id="9bccd-120">Mode Attribute</span></span>  
  
|<span data-ttu-id="9bccd-121">Değer</span><span class="sxs-lookup"><span data-stu-id="9bccd-121">Value</span></span>|<span data-ttu-id="9bccd-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9bccd-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="9bccd-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="9bccd-123">None</span></span>|<span data-ttu-id="9bccd-124">Güvenlik devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="9bccd-124">Security is disabled.</span></span>|  
|<span data-ttu-id="9bccd-125">İleti</span><span class="sxs-lookup"><span data-stu-id="9bccd-125">Message</span></span>|<span data-ttu-id="9bccd-126">SOAP ileti güveliği kullanarak güvenliği sağlanır.</span><span class="sxs-lookup"><span data-stu-id="9bccd-126">Security is provided using SOAP message security.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9bccd-127">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="9bccd-127">Child Elements</span></span>  
  
|<span data-ttu-id="9bccd-128">Öğe</span><span class="sxs-lookup"><span data-stu-id="9bccd-128">Element</span></span>|<span data-ttu-id="9bccd-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9bccd-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9bccd-130">\<İleti ></span><span class="sxs-lookup"><span data-stu-id="9bccd-130">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wsdualhttpbinding.md)|<span data-ttu-id="9bccd-131">İleti düzeyi güvenlik ayarları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="9bccd-131">Defines the settings for the message-level security.</span></span> <span data-ttu-id="9bccd-132">Bu öğe türünde <xref:System.ServiceModel.MessageSecurityOverHttp>.</span><span class="sxs-lookup"><span data-stu-id="9bccd-132">This element is of type <xref:System.ServiceModel.MessageSecurityOverHttp>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9bccd-133">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="9bccd-133">Parent Elements</span></span>  
  
|<span data-ttu-id="9bccd-134">Öğe</span><span class="sxs-lookup"><span data-stu-id="9bccd-134">Element</span></span>|<span data-ttu-id="9bccd-135">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9bccd-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9bccd-136">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="9bccd-136">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="9bccd-137">Tüm bağlama yeteneklerini tanımlar [ \<wsDualHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="9bccd-137">Defines all binding capabilities of the [\<wsDualHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9bccd-138">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9bccd-138">Remarks</span></span>  
 <span data-ttu-id="9bccd-139">İkili bir bağlama hizmeti için istemci IP adresi sunar.</span><span class="sxs-lookup"><span data-stu-id="9bccd-139">A dual binding exposes the IP address of the client to the service.</span></span> <span data-ttu-id="9bccd-140">İstemci, yalnızca Hizmetleri güvenleri bağladığı emin olmak için güvenlik kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="9bccd-140">The client should use security to ensure that it only connects to services it trusts.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9bccd-141">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9bccd-141">See Also</span></span>  
 <xref:System.ServiceModel.WSDualHttpSecurity>  
 <xref:System.ServiceModel.BasicHttpSecurity>  
 [<span data-ttu-id="9bccd-142">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="9bccd-142">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="9bccd-143">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="9bccd-143">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="9bccd-144">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="9bccd-144">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="9bccd-145">Windows Communication Foundation Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma</span><span class="sxs-lookup"><span data-stu-id="9bccd-145">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="9bccd-146">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="9bccd-146">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
