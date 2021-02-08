---
description: 'Daha fazla bilgi edinin: AddressOf Işleci (Visual Basic)'
title: AddressOf İşleci
ms.date: 07/20/2015
f1_keywords:
- AddressOf
- vb.AddressOf
helpviewer_keywords:
- AddressOf operator [Visual Basic]
- addresses, passing to API procedures
ms.assetid: 8105a59d-60d8-4ab5-b221-5899cdfacbf4
ms.openlocfilehash: 2aba8c26aa9581fe1070574b8c408e09bf063d1f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99774388"
---
# <a name="addressof-operator-visual-basic"></a><span data-ttu-id="16386-103">AddressOf İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="16386-103">AddressOf Operator (Visual Basic)</span></span>

<span data-ttu-id="16386-104">Belirli yordama başvuran bir temsilci örneği oluşturur.</span><span class="sxs-lookup"><span data-stu-id="16386-104">Creates a delegate instance that references the specific procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16386-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="16386-105">Syntax</span></span>  
  
```vb  
AddressOf procedurename  
```  
  
## <a name="parts"></a><span data-ttu-id="16386-106">Bölümler</span><span class="sxs-lookup"><span data-stu-id="16386-106">Parts</span></span>  

 `procedurename`  
 <span data-ttu-id="16386-107">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="16386-107">Required.</span></span> <span data-ttu-id="16386-108">Yeni oluşturulan temsilci tarafından başvurulacak prosedürü belirtir.</span><span class="sxs-lookup"><span data-stu-id="16386-108">Specifies the procedure to be referenced by the newly created delegate.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="16386-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="16386-109">Remarks</span></span>  

 <span data-ttu-id="16386-110">`AddressOf`İşleci, tarafından belirtilen Sub veya Function öğesine işaret eden bir temsilci oluşturur `procedurename` .</span><span class="sxs-lookup"><span data-stu-id="16386-110">The `AddressOf` operator creates a delegate that points to the sub or function specified by `procedurename`.</span></span> <span data-ttu-id="16386-111">Belirtilen yordam bir örnek yöntemi olduğunda, temsilci hem örneğe hem de yöntemine başvurur.</span><span class="sxs-lookup"><span data-stu-id="16386-111">When the specified procedure is an instance method then the delegate refers to both the instance and the method.</span></span> <span data-ttu-id="16386-112">Ardından, temsilci çağrıldığında belirtilen örnek için belirtilen yöntem çağrılır.</span><span class="sxs-lookup"><span data-stu-id="16386-112">Then, when the  delegate is invoked the specified method of the specified instance is called.</span></span>  
  
 <span data-ttu-id="16386-113">`AddressOf`İşleci, bir temsilci oluşturucusunun işleneni olarak kullanılabilir ya da temsilci türünün derleyici tarafından belirlenebileceği bir bağlamda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="16386-113">The `AddressOf` operator can be used as the operand of a delegate constructor or it can be used in a context in which the type of the delegate can be determined by the compiler.</span></span>  
  
## <a name="example"></a><span data-ttu-id="16386-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="16386-114">Example</span></span>  

 <span data-ttu-id="16386-115">Bu örnek, `AddressOf` bir düğmenin olayını işlemek üzere bir temsilci belirlemek için işlecini kullanır `Click` .</span><span class="sxs-lookup"><span data-stu-id="16386-115">This example uses the `AddressOf` operator to designate a delegate to handle the `Click` event of a button.</span></span>  
  
 [!code-vb[VbVbalrDelegates#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#8)]  
  
## <a name="example"></a><span data-ttu-id="16386-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="16386-116">Example</span></span>  

 <span data-ttu-id="16386-117">Aşağıdaki örnek, `AddressOf` bir iş parçacığının başlangıç işlevini belirlemek için işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="16386-117">The following example uses the `AddressOf` operator to designate the startup function for a thread.</span></span>  
  
 [!code-vb[VbVbalrDelegates#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="16386-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="16386-118">See also</span></span>

- [<span data-ttu-id="16386-119">Declare Deyimi</span><span class="sxs-lookup"><span data-stu-id="16386-119">Declare Statement</span></span>](../statements/declare-statement.md)
- [<span data-ttu-id="16386-120">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="16386-120">Function Statement</span></span>](../statements/function-statement.md)
- [<span data-ttu-id="16386-121">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="16386-121">Sub Statement</span></span>](../statements/sub-statement.md)
- [<span data-ttu-id="16386-122">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="16386-122">Delegates</span></span>](../../programming-guide/language-features/delegates/index.md)
