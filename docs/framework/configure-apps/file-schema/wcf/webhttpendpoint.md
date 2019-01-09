---
title: '&lt;webHttpEndpoint&gt;'
ms.date: 03/30/2017
ms.assetid: ecaaeb6f-ebd0-411d-8b53-92477cd45347
ms.openlocfilehash: ee14ce23370675782f4c25385c1786fdce11eba0
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54151975"
---
# <a name="ltwebhttpendpointgt"></a><span data-ttu-id="621a4-102">&lt;webHttpEndpoint&gt;</span><span class="sxs-lookup"><span data-stu-id="621a4-102">&lt;webHttpEndpoint&gt;</span></span>
<span data-ttu-id="621a4-103">Bu yapılandırma öğesi ile bir sabit bir standart uç nokta tanımlar [ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) otomatik olarak bağlama ekler [ \<webHttp >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md) davranışı.</span><span class="sxs-lookup"><span data-stu-id="621a4-103">This configuration element defines a standard endpoint with a fixed [\<webHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) binding that automatically adds the [\<webHttp>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md) behavior.</span></span> <span data-ttu-id="621a4-104">Bir REST hizmeti yazarken Bu uç noktayı kullanın.</span><span class="sxs-lookup"><span data-stu-id="621a4-104">Use this endpoint when writing a REST service.</span></span>  
  
<span data-ttu-id="621a4-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="621a4-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="621a4-106">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="621a4-106">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="621a4-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="621a4-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="621a4-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="621a4-108">Attributes and Elements</span></span>  
 <span data-ttu-id="621a4-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="621a4-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="621a4-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="621a4-110">Attributes</span></span>  
  
|<span data-ttu-id="621a4-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="621a4-111">Attribute</span></span>|<span data-ttu-id="621a4-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="621a4-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="621a4-113">automaticFormatSelectionEnabled</span><span class="sxs-lookup"><span data-stu-id="621a4-113">automaticFormatSelectionEnabled</span></span>|<span data-ttu-id="621a4-114">Otomatik Biçim Seçimi etkin olup olmadığını gösteren bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="621a4-114">A Boolean value that indicates whether automatic format selection is enabled.</span></span><br /><br /> <span data-ttu-id="621a4-115">Otomatik Biçim Seçimi etkinleştirildiğinde altyapı ayrıştırır `Accept` istek iletisinin üst bilgi ve en uygun yanıt biçimi belirler.</span><span class="sxs-lookup"><span data-stu-id="621a4-115">When automatic format selection is enabled, the infrastructure parses the `Accept` header of the request message and determines the most appropriate response format.</span></span> <span data-ttu-id="621a4-116">Varsa `Accept` üstbilgisi, uygun yanıt biçimi belirtmiyor, altyapısını kullanan `Content-Type` istek iletisi veya işlemin varsayılan yanıt biçimi.</span><span class="sxs-lookup"><span data-stu-id="621a4-116">If the `Accept` header does not specify a suitable response format, the infrastructure uses the `Content-Type` of the request message or the default response format of the operation.</span></span>|  
|<span data-ttu-id="621a4-117">defaultOutgoingResponseFormat</span><span class="sxs-lookup"><span data-stu-id="621a4-117">defaultOutgoingResponseFormat</span></span>|<span data-ttu-id="621a4-118">Varsayılan giden yanıt biçimini belirten bir özniteliği.</span><span class="sxs-lookup"><span data-stu-id="621a4-118">An attribute that specifies the default outgoing response format.</span></span> <span data-ttu-id="621a4-119">Bu özniteliktir <xref:System.ServiceModel.Web.WebMessageFormat> türü</span><span class="sxs-lookup"><span data-stu-id="621a4-119">This attribute is of the <xref:System.ServiceModel.Web.WebMessageFormat> type</span></span>|  
|<span data-ttu-id="621a4-120">helpEnabled</span><span class="sxs-lookup"><span data-stu-id="621a4-120">helpEnabled</span></span>|<span data-ttu-id="621a4-121">Uç nokta için HTTP Yardım sayfasının etkinleştirilip etkinleştirilmeyeceğini gösteren bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="621a4-121">A Boolean value that indicates whether the HTTP help page is enabled for the endpoint.</span></span>|  
|<span data-ttu-id="621a4-122">webEndpointType</span><span class="sxs-lookup"><span data-stu-id="621a4-122">webEndpointType</span></span>|<span data-ttu-id="621a4-123">Uç nokta türünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="621a4-123">A string that specifies the type of the endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="621a4-124">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="621a4-124">Child Elements</span></span>  
 <span data-ttu-id="621a4-125">Yok.</span><span class="sxs-lookup"><span data-stu-id="621a4-125">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="621a4-126">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="621a4-126">Parent Elements</span></span>  
  
|<span data-ttu-id="621a4-127">Öğe</span><span class="sxs-lookup"><span data-stu-id="621a4-127">Element</span></span>|<span data-ttu-id="621a4-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="621a4-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="621a4-129">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="621a4-129">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="621a4-130">Daha fazla (adresi, bağlama, anlaşma) kendi özellik sabit veya olan standart uç noktaları koleksiyonu uç noktaları biriyle önceden tanımlanmış.</span><span class="sxs-lookup"><span data-stu-id="621a4-130">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="621a4-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="621a4-131">See Also</span></span>  
 <xref:System.ServiceModel.Description.WebHttpEndpoint>  
 <xref:System.ServiceModel.Configuration.WebHttpEndpointElement>
