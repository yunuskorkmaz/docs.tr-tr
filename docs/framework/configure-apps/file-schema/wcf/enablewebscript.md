---
title: <enableWebScript>
ms.date: 03/30/2017
ms.assetid: 9c7e96e1-af70-4e6e-ac5c-d67929dddbaa
ms.openlocfilehash: 11378e6cc8cbe8e631fd77ab74c91a616099df52
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91190091"
---
# \<enableWebScript>

<span data-ttu-id="a1145-101">Bu öğe, hizmeti ASP.NET AJAX web sayfalarından kullanmasını olanaklı kılan uç nokta davranışını sağlar.</span><span class="sxs-lookup"><span data-stu-id="a1145-101">This element enables the endpoint behavior that makes it possible to consume the service from ASP.NET AJAX web pages.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<enableWebScript>**  
  
## <a name="syntax"></a><span data-ttu-id="a1145-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="a1145-102">Syntax</span></span>  
  
```xml  
<enableWebScript />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a1145-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a1145-103">Attributes and Elements</span></span>  

 <span data-ttu-id="a1145-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a1145-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a1145-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a1145-105">Attributes</span></span>  

 <span data-ttu-id="a1145-106">Yok.</span><span class="sxs-lookup"><span data-stu-id="a1145-106">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a1145-107">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a1145-107">Child Elements</span></span>  

 <span data-ttu-id="a1145-108">Yok.</span><span class="sxs-lookup"><span data-stu-id="a1145-108">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a1145-109">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a1145-109">Parent Elements</span></span>  
  
|<span data-ttu-id="a1145-110">Öğe</span><span class="sxs-lookup"><span data-stu-id="a1145-110">Element</span></span>|<span data-ttu-id="a1145-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a1145-111">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="a1145-112">Uç nokta davranışları kümesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a1145-112">Specifies the set of endpoint behaviors.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a1145-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a1145-113">Remarks</span></span>  

 <span data-ttu-id="a1145-114">Bu davranış yalnızca [\<webHttpBinding>](webhttpbinding.md) Standart bağlama veya [\<webMessageEncoding>](webmessageencoding.md) bağlama öğesiyle birlikte kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a1145-114">This behavior should only be used in conjunction with either the [\<webHttpBinding>](webhttpbinding.md) standard binding, or the [\<webMessageEncoding>](webmessageencoding.md) binding element.</span></span>  <span data-ttu-id="a1145-115">Bu davranış hakkında daha fazla bilgi için bkz <xref:System.ServiceModel.Description.WebScriptEnablingBehavior> ..</span><span class="sxs-lookup"><span data-stu-id="a1145-115">For more information on this behavior, see <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1145-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a1145-116">See also</span></span>

- <xref:System.ServiceModel.Configuration.WebScriptEnablingElement>
- <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>
- [<span data-ttu-id="a1145-117">AJAX Tümleştirme ve JSON Desteği</span><span class="sxs-lookup"><span data-stu-id="a1145-117">AJAX Integration and JSON Support</span></span>](../../../wcf/feature-details/ajax-integration-and-json-support.md)
- [\<webHttp>](webhttp.md)
