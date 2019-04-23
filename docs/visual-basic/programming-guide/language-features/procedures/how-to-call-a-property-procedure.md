---
title: 'Nasıl yapılır: (Visual Basic) bir özellik yordamı çağırma'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- Visual Basic code, properties
- procedures [Visual Basic], calling
- properties [Visual Basic], property procedures
- procedure calls [Visual Basic], property procedures
ms.assetid: 96bc4d74-d9c3-4b7a-954d-58ac8553cd94
ms.openlocfilehash: d05c1b63f5567ade9935f80ecc022eb4840e0af0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59318760"
---
# <a name="how-to-call-a-property-procedure-visual-basic"></a><span data-ttu-id="6fc2b-102">Nasıl yapılır: (Visual Basic) bir özellik yordamı çağırma</span><span class="sxs-lookup"><span data-stu-id="6fc2b-102">How to: Call a Property Procedure (Visual Basic)</span></span>
<span data-ttu-id="6fc2b-103">Özelliğin değeri depolamak veya değeri alınırken bir özellik yordamı çağırma.</span><span class="sxs-lookup"><span data-stu-id="6fc2b-103">You call a property procedure by storing a value in the property or retrieving its value.</span></span> <span data-ttu-id="6fc2b-104">Bir özelliği bir değişkene erişme gibi erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6fc2b-104">You access a property the same way you access a variable.</span></span>  
  
 <span data-ttu-id="6fc2b-105">Özelliğin `Set` yordamı bir değer depolar ve kendi `Get` yordamı değeri alır.</span><span class="sxs-lookup"><span data-stu-id="6fc2b-105">The property's `Set` procedure stores a value, and its `Get` procedure retrieves the value.</span></span> <span data-ttu-id="6fc2b-106">Ancak, açıkça bu yordamları adıyla çağırmayın.</span><span class="sxs-lookup"><span data-stu-id="6fc2b-106">However, you do not explicitly call these procedures by name.</span></span> <span data-ttu-id="6fc2b-107">Yalnızca siz depolamak veya bir değişkenin değerini almak bir atama ifadesi veya bir ifade özelliği kullanın.</span><span class="sxs-lookup"><span data-stu-id="6fc2b-107">You use the property in an assignment statement or an expression, just as you would store or retrieve the value of a variable.</span></span> <span data-ttu-id="6fc2b-108">Visual Basic özelliğin yordamları çağrılar yapar.</span><span class="sxs-lookup"><span data-stu-id="6fc2b-108">Visual Basic makes the calls to the property's procedures.</span></span>  
  
### <a name="to-call-a-propertys-get-procedure"></a><span data-ttu-id="6fc2b-109">Özellik Get yordamı çağırmak için</span><span class="sxs-lookup"><span data-stu-id="6fc2b-109">To call a property's Get procedure</span></span>  
  
