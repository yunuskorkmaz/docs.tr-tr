---
title: '&lt;webHttpEndpoint&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ecaaeb6f-ebd0-411d-8b53-92477cd45347
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fc45511e0e7b4644704a834f0bc08d64ff3367f3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltwebhttpendpointgt"></a><span data-ttu-id="fcd24-102">&lt;webHttpEndpoint&gt;</span><span class="sxs-lookup"><span data-stu-id="fcd24-102">&lt;webHttpEndpoint&gt;</span></span>
<span data-ttu-id="fcd24-103">Bu yapılandırma öğesi bir sabit ile standart bir uç nokta tanımlayan [ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) otomatik olarak bağlama ekler [ \<webHttp >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md) davranışı.</span><span class="sxs-lookup"><span data-stu-id="fcd24-103">This configuration element defines a standard endpoint with a fixed [\<webHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) binding that automatically adds the [\<webHttp>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md) behavior.</span></span> <span data-ttu-id="fcd24-104">Bu uç noktaya bir REST hizmeti yazarken kullanın.</span><span class="sxs-lookup"><span data-stu-id="fcd24-104">Use this endpoint when writing a REST service.</span></span>  
  
<span data-ttu-id="fcd24-105">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="fcd24-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="fcd24-106">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="fcd24-106">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fcd24-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fcd24-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>
    <webHttpEndpoint>
      <standardEndpoint automaticFormatSelectionEnabled="String" 
                        defaultOutgoingResponseFormat="Xml/Json" 
                        helpEnabled="Boolean" 
                        webEndpointType="String"/>
    </webHttpEndpoint>
  </standardEndpoints>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fcd24-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="fcd24-108">Attributes and Elements</span></span>  
 <span data-ttu-id="fcd24-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="fcd24-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fcd24-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="fcd24-110">Attributes</span></span>  
  
|<span data-ttu-id="fcd24-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="fcd24-111">Attribute</span></span>|<span data-ttu-id="fcd24-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fcd24-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fcd24-113">automaticFormatSelectionEnabled</span><span class="sxs-lookup"><span data-stu-id="fcd24-113">automaticFormatSelectionEnabled</span></span>|<span data-ttu-id="fcd24-114">Otomatik Biçim Seçimi etkin olup olmadığını gösteren bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="fcd24-114">A Boolean value that indicates whether automatic format selection is enabled.</span></span><br /><br /> <span data-ttu-id="fcd24-115">Otomatik Biçim Seçimi etkin olduğunda, altyapı ayrıştırır `Accept` istek iletisinin üstbilgi ve en uygun yanıt biçimi belirler.</span><span class="sxs-lookup"><span data-stu-id="fcd24-115">When automatic format selection is enabled, the infrastructure parses the `Accept` header of the request message and determines the most appropriate response format.</span></span> <span data-ttu-id="fcd24-116">Varsa `Accept` üstbilgisi, uygun yanıt biçimi belirtmiyor, altyapısını kullanan `Content-Type` istek iletisi ya da işlemi varsayılan yanıt biçimi.</span><span class="sxs-lookup"><span data-stu-id="fcd24-116">If the `Accept` header does not specify a suitable response format, the infrastructure uses the `Content-Type` of the request message or the default response format of the operation.</span></span>|  
|<span data-ttu-id="fcd24-117">defaultOutgoingResponseFormat</span><span class="sxs-lookup"><span data-stu-id="fcd24-117">defaultOutgoingResponseFormat</span></span>|<span data-ttu-id="fcd24-118">Varsayılan giden yanıt biçimi belirten bir özniteliği.</span><span class="sxs-lookup"><span data-stu-id="fcd24-118">An attribute that specifies the default outgoing response format.</span></span> <span data-ttu-id="fcd24-119">Bu özniteliktir <xref:System.ServiceModel.Web.WebMessageFormat> türü</span><span class="sxs-lookup"><span data-stu-id="fcd24-119">This attribute is of the <xref:System.ServiceModel.Web.WebMessageFormat> type</span></span>|  
|<span data-ttu-id="fcd24-120">helpEnabled</span><span class="sxs-lookup"><span data-stu-id="fcd24-120">helpEnabled</span></span>|<span data-ttu-id="fcd24-121">HTTP Yardım sayfası uç nokta için etkinleştirilip etkinleştirilmediğini gösteren bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="fcd24-121">A Boolean value that indicates whether the HTTP help page is enabled for the endpoint.</span></span>|  
|<span data-ttu-id="fcd24-122">webEndpointType</span><span class="sxs-lookup"><span data-stu-id="fcd24-122">webEndpointType</span></span>|<span data-ttu-id="fcd24-123">Uç nokta türünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="fcd24-123">A string that specifies the type of the endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fcd24-124">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="fcd24-124">Child Elements</span></span>  
 <span data-ttu-id="fcd24-125">Yok.</span><span class="sxs-lookup"><span data-stu-id="fcd24-125">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fcd24-126">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="fcd24-126">Parent Elements</span></span>  
  
|<span data-ttu-id="fcd24-127">Öğe</span><span class="sxs-lookup"><span data-stu-id="fcd24-127">Element</span></span>|<span data-ttu-id="fcd24-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fcd24-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fcd24-129">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="fcd24-129">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="fcd24-130">Standart uç noktalar koleksiyonu uç noktaları biriyle önceden tanımlanmış veya bunların özelliklerinin (adresi, bağlama, sözleşme) daha fazla sabit.</span><span class="sxs-lookup"><span data-stu-id="fcd24-130">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fcd24-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fcd24-131">See Also</span></span>  
 <xref:System.ServiceModel.Description.WebHttpEndpoint>  
 <xref:System.ServiceModel.Configuration.WebHttpEndpointElement>
