---
title: 'Nasıl yapılır: Bir Özelliğe Değer Ekleme'
ms.date: 07/20/2015
helpviewer_keywords:
- property values [Visual Basic]
- Visual Basic code, procedures
- values [Visual Basic], properties
- Visual Basic code, properties
- properties [Visual Basic], values
ms.assetid: c39401e5-b5fc-4439-8f31-ed640f7ce6ed
ms.openlocfilehash: c0fb3e137010390097a68aea161efcff93839d94
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414343"
---
# <a name="how-to-put-a-value-in-a-property-visual-basic"></a><span data-ttu-id="f14ca-102">Nasıl yapılır: Bir Özelliğe Değer Ekleme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f14ca-102">How to: Put a Value in a Property (Visual Basic)</span></span>
<span data-ttu-id="f14ca-103">Özellik adını atama ifadesinin sol tarafına yerleştirerek bir özelliği bir değer depoluyorsanız.</span><span class="sxs-lookup"><span data-stu-id="f14ca-103">You store a value in a property by putting the property name on the left side of an assignment statement.</span></span>  
  
 <span data-ttu-id="f14ca-104">Özelliğin `Set` yordamı bir değer depolar, ancak bunu açıkça adıyla çağırmayın.</span><span class="sxs-lookup"><span data-stu-id="f14ca-104">The property's `Set` procedure stores a value, but you do not explicitly call it by name.</span></span> <span data-ttu-id="f14ca-105">Özelliğini, bir değişkeni kullandığınız gibi kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="f14ca-105">You use the property just as you would use a variable.</span></span> <span data-ttu-id="f14ca-106">Visual Basic, özelliğin yordamlarına çağrı yapar.</span><span class="sxs-lookup"><span data-stu-id="f14ca-106">Visual Basic makes the calls to the property's procedures.</span></span>  
  
### <a name="to-store-a-value-in-a-property"></a><span data-ttu-id="f14ca-107">Bir özelliğinde bir değeri depolamak için</span><span class="sxs-lookup"><span data-stu-id="f14ca-107">To store a value in a property</span></span>  
  
1. <span data-ttu-id="f14ca-108">Atama ifadesinin sol tarafındaki özellik adını kullanın.</span><span class="sxs-lookup"><span data-stu-id="f14ca-108">Use the property name on the left side of an assignment statement.</span></span>  
  
     <span data-ttu-id="f14ca-109">Aşağıdaki örnek, `TimeOfDay` yordamını dolaylı olarak çağıran Visual Basic özelliğinin değerini öğle olarak ayarlar `Set` .</span><span class="sxs-lookup"><span data-stu-id="f14ca-109">The following example sets the value of the Visual Basic `TimeOfDay` property to noon, implicitly calling its `Set` procedure.</span></span>  
  
     [!code-vb[VbVbcnProcedures#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#11)]  
  
2. <span data-ttu-id="f14ca-110">Özelliği bağımsız değişkenler alırsa, bağımsız değişken listesini kapsamak için parantez ile birlikte özellik adını izleyin.</span><span class="sxs-lookup"><span data-stu-id="f14ca-110">If the property takes arguments, follow the property name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="f14ca-111">Bağımsız değişken yoksa, isteğe bağlı olarak ayraçları atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f14ca-111">If there are no arguments, you can optionally omit the parentheses.</span></span>  
  
3. <span data-ttu-id="f14ca-112">Bağımsız değişkenleri virgülle ayırarak parantez içindeki bağımsız değişken listesine yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="f14ca-112">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="f14ca-113">Bağımsız değişkenleri özelliğin ilgili parametreleri tanımladığı sırayla girdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="f14ca-113">Be sure you supply the arguments in the same order that the property defines the corresponding parameters.</span></span>  
  
4. <span data-ttu-id="f14ca-114">Atama ifadesinin sağ tarafında oluşturulan değer özelliğinde depolanır.</span><span class="sxs-lookup"><span data-stu-id="f14ca-114">The value generated on the right side of the assignment statement is stored in the property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f14ca-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f14ca-115">See also</span></span>

- <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A>
- [<span data-ttu-id="f14ca-116">Özellik Yordamları</span><span class="sxs-lookup"><span data-stu-id="f14ca-116">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="f14ca-117">Yordam Parametreleri ve Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="f14ca-117">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="f14ca-118">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="f14ca-118">Property Statement</span></span>](../../../language-reference/statements/property-statement.md)
- [<span data-ttu-id="f14ca-119">Visual Basic'de Özellikler ve Değişkenler Arasındaki Farklar</span><span class="sxs-lookup"><span data-stu-id="f14ca-119">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)
- [<span data-ttu-id="f14ca-120">Nasıl yapılır: Özellik Oluşturma</span><span class="sxs-lookup"><span data-stu-id="f14ca-120">How to: Create a Property</span></span>](./how-to-create-a-property.md)
- [<span data-ttu-id="f14ca-121">Nasıl yapılır: Bir Özelliği Karışık Erişim Düzeyleriyle Bildirme</span><span class="sxs-lookup"><span data-stu-id="f14ca-121">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)
- [<span data-ttu-id="f14ca-122">Nasıl yapılır: Bir Özellik Yordamı Çağırma</span><span class="sxs-lookup"><span data-stu-id="f14ca-122">How to: Call a Property Procedure</span></span>](./how-to-call-a-property-procedure.md)
- [<span data-ttu-id="f14ca-123">Nasıl yapılır: Visual Basic'de Varsayılan Bir Özelliği Bildirme ve Çağırma</span><span class="sxs-lookup"><span data-stu-id="f14ca-123">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)
- [<span data-ttu-id="f14ca-124">Nasıl yapılır: Bir Özellikten Değer Alma</span><span class="sxs-lookup"><span data-stu-id="f14ca-124">How to: Get a Value from a Property</span></span>](./how-to-get-a-value-from-a-property.md)
