---
title: '&lt;wsDualHttpBinding&gt; &lt;güvenliği&gt;'
ms.date: 03/30/2017
ms.assetid: 869c05e7-4ebe-467d-95ab-c8f8de4e6b9e
author: BrucePerlerMS
ms.openlocfilehash: c817ea6faf5229a8d372a06b866c75e0f40af3b3
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48033109"
---
# <a name="ltsecuritygt-of-ltwsdualhttpbindinggt"></a><span data-ttu-id="ec1b9-102">&lt;wsDualHttpBinding&gt; &lt;güvenliği&gt;</span><span class="sxs-lookup"><span data-stu-id="ec1b9-102">&lt;security&gt; of &lt;wsDualHttpBinding&gt;</span></span>
<span data-ttu-id="ec1b9-103">Güvenlik yeteneklerini tanımlar [ \<wsDualHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="ec1b9-103">Defines the security capabilities of the [\<wsDualHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span></span>  
  
 <span data-ttu-id="ec1b9-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="ec1b9-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="ec1b9-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="ec1b9-105">\<bindings></span></span>  
<span data-ttu-id="ec1b9-106">\<wsDualHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="ec1b9-106">\<wsDualHttpBinding></span></span>  
<span data-ttu-id="ec1b9-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="ec1b9-107">\<binding></span></span>  
<span data-ttu-id="ec1b9-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="ec1b9-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec1b9-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ec1b9-109">Syntax</span></span>  
  
```xml  
<security mode="Message/None">  
   <message  
      algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
      clientCredentialType="Certificate/IssuedToken/None/UserName/Windows"  
      negotiateServiceCredential="Boolean"/>  
</security>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ec1b9-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ec1b9-110">Attributes and Elements</span></span>  
 <span data-ttu-id="ec1b9-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ec1b9-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ec1b9-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ec1b9-112">Attributes</span></span>  
  
|<span data-ttu-id="ec1b9-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="ec1b9-113">Attribute</span></span>|<span data-ttu-id="ec1b9-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ec1b9-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ec1b9-115">mod</span><span class="sxs-lookup"><span data-stu-id="ec1b9-115">mode</span></span>|<span data-ttu-id="ec1b9-116">-İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="ec1b9-116">-   Optional.</span></span> <span data-ttu-id="ec1b9-117">Uygulanan güvenlik türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="ec1b9-117">Specifies the type of security that is applied.</span></span> <span data-ttu-id="ec1b9-118">Varsayılan değer `Message` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="ec1b9-118">The default value is `Message`.</span></span> <span data-ttu-id="ec1b9-119">Bu öznitelik türünde <xref:System.ServiceModel.WSDualHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="ec1b9-119">This attribute is of type <xref:System.ServiceModel.WSDualHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="ec1b9-120">mod özniteliği</span><span class="sxs-lookup"><span data-stu-id="ec1b9-120">Mode Attribute</span></span>  
  
|<span data-ttu-id="ec1b9-121">Değer</span><span class="sxs-lookup"><span data-stu-id="ec1b9-121">Value</span></span>|<span data-ttu-id="ec1b9-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ec1b9-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ec1b9-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="ec1b9-123">None</span></span>|<span data-ttu-id="ec1b9-124">Güvenlik devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="ec1b9-124">Security is disabled.</span></span>|  
|<span data-ttu-id="ec1b9-125">İleti</span><span class="sxs-lookup"><span data-stu-id="ec1b9-125">Message</span></span>|<span data-ttu-id="ec1b9-126">SOAP ileti güveliği kullanarak güvenliği sağlanır.</span><span class="sxs-lookup"><span data-stu-id="ec1b9-126">Security is provided using SOAP message security.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ec1b9-127">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ec1b9-127">Child Elements</span></span>  
  
|<span data-ttu-id="ec1b9-128">Öğe</span><span class="sxs-lookup"><span data-stu-id="ec1b9-128">Element</span></span>|<span data-ttu-id="ec1b9-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ec1b9-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ec1b9-130">\<İleti ></span><span class="sxs-lookup"><span data-stu-id="ec1b9-130">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wsdualhttpbinding.md)|<span data-ttu-id="ec1b9-131">İleti düzeyi güvenlik ayarları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ec1b9-131">Defines the settings for the message-level security.</span></span> <span data-ttu-id="ec1b9-132">Bu öğe türünde <xref:System.ServiceModel.MessageSecurityOverHttp>.</span><span class="sxs-lookup"><span data-stu-id="ec1b9-132">This element is of type <xref:System.ServiceModel.MessageSecurityOverHttp>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ec1b9-133">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ec1b9-133">Parent Elements</span></span>  
  
|<span data-ttu-id="ec1b9-134">Öğe</span><span class="sxs-lookup"><span data-stu-id="ec1b9-134">Element</span></span>|<span data-ttu-id="ec1b9-135">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ec1b9-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ec1b9-136">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="ec1b9-136">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="ec1b9-137">Tüm bağlama yeteneklerini tanımlar [ \<wsDualHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="ec1b9-137">Defines all binding capabilities of the [\<wsDualHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ec1b9-138">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ec1b9-138">Remarks</span></span>  
 <span data-ttu-id="ec1b9-139">İkili bir bağlama hizmeti için istemci IP adresi sunar.</span><span class="sxs-lookup"><span data-stu-id="ec1b9-139">A dual binding exposes the IP address of the client to the service.</span></span> <span data-ttu-id="ec1b9-140">İstemci, yalnızca Hizmetleri güvenleri bağladığı emin olmak için güvenlik kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ec1b9-140">The client should use security to ensure that it only connects to services it trusts.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec1b9-141">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ec1b9-141">See Also</span></span>  
 <xref:System.ServiceModel.WSDualHttpSecurity>  
 <xref:System.ServiceModel.BasicHttpSecurity>  
 [<span data-ttu-id="ec1b9-142">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="ec1b9-142">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="ec1b9-143">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="ec1b9-143">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="ec1b9-144">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="ec1b9-144">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="ec1b9-145">Windows Communication Foundation Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma</span><span class="sxs-lookup"><span data-stu-id="ec1b9-145">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="ec1b9-146">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="ec1b9-146">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
