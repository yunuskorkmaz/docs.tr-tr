---
title: 'Nasıl yapılır: Değeri Değişmeyen Bir Değişken Oluşturma'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], read-only
- variables [Visual Basic], constant value
ms.assetid: 86b59266-25df-4635-ae15-9b59c411d036
ms.openlocfilehash: d5d8a6b066ae7e8795afd2f788b60823d8efdafa
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348640"
---
# <a name="how-to-create-a-variable-that-does-not-change-in-value-visual-basic"></a><span data-ttu-id="14ce6-102">Nasıl yapılır: Değeri Değişmeyen Bir Değişken Oluşturma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="14ce6-102">How to: Create a Variable that Does Not Change in Value (Visual Basic)</span></span>

<span data-ttu-id="14ce6-103">Değerini değiştirolmayan bir değişken kavramı, çelişkili gibi görünebilir.</span><span class="sxs-lookup"><span data-stu-id="14ce6-103">The notion of a variable that does not change its value might appear to be contradictory.</span></span> <span data-ttu-id="14ce6-104">Ancak, bir sabit değer mümkün olmadığında ve sabit bir değere sahip bir değişken olması faydalı olduğunda durumlar vardır.</span><span class="sxs-lookup"><span data-stu-id="14ce6-104">But there are situations when a constant is not feasible and it is useful to have a variable with a fixed value.</span></span> <span data-ttu-id="14ce6-105">Böyle bir durumda, [salt okunur](../../../../visual-basic/language-reference/modifiers/readonly.md) anahtar sözcüğüyle bir üye değişkeni tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="14ce6-105">In such a case you can define a member variable with the [ReadOnly](../../../../visual-basic/language-reference/modifiers/readonly.md) keyword.</span></span>

<span data-ttu-id="14ce6-106">[Const ifadesini](../../../../visual-basic/language-reference/statements/const-statement.md) aşağıdaki koşullarda bir sabit değer bildirmek ve atamak için kullanamazsınız:</span><span class="sxs-lookup"><span data-stu-id="14ce6-106">You cannot use the [Const Statement](../../../../visual-basic/language-reference/statements/const-statement.md) to declare and assign a constant value in the following circumstances:</span></span>

- <span data-ttu-id="14ce6-107">`Const` deyimin kullanmak istediğiniz veri türü kabul etmez</span><span class="sxs-lookup"><span data-stu-id="14ce6-107">The `Const` statement does not accept the data type you want to use</span></span>

- <span data-ttu-id="14ce6-108">Derleme zamanında değeri bilemezsiniz</span><span class="sxs-lookup"><span data-stu-id="14ce6-108">You do not know the value at compile time</span></span>

- <span data-ttu-id="14ce6-109">Derleme zamanında sabit değeri hesaplayamıyor</span><span class="sxs-lookup"><span data-stu-id="14ce6-109">You are unable to compute the constant value at compile time</span></span>

### <a name="to-create-a-variable-that-does-not-change-in-value"></a><span data-ttu-id="14ce6-110">Değerde değişiklik olmayan bir değişken oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="14ce6-110">To create a variable that does not change in value</span></span>

1. <span data-ttu-id="14ce6-111">Modül düzeyinde, [Dim ifadesiyle](../../../../visual-basic/language-reference/statements/dim-statement.md)bir üye değişkeni bildirin ve [salt okunur](../../../../visual-basic/language-reference/modifiers/readonly.md) anahtar sözcüğünü ekleyin.</span><span class="sxs-lookup"><span data-stu-id="14ce6-111">At module level, declare a member variable with the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md), and include the [ReadOnly](../../../../visual-basic/language-reference/modifiers/readonly.md) keyword.</span></span>

    ```vb
    Dim ReadOnly timeStarted
    ```

    <span data-ttu-id="14ce6-112">Yalnızca üye değişkeninde `ReadOnly` belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="14ce6-112">You can specify `ReadOnly` only on a member variable.</span></span> <span data-ttu-id="14ce6-113">Bu, herhangi bir yordamın dışında değişkeni modül düzeyinde tanımlamanız gereken anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="14ce6-113">This means you must define the variable at module level, outside of any procedure.</span></span>

2. <span data-ttu-id="14ce6-114">Derleme zamanında değeri tek bir ifadede hesapladıysanız, `Dim` deyimindeki bir başlatma yan tümcesi kullanın.</span><span class="sxs-lookup"><span data-stu-id="14ce6-114">If you can compute the value in a single statement at compile time, use an initialization clause in the `Dim` statement.</span></span> <span data-ttu-id="14ce6-115">[As](../../../../visual-basic/language-reference/statements/as-clause.md) yan tümcesini, eşittir işareti (`=`) ve ardından bir ifade ile izleyin.</span><span class="sxs-lookup"><span data-stu-id="14ce6-115">Follow the [As](../../../../visual-basic/language-reference/statements/as-clause.md) clause with an equal sign (`=`), followed by an expression.</span></span> <span data-ttu-id="14ce6-116">Derleyicinin bu ifadeyi sabit bir değere değerlendirebilmesi için emin olun.</span><span class="sxs-lookup"><span data-stu-id="14ce6-116">Be sure the compiler can evaluate this expression to a constant value.</span></span>

    ```vb
    Dim ReadOnly timeStarted As Date = Now
    ```

    <span data-ttu-id="14ce6-117">Bir `ReadOnly` değişkenine yalnızca bir kez değer atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="14ce6-117">You can assign a value to a `ReadOnly` variable only once.</span></span> <span data-ttu-id="14ce6-118">Bunu yaptığınızda, herhangi bir kod hiçbir zaman değerini değiştiremez.</span><span class="sxs-lookup"><span data-stu-id="14ce6-118">Once you do so, no code can ever change its value.</span></span>

    <span data-ttu-id="14ce6-119">Derleme zamanında değeri bilemezsiniz veya tek bir ifadede derleme zamanında hesapladıysanız, yine de bir oluşturucuda çalışma zamanında atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="14ce6-119">If you do not know the value at compile time, or cannot compute it at compile time in a single statement, you can still assign it at run time in a constructor.</span></span> <span data-ttu-id="14ce6-120">Bunu yapmak için, sınıf veya yapı düzeyinde `ReadOnly` değişkenini bildirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="14ce6-120">To do this, you must declare the `ReadOnly` variable at class or structure level.</span></span> <span data-ttu-id="14ce6-121">Bu sınıf veya yapı için oluşturucuda, değişkenin sabit değerini hesaplayın ve oluşturucuyu döndürmeden önce değişkenine atayın.</span><span class="sxs-lookup"><span data-stu-id="14ce6-121">In the constructor for that class or structure, compute the variable's fixed value, and assign it to the variable before returning from the constructor.</span></span>

## <a name="see-also"></a><span data-ttu-id="14ce6-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="14ce6-122">See also</span></span>

- [<span data-ttu-id="14ce6-123">WriteOnly</span><span class="sxs-lookup"><span data-stu-id="14ce6-123">WriteOnly</span></span>](../../../../visual-basic/language-reference/modifiers/writeonly.md)
- [<span data-ttu-id="14ce6-124">Const Deyimi</span><span class="sxs-lookup"><span data-stu-id="14ce6-124">Const Statement</span></span>](../../../../visual-basic/language-reference/statements/const-statement.md)
