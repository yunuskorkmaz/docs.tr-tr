---
title: AddressOf İşleci (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- AddressOf
- vb.AddressOf
helpviewer_keywords:
- AddressOf operator [Visual Basic]
- addresses, passing to API procedures
ms.assetid: 8105a59d-60d8-4ab5-b221-5899cdfacbf4
ms.openlocfilehash: b68d93009d2d297f8b8867fb8e79b26173a45095
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56964675"
---
# <a name="addressof-operator-visual-basic"></a><span data-ttu-id="c6606-102">AddressOf İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c6606-102">AddressOf Operator (Visual Basic)</span></span>
<span data-ttu-id="c6606-103">Özel yordam başvuran bir yordam temsilci örneği oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c6606-103">Creates a procedure delegate instance that references the specific procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6606-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c6606-104">Syntax</span></span>  
  
```  
AddressOf procedurename  
```  
  
## <a name="parts"></a><span data-ttu-id="c6606-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="c6606-105">Parts</span></span>  
 `procedurename`  
 <span data-ttu-id="c6606-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="c6606-106">Required.</span></span> <span data-ttu-id="c6606-107">Yeni oluşturulan yordamı temsilci tarafından başvurulabilmesi için yordamı belirtir.</span><span class="sxs-lookup"><span data-stu-id="c6606-107">Specifies the procedure to be referenced by the newly created procedure delegate.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c6606-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c6606-108">Remarks</span></span>  
 <span data-ttu-id="c6606-109">`AddressOf` İşleci tarafından belirtilen işlevin işaret eden bir işlev temsilcisi oluşturur `procedurename`.</span><span class="sxs-lookup"><span data-stu-id="c6606-109">The `AddressOf` operator creates a function delegate that points to the function specified by `procedurename`.</span></span> <span data-ttu-id="c6606-110">Örnek hem yöntemi bir örnek yöntemi ardından işlev temsilcisi başvuruyor belirtilen yordam olduğunda.</span><span class="sxs-lookup"><span data-stu-id="c6606-110">When the specified procedure is an instance method then the function delegate refers to both the instance and the method.</span></span> <span data-ttu-id="c6606-111">Ardından, işlev temsilcisi çağrıldığında belirtilen örneğinin belirtilen yöntem çağrılır.</span><span class="sxs-lookup"><span data-stu-id="c6606-111">Then, when the function delegate is invoked the specified method of the specified instance is called.</span></span>  
  
 <span data-ttu-id="c6606-112">`AddressOf` İşleci, bir temsilci Oluşturucu işleneni kullanılabilir veya bir bağlamda, temsilci türü belirlenebilir derleyici tarafından kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c6606-112">The `AddressOf` operator can be used as the operand of a delegate constructor or it can be used in a context in which the type of the delegate can be determined by the compiler.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c6606-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="c6606-113">Example</span></span>  
 <span data-ttu-id="c6606-114">Bu örnekte `AddressOf` işlemek için bir temsilci atamak için işleç `Click` düğmesinin olay.</span><span class="sxs-lookup"><span data-stu-id="c6606-114">This example uses the `AddressOf` operator to designate a delegate to handle the `Click` event of a button.</span></span>  
  
 [!code-vb[VbVbalrDelegates#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#8)]  
  
## <a name="example"></a><span data-ttu-id="c6606-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="c6606-115">Example</span></span>  
 <span data-ttu-id="c6606-116">Aşağıdaki örnekte `AddressOf` iş parçacığı başlangıç işlevi atamak için işleç.</span><span class="sxs-lookup"><span data-stu-id="c6606-116">The following example uses the `AddressOf` operator to designate the startup function for a thread.</span></span>  
  
 [!code-vb[VbVbalrDelegates#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="c6606-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c6606-117">See also</span></span>
- [<span data-ttu-id="c6606-118">Declare Deyimi</span><span class="sxs-lookup"><span data-stu-id="c6606-118">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)
- [<span data-ttu-id="c6606-119">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="c6606-119">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="c6606-120">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="c6606-120">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="c6606-121">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="c6606-121">Delegates</span></span>](../../../visual-basic/programming-guide/language-features/delegates/index.md)
