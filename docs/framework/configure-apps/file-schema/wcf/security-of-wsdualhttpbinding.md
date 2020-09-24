---
title: <security> / <wsDualHttpBinding>
ms.date: 03/30/2017
ms.assetid: 869c05e7-4ebe-467d-95ab-c8f8de4e6b9e
ms.openlocfilehash: 7398cd538bb240e78413575f7c28abe7f797d05c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91162211"
---
# <a name="security-of-wsdualhttpbinding"></a><span data-ttu-id="7c8d9-102">\<security> / \<wsDualHttpBinding></span><span class="sxs-lookup"><span data-stu-id="7c8d9-102">\<security> of \<wsDualHttpBinding></span></span>

<span data-ttu-id="7c8d9-103">Uygulamasının güvenlik yeteneklerini tanımlar [\<wsDualHttpBinding>](wsdualhttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="7c8d9-103">Defines the security capabilities of the [\<wsDualHttpBinding>](wsdualhttpbinding.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsDualHttpBinding>**](wsdualhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="7c8d9-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="7c8d9-104">Syntax</span></span>  
  
```xml  
<security mode="Message/None">
  <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           clientCredentialType="Certificate/IssuedToken/None/UserName/Windows"
           negotiateServiceCredential="Boolean"/>
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7c8d9-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="7c8d9-105">Attributes and Elements</span></span>  

 <span data-ttu-id="7c8d9-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7c8d9-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7c8d9-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="7c8d9-107">Attributes</span></span>  
  
|<span data-ttu-id="7c8d9-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="7c8d9-108">Attribute</span></span>|<span data-ttu-id="7c8d9-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7c8d9-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7c8d9-110">mod</span><span class="sxs-lookup"><span data-stu-id="7c8d9-110">mode</span></span>|<span data-ttu-id="7c8d9-111">Seçim.</span><span class="sxs-lookup"><span data-stu-id="7c8d9-111">-   Optional.</span></span> <span data-ttu-id="7c8d9-112">Uygulanan güvenlik türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="7c8d9-112">Specifies the type of security that is applied.</span></span> <span data-ttu-id="7c8d9-113">Varsayılan değer: `Message`.</span><span class="sxs-lookup"><span data-stu-id="7c8d9-113">The default value is `Message`.</span></span> <span data-ttu-id="7c8d9-114">Bu öznitelik türü <xref:System.ServiceModel.WSDualHttpSecurityMode> .</span><span class="sxs-lookup"><span data-stu-id="7c8d9-114">This attribute is of type <xref:System.ServiceModel.WSDualHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="7c8d9-115">Mode özniteliği</span><span class="sxs-lookup"><span data-stu-id="7c8d9-115">Mode Attribute</span></span>  
  
|<span data-ttu-id="7c8d9-116">Değer</span><span class="sxs-lookup"><span data-stu-id="7c8d9-116">Value</span></span>|<span data-ttu-id="7c8d9-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7c8d9-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="7c8d9-118">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="7c8d9-118">None</span></span>|<span data-ttu-id="7c8d9-119">Güvenlik devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="7c8d9-119">Security is disabled.</span></span>|  
|<span data-ttu-id="7c8d9-120">İleti</span><span class="sxs-lookup"><span data-stu-id="7c8d9-120">Message</span></span>|<span data-ttu-id="7c8d9-121">Güvenlik, SOAP iletisi güvenliği kullanılarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="7c8d9-121">Security is provided using SOAP message security.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7c8d9-122">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="7c8d9-122">Child Elements</span></span>  
  
|<span data-ttu-id="7c8d9-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="7c8d9-123">Element</span></span>|<span data-ttu-id="7c8d9-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7c8d9-124">Description</span></span>|  
|-------------|-----------------|  
|[\<message>](message-of-wsdualhttpbinding.md)|<span data-ttu-id="7c8d9-125">İleti düzeyinde güvenlik için ayarları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="7c8d9-125">Defines the settings for the message-level security.</span></span> <span data-ttu-id="7c8d9-126">Bu öğe türündedir <xref:System.ServiceModel.MessageSecurityOverHttp> .</span><span class="sxs-lookup"><span data-stu-id="7c8d9-126">This element is of type <xref:System.ServiceModel.MessageSecurityOverHttp>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7c8d9-127">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="7c8d9-127">Parent Elements</span></span>  
  
|<span data-ttu-id="7c8d9-128">Öğe</span><span class="sxs-lookup"><span data-stu-id="7c8d9-128">Element</span></span>|<span data-ttu-id="7c8d9-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7c8d9-129">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="7c8d9-130">Öğesinin tüm bağlama yeteneklerini tanımlar [\<wsDualHttpBinding>](wsdualhttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="7c8d9-130">Defines all binding capabilities of the [\<wsDualHttpBinding>](wsdualhttpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7c8d9-131">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7c8d9-131">Remarks</span></span>  

 <span data-ttu-id="7c8d9-132">İkili bağlama, istemcinin IP adresini hizmete gösterir.</span><span class="sxs-lookup"><span data-stu-id="7c8d9-132">A dual binding exposes the IP address of the client to the service.</span></span> <span data-ttu-id="7c8d9-133">İstemci, yalnızca güvendiği hizmetlere bağlanmasını sağlamak için güvenliği kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7c8d9-133">The client should use security to ensure that it only connects to services it trusts.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c8d9-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7c8d9-134">See also</span></span>

- <xref:System.ServiceModel.WSDualHttpSecurity>
- <xref:System.ServiceModel.BasicHttpSecurity>
- [<span data-ttu-id="7c8d9-135">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="7c8d9-135">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="7c8d9-136">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="7c8d9-136">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="7c8d9-137">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="7c8d9-137">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="7c8d9-138">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="7c8d9-138">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
