---
title: AddressOf İşleci
ms.date: 07/20/2015
f1_keywords:
- AddressOf
- vb.AddressOf
helpviewer_keywords:
- AddressOf operator [Visual Basic]
- addresses, passing to API procedures
ms.assetid: 8105a59d-60d8-4ab5-b221-5899cdfacbf4
ms.openlocfilehash: 3e7db8e7329ce8d21b6e07863e6f1673a6389608
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84372070"
---
# <a name="addressof-operator-visual-basic"></a><span data-ttu-id="4d309-102">AddressOf İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4d309-102">AddressOf Operator (Visual Basic)</span></span>
<span data-ttu-id="4d309-103">Belirli yordama başvuran bir temsilci örneği oluşturur.</span><span class="sxs-lookup"><span data-stu-id="4d309-103">Creates a delegate instance that references the specific procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d309-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4d309-104">Syntax</span></span>  
  
```vb  
AddressOf procedurename  
```  
  
## <a name="parts"></a><span data-ttu-id="4d309-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="4d309-105">Parts</span></span>  
 `procedurename`  
 <span data-ttu-id="4d309-106">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="4d309-106">Required.</span></span> <span data-ttu-id="4d309-107">Yeni oluşturulan temsilci tarafından başvurulacak prosedürü belirtir.</span><span class="sxs-lookup"><span data-stu-id="4d309-107">Specifies the procedure to be referenced by the newly created delegate.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4d309-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4d309-108">Remarks</span></span>  
 <span data-ttu-id="4d309-109">`AddressOf`İşleci, tarafından belirtilen Sub veya Function öğesine işaret eden bir temsilci oluşturur `procedurename` .</span><span class="sxs-lookup"><span data-stu-id="4d309-109">The `AddressOf` operator creates a delegate that points to the sub or function specified by `procedurename`.</span></span> <span data-ttu-id="4d309-110">Belirtilen yordam bir örnek yöntemi olduğunda, temsilci hem örneğe hem de yöntemine başvurur.</span><span class="sxs-lookup"><span data-stu-id="4d309-110">When the specified procedure is an instance method then the delegate refers to both the instance and the method.</span></span> <span data-ttu-id="4d309-111">Ardından, temsilci çağrıldığında belirtilen örnek için belirtilen yöntem çağrılır.</span><span class="sxs-lookup"><span data-stu-id="4d309-111">Then, when the  delegate is invoked the specified method of the specified instance is called.</span></span>  
  
 <span data-ttu-id="4d309-112">`AddressOf`İşleci, bir temsilci oluşturucusunun işleneni olarak kullanılabilir ya da temsilci türünün derleyici tarafından belirlenebileceği bir bağlamda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4d309-112">The `AddressOf` operator can be used as the operand of a delegate constructor or it can be used in a context in which the type of the delegate can be determined by the compiler.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4d309-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="4d309-113">Example</span></span>  
 <span data-ttu-id="4d309-114">Bu örnek, `AddressOf` bir düğmenin olayını işlemek üzere bir temsilci belirlemek için işlecini kullanır `Click` .</span><span class="sxs-lookup"><span data-stu-id="4d309-114">This example uses the `AddressOf` operator to designate a delegate to handle the `Click` event of a button.</span></span>  
  
 [!code-vb[VbVbalrDelegates#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#8)]  
  
## <a name="example"></a><span data-ttu-id="4d309-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="4d309-115">Example</span></span>  
 <span data-ttu-id="4d309-116">Aşağıdaki örnek, `AddressOf` bir iş parçacığının başlangıç işlevini belirlemek için işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="4d309-116">The following example uses the `AddressOf` operator to designate the startup function for a thread.</span></span>  
  
 [!code-vb[VbVbalrDelegates#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="4d309-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4d309-117">See also</span></span>

- [<span data-ttu-id="4d309-118">Declare Deyimi</span><span class="sxs-lookup"><span data-stu-id="4d309-118">Declare Statement</span></span>](../statements/declare-statement.md)
- [<span data-ttu-id="4d309-119">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="4d309-119">Function Statement</span></span>](../statements/function-statement.md)
- [<span data-ttu-id="4d309-120">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="4d309-120">Sub Statement</span></span>](../statements/sub-statement.md)
- [<span data-ttu-id="4d309-121">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="4d309-121">Delegates</span></span>](../../programming-guide/language-features/delegates/index.md)
