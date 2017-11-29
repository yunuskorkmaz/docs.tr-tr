---
title: "unchecked (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- unchecked_CSharpKeyword
- unchecked
helpviewer_keywords: unchecked keyword [C#]
ms.assetid: 0c021f7c-923f-4b3d-a58f-55336f5ac27e
caps.latest.revision: "23"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c05e7cb742d8e8f5a7804656a5ec13548d0498b1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="unchecked-c-reference"></a><span data-ttu-id="78a94-102">unchecked (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="78a94-102">unchecked (C# Reference)</span></span>
<span data-ttu-id="78a94-103">`unchecked` Anahtar sözcüğü taşma denetimi integral türü aritmetik işlemler ve dönüştürmeleri için gizlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="78a94-103">The `unchecked` keyword is used to suppress overflow-checking for integral-type arithmetic operations and conversions.</span></span>  
  
 <span data-ttu-id="78a94-104">Bir ifade hedef türü aralık dışında bir değer oluşturursa denetlenmeyen bir bağlamda taşma işaretlenmemiştir.</span><span class="sxs-lookup"><span data-stu-id="78a94-104">In an unchecked context, if an expression produces a value that is outside the range of the destination type, the overflow is not flagged.</span></span> <span data-ttu-id="78a94-105">Örneğin, aşağıdaki örnekte hesaplama yapıldığından bir `unchecked` blok veya ifadesi, bir tamsayı göz ardı için sonucu çok büyük olduğunu olgu ve `int1` -2,147,483,639 değeri atanır.</span><span class="sxs-lookup"><span data-stu-id="78a94-105">For example, because the calculation in the following example is performed in an `unchecked` block or expression, the fact that the result is too large for an integer is ignored, and `int1` is assigned the value -2,147,483,639.</span></span>  
  
 [!code-csharp[csrefKeywordsChecked#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/unchecked_1.cs)]  
  
 <span data-ttu-id="78a94-106">Varsa `unchecked` ortamı kaldırılır, derleme hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="78a94-106">If the `unchecked` environment is removed, a compilation error occurs.</span></span> <span data-ttu-id="78a94-107">İfadenin tüm koşulları sabitleri olduğundan taşma derleme zamanında algılanabilir.</span><span class="sxs-lookup"><span data-stu-id="78a94-107">The overflow can be detected at compile time because all the terms of the expression are constants.</span></span>  
  
 <span data-ttu-id="78a94-108">Sabit olmayan terimleri içeren ifadeleri derleme zamanında varsayılan olarak işaretli ve çalışma zamanı.</span><span class="sxs-lookup"><span data-stu-id="78a94-108">Expressions that contain non-constant terms are unchecked by default at compile time and run time.</span></span> <span data-ttu-id="78a94-109">Bkz: [işaretli](../../../csharp/language-reference/keywords/checked.md) işaretli bir ortamda etkinleştirme hakkında bilgi için.</span><span class="sxs-lookup"><span data-stu-id="78a94-109">See [checked](../../../csharp/language-reference/keywords/checked.md) for information about enabling a checked environment.</span></span>  
  
 <span data-ttu-id="78a94-110">Taşma sürüyor, durumlarda denetlenmeyen kod kullanımı için denetimi için söz konusu olduğunda, tehlike taşma performansı iyileştirebilir.</span><span class="sxs-lookup"><span data-stu-id="78a94-110">Because checking for overflow takes time, the use of unchecked code in situations where there is no danger of overflow might improve performance.</span></span> <span data-ttu-id="78a94-111">Taşma olasılığı varsa, ancak, denetlenen bir ortamda kullanılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="78a94-111">However, if overflow is a possibility, a checked environment should be used.</span></span>  
  
## <a name="example"></a><span data-ttu-id="78a94-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="78a94-112">Example</span></span>  
 <span data-ttu-id="78a94-113">Bu örnek nasıl kullanılacağını göstermektedir `unchecked` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="78a94-113">This sample shows how to use the `unchecked` keyword.</span></span>  
  
 [!code-csharp[csrefKeywordsChecked#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/unchecked_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="78a94-114">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="78a94-114">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="78a94-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="78a94-115">See Also</span></span>  
 [<span data-ttu-id="78a94-116">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="78a94-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="78a94-117">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="78a94-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="78a94-118">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="78a94-118">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="78a94-119">Checked ve Unchecked</span><span class="sxs-lookup"><span data-stu-id="78a94-119">Checked and Unchecked</span></span>](../../../csharp/language-reference/keywords/checked-and-unchecked.md)  
 [<span data-ttu-id="78a94-120">işaretli</span><span class="sxs-lookup"><span data-stu-id="78a94-120">checked</span></span>](../../../csharp/language-reference/keywords/checked.md)
