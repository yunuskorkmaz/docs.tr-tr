---
title: 'Nasıl yapılır: Koleksiyon Başlatıcısı Tarafından Kullanılan Bir Koleksiyon Oluşturma'
ms.date: 07/20/2015
helpviewer_keywords:
- collection initializers [Visual Basic]
ms.assetid: c858db10-424d-47e0-92cd-e08087cc5ebc
ms.openlocfilehash: 5eaf9e828455bf2accda86ab52a1ce645f10b9ee
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349056"
---
# <a name="how-to-create-a-collection-used-by-a-collection-initializer-visual-basic"></a>Nasıl yapılır: Koleksiyon Başlatıcısı Tarafından Kullanılan Bir Koleksiyon Oluşturma (Visual Basic)
Koleksiyon oluşturmak için bir koleksiyon başlatıcısı kullandığınızda Visual Basic derleyici, koleksiyon başlatıcısındaki değerlerin türleriyle eşleşen `Add` yöntemi için parametrelerin `Add` yöntemini arar. Bu `Add` yöntemi, koleksiyonu koleksiyon başlatıcısındaki değerlerle doldurmak için kullanılır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir koleksiyon başlatıcısının `Order`türündeki nesneleri eklemek için kullanabileceği ortak bir `Add` yöntemi içeren bir `OrderCollection` koleksiyonunu gösterir. `Add` yöntemi, kısaltılmış koleksiyon başlatıcısı sözdizimini kullanmanıza olanak sağlar.  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#4)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#1)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#2)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#3)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Öğe Başlatıcıları](../../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)
- [Nasıl yapılır: Öğe Başlatıcısı Tarafından Kullanılan Bir Uzantı Ekleme Yöntemi Oluşturma](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-an-add-extension-method-used-by-a-collection-initializer.md)
