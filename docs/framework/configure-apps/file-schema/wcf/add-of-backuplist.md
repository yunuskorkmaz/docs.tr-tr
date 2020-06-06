---
title: <add> / <backupList>
ms.date: 03/30/2017
ms.assetid: bc5939fc-314a-4ea4-a533-c96958da7173
ms.openlocfilehash: 80726cc22cb56013c85c7704c28579b1337666c9
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850546"
---
# <a name="add-of-backuplist"></a><span data-ttu-id="9c328-102">\<add> / \<backupList></span><span class="sxs-lookup"><span data-stu-id="9c328-102">\<add> of \<backupList></span></span>
<span data-ttu-id="9c328-103">Bir yedekleme uç nokta öğesini tanımlayan bir yapılandırma öğesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="9c328-103">Represents a configuration element that defines a backup endpoint element.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<backupLists>**](backuplists.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<backupList>**](backuplist.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="9c328-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9c328-104">Syntax</span></span>  
  
```xml  
<routing>
  <backupLists>
    <backupList name="String">
      <add endpointName="String" />
    </backupList>
  </backupLists>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9c328-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="9c328-105">Attributes and Elements</span></span>  
 <span data-ttu-id="9c328-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9c328-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9c328-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="9c328-107">Attributes</span></span>  
  
|<span data-ttu-id="9c328-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="9c328-108">Attribute</span></span>|<span data-ttu-id="9c328-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9c328-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9c328-110">name</span><span class="sxs-lookup"><span data-stu-id="9c328-110">name</span></span>|<span data-ttu-id="9c328-111">Yedekleme uç noktasının adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="9c328-111">A string that specifies the name of the backup endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9c328-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="9c328-112">Child Elements</span></span>  
 <span data-ttu-id="9c328-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="9c328-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9c328-114">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="9c328-114">Parent Elements</span></span>  
  
|<span data-ttu-id="9c328-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="9c328-115">Element</span></span>|<span data-ttu-id="9c328-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9c328-116">Description</span></span>|  
|-------------|-----------------|  
|[\<routing>](routing.md)|<span data-ttu-id="9c328-117">Birincil uç noktaya ulaşılamadığından, yönlendirme hizmeti 'nin kullanmasını istediğiniz uç noktaların listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="9c328-117">Contains a list of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9c328-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9c328-118">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.BackupEndpointElement?displayProperty=nameWithType>
