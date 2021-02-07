---
description: 'Daha fazla bilgi edinin: <probing> öğesi'
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
ms.openlocfilehash: 404e53f735ce02c2a3d7911216f834d38e309789
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99726110"
---
# <a name="probing-element"></a><span data-ttu-id="c27e3-103">\<probing> Öğesi</span><span class="sxs-lookup"><span data-stu-id="c27e3-103">\<probing> Element</span></span>

<span data-ttu-id="c27e3-104">Derlemeler yüklenirken aranacak ortak dil çalışma zamanının uygulama temel alt dizinlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c27e3-104">Specifies application base subdirectories for the common language runtime to search when loading assemblies.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<probing>**  
  
## <a name="syntax"></a><span data-ttu-id="c27e3-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="c27e3-105">Syntax</span></span>  
  
```xml  
<probing privatePath="paths"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c27e3-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c27e3-106">Attributes and Elements</span></span>  

 <span data-ttu-id="c27e3-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c27e3-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c27e3-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c27e3-108">Attributes</span></span>  
  
|<span data-ttu-id="c27e3-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="c27e3-109">Attribute</span></span>|<span data-ttu-id="c27e3-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c27e3-110">Description</span></span>|  
|---------------|-----------------|  
|`privatePath`|<span data-ttu-id="c27e3-111">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="c27e3-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="c27e3-112">Derlemeler içerebilen uygulamanın temel dizininin alt dizinlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c27e3-112">Specifies subdirectories of the application's base directory that might contain assemblies.</span></span> <span data-ttu-id="c27e3-113">Her alt dizini noktalı virgül ile sınırlandırın.</span><span class="sxs-lookup"><span data-stu-id="c27e3-113">Delimit each subdirectory with a semicolon.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c27e3-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c27e3-114">Child Elements</span></span>  

<span data-ttu-id="c27e3-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="c27e3-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c27e3-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c27e3-116">Parent Elements</span></span>  
  
|<span data-ttu-id="c27e3-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="c27e3-117">Element</span></span>|<span data-ttu-id="c27e3-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c27e3-118">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="c27e3-119">Derleme sürümü yeniden yönlendirmesi ve derlemelerin konumları hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="c27e3-119">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="c27e3-120">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="c27e3-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="c27e3-121">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="c27e3-121">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="c27e3-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="c27e3-122">Example</span></span>  

 <span data-ttu-id="c27e3-123">Aşağıdaki örnek, çalışma zamanının derlemeleri araması gereken uygulama temel alt dizinlerin nasıl yapılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c27e3-123">The following example shows how to specify application base subdirectories the runtime should search for assemblies.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <probing privatePath="bin;bin2\subbin;bin3"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c27e3-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c27e3-124">See also</span></span>

- [<span data-ttu-id="c27e3-125">Çalışma zamanı ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="c27e3-125">Runtime settings schema</span></span>](index.md)
- [<span data-ttu-id="c27e3-126">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="c27e3-126">Configuration file schema</span></span>](../index.md)
- [<span data-ttu-id="c27e3-127">Bir derlemenin konumunu belirtin</span><span class="sxs-lookup"><span data-stu-id="c27e3-127">Specify an assembly's location</span></span>](../../../../standard/assembly/location.md)
- [<span data-ttu-id="c27e3-128">Çalışma zamanının derlemeleri nasıl konumlandırır</span><span class="sxs-lookup"><span data-stu-id="c27e3-128">How the runtime locates assemblies</span></span>](../../../deployment/how-the-runtime-locates-assemblies.md)
