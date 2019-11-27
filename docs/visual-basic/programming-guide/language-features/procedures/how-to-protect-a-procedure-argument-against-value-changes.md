---
title: 'Nasıl yapılır: Bir Yordam Bağımsız Değişkenini Değer Değişikliklerine Karşı Koruma'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedures [Visual Basic], parameters
- procedure arguments
- arguments [Visual Basic], passing by reference
- Visual Basic code, procedures
- arguments [Visual Basic], ByVal
- arguments [Visual Basic], passing by value
- procedure parameters
- procedures [Visual Basic], calling
- arguments [Visual Basic], ByRef
- arguments [Visual Basic], changing value
ms.assetid: d2b7c766-ce16-4d2c-8d79-3fc0e7ba2227
ms.openlocfilehash: 36092eb597b5b20e1da42cd9d15ab8633636cfb1
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344855"
---
# <a name="how-to-protect-a-procedure-argument-against-value-changes-visual-basic"></a>Nasıl yapılır: Bir Yordam Bağımsız Değişkenini Değer Değişikliklerine Karşı Koruma (Visual Basic)
Bir yordam bir parametreyi [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)olarak bildiriyorsa Visual Basic, yordam kodunu çağıran koddaki bağımsız değişkeni temel alan programlama öğesine doğrudan başvuru olarak verir. Bu yordam, çağıran koddaki bağımsız değişkenin temelindeki değeri değiştirmesine izin verir. Bazı durumlarda, çağıran kod bu tür bir değişikliğe karşı korumak isteyebilir.  
  
 Yordamda karşılık gelen parametre [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) ' i bildirerek, bir bağımsız değişkeni her zaman bir değişikliğe karşı koruyabilirsiniz. Belirli bir bağımsız değişkeni bazı durumlarda değiştirebilmek istiyorsanız, ancak diğerlerini değil, `ByRef` bildirebilir ve çağıran kodun her çağrıda geçen mekanizmayı belirlemesini sağlayabilirsiniz. Bunu değere göre iletmek için karşılık gelen bağımsız değişkeni parantez içine alarak veya başvuruya göre geçirmek için parantez içine almak için bunu yapar. Daha fazla bilgi için bkz. [nasıl yapılır: bağımsız değişkeni değere göre geçirilmesine zorlama](./how-to-force-an-argument-to-be-passed-by-value.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir dizi değişkeni alan ve öğelerinde çalışan iki yordamı gösterir. `increase` yordamı her bir öğeye yalnızca bir tane ekler. `replace` yordamı parametre `a()` yeni bir dizi atar ve sonra her öğeye bir tane ekler. Ancak, yeniden atama, çağıran koddaki temeldeki dizi değişkenini etkilemez.  
  
 [!code-vb[VbVbcnProcedures#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#35)]  
  
 [!code-vb[VbVbcnProcedures#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#38)]  
  
 [!code-vb[VbVbcnProcedures#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#37)]  
  
 İlk `MsgBox` çağrısı, "artdıktan sonra (n): 11, 21, 31, 41" olarak görüntülenir. Dizi `n` bir başvuru türü olduğundan, `increase`, geçirme mekanizması `ByVal`olmasına rağmen üyelerini değiştirebilir.  
  
 İkinci `MsgBox` çağrısı "yenisiyle değiştirildikten sonra (n): 11, 21, 31, 41" olarak görüntülenir. `n` `ByVal`geçirildiğinden `replace`, çağıran koddaki `n` değişkeni kendisine yeni bir dizi atayarak değiştiremez. `replace` yeni dizi örneği `k` oluşturduğunda ve yerel değişkene `a`atarken, çağıran kod tarafından geçirilen `n` başvurusunu kaybeder. `a`üyelerini değiştirdiğinde, yalnızca yerel dizi `k` etkilenir. Bu nedenle `replace`, çağıran koddaki dizi `n` değerlerini artırmaz.  
  
## <a name="compiling-the-code"></a>Kod Derleme  
 Visual Basic varsayılan değeri, bağımsız değişkenleri değere göre geçirmektir. Ancak, her bir belirtilen parametreye ilişkin [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) veya [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) anahtar sözcüğünü eklemek iyi bir programlama uygulamasıdır. Bu, kodunuzun okunmasını kolaylaştırır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yordamlar](./index.md)
- [Yordam Parametreleri ve Bağımsız Değişkenleri](./procedure-parameters-and-arguments.md)
- [Nasıl yapılır: Bir Yordama Bağımsız Değişkenler Geçirme](./how-to-pass-arguments-to-a-procedure.md)
- [Bağımsız Değişkenleri Değere ve Başvuruya Göre Geçirme](./passing-arguments-by-value-and-by-reference.md)
- [Değiştirilebilir ve Değiştirilemez Bağımsız Değişkenler Arasındaki Farklar](./differences-between-modifiable-and-nonmodifiable-arguments.md)
- [Değere ve Başvuruya Göre Bağımsız Değişken Geçirme Arasındaki Farklar](./differences-between-passing-an-argument-by-value-and-by-reference.md)
- [Nasıl yapılır: Bir Yordam Bağımsız Değişkeninin Değerini Değiştirme](./how-to-change-the-value-of-a-procedure-argument.md)
- [Nasıl yapılır: Bağımsız Değişkeni Değere Göre Geçirilecek Şekilde Zorlama](./how-to-force-an-argument-to-be-passed-by-value.md)
- [Bağımsız Değişkenleri Konuma ve Ada Göre Geçirme](./passing-arguments-by-position-and-by-name.md)
- [Değer Türleri ve Başvuru Türleri](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
