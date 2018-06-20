---
title: Erişilebilirlik Etki Alanı (C# Başvurusu)
ms.date: 07/20/2015
helpviewer_keywords:
- accessibility domain [C#]
ms.assetid: 8af779c1-275b-44be-a864-9edfbca71bcc
ms.openlocfilehash: 8e6af35ea41f6d062bc2b8ee771a1fac21667462
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36208413"
---
# <a name="accessibility-domain-c-reference"></a><span data-ttu-id="5e50d-102">Erişilebilirlik Etki Alanı (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="5e50d-102">Accessibility Domain (C# Reference)</span></span>
<span data-ttu-id="5e50d-103">Erişilebilirlik etki alanı üyesi hangi program bölümlerde üyesi başvurulabilir belirtir.</span><span class="sxs-lookup"><span data-stu-id="5e50d-103">The accessibility domain of a member specifies in which program sections a member can be referenced.</span></span> <span data-ttu-id="5e50d-104">Üye içinde başka bir tür geçmişse erişilebilirlik etki alanı her ikisi için de belirlenir [erişilebilirlik düzeyi](../../../csharp/language-reference/keywords/accessibility-levels.md) üye ve erişilebilirlik etki alanı hemen içeren türü.</span><span class="sxs-lookup"><span data-stu-id="5e50d-104">If the member is nested within another type, its accessibility domain is determined by both the [accessibility level](../../../csharp/language-reference/keywords/accessibility-levels.md) of the member and the accessibility domain of the immediately containing type.</span></span>  
  
 <span data-ttu-id="5e50d-105">Erişilebilirlik etki alanı en üst düzey bir türde en az içinde bildirilen projesinin program metindir.</span><span class="sxs-lookup"><span data-stu-id="5e50d-105">The accessibility domain of a top-level type is at least the program text of the project that it is declared in.</span></span> <span data-ttu-id="5e50d-106">Diğer bir deyişle, etki alanı tüm bu projenin kaynak dosyalarını içerir.</span><span class="sxs-lookup"><span data-stu-id="5e50d-106">That is, the domain includes all of the source files of this project.</span></span> <span data-ttu-id="5e50d-107">Erişilebilirlik etki alanı iç içe bir türde en az hangi bildirilmiş türü program metindir.</span><span class="sxs-lookup"><span data-stu-id="5e50d-107">The accessibility domain of a nested type is at least the program text of the type in which it is declared.</span></span> <span data-ttu-id="5e50d-108">Diğer bir deyişle, tüm iç içe geçmiş türler içeren türü gövdesi etki alanıdır.</span><span class="sxs-lookup"><span data-stu-id="5e50d-108">That is, the domain is the type body, which includes all nested types.</span></span> <span data-ttu-id="5e50d-109">Erişilebilirlik etki alanı iç içe geçmiş tür hiçbir zaman, kapsayan tür aşıyor.</span><span class="sxs-lookup"><span data-stu-id="5e50d-109">The accessibility domain of a nested type never exceeds that of the containing type.</span></span> <span data-ttu-id="5e50d-110">Bu kavram aşağıdaki örnekte gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="5e50d-110">These concepts are demonstrated in the following example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5e50d-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="5e50d-111">Example</span></span>  
 <span data-ttu-id="5e50d-112">Bu örnek bir üst düzey türünü içeren `T1`ve iki iç içe geçmiş sınıflar `M1` ve `M2`.</span><span class="sxs-lookup"><span data-stu-id="5e50d-112">This example contains a top-level type, `T1`, and two nested classes, `M1` and `M2`.</span></span> <span data-ttu-id="5e50d-113">Sınıfları farklı bildirilen eriþebilirlik sahip alanlar içeriyor.</span><span class="sxs-lookup"><span data-stu-id="5e50d-113">The classes contain fields that have different declared accessibilities.</span></span> <span data-ttu-id="5e50d-114">İçinde `Main` yöntemi, bir açıklamayı izleyen her üyesinin erişilebilirlik etki alanı belirtmek için her bir deyimi.</span><span class="sxs-lookup"><span data-stu-id="5e50d-114">In the `Main` method, a comment follows each statement to indicate the accessibility domain of each member.</span></span> <span data-ttu-id="5e50d-115">Erişilemez üyeleri başvurmak için deneyin deyimleri kılınmıştır dikkat edin. Erişilemez bir üye başvurarak kaynaklanan derleyici hataları görmek istiyorsanız, bir açıklama aynı anda kaldırın.</span><span class="sxs-lookup"><span data-stu-id="5e50d-115">Notice that the statements that try to reference the inaccessible members are commented out. If you want to see the compiler errors caused by referencing an inaccessible member, remove the comments one at a time.</span></span>  
  
[!code-csharp[csrefKeywordsModifiers#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#4)]
  
## <a name="c-language-specification"></a><span data-ttu-id="5e50d-116">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="5e50d-116">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="5e50d-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5e50d-117">See Also</span></span>  
 [<span data-ttu-id="5e50d-118">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="5e50d-118">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="5e50d-119">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="5e50d-119">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="5e50d-120">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="5e50d-120">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="5e50d-121">Erişim Değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="5e50d-121">Access Modifiers</span></span>](../../../csharp/language-reference/keywords/access-modifiers.md)  
 [<span data-ttu-id="5e50d-122">Erişilebilirlik Düzeyleri</span><span class="sxs-lookup"><span data-stu-id="5e50d-122">Accessibility Levels</span></span>](../../../csharp/language-reference/keywords/accessibility-levels.md)  
 [<span data-ttu-id="5e50d-123">Erişilebilirlik Düzeylerinin Kullanılmasındaki Kısıtlamalar</span><span class="sxs-lookup"><span data-stu-id="5e50d-123">Restrictions on Using Accessibility Levels</span></span>](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md)  
 [<span data-ttu-id="5e50d-124">Erişim Değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="5e50d-124">Access Modifiers</span></span>](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
 [<span data-ttu-id="5e50d-125">public</span><span class="sxs-lookup"><span data-stu-id="5e50d-125">public</span></span>](../../../csharp/language-reference/keywords/public.md)  
 [<span data-ttu-id="5e50d-126">private</span><span class="sxs-lookup"><span data-stu-id="5e50d-126">private</span></span>](../../../csharp/language-reference/keywords/private.md)  
 [<span data-ttu-id="5e50d-127">protected</span><span class="sxs-lookup"><span data-stu-id="5e50d-127">protected</span></span>](../../../csharp/language-reference/keywords/protected.md)  
 [<span data-ttu-id="5e50d-128">internal</span><span class="sxs-lookup"><span data-stu-id="5e50d-128">internal</span></span>](../../../csharp/language-reference/keywords/internal.md)
