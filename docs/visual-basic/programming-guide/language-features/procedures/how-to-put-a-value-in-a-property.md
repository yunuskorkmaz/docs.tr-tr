---
title: "Nasıl yapılır: Bir Özelliğe Değer Ekleme (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- property values [Visual Basic]
- Visual Basic code, procedures
- values [Visual Basic], properties
- Visual Basic code, properties
- properties [Visual Basic], values
ms.assetid: c39401e5-b5fc-4439-8f31-ed640f7ce6ed
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 44e7c4a92ea3d087c12e74aa2ede33a52c8730cf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-put-a-value-in-a-property-visual-basic"></a><span data-ttu-id="be73f-102">Nasıl yapılır: Bir Özelliğe Değer Ekleme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="be73f-102">How to: Put a Value in a Property (Visual Basic)</span></span>
<span data-ttu-id="be73f-103">Bir özellik değeri Atama ifadesinin sol tarafta özellik adını koyarak depolar.</span><span class="sxs-lookup"><span data-stu-id="be73f-103">You store a value in a property by putting the property name on the left side of an assignment statement.</span></span>  
  
 <span data-ttu-id="be73f-104">Özelliğin `Set` yordamı bir değer depolar, ancak siz açıkça, ada göre çağırmayın.</span><span class="sxs-lookup"><span data-stu-id="be73f-104">The property's `Set` procedure stores a value, but you do not explicitly call it by name.</span></span> <span data-ttu-id="be73f-105">Bir değişken kullandığınız özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="be73f-105">You use the property just as you would use a variable.</span></span> [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="be73f-106">özelliğin yordamlara çağrılar.</span><span class="sxs-lookup"><span data-stu-id="be73f-106"> makes the calls to the property's procedures.</span></span>  
  
### <a name="to-store-a-value-in-a-property"></a><span data-ttu-id="be73f-107">Bir özelliğin değeri depolamak için</span><span class="sxs-lookup"><span data-stu-id="be73f-107">To store a value in a property</span></span>  
  
1.  <span data-ttu-id="be73f-108">Özellik adı atama ifadesinin sol taraftaki kullanın.</span><span class="sxs-lookup"><span data-stu-id="be73f-108">Use the property name on the left side of an assignment statement.</span></span>  
  
     <span data-ttu-id="be73f-109">Aşağıdaki örnek değerini ayarlar [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] `TimeOfDay` öğlen, örtük çağırma özelliğine kendi `Set` yordamı.</span><span class="sxs-lookup"><span data-stu-id="be73f-109">The following example sets the value of the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] `TimeOfDay` property to noon, implicitly calling its `Set` procedure.</span></span>  
  
     [!code-vb[VbVbcnProcedures#11](./codesnippet/VisualBasic/how-to-put-a-value-in-a-property_1.vb)]  
  
2.  <span data-ttu-id="be73f-110">Özellik bağımsız değişken alıyorsa, özellik adı bağımsız değişken listesi kapsamak için parantez ile izleyin.</span><span class="sxs-lookup"><span data-stu-id="be73f-110">If the property takes arguments, follow the property name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="be73f-111">Bağımsız değişkenler varsa, isteğe bağlı olarak parantez atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="be73f-111">If there are no arguments, you can optionally omit the parentheses.</span></span>  
  
3.  <span data-ttu-id="be73f-112">Bağımsız değişkenler, virgülle ayrılmış parantez içinde bağımsız değişken listesinde yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="be73f-112">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="be73f-113">Bağımsız değişkenler özelliği ilgili parametreleri tanımlar aynı sırada sağladığınız emin olun.</span><span class="sxs-lookup"><span data-stu-id="be73f-113">Be sure you supply the arguments in the same order that the property defines the corresponding parameters.</span></span>  
  
4.  <span data-ttu-id="be73f-114">Atama ifadesinin sağ tarafında oluşturulan değeri özelliğinde depolanır.</span><span class="sxs-lookup"><span data-stu-id="be73f-114">The value generated on the right side of the assignment statement is stored in the property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be73f-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="be73f-115">See Also</span></span>  
 <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A>  
 [<span data-ttu-id="be73f-116">Özellik yordamları</span><span class="sxs-lookup"><span data-stu-id="be73f-116">Property Procedures</span></span>](./property-procedures.md)  
 [<span data-ttu-id="be73f-117">Parametreler ve bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="be73f-117">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="be73f-118">Property deyimi</span><span class="sxs-lookup"><span data-stu-id="be73f-118">Property Statement</span></span>](../../../../visual-basic/language-reference/statements/property-statement.md)  
 [<span data-ttu-id="be73f-119">Visual Basic'de özellikler ve değişkenler arasındaki farklar</span><span class="sxs-lookup"><span data-stu-id="be73f-119">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)  
 [<span data-ttu-id="be73f-120">Nasıl yapılır: özellik oluşturma</span><span class="sxs-lookup"><span data-stu-id="be73f-120">How to: Create a Property</span></span>](./how-to-create-a-property.md)  
 [<span data-ttu-id="be73f-121">Nasıl yapılır: bir özelliği karışık erişim düzeyleriyle bildirme</span><span class="sxs-lookup"><span data-stu-id="be73f-121">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)  
 [<span data-ttu-id="be73f-122">Nasıl yapılır: bir özellik yordamı çağırma</span><span class="sxs-lookup"><span data-stu-id="be73f-122">How to: Call a Property Procedure</span></span>](./how-to-call-a-property-procedure.md)  
 [<span data-ttu-id="be73f-123">Nasıl yapılır: bildirme ve Visual Basic'te varsayılan özelliğini çağırın</span><span class="sxs-lookup"><span data-stu-id="be73f-123">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)  
 [<span data-ttu-id="be73f-124">Nasıl yapılır: bir özellikten değer alma</span><span class="sxs-lookup"><span data-stu-id="be73f-124">How to: Get a Value from a Property</span></span>](./how-to-get-a-value-from-a-property.md)
