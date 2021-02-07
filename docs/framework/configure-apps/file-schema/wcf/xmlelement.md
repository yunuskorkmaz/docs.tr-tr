---
description: 'Hakkında daha fazla bilgi edinin: <xmlElement>'
title: <xmlElement>
ms.date: 03/30/2017
ms.assetid: 395205c2-d8c0-4a5e-90f3-7ce3c085fccd
ms.openlocfilehash: 891f1a95c1f6a79127d48a1572bc805574225530
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99682013"
---
# \<xmlElement>

<span data-ttu-id="9060c-102">Belirteç istenirken güvenlik belirteci hizmetine ileti gövdesinde gönderilen bir XML öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="9060c-102">Specifies an XML element that is sent in the message body to the Security Token Service when requesting a token.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<message>**](message-element-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<tokenRequestParameters>**](tokenrequestparameters.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<xmlElement>**  
  
## <a name="syntax"></a><span data-ttu-id="9060c-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="9060c-103">Syntax</span></span>  
  
```xml  
<tokenRequestParameters>
  <xmlElement xmlElement="String" />
</tokenRequestParameters>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9060c-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="9060c-104">Attributes and Elements</span></span>  

 <span data-ttu-id="9060c-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9060c-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9060c-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="9060c-106">Attributes</span></span>  
  
|<span data-ttu-id="9060c-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="9060c-107">Attribute</span></span>|<span data-ttu-id="9060c-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9060c-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9060c-109">xmlElement</span><span class="sxs-lookup"><span data-stu-id="9060c-109">xmlElement</span></span>|<span data-ttu-id="9060c-110">Belirteç istenirken güvenlik belirteci hizmetine ileti gövdesinde gönderilen bir XML öğesini belirten dize.</span><span class="sxs-lookup"><span data-stu-id="9060c-110">A string specifying an XML element that is sent in the message body to the Security Token Service when requesting a token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9060c-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="9060c-111">Child Elements</span></span>  

 <span data-ttu-id="9060c-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="9060c-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9060c-113">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="9060c-113">Parent Elements</span></span>  
  
|<span data-ttu-id="9060c-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="9060c-114">Element</span></span>|<span data-ttu-id="9060c-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9060c-115">Description</span></span>|  
|-------------|-----------------|  
|[\<tokenRequestParameters>](tokenrequestparameters.md)|<span data-ttu-id="9060c-116">Belirteç isteği parametrelerinin bir koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="9060c-116">A collection of token request parameters.</span></span> <span data-ttu-id="9060c-117">Her parametre bir XML öğesidir.</span><span class="sxs-lookup"><span data-stu-id="9060c-117">Each parameter is an XML element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9060c-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9060c-118">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.TokenRequestParameters%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.TokenRequestParameters%2A>
- [<span data-ttu-id="9060c-119">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="9060c-119">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="9060c-120">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="9060c-120">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="9060c-121">Özel Bağlamalarla Güvenlik Özellikleri</span><span class="sxs-lookup"><span data-stu-id="9060c-121">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="9060c-122">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="9060c-122">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="9060c-123">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="9060c-123">Bindings</span></span>](../../../wcf/bindings.md)
