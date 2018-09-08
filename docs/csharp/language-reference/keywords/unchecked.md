---
title: unchecked (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- unchecked_CSharpKeyword
- unchecked
helpviewer_keywords:
- unchecked keyword [C#]
ms.assetid: 0c021f7c-923f-4b3d-a58f-55336f5ac27e
ms.openlocfilehash: daccd7916a9f81f26f468ab0f64833d9537cff8e
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44206016"
---
# <a name="unchecked-c-reference"></a><span data-ttu-id="86604-102">unchecked (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="86604-102">unchecked (C# Reference)</span></span>
<span data-ttu-id="86604-103">`unchecked` Anahtar sözcüğü, Tamsayı türünde aritmetik işlemler ve dönüştürmeler için taşma denetimi gizlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="86604-103">The `unchecked` keyword is used to suppress overflow-checking for integral-type arithmetic operations and conversions.</span></span>  
  
 <span data-ttu-id="86604-104">Bir ifade hedef türün aralığı dışında bir değer veriyorsa işaretlenmemiş bir bağlamda taşma işaretlenmemiştir.</span><span class="sxs-lookup"><span data-stu-id="86604-104">In an unchecked context, if an expression produces a value that is outside the range of the destination type, the overflow is not flagged.</span></span> <span data-ttu-id="86604-105">Örneğin, aşağıdaki örnekte hesaplama yapıldığından bir `unchecked` blok veya ifade, bir tamsayı göz ardı edilir için sonuç çok büyük olduğunu ve `int1` -2,147,483,639 değeri atanır.</span><span class="sxs-lookup"><span data-stu-id="86604-105">For example, because the calculation in the following example is performed in an `unchecked` block or expression, the fact that the result is too large for an integer is ignored, and `int1` is assigned the value -2,147,483,639.</span></span>  
  
 [!code-csharp[csrefKeywordsChecked#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/unchecked_1.cs)]  
  
 <span data-ttu-id="86604-106">Varsa `unchecked` ortam kaldırılır, bir derleme hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="86604-106">If the `unchecked` environment is removed, a compilation error occurs.</span></span> <span data-ttu-id="86604-107">İfadenin tüm koşulları sabitleri olduğundan overflow derleme zamanında algılanabilir.</span><span class="sxs-lookup"><span data-stu-id="86604-107">The overflow can be detected at compile time because all the terms of the expression are constants.</span></span>  
  
 <span data-ttu-id="86604-108">Sabit olmayan terimleri içeren ifadeler, derleme zamanında varsayılan olarak işaretli ve çalışma zamanı.</span><span class="sxs-lookup"><span data-stu-id="86604-108">Expressions that contain non-constant terms are unchecked by default at compile time and run time.</span></span> <span data-ttu-id="86604-109">Bkz: [işaretli](../../../csharp/language-reference/keywords/checked.md) denetlenmiş bir ortamda etkinleştirme hakkında bilgi için.</span><span class="sxs-lookup"><span data-stu-id="86604-109">See [checked](../../../csharp/language-reference/keywords/checked.md) for information about enabling a checked environment.</span></span>  
  
 <span data-ttu-id="86604-110">Taşma sürüyor, durumlarda denetlenmeyen kod kullanımı için denetimi olduğundan, tehlike olduğu taşma performansı iyileştirebilir.</span><span class="sxs-lookup"><span data-stu-id="86604-110">Because checking for overflow takes time, the use of unchecked code in situations where there is no danger of overflow might improve performance.</span></span> <span data-ttu-id="86604-111">Ancak, denetlenmiş bir ortamda taşma olasılığı varsa kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="86604-111">However, if overflow is a possibility, a checked environment should be used.</span></span>  
  
## <a name="example"></a><span data-ttu-id="86604-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="86604-112">Example</span></span>  
 <span data-ttu-id="86604-113">Bu örnek nasıl kullanılacağını gösterir `unchecked` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="86604-113">This sample shows how to use the `unchecked` keyword.</span></span>  
  
 [!code-csharp[csrefKeywordsChecked#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/unchecked_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="86604-114">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="86604-114">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="86604-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="86604-115">See Also</span></span>

- [<span data-ttu-id="86604-116">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="86604-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="86604-117">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="86604-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="86604-118">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="86604-118">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="86604-119">İşaretli ve İşaretsiz</span><span class="sxs-lookup"><span data-stu-id="86604-119">Checked and Unchecked</span></span>](../../../csharp/language-reference/keywords/checked-and-unchecked.md)  
- [<span data-ttu-id="86604-120">checked</span><span class="sxs-lookup"><span data-stu-id="86604-120">checked</span></span>](../../../csharp/language-reference/keywords/checked.md)
