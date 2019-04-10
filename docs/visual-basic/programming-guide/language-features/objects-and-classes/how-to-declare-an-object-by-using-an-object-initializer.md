---
title: 'Nasıl yapılır: (Visual Basic) nesne Başlatıcı kullanarak nesne bildirme'
ms.date: 07/20/2015
helpviewer_keywords:
- declaring objects using object initializer
- object initializers [Visual Basic]
- initializers [Visual Basic]
- Video How tos, Visual Basic
ms.assetid: 0f53a553-efd6-466d-80bf-6b679e5cd174
ms.openlocfilehash: 775c40cbb62272f913297d5a58914a0c82c5a7d7
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59305318"
---
# <a name="how-to-declare-an-object-by-using-an-object-initializer-visual-basic"></a>Nasıl yapılır: (Visual Basic) nesne Başlatıcı kullanarak nesne bildirme
Nesne başlatıcıları bildirme ve tek bir deyimde bir sınıfın bir örneğini sağlar. Ayrıca, parametreli bir kurucu çağırmadan aynı anda bir veya daha fazla üye örneğinin başlatabilirsiniz.  
  
 Adlandırılmış bir türün bir örneğini oluşturmak için bir nesne Başlatıcısı kullandığınızda, belirttiğiniz sırada belirtilen üyeleri başlatma sonrasında sınıfı için varsayılan oluşturucu çağrılır.  
  
 Aşağıdaki yordam bir örneğini oluşturmak nasıl gösterir bir `Student` üç farklı yolla sınıfı. Sınıfı, ad, Soyadı ve diğerlerinin yanı sıra sınıf yıl özelliklerine sahiptir. Her üç bildirimlerinin yeni bir örneğini oluşturur `Student`, özelliğiyle `First` "Michael için", özellik kümesi `Last` "Tucker için" ve diğer tüm üyeleri varsayılan değerlerine ayarlayın. Yordamdaki her bildirimin sonucu nesne Başlatıcı kullanmaz aşağıdaki örneğe eşdeğerdir.  
  
 [!code-vb[VbVbalrObjectInit#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class2.vb#20)]  
  
 Bir uygulama için `Student` sınıfı [nasıl yapılır: Öğe listesi oluşturma](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md). Sınıfı oluşturan ve listesini oluşturmak için bu konudan kod kopyalayabilirsiniz `Student` çalışmak için nesneleri.  
  
### <a name="to-create-an-object-of-a-named-class-by-using-an-object-initializer"></a>Bir nesne Başlatıcı kullanarak adlandırılmış bir sınıfın bir nesnesi oluşturmak için  
  
1. Bir oluşturucu kullanmayı planladığınız gibi bildirimi başlar.  
  
     `Dim student1 As New Student`  
  
2. Anahtar sözcüğü yazın `With`, küme ayraçları içinde bir başlatma listesi tarafından izlenen.  
  
     `Dim student1 As New Student With { <initialization list> }`  
  
3. Başlatma listesinde başlatın ve bir başlangıç değeri için atamak istediğiniz her bir özellik içerir. Özelliğin adı öncesinde bir nokta.  
  
     [!code-vb[VbVbalrObjectInit#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class2.vb#21)]  
  
     Bir veya daha fazla sınıf üyelerini başlatabilirsiniz.  
  
4. Alternatif olarak, yeni bir sınıf örneği bildirebilir ve bir değer atayın. İlk olarak, bir örneğini bildirmeniz `Student`:  
  
     `Dim student2 As Student`  
  
5. Bir örneğinin oluşturulmasını başlatmak `Student` normal şekilde.  
  
     `Dim student2 As Student = New Student`  
  
6. Tür `With` ve ardından bir veya daha fazla üyesi yeni örneği başlatmak için nesne Başlatıcı.  
  
     [!code-vb[VbVbalrObjectInit#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class2.vb#22)]  
  
7. Tanım önceki adımda gt;(yok) basitleştirebilirsiniz `As Student`. Bunu yaparsanız, derleyici belirleyen `student3` örneğidir `Student` yerel tür çıkarımı kullanarak.  
  
     [!code-vb[VbVbalrObjectInit#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class2.vb#23)]  
  
     Daha fazla bilgi için [yerel tür çıkarımı](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yerel Tür Arabirimi](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Nasıl yapılır: Öğe Listesi Oluşturma](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)
- [Nesne Başlatıcıları: Adlandırılmış ve Anonim Türler](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [Anonim Türler](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
