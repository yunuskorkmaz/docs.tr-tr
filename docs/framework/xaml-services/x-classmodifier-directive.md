---
title: x:ClassModifier Yönergesi
ms.date: 03/30/2017
f1_keywords:
- xClassModifier
- x:ClassModifier
- ClassModifier
helpviewer_keywords:
- XAML [XAML Services], x:ClassModifier attribute
- x:ClassModifier attribute [XAML Services]
- ClassModifier attribute in XAML [XAML Services]
ms.assetid: ef30ab78-d334-4668-917d-c9f66c3b6aea
ms.openlocfilehash: 67b53a63dbd6e1377d5684d64ed32b0374c84b5a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33564384"
---
# <a name="xclassmodifier-directive"></a><span data-ttu-id="0b2d2-102">x:ClassModifier Yönergesi</span><span class="sxs-lookup"><span data-stu-id="0b2d2-102">x:ClassModifier Directive</span></span>
<span data-ttu-id="0b2d2-103">XAML derleme davranışını değiştiren zaman `x:Class` de sağlanır.</span><span class="sxs-lookup"><span data-stu-id="0b2d2-103">Modifies XAML compilation behavior when `x:Class` is also provided.</span></span> <span data-ttu-id="0b2d2-104">Özellikle, kısmi oluşturmak yerine `class` olan bir `Public` erişim düzeyine (varsayılan), sağlanan `x:Class` ile oluşturulan bir `NotPublic` erişim düzeyi.</span><span class="sxs-lookup"><span data-stu-id="0b2d2-104">Specifically, instead of creating a partial `class` that has a `Public` access level (the default), the provided `x:Class` is created with a `NotPublic` access level.</span></span> <span data-ttu-id="0b2d2-105">Bu davranış oluşturulmuş derlemeler sınıfında erişim düzeyini etkiler.</span><span class="sxs-lookup"><span data-stu-id="0b2d2-105">This behavior affects the access level for the class in the generated assemblies.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="0b2d2-106">XAML Öznitelik Kullanımı</span><span class="sxs-lookup"><span data-stu-id="0b2d2-106">XAML Attribute Usage</span></span>  
  
