---
title: '&lt;ana bilgisayar&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: be566d55-9d50-4b2e-985d-52a5cc26cbbb
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7177c62af8501258ad8709bff88cb85488b56727
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="lthostgt"></a><span data-ttu-id="68cff-102">&lt;ana bilgisayar&gt;</span><span class="sxs-lookup"><span data-stu-id="68cff-102">&lt;host&gt;</span></span>
<span data-ttu-id="68cff-103">Hizmet ana bilgisayarı ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="68cff-103">Specifies settings for a service host.</span></span>  
  
 <span data-ttu-id="68cff-104">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="68cff-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="68cff-105">\<Hizmetleri ></span><span class="sxs-lookup"><span data-stu-id="68cff-105">\<services></span></span>  
<span data-ttu-id="68cff-106">\<Hizmet ></span><span class="sxs-lookup"><span data-stu-id="68cff-106">\<service></span></span>  
<span data-ttu-id="68cff-107">\<ana bilgisayar ></span><span class="sxs-lookup"><span data-stu-id="68cff-107">\<host></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68cff-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="68cff-108">Syntax</span></span>  
  
```xml  
<host>  
      <baseAddresses>  
         <baseAddress baseAddress="string" />  
      </baseAddresses>  
      <timeOuts closeTimeout="TimeSpan"  
         openTimeout="TimeSpan" >  
</host>  
```  
  
## <a name="type"></a><span data-ttu-id="68cff-109">Tür</span><span class="sxs-lookup"><span data-stu-id="68cff-109">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="68cff-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="68cff-110">Attributes and Elements</span></span>  
 <span data-ttu-id="68cff-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="68cff-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="68cff-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="68cff-112">Attributes</span></span>  
 <span data-ttu-id="68cff-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="68cff-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="68cff-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="68cff-114">Child Elements</span></span>  
  
|<span data-ttu-id="68cff-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="68cff-115">Element</span></span>|<span data-ttu-id="68cff-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="68cff-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="68cff-117">\<baseAddresses ></span><span class="sxs-lookup"><span data-stu-id="68cff-117">\<baseAddresses></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md)|<span data-ttu-id="68cff-118">Bir koleksiyonu `baseAddress` hizmeti ana bilgisayar tarafından kullanılan temel adres belirtir öğeleri.</span><span class="sxs-lookup"><span data-stu-id="68cff-118">A collection of `baseAddress` elements that specifies the base addresses used by the service host.</span></span>|  
|[<span data-ttu-id="68cff-119">\<zaman aşımı ></span><span class="sxs-lookup"><span data-stu-id="68cff-119">\<timeOuts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/timeouts.md)|<span data-ttu-id="68cff-120">Hizmet ana bilgisayarı açmak veya kapatmak izin verilen zaman aralığını belirtir bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="68cff-120">A configuration element that specifies the interval of time allowed for the service host to open or close.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="68cff-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="68cff-121">Parent Elements</span></span>  
  
|<span data-ttu-id="68cff-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="68cff-122">Element</span></span>|<span data-ttu-id="68cff-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="68cff-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="68cff-124">\<Hizmet ></span><span class="sxs-lookup"><span data-stu-id="68cff-124">\<service></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/service.md)|<span data-ttu-id="68cff-125">Ayarlarını belirten bir [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] hizmet.</span><span class="sxs-lookup"><span data-stu-id="68cff-125">Specifies the settings for a [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] service.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="68cff-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="68cff-126">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.HostElement>  
 <xref:System.ServiceModel.ServiceHost>  
 [<span data-ttu-id="68cff-127">Barındırma</span><span class="sxs-lookup"><span data-stu-id="68cff-127">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
