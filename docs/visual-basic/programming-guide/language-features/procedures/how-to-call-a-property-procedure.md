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
ms.openlocfilehash: 006961a0f1d4be6b0d52be5bc273dad9733bfe56
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84388705"
---
# <a name="how-to-call-a-property-procedure-visual-basic"></a><span data-ttu-id="0dd83-102">Nasıl yapılır: Bir Özellik Yordamı Çağırma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0dd83-102">How to: Call a Property Procedure (Visual Basic)</span></span>
<span data-ttu-id="0dd83-103">Özellik yordamını, özelliğinde bir değer depolayarak veya değerini alarak çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0dd83-103">You call a property procedure by storing a value in the property or retrieving its value.</span></span> <span data-ttu-id="0dd83-104">Bir özelliğe, bir değişkene erişirken aynı şekilde erişirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0dd83-104">You access a property the same way you access a variable.</span></span>  
  
 <span data-ttu-id="0dd83-105">Özelliğin `Set` yordamı bir değeri depolar ve `Get` yordamı değerini alır.</span><span class="sxs-lookup"><span data-stu-id="0dd83-105">The property's `Set` procedure stores a value, and its `Get` procedure retrieves the value.</span></span> <span data-ttu-id="0dd83-106">Ancak, bu yordamları adına göre açıkça çağırmayın.</span><span class="sxs-lookup"><span data-stu-id="0dd83-106">However, you do not explicitly call these procedures by name.</span></span> <span data-ttu-id="0dd83-107">Bir değişkenin değerini depoladığınız veya alacağınız gibi, bir atama deyiminde veya bir ifadede özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="0dd83-107">You use the property in an assignment statement or an expression, just as you would store or retrieve the value of a variable.</span></span> <span data-ttu-id="0dd83-108">Visual Basic, özelliğin yordamlarına çağrı yapar.</span><span class="sxs-lookup"><span data-stu-id="0dd83-108">Visual Basic makes the calls to the property's procedures.</span></span>  
  
### <a name="to-call-a-propertys-get-procedure"></a><span data-ttu-id="0dd83-109">Bir özelliğin get yordamını çağırmak için</span><span class="sxs-lookup"><span data-stu-id="0dd83-109">To call a property's Get procedure</span></span>  
  
