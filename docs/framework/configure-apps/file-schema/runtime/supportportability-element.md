---
title: "&lt;supportPortability&gt; öğesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- supportPortability element
- <supportPortability> element
ms.assetid: 6453ef66-19b4-41f3-b712-52d0c2abc9ca
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9776e900015dad8bce8c16991b8ce0aeb6067812
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltsupportportabilitygt-element"></a><span data-ttu-id="3c7bc-102">&lt;supportPortability&gt; öğesi</span><span class="sxs-lookup"><span data-stu-id="3c7bc-102">&lt;supportPortability&gt; Element</span></span>
<span data-ttu-id="3c7bc-103">Bir uygulama aynı bütünleştirilmiş kodda iki farklı uygulamaları .NET Framework'ün derlemeleri uygulama taşınabilirliği amacıyla eşdeğer olarak davranır varsayılan davranışı devre dışı bırakarak başvurabilir belirtir.</span><span class="sxs-lookup"><span data-stu-id="3c7bc-103">Specifies that an application can reference the same assembly in two different implementations of the .NET Framework, by disabling the default behavior that treats the assemblies as equivalent for application portability purposes.</span></span>  
  
 <span data-ttu-id="3c7bc-104">\<Yapılandırma > öğesi</span><span class="sxs-lookup"><span data-stu-id="3c7bc-104">\<configuration> Element</span></span>  
<span data-ttu-id="3c7bc-105">\<çalışma zamanı > öğesi</span><span class="sxs-lookup"><span data-stu-id="3c7bc-105">\<runtime> Element</span></span>  
<span data-ttu-id="3c7bc-106">\<assemblyBinding > öğesi</span><span class="sxs-lookup"><span data-stu-id="3c7bc-106">\<assemblyBinding> Element</span></span>  
<span data-ttu-id="3c7bc-107">\<supportPortability > öğesi</span><span class="sxs-lookup"><span data-stu-id="3c7bc-107">\<supportPortability> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c7bc-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3c7bc-108">Syntax</span></span>  
  
