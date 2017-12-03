---
title: '&lt;xmlElement&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 395205c2-d8c0-4a5e-90f3-7ce3c085fccd
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b36eb762de3864eb786d0b7157d316ab071dc2fa
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltxmlelementgt"></a><span data-ttu-id="b96c8-102">&lt;xmlElement&gt;</span><span class="sxs-lookup"><span data-stu-id="b96c8-102">&lt;xmlElement&gt;</span></span>
<span data-ttu-id="b96c8-103">İleti gövdesinde güvenlik belirteci hizmeti için bir belirteç isterken gönderilen bir XML öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="b96c8-103">Specifies an XML element that is sent in the message body to the Security Token Service when requesting a token.</span></span>  
  
 <span data-ttu-id="b96c8-104">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="b96c8-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="b96c8-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="b96c8-105">\<bindings></span></span>  
<span data-ttu-id="b96c8-106">\<wsFederatedBinding ></span><span class="sxs-lookup"><span data-stu-id="b96c8-106">\<wsFederatedBinding></span></span>  
<span data-ttu-id="b96c8-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="b96c8-107">\<binding></span></span>  
<span data-ttu-id="b96c8-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="b96c8-108">\<security></span></span>  
<span data-ttu-id="b96c8-109">\<İleti ></span><span class="sxs-lookup"><span data-stu-id="b96c8-109">\<message></span></span>  
<span data-ttu-id="b96c8-110">\<tokenRequestParameters ></span><span class="sxs-lookup"><span data-stu-id="b96c8-110">\<tokenRequestParameters></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b96c8-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b96c8-111">Syntax</span></span>  
  
```xml  
<tokenRequestParameters>  
      <xmlElement xmlElement="String" />  
</tokenRequestParameters>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b96c8-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="b96c8-112">Attributes and Elements</span></span>  
 <span data-ttu-id="b96c8-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b96c8-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b96c8-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b96c8-114">Attributes</span></span>  
  
|<span data-ttu-id="b96c8-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="b96c8-115">Attribute</span></span>|<span data-ttu-id="b96c8-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b96c8-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b96c8-117">xmlElement</span><span class="sxs-lookup"><span data-stu-id="b96c8-117">xmlElement</span></span>|<span data-ttu-id="b96c8-118">İleti gövdesinde güvenlik belirteci hizmeti için bir belirteç isterken gönderilen bir XML öğesi belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="b96c8-118">A string specifying an XML element that is sent in the message body to the Security Token Service when requesting a token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b96c8-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="b96c8-119">Child Elements</span></span>  
 <span data-ttu-id="b96c8-120">Yok.</span><span class="sxs-lookup"><span data-stu-id="b96c8-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b96c8-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="b96c8-121">Parent Elements</span></span>  
  
|<span data-ttu-id="b96c8-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="b96c8-122">Element</span></span>|<span data-ttu-id="b96c8-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b96c8-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b96c8-124">\<tokenRequestParameters ></span><span class="sxs-lookup"><span data-stu-id="b96c8-124">\<tokenRequestParameters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/tokenrequestparameters.md)|<span data-ttu-id="b96c8-125">Belirteç isteği parametreleri topluluğu.</span><span class="sxs-lookup"><span data-stu-id="b96c8-125">A collection of token request parameters.</span></span> <span data-ttu-id="b96c8-126">Her bir XML öğesi parametresidir.</span><span class="sxs-lookup"><span data-stu-id="b96c8-126">Each parameter is an XML element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b96c8-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b96c8-127">See Also</span></span>  
 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.TokenRequestParameters%2A>  
 <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.TokenRequestParameters%2A>  
 [<span data-ttu-id="b96c8-128">Hizmet kimliği ve kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="b96c8-128">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="b96c8-129">Federasyon ve verilen belirteçler</span><span class="sxs-lookup"><span data-stu-id="b96c8-129">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="b96c8-130">Özel bağlamalarla güvenlik özellikleri</span><span class="sxs-lookup"><span data-stu-id="b96c8-130">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
 [<span data-ttu-id="b96c8-131">Federasyon ve verilen belirteçler</span><span class="sxs-lookup"><span data-stu-id="b96c8-131">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="b96c8-132">Bağlamaları</span><span class="sxs-lookup"><span data-stu-id="b96c8-132">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