```  
<object x:Class="namespace.classname" x:ClassModifier="NotPublic">  
   ...  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="0b2d2-107">XAML Değerleri</span><span class="sxs-lookup"><span data-stu-id="0b2d2-107">XAML Values</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0b2d2-108">*NotPublic*</span><span class="sxs-lookup"><span data-stu-id="0b2d2-108">*NotPublic*</span></span>|<span data-ttu-id="0b2d2-109">Belirtmek için geçirmek için tam dizeyi <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> karşı <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> , kullandığınız arka plan kodu programlama dili bağlı olarak değişir.</span><span class="sxs-lookup"><span data-stu-id="0b2d2-109">The exact string to pass to specify <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> versus <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> varies, depending on the code-behind programming language that you use.</span></span> <span data-ttu-id="0b2d2-110">Açıklamalar bakın.</span><span class="sxs-lookup"><span data-stu-id="0b2d2-110">See Remarks.</span></span>|  
  
## <a name="dependencies"></a><span data-ttu-id="0b2d2-111">Bağımlılıklar</span><span class="sxs-lookup"><span data-stu-id="0b2d2-111">Dependencies</span></span>  
 <span data-ttu-id="0b2d2-112">[x: Class](../../../docs/framework/xaml-services/x-class-directive.md) de aynı öğede sağlanması gerekir ve bu öğe bir sayfa kök öğe olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0b2d2-112">[x:Class](../../../docs/framework/xaml-services/x-class-directive.md) must also be provided on the same element, and that element must be the root element in a page.</span></span> <span data-ttu-id="0b2d2-113">Daha fazla bilgi için bkz: [ \[MS XAML\] bölüm 4.3.1.8](http://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="0b2d2-113">For more information, see [\[MS-XAML\] Section 4.3.1.8](http://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0b2d2-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0b2d2-114">Remarks</span></span>  
 <span data-ttu-id="0b2d2-115">Değeri `x:ClassModifier` programlama dili tarafından kullanım .NET Framework XAML hizmetlerinde değişir.</span><span class="sxs-lookup"><span data-stu-id="0b2d2-115">The value of `x:ClassModifier` in .NET Framework XAML Services usage varies by programming language.</span></span> <span data-ttu-id="0b2d2-116">Her bir dilin nasıl uyguladığını kullanılacak dizesi bağlıdır, <xref:System.CodeDom.Compiler.CodeDomProvider> ve döndürür anlamı tanımlamak için tür dönüştürücüleri <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> ve <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>, ve bu dil büyük küçük harfe duyarlı olup olmadığını.</span><span class="sxs-lookup"><span data-stu-id="0b2d2-116">The string to use depends on how each language implements its <xref:System.CodeDom.Compiler.CodeDomProvider> and the type converters it returns to define the meanings for <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> and <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>, and whether that language is case sensitive.</span></span>  
  
-   <span data-ttu-id="0b2d2-117">C#, atamak iletilecek dizeyi <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> olan `internal`.</span><span class="sxs-lookup"><span data-stu-id="0b2d2-117">For C#, the string to pass to designate <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> is `internal`.</span></span>  
  
-   <span data-ttu-id="0b2d2-118">Microsoft Visual Basic .NET, atamak iletilecek dizeyi için <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> olan `Friend`.</span><span class="sxs-lookup"><span data-stu-id="0b2d2-118">For Microsoft Visual Basic .NET, the string to pass to designate <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> is `Friend`.</span></span>  
  
-   <span data-ttu-id="0b2d2-119">İçin [!INCLUDE[TLA2#tla_cppcli](../../../includes/tla2sharptla-cppcli-md.md)], XAML derleme destekleyen hiçbir hedef var; Bu nedenle, geçirmek için değer belirtilmemiş.</span><span class="sxs-lookup"><span data-stu-id="0b2d2-119">For [!INCLUDE[TLA2#tla_cppcli](../../../includes/tla2sharptla-cppcli-md.md)], no targets exist that support compiling XAML; therefore, the value to pass is unspecified.</span></span>  
  
 <span data-ttu-id="0b2d2-120">Ayrıca belirtebilirsiniz <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> (`public` C# ' ta, `Public` Visual Basic'te); ancak, belirtme <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> seyrek yapılır, çünkü <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> zaten varsayılan davranıştır.</span><span class="sxs-lookup"><span data-stu-id="0b2d2-120">You can also specify <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> (`public` in C#, `Public` in Visual Basic); however, specifying <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> is infrequently done because <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> is already the default behavior.</span></span>  
  
 <span data-ttu-id="0b2d2-121">Eşdeğer kullanıcı kodu diğer değerlerle erişim düzeyi kısıtlamaları gibi `private` C# ' ta ilgili olmayan `x:ClassModifier` iç içe geçmiş sınıf başvurularını XAML'de desteklenmediğinden ve bu nedenle, <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> değiştirici ile aynı etkiye sahiptir.</span><span class="sxs-lookup"><span data-stu-id="0b2d2-121">Other values with equivalent user code access-level restrictions, such as `private` in C#, are not relevant for `x:ClassModifier` because nested class references are not supported in XAML, and therefore, the <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> modifier has the same effect.</span></span>  
  
## <a name="security-notes"></a><span data-ttu-id="0b2d2-122">Güvenlik notları</span><span class="sxs-lookup"><span data-stu-id="0b2d2-122">Security Notes</span></span>  
 <span data-ttu-id="0b2d2-123">Bildirilen gibi erişim düzeyini `x:ClassModifier` belirli çerçeveler ve yeteneklerini tarafından tercüme hala tabidir.</span><span class="sxs-lookup"><span data-stu-id="0b2d2-123">The access level as declared in `x:ClassModifier` is still subject to interpretation by particular frameworks and their capabilities.</span></span> <span data-ttu-id="0b2d2-124">WPF yüklemek ve türleri örneği için özellikleri içerir nerede `x:ClassModifier` olan `internal`, o sınıfın bir paketi URI başvuru aracılığıyla bir WPF kaynaktan başvuruluyor.</span><span class="sxs-lookup"><span data-stu-id="0b2d2-124">WPF includes capabilities to load and instantiate types where `x:ClassModifier` is `internal`, if that class is referenced from a WPF resource through a pack URI reference.</span></span> <span data-ttu-id="0b2d2-125">Bu durumda ve diğerleri gibi bu diğer çerçeveler tarafından uygulanan gruplarındaki sonucu olarak, özel olarak üzerinde güvenmeyin `x:ClassModifier` olası tüm örneklemesi engelleyecek şekilde çalışır.</span><span class="sxs-lookup"><span data-stu-id="0b2d2-125">As a consequence of this case and potentially others like it implemented by other frameworks, do not rely exclusively on `x:ClassModifier` to block all possible instantiation attempts.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b2d2-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0b2d2-126">See Also</span></span>  
 [<span data-ttu-id="0b2d2-127">x:Class Yönergesi</span><span class="sxs-lookup"><span data-stu-id="0b2d2-127">x:Class Directive</span></span>](../../../docs/framework/xaml-services/x-class-directive.md)  
 [<span data-ttu-id="0b2d2-128">Arka Plan Kod ve WPF İçindeki XAML</span><span class="sxs-lookup"><span data-stu-id="0b2d2-128">Code-Behind and XAML in WPF</span></span>](../../../docs/framework/wpf/advanced/code-behind-and-xaml-in-wpf.md)  
 [<span data-ttu-id="0b2d2-129">x:FieldModifier Yönergesi</span><span class="sxs-lookup"><span data-stu-id="0b2d2-129">x:FieldModifier Directive</span></span>](../../../docs/framework/xaml-services/x-fieldmodifier-directive.md)  
 [<span data-ttu-id="0b2d2-130">Güvenlik (WPF)</span><span class="sxs-lookup"><span data-stu-id="0b2d2-130">Security (WPF)</span></span>](../../../docs/framework/wpf/security-wpf.md)  
 [<span data-ttu-id="0b2d2-131">WPF'den System.Xaml'e Geçirilen Türler</span><span class="sxs-lookup"><span data-stu-id="0b2d2-131">Types Migrated from WPF to System.Xaml</span></span>](../../../docs/framework/xaml-services/types-migrated-from-wpf-to-system-xaml.md)
