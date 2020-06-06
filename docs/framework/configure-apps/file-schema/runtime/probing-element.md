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
ms.openlocfilehash: e9e48ea97e1b70fef7fcc78a113e18c5fec23b7c
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73115858"
---
# <a name="probing-element"></a><span data-ttu-id="5b5f2-102">\<probing> Öğesi</span><span class="sxs-lookup"><span data-stu-id="5b5f2-102">\<probing> Element</span></span>
<span data-ttu-id="5b5f2-103">Derlemeler yüklenirken aranacak ortak dil çalışma zamanının uygulama temel alt dizinlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="5b5f2-103">Specifies application base subdirectories for the common language runtime to search when loading assemblies.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<probing>**  
  
## <a name="syntax"></a><span data-ttu-id="5b5f2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5b5f2-104">Syntax</span></span>  
  
```xml  
<probing privatePath="paths"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5b5f2-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="5b5f2-105">Attributes and Elements</span></span>  
 <span data-ttu-id="5b5f2-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5b5f2-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5b5f2-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5b5f2-107">Attributes</span></span>  
  
|<span data-ttu-id="5b5f2-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="5b5f2-108">Attribute</span></span>|<span data-ttu-id="5b5f2-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5b5f2-109">Description</span></span>|  
|---------------|-----------------|  
|`privatePath`|<span data-ttu-id="5b5f2-110">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="5b5f2-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="5b5f2-111">Derlemeler içerebilen uygulamanın temel dizininin alt dizinlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="5b5f2-111">Specifies subdirectories of the application's base directory that might contain assemblies.</span></span> <span data-ttu-id="5b5f2-112">Her alt dizini noktalı virgül ile sınırlandırın.</span><span class="sxs-lookup"><span data-stu-id="5b5f2-112">Delimit each subdirectory with a semicolon.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5b5f2-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="5b5f2-113">Child Elements</span></span>  

<span data-ttu-id="5b5f2-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="5b5f2-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5b5f2-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="5b5f2-115">Parent Elements</span></span>  
  
|<span data-ttu-id="5b5f2-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="5b5f2-116">Element</span></span>|<span data-ttu-id="5b5f2-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5b5f2-117">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="5b5f2-118">Derleme sürümü yeniden yönlendirmesi ve derlemelerin konumları hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="5b5f2-118">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="5b5f2-119">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="5b5f2-119">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="5b5f2-120">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="5b5f2-120">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="5b5f2-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="5b5f2-121">Example</span></span>  
 <span data-ttu-id="5b5f2-122">Aşağıdaki örnek, çalışma zamanının derlemeleri araması gereken uygulama temel alt dizinlerin nasıl yapılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="5b5f2-122">The following example shows how to specify application base subdirectories the runtime should search for assemblies.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <probing privatePath="bin;bin2\subbin;bin3"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5b5f2-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5b5f2-123">See also</span></span>

- [<span data-ttu-id="5b5f2-124">Çalışma zamanı ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="5b5f2-124">Runtime settings schema</span></span>](index.md)
- [<span data-ttu-id="5b5f2-125">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="5b5f2-125">Configuration file schema</span></span>](../index.md)
- [<span data-ttu-id="5b5f2-126">Bir derlemenin konumunu belirtin</span><span class="sxs-lookup"><span data-stu-id="5b5f2-126">Specify an assembly's location</span></span>](../../../../standard/assembly/location.md)
- [<span data-ttu-id="5b5f2-127">Çalışma zamanının derlemeleri nasıl konumlandırır</span><span class="sxs-lookup"><span data-stu-id="5b5f2-127">How the runtime locates assemblies</span></span>](../../../deployment/how-the-runtime-locates-assemblies.md)
