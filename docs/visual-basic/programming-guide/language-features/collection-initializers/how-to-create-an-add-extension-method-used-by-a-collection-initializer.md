---
title: 'Nasıl yapılır: Oluşturma bir genişletme yöntemi (Visual Basic) koleksiyon başlatıcısı tarafından kullanılan Ekle'
ms.date: 07/20/2015
helpviewer_keywords:
- collection initializers [Visual Basic]
ms.assetid: f64b52c7-8b11-4410-93a6-cb3aeebcc772
ms.openlocfilehash: a5af41e25b8f82aa173e2df28cc41b313c8d68dd
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58825410"
---
# <a name="how-to-create-an-add-extension-method-used-by-a-collection-initializer-visual-basic"></a><span data-ttu-id="957d6-102">Nasıl yapılır: Oluşturma bir genişletme yöntemi (Visual Basic) koleksiyon başlatıcısı tarafından kullanılan Ekle</span><span class="sxs-lookup"><span data-stu-id="957d6-102">How to: Create an Add Extension Method Used by a Collection Initializer (Visual Basic)</span></span>
<span data-ttu-id="957d6-103">Bir koleksiyon oluşturmak için bir koleksiyon Başlatıcısı kullandığınızda, Visual Basic Derleyicisi arar bir `Add` koleksiyon türü yöntemi için parametreleri `Add` koleksiyon Başlatıcısı değerleri türlerini match yöntemi.</span><span class="sxs-lookup"><span data-stu-id="957d6-103">When you use a collection initializer to create a collection, the Visual Basic compiler searches for an `Add` method of the collection type for which the parameters for the `Add` method match the types of the values in the collection initializer.</span></span> <span data-ttu-id="957d6-104">Bu `Add` yöntemi koleksiyon Başlatıcısı değerlerle doldurmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="957d6-104">This `Add` method is used to populate the collection with the values from the collection initializer.</span></span>  
  
 <span data-ttu-id="957d6-105">Hiç eşleşen `Add` yöntemi var ve koleksiyon kodunu değiştiremediğiniz, adlı bir genişletme yöntemi ekleyebilirsiniz `Add` koleksiyon başlatıcısı tarafından gerekli olan parametreleri alır.</span><span class="sxs-lookup"><span data-stu-id="957d6-105">If no matching `Add` method exists and you cannot modify the code for the collection, you can add an extension method called `Add` that takes the parameters that are required by the collection initializer.</span></span> <span data-ttu-id="957d6-106">Genel koleksiyonlar için koleksiyon başlatıcıları kullandığınızda yapmanız gerekenler genellikle budur.</span><span class="sxs-lookup"><span data-stu-id="957d6-106">This is typically what you need to do when you use collection initializers for generic collections.</span></span>  
  
## <a name="example"></a><span data-ttu-id="957d6-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="957d6-107">Example</span></span>  
 <span data-ttu-id="957d6-108">Aşağıdaki örnek, bir genişletme yöntemi için genel ekleme işlemi gösterilmektedir <xref:System.Collections.Generic.List%601> koleksiyon Başlatıcısı türden nesneleri eklemek için kullanılabilir olacak şekilde yazın `Employee`.</span><span class="sxs-lookup"><span data-stu-id="957d6-108">The following example shows how to add an extension method to the generic <xref:System.Collections.Generic.List%601> type so that a collection initializer can be used to add objects of type `Employee`.</span></span> <span data-ttu-id="957d6-109">Genişletme yöntemi, kısaltılmış koleksiyon Başlatıcısı sözdizimi kullanmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="957d6-109">The extension method enables you to use the shortened collection initializer syntax.</span></span>  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo1/VB/Module1.vb#1)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo1/VB/Module1.vb#2)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo1/VB/Module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="957d6-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="957d6-110">See also</span></span>

- [<span data-ttu-id="957d6-111">Öğe Başlatıcıları</span><span class="sxs-lookup"><span data-stu-id="957d6-111">Collection Initializers</span></span>](../../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)
- [<span data-ttu-id="957d6-112">Nasıl yapılır: Koleksiyon başlatıcısı tarafından kullanılan bir koleksiyon oluşturma</span><span class="sxs-lookup"><span data-stu-id="957d6-112">How to: Create a Collection Used by a Collection Initializer</span></span>](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-a-collection-used-by-a-collection-initializer.md)
