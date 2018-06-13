---
title: 'Nasıl yapılır: Koleksiyon Başlatıcısı Tarafından Kullanılan Bir Koleksiyon Oluşturma (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- collection initializers [Visual Basic]
ms.assetid: c858db10-424d-47e0-92cd-e08087cc5ebc
ms.openlocfilehash: 6158b6f02d95260e2955e77d732fae8b8d9d5e04
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33654167"
---
# <a name="how-to-create-a-collection-used-by-a-collection-initializer-visual-basic"></a><span data-ttu-id="0f9aa-102">Nasıl yapılır: Koleksiyon Başlatıcısı Tarafından Kullanılan Bir Koleksiyon Oluşturma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0f9aa-102">How to: Create a Collection Used by a Collection Initializer (Visual Basic)</span></span>
<span data-ttu-id="0f9aa-103">Bir koleksiyon oluşturmak için koleksiyon Başlatıcısı kullandığınızda, Visual Basic derleyici arar bir `Add` koleksiyon türü yöntemi için hangi parametrelerini `Add` yöntemi eşleşen koleksiyon Başlatıcısı değerlerde türleri.</span><span class="sxs-lookup"><span data-stu-id="0f9aa-103">When you use a collection initializer to create a collection, the Visual Basic compiler searches for an `Add` method of the collection type for which the parameters for the `Add` method match the types of the values in the collection initializer.</span></span> <span data-ttu-id="0f9aa-104">Bu `Add` yöntemi koleksiyonu koleksiyon Başlatıcısı gelen değerlerle doldurmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0f9aa-104">This `Add` method is used to populate the collection with the values from the collection initializer.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0f9aa-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="0f9aa-105">Example</span></span>  
 <span data-ttu-id="0f9aa-106">Aşağıdaki örnekte gösterildiği bir `OrderCollection` ortak bir içeren koleksiyon `Add` koleksiyon Başlatıcısı türündeki nesneleri eklemek için kullanabileceğiniz yöntemini `Order`.</span><span class="sxs-lookup"><span data-stu-id="0f9aa-106">The following example shows an `OrderCollection` collection that contains a public `Add` method that a collection initializer can use to add objects of type `Order`.</span></span> <span data-ttu-id="0f9aa-107">`Add` Yöntemi kısaltılmış koleksiyon Başlatıcısı sözdizimi kullanmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="0f9aa-107">The `Add` method enables you to use the shortened collection initializer syntax.</span></span>  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#4](../../../../visual-basic/programming-guide/language-features/collection-initializers/codesnippet/VisualBasic/how-to-create-a-collection-used-by-a-collection-initializer_1.vb)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#1](../../../../visual-basic/programming-guide/language-features/collection-initializers/codesnippet/VisualBasic/how-to-create-a-collection-used-by-a-collection-initializer_2.vb)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#2](../../../../visual-basic/programming-guide/language-features/collection-initializers/codesnippet/VisualBasic/how-to-create-a-collection-used-by-a-collection-initializer_3.vb)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#3](../../../../visual-basic/programming-guide/language-features/collection-initializers/codesnippet/VisualBasic/how-to-create-a-collection-used-by-a-collection-initializer_4.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="0f9aa-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0f9aa-108">See Also</span></span>  
 [<span data-ttu-id="0f9aa-109">Öğe Başlatıcıları</span><span class="sxs-lookup"><span data-stu-id="0f9aa-109">Collection Initializers</span></span>](../../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)  
 [<span data-ttu-id="0f9aa-110">Nasıl yapılır: Öğe Başlatıcısı Tarafından Kullanılan Bir Uzantı Ekleme Yöntemi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="0f9aa-110">How to: Create an Add Extension Method Used by a Collection Initializer</span></span>](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-an-add-extension-method-used-by-a-collection-initializer.md)
