---
title: '&lt;Hizmetleri&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 80d76ba9-2058-48ad-9b91-5e4be7e5c113
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: eb292a62c2b042c387799164ff4cec88bd2ca482
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="ltservicesgt"></a><span data-ttu-id="4d2b7-102">&lt;Hizmetleri&gt;</span><span class="sxs-lookup"><span data-stu-id="4d2b7-102">&lt;services&gt;</span></span>
<span data-ttu-id="4d2b7-103">Hizmetleri tanımlanmış `services` yapılandırma dosyasının.</span><span class="sxs-lookup"><span data-stu-id="4d2b7-103">Services are defined in the `services` section of the configuration file.</span></span> <span data-ttu-id="4d2b7-104">Her hizmetin kendi vardır `service` yapılandırma bölümü.</span><span class="sxs-lookup"><span data-stu-id="4d2b7-104">Each service has its own `service` configuration section.</span></span>  
  
 <span data-ttu-id="4d2b7-105">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="4d2b7-105">\<system.ServiceModel></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d2b7-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4d2b7-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
        <services>  
        <service>  
        </service>  
        </services>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4d2b7-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="4d2b7-107">Attributes and Elements</span></span>  
 <span data-ttu-id="4d2b7-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4d2b7-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4d2b7-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="4d2b7-109">Attributes</span></span>  
 <span data-ttu-id="4d2b7-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="4d2b7-110">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="4d2b7-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="4d2b7-111">Child Elements</span></span>  
  
|<span data-ttu-id="4d2b7-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="4d2b7-112">Element</span></span>|<span data-ttu-id="4d2b7-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4d2b7-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4d2b7-114">\<Hizmet ></span><span class="sxs-lookup"><span data-stu-id="4d2b7-114">\<service></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/service.md)|<span data-ttu-id="4d2b7-115">Hizmet sözleşmesi, davranış ve belirli bir hizmet uç noktalarına tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="4d2b7-115">Define the service contract, behavior, and endpoints of the particular service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4d2b7-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="4d2b7-116">Parent Elements</span></span>  
  
|<span data-ttu-id="4d2b7-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="4d2b7-117">Element</span></span>|<span data-ttu-id="4d2b7-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4d2b7-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4d2b7-119">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="4d2b7-119">\<system.serviceModel></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|<span data-ttu-id="4d2b7-120">Tüm Windows Communication Foundation (WCF) yapılandırma öğelerinin kök öğesi.</span><span class="sxs-lookup"><span data-stu-id="4d2b7-120">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4d2b7-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4d2b7-121">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServicesSection>
