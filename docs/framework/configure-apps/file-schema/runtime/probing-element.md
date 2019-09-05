---
title: <probing> Öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/probing
- http://schemas.microsoft.com/.NetConfiguration/v2.0#probing
helpviewer_keywords:
- <probing> element
- container tags, <probing> element
- probing element
ms.assetid: 09c80fc9-1ba5-4192-89f7-3a79b2e4b024
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 05634cb319ac69bd76e16e592ba59490b30c9c9d
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252392"
---
# <a name="probing-element"></a><span data-ttu-id="e1dc7-102">\<> öğe algılanıyor</span><span class="sxs-lookup"><span data-stu-id="e1dc7-102">\<probing> Element</span></span>
<span data-ttu-id="e1dc7-103">Derlemeler yüklenirken aranacak ortak dil çalışma zamanının uygulama temel alt dizinlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e1dc7-103">Specifies application base subdirectories for the common language runtime to search when loading assemblies.</span></span>  
  
<span data-ttu-id="e1dc7-104">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="e1dc7-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="e1dc7-105">&nbsp;&nbsp;[ **\<çalışma zamanı >** ](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="e1dc7-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="e1dc7-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<assemblyBinding >** ](assemblybinding-element-for-runtime.md)</span><span class="sxs-lookup"><span data-stu-id="e1dc7-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)</span></span>\
<span data-ttu-id="e1dc7-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<yoklama >**</span><span class="sxs-lookup"><span data-stu-id="e1dc7-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<probing>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1dc7-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e1dc7-108">Syntax</span></span>  
  
```xml  
<probing privatePath="paths"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e1dc7-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e1dc7-109">Attributes and Elements</span></span>  
 <span data-ttu-id="e1dc7-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e1dc7-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e1dc7-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e1dc7-111">Attributes</span></span>  
  
|<span data-ttu-id="e1dc7-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e1dc7-112">Attribute</span></span>|<span data-ttu-id="e1dc7-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e1dc7-113">Description</span></span>|  
|---------------|-----------------|  
|`privatePath`|<span data-ttu-id="e1dc7-114">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="e1dc7-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="e1dc7-115">Derlemeler içerebilen uygulamanın temel dizininin alt dizinlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e1dc7-115">Specifies subdirectories of the application's base directory that might contain assemblies.</span></span> <span data-ttu-id="e1dc7-116">Her alt dizini noktalı virgül ile sınırlandırın.</span><span class="sxs-lookup"><span data-stu-id="e1dc7-116">Delimit each subdirectory with a semicolon.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e1dc7-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e1dc7-117">Child Elements</span></span>  

<span data-ttu-id="e1dc7-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="e1dc7-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e1dc7-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e1dc7-119">Parent Elements</span></span>  
  
|<span data-ttu-id="e1dc7-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="e1dc7-120">Element</span></span>|<span data-ttu-id="e1dc7-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e1dc7-121">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="e1dc7-122">Derleme sürümü yeniden yönlendirmesi ve derlemelerin konumları hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="e1dc7-122">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="e1dc7-123">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="e1dc7-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="e1dc7-124">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="e1dc7-124">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e1dc7-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="e1dc7-125">Example</span></span>  
 <span data-ttu-id="e1dc7-126">Aşağıdaki örnek, çalışma zamanının derlemeleri araması gereken uygulama temel alt dizinlerin nasıl yapılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e1dc7-126">The following example shows how to specify application base subdirectories the runtime should search for assemblies.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <probing privatePath="bin;bin2\subbin;bin3"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e1dc7-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e1dc7-127">See also</span></span>

- [<span data-ttu-id="e1dc7-128">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="e1dc7-128">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="e1dc7-129">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="e1dc7-129">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="e1dc7-130">Bütünleştirilmiş Kodun Konumunu Belirtme</span><span class="sxs-lookup"><span data-stu-id="e1dc7-130">Specifying an Assembly's Location</span></span>](../../specify-assembly-location.md)
- [<span data-ttu-id="e1dc7-131">Çalışma Zamanının Bütünleştirilmiş Kodların Konumunu Bulması</span><span class="sxs-lookup"><span data-stu-id="e1dc7-131">How the Runtime Locates Assemblies</span></span>](../../../deployment/how-the-runtime-locates-assemblies.md)
