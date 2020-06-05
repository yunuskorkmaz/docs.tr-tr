---
title: 'Nasıl yapılır: Koleksiyon Başlatıcısı Tarafından Kullanılan Bir Uzantı Ekleme Yöntemi Oluşturma'
ms.date: 07/20/2015
helpviewer_keywords:
- collection initializers [Visual Basic]
ms.assetid: f64b52c7-8b11-4410-93a6-cb3aeebcc772
ms.openlocfilehash: 4dbe6146b70181864a6717146071f9b93a1f583e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414575"
---
# <a name="how-to-create-an-add-extension-method-used-by-a-collection-initializer-visual-basic"></a><span data-ttu-id="76cb0-102">Nasıl yapılır: Koleksiyon Başlatıcısı Tarafından Kullanılan Bir Uzantı Ekleme Yöntemi Oluşturma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="76cb0-102">How to: Create an Add Extension Method Used by a Collection Initializer (Visual Basic)</span></span>
<span data-ttu-id="76cb0-103">Koleksiyon oluşturmak için bir koleksiyon başlatıcısı kullandığınızda, Visual Basic derleyici, `Add` yöntemi için parametrelerin `Add` koleksiyon başlatıcısındaki değerlerin türleriyle eşleştiği koleksiyon türünde bir yöntemi arar.</span><span class="sxs-lookup"><span data-stu-id="76cb0-103">When you use a collection initializer to create a collection, the Visual Basic compiler searches for an `Add` method of the collection type for which the parameters for the `Add` method match the types of the values in the collection initializer.</span></span> <span data-ttu-id="76cb0-104">Bu `Add` Yöntem, koleksiyonu koleksiyon başlatıcısındaki değerlerle doldurmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="76cb0-104">This `Add` method is used to populate the collection with the values from the collection initializer.</span></span>  
  
 <span data-ttu-id="76cb0-105">Eşleşen `Add` bir yöntem yoksa ve koleksiyon için kodu değiştiremeyeceğiniz takdirde, `Add` koleksiyon başlatıcısı tarafından gereken parametreleri alan adlı bir genişletme yöntemi ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="76cb0-105">If no matching `Add` method exists and you cannot modify the code for the collection, you can add an extension method called `Add` that takes the parameters that are required by the collection initializer.</span></span> <span data-ttu-id="76cb0-106">Genel Koleksiyonlar için koleksiyon başlatıcıları kullandığınızda bu genellikle yapmanız gereken şeydir.</span><span class="sxs-lookup"><span data-stu-id="76cb0-106">This is typically what you need to do when you use collection initializers for generic collections.</span></span>  
  
## <a name="example"></a><span data-ttu-id="76cb0-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="76cb0-107">Example</span></span>  
 <span data-ttu-id="76cb0-108">Aşağıdaki örnek, <xref:System.Collections.Generic.List%601> bir koleksiyon başlatıcısının tür nesneleri eklemek için kullanılabilmesi için genel türe bir genişletme yönteminin nasıl ekleneceğini gösterir `Employee` .</span><span class="sxs-lookup"><span data-stu-id="76cb0-108">The following example shows how to add an extension method to the generic <xref:System.Collections.Generic.List%601> type so that a collection initializer can be used to add objects of type `Employee`.</span></span> <span data-ttu-id="76cb0-109">Genişletme yöntemi, kısaltılmış koleksiyon başlatıcısı sözdizimini kullanmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="76cb0-109">The extension method enables you to use the shortened collection initializer syntax.</span></span>  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo1/VB/Module1.vb#1)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo1/VB/Module1.vb#2)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo1/VB/Module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="76cb0-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="76cb0-110">See also</span></span>

- [<span data-ttu-id="76cb0-111">Koleksiyon Başlatıcıları</span><span class="sxs-lookup"><span data-stu-id="76cb0-111">Collection Initializers</span></span>](index.md)
- [<span data-ttu-id="76cb0-112">Nasıl yapılır: Öğe Başlatıcısı Tarafından Kullanılan Bir Koleksiyon Oluşturma</span><span class="sxs-lookup"><span data-stu-id="76cb0-112">How to: Create a Collection Used by a Collection Initializer</span></span>](how-to-create-a-collection-used-by-a-collection-initializer.md)
