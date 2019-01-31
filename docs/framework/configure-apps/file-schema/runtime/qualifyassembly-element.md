---
title: <qualifyAssembly> Öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#qualifyAssembly
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/qualifyAssembly
helpviewer_keywords:
- container tags, <qualifyAssembly> element
- <qualifyAssembly> element
- qualifyAssembly element
ms.assetid: ad6442f6-1a9d-43b6-b733-04ac1b7f9b82
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e862c52235c3836c79506dc2e80a264ceceddab3
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55267837"
---
# <a name="qualifyassembly-element"></a><span data-ttu-id="44e72-102">\<qualifyAssembly > öğesi</span><span class="sxs-lookup"><span data-stu-id="44e72-102">\<qualifyAssembly> Element</span></span>
<span data-ttu-id="44e72-103">Kısmi bir adı kullanıldığında dinamik olarak yüklenmesi gereken bütünleştirilmiş kodun tam adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="44e72-103">Specifies the full name of the assembly that should be dynamically loaded when a partial name is used.</span></span>  
  
 <span data-ttu-id="44e72-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="44e72-104">\<configuration></span></span>  
<span data-ttu-id="44e72-105">\<çalışma zamanı ></span><span class="sxs-lookup"><span data-stu-id="44e72-105">\<runtime></span></span>  
<span data-ttu-id="44e72-106">\<assemblyBinding ></span><span class="sxs-lookup"><span data-stu-id="44e72-106">\<assemblyBinding></span></span>  
<span data-ttu-id="44e72-107">\<qualifyAssembly ></span><span class="sxs-lookup"><span data-stu-id="44e72-107">\<qualifyAssembly></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44e72-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="44e72-108">Syntax</span></span>  
  
```xml  
      <qualifyAssembly partialName=  
      "PartialAssemblyName"  
                 fullName="FullAssemblyName"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="44e72-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="44e72-109">Attributes and Elements</span></span>  
 <span data-ttu-id="44e72-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="44e72-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="44e72-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="44e72-111">Attributes</span></span>  
  
|<span data-ttu-id="44e72-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="44e72-112">Attribute</span></span>|<span data-ttu-id="44e72-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="44e72-113">Description</span></span>|  
|---------------|-----------------|  
|`partialName`|<span data-ttu-id="44e72-114">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="44e72-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="44e72-115">Kod içinde göründüğü gibi kısmi derlemenin adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="44e72-115">Specifies the partial name of the assembly as it appears in the code.</span></span>|  
|`fullName`|<span data-ttu-id="44e72-116">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="44e72-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="44e72-117">Genel derleme önbelleğinde göründüğü şekliyle tam derleme adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="44e72-117">Specifies the full name of the assembly as it appears in the global assembly cache.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="44e72-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="44e72-118">Child Elements</span></span>  
 <span data-ttu-id="44e72-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="44e72-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="44e72-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="44e72-120">Parent Elements</span></span>  
  
|<span data-ttu-id="44e72-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="44e72-121">Element</span></span>|<span data-ttu-id="44e72-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="44e72-122">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="44e72-123">Derleme sürümü yeniden yönlendirmesi ve derlemelerin konumları hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="44e72-123">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="44e72-124">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="44e72-124">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="44e72-125">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="44e72-125">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="44e72-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="44e72-126">Remarks</span></span>  
 <span data-ttu-id="44e72-127">Çağırma <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> yöntemi kısmi derleme adları kullanarak uygulama temel dizininin derlemesinde yalnızca aramak ortak dil çalışma zamanı neden olur.</span><span class="sxs-lookup"><span data-stu-id="44e72-127">Calling the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method using partial assembly names causes the common language runtime to look for the assembly only in the application base directory.</span></span> <span data-ttu-id="44e72-128">Kullanım  **\<qualifyAssembly >** öğesi uygulama yapılandırma dosyanızda aramak ortak dil çalışma zamanı (adı, sürümü, ortak anahtar belirteci ve kültür) tam bütünleştirilmiş kod bilgileri sağlayın ve genel derleme önbelleğinde derleme için.</span><span class="sxs-lookup"><span data-stu-id="44e72-128">Use the **\<qualifyAssembly>** element in your application configuration file to provide the full assembly information (name, version, public key token, and culture) and cause the common language runtime to search for the assembly in the global assembly cache.</span></span>  
  
 <span data-ttu-id="44e72-129">**FullName** özniteliği derleme kimliğinin dört alanı içermelidir: ad, sürüm, ortak anahtar belirteci ve kültür.</span><span class="sxs-lookup"><span data-stu-id="44e72-129">The **fullName** attribute must include the four fields of assembly identity: name, version, public key token, and culture.</span></span> <span data-ttu-id="44e72-130">**PartialName** öznitelik, bir derlemeyi kısmen başvurmalıdır.</span><span class="sxs-lookup"><span data-stu-id="44e72-130">The **partialName** attribute must partially reference an assembly.</span></span> <span data-ttu-id="44e72-131">Derlemenin metin adı (en yaygın durumda) en az belirtmeniz gerekir, ancak bu sürüm, ortak anahtar belirteci veya kültürü (veya herhangi bir birleşimini dört, ancak tüm dört) de içerebilir.</span><span class="sxs-lookup"><span data-stu-id="44e72-131">You must specify at least the assembly's text name (the most common case), but you can also include version, public key token, or culture (or any combination of the four, but not all four).</span></span> <span data-ttu-id="44e72-132">**PartialName** çağrınızda belirtilen adla eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="44e72-132">The **partialName** must match the name specified in your call.</span></span> <span data-ttu-id="44e72-133">Örneğin, belirtemezsiniz `"math"` olarak **partialName** yapılandırma dosyası ve çağrı özniteliğinde `Assembly.Load("math, Version=3.3.3.3")` kodunuzda.</span><span class="sxs-lookup"><span data-stu-id="44e72-133">For example, you cannot specify `"math"` as the **partialName** attribute in your configuration file and call `Assembly.Load("math, Version=3.3.3.3")` in your code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="44e72-134">Örnek</span><span class="sxs-lookup"><span data-stu-id="44e72-134">Example</span></span>  
 <span data-ttu-id="44e72-135">Aşağıdaki örnek, mantıksal çağrı kapatır `Assembly.Load("math")` içine `Assembly.Load("math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral")`.</span><span class="sxs-lookup"><span data-stu-id="44e72-135">The following example logically turns the call `Assembly.Load("math")` into `Assembly.Load("math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral")`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="44e72-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="44e72-136">See also</span></span>
- [<span data-ttu-id="44e72-137">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="44e72-137">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="44e72-138">Çalışma Zamanının Bütünleştirilmiş Kodların Konumunu Bulması</span><span class="sxs-lookup"><span data-stu-id="44e72-138">How the Runtime Locates Assemblies</span></span>](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="44e72-139">NIB: Kısmi derleme başvuruları</span><span class="sxs-lookup"><span data-stu-id="44e72-139">NIB: Partial Assembly References</span></span>](https://msdn.microsoft.com/library/ec90f07a-398c-4306-9401-0fc5ff9cb59f)
