---
title: unchecked (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- unchecked_CSharpKeyword
- unchecked
helpviewer_keywords:
- unchecked keyword [C#]
ms.assetid: 0c021f7c-923f-4b3d-a58f-55336f5ac27e
ms.openlocfilehash: d7a48950b7158be3cd589c20fbfe0661f3c9c5af
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33267986"
---
# <a name="unchecked-c-reference"></a><span data-ttu-id="00377-102">unchecked (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="00377-102">unchecked (C# Reference)</span></span>
<span data-ttu-id="00377-103">`unchecked` Anahtar sözcüğü taşma denetimi integral türü aritmetik işlemler ve dönüştürmeleri için gizlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="00377-103">The `unchecked` keyword is used to suppress overflow-checking for integral-type arithmetic operations and conversions.</span></span>  
  
 <span data-ttu-id="00377-104">Bir ifade hedef türü aralık dışında bir değer oluşturursa denetlenmeyen bir bağlamda taşma işaretlenmemiştir.</span><span class="sxs-lookup"><span data-stu-id="00377-104">In an unchecked context, if an expression produces a value that is outside the range of the destination type, the overflow is not flagged.</span></span> <span data-ttu-id="00377-105">Örneğin, aşağıdaki örnekte hesaplama yapıldığından bir `unchecked` blok veya ifadesi, bir tamsayı göz ardı için sonucu çok büyük olduğunu olgu ve `int1` -2,147,483,639 değeri atanır.</span><span class="sxs-lookup"><span data-stu-id="00377-105">For example, because the calculation in the following example is performed in an `unchecked` block or expression, the fact that the result is too large for an integer is ignored, and `int1` is assigned the value -2,147,483,639.</span></span>  
  
 [!code-csharp[csrefKeywordsChecked#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/unchecked_1.cs)]  
  
 <span data-ttu-id="00377-106">Varsa `unchecked` ortamı kaldırılır, derleme hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="00377-106">If the `unchecked` environment is removed, a compilation error occurs.</span></span> <span data-ttu-id="00377-107">İfadenin tüm koşulları sabitleri olduğundan taşma derleme zamanında algılanabilir.</span><span class="sxs-lookup"><span data-stu-id="00377-107">The overflow can be detected at compile time because all the terms of the expression are constants.</span></span>  
  
 <span data-ttu-id="00377-108">Sabit olmayan terimleri içeren ifadeleri derleme zamanında varsayılan olarak işaretli ve çalışma zamanı.</span><span class="sxs-lookup"><span data-stu-id="00377-108">Expressions that contain non-constant terms are unchecked by default at compile time and run time.</span></span> <span data-ttu-id="00377-109">Bkz: [işaretli](../../../csharp/language-reference/keywords/checked.md) işaretli bir ortamda etkinleştirme hakkında bilgi için.</span><span class="sxs-lookup"><span data-stu-id="00377-109">See [checked](../../../csharp/language-reference/keywords/checked.md) for information about enabling a checked environment.</span></span>  
  
 <span data-ttu-id="00377-110">Taşma sürüyor, durumlarda denetlenmeyen kod kullanımı için denetimi için söz konusu olduğunda, tehlike taşma performansı iyileştirebilir.</span><span class="sxs-lookup"><span data-stu-id="00377-110">Because checking for overflow takes time, the use of unchecked code in situations where there is no danger of overflow might improve performance.</span></span> <span data-ttu-id="00377-111">Taşma olasılığı varsa, ancak, denetlenen bir ortamda kullanılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="00377-111">However, if overflow is a possibility, a checked environment should be used.</span></span>  
  
## <a name="example"></a><span data-ttu-id="00377-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="00377-112">Example</span></span>  
 <span data-ttu-id="00377-113">Bu örnek nasıl kullanılacağını göstermektedir `unchecked` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="00377-113">This sample shows how to use the `unchecked` keyword.</span></span>  
  
 [!code-csharp[csrefKeywordsChecked#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/unchecked_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="00377-114">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="00377-114">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="00377-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="00377-115">See Also</span></span>  
 [<span data-ttu-id="00377-116">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="00377-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="00377-117">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="00377-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="00377-118">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="00377-118">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="00377-119">İşaretli ve İşaretsiz</span><span class="sxs-lookup"><span data-stu-id="00377-119">Checked and Unchecked</span></span>](../../../csharp/language-reference/keywords/checked-and-unchecked.md)  
 [<span data-ttu-id="00377-120">checked</span><span class="sxs-lookup"><span data-stu-id="00377-120">checked</span></span>](../../../csharp/language-reference/keywords/checked.md)
