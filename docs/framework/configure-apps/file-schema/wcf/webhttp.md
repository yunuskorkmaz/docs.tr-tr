---
title: '&lt;webHttp&gt;'
ms.date: 03/30/2017
ms.assetid: 1f9d0754-d41e-44ce-a298-e51cb3096c64
ms.openlocfilehash: b52259af5e05de5bf5dd42a2cd0bf4b01f3e46f9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54597560"
---
# <a name="ltwebhttpgt"></a><span data-ttu-id="41455-102">&lt;webHttp&gt;</span><span class="sxs-lookup"><span data-stu-id="41455-102">&lt;webHttp&gt;</span></span>
<span data-ttu-id="41455-103">Bu öğeyi belirten <xref:System.ServiceModel.Description.WebHttpBehavior> yapılandırma yoluyla bir uç noktada.</span><span class="sxs-lookup"><span data-stu-id="41455-103">This element specifies the <xref:System.ServiceModel.Description.WebHttpBehavior> on an endpoint through configuration.</span></span> <span data-ttu-id="41455-104">İle birlikte kullanıldığında bu davranışı [ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) standart bağlama için bir Windows Communication Foundation (WCF) hizmeti Web programlama modeli sağlar.</span><span class="sxs-lookup"><span data-stu-id="41455-104">This behavior, when used in conjunction with the [\<webHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) standard binding, enables the Web programming model for a Windows Communication Foundation (WCF) service.</span></span>  
  
 <span data-ttu-id="41455-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="41455-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="41455-106">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="41455-106">\<behaviors></span></span>  
<span data-ttu-id="41455-107">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="41455-107">\<endpointBehaviors></span></span>  
<span data-ttu-id="41455-108">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="41455-108">\<behavior></span></span>  
<span data-ttu-id="41455-109">\<webHttp ></span><span class="sxs-lookup"><span data-stu-id="41455-109">\<webHttp></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41455-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="41455-110">Syntax</span></span>  
  
```xml  
<webHttp />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="41455-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="41455-111">Attributes and Elements</span></span>  
 <span data-ttu-id="41455-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="41455-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="41455-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="41455-113">Attributes</span></span>  
  
|<span data-ttu-id="41455-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="41455-114">Attribute</span></span>|<span data-ttu-id="41455-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="41455-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="41455-116">automaticFormatSelectionEnabled</span><span class="sxs-lookup"><span data-stu-id="41455-116">automaticFormatSelectionEnabled</span></span>|<span data-ttu-id="41455-117">Bu özelliği ayarlandığında `true`, WCF altyapısı kullanılacak en iyi biçimi belirler.</span><span class="sxs-lookup"><span data-stu-id="41455-117">When this property is set to `true`, the WCF infrastructure determines the best format to use.</span></span> <span data-ttu-id="41455-118">Otomatik Biçim Seçimi varsayılan olarak devre dışıdır için geriye dönük uyumluluk.</span><span class="sxs-lookup"><span data-stu-id="41455-118">Automatic format selection is disabled by default for backwards compatibility.</span></span> <span data-ttu-id="41455-119">Otomatik Biçim Seçimi program aracılığıyla veya yapılandırma yoluyla etkinleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="41455-119">Automatic format selection can be enabled programmatically or through configuration.</span></span>|  
|<span data-ttu-id="41455-120">defaultBodyStyle</span><span class="sxs-lookup"><span data-stu-id="41455-120">defaultBodyStyle</span></span>|<span data-ttu-id="41455-121">Döndürülen iletilerin varsayılan gövde stilini belirtir.</span><span class="sxs-lookup"><span data-stu-id="41455-121">Specifies the default body style of returned messages.</span></span> <span data-ttu-id="41455-122">Daha fazla bilgi için <xref:System.ServiceModel.Web.WebMessageBodyStyle> ve [WCF Web HTTP biçimlendirme](../../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="41455-122">For more information, see <xref:System.ServiceModel.Web.WebMessageBodyStyle> and [WCF Web HTTP Formatting](../../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).</span></span>|  
|<span data-ttu-id="41455-123">defaultOutgoingResponseFormat</span><span class="sxs-lookup"><span data-stu-id="41455-123">defaultOutgoingResponseFormat</span></span>|<span data-ttu-id="41455-124">İletiler için varsayılan giden yanıt biçimini belirtir.</span><span class="sxs-lookup"><span data-stu-id="41455-124">Specifies the default outgoing response format for messages.</span></span> <span data-ttu-id="41455-125">Daha fazla bilgi için [WCF Web HTTP biçimlendirme](../../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="41455-125">For more information, see [WCF Web HTTP Formatting](../../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).</span></span>|  
|<span data-ttu-id="41455-126">faultExceptionEnabled</span><span class="sxs-lookup"><span data-stu-id="41455-126">faultExceptionEnabled</span></span>|<span data-ttu-id="41455-127">Bir iç sunucu hatası bir FaultException oluşturulup oluşturulmayacağını belirten bayrağı alır veya ayarlar (HTTP durum kodu: 500) oluşur.</span><span class="sxs-lookup"><span data-stu-id="41455-127">Gets or sets the flag that specifies whether a FaultException is generated when an internal server error (HTTP status code: 500) occurs.</span></span>|  
|<span data-ttu-id="41455-128">helpEnabled</span><span class="sxs-lookup"><span data-stu-id="41455-128">helpEnabled</span></span>|<span data-ttu-id="41455-129">Alır veya Yardım sayfasının etkinleştirilip etkinleştirilmediğini belirleyen bir değer ayarlar.</span><span class="sxs-lookup"><span data-stu-id="41455-129">Gets or sets a value that determines if the Help page is enabled.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="41455-130">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="41455-130">Child Elements</span></span>  
 <span data-ttu-id="41455-131">Yok.</span><span class="sxs-lookup"><span data-stu-id="41455-131">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="41455-132">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="41455-132">Parent Elements</span></span>  
  
|<span data-ttu-id="41455-133">Öğe</span><span class="sxs-lookup"><span data-stu-id="41455-133">Element</span></span>|<span data-ttu-id="41455-134">Açıklama</span><span class="sxs-lookup"><span data-stu-id="41455-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="41455-135">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="41455-135">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="41455-136">Uç nokta davranışları kümesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="41455-136">Specifies the set of endpoint behaviors.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="41455-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="41455-137">See also</span></span>
- <xref:System.ServiceModel.Configuration.WebHttpElement>
- <xref:System.ServiceModel.Description.WebHttpBehavior>
- [<span data-ttu-id="41455-138">AJAX Tümleştirme ve JSON Desteği</span><span class="sxs-lookup"><span data-stu-id="41455-138">AJAX Integration and JSON Support</span></span>](../../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md)
- [<span data-ttu-id="41455-139">\<webHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="41455-139">\<webHttpBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md)
