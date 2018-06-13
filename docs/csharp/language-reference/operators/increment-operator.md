---
title: ++ İşleci (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- ++_CSharpKeyword
helpviewer_keywords:
- increment operator (++) [C#]
- ++ operator [C#]
ms.assetid: e9dec353-070b-44fb-98ed-eb8fdf753feb
ms.openlocfilehash: 0fe1150ca7267d02feeab33168eab7f79734c2a1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33275070"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="f9116-102">++ İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="f9116-102">++ Operator (C# Reference)</span></span>
<span data-ttu-id="f9116-103">Artış işleci (`++`), işlenen 1 arttırır.</span><span class="sxs-lookup"><span data-stu-id="f9116-103">The increment operator (`++`) increments its operand by 1.</span></span> <span data-ttu-id="f9116-104">Artış işleci önce veya sonra işlenen görünebilir: `++variable` ve `variable++`.</span><span class="sxs-lookup"><span data-stu-id="f9116-104">The increment operator can appear before or after its operand: `++variable` and `variable++`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f9116-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f9116-105">Remarks</span></span>  
 <span data-ttu-id="f9116-106">İlk form bir önek artırma işlemdir.</span><span class="sxs-lookup"><span data-stu-id="f9116-106">The first form is a prefix increment operation.</span></span> <span data-ttu-id="f9116-107">Bunu artar sonra işlemin sonucunu işleneni değerdir.</span><span class="sxs-lookup"><span data-stu-id="f9116-107">The result of the operation is the value of the operand after it has been incremented.</span></span>  
  
 <span data-ttu-id="f9116-108">İkinci form bir sonek artırma işlemdir.</span><span class="sxs-lookup"><span data-stu-id="f9116-108">The second form is a postfix increment operation.</span></span> <span data-ttu-id="f9116-109">Bunu artar önce işleminin sonucu işleneni değerdir.</span><span class="sxs-lookup"><span data-stu-id="f9116-109">The result of the operation is the value of the operand before it has been incremented.</span></span>  
  
 <span data-ttu-id="f9116-110">Sayısal ve Numaralandırma türleri artırma işleçleri önceden.</span><span class="sxs-lookup"><span data-stu-id="f9116-110">Numeric and enumeration types have predefined increment operators.</span></span> <span data-ttu-id="f9116-111">Kullanıcı tanımlı türler aşırı yükleme `++` işleci.</span><span class="sxs-lookup"><span data-stu-id="f9116-111">User-defined types can overload the `++` operator.</span></span> <span data-ttu-id="f9116-112">Tam sayı türleri üzerinde işlemler genellikle numaralandırma üzerinde izin verilir.</span><span class="sxs-lookup"><span data-stu-id="f9116-112">Operations on integral types are generally allowed on enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f9116-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="f9116-113">Example</span></span>  
 [!code-csharp[csRefOperators#3](../../../csharp/language-reference/operators/codesnippet/CSharp/increment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="f9116-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f9116-114">See Also</span></span>  
 [<span data-ttu-id="f9116-115">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="f9116-115">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="f9116-116">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="f9116-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="f9116-117">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="f9116-117">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
