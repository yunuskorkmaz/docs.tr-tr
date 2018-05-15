---
title: '&lt;Hizmetleri&gt;'
ms.date: 03/30/2017
ms.assetid: 80d76ba9-2058-48ad-9b91-5e4be7e5c113
ms.openlocfilehash: 789fc52f628174ef61a9c7169cb0cae0f1ba8e31
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltservicesgt"></a><span data-ttu-id="5ee34-102">&lt;Hizmetleri&gt;</span><span class="sxs-lookup"><span data-stu-id="5ee34-102">&lt;services&gt;</span></span>
<span data-ttu-id="5ee34-103">Hizmetleri tanımlanmış `services` yapılandırma dosyasının.</span><span class="sxs-lookup"><span data-stu-id="5ee34-103">Services are defined in the `services` section of the configuration file.</span></span> <span data-ttu-id="5ee34-104">Her hizmetin kendi vardır `service` yapılandırma bölümü.</span><span class="sxs-lookup"><span data-stu-id="5ee34-104">Each service has its own `service` configuration section.</span></span>  
  
 <span data-ttu-id="5ee34-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="5ee34-105">\<system.ServiceModel></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ee34-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5ee34-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
        <services>  
        <service>  
        </service>  
        </services>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5ee34-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="5ee34-107">Attributes and Elements</span></span>  
 <span data-ttu-id="5ee34-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5ee34-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5ee34-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5ee34-109">Attributes</span></span>  
 <span data-ttu-id="5ee34-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="5ee34-110">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="5ee34-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="5ee34-111">Child Elements</span></span>  
  
|<span data-ttu-id="5ee34-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="5ee34-112">Element</span></span>|<span data-ttu-id="5ee34-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5ee34-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5ee34-114">\<Hizmet ></span><span class="sxs-lookup"><span data-stu-id="5ee34-114">\<service></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/service.md)|<span data-ttu-id="5ee34-115">Hizmet sözleşmesi, davranış ve belirli bir hizmet uç noktalarına tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="5ee34-115">Define the service contract, behavior, and endpoints of the particular service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5ee34-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="5ee34-116">Parent Elements</span></span>  
  
|<span data-ttu-id="5ee34-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="5ee34-117">Element</span></span>|<span data-ttu-id="5ee34-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5ee34-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5ee34-119">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="5ee34-119">\<system.serviceModel></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|<span data-ttu-id="5ee34-120">Tüm Windows Communication Foundation (WCF) yapılandırma öğelerinin kök öğesi.</span><span class="sxs-lookup"><span data-stu-id="5ee34-120">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5ee34-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5ee34-121">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServicesSection>
