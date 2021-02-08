---
description: 'Hakkında daha fazla bilgi edinin: <services>'
title: <services>
ms.date: 03/30/2017
ms.assetid: 80d76ba9-2058-48ad-9b91-5e4be7e5c113
ms.openlocfilehash: 6e8c0c5ad5390c097db7bf1be1f0d489e1c0d624
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786713"
---
# \<services>

<span data-ttu-id="c38b4-102">Hizmetler, `services` yapılandırma dosyasının bölümünde tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="c38b4-102">Services are defined in the `services` section of the configuration file.</span></span> <span data-ttu-id="c38b4-103">Her hizmetin kendi `service` yapılandırma bölümü vardır.</span><span class="sxs-lookup"><span data-stu-id="c38b4-103">Each service has its own `service` configuration section.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<services>**  
  
## <a name="syntax"></a><span data-ttu-id="c38b4-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="c38b4-104">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <services>
    <service>
    </service>
  </services>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c38b4-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c38b4-105">Attributes and Elements</span></span>  

 <span data-ttu-id="c38b4-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c38b4-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c38b4-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c38b4-107">Attributes</span></span>  

 <span data-ttu-id="c38b4-108">Yok</span><span class="sxs-lookup"><span data-stu-id="c38b4-108">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c38b4-109">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c38b4-109">Child Elements</span></span>  
  
|<span data-ttu-id="c38b4-110">Öğe</span><span class="sxs-lookup"><span data-stu-id="c38b4-110">Element</span></span>|<span data-ttu-id="c38b4-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c38b4-111">Description</span></span>|  
|-------------|-----------------|  
|[\<service>](service.md)|<span data-ttu-id="c38b4-112">Belirli bir hizmetin hizmet sözleşmesini, davranışını ve uç noktalarını tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="c38b4-112">Define the service contract, behavior, and endpoints of the particular service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c38b4-113">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c38b4-113">Parent Elements</span></span>  
  
|<span data-ttu-id="c38b4-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="c38b4-114">Element</span></span>|<span data-ttu-id="c38b4-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c38b4-115">Description</span></span>|  
|-------------|-----------------|  
|[\<system.serviceModel>](system-servicemodel.md)|<span data-ttu-id="c38b4-116">Tüm Windows Communication Foundation (WCF) yapılandırma öğelerinin kök öğesi.</span><span class="sxs-lookup"><span data-stu-id="c38b4-116">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c38b4-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c38b4-117">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServicesSection>
