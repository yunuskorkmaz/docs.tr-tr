---
title: 'Nasıl yapılır: Bir Yordam Bağımsız Değişkenini Değer Değişikliklerine Karşı Koruma (Visual Basic)'
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
ms.openlocfilehash: d2e131b770d8498a634d946a5900f9b373ca7e56
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33651524"
---
# <a name="how-to-protect-a-procedure-argument-against-value-changes-visual-basic"></a>Nasıl yapılır: Bir Yordam Bağımsız Değişkenini Değer Değişikliklerine Karşı Koruma (Visual Basic)
Bir yordam parametre olarak bildirirse [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), Visual Basic yordamı kod çağıran kodu değişkeninde temel programlama öğesi için doğrudan bir başvuru sağlar. Bu, yordamı çağıran kodu değişkeninde alttaki değerini değiştirmek için izin verir. Bazı durumlarda, bu tür bir değişiklik karşı korumak çağıran kodu isteyebilirsiniz.  
  
 Her zaman bir bağımsız değişken değişikliği karşılık gelen bir parametre bildirerek Koruyabileceğiniz [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) yordamda. Bazı durumlarda ancak diğer belirtilen bir bağımsız değişkeni değiştirmek istiyorsanız, bildirebilir `ByRef` ve her çağrıda geçirme mekanizması belirlemek çağıran kodu izin verin. Karşılık gelen bağımsız değişkeni değere göre geçirilecek parantez içinde kapsayan ya da bu başvuruya göre geçirmek için parantez içinde kapsayan değil bunu yapar. Daha fazla bilgi için bkz: [nasıl yapılır: bağımsız değişkeni değere göre bayraklarıdır için zorlama](./how-to-force-an-argument-to-be-passed-by-value.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir dizi değişkeni alabilir ve çalışan iki yordam üzerinde öğeleri gösterir. `increase` Yordamı yalnızca ekler her öğe için. `replace` Yordamı atar yeni bir dizi parametre `a()` ve her öğe için ekler. Ancak, yeniden atama çağıran kodu temel alınan dizi değişkeni etkilemez.  
  
 [!code-vb[VbVbcnProcedures#35](./codesnippet/VisualBasic/how-to-protect-a-procedure-argument-against-value-changes_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#38](./codesnippet/VisualBasic/how-to-protect-a-procedure-argument-against-value-changes_2.vb)]  
  
 [!code-vb[VbVbcnProcedures#37](./codesnippet/VisualBasic/how-to-protect-a-procedure-argument-against-value-changes_3.vb)]  
  
 İlk `MsgBox` çağrısı görüntüler "increase(n) sonra: 11, 21, 31, 41". Çünkü dizi `n` bir başvuru türü `replace` geçirme mekanizması olmamasına rağmen bu grubun üyeleri değiştirebilirsiniz `ByVal`.  
  
 İkinci `MsgBox` çağrısı görüntüler "replace(n) sonra: 11, 21, 31, 41". Çünkü `n` geçirilen `ByVal`, `replace` değişkeni değiştirilemiyor `n` yeni bir dizi atayarak çağıran kodu. Zaman `replace` yeni dizi örneği oluşturur `k` ve yerel bir değişkene atar `a`, başvuru kaybederse `n` çağıran kodu tarafından geçirilen. Üyeleri değiştiğinde `a`, yalnızca yerel dizi `k` etkilenir. Bu nedenle, `replace` dizi değerlerini artırmaz `n` çağıran kodu.  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Visual Basic'de bağımsız değişkenleri değere göre geçirilecek varsayılandır. Ancak, ya da dahil etmek için uygulama programlama iyi [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) veya [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) bildirilen her parametre olan anahtar sözcük. Bu, kodunuzu okumak kolaylaştırır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yordamlar](./index.md)  
 [Yordam Parametreleri ve Bağımsız Değişkenleri](./procedure-parameters-and-arguments.md)  
 [Nasıl yapılır: Bir Yordama Bağımsız Değişkenler Geçirme](./how-to-pass-arguments-to-a-procedure.md)  
 [Bağımsız Değişkenleri Değere ve Başvuruya Göre Geçirme](./passing-arguments-by-value-and-by-reference.md)  
 [Değiştirilebilir ve Değiştirilemez Bağımsız Değişkenler Arasındaki Farklar](./differences-between-modifiable-and-nonmodifiable-arguments.md)  
 [Değere ve Başvuruya Göre Bağımsız Değişken Geçirme Arasındaki Farklar](./differences-between-passing-an-argument-by-value-and-by-reference.md)  
 [Nasıl yapılır: Bir Yordam Bağımsız Değişkeninin Değerini Değiştirme](./how-to-change-the-value-of-a-procedure-argument.md)  
 [Nasıl yapılır: Bağımsız Değişkeni Değere Göre Geçirilecek Şekilde Zorlama](./how-to-force-an-argument-to-be-passed-by-value.md)  
 [Bağımsız Değişkenleri Konuma ve Ada Göre Geçirme](./passing-arguments-by-position-and-by-name.md)  
 [Değer Türleri ve Başvuru Türleri](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
