---
title: 'Nasıl yapılır: Bir Özellik Yordamı Çağırma'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- Visual Basic code, properties
- procedures [Visual Basic], calling
- properties [Visual Basic], property procedures
- procedure calls [Visual Basic], property procedures
ms.assetid: 96bc4d74-d9c3-4b7a-954d-58ac8553cd94
ms.openlocfilehash: 52e6c62ffb81c480ccc1abf06f04eb780218dbf1
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74340550"
---
# <a name="how-to-call-a-property-procedure-visual-basic"></a><span data-ttu-id="531ec-102">Nasıl yapılır: Bir Özellik Yordamı Çağırma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="531ec-102">How to: Call a Property Procedure (Visual Basic)</span></span>
<span data-ttu-id="531ec-103">Özellik yordamını, özelliğinde bir değer depolayarak veya değerini alarak çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="531ec-103">You call a property procedure by storing a value in the property or retrieving its value.</span></span> <span data-ttu-id="531ec-104">Bir özelliğe, bir değişkene erişirken aynı şekilde erişirsiniz.</span><span class="sxs-lookup"><span data-stu-id="531ec-104">You access a property the same way you access a variable.</span></span>  
  
 <span data-ttu-id="531ec-105">Özelliğin `Set` yordamı bir değeri depolar ve `Get` yordamı değeri alır.</span><span class="sxs-lookup"><span data-stu-id="531ec-105">The property's `Set` procedure stores a value, and its `Get` procedure retrieves the value.</span></span> <span data-ttu-id="531ec-106">Ancak, bu yordamları adına göre açıkça çağırmayın.</span><span class="sxs-lookup"><span data-stu-id="531ec-106">However, you do not explicitly call these procedures by name.</span></span> <span data-ttu-id="531ec-107">Bir değişkenin değerini depoladığınız veya alacağınız gibi, bir atama deyiminde veya bir ifadede özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="531ec-107">You use the property in an assignment statement or an expression, just as you would store or retrieve the value of a variable.</span></span> <span data-ttu-id="531ec-108">Visual Basic, özelliğin yordamlarına çağrı yapar.</span><span class="sxs-lookup"><span data-stu-id="531ec-108">Visual Basic makes the calls to the property's procedures.</span></span>  
  
### <a name="to-call-a-propertys-get-procedure"></a><span data-ttu-id="531ec-109">Bir özelliğin get yordamını çağırmak için</span><span class="sxs-lookup"><span data-stu-id="531ec-109">To call a property's Get procedure</span></span>  
  
