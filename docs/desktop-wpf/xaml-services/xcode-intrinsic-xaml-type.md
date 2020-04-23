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
ms.openlocfilehash: 4da72ed630c1df001e3fd6c7e55f866b94c4d9b1
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071558"
---
# <a name="xcode-intrinsic-xaml-type"></a><span data-ttu-id="422ba-102">x:Code İç XAML Türü</span><span class="sxs-lookup"><span data-stu-id="422ba-102">x:Code Intrinsic XAML Type</span></span>
<span data-ttu-id="422ba-103">Kodun XAML üretimi ne rendesi içine yerleştirilmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="422ba-103">Allows placement of code within a XAML production.</span></span> <span data-ttu-id="422ba-104">Bu tür kod, XAML'yi derleyen herhangi bir XAML işlemci uygulaması tarafından derlenebilir veya daha sonraki kullanımlar için XAML üretiminde bırakılabilir.</span><span class="sxs-lookup"><span data-stu-id="422ba-104">Such code can either be compiled by any XAML processor implementation that compiles XAML, or left in the XAML production for later uses such as interpretation by a runtime.</span></span>

## <a name="xaml-object-element-usage"></a><span data-ttu-id="422ba-105">XAML Nesne Öğesi Kullanımı</span><span class="sxs-lookup"><span data-stu-id="422ba-105">XAML Object Element Usage</span></span>

```xaml
<x:Code>
   // code instructions, usually enclosed by CDATA...
</x:Code>
```

## <a name="remarks"></a><span data-ttu-id="422ba-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="422ba-106">Remarks</span></span>

<span data-ttu-id="422ba-107">`x:Code` XAML yönerge öğesi içindeki kod, yine de genel XML ad alanı ve sağlanan XAML ad alanları içinde yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="422ba-107">The code within the `x:Code` XAML directive element is still interpreted within the general XML namespace and the XAML namespaces provided.</span></span> <span data-ttu-id="422ba-108">Bu nedenle, genellikle bir `x:Code` `CDATA` segment içinde kullanılan kodu içine almak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="422ba-108">Therefore, it is usually necessary to enclose the code used for `x:Code` inside a `CDATA` segment.</span></span>

<span data-ttu-id="422ba-109">`x:Code`bir XAML üretiminin olası tüm dağıtım mekanizmaları için izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="422ba-109">`x:Code` is not permitted for all possible deployment mechanisms of a XAML production.</span></span> <span data-ttu-id="422ba-110">Belirli çerçevelerde (örneğin WPF) kod derlenmelidir.</span><span class="sxs-lookup"><span data-stu-id="422ba-110">In specific frameworks (for example WPF) the code must be compiled.</span></span> <span data-ttu-id="422ba-111">Diğer çerçevelerde, `x:Code` kullanıma genellikle izin verilemeyebilir.</span><span class="sxs-lookup"><span data-stu-id="422ba-111">In other frameworks, `x:Code` usage might be generally disallowed.</span></span>

<span data-ttu-id="422ba-112">Yönetilen `x:Code` içeriğe izin veren çerçeveler için, içerik `x:Code` için kullanılacak doğru dil derleyicisi, uygulamayı derlemek için kullanılan içeren projenin ayarları ve hedefleri tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="422ba-112">For frameworks that permit managed `x:Code` content, the correct language compiler to use for `x:Code` content is determined by settings and targets of the containing project that is used to compile the application.</span></span>

## <a name="wpf-usage-notes"></a><span data-ttu-id="422ba-113">WPF Kullanım Notları</span><span class="sxs-lookup"><span data-stu-id="422ba-113">WPF Usage Notes</span></span>

<span data-ttu-id="422ba-114">WPF `x:Code` için bildirilen kodun birkaç önemli sınırlaması vardır:</span><span class="sxs-lookup"><span data-stu-id="422ba-114">Code declared within `x:Code` for WPF has several notable limitations:</span></span>

