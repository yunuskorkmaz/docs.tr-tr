---
description: 'Hakkında daha fazla bilgi edinin: <webHttp>'
title: <webHttp>
ms.date: 03/30/2017
ms.assetid: 1f9d0754-d41e-44ce-a298-e51cb3096c64
ms.openlocfilehash: acd8d77e00828d132d076c867ff3164ca1ba7230
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99664385"
---
# \<webHttp>

<span data-ttu-id="fbf23-102">Bu öğe, <xref:System.ServiceModel.Description.WebHttpBehavior> yapılandırma yoluyla bir uç nokta üzerinde belirtir.</span><span class="sxs-lookup"><span data-stu-id="fbf23-102">This element specifies the <xref:System.ServiceModel.Description.WebHttpBehavior> on an endpoint through configuration.</span></span> <span data-ttu-id="fbf23-103">Bu davranış, [\<webHttpBinding>](webhttpbinding.md) Standart bağlama birlikte kullanıldığında, bir Windows Communication Foundation (WCF) hizmeti Için Web programlama modeline izin vermez.</span><span class="sxs-lookup"><span data-stu-id="fbf23-103">This behavior, when used in conjunction with the [\<webHttpBinding>](webhttpbinding.md) standard binding, enables the Web programming model for a Windows Communication Foundation (WCF) service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webHttp>**  
  
## <a name="syntax"></a><span data-ttu-id="fbf23-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="fbf23-104">Syntax</span></span>  
  
```xml  
<webHttp />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fbf23-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="fbf23-105">Attributes and Elements</span></span>  

 <span data-ttu-id="fbf23-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="fbf23-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fbf23-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="fbf23-107">Attributes</span></span>  
  
|<span data-ttu-id="fbf23-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="fbf23-108">Attribute</span></span>|<span data-ttu-id="fbf23-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fbf23-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fbf23-110">automaticFormatSelectionEnabled etkin</span><span class="sxs-lookup"><span data-stu-id="fbf23-110">automaticFormatSelectionEnabled</span></span>|<span data-ttu-id="fbf23-111">Bu özellik olarak ayarlandığında `true` , WCF altyapısı kullanılacak en iyi biçimi belirler.</span><span class="sxs-lookup"><span data-stu-id="fbf23-111">When this property is set to `true`, the WCF infrastructure determines the best format to use.</span></span> <span data-ttu-id="fbf23-112">Otomatik Biçim seçimi, geriye doğru uyumluluk için varsayılan olarak devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="fbf23-112">Automatic format selection is disabled by default for backwards compatibility.</span></span> <span data-ttu-id="fbf23-113">Otomatik Biçim Seçimi programlı bir şekilde veya yapılandırma aracılığıyla etkinleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="fbf23-113">Automatic format selection can be enabled programmatically or through configuration.</span></span>|  
|<span data-ttu-id="fbf23-114">defaultBodyStyle</span><span class="sxs-lookup"><span data-stu-id="fbf23-114">defaultBodyStyle</span></span>|<span data-ttu-id="fbf23-115">Döndürülen iletilerin varsayılan gövde stilini belirtir.</span><span class="sxs-lookup"><span data-stu-id="fbf23-115">Specifies the default body style of returned messages.</span></span> <span data-ttu-id="fbf23-116">Daha fazla bilgi için bkz <xref:System.ServiceModel.Web.WebMessageBodyStyle> . ve [WCF Web http biçimlendirmesi](../../../wcf/feature-details/wcf-web-http-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="fbf23-116">For more information, see <xref:System.ServiceModel.Web.WebMessageBodyStyle> and [WCF Web HTTP Formatting](../../../wcf/feature-details/wcf-web-http-formatting.md).</span></span>|  
|<span data-ttu-id="fbf23-117">defaultOutgoingResponseFormat</span><span class="sxs-lookup"><span data-stu-id="fbf23-117">defaultOutgoingResponseFormat</span></span>|<span data-ttu-id="fbf23-118">İletiler için varsayılan giden yanıt biçimini belirtir.</span><span class="sxs-lookup"><span data-stu-id="fbf23-118">Specifies the default outgoing response format for messages.</span></span> <span data-ttu-id="fbf23-119">Daha fazla bilgi için bkz. [WCF Web http biçimlendirmesi](../../../wcf/feature-details/wcf-web-http-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="fbf23-119">For more information, see [WCF Web HTTP Formatting](../../../wcf/feature-details/wcf-web-http-formatting.md).</span></span>|  
|<span data-ttu-id="fbf23-120">faultExceptionEnabled</span><span class="sxs-lookup"><span data-stu-id="fbf23-120">faultExceptionEnabled</span></span>|<span data-ttu-id="fbf23-121">Bir iç sunucu hatası (HTTP durum kodu: 500) oluştuğunda bir FaultException oluşturulup oluşturulmayacağını belirten bayrağı alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="fbf23-121">Gets or sets the flag that specifies whether a FaultException is generated when an internal server error (HTTP status code: 500) occurs.</span></span>|  
|<span data-ttu-id="fbf23-122">Yardım etkin</span><span class="sxs-lookup"><span data-stu-id="fbf23-122">helpEnabled</span></span>|<span data-ttu-id="fbf23-123">Yardım sayfasının etkinleştirilip etkinleştirilmediğini belirleyen bir değer alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="fbf23-123">Gets or sets a value that determines if the Help page is enabled.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fbf23-124">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="fbf23-124">Child Elements</span></span>  

 <span data-ttu-id="fbf23-125">Yok.</span><span class="sxs-lookup"><span data-stu-id="fbf23-125">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fbf23-126">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="fbf23-126">Parent Elements</span></span>  
  
|<span data-ttu-id="fbf23-127">Öğe</span><span class="sxs-lookup"><span data-stu-id="fbf23-127">Element</span></span>|<span data-ttu-id="fbf23-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fbf23-128">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="fbf23-129">Uç nokta davranışları kümesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="fbf23-129">Specifies the set of endpoint behaviors.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fbf23-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fbf23-130">See also</span></span>

- <xref:System.ServiceModel.Configuration.WebHttpElement>
- <xref:System.ServiceModel.Description.WebHttpBehavior>
- [<span data-ttu-id="fbf23-131">AJAX Tümleştirme ve JSON Desteği</span><span class="sxs-lookup"><span data-stu-id="fbf23-131">AJAX Integration and JSON Support</span></span>](../../../wcf/feature-details/ajax-integration-and-json-support.md)
- [\<webHttpBinding>](webhttpbinding.md)
