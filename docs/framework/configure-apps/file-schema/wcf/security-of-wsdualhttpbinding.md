---
description: 'Hakkında daha fazla bilgi <security> edinin: <wsDualHttpBinding>'
title: <security> / <wsDualHttpBinding>
ms.date: 03/30/2017
ms.assetid: 869c05e7-4ebe-467d-95ab-c8f8de4e6b9e
ms.openlocfilehash: 6d2e87912aef6114d7dcb99b82e4a7804317b28a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99683040"
---
# <a name="security-of-wsdualhttpbinding"></a><span data-ttu-id="dd187-103">\<security> / \<wsDualHttpBinding></span><span class="sxs-lookup"><span data-stu-id="dd187-103">\<security> of \<wsDualHttpBinding></span></span>

<span data-ttu-id="dd187-104">Uygulamasının güvenlik yeteneklerini tanımlar [\<wsDualHttpBinding>](wsdualhttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="dd187-104">Defines the security capabilities of the [\<wsDualHttpBinding>](wsdualhttpbinding.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsDualHttpBinding>**](wsdualhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="dd187-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="dd187-105">Syntax</span></span>  
  
```xml  
<security mode="Message/None">
  <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           clientCredentialType="Certificate/IssuedToken/None/UserName/Windows"
           negotiateServiceCredential="Boolean"/>
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dd187-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="dd187-106">Attributes and Elements</span></span>  

 <span data-ttu-id="dd187-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="dd187-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dd187-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="dd187-108">Attributes</span></span>  
  
|<span data-ttu-id="dd187-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="dd187-109">Attribute</span></span>|<span data-ttu-id="dd187-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dd187-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="dd187-111">mod</span><span class="sxs-lookup"><span data-stu-id="dd187-111">mode</span></span>|<span data-ttu-id="dd187-112">Seçim.</span><span class="sxs-lookup"><span data-stu-id="dd187-112">-   Optional.</span></span> <span data-ttu-id="dd187-113">Uygulanan güvenlik türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="dd187-113">Specifies the type of security that is applied.</span></span> <span data-ttu-id="dd187-114">`Message` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="dd187-114">The default value is `Message`.</span></span> <span data-ttu-id="dd187-115">Bu öznitelik türü <xref:System.ServiceModel.WSDualHttpSecurityMode> .</span><span class="sxs-lookup"><span data-stu-id="dd187-115">This attribute is of type <xref:System.ServiceModel.WSDualHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="dd187-116">Mode özniteliği</span><span class="sxs-lookup"><span data-stu-id="dd187-116">Mode Attribute</span></span>  
  
|<span data-ttu-id="dd187-117">Değer</span><span class="sxs-lookup"><span data-stu-id="dd187-117">Value</span></span>|<span data-ttu-id="dd187-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dd187-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="dd187-119">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="dd187-119">None</span></span>|<span data-ttu-id="dd187-120">Güvenlik devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="dd187-120">Security is disabled.</span></span>|  
|<span data-ttu-id="dd187-121">İleti</span><span class="sxs-lookup"><span data-stu-id="dd187-121">Message</span></span>|<span data-ttu-id="dd187-122">Güvenlik, SOAP iletisi güvenliği kullanılarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="dd187-122">Security is provided using SOAP message security.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dd187-123">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="dd187-123">Child Elements</span></span>  
  
|<span data-ttu-id="dd187-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="dd187-124">Element</span></span>|<span data-ttu-id="dd187-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dd187-125">Description</span></span>|  
|-------------|-----------------|  
|[\<message>](message-of-wsdualhttpbinding.md)|<span data-ttu-id="dd187-126">İleti düzeyinde güvenlik için ayarları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="dd187-126">Defines the settings for the message-level security.</span></span> <span data-ttu-id="dd187-127">Bu öğe türündedir <xref:System.ServiceModel.MessageSecurityOverHttp> .</span><span class="sxs-lookup"><span data-stu-id="dd187-127">This element is of type <xref:System.ServiceModel.MessageSecurityOverHttp>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="dd187-128">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="dd187-128">Parent Elements</span></span>  
  
|<span data-ttu-id="dd187-129">Öğe</span><span class="sxs-lookup"><span data-stu-id="dd187-129">Element</span></span>|<span data-ttu-id="dd187-130">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dd187-130">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="dd187-131">Öğesinin tüm bağlama yeteneklerini tanımlar [\<wsDualHttpBinding>](wsdualhttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="dd187-131">Defines all binding capabilities of the [\<wsDualHttpBinding>](wsdualhttpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dd187-132">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dd187-132">Remarks</span></span>  

 <span data-ttu-id="dd187-133">İkili bağlama, istemcinin IP adresini hizmete gösterir.</span><span class="sxs-lookup"><span data-stu-id="dd187-133">A dual binding exposes the IP address of the client to the service.</span></span> <span data-ttu-id="dd187-134">İstemci, yalnızca güvendiği hizmetlere bağlanmasını sağlamak için güvenliği kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="dd187-134">The client should use security to ensure that it only connects to services it trusts.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd187-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dd187-135">See also</span></span>

- <xref:System.ServiceModel.WSDualHttpSecurity>
- <xref:System.ServiceModel.BasicHttpSecurity>
- [<span data-ttu-id="dd187-136">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="dd187-136">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="dd187-137">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="dd187-137">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="dd187-138">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="dd187-138">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="dd187-139">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="dd187-139">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
