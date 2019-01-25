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
ms.openlocfilehash: ef55549b43ecbef539d7e84a7281fa704a328938
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54507596"
---
# <a name="xclassmodifier-directive"></a><span data-ttu-id="92271-102">x:ClassModifier Yönergesi</span><span class="sxs-lookup"><span data-stu-id="92271-102">x:ClassModifier Directive</span></span>
<span data-ttu-id="92271-103">XAML derlemesi davranışı değiştirir, `x:Class` de sağlanır.</span><span class="sxs-lookup"><span data-stu-id="92271-103">Modifies XAML compilation behavior when `x:Class` is also provided.</span></span> <span data-ttu-id="92271-104">Kısmi oluşturmak yerine özellikle `class` olan bir `Public` erişim düzeyi (varsayılan), sağlanan `x:Class` ile oluşturulan bir `NotPublic` erişim düzeyi.</span><span class="sxs-lookup"><span data-stu-id="92271-104">Specifically, instead of creating a partial `class` that has a `Public` access level (the default), the provided `x:Class` is created with a `NotPublic` access level.</span></span> <span data-ttu-id="92271-105">Bu davranış, sınıf oluşturulmuş derlemeler için erişim düzeyi etkiler.</span><span class="sxs-lookup"><span data-stu-id="92271-105">This behavior affects the access level for the class in the generated assemblies.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="92271-106">XAML Öznitelik Kullanımı</span><span class="sxs-lookup"><span data-stu-id="92271-106">XAML Attribute Usage</span></span>  
  
