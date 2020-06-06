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
ms.openlocfilehash: 2de8c752867d00708173d11d1851f415a2e8518d
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154211"
---
# <a name="dependentassembly-element"></a><span data-ttu-id="31a14-102">\<dependentAssembly> Öğesi</span><span class="sxs-lookup"><span data-stu-id="31a14-102">\<dependentAssembly> Element</span></span>
<span data-ttu-id="31a14-103">Her bir derleme için bağlama ilkesi ve derleme konumunu saklar.</span><span class="sxs-lookup"><span data-stu-id="31a14-103">Encapsulates binding policy and assembly location for each assembly.</span></span> <span data-ttu-id="31a14-104">`dependentAssembly`Her derleme için bir öğe kullanın.</span><span class="sxs-lookup"><span data-stu-id="31a14-104">Use one `dependentAssembly` element for each assembly.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dependentAssembly>**  
  
## <a name="syntax"></a><span data-ttu-id="31a14-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="31a14-105">Syntax</span></span>  
  
```xml  
<dependentAssembly>
</dependentAssembly>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="31a14-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="31a14-106">Attributes and Elements</span></span>  
 <span data-ttu-id="31a14-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="31a14-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="31a14-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="31a14-108">Attributes</span></span>  
 <span data-ttu-id="31a14-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="31a14-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="31a14-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="31a14-110">Child Elements</span></span>  
  
|<span data-ttu-id="31a14-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="31a14-111">Element</span></span>|<span data-ttu-id="31a14-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="31a14-112">Description</span></span>|  
|-------------|-----------------|  
|`assemblyIdentity`|<span data-ttu-id="31a14-113">Derlemeyle ilgili tanımlama bilgilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="31a14-113">Contains identifying information about the assembly.</span></span> <span data-ttu-id="31a14-114">Bu öğe her bir `dependentAssembly` öğeye eklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="31a14-114">This element must be included in each `dependentAssembly` element.</span></span>|  
|`codeBase`|<span data-ttu-id="31a14-115">Çalışma zamanının, bilgisayarda yüklü değilse paylaşılan bir derlemeyi bulabilecekleri yeri belirtir.</span><span class="sxs-lookup"><span data-stu-id="31a14-115">Specifies where the runtime can find a shared assembly if it is not installed on the computer.</span></span>|  
|`bindingRedirect`|<span data-ttu-id="31a14-116">Bir derleme sürümünü diğerine yeniden yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="31a14-116">Redirects one assembly version to another.</span></span>|  
|`publisherPolicy`|<span data-ttu-id="31a14-117">Çalışma zamanının bu derleme için yayımcı ilkesi uygulanıp uygulanmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="31a14-117">Specifies whether the runtime applies publisher policy for this assembly.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="31a14-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="31a14-118">Parent Elements</span></span>  
  
|<span data-ttu-id="31a14-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="31a14-119">Element</span></span>|<span data-ttu-id="31a14-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="31a14-120">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="31a14-121">Derleme sürümü yeniden yönlendirmesi ve derlemelerin konumları hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="31a14-121">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="31a14-122">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="31a14-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="31a14-123">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="31a14-123">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="31a14-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="31a14-124">Example</span></span>  
 <span data-ttu-id="31a14-125">Aşağıdaki örnek, iki derleme için derleme bilgilerinin nasıl kapsüllagösterdiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="31a14-125">The following example shows how to encapsulate assembly information for two assemblies.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="31a14-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="31a14-126">See also</span></span>

- [<span data-ttu-id="31a14-127">Çalışma zamanı ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="31a14-127">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="31a14-128">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="31a14-128">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="31a14-129">Derleme Sürümlerini Yönlendirme</span><span class="sxs-lookup"><span data-stu-id="31a14-129">Redirecting Assembly Versions</span></span>](../../redirect-assembly-versions.md)