1. <span data-ttu-id="6fc2b-110">Özellik adı bir ifade bir değişken adı kullanacağınız aynı şekilde kullanın.</span><span class="sxs-lookup"><span data-stu-id="6fc2b-110">Use the property name in an expression the same way you would use a variable name.</span></span> <span data-ttu-id="6fc2b-111">Bir özellik kullanabileceğiniz bir değişken veya sabit her yerde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6fc2b-111">You can use a property anywhere you can use a variable or a constant.</span></span>  
  
     <span data-ttu-id="6fc2b-112">-veya-</span><span class="sxs-lookup"><span data-stu-id="6fc2b-112">-or-</span></span>  
  
     <span data-ttu-id="6fc2b-113">Eşit aşağıdaki özellik adını kullanın (`=`) bir atama ifadesinde oturum açın.</span><span class="sxs-lookup"><span data-stu-id="6fc2b-113">Use the property name following the equal (`=`) sign in an assignment statement.</span></span>  
  
     <span data-ttu-id="6fc2b-114">Aşağıdaki örnek değerini okur <xref:Microsoft.VisualBasic.DateAndTime.Now%2A> örtük olarak arama özelliğini kendi `Get` yordamı.</span><span class="sxs-lookup"><span data-stu-id="6fc2b-114">The following example reads the value of the <xref:Microsoft.VisualBasic.DateAndTime.Now%2A> property, implicitly calling its `Get` procedure.</span></span>  
  
     [!code-vb[VbVbalrDateProperties#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDateProperties/VB/Module1.vb#4)]  
  
2. <span data-ttu-id="6fc2b-115">Özellik bağımsız değişkeni alır, parantez içine bağımsız değişken listesi için özellik adıyla izleyin.</span><span class="sxs-lookup"><span data-stu-id="6fc2b-115">If the property takes arguments, follow the property name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="6fc2b-116">Hiçbir bağımsız değişken varsa, isteğe bağlı olarak ayraçları atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6fc2b-116">If there are no arguments, you can optionally omit the parentheses.</span></span>  
  
3. <span data-ttu-id="6fc2b-117">Bağımsız değişken listesi parantezlerinin virgülle ayırarak yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="6fc2b-117">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="6fc2b-118">Bağımsız değişkenler özelliği karşılık gelen parametreleri tanımlar aynı sırada sağladığınız emin olun.</span><span class="sxs-lookup"><span data-stu-id="6fc2b-118">Be sure you supply the arguments in the same order that the property defines the corresponding parameters.</span></span>  
  
 <span data-ttu-id="6fc2b-119">İfade bir değişken gibi bir özelliğin değerini katıldığı sabiti misiniz veya değişken veya özellik atama ifadesi sol tarafında depolanır.</span><span class="sxs-lookup"><span data-stu-id="6fc2b-119">The value of the property participates in the expression just as a variable or constant would, or it is stored in the variable or property on the left side of the assignment statement.</span></span>  
  
### <a name="to-call-a-propertys-set-procedure"></a><span data-ttu-id="6fc2b-120">Bir özellik çağırmak için yordam kümesinde</span><span class="sxs-lookup"><span data-stu-id="6fc2b-120">To call a property's Set procedure</span></span>  
  
1. <span data-ttu-id="6fc2b-121">Özellik adı, atama deyiminin sol tarafında kullanın.</span><span class="sxs-lookup"><span data-stu-id="6fc2b-121">Use the property name on the left side of an assignment statement.</span></span>  
  
     <span data-ttu-id="6fc2b-122">Aşağıdaki örnekte ayarlar <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A> özelliği, örtük olarak çağırma `Set` yordamı.</span><span class="sxs-lookup"><span data-stu-id="6fc2b-122">The following example sets the value of the <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A> property, implicitly calling the `Set` procedure.</span></span>  
  
     [!code-vb[VbVbcnProcedures#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#11)]  
  
2. <span data-ttu-id="6fc2b-123">Özellik bağımsız değişkeni alır, parantez içine bağımsız değişken listesi için özellik adıyla izleyin.</span><span class="sxs-lookup"><span data-stu-id="6fc2b-123">If the property takes arguments, follow the property name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="6fc2b-124">Hiçbir bağımsız değişken varsa, isteğe bağlı olarak ayraçları atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6fc2b-124">If there are no arguments, you can optionally omit the parentheses.</span></span>  
  
3. <span data-ttu-id="6fc2b-125">Bağımsız değişken listesi parantezlerinin virgülle ayırarak yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="6fc2b-125">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="6fc2b-126">Bağımsız değişkenler özelliği karşılık gelen parametreleri tanımlar aynı sırada sağladığınız emin olun.</span><span class="sxs-lookup"><span data-stu-id="6fc2b-126">Be sure you supply the arguments in the same order that the property defines the corresponding parameters.</span></span>  
  
 <span data-ttu-id="6fc2b-127">Atama ifadesi sağ tarafında oluşturulan değeri özelliğinde depolanır.</span><span class="sxs-lookup"><span data-stu-id="6fc2b-127">The value generated on the right side of the assignment statement is stored in the property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6fc2b-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6fc2b-128">See also</span></span>

- [<span data-ttu-id="6fc2b-129">Özellik Yordamları</span><span class="sxs-lookup"><span data-stu-id="6fc2b-129">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="6fc2b-130">Yordam Parametreleri ve Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="6fc2b-130">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="6fc2b-131">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="6fc2b-131">Property Statement</span></span>](../../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="6fc2b-132">Visual Basic'de özellikler ile değişkenler arasındaki farklar</span><span class="sxs-lookup"><span data-stu-id="6fc2b-132">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)
- [<span data-ttu-id="6fc2b-133">Nasıl yapılır: Özellik oluşturma</span><span class="sxs-lookup"><span data-stu-id="6fc2b-133">How to: Create a Property</span></span>](./how-to-create-a-property.md)
- [<span data-ttu-id="6fc2b-134">Nasıl yapılır: Bir özelliği karışık erişim düzeyleriyle bildirme</span><span class="sxs-lookup"><span data-stu-id="6fc2b-134">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)
- [<span data-ttu-id="6fc2b-135">Nasıl yapılır: Bildirme ve Visual Basic'te bir varsayılan özelliğini çağırın</span><span class="sxs-lookup"><span data-stu-id="6fc2b-135">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)
- [<span data-ttu-id="6fc2b-136">Nasıl yapılır: Bir özelliğe değer ekleme</span><span class="sxs-lookup"><span data-stu-id="6fc2b-136">How to: Put a Value in a Property</span></span>](./how-to-put-a-value-in-a-property.md)
- [<span data-ttu-id="6fc2b-137">Nasıl yapılır: Bir özellikten değer alma</span><span class="sxs-lookup"><span data-stu-id="6fc2b-137">How to: Get a Value from a Property</span></span>](./how-to-get-a-value-from-a-property.md)
- [<span data-ttu-id="6fc2b-138">Get Deyimi</span><span class="sxs-lookup"><span data-stu-id="6fc2b-138">Get Statement</span></span>](../../../../visual-basic/language-reference/statements/get-statement.md)
- [<span data-ttu-id="6fc2b-139">Set Deyimi</span><span class="sxs-lookup"><span data-stu-id="6fc2b-139">Set Statement</span></span>](../../../../visual-basic/language-reference/statements/set-statement.md)
