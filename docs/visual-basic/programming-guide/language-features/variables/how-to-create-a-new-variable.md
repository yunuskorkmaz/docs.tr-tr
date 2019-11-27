---
title: 'Nasıl yapılır: Yeni Değişken Oluşturma'
ms.date: 07/20/2015
helpviewer_keywords:
- Dim statement [Visual Basic]
- variables [Visual Basic], creating
ms.assetid: 35300be3-77b0-4bef-a156-034d3cdedde0
ms.openlocfilehash: 2a2b5b8bef3b66f9727f0e65b61882186c007e94
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353628"
---
# <a name="how-to-create-a-new-variable-visual-basic"></a><span data-ttu-id="ba78a-102">Nasıl yapılır: Yeni Değişken Oluşturma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ba78a-102">How to: Create a New Variable (Visual Basic)</span></span>

<span data-ttu-id="ba78a-103">[Dim ifadesiyle](../../../../visual-basic/language-reference/statements/dim-statement.md)bir değişken oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ba78a-103">You create a variable with a [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md).</span></span>

### <a name="to-create-a-new-variable"></a><span data-ttu-id="ba78a-104">Yeni bir değişken oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="ba78a-104">To create a new variable</span></span>

1. <span data-ttu-id="ba78a-105">Değişkeni bir `Dim` bildiriminde bildirin.</span><span class="sxs-lookup"><span data-stu-id="ba78a-105">Declare the variable in a `Dim` statement.</span></span>

    ```vb
    Dim newCustomer
    ```

2. <span data-ttu-id="ba78a-106">Değişkenin [özel](../../../../visual-basic/language-reference/modifiers/private.md), [statik](../../../../visual-basic/language-reference/modifiers/static.md), [Gölge](../../../../visual-basic/language-reference/modifiers/shadows.md)veya [WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md)gibi özelliklerine ilişkin belirtimleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="ba78a-106">Include specifications for the variable's characteristics, such as [Private](../../../../visual-basic/language-reference/modifiers/private.md), [Static](../../../../visual-basic/language-reference/modifiers/static.md), [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md), or [WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md).</span></span> <span data-ttu-id="ba78a-107">Daha fazla bilgi için bkz. [bildirilmemiş öğe özellikleri](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md).</span><span class="sxs-lookup"><span data-stu-id="ba78a-107">For more information, see [Declared Element Characteristics](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md).</span></span>

    ```vb
    Public Static newCustomer
    ```

    <span data-ttu-id="ba78a-108">Bildirimde diğer anahtar sözcükleri kullanıyorsanız, `Dim` anahtar kelime gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="ba78a-108">You do not need the `Dim` keyword if you use other keywords in the declaration.</span></span>

3. <span data-ttu-id="ba78a-109">Visual Basic kuralları ve kuralları izlemeniz gereken değişkenin adıyla ilgili belirtimleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="ba78a-109">Follow the specifications with the variable's name, which must follow Visual Basic rules and conventions.</span></span> <span data-ttu-id="ba78a-110">Daha fazla bilgi için bkz. [bildirilmemiş öğe adları](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="ba78a-110">For more information, see [Declared Element Names](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>

    ```vb
    Public Static newCustomer
    ```

4. <span data-ttu-id="ba78a-111">Değişkenin veri türünü belirtmek için [as](../../../../visual-basic/language-reference/statements/as-clause.md) yan tümcesiyle birlikte adı izleyin.</span><span class="sxs-lookup"><span data-stu-id="ba78a-111">Follow the name with the [As](../../../../visual-basic/language-reference/statements/as-clause.md) clause to specify the variable's data type.</span></span>

    ```vb
    Public Static newCustomer As Customer
    ```

    <span data-ttu-id="ba78a-112">Veri türünü belirtmezseniz, varsayılan: `Object`kullanır.</span><span class="sxs-lookup"><span data-stu-id="ba78a-112">If you do not specify the data type, it uses the default: `Object`.</span></span>

5. <span data-ttu-id="ba78a-113">Eşittir işareti (`=`) ile `As` yan tümcesini izleyin ve değişkenin başlangıç değeriyle eşittir işaretini izleyin.</span><span class="sxs-lookup"><span data-stu-id="ba78a-113">Follow the `As` clause with an equal sign (`=`) and follow the equal sign with the variable's initial value.</span></span>

    <span data-ttu-id="ba78a-114">Visual Basic, `Dim` ifadesini her çalıştırdığında, değişkene belirtilen değeri atar.</span><span class="sxs-lookup"><span data-stu-id="ba78a-114">Visual Basic assigns the specified value to the variable every time it runs the `Dim` statement.</span></span> <span data-ttu-id="ba78a-115">Bir başlangıç değeri belirtmezseniz, Visual Basic değişkenin veri türü için varsayılan başlangıç değerini, `Dim` ifadesini içeren kodu ilk kez girdiğinde atar.</span><span class="sxs-lookup"><span data-stu-id="ba78a-115">If you do not specify an initial value, Visual Basic assigns the default initial value for the variable's data type when it first enters the code that contains the `Dim` statement.</span></span>

    <span data-ttu-id="ba78a-116">Değişken bir başvuru türü ise, `As` yan tümcesine [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md) anahtar sözcüğünü ekleyerek sınıfının bir örneğini oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ba78a-116">If the variable is a reference type, you can create an instance of its class by including the [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md) keyword in the `As` clause.</span></span> <span data-ttu-id="ba78a-117">`New`kullanmıyorsanız, değişkenin ilk değeri [Nothing](../../../../visual-basic/language-reference/nothing.md)olur.</span><span class="sxs-lookup"><span data-stu-id="ba78a-117">If you do not use `New`, the initial value of the variable is [Nothing](../../../../visual-basic/language-reference/nothing.md).</span></span>

    ```vb
    Public Static newCustomer As New Customer
    ```

## <a name="see-also"></a><span data-ttu-id="ba78a-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ba78a-118">See also</span></span>

- [<span data-ttu-id="ba78a-119">Değişkenler</span><span class="sxs-lookup"><span data-stu-id="ba78a-119">Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/index.md)
- [<span data-ttu-id="ba78a-120">Değişken Bildirimi</span><span class="sxs-lookup"><span data-stu-id="ba78a-120">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [<span data-ttu-id="ba78a-121">Bildirilen Öğe Adları</span><span class="sxs-lookup"><span data-stu-id="ba78a-121">Declared Element Names</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [<span data-ttu-id="ba78a-122">Bildirilen Öğe Özellikleri</span><span class="sxs-lookup"><span data-stu-id="ba78a-122">Declared Element Characteristics</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)
- [<span data-ttu-id="ba78a-123">Değer Türleri ve Başvuru Türleri</span><span class="sxs-lookup"><span data-stu-id="ba78a-123">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [<span data-ttu-id="ba78a-124">Deyimler</span><span class="sxs-lookup"><span data-stu-id="ba78a-124">Statements</span></span>](../../../../visual-basic/language-reference/statements/index.md)
- [<span data-ttu-id="ba78a-125">Yerel Çıkarım</span><span class="sxs-lookup"><span data-stu-id="ba78a-125">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="ba78a-126">Option Infer Deyimi</span><span class="sxs-lookup"><span data-stu-id="ba78a-126">Option Infer Statement</span></span>](../../../../visual-basic/language-reference/statements/option-infer-statement.md)
