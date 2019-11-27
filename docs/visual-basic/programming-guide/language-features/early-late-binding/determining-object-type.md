---
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
ms.openlocfilehash: a77cc0603a0b61f58a4aa703c4b1e6ef4c26729c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345193"
---
# <a name="determining-object-type-visual-basic"></a><span data-ttu-id="2de27-102">Nesne Türünü Belirleme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2de27-102">Determining Object Type (Visual Basic)</span></span>
<span data-ttu-id="2de27-103">Genel nesne değişkenleri (yani, `Object`olarak bildirdiğiniz değişkenler) herhangi bir sınıftan nesne tutabilir.</span><span class="sxs-lookup"><span data-stu-id="2de27-103">Generic object variables (that is, variables you declare as `Object`) can hold objects from any class.</span></span> <span data-ttu-id="2de27-104">`Object`değişkenleri kullanırken, nesnenin sınıfına göre farklı eylemler gerçekleştirmeniz gerekebilir; Örneğin, bazı nesneler belirli bir özelliği veya yöntemi desteklemiyor.</span><span class="sxs-lookup"><span data-stu-id="2de27-104">When using variables of type `Object`, you may need to take different actions based on the class of the object; for example, some objects might not support a particular property or method.</span></span> <span data-ttu-id="2de27-105">Visual Basic, nesne değişkeninde hangi tür nesnenin depolandığını belirlemek için iki yol sunar: `TypeName` işlevi ve `TypeOf...Is` işleci.</span><span class="sxs-lookup"><span data-stu-id="2de27-105">Visual Basic provides two means of determining which type of object is stored in an object variable: the `TypeName` function and the `TypeOf...Is` operator.</span></span>  
  
