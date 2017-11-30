---
title: "Nasıl yapılır: Koleksiyon Başlatıcısı Tarafından Kullanılan Bir Uzantı Ekleme Metodu Oluşturma (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords: collection initializers [Visual Basic]
ms.assetid: f64b52c7-8b11-4410-93a6-cb3aeebcc772
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d19ac8b03b992eb9b09b5cb45fdcceadad3a822a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-an-add-extension-method-used-by-a-collection-initializer-visual-basic"></a>Nasıl yapılır: Koleksiyon Başlatıcısı Tarafından Kullanılan Bir Uzantı Ekleme Metodu Oluşturma (Visual Basic)
Bir koleksiyon oluşturmak için koleksiyon Başlatıcısı kullandığınızda, Visual Basic derleyici arar bir `Add` koleksiyon türü yöntemi için hangi parametrelerini `Add` yöntemi eşleşen koleksiyon Başlatıcısı değerlerde türleri. Bu `Add` yöntemi koleksiyonu koleksiyon Başlatıcısı gelen değerlerle doldurmak için kullanılır.  
  
 Eşleşme varsa `Add` yöntemi var ve koleksiyon için kod değiştirilemiyor, olarak adlandırılan bir genişletme yöntemi ekleyebilirsiniz `Add` koleksiyon başlatıcısı tarafından gerekli parametreleri alır. Bu, genellikle genel koleksiyonlar için koleksiyon başlatıcıları kullandığınızda yapmanız gerekenler olur.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek genel bir genişletme yöntemi ekleme gösterir <xref:System.Collections.Generic.List%601> koleksiyon Başlatıcısı türündeki nesneleri eklemek için kullanılan yazın `Employee`. Genişletme yöntemi, kısaltılmış koleksiyon Başlatıcısı sözdizimi kullanmanıza olanak sağlar.  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#1](../../../../visual-basic/programming-guide/language-features/collection-initializers/codesnippet/VisualBasic/how-to-create-an-add-extension-method-used-by-a-collection-initializer_1.vb)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#2](../../../../visual-basic/programming-guide/language-features/collection-initializers/codesnippet/VisualBasic/how-to-create-an-add-extension-method-used-by-a-collection-initializer_2.vb)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#3](../../../../visual-basic/programming-guide/language-features/collection-initializers/codesnippet/VisualBasic/how-to-create-an-add-extension-method-used-by-a-collection-initializer_3.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Koleksiyon başlatıcıları](../../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)  
 [Nasıl yapılır: Koleksiyon başlatıcısı tarafından kullanılan bir koleksiyon oluşturma](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-a-collection-used-by-a-collection-initializer.md)
