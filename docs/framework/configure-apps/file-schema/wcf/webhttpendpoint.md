---
title: <webHttpEndpoint>
ms.date: 03/30/2017
ms.assetid: ecaaeb6f-ebd0-411d-8b53-92477cd45347
ms.openlocfilehash: 866be522cb1c64142227a8d6a1a8f88551ca9105
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940479"
---
# <a name="webhttpendpoint"></a><span data-ttu-id="55958-101">\<webHttpEndpoint ></span><span class="sxs-lookup"><span data-stu-id="55958-101">\<webHttpEndpoint></span></span>
<span data-ttu-id="55958-102">Bu yapılandırma öğesi [ ,\<Web http >](webhttp.md) davranışını otomatik olarak ekleyen bir fixed [ \<WebHttpBinding >](webhttpbinding.md) bağlaması ile standart bir uç nokta tanımlar.</span><span class="sxs-lookup"><span data-stu-id="55958-102">This configuration element defines a standard endpoint with a fixed [\<webHttpBinding>](webhttpbinding.md) binding that automatically adds the [\<webHttp>](webhttp.md) behavior.</span></span> <span data-ttu-id="55958-103">Bir REST hizmeti yazarken bu uç noktayı kullanın.</span><span class="sxs-lookup"><span data-stu-id="55958-103">Use this endpoint when writing a REST service.</span></span>  
  
<span data-ttu-id="55958-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="55958-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="55958-105">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="55958-105">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55958-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="55958-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="55958-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="55958-107">Attributes and Elements</span></span>  
 <span data-ttu-id="55958-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="55958-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="55958-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="55958-109">Attributes</span></span>  
  
|<span data-ttu-id="55958-110">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="55958-110">Attribute</span></span>|<span data-ttu-id="55958-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="55958-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="55958-112">automaticFormatSelectionEnabled etkin</span><span class="sxs-lookup"><span data-stu-id="55958-112">automaticFormatSelectionEnabled</span></span>|<span data-ttu-id="55958-113">Otomatik biçim seçiminin etkin olup olmadığını gösteren bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="55958-113">A Boolean value that indicates whether automatic format selection is enabled.</span></span><br /><br /> <span data-ttu-id="55958-114">Otomatik Biçim Seçimi etkinleştirildiğinde altyapı, istek iletisinin `Accept` üstbilgisini ayrıştırır ve en uygun yanıt biçimini belirler.</span><span class="sxs-lookup"><span data-stu-id="55958-114">When automatic format selection is enabled, the infrastructure parses the `Accept` header of the request message and determines the most appropriate response format.</span></span> <span data-ttu-id="55958-115">Üst bilgi uygun bir yanıt biçimi belirtmezse, altyapı istek iletisini veya işlemin varsayılan `Content-Type` yanıt biçimini kullanır. `Accept`</span><span class="sxs-lookup"><span data-stu-id="55958-115">If the `Accept` header does not specify a suitable response format, the infrastructure uses the `Content-Type` of the request message or the default response format of the operation.</span></span>|  
|<span data-ttu-id="55958-116">defaultOutgoingResponseFormat</span><span class="sxs-lookup"><span data-stu-id="55958-116">defaultOutgoingResponseFormat</span></span>|<span data-ttu-id="55958-117">Varsayılan giden yanıt biçimini belirten bir özniteliği.</span><span class="sxs-lookup"><span data-stu-id="55958-117">An attribute that specifies the default outgoing response format.</span></span> <span data-ttu-id="55958-118">Bu öznitelik <xref:System.ServiceModel.Web.WebMessageFormat> türü</span><span class="sxs-lookup"><span data-stu-id="55958-118">This attribute is of the <xref:System.ServiceModel.Web.WebMessageFormat> type</span></span>|  
|<span data-ttu-id="55958-119">Yardım etkin</span><span class="sxs-lookup"><span data-stu-id="55958-119">helpEnabled</span></span>|<span data-ttu-id="55958-120">Uç nokta için HTTP yardım sayfasının etkinleştirilip etkinleştirilmediğini belirten bir Boolean değer.</span><span class="sxs-lookup"><span data-stu-id="55958-120">A Boolean value that indicates whether the HTTP help page is enabled for the endpoint.</span></span>|  
|<span data-ttu-id="55958-121">webEndpointType</span><span class="sxs-lookup"><span data-stu-id="55958-121">webEndpointType</span></span>|<span data-ttu-id="55958-122">Uç noktanın türünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="55958-122">A string that specifies the type of the endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="55958-123">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="55958-123">Child Elements</span></span>  
 <span data-ttu-id="55958-124">Yok.</span><span class="sxs-lookup"><span data-stu-id="55958-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="55958-125">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="55958-125">Parent Elements</span></span>  
  
|<span data-ttu-id="55958-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="55958-126">Element</span></span>|<span data-ttu-id="55958-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="55958-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="55958-128">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="55958-128">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="55958-129">Özelliklerinden biri veya daha fazlası (adres, bağlama, sözleşme) düzeltilen, önceden tanımlanmış uç noktalar koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="55958-129">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="55958-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="55958-130">See also</span></span>

- <xref:System.ServiceModel.Description.WebHttpEndpoint>
- <xref:System.ServiceModel.Configuration.WebHttpEndpointElement>
