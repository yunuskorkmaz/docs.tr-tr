---
title: 'Nasıl yapılır: Bir Özellik Yordamı Çağırma (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- Visual Basic code, properties
- procedures [Visual Basic], calling
- properties [Visual Basic], property procedures
- procedure calls [Visual Basic], property procedures
ms.assetid: 96bc4d74-d9c3-4b7a-954d-58ac8553cd94
ms.openlocfilehash: 61d79b9ff99ec144a9c629872abd2a7e7ebda4d0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33654823"
---
# <a name="how-to-call-a-property-procedure-visual-basic"></a><span data-ttu-id="f830a-102">Nasıl yapılır: Bir Özellik Yordamı Çağırma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f830a-102">How to: Call a Property Procedure (Visual Basic)</span></span>
<span data-ttu-id="f830a-103">Bir özellik değeri depolamak veya değeri alınırken bir özellik yordamı çağırma.</span><span class="sxs-lookup"><span data-stu-id="f830a-103">You call a property procedure by storing a value in the property or retrieving its value.</span></span> <span data-ttu-id="f830a-104">Bir özelliği bir değişkene erişme aynı şekilde erişin.</span><span class="sxs-lookup"><span data-stu-id="f830a-104">You access a property the same way you access a variable.</span></span>  
  
 <span data-ttu-id="f830a-105">Özelliğin `Set` yordamı bir değer depolar ve kendi `Get` yordamı değerini alır.</span><span class="sxs-lookup"><span data-stu-id="f830a-105">The property's `Set` procedure stores a value, and its `Get` procedure retrieves the value.</span></span> <span data-ttu-id="f830a-106">Ancak, siz açıkça bu yordamları adıyla çağırmayın.</span><span class="sxs-lookup"><span data-stu-id="f830a-106">However, you do not explicitly call these procedures by name.</span></span> <span data-ttu-id="f830a-107">Yalnızca siz depolamak veya bir değişkenin değerini almak bir atama ifadesi veya bir ifade özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="f830a-107">You use the property in an assignment statement or an expression, just as you would store or retrieve the value of a variable.</span></span> <span data-ttu-id="f830a-108">Visual Basic özelliğin yordamları çağrılar.</span><span class="sxs-lookup"><span data-stu-id="f830a-108">Visual Basic makes the calls to the property's procedures.</span></span>  
  
### <a name="to-call-a-propertys-get-procedure"></a><span data-ttu-id="f830a-109">Bir özelliğin Get yordamı çağırmak için</span><span class="sxs-lookup"><span data-stu-id="f830a-109">To call a property's Get procedure</span></span>  
  
