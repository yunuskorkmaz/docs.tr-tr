---
title: '&lt;backupList&gt; &lt;ekleme&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bc5939fc-314a-4ea4-a533-c96958da7173
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 786620b0daf1cd22a95f9d0c94b7fc3d17c1a2c3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltaddgt-of-ltbackuplistgt"></a><span data-ttu-id="34946-102">&lt;backupList&gt; &lt;ekleme&gt;</span><span class="sxs-lookup"><span data-stu-id="34946-102">&lt;add&gt; of &lt;backupList&gt;</span></span>
<span data-ttu-id="34946-103">Bir yedekleme endpoint öğesi tanımlayan bir yapılandırma öğesi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="34946-103">Represents a configuration element that defines a backup endpoint element.</span></span>  
  
 <span data-ttu-id="34946-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="34946-104">\<system.serviceModel></span></span>  
<span data-ttu-id="34946-105">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="34946-105">\<routing></span></span>  
<span data-ttu-id="34946-106">\<backupLists ></span><span class="sxs-lookup"><span data-stu-id="34946-106">\<backupLists></span></span>  
<span data-ttu-id="34946-107">\<backupList ></span><span class="sxs-lookup"><span data-stu-id="34946-107">\<backupList></span></span>  
<span data-ttu-id="34946-108">\<ekleme ></span><span class="sxs-lookup"><span data-stu-id="34946-108">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34946-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="34946-109">Syntax</span></span>  
  
```xml  
   <routing>  <backupLists>    <backupList name="String">      <add endpointName="String" />    </backupList>    </backupLists></routing>  
```  
  
```csharp  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="34946-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="34946-110">Attributes and Elements</span></span>  
 <span data-ttu-id="34946-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="34946-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="34946-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="34946-112">Attributes</span></span>  
  
|<span data-ttu-id="34946-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="34946-113">Attribute</span></span>|<span data-ttu-id="34946-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="34946-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="34946-115">name</span><span class="sxs-lookup"><span data-stu-id="34946-115">name</span></span>|<span data-ttu-id="34946-116">Yedekleme uç noktanın adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="34946-116">A string that specifies the name of the backup endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="34946-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="34946-117">Child Elements</span></span>  
 <span data-ttu-id="34946-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="34946-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="34946-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="34946-119">Parent Elements</span></span>  
  
|<span data-ttu-id="34946-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="34946-120">Element</span></span>|<span data-ttu-id="34946-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="34946-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="34946-122">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="34946-122">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="34946-123">Birincil endpoint ulaşılamıyor durumunda kullanmak için yönlendirme hizmeti istediğiniz uç noktaları listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="34946-123">Contains a list of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="34946-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="34946-124">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.BackupEndpointElement?displayProperty=nameWithType> 
