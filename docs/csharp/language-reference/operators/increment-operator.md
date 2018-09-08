---
title: ++ İşleci (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- ++_CSharpKeyword
helpviewer_keywords:
- increment operator (++) [C#]
- ++ operator [C#]
ms.assetid: e9dec353-070b-44fb-98ed-eb8fdf753feb
ms.openlocfilehash: a52f614ce1bbfb8e9d9be686b277c1e69f6f9d35
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44180939"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="c4daf-102">++ İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="c4daf-102">++ Operator (C# Reference)</span></span>
<span data-ttu-id="c4daf-103">Artırım işleci (`++`) işleneniyle 1 artar.</span><span class="sxs-lookup"><span data-stu-id="c4daf-103">The increment operator (`++`) increments its operand by 1.</span></span> <span data-ttu-id="c4daf-104">Artırım işleci önce veya sonra işleneniyle görünebilir: `++variable` ve `variable++`.</span><span class="sxs-lookup"><span data-stu-id="c4daf-104">The increment operator can appear before or after its operand: `++variable` and `variable++`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c4daf-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c4daf-105">Remarks</span></span>  
 <span data-ttu-id="c4daf-106">Önek artırma işlemi ilk biçimidir.</span><span class="sxs-lookup"><span data-stu-id="c4daf-106">The first form is a prefix increment operation.</span></span> <span data-ttu-id="c4daf-107">Bunu artırıldıktan sonra işleminin sonucu işlenenin değerdir.</span><span class="sxs-lookup"><span data-stu-id="c4daf-107">The result of the operation is the value of the operand after it has been incremented.</span></span>  
  
 <span data-ttu-id="c4daf-108">Bir sonek artırma işlemi ikinci biçimidir.</span><span class="sxs-lookup"><span data-stu-id="c4daf-108">The second form is a postfix increment operation.</span></span> <span data-ttu-id="c4daf-109">Bunu artırıldıktan önce işleminin sonucu işlenenin değerdir.</span><span class="sxs-lookup"><span data-stu-id="c4daf-109">The result of the operation is the value of the operand before it has been incremented.</span></span>  
  
 <span data-ttu-id="c4daf-110">Sayısal ve Numaralandırma türleri artırma işleçleri önceden tanımlanmış.</span><span class="sxs-lookup"><span data-stu-id="c4daf-110">Numeric and enumeration types have predefined increment operators.</span></span> <span data-ttu-id="c4daf-111">Kullanıcı tanımlı türler aşırı yükleme `++` işleci.</span><span class="sxs-lookup"><span data-stu-id="c4daf-111">User-defined types can overload the `++` operator.</span></span> <span data-ttu-id="c4daf-112">Tamsayı türlerinde işlemler genellikle numaralandırma üzerinde izin verilir.</span><span class="sxs-lookup"><span data-stu-id="c4daf-112">Operations on integral types are generally allowed on enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c4daf-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="c4daf-113">Example</span></span>  
 [!code-csharp[csRefOperators#3](../../../csharp/language-reference/operators/codesnippet/CSharp/increment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="c4daf-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c4daf-114">See Also</span></span>

- [<span data-ttu-id="c4daf-115">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="c4daf-115">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="c4daf-116">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="c4daf-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="c4daf-117">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="c4daf-117">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
