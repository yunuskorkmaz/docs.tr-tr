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
ms.openlocfilehash: 436204774c2d59b43a77865c666aed702f7681db
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2020
ms.locfileid: "82072034"
---
# <a name="xclassmodifier-directive"></a><span data-ttu-id="0ec25-102">x:ClassModifier Yönergesi</span><span class="sxs-lookup"><span data-stu-id="0ec25-102">x:ClassModifier Directive</span></span>
<span data-ttu-id="0ec25-103">XAML derleme davranışını `x:Class` da sağlandığında değiştirir.</span><span class="sxs-lookup"><span data-stu-id="0ec25-103">Modifies XAML compilation behavior when `x:Class` is also provided.</span></span> <span data-ttu-id="0ec25-104">Özellikle, erişim düzeyi `class` (varsayılan) `Public` olan bir kısmi oluşturmak `x:Class` yerine, `NotPublic` sağlanan bir erişim düzeyi ile oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="0ec25-104">Specifically, instead of creating a partial `class` that has a `Public` access level (the default), the provided `x:Class` is created with a `NotPublic` access level.</span></span> <span data-ttu-id="0ec25-105">Bu davranış, oluşturulan derlemelerde sınıfın erişim düzeyini etkiler.</span><span class="sxs-lookup"><span data-stu-id="0ec25-105">This behavior affects the access level for the class in the generated assemblies.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="0ec25-106">XAML Öznitelik Kullanımı</span><span class="sxs-lookup"><span data-stu-id="0ec25-106">XAML Attribute Usage</span></span>

```xaml
<object x:Class="namespace.classname" x:ClassModifier="NotPublic">
   ...
</object>
```

## <a name="xaml-values"></a><span data-ttu-id="0ec25-107">XAML Değerleri</span><span class="sxs-lookup"><span data-stu-id="0ec25-107">XAML Values</span></span>

|||
|-|-|
|<span data-ttu-id="0ec25-108">*Genel Not*</span><span class="sxs-lookup"><span data-stu-id="0ec25-108">*NotPublic*</span></span>|<span data-ttu-id="0ec25-109">Karşı belirtmek <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> için geçecek <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> tam dize, kullandığınız kod arkası programlama diline bağlı olarak değişir.</span><span class="sxs-lookup"><span data-stu-id="0ec25-109">The exact string to pass to specify <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> versus <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> varies, depending on the code-behind programming language that you use.</span></span> <span data-ttu-id="0ec25-110">Bkz. Açıklamalar.</span><span class="sxs-lookup"><span data-stu-id="0ec25-110">See Remarks.</span></span>|

## <a name="dependencies"></a><span data-ttu-id="0ec25-111">Bağımlılıklar</span><span class="sxs-lookup"><span data-stu-id="0ec25-111">Dependencies</span></span>

<span data-ttu-id="0ec25-112">[x:Sınıf](xclass-directive.md) da aynı öğe üzerinde sağlanmalıdır ve bu öğe bir sayfadaki kök öğe olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0ec25-112">[x:Class](xclass-directive.md) must also be provided on the same element, and that element must be the root element in a page.</span></span> <span data-ttu-id="0ec25-113">Daha fazla bilgi için [ \[MS-XAML\] Bölüm 4.3.1.8'e](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10))bakın.</span><span class="sxs-lookup"><span data-stu-id="0ec25-113">For more information, see [\[MS-XAML\] Section 4.3.1.8](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>

## <a name="remarks"></a><span data-ttu-id="0ec25-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0ec25-114">Remarks</span></span>

<span data-ttu-id="0ec25-115">.NET `x:ClassModifier` XAML Hizmetleri'ndeki değer programlama diline göre değişir.</span><span class="sxs-lookup"><span data-stu-id="0ec25-115">The value of `x:ClassModifier` in .NET XAML Services usage varies by programming language.</span></span> <span data-ttu-id="0ec25-116">Kullanılacak dize, her dilin kendi <xref:System.CodeDom.Compiler.CodeDomProvider> sini nasıl uyguladığına ve anlamları tanımlamak <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>için döndürdüğü tür dönüştürücülerine ve bu dilin büyük/küçük harf duyarlı olup olmadığına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="0ec25-116">The string to use depends on how each language implements its <xref:System.CodeDom.Compiler.CodeDomProvider> and the type converters it returns to define the meanings for <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> and <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>, and whether that language is case sensitive.</span></span>

- <span data-ttu-id="0ec25-117">C# için, belirtmek <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> için geçmek `internal`için dize.</span><span class="sxs-lookup"><span data-stu-id="0ec25-117">For C#, the string to pass to designate <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> is `internal`.</span></span>

