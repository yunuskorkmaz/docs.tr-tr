---
description: 'Daha fazla bilgi edinin: <qualifyAssembly> öğesi'
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
ms.openlocfilehash: 16891cca40d907d0ca32aea7f610e84305fcd0e6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802468"
---
# <a name="qualifyassembly-element"></a><span data-ttu-id="4b9f6-103">\<qualifyAssembly> Öğesi</span><span class="sxs-lookup"><span data-stu-id="4b9f6-103">\<qualifyAssembly> Element</span></span>

<span data-ttu-id="4b9f6-104">Kısmi bir ad kullanıldığında dinamik olarak yüklenmesi gereken derlemenin tam adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="4b9f6-104">Specifies the full name of the assembly that should be dynamically loaded when a partial name is used.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<qualifyAssembly>**  
  
## <a name="syntax"></a><span data-ttu-id="4b9f6-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="4b9f6-105">Syntax</span></span>  
  
```xml  
      <qualifyAssembly partialName=  
      "PartialAssemblyName"  
                 fullName="FullAssemblyName"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4b9f6-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="4b9f6-106">Attributes and Elements</span></span>  

 <span data-ttu-id="4b9f6-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4b9f6-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4b9f6-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="4b9f6-108">Attributes</span></span>  
  
|<span data-ttu-id="4b9f6-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="4b9f6-109">Attribute</span></span>|<span data-ttu-id="4b9f6-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4b9f6-110">Description</span></span>|  
|---------------|-----------------|  
|`partialName`|<span data-ttu-id="4b9f6-111">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="4b9f6-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="4b9f6-112">Kodda göründüğü gibi derlemenin kısmi adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="4b9f6-112">Specifies the partial name of the assembly as it appears in the code.</span></span>|  
|`fullName`|<span data-ttu-id="4b9f6-113">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="4b9f6-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="4b9f6-114">Derlemenin genel derleme önbelleğinde göründüğü haliyle tam adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="4b9f6-114">Specifies the full name of the assembly as it appears in the global assembly cache.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4b9f6-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="4b9f6-115">Child Elements</span></span>  

 <span data-ttu-id="4b9f6-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="4b9f6-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4b9f6-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="4b9f6-117">Parent Elements</span></span>  
  
|<span data-ttu-id="4b9f6-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="4b9f6-118">Element</span></span>|<span data-ttu-id="4b9f6-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4b9f6-119">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="4b9f6-120">Derleme sürümü yeniden yönlendirmesi ve derlemelerin konumları hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="4b9f6-120">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="4b9f6-121">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="4b9f6-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="4b9f6-122">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="4b9f6-122">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4b9f6-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4b9f6-123">Remarks</span></span>  

 <span data-ttu-id="4b9f6-124"><xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>Kısmi derleme adlarını kullanarak yöntemi çağırmak, ortak dil çalışma zamanının derlemeyi yalnızca uygulama temel dizininde aramasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="4b9f6-124">Calling the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method using partial assembly names causes the common language runtime to look for the assembly only in the application base directory.</span></span> <span data-ttu-id="4b9f6-125">**\<qualifyAssembly>** Tüm derleme bilgilerini (ad, sürüm, ortak anahtar belirteci ve kültür) sağlamak ve ortak dil çalışma zamanının genel derleme önbelleğinde derlemeyi aramasını sağlamak için uygulama yapılandırma dosyanızda öğesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="4b9f6-125">Use the **\<qualifyAssembly>** element in your application configuration file to provide the full assembly information (name, version, public key token, and culture) and cause the common language runtime to search for the assembly in the global assembly cache.</span></span>  
  
 <span data-ttu-id="4b9f6-126">**FullName** özniteliği, derleme kimliğinin dört alanını içermelidir: ad, sürüm, ortak anahtar belirteci ve kültür.</span><span class="sxs-lookup"><span data-stu-id="4b9f6-126">The **fullName** attribute must include the four fields of assembly identity: name, version, public key token, and culture.</span></span> <span data-ttu-id="4b9f6-127">**PartialName** özniteliği kısmen bir derlemeye başvurmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4b9f6-127">The **partialName** attribute must partially reference an assembly.</span></span> <span data-ttu-id="4b9f6-128">En azından derlemenin metin adını (en yaygın durum) belirtmeniz gerekir, ancak sürüm, ortak anahtar belirteci veya kültürü (ya da dört ' un herhangi bir birleşimini değil) dahil edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4b9f6-128">You must specify at least the assembly's text name (the most common case), but you can also include version, public key token, or culture (or any combination of the four, but not all four).</span></span> <span data-ttu-id="4b9f6-129">**PartialName** , çağrın içinde belirtilen ad ile aynı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4b9f6-129">The **partialName** must match the name specified in your call.</span></span> <span data-ttu-id="4b9f6-130">Örneğin, `"math"` yapılandırma dosyanızda **partialName** özniteliği olarak belirtemezsiniz ve kodunuzda çağrı yapabilirsiniz `Assembly.Load("math, Version=3.3.3.3")` .</span><span class="sxs-lookup"><span data-stu-id="4b9f6-130">For example, you cannot specify `"math"` as the **partialName** attribute in your configuration file and call `Assembly.Load("math, Version=3.3.3.3")` in your code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4b9f6-131">Örnek</span><span class="sxs-lookup"><span data-stu-id="4b9f6-131">Example</span></span>  

 <span data-ttu-id="4b9f6-132">Aşağıdaki örnek, çağrısını mantıksal olarak etkinleştirir `Assembly.Load("math")` `Assembly.Load("math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral")` .</span><span class="sxs-lookup"><span data-stu-id="4b9f6-132">The following example logically turns the call `Assembly.Load("math")` into `Assembly.Load("math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral")`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4b9f6-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4b9f6-133">See also</span></span>

- [<span data-ttu-id="4b9f6-134">Çalışma zamanı ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="4b9f6-134">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="4b9f6-135">Çalışma Zamanının Derlemelerin Konumunu Bulması</span><span class="sxs-lookup"><span data-stu-id="4b9f6-135">How the Runtime Locates Assemblies</span></span>](../../../deployment/how-the-runtime-locates-assemblies.md)
- <span data-ttu-id="4b9f6-136">[Kısmi derleme başvuruları](/previous-versions/dotnet/netframework-4.0/0a7zy9z5(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="4b9f6-136">[Partial Assembly References](/previous-versions/dotnet/netframework-4.0/0a7zy9z5(v=vs.100))</span></span>
