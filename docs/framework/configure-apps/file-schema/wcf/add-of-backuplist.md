---
title: '&lt;backupList&gt; &lt;ekleme&gt;'
ms.date: 03/30/2017
ms.assetid: bc5939fc-314a-4ea4-a533-c96958da7173
ms.openlocfilehash: 7e7361b24c0444b5f3d51a6f5bf079d5eb2dee18
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltaddgt-of-ltbackuplistgt"></a><span data-ttu-id="62f09-102">&lt;backupList&gt; &lt;ekleme&gt;</span><span class="sxs-lookup"><span data-stu-id="62f09-102">&lt;add&gt; of &lt;backupList&gt;</span></span>
<span data-ttu-id="62f09-103">Bir yedekleme endpoint öğesi tanımlayan bir yapılandırma öğesi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="62f09-103">Represents a configuration element that defines a backup endpoint element.</span></span>  
  
 <span data-ttu-id="62f09-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="62f09-104">\<system.serviceModel></span></span>  
<span data-ttu-id="62f09-105">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="62f09-105">\<routing></span></span>  
<span data-ttu-id="62f09-106">\<backupLists ></span><span class="sxs-lookup"><span data-stu-id="62f09-106">\<backupLists></span></span>  
<span data-ttu-id="62f09-107">\<backupList ></span><span class="sxs-lookup"><span data-stu-id="62f09-107">\<backupList></span></span>  
<span data-ttu-id="62f09-108">\<ekleme ></span><span class="sxs-lookup"><span data-stu-id="62f09-108">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62f09-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="62f09-109">Syntax</span></span>  
  
```xml  
   <routing>  <backupLists>    <backupList name="String">      <add endpointName="String" />    </backupList>    </backupLists></routing>  
```  
  
```csharp  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="62f09-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="62f09-110">Attributes and Elements</span></span>  
 <span data-ttu-id="62f09-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="62f09-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="62f09-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="62f09-112">Attributes</span></span>  
  
|<span data-ttu-id="62f09-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="62f09-113">Attribute</span></span>|<span data-ttu-id="62f09-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="62f09-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="62f09-115">name</span><span class="sxs-lookup"><span data-stu-id="62f09-115">name</span></span>|<span data-ttu-id="62f09-116">Yedekleme uç noktanın adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="62f09-116">A string that specifies the name of the backup endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="62f09-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="62f09-117">Child Elements</span></span>  
 <span data-ttu-id="62f09-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="62f09-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="62f09-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="62f09-119">Parent Elements</span></span>  
  
|<span data-ttu-id="62f09-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="62f09-120">Element</span></span>|<span data-ttu-id="62f09-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="62f09-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="62f09-122">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="62f09-122">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="62f09-123">Birincil endpoint ulaşılamıyor durumunda kullanmak için yönlendirme hizmeti istediğiniz uç noktaları listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="62f09-123">Contains a list of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="62f09-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="62f09-124">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.BackupEndpointElement?displayProperty=nameWithType> 
