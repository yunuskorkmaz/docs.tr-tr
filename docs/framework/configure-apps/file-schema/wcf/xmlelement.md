---
title: <xmlElement>
ms.date: 03/30/2017
ms.assetid: 395205c2-d8c0-4a5e-90f3-7ce3c085fccd
ms.openlocfilehash: 841331f233bb8c42c25c88ad8e9b4fb1a86faa76
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398994"
---
# \<xmlElement>
<span data-ttu-id="d3fc9-101">Belirteç istenirken güvenlik belirteci hizmetine ileti gövdesinde gönderilen bir XML öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="d3fc9-101">Specifies an XML element that is sent in the message body to the Security Token Service when requesting a token.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<message>**](message-element-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<tokenRequestParameters>**](tokenrequestparameters.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<xmlElement>**  
  
## <a name="syntax"></a><span data-ttu-id="d3fc9-102">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d3fc9-102">Syntax</span></span>  
  
```xml  
<tokenRequestParameters>
  <xmlElement xmlElement="String" />
</tokenRequestParameters>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d3fc9-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d3fc9-103">Attributes and Elements</span></span>  
 <span data-ttu-id="d3fc9-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d3fc9-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d3fc9-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d3fc9-105">Attributes</span></span>  
  
|<span data-ttu-id="d3fc9-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="d3fc9-106">Attribute</span></span>|<span data-ttu-id="d3fc9-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d3fc9-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d3fc9-108">xmlElement</span><span class="sxs-lookup"><span data-stu-id="d3fc9-108">xmlElement</span></span>|<span data-ttu-id="d3fc9-109">Belirteç istenirken güvenlik belirteci hizmetine ileti gövdesinde gönderilen bir XML öğesini belirten dize.</span><span class="sxs-lookup"><span data-stu-id="d3fc9-109">A string specifying an XML element that is sent in the message body to the Security Token Service when requesting a token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d3fc9-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d3fc9-110">Child Elements</span></span>  
 <span data-ttu-id="d3fc9-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="d3fc9-111">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d3fc9-112">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d3fc9-112">Parent Elements</span></span>  
  
|<span data-ttu-id="d3fc9-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="d3fc9-113">Element</span></span>|<span data-ttu-id="d3fc9-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d3fc9-114">Description</span></span>|  
|-------------|-----------------|  
|[\<tokenRequestParameters>](tokenrequestparameters.md)|<span data-ttu-id="d3fc9-115">Belirteç isteği parametrelerinin bir koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="d3fc9-115">A collection of token request parameters.</span></span> <span data-ttu-id="d3fc9-116">Her parametre bir XML öğesidir.</span><span class="sxs-lookup"><span data-stu-id="d3fc9-116">Each parameter is an XML element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d3fc9-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d3fc9-117">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.TokenRequestParameters%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.TokenRequestParameters%2A>
- [<span data-ttu-id="d3fc9-118">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="d3fc9-118">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="d3fc9-119">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="d3fc9-119">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="d3fc9-120">Özel Bağlamalarla Güvenlik Özellikleri</span><span class="sxs-lookup"><span data-stu-id="d3fc9-120">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="d3fc9-121">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="d3fc9-121">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="d3fc9-122">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="d3fc9-122">Bindings</span></span>](../../../wcf/bindings.md)
