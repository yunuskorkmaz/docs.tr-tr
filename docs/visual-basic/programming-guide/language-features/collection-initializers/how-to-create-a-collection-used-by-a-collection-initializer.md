---
title: 'Nasıl yapılır: (Visual Basic) koleksiyon başlatıcısı tarafından kullanılan bir koleksiyon oluşturma'
ms.date: 07/20/2015
helpviewer_keywords:
- collection initializers [Visual Basic]
ms.assetid: c858db10-424d-47e0-92cd-e08087cc5ebc
ms.openlocfilehash: d0007ebf5f18dee5bd8448a071fe1f0f984aff1a
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56967457"
---
# <a name="how-to-create-a-collection-used-by-a-collection-initializer-visual-basic"></a>Nasıl yapılır: (Visual Basic) koleksiyon başlatıcısı tarafından kullanılan bir koleksiyon oluşturma
Bir koleksiyon oluşturmak için bir koleksiyon Başlatıcısı kullandığınızda, Visual Basic Derleyicisi arar bir `Add` koleksiyon türü yöntemi için parametreleri `Add` koleksiyon Başlatıcısı değerleri türlerini match yöntemi. Bu `Add` yöntemi koleksiyon Başlatıcısı değerlerle doldurmak için kullanılır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte gösterildiği bir `OrderCollection` içeren bir genel koleksiyon `Add` koleksiyon Başlatıcısı türden nesneleri eklemek için kullanabileceğiniz yöntem `Order`. `Add` Yöntemi kısaltılmış koleksiyon Başlatıcısı sözdizimi kullanmanıza olanak sağlar.  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#4)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#1)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#2)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#3)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Öğe Başlatıcıları](../../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)
- [Nasıl yapılır: Oluşturma bir koleksiyon başlatıcısı tarafından kullanılan uzantı ekleme metodu](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-an-add-extension-method-used-by-a-collection-initializer.md)
