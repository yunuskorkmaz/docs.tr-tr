---
title: "= İşleci (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: =_CSharpKeyword
helpviewer_keywords: = operator [C#]
ms.assetid: d802a6d5-32f0-42b8-b180-12f5a081bfc1
caps.latest.revision: "14"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4c7188abe54cb69678720b4dbbf4dbdea1be4abe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a><span data-ttu-id="1fcde-102">= İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="1fcde-102">= Operator (C# Reference)</span></span>
<span data-ttu-id="1fcde-103">Atama işleci (`=`) depolama konumu, özellik ya da kendi sol işleneni tarafından belirtilen dizin oluşturucu sağ işleneni değerini depolar ve sonuç olarak değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="1fcde-103">The assignment operator (`=`) stores the value of its right-hand operand in the storage location, property, or indexer denoted by its left-hand operand and returns the value as its result.</span></span> <span data-ttu-id="1fcde-104">İşlenen aynı türde olması gerekir (veya sağ işleneni sol işleneni türüne örtük olarak dönüştürülebilir olmalıdır).</span><span class="sxs-lookup"><span data-stu-id="1fcde-104">The operands must be of the same type (or the right-hand operand must be implicitly convertible to the type of the left-hand operand).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1fcde-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1fcde-105">Remarks</span></span>  
 <span data-ttu-id="1fcde-106">Atama işleci aşırı yüklenemez.</span><span class="sxs-lookup"><span data-stu-id="1fcde-106">The assignment operator cannot be overloaded.</span></span> <span data-ttu-id="1fcde-107">Ancak, bu tür atama işleci kullanmanıza olanak sağlayan örtük dönüşüm işleçleri bir tür için tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1fcde-107">However, you can define implicit conversion operators for a type, which enable you to use the assignment operator with those types.</span></span> <span data-ttu-id="1fcde-108">Daha fazla bilgi için bkz: [dönüşüm işleçleri kullanma](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md).</span><span class="sxs-lookup"><span data-stu-id="1fcde-108">For more information, see [Using Conversion Operators](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1fcde-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="1fcde-109">Example</span></span>  
 [!code-csharp[csRefOperators#49](../../../csharp/language-reference/operators/codesnippet/CSharp/assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="1fcde-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1fcde-110">See Also</span></span>  
 [<span data-ttu-id="1fcde-111">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="1fcde-111">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="1fcde-112">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="1fcde-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="1fcde-113">C# işleçleri</span><span class="sxs-lookup"><span data-stu-id="1fcde-113">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
