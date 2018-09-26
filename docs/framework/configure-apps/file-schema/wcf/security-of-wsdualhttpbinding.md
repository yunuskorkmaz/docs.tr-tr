---
title: '&lt;wsDualHttpBinding&gt; &lt;güvenliği&gt;'
ms.date: 03/30/2017
ms.assetid: 869c05e7-4ebe-467d-95ab-c8f8de4e6b9e
author: BrucePerlerMS
ms.openlocfilehash: c817ea6faf5229a8d372a06b866c75e0f40af3b3
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47113062"
---
# <a name="ltsecuritygt-of-ltwsdualhttpbindinggt"></a><span data-ttu-id="2fd6c-102">&lt;wsDualHttpBinding&gt; &lt;güvenliği&gt;</span><span class="sxs-lookup"><span data-stu-id="2fd6c-102">&lt;security&gt; of &lt;wsDualHttpBinding&gt;</span></span>
<span data-ttu-id="2fd6c-103">Güvenlik yeteneklerini tanımlar [ \<wsDualHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="2fd6c-103">Defines the security capabilities of the [\<wsDualHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span></span>  
  
 <span data-ttu-id="2fd6c-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="2fd6c-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="2fd6c-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="2fd6c-105">\<bindings></span></span>  
<span data-ttu-id="2fd6c-106">\<wsDualHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="2fd6c-106">\<wsDualHttpBinding></span></span>  
<span data-ttu-id="2fd6c-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="2fd6c-107">\<binding></span></span>  
<span data-ttu-id="2fd6c-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="2fd6c-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2fd6c-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2fd6c-109">Syntax</span></span>  
  
```xml  
<security mode="Message/None">  
   <message  
      algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
      clientCredentialType="Certificate/IssuedToken/None/UserName/Windows"  
      negotiateServiceCredential="Boolean"/>  
</security>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2fd6c-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="2fd6c-110">Attributes and Elements</span></span>  
 <span data-ttu-id="2fd6c-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2fd6c-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2fd6c-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="2fd6c-112">Attributes</span></span>  
  
|<span data-ttu-id="2fd6c-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="2fd6c-113">Attribute</span></span>|<span data-ttu-id="2fd6c-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2fd6c-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2fd6c-115">mod</span><span class="sxs-lookup"><span data-stu-id="2fd6c-115">mode</span></span>|<span data-ttu-id="2fd6c-116">-İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="2fd6c-116">-   Optional.</span></span> <span data-ttu-id="2fd6c-117">Uygulanan güvenlik türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="2fd6c-117">Specifies the type of security that is applied.</span></span> <span data-ttu-id="2fd6c-118">Varsayılan değer `Message` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="2fd6c-118">The default value is `Message`.</span></span> <span data-ttu-id="2fd6c-119">Bu öznitelik türünde <xref:System.ServiceModel.WSDualHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="2fd6c-119">This attribute is of type <xref:System.ServiceModel.WSDualHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="2fd6c-120">mod özniteliği</span><span class="sxs-lookup"><span data-stu-id="2fd6c-120">Mode Attribute</span></span>  
  
|<span data-ttu-id="2fd6c-121">Değer</span><span class="sxs-lookup"><span data-stu-id="2fd6c-121">Value</span></span>|<span data-ttu-id="2fd6c-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2fd6c-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="2fd6c-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="2fd6c-123">None</span></span>|<span data-ttu-id="2fd6c-124">Güvenlik devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="2fd6c-124">Security is disabled.</span></span>|  
|<span data-ttu-id="2fd6c-125">İleti</span><span class="sxs-lookup"><span data-stu-id="2fd6c-125">Message</span></span>|<span data-ttu-id="2fd6c-126">SOAP ileti güveliği kullanarak güvenliği sağlanır.</span><span class="sxs-lookup"><span data-stu-id="2fd6c-126">Security is provided using SOAP message security.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2fd6c-127">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="2fd6c-127">Child Elements</span></span>  
  
|<span data-ttu-id="2fd6c-128">Öğe</span><span class="sxs-lookup"><span data-stu-id="2fd6c-128">Element</span></span>|<span data-ttu-id="2fd6c-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2fd6c-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2fd6c-130">\<İleti ></span><span class="sxs-lookup"><span data-stu-id="2fd6c-130">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wsdualhttpbinding.md)|<span data-ttu-id="2fd6c-131">İleti düzeyi güvenlik ayarları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="2fd6c-131">Defines the settings for the message-level security.</span></span> <span data-ttu-id="2fd6c-132">Bu öğe türünde <xref:System.ServiceModel.MessageSecurityOverHttp>.</span><span class="sxs-lookup"><span data-stu-id="2fd6c-132">This element is of type <xref:System.ServiceModel.MessageSecurityOverHttp>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2fd6c-133">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="2fd6c-133">Parent Elements</span></span>  
  
|<span data-ttu-id="2fd6c-134">Öğe</span><span class="sxs-lookup"><span data-stu-id="2fd6c-134">Element</span></span>|<span data-ttu-id="2fd6c-135">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2fd6c-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2fd6c-136">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="2fd6c-136">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="2fd6c-137">Tüm bağlama yeteneklerini tanımlar [ \<wsDualHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="2fd6c-137">Defines all binding capabilities of the [\<wsDualHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2fd6c-138">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2fd6c-138">Remarks</span></span>  
 <span data-ttu-id="2fd6c-139">İkili bir bağlama hizmeti için istemci IP adresi sunar.</span><span class="sxs-lookup"><span data-stu-id="2fd6c-139">A dual binding exposes the IP address of the client to the service.</span></span> <span data-ttu-id="2fd6c-140">İstemci, yalnızca Hizmetleri güvenleri bağladığı emin olmak için güvenlik kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="2fd6c-140">The client should use security to ensure that it only connects to services it trusts.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2fd6c-141">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2fd6c-141">See Also</span></span>  
 <xref:System.ServiceModel.WSDualHttpSecurity>  
 <xref:System.ServiceModel.BasicHttpSecurity>  
 [<span data-ttu-id="2fd6c-142">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="2fd6c-142">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="2fd6c-143">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="2fd6c-143">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="2fd6c-144">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="2fd6c-144">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="2fd6c-145">Windows Communication Foundation Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma</span><span class="sxs-lookup"><span data-stu-id="2fd6c-145">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="2fd6c-146">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="2fd6c-146">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
