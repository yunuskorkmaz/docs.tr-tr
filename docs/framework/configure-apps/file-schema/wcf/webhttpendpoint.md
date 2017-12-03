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
ms.openlocfilehash: ee055be8c4d2e53dc22a101529e5521add9b54a4
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltwebhttpendpointgt"></a><span data-ttu-id="941d5-102">&lt;webHttpEndpoint&gt;</span><span class="sxs-lookup"><span data-stu-id="941d5-102">&lt;webHttpEndpoint&gt;</span></span>
<span data-ttu-id="941d5-103">Bu yapılandırma öğesi bir sabit ile standart bir uç nokta tanımlayan [ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) otomatik olarak bağlama ekler [ \<webHttp >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md) davranışı.</span><span class="sxs-lookup"><span data-stu-id="941d5-103">This configuration element defines a standard endpoint with a fixed [\<webHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) binding that automatically adds the [\<webHttp>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md) behavior.</span></span> <span data-ttu-id="941d5-104">Bu uç noktaya bir REST hizmeti yazarken kullanın.</span><span class="sxs-lookup"><span data-stu-id="941d5-104">Use this endpoint when writing a REST service.</span></span>  
  
<span data-ttu-id="941d5-105">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="941d5-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="941d5-106">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="941d5-106">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="941d5-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="941d5-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="941d5-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="941d5-108">Attributes and Elements</span></span>  
 <span data-ttu-id="941d5-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="941d5-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="941d5-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="941d5-110">Attributes</span></span>  
  
|<span data-ttu-id="941d5-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="941d5-111">Attribute</span></span>|<span data-ttu-id="941d5-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="941d5-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="941d5-113">automaticFormatSelectionEnabled</span><span class="sxs-lookup"><span data-stu-id="941d5-113">automaticFormatSelectionEnabled</span></span>|<span data-ttu-id="941d5-114">Otomatik Biçim Seçimi etkin olup olmadığını gösteren bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="941d5-114">A Boolean value that indicates whether automatic format selection is enabled.</span></span><br /><br /> <span data-ttu-id="941d5-115">Otomatik Biçim Seçimi etkin olduğunda, altyapı ayrıştırır `Accept` istek iletisinin üstbilgi ve en uygun yanıt biçimi belirler.</span><span class="sxs-lookup"><span data-stu-id="941d5-115">When automatic format selection is enabled, the infrastructure parses the `Accept` header of the request message and determines the most appropriate response format.</span></span> <span data-ttu-id="941d5-116">Varsa `Accept` üstbilgisi, uygun yanıt biçimi belirtmiyor, altyapısını kullanan `Content-Type` istek iletisi ya da işlemi varsayılan yanıt biçimi.</span><span class="sxs-lookup"><span data-stu-id="941d5-116">If the `Accept` header does not specify a suitable response format, the infrastructure uses the `Content-Type` of the request message or the default response format of the operation.</span></span>|  
|<span data-ttu-id="941d5-117">defaultOutgoingResponseFormat</span><span class="sxs-lookup"><span data-stu-id="941d5-117">defaultOutgoingResponseFormat</span></span>|<span data-ttu-id="941d5-118">Varsayılan giden yanıt biçimi belirten bir özniteliği.</span><span class="sxs-lookup"><span data-stu-id="941d5-118">An attribute that specifies the default outgoing response format.</span></span> <span data-ttu-id="941d5-119">Bu özniteliktir <xref:System.ServiceModel.Web.WebMessageFormat> türü</span><span class="sxs-lookup"><span data-stu-id="941d5-119">This attribute is of the <xref:System.ServiceModel.Web.WebMessageFormat> type</span></span>|  
|<span data-ttu-id="941d5-120">helpEnabled</span><span class="sxs-lookup"><span data-stu-id="941d5-120">helpEnabled</span></span>|<span data-ttu-id="941d5-121">HTTP Yardım sayfası uç nokta için etkinleştirilip etkinleştirilmediğini gösteren bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="941d5-121">A Boolean value that indicates whether the HTTP help page is enabled for the endpoint.</span></span>|  
|<span data-ttu-id="941d5-122">webEndpointType</span><span class="sxs-lookup"><span data-stu-id="941d5-122">webEndpointType</span></span>|<span data-ttu-id="941d5-123">Uç nokta türünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="941d5-123">A string that specifies the type of the endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="941d5-124">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="941d5-124">Child Elements</span></span>  
 <span data-ttu-id="941d5-125">Yok.</span><span class="sxs-lookup"><span data-stu-id="941d5-125">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="941d5-126">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="941d5-126">Parent Elements</span></span>  
  
|<span data-ttu-id="941d5-127">Öğe</span><span class="sxs-lookup"><span data-stu-id="941d5-127">Element</span></span>|<span data-ttu-id="941d5-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="941d5-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="941d5-129">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="941d5-129">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="941d5-130">Standart uç noktalar koleksiyonu uç noktaları biriyle önceden tanımlanmış veya bunların özelliklerinin (adresi, bağlama, sözleşme) daha fazla sabit.</span><span class="sxs-lookup"><span data-stu-id="941d5-130">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="941d5-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="941d5-131">See Also</span></span>  
 <xref:System.ServiceModel.Description.WebHttpEndpoint>  
 <xref:System.ServiceModel.Configuration.WebHttpEndpointElement>
