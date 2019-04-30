---
title: unchecked anahtar sözcüğü - C# başvurusu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- unchecked_CSharpKeyword
- unchecked
helpviewer_keywords:
- unchecked keyword [C#]
ms.assetid: 0c021f7c-923f-4b3d-a58f-55336f5ac27e
ms.openlocfilehash: 44301333f7a36e6b0baa6ea9e089d930bb485a45
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61660482"
---
# <a name="unchecked-c-reference"></a><span data-ttu-id="c3352-102">unchecked (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="c3352-102">unchecked (C# Reference)</span></span>

<span data-ttu-id="c3352-103">`unchecked` Anahtar sözcüğü, Tamsayı türünde aritmetik işlemler ve dönüştürmeler için taşma denetimi gizlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c3352-103">The `unchecked` keyword is used to suppress overflow-checking for integral-type arithmetic operations and conversions.</span></span>

<span data-ttu-id="c3352-104">Bir ifade hedef türün aralığı dışında bir değer veriyorsa işaretlenmemiş bir bağlamda taşma işaretlenmemiştir.</span><span class="sxs-lookup"><span data-stu-id="c3352-104">In an unchecked context, if an expression produces a value that is outside the range of the destination type, the overflow is not flagged.</span></span> <span data-ttu-id="c3352-105">Örneğin, aşağıdaki örnekte hesaplama yapıldığından bir `unchecked` blok veya ifade, bir tamsayı göz ardı edilir için sonuç çok büyük olduğunu ve `int1` -2,147,483,639 değeri atanır.</span><span class="sxs-lookup"><span data-stu-id="c3352-105">For example, because the calculation in the following example is performed in an `unchecked` block or expression, the fact that the result is too large for an integer is ignored, and `int1` is assigned the value -2,147,483,639.</span></span>

[!code-csharp[csrefKeywordsChecked#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#5)]

<span data-ttu-id="c3352-106">Varsa `unchecked` ortam kaldırılır, bir derleme hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="c3352-106">If the `unchecked` environment is removed, a compilation error occurs.</span></span> <span data-ttu-id="c3352-107">İfadenin tüm koşulları sabitleri olduğundan overflow derleme zamanında algılanabilir.</span><span class="sxs-lookup"><span data-stu-id="c3352-107">The overflow can be detected at compile time because all the terms of the expression are constants.</span></span>

<span data-ttu-id="c3352-108">Sabit olmayan terimleri içeren ifadeler, derleme zamanında varsayılan olarak işaretli ve çalışma zamanı.</span><span class="sxs-lookup"><span data-stu-id="c3352-108">Expressions that contain non-constant terms are unchecked by default at compile time and run time.</span></span> <span data-ttu-id="c3352-109">Bkz: [işaretli](checked.md) denetlenmiş bir ortamda etkinleştirme hakkında bilgi için.</span><span class="sxs-lookup"><span data-stu-id="c3352-109">See [checked](checked.md) for information about enabling a checked environment.</span></span>

<span data-ttu-id="c3352-110">Taşma sürüyor, durumlarda denetlenmeyen kod kullanımı için denetimi olduğundan, tehlike olduğu taşma performansı iyileştirebilir.</span><span class="sxs-lookup"><span data-stu-id="c3352-110">Because checking for overflow takes time, the use of unchecked code in situations where there is no danger of overflow might improve performance.</span></span> <span data-ttu-id="c3352-111">Ancak, denetlenmiş bir ortamda taşma olasılığı varsa kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c3352-111">However, if overflow is a possibility, a checked environment should be used.</span></span>

## <a name="example"></a><span data-ttu-id="c3352-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="c3352-112">Example</span></span>

<span data-ttu-id="c3352-113">Bu örnek nasıl kullanılacağını gösterir `unchecked` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="c3352-113">This sample shows how to use the `unchecked` keyword.</span></span>

[!code-csharp[csrefKeywordsChecked#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#2)]

## <a name="c-language-specification"></a><span data-ttu-id="c3352-114">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="c3352-114">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="c3352-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c3352-115">See also</span></span>

- [<span data-ttu-id="c3352-116">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="c3352-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="c3352-117">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="c3352-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="c3352-118">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="c3352-118">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="c3352-119">İşaretli ve İşaretsiz</span><span class="sxs-lookup"><span data-stu-id="c3352-119">Checked and Unchecked</span></span>](checked-and-unchecked.md)
- [<span data-ttu-id="c3352-120">checked</span><span class="sxs-lookup"><span data-stu-id="c3352-120">checked</span></span>](checked.md)