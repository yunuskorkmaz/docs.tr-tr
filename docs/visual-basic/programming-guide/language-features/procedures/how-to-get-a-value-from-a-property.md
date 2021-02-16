---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: bir özellikten değer alma (Visual Basic)'
title: 'Nasıl yapılır: Bir Özellikten Değer Alma'
ms.date: 07/20/2015
helpviewer_keywords:
- property values [Visual Basic]
- Visual Basic code, procedures
- values [Visual Basic], properties
- Visual Basic code, properties
- properties [Visual Basic], values
ms.assetid: 3954423e-6ab7-4a4c-b55c-a8d27be47891
ms.openlocfilehash: 5626ad1a248c3bb51e0f80076628c8108e424186
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100427602"
---
# <a name="how-to-get-a-value-from-a-property-visual-basic"></a><span data-ttu-id="388ec-103">Nasıl yapılır: Bir Özellikten Değer Alma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="388ec-103">How to: Get a Value from a Property (Visual Basic)</span></span>

<span data-ttu-id="388ec-104">Özellik adını bir ifadeye ekleyerek bir özelliğin değerini elde edersiniz.</span><span class="sxs-lookup"><span data-stu-id="388ec-104">You retrieve a property's value by including the property name in an expression.</span></span>  
  
 <span data-ttu-id="388ec-105">Özelliğin `Get` yordamı değeri alır, ancak bunu açıkça adıyla çağırmayın.</span><span class="sxs-lookup"><span data-stu-id="388ec-105">The property's `Get` procedure retrieves the value, but you do not explicitly call it by name.</span></span> <span data-ttu-id="388ec-106">Özelliğini, bir değişkeni kullandığınız gibi kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="388ec-106">You use the property just as you would use a variable.</span></span> <span data-ttu-id="388ec-107">Visual Basic, özelliğin yordamlarına çağrı yapar.</span><span class="sxs-lookup"><span data-stu-id="388ec-107">Visual Basic makes the calls to the property's procedures.</span></span>  
  
### <a name="to-retrieve-a-value-from-a-property"></a><span data-ttu-id="388ec-108">Bir özellikten değer almak için</span><span class="sxs-lookup"><span data-stu-id="388ec-108">To retrieve a value from a property</span></span>  
  
1. <span data-ttu-id="388ec-109">Bir ifadede özellik adını bir değişken adı kullandığınız şekilde kullanın.</span><span class="sxs-lookup"><span data-stu-id="388ec-109">Use the property name in an expression the same way you would use a variable name.</span></span> <span data-ttu-id="388ec-110">Bir özelliği, bir değişkeni veya sabiti kullanabileceğiniz her yerde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="388ec-110">You can use a property anywhere you can use a variable or a constant.</span></span>  
  
     <span data-ttu-id="388ec-111">-veya-</span><span class="sxs-lookup"><span data-stu-id="388ec-111">-or-</span></span>  
  
     <span data-ttu-id="388ec-112">Atama ifadesinde eşittir () işaretinden sonra özellik adını kullanın `=` .</span><span class="sxs-lookup"><span data-stu-id="388ec-112">Use the property name following the equal (`=`) sign in an assignment statement.</span></span>  
  
     <span data-ttu-id="388ec-113">Aşağıdaki örnek, `Now` yordamını dolaylı olarak çağıran Visual Basic özelliğinin değerini okur `Get` .</span><span class="sxs-lookup"><span data-stu-id="388ec-113">The following example reads the value of the Visual Basic `Now` property, implicitly calling its `Get` procedure.</span></span>  
  
     [!code-vb[VbVbalrDateProperties#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDateProperties/VB/Module1.vb#4)]  
  
2. <span data-ttu-id="388ec-114">Özelliği bağımsız değişkenler alırsa, bağımsız değişken listesini kapsamak için parantez ile birlikte özellik adını izleyin.</span><span class="sxs-lookup"><span data-stu-id="388ec-114">If the property takes arguments, follow the property name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="388ec-115">Bağımsız değişken yoksa, isteğe bağlı olarak ayraçları atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="388ec-115">If there are no arguments, you can optionally omit the parentheses.</span></span>  
  
3. <span data-ttu-id="388ec-116">Bağımsız değişkenleri virgülle ayırarak parantez içindeki bağımsız değişken listesine yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="388ec-116">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="388ec-117">Bağımsız değişkenleri özelliğin ilgili parametreleri tanımladığı sırayla girdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="388ec-117">Be sure you supply the arguments in the same order that the property defines the corresponding parameters.</span></span>  
  
 <span data-ttu-id="388ec-118">Özelliğin değeri, ifadeye yalnızca değişken veya sabit gibi, ya da atama deyiminin sol tarafındaki değişkende veya özellikte saklanır.</span><span class="sxs-lookup"><span data-stu-id="388ec-118">The value of the property participates in the expression just as a variable or constant would, or it is stored in the variable or property on the left side of the assignment statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="388ec-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="388ec-119">See also</span></span>

- [<span data-ttu-id="388ec-120">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="388ec-120">Procedures</span></span>](./index.md)
- [<span data-ttu-id="388ec-121">Özellik Yordamları</span><span class="sxs-lookup"><span data-stu-id="388ec-121">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="388ec-122">Yordam Parametreleri ve Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="388ec-122">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="388ec-123">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="388ec-123">Property Statement</span></span>](../../../language-reference/statements/property-statement.md)
- [<span data-ttu-id="388ec-124">Visual Basic'de Özellikler ve Değişkenler Arasındaki Farklar</span><span class="sxs-lookup"><span data-stu-id="388ec-124">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)
- [<span data-ttu-id="388ec-125">Nasıl yapılır: Özellik Oluşturma</span><span class="sxs-lookup"><span data-stu-id="388ec-125">How to: Create a Property</span></span>](./how-to-create-a-property.md)
- [<span data-ttu-id="388ec-126">Nasıl yapılır: Bir Özelliği Karışık Erişim Düzeyleriyle Bildirme</span><span class="sxs-lookup"><span data-stu-id="388ec-126">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)
- [<span data-ttu-id="388ec-127">Nasıl yapılır: Bir Özellik Yordamı Çağırma</span><span class="sxs-lookup"><span data-stu-id="388ec-127">How to: Call a Property Procedure</span></span>](./how-to-call-a-property-procedure.md)
- [<span data-ttu-id="388ec-128">Nasıl yapılır: Visual Basic'de Varsayılan Bir Özelliği Bildirme ve Çağırma</span><span class="sxs-lookup"><span data-stu-id="388ec-128">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)
- [<span data-ttu-id="388ec-129">Nasıl yapılır: Bir Özelliğe Değer Ekleme</span><span class="sxs-lookup"><span data-stu-id="388ec-129">How to: Put a Value in a Property</span></span>](./how-to-put-a-value-in-a-property.md)
