---
title: '&lt;webHttp&gt;'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1f9d0754-d41e-44ce-a298-e51cb3096c64
caps.latest.revision: 5
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9bf92421d09f25c760f8edc5062b7b7d6276902f
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="ltwebhttpgt"></a><span data-ttu-id="60fb2-102">&lt;webHttp&gt;</span><span class="sxs-lookup"><span data-stu-id="60fb2-102">&lt;webHttp&gt;</span></span>
<span data-ttu-id="60fb2-103">Bu öğe belirtir <xref:System.ServiceModel.Description.WebHttpBehavior> yapılandırma yoluyla bir uç noktada.</span><span class="sxs-lookup"><span data-stu-id="60fb2-103">This element specifies the <xref:System.ServiceModel.Description.WebHttpBehavior> on an endpoint through configuration.</span></span> <span data-ttu-id="60fb2-104">İle birlikte kullanıldığında bu davranış, [ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) standart bağlama sağlayan Web programlama modeli için bir [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] hizmet.</span><span class="sxs-lookup"><span data-stu-id="60fb2-104">This behavior, when used in conjunction with the [\<webHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) standard binding, enables the Web programming model for a [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] service.</span></span>  
  
 <span data-ttu-id="60fb2-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="60fb2-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="60fb2-106">\<davranışları ></span><span class="sxs-lookup"><span data-stu-id="60fb2-106">\<behaviors></span></span>  
<span data-ttu-id="60fb2-107">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="60fb2-107">\<endpointBehaviors></span></span>  
<span data-ttu-id="60fb2-108">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="60fb2-108">\<behavior></span></span>  
<span data-ttu-id="60fb2-109">\<webHttp ></span><span class="sxs-lookup"><span data-stu-id="60fb2-109">\<webHttp></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60fb2-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="60fb2-110">Syntax</span></span>  
  
```xml  
<webHttp />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="60fb2-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="60fb2-111">Attributes and Elements</span></span>  
 <span data-ttu-id="60fb2-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="60fb2-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="60fb2-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="60fb2-113">Attributes</span></span>  
  
|<span data-ttu-id="60fb2-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="60fb2-114">Attribute</span></span>|<span data-ttu-id="60fb2-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="60fb2-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="60fb2-116">automaticFormatSelectionEnabled</span><span class="sxs-lookup"><span data-stu-id="60fb2-116">automaticFormatSelectionEnabled</span></span>|<span data-ttu-id="60fb2-117">Bu özellik ayarlandığında `true`, WCF altyapı kullanmak için en iyi biçimini belirler.</span><span class="sxs-lookup"><span data-stu-id="60fb2-117">When this property is set to `true`, the WCF infrastructure determines the best format to use.</span></span> <span data-ttu-id="60fb2-118">Otomatik Biçim Seçimi varsayılan olarak devre dışıdır için geriye dönük uyumluluk.</span><span class="sxs-lookup"><span data-stu-id="60fb2-118">Automatic format selection is disabled by default for backwards compatibility.</span></span> <span data-ttu-id="60fb2-119">Otomatik Biçim Seçimi program aracılığıyla veya yapılandırma yoluyla etkinleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="60fb2-119">Automatic format selection can be enabled programmatically or through configuration.</span></span>|  
|<span data-ttu-id="60fb2-120">defaultBodyStyle</span><span class="sxs-lookup"><span data-stu-id="60fb2-120">defaultBodyStyle</span></span>|<span data-ttu-id="60fb2-121">Döndürülen iletilerini varsayılan gövde stilini belirtir.</span><span class="sxs-lookup"><span data-stu-id="60fb2-121">Specifies the default body style of returned messages.</span></span> <span data-ttu-id="60fb2-122">Daha fazla bilgi için bkz: <xref:System.ServiceModel.Web.WebMessageBodyStyle> ve [WCF Web HTTP biçimlendirme](../../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="60fb2-122">For more information, see <xref:System.ServiceModel.Web.WebMessageBodyStyle> and [WCF Web HTTP Formatting](../../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).</span></span>|  
|<span data-ttu-id="60fb2-123">defaultOutgoingResponseFormat</span><span class="sxs-lookup"><span data-stu-id="60fb2-123">defaultOutgoingResponseFormat</span></span>|<span data-ttu-id="60fb2-124">İletileri için varsayılan giden yanıt biçimi belirtir.</span><span class="sxs-lookup"><span data-stu-id="60fb2-124">Specifies the default outgoing response format for messages.</span></span> <span data-ttu-id="60fb2-125">Daha fazla bilgi için bkz: [WCF Web HTTP biçimlendirme](../../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="60fb2-125">For more information, see [WCF Web HTTP Formatting](../../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).</span></span>|  
|<span data-ttu-id="60fb2-126">faultExceptionEnabled</span><span class="sxs-lookup"><span data-stu-id="60fb2-126">faultExceptionEnabled</span></span>|<span data-ttu-id="60fb2-127">Bir iç sunucu hatası olduğunda bir FaultException oluşturulup oluşturulmayacağını belirten bir bayrak alır veya ayarlar (HTTP durum kodu: 500) oluşur.</span><span class="sxs-lookup"><span data-stu-id="60fb2-127">Gets or sets the flag that specifies whether a FaultException is generated when an internal server error (HTTP status code: 500) occurs.</span></span>|  
|<span data-ttu-id="60fb2-128">helpEnabled</span><span class="sxs-lookup"><span data-stu-id="60fb2-128">helpEnabled</span></span>|<span data-ttu-id="60fb2-129">Alır veya yardım sayfasına etkin olup olmadığını belirleyen bir değer ayarlar.</span><span class="sxs-lookup"><span data-stu-id="60fb2-129">Gets or sets a value that determines if the Help page is enabled.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="60fb2-130">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="60fb2-130">Child Elements</span></span>  
 <span data-ttu-id="60fb2-131">Yok.</span><span class="sxs-lookup"><span data-stu-id="60fb2-131">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="60fb2-132">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="60fb2-132">Parent Elements</span></span>  
  
|<span data-ttu-id="60fb2-133">Öğe</span><span class="sxs-lookup"><span data-stu-id="60fb2-133">Element</span></span>|<span data-ttu-id="60fb2-134">Açıklama</span><span class="sxs-lookup"><span data-stu-id="60fb2-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="60fb2-135">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="60fb2-135">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="60fb2-136">Uç nokta davranışları kümesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="60fb2-136">Specifies the set of endpoint behaviors.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="60fb2-137">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="60fb2-137">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.WebHttpElement>  
 <xref:System.ServiceModel.Description.WebHttpBehavior>  
 [<span data-ttu-id="60fb2-138">AJAX Tümleştirme ve JSON Desteği</span><span class="sxs-lookup"><span data-stu-id="60fb2-138">AJAX Integration and JSON Support</span></span>](../../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md)  
 [<span data-ttu-id="60fb2-139">\<webHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="60fb2-139">\<webHttpBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md)
