---
title: <xmlElement>
ms.date: 03/30/2017
ms.assetid: 395205c2-d8c0-4a5e-90f3-7ce3c085fccd
ms.openlocfilehash: 841331f233bb8c42c25c88ad8e9b4fb1a86faa76
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398994"
---
# <a name="xmlelement"></a><span data-ttu-id="dd44c-101">\<xmlElement ></span><span class="sxs-lookup"><span data-stu-id="dd44c-101">\<xmlElement></span></span>
<span data-ttu-id="dd44c-102">Belirteç istenirken güvenlik belirteci hizmetine ileti gövdesinde gönderilen bir XML öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="dd44c-102">Specifies an XML element that is sent in the message body to the Security Token Service when requesting a token.</span></span>  
  
<span data-ttu-id="dd44c-103">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="dd44c-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="dd44c-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="dd44c-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="dd44c-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bağlama >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="dd44c-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="dd44c-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<wsFederationHttpBinding >** ](wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="dd44c-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="dd44c-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bağlama >** </span><span class="sxs-lookup"><span data-stu-id="dd44c-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="dd44c-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Güvenlik >** ](security-of-wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="dd44c-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="dd44c-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<ileti >** ](message-element-of-wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="dd44c-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<message>**](message-element-of-wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="dd44c-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<tokenRequestParameters >** ](tokenrequestparameters.md)</span><span class="sxs-lookup"><span data-stu-id="dd44c-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<tokenRequestParameters>**](tokenrequestparameters.md)</span></span>\
<span data-ttu-id="dd44c-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<xmlElement >**</span><span class="sxs-lookup"><span data-stu-id="dd44c-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<xmlElement>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd44c-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dd44c-112">Syntax</span></span>  
  
```xml  
<tokenRequestParameters>
  <xmlElement xmlElement="String" />
</tokenRequestParameters>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dd44c-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="dd44c-113">Attributes and Elements</span></span>  
 <span data-ttu-id="dd44c-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="dd44c-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dd44c-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="dd44c-115">Attributes</span></span>  
  
|<span data-ttu-id="dd44c-116">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="dd44c-116">Attribute</span></span>|<span data-ttu-id="dd44c-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dd44c-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="dd44c-118">xmlElement</span><span class="sxs-lookup"><span data-stu-id="dd44c-118">xmlElement</span></span>|<span data-ttu-id="dd44c-119">Belirteç istenirken güvenlik belirteci hizmetine ileti gövdesinde gönderilen bir XML öğesini belirten dize.</span><span class="sxs-lookup"><span data-stu-id="dd44c-119">A string specifying an XML element that is sent in the message body to the Security Token Service when requesting a token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dd44c-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="dd44c-120">Child Elements</span></span>  
 <span data-ttu-id="dd44c-121">Yok.</span><span class="sxs-lookup"><span data-stu-id="dd44c-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="dd44c-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="dd44c-122">Parent Elements</span></span>  
  
|<span data-ttu-id="dd44c-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="dd44c-123">Element</span></span>|<span data-ttu-id="dd44c-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dd44c-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dd44c-125">\<tokenRequestParameters></span><span class="sxs-lookup"><span data-stu-id="dd44c-125">\<tokenRequestParameters></span></span>](tokenrequestparameters.md)|<span data-ttu-id="dd44c-126">Belirteç isteği parametrelerinin bir koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="dd44c-126">A collection of token request parameters.</span></span> <span data-ttu-id="dd44c-127">Her parametre bir XML öğesidir.</span><span class="sxs-lookup"><span data-stu-id="dd44c-127">Each parameter is an XML element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dd44c-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dd44c-128">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.TokenRequestParameters%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.TokenRequestParameters%2A>
- [<span data-ttu-id="dd44c-129">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="dd44c-129">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="dd44c-130">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="dd44c-130">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="dd44c-131">Özel Bağlamalarla Güvenlik Özellikleri</span><span class="sxs-lookup"><span data-stu-id="dd44c-131">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="dd44c-132">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="dd44c-132">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="dd44c-133">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="dd44c-133">Bindings</span></span>](../../../wcf/bindings.md)
