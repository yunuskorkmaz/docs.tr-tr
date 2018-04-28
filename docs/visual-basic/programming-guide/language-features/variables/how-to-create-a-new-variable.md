---
title: 'Nasıl yapılır: Yeni Değişken Oluşturma (Visual Basic)'
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Dim statement [Visual Basic]
- variables [Visual Basic], creating
ms.assetid: 35300be3-77b0-4bef-a156-034d3cdedde0
caps.latest.revision: 29
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: aff160584d3d1fe382020d5b8c25ac57dab66d92
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-create-a-new-variable-visual-basic"></a><span data-ttu-id="3e99d-102">Nasıl yapılır: Yeni Değişken Oluşturma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3e99d-102">How to: Create a New Variable (Visual Basic)</span></span>
<span data-ttu-id="3e99d-103">Sahip bir değişken oluşturmak bir [Dim deyimi](../../../../visual-basic/language-reference/statements/dim-statement.md).</span><span class="sxs-lookup"><span data-stu-id="3e99d-103">You create a variable with a [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md).</span></span>  
  
### <a name="to-create-a-new-variable"></a><span data-ttu-id="3e99d-104">Yeni bir değişken oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="3e99d-104">To create a new variable</span></span>  
  
1.  <span data-ttu-id="3e99d-105">Değişken bildirme bir `Dim` deyimi.</span><span class="sxs-lookup"><span data-stu-id="3e99d-105">Declare the variable in a `Dim` statement.</span></span>  
  
    ```  
    Dim newCustomer  
    ```  
  
2.  <span data-ttu-id="3e99d-106">Değişkenin özellikleri için belirtimleri gibi içeren [özel](../../../../visual-basic/language-reference/modifiers/private.md), [statik](../../../../visual-basic/language-reference/modifiers/static.md), [gölgeleri](../../../../visual-basic/language-reference/modifiers/shadows.md), veya [WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md).</span><span class="sxs-lookup"><span data-stu-id="3e99d-106">Include specifications for the variable's characteristics, such as [Private](../../../../visual-basic/language-reference/modifiers/private.md), [Static](../../../../visual-basic/language-reference/modifiers/static.md), [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md), or [WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md).</span></span> <span data-ttu-id="3e99d-107">Daha fazla bilgi için bkz: [bildirilen öğe özellikleri](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md).</span><span class="sxs-lookup"><span data-stu-id="3e99d-107">For more information, see [Declared Element Characteristics](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md).</span></span>  
  
    ```  
    Public Static newCustomer  
    ```  
  
     <span data-ttu-id="3e99d-108">İhtiyacınız olmayan `Dim` bildiriminde diğer anahtar sözcükler kullanırsanız, anahtar sözcük.</span><span class="sxs-lookup"><span data-stu-id="3e99d-108">You do not need the `Dim` keyword if you use other keywords in the declaration.</span></span>  
  
3.  <span data-ttu-id="3e99d-109">Visual Basic kuralları ve kurallarına uymalıdır değişkenin adını belirtimlere izleyin.</span><span class="sxs-lookup"><span data-stu-id="3e99d-109">Follow the specifications with the variable's name, which must follow Visual Basic rules and conventions.</span></span> <span data-ttu-id="3e99d-110">Daha fazla bilgi için bkz: [bildirilen öğe adları](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="3e99d-110">For more information, see [Declared Element Names](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
    ```  
    Public Static newCustomer  
    ```  
  
4.  <span data-ttu-id="3e99d-111">Adlı izleyin [olarak](../../../../visual-basic/language-reference/statements/as-clause.md) yan tümcesini değişkenin veri türü belirtin.</span><span class="sxs-lookup"><span data-stu-id="3e99d-111">Follow the name with the [As](../../../../visual-basic/language-reference/statements/as-clause.md) clause to specify the variable's data type.</span></span>  
  
    ```  
    Public Static newCustomer As Customer  
    ```  
  
     <span data-ttu-id="3e99d-112">Veri türünü belirtmezseniz varsayılan kullanır: `Object`.</span><span class="sxs-lookup"><span data-stu-id="3e99d-112">If you do not specify the data type, it uses the default: `Object`.</span></span>  
  
5.  <span data-ttu-id="3e99d-113">İzleyin `As` yan tümcesi eşittir işareti (`=`) ve değişken ilk değerinin eşittir işaretiyle izleyin.</span><span class="sxs-lookup"><span data-stu-id="3e99d-113">Follow the `As` clause with an equal sign (`=`) and follow the equal sign with the variable's initial value.</span></span>  
  
     <span data-ttu-id="3e99d-114">Visual Basic her çalıştığında bu belirtilen değere değişkenine atar `Dim` deyimi.</span><span class="sxs-lookup"><span data-stu-id="3e99d-114">Visual Basic assigns the specified value to the variable every time it runs the `Dim` statement.</span></span> <span data-ttu-id="3e99d-115">Bir başlangıç değeri belirtmezseniz, ilk içeren kodu girdiğinde, Visual Basic değişkenin veri türü için varsayılan başlangıç değeri atar `Dim` deyimi.</span><span class="sxs-lookup"><span data-stu-id="3e99d-115">If you do not specify an initial value, Visual Basic assigns the default initial value for the variable's data type when it first enters the code that contains the `Dim` statement.</span></span>  
  
     <span data-ttu-id="3e99d-116">Değişkeni bir başvuru türü ise dahil ederek kendi sınıfının bir örneğini oluşturabilirsiniz [New işleci](../../../../visual-basic/language-reference/operators/new-operator.md) anahtar sözcük `As` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="3e99d-116">If the variable is a reference type, you can create an instance of its class by including the [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md) keyword in the `As` clause.</span></span> <span data-ttu-id="3e99d-117">Kullanmıyorsanız, `New`, ilk değer değişkenin [hiçbir şey](../../../../visual-basic/language-reference/nothing.md).</span><span class="sxs-lookup"><span data-stu-id="3e99d-117">If you do not use `New`, the initial value of the variable is [Nothing](../../../../visual-basic/language-reference/nothing.md).</span></span>  
  
    ```  
    Public Static newCustomer As New Customer  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="3e99d-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3e99d-118">See Also</span></span>  
 [<span data-ttu-id="3e99d-119">Değişkenler</span><span class="sxs-lookup"><span data-stu-id="3e99d-119">Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/index.md)  
 [<span data-ttu-id="3e99d-120">Değişken Bildirimi</span><span class="sxs-lookup"><span data-stu-id="3e99d-120">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [<span data-ttu-id="3e99d-121">Bildirilen Öğe Adları</span><span class="sxs-lookup"><span data-stu-id="3e99d-121">Declared Element Names</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [<span data-ttu-id="3e99d-122">Bildirilen Öğe Özellikleri</span><span class="sxs-lookup"><span data-stu-id="3e99d-122">Declared Element Characteristics</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)  
 [<span data-ttu-id="3e99d-123">Değer Türleri ve Başvuru Türleri</span><span class="sxs-lookup"><span data-stu-id="3e99d-123">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [<span data-ttu-id="3e99d-124">Deyimler</span><span class="sxs-lookup"><span data-stu-id="3e99d-124">Statements</span></span>](../../../../visual-basic/language-reference/statements/index.md)  
 [<span data-ttu-id="3e99d-125">Yerel Çıkarım</span><span class="sxs-lookup"><span data-stu-id="3e99d-125">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [<span data-ttu-id="3e99d-126">Option Infer Deyimi</span><span class="sxs-lookup"><span data-stu-id="3e99d-126">Option Infer Statement</span></span>](../../../../visual-basic/language-reference/statements/option-infer-statement.md)
