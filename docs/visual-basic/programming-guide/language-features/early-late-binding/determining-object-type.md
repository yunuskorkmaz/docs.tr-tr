---
description: 'Hakkında daha fazla bilgi edinin: nesne türünü belirleme (Visual Basic)'
title: Nesne Türünü Belirleme
ms.date: 07/20/2015
helpviewer_keywords:
- classes [Visual Basic], discovering which an object belongs to
- types [Visual Basic], determining Visual Basic object types
- object variables [Visual Basic], testing values
- TypeOf...Is expression, object type at run time
- TypeName function
- objects [Visual Basic], type determining
ms.assetid: d95e7ad1-cd63-41d6-9a28-d7a1380d49c1
ms.openlocfilehash: 0cf64b6dde74b98edaf055537533cb648ed3381a
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100434413"
---
# <a name="determining-object-type-visual-basic"></a><span data-ttu-id="912fd-103">Nesne Türünü Belirleme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="912fd-103">Determining Object Type (Visual Basic)</span></span>

<span data-ttu-id="912fd-104">Genel nesne değişkenleri (diğer bir deyişle, olarak bildirdiğiniz değişkenler `Object` ) herhangi bir sınıftan nesne tutabilir.</span><span class="sxs-lookup"><span data-stu-id="912fd-104">Generic object variables (that is, variables you declare as `Object`) can hold objects from any class.</span></span> <span data-ttu-id="912fd-105">Türündeki değişkenleri kullanırken `Object` , nesnenin sınıfına göre farklı eylemler gerçekleştirmeniz gerekebilir; Örneğin, bazı nesneler belirli bir özelliği veya yöntemi desteklemiyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="912fd-105">When using variables of type `Object`, you may need to take different actions based on the class of the object; for example, some objects might not support a particular property or method.</span></span> <span data-ttu-id="912fd-106">Visual Basic, nesne değişkeninde hangi tür nesnenin depolandığını belirlemek için iki yol sunar: `TypeName` işlev ve `TypeOf...Is` işleç.</span><span class="sxs-lookup"><span data-stu-id="912fd-106">Visual Basic provides two means of determining which type of object is stored in an object variable: the `TypeName` function and the `TypeOf...Is` operator.</span></span>  
  
