---
title: -- İşleci (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- --_CSharpKeyword
helpviewer_keywords:
- -- operator [C#]
- decrement operator (--) [C#]
ms.assetid: 6b9cfe86-63c7-421f-9379-c9690fea8720
ms.openlocfilehash: 615b100447233856ab3740d075d69e3ae19285fd
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44210435"
---
# <a name="---operator-c-reference"></a><span data-ttu-id="d6455-102">-- İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="d6455-102">-- Operator (C# Reference)</span></span>
<span data-ttu-id="d6455-103">Azaltma işleci (`--`) azaltır işleneniyle 1.</span><span class="sxs-lookup"><span data-stu-id="d6455-103">The decrement operator (`--`) decrements its operand by 1.</span></span> <span data-ttu-id="d6455-104">Azaltma işleci önce veya sonra işleneniyle görünebilir: `--variable` ve `variable--`.</span><span class="sxs-lookup"><span data-stu-id="d6455-104">The decrement operator can appear before or after its operand: `--variable` and `variable--`.</span></span> <span data-ttu-id="d6455-105">Önek azaltma işlemi ilk biçimidir.</span><span class="sxs-lookup"><span data-stu-id="d6455-105">The first form is a prefix decrement operation.</span></span> <span data-ttu-id="d6455-106">"İndirildiği sonra" işleminin sonucu işlenenin değerdir.</span><span class="sxs-lookup"><span data-stu-id="d6455-106">The result of the operation is the value of the operand "after" it has been decremented.</span></span> <span data-ttu-id="d6455-107">İkinci bir sonek azaltma işlemi biçimidir.</span><span class="sxs-lookup"><span data-stu-id="d6455-107">The second form is a postfix decrement operation.</span></span> <span data-ttu-id="d6455-108">"Önce" indirildiği olmuştur işleminin sonucu işlenenin değerdir.</span><span class="sxs-lookup"><span data-stu-id="d6455-108">The result of the operation is the value of the operand "before" it has been decremented.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d6455-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d6455-109">Remarks</span></span>  
 <span data-ttu-id="d6455-110">Sayısal ve Numaralandırma türleri azaltma işleçleri önceden tanımlanmış.</span><span class="sxs-lookup"><span data-stu-id="d6455-110">Numeric and enumeration types have predefined decrement operators.</span></span>  
  
 <span data-ttu-id="d6455-111">Kullanıcı tanımlı türler aşırı yükleme `--` işleci (bkz [işleci](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="d6455-111">User-defined types can overload the `--` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="d6455-112">Tamsayı türlerinde işlemler genellikle numaralandırma üzerinde izin verilir.</span><span class="sxs-lookup"><span data-stu-id="d6455-112">Operations on integral types are generally allowed on enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d6455-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="d6455-113">Example</span></span>  
 [!code-csharp[csRefOperators#8](../../../csharp/language-reference/operators/codesnippet/CSharp/decrement-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="d6455-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d6455-114">See Also</span></span>

- [<span data-ttu-id="d6455-115">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="d6455-115">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="d6455-116">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="d6455-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="d6455-117">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="d6455-117">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
