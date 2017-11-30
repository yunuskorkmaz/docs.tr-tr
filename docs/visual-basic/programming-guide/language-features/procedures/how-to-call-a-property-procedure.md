---
title: "Nasıl yapılır: Bir Özellik Yordamı Çağırma (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Visual Basic code, procedures
- Visual Basic code, properties
- procedures [Visual Basic], calling
- properties [Visual Basic], property procedures
- procedure calls [Visual Basic], property procedures
ms.assetid: 96bc4d74-d9c3-4b7a-954d-58ac8553cd94
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: cf9080e3c2b23302257499f13e734231f3614495
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-call-a-property-procedure-visual-basic"></a><span data-ttu-id="80704-102">Nasıl yapılır: Bir Özellik Yordamı Çağırma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="80704-102">How to: Call a Property Procedure (Visual Basic)</span></span>
<span data-ttu-id="80704-103">Bir özellik değeri depolamak veya değeri alınırken bir özellik yordamı çağırma.</span><span class="sxs-lookup"><span data-stu-id="80704-103">You call a property procedure by storing a value in the property or retrieving its value.</span></span> <span data-ttu-id="80704-104">Bir özelliği bir değişkene erişme aynı şekilde erişin.</span><span class="sxs-lookup"><span data-stu-id="80704-104">You access a property the same way you access a variable.</span></span>  
  
 <span data-ttu-id="80704-105">Özelliğin `Set` yordamı bir değer depolar ve kendi `Get` yordamı değerini alır.</span><span class="sxs-lookup"><span data-stu-id="80704-105">The property's `Set` procedure stores a value, and its `Get` procedure retrieves the value.</span></span> <span data-ttu-id="80704-106">Ancak, siz açıkça bu yordamları adıyla çağırmayın.</span><span class="sxs-lookup"><span data-stu-id="80704-106">However, you do not explicitly call these procedures by name.</span></span> <span data-ttu-id="80704-107">Yalnızca siz depolamak veya bir değişkenin değerini almak bir atama ifadesi veya bir ifade özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="80704-107">You use the property in an assignment statement or an expression, just as you would store or retrieve the value of a variable.</span></span> [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="80704-108">özelliğin yordamlara çağrılar.</span><span class="sxs-lookup"><span data-stu-id="80704-108"> makes the calls to the property's procedures.</span></span>  
  
### <a name="to-call-a-propertys-get-procedure"></a><span data-ttu-id="80704-109">Bir özelliğin Get yordamı çağırmak için</span><span class="sxs-lookup"><span data-stu-id="80704-109">To call a property's Get procedure</span></span>  
  