```xml  
<supportPortability PKT="public_key_token" enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3c7bc-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="3c7bc-109">Attributes and Elements</span></span>  
 <span data-ttu-id="3c7bc-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3c7bc-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3c7bc-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="3c7bc-111">Attributes</span></span>  
  
|<span data-ttu-id="3c7bc-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="3c7bc-112">Attribute</span></span>|<span data-ttu-id="3c7bc-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3c7bc-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3c7bc-114">PKT</span><span class="sxs-lookup"><span data-stu-id="3c7bc-114">PKT</span></span>|<span data-ttu-id="3c7bc-115">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="3c7bc-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="3c7bc-116">Ortak anahtar belirteci etkilenen bütünleştirilmiş kodun bir dize olarak belirtir.</span><span class="sxs-lookup"><span data-stu-id="3c7bc-116">Specifies the public key token of the affected assembly, as a string.</span></span>|  
|<span data-ttu-id="3c7bc-117">Etkin</span><span class="sxs-lookup"><span data-stu-id="3c7bc-117">enabled</span></span>|<span data-ttu-id="3c7bc-118">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="3c7bc-118">Optional attribute.</span></span><br /><br /> <span data-ttu-id="3c7bc-119">Belirtilen .NET Framework derlemesinin uygulamaları arasındaki taşınabilirlik desteği etkin olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="3c7bc-119">Specifies whether support for portability between implementations of the specified .NET Framework assembly should be enabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="3c7bc-120">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="3c7bc-120">enabled Attribute</span></span>  
  
|<span data-ttu-id="3c7bc-121">Değer</span><span class="sxs-lookup"><span data-stu-id="3c7bc-121">Value</span></span>|<span data-ttu-id="3c7bc-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3c7bc-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3c7bc-123">true</span><span class="sxs-lookup"><span data-stu-id="3c7bc-123">true</span></span>|<span data-ttu-id="3c7bc-124">Belirtilen .NET Framework derlemesinin uygulamaları arasındaki taşınabilirlik desteğini etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="3c7bc-124">Enable support for portability between implementations of the specified .NET Framework assembly.</span></span> <span data-ttu-id="3c7bc-125">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="3c7bc-125">This is the default.</span></span>|  
|<span data-ttu-id="3c7bc-126">false</span><span class="sxs-lookup"><span data-stu-id="3c7bc-126">false</span></span>|<span data-ttu-id="3c7bc-127">Belirtilen .NET Framework derlemesinin uygulamaları arasındaki taşınabilirlik desteğini devre dışı bırakın.</span><span class="sxs-lookup"><span data-stu-id="3c7bc-127">Disable support for portability between implementations of the specified .NET Framework assembly.</span></span> <span data-ttu-id="3c7bc-128">Bu uygulamanın belirtilen bütünleştirilmiş kod, birden çok uygulamalarını başvuran sağlar.</span><span class="sxs-lookup"><span data-stu-id="3c7bc-128">This enables the application to have references to multiple implementations of the specified assembly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3c7bc-129">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="3c7bc-129">Child Elements</span></span>  
 <span data-ttu-id="3c7bc-130">Yok.</span><span class="sxs-lookup"><span data-stu-id="3c7bc-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3c7bc-131">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="3c7bc-131">Parent Elements</span></span>  
  
|<span data-ttu-id="3c7bc-132">Öğe</span><span class="sxs-lookup"><span data-stu-id="3c7bc-132">Element</span></span>|<span data-ttu-id="3c7bc-133">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3c7bc-133">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="3c7bc-134">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="3c7bc-134">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="3c7bc-135">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="3c7bc-135">Contains information about assembly binding and garbage collection.</span></span>|  
|`assemblyBinding`|<span data-ttu-id="3c7bc-136">Derleme sürümü yeniden yönlendirmesi ve derlemelerin konumları hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="3c7bc-136">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3c7bc-137">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3c7bc-137">Remarks</span></span>  
 <span data-ttu-id="3c7bc-138">İle başlayarak [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], destek ya da .NET Framework'ün iki uygulamaları kullanan uygulamalar için otomatik olarak sağlanan örneğin .NET Framework uygulamasını ya da .NET Framework Silverlight uygulaması için.</span><span class="sxs-lookup"><span data-stu-id="3c7bc-138">Beginning with the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], support is automatically provided for applications that can use either of two implementations of the .NET Framework, for example either the .NET Framework implementation or the .NET Framework for Silverlight implementation.</span></span> <span data-ttu-id="3c7bc-139">Belirli bir .NET Framework derlemesinin iki uygulamaları eşdeğer olarak derleme bağlayıcı tarafından görülür.</span><span class="sxs-lookup"><span data-stu-id="3c7bc-139">The two implementations of a particular .NET Framework assembly are seen as equivalent by the assembly binder.</span></span> <span data-ttu-id="3c7bc-140">Bazı senaryolarda, bu uygulama taşınabilirliği özelliği sorunlara neden olur.</span><span class="sxs-lookup"><span data-stu-id="3c7bc-140">In a few scenarios, this application portability feature causes problems.</span></span> <span data-ttu-id="3c7bc-141">Bu senaryolarda `<supportPortability>` öğesi, özelliği devre dışı bırakmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3c7bc-141">In those scenarios, the `<supportPortability>` element can be used to disable the feature.</span></span>  
  
 <span data-ttu-id="3c7bc-142">Böyle bir senaryo hem .NET Framework uygulamasını hem de belirli referans derlemesini Silverlight uygulama için .NET Framework başvurusu olan bir derlemedir.</span><span class="sxs-lookup"><span data-stu-id="3c7bc-142">One such scenario is an assembly that has to reference both the .NET Framework implementation and the .NET Framework for Silverlight implementation of a particular reference assembly.</span></span> <span data-ttu-id="3c7bc-143">Örneğin, Windows Presentation Foundation (WPF) yazılmış bir XAML Tasarımcısı hem WPF Masaüstü uygulamasını, tasarımcının kullanıcı arabirimi ve Silverlight uygulamaları, eklenen WPF alt başvuru gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="3c7bc-143">For example, a XAML designer written in Windows Presentation Foundation (WPF) might need to reference both the WPF Desktop implementation, for the designer's user interface, and the subset of WPF that is included in the Silverlight implementation.</span></span> <span data-ttu-id="3c7bc-144">Derleme bağlama eşdeğer olarak iki derleme gördüğünden varsayılan olarak, bir derleyici hatası ayrı başvuruları neden.</span><span class="sxs-lookup"><span data-stu-id="3c7bc-144">By default, the separate references cause a compiler error, because assembly binding sees the two assemblies as equivalent.</span></span> <span data-ttu-id="3c7bc-145">Bu öğe varsayılan davranışı devre dışı bırakır ve başarılı olması derleme sağlar.</span><span class="sxs-lookup"><span data-stu-id="3c7bc-145">This element disables the default behavior, and allows compilation to succeed.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="3c7bc-146">Ortak dil çalışma zamanı 's derleme bağlama mantığı bilgi geçirmek derleyici için sırayla kullanmalısınız `/appconfig` derleyici seçeneği bu öğeyi içeren app.config dosyasının konumunu belirtin.</span><span class="sxs-lookup"><span data-stu-id="3c7bc-146">In order for the compiler to pass the information to the common language runtime's assembly-binding logic, you must use the `/appconfig` compiler option to specify the location of the app.config file that contains this element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3c7bc-147">Örnek</span><span class="sxs-lookup"><span data-stu-id="3c7bc-147">Example</span></span>  
 <span data-ttu-id="3c7bc-148">Aşağıdaki örnek bir uygulama hem .NET Framework uygulamasını hem de her iki uygulamada da bulunan herhangi bir .NET Framework derlemesinin Silverlight uygulama için .NET Framework başvuran etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="3c7bc-148">The following example enables an application to have references to both the .NET Framework implementation and the .NET Framework for Silverlight implementation of any .NET Framework assembly that exists in both implementations.</span></span> <span data-ttu-id="3c7bc-149">`/appconfig` Derleyici seçeneği, bu app.config dosyasının konumunu belirtmek için kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3c7bc-149">The `/appconfig` compiler option must be used to specify the location of this app.config file.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding>  
         <supportPortability PKT="7cec85d7bea7798e" enable="false"/>  
         <supportPortability PKT="31bf3856ad364e35" enable="false"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3c7bc-150">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3c7bc-150">See Also</span></span>  
 [<span data-ttu-id="3c7bc-151">/ appConfig (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="3c7bc-151">/appconfig (C# Compiler Options)</span></span>](http://msdn.microsoft.com/library/ee523958.aspx)  
 [<span data-ttu-id="3c7bc-152">.NET framework derleme Birleştirici genel bakış</span><span class="sxs-lookup"><span data-stu-id="3c7bc-152">.NET Framework Assembly Unification Overview</span></span>](http://msdn.microsoft.com/en-us/8d8cc65e-031d-463b-bde3-2c6dc2e3bc48)
