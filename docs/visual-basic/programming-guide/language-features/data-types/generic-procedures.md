---
title: Genel Yordamlar
ms.date: 07/20/2015
helpviewer_keywords:
- generic methods [Visual Basic], type inference
- generics [Visual Basic], type inference
- procedures [Visual Basic], generic
- generic procedures
- type inference, generics
- generic methods [Visual Basic]
- type inference
- generics [Visual Basic], procedures
- generic procedures [Visual Basic], type inference
ms.assetid: 95577b28-137f-4d5c-a149-919c828600e5
ms.openlocfilehash: 16a629e07cf711778b3d8d1863958ec7a6300649
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350080"
---
# <a name="generic-procedures-in-visual-basic"></a>Visual Basic'de Genel Yordamlar
*Genel yöntem*olarak da adlandırılan *genel yordam*, en az bir tür parametresiyle tanımlanmış bir yordamdır. Bu, çağıran kodun, yordamı her çağırdığında veri türlerini gereksinimlerine uyarlayabilmenizi sağlar.  
  
 Bir yordam, genel bir sınıf veya genel bir yapı içinde tanımlanmakta olan virtuale tarafından genel değildir. Genel olması için, yordamın, gerçekleştirebileceğiniz normal parametrelere ek olarak en az bir tür parametresi olması gerekir. Genel bir sınıf veya yapı genel olmayan yordamlar içerebilir ve genel olmayan bir sınıf, yapı veya modül genel yordamlar içerebilir.  
  
 Genel yordam, kendi tür parametrelerini normal parametre listesinde, bir tane varsa dönüş türünde ve yordam kodunda kullanabilir.  
  
## <a name="type-inference"></a>Tür Çıkarma  
 Herhangi bir tür bağımsız değişkeni sağlamadan, genel bir yordamı çağırabilirsiniz. Bu şekilde çağırırsanız, derleyici yordamın tür bağımsız değişkenlerine geçirilecek uygun veri türlerini saptamaya çalışır. Buna *tür çıkarımı*denir. Aşağıdaki kod, derleyicinin tür parametre `t`tür `String` geçmesi gerektiğini gösterdiği bir çağrıyı gösterir.  
  
 [!code-vb[VbVbalrDataTypes#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#15)]  
  
 Derleyici, tür bağımsız değişkenlerini çağrınızın bağlamından çıkarsanamıyor bir hata bildirir. Bu tür bir hatanın olası nedeni bir dizi sırası uyumsuzluğu. Örneğin, bir tür parametresinin dizisi olarak normal bir parametre tanımladığınızı varsayalım. Farklı bir derece (boyut sayısı) dizisi sağlayan genel yordamı çağırırsanız, uyuşmazlık tür çıkarımını başarısız olmasına neden olur. Aşağıdaki kod, tek boyutlu bir dizi bekleyen bir yordama iki boyutlu bir dizinin geçirildiği bir çağrıyı gösterir.  
  
```vb  
Public Sub demoSub(Of t)(ByVal arg() As t)
End Sub

Public Sub callDemoSub()
    Dim twoDimensions(,) As Integer
    demoSub(twoDimensions)
End Sub
```
  
 Tür çıkarımı yalnızca tüm tür bağımsız değişkenlerini atlayarak çağırabilirsiniz. Bir tür bağımsız değişkeni sağlarsanız, bunları sağlamanız gerekir.  
  
 Tür çıkarımı yalnızca genel yordamlar için desteklenir. Genel sınıflarda, yapılarda, arabirimlerde veya Temsilcilerde tür çıkarımı çağıramazsınız.  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Açıklama  
 Aşağıdaki örnek, bir dizide belirli bir öğeyi bulmak için genel `Function` yordamını tanımlar. Bir tür parametresini tanımlar ve parametre listesinde iki parametreyi oluşturmak için onu kullanır.  
  
### <a name="code"></a>Kod  
 [!code-vb[VbVbalrDataTypes#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#14)]  
  
### <a name="comments"></a>Açıklamalar  
 Yukarıdaki örnek, `searchValue` `searchArray`her öğesine karşı karşılaştırma yeteneği gerektirir. Bu özelliği garantilemek için, <xref:System.IComparable%601> arabirimini uygulamak üzere `T` tür parametresini kısıtlar. Kod, `T` için sağlanan bir tür bağımsız değişkeninin `=` işlecini desteklediğinden emin olmadığı için `=` işleci yerine <xref:System.IComparable%601.CompareTo%2A> yöntemini kullanır.  
  
 `findElement` yordamı aşağıdaki kodla test edebilirsiniz.  
  
 [!code-vb[VbVbalrDataTypes#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#13)]  
  
 `MsgBox` önceki çağrılar sırasıyla "0", "1" ve "-1" görüntüler.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic genel türler](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [Nasıl yapılır: Farklı Veri Türlerinde Aynı İşlevselliği Sağlayabilen Bir Sınıf Tanımlama](../../../../visual-basic/programming-guide/language-features/data-types/how-to-define-a-class-that-can-provide-identical-functionality.md)
- [Nasıl yapılır: Genel Bir Sınıf Kullanma](../../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [Yordamlar](../../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [Yordam Parametreleri ve Bağımsız Değişkenleri](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)
- [Tür Listesi](../../../../visual-basic/language-reference/statements/type-list.md)
- [Parametre Listesi](../../../../visual-basic/language-reference/statements/parameter-list.md)
