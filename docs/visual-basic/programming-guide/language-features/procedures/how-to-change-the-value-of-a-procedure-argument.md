---
title: 'Nasıl yapılır: Bir Yordam Bağımsız Değişkeninin Değerini Değiştirme (Visual Basic)'
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedures [Visual Basic], parameters
- procedure arguments
- arguments [Visual Basic], passing by reference
- Visual Basic code, procedures
- arguments [Visual Basic], ByVal
- arguments [Visual Basic], passing by value
- procedure parameters
- arguments [Visual Basic], ByRef
- arguments [Visual Basic], changing value
ms.assetid: 6fad2368-5da7-4c07-8bf8-0f4e65a1be67
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 93d9cc11e919e45fdd3b48dd2731b165f3466640
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-change-the-value-of-a-procedure-argument-visual-basic"></a>Nasıl yapılır: Bir Yordam Bağımsız Değişkeninin Değerini Değiştirme (Visual Basic)
Bir yordam çağrısı, sağladığınız her bağımsız değişkeni yordamda tanımlanan parametrelerin birine karşılık gelir. Bazı durumlarda, yordam kodunu çağıran kodu bir bağımsız değişken temel değeri değiştirebilirsiniz. Diğer durumlarda, yordam bir bağımsız değişken yalnızca kendi yerel kopyasını değiştirebilirsiniz.  
  
 Yordam çağrısı, Visual Basic geçirilen her bağımsız değişkeni yerel bir kopyasını oluşturur [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md). Her değişken için [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), Visual Basic yordamı kod çağıran kodu değişkeninde temel programlama öğesi için doğrudan bir başvuru sağlar.  
  
 Çağrıyı yapan kod temel alınan öğe değiştirilebilir bir öğedir ve bağımsız değişken geçirildi `ByRef`, yordam kodu çağıran kodu öğenin değerini değiştirmek için doğrudan başvuru kullanabilirsiniz.  
  
## <a name="changing-the-underlying-value"></a>Temel alınan değerini değiştirme  
  
#### <a name="to-change-the-underlying-value-of-a-procedure-argument-in-the-calling-code"></a>Temel alınan arama kodda bir yordam bağımsız değişkeninin değerini değiştirmek için  
  
1.  Yordam bildiriminde belirtin [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) bağımsız değişkeni için karşılık gelen parametresi için.  
  
2.  Arama kodda değiştirilebilir bir programlama öğesi bağımsız değişken olarak geçirin.  
  
3.  Arama kodda bağımsız değişken bağımsız değişken listesinde parantez içine almayın.  
  
4.  Yordam kodunda parametre adı çağıran kodu temel alınan öğe için bir değer atamak için kullanın.  
  
 Örnek bir örnek için aşağı daha fazla.  
  
## <a name="changing-local-copies"></a>Yerel kopyaları değiştirme  
 Çağrıyı yapan kod temel alınan öğe değiştirilemez bir öğeyse ya da bağımsız değişken geçirildi `ByVal`, yordamı çağıran kodu değeriyle değiştiremezsiniz. Ancak, yordam böyle bir bağımsız değişken yerel kopyasını değiştirebilirsiniz.  
  
#### <a name="to-change-the-copy-of-a-procedure-argument-in-the-procedure-code"></a>Bir yordam bağımsız değişkenini yordamı kodda kopyasını değiştirmek için  
  
1.  Yordam bildiriminde belirtin [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) bağımsız değişkeni için karşılık gelen parametresi için.  
  
     -veya-  
  
     Çağrıyı yapan kod içinde bağımsız değişken bağımsız değişken listesinde parantez içinde alın. Karşılık gelen bir parametre belirtir olsa bile bu bağımsız değişkeni değere göre geçirilecek Visual Basic zorlar `ByRef`.  
  
2.  Yordam kodunda parametre adı yerel kopyasını bağımsız değişkeni için bir değer atamak için kullanın. Çağrıyı yapan kod temel alınan değer değiştirilmez.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir dizi değişkeni alabilir ve çalışan iki yordam üzerinde öğeleri gösterir. `increase` Yordamı yalnızca ekler her öğe için. `replace` Yordamı atar yeni bir dizi parametre `a()` ve her öğe için ekler.  
  
 [!code-vb[VbVbcnProcedures#35](./codesnippet/VisualBasic/how-to-change-the-value-of-a-procedure-argument_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#36](./codesnippet/VisualBasic/how-to-change-the-value-of-a-procedure-argument_2.vb)]  
  
 [!code-vb[VbVbcnProcedures#37](./codesnippet/VisualBasic/how-to-change-the-value-of-a-procedure-argument_3.vb)]  
  
 İlk `MsgBox` çağrısı görüntüler "increase(n) sonra: 11, 21, 31, 41". Çünkü dizi `n` bir başvuru türü `replace` geçirme mekanizması olmamasına rağmen bu grubun üyeleri değiştirebilirsiniz `ByVal`.  
  
 İkinci `MsgBox` çağrısı görüntüler "replace(n) sonra: 101, 201, 301". Çünkü `n` geçirilen `ByRef`, `replace` değişkeni değiştirebilirsiniz `n` çağıran kodu ve ata ona yeni bir dizi. Çünkü `n` bir başvuru türü `replace` üyelerini de değiştirebilirsiniz.  
  
 Çağrıyı yapan kod değişkenin kendisine değiştirme yordamı engelleyebilir. Bkz: [nasıl yapılır: bir yordam bağımsız değişkenini değer değişikliklerine karşı koruma](./how-to-protect-a-procedure-argument-against-value-changes.md).  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Başvuruya göre bir değişken geçirdiğinizde kullanmalısınız `ByRef` anahtar Bu mekanizma belirtin.  
  
 Visual Basic'de bağımsız değişkenleri değere göre geçirilecek varsayılandır. Ancak, ya da dahil etmek için uygulama programlama iyi [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) veya [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) bildirilen her parametre olan anahtar sözcük. Bu, kodunuzu okumak kolaylaştırır.  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Yoktur her zaman potansiyel bir risk çağıran kodu bir bağımsız değişken alttaki değerini değiştirmek bir yordam sağlar. Bu değeri değiştirilmesi ve kullanmadan önce geçerliliğini denetlemek için hazırlanması beklediğiniz emin olun.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yordamlar](./index.md)  
 [Yordam Parametreleri ve Bağımsız Değişkenleri](./procedure-parameters-and-arguments.md)  
 [Nasıl yapılır: Bir Yordama Bağımsız Değişkenler Geçirme](./how-to-pass-arguments-to-a-procedure.md)  
 [Bağımsız Değişkenleri Değere ve Başvuruya Göre Geçirme](./passing-arguments-by-value-and-by-reference.md)  
 [Değiştirilebilir ve Değiştirilemez Bağımsız Değişkenler Arasındaki Farklar](./differences-between-modifiable-and-nonmodifiable-arguments.md)  
 [Değere ve Başvuruya Göre Bağımsız Değişken Geçirme Arasındaki Farklar](./differences-between-passing-an-argument-by-value-and-by-reference.md)  
 [Nasıl yapılır: Bir Yordam Bağımsız Değişkenini Değer Değişikliklerine Karşı Koruma](./how-to-protect-a-procedure-argument-against-value-changes.md)  
 [Nasıl yapılır: Bağımsız Değişkeni Değere Göre Geçirilecek Şekilde Zorlama](./how-to-force-an-argument-to-be-passed-by-value.md)  
 [Bağımsız Değişkenleri Konuma ve Ada Göre Geçirme](./passing-arguments-by-position-and-by-name.md)  
 [Değer Türleri ve Başvuru Türleri](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
