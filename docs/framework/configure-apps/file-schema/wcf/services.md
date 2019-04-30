---
title: <services>
ms.date: 03/30/2017
ms.assetid: 80d76ba9-2058-48ad-9b91-5e4be7e5c113
ms.openlocfilehash: 2db168d48e3959a7d80a10ca27134f58e3fcb2de
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61758164"
---
# <a name="services"></a><span data-ttu-id="e4ac7-101">\<Hizmetleri ></span><span class="sxs-lookup"><span data-stu-id="e4ac7-101">\<services></span></span>
<span data-ttu-id="e4ac7-102">Hizmetleri tanımlanmış `services` yapılandırma dosyasının.</span><span class="sxs-lookup"><span data-stu-id="e4ac7-102">Services are defined in the `services` section of the configuration file.</span></span> <span data-ttu-id="e4ac7-103">Her hizmet kendi sahip `service` yapılandırma bölümü.</span><span class="sxs-lookup"><span data-stu-id="e4ac7-103">Each service has its own `service` configuration section.</span></span>  
  
 <span data-ttu-id="e4ac7-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="e4ac7-104">\<system.ServiceModel></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4ac7-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e4ac7-105">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <services>
    <service>
    </service>
  </services>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e4ac7-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e4ac7-106">Attributes and Elements</span></span>  
 <span data-ttu-id="e4ac7-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e4ac7-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e4ac7-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e4ac7-108">Attributes</span></span>  
 <span data-ttu-id="e4ac7-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="e4ac7-109">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e4ac7-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e4ac7-110">Child Elements</span></span>  
  
|<span data-ttu-id="e4ac7-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="e4ac7-111">Element</span></span>|<span data-ttu-id="e4ac7-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e4ac7-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e4ac7-113">\<Hizmet ></span><span class="sxs-lookup"><span data-stu-id="e4ac7-113">\<service></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/service.md)|<span data-ttu-id="e4ac7-114">Hizmet sözleşmesi, davranış ve belirli bir hizmet uç noktaları tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="e4ac7-114">Define the service contract, behavior, and endpoints of the particular service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e4ac7-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e4ac7-115">Parent Elements</span></span>  
  
|<span data-ttu-id="e4ac7-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="e4ac7-116">Element</span></span>|<span data-ttu-id="e4ac7-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e4ac7-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e4ac7-118">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="e4ac7-118">\<system.serviceModel></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|<span data-ttu-id="e4ac7-119">Tüm Windows Communication Foundation (WCF) yapılandırma öğelerinin kök öğe.</span><span class="sxs-lookup"><span data-stu-id="e4ac7-119">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e4ac7-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e4ac7-120">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServicesSection>
