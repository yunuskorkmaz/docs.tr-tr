---
title: 'Nasıl yapılır: Bir yordam bağımsız değişkenini değer değişikliklerine (Visual Basic) karşı koruma'
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
ms.openlocfilehash: 2548d7a686f3557d154fc4cc15f6fc8026ac46bf
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56968380"
---
# <a name="how-to-protect-a-procedure-argument-against-value-changes-visual-basic"></a>Nasıl yapılır: Bir yordam bağımsız değişkenini değer değişikliklerine (Visual Basic) karşı koruma
Bir yordam parametre olarak bildirirse [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), Visual Basic programlama öğesine çağıran koddaki bağımsız değişken arka plandaki bir doğrudan başvuru yordamının kodunu verir. Bu yordam çağıran koddaki bağımsız değişken temel değeri değiştirmek için izin verir. Bazı durumlarda, bu tür bir değişiklik karşı korumak çağıran kod isteyebilirsiniz.  
  
 Her zaman bir bağımsız değişken değişimi karşılık gelen parametre bildirerek Koruyabileceğiniz [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) yordamda. Bazı durumlarda, ancak diğerlerini belirli bir bağımsız değişkeni değiştirmek istiyorsanız, bildirebilirsiniz `ByRef` ve her çağrıda geçirme mekanizması belirlemek çağıran kod izin verin. Karşılık gelen bağımsız değişkeni değere göre geçirilecek ayraç içinde kapsayan ya da başvuruya göre geçiren parantezlerdeki kapsayan değil bunu yapar. Daha fazla bilgi için [nasıl yapılır: Bağımsız değişkeni değere göre geçirilecek şekilde zorlama](./how-to-force-an-argument-to-be-passed-by-value.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir dizi değişkenini alabilir ve çalışan iki yordamı öğeleri üzerinde gösterir. `increase` Yordamı yalnızca ekler her öğe için. `replace` Yordamı yeni bir dizi parametresine atar `a()` ve sonra her öğeye ekler. Ancak, yakaladığından, temel alınan dizi değişkeni çağıran koddaki etkilemez.  
  
 [!code-vb[VbVbcnProcedures#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#35)]  
  
 [!code-vb[VbVbcnProcedures#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#38)]  
  
 [!code-vb[VbVbcnProcedures#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#37)]  
  
 İlk `MsgBox` çağrı görüntüler "increase(n) sonra: 11, 21, 31, 41". Çünkü dizi `n` bir başvuru türüdür `increase` geçirme mekanizmasını olsa bile, bu grubun üyeleri değiştirebilirsiniz `ByVal`.  
  
 İkinci `MsgBox` çağrı görüntüler "replace(n) sonra: 11, 21, 31, 41". Çünkü `n` geçirilen `ByVal`, `replace` değişkeni değiştiremezsiniz `n` yeni bir dizi atayarak çağıran koddaki. Zaman `replace` yeni dizi örneği oluşturur `k` ve yerel bir değişkene atar `a`, başvuru kaybeder `n` çağıran kod tarafından geçirilen. Üyeleri değiştiğinde `a`, yalnızca yerel dizi `k` etkilenir. Bu nedenle, `replace` dizi değerlerini artırmaz `n` çağıran koddaki.  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Visual Basic'te bağımsız değişkenleri değere göre geçirilecek varsayılandır. Ancak, iyi bir ya da içerecek şekilde programlama [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) veya [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) anahtar sözcüğü ile bildirilen her parametre. Bu, kodunuzu daha kolay okunmasını sağlar.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Yordamlar](./index.md)
- [Yordam Parametreleri ve Bağımsız Değişkenleri](./procedure-parameters-and-arguments.md)
- [Nasıl yapılır: Bir yordama bağımsız değişkenler geçirme](./how-to-pass-arguments-to-a-procedure.md)
- [Bağımsız Değişkenleri Değere ve Başvuruya Göre Geçirme](./passing-arguments-by-value-and-by-reference.md)
- [Değiştirilebilir ve Değiştirilemez Bağımsız Değişkenler Arasındaki Farklar](./differences-between-modifiable-and-nonmodifiable-arguments.md)
- [Değere ve Başvuruya Göre Bağımsız Değişken Geçirme Arasındaki Farklar](./differences-between-passing-an-argument-by-value-and-by-reference.md)
- [Nasıl yapılır: Bir yordam bağımsız değişkeninin değerini değiştirme](./how-to-change-the-value-of-a-procedure-argument.md)
- [Nasıl yapılır: Bağımsız değişkeni değere göre geçirilecek şekilde zorlama](./how-to-force-an-argument-to-be-passed-by-value.md)
- [Bağımsız Değişkenleri Konuma ve Ada Göre Geçirme](./passing-arguments-by-position-and-by-name.md)
- [Değer Türleri ve Başvuru Türleri](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
