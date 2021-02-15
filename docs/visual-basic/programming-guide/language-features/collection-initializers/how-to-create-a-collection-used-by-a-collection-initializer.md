---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: koleksiyon başlatıcısı tarafından kullanılan bir koleksiyon oluşturma (Visual Basic)'
title: 'Nasıl yapılır: Koleksiyon Başlatıcısı Tarafından Kullanılan Bir Koleksiyon Oluşturma'
ms.date: 07/20/2015
helpviewer_keywords:
- collection initializers [Visual Basic]
ms.assetid: c858db10-424d-47e0-92cd-e08087cc5ebc
ms.openlocfilehash: 09928cb0fbeb0346fd0e1148ffcd6ddce54279c0
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100460026"
---
# <a name="how-to-create-a-collection-used-by-a-collection-initializer-visual-basic"></a><span data-ttu-id="f6b75-103">Nasıl yapılır: Koleksiyon Başlatıcısı Tarafından Kullanılan Bir Koleksiyon Oluşturma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f6b75-103">How to: Create a Collection Used by a Collection Initializer (Visual Basic)</span></span>

<span data-ttu-id="f6b75-104">Koleksiyon oluşturmak için bir koleksiyon başlatıcısı kullandığınızda, Visual Basic derleyici, `Add` yöntemi için parametrelerin `Add` koleksiyon başlatıcısındaki değerlerin türleriyle eşleştiği koleksiyon türünde bir yöntemi arar.</span><span class="sxs-lookup"><span data-stu-id="f6b75-104">When you use a collection initializer to create a collection, the Visual Basic compiler searches for an `Add` method of the collection type for which the parameters for the `Add` method match the types of the values in the collection initializer.</span></span> <span data-ttu-id="f6b75-105">Bu `Add` Yöntem, koleksiyonu koleksiyon başlatıcısındaki değerlerle doldurmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f6b75-105">This `Add` method is used to populate the collection with the values from the collection initializer.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f6b75-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="f6b75-106">Example</span></span>  

 <span data-ttu-id="f6b75-107">Aşağıdaki örnek, `OrderCollection` `Add` bir koleksiyon başlatıcısının türündeki nesneleri eklemek için kullanabileceği bir ortak yöntemi içeren bir koleksiyonu gösterir `Order` .</span><span class="sxs-lookup"><span data-stu-id="f6b75-107">The following example shows an `OrderCollection` collection that contains a public `Add` method that a collection initializer can use to add objects of type `Order`.</span></span> <span data-ttu-id="f6b75-108">`Add`Yöntemi, kısaltılmış koleksiyon başlatıcısı sözdizimini kullanmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="f6b75-108">The `Add` method enables you to use the shortened collection initializer syntax.</span></span>  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#4)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#1)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#2)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="f6b75-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f6b75-109">See also</span></span>

- [<span data-ttu-id="f6b75-110">Koleksiyon Başlatıcıları</span><span class="sxs-lookup"><span data-stu-id="f6b75-110">Collection Initializers</span></span>](index.md)
- [<span data-ttu-id="f6b75-111">Nasıl yapılır: Öğe Başlatıcısı Tarafından Kullanılan Bir Uzantı Ekleme Yöntemi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="f6b75-111">How to: Create an Add Extension Method Used by a Collection Initializer</span></span>](how-to-create-an-add-extension-method-used-by-a-collection-initializer.md)
