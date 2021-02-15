---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: bir özelliğe değer koyma (Visual Basic)'
title: 'Nasıl yapılır: Bir Özelliğe Değer Ekleme'
ms.date: 07/20/2015
helpviewer_keywords:
- property values [Visual Basic]
- Visual Basic code, procedures
- values [Visual Basic], properties
- Visual Basic code, properties
- properties [Visual Basic], values
ms.assetid: c39401e5-b5fc-4439-8f31-ed640f7ce6ed
ms.openlocfilehash: 62f5552f821fb98bd3a4695505aba5ff73b08fc7
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100476208"
---
# <a name="how-to-put-a-value-in-a-property-visual-basic"></a><span data-ttu-id="9cf60-103">Nasıl yapılır: Bir Özelliğe Değer Ekleme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9cf60-103">How to: Put a Value in a Property (Visual Basic)</span></span>

<span data-ttu-id="9cf60-104">Özellik adını atama ifadesinin sol tarafına yerleştirerek bir özelliği bir değer depoluyorsanız.</span><span class="sxs-lookup"><span data-stu-id="9cf60-104">You store a value in a property by putting the property name on the left side of an assignment statement.</span></span>  
  
 <span data-ttu-id="9cf60-105">Özelliğin `Set` yordamı bir değer depolar, ancak bunu açıkça adıyla çağırmayın.</span><span class="sxs-lookup"><span data-stu-id="9cf60-105">The property's `Set` procedure stores a value, but you do not explicitly call it by name.</span></span> <span data-ttu-id="9cf60-106">Özelliğini, bir değişkeni kullandığınız gibi kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="9cf60-106">You use the property just as you would use a variable.</span></span> <span data-ttu-id="9cf60-107">Visual Basic, özelliğin yordamlarına çağrı yapar.</span><span class="sxs-lookup"><span data-stu-id="9cf60-107">Visual Basic makes the calls to the property's procedures.</span></span>  
  
### <a name="to-store-a-value-in-a-property"></a><span data-ttu-id="9cf60-108">Bir özelliğinde bir değeri depolamak için</span><span class="sxs-lookup"><span data-stu-id="9cf60-108">To store a value in a property</span></span>  
  
1. <span data-ttu-id="9cf60-109">Atama ifadesinin sol tarafındaki özellik adını kullanın.</span><span class="sxs-lookup"><span data-stu-id="9cf60-109">Use the property name on the left side of an assignment statement.</span></span>  
  
     <span data-ttu-id="9cf60-110">Aşağıdaki örnek, `TimeOfDay` yordamını dolaylı olarak çağıran Visual Basic özelliğinin değerini öğle olarak ayarlar `Set` .</span><span class="sxs-lookup"><span data-stu-id="9cf60-110">The following example sets the value of the Visual Basic `TimeOfDay` property to noon, implicitly calling its `Set` procedure.</span></span>  
  
     [!code-vb[VbVbcnProcedures#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#11)]  
  
2. <span data-ttu-id="9cf60-111">Özelliği bağımsız değişkenler alırsa, bağımsız değişken listesini kapsamak için parantez ile birlikte özellik adını izleyin.</span><span class="sxs-lookup"><span data-stu-id="9cf60-111">If the property takes arguments, follow the property name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="9cf60-112">Bağımsız değişken yoksa, isteğe bağlı olarak ayraçları atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9cf60-112">If there are no arguments, you can optionally omit the parentheses.</span></span>  
  
3. <span data-ttu-id="9cf60-113">Bağımsız değişkenleri virgülle ayırarak parantez içindeki bağımsız değişken listesine yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="9cf60-113">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="9cf60-114">Bağımsız değişkenleri özelliğin ilgili parametreleri tanımladığı sırayla girdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="9cf60-114">Be sure you supply the arguments in the same order that the property defines the corresponding parameters.</span></span>  
  
4. <span data-ttu-id="9cf60-115">Atama ifadesinin sağ tarafında oluşturulan değer özelliğinde depolanır.</span><span class="sxs-lookup"><span data-stu-id="9cf60-115">The value generated on the right side of the assignment statement is stored in the property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9cf60-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9cf60-116">See also</span></span>

- <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A>
- [<span data-ttu-id="9cf60-117">Özellik Yordamları</span><span class="sxs-lookup"><span data-stu-id="9cf60-117">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="9cf60-118">Yordam Parametreleri ve Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="9cf60-118">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="9cf60-119">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="9cf60-119">Property Statement</span></span>](../../../language-reference/statements/property-statement.md)
- [<span data-ttu-id="9cf60-120">Visual Basic'de Özellikler ve Değişkenler Arasındaki Farklar</span><span class="sxs-lookup"><span data-stu-id="9cf60-120">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)
- [<span data-ttu-id="9cf60-121">Nasıl yapılır: Özellik Oluşturma</span><span class="sxs-lookup"><span data-stu-id="9cf60-121">How to: Create a Property</span></span>](./how-to-create-a-property.md)
- [<span data-ttu-id="9cf60-122">Nasıl yapılır: Bir Özelliği Karışık Erişim Düzeyleriyle Bildirme</span><span class="sxs-lookup"><span data-stu-id="9cf60-122">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)
- [<span data-ttu-id="9cf60-123">Nasıl yapılır: Bir Özellik Yordamı Çağırma</span><span class="sxs-lookup"><span data-stu-id="9cf60-123">How to: Call a Property Procedure</span></span>](./how-to-call-a-property-procedure.md)
- [<span data-ttu-id="9cf60-124">Nasıl yapılır: Visual Basic'de Varsayılan Bir Özelliği Bildirme ve Çağırma</span><span class="sxs-lookup"><span data-stu-id="9cf60-124">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)
- [<span data-ttu-id="9cf60-125">Nasıl yapılır: Bir Özellikten Değer Alma</span><span class="sxs-lookup"><span data-stu-id="9cf60-125">How to: Get a Value from a Property</span></span>](./how-to-get-a-value-from-a-property.md)
