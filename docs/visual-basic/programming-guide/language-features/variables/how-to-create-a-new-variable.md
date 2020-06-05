---
title: 'Nasıl yapılır: Yeni Değişken Oluşturma'
ms.date: 07/20/2015
helpviewer_keywords:
- Dim statement [Visual Basic]
- variables [Visual Basic], creating
ms.assetid: 35300be3-77b0-4bef-a156-034d3cdedde0
ms.openlocfilehash: 501c8f3aff4c5b204d231bdc26213e13d125a7cf
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410535"
---
# <a name="how-to-create-a-new-variable-visual-basic"></a><span data-ttu-id="f357a-102">Nasıl yapılır: Yeni Değişken Oluşturma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f357a-102">How to: Create a New Variable (Visual Basic)</span></span>

<span data-ttu-id="f357a-103">[Dim ifadesiyle](../../../language-reference/statements/dim-statement.md)bir değişken oluşturun.</span><span class="sxs-lookup"><span data-stu-id="f357a-103">You create a variable with a [Dim Statement](../../../language-reference/statements/dim-statement.md).</span></span>

### <a name="to-create-a-new-variable"></a><span data-ttu-id="f357a-104">Yeni bir değişken oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="f357a-104">To create a new variable</span></span>

1. <span data-ttu-id="f357a-105">Değişkeni bir `Dim` ifadede bildirin.</span><span class="sxs-lookup"><span data-stu-id="f357a-105">Declare the variable in a `Dim` statement.</span></span>

    ```vb
    Dim newCustomer
    ```

2. <span data-ttu-id="f357a-106">Değişkenin [özel](../../../language-reference/modifiers/private.md), [statik](../../../language-reference/modifiers/static.md), [Gölge](../../../language-reference/modifiers/shadows.md)veya [WithEvents](../../../language-reference/modifiers/withevents.md)gibi özelliklerine ilişkin belirtimleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f357a-106">Include specifications for the variable's characteristics, such as [Private](../../../language-reference/modifiers/private.md), [Static](../../../language-reference/modifiers/static.md), [Shadows](../../../language-reference/modifiers/shadows.md), or [WithEvents](../../../language-reference/modifiers/withevents.md).</span></span> <span data-ttu-id="f357a-107">Daha fazla bilgi için bkz. [bildirilmemiş öğe özellikleri](../declared-elements/declared-element-characteristics.md).</span><span class="sxs-lookup"><span data-stu-id="f357a-107">For more information, see [Declared Element Characteristics](../declared-elements/declared-element-characteristics.md).</span></span>

    ```vb
    Public Static newCustomer
    ```

    <span data-ttu-id="f357a-108">`Dim`Bildirimde diğer anahtar sözcükleri kullanıyorsanız, anahtar kelime gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="f357a-108">You do not need the `Dim` keyword if you use other keywords in the declaration.</span></span>

3. <span data-ttu-id="f357a-109">Visual Basic kuralları ve kuralları izlemeniz gereken değişkenin adıyla ilgili belirtimleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="f357a-109">Follow the specifications with the variable's name, which must follow Visual Basic rules and conventions.</span></span> <span data-ttu-id="f357a-110">Daha fazla bilgi için bkz. [bildirilmemiş öğe adları](../declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="f357a-110">For more information, see [Declared Element Names](../declared-elements/declared-element-names.md).</span></span>

    ```vb
    Public Static newCustomer
    ```

4. <span data-ttu-id="f357a-111">Değişkenin veri türünü belirtmek için [as](../../../language-reference/statements/as-clause.md) yan tümcesiyle birlikte adı izleyin.</span><span class="sxs-lookup"><span data-stu-id="f357a-111">Follow the name with the [As](../../../language-reference/statements/as-clause.md) clause to specify the variable's data type.</span></span>

    ```vb
    Public Static newCustomer As Customer
    ```

    <span data-ttu-id="f357a-112">Veri türünü belirtmezseniz, varsayılan: ' ı kullanır `Object` .</span><span class="sxs-lookup"><span data-stu-id="f357a-112">If you do not specify the data type, it uses the default: `Object`.</span></span>