- <span data-ttu-id="422ba-115">Yönerge öğesi XAML `x:Code` üretiminin kök elemanının hemen bir alt öğesi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="422ba-115">The `x:Code` directive element must be an immediate child element of the root element of the XAML production.</span></span>

- <span data-ttu-id="422ba-116">[x:Sınıf Yönergesi](xclass-directive.md) ana kök öğesi üzerinde sağlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="422ba-116">[x:Class Directive](xclass-directive.md) must be provided on the parent root element.</span></span>

- <span data-ttu-id="422ba-117">İçe `x:Code` yerleştirilen kod, o XAML sayfası için zaten oluşturulmakta olan kısmi sınıfın kapsamı içinde olmak üzere derleme ile işlem göreceksiniz.</span><span class="sxs-lookup"><span data-stu-id="422ba-117">The code placed within `x:Code` will be treated by compilation to be within the scope of the partial class that is already being created for that XAML page.</span></span> <span data-ttu-id="422ba-118">Bu nedenle tanımladığınız tüm kod, o kısmi sınıfın üyeleri veya değişkenleri olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="422ba-118">Therefore all code you define must be members or variables of that partial class.</span></span>

- <span data-ttu-id="422ba-119">Kısmi sınıfın içinde bir sınıf iç içe geçme dışında ek sınıflar tanımlayamazsınız (iç içe geçmeizin verilir, ancak iç içe geçen sınıflar XAML'de başvurulamadığından tipik değildir).</span><span class="sxs-lookup"><span data-stu-id="422ba-119">You cannot define additional classes, other than by nesting a class inside the partial class (nesting is allowed, but it is not typical because nested classes cannot be referenced in XAML).</span></span> <span data-ttu-id="422ba-120">Varolan kısmi sınıf için kullanılan ad alanı dışındaki CLR ad alanları tanımlanamaz veya eklenemez.</span><span class="sxs-lookup"><span data-stu-id="422ba-120">CLR namespaces other than the namespace that is used for the existing partial class cannot be defined or added to.</span></span>

- <span data-ttu-id="422ba-121">Kısmi sınıf CLR ad alanı dışındaki kod varlıklarına yapılan başvuruların tümü tam olarak nitelikli olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="422ba-121">References to code entities outside the partial class CLR namespace must all be fully qualified.</span></span> <span data-ttu-id="422ba-122">Bildirilen üyeler kısmi sınıf geçersiz kılınan üyelere geçersiz kılınmışsa, bunun dile özgü geçersiz kılma anahtar sözcüğüyle belirtilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="422ba-122">If members being declared are overrides to the partial class overridable members, this must be specified with the language-specific override keyword.</span></span> <span data-ttu-id="422ba-123">`x:Code` Kapsamda bildirilen üyeler XAML dışında oluşturulan kısmi sınıfın üyeleriyle, derleyiciçleçliği bildirebilecek şekilde çakışacak şekilde çakışırsa, XAML dosyası derleyemez veya yüklenemez.</span><span class="sxs-lookup"><span data-stu-id="422ba-123">If members declared in `x:Code` scope conflict with members of the partial class created out of the XAML, in such a way that the compiler reports the conflict, the XAML file cannot compile or load.</span></span>

## <a name="see-also"></a><span data-ttu-id="422ba-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="422ba-124">See also</span></span>

- [<span data-ttu-id="422ba-125">x:Class Yönergesi</span><span class="sxs-lookup"><span data-stu-id="422ba-125">x:Class Directive</span></span>](xclass-directive.md)
- [<span data-ttu-id="422ba-126">Arka Plan Kod ve WPF İçindeki XAML</span><span class="sxs-lookup"><span data-stu-id="422ba-126">Code-Behind and XAML in WPF</span></span>](../../framework/wpf/advanced/code-behind-and-xaml-in-wpf.md)
- [<span data-ttu-id="422ba-127">XAML'ye Genel Bakış (WPF)</span><span class="sxs-lookup"><span data-stu-id="422ba-127">XAML Overview (WPF)</span></span>](../fundamentals/xaml.md)
