---
description: 'Hakkında daha fazla bilgi edinin: <enableWebScript>'
title: <enableWebScript>
ms.date: 03/30/2017
ms.assetid: 9c7e96e1-af70-4e6e-ac5c-d67929dddbaa
ms.openlocfilehash: f357bf1ab726cd434a16b2daa9c8115afe7d4430
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99725889"
---
# \<enableWebScript>

<span data-ttu-id="cee83-102">Bu öğe, hizmeti ASP.NET AJAX web sayfalarından kullanmasını olanaklı kılan uç nokta davranışını sağlar.</span><span class="sxs-lookup"><span data-stu-id="cee83-102">This element enables the endpoint behavior that makes it possible to consume the service from ASP.NET AJAX web pages.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<enableWebScript>**  
  
## <a name="syntax"></a><span data-ttu-id="cee83-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="cee83-103">Syntax</span></span>  
  
```xml  
<enableWebScript />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cee83-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="cee83-104">Attributes and Elements</span></span>  

 <span data-ttu-id="cee83-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="cee83-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cee83-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="cee83-106">Attributes</span></span>  

 <span data-ttu-id="cee83-107">Yok.</span><span class="sxs-lookup"><span data-stu-id="cee83-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="cee83-108">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="cee83-108">Child Elements</span></span>  

 <span data-ttu-id="cee83-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="cee83-109">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cee83-110">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="cee83-110">Parent Elements</span></span>  
  
|<span data-ttu-id="cee83-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="cee83-111">Element</span></span>|<span data-ttu-id="cee83-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cee83-112">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="cee83-113">Uç nokta davranışları kümesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="cee83-113">Specifies the set of endpoint behaviors.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cee83-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cee83-114">Remarks</span></span>  

 <span data-ttu-id="cee83-115">Bu davranış yalnızca [\<webHttpBinding>](webhttpbinding.md) Standart bağlama veya [\<webMessageEncoding>](webmessageencoding.md) bağlama öğesiyle birlikte kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="cee83-115">This behavior should only be used in conjunction with either the [\<webHttpBinding>](webhttpbinding.md) standard binding, or the [\<webMessageEncoding>](webmessageencoding.md) binding element.</span></span>  <span data-ttu-id="cee83-116">Bu davranış hakkında daha fazla bilgi için bkz <xref:System.ServiceModel.Description.WebScriptEnablingBehavior> ..</span><span class="sxs-lookup"><span data-stu-id="cee83-116">For more information on this behavior, see <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cee83-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cee83-117">See also</span></span>

- <xref:System.ServiceModel.Configuration.WebScriptEnablingElement>
- <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>
- [<span data-ttu-id="cee83-118">AJAX Tümleştirme ve JSON Desteği</span><span class="sxs-lookup"><span data-stu-id="cee83-118">AJAX Integration and JSON Support</span></span>](../../../wcf/feature-details/ajax-integration-and-json-support.md)
- [\<webHttp>](webhttp.md)
