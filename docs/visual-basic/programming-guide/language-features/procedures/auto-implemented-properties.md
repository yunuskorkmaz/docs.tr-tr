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
ms.openlocfilehash: bc83163a024bd50d3e256b4eb49861669f8c02c3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="auto-implemented-properties-visual-basic"></a>Otomatik Uygulanan Özellikler (Visual Basic)
*Otomatik uygulanan Özellikler* kod yazmak zorunda kalmadan bir özelliği bir sınıfın hızla belirtmenizi sağlayan `Get` ve `Set` özelliği. Otomatik uygulanan bir özellik için kodu yazarken, Visual Basic derleyici ilişkili oluşturma yanı sıra özelliği değişkeni depolamak için özel bir alan otomatik olarak oluşturur. `Get` ve `Set` yordamları.  
  
 Otomatik uygulanan özellikler ile bir varsayılan değer de dahil olmak üzere bir özellik, tek bir satırda bildirilebilir. Aşağıdaki örnekte, üç özellik bildirimini gösterir.  
  
 [!code-vb[VbVbalrAutoImplementedProperties#1](./codesnippet/VisualBasic/auto-implemented-properties_1.vb)]  
  
 Otomatik uygulanan bir özellik, özellik değeri özel bir alanda depolanan bir özellik eşdeğerdir. Aşağıdaki kod örneğinde otomatik uygulanan bir özellik gösterir.  
  
 [!code-vb[VbVbalrAutoImplementedProperties#5](./codesnippet/VisualBasic/auto-implemented-properties_2.vb)]  
  
 Aşağıdaki kod örneğinde, önceki otomatik uygulanan özelliği örneğin eşdeğer kodu gösterir.  
  
 [!code-vb[VbVbalrAutoImplementedProperties#2](./codesnippet/VisualBasic/auto-implemented-properties_3.vb)]  
  
 Aşağıdaki kod Göster salt okunur özellikler uygulama:  
  
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
  
 Örnekte gösterildiği gibi başlatma ifadelerle özelliğine atayabilir veya içeren tür Oluşturucu özelliklerinde atayabilirsiniz.  Herhangi bir anda salt okunur özellikler yedekleme alanlarına atayabilirsiniz.  
  
## <a name="backing-field"></a>Yedekleme alanı  
 Otomatik uygulanan bir özellik bildirirken Visual Basic adlı gizli bir özel alan otomatik olarak oluşturur. *yedekleme alanını* özellik değeri alamayacak. Yedekleme alan adı alt çizgi (_) öncesinde otomatik uygulanan özelliği adıdır. Örneğin, otomatik uygulanan adlı bir özellik bildirirseniz `ID`, yedekleme alanını adlı `_ID`. Bir üyesi olarak da adlandırılır sınıfınız içerip içermediğini `_ID`, bir ad çakışması üretmek ve Visual Basic derleyici hatası raporlar.  
  
 Yedekleme alanını ayrıca aşağıdaki özelliklere sahiptir:  
  
-   Yedekleme alanı için erişim değiştiricisi her zaman olduğu `Private`, özellik farklı erişim düzeyi gibi olsa bile `Public`.  
  
-   Özellik olarak işaretlenmişse `Shared`, yedekleme alanını da paylaşılır.  
  
-   Özelliği için belirtilen öznitelikler, yedekleme alanını uygulamayın.  
  
-   Yedekleme alanını sınıfın içindeki kod ve Gözcü penceresi gibi hata ayıklama araçları'ndan erişilebilir. Ancak, yedekleme alanını IntelliSense Sözcük tamamlama listesinde göstermez.  
  
## <a name="initializing-an-auto-implemented-property"></a>Otomatik uygulanan bir özellik başlatılıyor  
 Bir alanı başlatmak için kullanılan herhangi bir ifade otomatik uygulanan bir özellik başlatmak için geçerli değil. Otomatik uygulanan bir özellik başlattığınızda ifade değerlendirilir ve geçirilen `Set` özelliği için yordamı. Aşağıdaki kod örnekleri ilk değerleri dahil bazı otomatik uygulanan özellikler gösterir.  
  
 [!code-vb[VbVbalrAutoImplementedProperties#3](./codesnippet/VisualBasic/auto-implemented-properties_4.vb)]  
  
 Üye otomatik uygulanan bir özellik başlatılamıyor bir `Interface`, veya işaretlenen `MustOverride`.  
  
 Ne zaman bildirdiğiniz otomatik uygulanan bir özellik üyesi olarak bir `Structure`, olarak işaretlenmiş olması durumunda otomatik uygulanan özelliği yalnızca başlatabilir `Shared`.  
  
 Otomatik uygulanan bir özellik olarak bir dizi bildirirken açık dizi sınırları belirtemezsiniz. Ancak, bir değer bir dizi Başlatıcı kullanarak aşağıdaki örneklerde gösterildiği gibi sağlayabilirsiniz.  
  
 [!code-vb[VbVbalrAutoImplementedProperties#4](./codesnippet/VisualBasic/auto-implemented-properties_5.vb)]  
  
## <a name="property-definitions-that-require-standard-syntax"></a>Standart sözdizimi gerekli özellik tanımları  
 Otomatik uygulanan özellikler, kullanışlı ve pek çok programlama senaryolarını destekler. Ancak, otomatik uygulanan bir özellik kullanamazsınız ve bunun yerine standart, kullanmalıdır durumlar vardır veya *Genişletilmiş*, özellik sözdizimi.  
  
 Genişletilmiş özellik tanımını sözdizimi herhangi aşağıdakilerden birini yapmak istiyorsanız kullanmak zorunda:  
  
-   Kodu ekleyin `Get` veya `Set` gelen değerleri doğrulamak için kod gibi bir özelliğin yordamı `Set` yordamı. Örneğin, özellik değeri ayarlamadan önce bir telefon numarasını temsil eden bir dize rakamları gereken sayıda içerdiğini doğrulamak isteyebilirsiniz.  
  
-   İçin farklı erişilebilirlik belirtin `Get` ve `Set` yordamı. Örneğin, yapmak isteyebilirsiniz `Set` yordam `Private` ve `Get` yordamı `Public`.  
  
-   Özellikler oluşturmak `WriteOnly`.  
  
-   Parametreli özelliklerini kullanın (de dahil olmak üzere `Default` özellikleri). Özelliği için bir parametreyi belirtmek için ya da ek parametreler belirtmek için bir genişletilmiş özellik bildirmelidir `Set` yordamı.  
  
-   Yedekleme alana bir öznitelik veya yedekleme alanını erişim düzeyini değiştirin.  
  
-   XML açıklamaları için yedekleme alanı sağlar.  
  
## <a name="expanding-an-auto-implemented-property"></a>Otomatik uygulanan bir özellik genişletme  
 Otomatik uygulanan bir özellik içeren bir genişletilmiş özelliğe dönüştürmek varsa bir `Get` veya `Set` yordamı, Visual Basic kod düzenleyicisinde üretebilir otomatik olarak `Get` ve `Set` yordamları ve `End Property`özelliği için deyimi. İmleç bir boş satır şu yerleştirirseniz kod oluşturulduktan `Property` deyimi, bir `G` (için `Get`) veya bir `S` (için `Set`) ve ENTER tuşuna basın. Visual Basic Kod Düzenleyicisi'ni otomatik olarak oluşturur `Get` veya `Set` yordam sonunda ENTER tuşuna bastığınızda, salt okunur ve salt yazılır özellikler için bir `Property` deyimi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: bildirme ve Visual Basic'te varsayılan özelliğini çağırın](./how-to-declare-and-call-a-default-property.md)  
 [Nasıl yapılır: Bir Özelliği Karışık Erişim Düzeyleriyle Bildirme](./how-to-declare-a-property-with-mixed-access-levels.md)  
 [Property Deyimi](../../../../visual-basic/language-reference/statements/property-statement.md)  
 [ReadOnly](../../../../visual-basic/language-reference/modifiers/readonly.md)  
 [WriteOnly](../../../../visual-basic/language-reference/modifiers/writeonly.md)  
 [Nesneler ve Sınıflar](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
