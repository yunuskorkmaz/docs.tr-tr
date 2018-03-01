---
title: "++ İşleci (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ++_CSharpKeyword
helpviewer_keywords:
- increment operator (++) [C#]
- ++ operator [C#]
ms.assetid: e9dec353-070b-44fb-98ed-eb8fdf753feb
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 6deb2f772fefc93020e7eaaed6be35e48b11df7a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a><span data-ttu-id="12e93-102">++ İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="12e93-102">++ Operator (C# Reference)</span></span>
<span data-ttu-id="12e93-103">Artış işleci (`++`), işlenen 1 arttırır.</span><span class="sxs-lookup"><span data-stu-id="12e93-103">The increment operator (`++`) increments its operand by 1.</span></span> <span data-ttu-id="12e93-104">Artış işleci önce veya sonra işlenen görünebilir: `++variable` ve `variable++`.</span><span class="sxs-lookup"><span data-stu-id="12e93-104">The increment operator can appear before or after its operand: `++variable` and `variable++`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="12e93-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="12e93-105">Remarks</span></span>  
 <span data-ttu-id="12e93-106">İlk form bir önek artırma işlemdir.</span><span class="sxs-lookup"><span data-stu-id="12e93-106">The first form is a prefix increment operation.</span></span> <span data-ttu-id="12e93-107">Bunu artar sonra işlemin sonucunu işleneni değerdir.</span><span class="sxs-lookup"><span data-stu-id="12e93-107">The result of the operation is the value of the operand after it has been incremented.</span></span>  
  
 <span data-ttu-id="12e93-108">İkinci form bir sonek artırma işlemdir.</span><span class="sxs-lookup"><span data-stu-id="12e93-108">The second form is a postfix increment operation.</span></span> <span data-ttu-id="12e93-109">Bunu artar önce işleminin sonucu işleneni değerdir.</span><span class="sxs-lookup"><span data-stu-id="12e93-109">The result of the operation is the value of the operand before it has been incremented.</span></span>  
  
 <span data-ttu-id="12e93-110">Sayısal ve Numaralandırma türleri artırma işleçleri önceden.</span><span class="sxs-lookup"><span data-stu-id="12e93-110">Numeric and enumeration types have predefined increment operators.</span></span> <span data-ttu-id="12e93-111">Kullanıcı tanımlı türler aşırı yükleme `++` işleci.</span><span class="sxs-lookup"><span data-stu-id="12e93-111">User-defined types can overload the `++` operator.</span></span> <span data-ttu-id="12e93-112">Tam sayı türleri üzerinde işlemler genellikle numaralandırma üzerinde izin verilir.</span><span class="sxs-lookup"><span data-stu-id="12e93-112">Operations on integral types are generally allowed on enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="12e93-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="12e93-113">Example</span></span>  
 [!code-csharp[csRefOperators#3](../../../csharp/language-reference/operators/codesnippet/CSharp/increment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="12e93-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="12e93-114">See Also</span></span>  
 [<span data-ttu-id="12e93-115">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="12e93-115">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="12e93-116">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="12e93-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="12e93-117">C# işleçleri</span><span class="sxs-lookup"><span data-stu-id="12e93-117">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
