---
title: <webHttpEndpoint>
ms.date: 03/30/2017
ms.assetid: ecaaeb6f-ebd0-411d-8b53-92477cd45347
ms.openlocfilehash: 3282871bf8dbd25726ada7003d3066b9a42e2366
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91177988"
---
# \<webHttpEndpoint>

<span data-ttu-id="a5f38-101">Bu yapılandırma öğesi [\<webHttpBinding>](webhttpbinding.md) , otomatik olarak davranışını ekleyen bir sabit bağlamaya sahip standart uç nokta tanımlar [\<webHttp>](webhttp.md) .</span><span class="sxs-lookup"><span data-stu-id="a5f38-101">This configuration element defines a standard endpoint with a fixed [\<webHttpBinding>](webhttpbinding.md) binding that automatically adds the [\<webHttp>](webhttp.md) behavior.</span></span> <span data-ttu-id="a5f38-102">Bir REST hizmeti yazarken bu uç noktayı kullanın.</span><span class="sxs-lookup"><span data-stu-id="a5f38-102">Use this endpoint when writing a REST service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webHttpEndpoint>**  
  
## <a name="syntax"></a><span data-ttu-id="a5f38-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="a5f38-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a5f38-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a5f38-104">Attributes and Elements</span></span>  

 <span data-ttu-id="a5f38-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a5f38-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a5f38-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a5f38-106">Attributes</span></span>  
  
|<span data-ttu-id="a5f38-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="a5f38-107">Attribute</span></span>|<span data-ttu-id="a5f38-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a5f38-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a5f38-109">automaticFormatSelectionEnabled etkin</span><span class="sxs-lookup"><span data-stu-id="a5f38-109">automaticFormatSelectionEnabled</span></span>|<span data-ttu-id="a5f38-110">Otomatik biçim seçiminin etkin olup olmadığını gösteren bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="a5f38-110">A Boolean value that indicates whether automatic format selection is enabled.</span></span><br /><br /> <span data-ttu-id="a5f38-111">Otomatik Biçim Seçimi etkinleştirildiğinde altyapı, `Accept` istek iletisinin üstbilgisini ayrıştırır ve en uygun yanıt biçimini belirler.</span><span class="sxs-lookup"><span data-stu-id="a5f38-111">When automatic format selection is enabled, the infrastructure parses the `Accept` header of the request message and determines the most appropriate response format.</span></span> <span data-ttu-id="a5f38-112">`Accept`Üst bilgi uygun bir yanıt biçimi belirtmezse, altyapı `Content-Type` istek iletisini veya işlemin varsayılan yanıt biçimini kullanır.</span><span class="sxs-lookup"><span data-stu-id="a5f38-112">If the `Accept` header does not specify a suitable response format, the infrastructure uses the `Content-Type` of the request message or the default response format of the operation.</span></span>|  
|<span data-ttu-id="a5f38-113">defaultOutgoingResponseFormat</span><span class="sxs-lookup"><span data-stu-id="a5f38-113">defaultOutgoingResponseFormat</span></span>|<span data-ttu-id="a5f38-114">Varsayılan giden yanıt biçimini belirten bir özniteliği.</span><span class="sxs-lookup"><span data-stu-id="a5f38-114">An attribute that specifies the default outgoing response format.</span></span> <span data-ttu-id="a5f38-115">Bu öznitelik <xref:System.ServiceModel.Web.WebMessageFormat> türü</span><span class="sxs-lookup"><span data-stu-id="a5f38-115">This attribute is of the <xref:System.ServiceModel.Web.WebMessageFormat> type</span></span>|  
|<span data-ttu-id="a5f38-116">Yardım etkin</span><span class="sxs-lookup"><span data-stu-id="a5f38-116">helpEnabled</span></span>|<span data-ttu-id="a5f38-117">Uç nokta için HTTP yardım sayfasının etkinleştirilip etkinleştirilmediğini belirten bir Boolean değer.</span><span class="sxs-lookup"><span data-stu-id="a5f38-117">A Boolean value that indicates whether the HTTP help page is enabled for the endpoint.</span></span>|  
|<span data-ttu-id="a5f38-118">webEndpointType</span><span class="sxs-lookup"><span data-stu-id="a5f38-118">webEndpointType</span></span>|<span data-ttu-id="a5f38-119">Uç noktanın türünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="a5f38-119">A string that specifies the type of the endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a5f38-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a5f38-120">Child Elements</span></span>  

 <span data-ttu-id="a5f38-121">Yok.</span><span class="sxs-lookup"><span data-stu-id="a5f38-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a5f38-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a5f38-122">Parent Elements</span></span>  
  
|<span data-ttu-id="a5f38-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="a5f38-123">Element</span></span>|<span data-ttu-id="a5f38-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a5f38-124">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="a5f38-125">Özelliklerinden biri veya daha fazlası (adres, bağlama, sözleşme) düzeltilen, önceden tanımlanmış uç noktalar koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="a5f38-125">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a5f38-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a5f38-126">See also</span></span>

- <xref:System.ServiceModel.Description.WebHttpEndpoint>
- <xref:System.ServiceModel.Configuration.WebHttpEndpointElement>
