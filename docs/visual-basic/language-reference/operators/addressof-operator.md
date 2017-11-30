---
title: "AddressOf İşleci (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- AddressOf
- vb.AddressOf
helpviewer_keywords:
- AddressOf operator [Visual Basic]
- addresses, passing to API procedures
ms.assetid: 8105a59d-60d8-4ab5-b221-5899cdfacbf4
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 52560a2d9071373fd28f7aad2e485da08324656d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="addressof-operator-visual-basic"></a><span data-ttu-id="cf5e4-102">AddressOf İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cf5e4-102">AddressOf Operator (Visual Basic)</span></span>
<span data-ttu-id="cf5e4-103">Özel yordam başvuruda bulunan bir yordam temsilci örneği oluşturur.</span><span class="sxs-lookup"><span data-stu-id="cf5e4-103">Creates a procedure delegate instance that references the specific procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf5e4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cf5e4-104">Syntax</span></span>  
  
```  
AddressOf procedurename  
```  
  
## <a name="parts"></a><span data-ttu-id="cf5e4-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="cf5e4-105">Parts</span></span>  
 `procedurename`  
 <span data-ttu-id="cf5e4-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="cf5e4-106">Required.</span></span> <span data-ttu-id="cf5e4-107">Yeni oluşturulan yordamı temsilci tarafından başvurulan yordamı belirtir.</span><span class="sxs-lookup"><span data-stu-id="cf5e4-107">Specifies the procedure to be referenced by the newly created procedure delegate.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cf5e4-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cf5e4-108">Remarks</span></span>  
 <span data-ttu-id="cf5e4-109">`AddressOf` İşleci tarafından belirtilen işlevin işaret eden bir işlev temsilcisi oluşturur `procedurename`.</span><span class="sxs-lookup"><span data-stu-id="cf5e4-109">The `AddressOf` operator creates a function delegate that points to the function specified by `procedurename`.</span></span> <span data-ttu-id="cf5e4-110">Örnek ve yöntemi için örnek yöntemi sonra işlev temsilcisi başvuruyor belirtilen yordam olduğunda.</span><span class="sxs-lookup"><span data-stu-id="cf5e4-110">When the specified procedure is an instance method then the function delegate refers to both the instance and the method.</span></span> <span data-ttu-id="cf5e4-111">Ardından, işlev temsilcisi çağrıldığında belirtilen örneğinin belirtilen yöntem çağrılır.</span><span class="sxs-lookup"><span data-stu-id="cf5e4-111">Then, when the function delegate is invoked the specified method of the specified instance is called.</span></span>  
  
 <span data-ttu-id="cf5e4-112">`AddressOf` İşleci temsilci Oluşturucu işleneni olarak kullanılabilir veya hangi temsilci türü belirlenebilir derleyici tarafından bağlamda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="cf5e4-112">The `AddressOf` operator can be used as the operand of a delegate constructor or it can be used in a context in which the type of the delegate can be determined by the compiler.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cf5e4-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="cf5e4-113">Example</span></span>  
 <span data-ttu-id="cf5e4-114">Bu örnekte `AddressOf` işlemek için temsilci atamak işleci `Click` düğmesinin olay.</span><span class="sxs-lookup"><span data-stu-id="cf5e4-114">This example uses the `AddressOf` operator to designate a delegate to handle the `Click` event of a button.</span></span>  
  
 [!code-vb[VbVbalrDelegates#8](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addressof-operator_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="cf5e4-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="cf5e4-115">Example</span></span>  
 <span data-ttu-id="cf5e4-116">Aşağıdaki örnek kullanır `AddressOf` başlangıç işlevi için bir iş parçacığı atamak işleci.</span><span class="sxs-lookup"><span data-stu-id="cf5e4-116">The following example uses the `AddressOf` operator to designate the startup function for a thread.</span></span>  
  
 [!code-vb[VbVbalrDelegates#9](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addressof-operator_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="cf5e4-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cf5e4-117">See Also</span></span>  
 [<span data-ttu-id="cf5e4-118">Declare deyimi</span><span class="sxs-lookup"><span data-stu-id="cf5e4-118">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
 [<span data-ttu-id="cf5e4-119">Function deyimi</span><span class="sxs-lookup"><span data-stu-id="cf5e4-119">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
 [<span data-ttu-id="cf5e4-120">Sub deyimi</span><span class="sxs-lookup"><span data-stu-id="cf5e4-120">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [<span data-ttu-id="cf5e4-121">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="cf5e4-121">Delegates</span></span>](../../../visual-basic/programming-guide/language-features/delegates/index.md)
