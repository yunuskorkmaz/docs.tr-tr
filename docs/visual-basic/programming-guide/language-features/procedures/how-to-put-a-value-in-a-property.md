---
title: 'Nasıl yapılır: Bir özelliğe (Visual Basic) bir değer ekleme'
ms.date: 07/20/2015
helpviewer_keywords:
- property values [Visual Basic]
- Visual Basic code, procedures
- values [Visual Basic], properties
- Visual Basic code, properties
- properties [Visual Basic], values
ms.assetid: c39401e5-b5fc-4439-8f31-ed640f7ce6ed
ms.openlocfilehash: e6aee5ea36c0315d5b01ae2734d17c9e7dab8e93
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59341861"
---
# <a name="how-to-put-a-value-in-a-property-visual-basic"></a><span data-ttu-id="92acf-102">Nasıl yapılır: Bir özelliğe (Visual Basic) bir değer ekleme</span><span class="sxs-lookup"><span data-stu-id="92acf-102">How to: Put a Value in a Property (Visual Basic)</span></span>
<span data-ttu-id="92acf-103">Atama deyiminin sol tarafında özellik adını koyarak bir özelliğe bir değer depolar.</span><span class="sxs-lookup"><span data-stu-id="92acf-103">You store a value in a property by putting the property name on the left side of an assignment statement.</span></span>  
  
 <span data-ttu-id="92acf-104">Özelliğin `Set` yordamı bir değer depolar, ancak siz açıkça bu ada göre çağırmayın.</span><span class="sxs-lookup"><span data-stu-id="92acf-104">The property's `Set` procedure stores a value, but you do not explicitly call it by name.</span></span> <span data-ttu-id="92acf-105">Bir değişken kullanma gibi özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="92acf-105">You use the property just as you would use a variable.</span></span> <span data-ttu-id="92acf-106">Visual Basic özelliğin yordamları çağrılar yapar.</span><span class="sxs-lookup"><span data-stu-id="92acf-106">Visual Basic makes the calls to the property's procedures.</span></span>  
  
### <a name="to-store-a-value-in-a-property"></a><span data-ttu-id="92acf-107">Bir özelliğin değeri depolamak için</span><span class="sxs-lookup"><span data-stu-id="92acf-107">To store a value in a property</span></span>  
  
1. <span data-ttu-id="92acf-108">Özellik adı, atama deyiminin sol tarafında kullanın.</span><span class="sxs-lookup"><span data-stu-id="92acf-108">Use the property name on the left side of an assignment statement.</span></span>  
  
     <span data-ttu-id="92acf-109">Aşağıdaki örnek, Visual Basic değerini ayarlar `TimeOfDay` noon, örtük olarak arama özelliğini kendi `Set` yordamı.</span><span class="sxs-lookup"><span data-stu-id="92acf-109">The following example sets the value of the Visual Basic `TimeOfDay` property to noon, implicitly calling its `Set` procedure.</span></span>  
  
     [!code-vb[VbVbcnProcedures#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#11)]  
  
2. <span data-ttu-id="92acf-110">Özellik bağımsız değişkeni alır, parantez içine bağımsız değişken listesi için özellik adıyla izleyin.</span><span class="sxs-lookup"><span data-stu-id="92acf-110">If the property takes arguments, follow the property name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="92acf-111">Hiçbir bağımsız değişken varsa, isteğe bağlı olarak ayraçları atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="92acf-111">If there are no arguments, you can optionally omit the parentheses.</span></span>  
  
3. <span data-ttu-id="92acf-112">Bağımsız değişken listesi parantezlerinin virgülle ayırarak yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="92acf-112">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="92acf-113">Bağımsız değişkenler özelliği karşılık gelen parametreleri tanımlar aynı sırada sağladığınız emin olun.</span><span class="sxs-lookup"><span data-stu-id="92acf-113">Be sure you supply the arguments in the same order that the property defines the corresponding parameters.</span></span>  
  
4. <span data-ttu-id="92acf-114">Atama ifadesi sağ tarafında oluşturulan değeri özelliğinde depolanır.</span><span class="sxs-lookup"><span data-stu-id="92acf-114">The value generated on the right side of the assignment statement is stored in the property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92acf-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="92acf-115">See also</span></span>

- <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A>
- [<span data-ttu-id="92acf-116">Özellik Yordamları</span><span class="sxs-lookup"><span data-stu-id="92acf-116">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="92acf-117">Yordam Parametreleri ve Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="92acf-117">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="92acf-118">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="92acf-118">Property Statement</span></span>](../../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="92acf-119">Visual Basic'de özellikler ile değişkenler arasındaki farklar</span><span class="sxs-lookup"><span data-stu-id="92acf-119">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)
- [<span data-ttu-id="92acf-120">Nasıl yapılır: Özellik oluşturma</span><span class="sxs-lookup"><span data-stu-id="92acf-120">How to: Create a Property</span></span>](./how-to-create-a-property.md)
- [<span data-ttu-id="92acf-121">Nasıl yapılır: Bir özelliği karışık erişim düzeyleriyle bildirme</span><span class="sxs-lookup"><span data-stu-id="92acf-121">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)
- [<span data-ttu-id="92acf-122">Nasıl yapılır: Bir özellik yordamı çağırma</span><span class="sxs-lookup"><span data-stu-id="92acf-122">How to: Call a Property Procedure</span></span>](./how-to-call-a-property-procedure.md)
- [<span data-ttu-id="92acf-123">Nasıl yapılır: Bildirme ve Visual Basic'te bir varsayılan özelliğini çağırın</span><span class="sxs-lookup"><span data-stu-id="92acf-123">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)
- [<span data-ttu-id="92acf-124">Nasıl yapılır: Bir özellikten değer alma</span><span class="sxs-lookup"><span data-stu-id="92acf-124">How to: Get a Value from a Property</span></span>](./how-to-get-a-value-from-a-property.md)
