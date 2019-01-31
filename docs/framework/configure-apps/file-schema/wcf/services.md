---
title: <services>
ms.date: 03/30/2017
ms.assetid: 80d76ba9-2058-48ad-9b91-5e4be7e5c113
ms.openlocfilehash: 4dc425fa97eaf99664f0d9bbbbc851c462cbf373
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55274969"
---
# <a name="services"></a><span data-ttu-id="506a0-101">\<Hizmetleri ></span><span class="sxs-lookup"><span data-stu-id="506a0-101">\<services></span></span>
<span data-ttu-id="506a0-102">Hizmetleri tanımlanmış `services` yapılandırma dosyasının.</span><span class="sxs-lookup"><span data-stu-id="506a0-102">Services are defined in the `services` section of the configuration file.</span></span> <span data-ttu-id="506a0-103">Her hizmet kendi sahip `service` yapılandırma bölümü.</span><span class="sxs-lookup"><span data-stu-id="506a0-103">Each service has its own `service` configuration section.</span></span>  
  
 <span data-ttu-id="506a0-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="506a0-104">\<system.ServiceModel></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="506a0-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="506a0-105">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <services>
    <service>
    </service>
  </services>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="506a0-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="506a0-106">Attributes and Elements</span></span>  
 <span data-ttu-id="506a0-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="506a0-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="506a0-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="506a0-108">Attributes</span></span>  
 <span data-ttu-id="506a0-109">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="506a0-109">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="506a0-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="506a0-110">Child Elements</span></span>  
  
|<span data-ttu-id="506a0-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="506a0-111">Element</span></span>|<span data-ttu-id="506a0-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="506a0-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="506a0-113">\<Hizmet ></span><span class="sxs-lookup"><span data-stu-id="506a0-113">\<service></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/service.md)|<span data-ttu-id="506a0-114">Hizmet sözleşmesi, davranış ve belirli bir hizmet uç noktaları tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="506a0-114">Define the service contract, behavior, and endpoints of the particular service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="506a0-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="506a0-115">Parent Elements</span></span>  
  
|<span data-ttu-id="506a0-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="506a0-116">Element</span></span>|<span data-ttu-id="506a0-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="506a0-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="506a0-118">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="506a0-118">\<system.serviceModel></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|<span data-ttu-id="506a0-119">Tüm Windows Communication Foundation (WCF) yapılandırma öğelerinin kök öğe.</span><span class="sxs-lookup"><span data-stu-id="506a0-119">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="506a0-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="506a0-120">See also</span></span>
- <xref:System.ServiceModel.Configuration.ServicesSection>
