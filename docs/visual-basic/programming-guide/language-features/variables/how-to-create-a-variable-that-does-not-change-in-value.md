---
title: "Nasıl yapılır: Değeri Değişmeyen Bir Değişken Oluşturma (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- variables [Visual Basic], read-only
- variables [Visual Basic], constant value
ms.assetid: 86b59266-25df-4635-ae15-9b59c411d036
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d1475553e64fef92ec3f3bb7e1b4fbfb357dbec8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-variable-that-does-not-change-in-value-visual-basic"></a><span data-ttu-id="5e57a-102">Nasıl yapılır: Değeri Değişmeyen Bir Değişken Oluşturma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5e57a-102">How to: Create a Variable that Does Not Change in Value (Visual Basic)</span></span>
<span data-ttu-id="5e57a-103">Değeri değişmeyen bir değişken kavramı çelişkili gibi görünebilir.</span><span class="sxs-lookup"><span data-stu-id="5e57a-103">The notion of a variable that does not change its value might appear to be contradictory.</span></span> <span data-ttu-id="5e57a-104">Ancak bazı durumlarda bir sabit uygun olmadığı ve sabit bir değere sahip bir değişken kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="5e57a-104">But there are situations when a constant is not feasible and it is useful to have a variable with a fixed value.</span></span> <span data-ttu-id="5e57a-105">Böyle bir durumda olan bir üye değişkenine tanımlayabilirsiniz [ReadOnly](../../../../visual-basic/language-reference/modifiers/readonly.md) anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="5e57a-105">In such a case you can define a member variable with the [ReadOnly](../../../../visual-basic/language-reference/modifiers/readonly.md) keyword.</span></span>  
  
 <span data-ttu-id="5e57a-106">Kullanamazsınız [Const deyimi](../../../../visual-basic/language-reference/statements/const-statement.md) bildirme ve aşağıdaki durumlarda sabit bir değer atamak için:</span><span class="sxs-lookup"><span data-stu-id="5e57a-106">You cannot use the [Const Statement](../../../../visual-basic/language-reference/statements/const-statement.md) to declare and assign a constant value in the following circumstances:</span></span>  
  
-   <span data-ttu-id="5e57a-107">`Const` Deyimi kullanmak istediğiniz veri türünü kabul etmiyor</span><span class="sxs-lookup"><span data-stu-id="5e57a-107">The `Const` statement does not accept the data type you want to use</span></span>  
  
-   <span data-ttu-id="5e57a-108">Derleme zamanında değeri biliyor musunuz</span><span class="sxs-lookup"><span data-stu-id="5e57a-108">You do not know the value at compile time</span></span>  
  
-   <span data-ttu-id="5e57a-109">Derleme zamanında sabit değer işlem oluşturulamıyor</span><span class="sxs-lookup"><span data-stu-id="5e57a-109">You are unable to compute the constant value at compile time</span></span>  
  
### <a name="to-create-a-variable-that-does-not-change-in-value"></a><span data-ttu-id="5e57a-110">Değeri değişmeyen bir değişken oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="5e57a-110">To create a variable that does not change in value</span></span>  
  
1.  <span data-ttu-id="5e57a-111">Modül düzeyinde sahip bir üye değişken bildirme [Dim deyimi](../../../../visual-basic/language-reference/statements/dim-statement.md)ve dahil [ReadOnly](../../../../visual-basic/language-reference/modifiers/readonly.md) anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="5e57a-111">At module level, declare a member variable with the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md), and include the [ReadOnly](../../../../visual-basic/language-reference/modifiers/readonly.md) keyword.</span></span>  
  
    ```  
    Dim ReadOnly timeStarted  
    ```  
  
     <span data-ttu-id="5e57a-112">Belirleyebileceğiniz `ReadOnly` yalnızca bir üye değişkenine üzerinde.</span><span class="sxs-lookup"><span data-stu-id="5e57a-112">You can specify `ReadOnly` only on a member variable.</span></span> <span data-ttu-id="5e57a-113">Başka bir deyişle, herhangi bir yordam dışında modülü düzeyinde değişkeni tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="5e57a-113">This means you must define the variable at module level, outside of any procedure.</span></span>  
  
2.  <span data-ttu-id="5e57a-114">Tek bir deyimde derleme zamanında değerinde işlem, bir başlatma yan tümcesinde kullanın. `Dim` deyimi.</span><span class="sxs-lookup"><span data-stu-id="5e57a-114">If you can compute the value in a single statement at compile time, use an initialization clause in the `Dim` statement.</span></span> <span data-ttu-id="5e57a-115">İzleyin [olarak](../../../../visual-basic/language-reference/statements/as-clause.md) yan tümcesi eşittir işareti (`=`), ardından bir ifade.</span><span class="sxs-lookup"><span data-stu-id="5e57a-115">Follow the [As](../../../../visual-basic/language-reference/statements/as-clause.md) clause with an equal sign (`=`), followed by an expression.</span></span> <span data-ttu-id="5e57a-116">Bu ifade bir sabit değere derleyici değerlendirebilir emin olun.</span><span class="sxs-lookup"><span data-stu-id="5e57a-116">Be sure the compiler can evaluate this expression to a constant value.</span></span>  
  
    ```  
    Dim ReadOnly timeStarted As Date = Now  
    ```  
  
     <span data-ttu-id="5e57a-117">Bir değere atayabileceğiniz bir `ReadOnly` değişken yalnızca bir kez.</span><span class="sxs-lookup"><span data-stu-id="5e57a-117">You can assign a value to a `ReadOnly` variable only once.</span></span> <span data-ttu-id="5e57a-118">Bunu yaptıktan sonra hiçbir kod hiç değerini değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5e57a-118">Once you do so, no code can ever change its value.</span></span>  
  
     <span data-ttu-id="5e57a-119">Değer derleme zamanında bilmiyorsanız ya da tek bir deyimde derleme zamanında hesaplayamıyor hala bunu bir oluşturucu çalışma zamanında atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5e57a-119">If you do not know the value at compile time, or cannot compute it at compile time in a single statement, you can still assign it at run time in a constructor.</span></span> <span data-ttu-id="5e57a-120">Bunu yapmak için bildirmelisiniz `ReadOnly` sınıf veya yapı düzeyinde değişken.</span><span class="sxs-lookup"><span data-stu-id="5e57a-120">To do this, you must declare the `ReadOnly` variable at class or structure level.</span></span> <span data-ttu-id="5e57a-121">Bu sınıf veya yapı oluşturucusu, değişkenin sabit değer işlem ve oluşturucudan döndürmeden önce değişkenine atayın.</span><span class="sxs-lookup"><span data-stu-id="5e57a-121">In the constructor for that class or structure, compute the variable's fixed value, and assign it to the variable before returning from the constructor.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e57a-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5e57a-122">See Also</span></span>  
 [<span data-ttu-id="5e57a-123">WriteOnly</span><span class="sxs-lookup"><span data-stu-id="5e57a-123">WriteOnly</span></span>](../../../../visual-basic/language-reference/modifiers/writeonly.md)  
 [<span data-ttu-id="5e57a-124">Const deyimi</span><span class="sxs-lookup"><span data-stu-id="5e57a-124">Const Statement</span></span>](../../../../visual-basic/language-reference/statements/const-statement.md)
