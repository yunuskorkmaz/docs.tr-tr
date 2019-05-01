---
title: <useRequestHeadersForMetadataAddress>
ms.date: 03/30/2017
ms.assetid: 679f0eae-f353-44d1-b42d-a9e247509774
ms.openlocfilehash: 969461d0e5bdc9f8c49b7a019a6000af5af77eec
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61788732"
---
# <a name="userequestheadersformetadataaddress"></a><span data-ttu-id="10308-101">\<useRequestHeadersForMetadataAddress ></span><span class="sxs-lookup"><span data-stu-id="10308-101">\<useRequestHeadersForMetadataAddress></span></span>
<span data-ttu-id="10308-102">İstek iletisi başlıklarından meta verisi adresi bilgilerine alınmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="10308-102">Enables the retrieval of metadata address information from the request message headers.</span></span>  
  
<span data-ttu-id="10308-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="10308-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="10308-104">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="10308-104">\<behaviors></span></span>  
<span data-ttu-id="10308-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="10308-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="10308-106">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="10308-106">\<behavior></span></span>  
<span data-ttu-id="10308-107">\<useRequestHeadersForMetadataAddress ></span><span class="sxs-lookup"><span data-stu-id="10308-107">\<useRequestHeadersForMetadataAddress></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10308-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="10308-108">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http"
         port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="10308-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="10308-109">Attributes and Elements</span></span>  
 <span data-ttu-id="10308-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="10308-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="10308-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="10308-111">Attributes</span></span>  
 <span data-ttu-id="10308-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="10308-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="10308-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="10308-113">Child Elements</span></span>  
  
|<span data-ttu-id="10308-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="10308-114">Element</span></span>|<span data-ttu-id="10308-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="10308-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="10308-116">\<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="10308-116">\<defaultPorts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/defaultports.md)|<span data-ttu-id="10308-117">İstemci uygulamasının dinleyeceği, varsayılan iletişim bitiş noktalarını listeleyen varsayılan bağlantı noktaları koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="10308-117">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="10308-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="10308-118">Parent Elements</span></span>  
  
|<span data-ttu-id="10308-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="10308-119">Element</span></span>|<span data-ttu-id="10308-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="10308-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="10308-121">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="10308-121">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="10308-122">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="10308-122">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="10308-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="10308-123">See also</span></span>

- <xref:System.ServiceModel.Configuration.UseRequestHeadersForMetadataAddressElement>
