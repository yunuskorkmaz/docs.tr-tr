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
ms.openlocfilehash: d991a385e537c43daeb708e96e712acd92110379
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403388"
---
# <a name="auto-implemented-properties-visual-basic"></a>Otomatik Uygulanan Özellikler (Visual Basic)
*Otomatik uygulanan özellikler* , kod yazmak zorunda kalmadan bir sınıfın özelliğini hızlı bir şekilde belirtmenizi sağlar `Get` `Set` . Otomatik uygulanan bir özellik için kod yazdığınızda, Visual Basic Derleyicisi otomatik olarak, ilişkili ve yordamları oluşturmaya ek olarak özellik değişkenini depolamak için bir özel alan oluşturur `Get` `Set` .  
  
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
 Otomatik olarak uygulanan bir özellik bildirdiğinizde, Visual Basic otomatik olarak, özellik değerini içerecek şekilde, *yedekleme alanı* olarak adlandırılan gizli bir özel alan oluşturur. Yedekleme alanı adı, önce bir alt çizgi (_) tarafından gerçekleştirilen otomatik uygulanan özellik adıdır. Örneğin, adlı otomatik uygulanan bir özellik bildirirseniz `ID` , yedekleme alanı olarak adlandırılır `_ID` . Aynı zamanda adlı sınıfınızın bir üyesini dahil ederseniz `_ID` , bir adlandırma çakışması üretir ve bir derleyici hatası Visual Basic rapor edebilirsiniz.  
  
 Ayrıca, yedekleme alanı aşağıdaki özelliklere sahiptir:  
  
- , `Private` Özelliği gibi farklı bir erişim düzeyine sahip olsa bile, yedekleme alanı için erişim değiştiricisi her zaman olur `Public` .  
  
- Özelliği olarak işaretlenmişse `Shared` , yedekleme alanı da paylaşılır.  
  
- Özelliği için belirtilen öznitelikler, yedekleme alanı için geçerlidir.  
  
- Yedekleme alanına, sınıf içindeki koddan ve izleme penceresi gibi hata ayıklama araçlarından erişilebilir. Ancak, yedekleme alanı bir IntelliSense sözcük tamamlama listesinde gösterilmez.  
  
## <a name="initializing-an-auto-implemented-property"></a>Otomatik uygulanan özellik başlatılıyor  
 Bir alanı başlatmak için kullanılabilecek herhangi bir ifade, otomatik olarak uygulanan bir özelliğin başlatılması için geçerlidir. Otomatik uygulanan bir özelliği başlattığınızda, ifade değerlendirilir ve `Set` özellik yordamına geçirilir. Aşağıdaki kod örnekleri, başlangıç değerlerini içeren bazı otomatik uygulanmış özellikleri gösterir.  
  
 [!code-vb[VbVbalrAutoImplementedProperties#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrautoimplementedproperties/vb/module1.vb#3)]  
  
 Bir veya işaretli bir üyesi olan bir otomatik uygulanan özelliği başlatamıyor `Interface` `MustOverride` .  
  
 Otomatik uygulanan bir özelliği bir üyesi olarak bildirdiğinizde `Structure` , yalnızca olarak işaretlenmişse otomatik uygulanan özelliğini başlatabilirsiniz `Shared` .  
  
 Otomatik uygulanan bir özelliği dizi olarak bildirdiğinizde açık dizi sınırları belirtemezsiniz. Ancak, aşağıdaki örneklerde gösterildiği gibi bir dizi başlatıcısı kullanarak bir değer sağlayabilirsiniz.  
  
 [!code-vb[VbVbalrAutoImplementedProperties#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrautoimplementedproperties/vb/module1.vb#4)]  
  
## <a name="property-definitions-that-require-standard-syntax"></a>Standart sözdizimi gerektiren özellik tanımları  
 Otomatik uygulanan özellikler kullanışlı ve birçok programlama senaryosunu destekler. Ancak, otomatik olarak uygulanan bir özelliği kullanabileceğiniz durumlar vardır ve bunun yerine standart ya da *genişletilmiş*, özellik sözdizimini kullanmanız gerekir.  
  
 Aşağıdakilerden birini yapmak istiyorsanız genişletilmiş özellik tanımı sözdizimini kullanmanız gerekir:  
  
- `Get` `Set` Yordamda gelen değerleri doğrulamak için kod gibi bir özelliğin veya yordamına kod ekleyin `Set` . Örneğin, bir telefon numarasını temsil eden bir dizenin, özellik değerini ayarlamadan önce gereken sayıda rakamları içerdiğini doğrulamak isteyebilirsiniz.  
  
- Ve yordamı için farklı erişilebilirlik `Get` belirtin `Set` . Örneğin, `Set` yordamı `Private` ve yordamı yapmak isteyebilirsiniz `Get` `Public` .  
  
- Olan özellikleri oluşturun `WriteOnly` .  
  
- Parametreli özellikleri kullanın ( `Default` Özellikler dahil). Özelliği için bir parametre belirtmek veya yordamın ek parametrelerini belirtmek için genişletilmiş bir özellik bildirmeniz gerekir `Set` .  
  
- Yedekleme alanına bir öznitelik yerleştirin veya yedekleme alanının erişim düzeyini değiştirin.  
  
- Yedekleme alanı için XML açıklamaları sağlayın.  
  
## <a name="expanding-an-auto-implemented-property"></a>Otomatik uygulanan bir özellik genişletiliyor  
 Otomatik olarak uygulanan bir özelliği bir veya yordamı içeren genişletilmiş bir özelliğe dönüştürmeniz gerekiyorsa `Get` `Set` , Visual Basic kod Düzenleyicisi, `Get` özelliği için otomatik olarak ve `Set` yordamlarını ve `End Property` ifadesini oluşturabilir. Bu kod, imleci deyimden sonra boş bir satıra yerleştirirseniz `Property` , bir `G` (için `Get` ) veya bir `S` (IÇIN `Set` ) yazın ve ENTER tuşuna basın. Visual Basic kod Düzenleyicisi, `Get` `Set` bir DEYIMIN sonunda ENTER tuşuna bastığınızda salt okunurdur ve salt yazılır özellikler için otomatik olarak or yordamını üretir `Property` .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Visual Basic'de Varsayılan Bir Özelliği Bildirme ve Çağırma](./how-to-declare-and-call-a-default-property.md)
- [Nasıl yapılır: Bir Özelliği Karışık Erişim Düzeyleriyle Bildirme](./how-to-declare-a-property-with-mixed-access-levels.md)
- [Property Deyimi](../../../language-reference/statements/property-statement.md)
- [Özelliğinin](../../../language-reference/modifiers/readonly.md)
- [WriteOnly](../../../language-reference/modifiers/writeonly.md)
- [Nesneler ve sınıflar](../objects-and-classes/index.md)
