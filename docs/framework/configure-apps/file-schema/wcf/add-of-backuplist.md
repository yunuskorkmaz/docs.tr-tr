---
title: '&lt;backupList&gt; &lt;ekleme&gt;'
ms.date: 03/30/2017
ms.assetid: bc5939fc-314a-4ea4-a533-c96958da7173
ms.openlocfilehash: 4a8eb3df9be6b6b5bfe43aee330f3174ddca66ab
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54151481"
---
# <a name="ltaddgt-of-ltbackuplistgt"></a><span data-ttu-id="0b65d-102">&lt;backupList&gt; &lt;ekleme&gt;</span><span class="sxs-lookup"><span data-stu-id="0b65d-102">&lt;add&gt; of &lt;backupList&gt;</span></span>
<span data-ttu-id="0b65d-103">Bir yedekleme uç nokta öğesini tanımlayan bir yapılandırma öğesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="0b65d-103">Represents a configuration element that defines a backup endpoint element.</span></span>  
  
 <span data-ttu-id="0b65d-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="0b65d-104">\<system.serviceModel></span></span>  
<span data-ttu-id="0b65d-105">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="0b65d-105">\<routing></span></span>  
<span data-ttu-id="0b65d-106">\<backupLists ></span><span class="sxs-lookup"><span data-stu-id="0b65d-106">\<backupLists></span></span>  
<span data-ttu-id="0b65d-107">\<backupList ></span><span class="sxs-lookup"><span data-stu-id="0b65d-107">\<backupList></span></span>  
<span data-ttu-id="0b65d-108">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="0b65d-108">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b65d-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0b65d-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0b65d-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="0b65d-110">Attributes and Elements</span></span>  
 <span data-ttu-id="0b65d-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0b65d-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0b65d-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="0b65d-112">Attributes</span></span>  
  
|<span data-ttu-id="0b65d-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="0b65d-113">Attribute</span></span>|<span data-ttu-id="0b65d-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0b65d-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0b65d-115">name</span><span class="sxs-lookup"><span data-stu-id="0b65d-115">name</span></span>|<span data-ttu-id="0b65d-116">Yedekleme uç noktası adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="0b65d-116">A string that specifies the name of the backup endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0b65d-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="0b65d-117">Child Elements</span></span>  
 <span data-ttu-id="0b65d-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="0b65d-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0b65d-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="0b65d-119">Parent Elements</span></span>  
  
|<span data-ttu-id="0b65d-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="0b65d-120">Element</span></span>|<span data-ttu-id="0b65d-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0b65d-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0b65d-122">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="0b65d-122">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="0b65d-123">Birincil uç noktaya erişilemiyor durumunda kullanmak için yönlendirme hizmeti istediğiniz uç noktalarının bir listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="0b65d-123">Contains a list of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0b65d-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0b65d-124">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.BackupEndpointElement?displayProperty=nameWithType> 