```  
<object x:Class="namespace.classname" x:ClassModifier="NotPublic">  
   ...  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="92271-107">XAML Değerleri</span><span class="sxs-lookup"><span data-stu-id="92271-107">XAML Values</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="92271-108">*NotPublic*</span><span class="sxs-lookup"><span data-stu-id="92271-108">*NotPublic*</span></span>|<span data-ttu-id="92271-109">Tam dizeyi belirtmek için geçirilecek <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> karşı <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> , kullandığınız arka plan kod programlama diline bağlı olarak değişir.</span><span class="sxs-lookup"><span data-stu-id="92271-109">The exact string to pass to specify <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> versus <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> varies, depending on the code-behind programming language that you use.</span></span> <span data-ttu-id="92271-110">Açıklamalara bakın.</span><span class="sxs-lookup"><span data-stu-id="92271-110">See Remarks.</span></span>|  
  
## <a name="dependencies"></a><span data-ttu-id="92271-111">Bağımlılıkları</span><span class="sxs-lookup"><span data-stu-id="92271-111">Dependencies</span></span>  
 <span data-ttu-id="92271-112">[x: Class](../../../docs/framework/xaml-services/x-class-directive.md) de aynı öğede sağlanması gerekir ve bu öğe bir sayfa kök öğesi olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="92271-112">[x:Class](../../../docs/framework/xaml-services/x-class-directive.md) must also be provided on the same element, and that element must be the root element in a page.</span></span> <span data-ttu-id="92271-113">Daha fazla bilgi için [ \[MS-XAML\] bölümü 4.3.1.8](https://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="92271-113">For more information, see [\[MS-XAML\] Section 4.3.1.8](https://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="92271-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="92271-114">Remarks</span></span>  
 <span data-ttu-id="92271-115">Değerini `x:ClassModifier` programlama dili tarafından kullanım .NET Framework XAML hizmetlerinde değişir.</span><span class="sxs-lookup"><span data-stu-id="92271-115">The value of `x:ClassModifier` in .NET Framework XAML Services usage varies by programming language.</span></span> <span data-ttu-id="92271-116">Her bir dilin nasıl uyguladığını kullanılacak dize bağlıdır, <xref:System.CodeDom.Compiler.CodeDomProvider> ve döndürür anlamı tanımlamak için tür dönüştürücüleri <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> ve <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>, ve bu dilin büyük küçük harfe duyarlı olup olmadığını.</span><span class="sxs-lookup"><span data-stu-id="92271-116">The string to use depends on how each language implements its <xref:System.CodeDom.Compiler.CodeDomProvider> and the type converters it returns to define the meanings for <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> and <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>, and whether that language is case sensitive.</span></span>  
  
-   <span data-ttu-id="92271-117">C#, belirlemek üzere iletilecek dizeyi <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> olduğu `internal`.</span><span class="sxs-lookup"><span data-stu-id="92271-117">For C#, the string to pass to designate <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> is `internal`.</span></span>  
  
-   <span data-ttu-id="92271-118">Microsoft Visual Basic .NET, atamak için geçirilecek dize için <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> olduğu `Friend`.</span><span class="sxs-lookup"><span data-stu-id="92271-118">For Microsoft Visual Basic .NET, the string to pass to designate <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> is `Friend`.</span></span>  
  
-   <span data-ttu-id="92271-119">İçin [!INCLUDE[TLA2#tla_cppcli](../../../includes/tla2sharptla-cppcli-md.md)], XAML derleme destekleyen hiçbir hedef var; Bu nedenle geçirilecek değer belirtilmemiş.</span><span class="sxs-lookup"><span data-stu-id="92271-119">For [!INCLUDE[TLA2#tla_cppcli](../../../includes/tla2sharptla-cppcli-md.md)], no targets exist that support compiling XAML; therefore, the value to pass is unspecified.</span></span>  
  
 <span data-ttu-id="92271-120">Belirtebilirsiniz <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> (`public` C# ' ta, `Public` Visual Basic'te); ancak belirtme <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> çünkü seyrek yapılan <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> zaten varsayılan davranıştır.</span><span class="sxs-lookup"><span data-stu-id="92271-120">You can also specify <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> (`public` in C#, `Public` in Visual Basic); however, specifying <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> is infrequently done because <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> is already the default behavior.</span></span>  
  
 <span data-ttu-id="92271-121">Diğer değerler eşdeğer kullanıcı kod ile erişim düzeyi kısıtlamaları gibi `private` C# ' ta ilgili olmayan `x:ClassModifier` çünkü iç içe geçmiş sınıf başvuruları XAML içinde desteklenmez ve bu nedenle, <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> değiştiricisi, aynı etkiye sahiptir.</span><span class="sxs-lookup"><span data-stu-id="92271-121">Other values with equivalent user code access-level restrictions, such as `private` in C#, are not relevant for `x:ClassModifier` because nested class references are not supported in XAML, and therefore, the <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> modifier has the same effect.</span></span>  
  
## <a name="security-notes"></a><span data-ttu-id="92271-122">Güvenlik notları</span><span class="sxs-lookup"><span data-stu-id="92271-122">Security Notes</span></span>  
 <span data-ttu-id="92271-123">Erişim düzeyi bildirilen `x:ClassModifier` yorumu belirli çerçeveleri ve yeteneklerini hala tabidir.</span><span class="sxs-lookup"><span data-stu-id="92271-123">The access level as declared in `x:ClassModifier` is still subject to interpretation by particular frameworks and their capabilities.</span></span> <span data-ttu-id="92271-124">WPF yüklemek ve türleri örneği için özellikleri içerir burada `x:ClassModifier` olduğu `internal`, bu sınıfı bir WPF kaynaktan bir URI başvuru paketi aracılığıyla başvurulur.</span><span class="sxs-lookup"><span data-stu-id="92271-124">WPF includes capabilities to load and instantiate types where `x:ClassModifier` is `internal`, if that class is referenced from a WPF resource through a pack URI reference.</span></span> <span data-ttu-id="92271-125">Bu durumda ve diğerleri gibi diğer çerçeveler tarafından uygulanan, söz konusu kümelerdeki potansiyel olarak, özel olarak üzerinde güvenmeyin `x:ClassModifier` olası tüm oluşturmada engellemeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="92271-125">As a consequence of this case and potentially others like it implemented by other frameworks, do not rely exclusively on `x:ClassModifier` to block all possible instantiation attempts.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92271-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="92271-126">See also</span></span>
- [<span data-ttu-id="92271-127">x:Class Yönergesi</span><span class="sxs-lookup"><span data-stu-id="92271-127">x:Class Directive</span></span>](../../../docs/framework/xaml-services/x-class-directive.md)
- [<span data-ttu-id="92271-128">Arka Plan Kod ve WPF İçindeki XAML</span><span class="sxs-lookup"><span data-stu-id="92271-128">Code-Behind and XAML in WPF</span></span>](../../../docs/framework/wpf/advanced/code-behind-and-xaml-in-wpf.md)
- [<span data-ttu-id="92271-129">x:FieldModifier Yönergesi</span><span class="sxs-lookup"><span data-stu-id="92271-129">x:FieldModifier Directive</span></span>](../../../docs/framework/xaml-services/x-fieldmodifier-directive.md)
- [<span data-ttu-id="92271-130">Güvenlik (WPF)</span><span class="sxs-lookup"><span data-stu-id="92271-130">Security (WPF)</span></span>](../../../docs/framework/wpf/security-wpf.md)
- [<span data-ttu-id="92271-131">WPF'den System.Xaml'e Geçirilen Türler</span><span class="sxs-lookup"><span data-stu-id="92271-131">Types Migrated from WPF to System.Xaml</span></span>](../../../docs/framework/xaml-services/types-migrated-from-wpf-to-system-xaml.md)
