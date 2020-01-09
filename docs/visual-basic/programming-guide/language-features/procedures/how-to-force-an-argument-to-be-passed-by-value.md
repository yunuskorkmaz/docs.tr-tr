---
title: 'Nasıl yapılır: Bağımsız Değişkeni Değere Göre Geçirilecek Şekilde Zorlama'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedures [Visual Basic], parameters
- procedure arguments
- Visual Basic code, procedures
- arguments [Visual Basic], ByVal
- arguments [Visual Basic], passing by value
- procedure parameters
- procedures [Visual Basic], calling
- arguments [Visual Basic], in parentheses
- procedure arguments [Visual Basic], in parentheses
- arguments [Visual Basic], changing value
ms.assetid: 77b4f2d2-1055-4c2f-a521-874d1db86946
ms.openlocfilehash: 047738a2cbadc6b7d72f41aade22bbeff16d1bac
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347608"
---
# <a name="how-to-force-an-argument-to-be-passed-by-value-visual-basic"></a>Nasıl yapılır: Bağımsız Değişkeni Değere Göre Geçirilecek Şekilde Zorlama (Visual Basic)
Yordam bildirimi, geçen mekanizmayı belirler. Bir parametre [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)olarak bildirilirse, Visual Basic karşılık gelen bağımsız değişkeni başvuruya göre geçmesini bekler. Bu yordam, çağıran koddaki bağımsız değişkenin temelindeki programlama öğesinin değerini değiştirmesine olanak sağlar. Temel öğeyi bu değişikliğe karşı korumak istiyorsanız, bağımsız değişken adını parantez içine alarak yordam çağrısındaki `ByRef` geçen mekanizmayı geçersiz kılabilirsiniz. Bu parantezler, çağrısındaki bağımsız değişken listesini çevreleyen parantezler için de ek olarak kullanılır.  
  
 Çağıran kod bir [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) mekanizmasını geçersiz kılamaz.  
  
### <a name="to-force-an-argument-to-be-passed-by-value"></a>Bir bağımsız değişkenin değere göre geçirilmesini zorlamak için  
  
- Yordamda karşılık gelen parametre `ByVal` bildirilirse, ek adımlar uygulamanız gerekmez. Visual Basic, zaten bağımsız değişkeni değere göre geçmesini bekliyor.  
  
- Yordamda karşılık gelen parametre `ByRef` bildirilirse, yordam çağrısında bağımsız değişkeni parantez içine alın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek bir `ByRef` parametresi bildirimini geçersiz kılar. `ByVal`zorlayan çağrıda, iki parantez düzeyini unutmayın.  
  
 [!code-vb[VbVbcnProcedures#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#39)]  
  
 [!code-vb[VbVbcnProcedures#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#40)]  
  
 `str`, bağımsız değişken listesi içinde fazladan parantez içine alınmışsa, `setNewString` yordamı çağıran koddaki değerini değiştiremez ve "bir ByVal geçirildiğinde değiştirilemez" `MsgBox` görüntülenir. `str` ek parantezler içine alınmadığından, yordamı değiştirebilir `MsgBox` ve "ınString bağımsız değişkeni için yeni bir değer" görüntülenir.  
  
## <a name="compile-the-code"></a>Kod derleme  
 Bir değişkeni başvuruya göre geçirdiğinizde, bu mekanizmayı belirtmek için `ByRef` anahtar sözcüğünü kullanmanız gerekir.  
  
 Visual Basic varsayılan değeri, bağımsız değişkenleri değere göre geçirmektir. Ancak, her bir belirtilen parametreye ilişkin [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) veya [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) anahtar sözcüğünü eklemek iyi bir programlama uygulamasıdır. Bu, kodunuzun okunmasını kolaylaştırır.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Bir yordam [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)parametresini bildiriyorsa, kodun doğru yürütülmesi, çağıran kodda temel alınan öğeyi değiştirebilmeyle ilgili olarak değişebilir. Çağıran kod, bağımsız değişkeni parantez içine alarak bu çağıran mekanizmayı geçersiz kılıyorsa veya değiştirilemeyen bir bağımsız değişken geçirirse yordam, temel alınan öğeyi değiştiremez. Bu, çağıran kodda beklenmeyen sonuçlara neden olabilirler.  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Bir yordamın, çağıran koddaki bağımsız değişkenin temelindeki değeri değiştirmesine izin vermek için her zaman potansiyel bir risk vardır. Bu değerin değiştirilmesini beklediğinizden ve kullanılmadan önce geçerliliği göz önünde denetlediğinizden emin olun.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yordamlar](./index.md)
- [Yordam Parametreleri ve Bağımsız Değişkenleri](./procedure-parameters-and-arguments.md)
- [Nasıl yapılır: Bir Yordama Bağımsız Değişkenler Geçirme](./how-to-pass-arguments-to-a-procedure.md)
- [Bağımsız Değişkenleri Değere ve Başvuruya Göre Geçirme](./passing-arguments-by-value-and-by-reference.md)
- [Değiştirilebilir ve Değiştirilemez Bağımsız Değişkenler Arasındaki Farklar](./differences-between-modifiable-and-nonmodifiable-arguments.md)
- [Değere ve Başvuruya Göre Bağımsız Değişken Geçirme Arasındaki Farklar](./differences-between-passing-an-argument-by-value-and-by-reference.md)
- [Nasıl yapılır: Bir Yordam Bağımsız Değişkeninin Değerini Değiştirme](./how-to-change-the-value-of-a-procedure-argument.md)
- [Nasıl yapılır: Bir Yordam Bağımsız Değişkenini Değer Değişikliklerine Karşı Koruma](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [Bağımsız Değişkenleri Konuma ve Ada Göre Geçirme](./passing-arguments-by-position-and-by-name.md)
- [Değer Türleri ve Başvuru Türleri](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
