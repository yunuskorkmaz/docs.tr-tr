---
title: <xmlElement>
ms.date: 03/30/2017
ms.assetid: 395205c2-d8c0-4a5e-90f3-7ce3c085fccd
ms.openlocfilehash: a72641b438801cfd493c322297e7c384e83e687c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59230505"
---
# <a name="xmlelement"></a><span data-ttu-id="4b2c7-101">\<xmlElement ></span><span class="sxs-lookup"><span data-stu-id="4b2c7-101">\<xmlElement></span></span>
<span data-ttu-id="4b2c7-102">İleti gövdesini güvenlik belirteci hizmeti için bir belirteç isterken gönderilen bir XML öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="4b2c7-102">Specifies an XML element that is sent in the message body to the Security Token Service when requesting a token.</span></span>  
  
 <span data-ttu-id="4b2c7-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="4b2c7-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="4b2c7-104">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="4b2c7-104">\<bindings></span></span>  
<span data-ttu-id="4b2c7-105">\<wsFederatedBinding ></span><span class="sxs-lookup"><span data-stu-id="4b2c7-105">\<wsFederatedBinding></span></span>  
<span data-ttu-id="4b2c7-106">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="4b2c7-106">\<binding></span></span>  
<span data-ttu-id="4b2c7-107">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="4b2c7-107">\<security></span></span>  
<span data-ttu-id="4b2c7-108">\<İleti ></span><span class="sxs-lookup"><span data-stu-id="4b2c7-108">\<message></span></span>  
<span data-ttu-id="4b2c7-109">\<tokenRequestParameters ></span><span class="sxs-lookup"><span data-stu-id="4b2c7-109">\<tokenRequestParameters></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b2c7-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4b2c7-110">Syntax</span></span>  
  
```xml  
<tokenRequestParameters>
  <xmlElement xmlElement="String" />
</tokenRequestParameters>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4b2c7-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="4b2c7-111">Attributes and Elements</span></span>  
 <span data-ttu-id="4b2c7-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4b2c7-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4b2c7-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="4b2c7-113">Attributes</span></span>  
  
|<span data-ttu-id="4b2c7-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="4b2c7-114">Attribute</span></span>|<span data-ttu-id="4b2c7-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4b2c7-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4b2c7-116">xmlElement</span><span class="sxs-lookup"><span data-stu-id="4b2c7-116">xmlElement</span></span>|<span data-ttu-id="4b2c7-117">İleti gövdesini güvenlik belirteci hizmeti için bir belirteç isterken gönderilen bir XML öğesi belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="4b2c7-117">A string specifying an XML element that is sent in the message body to the Security Token Service when requesting a token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4b2c7-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="4b2c7-118">Child Elements</span></span>  
 <span data-ttu-id="4b2c7-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="4b2c7-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4b2c7-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="4b2c7-120">Parent Elements</span></span>  
  
|<span data-ttu-id="4b2c7-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="4b2c7-121">Element</span></span>|<span data-ttu-id="4b2c7-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4b2c7-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4b2c7-123">\<tokenRequestParameters ></span><span class="sxs-lookup"><span data-stu-id="4b2c7-123">\<tokenRequestParameters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/tokenrequestparameters.md)|<span data-ttu-id="4b2c7-124">Belirteç isteği parametreleri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="4b2c7-124">A collection of token request parameters.</span></span> <span data-ttu-id="4b2c7-125">Her bir XML öğesi parametredir.</span><span class="sxs-lookup"><span data-stu-id="4b2c7-125">Each parameter is an XML element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4b2c7-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4b2c7-126">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.TokenRequestParameters%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.TokenRequestParameters%2A>
- [<span data-ttu-id="4b2c7-127">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="4b2c7-127">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="4b2c7-128">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="4b2c7-128">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="4b2c7-129">Özel Bağlamalarla Güvenlik Özellikleri</span><span class="sxs-lookup"><span data-stu-id="4b2c7-129">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="4b2c7-130">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="4b2c7-130">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="4b2c7-131">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="4b2c7-131">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