1.  <span data-ttu-id="f830a-110">Özellik adı bir ifade bir değişken adı kullanacağınız aynı şekilde kullanın.</span><span class="sxs-lookup"><span data-stu-id="f830a-110">Use the property name in an expression the same way you would use a variable name.</span></span> <span data-ttu-id="f830a-111">Bir özellik kullanabileceğiniz bir değişken veya sabit herhangi bir yerde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f830a-111">You can use a property anywhere you can use a variable or a constant.</span></span>  
  
     <span data-ttu-id="f830a-112">-veya-</span><span class="sxs-lookup"><span data-stu-id="f830a-112">-or-</span></span>  
  
     <span data-ttu-id="f830a-113">Eşittir aşağıdaki özellik adı kullanın (`=`) bir atama deyiminde oturum açın.</span><span class="sxs-lookup"><span data-stu-id="f830a-113">Use the property name following the equal (`=`) sign in an assignment statement.</span></span>  
  
     <span data-ttu-id="f830a-114">Aşağıdaki örnek değeri okuyan <xref:Microsoft.VisualBasic.DateAndTime.Now%2A> örtük olarak arama özelliği, kendi `Get` yordamı.</span><span class="sxs-lookup"><span data-stu-id="f830a-114">The following example reads the value of the <xref:Microsoft.VisualBasic.DateAndTime.Now%2A> property, implicitly calling its `Get` procedure.</span></span>  
  
     [!code-vb[VbVbalrDateProperties#4](./codesnippet/VisualBasic/how-to-call-a-property-procedure_1.vb)]  
  
2.  <span data-ttu-id="f830a-115">Özellik bağımsız değişken alıyorsa, özellik adı bağımsız değişken listesi kapsamak için parantez ile izleyin.</span><span class="sxs-lookup"><span data-stu-id="f830a-115">If the property takes arguments, follow the property name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="f830a-116">Bağımsız değişkenler varsa, isteğe bağlı olarak parantez atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f830a-116">If there are no arguments, you can optionally omit the parentheses.</span></span>  
  
3.  <span data-ttu-id="f830a-117">Bağımsız değişkenler, virgülle ayrılmış parantez içinde bağımsız değişken listesinde yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="f830a-117">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="f830a-118">Bağımsız değişkenler özelliği ilgili parametreleri tanımlar aynı sırada sağladığınız emin olun.</span><span class="sxs-lookup"><span data-stu-id="f830a-118">Be sure you supply the arguments in the same order that the property defines the corresponding parameters.</span></span>  
  
 <span data-ttu-id="f830a-119">İfade bir değişken olarak yalnızca özelliğin değerini katıldığı sabiti misiniz veya değişkenin veya özelliğin Atama ifadesinin sol tarafında depolanır.</span><span class="sxs-lookup"><span data-stu-id="f830a-119">The value of the property participates in the expression just as a variable or constant would, or it is stored in the variable or property on the left side of the assignment statement.</span></span>  
  
### <a name="to-call-a-propertys-set-procedure"></a><span data-ttu-id="f830a-120">Bir özellik çağırmak için yordam kümesinde</span><span class="sxs-lookup"><span data-stu-id="f830a-120">To call a property's Set procedure</span></span>  
  
1.  <span data-ttu-id="f830a-121">Özellik adı atama ifadesinin sol taraftaki kullanın.</span><span class="sxs-lookup"><span data-stu-id="f830a-121">Use the property name on the left side of an assignment statement.</span></span>  
  
     <span data-ttu-id="f830a-122">Aşağıdaki örnek değerini ayarlar <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A> örtük olarak arama özelliği, `Set` yordamı.</span><span class="sxs-lookup"><span data-stu-id="f830a-122">The following example sets the value of the <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A> property, implicitly calling the `Set` procedure.</span></span>  
  
     [!code-vb[VbVbcnProcedures#11](./codesnippet/VisualBasic/how-to-call-a-property-procedure_2.vb)]  
  
2.  <span data-ttu-id="f830a-123">Özellik bağımsız değişken alıyorsa, özellik adı bağımsız değişken listesi kapsamak için parantez ile izleyin.</span><span class="sxs-lookup"><span data-stu-id="f830a-123">If the property takes arguments, follow the property name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="f830a-124">Bağımsız değişkenler varsa, isteğe bağlı olarak parantez atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f830a-124">If there are no arguments, you can optionally omit the parentheses.</span></span>  
  
3.  <span data-ttu-id="f830a-125">Bağımsız değişkenler, virgülle ayrılmış parantez içinde bağımsız değişken listesinde yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="f830a-125">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="f830a-126">Bağımsız değişkenler özelliği ilgili parametreleri tanımlar aynı sırada sağladığınız emin olun.</span><span class="sxs-lookup"><span data-stu-id="f830a-126">Be sure you supply the arguments in the same order that the property defines the corresponding parameters.</span></span>  
  
 <span data-ttu-id="f830a-127">Atama ifadesinin sağ tarafında oluşturulan değeri özelliğinde depolanır.</span><span class="sxs-lookup"><span data-stu-id="f830a-127">The value generated on the right side of the assignment statement is stored in the property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f830a-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f830a-128">See Also</span></span>  
 [<span data-ttu-id="f830a-129">Özellik Yordamları</span><span class="sxs-lookup"><span data-stu-id="f830a-129">Property Procedures</span></span>](./property-procedures.md)  
 [<span data-ttu-id="f830a-130">Yordam Parametreleri ve Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="f830a-130">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="f830a-131">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="f830a-131">Property Statement</span></span>](../../../../visual-basic/language-reference/statements/property-statement.md)  
 [<span data-ttu-id="f830a-132">Visual Basic'de özellikler ve değişkenler arasındaki farklar</span><span class="sxs-lookup"><span data-stu-id="f830a-132">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)  
 [<span data-ttu-id="f830a-133">Nasıl yapılır: Özellik Oluşturma</span><span class="sxs-lookup"><span data-stu-id="f830a-133">How to: Create a Property</span></span>](./how-to-create-a-property.md)  
 [<span data-ttu-id="f830a-134">Nasıl yapılır: Bir Özelliği Karışık Erişim Düzeyleriyle Bildirme</span><span class="sxs-lookup"><span data-stu-id="f830a-134">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)  
 [<span data-ttu-id="f830a-135">Nasıl yapılır: bildirme ve Visual Basic'te varsayılan özelliğini çağırın</span><span class="sxs-lookup"><span data-stu-id="f830a-135">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)  
 [<span data-ttu-id="f830a-136">Nasıl yapılır: Bir Özelliğe Değer Ekleme</span><span class="sxs-lookup"><span data-stu-id="f830a-136">How to: Put a Value in a Property</span></span>](./how-to-put-a-value-in-a-property.md)  
 [<span data-ttu-id="f830a-137">Nasıl yapılır: Bir Özellikten Değer Alma</span><span class="sxs-lookup"><span data-stu-id="f830a-137">How to: Get a Value from a Property</span></span>](./how-to-get-a-value-from-a-property.md)  
 [<span data-ttu-id="f830a-138">Get Deyimi</span><span class="sxs-lookup"><span data-stu-id="f830a-138">Get Statement</span></span>](../../../../visual-basic/language-reference/statements/get-statement.md)  
 [<span data-ttu-id="f830a-139">Set Deyimi</span><span class="sxs-lookup"><span data-stu-id="f830a-139">Set Statement</span></span>](../../../../visual-basic/language-reference/statements/set-statement.md)
