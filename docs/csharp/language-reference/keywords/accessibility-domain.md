---
description: Erişilebilirlik etki alanı-C# başvurusu
title: Erişilebilirlik etki alanı-C# başvurusu
ms.date: 07/20/2015
helpviewer_keywords:
- accessibility domain [C#]
ms.assetid: 8af779c1-275b-44be-a864-9edfbca71bcc
ms.openlocfilehash: 2cfc4cc72a79b33276b7d822a2b31eb518dcf784
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89127067"
---
# <a name="accessibility-domain-c-reference"></a><span data-ttu-id="d1323-103">Erişilebilirlik Etki Alanı (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="d1323-103">Accessibility Domain (C# Reference)</span></span>
<span data-ttu-id="d1323-104">Üyenin erişilebilirlik etki alanı bir üyenin hangi program bölümlerine başvurduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="d1323-104">The accessibility domain of a member specifies in which program sections a member can be referenced.</span></span> <span data-ttu-id="d1323-105">Üye başka bir tür içinde iç içe ise, erişilebilirlik etki alanı hem üyenin [Erişilebilirlik düzeyine](./accessibility-levels.md) hem de hemen kapsayan türdeki erişilebilirlik etki alanına göre belirlenir.</span><span class="sxs-lookup"><span data-stu-id="d1323-105">If the member is nested within another type, its accessibility domain is determined by both the [accessibility level](./accessibility-levels.md) of the member and the accessibility domain of the immediately containing type.</span></span>  
  
 <span data-ttu-id="d1323-106">Üst düzey bir türün erişilebilirlik etki alanı, en azından içinde bildirildiği projenin program metni.</span><span class="sxs-lookup"><span data-stu-id="d1323-106">The accessibility domain of a top-level type is at least the program text of the project that it is declared in.</span></span> <span data-ttu-id="d1323-107">Diğer bir deyişle, etki alanı bu projenin tüm kaynak dosyalarını içerir.</span><span class="sxs-lookup"><span data-stu-id="d1323-107">That is, the domain includes all of the source files of this project.</span></span> <span data-ttu-id="d1323-108">İç içe bir türün erişilebilirlik etki alanı, bildirildiği türün en az program metniyle.</span><span class="sxs-lookup"><span data-stu-id="d1323-108">The accessibility domain of a nested type is at least the program text of the type in which it is declared.</span></span> <span data-ttu-id="d1323-109">Diğer bir deyişle, etki alanı tüm iç içe geçmiş türleri içeren tür gövdesidir.</span><span class="sxs-lookup"><span data-stu-id="d1323-109">That is, the domain is the type body, which includes all nested types.</span></span> <span data-ttu-id="d1323-110">İç içe bir türün erişilebilirlik etki alanı, kendisini kapsayan türden hiçbir şekilde aşamaz.</span><span class="sxs-lookup"><span data-stu-id="d1323-110">The accessibility domain of a nested type never exceeds that of the containing type.</span></span> <span data-ttu-id="d1323-111">Bu kavramlar aşağıdaki örnekte gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="d1323-111">These concepts are demonstrated in the following example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d1323-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="d1323-112">Example</span></span>  
 <span data-ttu-id="d1323-113">Bu örnek, en üst düzey bir tür, ve `T1` iki iç içe geçmiş sınıf `M1` içerir `M2` .</span><span class="sxs-lookup"><span data-stu-id="d1323-113">This example contains a top-level type, `T1`, and two nested classes, `M1` and `M2`.</span></span> <span data-ttu-id="d1323-114">Sınıflar, farklı tanımlanmış erişilebilir alanlara sahip alanlar içerir.</span><span class="sxs-lookup"><span data-stu-id="d1323-114">The classes contain fields that have different declared accessibilities.</span></span> <span data-ttu-id="d1323-115">`Main`Yönteminde, her üyenin erişilebilirlik etki alanını göstermek için her deyimin bir açıklaması.</span><span class="sxs-lookup"><span data-stu-id="d1323-115">In the `Main` method, a comment follows each statement to indicate the accessibility domain of each member.</span></span> <span data-ttu-id="d1323-116">Erişilemeyen üyelere başvuruda bulunan deyimlerin açıklama olarak oluşturulduğuna dikkat edin. Erişilemeyen bir üyeye başvuruda bulunarak oluşan derleyici hatalarını görmek isterseniz, açıklamaları tek seferde kaldırın.</span><span class="sxs-lookup"><span data-stu-id="d1323-116">Notice that the statements that try to reference the inaccessible members are commented out. If you want to see the compiler errors caused by referencing an inaccessible member, remove the comments one at a time.</span></span>  
  
[!code-csharp[csrefKeywordsModifiers#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#4)]
  
## <a name="c-language-specification"></a><span data-ttu-id="d1323-117">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="d1323-117">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d1323-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d1323-118">See also</span></span>

- [<span data-ttu-id="d1323-119">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="d1323-119">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="d1323-120">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="d1323-120">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="d1323-121">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="d1323-121">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="d1323-122">Erişim Değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="d1323-122">Access Modifiers</span></span>](./access-modifiers.md)
- [<span data-ttu-id="d1323-123">Erişilebilirlik Düzeyleri</span><span class="sxs-lookup"><span data-stu-id="d1323-123">Accessibility Levels</span></span>](./accessibility-levels.md)
- [<span data-ttu-id="d1323-124">Erişilebilirlik Düzeylerinin Kullanılmasındaki Kısıtlamalar</span><span class="sxs-lookup"><span data-stu-id="d1323-124">Restrictions on Using Accessibility Levels</span></span>](./restrictions-on-using-accessibility-levels.md)
- [<span data-ttu-id="d1323-125">Erişim Değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="d1323-125">Access Modifiers</span></span>](../../programming-guide/classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="d1323-126">genel</span><span class="sxs-lookup"><span data-stu-id="d1323-126">public</span></span>](./public.md)
- [<span data-ttu-id="d1323-127">private</span><span class="sxs-lookup"><span data-stu-id="d1323-127">private</span></span>](./private.md)
- [<span data-ttu-id="d1323-128">protected</span><span class="sxs-lookup"><span data-stu-id="d1323-128">protected</span></span>](./protected.md)
- [<span data-ttu-id="d1323-129">internal</span><span class="sxs-lookup"><span data-stu-id="d1323-129">internal</span></span>](./internal.md)
