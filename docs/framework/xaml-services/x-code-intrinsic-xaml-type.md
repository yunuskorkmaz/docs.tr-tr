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
ms.openlocfilehash: 7312c59cdcddfdbda39a4a9f05788b6a021f9b75
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459590"
---
# <a name="xcode-intrinsic-xaml-type"></a><span data-ttu-id="8f60b-102">x:Code İç XAML Türü</span><span class="sxs-lookup"><span data-stu-id="8f60b-102">x:Code Intrinsic XAML Type</span></span>
<span data-ttu-id="8f60b-103">Bir XAML üretimi içindeki kodun yerleştirilmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="8f60b-103">Allows placement of code within a XAML production.</span></span> <span data-ttu-id="8f60b-104">Bu kod, XAML 'yi derlenen herhangi bir XAML işlemci uygulamasıyla veya bir çalışma zamanı tarafından yorum gibi daha sonra kullanımlar için XAML üretimde solda derlenir.</span><span class="sxs-lookup"><span data-stu-id="8f60b-104">Such code can either be compiled by any XAML processor implementation that compiles XAML, or left in the XAML production for later uses such as interpretation by a runtime.</span></span>  
  
## <a name="xaml-object-element-usage"></a><span data-ttu-id="8f60b-105">XAML Nesne Öğesi Kullanımı</span><span class="sxs-lookup"><span data-stu-id="8f60b-105">XAML Object Element Usage</span></span>  
  
```xaml  
<x:Code>  
   // code instructions, usually enclosed by CDATA...  
</x:Code>  
```  
  
## <a name="remarks"></a><span data-ttu-id="8f60b-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8f60b-106">Remarks</span></span>  
 <span data-ttu-id="8f60b-107">`x:Code` XAML yönergesi öğesi içindeki kod, hala genel XML ad alanı ve belirtilen XAML ad alanları içinde yorumlanıyor.</span><span class="sxs-lookup"><span data-stu-id="8f60b-107">The code within the `x:Code` XAML directive element is still interpreted within the general XML namespace and the XAML namespaces provided.</span></span> <span data-ttu-id="8f60b-108">Bu nedenle, genellikle `x:Code` için kullanılan kodu bir `CDATA` segmenti içine almanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="8f60b-108">Therefore, it is usually necessary to enclose the code used for `x:Code` inside a `CDATA` segment.</span></span>  
  
 <span data-ttu-id="8f60b-109">XAML üretiminin tüm olası dağıtım mekanizmaları için `x:Code` izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="8f60b-109">`x:Code` is not permitted for all possible deployment mechanisms of a XAML production.</span></span> <span data-ttu-id="8f60b-110">Belirli çerçevelerde (örneğin, WPF) kodun derlenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="8f60b-110">In specific frameworks (for example WPF) the code must be compiled.</span></span> <span data-ttu-id="8f60b-111">Diğer çerçevelerde, `x:Code` kullanım genellikle izin verilmiyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="8f60b-111">In other frameworks, `x:Code` usage might be generally disallowed.</span></span>  
  
 <span data-ttu-id="8f60b-112">Yönetilen `x:Code` içeriğine izin veren çerçeveler için, `x:Code` içerik için kullanılacak doğru dil derleyicisi, uygulamayı derlemek için kullanılan içerilen projenin ayarlarına ve hedeflerine göre belirlenir.</span><span class="sxs-lookup"><span data-stu-id="8f60b-112">For frameworks that permit managed `x:Code` content, the correct language compiler to use for `x:Code` content is determined by settings and targets of the containing project that is used to compile the application.</span></span>  
  
## <a name="wpf-usage-notes"></a><span data-ttu-id="8f60b-113">WPF kullanım notları</span><span class="sxs-lookup"><span data-stu-id="8f60b-113">WPF Usage Notes</span></span>  
 <span data-ttu-id="8f60b-114">WPF için `x:Code` içinde bildirildiği kodun çeşitli önemli sınırlamaları vardır:</span><span class="sxs-lookup"><span data-stu-id="8f60b-114">Code declared within `x:Code` for WPF has several notable limitations:</span></span>  
  
