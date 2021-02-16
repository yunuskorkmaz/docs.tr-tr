---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: karışık erişim düzeylerine sahip bir özellik bildirme (Visual Basic)'
title: 'Nasıl yapılır: Bir Özelliği Karışık Erişim Düzeyleriyle Bildirme'
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
ms.openlocfilehash: e01849b0a590e499c1ee7b4a67d6aa794cd7cc5d
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100472468"
---
# <a name="how-to-declare-a-property-with-mixed-access-levels-visual-basic"></a><span data-ttu-id="cc0ec-103">Nasıl yapılır: Bir Özelliği Karışık Erişim Düzeyleriyle Bildirme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cc0ec-103">How to: Declare a Property with Mixed Access Levels (Visual Basic)</span></span>

<span data-ttu-id="cc0ec-104">`Get` `Set` Bir özellik üzerindeki ve yordamlarının farklı erişim düzeylerine sahip olmasını istiyorsanız, deyimdeki daha fazla izin düzeyini `Property` ve ya da ifadesinde daha kısıtlayıcı olan düzeyi kullanabilirsiniz `Get` `Set` .</span><span class="sxs-lookup"><span data-stu-id="cc0ec-104">If you want the `Get` and `Set` procedures on a property to have different access levels, you can use the more permissive level in the `Property` statement and the more restrictive level in either the `Get` or `Set` statement.</span></span> <span data-ttu-id="cc0ec-105">Kodun belirli bölümlerinin özelliğin değerini almasını ve kodun değeri değiştirebilmesini sağlamak için, bir özellik üzerinde karışık erişim düzeyleri kullanırsınız,.</span><span class="sxs-lookup"><span data-stu-id="cc0ec-105">You use mixed access levels on a property when you want certain parts of the code to be able to get the property's value, and certain other parts of the code to be able to change the value.</span></span>  
  
 <span data-ttu-id="cc0ec-106">Erişim düzeyleri hakkında daha fazla bilgi için bkz. [Visual Basic erişim düzeyleri](../declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="cc0ec-106">For more information on access levels, see [Access levels in Visual Basic](../declared-elements/access-levels.md).</span></span>  
  
### <a name="to-declare-a-property-with-mixed-access-levels"></a><span data-ttu-id="cc0ec-107">Karışık erişim düzeylerine sahip bir özelliği bildirmek için</span><span class="sxs-lookup"><span data-stu-id="cc0ec-107">To declare a property with mixed access levels</span></span>  
  
1. <span data-ttu-id="cc0ec-108">Özelliği normal şekilde bildirin ve deyimdeki daha az kısıtlayıcı erişim düzeyini (gibi `Public` ) belirtin `Property` .</span><span class="sxs-lookup"><span data-stu-id="cc0ec-108">Declare the property in the normal way, and specify the less restrictive access level (such as `Public`) in the `Property` statement.</span></span>  
  
2. <span data-ttu-id="cc0ec-109">`Get`Ya da `Set` daha kısıtlayıcı erişim düzeyini (gibi) belirten yordamı bildirin `Friend` .</span><span class="sxs-lookup"><span data-stu-id="cc0ec-109">Declare either the `Get` or the `Set` procedure specifying the more restrictive access level (such as `Friend`).</span></span>  
  
3. <span data-ttu-id="cc0ec-110">Diğer özellik yordamında bir erişim düzeyi belirtmeyin.</span><span class="sxs-lookup"><span data-stu-id="cc0ec-110">Do not specify an access level on the other property procedure.</span></span> <span data-ttu-id="cc0ec-111">Bu, bildiriminde belirtilen erişim düzeyini varsayar `Property` .</span><span class="sxs-lookup"><span data-stu-id="cc0ec-111">It assumes the access level declared in the `Property` statement.</span></span> <span data-ttu-id="cc0ec-112">Yalnızca özellik yordamlarından birinde erişimi kısıtlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cc0ec-112">You can restrict access on only one of the property procedures.</span></span>  
  
     [!code-vb[VbVbcnProcedures#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#10)]  
  
     <span data-ttu-id="cc0ec-113">Önceki örnekte, yordam, `Get` `Protected` özelliğin kendisiyle aynı erişime sahiptir, ancak `Set` yordam `Private` erişimidir.</span><span class="sxs-lookup"><span data-stu-id="cc0ec-113">In the preceding example, the `Get` procedure has the same `Protected` access as the property itself, while the `Set` procedure has `Private` access.</span></span> <span data-ttu-id="cc0ec-114">Öğesinden türetilen bir sınıf `employee` `salary` değeri okuyabilir, ancak yalnızca `employee` sınıfı ayarlayabilir.</span><span class="sxs-lookup"><span data-stu-id="cc0ec-114">A class derived from `employee` can read the `salary` value, but only the `employee` class can set it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc0ec-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cc0ec-115">See also</span></span>

- [<span data-ttu-id="cc0ec-116">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="cc0ec-116">Procedures</span></span>](./index.md)
- [<span data-ttu-id="cc0ec-117">Özellik Yordamları</span><span class="sxs-lookup"><span data-stu-id="cc0ec-117">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="cc0ec-118">Yordam Parametreleri ve Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="cc0ec-118">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="cc0ec-119">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="cc0ec-119">Property Statement</span></span>](../../../language-reference/statements/property-statement.md)
- [<span data-ttu-id="cc0ec-120">Visual Basic'de Özellikler ve Değişkenler Arasındaki Farklar</span><span class="sxs-lookup"><span data-stu-id="cc0ec-120">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)
- [<span data-ttu-id="cc0ec-121">Nasıl yapılır: Özellik Oluşturma</span><span class="sxs-lookup"><span data-stu-id="cc0ec-121">How to: Create a Property</span></span>](./how-to-create-a-property.md)
- [<span data-ttu-id="cc0ec-122">Nasıl yapılır: Bir Özellik Yordamı Çağırma</span><span class="sxs-lookup"><span data-stu-id="cc0ec-122">How to: Call a Property Procedure</span></span>](./how-to-call-a-property-procedure.md)
- [<span data-ttu-id="cc0ec-123">Nasıl yapılır: Visual Basic'de Varsayılan Bir Özelliği Bildirme ve Çağırma</span><span class="sxs-lookup"><span data-stu-id="cc0ec-123">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)
- [<span data-ttu-id="cc0ec-124">Nasıl yapılır: Bir Özelliğe Değer Ekleme</span><span class="sxs-lookup"><span data-stu-id="cc0ec-124">How to: Put a Value in a Property</span></span>](./how-to-put-a-value-in-a-property.md)
- [<span data-ttu-id="cc0ec-125">Nasıl yapılır: Bir Özellikten Değer Alma</span><span class="sxs-lookup"><span data-stu-id="cc0ec-125">How to: Get a Value from a Property</span></span>](./how-to-get-a-value-from-a-property.md)
