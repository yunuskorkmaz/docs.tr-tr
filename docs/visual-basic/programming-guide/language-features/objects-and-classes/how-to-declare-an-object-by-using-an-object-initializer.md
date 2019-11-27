---
title: 'Nasıl yapılır: Nesne Başlatıcı Kullanarak Nesne Bildirme'
ms.date: 07/20/2015
helpviewer_keywords:
- declaring objects using object initializer
- object initializers [Visual Basic]
- initializers [Visual Basic]
- Video How tos, Visual Basic
ms.assetid: 0f53a553-efd6-466d-80bf-6b679e5cd174
ms.openlocfilehash: ae04d338b61027c3917ad3a7f62ff40f0a95e53e
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347131"
---
# <a name="how-to-declare-an-object-by-using-an-object-initializer-visual-basic"></a>Nasıl yapılır: Nesne Başlatıcı Kullanarak Bir Nesne Bildirme (Visual Basic)
Nesne başlatıcıları, tek bir ifadede bir sınıfın örneğini bildirmenize ve örneklendirimenizi sağlar. Ayrıca, parametreli bir Oluşturucu çağırmadan, örneğin bir veya daha fazla üyesini aynı zamanda başlatabilirsiniz.  
  
 Adlandırılmış bir türün örneğini oluşturmak için bir nesne Başlatıcısı kullandığınızda, sınıfının parametresiz oluşturucusu çağrılır, ardından belirttiğiniz sırada belirtilen üyelerin başlatılması gelir.  
  
 Aşağıdaki yordamda üç farklı yolla `Student` sınıfının bir örneğinin nasıl oluşturulacağı gösterilmektedir. Sınıfın adı, soyadı ve sınıf yılı özellikleri diğerleri arasında bulunur. Üç bildirime her biri, özellik `First` "Michael" olarak ayarlanmış `Student`yeni bir örneğini oluşturur, özellik `Last` "Tucker" olarak ayarlanır ve diğer tüm Üyeler varsayılan değerlerine ayarlanır. Yordamdaki her bir bildirimin sonucu, nesne Başlatıcısı kullanmayan aşağıdaki örneğe eşdeğerdir.  
  
 [!code-vb[VbVbalrObjectInit#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class2.vb#20)]  
  
 `Student` sınıfının uygulanması için bkz. [nasıl yapılır: öğe listesi oluşturma](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md). Sınıfı ayarlamak ve birlikte çalışmak üzere `Student` nesnelerinin bir listesini oluşturmak için bu konudaki kodu kopyalayabilirsiniz.  
  
### <a name="to-create-an-object-of-a-named-class-by-using-an-object-initializer"></a>Bir nesne Başlatıcısı kullanarak adlandırılmış bir sınıfın nesnesini oluşturmak için  
  
1. Oluşturucuyu kullanmayı planladıysanız bildirimi başlatın.  
  
     `Dim student1 As New Student`  
  
2. Anahtar ayracın ardından bir başlatma listesi olan `With`anahtar sözcüğünü yazın.  
  
     `Dim student1 As New Student With { <initialization list> }`  
  
3. Başlatma listesinde, başlatmak istediğiniz her bir özelliği ekleyin ve buna bir başlangıç değeri atayın. Özelliğin adı önünde bir nokta gelir.  
  
     [!code-vb[VbVbalrObjectInit#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class2.vb#21)]  
  
     Sınıfının bir veya daha fazla üyesini başlatabilirsiniz.  
  
4. Alternatif olarak, sınıfının yeni bir örneğini bildirebilir ve sonra bir değer atayabilirsiniz. İlk olarak, bir `Student`örneği bildirin:  
  
     `Dim student2 As Student`  
  
5. Bir `Student` örneğinin oluşturulmasını normal şekilde başlatın.  
  
     `Dim student2 As Student = New Student`  
  
6. Yeni örneğin bir veya daha fazla üyesini başlatmak için `With` ve ardından bir nesne Başlatıcısı yazın.  
  
     [!code-vb[VbVbalrObjectInit#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class2.vb#22)]  
  
7. Önceki adımda `As Student`atlayarak tanımlamayı kolaylaştırabilirsiniz. Bunu yaparsanız, derleyici `student3` yerel tür çıkarımı kullanılarak `Student` bir örneği olduğunu belirler.  
  
     [!code-vb[VbVbalrObjectInit#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class2.vb#23)]  
  
     Daha fazla bilgi için bkz. [Yerel tür çıkarımı](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yerel Çıkarım](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Nasıl yapılır: Öğe Listesi Oluşturma](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)
- [Nesne Başlatıcıları: Adlandırılmış ve Anonim Tipler](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [Anonim Tipler](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
