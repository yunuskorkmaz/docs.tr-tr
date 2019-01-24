---
title: '&lt;yoklama&gt; öğesi'
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
ms.openlocfilehash: 711903656d8bcce3a2d213af68160707a55a48e4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54700006"
---
# <a name="ltprobinggt-element"></a><span data-ttu-id="19d81-102">&lt;yoklama&gt; öğesi</span><span class="sxs-lookup"><span data-stu-id="19d81-102">&lt;probing&gt; Element</span></span>
<span data-ttu-id="19d81-103">Derlemeler yüklenirken aramak ortak dil çalışma zamanı için uygulama temel alt dizinleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="19d81-103">Specifies application base subdirectories for the common language runtime to search when loading assemblies.</span></span>  
  
 <span data-ttu-id="19d81-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="19d81-104">\<configuration></span></span>  
<span data-ttu-id="19d81-105">\<çalışma zamanı ></span><span class="sxs-lookup"><span data-stu-id="19d81-105">\<runtime></span></span>  
<span data-ttu-id="19d81-106">\<assemblyBinding ></span><span class="sxs-lookup"><span data-stu-id="19d81-106">\<assemblyBinding></span></span>  
<span data-ttu-id="19d81-107">\<yoklama ></span><span class="sxs-lookup"><span data-stu-id="19d81-107">\<probing></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19d81-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="19d81-108">Syntax</span></span>  
  
```xml  
<probing privatePath="paths"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="19d81-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="19d81-109">Attributes and Elements</span></span>  
 <span data-ttu-id="19d81-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="19d81-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="19d81-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="19d81-111">Attributes</span></span>  
  
|<span data-ttu-id="19d81-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="19d81-112">Attribute</span></span>|<span data-ttu-id="19d81-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="19d81-113">Description</span></span>|  
|---------------|-----------------|  
|`privatePath`|<span data-ttu-id="19d81-114">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="19d81-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="19d81-115">Derlemeleri içerebilir uygulama temel dizininin alt dizinleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="19d81-115">Specifies subdirectories of the application's base directory that might contain assemblies.</span></span> <span data-ttu-id="19d81-116">Her alt noktalı virgül ile sınırlandırın.</span><span class="sxs-lookup"><span data-stu-id="19d81-116">Delimit each subdirectory with a semicolon.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="19d81-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="19d81-117">Child Elements</span></span>  
 <span data-ttu-id="19d81-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="19d81-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="19d81-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="19d81-119">Parent Elements</span></span>  
  
|<span data-ttu-id="19d81-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="19d81-120">Element</span></span>|<span data-ttu-id="19d81-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="19d81-121">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="19d81-122">Derleme sürümü yeniden yönlendirmesi ve derlemelerin konumları hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="19d81-122">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="19d81-123">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="19d81-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="19d81-124">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="19d81-124">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="19d81-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="19d81-125">Example</span></span>  
 <span data-ttu-id="19d81-126">Aşağıdaki örnek, çalışma zamanı derlemeleri araması gereken uygulama temel alt dizinleri belirtmek gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="19d81-126">The following example shows how to specify application base subdirectories the runtime should search for assemblies.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <probing privatePath="bin;bin2\subbin;bin3"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="19d81-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="19d81-127">See also</span></span>
- [<span data-ttu-id="19d81-128">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="19d81-128">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="19d81-129">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="19d81-129">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="19d81-130">Bütünleştirilmiş Kodun Konumunu Belirtme</span><span class="sxs-lookup"><span data-stu-id="19d81-130">Specifying an Assembly's Location</span></span>](../../../../../docs/framework/configure-apps/specify-assembly-location.md)
- [<span data-ttu-id="19d81-131">Çalışma Zamanının Bütünleştirilmiş Kodların Konumunu Bulması</span><span class="sxs-lookup"><span data-stu-id="19d81-131">How the Runtime Locates Assemblies</span></span>](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
