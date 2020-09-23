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
ms.openlocfilehash: 558601f038fccdcb9b94acb7c796e2b49fb6e6f4
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91059203"
---
# <a name="generic-procedures-in-visual-basic"></a>Visual Basic'de Genel Yordamlar

*Genel yöntem*olarak da adlandırılan *genel yordam*, en az bir tür parametresiyle tanımlanmış bir yordamdır. Bu, çağıran kodun, yordamı her çağırdığında veri türlerini gereksinimlerine uyarlayabilmenizi sağlar.  
  
 Bir yordam, genel bir sınıf veya genel bir yapı içinde tanımlanmakta olan virtuale tarafından genel değildir. Genel olması için, yordamın, gerçekleştirebileceğiniz normal parametrelere ek olarak en az bir tür parametresi olması gerekir. Genel bir sınıf veya yapı genel olmayan yordamlar içerebilir ve genel olmayan bir sınıf, yapı veya modül genel yordamlar içerebilir.  
  
 Genel yordam, kendi tür parametrelerini normal parametre listesinde, bir tane varsa dönüş türünde ve yordam kodunda kullanabilir.  
  
## <a name="type-inference"></a>Tür Çıkarma  

 Herhangi bir tür bağımsız değişkeni sağlamadan, genel bir yordamı çağırabilirsiniz. Bu şekilde çağırırsanız, derleyici yordamın tür bağımsız değişkenlerine geçirilecek uygun veri türlerini saptamaya çalışır. Buna *tür çıkarımı*denir. Aşağıdaki kod, derleyicinin türü tür parametresine geçmesi gereken bir çağrıyı gösterir `String` `t` .  
  
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
  
### <a name="description"></a>Description  

 Aşağıdaki örnek, `Function` bir dizide belirli bir öğeyi bulmak için genel bir yordam tanımlar. Bir tür parametresini tanımlar ve parametre listesinde iki parametreyi oluşturmak için onu kullanır.  
  
### <a name="code"></a>Kod  

 [!code-vb[VbVbalrDataTypes#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#14)]  
  
### <a name="comments"></a>Yorumlar  

 Yukarıdaki örnek, öğesinin `searchValue` her öğesine karşı karşılaştırma yeteneği gerektirir `searchArray` . Bu özelliği garantilemek için, `T` arabirimi uygulamak üzere tür parametresini kısıtlar <xref:System.IComparable%601> . Kodu, <xref:System.IComparable%601.CompareTo%2A> `=` için sağlanan bir tür bağımsız değişkeninin işleci desteklediği garantisi olmadığından, işleci yerine yöntemini kullanır `T` `=` .  
  
 `findElement`Yordamı aşağıdaki kodla test edebilirsiniz.  
  
 [!code-vb[VbVbalrDataTypes#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#13)]  
  
 Yukarıdaki `MsgBox` "0", "1" ve "-1" sırasıyla görüntülenecek çağrılar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic genel türler](generic-types.md)
- [Nasıl yapılır: Farklı Veri Türlerinde Aynı İşlevselliği Sağlayabilen Bir Sınıf Tanımlama](how-to-define-a-class-that-can-provide-identical-functionality.md)
- [Nasıl yapılır: Genel Bir Sınıf Kullanma](how-to-use-a-generic-class.md)
- [Yordamlar](../procedures/index.md)
- [Yordam Parametreleri ve Bağımsız Değişkenleri](../procedures/procedure-parameters-and-arguments.md)
- [Tür Listesi](../../../language-reference/statements/type-list.md)
- [Parametre Listesi](../../../language-reference/statements/parameter-list.md)
