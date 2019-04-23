---
title: 'Nasıl yapılır: (Visual Basic) değeri değişmeyen bir değişken oluşturma'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], read-only
- variables [Visual Basic], constant value
ms.assetid: 86b59266-25df-4635-ae15-9b59c411d036
ms.openlocfilehash: 7180e5141572d219ed02c57103e9d4b80cde536e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59342940"
---
# <a name="how-to-create-a-variable-that-does-not-change-in-value-visual-basic"></a><span data-ttu-id="d41ed-102">Nasıl yapılır: (Visual Basic) değeri değişmeyen bir değişken oluşturma</span><span class="sxs-lookup"><span data-stu-id="d41ed-102">How to: Create a Variable that Does Not Change in Value (Visual Basic)</span></span>
<span data-ttu-id="d41ed-103">Bir değişkenin değerini değiştirmez kavramımız çelişkili görünebilir.</span><span class="sxs-lookup"><span data-stu-id="d41ed-103">The notion of a variable that does not change its value might appear to be contradictory.</span></span> <span data-ttu-id="d41ed-104">Ancak bazı durumlarda bir sabit uygun olmadığı durumlarda ve sabit bir değere sahip bir değişken sağlamak kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="d41ed-104">But there are situations when a constant is not feasible and it is useful to have a variable with a fixed value.</span></span> <span data-ttu-id="d41ed-105">Böyle bir durumda olan bir üye değişkeni tanımlayabilirsiniz [salt okunur](../../../../visual-basic/language-reference/modifiers/readonly.md) anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="d41ed-105">In such a case you can define a member variable with the [ReadOnly](../../../../visual-basic/language-reference/modifiers/readonly.md) keyword.</span></span>  
  
 <span data-ttu-id="d41ed-106">Kullanamazsınız [Const deyimi](../../../../visual-basic/language-reference/statements/const-statement.md) bildirmek ve aşağıdaki durumlarda bir sabit değer atamak için:</span><span class="sxs-lookup"><span data-stu-id="d41ed-106">You cannot use the [Const Statement](../../../../visual-basic/language-reference/statements/const-statement.md) to declare and assign a constant value in the following circumstances:</span></span>  
  
-   <span data-ttu-id="d41ed-107">`Const` Deyimi kullanmak istediğiniz veri türünü kabul etmiyor</span><span class="sxs-lookup"><span data-stu-id="d41ed-107">The `Const` statement does not accept the data type you want to use</span></span>  
  
-   <span data-ttu-id="d41ed-108">Derleme zamanında bir değer kattığını değil</span><span class="sxs-lookup"><span data-stu-id="d41ed-108">You do not know the value at compile time</span></span>  
  
-   <span data-ttu-id="d41ed-109">Sabit değer derleme zamanında işlem belirleyemiyoruz</span><span class="sxs-lookup"><span data-stu-id="d41ed-109">You are unable to compute the constant value at compile time</span></span>  
  
### <a name="to-create-a-variable-that-does-not-change-in-value"></a><span data-ttu-id="d41ed-110">Değeri değişmeyen bir değişken oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="d41ed-110">To create a variable that does not change in value</span></span>  
  
1. <span data-ttu-id="d41ed-111">Modül düzeyinde olan bir üye değişkeni bildirme [Dim deyimi](../../../../visual-basic/language-reference/statements/dim-statement.md)ve [salt okunur](../../../../visual-basic/language-reference/modifiers/readonly.md) anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="d41ed-111">At module level, declare a member variable with the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md), and include the [ReadOnly](../../../../visual-basic/language-reference/modifiers/readonly.md) keyword.</span></span>  
  
    ```  
    Dim ReadOnly timeStarted  
    ```  
  
     <span data-ttu-id="d41ed-112">Belirtebileceğiniz `ReadOnly` yalnızca bir üye değişkeni üzerinde.</span><span class="sxs-lookup"><span data-stu-id="d41ed-112">You can specify `ReadOnly` only on a member variable.</span></span> <span data-ttu-id="d41ed-113">Başka bir deyişle, her türlü yordam dışında Modül düzeyinde değişkeni tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d41ed-113">This means you must define the variable at module level, outside of any procedure.</span></span>  
  
2. <span data-ttu-id="d41ed-114">Değerin tek bir deyimde derleme zamanında bilgi işlem, bir başlatma yan tümcesi içinde kullanın. `Dim` deyimi.</span><span class="sxs-lookup"><span data-stu-id="d41ed-114">If you can compute the value in a single statement at compile time, use an initialization clause in the `Dim` statement.</span></span> <span data-ttu-id="d41ed-115">İzleyin [olarak](../../../../visual-basic/language-reference/statements/as-clause.md) yan tümcesiyle birlikte bir eşittir işareti (`=`) ve ardından bir ifade.</span><span class="sxs-lookup"><span data-stu-id="d41ed-115">Follow the [As](../../../../visual-basic/language-reference/statements/as-clause.md) clause with an equal sign (`=`), followed by an expression.</span></span> <span data-ttu-id="d41ed-116">Derleyici, bu ifade bir sabit değere değerlendirebilirsiniz emin olun.</span><span class="sxs-lookup"><span data-stu-id="d41ed-116">Be sure the compiler can evaluate this expression to a constant value.</span></span>  
  
    ```  
    Dim ReadOnly timeStarted As Date = Now  
    ```  
  
     <span data-ttu-id="d41ed-117">Bir değer atamak için bir `ReadOnly` değişken yalnızca bir kez.</span><span class="sxs-lookup"><span data-stu-id="d41ed-117">You can assign a value to a `ReadOnly` variable only once.</span></span> <span data-ttu-id="d41ed-118">Bunu yaptıktan sonra kod her zamankinden değerini değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d41ed-118">Once you do so, no code can ever change its value.</span></span>  
  
     <span data-ttu-id="d41ed-119">Değer derleme zamanında bilmiyorsanız veya tek bir deyimde derleme zamanında hesaplayamıyor, yine de uygulamayı çalışma zamanında bir oluşturucuda atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d41ed-119">If you do not know the value at compile time, or cannot compute it at compile time in a single statement, you can still assign it at run time in a constructor.</span></span> <span data-ttu-id="d41ed-120">Bunu yapmak için size bildirmelidir `ReadOnly` sınıf veya yapı düzeyinde değişken.</span><span class="sxs-lookup"><span data-stu-id="d41ed-120">To do this, you must declare the `ReadOnly` variable at class or structure level.</span></span> <span data-ttu-id="d41ed-121">Bu sınıf veya yapı için oluşturucu, sabit değişkenin değerini hesaplamak ve oluşturucudan döndürmeden önce değişkene atayın.</span><span class="sxs-lookup"><span data-stu-id="d41ed-121">In the constructor for that class or structure, compute the variable's fixed value, and assign it to the variable before returning from the constructor.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d41ed-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d41ed-122">See also</span></span>

- [<span data-ttu-id="d41ed-123">WriteOnly</span><span class="sxs-lookup"><span data-stu-id="d41ed-123">WriteOnly</span></span>](../../../../visual-basic/language-reference/modifiers/writeonly.md)
- [<span data-ttu-id="d41ed-124">Const Deyimi</span><span class="sxs-lookup"><span data-stu-id="d41ed-124">Const Statement</span></span>](../../../../visual-basic/language-reference/statements/const-statement.md)
