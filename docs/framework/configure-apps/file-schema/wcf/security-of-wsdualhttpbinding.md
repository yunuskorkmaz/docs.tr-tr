---
title: '&lt;wsDualHttpBinding&gt; &lt;güvenliği&gt;'
ms.date: 03/30/2017
ms.assetid: 869c05e7-4ebe-467d-95ab-c8f8de4e6b9e
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 734b6d0625cfda79b600a0920ab39bda25ee2e8b
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltsecuritygt-of-ltwsdualhttpbindinggt"></a><span data-ttu-id="a5035-102">&lt;wsDualHttpBinding&gt; &lt;güvenliği&gt;</span><span class="sxs-lookup"><span data-stu-id="a5035-102">&lt;security&gt; of &lt;wsDualHttpBinding&gt;</span></span>
<span data-ttu-id="a5035-103">Güvenlik özelliklerini tanımlayan [ \<wsDualHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="a5035-103">Defines the security capabilities of the [\<wsDualHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span></span>  
  
 <span data-ttu-id="a5035-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="a5035-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="a5035-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="a5035-105">\<bindings></span></span>  
<span data-ttu-id="a5035-106">\<wsDualHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="a5035-106">\<wsDualHttpBinding></span></span>  
<span data-ttu-id="a5035-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="a5035-107">\<binding></span></span>  
<span data-ttu-id="a5035-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="a5035-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5035-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a5035-109">Syntax</span></span>  
  
```xml  
<security mode="Message/None">  
   <message  
      algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
      clientCredentialType="Certificate/IssuedToken/None/UserName/Windows"  
      negotiateServiceCredential="Boolean"/>  
</security>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a5035-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a5035-110">Attributes and Elements</span></span>  
 <span data-ttu-id="a5035-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a5035-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a5035-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a5035-112">Attributes</span></span>  
  
|<span data-ttu-id="a5035-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="a5035-113">Attribute</span></span>|<span data-ttu-id="a5035-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a5035-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a5035-115">mod</span><span class="sxs-lookup"><span data-stu-id="a5035-115">mode</span></span>|<span data-ttu-id="a5035-116">-İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="a5035-116">-   Optional.</span></span> <span data-ttu-id="a5035-117">Uygulanan güvenlik türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="a5035-117">Specifies the type of security that is applied.</span></span> <span data-ttu-id="a5035-118">Varsayılan değer `Message` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="a5035-118">The default value is `Message`.</span></span> <span data-ttu-id="a5035-119">Bu öznitelik türünde <xref:System.ServiceModel.WSDualHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="a5035-119">This attribute is of type <xref:System.ServiceModel.WSDualHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="a5035-120">mod özniteliği</span><span class="sxs-lookup"><span data-stu-id="a5035-120">Mode Attribute</span></span>  
  
|<span data-ttu-id="a5035-121">Değer</span><span class="sxs-lookup"><span data-stu-id="a5035-121">Value</span></span>|<span data-ttu-id="a5035-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a5035-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a5035-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="a5035-123">None</span></span>|<span data-ttu-id="a5035-124">Güvenliği devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="a5035-124">Security is disabled.</span></span>|  
|<span data-ttu-id="a5035-125">İleti</span><span class="sxs-lookup"><span data-stu-id="a5035-125">Message</span></span>|<span data-ttu-id="a5035-126">Güvenlik SOAP ileti güvenliği sağlanır.</span><span class="sxs-lookup"><span data-stu-id="a5035-126">Security is provided using SOAP message security.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a5035-127">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a5035-127">Child Elements</span></span>  
  
|<span data-ttu-id="a5035-128">Öğe</span><span class="sxs-lookup"><span data-stu-id="a5035-128">Element</span></span>|<span data-ttu-id="a5035-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a5035-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a5035-130">\<İleti ></span><span class="sxs-lookup"><span data-stu-id="a5035-130">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wsdualhttpbinding.md)|<span data-ttu-id="a5035-131">İleti düzeyi güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a5035-131">Defines the settings for the message-level security.</span></span> <span data-ttu-id="a5035-132">Bu öğe türünde <xref:System.ServiceModel.MessageSecurityOverHttp>.</span><span class="sxs-lookup"><span data-stu-id="a5035-132">This element is of type <xref:System.ServiceModel.MessageSecurityOverHttp>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a5035-133">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a5035-133">Parent Elements</span></span>  
  
|<span data-ttu-id="a5035-134">Öğe</span><span class="sxs-lookup"><span data-stu-id="a5035-134">Element</span></span>|<span data-ttu-id="a5035-135">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a5035-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a5035-136">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="a5035-136">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="a5035-137">Tüm bağlama özelliklerini tanımlayan [ \<wsDualHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="a5035-137">Defines all binding capabilities of the [\<wsDualHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a5035-138">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a5035-138">Remarks</span></span>  
 <span data-ttu-id="a5035-139">Bir çift bağlama hizmeti istemcinin IP adresini gösterir.</span><span class="sxs-lookup"><span data-stu-id="a5035-139">A dual binding exposes the IP address of the client to the service.</span></span> <span data-ttu-id="a5035-140">İstemci, yalnızca Hizmetleri güvenleri bağladığı emin olmak için güvenlik kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a5035-140">The client should use security to ensure that it only connects to services it trusts.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5035-141">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a5035-141">See Also</span></span>  
 <xref:System.ServiceModel.WSDualHttpSecurity>  
 <xref:System.ServiceModel.BasicHttpSecurity>  
 [<span data-ttu-id="a5035-142">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="a5035-142">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="a5035-143">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="a5035-143">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="a5035-144">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="a5035-144">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="a5035-145">Windows Communication Foundation Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma</span><span class="sxs-lookup"><span data-stu-id="a5035-145">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="a5035-146">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="a5035-146">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
