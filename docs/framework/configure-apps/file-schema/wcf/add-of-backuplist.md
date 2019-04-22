---
title: <add> / <backupList>
ms.date: 03/30/2017
ms.assetid: bc5939fc-314a-4ea4-a533-c96958da7173
ms.openlocfilehash: 03bf1bbb8156e4722d987e171d9034747ac6bb61
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59089542"
---
# <a name="add-of-backuplist"></a><span data-ttu-id="9e405-102">\<Ekle >, \<backupList ></span><span class="sxs-lookup"><span data-stu-id="9e405-102">\<add> of \<backupList></span></span>
<span data-ttu-id="9e405-103">Bir yedekleme uç nokta öğesini tanımlayan bir yapılandırma öğesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="9e405-103">Represents a configuration element that defines a backup endpoint element.</span></span>  
  
 <span data-ttu-id="9e405-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="9e405-104">\<system.serviceModel></span></span>  
<span data-ttu-id="9e405-105">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="9e405-105">\<routing></span></span>  
<span data-ttu-id="9e405-106">\<backupLists ></span><span class="sxs-lookup"><span data-stu-id="9e405-106">\<backupLists></span></span>  
<span data-ttu-id="9e405-107">\<backupList ></span><span class="sxs-lookup"><span data-stu-id="9e405-107">\<backupList></span></span>  
<span data-ttu-id="9e405-108">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="9e405-108">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e405-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9e405-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9e405-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="9e405-110">Attributes and Elements</span></span>  
 <span data-ttu-id="9e405-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9e405-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9e405-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="9e405-112">Attributes</span></span>  
  
|<span data-ttu-id="9e405-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="9e405-113">Attribute</span></span>|<span data-ttu-id="9e405-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9e405-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9e405-115">name</span><span class="sxs-lookup"><span data-stu-id="9e405-115">name</span></span>|<span data-ttu-id="9e405-116">Yedekleme uç noktası adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="9e405-116">A string that specifies the name of the backup endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9e405-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="9e405-117">Child Elements</span></span>  
 <span data-ttu-id="9e405-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="9e405-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9e405-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="9e405-119">Parent Elements</span></span>  
  
|<span data-ttu-id="9e405-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="9e405-120">Element</span></span>|<span data-ttu-id="9e405-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9e405-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9e405-122">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="9e405-122">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="9e405-123">Birincil uç noktaya erişilemiyor durumunda kullanmak için yönlendirme hizmeti istediğiniz uç noktalarının bir listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="9e405-123">Contains a list of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9e405-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9e405-124">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.BackupEndpointElement?displayProperty=nameWithType>
