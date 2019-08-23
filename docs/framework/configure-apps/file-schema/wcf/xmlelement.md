---
title: <xmlElement>
ms.date: 03/30/2017
ms.assetid: 395205c2-d8c0-4a5e-90f3-7ce3c085fccd
ms.openlocfilehash: cc178dcc3684ab338282acc369e0ab5c789c15e4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69941432"
---
# <a name="xmlelement"></a><span data-ttu-id="ceab1-101">\<xmlElement ></span><span class="sxs-lookup"><span data-stu-id="ceab1-101">\<xmlElement></span></span>
<span data-ttu-id="ceab1-102">Belirteç istenirken güvenlik belirteci hizmetine ileti gövdesinde gönderilen bir XML öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="ceab1-102">Specifies an XML element that is sent in the message body to the Security Token Service when requesting a token.</span></span>  
  
 <span data-ttu-id="ceab1-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="ceab1-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="ceab1-104">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="ceab1-104">\<bindings></span></span>  
<span data-ttu-id="ceab1-105">\<wsFederatedBinding ></span><span class="sxs-lookup"><span data-stu-id="ceab1-105">\<wsFederatedBinding></span></span>  
<span data-ttu-id="ceab1-106">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="ceab1-106">\<binding></span></span>  
<span data-ttu-id="ceab1-107">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="ceab1-107">\<security></span></span>  
<span data-ttu-id="ceab1-108">\<ileti ></span><span class="sxs-lookup"><span data-stu-id="ceab1-108">\<message></span></span>  
<span data-ttu-id="ceab1-109">\<tokenRequestParameters ></span><span class="sxs-lookup"><span data-stu-id="ceab1-109">\<tokenRequestParameters></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ceab1-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ceab1-110">Syntax</span></span>  
  
```xml  
<tokenRequestParameters>
  <xmlElement xmlElement="String" />
</tokenRequestParameters>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ceab1-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ceab1-111">Attributes and Elements</span></span>  
 <span data-ttu-id="ceab1-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ceab1-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ceab1-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ceab1-113">Attributes</span></span>  
  
|<span data-ttu-id="ceab1-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="ceab1-114">Attribute</span></span>|<span data-ttu-id="ceab1-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ceab1-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ceab1-116">xmlElement</span><span class="sxs-lookup"><span data-stu-id="ceab1-116">xmlElement</span></span>|<span data-ttu-id="ceab1-117">Belirteç istenirken güvenlik belirteci hizmetine ileti gövdesinde gönderilen bir XML öğesini belirten dize.</span><span class="sxs-lookup"><span data-stu-id="ceab1-117">A string specifying an XML element that is sent in the message body to the Security Token Service when requesting a token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ceab1-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ceab1-118">Child Elements</span></span>  
 <span data-ttu-id="ceab1-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="ceab1-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ceab1-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ceab1-120">Parent Elements</span></span>  
  
|<span data-ttu-id="ceab1-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="ceab1-121">Element</span></span>|<span data-ttu-id="ceab1-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ceab1-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ceab1-123">\<tokenRequestParameters></span><span class="sxs-lookup"><span data-stu-id="ceab1-123">\<tokenRequestParameters></span></span>](tokenrequestparameters.md)|<span data-ttu-id="ceab1-124">Belirteç isteği parametrelerinin bir koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="ceab1-124">A collection of token request parameters.</span></span> <span data-ttu-id="ceab1-125">Her parametre bir XML öğesidir.</span><span class="sxs-lookup"><span data-stu-id="ceab1-125">Each parameter is an XML element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ceab1-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ceab1-126">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.TokenRequestParameters%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.TokenRequestParameters%2A>
- [<span data-ttu-id="ceab1-127">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="ceab1-127">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="ceab1-128">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="ceab1-128">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="ceab1-129">Özel Bağlamalarla Güvenlik Özellikleri</span><span class="sxs-lookup"><span data-stu-id="ceab1-129">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="ceab1-130">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="ceab1-130">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="ceab1-131">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="ceab1-131">Bindings</span></span>](../../../wcf/bindings.md)
