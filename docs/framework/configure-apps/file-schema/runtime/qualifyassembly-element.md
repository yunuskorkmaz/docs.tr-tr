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
ms.openlocfilehash: 26b265996a059d8e52901557603bcf5e7636e596
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91195226"
---
# <a name="qualifyassembly-element"></a><span data-ttu-id="3f852-102">\<qualifyAssembly> Öğesi</span><span class="sxs-lookup"><span data-stu-id="3f852-102">\<qualifyAssembly> Element</span></span>

<span data-ttu-id="3f852-103">Kısmi bir ad kullanıldığında dinamik olarak yüklenmesi gereken derlemenin tam adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="3f852-103">Specifies the full name of the assembly that should be dynamically loaded when a partial name is used.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<qualifyAssembly>**  
  
## <a name="syntax"></a><span data-ttu-id="3f852-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="3f852-104">Syntax</span></span>  
  
```xml  
      <qualifyAssembly partialName=  
      "PartialAssemblyName"  
                 fullName="FullAssemblyName"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3f852-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="3f852-105">Attributes and Elements</span></span>  

 <span data-ttu-id="3f852-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3f852-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3f852-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="3f852-107">Attributes</span></span>  
  
|<span data-ttu-id="3f852-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="3f852-108">Attribute</span></span>|<span data-ttu-id="3f852-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3f852-109">Description</span></span>|  
|---------------|-----------------|  
|`partialName`|<span data-ttu-id="3f852-110">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="3f852-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="3f852-111">Kodda göründüğü gibi derlemenin kısmi adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="3f852-111">Specifies the partial name of the assembly as it appears in the code.</span></span>|  
|`fullName`|<span data-ttu-id="3f852-112">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="3f852-112">Required attribute.</span></span><br /><br /> <span data-ttu-id="3f852-113">Derlemenin genel derleme önbelleğinde göründüğü haliyle tam adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="3f852-113">Specifies the full name of the assembly as it appears in the global assembly cache.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3f852-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="3f852-114">Child Elements</span></span>  

 <span data-ttu-id="3f852-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="3f852-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3f852-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="3f852-116">Parent Elements</span></span>  
  
|<span data-ttu-id="3f852-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="3f852-117">Element</span></span>|<span data-ttu-id="3f852-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3f852-118">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="3f852-119">Derleme sürümü yeniden yönlendirmesi ve derlemelerin konumları hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="3f852-119">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="3f852-120">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="3f852-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="3f852-121">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="3f852-121">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3f852-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3f852-122">Remarks</span></span>  

 <span data-ttu-id="3f852-123"><xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>Kısmi derleme adlarını kullanarak yöntemi çağırmak, ortak dil çalışma zamanının derlemeyi yalnızca uygulama temel dizininde aramasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="3f852-123">Calling the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method using partial assembly names causes the common language runtime to look for the assembly only in the application base directory.</span></span> <span data-ttu-id="3f852-124">**\<qualifyAssembly>** Tüm derleme bilgilerini (ad, sürüm, ortak anahtar belirteci ve kültür) sağlamak ve ortak dil çalışma zamanının genel derleme önbelleğinde derlemeyi aramasını sağlamak için uygulama yapılandırma dosyanızda öğesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="3f852-124">Use the **\<qualifyAssembly>** element in your application configuration file to provide the full assembly information (name, version, public key token, and culture) and cause the common language runtime to search for the assembly in the global assembly cache.</span></span>  
  
 <span data-ttu-id="3f852-125">**FullName** özniteliği, derleme kimliğinin dört alanını içermelidir: ad, sürüm, ortak anahtar belirteci ve kültür.</span><span class="sxs-lookup"><span data-stu-id="3f852-125">The **fullName** attribute must include the four fields of assembly identity: name, version, public key token, and culture.</span></span> <span data-ttu-id="3f852-126">**PartialName** özniteliği kısmen bir derlemeye başvurmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3f852-126">The **partialName** attribute must partially reference an assembly.</span></span> <span data-ttu-id="3f852-127">En azından derlemenin metin adını (en yaygın durum) belirtmeniz gerekir, ancak sürüm, ortak anahtar belirteci veya kültürü (ya da dört ' un herhangi bir birleşimini değil) dahil edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3f852-127">You must specify at least the assembly's text name (the most common case), but you can also include version, public key token, or culture (or any combination of the four, but not all four).</span></span> <span data-ttu-id="3f852-128">**PartialName** , çağrın içinde belirtilen ad ile aynı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3f852-128">The **partialName** must match the name specified in your call.</span></span> <span data-ttu-id="3f852-129">Örneğin, `"math"` yapılandırma dosyanızda **partialName** özniteliği olarak belirtemezsiniz ve kodunuzda çağrı yapabilirsiniz `Assembly.Load("math, Version=3.3.3.3")` .</span><span class="sxs-lookup"><span data-stu-id="3f852-129">For example, you cannot specify `"math"` as the **partialName** attribute in your configuration file and call `Assembly.Load("math, Version=3.3.3.3")` in your code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3f852-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="3f852-130">Example</span></span>  

 <span data-ttu-id="3f852-131">Aşağıdaki örnek, çağrısını mantıksal olarak etkinleştirir `Assembly.Load("math")` `Assembly.Load("math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral")` .</span><span class="sxs-lookup"><span data-stu-id="3f852-131">The following example logically turns the call `Assembly.Load("math")` into `Assembly.Load("math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral")`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3f852-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3f852-132">See also</span></span>

- [<span data-ttu-id="3f852-133">Çalışma zamanı ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="3f852-133">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="3f852-134">Çalışma Zamanının Derlemelerin Konumunu Bulması</span><span class="sxs-lookup"><span data-stu-id="3f852-134">How the Runtime Locates Assemblies</span></span>](../../../deployment/how-the-runtime-locates-assemblies.md)
- <span data-ttu-id="3f852-135">[Kısmi derleme başvuruları](/previous-versions/dotnet/netframework-4.0/0a7zy9z5(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="3f852-135">[Partial Assembly References](/previous-versions/dotnet/netframework-4.0/0a7zy9z5(v=vs.100))</span></span>