- <span data-ttu-id="8f60b-115">`x:Code` Directive öğesi XAML üretiminin kök öğesinin hemen bir alt öğesi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8f60b-115">The `x:Code` directive element must be an immediate child element of the root element of the XAML production.</span></span>  
  
- <span data-ttu-id="8f60b-116">[X:Class yönergesinin](x-class-directive.md) üst kök öğesinde sağlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="8f60b-116">[x:Class Directive](x-class-directive.md) must be provided on the parent root element.</span></span>  
  
- <span data-ttu-id="8f60b-117">`x:Code` içine yerleştirilmiş kod, derleme tarafından, bu XAML sayfası için zaten oluşturulmakta olan kısmi sınıfın kapsamı içinde olacak şekilde değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="8f60b-117">The code placed within `x:Code` will be treated by compilation to be within the scope of the partial class that is already being created for that XAML page.</span></span> <span data-ttu-id="8f60b-118">Bu nedenle, tanımladığınız tüm kodlar üye veya bu kısmi sınıfın değişkenleri olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8f60b-118">Therefore all code you define must be members or variables of that partial class.</span></span>  
  
- <span data-ttu-id="8f60b-119">Kısmi sınıfın içindeki bir sınıfı iç içe geçirerek dışında ek sınıflar tanımlayamazsınız (iç içe geçme izin verilir, ancak iç içe geçmiş sınıflara XAML 'de başvurulduğundan, bu normal değildir).</span><span class="sxs-lookup"><span data-stu-id="8f60b-119">You cannot define additional classes, other than by nesting a class inside the partial class (nesting is allowed, but it is not typical because nested classes cannot be referenced in XAML).</span></span> <span data-ttu-id="8f60b-120">Mevcut kısmi sınıf için kullanılan ad alanı dışındaki CLR ad alanları tanımlanamıyor veya öğesine eklenemiyor.</span><span class="sxs-lookup"><span data-stu-id="8f60b-120">CLR namespaces other than the namespace that is used for the existing partial class cannot be defined or added to.</span></span>  
  
- <span data-ttu-id="8f60b-121">Kısmi sınıf CLR ad alanı dışındaki kod varlıklarına yapılan başvurular tamamen tam nitelenmiş olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8f60b-121">References to code entities outside the partial class CLR namespace must all be fully qualified.</span></span> <span data-ttu-id="8f60b-122">Bildirmekte olan Üyeler kısmi sınıf geçersiz kılınabilir Üyeler için geçersiz kılındığında, bu, dile özgü geçersiz kılma anahtar sözcüğü ile belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="8f60b-122">If members being declared are overrides to the partial class overridable members, this must be specified with the language-specific override keyword.</span></span> <span data-ttu-id="8f60b-123">`x:Code` kapsamda belirtilen Üyeler XAML dışında oluşturulan kısmi sınıfın üyeleriyle çakışıyorsa, bu şekilde derleyicinin çakışmayı bildirdiği, XAML dosyası derlenemez veya yüklenemez.</span><span class="sxs-lookup"><span data-stu-id="8f60b-123">If members declared in `x:Code` scope conflict with members of the partial class created out of the XAML, in such a way that the compiler reports the conflict, the XAML file cannot compile or load.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f60b-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8f60b-124">See also</span></span>

- [<span data-ttu-id="8f60b-125">x:Class Yönergesi</span><span class="sxs-lookup"><span data-stu-id="8f60b-125">x:Class Directive</span></span>](x-class-directive.md)
- [<span data-ttu-id="8f60b-126">Arka Plan Kod ve WPF İçindeki XAML</span><span class="sxs-lookup"><span data-stu-id="8f60b-126">Code-Behind and XAML in WPF</span></span>](../wpf/advanced/code-behind-and-xaml-in-wpf.md)
- [<span data-ttu-id="8f60b-127">XAML'ye Genel Bakış (WPF)</span><span class="sxs-lookup"><span data-stu-id="8f60b-127">XAML Overview (WPF)</span></span>](../../desktop-wpf/fundamentals/xaml.md)
