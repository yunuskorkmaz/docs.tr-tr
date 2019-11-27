---
title: 'Nasıl yapılır: Koleksiyon Başlatıcısı Tarafından Kullanılan Bir Uzantı Ekleme Yöntemi Oluşturma'
ms.date: 07/20/2015
helpviewer_keywords:
- collection initializers [Visual Basic]
ms.assetid: f64b52c7-8b11-4410-93a6-cb3aeebcc772
ms.openlocfilehash: 6d5f9d38b413b79f111a14ec3829c57a9797ce54
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346720"
---
# <a name="how-to-create-an-add-extension-method-used-by-a-collection-initializer-visual-basic"></a>Nasıl yapılır: Koleksiyon Başlatıcısı Tarafından Kullanılan Bir Uzantı Ekleme Yöntemi Oluşturma (Visual Basic)
Koleksiyon oluşturmak için bir koleksiyon başlatıcısı kullandığınızda Visual Basic derleyici, koleksiyon başlatıcısındaki değerlerin türleriyle eşleşen `Add` yöntemi için parametrelerin `Add` yöntemini arar. Bu `Add` yöntemi, koleksiyonu koleksiyon başlatıcısındaki değerlerle doldurmak için kullanılır.  
  
 Eşleşen bir `Add` yöntemi yoksa ve koleksiyon için kodu değiştiremeyeceğiniz takdirde, koleksiyon başlatıcısı tarafından gereken parametreleri alan `Add` adlı bir uzantı yöntemi ekleyebilirsiniz. Genel Koleksiyonlar için koleksiyon başlatıcıları kullandığınızda bu genellikle yapmanız gereken şeydir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir koleksiyon başlatıcısının `Employee`türündeki nesneleri eklemek için kullanılabilmesi için genel <xref:System.Collections.Generic.List%601> türüne bir genişletme yönteminin nasıl ekleneceğini gösterir. Genişletme yöntemi, kısaltılmış koleksiyon başlatıcısı sözdizimini kullanmanıza olanak sağlar.  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo1/VB/Module1.vb#1)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo1/VB/Module1.vb#2)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo1/VB/Module1.vb#3)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Öğe Başlatıcıları](../../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)
- [Nasıl yapılır: Öğe Başlatıcısı Tarafından Kullanılan Bir Koleksiyon Oluşturma](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-a-collection-used-by-a-collection-initializer.md)