- <span data-ttu-id="0ec25-118">Microsoft Visual Basic .NET için, belirtmek <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> `Friend`için geçmek için dize.</span><span class="sxs-lookup"><span data-stu-id="0ec25-118">For Microsoft Visual Basic .NET, the string to pass to designate <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> is `Friend`.</span></span>

- <span data-ttu-id="0ec25-119">C++/CLI için XAML derlemeyi destekleyen hiçbir hedef yoktur; bu nedenle, geçmek için değer belirtilmemiştir.</span><span class="sxs-lookup"><span data-stu-id="0ec25-119">For C++/CLI, no targets exist that support compiling XAML; therefore, the value to pass is unspecified.</span></span>

<span data-ttu-id="0ec25-120">Ayrıca belirtebilirsiniz <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> `public` (C#, `Public` Visual Basic'te); ancak, zaten <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> varsayılan davranış <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> olduğundan belirtme seyrek yapılır.</span><span class="sxs-lookup"><span data-stu-id="0ec25-120">You can also specify <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> (`public` in C#, `Public` in Visual Basic); however, specifying <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> is infrequently done because <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> is already the default behavior.</span></span>

<span data-ttu-id="0ec25-121">C# gibi `private` eşdeğer kullanıcı kodu erişim düzeyi kısıtlamalarına sahip diğer `x:ClassModifier` değerler, iç içe geçen sınıf başvuruları XAML'de desteklenmediği ve bu nedenle değiştiricinin <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> aynı etkiye sahip olması nedeniyle ilgili değildir.</span><span class="sxs-lookup"><span data-stu-id="0ec25-121">Other values with equivalent user code access-level restrictions, such as `private` in C#, are not relevant for `x:ClassModifier` because nested class references are not supported in XAML, and therefore, the <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> modifier has the same effect.</span></span>

## <a name="security-notes"></a><span data-ttu-id="0ec25-122">Güvenlik Notları</span><span class="sxs-lookup"><span data-stu-id="0ec25-122">Security Notes</span></span>

<span data-ttu-id="0ec25-123">Beyan edildiği `x:ClassModifier` gibi erişim düzeyi hala belirli çerçeveler ve yetenekleri tarafından yorumlanmasına tabidir.</span><span class="sxs-lookup"><span data-stu-id="0ec25-123">The access level as declared in `x:ClassModifier` is still subject to interpretation by particular frameworks and their capabilities.</span></span> <span data-ttu-id="0ec25-124">WPF, bir paket URI başvurusu aracılığıyla `x:ClassModifier` wpf kaynağından `internal`başvurulmuşsa, türleri yüklemek ve anlık olarak yüklemek için yetenekler içerir.</span><span class="sxs-lookup"><span data-stu-id="0ec25-124">WPF includes capabilities to load and instantiate types where `x:ClassModifier` is `internal`, if that class is referenced from a WPF resource through a pack URI reference.</span></span> <span data-ttu-id="0ec25-125">Bu durumda bir sonucu olarak ve diğer çerçeveler tarafından uygulanan gibi potansiyel `x:ClassModifier` diğerleri, sadece tüm olası anlık açma girişimleri engellemek için güvenmeyin.</span><span class="sxs-lookup"><span data-stu-id="0ec25-125">As a consequence of this case and potentially others like it implemented by other frameworks, do not rely exclusively on `x:ClassModifier` to block all possible instantiation attempts.</span></span>

## <a name="see-also"></a><span data-ttu-id="0ec25-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0ec25-126">See also</span></span>

- [<span data-ttu-id="0ec25-127">x:Class Yönergesi</span><span class="sxs-lookup"><span data-stu-id="0ec25-127">x:Class Directive</span></span>](xclass-directive.md)
- [<span data-ttu-id="0ec25-128">Arka Plan Kod ve WPF İçindeki XAML</span><span class="sxs-lookup"><span data-stu-id="0ec25-128">Code-Behind and XAML in WPF</span></span>](../../framework/wpf/advanced/code-behind-and-xaml-in-wpf.md)
- [<span data-ttu-id="0ec25-129">x:FieldModifier Yönergesi</span><span class="sxs-lookup"><span data-stu-id="0ec25-129">x:FieldModifier Directive</span></span>](xfieldmodifier-directive.md)
- [<span data-ttu-id="0ec25-130">Güvenlik (WPF)</span><span class="sxs-lookup"><span data-stu-id="0ec25-130">Security (WPF)</span></span>](../../framework/wpf/security-wpf.md)
- [<span data-ttu-id="0ec25-131">WPF'den System.Xaml'e Geçirilen Türler</span><span class="sxs-lookup"><span data-stu-id="0ec25-131">Types Migrated from WPF to System.Xaml</span></span>](../../framework/wpf/advanced/types-migrated-from-wpf-to-system.md)
