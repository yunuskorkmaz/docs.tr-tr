---
title: Otomatik Uygulanan Özellikler (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.AutoProperty
- vb.AutoImplementedProperty
helpviewer_keywords:
- properties [Visual Basic], auto-implemented
- auto-implemented properties [Visual Basic]
ms.assetid: 5c669f0b-cf95-4b4e-ae84-9cc55212ca87
ms.openlocfilehash: f2e25c7bcd3556f93dfedee7aa8e49bb14888123
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70254026"
---
# <a name="auto-implemented-properties-visual-basic"></a>Otomatik Uygulanan Özellikler (Visual Basic)
*Otomatik uygulanan özellikler* `Get` `Set` , kod yazmak zorunda kalmadan bir sınıfın özelliğini hızlı bir şekilde belirtmenizi sağlar. Otomatik uygulanan bir özellik için kod yazdığınızda, Visual Basic Derleyicisi otomatik olarak, ilişkili `Get` ve `Set` yordamları oluşturmaya ek olarak özellik değişkenini depolamak için bir özel alan oluşturur.  
  
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
 Otomatik olarak uygulanan bir özellik bildirdiğinizde, Visual Basic otomatik olarak, özellik değerini içerecek şekilde, *yedekleme alanı* olarak adlandırılan gizli bir özel alan oluşturur. Yedekleme alanı adı, önce bir alt çizgi (_) tarafından gerçekleştirilen otomatik uygulanan özellik adıdır. Örneğin, adlı `ID`otomatik uygulanan bir özellik bildirirseniz, yedekleme alanı olarak adlandırılır `_ID`. Aynı zamanda adlı `_ID`sınıfınızın bir üyesini dahil ederseniz, bir adlandırma çakışması üretir ve bir derleyici hatası Visual Basic rapor edebilirsiniz.  
  
 Ayrıca, yedekleme alanı aşağıdaki özelliklere sahiptir:  
  
- , Özelliği gibi farklı bir erişim düzeyine `Private` `Public`sahip olsa bile, yedekleme alanı için erişim değiştiricisi her zaman olur.  
  
- Özelliği olarak `Shared`işaretlenmişse, yedekleme alanı da paylaşılır.  
  
- Özelliği için belirtilen öznitelikler, yedekleme alanı için geçerlidir.  
  
- Yedekleme alanına, sınıf içindeki koddan ve izleme penceresi gibi hata ayıklama araçlarından erişilebilir. Ancak, yedekleme alanı bir IntelliSense sözcük tamamlama listesinde gösterilmez.  
  
## <a name="initializing-an-auto-implemented-property"></a>Otomatik uygulanan özellik başlatılıyor  
 Bir alanı başlatmak için kullanılabilecek herhangi bir ifade, otomatik olarak uygulanan bir özelliğin başlatılması için geçerlidir. Otomatik uygulanan bir özelliği başlattığınızda, ifade değerlendirilir ve özellik `Set` yordamına geçirilir. Aşağıdaki kod örnekleri, başlangıç değerlerini içeren bazı otomatik uygulanmış özellikleri gösterir.  
  
 [!code-vb[VbVbalrAutoImplementedProperties#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrautoimplementedproperties/vb/module1.vb#3)]  
  
 Bir `Interface`veya işaretli `MustOverride`bir üyesi olan bir otomatik uygulanan özelliği başlatamıyor.  
  
 Otomatik uygulanan bir özelliği bir `Structure`üyesi olarak bildirdiğinizde, yalnızca olarak `Shared`işaretlenmişse otomatik uygulanan özelliğini başlatabilirsiniz.  
  
 Otomatik uygulanan bir özelliği dizi olarak bildirdiğinizde açık dizi sınırları belirtemezsiniz. Ancak, aşağıdaki örneklerde gösterildiği gibi bir dizi başlatıcısı kullanarak bir değer sağlayabilirsiniz.  
  
 [!code-vb[VbVbalrAutoImplementedProperties#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrautoimplementedproperties/vb/module1.vb#4)]  
  
## <a name="property-definitions-that-require-standard-syntax"></a>Standart sözdizimi gerektiren özellik tanımları  
 Otomatik uygulanan özellikler kullanışlı ve birçok programlama senaryosunu destekler. Ancak, otomatik olarak uygulanan bir özelliği kullanabileceğiniz durumlar vardır ve bunun yerine standart ya da *genişletilmiş*, özellik sözdizimini kullanmanız gerekir.  
  
 Aşağıdakilerden birini yapmak istiyorsanız genişletilmiş özellik tanımı sözdizimini kullanmanız gerekir:  
  
- Yordamda gelen değerleri `Get` `Set` doğrulamak için kod gibi bir özelliğin veya yordamına kod ekleyin. `Set` Örneğin, bir telefon numarasını temsil eden bir dizenin, özellik değerini ayarlamadan önce gereken sayıda rakamları içerdiğini doğrulamak isteyebilirsiniz.  
  
- `Get` Ve`Set` yordamı için farklı erişilebilirlik belirtin. Örneğin, `Set` yordamı `Private` ve `Get` yordamı yapmakisteyebilirsiniz.`Public`  
  
- Olan özellikleri oluşturun `WriteOnly`.  
  
- Parametreli özellikleri kullanın (Özellikler `Default` dahil). Özelliği için bir parametre belirtmek veya `Set` yordamın ek parametrelerini belirtmek için genişletilmiş bir özellik bildirmeniz gerekir.  
  
- Yedekleme alanına bir öznitelik yerleştirin veya yedekleme alanının erişim düzeyini değiştirin.  
  
- Yedekleme alanı için XML açıklamaları sağlayın.  
  
## <a name="expanding-an-auto-implemented-property"></a>Otomatik uygulanan bir özellik genişletiliyor  
 Otomatik uygulanan bir özelliği `Get` bir veya `Set` yordamı içeren genişletilmiş bir özelliğe dönüştürmeniz gerekiyorsa, Visual Basic kod `Get` Düzenleyicisi otomatik olarak ve `Set` yordamlarını oluşturabilir ve `End Property`özelliği için bildirim. Bu kod, imleci `Property` deyimden sonra boş bir satıra yerleştirirseniz, bir `G` (için `Get`) veya bir `S` (için `Set`) yazın ve ENTER tuşuna basın. Visual Basic kod Düzenleyicisi, bir `Get` `Property` deyimin sonunda ENTER `Set` tuşuna bastığınızda salt okunurdur ve salt yazılır özellikler için otomatik olarak or yordamını üretir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Visual Basic varsayılan bir özellik bildirin ve çağırın](./how-to-declare-and-call-a-default-property.md)
- [Nasıl yapılır: Karışık erişim düzeylerine sahip bir özellik bildirme](./how-to-declare-a-property-with-mixed-access-levels.md)
- [Property Deyimi](../../../../visual-basic/language-reference/statements/property-statement.md)
- [ReadOnly](../../../../visual-basic/language-reference/modifiers/readonly.md)
- [WriteOnly](../../../../visual-basic/language-reference/modifiers/writeonly.md)
- [Nesneler ve Sınıflar](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
