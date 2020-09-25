---
title: <webHttp>
ms.date: 03/30/2017
ms.assetid: 1f9d0754-d41e-44ce-a298-e51cb3096c64
ms.openlocfilehash: 716d960e2d5f896976c22a60d419d9b165b36178
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91202467"
---
# \<webHttp>

<span data-ttu-id="0725b-101">Bu öğe, <xref:System.ServiceModel.Description.WebHttpBehavior> yapılandırma yoluyla bir uç nokta üzerinde belirtir.</span><span class="sxs-lookup"><span data-stu-id="0725b-101">This element specifies the <xref:System.ServiceModel.Description.WebHttpBehavior> on an endpoint through configuration.</span></span> <span data-ttu-id="0725b-102">Bu davranış, [\<webHttpBinding>](webhttpbinding.md) Standart bağlama birlikte kullanıldığında, bir Windows Communication Foundation (WCF) hizmeti Için Web programlama modeline izin vermez.</span><span class="sxs-lookup"><span data-stu-id="0725b-102">This behavior, when used in conjunction with the [\<webHttpBinding>](webhttpbinding.md) standard binding, enables the Web programming model for a Windows Communication Foundation (WCF) service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webHttp>**  
  
## <a name="syntax"></a><span data-ttu-id="0725b-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="0725b-103">Syntax</span></span>  
  
```xml  
<webHttp />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0725b-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="0725b-104">Attributes and Elements</span></span>  

 <span data-ttu-id="0725b-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0725b-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0725b-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="0725b-106">Attributes</span></span>  
  
|<span data-ttu-id="0725b-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="0725b-107">Attribute</span></span>|<span data-ttu-id="0725b-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0725b-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0725b-109">automaticFormatSelectionEnabled etkin</span><span class="sxs-lookup"><span data-stu-id="0725b-109">automaticFormatSelectionEnabled</span></span>|<span data-ttu-id="0725b-110">Bu özellik olarak ayarlandığında `true` , WCF altyapısı kullanılacak en iyi biçimi belirler.</span><span class="sxs-lookup"><span data-stu-id="0725b-110">When this property is set to `true`, the WCF infrastructure determines the best format to use.</span></span> <span data-ttu-id="0725b-111">Otomatik Biçim seçimi, geriye doğru uyumluluk için varsayılan olarak devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="0725b-111">Automatic format selection is disabled by default for backwards compatibility.</span></span> <span data-ttu-id="0725b-112">Otomatik Biçim Seçimi programlı bir şekilde veya yapılandırma aracılığıyla etkinleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="0725b-112">Automatic format selection can be enabled programmatically or through configuration.</span></span>|  
|<span data-ttu-id="0725b-113">defaultBodyStyle</span><span class="sxs-lookup"><span data-stu-id="0725b-113">defaultBodyStyle</span></span>|<span data-ttu-id="0725b-114">Döndürülen iletilerin varsayılan gövde stilini belirtir.</span><span class="sxs-lookup"><span data-stu-id="0725b-114">Specifies the default body style of returned messages.</span></span> <span data-ttu-id="0725b-115">Daha fazla bilgi için bkz <xref:System.ServiceModel.Web.WebMessageBodyStyle> . ve [WCF Web http biçimlendirmesi](../../../wcf/feature-details/wcf-web-http-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="0725b-115">For more information, see <xref:System.ServiceModel.Web.WebMessageBodyStyle> and [WCF Web HTTP Formatting](../../../wcf/feature-details/wcf-web-http-formatting.md).</span></span>|  
|<span data-ttu-id="0725b-116">defaultOutgoingResponseFormat</span><span class="sxs-lookup"><span data-stu-id="0725b-116">defaultOutgoingResponseFormat</span></span>|<span data-ttu-id="0725b-117">İletiler için varsayılan giden yanıt biçimini belirtir.</span><span class="sxs-lookup"><span data-stu-id="0725b-117">Specifies the default outgoing response format for messages.</span></span> <span data-ttu-id="0725b-118">Daha fazla bilgi için bkz. [WCF Web http biçimlendirmesi](../../../wcf/feature-details/wcf-web-http-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="0725b-118">For more information, see [WCF Web HTTP Formatting](../../../wcf/feature-details/wcf-web-http-formatting.md).</span></span>|  
|<span data-ttu-id="0725b-119">faultExceptionEnabled</span><span class="sxs-lookup"><span data-stu-id="0725b-119">faultExceptionEnabled</span></span>|<span data-ttu-id="0725b-120">Bir iç sunucu hatası (HTTP durum kodu: 500) oluştuğunda bir FaultException oluşturulup oluşturulmayacağını belirten bayrağı alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="0725b-120">Gets or sets the flag that specifies whether a FaultException is generated when an internal server error (HTTP status code: 500) occurs.</span></span>|  
|<span data-ttu-id="0725b-121">Yardım etkin</span><span class="sxs-lookup"><span data-stu-id="0725b-121">helpEnabled</span></span>|<span data-ttu-id="0725b-122">Yardım sayfasının etkinleştirilip etkinleştirilmediğini belirleyen bir değer alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="0725b-122">Gets or sets a value that determines if the Help page is enabled.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0725b-123">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="0725b-123">Child Elements</span></span>  

 <span data-ttu-id="0725b-124">Yok.</span><span class="sxs-lookup"><span data-stu-id="0725b-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0725b-125">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="0725b-125">Parent Elements</span></span>  
  
|<span data-ttu-id="0725b-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="0725b-126">Element</span></span>|<span data-ttu-id="0725b-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0725b-127">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="0725b-128">Uç nokta davranışları kümesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="0725b-128">Specifies the set of endpoint behaviors.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0725b-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0725b-129">See also</span></span>

- <xref:System.ServiceModel.Configuration.WebHttpElement>
- <xref:System.ServiceModel.Description.WebHttpBehavior>
- [<span data-ttu-id="0725b-130">AJAX Tümleştirme ve JSON Desteği</span><span class="sxs-lookup"><span data-stu-id="0725b-130">AJAX Integration and JSON Support</span></span>](../../../wcf/feature-details/ajax-integration-and-json-support.md)
- [\<webHttpBinding>](webhttpbinding.md)
