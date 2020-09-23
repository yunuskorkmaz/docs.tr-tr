---
title: 'Nasıl yapılır: Koleksiyon Başlatıcısı Tarafından Kullanılan Bir Koleksiyon Oluşturma'
ms.date: 07/20/2015
helpviewer_keywords:
- collection initializers [Visual Basic]
ms.assetid: c858db10-424d-47e0-92cd-e08087cc5ebc
ms.openlocfilehash: b332ffb44ebc20ce8431e586fc380b8c6a29967d
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91086380"
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
