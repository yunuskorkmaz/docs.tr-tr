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
ms.openlocfilehash: a24277a4d5fbc4870157b6c8ba00ba71ba61e656
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837239"
---
# <a name="xclassmodifier-directive"></a><span data-ttu-id="f2f9e-102">x:ClassModifier Yönergesi</span><span class="sxs-lookup"><span data-stu-id="f2f9e-102">x:ClassModifier Directive</span></span>
<span data-ttu-id="f2f9e-103">`x:Class` de sağlandığında XAML derleme davranışını değiştirir.</span><span class="sxs-lookup"><span data-stu-id="f2f9e-103">Modifies XAML compilation behavior when `x:Class` is also provided.</span></span> <span data-ttu-id="f2f9e-104">Özellikle, `Public` erişim düzeyine sahip (varsayılan) bir kısmi `class` oluşturmak yerine, belirtilen `x:Class` `NotPublic` erişim düzeyiyle oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="f2f9e-104">Specifically, instead of creating a partial `class` that has a `Public` access level (the default), the provided `x:Class` is created with a `NotPublic` access level.</span></span> <span data-ttu-id="f2f9e-105">Bu davranış, oluşturulan derlemelerdeki sınıfın erişim düzeyini etkiler.</span><span class="sxs-lookup"><span data-stu-id="f2f9e-105">This behavior affects the access level for the class in the generated assemblies.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="f2f9e-106">XAML Öznitelik Kullanımı</span><span class="sxs-lookup"><span data-stu-id="f2f9e-106">XAML Attribute Usage</span></span>  
  
