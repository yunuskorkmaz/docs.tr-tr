---
title: Nesne Türünü Belirleme (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- classes [Visual Basic], discovering which an object belongs to
- types [Visual Basic], determining Visual Basic object types
- object variables [Visual Basic], testing values
- TypeOf...Is expression, object type at run time
- TypeName function
- objects [Visual Basic], type determining
ms.assetid: d95e7ad1-cd63-41d6-9a28-d7a1380d49c1
ms.openlocfilehash: 4014bef2e0c27a0f6a684bc1ed95019f392062a5
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59302718"
---
# <a name="determining-object-type-visual-basic"></a><span data-ttu-id="44280-102">Nesne Türünü Belirleme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="44280-102">Determining Object Type (Visual Basic)</span></span>
<span data-ttu-id="44280-103">Genel nesne değişkenleri (diğer bir deyişle, değişkenleri olarak bildirdiğiniz `Object`) herhangi bir sınıftan nesneleri içerebilir.</span><span class="sxs-lookup"><span data-stu-id="44280-103">Generic object variables (that is, variables you declare as `Object`) can hold objects from any class.</span></span> <span data-ttu-id="44280-104">Türü değişkenlerindeki kullanırken `Object`, nesnenin sınıfına göre farklı eylemlerde gerekebilir; örneğin, bazı nesneler belirli bir özelliği veya yöntemi desteklemiyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="44280-104">When using variables of type `Object`, you may need to take different actions based on the class of the object; for example, some objects might not support a particular property or method.</span></span> <span data-ttu-id="44280-105">Visual Basic nesne türü bir nesne değişkenine depolandığını belirleyen iki yol sunar: `TypeName` işlevi ve `TypeOf...Is` işleci.</span><span class="sxs-lookup"><span data-stu-id="44280-105">Visual Basic provides two means of determining which type of object is stored in an object variable: the `TypeName` function and the `TypeOf...Is` operator.</span></span>  
  
## <a name="typename-and-typeofis"></a><span data-ttu-id="44280-106">TypeName ve TypeOf... Olduğu</span><span class="sxs-lookup"><span data-stu-id="44280-106">TypeName and TypeOf…Is</span></span>  
 <span data-ttu-id="44280-107">`TypeName` İşlevi bir dize döndürür ve aşağıdaki kod parçasını gösterildiği depolamak veya bir nesne sınıfı adını görüntülemek gereken en iyi seçenektir:</span><span class="sxs-lookup"><span data-stu-id="44280-107">The `TypeName` function returns a string and is the best choice when you need to store or display the class name of an object, as shown in the following code fragment:</span></span>  
  
 [!code-vb[VbVbalrOOP#92](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#92)]  
  
 <span data-ttu-id="44280-108">`TypeOf...Is` İşleci, bir nesnenin türü, test etmek için en iyi seçenek, bir dize karşılaştırma kullanmaktan çok daha hızlı olduğundan `TypeName`.</span><span class="sxs-lookup"><span data-stu-id="44280-108">The `TypeOf...Is` operator is the best choice for testing an object's type, because it is much faster than an equivalent string comparison using `TypeName`.</span></span> <span data-ttu-id="44280-109">Aşağıdaki kod parçası kullanan `TypeOf...Is` içinde bir `If...Then...Else` deyimi:</span><span class="sxs-lookup"><span data-stu-id="44280-109">The following code fragment uses `TypeOf...Is` within an `If...Then...Else` statement:</span></span>  
  
 [!code-vb[VbVbalrOOP#93](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#93)]  
  
 <span data-ttu-id="44280-110">Bir sözcük uyarı son İşte.</span><span class="sxs-lookup"><span data-stu-id="44280-110">A word of caution is due here.</span></span> <span data-ttu-id="44280-111">`TypeOf...Is` İşleci döndürür `True` bir nesne belirli bir tür ya da belirli bir türden türetilir.</span><span class="sxs-lookup"><span data-stu-id="44280-111">The `TypeOf...Is` operator returns `True` if an object is of a specific type, or is derived from a specific type.</span></span> <span data-ttu-id="44280-112">Hemen Visual Basic ile yaptığınız her şey, normalde, dizeler ve tamsayılar gibi nesneler olarak düşünülebilir bazı öğeleri içeren nesneleri içerir.</span><span class="sxs-lookup"><span data-stu-id="44280-112">Almost everything you do with Visual Basic involves objects, which include some elements not normally thought of as objects, such as strings and integers.</span></span> <span data-ttu-id="44280-113">Bu nesnelerin türetilmiştir ve yöntemleri devralan <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="44280-113">These objects are derived from and inherit methods from <xref:System.Object>.</span></span> <span data-ttu-id="44280-114">Geçirildiğinde bir `Integer` ve ile değerlendirilen `Object`, `TypeOf...Is` işleci döndürür `True`.</span><span class="sxs-lookup"><span data-stu-id="44280-114">When passed an `Integer` and evaluated with `Object`, the `TypeOf...Is` operator returns `True`.</span></span> <span data-ttu-id="44280-115">Aşağıdaki örnek, rapor parametresi `InParam` hem de bir `Object` ve `Integer`:</span><span class="sxs-lookup"><span data-stu-id="44280-115">The following example reports that the parameter `InParam` is both an `Object` and an `Integer`:</span></span>  
  
 [!code-vb[VbVbalrOOP#94](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#94)]  
  
 <span data-ttu-id="44280-116">Aşağıdaki örnek, her ikisi de kullanır `TypeOf...Is` ve `TypeName` kendisine geçirilen nesne türünü belirlemek için `Ctrl` bağımsız değişken.</span><span class="sxs-lookup"><span data-stu-id="44280-116">The following example uses both `TypeOf...Is` and `TypeName` to determine the type of object passed to it in the `Ctrl` argument.</span></span> <span data-ttu-id="44280-117">`TestObject` Yordam çağrılarını `ShowType` denetimleri üç farklı tür ile.</span><span class="sxs-lookup"><span data-stu-id="44280-117">The `TestObject` procedure calls `ShowType` with three different kinds of controls.</span></span>  
  
#### <a name="to-run-the-example"></a><span data-ttu-id="44280-118">Örneği çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="44280-118">To run the example</span></span>  
  
1. <span data-ttu-id="44280-119">Yeni bir Windows uygulaması projesi oluşturma ve ekleme bir <xref:System.Windows.Forms.Button> denetimi, bir <xref:System.Windows.Forms.CheckBox> denetimi ve bir <xref:System.Windows.Forms.RadioButton> forma.</span><span class="sxs-lookup"><span data-stu-id="44280-119">Create a new Windows Application project and add a <xref:System.Windows.Forms.Button> control, a <xref:System.Windows.Forms.CheckBox> control, and a <xref:System.Windows.Forms.RadioButton> control to the form.</span></span>  
  
2. <span data-ttu-id="44280-120">Formunuzdaki düğmesinden çağrı `TestObject` yordamı.</span><span class="sxs-lookup"><span data-stu-id="44280-120">From the button on your form, call the `TestObject` procedure.</span></span>  
  
3. <span data-ttu-id="44280-121">Formunuza aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="44280-121">Add the following code to your form:</span></span>  
  
     [!code-vb[VbVbalrOOP#95](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#95)]  
  
## <a name="see-also"></a><span data-ttu-id="44280-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="44280-122">See also</span></span>

- <xref:Microsoft.VisualBasic.Information.TypeName%2A>
- [<span data-ttu-id="44280-123">Bir Dize Adı Kullanarak Bir Özelliği veya Yöntemi Çağırma</span><span class="sxs-lookup"><span data-stu-id="44280-123">Calling a Property or Method Using a String Name</span></span>](../../../../visual-basic/programming-guide/language-features/early-late-binding/calling-a-property-or-method-using-a-string-name.md)
- [<span data-ttu-id="44280-124">Nesne Veri Türü</span><span class="sxs-lookup"><span data-stu-id="44280-124">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="44280-125">If...Then...Else Deyimi</span><span class="sxs-lookup"><span data-stu-id="44280-125">If...Then...Else Statement</span></span>](../../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [<span data-ttu-id="44280-126">Dize Veri Türü</span><span class="sxs-lookup"><span data-stu-id="44280-126">String Data Type</span></span>](../../../../visual-basic/language-reference/data-types/string-data-type.md)
- [<span data-ttu-id="44280-127">Tamsayı Veri Türü</span><span class="sxs-lookup"><span data-stu-id="44280-127">Integer Data Type</span></span>](../../../../visual-basic/language-reference/data-types/integer-data-type.md)
