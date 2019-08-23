---
title: <webHttp>
ms.date: 03/30/2017
ms.assetid: 1f9d0754-d41e-44ce-a298-e51cb3096c64
ms.openlocfilehash: 366def5d0f4cc82b0ff0a5127701b0b5a6adb6a0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940498"
---
# <a name="webhttp"></a><span data-ttu-id="2a956-101">\<webHttp ></span><span class="sxs-lookup"><span data-stu-id="2a956-101">\<webHttp></span></span>
<span data-ttu-id="2a956-102">Bu öğe, <xref:System.ServiceModel.Description.WebHttpBehavior> yapılandırma yoluyla bir uç nokta üzerinde belirtir.</span><span class="sxs-lookup"><span data-stu-id="2a956-102">This element specifies the <xref:System.ServiceModel.Description.WebHttpBehavior> on an endpoint through configuration.</span></span> <span data-ttu-id="2a956-103">Bu davranış, [ \<WebHttpBinding >](webhttpbinding.md) standart bağlamasıyla birlikte kullanıldığında, bir Windows Communication Foundation (WCF) hizmeti için Web programlama modeline izin vermez.</span><span class="sxs-lookup"><span data-stu-id="2a956-103">This behavior, when used in conjunction with the [\<webHttpBinding>](webhttpbinding.md) standard binding, enables the Web programming model for a Windows Communication Foundation (WCF) service.</span></span>  
  
 <span data-ttu-id="2a956-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="2a956-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="2a956-105">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="2a956-105">\<behaviors></span></span>  
<span data-ttu-id="2a956-106">\<Endpointdavranışlar ></span><span class="sxs-lookup"><span data-stu-id="2a956-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="2a956-107">\<davranış ></span><span class="sxs-lookup"><span data-stu-id="2a956-107">\<behavior></span></span>  
<span data-ttu-id="2a956-108">\<webHttp ></span><span class="sxs-lookup"><span data-stu-id="2a956-108">\<webHttp></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a956-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2a956-109">Syntax</span></span>  
  
```xml  
<webHttp />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2a956-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="2a956-110">Attributes and Elements</span></span>  
 <span data-ttu-id="2a956-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2a956-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2a956-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="2a956-112">Attributes</span></span>  
  
|<span data-ttu-id="2a956-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="2a956-113">Attribute</span></span>|<span data-ttu-id="2a956-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2a956-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2a956-115">automaticFormatSelectionEnabled etkin</span><span class="sxs-lookup"><span data-stu-id="2a956-115">automaticFormatSelectionEnabled</span></span>|<span data-ttu-id="2a956-116">Bu özellik olarak `true`ayarlandığında, WCF altyapısı kullanılacak en iyi biçimi belirler.</span><span class="sxs-lookup"><span data-stu-id="2a956-116">When this property is set to `true`, the WCF infrastructure determines the best format to use.</span></span> <span data-ttu-id="2a956-117">Otomatik Biçim seçimi, geriye doğru uyumluluk için varsayılan olarak devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="2a956-117">Automatic format selection is disabled by default for backwards compatibility.</span></span> <span data-ttu-id="2a956-118">Otomatik Biçim Seçimi programlı bir şekilde veya yapılandırma aracılığıyla etkinleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="2a956-118">Automatic format selection can be enabled programmatically or through configuration.</span></span>|  
|<span data-ttu-id="2a956-119">defaultBodyStyle</span><span class="sxs-lookup"><span data-stu-id="2a956-119">defaultBodyStyle</span></span>|<span data-ttu-id="2a956-120">Döndürülen iletilerin varsayılan gövde stilini belirtir.</span><span class="sxs-lookup"><span data-stu-id="2a956-120">Specifies the default body style of returned messages.</span></span> <span data-ttu-id="2a956-121">Daha fazla bilgi için bkz <xref:System.ServiceModel.Web.WebMessageBodyStyle> . ve [WCF Web http biçimlendirmesi](../../../wcf/feature-details/wcf-web-http-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="2a956-121">For more information, see <xref:System.ServiceModel.Web.WebMessageBodyStyle> and [WCF Web HTTP Formatting](../../../wcf/feature-details/wcf-web-http-formatting.md).</span></span>|  
|<span data-ttu-id="2a956-122">defaultOutgoingResponseFormat</span><span class="sxs-lookup"><span data-stu-id="2a956-122">defaultOutgoingResponseFormat</span></span>|<span data-ttu-id="2a956-123">İletiler için varsayılan giden yanıt biçimini belirtir.</span><span class="sxs-lookup"><span data-stu-id="2a956-123">Specifies the default outgoing response format for messages.</span></span> <span data-ttu-id="2a956-124">Daha fazla bilgi için bkz. [WCF Web http biçimlendirmesi](../../../wcf/feature-details/wcf-web-http-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="2a956-124">For more information, see [WCF Web HTTP Formatting](../../../wcf/feature-details/wcf-web-http-formatting.md).</span></span>|  
|<span data-ttu-id="2a956-125">faultExceptionEnabled</span><span class="sxs-lookup"><span data-stu-id="2a956-125">faultExceptionEnabled</span></span>|<span data-ttu-id="2a956-126">Bir iç sunucu hatası (HTTP durum kodu:) sırasında bir FaultException oluşturulup oluşturulmayacağını belirten bayrağı alır veya ayarlar. 500) oluşur.</span><span class="sxs-lookup"><span data-stu-id="2a956-126">Gets or sets the flag that specifies whether a FaultException is generated when an internal server error (HTTP status code: 500) occurs.</span></span>|  
|<span data-ttu-id="2a956-127">Yardım etkin</span><span class="sxs-lookup"><span data-stu-id="2a956-127">helpEnabled</span></span>|<span data-ttu-id="2a956-128">Yardım sayfasının etkinleştirilip etkinleştirilmediğini belirleyen bir değer alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="2a956-128">Gets or sets a value that determines if the Help page is enabled.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2a956-129">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="2a956-129">Child Elements</span></span>  
 <span data-ttu-id="2a956-130">Yok.</span><span class="sxs-lookup"><span data-stu-id="2a956-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2a956-131">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="2a956-131">Parent Elements</span></span>  
  
|<span data-ttu-id="2a956-132">Öğe</span><span class="sxs-lookup"><span data-stu-id="2a956-132">Element</span></span>|<span data-ttu-id="2a956-133">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2a956-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2a956-134">\<davranış ></span><span class="sxs-lookup"><span data-stu-id="2a956-134">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="2a956-135">Uç nokta davranışları kümesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="2a956-135">Specifies the set of endpoint behaviors.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2a956-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2a956-136">See also</span></span>

- <xref:System.ServiceModel.Configuration.WebHttpElement>
- <xref:System.ServiceModel.Description.WebHttpBehavior>
- [<span data-ttu-id="2a956-137">AJAX Tümleştirme ve JSON Desteği</span><span class="sxs-lookup"><span data-stu-id="2a956-137">AJAX Integration and JSON Support</span></span>](../../../wcf/feature-details/ajax-integration-and-json-support.md)
- [<span data-ttu-id="2a956-138">\<webHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="2a956-138">\<webHttpBinding></span></span>](webhttpbinding.md)
