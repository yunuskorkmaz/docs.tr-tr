---
title: Erişilebilirlik etki alanı C# başvurusu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- accessibility domain [C#]
ms.assetid: 8af779c1-275b-44be-a864-9edfbca71bcc
ms.openlocfilehash: 814aa8d3965674abe8bdb60b738cbeff93701ceb
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606130"
---
# <a name="accessibility-domain-c-reference"></a><span data-ttu-id="05860-102">Erişilebilirlik Etki Alanı (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="05860-102">Accessibility Domain (C# Reference)</span></span>
<span data-ttu-id="05860-103">Üyenin erişilebilirlik etki alanı bir üyenin hangi program bölümlerine başvurduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="05860-103">The accessibility domain of a member specifies in which program sections a member can be referenced.</span></span> <span data-ttu-id="05860-104">Üye başka bir tür içinde iç içe ise, erişilebilirlik etki alanı hem üyenin [Erişilebilirlik düzeyine](./accessibility-levels.md) hem de hemen kapsayan türdeki erişilebilirlik etki alanına göre belirlenir.</span><span class="sxs-lookup"><span data-stu-id="05860-104">If the member is nested within another type, its accessibility domain is determined by both the [accessibility level](./accessibility-levels.md) of the member and the accessibility domain of the immediately containing type.</span></span>  
  
 <span data-ttu-id="05860-105">Üst düzey bir türün erişilebilirlik etki alanı, en azından içinde bildirildiği projenin program metni.</span><span class="sxs-lookup"><span data-stu-id="05860-105">The accessibility domain of a top-level type is at least the program text of the project that it is declared in.</span></span> <span data-ttu-id="05860-106">Diğer bir deyişle, etki alanı bu projenin tüm kaynak dosyalarını içerir.</span><span class="sxs-lookup"><span data-stu-id="05860-106">That is, the domain includes all of the source files of this project.</span></span> <span data-ttu-id="05860-107">İç içe bir türün erişilebilirlik etki alanı, bildirildiği türün en az program metniyle.</span><span class="sxs-lookup"><span data-stu-id="05860-107">The accessibility domain of a nested type is at least the program text of the type in which it is declared.</span></span> <span data-ttu-id="05860-108">Diğer bir deyişle, etki alanı tüm iç içe geçmiş türleri içeren tür gövdesidir.</span><span class="sxs-lookup"><span data-stu-id="05860-108">That is, the domain is the type body, which includes all nested types.</span></span> <span data-ttu-id="05860-109">İç içe bir türün erişilebilirlik etki alanı, kendisini kapsayan türden hiçbir şekilde aşamaz.</span><span class="sxs-lookup"><span data-stu-id="05860-109">The accessibility domain of a nested type never exceeds that of the containing type.</span></span> <span data-ttu-id="05860-110">Bu kavramlar aşağıdaki örnekte gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="05860-110">These concepts are demonstrated in the following example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="05860-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="05860-111">Example</span></span>  
 <span data-ttu-id="05860-112">Bu örnek, en üst düzey bir tür, `T1`ve iki iç içe geçmiş `M1` sınıf `M2`içerir.</span><span class="sxs-lookup"><span data-stu-id="05860-112">This example contains a top-level type, `T1`, and two nested classes, `M1` and `M2`.</span></span> <span data-ttu-id="05860-113">Sınıflar, farklı tanımlanmış erişilebilir alanlara sahip alanlar içerir.</span><span class="sxs-lookup"><span data-stu-id="05860-113">The classes contain fields that have different declared accessibilities.</span></span> <span data-ttu-id="05860-114">`Main` Yönteminde, her üyenin erişilebilirlik etki alanını göstermek için her deyimin bir açıklaması.</span><span class="sxs-lookup"><span data-stu-id="05860-114">In the `Main` method, a comment follows each statement to indicate the accessibility domain of each member.</span></span> <span data-ttu-id="05860-115">Erişilemeyen üyelere başvuruda bulunan deyimlerin açıklama olarak oluşturulduğuna dikkat edin. Erişilemeyen bir üyeye başvuruda bulunarak oluşan derleyici hatalarını görmek isterseniz, açıklamaları tek seferde kaldırın.</span><span class="sxs-lookup"><span data-stu-id="05860-115">Notice that the statements that try to reference the inaccessible members are commented out. If you want to see the compiler errors caused by referencing an inaccessible member, remove the comments one at a time.</span></span>  
  
[!code-csharp[csrefKeywordsModifiers#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#4)]
  
## <a name="c-language-specification"></a><span data-ttu-id="05860-116">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="05860-116">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="05860-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="05860-117">See also</span></span>

- [<span data-ttu-id="05860-118">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="05860-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="05860-119">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="05860-119">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="05860-120">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="05860-120">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="05860-121">Erişim Değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="05860-121">Access Modifiers</span></span>](./access-modifiers.md)
- [<span data-ttu-id="05860-122">Erişilebilirlik Düzeyleri</span><span class="sxs-lookup"><span data-stu-id="05860-122">Accessibility Levels</span></span>](./accessibility-levels.md)
- [<span data-ttu-id="05860-123">Erişilebilirlik Düzeylerinin Kullanılmasındaki Kısıtlamalar</span><span class="sxs-lookup"><span data-stu-id="05860-123">Restrictions on Using Accessibility Levels</span></span>](./restrictions-on-using-accessibility-levels.md)
- [<span data-ttu-id="05860-124">Erişim Değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="05860-124">Access Modifiers</span></span>](../../programming-guide/classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="05860-125">public</span><span class="sxs-lookup"><span data-stu-id="05860-125">public</span></span>](./public.md)
- [<span data-ttu-id="05860-126">private</span><span class="sxs-lookup"><span data-stu-id="05860-126">private</span></span>](./private.md)
- [<span data-ttu-id="05860-127">protected</span><span class="sxs-lookup"><span data-stu-id="05860-127">protected</span></span>](./protected.md)
- [<span data-ttu-id="05860-128">internal</span><span class="sxs-lookup"><span data-stu-id="05860-128">internal</span></span>](./internal.md)
