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
ms.openlocfilehash: 2ebadf5ded1a23fe46b8e16cf18ae265b5d3c255
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/28/2019
ms.locfileid: "71591662"
---
# <a name="addressof-operator-visual-basic"></a><span data-ttu-id="830bc-102">AddressOf İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="830bc-102">AddressOf Operator (Visual Basic)</span></span>
<span data-ttu-id="830bc-103">Belirli yordama başvuran bir temsilci örneği oluşturur.</span><span class="sxs-lookup"><span data-stu-id="830bc-103">Creates a delegate instance that references the specific procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="830bc-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="830bc-104">Syntax</span></span>  
  
```vb  
AddressOf procedurename  
```  
  
## <a name="parts"></a><span data-ttu-id="830bc-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="830bc-105">Parts</span></span>  
 `procedurename`  
 <span data-ttu-id="830bc-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="830bc-106">Required.</span></span> <span data-ttu-id="830bc-107">Yeni oluşturulan temsilci tarafından başvurulacak prosedürü belirtir.</span><span class="sxs-lookup"><span data-stu-id="830bc-107">Specifies the procedure to be referenced by the newly created delegate.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="830bc-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="830bc-108">Remarks</span></span>  
 <span data-ttu-id="830bc-109">@No__t-0 işleci, `procedurename` tarafından belirtilen Sub veya Function öğesine işaret eden bir temsilci oluşturur.</span><span class="sxs-lookup"><span data-stu-id="830bc-109">The `AddressOf` operator creates a delegate that points to the sub or function specified by `procedurename`.</span></span> <span data-ttu-id="830bc-110">Belirtilen yordam bir örnek yöntemi olduğunda, temsilci hem örneğe hem de yöntemine başvurur.</span><span class="sxs-lookup"><span data-stu-id="830bc-110">When the specified procedure is an instance method then the delegate refers to both the instance and the method.</span></span> <span data-ttu-id="830bc-111">Ardından, temsilci çağrıldığında belirtilen örnek için belirtilen yöntem çağrılır.</span><span class="sxs-lookup"><span data-stu-id="830bc-111">Then, when the  delegate is invoked the specified method of the specified instance is called.</span></span>  
  
 <span data-ttu-id="830bc-112">@No__t-0 işleci bir temsilci oluşturucusunun işleneni olarak kullanılabilir ya da temsilci türünün derleyici tarafından belirlenebileceği bir bağlamda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="830bc-112">The `AddressOf` operator can be used as the operand of a delegate constructor or it can be used in a context in which the type of the delegate can be determined by the compiler.</span></span>  
  
## <a name="example"></a><span data-ttu-id="830bc-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="830bc-113">Example</span></span>  
 <span data-ttu-id="830bc-114">Bu örnek, bir düğmenin `Click` olayını işlemek üzere bir temsilci belirlemek için `AddressOf` işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="830bc-114">This example uses the `AddressOf` operator to designate a delegate to handle the `Click` event of a button.</span></span>  
  
 [!code-vb[VbVbalrDelegates#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#8)]  
  
## <a name="example"></a><span data-ttu-id="830bc-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="830bc-115">Example</span></span>  
 <span data-ttu-id="830bc-116">Aşağıdaki örnek, bir iş parçacığının başlangıç işlevini belirlemek için `AddressOf` işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="830bc-116">The following example uses the `AddressOf` operator to designate the startup function for a thread.</span></span>  
  
 [!code-vb[VbVbalrDelegates#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="830bc-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="830bc-117">See also</span></span>

- [<span data-ttu-id="830bc-118">Declare Deyimi</span><span class="sxs-lookup"><span data-stu-id="830bc-118">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)
- [<span data-ttu-id="830bc-119">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="830bc-119">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="830bc-120">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="830bc-120">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="830bc-121">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="830bc-121">Delegates</span></span>](../../../visual-basic/programming-guide/language-features/delegates/index.md)
