---
title: <security> / <wsDualHttpBinding>
ms.date: 03/30/2017
ms.assetid: 869c05e7-4ebe-467d-95ab-c8f8de4e6b9e
ms.openlocfilehash: 4969c041678bbf3490975bc0ec53507b6cf762bb
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738609"
---
# <a name="security-of-wsdualhttpbinding"></a><span data-ttu-id="25474-102">\<wsDualHttpBinding \<güvenlik > ></span><span class="sxs-lookup"><span data-stu-id="25474-102">\<security> of \<wsDualHttpBinding></span></span>
<span data-ttu-id="25474-103">[\<wsDualHttpBinding >](wsdualhttpbinding.md)'nin güvenlik yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="25474-103">Defines the security capabilities of the [\<wsDualHttpBinding>](wsdualhttpbinding.md).</span></span>  
  
<span data-ttu-id="25474-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="25474-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="25474-105">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="25474-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="25474-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bağlamaları >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="25474-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="25474-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<wsDualHttpBinding >** ](wsdualhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="25474-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsDualHttpBinding>**](wsdualhttpbinding.md)</span></span>\
<span data-ttu-id="25474-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bağlama >** </span><span class="sxs-lookup"><span data-stu-id="25474-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="25474-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<güvenlik >**</span><span class="sxs-lookup"><span data-stu-id="25474-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25474-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="25474-110">Syntax</span></span>  
  
```xml  
<security mode="Message/None">
  <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           clientCredentialType="Certificate/IssuedToken/None/UserName/Windows"
           negotiateServiceCredential="Boolean"/>
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="25474-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="25474-111">Attributes and Elements</span></span>  
 <span data-ttu-id="25474-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="25474-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="25474-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="25474-113">Attributes</span></span>  
  
|<span data-ttu-id="25474-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="25474-114">Attribute</span></span>|<span data-ttu-id="25474-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="25474-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="25474-116">mod</span><span class="sxs-lookup"><span data-stu-id="25474-116">mode</span></span>|<span data-ttu-id="25474-117">Seçim.</span><span class="sxs-lookup"><span data-stu-id="25474-117">-   Optional.</span></span> <span data-ttu-id="25474-118">Uygulanan güvenlik türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="25474-118">Specifies the type of security that is applied.</span></span> <span data-ttu-id="25474-119">Varsayılan değer `Message` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="25474-119">The default value is `Message`.</span></span> <span data-ttu-id="25474-120">Bu öznitelik <xref:System.ServiceModel.WSDualHttpSecurityMode>türündedir.</span><span class="sxs-lookup"><span data-stu-id="25474-120">This attribute is of type <xref:System.ServiceModel.WSDualHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="25474-121">Mode özniteliği</span><span class="sxs-lookup"><span data-stu-id="25474-121">Mode Attribute</span></span>  
  
|<span data-ttu-id="25474-122">Değer</span><span class="sxs-lookup"><span data-stu-id="25474-122">Value</span></span>|<span data-ttu-id="25474-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="25474-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="25474-124">Yok.</span><span class="sxs-lookup"><span data-stu-id="25474-124">None</span></span>|<span data-ttu-id="25474-125">Güvenlik devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="25474-125">Security is disabled.</span></span>|  
|<span data-ttu-id="25474-126">İleti</span><span class="sxs-lookup"><span data-stu-id="25474-126">Message</span></span>|<span data-ttu-id="25474-127">Güvenlik, SOAP iletisi güvenliği kullanılarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="25474-127">Security is provided using SOAP message security.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="25474-128">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="25474-128">Child Elements</span></span>  
  
|<span data-ttu-id="25474-129">Öğe</span><span class="sxs-lookup"><span data-stu-id="25474-129">Element</span></span>|<span data-ttu-id="25474-130">Açıklama</span><span class="sxs-lookup"><span data-stu-id="25474-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="25474-131">\<ileti ></span><span class="sxs-lookup"><span data-stu-id="25474-131">\<message></span></span>](message-of-wsdualhttpbinding.md)|<span data-ttu-id="25474-132">İleti düzeyinde güvenlik için ayarları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="25474-132">Defines the settings for the message-level security.</span></span> <span data-ttu-id="25474-133">Bu öğe <xref:System.ServiceModel.MessageSecurityOverHttp>türündedir.</span><span class="sxs-lookup"><span data-stu-id="25474-133">This element is of type <xref:System.ServiceModel.MessageSecurityOverHttp>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="25474-134">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="25474-134">Parent Elements</span></span>  
  
|<span data-ttu-id="25474-135">Öğe</span><span class="sxs-lookup"><span data-stu-id="25474-135">Element</span></span>|<span data-ttu-id="25474-136">Açıklama</span><span class="sxs-lookup"><span data-stu-id="25474-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="25474-137">\< bağlama ></span><span class="sxs-lookup"><span data-stu-id="25474-137">\<binding></span></span>](bindings.md)|<span data-ttu-id="25474-138">[\<wsDualHttpBinding >](wsdualhttpbinding.md)'in tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="25474-138">Defines all binding capabilities of the [\<wsDualHttpBinding>](wsdualhttpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="25474-139">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="25474-139">Remarks</span></span>  
 <span data-ttu-id="25474-140">İkili bağlama, istemcinin IP adresini hizmete gösterir.</span><span class="sxs-lookup"><span data-stu-id="25474-140">A dual binding exposes the IP address of the client to the service.</span></span> <span data-ttu-id="25474-141">İstemci, yalnızca güvendiği hizmetlere bağlanmasını sağlamak için güvenliği kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="25474-141">The client should use security to ensure that it only connects to services it trusts.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25474-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="25474-142">See also</span></span>

- <xref:System.ServiceModel.WSDualHttpSecurity>
- <xref:System.ServiceModel.BasicHttpSecurity>
- [<span data-ttu-id="25474-143">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="25474-143">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="25474-144">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="25474-144">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="25474-145">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="25474-145">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="25474-146">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="25474-146">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="25474-147">\< bağlama ></span><span class="sxs-lookup"><span data-stu-id="25474-147">\<binding></span></span>](bindings.md)
