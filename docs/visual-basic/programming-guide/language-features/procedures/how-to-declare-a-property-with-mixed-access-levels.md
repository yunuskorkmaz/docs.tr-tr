---
title: 'Nasıl yapılır: Bir özelliği karışık erişim düzeyleri (Visual Basic) bildirme'
ms.date: 07/20/2015
helpviewer_keywords:
- access levels [Visual Basic], properties
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- mixed access levels
- Visual Basic code, properties
- properties [Visual Basic], access levels
- Property statement [Visual Basic], declaring mixed access levels
ms.assetid: fdbb2d97-279a-4956-b26c-cbdfbc34915a
ms.openlocfilehash: e899b57e02f492b0e4909aca84c069e5b7688618
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61863694"
---
# <a name="how-to-declare-a-property-with-mixed-access-levels-visual-basic"></a><span data-ttu-id="e7ae4-102">Nasıl yapılır: Bir özelliği karışık erişim düzeyleri (Visual Basic) bildirme</span><span class="sxs-lookup"><span data-stu-id="e7ae4-102">How to: Declare a Property with Mixed Access Levels (Visual Basic)</span></span>
<span data-ttu-id="e7ae4-103">İsterseniz `Get` ve `Set` yordamları farklı erişim düzeylerine sahip bir özellik üzerinde daha fazla izin veremez düzeyinde kullanabilirsiniz `Property` deyimi ve ya da daha kısıtlayıcı düzeyinde `Get` veya `Set` deyimi.</span><span class="sxs-lookup"><span data-stu-id="e7ae4-103">If you want the `Get` and `Set` procedures on a property to have different access levels, you can use the more permissive level in the `Property` statement and the more restrictive level in either the `Get` or `Set` statement.</span></span> <span data-ttu-id="e7ae4-104">Belirli bölümlerini özelliğin değerini almak kod ve belirli bir değeri değiştirmek kod bölümlerini istediğinizde bir özelliği karışık erişim düzeyleriyle kullanın.</span><span class="sxs-lookup"><span data-stu-id="e7ae4-104">You use mixed access levels on a property when you want certain parts of the code to be able to get the property's value, and certain other parts of the code to be able to change the value.</span></span>  
  
 <span data-ttu-id="e7ae4-105">Erişim düzeyleri hakkında daha fazla bilgi için bkz. [erişim düzeyini Visual Basic'te](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="e7ae4-105">For more information on access levels, see [Access levels in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
### <a name="to-declare-a-property-with-mixed-access-levels"></a><span data-ttu-id="e7ae4-106">Bir özelliği karışık erişim düzeyleriyle bildirme</span><span class="sxs-lookup"><span data-stu-id="e7ae4-106">To declare a property with mixed access levels</span></span>  
  
1. <span data-ttu-id="e7ae4-107">Normal bir şekilde özelliği bildirme ve daha az kısıtlayıcı erişim düzeyini belirtin (gibi `Public`) içinde `Property` deyimi.</span><span class="sxs-lookup"><span data-stu-id="e7ae4-107">Declare the property in the normal way, and specify the less restrictive access level (such as `Public`) in the `Property` statement.</span></span>  
  
2. <span data-ttu-id="e7ae4-108">Ya da bildirmek `Get` veya `Set` daha kısıtlayıcı erişim düzeyini belirterek yordamı (gibi `Friend`).</span><span class="sxs-lookup"><span data-stu-id="e7ae4-108">Declare either the `Get` or the `Set` procedure specifying the more restrictive access level (such as `Friend`).</span></span>  
  
3. <span data-ttu-id="e7ae4-109">Bir özellik yordamı üzerinde bir erişim düzeyi belirtmeyin.</span><span class="sxs-lookup"><span data-stu-id="e7ae4-109">Do not specify an access level on the other property procedure.</span></span> <span data-ttu-id="e7ae4-110">Bildirilen erişim düzeyi varsayar `Property` deyimi.</span><span class="sxs-lookup"><span data-stu-id="e7ae4-110">It assumes the access level declared in the `Property` statement.</span></span> <span data-ttu-id="e7ae4-111">Özellik yordamları yalnızca birinde erişimi kısıtlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e7ae4-111">You can restrict access on only one of the property procedures.</span></span>  
  
     [!code-vb[VbVbcnProcedures#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#10)]  
  
     <span data-ttu-id="e7ae4-112">Önceki örnekte, `Get` yordamı sahip aynı `Protected` özellik kendisine erişim sırasında `Set` yordamı sahip `Private` erişim.</span><span class="sxs-lookup"><span data-stu-id="e7ae4-112">In the preceding example, the `Get` procedure has the same `Protected` access as the property itself, while the `Set` procedure has `Private` access.</span></span> <span data-ttu-id="e7ae4-113">Öğesinden türetilen bir sınıf `employee` okuyabilirsiniz `salary` değeri, ancak yalnızca `employee` sınıf ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e7ae4-113">A class derived from `employee` can read the `salary` value, but only the `employee` class can set it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7ae4-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e7ae4-114">See also</span></span>

- [<span data-ttu-id="e7ae4-115">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="e7ae4-115">Procedures</span></span>](./index.md)
- [<span data-ttu-id="e7ae4-116">Özellik Yordamları</span><span class="sxs-lookup"><span data-stu-id="e7ae4-116">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="e7ae4-117">Yordam Parametreleri ve Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="e7ae4-117">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="e7ae4-118">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="e7ae4-118">Property Statement</span></span>](../../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="e7ae4-119">Visual Basic'de özellikler ile değişkenler arasındaki farklar</span><span class="sxs-lookup"><span data-stu-id="e7ae4-119">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)
- [<span data-ttu-id="e7ae4-120">Nasıl yapılır: Özellik oluşturma</span><span class="sxs-lookup"><span data-stu-id="e7ae4-120">How to: Create a Property</span></span>](./how-to-create-a-property.md)
- [<span data-ttu-id="e7ae4-121">Nasıl yapılır: Bir özellik yordamı çağırma</span><span class="sxs-lookup"><span data-stu-id="e7ae4-121">How to: Call a Property Procedure</span></span>](./how-to-call-a-property-procedure.md)
- [<span data-ttu-id="e7ae4-122">Nasıl yapılır: Bildirme ve Visual Basic'te bir varsayılan özelliğini çağırın</span><span class="sxs-lookup"><span data-stu-id="e7ae4-122">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)
- [<span data-ttu-id="e7ae4-123">Nasıl yapılır: Bir özelliğe değer ekleme</span><span class="sxs-lookup"><span data-stu-id="e7ae4-123">How to: Put a Value in a Property</span></span>](./how-to-put-a-value-in-a-property.md)
- [<span data-ttu-id="e7ae4-124">Nasıl yapılır: Bir özellikten değer alma</span><span class="sxs-lookup"><span data-stu-id="e7ae4-124">How to: Get a Value from a Property</span></span>](./how-to-get-a-value-from-a-property.md)
