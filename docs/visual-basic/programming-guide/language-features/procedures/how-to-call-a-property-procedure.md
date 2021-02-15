---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: bir özellik yordamı çağırma (Visual Basic)'
title: 'Nasıl yapılır: Bir Özellik Yordamı Çağırma'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- Visual Basic code, properties
- procedures [Visual Basic], calling
- properties [Visual Basic], property procedures
- procedure calls [Visual Basic], property procedures
ms.assetid: 96bc4d74-d9c3-4b7a-954d-58ac8553cd94
ms.openlocfilehash: 541768cb6381aa3d2b1bf75267c5b34a82a3d2ab
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100466763"
---
# <a name="how-to-call-a-property-procedure-visual-basic"></a><span data-ttu-id="0f8d1-103">Nasıl yapılır: Bir Özellik Yordamı Çağırma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0f8d1-103">How to: Call a Property Procedure (Visual Basic)</span></span>

<span data-ttu-id="0f8d1-104">Özellik yordamını, özelliğinde bir değer depolayarak veya değerini alarak çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0f8d1-104">You call a property procedure by storing a value in the property or retrieving its value.</span></span> <span data-ttu-id="0f8d1-105">Bir özelliğe, bir değişkene erişirken aynı şekilde erişirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0f8d1-105">You access a property the same way you access a variable.</span></span>  
  
 <span data-ttu-id="0f8d1-106">Özelliğin `Set` yordamı bir değeri depolar ve `Get` yordamı değerini alır.</span><span class="sxs-lookup"><span data-stu-id="0f8d1-106">The property's `Set` procedure stores a value, and its `Get` procedure retrieves the value.</span></span> <span data-ttu-id="0f8d1-107">Ancak, bu yordamları adına göre açıkça çağırmayın.</span><span class="sxs-lookup"><span data-stu-id="0f8d1-107">However, you do not explicitly call these procedures by name.</span></span> <span data-ttu-id="0f8d1-108">Bir değişkenin değerini depoladığınız veya alacağınız gibi, bir atama deyiminde veya bir ifadede özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="0f8d1-108">You use the property in an assignment statement or an expression, just as you would store or retrieve the value of a variable.</span></span> <span data-ttu-id="0f8d1-109">Visual Basic, özelliğin yordamlarına çağrı yapar.</span><span class="sxs-lookup"><span data-stu-id="0f8d1-109">Visual Basic makes the calls to the property's procedures.</span></span>  
  
### <a name="to-call-a-propertys-get-procedure"></a><span data-ttu-id="0f8d1-110">Bir özelliğin get yordamını çağırmak için</span><span class="sxs-lookup"><span data-stu-id="0f8d1-110">To call a property's Get procedure</span></span>  
  
