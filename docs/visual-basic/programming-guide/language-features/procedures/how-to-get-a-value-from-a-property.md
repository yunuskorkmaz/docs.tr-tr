---
title: 'Nasıl yapılır: Bir Özellikten Değer Alma (Visual Basic)'
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- property values [Visual Basic]
- Visual Basic code, procedures
- values [Visual Basic], properties
- Visual Basic code, properties
- properties [Visual Basic], values
ms.assetid: 3954423e-6ab7-4a4c-b55c-a8d27be47891
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7161052b9d9b388d8da8bd421c3b220f15037805
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-get-a-value-from-a-property-visual-basic"></a><span data-ttu-id="fb8b9-102">Nasıl yapılır: Bir Özellikten Değer Alma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fb8b9-102">How to: Get a Value from a Property (Visual Basic)</span></span>
<span data-ttu-id="fb8b9-103">Bir ifadeyi özellik adı dahil olmak üzere bir özelliğin değerini alır.</span><span class="sxs-lookup"><span data-stu-id="fb8b9-103">You retrieve a property's value by including the property name in an expression.</span></span>  
  
 <span data-ttu-id="fb8b9-104">Özelliğin `Get` yordamı değeri alır, ancak siz açıkça, ada göre çağırmayın.</span><span class="sxs-lookup"><span data-stu-id="fb8b9-104">The property's `Get` procedure retrieves the value, but you do not explicitly call it by name.</span></span> <span data-ttu-id="fb8b9-105">Bir değişken kullandığınız özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="fb8b9-105">You use the property just as you would use a variable.</span></span> <span data-ttu-id="fb8b9-106">Visual Basic özelliğin yordamları çağrılar.</span><span class="sxs-lookup"><span data-stu-id="fb8b9-106">Visual Basic makes the calls to the property's procedures.</span></span>  
  
### <a name="to-retrieve-a-value-from-a-property"></a><span data-ttu-id="fb8b9-107">Bir özellikten değer almak için</span><span class="sxs-lookup"><span data-stu-id="fb8b9-107">To retrieve a value from a property</span></span>  
  
1.  <span data-ttu-id="fb8b9-108">Özellik adı bir ifade bir değişken adı kullanacağınız aynı şekilde kullanın.</span><span class="sxs-lookup"><span data-stu-id="fb8b9-108">Use the property name in an expression the same way you would use a variable name.</span></span> <span data-ttu-id="fb8b9-109">Bir özellik kullanabileceğiniz bir değişken veya sabit herhangi bir yerde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fb8b9-109">You can use a property anywhere you can use a variable or a constant.</span></span>  
  
     <span data-ttu-id="fb8b9-110">-veya-</span><span class="sxs-lookup"><span data-stu-id="fb8b9-110">-or-</span></span>  
  
     <span data-ttu-id="fb8b9-111">Eşittir aşağıdaki özellik adı kullanın (`=`) bir atama deyiminde oturum açın.</span><span class="sxs-lookup"><span data-stu-id="fb8b9-111">Use the property name following the equal (`=`) sign in an assignment statement.</span></span>  
  
     <span data-ttu-id="fb8b9-112">Aşağıdaki örnek Visual Basic değerini okur `Now` örtük olarak arama özelliği, kendi `Get` yordamı.</span><span class="sxs-lookup"><span data-stu-id="fb8b9-112">The following example reads the value of the Visual Basic `Now` property, implicitly calling its `Get` procedure.</span></span>  
  
     [!code-vb[VbVbalrDateProperties#4](./codesnippet/VisualBasic/how-to-get-a-value-from-a-property_1.vb)]  
  
2.  <span data-ttu-id="fb8b9-113">Özellik bağımsız değişken alıyorsa, özellik adı bağımsız değişken listesi kapsamak için parantez ile izleyin.</span><span class="sxs-lookup"><span data-stu-id="fb8b9-113">If the property takes arguments, follow the property name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="fb8b9-114">Bağımsız değişkenler varsa, isteğe bağlı olarak parantez atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fb8b9-114">If there are no arguments, you can optionally omit the parentheses.</span></span>  
  
3.  <span data-ttu-id="fb8b9-115">Bağımsız değişkenler, virgülle ayrılmış parantez içinde bağımsız değişken listesinde yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="fb8b9-115">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="fb8b9-116">Bağımsız değişkenler özelliği ilgili parametreleri tanımlar aynı sırada sağladığınız emin olun.</span><span class="sxs-lookup"><span data-stu-id="fb8b9-116">Be sure you supply the arguments in the same order that the property defines the corresponding parameters.</span></span>  
  
 <span data-ttu-id="fb8b9-117">İfade bir değişken olarak yalnızca özelliğin değerini katıldığı sabiti misiniz veya değişkenin veya özelliğin Atama ifadesinin sol tarafında depolanır.</span><span class="sxs-lookup"><span data-stu-id="fb8b9-117">The value of the property participates in the expression just as a variable or constant would, or it is stored in the variable or property on the left side of the assignment statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb8b9-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fb8b9-118">See Also</span></span>  
 [<span data-ttu-id="fb8b9-119">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="fb8b9-119">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="fb8b9-120">Özellik Yordamları</span><span class="sxs-lookup"><span data-stu-id="fb8b9-120">Property Procedures</span></span>](./property-procedures.md)  
 [<span data-ttu-id="fb8b9-121">Yordam Parametreleri ve Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="fb8b9-121">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="fb8b9-122">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="fb8b9-122">Property Statement</span></span>](../../../../visual-basic/language-reference/statements/property-statement.md)  
 [<span data-ttu-id="fb8b9-123">Visual Basic'de özellikler ve değişkenler arasındaki farklar</span><span class="sxs-lookup"><span data-stu-id="fb8b9-123">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)  
 [<span data-ttu-id="fb8b9-124">Nasıl yapılır: Özellik Oluşturma</span><span class="sxs-lookup"><span data-stu-id="fb8b9-124">How to: Create a Property</span></span>](./how-to-create-a-property.md)  
 [<span data-ttu-id="fb8b9-125">Nasıl yapılır: Bir Özelliği Karışık Erişim Düzeyleriyle Bildirme</span><span class="sxs-lookup"><span data-stu-id="fb8b9-125">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)  
 [<span data-ttu-id="fb8b9-126">Nasıl yapılır: Bir Özellik Yordamı Çağırma</span><span class="sxs-lookup"><span data-stu-id="fb8b9-126">How to: Call a Property Procedure</span></span>](./how-to-call-a-property-procedure.md)  
 [<span data-ttu-id="fb8b9-127">Nasıl yapılır: bildirme ve Visual Basic'te varsayılan özelliğini çağırın</span><span class="sxs-lookup"><span data-stu-id="fb8b9-127">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)  
 [<span data-ttu-id="fb8b9-128">Nasıl yapılır: Bir Özelliğe Değer Ekleme</span><span class="sxs-lookup"><span data-stu-id="fb8b9-128">How to: Put a Value in a Property</span></span>](./how-to-put-a-value-in-a-property.md)
