---
title: Erişilebilirlik Etki Alanı - C# Referans
ms.date: 07/20/2015
helpviewer_keywords:
- accessibility domain [C#]
ms.assetid: 8af779c1-275b-44be-a864-9edfbca71bcc
ms.openlocfilehash: 4a4319b03f3e0d7f9ec721e611b78c124a8a8ee5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713829"
---
# <a name="accessibility-domain-c-reference"></a><span data-ttu-id="62e0d-102">Erişilebilirlik Etki Alanı (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="62e0d-102">Accessibility Domain (C# Reference)</span></span>
<span data-ttu-id="62e0d-103">Bir üyenin erişilebilirlik etki alanı, bir üyenin hangi program bölümlerine başvurulabileceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="62e0d-103">The accessibility domain of a member specifies in which program sections a member can be referenced.</span></span> <span data-ttu-id="62e0d-104">Üye başka bir türde iç içe yse, erişilebilirlik etki alanı hem üyenin [erişilebilirlik düzeyine](./accessibility-levels.md) hem de hemen içeren türün erişilebilirlik etki alanına göre belirlenir.</span><span class="sxs-lookup"><span data-stu-id="62e0d-104">If the member is nested within another type, its accessibility domain is determined by both the [accessibility level](./accessibility-levels.md) of the member and the accessibility domain of the immediately containing type.</span></span>  
  
 <span data-ttu-id="62e0d-105">Üst düzey bir türün erişilebilirlik etki alanı, en azından beyan edildiği projenin program metnidir.</span><span class="sxs-lookup"><span data-stu-id="62e0d-105">The accessibility domain of a top-level type is at least the program text of the project that it is declared in.</span></span> <span data-ttu-id="62e0d-106">Diğer bir zamanda, etki alanı bu projenin tüm kaynak dosyalarını içerir.</span><span class="sxs-lookup"><span data-stu-id="62e0d-106">That is, the domain includes all of the source files of this project.</span></span> <span data-ttu-id="62e0d-107">İç içe geçmiş bir türün erişilebilirlik etki alanı, en azından beyan edildiği türün program metnidir.</span><span class="sxs-lookup"><span data-stu-id="62e0d-107">The accessibility domain of a nested type is at least the program text of the type in which it is declared.</span></span> <span data-ttu-id="62e0d-108">Diğer bir zamanda, etki alanı, iç içe olan tüm türleri içeren tür gövdesidir.</span><span class="sxs-lookup"><span data-stu-id="62e0d-108">That is, the domain is the type body, which includes all nested types.</span></span> <span data-ttu-id="62e0d-109">İç içe bir türün erişilebilirlik etki alanı, içeren türün etki alanını asla aşmaz.</span><span class="sxs-lookup"><span data-stu-id="62e0d-109">The accessibility domain of a nested type never exceeds that of the containing type.</span></span> <span data-ttu-id="62e0d-110">Bu kavramlar aşağıdaki örnekte gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="62e0d-110">These concepts are demonstrated in the following example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="62e0d-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="62e0d-111">Example</span></span>  
 <span data-ttu-id="62e0d-112">Bu örnek, `T1`üst düzey bir tür ve iki `M1` `M2`iç içe sınıf ve.</span><span class="sxs-lookup"><span data-stu-id="62e0d-112">This example contains a top-level type, `T1`, and two nested classes, `M1` and `M2`.</span></span> <span data-ttu-id="62e0d-113">Sınıflar, farklı bildirilen erişilebilirliklere sahip alanlar içerir.</span><span class="sxs-lookup"><span data-stu-id="62e0d-113">The classes contain fields that have different declared accessibilities.</span></span> <span data-ttu-id="62e0d-114">`Main` Yöntemde, her üyenin erişilebilirlik etki alanını belirtmek için bir açıklama her deyimi izler.</span><span class="sxs-lookup"><span data-stu-id="62e0d-114">In the `Main` method, a comment follows each statement to indicate the accessibility domain of each member.</span></span> <span data-ttu-id="62e0d-115">Erişilemeyen üyelere başvuru yapmaya çalışan ifadelerin yorumlanabildiğine dikkat edin. Erişilemeyen bir üyeye başvurmaktan kaynaklanan derleyici hatalarını görmek istiyorsanız, yorumları teker teker kaldırın.</span><span class="sxs-lookup"><span data-stu-id="62e0d-115">Notice that the statements that try to reference the inaccessible members are commented out. If you want to see the compiler errors caused by referencing an inaccessible member, remove the comments one at a time.</span></span>  
  
[!code-csharp[csrefKeywordsModifiers#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#4)]
  
## <a name="c-language-specification"></a><span data-ttu-id="62e0d-116">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="62e0d-116">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="62e0d-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="62e0d-117">See also</span></span>

- [<span data-ttu-id="62e0d-118">C# Referans</span><span class="sxs-lookup"><span data-stu-id="62e0d-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="62e0d-119">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="62e0d-119">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="62e0d-120">C# Anahtar Kelimeler</span><span class="sxs-lookup"><span data-stu-id="62e0d-120">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="62e0d-121">Erişim Değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="62e0d-121">Access Modifiers</span></span>](./access-modifiers.md)
- [<span data-ttu-id="62e0d-122">Erişilebilirlik Düzeyleri</span><span class="sxs-lookup"><span data-stu-id="62e0d-122">Accessibility Levels</span></span>](./accessibility-levels.md)
- [<span data-ttu-id="62e0d-123">Erişilebilirlik Düzeylerinin Kullanılmasındaki Kısıtlamalar</span><span class="sxs-lookup"><span data-stu-id="62e0d-123">Restrictions on Using Accessibility Levels</span></span>](./restrictions-on-using-accessibility-levels.md)
- [<span data-ttu-id="62e0d-124">Erişim Değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="62e0d-124">Access Modifiers</span></span>](../../programming-guide/classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="62e0d-125">Kamu</span><span class="sxs-lookup"><span data-stu-id="62e0d-125">public</span></span>](./public.md)
- [<span data-ttu-id="62e0d-126">Özel</span><span class="sxs-lookup"><span data-stu-id="62e0d-126">private</span></span>](./private.md)
- [<span data-ttu-id="62e0d-127">protected</span><span class="sxs-lookup"><span data-stu-id="62e0d-127">protected</span></span>](./protected.md)
- [<span data-ttu-id="62e0d-128">Iç</span><span class="sxs-lookup"><span data-stu-id="62e0d-128">internal</span></span>](./internal.md)
