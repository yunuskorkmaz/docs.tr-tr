---
title: '&lt;supportPortability&gt; öğesi'
ms.date: 03/30/2017
helpviewer_keywords:
- supportPortability element
- <supportPortability> element
ms.assetid: 6453ef66-19b4-41f3-b712-52d0c2abc9ca
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0a8a454919a195a0f0c03ed6890e51b2723f64fb
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32754112"
---
# <a name="ltsupportportabilitygt-element"></a><span data-ttu-id="34c15-102">&lt;supportPortability&gt; öğesi</span><span class="sxs-lookup"><span data-stu-id="34c15-102">&lt;supportPortability&gt; Element</span></span>
<span data-ttu-id="34c15-103">Bir uygulama aynı bütünleştirilmiş kodda iki farklı uygulamaları .NET Framework'ün derlemeleri uygulama taşınabilirliği amacıyla eşdeğer olarak davranır varsayılan davranışı devre dışı bırakarak başvurabilir belirtir.</span><span class="sxs-lookup"><span data-stu-id="34c15-103">Specifies that an application can reference the same assembly in two different implementations of the .NET Framework, by disabling the default behavior that treats the assemblies as equivalent for application portability purposes.</span></span>  
  
 <span data-ttu-id="34c15-104">\<Yapılandırma > öğesi</span><span class="sxs-lookup"><span data-stu-id="34c15-104">\<configuration> Element</span></span>  
<span data-ttu-id="34c15-105">\<çalışma zamanı > öğesi</span><span class="sxs-lookup"><span data-stu-id="34c15-105">\<runtime> Element</span></span>  
<span data-ttu-id="34c15-106">\<assemblyBinding > öğesi</span><span class="sxs-lookup"><span data-stu-id="34c15-106">\<assemblyBinding> Element</span></span>  
<span data-ttu-id="34c15-107">\<supportPortability > öğesi</span><span class="sxs-lookup"><span data-stu-id="34c15-107">\<supportPortability> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34c15-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="34c15-108">Syntax</span></span>  
  
