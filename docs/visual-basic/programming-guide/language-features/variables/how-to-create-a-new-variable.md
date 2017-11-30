---
title: "Nasıl yapılır: Yeni Değişken Oluşturma (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Dim statement [Visual Basic]
- variables [Visual Basic], creating
ms.assetid: 35300be3-77b0-4bef-a156-034d3cdedde0
caps.latest.revision: "29"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a6806dcbe9e00cbae77181b79d74ddb9a1e1493f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-new-variable-visual-basic"></a><span data-ttu-id="cc9cb-102">Nasıl yapılır: Yeni Değişken Oluşturma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cc9cb-102">How to: Create a New Variable (Visual Basic)</span></span>
<span data-ttu-id="cc9cb-103">Sahip bir değişken oluşturmak bir [Dim deyimi](../../../../visual-basic/language-reference/statements/dim-statement.md).</span><span class="sxs-lookup"><span data-stu-id="cc9cb-103">You create a variable with a [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md).</span></span>  
  
### <a name="to-create-a-new-variable"></a><span data-ttu-id="cc9cb-104">Yeni bir değişken oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="cc9cb-104">To create a new variable</span></span>  
  
1.  <span data-ttu-id="cc9cb-105">Değişken bildirme bir `Dim` deyimi.</span><span class="sxs-lookup"><span data-stu-id="cc9cb-105">Declare the variable in a `Dim` statement.</span></span>  
  
    ```  
    Dim newCustomer  
    ```  
  
2.  <span data-ttu-id="cc9cb-106">Değişkenin özellikleri için belirtimleri gibi içeren [özel](../../../../visual-basic/language-reference/modifiers/private.md), [statik](../../../../visual-basic/language-reference/modifiers/static.md), [gölgeleri](../../../../visual-basic/language-reference/modifiers/shadows.md), veya [WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md).</span><span class="sxs-lookup"><span data-stu-id="cc9cb-106">Include specifications for the variable's characteristics, such as [Private](../../../../visual-basic/language-reference/modifiers/private.md), [Static](../../../../visual-basic/language-reference/modifiers/static.md), [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md), or [WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md).</span></span> <span data-ttu-id="cc9cb-107">Daha fazla bilgi için bkz: [bildirilen öğe özellikleri](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md).</span><span class="sxs-lookup"><span data-stu-id="cc9cb-107">For more information, see [Declared Element Characteristics](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md).</span></span>  
  
    ```  
    Public Static newCustomer  
    ```  
  
     <span data-ttu-id="cc9cb-108">İhtiyacınız olmayan `Dim` bildiriminde diğer anahtar sözcükler kullanırsanız, anahtar sözcük.</span><span class="sxs-lookup"><span data-stu-id="cc9cb-108">You do not need the `Dim` keyword if you use other keywords in the declaration.</span></span>  
  
3.  <span data-ttu-id="cc9cb-109">İzlemeniz gereken değişkenin adını belirtimlere izleyin [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] kurallar.</span><span class="sxs-lookup"><span data-stu-id="cc9cb-109">Follow the specifications with the variable's name, which must follow [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] rules and conventions.</span></span> <span data-ttu-id="cc9cb-110">Daha fazla bilgi için bkz: [bildirilen öğe adları](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="cc9cb-110">For more information, see [Declared Element Names](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
    ```  
    Public Static newCustomer  
    ```  
  
4.  <span data-ttu-id="cc9cb-111">Adlı izleyin [olarak](../../../../visual-basic/language-reference/statements/as-clause.md) yan tümcesini değişkenin veri türü belirtin.</span><span class="sxs-lookup"><span data-stu-id="cc9cb-111">Follow the name with the [As](../../../../visual-basic/language-reference/statements/as-clause.md) clause to specify the variable's data type.</span></span>  
  
    ```  
    Public Static newCustomer As Customer  
    ```  
  
     <span data-ttu-id="cc9cb-112">Veri türünü belirtmezseniz varsayılan kullanır: `Object`.</span><span class="sxs-lookup"><span data-stu-id="cc9cb-112">If you do not specify the data type, it uses the default: `Object`.</span></span>  
  
5.  <span data-ttu-id="cc9cb-113">İzleyin `As` yan tümcesi eşittir işareti (`=`) ve değişken ilk değerinin eşittir işaretiyle izleyin.</span><span class="sxs-lookup"><span data-stu-id="cc9cb-113">Follow the `As` clause with an equal sign (`=`) and follow the equal sign with the variable's initial value.</span></span>  
  
     [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="cc9cb-114">Belirtilen değer her çalıştığında değişkenine atar `Dim` deyimi.</span><span class="sxs-lookup"><span data-stu-id="cc9cb-114"> assigns the specified value to the variable every time it runs the `Dim` statement.</span></span> <span data-ttu-id="cc9cb-115">Bir başlangıç değeri belirtmezseniz, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] ilk içeren kodu girdiğinde değişkenin veri türü için varsayılan başlangıç değeri atar `Dim` deyimi.</span><span class="sxs-lookup"><span data-stu-id="cc9cb-115">If you do not specify an initial value, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] assigns the default initial value for the variable's data type when it first enters the code that contains the `Dim` statement.</span></span>  
  
     <span data-ttu-id="cc9cb-116">Değişkeni bir başvuru türü ise dahil ederek kendi sınıfının bir örneğini oluşturabilirsiniz [New işleci](../../../../visual-basic/language-reference/operators/new-operator.md) anahtar sözcük `As` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="cc9cb-116">If the variable is a reference type, you can create an instance of its class by including the [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md) keyword in the `As` clause.</span></span> <span data-ttu-id="cc9cb-117">Kullanmıyorsanız, `New`, ilk değer değişkenin [hiçbir şey](../../../../visual-basic/language-reference/nothing.md).</span><span class="sxs-lookup"><span data-stu-id="cc9cb-117">If you do not use `New`, the initial value of the variable is [Nothing](../../../../visual-basic/language-reference/nothing.md).</span></span>  
  
    ```  
    Public Static newCustomer As New Customer  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="cc9cb-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cc9cb-118">See Also</span></span>  
 [<span data-ttu-id="cc9cb-119">Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="cc9cb-119">Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/index.md)  
 [<span data-ttu-id="cc9cb-120">Değişken bildirimi</span><span class="sxs-lookup"><span data-stu-id="cc9cb-120">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [<span data-ttu-id="cc9cb-121">Bildirilen öğe adları</span><span class="sxs-lookup"><span data-stu-id="cc9cb-121">Declared Element Names</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [<span data-ttu-id="cc9cb-122">Bildirilen öğe özellikleri</span><span class="sxs-lookup"><span data-stu-id="cc9cb-122">Declared Element Characteristics</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)  
 [<span data-ttu-id="cc9cb-123">Değer türleri ve başvuru türleri</span><span class="sxs-lookup"><span data-stu-id="cc9cb-123">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [<span data-ttu-id="cc9cb-124">Deyimleri</span><span class="sxs-lookup"><span data-stu-id="cc9cb-124">Statements</span></span>](../../../../visual-basic/language-reference/statements/index.md)  
 [<span data-ttu-id="cc9cb-125">Yerel tür çıkarımı</span><span class="sxs-lookup"><span data-stu-id="cc9cb-125">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [<span data-ttu-id="cc9cb-126">Option Infer deyimi</span><span class="sxs-lookup"><span data-stu-id="cc9cb-126">Option Infer Statement</span></span>](../../../../visual-basic/language-reference/statements/option-infer-statement.md)
