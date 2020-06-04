---
title: 'Nasıl yapılır: Nesne Başlatıcı Kullanarak Nesne Bildirme'
ms.date: 07/20/2015
helpviewer_keywords:
- declaring objects using object initializer
- object initializers [Visual Basic]
- initializers [Visual Basic]
- Video How tos, Visual Basic
ms.assetid: 0f53a553-efd6-466d-80bf-6b679e5cd174
ms.openlocfilehash: cf4954059a4b0bf015bed82a74357ecfd5f5987e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404881"
---
# <a name="how-to-declare-an-object-by-using-an-object-initializer-visual-basic"></a>Nasıl yapılır: Nesne Başlatıcı Kullanarak Bir Nesne Bildirme (Visual Basic)
Nesne başlatıcıları, tek bir ifadede bir sınıfın örneğini bildirmenize ve örneklendirimenizi sağlar. Ayrıca, parametreli bir Oluşturucu çağırmadan, örneğin bir veya daha fazla üyesini aynı zamanda başlatabilirsiniz.  
  
 Adlandırılmış bir türün örneğini oluşturmak için bir nesne Başlatıcısı kullandığınızda, sınıfının parametresiz oluşturucusu çağrılır, ardından belirttiğiniz sırada belirtilen üyelerin başlatılması gelir.  
  
 Aşağıdaki yordamda üç farklı şekilde bir sınıf örneğinin nasıl oluşturulacağı gösterilmektedir `Student` . Sınıfın adı, soyadı ve sınıf yılı özellikleri diğerleri arasında bulunur. Üç bildirime her biri `Student` , özelliği `First` "Michael", özelliği `Last` "Tucker" olarak ayarlanmış ve diğer tüm Üyeler varsayılan değerlerine ayarlanmış olan yeni bir örneğini oluşturur. Yordamdaki her bir bildirimin sonucu, nesne Başlatıcısı kullanmayan aşağıdaki örneğe eşdeğerdir.  
  
 [!code-vb[VbVbalrObjectInit#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class2.vb#20)]  
  
 Sınıfının uygulanması için `Student` bkz. [nasıl yapılır: öğe listesi oluşturma](../../concepts/linq/how-to-create-a-list-of-items.md). Sınıfı ayarlamak ve birlikte çalışmak üzere bir nesne listesi oluşturmak için bu konudaki kodu kopyalayabilirsiniz `Student` .  
  
### <a name="to-create-an-object-of-a-named-class-by-using-an-object-initializer"></a>Bir nesne Başlatıcısı kullanarak adlandırılmış bir sınıfın nesnesini oluşturmak için  
  
1. Oluşturucuyu kullanmayı planladıysanız bildirimi başlatın.  
  
     `Dim student1 As New Student`  
  
2. Anahtar sözcüğünü ve `With` ardından Küme ayraçları içinde bir başlatma listesini yazın.  
  
     `Dim student1 As New Student With { <initialization list> }`  
  
3. Başlatma listesinde, başlatmak istediğiniz her bir özelliği ekleyin ve buna bir başlangıç değeri atayın. Özelliğin adı önünde bir nokta gelir.  
  
     [!code-vb[VbVbalrObjectInit#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class2.vb#21)]  
  
     Sınıfının bir veya daha fazla üyesini başlatabilirsiniz.  
  
4. Alternatif olarak, sınıfının yeni bir örneğini bildirebilir ve sonra bir değer atayabilirsiniz. İlk olarak, bir örneği bildirin `Student` :  
  
     `Dim student2 As Student`  
  
5. Bir örneğinin oluşturulmasını `Student` normal şekilde başlatın.  
  
     `Dim student2 As Student = New Student`  
  
6. `With`Yeni örneğin bir veya daha fazla üyesini başlatmak için bir nesne Başlatıcısı yazın.  
  
     [!code-vb[VbVbalrObjectInit#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class2.vb#22)]  
  
7. Önceki adımda, öğesini atlayarak tanımlamayı kolaylaştırabilirsiniz `As Student` . Bunu yaparsanız, derleyici `student3` `Student` Yerel tür çıkarımı kullanarak bir örneği olduğunu belirler.  
  
     [!code-vb[VbVbalrObjectInit#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class2.vb#23)]  
  
     Daha fazla bilgi için bkz. [Yerel tür çıkarımı](../variables/local-type-inference.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yerel Tür Arabirimi](../variables/local-type-inference.md)
- [Nasıl yapılır: Öğe Listesi Oluşturma](../../concepts/linq/how-to-create-a-list-of-items.md)
- [Nesne Başlatıcıları: Adlandırılmış ve Anonim Türler](object-initializers-named-and-anonymous-types.md)
- [Anonim Türler](anonymous-types.md)
