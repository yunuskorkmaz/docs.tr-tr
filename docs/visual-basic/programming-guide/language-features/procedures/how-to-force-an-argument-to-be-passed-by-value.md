---
title: "Nasıl yapılır: Bağımsız Değişkeni Değere Göre Geçirilecek Şekilde Zorlama (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: fdb2df7e114f49c23db9f5b322ca9dd32135ac88
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-force-an-argument-to-be-passed-by-value-visual-basic"></a>Nasıl yapılır: Bağımsız Değişkeni Değere Göre Geçirilecek Şekilde Zorlama (Visual Basic)
Yordam bildirimi geçirme mekanizması belirler. Bir parametre bildirilirse [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] başvuru ile ilgili bağımsız değişken geçirmek bekliyor. Bu, çağrıyı yapan kod değişkeninde temel programlama öğenin değerini değiştirmek için yordamı sağlar. Temel alınan öğe bu tür değişiklik karşı korumak isterseniz, geçersiz kılabilirsiniz `ByRef` geçirme mekanizması yordamda çağrı parantez içinde bağımsız değişken adı kapsayan tarafından. Bağımsız değişken listesi çağrısında kapsayan parantez yanı sıra bu parantezler var.  
  
 Çağrıyı yapan kod geçersiz kılınamaz bir [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) mekanizması.  
  
### <a name="to-force-an-argument-to-be-passed-by-value"></a>Bağımsız değişkeni değere göre geçirilecek şekilde zorlama  
  
-   Karşılık gelen bir parametre bildirilirse `ByVal` yordamda herhangi bir ek adımlar gerekmez. [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]bağımsız değişkeni değere göre geçirilecek zaten bekliyor.  
  
-   Karşılık gelen bir parametre bildirilirse `ByRef` bağımsız değişkeni parantez içinde yordam çağrısı yordamda alın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte geçersiz kılan bir `ByRef` parametre bildirimi. Zorlar çağrısında `ByVal`, parantez iki düzeyde unutmayın.  
  
 [!code-vb[VbVbcnProcedures#39](./codesnippet/VisualBasic/how-to-force-an-argument-to-be-passed-by-value_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#40](./codesnippet/VisualBasic/how-to-force-an-argument-to-be-passed-by-value_2.vb)]  
  
 Zaman `str` bağımsız değişken listesi içinde ek parantez içine `setNewString` yordamı çağıran kodu değerini değiştiremez ve `MsgBox` "değiştirilemez, ByVal aktarılırsa" görüntüler. Zaman `str` içine alınmayan fazladan parantez içinde yordamı, değiştirebilir ve `MsgBox` "Bu inString bağımsız değişken için yeni bir değer" görüntülüyor.  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Başvuruya göre bir değişken geçirdiğinizde kullanmalısınız `ByRef` anahtar Bu mekanizma belirtin.  
  
 Varsayılan olarak [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] bağımsız değişkenleri değere göre geçirmektir. Ancak, ya da dahil etmek için uygulama programlama iyi [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) veya [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) bildirilen her parametre olan anahtar sözcük. Bu, kodunuzu okumak kolaylaştırır.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Bir yordam bir parametre bildirirse [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), doğru kodunun yürütülmesini çağıran kodu temel alınan öğe değiştirme yetkisi olan bağlı olabilir. Çağrıyı yapan kod parantez içinde bağımsız değişken kapsayan tarafından bu arama mekanizması kılıyorsa veya değiştirilemez bağımsız değişkeni geçerse yordamı temel öğesi değiştiremezsiniz. Bu, çağrıyı yapan kod beklenmeyen sonuçlara yol açabilir.  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Yoktur her zaman potansiyel bir risk çağıran kodu bir bağımsız değişken alttaki değerini değiştirmek bir yordam sağlar. Bu değeri değiştirilmesi ve kullanmadan önce geçerliliğini denetlemek için hazırlanması beklediğiniz emin olun.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yordamları](./index.md)  
 [Parametreler ve bağımsız değişkenler](./procedure-parameters-and-arguments.md)  
 [Nasıl yapılır: bir yordama bağımsız değişkenler geçirme](./how-to-pass-arguments-to-a-procedure.md)  
 [Bağımsız değişkenleri değere ve başvuruya göre geçirme](./passing-arguments-by-value-and-by-reference.md)  
 [Değiştirilebilir ve değiştirilemez bağımsız değişkenler arasındaki farklar](./differences-between-modifiable-and-nonmodifiable-arguments.md)  
 [Değere ve başvuruya göre bağımsız değişken geçirme arasındaki farklar](./differences-between-passing-an-argument-by-value-and-by-reference.md)  
 [Nasıl yapılır: bir yordam bağımsız değişkeninin değerini değiştirme](./how-to-change-the-value-of-a-procedure-argument.md)  
 [Nasıl yapılır: bir yordam bağımsız değişkenini değer değişikliklerine karşı koruma](./how-to-protect-a-procedure-argument-against-value-changes.md)  
 [Bağımsız değişkenleri konuma göre ve ada göre geçirme](./passing-arguments-by-position-and-by-name.md)  
 [Değer türleri ve başvuru türleri](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
