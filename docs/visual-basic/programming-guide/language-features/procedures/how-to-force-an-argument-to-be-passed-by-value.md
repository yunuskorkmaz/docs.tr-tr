---
title: 'Nasıl yapılır: Bağımsız değişkeni (Visual Basic) değere göre geçirilecek şekilde zorlama'
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
ms.openlocfilehash: 9c4d6397d9a9ab1b95c4708c1e98741c01e9302e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54706647"
---
# <a name="how-to-force-an-argument-to-be-passed-by-value-visual-basic"></a>Nasıl yapılır: Bağımsız değişkeni (Visual Basic) değere göre geçirilecek şekilde zorlama
Yordam bildirimi geçirme mekanizması belirler. Bir parametre bildirilirse [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), Visual Basic bekliyor karşılık gelen bağımsız değişken başvuru ile geçirilecek. Bu yordam çağıran koddaki bağımsız değişken temel programlama öğenin değerini değiştirmek sağlar. Temel alınan öğe bu tür değişiklik karşı korumak istiyorsanız, geçersiz kılabilirsiniz `ByRef` geçirme mekanizmasında yordamı çağırma bağımsız değişken adı parantez içine alarak. Çağrısında bağımsız değişken listesini çevreleyen parantezler yanı sıra bu parantezler var.  
  
 Çağıran kod geçersiz kılamaz bir [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) mekanizması.  
  
### <a name="to-force-an-argument-to-be-passed-by-value"></a>Bağımsız değişkeni değere göre geçirilecek şekilde zorlama  
  
-   Karşılık gelen parametre bildirilirse `ByVal` yordamda herhangi bir ek adımlar gerekmez. Visual Basic bağımsız değişkeni değere göre geçirilecek zaten bekliyor.  
  
-   Karşılık gelen parametre bildirilirse `ByRef` parantez yordam çağrısı içinde bağımsız değişkeni yordamda alın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek geçersiz kılan bir `ByRef` parametre bildirimi. Zorlayan çağrısında `ByVal`, iki düzeyi parantez unutmayın.  
  
 [!code-vb[VbVbcnProcedures#39](./codesnippet/VisualBasic/how-to-force-an-argument-to-be-passed-by-value_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#40](./codesnippet/VisualBasic/how-to-force-an-argument-to-be-passed-by-value_2.vb)]  
  
 Zaman `str` bağımsız değişken listesi içinde ek parantez içine `setNewString` yordamı çağıran koddaki değerini değiştiremez ve `MsgBox` "değiştirilemez, ByVal aktarılırsa" görüntüler. Zaman `str` içine alınmayan ek parantez içine yordamı, değiştirebilir ve `MsgBox` görüntüler "İnString bağımsız değişken için yeni bir değer budur."  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Başvuruya göre değişken başarıyla sonuçlandıktan sonra kullanmalısınız `ByRef` Bu mekanizma belirtmek için anahtar sözcüğü.  
  
 Visual Basic'te bağımsız değişkenleri değere göre geçirilecek varsayılandır. Ancak, iyi bir ya da içerecek şekilde programlama [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) veya [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) anahtar sözcüğü ile bildirilen her parametre. Bu, kodunuzu daha kolay okunmasını sağlar.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Bir yordam parametre bildirirse [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), kodun doğru yürütme çağıran koddaki temel alınan öğeyi değiştirmek için bağlı olabilir. Çağıran kod, bağımsız değişken parantez içine alarak çağıran Bu mekanizma geçersiz kılar veya değiştirilemez bir bağımsız değişken geçerse, temel alınan öğe yordamı değiştiremezsiniz. Bu, çağıran koddaki beklenmeyen sonuçlara yol açabilir.  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Her zaman bir olası riski yoktur çağıran koddaki bağımsız değişken temel değeri değiştirmek bir yordam vermek. Bu değer, değiştirilmesi ve kullanmadan önce geçerliliğini denetlemek için hazırlanması beklediğiniz emin olun.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Yordamlar](./index.md)
- [Yordam Parametreleri ve Bağımsız Değişkenleri](./procedure-parameters-and-arguments.md)
- [Nasıl yapılır: Bir yordama bağımsız değişkenler geçirme](./how-to-pass-arguments-to-a-procedure.md)
- [Bağımsız Değişkenleri Değere ve Başvuruya Göre Geçirme](./passing-arguments-by-value-and-by-reference.md)
- [Değiştirilebilir ve Değiştirilemez Bağımsız Değişkenler Arasındaki Farklar](./differences-between-modifiable-and-nonmodifiable-arguments.md)
- [Değere ve Başvuruya Göre Bağımsız Değişken Geçirme Arasındaki Farklar](./differences-between-passing-an-argument-by-value-and-by-reference.md)
- [Nasıl yapılır: Bir yordam bağımsız değişkeninin değerini değiştirme](./how-to-change-the-value-of-a-procedure-argument.md)
- [Nasıl yapılır: Bir yordam bağımsız değişkenini değer değişikliklerine karşı koruma](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [Bağımsız Değişkenleri Konuma ve Ada Göre Geçirme](./passing-arguments-by-position-and-by-name.md)
- [Değer Türleri ve Başvuru Türleri](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
