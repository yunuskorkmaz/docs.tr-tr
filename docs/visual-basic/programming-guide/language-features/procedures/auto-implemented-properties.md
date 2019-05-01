---
title: Otomatik Uygulanan Özellikler (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.AutoProperty
- vb.AutoImplementedProperty
helpviewer_keywords:
- properties [Visual Basic], auto-implemented
- properties [Visual Basic], auto-implemented
- auto-implemented properties [Visual Basic]
ms.assetid: 5c669f0b-cf95-4b4e-ae84-9cc55212ca87
ms.openlocfilehash: aa045dd5454819a37ad81c76d97fd3e61e7d0420
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61864320"
---
# <a name="auto-implemented-properties-visual-basic"></a>Otomatik Uygulanan Özellikler (Visual Basic)
*Otomatik uygulanan Özellikler* hızlı bir şekilde kod yazmak zorunda kalmadan bir sınıfın bir özelliği belirtmenize olanak verir `Get` ve `Set` özelliği. Otomatik uygulanan bir özellik için kod yazdığınızda, Visual Basic Derleyicisi ilişkili oluşturmaya ek olarak özellik değişkeni depolamak için özel bir alan otomatik olarak oluşturur. `Get` ve `Set` yordamları.  
  
 Otomatik uygulanan özelliklerle tek bir satırda varsayılan bir değer de dahil olmak üzere, bir özellik bildirilebilir. Aşağıdaki örnek, üç özellik bildirimini gösterir.  
  
 [!code-vb[VbVbalrAutoImplementedProperties#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrautoimplementedproperties/vb/module1.vb#1)]  
  
 Otomatik uygulanan bir özellik, özellik değeri özel bir alanda depolandığı bir özellik eşdeğerdir. Aşağıdaki kod örneği, otomatik uygulanan bir özellik gösterilmektedir.  
  
 [!code-vb[VbVbalrAutoImplementedProperties#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrautoimplementedproperties/vb/module1.vb#5)]  
  
 Aşağıdaki kod örneği, önceki otomatik uygulanan özellik örneğin eşdeğer kodu gösterir.  
  
 [!code-vb[VbVbalrAutoImplementedProperties#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrautoimplementedproperties/vb/module1.vb#2)]  
  
 Aşağıdaki kod, salt okunur özellikler uygulama göster:  
  
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
  
 Örnekte gösterildiği gibi özelliğine başlatma ifadeleri ile atayabilir veya içeren türün yapıcı özelliklerinde atayabilirsiniz.  Salt okunur özellikler yedekleme alanlarına herhangi bir zamanda atayabilirsiniz.  
  
## <a name="backing-field"></a>Destek alanı  
 Otomatik uygulanan bir özellik bildirdiğinizde, Visual Basic adlı gizli bir özel alan otomatik olarak oluşturur. *destek alanı* özellik değeri içerecek. Yedekleme alan adı, alt çizgi (_) tarafından öncesinde otomatik uygulanan özellik adıdır. Örneğin, adında bir otomatik uygulanan özellik bildirirseniz `ID`, yedekleme alanını adlı `_ID`. Olarak da adlandırılır sınıfınızın bir üye içerip içermediğini `_ID`çakışması üretmek ve Visual Basic derleyici hatası bildirir.  
  
 Destek alanı ayrıca aşağıdaki özelliklere sahiptir:  
  
- Her zaman erişim değiştiricisini destek alanı olan `Private`, özelliği bir farklı erişim düzeyi gibi olsa bile `Public`.  
  
- Özellik olarak işaretlenmişse `Shared`, yedekleme alanını da paylaşılır.  
  
- Özelliği için belirtilen öznitelikler için destek alanı geçerli değildir.  
  
- Destek alanı, sınıf içindeki kod ve İzleme penceresi gibi hata ayıklama araçları'ndan erişilebilir. Ancak, yedekleme alanını IntelliSense Sözcük tamamlama listesinde göstermez.  
  
## <a name="initializing-an-auto-implemented-property"></a>Otomatik uygulanan bir özellik başlatma  
 Bir alanı başlatmak için kullanılan herhangi bir ifade başlatma otomatik olarak uygulanan bir özellik için geçerli değil. Otomatik uygulanan bir özellik başlattığınızda, ifade değerlendirilir ve geçirilen `Set` özelliği için yordamı. Aşağıdaki kod örnekleri başlangıç değerleri içeren bazı otomatik uygulanan özellikler gösterir.  
  
 [!code-vb[VbVbalrAutoImplementedProperties#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrautoimplementedproperties/vb/module1.vb#3)]  
  
 Otomatik uygulanan bir üyesi olan bir özellik başlatılamıyor bir `Interface`, veya olarak işaretlenmiş bir `MustOverride`.  
  
 Otomatik uygulanan bir özellik üyesi bildirdiğinizde bir `Structure`, olarak işaretlenmişse yalnızca otomatik uygulanan özellik başlatabilirsiniz `Shared`.  
  
 Otomatik uygulanan bir özellik olarak bir dizi bildirdiğinizde açıkça dizi sınırları belirtemezsiniz. Ancak, bir değer bir dizi Başlatıcısı kullanarak aşağıdaki örneklerde gösterildiği gibi sağlayabilirsiniz.  
  
 [!code-vb[VbVbalrAutoImplementedProperties#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrautoimplementedproperties/vb/module1.vb#4)]  
  
## <a name="property-definitions-that-require-standard-syntax"></a>Standart söz dizimi gerektiren özellik tanımları  
 Otomatik uygulanan özellikler kullanışlı ve çok sayıda programlama senaryolarını destekler. Ancak, otomatik uygulanan bir özellik kullanamazsınız ve bunun yerine standart kullanmalısınız durumlar vardır veya *Genişletilmiş*, özellik sözdizimi.  
  
 Genişletilmiş özellik tanımı sözdizimleri aşağıdakilerden herhangi biri yapmak istiyorsanız kullanmak zorunda:  
  
- Kodu `Get` veya `Set` yordamı gelen değerleri doğrulamak için kodu gibi bir özelliğin `Set` yordamı. Örneğin, özellik değeri ayarlamadan önce bir telefon numarasını temsil eden bir dize gerekli rakam sayısını içerdiğini doğrulamak isteyebilirsiniz.  
  
- Belirtmek için farklı erişilebilirlik `Get` ve `Set` yordamı. Örneğin, yapmak isteyebilirsiniz `Set` yordamı `Private` ve `Get` yordamı `Public`.  
  
- Özellikleri oluşturma `WriteOnly`.  
  
- Parametreli özelliklerini kullanma (dahil olmak üzere `Default` özellikleri). İçin ek parametreler belirtmek için veya bir özellik için bir parametreyi belirtmek için genişletilmiş bir özellik bildirmelidir `Set` yordamı.  
  
- Yedekleme alana bir öznitelik veya destek alanı erişim düzeyini değiştirebilirsiniz.  
  
- XML açıklamaları için yedekleme alanı sağlar.  
  
## <a name="expanding-an-auto-implemented-property"></a>Otomatik uygulanan bir özellik genişletme  
 Otomatik uygulanan bir özellik içeren bir genişletilmiş özelliğe Dönüştür varsa bir `Get` veya `Set` yordamı, Visual Basic Kod Düzenleyicisi oluşturabileceği otomatik olarak `Get` ve `Set` yordamlar ve `End Property`özelliği için deyimi. İmleç bir boş satır şu koyarsanız kod oluşturulur `Property` deyimi, bir `G` (için `Get`) veya bir `S` (için `Set`) ve ENTER tuşuna basın. Visual Basic Kod Düzenleyicisi'ni otomatik olarak oluşturduğu `Get` veya `Set` yordamın sonunda ENTER tuşuna bastığınızda, salt okunur ve salt yazılır özellikler için bir `Property` deyimi.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Bildirme ve Visual Basic'te bir varsayılan özelliğini çağırın](./how-to-declare-and-call-a-default-property.md)
- [Nasıl yapılır: Bir özelliği karışık erişim düzeyleriyle bildirme](./how-to-declare-a-property-with-mixed-access-levels.md)
- [Property Deyimi](../../../../visual-basic/language-reference/statements/property-statement.md)
- [ReadOnly](../../../../visual-basic/language-reference/modifiers/readonly.md)
- [WriteOnly](../../../../visual-basic/language-reference/modifiers/writeonly.md)
- [Nesneler ve Sınıflar](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
