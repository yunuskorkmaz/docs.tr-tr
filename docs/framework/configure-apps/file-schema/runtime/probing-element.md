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
ms.openlocfilehash: 1435ee8ea887b5d7d3e785eef0f25ffed14b1b97
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91195278"
---
# <a name="probing-element"></a><span data-ttu-id="647df-102">\<probing> Öğesi</span><span class="sxs-lookup"><span data-stu-id="647df-102">\<probing> Element</span></span>

<span data-ttu-id="647df-103">Derlemeler yüklenirken aranacak ortak dil çalışma zamanının uygulama temel alt dizinlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="647df-103">Specifies application base subdirectories for the common language runtime to search when loading assemblies.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<probing>**  
  
## <a name="syntax"></a><span data-ttu-id="647df-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="647df-104">Syntax</span></span>  
  
```xml  
<probing privatePath="paths"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="647df-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="647df-105">Attributes and Elements</span></span>  

 <span data-ttu-id="647df-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="647df-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="647df-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="647df-107">Attributes</span></span>  
  
|<span data-ttu-id="647df-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="647df-108">Attribute</span></span>|<span data-ttu-id="647df-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="647df-109">Description</span></span>|  
|---------------|-----------------|  
|`privatePath`|<span data-ttu-id="647df-110">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="647df-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="647df-111">Derlemeler içerebilen uygulamanın temel dizininin alt dizinlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="647df-111">Specifies subdirectories of the application's base directory that might contain assemblies.</span></span> <span data-ttu-id="647df-112">Her alt dizini noktalı virgül ile sınırlandırın.</span><span class="sxs-lookup"><span data-stu-id="647df-112">Delimit each subdirectory with a semicolon.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="647df-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="647df-113">Child Elements</span></span>  

<span data-ttu-id="647df-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="647df-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="647df-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="647df-115">Parent Elements</span></span>  
  
|<span data-ttu-id="647df-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="647df-116">Element</span></span>|<span data-ttu-id="647df-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="647df-117">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="647df-118">Derleme sürümü yeniden yönlendirmesi ve derlemelerin konumları hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="647df-118">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="647df-119">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="647df-119">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="647df-120">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="647df-120">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="647df-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="647df-121">Example</span></span>  

 <span data-ttu-id="647df-122">Aşağıdaki örnek, çalışma zamanının derlemeleri araması gereken uygulama temel alt dizinlerin nasıl yapılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="647df-122">The following example shows how to specify application base subdirectories the runtime should search for assemblies.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <probing privatePath="bin;bin2\subbin;bin3"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="647df-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="647df-123">See also</span></span>

- [<span data-ttu-id="647df-124">Çalışma zamanı ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="647df-124">Runtime settings schema</span></span>](index.md)
- [<span data-ttu-id="647df-125">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="647df-125">Configuration file schema</span></span>](../index.md)
- [<span data-ttu-id="647df-126">Bir derlemenin konumunu belirtin</span><span class="sxs-lookup"><span data-stu-id="647df-126">Specify an assembly's location</span></span>](../../../../standard/assembly/location.md)
- [<span data-ttu-id="647df-127">Çalışma zamanının derlemeleri nasıl konumlandırır</span><span class="sxs-lookup"><span data-stu-id="647df-127">How the runtime locates assemblies</span></span>](../../../deployment/how-the-runtime-locates-assemblies.md)
