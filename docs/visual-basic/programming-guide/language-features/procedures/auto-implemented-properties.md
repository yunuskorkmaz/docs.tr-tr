---
title: Otomatik Uygulanan Özellikler
ms.date: 07/20/2015
f1_keywords:
- vb.AutoProperty
- vb.AutoImplementedProperty
helpviewer_keywords:
- properties [Visual Basic], auto-implemented
- auto-implemented properties [Visual Basic]
ms.assetid: 5c669f0b-cf95-4b4e-ae84-9cc55212ca87
ms.openlocfilehash: b322bd2215c95298be0a33ace1f3590a63878e24
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350377"
---
# <a name="auto-implemented-properties-visual-basic"></a>Otomatik Uygulanan Özellikler (Visual Basic)
*Otomatik uygulanan özellikler* , `Get` kod yazmak ve özelliği `Set` zorunda kalmadan bir sınıfın bir özelliğini hızlı bir şekilde belirtmenizi sağlar. Otomatik uygulanan bir özellik için kod yazdığınızda Visual Basic derleyici, ilişkili `Get` ve `Set` yordamlarını oluşturmaya ek olarak özellik değişkenini depolamak için otomatik olarak bir özel alan oluşturur.  
  
 Otomatik uygulanan özellikler ile, varsayılan değer de dahil olmak üzere tek bir satırda bildirilebilecek bir özellik. Aşağıdaki örnek, üç özellik bildirimini gösterir.  
  
 [!code-vb[VbVbalrAutoImplementedProperties#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrautoimplementedproperties/vb/module1.vb#1)]  
  
 Otomatik uygulanan bir özellik, özellik değerinin özel bir alanda depolandığı bir özelliğe eşdeğerdir. Aşağıdaki kod örneği, otomatik olarak uygulanan bir özelliği gösterir.  
  
 [!code-vb[VbVbalrAutoImplementedProperties#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrautoimplementedproperties/vb/module1.vb#5)]  
  
 Aşağıdaki kod örneği, önceki otomatik uygulanan özellik örneği için denk kodu gösterir.  
  
 [!code-vb[VbVbalrAutoImplementedProperties#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrautoimplementedproperties/vb/module1.vb#2)]  
  
 Aşağıdaki kod, salt okunur özellikleri uygulamayı gösterir:  
  
```vb  
Class Customer  
   Public ReadOnly Property Tags As New List(Of String)  
   Public ReadOnly Property Name As String = ""  
   Public ReadOnly Property File As String  
  
   Sub New(file As String)  
      Me.File = file  
   End Sub  
End Class  
```  
  
 Örneğinde gösterildiği gibi başlatma ifadeleriyle özelliğe atayabilirsiniz veya kapsayan türün oluşturucusunda özelliklere atayabilirsiniz.  Herhangi bir zamanda ReadOnly özelliklerinin yedekleme alanlarına atayabilirsiniz.  
  
## <a name="backing-field"></a>Destek alanı  
 Otomatik olarak uygulanan bir özellik bildirdiğinizde, Visual Basic otomatik olarak, özellik değerini içerecek şekilde, *yedekleme alanı* olarak adlandırılan gizli bir özel alan oluşturur. Yedekleme alanı adı, önce bir alt çizgi (_) tarafından gerçekleştirilen otomatik uygulanan özellik adıdır. Örneğin, `ID`adlı otomatik uygulanan bir özellik bildirirseniz, yedekleme alanı `_ID`olarak adlandırılır. `_ID`adlı sınıfınızın bir üyesini dahil ederseniz, bir adlandırma çakışması oluşturursunuz ve bir derleyici hatası rapor Visual Basic.  
  
 Ayrıca, yedekleme alanı aşağıdaki özelliklere sahiptir:  
  
- Özellik, `Public`gibi farklı bir erişim düzeyine sahip olsa bile, yedekleme alanı için erişim değiştiricisi her zaman `Private`.  
  
- Özellik `Shared`olarak işaretlenmişse, yedekleme alanı da paylaşılır.  
  
- Özelliği için belirtilen öznitelikler, yedekleme alanı için geçerlidir.  
  
- Yedekleme alanına, sınıf içindeki koddan ve izleme penceresi gibi hata ayıklama araçlarından erişilebilir. Ancak, yedekleme alanı bir IntelliSense sözcük tamamlama listesinde gösterilmez.  
  
## <a name="initializing-an-auto-implemented-property"></a>Otomatik uygulanan özellik başlatılıyor  
 Bir alanı başlatmak için kullanılabilecek herhangi bir ifade, otomatik olarak uygulanan bir özelliğin başlatılması için geçerlidir. Otomatik olarak uygulanan bir özelliği başlattığınızda, ifade değerlendirilir ve özellik için `Set` yordamına geçirilir. Aşağıdaki kod örnekleri, başlangıç değerlerini içeren bazı otomatik uygulanmış özellikleri gösterir.  
  
 [!code-vb[VbVbalrAutoImplementedProperties#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrautoimplementedproperties/vb/module1.vb#3)]  
  
 Bir `Interface`üyesi olan veya `MustOverride`olarak işaretlenmiş bir otomatik uygulanan özelliği başlatılamaz.  
  
 Otomatik uygulanan bir özelliği bir `Structure`üyesi olarak bildirdiğinizde, otomatik uygulanan özelliği yalnızca `Shared`olarak işaretlenmişse başlatabilirsiniz.  
  
 Otomatik uygulanan bir özelliği dizi olarak bildirdiğinizde açık dizi sınırları belirtemezsiniz. Ancak, aşağıdaki örneklerde gösterildiği gibi bir dizi başlatıcısı kullanarak bir değer sağlayabilirsiniz.  
  
 [!code-vb[VbVbalrAutoImplementedProperties#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrautoimplementedproperties/vb/module1.vb#4)]  
  
## <a name="property-definitions-that-require-standard-syntax"></a>Standart sözdizimi gerektiren özellik tanımları  
 Otomatik uygulanan özellikler kullanışlı ve birçok programlama senaryosunu destekler. Ancak, otomatik olarak uygulanan bir özelliği kullanabileceğiniz durumlar vardır ve bunun yerine standart ya da *genişletilmiş*, özellik sözdizimini kullanmanız gerekir.  
  
 Aşağıdakilerden birini yapmak istiyorsanız genişletilmiş özellik tanımı sözdizimini kullanmanız gerekir:  
  
- `Set` yordamındaki gelen değerleri doğrulamak için kod gibi bir özelliğin `Get` veya `Set` yordamına kod ekleyin. Örneğin, bir telefon numarasını temsil eden bir dizenin, özellik değerini ayarlamadan önce gereken sayıda rakamları içerdiğini doğrulamak isteyebilirsiniz.  
  
- `Get` ve `Set` yordamı için farklı erişilebilirlik belirtin. Örneğin, `Set` yordamı `Private` ve `Get` yordamı `Public`yapmak isteyebilirsiniz.  
  
- `WriteOnly`Özellikler oluşturun.  
  
- Parametreli özellikleri kullanın (`Default` özellikler dahil). Özelliği için bir parametre belirtmek veya `Set` yordamı için ek parametreler belirtmek üzere genişletilmiş bir özellik bildirmeniz gerekir.  
  
- Yedekleme alanına bir öznitelik yerleştirin veya yedekleme alanının erişim düzeyini değiştirin.  
  
- Yedekleme alanı için XML açıklamaları sağlayın.  
  
## <a name="expanding-an-auto-implemented-property"></a>Otomatik uygulanan bir özellik genişletiliyor  
 Otomatik uygulanan bir özelliği bir `Get` veya `Set` yordamı içeren genişletilmiş bir özelliğe dönüştürmeniz gerekiyorsa Visual Basic kod Düzenleyicisi, özelliği için `Get` ve `Set` yordamlarını ve `End Property` ifadesini otomatik olarak oluşturabilir. İmleci `Property` deyimden sonra boş bir satıra yerleştirirseniz, bir `G` (`Get`) veya `S` (`Set`için) yazın ve ENTER tuşuna basın. Visual Basic kodu Düzenleyicisi, `Property` deyimin sonunda ENTER tuşuna bastığınızda salt okunurdur ve salt yazılır özellikler için `Get` veya `Set` yordamını otomatik olarak oluşturur.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Visual Basic varsayılan bir özellik bildirme ve çağırma](./how-to-declare-and-call-a-default-property.md)
- [Nasıl yapılır: Bir Özelliği Karışık Erişim Düzeyleriyle Bildirme](./how-to-declare-a-property-with-mixed-access-levels.md)
- [Property Deyimi](../../../../visual-basic/language-reference/statements/property-statement.md)
- [ReadOnly](../../../../visual-basic/language-reference/modifiers/readonly.md)
- [WriteOnly](../../../../visual-basic/language-reference/modifiers/writeonly.md)
- [Nesneler ve Sınıflar](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