## <a name="typename-and-typeofis"></a><span data-ttu-id="2de27-106">TypeName ve TypeOf... Eklenir</span><span class="sxs-lookup"><span data-stu-id="2de27-106">TypeName and TypeOf…Is</span></span>  
 <span data-ttu-id="2de27-107">`TypeName` işlevi bir dize döndürür ve aşağıdaki kod parçasında gösterildiği gibi bir nesnenin sınıf adını depolamanız veya görüntüetmeniz gerektiğinde en iyi seçenektir:</span><span class="sxs-lookup"><span data-stu-id="2de27-107">The `TypeName` function returns a string and is the best choice when you need to store or display the class name of an object, as shown in the following code fragment:</span></span>  
  
 [!code-vb[VbVbalrOOP#92](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#92)]  
  
 <span data-ttu-id="2de27-108">`TypeOf...Is` işleci, bir nesnenin türünü test etmek için en iyi seçimdir, çünkü `TypeName`kullanılarak denk dize karşılaştırmasının çok daha hızlıdır.</span><span class="sxs-lookup"><span data-stu-id="2de27-108">The `TypeOf...Is` operator is the best choice for testing an object's type, because it is much faster than an equivalent string comparison using `TypeName`.</span></span> <span data-ttu-id="2de27-109">Aşağıdaki kod parçası bir `If...Then...Else` deyimindeki `TypeOf...Is` kullanır:</span><span class="sxs-lookup"><span data-stu-id="2de27-109">The following code fragment uses `TypeOf...Is` within an `If...Then...Else` statement:</span></span>  
  
 [!code-vb[VbVbalrOOP#93](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#93)]  
  
 <span data-ttu-id="2de27-110">Burada dikkatli bir sözcük verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="2de27-110">A word of caution is due here.</span></span> <span data-ttu-id="2de27-111">`TypeOf...Is` işleci, bir nesne belirli bir tür veya belirli bir türden türetildiyse `True` döndürür.</span><span class="sxs-lookup"><span data-stu-id="2de27-111">The `TypeOf...Is` operator returns `True` if an object is of a specific type, or is derived from a specific type.</span></span> <span data-ttu-id="2de27-112">Visual Basic ile yaptığınız neredeyse her şey, genellikle dizeler ve tamsayılar gibi nesneler olarak düşünmeden bazı öğeleri içeren nesneler içerir.</span><span class="sxs-lookup"><span data-stu-id="2de27-112">Almost everything you do with Visual Basic involves objects, which include some elements not normally thought of as objects, such as strings and integers.</span></span> <span data-ttu-id="2de27-113">Bu nesneler, ' den türetilir ve <xref:System.Object>yöntemlerden devralınır.</span><span class="sxs-lookup"><span data-stu-id="2de27-113">These objects are derived from and inherit methods from <xref:System.Object>.</span></span> <span data-ttu-id="2de27-114">Bir `Integer` geçirildiğinde ve `Object`ile değerlendirildiğinde `TypeOf...Is` işleci `True`döndürür.</span><span class="sxs-lookup"><span data-stu-id="2de27-114">When passed an `Integer` and evaluated with `Object`, the `TypeOf...Is` operator returns `True`.</span></span> <span data-ttu-id="2de27-115">Aşağıdaki örnek, `InParam` parametresinin hem `Object` hem de `Integer`olduğunu bildiriyor:</span><span class="sxs-lookup"><span data-stu-id="2de27-115">The following example reports that the parameter `InParam` is both an `Object` and an `Integer`:</span></span>  
  
 [!code-vb[VbVbalrOOP#94](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#94)]  
  
 <span data-ttu-id="2de27-116">Aşağıdaki örnek, `Ctrl` bağımsız değişkeninde kendisine geçirilen nesne türünü belirleyebilmek için hem `TypeOf...Is` hem de `TypeName` kullanır.</span><span class="sxs-lookup"><span data-stu-id="2de27-116">The following example uses both `TypeOf...Is` and `TypeName` to determine the type of object passed to it in the `Ctrl` argument.</span></span> <span data-ttu-id="2de27-117">`TestObject` yordamı üç farklı denetim türüyle `ShowType` çağırır.</span><span class="sxs-lookup"><span data-stu-id="2de27-117">The `TestObject` procedure calls `ShowType` with three different kinds of controls.</span></span>  
  
#### <a name="to-run-the-example"></a><span data-ttu-id="2de27-118">Örneği çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="2de27-118">To run the example</span></span>  
  
1. <span data-ttu-id="2de27-119">Yeni bir Windows uygulaması projesi oluşturun ve forma bir <xref:System.Windows.Forms.Button> denetimi, <xref:System.Windows.Forms.CheckBox> denetimi ve bir <xref:System.Windows.Forms.RadioButton> denetimi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="2de27-119">Create a new Windows Application project and add a <xref:System.Windows.Forms.Button> control, a <xref:System.Windows.Forms.CheckBox> control, and a <xref:System.Windows.Forms.RadioButton> control to the form.</span></span>  
  
2. <span data-ttu-id="2de27-120">Formunuzdaki düğmeden `TestObject` yordamını çağırın.</span><span class="sxs-lookup"><span data-stu-id="2de27-120">From the button on your form, call the `TestObject` procedure.</span></span>  
  
3. <span data-ttu-id="2de27-121">Formunuza aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="2de27-121">Add the following code to your form:</span></span>  
  
     [!code-vb[VbVbalrOOP#95](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#95)]  
  
## <a name="see-also"></a><span data-ttu-id="2de27-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2de27-122">See also</span></span>

- <xref:Microsoft.VisualBasic.Information.TypeName%2A>
- [<span data-ttu-id="2de27-123">Bir Dize Adı Kullanarak Bir Özelliği veya Yöntemi Çağırma</span><span class="sxs-lookup"><span data-stu-id="2de27-123">Calling a Property or Method Using a String Name</span></span>](../../../../visual-basic/programming-guide/language-features/early-late-binding/calling-a-property-or-method-using-a-string-name.md)
- [<span data-ttu-id="2de27-124">Object Veri Türü</span><span class="sxs-lookup"><span data-stu-id="2de27-124">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="2de27-125">If...Then...Else Deyimi</span><span class="sxs-lookup"><span data-stu-id="2de27-125">If...Then...Else Statement</span></span>](../../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [<span data-ttu-id="2de27-126">String Veri Türü</span><span class="sxs-lookup"><span data-stu-id="2de27-126">String Data Type</span></span>](../../../../visual-basic/language-reference/data-types/string-data-type.md)
- [<span data-ttu-id="2de27-127">Integer Veri Türü</span><span class="sxs-lookup"><span data-stu-id="2de27-127">Integer Data Type</span></span>](../../../../visual-basic/language-reference/data-types/integer-data-type.md)
