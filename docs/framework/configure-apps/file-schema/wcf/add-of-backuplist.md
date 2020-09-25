---
title: <add> / <backupList>
ms.date: 03/30/2017
ms.assetid: bc5939fc-314a-4ea4-a533-c96958da7173
ms.openlocfilehash: 6d8fd26170059226583a300b1b48b849666db929
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91181628"
---
# <a name="add-of-backuplist"></a><span data-ttu-id="f085a-102">\<add> / \<backupList></span><span class="sxs-lookup"><span data-stu-id="f085a-102">\<add> of \<backupList></span></span>

<span data-ttu-id="f085a-103">Bir yedekleme uç nokta öğesini tanımlayan bir yapılandırma öğesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f085a-103">Represents a configuration element that defines a backup endpoint element.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<backupLists>**](backuplists.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<backupList>**](backuplist.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="f085a-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="f085a-104">Syntax</span></span>  
  
```xml  
<routing>
  <backupLists>
    <backupList name="String">
      <add endpointName="String" />
    </backupList>
  </backupLists>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f085a-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f085a-105">Attributes and Elements</span></span>  

 <span data-ttu-id="f085a-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f085a-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f085a-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f085a-107">Attributes</span></span>  
  
|<span data-ttu-id="f085a-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="f085a-108">Attribute</span></span>|<span data-ttu-id="f085a-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f085a-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f085a-110">name</span><span class="sxs-lookup"><span data-stu-id="f085a-110">name</span></span>|<span data-ttu-id="f085a-111">Yedekleme uç noktasının adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="f085a-111">A string that specifies the name of the backup endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f085a-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f085a-112">Child Elements</span></span>  

 <span data-ttu-id="f085a-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="f085a-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f085a-114">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f085a-114">Parent Elements</span></span>  
  
|<span data-ttu-id="f085a-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="f085a-115">Element</span></span>|<span data-ttu-id="f085a-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f085a-116">Description</span></span>|  
|-------------|-----------------|  
|[\<routing>](routing.md)|<span data-ttu-id="f085a-117">Birincil uç noktaya ulaşılamadığından, yönlendirme hizmeti 'nin kullanmasını istediğiniz uç noktaların listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="f085a-117">Contains a list of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f085a-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f085a-118">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.BackupEndpointElement?displayProperty=nameWithType>
