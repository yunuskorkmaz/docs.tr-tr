---
description: 'Hakkında daha fazla bilgi <add> edinin: <backupList>'
title: <add> / <backupList>
ms.date: 03/30/2017
ms.assetid: bc5939fc-314a-4ea4-a533-c96958da7173
ms.openlocfilehash: 9855d93be011b4eaa2890c4d24392fde3b65d05a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99804081"
---
# <a name="add-of-backuplist"></a><span data-ttu-id="21a67-103">\<add> / \<backupList></span><span class="sxs-lookup"><span data-stu-id="21a67-103">\<add> of \<backupList></span></span>

<span data-ttu-id="21a67-104">Bir yedekleme uç nokta öğesini tanımlayan bir yapılandırma öğesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="21a67-104">Represents a configuration element that defines a backup endpoint element.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<backupLists>**](backuplists.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<backupList>**](backuplist.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="21a67-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="21a67-105">Syntax</span></span>  
  
```xml  
<routing>
  <backupLists>
    <backupList name="String">
      <add endpointName="String" />
    </backupList>
  </backupLists>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="21a67-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="21a67-106">Attributes and Elements</span></span>  

 <span data-ttu-id="21a67-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="21a67-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="21a67-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="21a67-108">Attributes</span></span>  
  
|<span data-ttu-id="21a67-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="21a67-109">Attribute</span></span>|<span data-ttu-id="21a67-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="21a67-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="21a67-111">name</span><span class="sxs-lookup"><span data-stu-id="21a67-111">name</span></span>|<span data-ttu-id="21a67-112">Yedekleme uç noktasının adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="21a67-112">A string that specifies the name of the backup endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="21a67-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="21a67-113">Child Elements</span></span>  

 <span data-ttu-id="21a67-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="21a67-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="21a67-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="21a67-115">Parent Elements</span></span>  
  
|<span data-ttu-id="21a67-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="21a67-116">Element</span></span>|<span data-ttu-id="21a67-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="21a67-117">Description</span></span>|  
|-------------|-----------------|  
|[\<routing>](routing.md)|<span data-ttu-id="21a67-118">Birincil uç noktaya ulaşılamadığından, yönlendirme hizmeti 'nin kullanmasını istediğiniz uç noktaların listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="21a67-118">Contains a list of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="21a67-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="21a67-119">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.BackupEndpointElement?displayProperty=nameWithType>