5. <span data-ttu-id="f357a-113">`As`Eşittir işareti () ile yan tümceyi izleyin `=` ve değişkenin başlangıç değeriyle eşittir işaretine uyun.</span><span class="sxs-lookup"><span data-stu-id="f357a-113">Follow the `As` clause with an equal sign (`=`) and follow the equal sign with the variable's initial value.</span></span>

    <span data-ttu-id="f357a-114">Visual Basic, ifadeyi her çalıştırdığında belirtilen değeri değişkenine atar `Dim` .</span><span class="sxs-lookup"><span data-stu-id="f357a-114">Visual Basic assigns the specified value to the variable every time it runs the `Dim` statement.</span></span> <span data-ttu-id="f357a-115">Bir başlangıç değeri belirtmezseniz, Visual Basic değişkenin veri türü için varsayılan başlangıç değerini, ifadeyi içeren kodu ilk kez girdiğinde atar `Dim` .</span><span class="sxs-lookup"><span data-stu-id="f357a-115">If you do not specify an initial value, Visual Basic assigns the default initial value for the variable's data type when it first enters the code that contains the `Dim` statement.</span></span>

    <span data-ttu-id="f357a-116">Değişken bir başvuru türü ise, yan tümcesine [New Operator](../../../language-reference/operators/new-operator.md) anahtar sözcüğünü ekleyerek sınıfının bir örneğini oluşturabilirsiniz `As` .</span><span class="sxs-lookup"><span data-stu-id="f357a-116">If the variable is a reference type, you can create an instance of its class by including the [New Operator](../../../language-reference/operators/new-operator.md) keyword in the `As` clause.</span></span> <span data-ttu-id="f357a-117">Kullanmıyorsanız `New` , değişkenin ilk değeri [Nothing](../../../language-reference/nothing.md)olur.</span><span class="sxs-lookup"><span data-stu-id="f357a-117">If you do not use `New`, the initial value of the variable is [Nothing](../../../language-reference/nothing.md).</span></span>

    ```vb
    Public Static newCustomer As New Customer
    ```

## <a name="see-also"></a><span data-ttu-id="f357a-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f357a-118">See also</span></span>

- [<span data-ttu-id="f357a-119">Değişkenler</span><span class="sxs-lookup"><span data-stu-id="f357a-119">Variables</span></span>](index.md)
- [<span data-ttu-id="f357a-120">Değişken Bildirimi</span><span class="sxs-lookup"><span data-stu-id="f357a-120">Variable Declaration</span></span>](variable-declaration.md)
- [<span data-ttu-id="f357a-121">Bildirilen Öğe Adları</span><span class="sxs-lookup"><span data-stu-id="f357a-121">Declared Element Names</span></span>](../declared-elements/declared-element-names.md)
- [<span data-ttu-id="f357a-122">Bildirilen Öğe Özellikleri</span><span class="sxs-lookup"><span data-stu-id="f357a-122">Declared Element Characteristics</span></span>](../declared-elements/declared-element-characteristics.md)
- [<span data-ttu-id="f357a-123">Değer Türleri ve Başvuru Türleri</span><span class="sxs-lookup"><span data-stu-id="f357a-123">Value Types and Reference Types</span></span>](../data-types/value-types-and-reference-types.md)
- [<span data-ttu-id="f357a-124">Deyimler</span><span class="sxs-lookup"><span data-stu-id="f357a-124">Statements</span></span>](../../../language-reference/statements/index.md)
- [<span data-ttu-id="f357a-125">Yerel Tür Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f357a-125">Local Type Inference</span></span>](local-type-inference.md)
- [<span data-ttu-id="f357a-126">Option Infer Deyimi</span><span class="sxs-lookup"><span data-stu-id="f357a-126">Option Infer Statement</span></span>](../../../language-reference/statements/option-infer-statement.md)
