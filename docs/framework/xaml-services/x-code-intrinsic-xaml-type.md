---
title: x:Code İç XAML Türü
ms.date: 03/30/2017
f1_keywords:
- Code
- x:Code
- xCode
helpviewer_keywords:
- Code directive in XAML [XAML Services]
- x:Code XAML directive element [XAML Services]
- XAML [XAML Services], x:Code directive element
ms.assetid: 87986b13-1a2e-4830-ae36-15f9dc5629e8
ms.openlocfilehash: 7bb78b05be7b3edc4471bc276010eabd92a07a14
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59145242"
---
# <a name="xcode-intrinsic-xaml-type"></a><span data-ttu-id="0dcd1-102">x:Code İç XAML Türü</span><span class="sxs-lookup"><span data-stu-id="0dcd1-102">x:Code Intrinsic XAML Type</span></span>
<span data-ttu-id="0dcd1-103">Kod içinde bir XAML üretim yerleşimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="0dcd1-103">Allows placement of code within a XAML production.</span></span> <span data-ttu-id="0dcd1-104">Bu tür kod ya da XAML veya bir çalışma zamanı tarafından yorumu gibi sonraki kullanımlar için XAML üretimde sol derleyen herhangi XAML işlemci uygulamasında tarafından derlenebilir.</span><span class="sxs-lookup"><span data-stu-id="0dcd1-104">Such code can either be compiled by any XAML processor implementation that compiles XAML, or left in the XAML production for later uses such as interpretation by a runtime.</span></span>  
  
## <a name="xaml-object-element-usage"></a><span data-ttu-id="0dcd1-105">XAML Nesne Öğesi Kullanımı</span><span class="sxs-lookup"><span data-stu-id="0dcd1-105">XAML Object Element Usage</span></span>  
  
```  
<x:Code>  
   // code instructions, usually enclosed by CDATA...  
</x:Code>  
```  
  
## <a name="remarks"></a><span data-ttu-id="0dcd1-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0dcd1-106">Remarks</span></span>  
 <span data-ttu-id="0dcd1-107">İçindeki kod `x:Code` XAML yönerge öğesi olduğundan hala genel XML ad alanı içinde yorumlanan ve sağlanan XAML ad alanları.</span><span class="sxs-lookup"><span data-stu-id="0dcd1-107">The code within the `x:Code` XAML directive element is still interpreted within the general XML namespace and the XAML namespaces provided.</span></span> <span data-ttu-id="0dcd1-108">Bu nedenle, genellikle için kullanılan kod içine alın gerekmez, `x:Code` içinde bir `CDATA` kesimi.</span><span class="sxs-lookup"><span data-stu-id="0dcd1-108">Therefore, it is usually necessary to enclose the code used for `x:Code` inside a `CDATA` segment.</span></span>  
  
 <span data-ttu-id="0dcd1-109">`x:Code` XAML üretim tüm olası dağıtım mekanizmaları için izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="0dcd1-109">`x:Code` is not permitted for all possible deployment mechanisms of a XAML production.</span></span> <span data-ttu-id="0dcd1-110">Belirli çerçeveleri (örneğin, WPF) kod olarak derlenmelidir.</span><span class="sxs-lookup"><span data-stu-id="0dcd1-110">In specific frameworks (for example WPF) the code must be compiled.</span></span> <span data-ttu-id="0dcd1-111">Diğer çerçeveleri de `x:Code` kullanım genellikle izin verilmiyor.</span><span class="sxs-lookup"><span data-stu-id="0dcd1-111">In other frameworks, `x:Code` usage might be generally disallowed.</span></span>  
  
 <span data-ttu-id="0dcd1-112">Yönetilen izin çerçeveler için `x:Code` içerik, kullanılacak doğru dil derleyicisi `x:Code` içeriği, ayarları ve uygulama derlemek için kullanılan içeren projenin hedefleri tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="0dcd1-112">For frameworks that permit managed `x:Code` content, the correct language compiler to use for `x:Code` content is determined by settings and targets of the containing project that is used to compile the application.</span></span>  
  
