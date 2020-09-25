---
title: <xmlElement>
ms.date: 03/30/2017
ms.assetid: 395205c2-d8c0-4a5e-90f3-7ce3c085fccd
ms.openlocfilehash: 0ab7fbd64cc92e940617f5334eeb16fcb3a50c4a
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91181241"
---
# \<xmlElement>

<span data-ttu-id="fcc31-101">Belirteç istenirken güvenlik belirteci hizmetine ileti gövdesinde gönderilen bir XML öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="fcc31-101">Specifies an XML element that is sent in the message body to the Security Token Service when requesting a token.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<message>**](message-element-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<tokenRequestParameters>**](tokenrequestparameters.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<xmlElement>**  
  
## <a name="syntax"></a><span data-ttu-id="fcc31-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="fcc31-102">Syntax</span></span>  
  
```xml  
<tokenRequestParameters>
  <xmlElement xmlElement="String" />
</tokenRequestParameters>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fcc31-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="fcc31-103">Attributes and Elements</span></span>  

 <span data-ttu-id="fcc31-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="fcc31-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fcc31-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="fcc31-105">Attributes</span></span>  
  
|<span data-ttu-id="fcc31-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="fcc31-106">Attribute</span></span>|<span data-ttu-id="fcc31-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fcc31-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fcc31-108">xmlElement</span><span class="sxs-lookup"><span data-stu-id="fcc31-108">xmlElement</span></span>|<span data-ttu-id="fcc31-109">Belirteç istenirken güvenlik belirteci hizmetine ileti gövdesinde gönderilen bir XML öğesini belirten dize.</span><span class="sxs-lookup"><span data-stu-id="fcc31-109">A string specifying an XML element that is sent in the message body to the Security Token Service when requesting a token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fcc31-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="fcc31-110">Child Elements</span></span>  

 <span data-ttu-id="fcc31-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="fcc31-111">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fcc31-112">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="fcc31-112">Parent Elements</span></span>  
  
|<span data-ttu-id="fcc31-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="fcc31-113">Element</span></span>|<span data-ttu-id="fcc31-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fcc31-114">Description</span></span>|  
|-------------|-----------------|  
|[\<tokenRequestParameters>](tokenrequestparameters.md)|<span data-ttu-id="fcc31-115">Belirteç isteği parametrelerinin bir koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="fcc31-115">A collection of token request parameters.</span></span> <span data-ttu-id="fcc31-116">Her parametre bir XML öğesidir.</span><span class="sxs-lookup"><span data-stu-id="fcc31-116">Each parameter is an XML element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fcc31-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fcc31-117">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.TokenRequestParameters%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.TokenRequestParameters%2A>
- [<span data-ttu-id="fcc31-118">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="fcc31-118">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="fcc31-119">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="fcc31-119">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="fcc31-120">Özel Bağlamalarla Güvenlik Özellikleri</span><span class="sxs-lookup"><span data-stu-id="fcc31-120">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="fcc31-121">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="fcc31-121">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="fcc31-122">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="fcc31-122">Bindings</span></span>](../../../wcf/bindings.md)
