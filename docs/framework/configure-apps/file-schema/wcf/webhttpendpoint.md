---
title: '&lt;webHttpEndpoint&gt;'
ms.date: 03/30/2017
ms.assetid: ecaaeb6f-ebd0-411d-8b53-92477cd45347
ms.openlocfilehash: b69ace451e90c824cdf8b911d596fdd158eb3f73
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54491726"
---
# <a name="ltwebhttpendpointgt"></a><span data-ttu-id="9eae1-102">&lt;webHttpEndpoint&gt;</span><span class="sxs-lookup"><span data-stu-id="9eae1-102">&lt;webHttpEndpoint&gt;</span></span>
<span data-ttu-id="9eae1-103">Bu yapılandırma öğesi ile bir sabit bir standart uç nokta tanımlar [ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) otomatik olarak bağlama ekler [ \<webHttp >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md) davranışı.</span><span class="sxs-lookup"><span data-stu-id="9eae1-103">This configuration element defines a standard endpoint with a fixed [\<webHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) binding that automatically adds the [\<webHttp>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md) behavior.</span></span> <span data-ttu-id="9eae1-104">Bir REST hizmeti yazarken Bu uç noktayı kullanın.</span><span class="sxs-lookup"><span data-stu-id="9eae1-104">Use this endpoint when writing a REST service.</span></span>  
  
<span data-ttu-id="9eae1-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="9eae1-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="9eae1-106">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="9eae1-106">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9eae1-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9eae1-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <webHttpEndpoint>
      <standardEndpoint automaticFormatSelectionEnabled="String"
                        defaultOutgoingResponseFormat="Xml/Json"
                        helpEnabled="Boolean"
                        webEndpointType="String" />
    </webHttpEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9eae1-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="9eae1-108">Attributes and Elements</span></span>  
 <span data-ttu-id="9eae1-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9eae1-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9eae1-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="9eae1-110">Attributes</span></span>  
  
|<span data-ttu-id="9eae1-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="9eae1-111">Attribute</span></span>|<span data-ttu-id="9eae1-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9eae1-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9eae1-113">automaticFormatSelectionEnabled</span><span class="sxs-lookup"><span data-stu-id="9eae1-113">automaticFormatSelectionEnabled</span></span>|<span data-ttu-id="9eae1-114">Otomatik Biçim Seçimi etkin olup olmadığını gösteren bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="9eae1-114">A Boolean value that indicates whether automatic format selection is enabled.</span></span><br /><br /> <span data-ttu-id="9eae1-115">Otomatik Biçim Seçimi etkinleştirildiğinde altyapı ayrıştırır `Accept` istek iletisinin üst bilgi ve en uygun yanıt biçimi belirler.</span><span class="sxs-lookup"><span data-stu-id="9eae1-115">When automatic format selection is enabled, the infrastructure parses the `Accept` header of the request message and determines the most appropriate response format.</span></span> <span data-ttu-id="9eae1-116">Varsa `Accept` üstbilgisi, uygun yanıt biçimi belirtmiyor, altyapısını kullanan `Content-Type` istek iletisi veya işlemin varsayılan yanıt biçimi.</span><span class="sxs-lookup"><span data-stu-id="9eae1-116">If the `Accept` header does not specify a suitable response format, the infrastructure uses the `Content-Type` of the request message or the default response format of the operation.</span></span>|  
|<span data-ttu-id="9eae1-117">defaultOutgoingResponseFormat</span><span class="sxs-lookup"><span data-stu-id="9eae1-117">defaultOutgoingResponseFormat</span></span>|<span data-ttu-id="9eae1-118">Varsayılan giden yanıt biçimini belirten bir özniteliği.</span><span class="sxs-lookup"><span data-stu-id="9eae1-118">An attribute that specifies the default outgoing response format.</span></span> <span data-ttu-id="9eae1-119">Bu özniteliktir <xref:System.ServiceModel.Web.WebMessageFormat> türü</span><span class="sxs-lookup"><span data-stu-id="9eae1-119">This attribute is of the <xref:System.ServiceModel.Web.WebMessageFormat> type</span></span>|  
|<span data-ttu-id="9eae1-120">helpEnabled</span><span class="sxs-lookup"><span data-stu-id="9eae1-120">helpEnabled</span></span>|<span data-ttu-id="9eae1-121">Uç nokta için HTTP Yardım sayfasının etkinleştirilip etkinleştirilmeyeceğini gösteren bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="9eae1-121">A Boolean value that indicates whether the HTTP help page is enabled for the endpoint.</span></span>|  
|<span data-ttu-id="9eae1-122">webEndpointType</span><span class="sxs-lookup"><span data-stu-id="9eae1-122">webEndpointType</span></span>|<span data-ttu-id="9eae1-123">Uç nokta türünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="9eae1-123">A string that specifies the type of the endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9eae1-124">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="9eae1-124">Child Elements</span></span>  
 <span data-ttu-id="9eae1-125">Yok.</span><span class="sxs-lookup"><span data-stu-id="9eae1-125">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9eae1-126">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="9eae1-126">Parent Elements</span></span>  
  
|<span data-ttu-id="9eae1-127">Öğe</span><span class="sxs-lookup"><span data-stu-id="9eae1-127">Element</span></span>|<span data-ttu-id="9eae1-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9eae1-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9eae1-129">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="9eae1-129">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="9eae1-130">Daha fazla (adresi, bağlama, anlaşma) kendi özellik sabit veya olan standart uç noktaları koleksiyonu uç noktaları biriyle önceden tanımlanmış.</span><span class="sxs-lookup"><span data-stu-id="9eae1-130">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9eae1-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9eae1-131">See also</span></span>
- <xref:System.ServiceModel.Description.WebHttpEndpoint>
- <xref:System.ServiceModel.Configuration.WebHttpEndpointElement>
