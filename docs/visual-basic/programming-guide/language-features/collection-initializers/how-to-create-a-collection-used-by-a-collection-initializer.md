---
title: 'Nasıl yapılır: Koleksiyon Başlatıcısı Tarafından Kullanılan Bir Koleksiyon Oluşturma'
ms.date: 07/20/2015
helpviewer_keywords:
- collection initializers [Visual Basic]
ms.assetid: c858db10-424d-47e0-92cd-e08087cc5ebc
ms.openlocfilehash: 7cba290b92f41125a93d1ed022e4db5ef62da789
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414562"
---
# <a name="how-to-create-a-collection-used-by-a-collection-initializer-visual-basic"></a>Nasıl yapılır: Koleksiyon Başlatıcısı Tarafından Kullanılan Bir Koleksiyon Oluşturma (Visual Basic)
Koleksiyon oluşturmak için bir koleksiyon başlatıcısı kullandığınızda, Visual Basic derleyici, `Add` yöntemi için parametrelerin `Add` koleksiyon başlatıcısındaki değerlerin türleriyle eşleştiği koleksiyon türünde bir yöntemi arar. Bu `Add` Yöntem, koleksiyonu koleksiyon başlatıcısındaki değerlerle doldurmak için kullanılır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, `OrderCollection` `Add` bir koleksiyon başlatıcısının türündeki nesneleri eklemek için kullanabileceği bir ortak yöntemi içeren bir koleksiyonu gösterir `Order` . `Add`Yöntemi, kısaltılmış koleksiyon başlatıcısı sözdizimini kullanmanıza olanak sağlar.  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#4)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#1)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#2)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#3)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Koleksiyon Başlatıcıları](index.md)
- [Nasıl yapılır: Öğe Başlatıcısı Tarafından Kullanılan Bir Uzantı Ekleme Yöntemi Oluşturma](how-to-create-an-add-extension-method-used-by-a-collection-initializer.md)
