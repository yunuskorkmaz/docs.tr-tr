---
title: 'Nasıl yapılır: Değer bir özelliği (Visual Basic) alma'
ms.date: 07/20/2015
helpviewer_keywords:
- property values [Visual Basic]
- Visual Basic code, procedures
- values [Visual Basic], properties
- Visual Basic code, properties
- properties [Visual Basic], values
ms.assetid: 3954423e-6ab7-4a4c-b55c-a8d27be47891
ms.openlocfilehash: 5e2676a0880092a78405fe5dafa0469161b85610
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59302939"
---
# <a name="how-to-get-a-value-from-a-property-visual-basic"></a><span data-ttu-id="cc98e-102">Nasıl yapılır: Değer bir özelliği (Visual Basic) alma</span><span class="sxs-lookup"><span data-stu-id="cc98e-102">How to: Get a Value from a Property (Visual Basic)</span></span>
<span data-ttu-id="cc98e-103">Bir özelliğin değeri, özellik adı bir ifade dahil ederek alın.</span><span class="sxs-lookup"><span data-stu-id="cc98e-103">You retrieve a property's value by including the property name in an expression.</span></span>  
  
 <span data-ttu-id="cc98e-104">Özelliğin `Get` yordamı değeri alır, ancak siz açıkça bu ada göre çağırmayın.</span><span class="sxs-lookup"><span data-stu-id="cc98e-104">The property's `Get` procedure retrieves the value, but you do not explicitly call it by name.</span></span> <span data-ttu-id="cc98e-105">Bir değişken kullanma gibi özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="cc98e-105">You use the property just as you would use a variable.</span></span> <span data-ttu-id="cc98e-106">Visual Basic özelliğin yordamları çağrılar yapar.</span><span class="sxs-lookup"><span data-stu-id="cc98e-106">Visual Basic makes the calls to the property's procedures.</span></span>  
  
### <a name="to-retrieve-a-value-from-a-property"></a><span data-ttu-id="cc98e-107">Bir özellikten değer almak için</span><span class="sxs-lookup"><span data-stu-id="cc98e-107">To retrieve a value from a property</span></span>  
  
1. <span data-ttu-id="cc98e-108">Özellik adı bir ifade bir değişken adı kullanacağınız aynı şekilde kullanın.</span><span class="sxs-lookup"><span data-stu-id="cc98e-108">Use the property name in an expression the same way you would use a variable name.</span></span> <span data-ttu-id="cc98e-109">Bir özellik kullanabileceğiniz bir değişken veya sabit her yerde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cc98e-109">You can use a property anywhere you can use a variable or a constant.</span></span>  
  
     <span data-ttu-id="cc98e-110">-veya-</span><span class="sxs-lookup"><span data-stu-id="cc98e-110">-or-</span></span>  
  
     <span data-ttu-id="cc98e-111">Eşit aşağıdaki özellik adını kullanın (`=`) bir atama ifadesinde oturum açın.</span><span class="sxs-lookup"><span data-stu-id="cc98e-111">Use the property name following the equal (`=`) sign in an assignment statement.</span></span>  
  
     <span data-ttu-id="cc98e-112">Aşağıdaki örnek, Visual Basic değerini okur `Now` örtük olarak arama özelliğini kendi `Get` yordamı.</span><span class="sxs-lookup"><span data-stu-id="cc98e-112">The following example reads the value of the Visual Basic `Now` property, implicitly calling its `Get` procedure.</span></span>  
  
     [!code-vb[VbVbalrDateProperties#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDateProperties/VB/Module1.vb#4)]  
  
2. <span data-ttu-id="cc98e-113">Özellik bağımsız değişkeni alır, parantez içine bağımsız değişken listesi için özellik adıyla izleyin.</span><span class="sxs-lookup"><span data-stu-id="cc98e-113">If the property takes arguments, follow the property name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="cc98e-114">Hiçbir bağımsız değişken varsa, isteğe bağlı olarak ayraçları atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cc98e-114">If there are no arguments, you can optionally omit the parentheses.</span></span>  
  
3. <span data-ttu-id="cc98e-115">Bağımsız değişken listesi parantezlerinin virgülle ayırarak yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="cc98e-115">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="cc98e-116">Bağımsız değişkenler özelliği karşılık gelen parametreleri tanımlar aynı sırada sağladığınız emin olun.</span><span class="sxs-lookup"><span data-stu-id="cc98e-116">Be sure you supply the arguments in the same order that the property defines the corresponding parameters.</span></span>  
  
 <span data-ttu-id="cc98e-117">İfade bir değişken gibi bir özelliğin değerini katıldığı sabiti misiniz veya değişken veya özellik atama ifadesi sol tarafında depolanır.</span><span class="sxs-lookup"><span data-stu-id="cc98e-117">The value of the property participates in the expression just as a variable or constant would, or it is stored in the variable or property on the left side of the assignment statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc98e-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cc98e-118">See also</span></span>

- [<span data-ttu-id="cc98e-119">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="cc98e-119">Procedures</span></span>](./index.md)
- [<span data-ttu-id="cc98e-120">Özellik Yordamları</span><span class="sxs-lookup"><span data-stu-id="cc98e-120">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="cc98e-121">Yordam Parametreleri ve Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="cc98e-121">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="cc98e-122">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="cc98e-122">Property Statement</span></span>](../../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="cc98e-123">Visual Basic'de Özellikler ve Değişkenler Arasındaki Farklar</span><span class="sxs-lookup"><span data-stu-id="cc98e-123">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)
- [<span data-ttu-id="cc98e-124">Nasıl yapılır: Özellik Oluşturma</span><span class="sxs-lookup"><span data-stu-id="cc98e-124">How to: Create a Property</span></span>](./how-to-create-a-property.md)
- [<span data-ttu-id="cc98e-125">Nasıl yapılır: Bir Özelliği Karışık Erişim Düzeyleriyle Bildirme</span><span class="sxs-lookup"><span data-stu-id="cc98e-125">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)
- [<span data-ttu-id="cc98e-126">Nasıl yapılır: Bir Özellik Yordamı Çağırma</span><span class="sxs-lookup"><span data-stu-id="cc98e-126">How to: Call a Property Procedure</span></span>](./how-to-call-a-property-procedure.md)
- [<span data-ttu-id="cc98e-127">Nasıl yapılır: Bildirme ve Visual Basic'te bir varsayılan özelliğini çağırın</span><span class="sxs-lookup"><span data-stu-id="cc98e-127">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)
- [<span data-ttu-id="cc98e-128">Nasıl yapılır: Bir Özelliğe Değer Ekleme</span><span class="sxs-lookup"><span data-stu-id="cc98e-128">How to: Put a Value in a Property</span></span>](./how-to-put-a-value-in-a-property.md)
