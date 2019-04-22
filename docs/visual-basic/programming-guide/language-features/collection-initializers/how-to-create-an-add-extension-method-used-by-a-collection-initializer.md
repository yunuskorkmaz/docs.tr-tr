---
title: 'Nasıl yapılır: Oluşturma bir genişletme yöntemi (Visual Basic) koleksiyon başlatıcısı tarafından kullanılan Ekle'
ms.date: 07/20/2015
helpviewer_keywords:
- collection initializers [Visual Basic]
ms.assetid: f64b52c7-8b11-4410-93a6-cb3aeebcc772
ms.openlocfilehash: a5af41e25b8f82aa173e2df28cc41b313c8d68dd
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58825410"
---
# <a name="how-to-create-an-add-extension-method-used-by-a-collection-initializer-visual-basic"></a>Nasıl yapılır: Oluşturma bir genişletme yöntemi (Visual Basic) koleksiyon başlatıcısı tarafından kullanılan Ekle
Bir koleksiyon oluşturmak için bir koleksiyon Başlatıcısı kullandığınızda, Visual Basic Derleyicisi arar bir `Add` koleksiyon türü yöntemi için parametreleri `Add` koleksiyon Başlatıcısı değerleri türlerini match yöntemi. Bu `Add` yöntemi koleksiyon Başlatıcısı değerlerle doldurmak için kullanılır.  
  
 Hiç eşleşen `Add` yöntemi var ve koleksiyon kodunu değiştiremediğiniz, adlı bir genişletme yöntemi ekleyebilirsiniz `Add` koleksiyon başlatıcısı tarafından gerekli olan parametreleri alır. Genel koleksiyonlar için koleksiyon başlatıcıları kullandığınızda yapmanız gerekenler genellikle budur.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir genişletme yöntemi için genel ekleme işlemi gösterilmektedir <xref:System.Collections.Generic.List%601> koleksiyon Başlatıcısı türden nesneleri eklemek için kullanılabilir olacak şekilde yazın `Employee`. Genişletme yöntemi, kısaltılmış koleksiyon Başlatıcısı sözdizimi kullanmanıza olanak sağlar.  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo1/VB/Module1.vb#1)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo1/VB/Module1.vb#2)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo1/VB/Module1.vb#3)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Öğe Başlatıcıları](../../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)
- [Nasıl yapılır: Koleksiyon başlatıcısı tarafından kullanılan bir koleksiyon oluşturma](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-a-collection-used-by-a-collection-initializer.md)
