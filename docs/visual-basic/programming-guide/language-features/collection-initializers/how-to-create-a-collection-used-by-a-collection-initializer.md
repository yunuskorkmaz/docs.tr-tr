---
title: 'Nasıl yapılır: (Visual Basic) koleksiyon başlatıcısı tarafından kullanılan bir koleksiyon oluşturma'
ms.date: 07/20/2015
helpviewer_keywords:
- collection initializers [Visual Basic]
ms.assetid: c858db10-424d-47e0-92cd-e08087cc5ebc
ms.openlocfilehash: aaa367e5a1739f26e9b0458d8f2fc44462b73b7b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54631730"
---
# <a name="how-to-create-a-collection-used-by-a-collection-initializer-visual-basic"></a><span data-ttu-id="5dc8b-102">Nasıl yapılır: (Visual Basic) koleksiyon başlatıcısı tarafından kullanılan bir koleksiyon oluşturma</span><span class="sxs-lookup"><span data-stu-id="5dc8b-102">How to: Create a Collection Used by a Collection Initializer (Visual Basic)</span></span>
<span data-ttu-id="5dc8b-103">Bir koleksiyon oluşturmak için bir koleksiyon Başlatıcısı kullandığınızda, Visual Basic Derleyicisi arar bir `Add` koleksiyon türü yöntemi için parametreleri `Add` koleksiyon Başlatıcısı değerleri türlerini match yöntemi.</span><span class="sxs-lookup"><span data-stu-id="5dc8b-103">When you use a collection initializer to create a collection, the Visual Basic compiler searches for an `Add` method of the collection type for which the parameters for the `Add` method match the types of the values in the collection initializer.</span></span> <span data-ttu-id="5dc8b-104">Bu `Add` yöntemi koleksiyon Başlatıcısı değerlerle doldurmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5dc8b-104">This `Add` method is used to populate the collection with the values from the collection initializer.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5dc8b-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="5dc8b-105">Example</span></span>  
 <span data-ttu-id="5dc8b-106">Aşağıdaki örnekte gösterildiği bir `OrderCollection` içeren bir genel koleksiyon `Add` koleksiyon Başlatıcısı türden nesneleri eklemek için kullanabileceğiniz yöntem `Order`.</span><span class="sxs-lookup"><span data-stu-id="5dc8b-106">The following example shows an `OrderCollection` collection that contains a public `Add` method that a collection initializer can use to add objects of type `Order`.</span></span> <span data-ttu-id="5dc8b-107">`Add` Yöntemi kısaltılmış koleksiyon Başlatıcısı sözdizimi kullanmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="5dc8b-107">The `Add` method enables you to use the shortened collection initializer syntax.</span></span>  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#4](../../../../visual-basic/programming-guide/language-features/collection-initializers/codesnippet/VisualBasic/how-to-create-a-collection-used-by-a-collection-initializer_1.vb)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#1](../../../../visual-basic/programming-guide/language-features/collection-initializers/codesnippet/VisualBasic/how-to-create-a-collection-used-by-a-collection-initializer_2.vb)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#2](../../../../visual-basic/programming-guide/language-features/collection-initializers/codesnippet/VisualBasic/how-to-create-a-collection-used-by-a-collection-initializer_3.vb)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#3](../../../../visual-basic/programming-guide/language-features/collection-initializers/codesnippet/VisualBasic/how-to-create-a-collection-used-by-a-collection-initializer_4.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="5dc8b-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5dc8b-108">See also</span></span>
- [<span data-ttu-id="5dc8b-109">Öğe Başlatıcıları</span><span class="sxs-lookup"><span data-stu-id="5dc8b-109">Collection Initializers</span></span>](../../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)
- [<span data-ttu-id="5dc8b-110">Nasıl yapılır: Oluşturma bir koleksiyon başlatıcısı tarafından kullanılan uzantı ekleme metodu</span><span class="sxs-lookup"><span data-stu-id="5dc8b-110">How to: Create an Add Extension Method Used by a Collection Initializer</span></span>](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-an-add-extension-method-used-by-a-collection-initializer.md)
