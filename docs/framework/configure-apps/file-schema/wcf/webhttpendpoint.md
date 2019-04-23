---
title: <webHttpEndpoint>
ms.date: 03/30/2017
ms.assetid: ecaaeb6f-ebd0-411d-8b53-92477cd45347
ms.openlocfilehash: 6fb31fca6ac38f6cb92ef087cc277a4d5066521c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59182461"
---
# <a name="webhttpendpoint"></a><span data-ttu-id="37c84-101">\<webHttpEndpoint ></span><span class="sxs-lookup"><span data-stu-id="37c84-101">\<webHttpEndpoint></span></span>
<span data-ttu-id="37c84-102">Bu yapılandırma öğesi ile bir sabit bir standart uç nokta tanımlar [ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) otomatik olarak bağlama ekler [ \<webHttp >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md) davranışı.</span><span class="sxs-lookup"><span data-stu-id="37c84-102">This configuration element defines a standard endpoint with a fixed [\<webHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) binding that automatically adds the [\<webHttp>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md) behavior.</span></span> <span data-ttu-id="37c84-103">Bir REST hizmeti yazarken Bu uç noktayı kullanın.</span><span class="sxs-lookup"><span data-stu-id="37c84-103">Use this endpoint when writing a REST service.</span></span>  
  
<span data-ttu-id="37c84-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="37c84-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="37c84-105">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="37c84-105">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37c84-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="37c84-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="37c84-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="37c84-107">Attributes and Elements</span></span>  
 <span data-ttu-id="37c84-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="37c84-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="37c84-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="37c84-109">Attributes</span></span>  
  
|<span data-ttu-id="37c84-110">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="37c84-110">Attribute</span></span>|<span data-ttu-id="37c84-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="37c84-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="37c84-112">automaticFormatSelectionEnabled</span><span class="sxs-lookup"><span data-stu-id="37c84-112">automaticFormatSelectionEnabled</span></span>|<span data-ttu-id="37c84-113">Otomatik Biçim Seçimi etkin olup olmadığını gösteren bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="37c84-113">A Boolean value that indicates whether automatic format selection is enabled.</span></span><br /><br /> <span data-ttu-id="37c84-114">Otomatik Biçim Seçimi etkinleştirildiğinde altyapı ayrıştırır `Accept` istek iletisinin üst bilgi ve en uygun yanıt biçimi belirler.</span><span class="sxs-lookup"><span data-stu-id="37c84-114">When automatic format selection is enabled, the infrastructure parses the `Accept` header of the request message and determines the most appropriate response format.</span></span> <span data-ttu-id="37c84-115">Varsa `Accept` üstbilgisi, uygun yanıt biçimi belirtmiyor, altyapısını kullanan `Content-Type` istek iletisi veya işlemin varsayılan yanıt biçimi.</span><span class="sxs-lookup"><span data-stu-id="37c84-115">If the `Accept` header does not specify a suitable response format, the infrastructure uses the `Content-Type` of the request message or the default response format of the operation.</span></span>|  
|<span data-ttu-id="37c84-116">defaultOutgoingResponseFormat</span><span class="sxs-lookup"><span data-stu-id="37c84-116">defaultOutgoingResponseFormat</span></span>|<span data-ttu-id="37c84-117">Varsayılan giden yanıt biçimini belirten bir özniteliği.</span><span class="sxs-lookup"><span data-stu-id="37c84-117">An attribute that specifies the default outgoing response format.</span></span> <span data-ttu-id="37c84-118">Bu özniteliktir <xref:System.ServiceModel.Web.WebMessageFormat> türü</span><span class="sxs-lookup"><span data-stu-id="37c84-118">This attribute is of the <xref:System.ServiceModel.Web.WebMessageFormat> type</span></span>|  
|<span data-ttu-id="37c84-119">helpEnabled</span><span class="sxs-lookup"><span data-stu-id="37c84-119">helpEnabled</span></span>|<span data-ttu-id="37c84-120">Uç nokta için HTTP Yardım sayfasının etkinleştirilip etkinleştirilmeyeceğini gösteren bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="37c84-120">A Boolean value that indicates whether the HTTP help page is enabled for the endpoint.</span></span>|  
|<span data-ttu-id="37c84-121">webEndpointType</span><span class="sxs-lookup"><span data-stu-id="37c84-121">webEndpointType</span></span>|<span data-ttu-id="37c84-122">Uç nokta türünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="37c84-122">A string that specifies the type of the endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="37c84-123">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="37c84-123">Child Elements</span></span>  
 <span data-ttu-id="37c84-124">Yok.</span><span class="sxs-lookup"><span data-stu-id="37c84-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="37c84-125">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="37c84-125">Parent Elements</span></span>  
  
|<span data-ttu-id="37c84-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="37c84-126">Element</span></span>|<span data-ttu-id="37c84-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="37c84-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="37c84-128">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="37c84-128">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="37c84-129">Daha fazla (adresi, bağlama, anlaşma) kendi özellik sabit veya olan standart uç noktaları koleksiyonu uç noktaları biriyle önceden tanımlanmış.</span><span class="sxs-lookup"><span data-stu-id="37c84-129">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="37c84-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="37c84-130">See also</span></span>

- <xref:System.ServiceModel.Description.WebHttpEndpoint>
- <xref:System.ServiceModel.Configuration.WebHttpEndpointElement>
