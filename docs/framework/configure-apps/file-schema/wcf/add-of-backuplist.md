---
title: <add> / <backupList>
ms.date: 03/30/2017
ms.assetid: bc5939fc-314a-4ea4-a533-c96958da7173
ms.openlocfilehash: 53af01a519c244376b262db1f6515a438dcc554f
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663365"
---
# <a name="add-of-backuplist"></a><span data-ttu-id="82b5a-102">\<\<BackupList > > ekleyin</span><span class="sxs-lookup"><span data-stu-id="82b5a-102">\<add> of \<backupList></span></span>
<span data-ttu-id="82b5a-103">Bir yedekleme uç nokta öğesini tanımlayan bir yapılandırma öğesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="82b5a-103">Represents a configuration element that defines a backup endpoint element.</span></span>  
  
 <span data-ttu-id="82b5a-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="82b5a-104">\<system.serviceModel></span></span>  
<span data-ttu-id="82b5a-105">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="82b5a-105">\<routing></span></span>  
<span data-ttu-id="82b5a-106">\<backupLists ></span><span class="sxs-lookup"><span data-stu-id="82b5a-106">\<backupLists></span></span>  
<span data-ttu-id="82b5a-107">\<backupList ></span><span class="sxs-lookup"><span data-stu-id="82b5a-107">\<backupList></span></span>  
<span data-ttu-id="82b5a-108">\<> Ekle</span><span class="sxs-lookup"><span data-stu-id="82b5a-108">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82b5a-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="82b5a-109">Syntax</span></span>  
  
```xml  
<routing>
  <backupLists>
    <backupList name="String">
      <add endpointName="String" />
    </backupList>
  </backupLists>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="82b5a-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="82b5a-110">Attributes and Elements</span></span>  
 <span data-ttu-id="82b5a-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="82b5a-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="82b5a-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="82b5a-112">Attributes</span></span>  
  
|<span data-ttu-id="82b5a-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="82b5a-113">Attribute</span></span>|<span data-ttu-id="82b5a-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="82b5a-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="82b5a-115">name</span><span class="sxs-lookup"><span data-stu-id="82b5a-115">name</span></span>|<span data-ttu-id="82b5a-116">Yedekleme uç noktasının adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="82b5a-116">A string that specifies the name of the backup endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="82b5a-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="82b5a-117">Child Elements</span></span>  
 <span data-ttu-id="82b5a-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="82b5a-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="82b5a-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="82b5a-119">Parent Elements</span></span>  
  
|<span data-ttu-id="82b5a-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="82b5a-120">Element</span></span>|<span data-ttu-id="82b5a-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="82b5a-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="82b5a-122">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="82b5a-122">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="82b5a-123">Birincil uç noktaya ulaşılamadığından, yönlendirme hizmeti 'nin kullanmasını istediğiniz uç noktaların listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="82b5a-123">Contains a list of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="82b5a-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="82b5a-124">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.BackupEndpointElement?displayProperty=nameWithType>
