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
ms.openlocfilehash: 48f7d7afebd76916cba11459532d89d71871c79b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84387991"
---
# <a name="how-to-force-an-argument-to-be-passed-by-value-visual-basic"></a>Nasıl yapılır: Bağımsız Değişkeni Değere Göre Geçirilecek Şekilde Zorlama (Visual Basic)
Yordam bildirimi, geçen mekanizmayı belirler. Bir parametre [ByRef](../../../language-reference/modifiers/byref.md)olarak bildirilirse, Visual Basic karşılık gelen bağımsız değişkeni başvuruya göre geçmesini bekler. Bu yordam, çağıran koddaki bağımsız değişkenin temelindeki programlama öğesinin değerini değiştirmesine olanak sağlar. Temel alınan öğeyi bu değişikliğe karşı korumak istiyorsanız `ByRef` bağımsız değişken adını parantez içine alarak yordam çağrısındaki geçen mekanizmayı geçersiz kılabilirsiniz. Bu parantezler, çağrısındaki bağımsız değişken listesini çevreleyen parantezler için de ek olarak kullanılır.  
  
 Çağıran kod bir [ByVal](../../../language-reference/modifiers/byval.md) mekanizmasını geçersiz kılamaz.  
  
### <a name="to-force-an-argument-to-be-passed-by-value"></a>Bir bağımsız değişkenin değere göre geçirilmesini zorlamak için  
  
- Yordamda karşılık gelen parametre bildirilirse `ByVal` , ek adımlar uygulamanız gerekmez. Visual Basic, zaten bağımsız değişkeni değere göre geçmesini bekliyor.  
  
- Yordamda karşılık gelen parametre bildirilirse `ByRef` , bağımsız değişkeni yordam çağrısında parantez içine alın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek bir `ByRef` parametre bildirimini geçersiz kılar. Zorlayan çağrıda `ByVal` , iki parantez düzeyini unutmayın.  
  
 [!code-vb[VbVbcnProcedures#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#39)]  
  
 [!code-vb[VbVbcnProcedures#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#40)]  
  
 `str`Bağımsız değişken listesi içinde fazladan parantezler içine geçirildiğinde `setNewString` yordam, çağıran koddaki değerini değiştiremez ve `MsgBox` "bir ByVal geçirildiğinde değiştirilemez" şeklinde görüntülenir. `str`Ek parantezler içine alınmayan yordam bunu değiştirebilir ve `MsgBox` "ınString bağımsız değişkeni için yeni bir değer" görüntüler.  
  
## <a name="compile-the-code"></a>Kodu derle  
 Bir değişkeni başvuruya göre geçirdiğinizde, `ByRef` Bu mekanizmayı belirtmek için anahtar sözcüğünü kullanmanız gerekir.  
  
 Visual Basic varsayılan değeri, bağımsız değişkenleri değere göre geçirmektir. Ancak, her bir belirtilen parametreye ilişkin [ByVal](../../../language-reference/modifiers/byval.md) veya [ByRef](../../../language-reference/modifiers/byref.md) anahtar sözcüğünü eklemek iyi bir programlama uygulamasıdır. Bu, kodunuzun okunmasını kolaylaştırır.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Bir yordam [ByRef](../../../language-reference/modifiers/byref.md)parametresini bildiriyorsa, kodun doğru yürütülmesi, çağıran kodda temel alınan öğeyi değiştirebilmeyle ilgili olarak değişebilir. Çağıran kod, bağımsız değişkeni parantez içine alarak bu çağıran mekanizmayı geçersiz kılıyorsa veya değiştirilemeyen bir bağımsız değişken geçirirse yordam, temel alınan öğeyi değiştiremez. Bu, çağıran kodda beklenmeyen sonuçlara neden olabilirler.  
  
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
- [Değer Türleri ve Başvuru Türleri](../data-types/value-types-and-reference-types.md)