## <a name="typename-and-typeofis"></a><span data-ttu-id="912fd-107">TypeName ve TypeOf... Eklenir</span><span class="sxs-lookup"><span data-stu-id="912fd-107">TypeName and TypeOf…Is</span></span>  

 <span data-ttu-id="912fd-108">`TypeName`İşlevi bir dize döndürür ve aşağıdaki kod parçasında gösterildiği gibi bir nesnenin sınıf adını depolamanız veya görüntüetmeniz gerektiğinde en iyi seçenektir:</span><span class="sxs-lookup"><span data-stu-id="912fd-108">The `TypeName` function returns a string and is the best choice when you need to store or display the class name of an object, as shown in the following code fragment:</span></span>  
  
 [!code-vb[VbVbalrOOP#92](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#92)]  
  
 <span data-ttu-id="912fd-109">`TypeOf...Is`İşleci, kullanılarak denk dize karşılaştırmasının çok daha hızlı olduğu için bir nesnenin türünü test etmek için en iyi seçimdir `TypeName` .</span><span class="sxs-lookup"><span data-stu-id="912fd-109">The `TypeOf...Is` operator is the best choice for testing an object's type, because it is much faster than an equivalent string comparison using `TypeName`.</span></span> <span data-ttu-id="912fd-110">Aşağıdaki kod parçası `TypeOf...Is` bir deyimin içinde kullanır `If...Then...Else` :</span><span class="sxs-lookup"><span data-stu-id="912fd-110">The following code fragment uses `TypeOf...Is` within an `If...Then...Else` statement:</span></span>  
  
 [!code-vb[VbVbalrOOP#93](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#93)]  
  
 <span data-ttu-id="912fd-111">Burada dikkatli bir sözcük verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="912fd-111">A word of caution is due here.</span></span> <span data-ttu-id="912fd-112">`TypeOf...Is`İşleci bir `True` nesne belirli bir tür ise veya belirli bir türden türetildiyse döndürür.</span><span class="sxs-lookup"><span data-stu-id="912fd-112">The `TypeOf...Is` operator returns `True` if an object is of a specific type, or is derived from a specific type.</span></span> <span data-ttu-id="912fd-113">Visual Basic ile yaptığınız neredeyse her şey, genellikle dizeler ve tamsayılar gibi nesneler olarak düşünmeden bazı öğeleri içeren nesneler içerir.</span><span class="sxs-lookup"><span data-stu-id="912fd-113">Almost everything you do with Visual Basic involves objects, which include some elements not normally thought of as objects, such as strings and integers.</span></span> <span data-ttu-id="912fd-114">Bu nesneler öğesinden türetilir ve öğesinden yöntemleri alır <xref:System.Object> .</span><span class="sxs-lookup"><span data-stu-id="912fd-114">These objects are derived from and inherit methods from <xref:System.Object>.</span></span> <span data-ttu-id="912fd-115">Bir ile geçirildiğinde `Integer` ve ile değerlendirildiğinde `Object` `TypeOf...Is` işleç döndürülür `True` .</span><span class="sxs-lookup"><span data-stu-id="912fd-115">When passed an `Integer` and evaluated with `Object`, the `TypeOf...Is` operator returns `True`.</span></span> <span data-ttu-id="912fd-116">Aşağıdaki örnek, parametresinin hem a hem `InParam` de bir olduğunu bildirir `Object` `Integer` :</span><span class="sxs-lookup"><span data-stu-id="912fd-116">The following example reports that the parameter `InParam` is both an `Object` and an `Integer`:</span></span>  
  
 [!code-vb[VbVbalrOOP#94](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#94)]  
  
 <span data-ttu-id="912fd-117">Aşağıdaki örnek, `TypeOf...Is` `TypeName` bağımsız değişkeninde kendisine geçirilen nesne türünü belirleyebilmek için ve ikisini kullanır `Ctrl` .</span><span class="sxs-lookup"><span data-stu-id="912fd-117">The following example uses both `TypeOf...Is` and `TypeName` to determine the type of object passed to it in the `Ctrl` argument.</span></span> <span data-ttu-id="912fd-118">`TestObject`Yordam `ShowType` üç farklı denetim türüyle çağrı yapılır.</span><span class="sxs-lookup"><span data-stu-id="912fd-118">The `TestObject` procedure calls `ShowType` with three different kinds of controls.</span></span>  
  
#### <a name="to-run-the-example"></a><span data-ttu-id="912fd-119">Örneği çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="912fd-119">To run the example</span></span>  
  
1. <span data-ttu-id="912fd-120">Yeni bir Windows uygulaması projesi oluşturun ve forma bir <xref:System.Windows.Forms.Button> Denetim, <xref:System.Windows.Forms.CheckBox> Denetim ve <xref:System.Windows.Forms.RadioButton> denetim ekleyin.</span><span class="sxs-lookup"><span data-stu-id="912fd-120">Create a new Windows Application project and add a <xref:System.Windows.Forms.Button> control, a <xref:System.Windows.Forms.CheckBox> control, and a <xref:System.Windows.Forms.RadioButton> control to the form.</span></span>  
  
2. <span data-ttu-id="912fd-121">Formunuzdaki düğmeden `TestObject` yordamını çağırın.</span><span class="sxs-lookup"><span data-stu-id="912fd-121">From the button on your form, call the `TestObject` procedure.</span></span>  
  
3. <span data-ttu-id="912fd-122">Formunuza aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="912fd-122">Add the following code to your form:</span></span>  
  
     [!code-vb[VbVbalrOOP#95](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#95)]  
  
## <a name="see-also"></a><span data-ttu-id="912fd-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="912fd-123">See also</span></span>

- <xref:Microsoft.VisualBasic.Information.TypeName%2A>
- [<span data-ttu-id="912fd-124">Bir Dize Adı Kullanarak Bir Özelliği veya Yöntemi Çağırma</span><span class="sxs-lookup"><span data-stu-id="912fd-124">Calling a Property or Method Using a String Name</span></span>](calling-a-property-or-method-using-a-string-name.md)
- [<span data-ttu-id="912fd-125">Nesne Veri Türü</span><span class="sxs-lookup"><span data-stu-id="912fd-125">Object Data Type</span></span>](../../../language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="912fd-126">If...Then...Else Deyimi</span><span class="sxs-lookup"><span data-stu-id="912fd-126">If...Then...Else Statement</span></span>](../../../language-reference/statements/if-then-else-statement.md)
- [<span data-ttu-id="912fd-127">Dize Veri Türü</span><span class="sxs-lookup"><span data-stu-id="912fd-127">String Data Type</span></span>](../../../language-reference/data-types/string-data-type.md)
- [<span data-ttu-id="912fd-128">Integer Veri Türü</span><span class="sxs-lookup"><span data-stu-id="912fd-128">Integer Data Type</span></span>](../../../language-reference/data-types/integer-data-type.md)
