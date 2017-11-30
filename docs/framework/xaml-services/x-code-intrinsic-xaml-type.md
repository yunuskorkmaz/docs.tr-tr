---
title: "x:Code İç XAML Türü"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Code
- x:Code
- xCode
helpviewer_keywords:
- Code directive in XAML [XAML Services]
- x:Code XAML directive element [XAML Services]
- XAML [XAML Services], x:Code directive element
ms.assetid: 87986b13-1a2e-4830-ae36-15f9dc5629e8
caps.latest.revision: "19"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: d1b21e2a654b18547c8da7da724c87946724f71f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="xcode-intrinsic-xaml-type"></a><span data-ttu-id="b86af-102">x:Code İç XAML Türü</span><span class="sxs-lookup"><span data-stu-id="b86af-102">x:Code Intrinsic XAML Type</span></span>
<span data-ttu-id="b86af-103">XAML üretim içindeki kod yerleşimini sağlar.</span><span class="sxs-lookup"><span data-stu-id="b86af-103">Allows placement of code within a XAML production.</span></span> <span data-ttu-id="b86af-104">Bu tür kodu ya da XAML ya da bir çalışma zamanı tarafından tercüme gibi sonraki kullanımlar için XAML üretimde sol derler herhangi bir XAML işlemci uygulaması tarafından derlenebilir.</span><span class="sxs-lookup"><span data-stu-id="b86af-104">Such code can either be compiled by any XAML processor implementation that compiles XAML, or left in the XAML production for later uses such as interpretation by a runtime.</span></span>  
  
## <a name="xaml-object-element-usage"></a><span data-ttu-id="b86af-105">XAML Nesne Öğesi Kullanımı</span><span class="sxs-lookup"><span data-stu-id="b86af-105">XAML Object Element Usage</span></span>  
  
```  
<x:Code>  
   // code instructions, usually enclosed by CDATA...  
</x:Code>  
```  
  
## <a name="remarks"></a><span data-ttu-id="b86af-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b86af-106">Remarks</span></span>  
 <span data-ttu-id="b86af-107">İçindeki kod `x:Code` genel XML ad alanı içinde yorumlanan hala ve sağlanan XAML ad uzayları XAML yönerge öğesi değil.</span><span class="sxs-lookup"><span data-stu-id="b86af-107">The code within the `x:Code` XAML directive element is still interpreted within the general XML namespace and the XAML namespaces provided.</span></span> <span data-ttu-id="b86af-108">Bu nedenle, için kullanılan kod içine genellikle gerekli `x:Code` içinde bir `CDATA` kesimi.</span><span class="sxs-lookup"><span data-stu-id="b86af-108">Therefore, it is usually necessary to enclose the code used for `x:Code` inside a `CDATA` segment.</span></span>  
  
 <span data-ttu-id="b86af-109">`x:Code`XAML üretim tüm olası dağıtım mekanizmaları izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="b86af-109">`x:Code` is not permitted for all possible deployment mechanisms of a XAML production.</span></span> <span data-ttu-id="b86af-110">Belirli çerçeveleri (örneğin, WPF) derlenmiş kod gerekir.</span><span class="sxs-lookup"><span data-stu-id="b86af-110">In specific frameworks (for example WPF) the code must be compiled.</span></span> <span data-ttu-id="b86af-111">Diğer çerçeveler içinde `x:Code` kullanım genellikle izin verilmiyor.</span><span class="sxs-lookup"><span data-stu-id="b86af-111">In other frameworks, `x:Code` usage might be generally disallowed.</span></span>  
  
 <span data-ttu-id="b86af-112">Yönetilen izin çerçeveler için `x:Code` içerik, kullanılmak üzere doğru dil derleyici `x:Code` içerik ayarları ve uygulama derlemek için kullanılan içeren proje hedefleri tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="b86af-112">For frameworks that permit managed `x:Code` content, the correct language compiler to use for `x:Code` content is determined by settings and targets of the containing project that is used to compile the application.</span></span>  
  
