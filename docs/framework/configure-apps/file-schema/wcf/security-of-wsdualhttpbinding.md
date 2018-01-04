---
title: "&lt;wsDualHttpBinding&gt; &lt;güvenliği&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 869c05e7-4ebe-467d-95ab-c8f8de4e6b9e
caps.latest.revision: "15"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 4b90bd304ef8d87593c5b78febc0182c8fa2f091
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltsecuritygt-of-ltwsdualhttpbindinggt"></a><span data-ttu-id="fb57c-102">&lt;wsDualHttpBinding&gt; &lt;güvenliği&gt;</span><span class="sxs-lookup"><span data-stu-id="fb57c-102">&lt;security&gt; of &lt;wsDualHttpBinding&gt;</span></span>
<span data-ttu-id="fb57c-103">Güvenlik özelliklerini tanımlayan [ \<wsDualHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="fb57c-103">Defines the security capabilities of the [\<wsDualHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span></span>  
  
 <span data-ttu-id="fb57c-104">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="fb57c-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="fb57c-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="fb57c-105">\<bindings></span></span>  
<span data-ttu-id="fb57c-106">\<wsDualHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="fb57c-106">\<wsDualHttpBinding></span></span>  
<span data-ttu-id="fb57c-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="fb57c-107">\<binding></span></span>  
<span data-ttu-id="fb57c-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="fb57c-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb57c-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fb57c-109">Syntax</span></span>  
  
```xml  
<security mode="Message/None">  
   <message  
      algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
      clientCredentialType="Certificate/IssuedToken/None/UserName/Windows"  
      negotiateServiceCredential="Boolean"/>  
</security>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fb57c-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="fb57c-110">Attributes and Elements</span></span>  
 <span data-ttu-id="fb57c-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="fb57c-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fb57c-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="fb57c-112">Attributes</span></span>  
  
|<span data-ttu-id="fb57c-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="fb57c-113">Attribute</span></span>|<span data-ttu-id="fb57c-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fb57c-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fb57c-115">mod</span><span class="sxs-lookup"><span data-stu-id="fb57c-115">mode</span></span>|<span data-ttu-id="fb57c-116">-İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="fb57c-116">-   Optional.</span></span> <span data-ttu-id="fb57c-117">Uygulanan güvenlik türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="fb57c-117">Specifies the type of security that is applied.</span></span> <span data-ttu-id="fb57c-118">Varsayılan değer `Message` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="fb57c-118">The default value is `Message`.</span></span> <span data-ttu-id="fb57c-119">Bu öznitelik türünde <xref:System.ServiceModel.WSDualHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="fb57c-119">This attribute is of type <xref:System.ServiceModel.WSDualHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="fb57c-120">mod özniteliği</span><span class="sxs-lookup"><span data-stu-id="fb57c-120">Mode Attribute</span></span>  
  
|<span data-ttu-id="fb57c-121">Değer</span><span class="sxs-lookup"><span data-stu-id="fb57c-121">Value</span></span>|<span data-ttu-id="fb57c-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fb57c-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="fb57c-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="fb57c-123">None</span></span>|<span data-ttu-id="fb57c-124">Güvenliği devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="fb57c-124">Security is disabled.</span></span>|  
|<span data-ttu-id="fb57c-125">İleti</span><span class="sxs-lookup"><span data-stu-id="fb57c-125">Message</span></span>|<span data-ttu-id="fb57c-126">Güvenlik SOAP ileti güvenliği sağlanır.</span><span class="sxs-lookup"><span data-stu-id="fb57c-126">Security is provided using SOAP message security.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fb57c-127">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="fb57c-127">Child Elements</span></span>  
  
|<span data-ttu-id="fb57c-128">Öğe</span><span class="sxs-lookup"><span data-stu-id="fb57c-128">Element</span></span>|<span data-ttu-id="fb57c-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fb57c-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fb57c-130">\<İleti ></span><span class="sxs-lookup"><span data-stu-id="fb57c-130">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wsdualhttpbinding.md)|<span data-ttu-id="fb57c-131">İleti düzeyi güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="fb57c-131">Defines the settings for the message-level security.</span></span> <span data-ttu-id="fb57c-132">Bu öğe türünde <xref:System.ServiceModel.MessageSecurityOverHttp>.</span><span class="sxs-lookup"><span data-stu-id="fb57c-132">This element is of type <xref:System.ServiceModel.MessageSecurityOverHttp>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fb57c-133">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="fb57c-133">Parent Elements</span></span>  
  
|<span data-ttu-id="fb57c-134">Öğe</span><span class="sxs-lookup"><span data-stu-id="fb57c-134">Element</span></span>|<span data-ttu-id="fb57c-135">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fb57c-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fb57c-136">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="fb57c-136">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="fb57c-137">Tüm bağlama özelliklerini tanımlayan [ \<wsDualHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="fb57c-137">Defines all binding capabilities of the [\<wsDualHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fb57c-138">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fb57c-138">Remarks</span></span>  
 <span data-ttu-id="fb57c-139">Bir çift bağlama hizmeti istemcinin IP adresini gösterir.</span><span class="sxs-lookup"><span data-stu-id="fb57c-139">A dual binding exposes the IP address of the client to the service.</span></span> <span data-ttu-id="fb57c-140">İstemci, yalnızca Hizmetleri güvenleri bağladığı emin olmak için güvenlik kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="fb57c-140">The client should use security to ensure that it only connects to services it trusts.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb57c-141">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fb57c-141">See Also</span></span>  
 <xref:System.ServiceModel.WSDualHttpSecurity>  
 <xref:System.ServiceModel.BasicHttpSecurity>  
 [<span data-ttu-id="fb57c-142">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="fb57c-142">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="fb57c-143">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="fb57c-143">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="fb57c-144">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="fb57c-144">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="fb57c-145">Windows Communication Foundation Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma</span><span class="sxs-lookup"><span data-stu-id="fb57c-145">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="fb57c-146">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="fb57c-146">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