1.  <span data-ttu-id="80704-110">Özellik adı bir ifade bir değişken adı kullanacağınız aynı şekilde kullanın.</span><span class="sxs-lookup"><span data-stu-id="80704-110">Use the property name in an expression the same way you would use a variable name.</span></span> <span data-ttu-id="80704-111">Bir özellik kullanabileceğiniz bir değişken veya sabit herhangi bir yerde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="80704-111">You can use a property anywhere you can use a variable or a constant.</span></span>  
  
     <span data-ttu-id="80704-112">veya</span><span class="sxs-lookup"><span data-stu-id="80704-112">-or-</span></span>  
  
     <span data-ttu-id="80704-113">Eşittir aşağıdaki özellik adı kullanın (`=`) bir atama deyiminde oturum açın.</span><span class="sxs-lookup"><span data-stu-id="80704-113">Use the property name following the equal (`=`) sign in an assignment statement.</span></span>  
  
     <span data-ttu-id="80704-114">Aşağıdaki örnek değeri okuyan <xref:Microsoft.VisualBasic.DateAndTime.Now%2A> örtük olarak arama özelliği, kendi `Get` yordamı.</span><span class="sxs-lookup"><span data-stu-id="80704-114">The following example reads the value of the <xref:Microsoft.VisualBasic.DateAndTime.Now%2A> property, implicitly calling its `Get` procedure.</span></span>  
  
     [!code-vb[VbVbalrDateProperties#4](./codesnippet/VisualBasic/how-to-call-a-property-procedure_1.vb)]  
  
2.  <span data-ttu-id="80704-115">Özellik bağımsız değişken alıyorsa, özellik adı bağımsız değişken listesi kapsamak için parantez ile izleyin.</span><span class="sxs-lookup"><span data-stu-id="80704-115">If the property takes arguments, follow the property name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="80704-116">Bağımsız değişkenler varsa, isteğe bağlı olarak parantez atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="80704-116">If there are no arguments, you can optionally omit the parentheses.</span></span>  
  
3.  <span data-ttu-id="80704-117">Bağımsız değişkenler, virgülle ayrılmış parantez içinde bağımsız değişken listesinde yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="80704-117">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="80704-118">Bağımsız değişkenler özelliği ilgili parametreleri tanımlar aynı sırada sağladığınız emin olun.</span><span class="sxs-lookup"><span data-stu-id="80704-118">Be sure you supply the arguments in the same order that the property defines the corresponding parameters.</span></span>  
  
 <span data-ttu-id="80704-119">İfade bir değişken olarak yalnızca özelliğin değerini katıldığı sabiti misiniz veya değişkenin veya özelliğin Atama ifadesinin sol tarafında depolanır.</span><span class="sxs-lookup"><span data-stu-id="80704-119">The value of the property participates in the expression just as a variable or constant would, or it is stored in the variable or property on the left side of the assignment statement.</span></span>  
  
### <a name="to-call-a-propertys-set-procedure"></a><span data-ttu-id="80704-120">Bir özellik çağırmak için yordam kümesinde</span><span class="sxs-lookup"><span data-stu-id="80704-120">To call a property's Set procedure</span></span>  
  
1.  <span data-ttu-id="80704-121">Özellik adı atama ifadesinin sol taraftaki kullanın.</span><span class="sxs-lookup"><span data-stu-id="80704-121">Use the property name on the left side of an assignment statement.</span></span>  
  
     <span data-ttu-id="80704-122">Aşağıdaki örnek değerini ayarlar <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A> örtük olarak arama özelliği, `Set` yordamı.</span><span class="sxs-lookup"><span data-stu-id="80704-122">The following example sets the value of the <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A> property, implicitly calling the `Set` procedure.</span></span>  
  
     [!code-vb[VbVbcnProcedures#11](./codesnippet/VisualBasic/how-to-call-a-property-procedure_2.vb)]  
  
2.  <span data-ttu-id="80704-123">Özellik bağımsız değişken alıyorsa, özellik adı bağımsız değişken listesi kapsamak için parantez ile izleyin.</span><span class="sxs-lookup"><span data-stu-id="80704-123">If the property takes arguments, follow the property name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="80704-124">Bağımsız değişkenler varsa, isteğe bağlı olarak parantez atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="80704-124">If there are no arguments, you can optionally omit the parentheses.</span></span>  
  
3.  <span data-ttu-id="80704-125">Bağımsız değişkenler, virgülle ayrılmış parantez içinde bağımsız değişken listesinde yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="80704-125">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="80704-126">Bağımsız değişkenler özelliği ilgili parametreleri tanımlar aynı sırada sağladığınız emin olun.</span><span class="sxs-lookup"><span data-stu-id="80704-126">Be sure you supply the arguments in the same order that the property defines the corresponding parameters.</span></span>  
  
 <span data-ttu-id="80704-127">Atama ifadesinin sağ tarafında oluşturulan değeri özelliğinde depolanır.</span><span class="sxs-lookup"><span data-stu-id="80704-127">The value generated on the right side of the assignment statement is stored in the property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80704-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="80704-128">See Also</span></span>  
 [<span data-ttu-id="80704-129">Özellik yordamları</span><span class="sxs-lookup"><span data-stu-id="80704-129">Property Procedures</span></span>](./property-procedures.md)  
 [<span data-ttu-id="80704-130">Parametreler ve bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="80704-130">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="80704-131">Property deyimi</span><span class="sxs-lookup"><span data-stu-id="80704-131">Property Statement</span></span>](../../../../visual-basic/language-reference/statements/property-statement.md)  
 [<span data-ttu-id="80704-132">Visual Basic'de özellikler ve değişkenler arasındaki farklar</span><span class="sxs-lookup"><span data-stu-id="80704-132">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)  
 [<span data-ttu-id="80704-133">Nasıl yapılır: özellik oluşturma</span><span class="sxs-lookup"><span data-stu-id="80704-133">How to: Create a Property</span></span>](./how-to-create-a-property.md)  
 [<span data-ttu-id="80704-134">Nasıl yapılır: bir özelliği karışık erişim düzeyleriyle bildirme</span><span class="sxs-lookup"><span data-stu-id="80704-134">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)  
 [<span data-ttu-id="80704-135">Nasıl yapılır: bildirme ve Visual Basic'te varsayılan özelliğini çağırın</span><span class="sxs-lookup"><span data-stu-id="80704-135">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)  
 [<span data-ttu-id="80704-136">Nasıl yapılır: bir özelliğe değer ekleme</span><span class="sxs-lookup"><span data-stu-id="80704-136">How to: Put a Value in a Property</span></span>](./how-to-put-a-value-in-a-property.md)  
 [<span data-ttu-id="80704-137">Nasıl yapılır: bir özellikten değer alma</span><span class="sxs-lookup"><span data-stu-id="80704-137">How to: Get a Value from a Property</span></span>](./how-to-get-a-value-from-a-property.md)  
 [<span data-ttu-id="80704-138">Get deyimi</span><span class="sxs-lookup"><span data-stu-id="80704-138">Get Statement</span></span>](../../../../visual-basic/language-reference/statements/get-statement.md)  
 [<span data-ttu-id="80704-139">Set deyimi</span><span class="sxs-lookup"><span data-stu-id="80704-139">Set Statement</span></span>](../../../../visual-basic/language-reference/statements/set-statement.md)
