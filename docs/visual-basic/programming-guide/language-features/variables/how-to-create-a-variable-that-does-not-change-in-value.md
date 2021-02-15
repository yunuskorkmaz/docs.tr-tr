---
description: 'Şu konuda daha fazla bilgi edinin: nasıl yapılır: değerde değişmez bir değişken oluşturma (Visual Basic)'
title: 'Nasıl yapılır: Değeri Değişmeyen Bir Değişken Oluşturma'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], read-only
- variables [Visual Basic], constant value
ms.assetid: 86b59266-25df-4635-ae15-9b59c411d036
ms.openlocfilehash: 0392a27249de3bf604a73c8f8aaa16caf6f1c3e2
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100481941"
---
# <a name="how-to-create-a-variable-that-does-not-change-in-value-visual-basic"></a><span data-ttu-id="e2a31-103">Nasıl yapılır: Değeri Değişmeyen Bir Değişken Oluşturma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e2a31-103">How to: Create a Variable that Does Not Change in Value (Visual Basic)</span></span>

<span data-ttu-id="e2a31-104">Değerini değiştirolmayan bir değişken kavramı, çelişkili gibi görünebilir.</span><span class="sxs-lookup"><span data-stu-id="e2a31-104">The notion of a variable that does not change its value might appear to be contradictory.</span></span> <span data-ttu-id="e2a31-105">Ancak, bir sabit değer mümkün olmadığında ve sabit bir değere sahip bir değişken olması faydalı olduğunda durumlar vardır.</span><span class="sxs-lookup"><span data-stu-id="e2a31-105">But there are situations when a constant is not feasible and it is useful to have a variable with a fixed value.</span></span> <span data-ttu-id="e2a31-106">Böyle bir durumda, [salt okunur](../../../language-reference/modifiers/readonly.md) anahtar sözcüğüyle bir üye değişkeni tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e2a31-106">In such a case you can define a member variable with the [ReadOnly](../../../language-reference/modifiers/readonly.md) keyword.</span></span>

<span data-ttu-id="e2a31-107">[Const ifadesini](../../../language-reference/statements/const-statement.md) aşağıdaki koşullarda bir sabit değer bildirmek ve atamak için kullanamazsınız:</span><span class="sxs-lookup"><span data-stu-id="e2a31-107">You cannot use the [Const Statement](../../../language-reference/statements/const-statement.md) to declare and assign a constant value in the following circumstances:</span></span>

- <span data-ttu-id="e2a31-108">`Const`İfade, kullanmak istediğiniz veri türünü kabul etmiyor</span><span class="sxs-lookup"><span data-stu-id="e2a31-108">The `Const` statement does not accept the data type you want to use</span></span>

- <span data-ttu-id="e2a31-109">Derleme zamanında değeri bilemezsiniz</span><span class="sxs-lookup"><span data-stu-id="e2a31-109">You do not know the value at compile time</span></span>

- <span data-ttu-id="e2a31-110">Derleme zamanında sabit değeri hesaplayamıyor</span><span class="sxs-lookup"><span data-stu-id="e2a31-110">You are unable to compute the constant value at compile time</span></span>

### <a name="to-create-a-variable-that-does-not-change-in-value"></a><span data-ttu-id="e2a31-111">Değerde değişiklik olmayan bir değişken oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="e2a31-111">To create a variable that does not change in value</span></span>

1. <span data-ttu-id="e2a31-112">Modül düzeyinde, [Dim ifadesiyle](../../../language-reference/statements/dim-statement.md)bir üye değişkeni bildirin ve [salt okunur](../../../language-reference/modifiers/readonly.md) anahtar sözcüğünü ekleyin.</span><span class="sxs-lookup"><span data-stu-id="e2a31-112">At module level, declare a member variable with the [Dim Statement](../../../language-reference/statements/dim-statement.md), and include the [ReadOnly](../../../language-reference/modifiers/readonly.md) keyword.</span></span>

    ```vb
    Dim ReadOnly timeStarted
    ```

    <span data-ttu-id="e2a31-113">`ReadOnly`Yalnızca bir üye değişkeninde belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e2a31-113">You can specify `ReadOnly` only on a member variable.</span></span> <span data-ttu-id="e2a31-114">Bu, herhangi bir yordamın dışında değişkeni modül düzeyinde tanımlamanız gereken anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="e2a31-114">This means you must define the variable at module level, outside of any procedure.</span></span>

2. <span data-ttu-id="e2a31-115">Derleme zamanında değeri tek bir ifadede hesapladıysanız, deyimindeki bir başlatma yan tümcesini kullanın `Dim` .</span><span class="sxs-lookup"><span data-stu-id="e2a31-115">If you can compute the value in a single statement at compile time, use an initialization clause in the `Dim` statement.</span></span> <span data-ttu-id="e2a31-116">Eşittir işareti [](../../../language-reference/statements/as-clause.md) ( `=` ) ve ardından bir ifade gelen as yan tümcesini izleyin.</span><span class="sxs-lookup"><span data-stu-id="e2a31-116">Follow the [As](../../../language-reference/statements/as-clause.md) clause with an equal sign (`=`), followed by an expression.</span></span> <span data-ttu-id="e2a31-117">Derleyicinin bu ifadeyi sabit bir değere değerlendirebilmesi için emin olun.</span><span class="sxs-lookup"><span data-stu-id="e2a31-117">Be sure the compiler can evaluate this expression to a constant value.</span></span>

    ```vb
    Dim ReadOnly timeStarted As Date = Now
    ```

    <span data-ttu-id="e2a31-118">Bir değişkene yalnızca bir kez değer atayabilirsiniz `ReadOnly` .</span><span class="sxs-lookup"><span data-stu-id="e2a31-118">You can assign a value to a `ReadOnly` variable only once.</span></span> <span data-ttu-id="e2a31-119">Bunu yaptığınızda, herhangi bir kod hiçbir zaman değerini değiştiremez.</span><span class="sxs-lookup"><span data-stu-id="e2a31-119">Once you do so, no code can ever change its value.</span></span>

    <span data-ttu-id="e2a31-120">Derleme zamanında değeri bilemezsiniz veya tek bir ifadede derleme zamanında hesapladıysanız, yine de bir oluşturucuda çalışma zamanında atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e2a31-120">If you do not know the value at compile time, or cannot compute it at compile time in a single statement, you can still assign it at run time in a constructor.</span></span> <span data-ttu-id="e2a31-121">Bunu yapmak için `ReadOnly` değişkeni sınıf veya yapı düzeyinde bildirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="e2a31-121">To do this, you must declare the `ReadOnly` variable at class or structure level.</span></span> <span data-ttu-id="e2a31-122">Bu sınıf veya yapı için oluşturucuda, değişkenin sabit değerini hesaplayın ve oluşturucuyu döndürmeden önce değişkenine atayın.</span><span class="sxs-lookup"><span data-stu-id="e2a31-122">In the constructor for that class or structure, compute the variable's fixed value, and assign it to the variable before returning from the constructor.</span></span>

## <a name="see-also"></a><span data-ttu-id="e2a31-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e2a31-123">See also</span></span>

- [<span data-ttu-id="e2a31-124">WriteOnly</span><span class="sxs-lookup"><span data-stu-id="e2a31-124">WriteOnly</span></span>](../../../language-reference/modifiers/writeonly.md)
- [<span data-ttu-id="e2a31-125">Const Deyimi</span><span class="sxs-lookup"><span data-stu-id="e2a31-125">Const Statement</span></span>](../../../language-reference/statements/const-statement.md)
