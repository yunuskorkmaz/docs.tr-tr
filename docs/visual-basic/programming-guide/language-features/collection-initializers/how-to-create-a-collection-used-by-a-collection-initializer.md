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
# <a name="how-to-create-a-collection-used-by-a-collection-initializer-visual-basic"></a>Nasıl yapılır: (Visual Basic) koleksiyon başlatıcısı tarafından kullanılan bir koleksiyon oluşturma
Bir koleksiyon oluşturmak için bir koleksiyon Başlatıcısı kullandığınızda, Visual Basic Derleyicisi arar bir `Add` koleksiyon türü yöntemi için parametreleri `Add` koleksiyon Başlatıcısı değerleri türlerini match yöntemi. Bu `Add` yöntemi koleksiyon Başlatıcısı değerlerle doldurmak için kullanılır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte gösterildiği bir `OrderCollection` içeren bir genel koleksiyon `Add` koleksiyon Başlatıcısı türden nesneleri eklemek için kullanabileceğiniz yöntem `Order`. `Add` Yöntemi kısaltılmış koleksiyon Başlatıcısı sözdizimi kullanmanıza olanak sağlar.  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#4](../../../../visual-basic/programming-guide/language-features/collection-initializers/codesnippet/VisualBasic/how-to-create-a-collection-used-by-a-collection-initializer_1.vb)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#1](../../../../visual-basic/programming-guide/language-features/collection-initializers/codesnippet/VisualBasic/how-to-create-a-collection-used-by-a-collection-initializer_2.vb)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#2](../../../../visual-basic/programming-guide/language-features/collection-initializers/codesnippet/VisualBasic/how-to-create-a-collection-used-by-a-collection-initializer_3.vb)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#3](../../../../visual-basic/programming-guide/language-features/collection-initializers/codesnippet/VisualBasic/how-to-create-a-collection-used-by-a-collection-initializer_4.vb)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Öğe Başlatıcıları](../../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)
- [Nasıl yapılır: Oluşturma bir koleksiyon başlatıcısı tarafından kullanılan uzantı ekleme metodu](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-an-add-extension-method-used-by-a-collection-initializer.md)
