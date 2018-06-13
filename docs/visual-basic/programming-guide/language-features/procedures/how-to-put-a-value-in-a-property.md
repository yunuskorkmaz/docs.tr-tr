---
title: 'Nasıl yapılır: Bir Özelliğe Değer Ekleme (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- property values [Visual Basic]
- Visual Basic code, procedures
- values [Visual Basic], properties
- Visual Basic code, properties
- properties [Visual Basic], values
ms.assetid: c39401e5-b5fc-4439-8f31-ed640f7ce6ed
ms.openlocfilehash: 29e68ca2b9436921c81346eb1def2417157aae9c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33650377"
---
# <a name="how-to-put-a-value-in-a-property-visual-basic"></a><span data-ttu-id="0a6b4-102">Nasıl yapılır: Bir Özelliğe Değer Ekleme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0a6b4-102">How to: Put a Value in a Property (Visual Basic)</span></span>
<span data-ttu-id="0a6b4-103">Bir özellik değeri Atama ifadesinin sol tarafta özellik adını koyarak depolar.</span><span class="sxs-lookup"><span data-stu-id="0a6b4-103">You store a value in a property by putting the property name on the left side of an assignment statement.</span></span>  
  
 <span data-ttu-id="0a6b4-104">Özelliğin `Set` yordamı bir değer depolar, ancak siz açıkça, ada göre çağırmayın.</span><span class="sxs-lookup"><span data-stu-id="0a6b4-104">The property's `Set` procedure stores a value, but you do not explicitly call it by name.</span></span> <span data-ttu-id="0a6b4-105">Bir değişken kullandığınız özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="0a6b4-105">You use the property just as you would use a variable.</span></span> <span data-ttu-id="0a6b4-106">Visual Basic özelliğin yordamları çağrılar.</span><span class="sxs-lookup"><span data-stu-id="0a6b4-106">Visual Basic makes the calls to the property's procedures.</span></span>  
  
### <a name="to-store-a-value-in-a-property"></a><span data-ttu-id="0a6b4-107">Bir özelliğin değeri depolamak için</span><span class="sxs-lookup"><span data-stu-id="0a6b4-107">To store a value in a property</span></span>  
  
1.  <span data-ttu-id="0a6b4-108">Özellik adı atama ifadesinin sol taraftaki kullanın.</span><span class="sxs-lookup"><span data-stu-id="0a6b4-108">Use the property name on the left side of an assignment statement.</span></span>  
  
     <span data-ttu-id="0a6b4-109">Aşağıdaki örnek Visual Basic değerini ayarlar `TimeOfDay` öğlen, örtük çağırma özelliğine kendi `Set` yordamı.</span><span class="sxs-lookup"><span data-stu-id="0a6b4-109">The following example sets the value of the Visual Basic `TimeOfDay` property to noon, implicitly calling its `Set` procedure.</span></span>  
  
     [!code-vb[VbVbcnProcedures#11](./codesnippet/VisualBasic/how-to-put-a-value-in-a-property_1.vb)]  
  
2.  <span data-ttu-id="0a6b4-110">Özellik bağımsız değişken alıyorsa, özellik adı bağımsız değişken listesi kapsamak için parantez ile izleyin.</span><span class="sxs-lookup"><span data-stu-id="0a6b4-110">If the property takes arguments, follow the property name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="0a6b4-111">Bağımsız değişkenler varsa, isteğe bağlı olarak parantez atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0a6b4-111">If there are no arguments, you can optionally omit the parentheses.</span></span>  
  
3.  <span data-ttu-id="0a6b4-112">Bağımsız değişkenler, virgülle ayrılmış parantez içinde bağımsız değişken listesinde yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="0a6b4-112">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="0a6b4-113">Bağımsız değişkenler özelliği ilgili parametreleri tanımlar aynı sırada sağladığınız emin olun.</span><span class="sxs-lookup"><span data-stu-id="0a6b4-113">Be sure you supply the arguments in the same order that the property defines the corresponding parameters.</span></span>  
  
4.  <span data-ttu-id="0a6b4-114">Atama ifadesinin sağ tarafında oluşturulan değeri özelliğinde depolanır.</span><span class="sxs-lookup"><span data-stu-id="0a6b4-114">The value generated on the right side of the assignment statement is stored in the property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a6b4-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0a6b4-115">See Also</span></span>  
 <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A>  
 [<span data-ttu-id="0a6b4-116">Özellik Yordamları</span><span class="sxs-lookup"><span data-stu-id="0a6b4-116">Property Procedures</span></span>](./property-procedures.md)  
 [<span data-ttu-id="0a6b4-117">Yordam Parametreleri ve Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="0a6b4-117">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="0a6b4-118">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="0a6b4-118">Property Statement</span></span>](../../../../visual-basic/language-reference/statements/property-statement.md)  
 [<span data-ttu-id="0a6b4-119">Visual Basic'de özellikler ve değişkenler arasındaki farklar</span><span class="sxs-lookup"><span data-stu-id="0a6b4-119">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)  
 [<span data-ttu-id="0a6b4-120">Nasıl yapılır: Özellik Oluşturma</span><span class="sxs-lookup"><span data-stu-id="0a6b4-120">How to: Create a Property</span></span>](./how-to-create-a-property.md)  
 [<span data-ttu-id="0a6b4-121">Nasıl yapılır: Bir Özelliği Karışık Erişim Düzeyleriyle Bildirme</span><span class="sxs-lookup"><span data-stu-id="0a6b4-121">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)  
 [<span data-ttu-id="0a6b4-122">Nasıl yapılır: Bir Özellik Yordamı Çağırma</span><span class="sxs-lookup"><span data-stu-id="0a6b4-122">How to: Call a Property Procedure</span></span>](./how-to-call-a-property-procedure.md)  
 [<span data-ttu-id="0a6b4-123">Nasıl yapılır: bildirme ve Visual Basic'te varsayılan özelliğini çağırın</span><span class="sxs-lookup"><span data-stu-id="0a6b4-123">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)  
 [<span data-ttu-id="0a6b4-124">Nasıl yapılır: Bir Özellikten Değer Alma</span><span class="sxs-lookup"><span data-stu-id="0a6b4-124">How to: Get a Value from a Property</span></span>](./how-to-get-a-value-from-a-property.md)
