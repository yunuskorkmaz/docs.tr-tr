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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154211"
---
# <a name="dependentassembly-element"></a><span data-ttu-id="f572a-102">\<bağımlıMontaj> Öğesi</span><span class="sxs-lookup"><span data-stu-id="f572a-102">\<dependentAssembly> Element</span></span>
<span data-ttu-id="f572a-103">Her bir derleme için bağlama ilkesi ve derleme konumunu saklar.</span><span class="sxs-lookup"><span data-stu-id="f572a-103">Encapsulates binding policy and assembly location for each assembly.</span></span> <span data-ttu-id="f572a-104">Her `dependentAssembly` montaj için bir öğe kullanın.</span><span class="sxs-lookup"><span data-stu-id="f572a-104">Use one `dependentAssembly` element for each assembly.</span></span>  
  
<span data-ttu-id="f572a-105">[**\<yapılandırma>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="f572a-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="f572a-106">&nbsp;&nbsp;[**\<çalışma zamanı>**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="f572a-106">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="f572a-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<montajBağlama>**](assemblybinding-element-for-runtime.md)</span><span class="sxs-lookup"><span data-stu-id="f572a-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)</span></span>\
<span data-ttu-id="f572a-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bağımlıAssembly>**</span><span class="sxs-lookup"><span data-stu-id="f572a-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dependentAssembly>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f572a-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f572a-109">Syntax</span></span>  
  
```xml  
<dependentAssembly>
</dependentAssembly>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f572a-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f572a-110">Attributes and Elements</span></span>  
 <span data-ttu-id="f572a-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f572a-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f572a-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f572a-112">Attributes</span></span>  
 <span data-ttu-id="f572a-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="f572a-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f572a-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f572a-114">Child Elements</span></span>  
  
|<span data-ttu-id="f572a-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="f572a-115">Element</span></span>|<span data-ttu-id="f572a-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f572a-116">Description</span></span>|  
|-------------|-----------------|  
|`assemblyIdentity`|<span data-ttu-id="f572a-117">Derleme hakkında tanımlayıcı bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="f572a-117">Contains identifying information about the assembly.</span></span> <span data-ttu-id="f572a-118">Bu öğe her `dependentAssembly` öğeye dahil edilmelidir.</span><span class="sxs-lookup"><span data-stu-id="f572a-118">This element must be included in each `dependentAssembly` element.</span></span>|  
|`codeBase`|<span data-ttu-id="f572a-119">Bilgisayarda yüklü değilse, çalışma zamanının paylaşılan bir derlemeyi nerede bulabileceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="f572a-119">Specifies where the runtime can find a shared assembly if it is not installed on the computer.</span></span>|  
|`bindingRedirect`|<span data-ttu-id="f572a-120">Bir derleme sürümünü diğerine yeniden yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="f572a-120">Redirects one assembly version to another.</span></span>|  
|`publisherPolicy`|<span data-ttu-id="f572a-121">Çalışma zamanının bu derleme için yayımcı ilkesini kullanıp uygulamayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="f572a-121">Specifies whether the runtime applies publisher policy for this assembly.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f572a-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f572a-122">Parent Elements</span></span>  
  
|<span data-ttu-id="f572a-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="f572a-123">Element</span></span>|<span data-ttu-id="f572a-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f572a-124">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="f572a-125">Derleme sürümü yeniden yönlendirmesi ve derlemelerin konumları hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="f572a-125">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="f572a-126">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="f572a-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="f572a-127">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="f572a-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="f572a-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="f572a-128">Example</span></span>  
 <span data-ttu-id="f572a-129">Aşağıdaki örnek, iki derleme için derleme bilgilerinin nasıl kapsüllenebildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="f572a-129">The following example shows how to encapsulate assembly information for two assemblies.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f572a-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f572a-130">See also</span></span>

- [<span data-ttu-id="f572a-131">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="f572a-131">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="f572a-132">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="f572a-132">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="f572a-133">Bütünleştirilmiş Kod Sürümlerini Yönlendirme</span><span class="sxs-lookup"><span data-stu-id="f572a-133">Redirecting Assembly Versions</span></span>](../../redirect-assembly-versions.md)
