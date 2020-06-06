---
title: <security> / <wsDualHttpBinding>
ms.date: 03/30/2017
ms.assetid: 869c05e7-4ebe-467d-95ab-c8f8de4e6b9e
ms.openlocfilehash: 4969c041678bbf3490975bc0ec53507b6cf762bb
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73738609"
---
# <a name="security-of-wsdualhttpbinding"></a><span data-ttu-id="78864-102">\<security> / \<wsDualHttpBinding></span><span class="sxs-lookup"><span data-stu-id="78864-102">\<security> of \<wsDualHttpBinding></span></span>
<span data-ttu-id="78864-103">Uygulamasının güvenlik yeteneklerini tanımlar [\<wsDualHttpBinding>](wsdualhttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="78864-103">Defines the security capabilities of the [\<wsDualHttpBinding>](wsdualhttpbinding.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsDualHttpBinding>**](wsdualhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="78864-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="78864-104">Syntax</span></span>  
  
```xml  
<security mode="Message/None">
  <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           clientCredentialType="Certificate/IssuedToken/None/UserName/Windows"
           negotiateServiceCredential="Boolean"/>
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="78864-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="78864-105">Attributes and Elements</span></span>  
 <span data-ttu-id="78864-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="78864-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="78864-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="78864-107">Attributes</span></span>  
  
|<span data-ttu-id="78864-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="78864-108">Attribute</span></span>|<span data-ttu-id="78864-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="78864-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="78864-110">mod</span><span class="sxs-lookup"><span data-stu-id="78864-110">mode</span></span>|<span data-ttu-id="78864-111">Seçim.</span><span class="sxs-lookup"><span data-stu-id="78864-111">-   Optional.</span></span> <span data-ttu-id="78864-112">Uygulanan güvenlik türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="78864-112">Specifies the type of security that is applied.</span></span> <span data-ttu-id="78864-113">Varsayılan değer: `Message`.</span><span class="sxs-lookup"><span data-stu-id="78864-113">The default value is `Message`.</span></span> <span data-ttu-id="78864-114">Bu öznitelik türü <xref:System.ServiceModel.WSDualHttpSecurityMode> .</span><span class="sxs-lookup"><span data-stu-id="78864-114">This attribute is of type <xref:System.ServiceModel.WSDualHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="78864-115">Mode özniteliği</span><span class="sxs-lookup"><span data-stu-id="78864-115">Mode Attribute</span></span>  
  
|<span data-ttu-id="78864-116">Değer</span><span class="sxs-lookup"><span data-stu-id="78864-116">Value</span></span>|<span data-ttu-id="78864-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="78864-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="78864-118">Yok</span><span class="sxs-lookup"><span data-stu-id="78864-118">None</span></span>|<span data-ttu-id="78864-119">Güvenlik devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="78864-119">Security is disabled.</span></span>|  
|<span data-ttu-id="78864-120">İleti</span><span class="sxs-lookup"><span data-stu-id="78864-120">Message</span></span>|<span data-ttu-id="78864-121">Güvenlik, SOAP iletisi güvenliği kullanılarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="78864-121">Security is provided using SOAP message security.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="78864-122">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="78864-122">Child Elements</span></span>  
  
|<span data-ttu-id="78864-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="78864-123">Element</span></span>|<span data-ttu-id="78864-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="78864-124">Description</span></span>|  
|-------------|-----------------|  
|[\<message>](message-of-wsdualhttpbinding.md)|<span data-ttu-id="78864-125">İleti düzeyinde güvenlik için ayarları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="78864-125">Defines the settings for the message-level security.</span></span> <span data-ttu-id="78864-126">Bu öğe türündedir <xref:System.ServiceModel.MessageSecurityOverHttp> .</span><span class="sxs-lookup"><span data-stu-id="78864-126">This element is of type <xref:System.ServiceModel.MessageSecurityOverHttp>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="78864-127">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="78864-127">Parent Elements</span></span>  
  
|<span data-ttu-id="78864-128">Öğe</span><span class="sxs-lookup"><span data-stu-id="78864-128">Element</span></span>|<span data-ttu-id="78864-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="78864-129">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="78864-130">Öğesinin tüm bağlama yeteneklerini tanımlar [\<wsDualHttpBinding>](wsdualhttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="78864-130">Defines all binding capabilities of the [\<wsDualHttpBinding>](wsdualhttpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="78864-131">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="78864-131">Remarks</span></span>  
 <span data-ttu-id="78864-132">İkili bağlama, istemcinin IP adresini hizmete gösterir.</span><span class="sxs-lookup"><span data-stu-id="78864-132">A dual binding exposes the IP address of the client to the service.</span></span> <span data-ttu-id="78864-133">İstemci, yalnızca güvendiği hizmetlere bağlanmasını sağlamak için güvenliği kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="78864-133">The client should use security to ensure that it only connects to services it trusts.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78864-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="78864-134">See also</span></span>

- <xref:System.ServiceModel.WSDualHttpSecurity>
- <xref:System.ServiceModel.BasicHttpSecurity>
- [<span data-ttu-id="78864-135">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="78864-135">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="78864-136">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="78864-136">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="78864-137">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="78864-137">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="78864-138">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="78864-138">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