```xml  
<supportPortability PKT="public_key_token" enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="34c15-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="34c15-109">Attributes and Elements</span></span>  
 <span data-ttu-id="34c15-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="34c15-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="34c15-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="34c15-111">Attributes</span></span>  
  
|<span data-ttu-id="34c15-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="34c15-112">Attribute</span></span>|<span data-ttu-id="34c15-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="34c15-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="34c15-114">PKT</span><span class="sxs-lookup"><span data-stu-id="34c15-114">PKT</span></span>|<span data-ttu-id="34c15-115">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="34c15-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="34c15-116">Ortak anahtar belirteci etkilenen bütünleştirilmiş kodun bir dize olarak belirtir.</span><span class="sxs-lookup"><span data-stu-id="34c15-116">Specifies the public key token of the affected assembly, as a string.</span></span>|  
|<span data-ttu-id="34c15-117">Etkin</span><span class="sxs-lookup"><span data-stu-id="34c15-117">enabled</span></span>|<span data-ttu-id="34c15-118">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="34c15-118">Optional attribute.</span></span><br /><br /> <span data-ttu-id="34c15-119">Belirtilen .NET Framework derlemesinin uygulamaları arasındaki taşınabilirlik desteği etkin olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="34c15-119">Specifies whether support for portability between implementations of the specified .NET Framework assembly should be enabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="34c15-120">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="34c15-120">enabled Attribute</span></span>  
  
|<span data-ttu-id="34c15-121">Değer</span><span class="sxs-lookup"><span data-stu-id="34c15-121">Value</span></span>|<span data-ttu-id="34c15-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="34c15-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="34c15-123">true</span><span class="sxs-lookup"><span data-stu-id="34c15-123">true</span></span>|<span data-ttu-id="34c15-124">Belirtilen .NET Framework derlemesinin uygulamaları arasındaki taşınabilirlik desteğini etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="34c15-124">Enable support for portability between implementations of the specified .NET Framework assembly.</span></span> <span data-ttu-id="34c15-125">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="34c15-125">This is the default.</span></span>|  
|<span data-ttu-id="34c15-126">false</span><span class="sxs-lookup"><span data-stu-id="34c15-126">false</span></span>|<span data-ttu-id="34c15-127">Belirtilen .NET Framework derlemesinin uygulamaları arasındaki taşınabilirlik desteğini devre dışı bırakın.</span><span class="sxs-lookup"><span data-stu-id="34c15-127">Disable support for portability between implementations of the specified .NET Framework assembly.</span></span> <span data-ttu-id="34c15-128">Bu uygulamanın belirtilen bütünleştirilmiş kod, birden çok uygulamalarını başvuran sağlar.</span><span class="sxs-lookup"><span data-stu-id="34c15-128">This enables the application to have references to multiple implementations of the specified assembly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="34c15-129">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="34c15-129">Child Elements</span></span>  
 <span data-ttu-id="34c15-130">Yok.</span><span class="sxs-lookup"><span data-stu-id="34c15-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="34c15-131">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="34c15-131">Parent Elements</span></span>  
  
|<span data-ttu-id="34c15-132">Öğe</span><span class="sxs-lookup"><span data-stu-id="34c15-132">Element</span></span>|<span data-ttu-id="34c15-133">Açıklama</span><span class="sxs-lookup"><span data-stu-id="34c15-133">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="34c15-134">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="34c15-134">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="34c15-135">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="34c15-135">Contains information about assembly binding and garbage collection.</span></span>|  
|`assemblyBinding`|<span data-ttu-id="34c15-136">Derleme sürümü yeniden yönlendirmesi ve derlemelerin konumları hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="34c15-136">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="34c15-137">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="34c15-137">Remarks</span></span>  
 <span data-ttu-id="34c15-138">İle başlayarak [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], destek ya da .NET Framework'ün iki uygulamaları kullanan uygulamalar için otomatik olarak sağlanan örneğin .NET Framework uygulamasını ya da .NET Framework Silverlight uygulaması için.</span><span class="sxs-lookup"><span data-stu-id="34c15-138">Beginning with the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], support is automatically provided for applications that can use either of two implementations of the .NET Framework, for example either the .NET Framework implementation or the .NET Framework for Silverlight implementation.</span></span> <span data-ttu-id="34c15-139">Belirli bir .NET Framework derlemesinin iki uygulamaları eşdeğer olarak derleme bağlayıcı tarafından görülür.</span><span class="sxs-lookup"><span data-stu-id="34c15-139">The two implementations of a particular .NET Framework assembly are seen as equivalent by the assembly binder.</span></span> <span data-ttu-id="34c15-140">Bazı senaryolarda, bu uygulama taşınabilirliği özelliği sorunlara neden olur.</span><span class="sxs-lookup"><span data-stu-id="34c15-140">In a few scenarios, this application portability feature causes problems.</span></span> <span data-ttu-id="34c15-141">Bu senaryolarda `<supportPortability>` öğesi, özelliği devre dışı bırakmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="34c15-141">In those scenarios, the `<supportPortability>` element can be used to disable the feature.</span></span>  
  
 <span data-ttu-id="34c15-142">Böyle bir senaryo hem .NET Framework uygulamasını hem de belirli referans derlemesini Silverlight uygulama için .NET Framework başvurusu olan bir derlemedir.</span><span class="sxs-lookup"><span data-stu-id="34c15-142">One such scenario is an assembly that has to reference both the .NET Framework implementation and the .NET Framework for Silverlight implementation of a particular reference assembly.</span></span> <span data-ttu-id="34c15-143">Örneğin, Windows Presentation Foundation (WPF) yazılmış bir XAML Tasarımcısı hem WPF Masaüstü uygulamasını, tasarımcının kullanıcı arabirimi ve Silverlight uygulamaları, eklenen WPF alt başvuru gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="34c15-143">For example, a XAML designer written in Windows Presentation Foundation (WPF) might need to reference both the WPF Desktop implementation, for the designer's user interface, and the subset of WPF that is included in the Silverlight implementation.</span></span> <span data-ttu-id="34c15-144">Derleme bağlama eşdeğer olarak iki derleme gördüğünden varsayılan olarak, bir derleyici hatası ayrı başvuruları neden.</span><span class="sxs-lookup"><span data-stu-id="34c15-144">By default, the separate references cause a compiler error, because assembly binding sees the two assemblies as equivalent.</span></span> <span data-ttu-id="34c15-145">Bu öğe varsayılan davranışı devre dışı bırakır ve başarılı olması derleme sağlar.</span><span class="sxs-lookup"><span data-stu-id="34c15-145">This element disables the default behavior, and allows compilation to succeed.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="34c15-146">Ortak dil çalışma zamanı 's derleme bağlama mantığı bilgi geçirmek derleyici için sırayla kullanmalısınız `/appconfig` derleyici seçeneği bu öğeyi içeren app.config dosyasının konumunu belirtin.</span><span class="sxs-lookup"><span data-stu-id="34c15-146">In order for the compiler to pass the information to the common language runtime's assembly-binding logic, you must use the `/appconfig` compiler option to specify the location of the app.config file that contains this element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="34c15-147">Örnek</span><span class="sxs-lookup"><span data-stu-id="34c15-147">Example</span></span>  
 <span data-ttu-id="34c15-148">Aşağıdaki örnek bir uygulama hem .NET Framework uygulamasını hem de her iki uygulamada da bulunan herhangi bir .NET Framework derlemesinin Silverlight uygulama için .NET Framework başvuran etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="34c15-148">The following example enables an application to have references to both the .NET Framework implementation and the .NET Framework for Silverlight implementation of any .NET Framework assembly that exists in both implementations.</span></span> <span data-ttu-id="34c15-149">`/appconfig` Derleyici seçeneği, bu app.config dosyasının konumunu belirtmek için kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="34c15-149">The `/appconfig` compiler option must be used to specify the location of this app.config file.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="34c15-150">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="34c15-150">See Also</span></span>  
 [<span data-ttu-id="34c15-151">/ appConfig (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="34c15-151">/appconfig (C# Compiler Options)</span></span>](http://msdn.microsoft.com/library/ee523958.aspx)  
 [<span data-ttu-id="34c15-152">.NET framework derleme Birleştirici genel bakış</span><span class="sxs-lookup"><span data-stu-id="34c15-152">.NET Framework Assembly Unification Overview</span></span>](http://msdn.microsoft.com/library/8d8cc65e-031d-463b-bde3-2c6dc2e3bc48)
