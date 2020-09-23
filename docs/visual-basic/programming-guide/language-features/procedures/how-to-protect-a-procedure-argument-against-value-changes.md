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
ms.openlocfilehash: 84eadf3d364b69120221d80e464b1175b1602e13
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91071488"
---
# <a name="how-to-protect-a-procedure-argument-against-value-changes-visual-basic"></a>Nasıl yapılır: Bir Yordam Bağımsız Değişkenini Değer Değişikliklerine Karşı Koruma (Visual Basic)

Bir yordam bir parametreyi [ByRef](../../../language-reference/modifiers/byref.md)olarak bildiriyorsa Visual Basic, yordam kodunu çağıran koddaki bağımsız değişkeni temel alan programlama öğesine doğrudan başvuru olarak verir. Bu yordam, çağıran koddaki bağımsız değişkenin temelindeki değeri değiştirmesine izin verir. Bazı durumlarda, çağıran kod bu tür bir değişikliğe karşı korumak isteyebilir.  
  
 Yordamda karşılık gelen parametre [ByVal](../../../language-reference/modifiers/byval.md) ' i bildirerek, bir bağımsız değişkeni her zaman bir değişikliğe karşı koruyabilirsiniz. Belirli bir bağımsız değişkeni bazı durumlarda değiştirebilmek istiyorsanız, ancak başka bir deyişle, çağrı `ByRef` kodunun her çağrıda geçen mekanizmayı belirlemesini sağlayabilirsiniz. Bunu değere göre iletmek için karşılık gelen bağımsız değişkeni parantez içine alarak veya başvuruya göre geçirmek için parantez içine almak için bunu yapar. Daha fazla bilgi için bkz. [nasıl yapılır: bağımsız değişkeni değere göre geçirilmesine zorlama](./how-to-force-an-argument-to-be-passed-by-value.md).  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, bir dizi değişkeni alan ve öğelerinde çalışan iki yordamı gösterir. `increase`Yordam her bir öğeye yalnızca bir tane ekler. `replace`Yordam parametreye yeni bir dizi atar `a()` ve sonra her öğeye bir tane ekler. Ancak, yeniden atama, çağıran koddaki temeldeki dizi değişkenini etkilemez.  
  
 [!code-vb[VbVbcnProcedures#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#35)]  
  
 [!code-vb[VbVbcnProcedures#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#38)]  
  
 [!code-vb[VbVbcnProcedures#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#37)]  
  
 İlk `MsgBox` çağrı, "Artdıktan sonra (n): 11, 21, 31, 41" görüntüler. Dizi `n` bir başvuru türü olduğundan, `increase` geçirme mekanizması olsa bile üyelerini değiştirebilir `ByVal` .  
  
 İkinci `MsgBox` çağrı "yenisiyle değiştirildikten sonra (n): 11, 21, 31, 41" görüntüler. `n`Geçirildiğinden `ByVal` , `replace` `n` çağıran koddaki değişkeni kendisine yeni bir dizi atayarak değiştiremezsiniz. `replace`Yeni dizi örneğini oluşturur `k` ve yerel değişkene atarsa `a` , `n` çağıran kod tarafından geçirilen başvuruyu kaybeder. Üyelerini değiştirdiğinde `a` , yalnızca yerel dizi `k` etkilenir. Bu nedenle, `replace` çağıran koddaki dizi değerlerini artırmaz `n` .  
  
## <a name="compile-the-code"></a>Kodu derle  

 Visual Basic varsayılan değeri, bağımsız değişkenleri değere göre geçirmektir. Ancak, her bir belirtilen parametreye ilişkin [ByVal](../../../language-reference/modifiers/byval.md) veya [ByRef](../../../language-reference/modifiers/byref.md) anahtar sözcüğünü eklemek iyi bir programlama uygulamasıdır. Bu, kodunuzun okunmasını kolaylaştırır.  
  
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
- [Değer Türleri ve Başvuru Türleri](../data-types/value-types-and-reference-types.md)
