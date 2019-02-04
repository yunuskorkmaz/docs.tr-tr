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
ms.openlocfilehash: ec72b1a1e3a2526dfb52f562be9fe92c677747ec
ms.sourcegitcommit: b8ace47d839f943f785b89e2fff8092b0bf8f565
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55674678"
---
# <a name="qualifyassembly-element"></a><span data-ttu-id="0b8ca-102">\<qualifyAssembly > öğesi</span><span class="sxs-lookup"><span data-stu-id="0b8ca-102">\<qualifyAssembly> Element</span></span>
<span data-ttu-id="0b8ca-103">Kısmi bir adı kullanıldığında dinamik olarak yüklenmesi gereken bütünleştirilmiş kodun tam adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="0b8ca-103">Specifies the full name of the assembly that should be dynamically loaded when a partial name is used.</span></span>  
  
 <span data-ttu-id="0b8ca-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="0b8ca-104">\<configuration></span></span>  
<span data-ttu-id="0b8ca-105">\<çalışma zamanı ></span><span class="sxs-lookup"><span data-stu-id="0b8ca-105">\<runtime></span></span>  
<span data-ttu-id="0b8ca-106">\<assemblyBinding ></span><span class="sxs-lookup"><span data-stu-id="0b8ca-106">\<assemblyBinding></span></span>  
<span data-ttu-id="0b8ca-107">\<qualifyAssembly ></span><span class="sxs-lookup"><span data-stu-id="0b8ca-107">\<qualifyAssembly></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b8ca-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0b8ca-108">Syntax</span></span>  
  
```xml  
      <qualifyAssembly partialName=  
      "PartialAssemblyName"  
                 fullName="FullAssemblyName"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0b8ca-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="0b8ca-109">Attributes and Elements</span></span>  
 <span data-ttu-id="0b8ca-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0b8ca-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0b8ca-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="0b8ca-111">Attributes</span></span>  
  
|<span data-ttu-id="0b8ca-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="0b8ca-112">Attribute</span></span>|<span data-ttu-id="0b8ca-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0b8ca-113">Description</span></span>|  
|---------------|-----------------|  
|`partialName`|<span data-ttu-id="0b8ca-114">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="0b8ca-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="0b8ca-115">Kod içinde göründüğü gibi kısmi derlemenin adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="0b8ca-115">Specifies the partial name of the assembly as it appears in the code.</span></span>|  
|`fullName`|<span data-ttu-id="0b8ca-116">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="0b8ca-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="0b8ca-117">Genel derleme önbelleğinde göründüğü şekliyle tam derleme adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="0b8ca-117">Specifies the full name of the assembly as it appears in the global assembly cache.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0b8ca-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="0b8ca-118">Child Elements</span></span>  
 <span data-ttu-id="0b8ca-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="0b8ca-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0b8ca-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="0b8ca-120">Parent Elements</span></span>  
  
|<span data-ttu-id="0b8ca-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="0b8ca-121">Element</span></span>|<span data-ttu-id="0b8ca-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0b8ca-122">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="0b8ca-123">Derleme sürümü yeniden yönlendirmesi ve derlemelerin konumları hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="0b8ca-123">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="0b8ca-124">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="0b8ca-124">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="0b8ca-125">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="0b8ca-125">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0b8ca-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0b8ca-126">Remarks</span></span>  
 <span data-ttu-id="0b8ca-127">Çağırma <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> yöntemi kısmi derleme adları kullanarak uygulama temel dizininin derlemesinde yalnızca aramak ortak dil çalışma zamanı neden olur.</span><span class="sxs-lookup"><span data-stu-id="0b8ca-127">Calling the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method using partial assembly names causes the common language runtime to look for the assembly only in the application base directory.</span></span> <span data-ttu-id="0b8ca-128">Kullanım  **\<qualifyAssembly >** öğesi uygulama yapılandırma dosyanızda aramak ortak dil çalışma zamanı (adı, sürümü, ortak anahtar belirteci ve kültür) tam bütünleştirilmiş kod bilgileri sağlayın ve genel derleme önbelleğinde derleme için.</span><span class="sxs-lookup"><span data-stu-id="0b8ca-128">Use the **\<qualifyAssembly>** element in your application configuration file to provide the full assembly information (name, version, public key token, and culture) and cause the common language runtime to search for the assembly in the global assembly cache.</span></span>  
  
 <span data-ttu-id="0b8ca-129">**FullName** özniteliği derleme kimliğinin dört alanı içermelidir: ad, sürüm, ortak anahtar belirteci ve kültür.</span><span class="sxs-lookup"><span data-stu-id="0b8ca-129">The **fullName** attribute must include the four fields of assembly identity: name, version, public key token, and culture.</span></span> <span data-ttu-id="0b8ca-130">**PartialName** öznitelik, bir derlemeyi kısmen başvurmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0b8ca-130">The **partialName** attribute must partially reference an assembly.</span></span> <span data-ttu-id="0b8ca-131">Derlemenin metin adı (en yaygın durumda) en az belirtmeniz gerekir, ancak bu sürüm, ortak anahtar belirteci veya kültürü (veya herhangi bir birleşimini dört, ancak tüm dört) de içerebilir.</span><span class="sxs-lookup"><span data-stu-id="0b8ca-131">You must specify at least the assembly's text name (the most common case), but you can also include version, public key token, or culture (or any combination of the four, but not all four).</span></span> <span data-ttu-id="0b8ca-132">**PartialName** çağrınızda belirtilen adla eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="0b8ca-132">The **partialName** must match the name specified in your call.</span></span> <span data-ttu-id="0b8ca-133">Örneğin, belirtemezsiniz `"math"` olarak **partialName** yapılandırma dosyası ve çağrı özniteliğinde `Assembly.Load("math, Version=3.3.3.3")` kodunuzda.</span><span class="sxs-lookup"><span data-stu-id="0b8ca-133">For example, you cannot specify `"math"` as the **partialName** attribute in your configuration file and call `Assembly.Load("math, Version=3.3.3.3")` in your code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0b8ca-134">Örnek</span><span class="sxs-lookup"><span data-stu-id="0b8ca-134">Example</span></span>  
 <span data-ttu-id="0b8ca-135">Aşağıdaki örnek, mantıksal çağrı kapatır `Assembly.Load("math")` içine `Assembly.Load("math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral")`.</span><span class="sxs-lookup"><span data-stu-id="0b8ca-135">The following example logically turns the call `Assembly.Load("math")` into `Assembly.Load("math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral")`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0b8ca-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0b8ca-136">See also</span></span>
- [<span data-ttu-id="0b8ca-137">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="0b8ca-137">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="0b8ca-138">Çalışma Zamanının Bütünleştirilmiş Kodların Konumunu Bulması</span><span class="sxs-lookup"><span data-stu-id="0b8ca-138">How the Runtime Locates Assemblies</span></span>](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- <span data-ttu-id="0b8ca-139">[Kısmi derleme başvuruları](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/0a7zy9z5(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="0b8ca-139">[Partial Assembly References](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/0a7zy9z5(v=vs.100))</span></span>
