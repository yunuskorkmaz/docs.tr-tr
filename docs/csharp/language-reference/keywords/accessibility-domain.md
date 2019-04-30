---
title: Erişilebilirlik etki alanı - C# başvurusu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- accessibility domain [C#]
ms.assetid: 8af779c1-275b-44be-a864-9edfbca71bcc
ms.openlocfilehash: 529d256a553c4000c77bcd5096db1a4d943874ff
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61662185"
---
# <a name="accessibility-domain-c-reference"></a><span data-ttu-id="57bc5-102">Erişilebilirlik Etki Alanı (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="57bc5-102">Accessibility Domain (C# Reference)</span></span>
<span data-ttu-id="57bc5-103">Hangi program bölümlerde üyesi başvurulabilir üyesi erişilebilirlik etki alanını belirtir.</span><span class="sxs-lookup"><span data-stu-id="57bc5-103">The accessibility domain of a member specifies in which program sections a member can be referenced.</span></span> <span data-ttu-id="57bc5-104">Başka bir türde üye içe yerleştirilmişse, onun erişilebilirlik etki alanı tarafından belirlenir [erişilebilirlik düzeyi](../../../csharp/language-reference/keywords/accessibility-levels.md) üyesi ve hemen içeren türün erişilebilirlik etki alanı.</span><span class="sxs-lookup"><span data-stu-id="57bc5-104">If the member is nested within another type, its accessibility domain is determined by both the [accessibility level](../../../csharp/language-reference/keywords/accessibility-levels.md) of the member and the accessibility domain of the immediately containing type.</span></span>  
  
 <span data-ttu-id="57bc5-105">Üst düzey tür erişilebilirlik etki alanı en az içinde bildirildiği proje öğesinin program metnidir.</span><span class="sxs-lookup"><span data-stu-id="57bc5-105">The accessibility domain of a top-level type is at least the program text of the project that it is declared in.</span></span> <span data-ttu-id="57bc5-106">Diğer bir deyişle, etki alanı, tüm bu projenin kaynak dosyaları içerir.</span><span class="sxs-lookup"><span data-stu-id="57bc5-106">That is, the domain includes all of the source files of this project.</span></span> <span data-ttu-id="57bc5-107">İç içe türün erişilebilirlik etki alanı en az tür içinde bildirildiği program metnidir.</span><span class="sxs-lookup"><span data-stu-id="57bc5-107">The accessibility domain of a nested type is at least the program text of the type in which it is declared.</span></span> <span data-ttu-id="57bc5-108">Diğer bir deyişle, tüm iç içe geçmiş türler içeren tür gövdesi etki alanıdır.</span><span class="sxs-lookup"><span data-stu-id="57bc5-108">That is, the domain is the type body, which includes all nested types.</span></span> <span data-ttu-id="57bc5-109">İç içe türün erişilebilirlik etki alanı hiçbir zaman, kapsayan türdeki aşıyor.</span><span class="sxs-lookup"><span data-stu-id="57bc5-109">The accessibility domain of a nested type never exceeds that of the containing type.</span></span> <span data-ttu-id="57bc5-110">Bu kavramlar, aşağıdaki örnekte gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="57bc5-110">These concepts are demonstrated in the following example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="57bc5-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="57bc5-111">Example</span></span>  
 <span data-ttu-id="57bc5-112">Bu örnek, bir üst düzey tür içerir `T1`ve iç içe iki sınıf `M1` ve `M2`.</span><span class="sxs-lookup"><span data-stu-id="57bc5-112">This example contains a top-level type, `T1`, and two nested classes, `M1` and `M2`.</span></span> <span data-ttu-id="57bc5-113">Sınıflar, farklı bildirilen erişilebilirlikleri alanlar içerir.</span><span class="sxs-lookup"><span data-stu-id="57bc5-113">The classes contain fields that have different declared accessibilities.</span></span> <span data-ttu-id="57bc5-114">İçinde `Main` yöntemi, bir açıklama her üyesinin erişilebilirlik etki alanı belirtmek için her deyim izler.</span><span class="sxs-lookup"><span data-stu-id="57bc5-114">In the `Main` method, a comment follows each statement to indicate the accessibility domain of each member.</span></span> <span data-ttu-id="57bc5-115">Erişilemeyen üyeler başvurmak için deneyin deyimleri satırlarıdır dikkat edin. Erişilemez bir üye başvurarak kaynaklanan derleyici hataları görmek istiyorsanız, bir kerede bir yorum kaldırın.</span><span class="sxs-lookup"><span data-stu-id="57bc5-115">Notice that the statements that try to reference the inaccessible members are commented out. If you want to see the compiler errors caused by referencing an inaccessible member, remove the comments one at a time.</span></span>  
  
[!code-csharp[csrefKeywordsModifiers#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#4)]
  
## <a name="c-language-specification"></a><span data-ttu-id="57bc5-116">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="57bc5-116">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="57bc5-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="57bc5-117">See also</span></span>

- [<span data-ttu-id="57bc5-118">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="57bc5-118">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="57bc5-119">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="57bc5-119">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="57bc5-120">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="57bc5-120">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
- [<span data-ttu-id="57bc5-121">Erişim Değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="57bc5-121">Access Modifiers</span></span>](../../../csharp/language-reference/keywords/access-modifiers.md)
- [<span data-ttu-id="57bc5-122">Erişilebilirlik Düzeyleri</span><span class="sxs-lookup"><span data-stu-id="57bc5-122">Accessibility Levels</span></span>](../../../csharp/language-reference/keywords/accessibility-levels.md)
- [<span data-ttu-id="57bc5-123">Erişilebilirlik Düzeylerinin Kullanılmasındaki Kısıtlamalar</span><span class="sxs-lookup"><span data-stu-id="57bc5-123">Restrictions on Using Accessibility Levels</span></span>](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md)
- [<span data-ttu-id="57bc5-124">Erişim Değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="57bc5-124">Access Modifiers</span></span>](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="57bc5-125">public</span><span class="sxs-lookup"><span data-stu-id="57bc5-125">public</span></span>](../../../csharp/language-reference/keywords/public.md)
- [<span data-ttu-id="57bc5-126">private</span><span class="sxs-lookup"><span data-stu-id="57bc5-126">private</span></span>](../../../csharp/language-reference/keywords/private.md)
- [<span data-ttu-id="57bc5-127">protected</span><span class="sxs-lookup"><span data-stu-id="57bc5-127">protected</span></span>](../../../csharp/language-reference/keywords/protected.md)
- [<span data-ttu-id="57bc5-128">internal</span><span class="sxs-lookup"><span data-stu-id="57bc5-128">internal</span></span>](../../../csharp/language-reference/keywords/internal.md)
