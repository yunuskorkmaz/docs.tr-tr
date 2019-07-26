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
ms.openlocfilehash: c3c08f61b49a6367663cf02099dda86d1a692284
ms.sourcegitcommit: 4b9c2d893b45d47048c6598b4182ba87759b1b59
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/25/2019
ms.locfileid: "68484754"
---
# <a name="xclassmodifier-directive"></a><span data-ttu-id="5969c-102">x:ClassModifier Yönergesi</span><span class="sxs-lookup"><span data-stu-id="5969c-102">x:ClassModifier Directive</span></span>
<span data-ttu-id="5969c-103">Ayrıca sağlandığında xaml derleme davranışını `x:Class` değiştirir.</span><span class="sxs-lookup"><span data-stu-id="5969c-103">Modifies XAML compilation behavior when `x:Class` is also provided.</span></span> <span data-ttu-id="5969c-104">Özellikle, `Public` erişim düzeyine sahip bir kısmi `class` oluşturmak yerine (varsayılan), `NotPublic` belirtilen `x:Class` bir erişim düzeyiyle oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="5969c-104">Specifically, instead of creating a partial `class` that has a `Public` access level (the default), the provided `x:Class` is created with a `NotPublic` access level.</span></span> <span data-ttu-id="5969c-105">Bu davranış, oluşturulan derlemelerdeki sınıfın erişim düzeyini etkiler.</span><span class="sxs-lookup"><span data-stu-id="5969c-105">This behavior affects the access level for the class in the generated assemblies.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="5969c-106">XAML Öznitelik Kullanımı</span><span class="sxs-lookup"><span data-stu-id="5969c-106">XAML Attribute Usage</span></span>  
  
