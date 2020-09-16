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
ms.openlocfilehash: 73732a06029cca3a4c6c6d82762d5263c5b8c955
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90544823"
---
# <a name="xclassmodifier-directive"></a><span data-ttu-id="79678-102">x:ClassModifier Yönergesi</span><span class="sxs-lookup"><span data-stu-id="79678-102">x:ClassModifier Directive</span></span>
<span data-ttu-id="79678-103">Ayrıca sağlandığında XAML derleme davranışını değiştirir `x:Class` .</span><span class="sxs-lookup"><span data-stu-id="79678-103">Modifies XAML compilation behavior when `x:Class` is also provided.</span></span> <span data-ttu-id="79678-104">Özellikle, erişim düzeyine sahip bir kısmi oluşturmak yerine `class` `Public` (varsayılan), belirtilen bir `x:Class` `NotPublic` erişim düzeyiyle oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="79678-104">Specifically, instead of creating a partial `class` that has a `Public` access level (the default), the provided `x:Class` is created with a `NotPublic` access level.</span></span> <span data-ttu-id="79678-105">Bu davranış, oluşturulan derlemelerdeki sınıfın erişim düzeyini etkiler.</span><span class="sxs-lookup"><span data-stu-id="79678-105">This behavior affects the access level for the class in the generated assemblies.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="79678-106">XAML Öznitelik Kullanımı</span><span class="sxs-lookup"><span data-stu-id="79678-106">XAML Attribute Usage</span></span>

```xaml
<object x:Class="namespace.classname" x:ClassModifier="NotPublic">
   ...
</object>
```

## <a name="xaml-values"></a><span data-ttu-id="79678-107">XAML Değerleri</span><span class="sxs-lookup"><span data-stu-id="79678-107">XAML Values</span></span>

|||
|-|-|
|<span data-ttu-id="79678-108">*NotPublic*</span><span class="sxs-lookup"><span data-stu-id="79678-108">*NotPublic*</span></span>|<span data-ttu-id="79678-109">Belirtmek için geçirilecek tam dize <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> , kullandığınız arka plan kod programlama diline bağlı olarak farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="79678-109">The exact string to pass to specify <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> versus <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> varies, depending on the code-behind programming language that you use.</span></span> <span data-ttu-id="79678-110">Bkz. açıklamalar.</span><span class="sxs-lookup"><span data-stu-id="79678-110">See Remarks.</span></span>|

## <a name="dependencies"></a><span data-ttu-id="79678-111">Bağımlılıklar</span><span class="sxs-lookup"><span data-stu-id="79678-111">Dependencies</span></span>

