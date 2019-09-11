---
title: <add> / <backupList>
ms.date: 03/30/2017
ms.assetid: bc5939fc-314a-4ea4-a533-c96958da7173
ms.openlocfilehash: 80726cc22cb56013c85c7704c28579b1337666c9
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850546"
---
# <a name="add-of-backuplist"></a><span data-ttu-id="a4ac1-102">\<\<BackupList > > ekleyin</span><span class="sxs-lookup"><span data-stu-id="a4ac1-102">\<add> of \<backupList></span></span>
<span data-ttu-id="a4ac1-103">Bir yedekleme uç nokta öğesini tanımlayan bir yapılandırma öğesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a4ac1-103">Represents a configuration element that defines a backup endpoint element.</span></span>  
  
<span data-ttu-id="a4ac1-104">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="a4ac1-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="a4ac1-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="a4ac1-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="a4ac1-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Yönlendirme >** ](routing.md)</span><span class="sxs-lookup"><span data-stu-id="a4ac1-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)</span></span>\
<span data-ttu-id="a4ac1-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<backupLists >** ](backuplists.md)</span><span class="sxs-lookup"><span data-stu-id="a4ac1-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<backupLists>**](backuplists.md)</span></span>\
<span data-ttu-id="a4ac1-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<backupList >** ](backuplist.md)</span><span class="sxs-lookup"><span data-stu-id="a4ac1-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<backupList>**](backuplist.md)</span></span>\
<span data-ttu-id="a4ac1-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> Ekle**</span><span class="sxs-lookup"><span data-stu-id="a4ac1-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4ac1-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a4ac1-110">Syntax</span></span>  
  
```xml  
<routing>
  <backupLists>
    <backupList name="String">
      <add endpointName="String" />
    </backupList>
  </backupLists>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a4ac1-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a4ac1-111">Attributes and Elements</span></span>  
 <span data-ttu-id="a4ac1-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a4ac1-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a4ac1-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a4ac1-113">Attributes</span></span>  
  
|<span data-ttu-id="a4ac1-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="a4ac1-114">Attribute</span></span>|<span data-ttu-id="a4ac1-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a4ac1-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a4ac1-116">name</span><span class="sxs-lookup"><span data-stu-id="a4ac1-116">name</span></span>|<span data-ttu-id="a4ac1-117">Yedekleme uç noktasının adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="a4ac1-117">A string that specifies the name of the backup endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a4ac1-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a4ac1-118">Child Elements</span></span>  
 <span data-ttu-id="a4ac1-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="a4ac1-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a4ac1-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a4ac1-120">Parent Elements</span></span>  
  
|<span data-ttu-id="a4ac1-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="a4ac1-121">Element</span></span>|<span data-ttu-id="a4ac1-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a4ac1-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a4ac1-123">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="a4ac1-123">\<routing></span></span>](routing.md)|<span data-ttu-id="a4ac1-124">Birincil uç noktaya ulaşılamadığından, yönlendirme hizmeti 'nin kullanmasını istediğiniz uç noktaların listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="a4ac1-124">Contains a list of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a4ac1-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a4ac1-125">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.BackupEndpointElement?displayProperty=nameWithType>
