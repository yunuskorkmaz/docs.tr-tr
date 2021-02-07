---
description: 'Hakkında daha fazla bilgi edinin: <webHttpEndpoint>'
title: <webHttpEndpoint>
ms.date: 03/30/2017
ms.assetid: ecaaeb6f-ebd0-411d-8b53-92477cd45347
ms.openlocfilehash: d1bcda1fc97dece833c8163e5facbefe614af0ac
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99682598"
---
# \<webHttpEndpoint>

<span data-ttu-id="1c901-102">Bu yapılandırma öğesi [\<webHttpBinding>](webhttpbinding.md) , otomatik olarak davranışını ekleyen bir sabit bağlamaya sahip standart uç nokta tanımlar [\<webHttp>](webhttp.md) .</span><span class="sxs-lookup"><span data-stu-id="1c901-102">This configuration element defines a standard endpoint with a fixed [\<webHttpBinding>](webhttpbinding.md) binding that automatically adds the [\<webHttp>](webhttp.md) behavior.</span></span> <span data-ttu-id="1c901-103">Bir REST hizmeti yazarken bu uç noktayı kullanın.</span><span class="sxs-lookup"><span data-stu-id="1c901-103">Use this endpoint when writing a REST service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webHttpEndpoint>**  
  
## <a name="syntax"></a><span data-ttu-id="1c901-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="1c901-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1c901-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="1c901-105">Attributes and Elements</span></span>  

 <span data-ttu-id="1c901-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1c901-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1c901-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="1c901-107">Attributes</span></span>  
  
|<span data-ttu-id="1c901-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="1c901-108">Attribute</span></span>|<span data-ttu-id="1c901-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1c901-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1c901-110">automaticFormatSelectionEnabled etkin</span><span class="sxs-lookup"><span data-stu-id="1c901-110">automaticFormatSelectionEnabled</span></span>|<span data-ttu-id="1c901-111">Otomatik biçim seçiminin etkin olup olmadığını gösteren bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="1c901-111">A Boolean value that indicates whether automatic format selection is enabled.</span></span><br /><br /> <span data-ttu-id="1c901-112">Otomatik Biçim Seçimi etkinleştirildiğinde altyapı, `Accept` istek iletisinin üstbilgisini ayrıştırır ve en uygun yanıt biçimini belirler.</span><span class="sxs-lookup"><span data-stu-id="1c901-112">When automatic format selection is enabled, the infrastructure parses the `Accept` header of the request message and determines the most appropriate response format.</span></span> <span data-ttu-id="1c901-113">`Accept`Üst bilgi uygun bir yanıt biçimi belirtmezse, altyapı `Content-Type` istek iletisini veya işlemin varsayılan yanıt biçimini kullanır.</span><span class="sxs-lookup"><span data-stu-id="1c901-113">If the `Accept` header does not specify a suitable response format, the infrastructure uses the `Content-Type` of the request message or the default response format of the operation.</span></span>|  
|<span data-ttu-id="1c901-114">defaultOutgoingResponseFormat</span><span class="sxs-lookup"><span data-stu-id="1c901-114">defaultOutgoingResponseFormat</span></span>|<span data-ttu-id="1c901-115">Varsayılan giden yanıt biçimini belirten bir özniteliği.</span><span class="sxs-lookup"><span data-stu-id="1c901-115">An attribute that specifies the default outgoing response format.</span></span> <span data-ttu-id="1c901-116">Bu öznitelik <xref:System.ServiceModel.Web.WebMessageFormat> türü</span><span class="sxs-lookup"><span data-stu-id="1c901-116">This attribute is of the <xref:System.ServiceModel.Web.WebMessageFormat> type</span></span>|  
|<span data-ttu-id="1c901-117">Yardım etkin</span><span class="sxs-lookup"><span data-stu-id="1c901-117">helpEnabled</span></span>|<span data-ttu-id="1c901-118">Uç nokta için HTTP yardım sayfasının etkinleştirilip etkinleştirilmediğini belirten bir Boolean değer.</span><span class="sxs-lookup"><span data-stu-id="1c901-118">A Boolean value that indicates whether the HTTP help page is enabled for the endpoint.</span></span>|  
|<span data-ttu-id="1c901-119">webEndpointType</span><span class="sxs-lookup"><span data-stu-id="1c901-119">webEndpointType</span></span>|<span data-ttu-id="1c901-120">Uç noktanın türünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="1c901-120">A string that specifies the type of the endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1c901-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="1c901-121">Child Elements</span></span>  

 <span data-ttu-id="1c901-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="1c901-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1c901-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="1c901-123">Parent Elements</span></span>  
  
|<span data-ttu-id="1c901-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="1c901-124">Element</span></span>|<span data-ttu-id="1c901-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1c901-125">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="1c901-126">Özelliklerinden biri veya daha fazlası (adres, bağlama, sözleşme) düzeltilen, önceden tanımlanmış uç noktalar koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="1c901-126">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1c901-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1c901-127">See also</span></span>

- <xref:System.ServiceModel.Description.WebHttpEndpoint>
- <xref:System.ServiceModel.Configuration.WebHttpEndpointElement>
