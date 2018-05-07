---
title: 'Nasıl yapılır: Bağımsız Değişkeni Değere Göre Geçirilecek Şekilde Zorlama (Visual Basic)'
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
ms.openlocfilehash: adc58c34150030eb0fc82050576bfecc453e21ed
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-force-an-argument-to-be-passed-by-value-visual-basic"></a>Nasıl yapılır: Bağımsız Değişkeni Değere Göre Geçirilecek Şekilde Zorlama (Visual Basic)
Yordam bildirimi geçirme mekanizması belirler. Bir parametre bildirilirse [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), Visual Basic başvuru ile ilgili bağımsız değişken geçirmek bekliyor. Bu, çağrıyı yapan kod değişkeninde temel programlama öğenin değerini değiştirmek için yordamı sağlar. Temel alınan öğe bu tür değişiklik karşı korumak isterseniz, geçersiz kılabilirsiniz `ByRef` geçirme mekanizması yordamda çağrı parantez içinde bağımsız değişken adı kapsayan tarafından. Bağımsız değişken listesi çağrısında kapsayan parantez yanı sıra bu parantezler var.  
  
 Çağrıyı yapan kod geçersiz kılınamaz bir [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) mekanizması.  
  
### <a name="to-force-an-argument-to-be-passed-by-value"></a>Bağımsız değişkeni değere göre geçirilecek şekilde zorlama  
  
-   Karşılık gelen bir parametre bildirilirse `ByVal` yordamda herhangi bir ek adımlar gerekmez. Visual Basic zaten bağımsız değişkeni değere göre geçirilecek bekliyor.  
  
-   Karşılık gelen bir parametre bildirilirse `ByRef` bağımsız değişkeni parantez içinde yordam çağrısı yordamda alın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte geçersiz kılan bir `ByRef` parametre bildirimi. Zorlar çağrısında `ByVal`, parantez iki düzeyde unutmayın.  
  
 [!code-vb[VbVbcnProcedures#39](./codesnippet/VisualBasic/how-to-force-an-argument-to-be-passed-by-value_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#40](./codesnippet/VisualBasic/how-to-force-an-argument-to-be-passed-by-value_2.vb)]  
  
 Zaman `str` bağımsız değişken listesi içinde ek parantez içine `setNewString` yordamı çağıran kodu değerini değiştiremez ve `MsgBox` "değiştirilemez, ByVal aktarılırsa" görüntüler. Zaman `str` içine alınmayan fazladan parantez içinde yordamı, değiştirebilir ve `MsgBox` "Bu inString bağımsız değişken için yeni bir değer" görüntülüyor.  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Başvuruya göre bir değişken geçirdiğinizde kullanmalısınız `ByRef` anahtar Bu mekanizma belirtin.  
  
 Visual Basic'de bağımsız değişkenleri değere göre geçirilecek varsayılandır. Ancak, ya da dahil etmek için uygulama programlama iyi [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) veya [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) bildirilen her parametre olan anahtar sözcük. Bu, kodunuzu okumak kolaylaştırır.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Bir yordam bir parametre bildirirse [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), doğru kodunun yürütülmesini çağıran kodu temel alınan öğe değiştirme yetkisi olan bağlı olabilir. Çağrıyı yapan kod parantez içinde bağımsız değişken kapsayan tarafından bu arama mekanizması kılıyorsa veya değiştirilemez bağımsız değişkeni geçerse yordamı temel öğesi değiştiremezsiniz. Bu, çağrıyı yapan kod beklenmeyen sonuçlara yol açabilir.  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Yoktur her zaman potansiyel bir risk çağıran kodu bir bağımsız değişken alttaki değerini değiştirmek bir yordam sağlar. Bu değeri değiştirilmesi ve kullanmadan önce geçerliliğini denetlemek için hazırlanması beklediğiniz emin olun.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yordamlar](./index.md)  
 [Yordam Parametreleri ve Bağımsız Değişkenleri](./procedure-parameters-and-arguments.md)  
 [Nasıl yapılır: Bir Yordama Bağımsız Değişkenler Geçirme](./how-to-pass-arguments-to-a-procedure.md)  
 [Bağımsız Değişkenleri Değere ve Başvuruya Göre Geçirme](./passing-arguments-by-value-and-by-reference.md)  
 [Değiştirilebilir ve Değiştirilemez Bağımsız Değişkenler Arasındaki Farklar](./differences-between-modifiable-and-nonmodifiable-arguments.md)  
 [Değere ve Başvuruya Göre Bağımsız Değişken Geçirme Arasındaki Farklar](./differences-between-passing-an-argument-by-value-and-by-reference.md)  
 [Nasıl yapılır: Bir Yordam Bağımsız Değişkeninin Değerini Değiştirme](./how-to-change-the-value-of-a-procedure-argument.md)  
 [Nasıl yapılır: Bir Yordam Bağımsız Değişkenini Değer Değişikliklerine Karşı Koruma](./how-to-protect-a-procedure-argument-against-value-changes.md)  
 [Bağımsız Değişkenleri Konuma ve Ada Göre Geçirme](./passing-arguments-by-position-and-by-name.md)  
 [Değer Türleri ve Başvuru Türleri](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
