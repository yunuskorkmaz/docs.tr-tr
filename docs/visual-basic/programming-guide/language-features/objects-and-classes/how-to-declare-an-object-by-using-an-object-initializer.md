---
title: "Nasıl yapılır: Nesne Başlatıcı Kullanarak Bir Nesne Bildirme (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- declaring objects using object initializer
- object initializers [Visual Basic]
- initializers [Visual Basic]
- Video How tos, Visual Basic
ms.assetid: 0f53a553-efd6-466d-80bf-6b679e5cd174
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 87c818765cbeac7a3080ee666d464052493e5bde
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-declare-an-object-by-using-an-object-initializer-visual-basic"></a>Nasıl yapılır: Nesne Başlatıcı Kullanarak Bir Nesne Bildirme (Visual Basic)
Nesne başlatıcıları bildirme ve tek bir deyimde sınıfının bir örneğini sağlar. Ayrıca, parametreli bir oluşturucu çağırmadan aynı anda bir veya daha fazla üye örneğinin başlatabilirsiniz.  
  
 Adlandırılmış bir türün bir örneği oluşturmak için nesne Başlatıcı kullandığınızda, belirttiğiniz sırayla belirlenen üyelerinin başlatma arkasından sınıfı için varsayılan oluşturucu çağrılır.  
  
 Aşağıdaki yordamda bir örneğini oluşturmak gösterilmiştir bir `Student` üç farklı yolla sınıfı. Sınıfı, ad, Soyadı ve diğerlerinin yanı sıra sınıfı yıl özellikleri vardır. Her üç bildirimlerinin yeni bir örneğini oluşturur `Student`, özelliğiyle `First` "Michael için", özellik kümesi `Last` "Tucker" ve diğer tüm üyeleri varsayılan değerlerine ayarlayın. Nesne Başlatıcı kullanmayan bir aşağıdaki örnek yordamı her bildirim sonucunu eşdeğerdir.  
  
 [!code-vb[VbVbalrObjectInit#20](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/how-to-declare-an-object-by-using-an-object-initializer_1.vb)]  
  
 Bir uygulama için `Student` sınıfı için bkz: [nasıl yapılır: öğelerinin listesi oluşturma](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md). Set sınıfı ve listesini oluşturmak için bu konudan kodu kopyalayabilirsiniz `Student` çalışmak için nesneleri.  
  
### <a name="to-create-an-object-of-a-named-class-by-using-an-object-initializer"></a>Nesne Başlatıcı kullanarak adlandırılmış bir sınıfın bir nesnesi oluşturmak için  
  
1.  Bir oluşturucu kullanmak planlı olarak bildirimi başlar.  
  
     `Dim student1 As New Student`  
  
2.  Anahtar sözcüğünü yazmanız `With`, küme ayraçları başlatma listesinde ardından.  
  
     `Dim student1 As New Student With { <initialization list> }`  
  
3.  Başlatma listesinde başlatmak ve ilk değer atamak için istediğiniz her bir özellik içerir. Özelliğin adını öncesinde nokta.  
  
     [!code-vb[VbVbalrObjectInit#21](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/how-to-declare-an-object-by-using-an-object-initializer_2.vb)]  
  
     Bir veya daha fazla üye sınıfının başlatabilirsiniz.  
  
4.  Alternatif olarak, sınıfının yeni bir örneğini bildirme ve bir değere atayın. Öncelikle, örneği bildirin `Student`:  
  
     `Dim student2 As Student`  
  
5.  Örneği oluşturmayı Başlat `Student` normal şekilde.  
  
     `Dim student2 As Student = New Student`  
  
6.  Tür `With` ve ardından yeni örnek bir veya daha fazla üyesi başlatmak için nesne Başlatıcı.  
  
     [!code-vb[VbVbalrObjectInit#22](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/how-to-declare-an-object-by-using-an-object-initializer_3.vb)]  
  
7.  Kaldırarak tanımı önceki adımda basitleştirebilir `As Student`. Bunu yaparsanız, belirleyen derleyici `student3` örneği `Student` yerel türü çıkarımı kullanarak.  
  
     [!code-vb[VbVbalrObjectInit#23](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/how-to-declare-an-object-by-using-an-object-initializer_4.vb)]  
  
     Daha fazla bilgi için bkz: [yerel türü çıkarımı](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yerel tür çıkarımı](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [Nasıl yapılır: öğe listesi oluşturma](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)  
 [Nesne başlatıcıları: Adlandırılmış ve anonim türler](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)  
 [Anonim türler](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
