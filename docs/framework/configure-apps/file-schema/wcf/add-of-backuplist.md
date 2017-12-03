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
ms.openlocfilehash: b93b442d21d34eea5031cea565bdcf62139abc81
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltaddgt-of-ltbackuplistgt"></a><span data-ttu-id="0139a-102">&lt;backupList&gt; &lt;ekleme&gt;</span><span class="sxs-lookup"><span data-stu-id="0139a-102">&lt;add&gt; of &lt;backupList&gt;</span></span>
<span data-ttu-id="0139a-103">Bir yedekleme endpoint öğesi tanımlayan bir yapılandırma öğesi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="0139a-103">Represents a configuration element that defines a backup endpoint element.</span></span>  
  
 <span data-ttu-id="0139a-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="0139a-104">\<system.serviceModel></span></span>  
<span data-ttu-id="0139a-105">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="0139a-105">\<routing></span></span>  
<span data-ttu-id="0139a-106">\<backupLists ></span><span class="sxs-lookup"><span data-stu-id="0139a-106">\<backupLists></span></span>  
<span data-ttu-id="0139a-107">\<backupList ></span><span class="sxs-lookup"><span data-stu-id="0139a-107">\<backupList></span></span>  
<span data-ttu-id="0139a-108">\<ekleme ></span><span class="sxs-lookup"><span data-stu-id="0139a-108">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0139a-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0139a-109">Syntax</span></span>  
  
```xml  
   <routing>  <backupLists>    <backupList name="String">      <add endpointName="String" />    </backupList>    </backupLists></routing>  
```  
  
```csharp  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0139a-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="0139a-110">Attributes and Elements</span></span>  
 <span data-ttu-id="0139a-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0139a-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0139a-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="0139a-112">Attributes</span></span>  
  
|<span data-ttu-id="0139a-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="0139a-113">Attribute</span></span>|<span data-ttu-id="0139a-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0139a-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0139a-115">name</span><span class="sxs-lookup"><span data-stu-id="0139a-115">name</span></span>|<span data-ttu-id="0139a-116">Yedekleme uç noktanın adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="0139a-116">A string that specifies the name of the backup endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0139a-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="0139a-117">Child Elements</span></span>  
 <span data-ttu-id="0139a-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="0139a-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0139a-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="0139a-119">Parent Elements</span></span>  
  
|<span data-ttu-id="0139a-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="0139a-120">Element</span></span>|<span data-ttu-id="0139a-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0139a-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0139a-122">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="0139a-122">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="0139a-123">Birincil endpoint ulaşılamıyor durumunda kullanmak için yönlendirme hizmeti istediğiniz uç noktaları listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="0139a-123">Contains a list of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0139a-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0139a-124">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.BackupEndpointElement?displayProperty=nameWithType> 
