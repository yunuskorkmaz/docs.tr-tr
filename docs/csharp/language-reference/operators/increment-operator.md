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
ms.sourcegitcommit: fe02afbc39e78afd78cc6050e4a9c12a75f579f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2018
ms.locfileid: "43254288"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="c6cde-102">++ İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="c6cde-102">++ Operator (C# Reference)</span></span>
<span data-ttu-id="c6cde-103">Artırım işleci (`++`) işleneniyle 1 artar.</span><span class="sxs-lookup"><span data-stu-id="c6cde-103">The increment operator (`++`) increments its operand by 1.</span></span> <span data-ttu-id="c6cde-104">Artırım işleci önce veya sonra işleneniyle görünebilir: `++variable` ve `variable++`.</span><span class="sxs-lookup"><span data-stu-id="c6cde-104">The increment operator can appear before or after its operand: `++variable` and `variable++`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c6cde-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c6cde-105">Remarks</span></span>  
 <span data-ttu-id="c6cde-106">Önek artırma işlemi ilk biçimidir.</span><span class="sxs-lookup"><span data-stu-id="c6cde-106">The first form is a prefix increment operation.</span></span> <span data-ttu-id="c6cde-107">Bunu artırıldıktan sonra işleminin sonucu işlenenin değerdir.</span><span class="sxs-lookup"><span data-stu-id="c6cde-107">The result of the operation is the value of the operand after it has been incremented.</span></span>  
  
 <span data-ttu-id="c6cde-108">Bir sonek artırma işlemi ikinci biçimidir.</span><span class="sxs-lookup"><span data-stu-id="c6cde-108">The second form is a postfix increment operation.</span></span> <span data-ttu-id="c6cde-109">Bunu artırıldıktan önce işleminin sonucu işlenenin değerdir.</span><span class="sxs-lookup"><span data-stu-id="c6cde-109">The result of the operation is the value of the operand before it has been incremented.</span></span>  
  
 <span data-ttu-id="c6cde-110">Sayısal ve Numaralandırma türleri artırma işleçleri önceden tanımlanmış.</span><span class="sxs-lookup"><span data-stu-id="c6cde-110">Numeric and enumeration types have predefined increment operators.</span></span> <span data-ttu-id="c6cde-111">Kullanıcı tanımlı türler aşırı yükleme `++` işleci.</span><span class="sxs-lookup"><span data-stu-id="c6cde-111">User-defined types can overload the `++` operator.</span></span> <span data-ttu-id="c6cde-112">Tamsayı türlerinde işlemler genellikle numaralandırma üzerinde izin verilir.</span><span class="sxs-lookup"><span data-stu-id="c6cde-112">Operations on integral types are generally allowed on enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c6cde-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="c6cde-113">Example</span></span>  
 [!code-csharp[csRefOperators#3](../../../csharp/language-reference/operators/codesnippet/CSharp/increment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="c6cde-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c6cde-114">See Also</span></span>

- [<span data-ttu-id="c6cde-115">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="c6cde-115">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="c6cde-116">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="c6cde-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="c6cde-117">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="c6cde-117">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
