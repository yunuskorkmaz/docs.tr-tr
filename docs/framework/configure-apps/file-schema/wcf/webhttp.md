---
title: <webHttp>
ms.date: 03/30/2017
ms.assetid: 1f9d0754-d41e-44ce-a298-e51cb3096c64
ms.openlocfilehash: 00644d248e6fb85d7cf712620e6ac74405e6b0c3
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399160"
---
# <a name="webhttp"></a><span data-ttu-id="c7ef0-101">\<webHttp ></span><span class="sxs-lookup"><span data-stu-id="c7ef0-101">\<webHttp></span></span>
<span data-ttu-id="c7ef0-102">Bu öğe, <xref:System.ServiceModel.Description.WebHttpBehavior> yapılandırma yoluyla bir uç nokta üzerinde belirtir.</span><span class="sxs-lookup"><span data-stu-id="c7ef0-102">This element specifies the <xref:System.ServiceModel.Description.WebHttpBehavior> on an endpoint through configuration.</span></span> <span data-ttu-id="c7ef0-103">Bu davranış, [ \<WebHttpBinding >](webhttpbinding.md) standart bağlamasıyla birlikte kullanıldığında, bir Windows Communication Foundation (WCF) hizmeti için Web programlama modeline izin vermez.</span><span class="sxs-lookup"><span data-stu-id="c7ef0-103">This behavior, when used in conjunction with the [\<webHttpBinding>](webhttpbinding.md) standard binding, enables the Web programming model for a Windows Communication Foundation (WCF) service.</span></span>  
  
<span data-ttu-id="c7ef0-104">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="c7ef0-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="c7ef0-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="c7ef0-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="c7ef0-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranışlar >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="c7ef0-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="c7ef0-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Endpointdavranışlar >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="c7ef0-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="c7ef0-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranış >** ](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="c7ef0-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="c7ef0-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<webHttp >**</span><span class="sxs-lookup"><span data-stu-id="c7ef0-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webHttp>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7ef0-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c7ef0-110">Syntax</span></span>  
  
```xml  
<webHttp />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c7ef0-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c7ef0-111">Attributes and Elements</span></span>  
 <span data-ttu-id="c7ef0-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c7ef0-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c7ef0-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c7ef0-113">Attributes</span></span>  
  
|<span data-ttu-id="c7ef0-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="c7ef0-114">Attribute</span></span>|<span data-ttu-id="c7ef0-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c7ef0-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c7ef0-116">automaticFormatSelectionEnabled etkin</span><span class="sxs-lookup"><span data-stu-id="c7ef0-116">automaticFormatSelectionEnabled</span></span>|<span data-ttu-id="c7ef0-117">Bu özellik olarak `true`ayarlandığında, WCF altyapısı kullanılacak en iyi biçimi belirler.</span><span class="sxs-lookup"><span data-stu-id="c7ef0-117">When this property is set to `true`, the WCF infrastructure determines the best format to use.</span></span> <span data-ttu-id="c7ef0-118">Otomatik Biçim seçimi, geriye doğru uyumluluk için varsayılan olarak devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="c7ef0-118">Automatic format selection is disabled by default for backwards compatibility.</span></span> <span data-ttu-id="c7ef0-119">Otomatik Biçim Seçimi programlı bir şekilde veya yapılandırma aracılığıyla etkinleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="c7ef0-119">Automatic format selection can be enabled programmatically or through configuration.</span></span>|  
|<span data-ttu-id="c7ef0-120">defaultBodyStyle</span><span class="sxs-lookup"><span data-stu-id="c7ef0-120">defaultBodyStyle</span></span>|<span data-ttu-id="c7ef0-121">Döndürülen iletilerin varsayılan gövde stilini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c7ef0-121">Specifies the default body style of returned messages.</span></span> <span data-ttu-id="c7ef0-122">Daha fazla bilgi için bkz <xref:System.ServiceModel.Web.WebMessageBodyStyle> . ve [WCF Web http biçimlendirmesi](../../../wcf/feature-details/wcf-web-http-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="c7ef0-122">For more information, see <xref:System.ServiceModel.Web.WebMessageBodyStyle> and [WCF Web HTTP Formatting](../../../wcf/feature-details/wcf-web-http-formatting.md).</span></span>|  
|<span data-ttu-id="c7ef0-123">defaultOutgoingResponseFormat</span><span class="sxs-lookup"><span data-stu-id="c7ef0-123">defaultOutgoingResponseFormat</span></span>|<span data-ttu-id="c7ef0-124">İletiler için varsayılan giden yanıt biçimini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c7ef0-124">Specifies the default outgoing response format for messages.</span></span> <span data-ttu-id="c7ef0-125">Daha fazla bilgi için bkz. [WCF Web http biçimlendirmesi](../../../wcf/feature-details/wcf-web-http-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="c7ef0-125">For more information, see [WCF Web HTTP Formatting](../../../wcf/feature-details/wcf-web-http-formatting.md).</span></span>|  
|<span data-ttu-id="c7ef0-126">faultExceptionEnabled</span><span class="sxs-lookup"><span data-stu-id="c7ef0-126">faultExceptionEnabled</span></span>|<span data-ttu-id="c7ef0-127">Bir iç sunucu hatası (HTTP durum kodu:) sırasında bir FaultException oluşturulup oluşturulmayacağını belirten bayrağı alır veya ayarlar. 500) oluşur.</span><span class="sxs-lookup"><span data-stu-id="c7ef0-127">Gets or sets the flag that specifies whether a FaultException is generated when an internal server error (HTTP status code: 500) occurs.</span></span>|  
|<span data-ttu-id="c7ef0-128">Yardım etkin</span><span class="sxs-lookup"><span data-stu-id="c7ef0-128">helpEnabled</span></span>|<span data-ttu-id="c7ef0-129">Yardım sayfasının etkinleştirilip etkinleştirilmediğini belirleyen bir değer alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="c7ef0-129">Gets or sets a value that determines if the Help page is enabled.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c7ef0-130">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c7ef0-130">Child Elements</span></span>  
 <span data-ttu-id="c7ef0-131">Yok.</span><span class="sxs-lookup"><span data-stu-id="c7ef0-131">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c7ef0-132">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c7ef0-132">Parent Elements</span></span>  
  
|<span data-ttu-id="c7ef0-133">Öğe</span><span class="sxs-lookup"><span data-stu-id="c7ef0-133">Element</span></span>|<span data-ttu-id="c7ef0-134">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c7ef0-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c7ef0-135">\<davranış ></span><span class="sxs-lookup"><span data-stu-id="c7ef0-135">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="c7ef0-136">Uç nokta davranışları kümesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c7ef0-136">Specifies the set of endpoint behaviors.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c7ef0-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c7ef0-137">See also</span></span>

- <xref:System.ServiceModel.Configuration.WebHttpElement>
- <xref:System.ServiceModel.Description.WebHttpBehavior>
- [<span data-ttu-id="c7ef0-138">AJAX Tümleştirme ve JSON Desteği</span><span class="sxs-lookup"><span data-stu-id="c7ef0-138">AJAX Integration and JSON Support</span></span>](../../../wcf/feature-details/ajax-integration-and-json-support.md)
- [<span data-ttu-id="c7ef0-139">\<webHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="c7ef0-139">\<webHttpBinding></span></span>](webhttpbinding.md)
