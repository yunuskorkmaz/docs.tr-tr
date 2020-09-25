---
title: <dependentAssembly> Öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly
- http://schemas.microsoft.com/.NetConfiguration/v2.0#dependentAssembly
helpviewer_keywords:
- container tags, <dependentAssembly> element
- dependentAssembly element
- <dependentAssembly> element
ms.assetid: 14e95627-dd79-4b82-ac85-e682aa3a31d8
ms.openlocfilehash: 6a924b1998651c923c64429029a118dd1e9ede69
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91199009"
---
# <a name="dependentassembly-element"></a><span data-ttu-id="fe77f-102">\<dependentAssembly> Öğesi</span><span class="sxs-lookup"><span data-stu-id="fe77f-102">\<dependentAssembly> Element</span></span>

<span data-ttu-id="fe77f-103">Her bir derleme için bağlama ilkesi ve derleme konumunu saklar.</span><span class="sxs-lookup"><span data-stu-id="fe77f-103">Encapsulates binding policy and assembly location for each assembly.</span></span> <span data-ttu-id="fe77f-104">`dependentAssembly`Her derleme için bir öğe kullanın.</span><span class="sxs-lookup"><span data-stu-id="fe77f-104">Use one `dependentAssembly` element for each assembly.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dependentAssembly>**  
  
## <a name="syntax"></a><span data-ttu-id="fe77f-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="fe77f-105">Syntax</span></span>  
  
```xml  
<dependentAssembly>
</dependentAssembly>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fe77f-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="fe77f-106">Attributes and Elements</span></span>  

 <span data-ttu-id="fe77f-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="fe77f-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fe77f-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="fe77f-108">Attributes</span></span>  

 <span data-ttu-id="fe77f-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="fe77f-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="fe77f-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="fe77f-110">Child Elements</span></span>  
  
|<span data-ttu-id="fe77f-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="fe77f-111">Element</span></span>|<span data-ttu-id="fe77f-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fe77f-112">Description</span></span>|  
|-------------|-----------------|  
|`assemblyIdentity`|<span data-ttu-id="fe77f-113">Derlemeyle ilgili tanımlama bilgilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="fe77f-113">Contains identifying information about the assembly.</span></span> <span data-ttu-id="fe77f-114">Bu öğe her bir `dependentAssembly` öğeye eklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="fe77f-114">This element must be included in each `dependentAssembly` element.</span></span>|  
|`codeBase`|<span data-ttu-id="fe77f-115">Çalışma zamanının, bilgisayarda yüklü değilse paylaşılan bir derlemeyi bulabilecekleri yeri belirtir.</span><span class="sxs-lookup"><span data-stu-id="fe77f-115">Specifies where the runtime can find a shared assembly if it is not installed on the computer.</span></span>|  
|`bindingRedirect`|<span data-ttu-id="fe77f-116">Bir derleme sürümünü diğerine yeniden yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="fe77f-116">Redirects one assembly version to another.</span></span>|  
|`publisherPolicy`|<span data-ttu-id="fe77f-117">Çalışma zamanının bu derleme için yayımcı ilkesi uygulanıp uygulanmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="fe77f-117">Specifies whether the runtime applies publisher policy for this assembly.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fe77f-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="fe77f-118">Parent Elements</span></span>  
  
|<span data-ttu-id="fe77f-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="fe77f-119">Element</span></span>|<span data-ttu-id="fe77f-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fe77f-120">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="fe77f-121">Derleme sürümü yeniden yönlendirmesi ve derlemelerin konumları hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="fe77f-121">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="fe77f-122">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="fe77f-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="fe77f-123">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="fe77f-123">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="fe77f-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="fe77f-124">Example</span></span>  

 <span data-ttu-id="fe77f-125">Aşağıdaki örnek, iki derleme için derleme bilgilerinin nasıl kapsüllagösterdiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="fe77f-125">The following example shows how to encapsulate assembly information for two assemblies.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                              publicKeyToken="32ab4ba45e0a69a1"  
                              culture="neutral" />  
            <!--Redirection and codeBase policy for myAssembly.-->  
         </dependentAssembly>  
         <dependentAssembly>  
            <assemblyIdentity name="mySecondAssembly"  
                              publicKeyToken="32ab4ba45e0a69a1"  
                              culture="neutral" />  
            <!--Redirection and codeBase policy for mySecondAssembly.-->  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="fe77f-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fe77f-126">See also</span></span>

- [<span data-ttu-id="fe77f-127">Çalışma zamanı ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="fe77f-127">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="fe77f-128">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="fe77f-128">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="fe77f-129">Derleme Sürümlerini Yönlendirme</span><span class="sxs-lookup"><span data-stu-id="fe77f-129">Redirecting Assembly Versions</span></span>](../../redirect-assembly-versions.md)