<span data-ttu-id="79678-112">[X:Class](xclass-directive.md) aynı öğe üzerinde de sağlanmalıdır ve bu öğenin bir sayfada kök öğe olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="79678-112">[x:Class](xclass-directive.md) must also be provided on the same element, and that element must be the root element in a page.</span></span> <span data-ttu-id="79678-113">Daha fazla bilgi için bkz. [ \[ MS-xaml \] section 4.3.1.8](/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="79678-113">For more information, see [\[MS-XAML\] Section 4.3.1.8](/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>

## <a name="remarks"></a><span data-ttu-id="79678-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="79678-114">Remarks</span></span>

<span data-ttu-id="79678-115">`x:ClassModifier`.Net xaml Hizmetleri kullanımındaki değeri programlama diline göre farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="79678-115">The value of `x:ClassModifier` in .NET XAML Services usage varies by programming language.</span></span> <span data-ttu-id="79678-116">Kullanılacak dize, her dilin <xref:System.CodeDom.Compiler.CodeDomProvider> ve için anlamlarını ve <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> bu dilin büyük/küçük harfe duyarlı olup olmadığını tanımlamak için döndürdüğü tür Dönüştürücülerine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="79678-116">The string to use depends on how each language implements its <xref:System.CodeDom.Compiler.CodeDomProvider> and the type converters it returns to define the meanings for <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> and <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>, and whether that language is case sensitive.</span></span>

- <span data-ttu-id="79678-117">C# için, atamak için geçirilecek dize <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> olur `internal` .</span><span class="sxs-lookup"><span data-stu-id="79678-117">For C#, the string to pass to designate <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> is `internal`.</span></span>

- <span data-ttu-id="79678-118">Microsoft Visual Basic .NET için, atamak için geçirilecek dize <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> olur `Friend` .</span><span class="sxs-lookup"><span data-stu-id="79678-118">For Microsoft Visual Basic .NET, the string to pass to designate <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> is `Friend`.</span></span>

- <span data-ttu-id="79678-119">C++/CLı için XAML derlemeyi destekleyen bir hedef yoktur; Bu nedenle, geçirilecek değer belirtilmemiş.</span><span class="sxs-lookup"><span data-stu-id="79678-119">For C++/CLI, no targets exist that support compiling XAML; therefore, the value to pass is unspecified.</span></span>

<span data-ttu-id="79678-120">Ayrıca, <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> ( `public` C# ' de Visual Basic) öğesini de belirtebilirsiniz `Public` ; ancak, <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> varsayılan davranış zaten olduğu için, belirtme daha seyrek yapılır <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="79678-120">You can also specify <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> (`public` in C#, `Public` in Visual Basic); however, specifying <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> is infrequently done because <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> is already the default behavior.</span></span>

<span data-ttu-id="79678-121">C# ' de olduğu gibi eşdeğer Kullanıcı kodu erişim düzeyi kısıtlamalarına sahip diğer değerler, `private` `x:ClassModifier` iç içe geçmiş sınıf başvuruları xaml 'de desteklenmediğinden, bu nedenle <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> değiştirici aynı etkiye sahiptir.</span><span class="sxs-lookup"><span data-stu-id="79678-121">Other values with equivalent user code access-level restrictions, such as `private` in C#, are not relevant for `x:ClassModifier` because nested class references are not supported in XAML, and therefore, the <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> modifier has the same effect.</span></span>

## <a name="security-notes"></a><span data-ttu-id="79678-122">Güvenlik notları</span><span class="sxs-lookup"><span data-stu-id="79678-122">Security Notes</span></span>

<span data-ttu-id="79678-123">İçinde bildirildiği gibi erişim düzeyi `x:ClassModifier` , hala belirli çerçeveler ve bunların özelliklerine göre yoruma tabidir.</span><span class="sxs-lookup"><span data-stu-id="79678-123">The access level as declared in `x:ClassModifier` is still subject to interpretation by particular frameworks and their capabilities.</span></span> <span data-ttu-id="79678-124">WPF, bir `x:ClassModifier` `internal` paket URI başvurusu aracılığıyla bir WPF kaynağından başvuruluyorsa, türü yükleme ve örnek oluşturma özelliklerini içerir.</span><span class="sxs-lookup"><span data-stu-id="79678-124">WPF includes capabilities to load and instantiate types where `x:ClassModifier` is `internal`, if that class is referenced from a WPF resource through a pack URI reference.</span></span> <span data-ttu-id="79678-125">Bu durumun bir sonucu ve diğer çerçeveler tarafından uygulandığı gibi diğerleri, `x:ClassModifier` olası tüm örnek oluşturma girişimlerini engellemek için özel olarak açık değildir.</span><span class="sxs-lookup"><span data-stu-id="79678-125">As a consequence of this case and potentially others like it implemented by other frameworks, do not rely exclusively on `x:ClassModifier` to block all possible instantiation attempts.</span></span>

## <a name="see-also"></a><span data-ttu-id="79678-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="79678-126">See also</span></span>

- [<span data-ttu-id="79678-127">x:Class Yönergesi</span><span class="sxs-lookup"><span data-stu-id="79678-127">x:Class Directive</span></span>](xclass-directive.md)
- [<span data-ttu-id="79678-128">Arka Plan Kod ve WPF İçindeki XAML</span><span class="sxs-lookup"><span data-stu-id="79678-128">Code-Behind and XAML in WPF</span></span>](/dotnet/desktop/wpf/advanced/code-behind-and-xaml-in-wpf)
- [<span data-ttu-id="79678-129">x:FieldModifier Yönergesi</span><span class="sxs-lookup"><span data-stu-id="79678-129">x:FieldModifier Directive</span></span>](xfieldmodifier-directive.md)
- [<span data-ttu-id="79678-130">Güvenlik (WPF)</span><span class="sxs-lookup"><span data-stu-id="79678-130">Security (WPF)</span></span>](/dotnet/desktop/wpf/security-wpf)
- [<span data-ttu-id="79678-131">WPF'den System.Xaml'e Geçirilen Türler</span><span class="sxs-lookup"><span data-stu-id="79678-131">Types Migrated from WPF to System.Xaml</span></span>](/dotnet/desktop/wpf/advanced/types-migrated-from-wpf-to-system)
