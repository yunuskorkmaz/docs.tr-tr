---
title: <webHttp>
ms.date: 03/30/2017
ms.assetid: 1f9d0754-d41e-44ce-a298-e51cb3096c64
ms.openlocfilehash: 795e61b9054d2ea9276970988018c50099bcbe17
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61769804"
---
# <a name="webhttp"></a><span data-ttu-id="d44a1-101">\<webHttp ></span><span class="sxs-lookup"><span data-stu-id="d44a1-101">\<webHttp></span></span>
<span data-ttu-id="d44a1-102">Bu öğeyi belirten <xref:System.ServiceModel.Description.WebHttpBehavior> yapılandırma yoluyla bir uç noktada.</span><span class="sxs-lookup"><span data-stu-id="d44a1-102">This element specifies the <xref:System.ServiceModel.Description.WebHttpBehavior> on an endpoint through configuration.</span></span> <span data-ttu-id="d44a1-103">İle birlikte kullanıldığında bu davranışı [ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) standart bağlama için bir Windows Communication Foundation (WCF) hizmeti Web programlama modeli sağlar.</span><span class="sxs-lookup"><span data-stu-id="d44a1-103">This behavior, when used in conjunction with the [\<webHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) standard binding, enables the Web programming model for a Windows Communication Foundation (WCF) service.</span></span>  
  
 <span data-ttu-id="d44a1-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="d44a1-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="d44a1-105">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="d44a1-105">\<behaviors></span></span>  
<span data-ttu-id="d44a1-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="d44a1-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="d44a1-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="d44a1-107">\<behavior></span></span>  
<span data-ttu-id="d44a1-108">\<webHttp ></span><span class="sxs-lookup"><span data-stu-id="d44a1-108">\<webHttp></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d44a1-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d44a1-109">Syntax</span></span>  
  
```xml  
<webHttp />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d44a1-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d44a1-110">Attributes and Elements</span></span>  
 <span data-ttu-id="d44a1-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d44a1-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d44a1-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d44a1-112">Attributes</span></span>  
  
|<span data-ttu-id="d44a1-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="d44a1-113">Attribute</span></span>|<span data-ttu-id="d44a1-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d44a1-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d44a1-115">automaticFormatSelectionEnabled</span><span class="sxs-lookup"><span data-stu-id="d44a1-115">automaticFormatSelectionEnabled</span></span>|<span data-ttu-id="d44a1-116">Bu özelliği ayarlandığında `true`, WCF altyapısı kullanılacak en iyi biçimi belirler.</span><span class="sxs-lookup"><span data-stu-id="d44a1-116">When this property is set to `true`, the WCF infrastructure determines the best format to use.</span></span> <span data-ttu-id="d44a1-117">Otomatik Biçim Seçimi varsayılan olarak devre dışıdır için geriye dönük uyumluluk.</span><span class="sxs-lookup"><span data-stu-id="d44a1-117">Automatic format selection is disabled by default for backwards compatibility.</span></span> <span data-ttu-id="d44a1-118">Otomatik Biçim Seçimi program aracılığıyla veya yapılandırma yoluyla etkinleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="d44a1-118">Automatic format selection can be enabled programmatically or through configuration.</span></span>|  
|<span data-ttu-id="d44a1-119">defaultBodyStyle</span><span class="sxs-lookup"><span data-stu-id="d44a1-119">defaultBodyStyle</span></span>|<span data-ttu-id="d44a1-120">Döndürülen iletilerin varsayılan gövde stilini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d44a1-120">Specifies the default body style of returned messages.</span></span> <span data-ttu-id="d44a1-121">Daha fazla bilgi için <xref:System.ServiceModel.Web.WebMessageBodyStyle> ve [WCF Web HTTP biçimlendirme](../../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="d44a1-121">For more information, see <xref:System.ServiceModel.Web.WebMessageBodyStyle> and [WCF Web HTTP Formatting](../../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).</span></span>|  
|<span data-ttu-id="d44a1-122">defaultOutgoingResponseFormat</span><span class="sxs-lookup"><span data-stu-id="d44a1-122">defaultOutgoingResponseFormat</span></span>|<span data-ttu-id="d44a1-123">İletiler için varsayılan giden yanıt biçimini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d44a1-123">Specifies the default outgoing response format for messages.</span></span> <span data-ttu-id="d44a1-124">Daha fazla bilgi için [WCF Web HTTP biçimlendirme](../../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="d44a1-124">For more information, see [WCF Web HTTP Formatting](../../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).</span></span>|  
|<span data-ttu-id="d44a1-125">faultExceptionEnabled</span><span class="sxs-lookup"><span data-stu-id="d44a1-125">faultExceptionEnabled</span></span>|<span data-ttu-id="d44a1-126">Bir iç sunucu hatası bir FaultException oluşturulup oluşturulmayacağını belirten bayrağı alır veya ayarlar (HTTP durum kodu: 500) oluşur.</span><span class="sxs-lookup"><span data-stu-id="d44a1-126">Gets or sets the flag that specifies whether a FaultException is generated when an internal server error (HTTP status code: 500) occurs.</span></span>|  
|<span data-ttu-id="d44a1-127">helpEnabled</span><span class="sxs-lookup"><span data-stu-id="d44a1-127">helpEnabled</span></span>|<span data-ttu-id="d44a1-128">Alır veya Yardım sayfasının etkinleştirilip etkinleştirilmediğini belirleyen bir değer ayarlar.</span><span class="sxs-lookup"><span data-stu-id="d44a1-128">Gets or sets a value that determines if the Help page is enabled.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d44a1-129">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d44a1-129">Child Elements</span></span>  
 <span data-ttu-id="d44a1-130">Yok.</span><span class="sxs-lookup"><span data-stu-id="d44a1-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d44a1-131">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d44a1-131">Parent Elements</span></span>  
  
|<span data-ttu-id="d44a1-132">Öğe</span><span class="sxs-lookup"><span data-stu-id="d44a1-132">Element</span></span>|<span data-ttu-id="d44a1-133">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d44a1-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d44a1-134">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="d44a1-134">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="d44a1-135">Uç nokta davranışları kümesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d44a1-135">Specifies the set of endpoint behaviors.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d44a1-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d44a1-136">See also</span></span>

- <xref:System.ServiceModel.Configuration.WebHttpElement>
- <xref:System.ServiceModel.Description.WebHttpBehavior>
- [<span data-ttu-id="d44a1-137">AJAX Tümleştirme ve JSON Desteği</span><span class="sxs-lookup"><span data-stu-id="d44a1-137">AJAX Integration and JSON Support</span></span>](../../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md)
- [<span data-ttu-id="d44a1-138">\<webHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="d44a1-138">\<webHttpBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md)
