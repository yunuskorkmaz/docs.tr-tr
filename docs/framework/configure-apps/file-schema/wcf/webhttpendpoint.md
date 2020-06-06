---
title: <webHttpEndpoint>
ms.date: 03/30/2017
ms.assetid: ecaaeb6f-ebd0-411d-8b53-92477cd45347
ms.openlocfilehash: 8d4f55fd5b51ea77839b7fdbb930e937f5700417
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70854804"
---
# \<webHttpEndpoint>
<span data-ttu-id="b811c-101">Bu yapılandırma öğesi [\<webHttpBinding>](webhttpbinding.md) , otomatik olarak davranışını ekleyen bir sabit bağlamaya sahip standart uç nokta tanımlar [\<webHttp>](webhttp.md) .</span><span class="sxs-lookup"><span data-stu-id="b811c-101">This configuration element defines a standard endpoint with a fixed [\<webHttpBinding>](webhttpbinding.md) binding that automatically adds the [\<webHttp>](webhttp.md) behavior.</span></span> <span data-ttu-id="b811c-102">Bir REST hizmeti yazarken bu uç noktayı kullanın.</span><span class="sxs-lookup"><span data-stu-id="b811c-102">Use this endpoint when writing a REST service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webHttpEndpoint>**  
  
## <a name="syntax"></a><span data-ttu-id="b811c-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b811c-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b811c-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="b811c-104">Attributes and Elements</span></span>  
 <span data-ttu-id="b811c-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b811c-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b811c-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b811c-106">Attributes</span></span>  
  
|<span data-ttu-id="b811c-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="b811c-107">Attribute</span></span>|<span data-ttu-id="b811c-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b811c-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b811c-109">automaticFormatSelectionEnabled etkin</span><span class="sxs-lookup"><span data-stu-id="b811c-109">automaticFormatSelectionEnabled</span></span>|<span data-ttu-id="b811c-110">Otomatik biçim seçiminin etkin olup olmadığını gösteren bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="b811c-110">A Boolean value that indicates whether automatic format selection is enabled.</span></span><br /><br /> <span data-ttu-id="b811c-111">Otomatik Biçim Seçimi etkinleştirildiğinde altyapı, `Accept` istek iletisinin üstbilgisini ayrıştırır ve en uygun yanıt biçimini belirler.</span><span class="sxs-lookup"><span data-stu-id="b811c-111">When automatic format selection is enabled, the infrastructure parses the `Accept` header of the request message and determines the most appropriate response format.</span></span> <span data-ttu-id="b811c-112">`Accept`Üst bilgi uygun bir yanıt biçimi belirtmezse, altyapı `Content-Type` istek iletisini veya işlemin varsayılan yanıt biçimini kullanır.</span><span class="sxs-lookup"><span data-stu-id="b811c-112">If the `Accept` header does not specify a suitable response format, the infrastructure uses the `Content-Type` of the request message or the default response format of the operation.</span></span>|  
|<span data-ttu-id="b811c-113">defaultOutgoingResponseFormat</span><span class="sxs-lookup"><span data-stu-id="b811c-113">defaultOutgoingResponseFormat</span></span>|<span data-ttu-id="b811c-114">Varsayılan giden yanıt biçimini belirten bir özniteliği.</span><span class="sxs-lookup"><span data-stu-id="b811c-114">An attribute that specifies the default outgoing response format.</span></span> <span data-ttu-id="b811c-115">Bu öznitelik <xref:System.ServiceModel.Web.WebMessageFormat> türü</span><span class="sxs-lookup"><span data-stu-id="b811c-115">This attribute is of the <xref:System.ServiceModel.Web.WebMessageFormat> type</span></span>|  
|<span data-ttu-id="b811c-116">Yardım etkin</span><span class="sxs-lookup"><span data-stu-id="b811c-116">helpEnabled</span></span>|<span data-ttu-id="b811c-117">Uç nokta için HTTP yardım sayfasının etkinleştirilip etkinleştirilmediğini belirten bir Boolean değer.</span><span class="sxs-lookup"><span data-stu-id="b811c-117">A Boolean value that indicates whether the HTTP help page is enabled for the endpoint.</span></span>|  
|<span data-ttu-id="b811c-118">webEndpointType</span><span class="sxs-lookup"><span data-stu-id="b811c-118">webEndpointType</span></span>|<span data-ttu-id="b811c-119">Uç noktanın türünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="b811c-119">A string that specifies the type of the endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b811c-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="b811c-120">Child Elements</span></span>  
 <span data-ttu-id="b811c-121">Yok.</span><span class="sxs-lookup"><span data-stu-id="b811c-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b811c-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="b811c-122">Parent Elements</span></span>  
  
|<span data-ttu-id="b811c-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="b811c-123">Element</span></span>|<span data-ttu-id="b811c-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b811c-124">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="b811c-125">Özelliklerinden biri veya daha fazlası (adres, bağlama, sözleşme) düzeltilen, önceden tanımlanmış uç noktalar koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="b811c-125">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b811c-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b811c-126">See also</span></span>

- <xref:System.ServiceModel.Description.WebHttpEndpoint>
- <xref:System.ServiceModel.Configuration.WebHttpEndpointElement>