```  
<object x:Class="namespace.classname" x:ClassModifier="NotPublic">  
   ...  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="5969c-107">XAML Değerleri</span><span class="sxs-lookup"><span data-stu-id="5969c-107">XAML Values</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5969c-108">*NotPublic*</span><span class="sxs-lookup"><span data-stu-id="5969c-108">*NotPublic*</span></span>|<span data-ttu-id="5969c-109"><xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> Belirtmek<xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> için geçirilecek tam dize, kullandığınız arka plan kod programlama diline bağlı olarak farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="5969c-109">The exact string to pass to specify <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> versus <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> varies, depending on the code-behind programming language that you use.</span></span> <span data-ttu-id="5969c-110">Bkz. açıklamalar.</span><span class="sxs-lookup"><span data-stu-id="5969c-110">See Remarks.</span></span>|  
  
## <a name="dependencies"></a><span data-ttu-id="5969c-111">Bağımlılıkları</span><span class="sxs-lookup"><span data-stu-id="5969c-111">Dependencies</span></span>  
 <span data-ttu-id="5969c-112">[X:Class](x-class-directive.md) aynı öğe üzerinde de sağlanmalıdır ve bu öğenin bir sayfada kök öğe olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="5969c-112">[x:Class](x-class-directive.md) must also be provided on the same element, and that element must be the root element in a page.</span></span> <span data-ttu-id="5969c-113">Daha fazla bilgi için bkz [ \[. MS-\] xaml Section 4.3.1.8](https://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="5969c-113">For more information, see [\[MS-XAML\] Section 4.3.1.8](https://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5969c-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5969c-114">Remarks</span></span>  
 <span data-ttu-id="5969c-115">.NET Framework xaml Hizmetleri `x:ClassModifier` kullanımındaki değeri programlama diline göre değişir.</span><span class="sxs-lookup"><span data-stu-id="5969c-115">The value of `x:ClassModifier` in .NET Framework XAML Services usage varies by programming language.</span></span> <span data-ttu-id="5969c-116">Kullanılacak dize, her dilin ve <xref:System.CodeDom.Compiler.CodeDomProvider> <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>için <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> anlamlarını ve bu dilin büyük/küçük harfe duyarlı olup olmadığını tanımlamak için döndürdüğü tür Dönüştürücülerine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="5969c-116">The string to use depends on how each language implements its <xref:System.CodeDom.Compiler.CodeDomProvider> and the type converters it returns to define the meanings for <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> and <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>, and whether that language is case sensitive.</span></span>  
  
- <span data-ttu-id="5969c-117">İçin C#, atamak <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> için geçirilecek dize olur `internal`.</span><span class="sxs-lookup"><span data-stu-id="5969c-117">For C#, the string to pass to designate <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> is `internal`.</span></span>  
  
- <span data-ttu-id="5969c-118">Microsoft Visual Basic .NET için, atamak <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> için geçirilecek dize olur. `Friend`</span><span class="sxs-lookup"><span data-stu-id="5969c-118">For Microsoft Visual Basic .NET, the string to pass to designate <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> is `Friend`.</span></span>  
  
- <span data-ttu-id="5969c-119">/CLI C++için XAML derlemeyi destekleyen bir hedef yok; Bu nedenle, geçirilecek değer belirtilmemiş.</span><span class="sxs-lookup"><span data-stu-id="5969c-119">For C++/CLI, no targets exist that support compiling XAML; therefore, the value to pass is unspecified.</span></span>  
  
 <span data-ttu-id="5969c-120">Ayrıca, (`public` içinde <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> C# <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> , `Public` Visual Basic ' de) belirtebilirsiniz; ancak, varsayılan davranış zaten olduğu için, ' de <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="5969c-120">You can also specify <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> (`public` in C#, `Public` in Visual Basic); however, specifying <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> is infrequently done because <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> is already the default behavior.</span></span>  
  
 <span data-ttu-id="5969c-121">`private` C#İçindeki gibi eşdeğer Kullanıcı kodu erişim düzeyi kısıtlamalarına sahip diğer değerler, iç içe geçmiş sınıf başvuruları xaml 'de `x:ClassModifier` desteklenmediğinden ve bu nedenle, değiştiricinin aynı etkiye sahip olduğu için ilgili değildir <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> . .</span><span class="sxs-lookup"><span data-stu-id="5969c-121">Other values with equivalent user code access-level restrictions, such as `private` in C#, are not relevant for `x:ClassModifier` because nested class references are not supported in XAML, and therefore, the <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> modifier has the same effect.</span></span>  
  
## <a name="security-notes"></a><span data-ttu-id="5969c-122">Güvenlik notları</span><span class="sxs-lookup"><span data-stu-id="5969c-122">Security Notes</span></span>  
 <span data-ttu-id="5969c-123">İçinde `x:ClassModifier` bildirildiği gibi erişim düzeyi, hala belirli çerçeveler ve bunların özelliklerine göre yoruma tabidir.</span><span class="sxs-lookup"><span data-stu-id="5969c-123">The access level as declared in `x:ClassModifier` is still subject to interpretation by particular frameworks and their capabilities.</span></span> <span data-ttu-id="5969c-124">WPF, bir paket URI başvurusu aracılığıyla bir WPF `x:ClassModifier` kaynağından `internal`başvuruluyorsa, türü yükleme ve örnek oluşturma özelliklerini içerir.</span><span class="sxs-lookup"><span data-stu-id="5969c-124">WPF includes capabilities to load and instantiate types where `x:ClassModifier` is `internal`, if that class is referenced from a WPF resource through a pack URI reference.</span></span> <span data-ttu-id="5969c-125">Bu durumun bir sonucu ve diğer çerçeveler tarafından uygulandığı gibi diğerleri, olası tüm örnek oluşturma girişimlerini engellemek için özel olarak `x:ClassModifier` açık değildir.</span><span class="sxs-lookup"><span data-stu-id="5969c-125">As a consequence of this case and potentially others like it implemented by other frameworks, do not rely exclusively on `x:ClassModifier` to block all possible instantiation attempts.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5969c-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5969c-126">See also</span></span>

- [<span data-ttu-id="5969c-127">x:Class Yönergesi</span><span class="sxs-lookup"><span data-stu-id="5969c-127">x:Class Directive</span></span>](x-class-directive.md)
- [<span data-ttu-id="5969c-128">Arka Plan Kod ve WPF İçindeki XAML</span><span class="sxs-lookup"><span data-stu-id="5969c-128">Code-Behind and XAML in WPF</span></span>](../wpf/advanced/code-behind-and-xaml-in-wpf.md)
- [<span data-ttu-id="5969c-129">x:FieldModifier Yönergesi</span><span class="sxs-lookup"><span data-stu-id="5969c-129">x:FieldModifier Directive</span></span>](x-fieldmodifier-directive.md)
- [<span data-ttu-id="5969c-130">Güvenlik (WPF)</span><span class="sxs-lookup"><span data-stu-id="5969c-130">Security (WPF)</span></span>](../wpf/security-wpf.md)
- [<span data-ttu-id="5969c-131">WPF'den System.Xaml'e Geçirilen Türler</span><span class="sxs-lookup"><span data-stu-id="5969c-131">Types Migrated from WPF to System.Xaml</span></span>](types-migrated-from-wpf-to-system-xaml.md)