1. <span data-ttu-id="0f8d1-111">Bir ifadede özellik adını bir değişken adı kullandığınız şekilde kullanın.</span><span class="sxs-lookup"><span data-stu-id="0f8d1-111">Use the property name in an expression the same way you would use a variable name.</span></span> <span data-ttu-id="0f8d1-112">Bir özelliği, bir değişkeni veya sabiti kullanabileceğiniz her yerde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0f8d1-112">You can use a property anywhere you can use a variable or a constant.</span></span>  
  
     <span data-ttu-id="0f8d1-113">-veya-</span><span class="sxs-lookup"><span data-stu-id="0f8d1-113">-or-</span></span>  
  
     <span data-ttu-id="0f8d1-114">Atama ifadesinde eşittir () işaretinden sonra özellik adını kullanın `=` .</span><span class="sxs-lookup"><span data-stu-id="0f8d1-114">Use the property name following the equal (`=`) sign in an assignment statement.</span></span>  
  
     <span data-ttu-id="0f8d1-115">Aşağıdaki örnek, <xref:Microsoft.VisualBasic.DateAndTime.Now%2A> yordamını dolaylı olarak çağıran özelliğinin değerini okur `Get` .</span><span class="sxs-lookup"><span data-stu-id="0f8d1-115">The following example reads the value of the <xref:Microsoft.VisualBasic.DateAndTime.Now%2A> property, implicitly calling its `Get` procedure.</span></span>  
  
     [!code-vb[VbVbalrDateProperties#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDateProperties/VB/Module1.vb#4)]  
  
2. <span data-ttu-id="0f8d1-116">Özelliği bağımsız değişkenler alırsa, bağımsız değişken listesini kapsamak için parantez ile birlikte özellik adını izleyin.</span><span class="sxs-lookup"><span data-stu-id="0f8d1-116">If the property takes arguments, follow the property name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="0f8d1-117">Bağımsız değişken yoksa, isteğe bağlı olarak ayraçları atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0f8d1-117">If there are no arguments, you can optionally omit the parentheses.</span></span>  
  
3. <span data-ttu-id="0f8d1-118">Bağımsız değişkenleri virgülle ayırarak parantez içindeki bağımsız değişken listesine yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="0f8d1-118">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="0f8d1-119">Bağımsız değişkenleri özelliğin ilgili parametreleri tanımladığı sırayla girdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="0f8d1-119">Be sure you supply the arguments in the same order that the property defines the corresponding parameters.</span></span>  
  
 <span data-ttu-id="0f8d1-120">Özelliğin değeri, ifadeye yalnızca değişken veya sabit gibi, ya da atama deyiminin sol tarafındaki değişkende veya özellikte saklanır.</span><span class="sxs-lookup"><span data-stu-id="0f8d1-120">The value of the property participates in the expression just as a variable or constant would, or it is stored in the variable or property on the left side of the assignment statement.</span></span>  
  
### <a name="to-call-a-propertys-set-procedure"></a><span data-ttu-id="0f8d1-121">Bir özelliğin set yordamını çağırmak için</span><span class="sxs-lookup"><span data-stu-id="0f8d1-121">To call a property's Set procedure</span></span>  
  
1. <span data-ttu-id="0f8d1-122">Atama ifadesinin sol tarafındaki özellik adını kullanın.</span><span class="sxs-lookup"><span data-stu-id="0f8d1-122">Use the property name on the left side of an assignment statement.</span></span>  
  
     <span data-ttu-id="0f8d1-123">Aşağıdaki örnek, <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A> yordamı dolaylı olarak çağıran özelliğin değerini ayarlar `Set` .</span><span class="sxs-lookup"><span data-stu-id="0f8d1-123">The following example sets the value of the <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A> property, implicitly calling the `Set` procedure.</span></span>  
  
     [!code-vb[VbVbcnProcedures#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#11)]  
  
2. <span data-ttu-id="0f8d1-124">Özelliği bağımsız değişkenler alırsa, bağımsız değişken listesini kapsamak için parantez ile birlikte özellik adını izleyin.</span><span class="sxs-lookup"><span data-stu-id="0f8d1-124">If the property takes arguments, follow the property name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="0f8d1-125">Bağımsız değişken yoksa, isteğe bağlı olarak ayraçları atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0f8d1-125">If there are no arguments, you can optionally omit the parentheses.</span></span>  
  
3. <span data-ttu-id="0f8d1-126">Bağımsız değişkenleri virgülle ayırarak parantez içindeki bağımsız değişken listesine yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="0f8d1-126">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="0f8d1-127">Bağımsız değişkenleri özelliğin ilgili parametreleri tanımladığı sırayla girdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="0f8d1-127">Be sure you supply the arguments in the same order that the property defines the corresponding parameters.</span></span>  
  
 <span data-ttu-id="0f8d1-128">Atama ifadesinin sağ tarafında oluşturulan değer özelliğinde depolanır.</span><span class="sxs-lookup"><span data-stu-id="0f8d1-128">The value generated on the right side of the assignment statement is stored in the property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f8d1-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0f8d1-129">See also</span></span>

- [<span data-ttu-id="0f8d1-130">Özellik Yordamları</span><span class="sxs-lookup"><span data-stu-id="0f8d1-130">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="0f8d1-131">Yordam Parametreleri ve Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="0f8d1-131">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="0f8d1-132">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="0f8d1-132">Property Statement</span></span>](../../../language-reference/statements/property-statement.md)
- [<span data-ttu-id="0f8d1-133">Visual Basic'de Özellikler ve Değişkenler Arasındaki Farklar</span><span class="sxs-lookup"><span data-stu-id="0f8d1-133">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)
- [<span data-ttu-id="0f8d1-134">Nasıl yapılır: Özellik Oluşturma</span><span class="sxs-lookup"><span data-stu-id="0f8d1-134">How to: Create a Property</span></span>](./how-to-create-a-property.md)
- [<span data-ttu-id="0f8d1-135">Nasıl yapılır: Bir Özelliği Karışık Erişim Düzeyleriyle Bildirme</span><span class="sxs-lookup"><span data-stu-id="0f8d1-135">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)
- [<span data-ttu-id="0f8d1-136">Nasıl yapılır: Visual Basic'de Varsayılan Bir Özelliği Bildirme ve Çağırma</span><span class="sxs-lookup"><span data-stu-id="0f8d1-136">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)
- [<span data-ttu-id="0f8d1-137">Nasıl yapılır: Bir Özelliğe Değer Ekleme</span><span class="sxs-lookup"><span data-stu-id="0f8d1-137">How to: Put a Value in a Property</span></span>](./how-to-put-a-value-in-a-property.md)
- [<span data-ttu-id="0f8d1-138">Nasıl yapılır: Bir Özellikten Değer Alma</span><span class="sxs-lookup"><span data-stu-id="0f8d1-138">How to: Get a Value from a Property</span></span>](./how-to-get-a-value-from-a-property.md)
- [<span data-ttu-id="0f8d1-139">Get Deyimi</span><span class="sxs-lookup"><span data-stu-id="0f8d1-139">Get Statement</span></span>](../../../language-reference/statements/get-statement.md)
- [<span data-ttu-id="0f8d1-140">Set deyimleri</span><span class="sxs-lookup"><span data-stu-id="0f8d1-140">Set Statement</span></span>](../../../language-reference/statements/set-statement.md)
