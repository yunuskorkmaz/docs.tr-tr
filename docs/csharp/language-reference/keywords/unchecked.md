---
title: işaretlenmemiş anahtar kelime - C# Başvurusu
ms.date: 07/20/2015
f1_keywords:
- unchecked_CSharpKeyword
- unchecked
helpviewer_keywords:
- unchecked keyword [C#]
ms.assetid: 0c021f7c-923f-4b3d-a58f-55336f5ac27e
ms.openlocfilehash: 6dad0dfd508fb390dd0a52d1b48d70b4c5725513
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713007"
---
# <a name="unchecked-c-reference"></a><span data-ttu-id="875be-102">unchecked (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="875be-102">unchecked (C# Reference)</span></span>

<span data-ttu-id="875be-103">Anahtar `unchecked` kelime, integral türü aritmetik işlemleri ve dönüşümleri için taşma denetimini bastırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="875be-103">The `unchecked` keyword is used to suppress overflow-checking for integral-type arithmetic operations and conversions.</span></span>

<span data-ttu-id="875be-104">Denetlenmemiş bir bağlamda, bir ifade hedef türünün aralığıdışında bir değer üretirse, taşma işaretlenmez.</span><span class="sxs-lookup"><span data-stu-id="875be-104">In an unchecked context, if an expression produces a value that is outside the range of the destination type, the overflow is not flagged.</span></span> <span data-ttu-id="875be-105">Örneğin, aşağıdaki örnekteki hesaplama bir `unchecked` blok veya ifadede gerçekleştirildiği için, sonucun bir arastıcı için `int1` çok büyük olması göz ardı edilir ve -2.147.483.639 değeri atanır.</span><span class="sxs-lookup"><span data-stu-id="875be-105">For example, because the calculation in the following example is performed in an `unchecked` block or expression, the fact that the result is too large for an integer is ignored, and `int1` is assigned the value -2,147,483,639.</span></span>

[!code-csharp[csrefKeywordsChecked#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#5)]

<span data-ttu-id="875be-106">Ortam `unchecked` kaldırılırsa, bir derleme hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="875be-106">If the `unchecked` environment is removed, a compilation error occurs.</span></span> <span data-ttu-id="875be-107">İfadenin tüm terimleri sabit olduğundan, taşma derleme zamanda algılanabilir.</span><span class="sxs-lookup"><span data-stu-id="875be-107">The overflow can be detected at compile time because all the terms of the expression are constants.</span></span>

<span data-ttu-id="875be-108">Sabit olmayan terimler içeren ifadeler derleme zamanında ve çalışma zamanında varsayılan olarak işaretlenmez.</span><span class="sxs-lookup"><span data-stu-id="875be-108">Expressions that contain non-constant terms are unchecked by default at compile time and run time.</span></span> <span data-ttu-id="875be-109">[Denetlenen](checked.md) ortamı etkinleştirme hakkında bilgi olup da kontrol edilmesine bakın.</span><span class="sxs-lookup"><span data-stu-id="875be-109">See [checked](checked.md) for information about enabling a checked environment.</span></span>

<span data-ttu-id="875be-110">Taşma için denetleme zaman aldığından, taşma tehlikesi nin olmadığı durumlarda denetlenmemiş kodun kullanılması performansı artırabilir.</span><span class="sxs-lookup"><span data-stu-id="875be-110">Because checking for overflow takes time, the use of unchecked code in situations where there is no danger of overflow might improve performance.</span></span> <span data-ttu-id="875be-111">Ancak, taşma olasılığı varsa, denetlenmiş bir ortam kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="875be-111">However, if overflow is a possibility, a checked environment should be used.</span></span>

## <a name="example"></a><span data-ttu-id="875be-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="875be-112">Example</span></span>

<span data-ttu-id="875be-113">Bu örnek, anahtar `unchecked` kelimenin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="875be-113">This sample shows how to use the `unchecked` keyword.</span></span>

[!code-csharp[csrefKeywordsChecked#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#2)]

## <a name="c-language-specification"></a><span data-ttu-id="875be-114">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="875be-114">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="875be-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="875be-115">See also</span></span>

- [<span data-ttu-id="875be-116">C# Referans</span><span class="sxs-lookup"><span data-stu-id="875be-116">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="875be-117">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="875be-117">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="875be-118">C# Anahtar Kelimeler</span><span class="sxs-lookup"><span data-stu-id="875be-118">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="875be-119">Checked ve Unchecked</span><span class="sxs-lookup"><span data-stu-id="875be-119">Checked and Unchecked</span></span>](checked-and-unchecked.md)
- [<span data-ttu-id="875be-120">Kontrol</span><span class="sxs-lookup"><span data-stu-id="875be-120">checked</span></span>](checked.md)
