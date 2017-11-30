---
title: "checked (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- checked_CSharpKeyword
- checked
helpviewer_keywords: checked keyword [C#]
ms.assetid: 718a1194-988d-48a3-b089-d6ee8bd1608d
caps.latest.revision: "24"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 0ae77894cdc94e41dfa281b92ed3304e0dc25731
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="checked-c-reference"></a><span data-ttu-id="7ba16-102">checked (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="7ba16-102">checked (C# Reference)</span></span>
<span data-ttu-id="7ba16-103">`checked` Anahtar sözcüğü açıkça taşma integral türü aritmetik işlemler ve dönüştürmeleri için denetimini etkinleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7ba16-103">The `checked` keyword is used to explicitly enable overflow checking for integral-type arithmetic operations and conversions.</span></span>  
  
 <span data-ttu-id="7ba16-104">Varsayılan olarak, hedef türü aralık dışında bir değer ifadesi neden oluyorsa yalnızca sabit değerler içeren bir ifade derleyici hatası neden olur.</span><span class="sxs-lookup"><span data-stu-id="7ba16-104">By default, an expression that contains only constant values causes a compiler error if the expression produces a value that is outside the range of the destination type.</span></span> <span data-ttu-id="7ba16-105">İfade bir veya daha fazla sabit olmayan değerler içeriyorsa, derleyicinin taşma algılamaz.</span><span class="sxs-lookup"><span data-stu-id="7ba16-105">If the expression contains one or more non-constant values, the compiler does not detect the overflow.</span></span> <span data-ttu-id="7ba16-106">Atanan ifade değerlendirme `i2` aşağıdaki örnekte bir derleyici hatası neden olmaz.</span><span class="sxs-lookup"><span data-stu-id="7ba16-106">Evaluating the expression assigned to `i2` in the following example does not cause a compiler error.</span></span>  
  
 [!code-csharp[csrefKeywordsChecked#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/checked_1.cs)]  
  
 <span data-ttu-id="7ba16-107">Varsayılan olarak, bu sabit olmayan ifadeleri taşma için çalışma zamanında ya da denetlenmez ve taşma özel durumlar yükseltmeyin.</span><span class="sxs-lookup"><span data-stu-id="7ba16-107">By default, these non-constant expressions are not checked for overflow at run time either, and they do not raise overflow exceptions.</span></span> <span data-ttu-id="7ba16-108">Önceki örnekte-2,147,483,639 iki pozitif tamsayıdır toplamı olarak görüntüler.</span><span class="sxs-lookup"><span data-stu-id="7ba16-108">The previous example displays -2,147,483,639 as the sum of two positive integers.</span></span>  
  
 <span data-ttu-id="7ba16-109">Taşma denetimi etkinleştirilebilir derleyici seçenekleri, ortamı yapılandırması veya kullanımı `checked` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="7ba16-109">Overflow checking can be enabled by compiler options, environment configuration, or use of the `checked` keyword.</span></span> <span data-ttu-id="7ba16-110">Aşağıdaki örneklerde nasıl kullanılacağını gösteren bir `checked` ifadesi veya bir `checked` tarafından önceki toplam çalışma zamanında üretilen taşma algılamak için blok.</span><span class="sxs-lookup"><span data-stu-id="7ba16-110">The following examples demonstrate how to use a `checked` expression or a `checked` block to detect the overflow that is produced by the previous sum at run time.</span></span> <span data-ttu-id="7ba16-111">Örneklerin her ikisi de taşma özel durumu yükseltin.</span><span class="sxs-lookup"><span data-stu-id="7ba16-111">Both examples raise an overflow exception.</span></span>  
  
 [!code-csharp[csrefKeywordsChecked#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/checked_2.cs)]  
  
 <span data-ttu-id="7ba16-112">[Denetlenmeyen](../../../csharp/language-reference/keywords/unchecked.md) anahtar sözcüğü, taşma denetimi önlemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7ba16-112">The [unchecked](../../../csharp/language-reference/keywords/unchecked.md) keyword can be used to prevent overflow checking.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7ba16-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="7ba16-113">Example</span></span>  
 <span data-ttu-id="7ba16-114">Bu örnek nasıl kullanılacağını göstermektedir `checked` taşma çalışma zamanında denetimini etkinleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="7ba16-114">This sample shows how to use `checked` to enable overflow checking at run time.</span></span>  
  
 [!code-csharp[csrefKeywordsChecked#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/checked_3.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="7ba16-115">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="7ba16-115">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="7ba16-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7ba16-116">See Also</span></span>  
 [<span data-ttu-id="7ba16-117">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="7ba16-117">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="7ba16-118">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="7ba16-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="7ba16-119">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="7ba16-119">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="7ba16-120">Checked ve Unchecked</span><span class="sxs-lookup"><span data-stu-id="7ba16-120">Checked and Unchecked</span></span>](../../../csharp/language-reference/keywords/checked-and-unchecked.md)  
 [<span data-ttu-id="7ba16-121">işaretli</span><span class="sxs-lookup"><span data-stu-id="7ba16-121">unchecked</span></span>](../../../csharp/language-reference/keywords/unchecked.md)
