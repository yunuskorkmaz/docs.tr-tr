---
title: 'Nasıl yapılır: Bir yordam bağımsız değişkeninin (Visual Basic) değerini değiştirme'
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
- arguments [Visual Basic], ByRef
- arguments [Visual Basic], changing value
ms.assetid: 6fad2368-5da7-4c07-8bf8-0f4e65a1be67
ms.openlocfilehash: a56bdf888163c9559b87e857abb33522c547ed45
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59316628"
---
# <a name="how-to-change-the-value-of-a-procedure-argument-visual-basic"></a>Nasıl yapılır: Bir yordam bağımsız değişkeninin (Visual Basic) değerini değiştirme
Bir yordamı çağırdığınızda, sağladığınız her bağımsız değişken yordamda tanımlanan parametrelerin birine karşılık gelir. Bazı durumlarda çağıran koddaki bağımsız değişken temel değer yordamının kodunu değiştirebilirsiniz. Diğer durumlarda, yordam bir bağımsız değişken yalnızca yerel kopyasına değiştirebilirsiniz.  
  
 Yordamı çağırdığınızda, Visual Basic geçirilen her bağımsız değişken yerel bir kopyasını oluşturur. [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md). Geçirilen her bağımsız değişken için [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), Visual Basic programlama öğesine çağıran koddaki bağımsız değişken arka plandaki bir doğrudan başvuru yordamının kodunu verir.  
  
 Temel alınan öğe çağıran koddaki değiştirilebilir bir öğedir ve geçirilen bağımsız değişken `ByRef`, yordam kodu doğrudan başvuruyu çağıran koddaki öğenin değerini değiştirmek için kullanabilirsiniz.  
  
## <a name="changing-the-underlying-value"></a>Temeldeki değeri değiştirme  
  
#### <a name="to-change-the-underlying-value-of-a-procedure-argument-in-the-calling-code"></a>Temel alınan çağıran koddaki bir yordam bağımsız değişkeninin değerini değiştirmek için  
  
1. Yordam bildiriminde belirtin [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) için argument'ine karşılık gelen parametre.  
  
2. Çağıran kod içinde değiştirilebilir bir programlama öğesine bağımsız değişken olarak geçirin.  
  
3. Çağıran kod içinde bağımsız değişken bağımsız değişken listesinde parantez içine almayın.  
  
4. Yordam kodunda parametre adı çağıran koddaki temel öğeye bir değer atamak için kullanın.  
  
 Örnek görmek için bir tanıtım daha ilerisine.  
  
## <a name="changing-local-copies"></a>Yerel kopya değiştirme  
 Temel alınan öğe çağıran koddaki değiştirilemez bir öğe ise veya bağımsız değişken geçirilmezse `ByVal`, yordamı çağıran koddaki değerini değiştiremezsiniz. Ancak, yordam böyle bir bağımsız değişken yerel kopyasına değiştirebilirsiniz.  
  
#### <a name="to-change-the-copy-of-a-procedure-argument-in-the-procedure-code"></a>Yordam kodunda bir yordam bağımsız değişkeninin kopyasını değiştirmek için  
  
1. Yordam bildiriminde belirtin [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) için argument'ine karşılık gelen parametre.  
  
     -veya-  
  
     Çağıran kod içinde bağımsız değişken bağımsız değişken listesinde parantez içinde alın. Karşılık gelen parametre belirtse dahi, bu bağımsız değişkeni değere göre geçirilecek Visual Basic zorlar `ByRef`.  
  
2. Yordam kodunda parametre adı bağımsız değişkeni bir yerel kopyasını için bir değer atamak için kullanın. Temeldeki değeri çağıran koddaki değiştirilmez.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir dizi değişkenini alabilir ve çalışan iki yordamı öğeleri üzerinde gösterir. `increase` Yordamı yalnızca ekler her öğe için. `replace` Yordamı yeni bir dizi parametresine atar `a()` ve sonra her öğeye ekler.  
  
 [!code-vb[VbVbcnProcedures#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#35)]  
  
 [!code-vb[VbVbcnProcedures#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#36)]  
  
 [!code-vb[VbVbcnProcedures#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#37)]  
  
 İlk `MsgBox` çağrı görüntüler "increase(n) sonra: 11, 21, 31, 41". Çünkü dizi `n` bir başvuru türüdür `replace` geçirme mekanizmasını olsa bile, bu grubun üyeleri değiştirebilirsiniz `ByVal`.  
  
 İkinci `MsgBox` çağrı görüntüler "replace(n) sonra: 101, 201, 301". Çünkü `n` geçirilen `ByRef`, `replace` değişkeni değiştirebilirsiniz `n` çağıran kod ve ona yeni bir dizi atayın. Çünkü `n` bir başvuru türüdür `replace` üyelerini de değiştirebilirsiniz.  
  
 Yordamı çağıran koddaki değişkenin kendisine değiştirmesini engelleyebilirsiniz. Bkz: [nasıl yapılır: Bir yordam bağımsız değişkenini değer değişikliklerine karşı koruma](./how-to-protect-a-procedure-argument-against-value-changes.md).  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Başvuruya göre değişken başarıyla sonuçlandıktan sonra kullanmalısınız `ByRef` Bu mekanizma belirtmek için anahtar sözcüğü.  
  
 Visual Basic'te bağımsız değişkenleri değere göre geçirilecek varsayılandır. Ancak, iyi bir ya da içerecek şekilde programlama [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) veya [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) anahtar sözcüğü ile bildirilen her parametre. Bu, kodunuzu daha kolay okunmasını sağlar.  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Her zaman bir olası riski yoktur çağıran koddaki bağımsız değişken temel değeri değiştirmek bir yordam vermek. Bu değer, değiştirilmesi ve kullanmadan önce geçerliliğini denetlemek için hazırlanması beklediğiniz emin olun.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yordamlar](./index.md)
- [Yordam Parametreleri ve Bağımsız Değişkenleri](./procedure-parameters-and-arguments.md)
- [Nasıl yapılır: Bir yordama bağımsız değişkenler geçirme](./how-to-pass-arguments-to-a-procedure.md)
- [Bağımsız Değişkenleri Değere ve Başvuruya Göre Geçirme](./passing-arguments-by-value-and-by-reference.md)
- [Değiştirilebilir ve Değiştirilemez Bağımsız Değişkenler Arasındaki Farklar](./differences-between-modifiable-and-nonmodifiable-arguments.md)
- [Değere ve Başvuruya Göre Bağımsız Değişken Geçirme Arasındaki Farklar](./differences-between-passing-an-argument-by-value-and-by-reference.md)
- [Nasıl yapılır: Bir yordam bağımsız değişkenini değer değişikliklerine karşı koruma](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [Nasıl yapılır: Bağımsız değişkeni değere göre geçirilecek şekilde zorlama](./how-to-force-an-argument-to-be-passed-by-value.md)
- [Bağımsız Değişkenleri Konuma ve Ada Göre Geçirme](./passing-arguments-by-position-and-by-name.md)
- [Değer Türleri ve Başvuru Türleri](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