```xaml  
<object x:Class="namespace.classname" x:ClassModifier="NotPublic">  
   ...  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="f2f9e-107">XAML Değerleri</span><span class="sxs-lookup"><span data-stu-id="f2f9e-107">XAML Values</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f2f9e-108">*NotPublic*</span><span class="sxs-lookup"><span data-stu-id="f2f9e-108">*NotPublic*</span></span>|<span data-ttu-id="f2f9e-109"><xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> ve <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> belirtmek için geçirilecek tam dize, kullandığınız kod arkasındaki programlama diline bağlı olarak değişir.</span><span class="sxs-lookup"><span data-stu-id="f2f9e-109">The exact string to pass to specify <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> versus <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> varies, depending on the code-behind programming language that you use.</span></span> <span data-ttu-id="f2f9e-110">Bkz. açıklamalar.</span><span class="sxs-lookup"><span data-stu-id="f2f9e-110">See Remarks.</span></span>|  
  
## <a name="dependencies"></a><span data-ttu-id="f2f9e-111">Bağımlılıklar</span><span class="sxs-lookup"><span data-stu-id="f2f9e-111">Dependencies</span></span>  
 <span data-ttu-id="f2f9e-112">[X:Class](x-class-directive.md) aynı öğe üzerinde de sağlanmalıdır ve bu öğenin bir sayfada kök öğe olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f2f9e-112">[x:Class](x-class-directive.md) must also be provided on the same element, and that element must be the root element in a page.</span></span> <span data-ttu-id="f2f9e-113">Daha fazla bilgi için bkz. [\[MS-XAML\] Bölüm 4.3.1.8](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="f2f9e-113">For more information, see [\[MS-XAML\] Section 4.3.1.8](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f2f9e-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f2f9e-114">Remarks</span></span>  
 <span data-ttu-id="f2f9e-115">.NET Framework XAML Hizmetleri kullanımındaki `x:ClassModifier` değeri programlama diline göre farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="f2f9e-115">The value of `x:ClassModifier` in .NET Framework XAML Services usage varies by programming language.</span></span> <span data-ttu-id="f2f9e-116">Kullanılacak dize, her dilin <xref:System.CodeDom.Compiler.CodeDomProvider> nasıl uyguladığı ve <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> ve <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>anlamlarını ve bu dilin büyük/küçük harfe duyarlı olup olmadığını tanımlamak için döndürdüğü tür Dönüştürücülerine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="f2f9e-116">The string to use depends on how each language implements its <xref:System.CodeDom.Compiler.CodeDomProvider> and the type converters it returns to define the meanings for <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> and <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>, and whether that language is case sensitive.</span></span>  
  
- <span data-ttu-id="f2f9e-117">İçin C#, <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> belirlemek için geçirilecek dize `internal`.</span><span class="sxs-lookup"><span data-stu-id="f2f9e-117">For C#, the string to pass to designate <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> is `internal`.</span></span>  
  
- <span data-ttu-id="f2f9e-118">Microsoft Visual Basic .NET için, <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> belirlemek için geçirilecek dize `Friend`.</span><span class="sxs-lookup"><span data-stu-id="f2f9e-118">For Microsoft Visual Basic .NET, the string to pass to designate <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> is `Friend`.</span></span>  
  
- <span data-ttu-id="f2f9e-119">/CLI C++için XAML derlemeyi destekleyen bir hedef yok; Bu nedenle, geçirilecek değer belirtilmemiş.</span><span class="sxs-lookup"><span data-stu-id="f2f9e-119">For C++/CLI, no targets exist that support compiling XAML; therefore, the value to pass is unspecified.</span></span>  
  
 <span data-ttu-id="f2f9e-120">Ayrıca C#, <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> de belirtebilirsiniz (`public`, Visual Basic içinde `Public`); Ancak, <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> zaten varsayılan davranış olduğu için <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> belirtme işlemi seyrek yapılır.</span><span class="sxs-lookup"><span data-stu-id="f2f9e-120">You can also specify <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> (`public` in C#, `Public` in Visual Basic); however, specifying <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> is infrequently done because <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> is already the default behavior.</span></span>  
  
 <span data-ttu-id="f2f9e-121">İçinde C#`private` gibi eşdeğer Kullanıcı kodu erişim düzeyi kısıtlamalarına sahip diğer değerler, XAML 'de iç içe geçmiş sınıf başvuruları desteklenmediğinden `x:ClassModifier` için uygun değildir ve bu nedenle <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> değiştiricisi aynı etkiye sahiptir.</span><span class="sxs-lookup"><span data-stu-id="f2f9e-121">Other values with equivalent user code access-level restrictions, such as `private` in C#, are not relevant for `x:ClassModifier` because nested class references are not supported in XAML, and therefore, the <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> modifier has the same effect.</span></span>  
  
## <a name="security-notes"></a><span data-ttu-id="f2f9e-122">Güvenlik notları</span><span class="sxs-lookup"><span data-stu-id="f2f9e-122">Security Notes</span></span>  
 <span data-ttu-id="f2f9e-123">`x:ClassModifier` içinde bildirildiği gibi erişim düzeyi, hala belirli çerçeveler ve bunların özelliklerine göre yoruma tabidir.</span><span class="sxs-lookup"><span data-stu-id="f2f9e-123">The access level as declared in `x:ClassModifier` is still subject to interpretation by particular frameworks and their capabilities.</span></span> <span data-ttu-id="f2f9e-124">WPF, bir paket URI başvurusu aracılığıyla bir WPF kaynağından başvuruluyorsa, `x:ClassModifier` `internal`olan türleri yükleme ve oluşturma özelliklerini içerir.</span><span class="sxs-lookup"><span data-stu-id="f2f9e-124">WPF includes capabilities to load and instantiate types where `x:ClassModifier` is `internal`, if that class is referenced from a WPF resource through a pack URI reference.</span></span> <span data-ttu-id="f2f9e-125">Bu durumun bir sonucu ve diğer çerçeveler tarafından uygulandığı gibi diğerleri, olası tüm örnek oluşturma girişimlerini engellemek için yalnızca `x:ClassModifier` güvenmeyin.</span><span class="sxs-lookup"><span data-stu-id="f2f9e-125">As a consequence of this case and potentially others like it implemented by other frameworks, do not rely exclusively on `x:ClassModifier` to block all possible instantiation attempts.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2f9e-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f2f9e-126">See also</span></span>

- [<span data-ttu-id="f2f9e-127">x:Class Yönergesi</span><span class="sxs-lookup"><span data-stu-id="f2f9e-127">x:Class Directive</span></span>](x-class-directive.md)
- [<span data-ttu-id="f2f9e-128">Arka Plan Kod ve WPF İçindeki XAML</span><span class="sxs-lookup"><span data-stu-id="f2f9e-128">Code-Behind and XAML in WPF</span></span>](../wpf/advanced/code-behind-and-xaml-in-wpf.md)
- [<span data-ttu-id="f2f9e-129">x:FieldModifier Yönergesi</span><span class="sxs-lookup"><span data-stu-id="f2f9e-129">x:FieldModifier Directive</span></span>](x-fieldmodifier-directive.md)
- [<span data-ttu-id="f2f9e-130">Güvenlik (WPF)</span><span class="sxs-lookup"><span data-stu-id="f2f9e-130">Security (WPF)</span></span>](../wpf/security-wpf.md)
- [<span data-ttu-id="f2f9e-131">WPF'den System.Xaml'e Geçirilen Türler</span><span class="sxs-lookup"><span data-stu-id="f2f9e-131">Types Migrated from WPF to System.Xaml</span></span>](types-migrated-from-wpf-to-system-xaml.md)
