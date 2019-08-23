---
title: <add> / <backupList>
ms.date: 03/30/2017
ms.assetid: bc5939fc-314a-4ea4-a533-c96958da7173
ms.openlocfilehash: c590dbd671807b32e08ad5d871d376a0dc51e611
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926869"
---
# <a name="add-of-backuplist"></a><span data-ttu-id="bc8f4-102">\<\<BackupList > > ekleyin</span><span class="sxs-lookup"><span data-stu-id="bc8f4-102">\<add> of \<backupList></span></span>
<span data-ttu-id="bc8f4-103">Bir yedekleme uç nokta öğesini tanımlayan bir yapılandırma öğesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="bc8f4-103">Represents a configuration element that defines a backup endpoint element.</span></span>  
  
 <span data-ttu-id="bc8f4-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="bc8f4-104">\<system.serviceModel></span></span>  
<span data-ttu-id="bc8f4-105">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="bc8f4-105">\<routing></span></span>  
<span data-ttu-id="bc8f4-106">\<backupLists ></span><span class="sxs-lookup"><span data-stu-id="bc8f4-106">\<backupLists></span></span>  
<span data-ttu-id="bc8f4-107">\<backupList ></span><span class="sxs-lookup"><span data-stu-id="bc8f4-107">\<backupList></span></span>  
<span data-ttu-id="bc8f4-108">\<> Ekle</span><span class="sxs-lookup"><span data-stu-id="bc8f4-108">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc8f4-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bc8f4-109">Syntax</span></span>  
  
```xml  
<routing>
  <backupLists>
    <backupList name="String">
      <add endpointName="String" />
    </backupList>
  </backupLists>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bc8f4-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="bc8f4-110">Attributes and Elements</span></span>  
 <span data-ttu-id="bc8f4-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="bc8f4-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bc8f4-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="bc8f4-112">Attributes</span></span>  
  
|<span data-ttu-id="bc8f4-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="bc8f4-113">Attribute</span></span>|<span data-ttu-id="bc8f4-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bc8f4-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="bc8f4-115">name</span><span class="sxs-lookup"><span data-stu-id="bc8f4-115">name</span></span>|<span data-ttu-id="bc8f4-116">Yedekleme uç noktasının adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="bc8f4-116">A string that specifies the name of the backup endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bc8f4-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="bc8f4-117">Child Elements</span></span>  
 <span data-ttu-id="bc8f4-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="bc8f4-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bc8f4-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="bc8f4-119">Parent Elements</span></span>  
  
|<span data-ttu-id="bc8f4-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="bc8f4-120">Element</span></span>|<span data-ttu-id="bc8f4-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bc8f4-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bc8f4-122">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="bc8f4-122">\<routing></span></span>](routing.md)|<span data-ttu-id="bc8f4-123">Birincil uç noktaya ulaşılamadığından, yönlendirme hizmeti 'nin kullanmasını istediğiniz uç noktaların listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="bc8f4-123">Contains a list of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bc8f4-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bc8f4-124">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.BackupEndpointElement?displayProperty=nameWithType>
