---
title: -- İşleci (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- --_CSharpKeyword
helpviewer_keywords:
- -- operator [C#]
- decrement operator (--) [C#]
ms.assetid: 6b9cfe86-63c7-421f-9379-c9690fea8720
ms.openlocfilehash: 25f301bc0b2bc9bf51b0a44f26b2efabae00e452
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33288807"
---
# <a name="---operator-c-reference"></a><span data-ttu-id="c7aab-102">-- İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="c7aab-102">-- Operator (C# Reference)</span></span>
<span data-ttu-id="c7aab-103">Azaltma işleci (`--`) azaltır, işlenen 1.</span><span class="sxs-lookup"><span data-stu-id="c7aab-103">The decrement operator (`--`) decrements its operand by 1.</span></span> <span data-ttu-id="c7aab-104">Azaltma işleci önce veya sonra işlenen görünebilir: `--variable` ve `variable--`.</span><span class="sxs-lookup"><span data-stu-id="c7aab-104">The decrement operator can appear before or after its operand: `--variable` and `variable--`.</span></span> <span data-ttu-id="c7aab-105">İlk form bir önek azaltma işlemdir.</span><span class="sxs-lookup"><span data-stu-id="c7aab-105">The first form is a prefix decrement operation.</span></span> <span data-ttu-id="c7aab-106">"İndirildiği sağlandıktan sonra" işleminin sonucu işleneni değerdir.</span><span class="sxs-lookup"><span data-stu-id="c7aab-106">The result of the operation is the value of the operand "after" it has been decremented.</span></span> <span data-ttu-id="c7aab-107">İkinci bir sonek azaltma işlemi biçimidir.</span><span class="sxs-lookup"><span data-stu-id="c7aab-107">The second form is a postfix decrement operation.</span></span> <span data-ttu-id="c7aab-108">"Önce" indirildiği bırakıldı işleminin sonucu işleneni değerdir.</span><span class="sxs-lookup"><span data-stu-id="c7aab-108">The result of the operation is the value of the operand "before" it has been decremented.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c7aab-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c7aab-109">Remarks</span></span>  
 <span data-ttu-id="c7aab-110">Sayısal ve Numaralandırma türleri azaltma işleçleri önceden.</span><span class="sxs-lookup"><span data-stu-id="c7aab-110">Numeric and enumeration types have predefined decrement operators.</span></span>  
  
 <span data-ttu-id="c7aab-111">Kullanıcı tanımlı türler aşırı yükleme `--` işleci (bkz [işleci](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="c7aab-111">User-defined types can overload the `--` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="c7aab-112">Tam sayı türleri üzerinde işlemler genellikle numaralandırma üzerinde izin verilir.</span><span class="sxs-lookup"><span data-stu-id="c7aab-112">Operations on integral types are generally allowed on enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c7aab-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="c7aab-113">Example</span></span>  
 [!code-csharp[csRefOperators#8](../../../csharp/language-reference/operators/codesnippet/CSharp/decrement-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="c7aab-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c7aab-114">See Also</span></span>  
 [<span data-ttu-id="c7aab-115">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="c7aab-115">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="c7aab-116">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="c7aab-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="c7aab-117">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="c7aab-117">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
