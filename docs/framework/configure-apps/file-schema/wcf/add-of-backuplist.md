---
title: <add> , <backupList>
ms.date: 03/30/2017
ms.assetid: bc5939fc-314a-4ea4-a533-c96958da7173
ms.openlocfilehash: e61ee275a7e98f13370504f5f15fdbe62a8221bd
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55285798"
---
# <a name="add-of-backuplist"></a><span data-ttu-id="3d350-102">\<Ekle >, \<backupList ></span><span class="sxs-lookup"><span data-stu-id="3d350-102">\<add> of \<backupList></span></span>
<span data-ttu-id="3d350-103">Bir yedekleme uç nokta öğesini tanımlayan bir yapılandırma öğesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="3d350-103">Represents a configuration element that defines a backup endpoint element.</span></span>  
  
 <span data-ttu-id="3d350-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="3d350-104">\<system.serviceModel></span></span>  
<span data-ttu-id="3d350-105">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="3d350-105">\<routing></span></span>  
<span data-ttu-id="3d350-106">\<backupLists ></span><span class="sxs-lookup"><span data-stu-id="3d350-106">\<backupLists></span></span>  
<span data-ttu-id="3d350-107">\<backupList ></span><span class="sxs-lookup"><span data-stu-id="3d350-107">\<backupList></span></span>  
<span data-ttu-id="3d350-108">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="3d350-108">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d350-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3d350-109">Syntax</span></span>  
  
```xml  
<routing>
  <backupLists>
    <backupList name="String">
      <add endpointName="String" />
    </backupList>
  </backupLists>
</routing>
```  
  
```csharp  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3d350-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="3d350-110">Attributes and Elements</span></span>  
 <span data-ttu-id="3d350-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3d350-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3d350-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="3d350-112">Attributes</span></span>  
  
|<span data-ttu-id="3d350-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="3d350-113">Attribute</span></span>|<span data-ttu-id="3d350-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3d350-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3d350-115">name</span><span class="sxs-lookup"><span data-stu-id="3d350-115">name</span></span>|<span data-ttu-id="3d350-116">Yedekleme uç noktası adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="3d350-116">A string that specifies the name of the backup endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3d350-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="3d350-117">Child Elements</span></span>  
 <span data-ttu-id="3d350-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="3d350-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3d350-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="3d350-119">Parent Elements</span></span>  
  
|<span data-ttu-id="3d350-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="3d350-120">Element</span></span>|<span data-ttu-id="3d350-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3d350-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3d350-122">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="3d350-122">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="3d350-123">Birincil uç noktaya erişilemiyor durumunda kullanmak için yönlendirme hizmeti istediğiniz uç noktalarının bir listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="3d350-123">Contains a list of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3d350-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3d350-124">See also</span></span>
- <xref:System.ServiceModel.Routing.Configuration.BackupEndpointElement?displayProperty=nameWithType>
