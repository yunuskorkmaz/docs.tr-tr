---
title: '&lt;ana bilgisayar&gt;'
ms.date: 03/30/2017
ms.assetid: be566d55-9d50-4b2e-985d-52a5cc26cbbb
ms.openlocfilehash: 9c48fff7473449192887bfd8cc201dd87cb4e7f7
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="lthostgt"></a><span data-ttu-id="06d3f-102">&lt;ana bilgisayar&gt;</span><span class="sxs-lookup"><span data-stu-id="06d3f-102">&lt;host&gt;</span></span>
<span data-ttu-id="06d3f-103">Hizmet ana bilgisayarı ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="06d3f-103">Specifies settings for a service host.</span></span>  
  
 <span data-ttu-id="06d3f-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="06d3f-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="06d3f-105">\<Hizmetleri ></span><span class="sxs-lookup"><span data-stu-id="06d3f-105">\<services></span></span>  
<span data-ttu-id="06d3f-106">\<Hizmet ></span><span class="sxs-lookup"><span data-stu-id="06d3f-106">\<service></span></span>  
<span data-ttu-id="06d3f-107">\<ana bilgisayar ></span><span class="sxs-lookup"><span data-stu-id="06d3f-107">\<host></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06d3f-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="06d3f-108">Syntax</span></span>  
  
```xml  
<host>  
      <baseAddresses>  
         <baseAddress baseAddress="string" />  
      </baseAddresses>  
      <timeOuts closeTimeout="TimeSpan"  
         openTimeout="TimeSpan" >  
</host>  
```  
  
## <a name="type"></a><span data-ttu-id="06d3f-109">Tür</span><span class="sxs-lookup"><span data-stu-id="06d3f-109">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="06d3f-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="06d3f-110">Attributes and Elements</span></span>  
 <span data-ttu-id="06d3f-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="06d3f-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="06d3f-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="06d3f-112">Attributes</span></span>  
 <span data-ttu-id="06d3f-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="06d3f-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="06d3f-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="06d3f-114">Child Elements</span></span>  
  
|<span data-ttu-id="06d3f-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="06d3f-115">Element</span></span>|<span data-ttu-id="06d3f-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="06d3f-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="06d3f-117">\<baseAddresses ></span><span class="sxs-lookup"><span data-stu-id="06d3f-117">\<baseAddresses></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md)|<span data-ttu-id="06d3f-118">Bir koleksiyonu `baseAddress` hizmeti ana bilgisayar tarafından kullanılan temel adres belirtir öğeleri.</span><span class="sxs-lookup"><span data-stu-id="06d3f-118">A collection of `baseAddress` elements that specifies the base addresses used by the service host.</span></span>|  
|[<span data-ttu-id="06d3f-119">\<zaman aşımı ></span><span class="sxs-lookup"><span data-stu-id="06d3f-119">\<timeOuts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/timeouts.md)|<span data-ttu-id="06d3f-120">Hizmet ana bilgisayarı açmak veya kapatmak izin verilen zaman aralığını belirtir bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="06d3f-120">A configuration element that specifies the interval of time allowed for the service host to open or close.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="06d3f-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="06d3f-121">Parent Elements</span></span>  
  
|<span data-ttu-id="06d3f-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="06d3f-122">Element</span></span>|<span data-ttu-id="06d3f-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="06d3f-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="06d3f-124">\<Hizmet ></span><span class="sxs-lookup"><span data-stu-id="06d3f-124">\<service></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/service.md)|<span data-ttu-id="06d3f-125">Windows Communication Foundation (WCF) hizmeti ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="06d3f-125">Specifies the settings for a Windows Communication Foundation (WCF) service.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="06d3f-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="06d3f-126">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.HostElement>  
 <xref:System.ServiceModel.ServiceHost>  
 [<span data-ttu-id="06d3f-127">Barındırma</span><span class="sxs-lookup"><span data-stu-id="06d3f-127">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
