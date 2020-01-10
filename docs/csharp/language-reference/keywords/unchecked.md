---
title: unchecked anahtar sözcüğü C# -başvuru
ms.date: 07/20/2015
f1_keywords:
- unchecked_CSharpKeyword
- unchecked
helpviewer_keywords:
- unchecked keyword [C#]
ms.assetid: 0c021f7c-923f-4b3d-a58f-55336f5ac27e
ms.openlocfilehash: 6dad0dfd508fb390dd0a52d1b48d70b4c5725513
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713007"
---
# <a name="unchecked-c-reference"></a><span data-ttu-id="409f9-102">unchecked (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="409f9-102">unchecked (C# Reference)</span></span>

<span data-ttu-id="409f9-103">`unchecked` anahtar sözcüğü, tamsayı türü aritmetik işlemler ve dönüştürmeler için taşma denetlemeyi gizlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="409f9-103">The `unchecked` keyword is used to suppress overflow-checking for integral-type arithmetic operations and conversions.</span></span>

<span data-ttu-id="409f9-104">İşaretlenmemiş bir bağlamda, bir ifade hedef türü aralığının dışında bir değer üretirse, taşma işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="409f9-104">In an unchecked context, if an expression produces a value that is outside the range of the destination type, the overflow is not flagged.</span></span> <span data-ttu-id="409f9-105">Örneğin, aşağıdaki örnekteki hesaplama bir `unchecked` bloğunda veya ifadesinde gerçekleştirildiğinden, sonucun bir tamsayı için çok büyük olduğu ve `int1`-2.147.483.639 değeri atanır.</span><span class="sxs-lookup"><span data-stu-id="409f9-105">For example, because the calculation in the following example is performed in an `unchecked` block or expression, the fact that the result is too large for an integer is ignored, and `int1` is assigned the value -2,147,483,639.</span></span>

[!code-csharp[csrefKeywordsChecked#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#5)]

<span data-ttu-id="409f9-106">`unchecked` ortam kaldırılırsa, bir derleme hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="409f9-106">If the `unchecked` environment is removed, a compilation error occurs.</span></span> <span data-ttu-id="409f9-107">İfadenin tüm terimleri sabitler olduğundan, derleme sırasında taşma tespit edilebilir.</span><span class="sxs-lookup"><span data-stu-id="409f9-107">The overflow can be detected at compile time because all the terms of the expression are constants.</span></span>

<span data-ttu-id="409f9-108">Sabit olmayan terimleri içeren ifadeler, derleme zamanında ve çalışma zamanında varsayılan olarak işaretli değildir.</span><span class="sxs-lookup"><span data-stu-id="409f9-108">Expressions that contain non-constant terms are unchecked by default at compile time and run time.</span></span> <span data-ttu-id="409f9-109">Denetlenen bir ortamı etkinleştirme hakkında bilgi için bkz. [denetlenir](checked.md) .</span><span class="sxs-lookup"><span data-stu-id="409f9-109">See [checked](checked.md) for information about enabling a checked environment.</span></span>

<span data-ttu-id="409f9-110">Taşma için denetim zaman alacağından, hiçbir tehlike olmaması durumunda Denetlenmemiş kod kullanımı performansı iyileştirebilir.</span><span class="sxs-lookup"><span data-stu-id="409f9-110">Because checking for overflow takes time, the use of unchecked code in situations where there is no danger of overflow might improve performance.</span></span> <span data-ttu-id="409f9-111">Ancak, taşma olasılığa karşı, denetlenen bir ortam kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="409f9-111">However, if overflow is a possibility, a checked environment should be used.</span></span>

## <a name="example"></a><span data-ttu-id="409f9-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="409f9-112">Example</span></span>

<span data-ttu-id="409f9-113">Bu örnek, `unchecked` anahtar sözcüğünün nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="409f9-113">This sample shows how to use the `unchecked` keyword.</span></span>

[!code-csharp[csrefKeywordsChecked#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#2)]

## <a name="c-language-specification"></a><span data-ttu-id="409f9-114">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="409f9-114">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="409f9-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="409f9-115">See also</span></span>

- [<span data-ttu-id="409f9-116">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="409f9-116">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="409f9-117">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="409f9-117">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="409f9-118">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="409f9-118">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="409f9-119">İşaretli ve İşaretsiz</span><span class="sxs-lookup"><span data-stu-id="409f9-119">Checked and Unchecked</span></span>](checked-and-unchecked.md)
- [<span data-ttu-id="409f9-120">checked</span><span class="sxs-lookup"><span data-stu-id="409f9-120">checked</span></span>](checked.md)
