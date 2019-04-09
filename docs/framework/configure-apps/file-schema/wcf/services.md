---
title: <services>
ms.date: 03/30/2017
ms.assetid: 80d76ba9-2058-48ad-9b91-5e4be7e5c113
ms.openlocfilehash: 2db168d48e3959a7d80a10ca27134f58e3fcb2de
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59168083"
---
# <a name="services"></a><span data-ttu-id="79bfe-101">\<Hizmetleri ></span><span class="sxs-lookup"><span data-stu-id="79bfe-101">\<services></span></span>
<span data-ttu-id="79bfe-102">Hizmetleri tanımlanmış `services` yapılandırma dosyasının.</span><span class="sxs-lookup"><span data-stu-id="79bfe-102">Services are defined in the `services` section of the configuration file.</span></span> <span data-ttu-id="79bfe-103">Her hizmet kendi sahip `service` yapılandırma bölümü.</span><span class="sxs-lookup"><span data-stu-id="79bfe-103">Each service has its own `service` configuration section.</span></span>  
  
 <span data-ttu-id="79bfe-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="79bfe-104">\<system.ServiceModel></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79bfe-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="79bfe-105">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <services>
    <service>
    </service>
  </services>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="79bfe-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="79bfe-106">Attributes and Elements</span></span>  
 <span data-ttu-id="79bfe-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="79bfe-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="79bfe-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="79bfe-108">Attributes</span></span>  
 <span data-ttu-id="79bfe-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="79bfe-109">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="79bfe-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="79bfe-110">Child Elements</span></span>  
  
|<span data-ttu-id="79bfe-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="79bfe-111">Element</span></span>|<span data-ttu-id="79bfe-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="79bfe-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="79bfe-113">\<Hizmet ></span><span class="sxs-lookup"><span data-stu-id="79bfe-113">\<service></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/service.md)|<span data-ttu-id="79bfe-114">Hizmet sözleşmesi, davranış ve belirli bir hizmet uç noktaları tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="79bfe-114">Define the service contract, behavior, and endpoints of the particular service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="79bfe-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="79bfe-115">Parent Elements</span></span>  
  
|<span data-ttu-id="79bfe-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="79bfe-116">Element</span></span>|<span data-ttu-id="79bfe-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="79bfe-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="79bfe-118">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="79bfe-118">\<system.serviceModel></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|<span data-ttu-id="79bfe-119">Tüm Windows Communication Foundation (WCF) yapılandırma öğelerinin kök öğe.</span><span class="sxs-lookup"><span data-stu-id="79bfe-119">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="79bfe-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="79bfe-120">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServicesSection>
