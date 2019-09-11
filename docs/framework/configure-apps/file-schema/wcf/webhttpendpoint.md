---
title: <webHttpEndpoint>
ms.date: 03/30/2017
ms.assetid: ecaaeb6f-ebd0-411d-8b53-92477cd45347
ms.openlocfilehash: 8d4f55fd5b51ea77839b7fdbb930e937f5700417
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854804"
---
# <a name="webhttpendpoint"></a><span data-ttu-id="31821-101">\<webHttpEndpoint ></span><span class="sxs-lookup"><span data-stu-id="31821-101">\<webHttpEndpoint></span></span>
<span data-ttu-id="31821-102">Bu yapılandırma öğesi [ ,\<Web http >](webhttp.md) davranışını otomatik olarak ekleyen bir fixed [ \<WebHttpBinding >](webhttpbinding.md) bağlaması ile standart bir uç nokta tanımlar.</span><span class="sxs-lookup"><span data-stu-id="31821-102">This configuration element defines a standard endpoint with a fixed [\<webHttpBinding>](webhttpbinding.md) binding that automatically adds the [\<webHttp>](webhttp.md) behavior.</span></span> <span data-ttu-id="31821-103">Bir REST hizmeti yazarken bu uç noktayı kullanın.</span><span class="sxs-lookup"><span data-stu-id="31821-103">Use this endpoint when writing a REST service.</span></span>  
  
<span data-ttu-id="31821-104">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="31821-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="31821-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="31821-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="31821-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<standardEndpoints >** ](standardendpoints.md)</span><span class="sxs-lookup"><span data-stu-id="31821-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)</span></span>\
<span data-ttu-id="31821-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<webHttpEndpoint >**</span><span class="sxs-lookup"><span data-stu-id="31821-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webHttpEndpoint>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31821-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="31821-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="31821-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="31821-109">Attributes and Elements</span></span>  
 <span data-ttu-id="31821-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="31821-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="31821-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="31821-111">Attributes</span></span>  
  
|<span data-ttu-id="31821-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="31821-112">Attribute</span></span>|<span data-ttu-id="31821-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="31821-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="31821-114">automaticFormatSelectionEnabled etkin</span><span class="sxs-lookup"><span data-stu-id="31821-114">automaticFormatSelectionEnabled</span></span>|<span data-ttu-id="31821-115">Otomatik biçim seçiminin etkin olup olmadığını gösteren bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="31821-115">A Boolean value that indicates whether automatic format selection is enabled.</span></span><br /><br /> <span data-ttu-id="31821-116">Otomatik Biçim Seçimi etkinleştirildiğinde altyapı, istek iletisinin `Accept` üstbilgisini ayrıştırır ve en uygun yanıt biçimini belirler.</span><span class="sxs-lookup"><span data-stu-id="31821-116">When automatic format selection is enabled, the infrastructure parses the `Accept` header of the request message and determines the most appropriate response format.</span></span> <span data-ttu-id="31821-117">Üst bilgi uygun bir yanıt biçimi belirtmezse, altyapı istek iletisini veya işlemin varsayılan `Content-Type` yanıt biçimini kullanır. `Accept`</span><span class="sxs-lookup"><span data-stu-id="31821-117">If the `Accept` header does not specify a suitable response format, the infrastructure uses the `Content-Type` of the request message or the default response format of the operation.</span></span>|  
|<span data-ttu-id="31821-118">defaultOutgoingResponseFormat</span><span class="sxs-lookup"><span data-stu-id="31821-118">defaultOutgoingResponseFormat</span></span>|<span data-ttu-id="31821-119">Varsayılan giden yanıt biçimini belirten bir özniteliği.</span><span class="sxs-lookup"><span data-stu-id="31821-119">An attribute that specifies the default outgoing response format.</span></span> <span data-ttu-id="31821-120">Bu öznitelik <xref:System.ServiceModel.Web.WebMessageFormat> türü</span><span class="sxs-lookup"><span data-stu-id="31821-120">This attribute is of the <xref:System.ServiceModel.Web.WebMessageFormat> type</span></span>|  
|<span data-ttu-id="31821-121">Yardım etkin</span><span class="sxs-lookup"><span data-stu-id="31821-121">helpEnabled</span></span>|<span data-ttu-id="31821-122">Uç nokta için HTTP yardım sayfasının etkinleştirilip etkinleştirilmediğini belirten bir Boolean değer.</span><span class="sxs-lookup"><span data-stu-id="31821-122">A Boolean value that indicates whether the HTTP help page is enabled for the endpoint.</span></span>|  
|<span data-ttu-id="31821-123">webEndpointType</span><span class="sxs-lookup"><span data-stu-id="31821-123">webEndpointType</span></span>|<span data-ttu-id="31821-124">Uç noktanın türünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="31821-124">A string that specifies the type of the endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="31821-125">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="31821-125">Child Elements</span></span>  
 <span data-ttu-id="31821-126">Yok.</span><span class="sxs-lookup"><span data-stu-id="31821-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="31821-127">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="31821-127">Parent Elements</span></span>  
  
|<span data-ttu-id="31821-128">Öğe</span><span class="sxs-lookup"><span data-stu-id="31821-128">Element</span></span>|<span data-ttu-id="31821-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="31821-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="31821-130">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="31821-130">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="31821-131">Özelliklerinden biri veya daha fazlası (adres, bağlama, sözleşme) düzeltilen, önceden tanımlanmış uç noktalar koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="31821-131">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="31821-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="31821-132">See also</span></span>

- <xref:System.ServiceModel.Description.WebHttpEndpoint>
- <xref:System.ServiceModel.Configuration.WebHttpEndpointElement>