## <a name="wpf-usage-notes"></a><span data-ttu-id="b86af-113">WPF kullanım notları</span><span class="sxs-lookup"><span data-stu-id="b86af-113">WPF Usage Notes</span></span>  
 <span data-ttu-id="b86af-114">Kod bildirilen içinde `x:Code` WPF birkaç önemli sınırlamalara sahiptir:</span><span class="sxs-lookup"><span data-stu-id="b86af-114">Code declared within `x:Code` for WPF has several notable limitations:</span></span>  
  
-   <span data-ttu-id="b86af-115">`x:Code` Yönerge öğesi XAML üretim kök öğesinin hemen alt öğesi olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="b86af-115">The `x:Code` directive element must be an immediate child element of the root element of the XAML production.</span></span>  
  
-   <span data-ttu-id="b86af-116">[x: Class yönergesi](../../../docs/framework/xaml-services/x-class-directive.md) üst kök öğesinde sağlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b86af-116">[x:Class Directive](../../../docs/framework/xaml-services/x-class-directive.md) must be provided on the parent root element.</span></span>  
  
-   <span data-ttu-id="b86af-117">Kod içinde yerleştirilen `x:Code` bu XAML sayfası için zaten oluşturuldu parçalı sınıf kapsamında olması için derleme tarafından kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="b86af-117">The code placed within `x:Code` will be treated by compilation to be within the scope of the partial class that is already being created for that XAML page.</span></span> <span data-ttu-id="b86af-118">Bu nedenle tanımladığınız tüm kod üyeleri veya kısmi o sınıfın değişkenleri olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b86af-118">Therefore all code you define must be members or variables of that partial class.</span></span>  
  
-   <span data-ttu-id="b86af-119">Bir sınıf parçalı sınıf içinde iç içe geçme tarafından dışında ek sınıfları tanımlayamazsınız (iç içe geçme izin verilir, ancak iç içe geçmiş sınıflar XAML'de başvurduğundan tipik değil).</span><span class="sxs-lookup"><span data-stu-id="b86af-119">You cannot define additional classes, other than by nesting a class inside the partial class (nesting is allowed, but it is not typical because nested classes cannot be referenced in XAML).</span></span> <span data-ttu-id="b86af-120">CLR ad alanları için varolan sınıfa kullanılan ad alanı dışında tanımlanmış veya eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="b86af-120">CLR namespaces other than the namespace that is used for the existing partial class cannot be defined or added to.</span></span>  
  
-   <span data-ttu-id="b86af-121">Kodu varlıkları parçalı sınıf CLR ad alanı dışında başvurular tümü tam olarak nitelenmiş olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b86af-121">References to code entities outside the partial class CLR namespace must all be fully qualified.</span></span> <span data-ttu-id="b86af-122">Bildirilen üyeleri geçersiz kılmalar kısmi sınıfı geçersiz kılınabilir üyeleri varsa, bu dile özgü geçersiz kılma anahtar sözcüğü ile belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="b86af-122">If members being declared are overrides to the partial class overridable members, this must be specified with the language-specific override keyword.</span></span> <span data-ttu-id="b86af-123">Bildirilen üyeleri varsa `x:Code` kapsam çakışan XAML dışında oluşturulan kısmi sınıfının üyeleriyle, bir şekilde derleyici çakışma raporları XAML dosyası derleme yüklemek veya olamaz.</span><span class="sxs-lookup"><span data-stu-id="b86af-123">If members declared in `x:Code` scope conflict with members of the partial class created out of the XAML, in such a way that the compiler reports the conflict, the XAML file cannot compile or load.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b86af-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b86af-124">See Also</span></span>  
 [<span data-ttu-id="b86af-125">x: Class yönergesi</span><span class="sxs-lookup"><span data-stu-id="b86af-125">x:Class Directive</span></span>](../../../docs/framework/xaml-services/x-class-directive.md)  
 [<span data-ttu-id="b86af-126">Arka plan kod ve WPF XAML</span><span class="sxs-lookup"><span data-stu-id="b86af-126">Code-Behind and XAML in WPF</span></span>](../../../docs/framework/wpf/advanced/code-behind-and-xaml-in-wpf.md)  
 [<span data-ttu-id="b86af-127">XAML genel bakış (WPF)</span><span class="sxs-lookup"><span data-stu-id="b86af-127">XAML Overview (WPF)</span></span>](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