1. <span data-ttu-id="531ec-110">Bir ifadede özellik adını bir değişken adı kullandığınız şekilde kullanın.</span><span class="sxs-lookup"><span data-stu-id="531ec-110">Use the property name in an expression the same way you would use a variable name.</span></span> <span data-ttu-id="531ec-111">Bir özelliği, bir değişkeni veya sabiti kullanabileceğiniz her yerde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="531ec-111">You can use a property anywhere you can use a variable or a constant.</span></span>  
  
     <span data-ttu-id="531ec-112">veya</span><span class="sxs-lookup"><span data-stu-id="531ec-112">-or-</span></span>  
  
     <span data-ttu-id="531ec-113">Atama deyimindeki eşittir (`=`) işaretinden sonra özellik adını kullanın.</span><span class="sxs-lookup"><span data-stu-id="531ec-113">Use the property name following the equal (`=`) sign in an assignment statement.</span></span>  
  
     <span data-ttu-id="531ec-114">Aşağıdaki örnek, `Get` yordamını dolaylı olarak çağıran <xref:Microsoft.VisualBasic.DateAndTime.Now%2A> özelliğinin değerini okur.</span><span class="sxs-lookup"><span data-stu-id="531ec-114">The following example reads the value of the <xref:Microsoft.VisualBasic.DateAndTime.Now%2A> property, implicitly calling its `Get` procedure.</span></span>  
  
     [!code-vb[VbVbalrDateProperties#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDateProperties/VB/Module1.vb#4)]  
  
2. <span data-ttu-id="531ec-115">Özelliği bağımsız değişkenler alırsa, bağımsız değişken listesini kapsamak için parantez ile birlikte özellik adını izleyin.</span><span class="sxs-lookup"><span data-stu-id="531ec-115">If the property takes arguments, follow the property name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="531ec-116">Bağımsız değişken yoksa, isteğe bağlı olarak ayraçları atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="531ec-116">If there are no arguments, you can optionally omit the parentheses.</span></span>  
  
3. <span data-ttu-id="531ec-117">Bağımsız değişkenleri virgülle ayırarak parantez içindeki bağımsız değişken listesine yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="531ec-117">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="531ec-118">Bağımsız değişkenleri özelliğin ilgili parametreleri tanımladığı sırayla girdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="531ec-118">Be sure you supply the arguments in the same order that the property defines the corresponding parameters.</span></span>  
  
 <span data-ttu-id="531ec-119">Özelliğin değeri, ifadeye yalnızca değişken veya sabit gibi, ya da atama deyiminin sol tarafındaki değişkende veya özellikte saklanır.</span><span class="sxs-lookup"><span data-stu-id="531ec-119">The value of the property participates in the expression just as a variable or constant would, or it is stored in the variable or property on the left side of the assignment statement.</span></span>  
  
### <a name="to-call-a-propertys-set-procedure"></a><span data-ttu-id="531ec-120">Bir özelliğin set yordamını çağırmak için</span><span class="sxs-lookup"><span data-stu-id="531ec-120">To call a property's Set procedure</span></span>  
  
1. <span data-ttu-id="531ec-121">Atama ifadesinin sol tarafındaki özellik adını kullanın.</span><span class="sxs-lookup"><span data-stu-id="531ec-121">Use the property name on the left side of an assignment statement.</span></span>  
  
     <span data-ttu-id="531ec-122">Aşağıdaki örnek, `Set` yordamını dolaylı olarak çağıran <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A> özelliğinin değerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="531ec-122">The following example sets the value of the <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A> property, implicitly calling the `Set` procedure.</span></span>  
  
     [!code-vb[VbVbcnProcedures#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#11)]  
  
2. <span data-ttu-id="531ec-123">Özelliği bağımsız değişkenler alırsa, bağımsız değişken listesini kapsamak için parantez ile birlikte özellik adını izleyin.</span><span class="sxs-lookup"><span data-stu-id="531ec-123">If the property takes arguments, follow the property name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="531ec-124">Bağımsız değişken yoksa, isteğe bağlı olarak ayraçları atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="531ec-124">If there are no arguments, you can optionally omit the parentheses.</span></span>  
  
3. <span data-ttu-id="531ec-125">Bağımsız değişkenleri virgülle ayırarak parantez içindeki bağımsız değişken listesine yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="531ec-125">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="531ec-126">Bağımsız değişkenleri özelliğin ilgili parametreleri tanımladığı sırayla girdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="531ec-126">Be sure you supply the arguments in the same order that the property defines the corresponding parameters.</span></span>  
  
 <span data-ttu-id="531ec-127">Atama ifadesinin sağ tarafında oluşturulan değer özelliğinde depolanır.</span><span class="sxs-lookup"><span data-stu-id="531ec-127">The value generated on the right side of the assignment statement is stored in the property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="531ec-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="531ec-128">See also</span></span>

- [<span data-ttu-id="531ec-129">Özellik Yordamları</span><span class="sxs-lookup"><span data-stu-id="531ec-129">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="531ec-130">Yordam Parametreleri ve Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="531ec-130">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="531ec-131">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="531ec-131">Property Statement</span></span>](../../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="531ec-132">Visual Basic Özellikler ve değişkenler arasındaki farklar</span><span class="sxs-lookup"><span data-stu-id="531ec-132">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)
- [<span data-ttu-id="531ec-133">Nasıl yapılır: Özellik Oluşturma</span><span class="sxs-lookup"><span data-stu-id="531ec-133">How to: Create a Property</span></span>](./how-to-create-a-property.md)
- [<span data-ttu-id="531ec-134">Nasıl yapılır: Bir Özelliği Karışık Erişim Düzeyleriyle Bildirme</span><span class="sxs-lookup"><span data-stu-id="531ec-134">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)
- [<span data-ttu-id="531ec-135">Nasıl yapılır: Visual Basic varsayılan bir özellik bildirme ve çağırma</span><span class="sxs-lookup"><span data-stu-id="531ec-135">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)
- [<span data-ttu-id="531ec-136">Nasıl yapılır: Bir Özelliğe Değer Ekleme</span><span class="sxs-lookup"><span data-stu-id="531ec-136">How to: Put a Value in a Property</span></span>](./how-to-put-a-value-in-a-property.md)
- [<span data-ttu-id="531ec-137">Nasıl yapılır: Bir Özellikten Değer Alma</span><span class="sxs-lookup"><span data-stu-id="531ec-137">How to: Get a Value from a Property</span></span>](./how-to-get-a-value-from-a-property.md)
- [<span data-ttu-id="531ec-138">Get Deyimi</span><span class="sxs-lookup"><span data-stu-id="531ec-138">Get Statement</span></span>](../../../../visual-basic/language-reference/statements/get-statement.md)
- [<span data-ttu-id="531ec-139">Set Deyimi</span><span class="sxs-lookup"><span data-stu-id="531ec-139">Set Statement</span></span>](../../../../visual-basic/language-reference/statements/set-statement.md)
