---
title: <supportPortability> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- supportPortability element
- <supportPortability> element
ms.assetid: 6453ef66-19b4-41f3-b712-52d0c2abc9ca
ms.openlocfilehash: 99fa51238040f21d998a8c6c2aef7c13d288104a
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90551591"
---
# <a name="supportportability-element"></a><span data-ttu-id="5ccab-102">\<supportPortability> Öğesi</span><span class="sxs-lookup"><span data-stu-id="5ccab-102">\<supportPortability> Element</span></span>
<span data-ttu-id="5ccab-103">Bir uygulamanın, uygulama taşınabilirlik amaçları doğrultusunda derlemeleri eşdeğer olarak ele alan varsayılan davranışı devre dışı bırakarak, .NET Framework iki farklı uygulamasındaki aynı derlemeye başvurabildiklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="5ccab-103">Specifies that an application can reference the same assembly in two different implementations of the .NET Framework, by disabling the default behavior that treats the assemblies as equivalent for application portability purposes.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<supportPortability>**  
  
## <a name="syntax"></a><span data-ttu-id="5ccab-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="5ccab-104">Syntax</span></span>  
  
```xml  
<supportPortability PKT="public_key_token" enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5ccab-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="5ccab-105">Attributes and Elements</span></span>  

<span data-ttu-id="5ccab-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5ccab-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5ccab-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5ccab-107">Attributes</span></span>  
  
|<span data-ttu-id="5ccab-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="5ccab-108">Attribute</span></span>|<span data-ttu-id="5ccab-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5ccab-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5ccab-110">PKT</span><span class="sxs-lookup"><span data-stu-id="5ccab-110">PKT</span></span>|<span data-ttu-id="5ccab-111">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="5ccab-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="5ccab-112">Etkilenen derlemenin ortak anahtar belirtecini bir dize olarak belirtir.</span><span class="sxs-lookup"><span data-stu-id="5ccab-112">Specifies the public key token of the affected assembly, as a string.</span></span>|  
|<span data-ttu-id="5ccab-113">enabled</span><span class="sxs-lookup"><span data-stu-id="5ccab-113">enabled</span></span>|<span data-ttu-id="5ccab-114">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="5ccab-114">Optional attribute.</span></span><br /><br /> <span data-ttu-id="5ccab-115">Belirtilen .NET Framework derlemesinin uygulamaları arasında taşınabilirlik desteğinin etkin olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="5ccab-115">Specifies whether support for portability between implementations of the specified .NET Framework assembly should be enabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="5ccab-116">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="5ccab-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="5ccab-117">Değer</span><span class="sxs-lookup"><span data-stu-id="5ccab-117">Value</span></span>|<span data-ttu-id="5ccab-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5ccab-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="5ccab-119">true</span><span class="sxs-lookup"><span data-stu-id="5ccab-119">true</span></span>|<span data-ttu-id="5ccab-120">Belirtilen .NET Framework derlemesinin uygulamaları arasında taşınabilirlik desteğini etkinleştir.</span><span class="sxs-lookup"><span data-stu-id="5ccab-120">Enable support for portability between implementations of the specified .NET Framework assembly.</span></span> <span data-ttu-id="5ccab-121">Bu varsayılan seçenektir.</span><span class="sxs-lookup"><span data-stu-id="5ccab-121">This is the default.</span></span>|  
|<span data-ttu-id="5ccab-122">yanlış</span><span class="sxs-lookup"><span data-stu-id="5ccab-122">false</span></span>|<span data-ttu-id="5ccab-123">Belirtilen .NET Framework derlemesinin uygulamaları arasında taşınabilirlik desteğini devre dışı bırakın.</span><span class="sxs-lookup"><span data-stu-id="5ccab-123">Disable support for portability between implementations of the specified .NET Framework assembly.</span></span> <span data-ttu-id="5ccab-124">Bu, uygulamanın belirtilen derlemenin birden çok uygulamasına başvurmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="5ccab-124">This enables the application to have references to multiple implementations of the specified assembly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5ccab-125">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="5ccab-125">Child Elements</span></span>  

<span data-ttu-id="5ccab-126">Yok.</span><span class="sxs-lookup"><span data-stu-id="5ccab-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5ccab-127">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="5ccab-127">Parent Elements</span></span>  
  
|<span data-ttu-id="5ccab-128">Öğe</span><span class="sxs-lookup"><span data-stu-id="5ccab-128">Element</span></span>|<span data-ttu-id="5ccab-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5ccab-129">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="5ccab-130">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="5ccab-130">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="5ccab-131">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="5ccab-131">Contains information about assembly binding and garbage collection.</span></span>|  
|`assemblyBinding`|<span data-ttu-id="5ccab-132">Derleme sürümü yeniden yönlendirmesi ve derlemelerin konumları hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="5ccab-132">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5ccab-133">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5ccab-133">Remarks</span></span>  

<span data-ttu-id="5ccab-134">.NET Framework 4 ' ten başlayarak, .NET Framework iki uygulamalarından birini (örneğin .NET Framework uygulaması veya Silverlight uygulaması için .NET Framework) kullanan uygulamalar için destek otomatik olarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="5ccab-134">Beginning with the .NET Framework 4, support is automatically provided for applications that can use either of two implementations of the .NET Framework, for example either the .NET Framework implementation or the .NET Framework for Silverlight implementation.</span></span> <span data-ttu-id="5ccab-135">Belirli bir .NET Framework derlemesinin iki uygulaması, derleme Bağlayıcısı tarafından eşdeğer olarak görülür.</span><span class="sxs-lookup"><span data-stu-id="5ccab-135">The two implementations of a particular .NET Framework assembly are seen as equivalent by the assembly binder.</span></span> <span data-ttu-id="5ccab-136">Birkaç senaryoda, bu uygulama taşınabilirlik özelliği sorun oluşmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="5ccab-136">In a few scenarios, this application portability feature causes problems.</span></span> <span data-ttu-id="5ccab-137">Bu senaryolarda, `<supportPortability>` özelliği devre dışı bırakmak için öğesi kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5ccab-137">In those scenarios, the `<supportPortability>` element can be used to disable the feature.</span></span>  
  
<span data-ttu-id="5ccab-138">Bu tür bir senaryo, hem .NET Framework uygulamasına hem de belirli bir başvuru derlemesinin Silverlight uygulamasına .NET Framework başvuran bir derlemedir.</span><span class="sxs-lookup"><span data-stu-id="5ccab-138">One such scenario is an assembly that has to reference both the .NET Framework implementation and the .NET Framework for Silverlight implementation of a particular reference assembly.</span></span> <span data-ttu-id="5ccab-139">Örneğin, Windows Presentation Foundation (WPF) yazılmış bir XAML tasarımcısının, tasarımcı 'nın Kullanıcı arabirimi için hem WPF Masaüstü uygulamasına hem de Silverlight uygulamasında bulunan WPF 'nin alt kümesine başvurması gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="5ccab-139">For example, a XAML designer written in Windows Presentation Foundation (WPF) might need to reference both the WPF Desktop implementation, for the designer's user interface, and the subset of WPF that is included in the Silverlight implementation.</span></span> <span data-ttu-id="5ccab-140">Varsayılan olarak, derleme bağlaması iki derlemeyi eşdeğer olarak gördüğü için ayrı başvurular bir derleyici hatasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="5ccab-140">By default, the separate references cause a compiler error, because assembly binding sees the two assemblies as equivalent.</span></span> <span data-ttu-id="5ccab-141">Bu öğe varsayılan davranışı devre dışı bırakır ve derlemenin başarılı olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="5ccab-141">This element disables the default behavior, and allows compilation to succeed.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="5ccab-142">Derleyicinin bilgileri ortak dil çalışma zamanının derleme bağlama mantığına geçirmesi için, `/appconfig` Bu öğeyi içeren app.config dosyasının konumunu belirtmek için derleyici seçeneğini kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="5ccab-142">In order for the compiler to pass the information to the common language runtime's assembly-binding logic, you must use the `/appconfig` compiler option to specify the location of the app.config file that contains this element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5ccab-143">Örnek</span><span class="sxs-lookup"><span data-stu-id="5ccab-143">Example</span></span>  

<span data-ttu-id="5ccab-144">Aşağıdaki örnek, bir uygulamanın hem .NET Framework uygulamasına hem de her iki uygulamada bulunan herhangi bir .NET Framework derlemesinin Silverlight uygulamasına .NET Framework başvurularına sahip olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="5ccab-144">The following example enables an application to have references to both the .NET Framework implementation and the .NET Framework for Silverlight implementation of any .NET Framework assembly that exists in both implementations.</span></span> <span data-ttu-id="5ccab-145">`/appconfig`Derleyici seçeneğinin bu app.config dosyasının konumunu belirtmek için kullanılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="5ccab-145">The `/appconfig` compiler option must be used to specify the location of this app.config file.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5ccab-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5ccab-146">See also</span></span>

- [<span data-ttu-id="5ccab-147">-appconfig (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="5ccab-147">-appconfig (C# Compiler Options)</span></span>](../../../../csharp/language-reference/compiler-options/appconfig-compiler-option.md)
- <span data-ttu-id="5ccab-148">[.NET Framework derleme birleşme genel bakış](/previous-versions/dotnet/netframework-4.0/db7849ey(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="5ccab-148">[.NET Framework Assembly Unification Overview](/previous-versions/dotnet/netframework-4.0/db7849ey(v=vs.100))</span></span>
