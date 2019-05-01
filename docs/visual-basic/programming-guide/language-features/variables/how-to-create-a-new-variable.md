---
title: 'Nasıl yapılır: (Visual Basic) yeni değişken oluşturma'
ms.date: 07/20/2015
helpviewer_keywords:
- Dim statement [Visual Basic]
- variables [Visual Basic], creating
ms.assetid: 35300be3-77b0-4bef-a156-034d3cdedde0
ms.openlocfilehash: ee1e93b4e9819992f17738eb024004a4d66210d1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61938248"
---
# <a name="how-to-create-a-new-variable-visual-basic"></a><span data-ttu-id="d5e6f-102">Nasıl yapılır: (Visual Basic) yeni değişken oluşturma</span><span class="sxs-lookup"><span data-stu-id="d5e6f-102">How to: Create a New Variable (Visual Basic)</span></span>
<span data-ttu-id="d5e6f-103">Bir değişken ile oluşturduğunuz bir [Dim deyimi](../../../../visual-basic/language-reference/statements/dim-statement.md).</span><span class="sxs-lookup"><span data-stu-id="d5e6f-103">You create a variable with a [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md).</span></span>  
  
### <a name="to-create-a-new-variable"></a><span data-ttu-id="d5e6f-104">Yeni bir değişken oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="d5e6f-104">To create a new variable</span></span>  
  
1. <span data-ttu-id="d5e6f-105">Değişken bildirimini bir `Dim` deyimi.</span><span class="sxs-lookup"><span data-stu-id="d5e6f-105">Declare the variable in a `Dim` statement.</span></span>  
  
    ```  
    Dim newCustomer  
    ```  
  
2. <span data-ttu-id="d5e6f-106">Değişkenin özelliklerini belirtimleri gibi dahil [özel](../../../../visual-basic/language-reference/modifiers/private.md), [statik](../../../../visual-basic/language-reference/modifiers/static.md), [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md), veya [WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md).</span><span class="sxs-lookup"><span data-stu-id="d5e6f-106">Include specifications for the variable's characteristics, such as [Private](../../../../visual-basic/language-reference/modifiers/private.md), [Static](../../../../visual-basic/language-reference/modifiers/static.md), [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md), or [WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md).</span></span> <span data-ttu-id="d5e6f-107">Daha fazla bilgi için [bildirilen öğe özellikleri](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md).</span><span class="sxs-lookup"><span data-stu-id="d5e6f-107">For more information, see [Declared Element Characteristics](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md).</span></span>  
  
    ```  
    Public Static newCustomer  
    ```  
  
     <span data-ttu-id="d5e6f-108">Gereksinim duymadığınız `Dim` bildiriminde diğer anahtar sözcükler kullanırsanız anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="d5e6f-108">You do not need the `Dim` keyword if you use other keywords in the declaration.</span></span>  
  
3. <span data-ttu-id="d5e6f-109">Visual Basic kuralları ve kuralları izlemelidir değişkenin adıyla belirtimleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="d5e6f-109">Follow the specifications with the variable's name, which must follow Visual Basic rules and conventions.</span></span> <span data-ttu-id="d5e6f-110">Daha fazla bilgi için [bildirilen öğe adları](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="d5e6f-110">For more information, see [Declared Element Names](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
    ```  
    Public Static newCustomer  
    ```  
  
4. <span data-ttu-id="d5e6f-111">Adıyla izleyin [olarak](../../../../visual-basic/language-reference/statements/as-clause.md) yan değişkenin veri türü belirtin.</span><span class="sxs-lookup"><span data-stu-id="d5e6f-111">Follow the name with the [As](../../../../visual-basic/language-reference/statements/as-clause.md) clause to specify the variable's data type.</span></span>  
  
    ```  
    Public Static newCustomer As Customer  
    ```  
  
     <span data-ttu-id="d5e6f-112">Veri türü belirtmezseniz varsayılan kullanır: `Object`.</span><span class="sxs-lookup"><span data-stu-id="d5e6f-112">If you do not specify the data type, it uses the default: `Object`.</span></span>  
  
5. <span data-ttu-id="d5e6f-113">İzleyin `As` yan tümcesiyle birlikte bir eşittir işareti (`=`) ve değişkenin başlangıç değeri eşittir işaretiyle izleyin.</span><span class="sxs-lookup"><span data-stu-id="d5e6f-113">Follow the `As` clause with an equal sign (`=`) and follow the equal sign with the variable's initial value.</span></span>  
  
     <span data-ttu-id="d5e6f-114">Visual Basic her çalıştırıldığında bu belirtilen değeri bir değişkene atar `Dim` deyimi.</span><span class="sxs-lookup"><span data-stu-id="d5e6f-114">Visual Basic assigns the specified value to the variable every time it runs the `Dim` statement.</span></span> <span data-ttu-id="d5e6f-115">Bir başlangıç değeri belirtmezseniz, ilk içerdiği kodu girdiğinde Visual Basic değişken veri türü için varsayılan başlangıç değeri atar `Dim` deyimi.</span><span class="sxs-lookup"><span data-stu-id="d5e6f-115">If you do not specify an initial value, Visual Basic assigns the default initial value for the variable's data type when it first enters the code that contains the `Dim` statement.</span></span>  
  
     <span data-ttu-id="d5e6f-116">Değişken bir başvuru türü ise ekleyerek, sınıfının bir örneğini oluşturabilirsiniz [New işleci](../../../../visual-basic/language-reference/operators/new-operator.md) anahtar sözcüğünü `As` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="d5e6f-116">If the variable is a reference type, you can create an instance of its class by including the [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md) keyword in the `As` clause.</span></span> <span data-ttu-id="d5e6f-117">Kullanmıyorsanız, `New`, ilk değişken değeri [hiçbir şey](../../../../visual-basic/language-reference/nothing.md).</span><span class="sxs-lookup"><span data-stu-id="d5e6f-117">If you do not use `New`, the initial value of the variable is [Nothing](../../../../visual-basic/language-reference/nothing.md).</span></span>  
  
    ```  
    Public Static newCustomer As New Customer  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="d5e6f-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d5e6f-118">See also</span></span>

- [<span data-ttu-id="d5e6f-119">Değişkenler</span><span class="sxs-lookup"><span data-stu-id="d5e6f-119">Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/index.md)
- [<span data-ttu-id="d5e6f-120">Değişken Bildirimi</span><span class="sxs-lookup"><span data-stu-id="d5e6f-120">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [<span data-ttu-id="d5e6f-121">Bildirilen Öğe Adları</span><span class="sxs-lookup"><span data-stu-id="d5e6f-121">Declared Element Names</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [<span data-ttu-id="d5e6f-122">Bildirilen Öğe Özellikleri</span><span class="sxs-lookup"><span data-stu-id="d5e6f-122">Declared Element Characteristics</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)
- [<span data-ttu-id="d5e6f-123">Değer Türleri ve Başvuru Türleri</span><span class="sxs-lookup"><span data-stu-id="d5e6f-123">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [<span data-ttu-id="d5e6f-124">Deyimler</span><span class="sxs-lookup"><span data-stu-id="d5e6f-124">Statements</span></span>](../../../../visual-basic/language-reference/statements/index.md)
- [<span data-ttu-id="d5e6f-125">Yerel Çıkarım</span><span class="sxs-lookup"><span data-stu-id="d5e6f-125">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="d5e6f-126">Option Infer Deyimi</span><span class="sxs-lookup"><span data-stu-id="d5e6f-126">Option Infer Statement</span></span>](../../../../visual-basic/language-reference/statements/option-infer-statement.md)