1. <span data-ttu-id="0dd83-110">Bir ifadede özellik adını bir değişken adı kullandığınız şekilde kullanın.</span><span class="sxs-lookup"><span data-stu-id="0dd83-110">Use the property name in an expression the same way you would use a variable name.</span></span> <span data-ttu-id="0dd83-111">Bir özelliği, bir değişkeni veya sabiti kullanabileceğiniz her yerde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0dd83-111">You can use a property anywhere you can use a variable or a constant.</span></span>  
  
     <span data-ttu-id="0dd83-112">-veya-</span><span class="sxs-lookup"><span data-stu-id="0dd83-112">-or-</span></span>  
  
     <span data-ttu-id="0dd83-113">Atama ifadesinde eşittir () işaretinden sonra özellik adını kullanın `=` .</span><span class="sxs-lookup"><span data-stu-id="0dd83-113">Use the property name following the equal (`=`) sign in an assignment statement.</span></span>  
  
     <span data-ttu-id="0dd83-114">Aşağıdaki örnek, <xref:Microsoft.VisualBasic.DateAndTime.Now%2A> yordamını dolaylı olarak çağıran özelliğinin değerini okur `Get` .</span><span class="sxs-lookup"><span data-stu-id="0dd83-114">The following example reads the value of the <xref:Microsoft.VisualBasic.DateAndTime.Now%2A> property, implicitly calling its `Get` procedure.</span></span>  
  
     [!code-vb[VbVbalrDateProperties#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDateProperties/VB/Module1.vb#4)]  
  
2. <span data-ttu-id="0dd83-115">Özelliği bağımsız değişkenler alırsa, bağımsız değişken listesini kapsamak için parantez ile birlikte özellik adını izleyin.</span><span class="sxs-lookup"><span data-stu-id="0dd83-115">If the property takes arguments, follow the property name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="0dd83-116">Bağımsız değişken yoksa, isteğe bağlı olarak ayraçları atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0dd83-116">If there are no arguments, you can optionally omit the parentheses.</span></span>  
  
3. <span data-ttu-id="0dd83-117">Bağımsız değişkenleri virgülle ayırarak parantez içindeki bağımsız değişken listesine yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="0dd83-117">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="0dd83-118">Bağımsız değişkenleri özelliğin ilgili parametreleri tanımladığı sırayla girdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="0dd83-118">Be sure you supply the arguments in the same order that the property defines the corresponding parameters.</span></span>  
  
 <span data-ttu-id="0dd83-119">Özelliğin değeri, ifadeye yalnızca değişken veya sabit gibi, ya da atama deyiminin sol tarafındaki değişkende veya özellikte saklanır.</span><span class="sxs-lookup"><span data-stu-id="0dd83-119">The value of the property participates in the expression just as a variable or constant would, or it is stored in the variable or property on the left side of the assignment statement.</span></span>  
  
### <a name="to-call-a-propertys-set-procedure"></a><span data-ttu-id="0dd83-120">Bir özelliğin set yordamını çağırmak için</span><span class="sxs-lookup"><span data-stu-id="0dd83-120">To call a property's Set procedure</span></span>  
  
1. <span data-ttu-id="0dd83-121">Atama ifadesinin sol tarafındaki özellik adını kullanın.</span><span class="sxs-lookup"><span data-stu-id="0dd83-121">Use the property name on the left side of an assignment statement.</span></span>  
  
     <span data-ttu-id="0dd83-122">Aşağıdaki örnek, <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A> yordamı dolaylı olarak çağıran özelliğin değerini ayarlar `Set` .</span><span class="sxs-lookup"><span data-stu-id="0dd83-122">The following example sets the value of the <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A> property, implicitly calling the `Set` procedure.</span></span>  
  
     [!code-vb[VbVbcnProcedures#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#11)]  
  
2. <span data-ttu-id="0dd83-123">Özelliği bağımsız değişkenler alırsa, bağımsız değişken listesini kapsamak için parantez ile birlikte özellik adını izleyin.</span><span class="sxs-lookup"><span data-stu-id="0dd83-123">If the property takes arguments, follow the property name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="0dd83-124">Bağımsız değişken yoksa, isteğe bağlı olarak ayraçları atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0dd83-124">If there are no arguments, you can optionally omit the parentheses.</span></span>  
  
3. <span data-ttu-id="0dd83-125">Bağımsız değişkenleri virgülle ayırarak parantez içindeki bağımsız değişken listesine yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="0dd83-125">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="0dd83-126">Bağımsız değişkenleri özelliğin ilgili parametreleri tanımladığı sırayla girdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="0dd83-126">Be sure you supply the arguments in the same order that the property defines the corresponding parameters.</span></span>  
  
 <span data-ttu-id="0dd83-127">Atama ifadesinin sağ tarafında oluşturulan değer özelliğinde depolanır.</span><span class="sxs-lookup"><span data-stu-id="0dd83-127">The value generated on the right side of the assignment statement is stored in the property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0dd83-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0dd83-128">See also</span></span>

- [<span data-ttu-id="0dd83-129">Özellik Yordamları</span><span class="sxs-lookup"><span data-stu-id="0dd83-129">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="0dd83-130">Yordam Parametreleri ve Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="0dd83-130">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="0dd83-131">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="0dd83-131">Property Statement</span></span>](../../../language-reference/statements/property-statement.md)
- [<span data-ttu-id="0dd83-132">Visual Basic'de Özellikler ve Değişkenler Arasındaki Farklar</span><span class="sxs-lookup"><span data-stu-id="0dd83-132">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)
- [<span data-ttu-id="0dd83-133">Nasıl yapılır: Özellik Oluşturma</span><span class="sxs-lookup"><span data-stu-id="0dd83-133">How to: Create a Property</span></span>](./how-to-create-a-property.md)
- [<span data-ttu-id="0dd83-134">Nasıl yapılır: Bir Özelliği Karışık Erişim Düzeyleriyle Bildirme</span><span class="sxs-lookup"><span data-stu-id="0dd83-134">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)
- [<span data-ttu-id="0dd83-135">Nasıl yapılır: Visual Basic'de Varsayılan Bir Özelliği Bildirme ve Çağırma</span><span class="sxs-lookup"><span data-stu-id="0dd83-135">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)
- [<span data-ttu-id="0dd83-136">Nasıl yapılır: Bir Özelliğe Değer Ekleme</span><span class="sxs-lookup"><span data-stu-id="0dd83-136">How to: Put a Value in a Property</span></span>](./how-to-put-a-value-in-a-property.md)
- [<span data-ttu-id="0dd83-137">Nasıl yapılır: Bir Özellikten Değer Alma</span><span class="sxs-lookup"><span data-stu-id="0dd83-137">How to: Get a Value from a Property</span></span>](./how-to-get-a-value-from-a-property.md)
- [<span data-ttu-id="0dd83-138">Get Deyimi</span><span class="sxs-lookup"><span data-stu-id="0dd83-138">Get Statement</span></span>](../../../language-reference/statements/get-statement.md)
- [<span data-ttu-id="0dd83-139">Set deyimleri</span><span class="sxs-lookup"><span data-stu-id="0dd83-139">Set Statement</span></span>](../../../language-reference/statements/set-statement.md)
