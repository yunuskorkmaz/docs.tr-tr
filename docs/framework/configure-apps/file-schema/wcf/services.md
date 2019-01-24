---
title: '&lt;Hizmetleri&gt;'
ms.date: 03/30/2017
ms.assetid: 80d76ba9-2058-48ad-9b91-5e4be7e5c113
ms.openlocfilehash: 7b26224f1217e7f73a529c082c2c9272ec189a5a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54573263"
---
# <a name="ltservicesgt"></a><span data-ttu-id="7994d-102">&lt;Hizmetleri&gt;</span><span class="sxs-lookup"><span data-stu-id="7994d-102">&lt;services&gt;</span></span>
<span data-ttu-id="7994d-103">Hizmetleri tanımlanmış `services` yapılandırma dosyasının.</span><span class="sxs-lookup"><span data-stu-id="7994d-103">Services are defined in the `services` section of the configuration file.</span></span> <span data-ttu-id="7994d-104">Her hizmet kendi sahip `service` yapılandırma bölümü.</span><span class="sxs-lookup"><span data-stu-id="7994d-104">Each service has its own `service` configuration section.</span></span>  
  
 <span data-ttu-id="7994d-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="7994d-105">\<system.ServiceModel></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7994d-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7994d-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <services>
    <service>
    </service>
  </services>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7994d-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="7994d-107">Attributes and Elements</span></span>  
 <span data-ttu-id="7994d-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7994d-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7994d-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="7994d-109">Attributes</span></span>  
 <span data-ttu-id="7994d-110">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="7994d-110">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="7994d-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="7994d-111">Child Elements</span></span>  
  
|<span data-ttu-id="7994d-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="7994d-112">Element</span></span>|<span data-ttu-id="7994d-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7994d-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7994d-114">\<Hizmet ></span><span class="sxs-lookup"><span data-stu-id="7994d-114">\<service></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/service.md)|<span data-ttu-id="7994d-115">Hizmet sözleşmesi, davranış ve belirli bir hizmet uç noktaları tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="7994d-115">Define the service contract, behavior, and endpoints of the particular service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7994d-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="7994d-116">Parent Elements</span></span>  
  
|<span data-ttu-id="7994d-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="7994d-117">Element</span></span>|<span data-ttu-id="7994d-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7994d-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7994d-119">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="7994d-119">\<system.serviceModel></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|<span data-ttu-id="7994d-120">Tüm Windows Communication Foundation (WCF) yapılandırma öğelerinin kök öğe.</span><span class="sxs-lookup"><span data-stu-id="7994d-120">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7994d-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7994d-121">See also</span></span>
- <xref:System.ServiceModel.Configuration.ServicesSection>
