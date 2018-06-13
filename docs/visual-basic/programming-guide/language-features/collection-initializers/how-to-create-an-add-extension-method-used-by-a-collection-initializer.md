---
title: 'Nasıl yapılır: Koleksiyon Başlatıcısı Tarafından Kullanılan Bir Uzantı Ekleme Metodu Oluşturma (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- collection initializers [Visual Basic]
ms.assetid: f64b52c7-8b11-4410-93a6-cb3aeebcc772
ms.openlocfilehash: 5e35ad80037e843fd3cbd9caa68dcb2a09d707e1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33646246"
---
# <a name="how-to-create-an-add-extension-method-used-by-a-collection-initializer-visual-basic"></a><span data-ttu-id="005e9-102">Nasıl yapılır: Koleksiyon Başlatıcısı Tarafından Kullanılan Bir Uzantı Ekleme Metodu Oluşturma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="005e9-102">How to: Create an Add Extension Method Used by a Collection Initializer (Visual Basic)</span></span>
<span data-ttu-id="005e9-103">Bir koleksiyon oluşturmak için koleksiyon Başlatıcısı kullandığınızda, Visual Basic derleyici arar bir `Add` koleksiyon türü yöntemi için hangi parametrelerini `Add` yöntemi eşleşen koleksiyon Başlatıcısı değerlerde türleri.</span><span class="sxs-lookup"><span data-stu-id="005e9-103">When you use a collection initializer to create a collection, the Visual Basic compiler searches for an `Add` method of the collection type for which the parameters for the `Add` method match the types of the values in the collection initializer.</span></span> <span data-ttu-id="005e9-104">Bu `Add` yöntemi koleksiyonu koleksiyon Başlatıcısı gelen değerlerle doldurmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="005e9-104">This `Add` method is used to populate the collection with the values from the collection initializer.</span></span>  
  
 <span data-ttu-id="005e9-105">Eşleşme varsa `Add` yöntemi var ve koleksiyon için kod değiştirilemiyor, olarak adlandırılan bir genişletme yöntemi ekleyebilirsiniz `Add` koleksiyon başlatıcısı tarafından gerekli parametreleri alır.</span><span class="sxs-lookup"><span data-stu-id="005e9-105">If no matching `Add` method exists and you cannot modify the code for the collection, you can add an extension method called `Add` that takes the parameters that are required by the collection initializer.</span></span> <span data-ttu-id="005e9-106">Bu, genellikle genel koleksiyonlar için koleksiyon başlatıcıları kullandığınızda yapmanız gerekenler olur.</span><span class="sxs-lookup"><span data-stu-id="005e9-106">This is typically what you need to do when you use collection initializers for generic collections.</span></span>  
  
## <a name="example"></a><span data-ttu-id="005e9-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="005e9-107">Example</span></span>  
 <span data-ttu-id="005e9-108">Aşağıdaki örnek genel bir genişletme yöntemi ekleme gösterir <xref:System.Collections.Generic.List%601> koleksiyon Başlatıcısı türündeki nesneleri eklemek için kullanılan yazın `Employee`.</span><span class="sxs-lookup"><span data-stu-id="005e9-108">The following example shows how to add an extension method to the generic <xref:System.Collections.Generic.List%601> type so that a collection initializer can be used to add objects of type `Employee`.</span></span> <span data-ttu-id="005e9-109">Genişletme yöntemi, kısaltılmış koleksiyon Başlatıcısı sözdizimi kullanmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="005e9-109">The extension method enables you to use the shortened collection initializer syntax.</span></span>  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#1](../../../../visual-basic/programming-guide/language-features/collection-initializers/codesnippet/VisualBasic/how-to-create-an-add-extension-method-used-by-a-collection-initializer_1.vb)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#2](../../../../visual-basic/programming-guide/language-features/collection-initializers/codesnippet/VisualBasic/how-to-create-an-add-extension-method-used-by-a-collection-initializer_2.vb)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#3](../../../../visual-basic/programming-guide/language-features/collection-initializers/codesnippet/VisualBasic/how-to-create-an-add-extension-method-used-by-a-collection-initializer_3.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="005e9-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="005e9-110">See Also</span></span>  
 [<span data-ttu-id="005e9-111">Öğe Başlatıcıları</span><span class="sxs-lookup"><span data-stu-id="005e9-111">Collection Initializers</span></span>](../../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)  
 [<span data-ttu-id="005e9-112">Nasıl yapılır: Öğe Başlatıcısı Tarafından Kullanılan Bir Koleksiyon Oluşturma</span><span class="sxs-lookup"><span data-stu-id="005e9-112">How to: Create a Collection Used by a Collection Initializer</span></span>](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-a-collection-used-by-a-collection-initializer.md)