## <a name="wpf-usage-notes"></a><span data-ttu-id="0dcd1-113">WPF kullanım notları</span><span class="sxs-lookup"><span data-stu-id="0dcd1-113">WPF Usage Notes</span></span>  
 <span data-ttu-id="0dcd1-114">Bildirilen kod içinde `x:Code` WPF birkaç önemli sınırlamaları vardır:</span><span class="sxs-lookup"><span data-stu-id="0dcd1-114">Code declared within `x:Code` for WPF has several notable limitations:</span></span>  
  
-   <span data-ttu-id="0dcd1-115">`x:Code` Yönerge öğesi, XAML üretim kök öğesinin ilk alt öğesi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0dcd1-115">The `x:Code` directive element must be an immediate child element of the root element of the XAML production.</span></span>  
  
-   <span data-ttu-id="0dcd1-116">[x: Class yönergesi](x-class-directive.md) üst kök öğe üzerinde sağlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0dcd1-116">[x:Class Directive](x-class-directive.md) must be provided on the parent root element.</span></span>  
  
-   <span data-ttu-id="0dcd1-117">Kod içinde yerleştirilen `x:Code` için bu XAML sayfası oluşturulmakta olan kısmi sınıf kapsamında olmasını derleme tarafından kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="0dcd1-117">The code placed within `x:Code` will be treated by compilation to be within the scope of the partial class that is already being created for that XAML page.</span></span> <span data-ttu-id="0dcd1-118">Bu nedenle tanımladığınız tüm kodları üyeleri veya kısmi söz konusu sınıfın değişkenleri olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0dcd1-118">Therefore all code you define must be members or variables of that partial class.</span></span>  
  
-   <span data-ttu-id="0dcd1-119">' Den başka bir sınıf kısmi sınıf içinde iç içe tarafından ek sınıfları tanımlanamaz (iç içe geçme izin verilir, ancak iç içe geçmiş sınıflar XAML içinde başvurulduğundan, tipik değildir).</span><span class="sxs-lookup"><span data-stu-id="0dcd1-119">You cannot define additional classes, other than by nesting a class inside the partial class (nesting is allowed, but it is not typical because nested classes cannot be referenced in XAML).</span></span> <span data-ttu-id="0dcd1-120">CLR ad var olan kısmi sınıf için kullanılan ad alanı dışında tanımlanan veya eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="0dcd1-120">CLR namespaces other than the namespace that is used for the existing partial class cannot be defined or added to.</span></span>  
  
-   <span data-ttu-id="0dcd1-121">Kısmi sınıf CLR ad alanı dışında kod varlıklara başvurular tüm tam olarak nitelenmiş olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0dcd1-121">References to code entities outside the partial class CLR namespace must all be fully qualified.</span></span> <span data-ttu-id="0dcd1-122">Bildirilen üyeleri geçersiz kılmalar için geçersiz kılınabilir kısmi sınıf üyeleri, bu dile özgü geçersiz kılma anahtar sözcüğü ile belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="0dcd1-122">If members being declared are overrides to the partial class overridable members, this must be specified with the language-specific override keyword.</span></span> <span data-ttu-id="0dcd1-123">Üyeleri bildirilmişlerse `x:Code` kapsam çakışan XAML dışında oluşturulan bir kısmi sınıf üyelerine, şekilde derleyici çakışma raporları XAML dosyası derleme yüklemek veya.</span><span class="sxs-lookup"><span data-stu-id="0dcd1-123">If members declared in `x:Code` scope conflict with members of the partial class created out of the XAML, in such a way that the compiler reports the conflict, the XAML file cannot compile or load.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0dcd1-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0dcd1-124">See also</span></span>

- [<span data-ttu-id="0dcd1-125">x:Class Yönergesi</span><span class="sxs-lookup"><span data-stu-id="0dcd1-125">x:Class Directive</span></span>](x-class-directive.md)
- [<span data-ttu-id="0dcd1-126">Arka Plan Kod ve WPF İçindeki XAML</span><span class="sxs-lookup"><span data-stu-id="0dcd1-126">Code-Behind and XAML in WPF</span></span>](../wpf/advanced/code-behind-and-xaml-in-wpf.md)
- [<span data-ttu-id="0dcd1-127">XAML'ye Genel Bakış (WPF)</span><span class="sxs-lookup"><span data-stu-id="0dcd1-127">XAML Overview (WPF)</span></span>](../wpf/advanced/xaml-overview-wpf.md)
