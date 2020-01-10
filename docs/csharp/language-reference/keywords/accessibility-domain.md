---
title: Erişilebilirlik etki alanı C# başvurusu
ms.date: 07/20/2015
helpviewer_keywords:
- accessibility domain [C#]
ms.assetid: 8af779c1-275b-44be-a864-9edfbca71bcc
ms.openlocfilehash: 4a4319b03f3e0d7f9ec721e611b78c124a8a8ee5
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713829"
---
# <a name="accessibility-domain-c-reference"></a><span data-ttu-id="b0a65-102">Erişilebilirlik Etki Alanı (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="b0a65-102">Accessibility Domain (C# Reference)</span></span>
<span data-ttu-id="b0a65-103">Üyenin erişilebilirlik etki alanı bir üyenin hangi program bölümlerine başvurduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="b0a65-103">The accessibility domain of a member specifies in which program sections a member can be referenced.</span></span> <span data-ttu-id="b0a65-104">Üye başka bir tür içinde iç içe ise, erişilebilirlik etki alanı hem üyenin [Erişilebilirlik düzeyine](./accessibility-levels.md) hem de hemen kapsayan türdeki erişilebilirlik etki alanına göre belirlenir.</span><span class="sxs-lookup"><span data-stu-id="b0a65-104">If the member is nested within another type, its accessibility domain is determined by both the [accessibility level](./accessibility-levels.md) of the member and the accessibility domain of the immediately containing type.</span></span>  
  
 <span data-ttu-id="b0a65-105">Üst düzey bir türün erişilebilirlik etki alanı, en azından içinde bildirildiği projenin program metni.</span><span class="sxs-lookup"><span data-stu-id="b0a65-105">The accessibility domain of a top-level type is at least the program text of the project that it is declared in.</span></span> <span data-ttu-id="b0a65-106">Diğer bir deyişle, etki alanı bu projenin tüm kaynak dosyalarını içerir.</span><span class="sxs-lookup"><span data-stu-id="b0a65-106">That is, the domain includes all of the source files of this project.</span></span> <span data-ttu-id="b0a65-107">İç içe bir türün erişilebilirlik etki alanı, bildirildiği türün en az program metniyle.</span><span class="sxs-lookup"><span data-stu-id="b0a65-107">The accessibility domain of a nested type is at least the program text of the type in which it is declared.</span></span> <span data-ttu-id="b0a65-108">Diğer bir deyişle, etki alanı tüm iç içe geçmiş türleri içeren tür gövdesidir.</span><span class="sxs-lookup"><span data-stu-id="b0a65-108">That is, the domain is the type body, which includes all nested types.</span></span> <span data-ttu-id="b0a65-109">İç içe bir türün erişilebilirlik etki alanı, kendisini kapsayan türden hiçbir şekilde aşamaz.</span><span class="sxs-lookup"><span data-stu-id="b0a65-109">The accessibility domain of a nested type never exceeds that of the containing type.</span></span> <span data-ttu-id="b0a65-110">Bu kavramlar aşağıdaki örnekte gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="b0a65-110">These concepts are demonstrated in the following example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b0a65-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="b0a65-111">Example</span></span>  
 <span data-ttu-id="b0a65-112">Bu örnek, en üst düzey bir tür, `T1`ve iki iç içe sınıf `M1` ve `M2`içerir.</span><span class="sxs-lookup"><span data-stu-id="b0a65-112">This example contains a top-level type, `T1`, and two nested classes, `M1` and `M2`.</span></span> <span data-ttu-id="b0a65-113">Sınıflar, farklı tanımlanmış erişilebilir alanlara sahip alanlar içerir.</span><span class="sxs-lookup"><span data-stu-id="b0a65-113">The classes contain fields that have different declared accessibilities.</span></span> <span data-ttu-id="b0a65-114">`Main` yönteminde, her üyenin erişilebilirlik etki alanını göstermek için her bir ifadeye bir yorum yapılır.</span><span class="sxs-lookup"><span data-stu-id="b0a65-114">In the `Main` method, a comment follows each statement to indicate the accessibility domain of each member.</span></span> <span data-ttu-id="b0a65-115">Erişilemeyen üyelere başvuruda bulunan deyimlerin açıklama olarak oluşturulduğuna dikkat edin. Erişilemeyen bir üyeye başvuruda bulunarak oluşan derleyici hatalarını görmek isterseniz, açıklamaları tek seferde kaldırın.</span><span class="sxs-lookup"><span data-stu-id="b0a65-115">Notice that the statements that try to reference the inaccessible members are commented out. If you want to see the compiler errors caused by referencing an inaccessible member, remove the comments one at a time.</span></span>  
  
[!code-csharp[csrefKeywordsModifiers#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#4)]
  
## <a name="c-language-specification"></a><span data-ttu-id="b0a65-116">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="b0a65-116">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b0a65-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b0a65-117">See also</span></span>

- [<span data-ttu-id="b0a65-118">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="b0a65-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="b0a65-119">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="b0a65-119">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="b0a65-120">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="b0a65-120">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="b0a65-121">Erişim Değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="b0a65-121">Access Modifiers</span></span>](./access-modifiers.md)
- [<span data-ttu-id="b0a65-122">Erişilebilirlik Düzeyleri</span><span class="sxs-lookup"><span data-stu-id="b0a65-122">Accessibility Levels</span></span>](./accessibility-levels.md)
- [<span data-ttu-id="b0a65-123">Erişilebilirlik Düzeylerinin Kullanılmasındaki Kısıtlamalar</span><span class="sxs-lookup"><span data-stu-id="b0a65-123">Restrictions on Using Accessibility Levels</span></span>](./restrictions-on-using-accessibility-levels.md)
- [<span data-ttu-id="b0a65-124">Erişim Değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="b0a65-124">Access Modifiers</span></span>](../../programming-guide/classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="b0a65-125">public</span><span class="sxs-lookup"><span data-stu-id="b0a65-125">public</span></span>](./public.md)
- [<span data-ttu-id="b0a65-126">private</span><span class="sxs-lookup"><span data-stu-id="b0a65-126">private</span></span>](./private.md)
- [<span data-ttu-id="b0a65-127">protected</span><span class="sxs-lookup"><span data-stu-id="b0a65-127">protected</span></span>](./protected.md)
- [<span data-ttu-id="b0a65-128">internal</span><span class="sxs-lookup"><span data-stu-id="b0a65-128">internal</span></span>](./internal.md)
