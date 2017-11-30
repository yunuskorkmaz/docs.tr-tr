---
title: "&lt;qualifyAssembly&gt; öğesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#qualifyAssembly
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/qualifyAssembly
helpviewer_keywords:
- container tags, <qualifyAssembly> element
- <qualifyAssembly> element
- qualifyAssembly element
ms.assetid: ad6442f6-1a9d-43b6-b733-04ac1b7f9b82
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 521bbccd83f224cc824dae41309715d65472454e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltqualifyassemblygt-element"></a><span data-ttu-id="4d4a8-102">&lt;qualifyAssembly&gt; öğesi</span><span class="sxs-lookup"><span data-stu-id="4d4a8-102">&lt;qualifyAssembly&gt; Element</span></span>
<span data-ttu-id="4d4a8-103">Kısmi bir ad kullanıldığında dinamik olarak yüklenmesi gereken derlemenin tam adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="4d4a8-103">Specifies the full name of the assembly that should be dynamically loaded when a partial name is used.</span></span>  
  
 <span data-ttu-id="4d4a8-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="4d4a8-104">\<configuration></span></span>  
<span data-ttu-id="4d4a8-105">\<çalışma zamanı ></span><span class="sxs-lookup"><span data-stu-id="4d4a8-105">\<runtime></span></span>  
<span data-ttu-id="4d4a8-106">\<assemblyBinding ></span><span class="sxs-lookup"><span data-stu-id="4d4a8-106">\<assemblyBinding></span></span>  
<span data-ttu-id="4d4a8-107">\<qualifyAssembly ></span><span class="sxs-lookup"><span data-stu-id="4d4a8-107">\<qualifyAssembly></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d4a8-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4d4a8-108">Syntax</span></span>  
  
```xml  
      <qualifyAssembly partialName=  
      "PartialAssemblyName"  
                 fullName="FullAssemblyName"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4d4a8-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="4d4a8-109">Attributes and Elements</span></span>  
 <span data-ttu-id="4d4a8-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4d4a8-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4d4a8-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="4d4a8-111">Attributes</span></span>  
  
|<span data-ttu-id="4d4a8-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="4d4a8-112">Attribute</span></span>|<span data-ttu-id="4d4a8-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4d4a8-113">Description</span></span>|  
|---------------|-----------------|  
|`partialName`|<span data-ttu-id="4d4a8-114">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="4d4a8-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="4d4a8-115">Kodda göründüğü gibi derleme kısmi adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="4d4a8-115">Specifies the partial name of the assembly as it appears in the code.</span></span>|  
|`fullName`|<span data-ttu-id="4d4a8-116">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="4d4a8-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="4d4a8-117">Genel derleme önbelleğinde göründüğü gibi derlemenin tam adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="4d4a8-117">Specifies the full name of the assembly as it appears in the global assembly cache.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4d4a8-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="4d4a8-118">Child Elements</span></span>  
 <span data-ttu-id="4d4a8-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="4d4a8-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4d4a8-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="4d4a8-120">Parent Elements</span></span>  
  
|<span data-ttu-id="4d4a8-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="4d4a8-121">Element</span></span>|<span data-ttu-id="4d4a8-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4d4a8-122">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="4d4a8-123">Derleme sürümü yeniden yönlendirmesi ve derlemelerin konumları hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="4d4a8-123">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="4d4a8-124">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="4d4a8-124">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="4d4a8-125">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="4d4a8-125">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4d4a8-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4d4a8-126">Remarks</span></span>  
 <span data-ttu-id="4d4a8-127">Çağırma <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> kısmi derleme adları kullanarak yöntemi uygulamanın ana dizin derlemede yalnızca aramak ortak dil çalışma zamanı neden olur.</span><span class="sxs-lookup"><span data-stu-id="4d4a8-127">Calling the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method using partial assembly names causes the common language runtime to look for the assembly only in the application base directory.</span></span> <span data-ttu-id="4d4a8-128">Kullanım  **\<qualifyAssembly >** aramak ortak dil çalışma zamanı neden ve tam derleme bilgileri (ad, sürüm, ortak anahtar belirteci ve kültür) sağlamak için uygulama yapılandırma dosyasında öğesi genel derleme önbelleğinde derleme için.</span><span class="sxs-lookup"><span data-stu-id="4d4a8-128">Use the **\<qualifyAssembly>** element in your application configuration file to provide the full assembly information (name, version, public key token, and culture) and cause the common language runtime to search for the assembly in the global assembly cache.</span></span>  
  
 <span data-ttu-id="4d4a8-129">**FullName** özniteliği derleme kimliği dört alanları içermelidir: ad, sürüm, ortak anahtar belirteci ve kültür.</span><span class="sxs-lookup"><span data-stu-id="4d4a8-129">The **fullName** attribute must include the four fields of assembly identity: name, version, public key token, and culture.</span></span> <span data-ttu-id="4d4a8-130">**PartialName** öznitelik, bir derlemeyi kısmen başvurmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4d4a8-130">The **partialName** attribute must partially reference an assembly.</span></span> <span data-ttu-id="4d4a8-131">En az derlemenin metin adı (en yaygın harf) belirtmeniz gerekir, ancak sürüm, ortak anahtar belirteci veya kültür (veya dört ancak tüm dört herhangi bir birleşimini) de içerir.</span><span class="sxs-lookup"><span data-stu-id="4d4a8-131">You must specify at least the assembly's text name (the most common case), but you can also include version, public key token, or culture (or any combination of the four, but not all four).</span></span> <span data-ttu-id="4d4a8-132">**PartialName** , çağrısında belirtilen adıyla eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="4d4a8-132">The **partialName** must match the name specified in your call.</span></span> <span data-ttu-id="4d4a8-133">Örneğin, belirtemezsiniz `"math"` olarak **partialName** yapılandırma dosyasını ve arama özniteliğinde `Assembly.Load("math, Version=3.3.3.3")` kodunuzda.</span><span class="sxs-lookup"><span data-stu-id="4d4a8-133">For example, you cannot specify `"math"` as the **partialName** attribute in your configuration file and call `Assembly.Load("math, Version=3.3.3.3")` in your code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4d4a8-134">Örnek</span><span class="sxs-lookup"><span data-stu-id="4d4a8-134">Example</span></span>  
 <span data-ttu-id="4d4a8-135">Aşağıdaki örnekte, mantıksal olarak çağrı kapatır `Assembly.Load("math")` içine `Assembly.Load("math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral")`.</span><span class="sxs-lookup"><span data-stu-id="4d4a8-135">The following example logically turns the call `Assembly.Load("math")` into `Assembly.Load("math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral")`.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <qualifyAssembly partialName="math"   
                         fullName=  
"math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4d4a8-136">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4d4a8-136">See Also</span></span>  
 [<span data-ttu-id="4d4a8-137">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="4d4a8-137">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="4d4a8-138">Çalışma zamanı derlemeleri nasıl bulur</span><span class="sxs-lookup"><span data-stu-id="4d4a8-138">How the Runtime Locates Assemblies</span></span>](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [<span data-ttu-id="4d4a8-139">NIB: Kısmi derleme başvuruları</span><span class="sxs-lookup"><span data-stu-id="4d4a8-139">NIB: Partial Assembly References</span></span>](http://msdn.microsoft.com/en-us/ec90f07a-398c-4306-9401-0fc5ff9cb59f)
