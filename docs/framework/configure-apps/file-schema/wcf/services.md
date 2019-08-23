---
title: <services>
ms.date: 03/30/2017
ms.assetid: 80d76ba9-2058-48ad-9b91-5e4be7e5c113
ms.openlocfilehash: c00d5fe3e8b2ba05843e09aca6aaa79386541bad
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937198"
---
# <a name="services"></a><span data-ttu-id="a20dc-101">\<Hizmetler ></span><span class="sxs-lookup"><span data-stu-id="a20dc-101">\<services></span></span>
<span data-ttu-id="a20dc-102">Hizmetler, yapılandırma dosyasının `services` bölümünde tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="a20dc-102">Services are defined in the `services` section of the configuration file.</span></span> <span data-ttu-id="a20dc-103">Her hizmetin kendi `service` yapılandırma bölümü vardır.</span><span class="sxs-lookup"><span data-stu-id="a20dc-103">Each service has its own `service` configuration section.</span></span>  
  
 <span data-ttu-id="a20dc-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="a20dc-104">\<system.ServiceModel></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a20dc-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a20dc-105">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <services>
    <service>
    </service>
  </services>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a20dc-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a20dc-106">Attributes and Elements</span></span>  
 <span data-ttu-id="a20dc-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a20dc-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a20dc-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a20dc-108">Attributes</span></span>  
 <span data-ttu-id="a20dc-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="a20dc-109">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a20dc-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a20dc-110">Child Elements</span></span>  
  
|<span data-ttu-id="a20dc-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="a20dc-111">Element</span></span>|<span data-ttu-id="a20dc-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a20dc-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a20dc-113">\<hizmet ></span><span class="sxs-lookup"><span data-stu-id="a20dc-113">\<service></span></span>](service.md)|<span data-ttu-id="a20dc-114">Belirli bir hizmetin hizmet sözleşmesini, davranışını ve uç noktalarını tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="a20dc-114">Define the service contract, behavior, and endpoints of the particular service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a20dc-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a20dc-115">Parent Elements</span></span>  
  
|<span data-ttu-id="a20dc-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="a20dc-116">Element</span></span>|<span data-ttu-id="a20dc-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a20dc-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a20dc-118">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="a20dc-118">\<system.serviceModel></span></span>](system-servicemodel.md)|<span data-ttu-id="a20dc-119">Tüm Windows Communication Foundation (WCF) yapılandırma öğelerinin kök öğesi.</span><span class="sxs-lookup"><span data-stu-id="a20dc-119">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a20dc-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a20dc-120">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServicesSection>
