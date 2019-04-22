---
title: Nesne Değişken Bildirimi (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- early binding [Visual Basic]
- declarations [Visual Basic], class
- classes [Visual Basic], declaring
- binding [Visual Basic], late and early
- object variables [Visual Basic], declaring
- variables [Visual Basic], object
- declaring variables [Visual Basic], object variables
- declaring classes [Visual Basic]
- late binding [Visual Basic]
ms.assetid: 2a5a41a3-1aa8-4236-b1f0-2382af7bf715
ms.openlocfilehash: 4a3ef3a8254153fa8695ffacd9829ca9316d77a5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58837657"
---
# <a name="object-variable-declaration-visual-basic"></a>Nesne Değişken Bildirimi (Visual Basic)
Bir normal bir bildirim deyiminin bir nesne değişkenini bildirmek için kullanın. Veri türü için ya da belirttiğiniz `Object` (diğer bir deyişle, [nesne veri türü](../../../../visual-basic/language-reference/data-types/object-data-type.md)) veya nesne olduğu oluşturulacak daha belirli bir sınıf.  
  
 Bir değişken olarak bildirme `Object` olarak bildirme aynı <xref:System.Object?displayProperty=nameWithType>.  
  
 Belirli nesne sınıfı sahip bir değişken bildirdiğinizde tüm yöntemler ve o sınıfın ve devraldığı sınıfları tarafından kullanıma sunulan özellikler erişebilirsiniz. Değişkenle bildirirseniz <xref:System.Object>, yalnızca üyelerinin erişebildiğinizi <xref:System.Object> sınıf özelliğini sürece `Option Strict Off` geç bağlamaya izin vermek için.  
  
## <a name="declaration-syntax"></a>Bildirim Sözdizimi  
 Bir nesne değişkenini bildirmek için aşağıdaki sözdizimini kullanın:  
  
```vb  
Dim variablename As [New] { objectclass | Object }  
```  
  
 Ayrıca belirtebileceğiniz [genel](../../../../visual-basic/language-reference/modifiers/public.md), [korumalı](../../../../visual-basic/language-reference/modifiers/protected.md), [arkadaş](../../../../visual-basic/language-reference/modifiers/friend.md), `Protected Friend`, [özel](../../../../visual-basic/language-reference/modifiers/private.md), [paylaşılan](../../../../visual-basic/language-reference/modifiers/shared.md), veya [statik](../../../../visual-basic/language-reference/modifiers/static.md) bildirimi. Aşağıdaki örnek bildirimleri geçerlidir:  
  
```vb  
Private objA As Object  
Static objB As System.Windows.Forms.Label  
Dim objC As System.OperatingSystem  
```  
  
## <a name="late-binding-and-early-binding"></a>Geç bağlama ve erken bağlama  
 Bazen belirli sınıf kodunuzu çalışana kadar bilinmiyor. Bu durumda, nesne değişkeni ile bildirilmelidir `Object` veri türü. Bu genel bir tür nesneyi başvuru oluşturur ve belirli bir sınıf, çalışma zamanında atanır. Bu adlandırılır *geç bağlama*. Geç bağlama ek yürütme süresi gerektirir. Ayrıca, kodunuzun en son kendisine atadığınız sınıfının özellikleri ve yöntemleri için sınırlar. Kodunuzu farklı bir sınıfın üyeleri erişmeye çalışırsa, bu çalışma zamanı hatalarına neden olabilir.  
  
 Derleme zamanında belirli sınıf bildiğinizde, bu sınıfı olmasını nesne değişkeni bildirmelidir. Bu adlandırılır *erken bağlama*. Erken bağlama performansını artırır ve tüm yöntemler ve Özellikler belirli bir sınıfın kod erişiminizi güvence altına alır. Önceki örnek bildirimlerinde, değişken `objA` yalnızca sınıfın nesneleri kullanan <xref:System.Windows.Forms.Label?displayProperty=nameWithType>, belirtmeniz gerekir `As System.Windows.Forms.Label` kendi bildirimi.  
  
### <a name="advantages-of-early-binding"></a>Erken bağlama avantajları  
 Belirli bir sınıf olarak bir nesne değişkeni bildirme çeşitli avantajlar sağlar:  
  
-   Otomatik tür denetleme  
  
-   Belirli bir sınıfın tüm üyeleri için erişim garantisi  
  
-   Kod Düzenleyicisi'nde Microsoft IntelliSense desteği  
  
-   Geliştirilmiş kod okunabilirliğini  
  
-   Kodunuzu daha az hataları  
  
-   Hataları sırasında yakalanan derleme zamanı yerine çalışma zamanı  
  
-   Daha hızlı kod yürütme  
  
## <a name="access-to-object-variable-members"></a>Nesne değişkeni üye erişimi  
 Zaman `Option Strict` etkinleştirilmişse `On`, yalnızca yöntemleri ve özellikleri ile kaydedilebilmeniz bu sınıfın bir nesne değişkenine erişebilir. Aşağıdaki örnek bunu göstermektedir.  
  
```vb  
' Option statements must precede all other source file lines.  
Option Strict On  
' Imports statement must precede all declarations in the source file.  
Imports System.Windows.Forms  
Public Sub accessMembers()  
    Dim p As Object  
    Dim q As System.Windows.Forms.Label  
    p = New System.Windows.Forms.Label  
    q = New System.Windows.Forms.Label  
    Dim j, k As Integer  
    ' The following statement generates a compiler ERROR.  
    j = p.Left  
    ' The following statement retrieves the left edge of the label in pixels.  
    k = q.Left  
End Sub  
```  
  
 Bu örnekte, `p` yalnızca üyelerinin kullanabileceği <xref:System.Object> kendisi, hangi içermeyen sınıf `Left` özelliği. Öte yandan, `q` türü olarak bildirildi <xref:System.Windows.Forms.Label>, tüm yöntemleri ve özellikleri kullanabilmesi için <xref:System.Windows.Forms.Label> sınıfını <xref:System.Windows.Forms> ad alanı.  
  
## <a name="flexibility-of-object-variables"></a>Nesne değişkenleri esnekliği  
 Devralma Hiyerarşisi nesneleri ile çalışırken, nesne değişkenini bildirmek için kullanılacak hangi sınıfın vardır. Bu seçim yaparken, nesne ataması bir sınıf üyelerine erişimi karşı esnekliğini dengelemeniz gerekir. Örneğin, yol açar Devralma Hiyerarşisi düşünün <xref:System.Windows.Forms.Form?displayProperty=nameWithType> sınıfı:  
  
 <xref:System.Object>  
  
 &nbsp;&nbsp;<xref:System.MarshalByRefObject>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;<xref:System.ComponentModel.Component>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.Control>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.ScrollableControl>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.ContainerControl>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.Form>  
  
 Uygulamanızı form adlı bir sınıf tanımlar varsayalım `specialForm`, sınıfından devralan <xref:System.Windows.Forms.Form>. Özellikle çok başvuran bir nesne değişkeninin bildirebilirsiniz `specialForm`aşağıdaki örnekte gösterildiği gibi.  
  
```vb  
Public Class specialForm  
    Inherits System.Windows.Forms.Form  
    ' Insert code defining methods and properties of specialForm.  
End Class  
Dim nextForm As New specialForm  
```  
  
 Değişken bildirimi önceki örnekte sınırlar `nextForm` sınıfındaki nesneler için `specialForm`, ancak tüm yöntemleri ve özellikleri de getirir `specialForm` kullanılabilir `nextForm`, içinden tüm sınıflar gibi tüm üyelerinin yanı sıra `specialForm` devralır.  
  
 Daha genel bir nesne değişkeninin türü olmasını bildirerek yapabileceğiniz <xref:System.Windows.Forms.Form>aşağıdaki örnekte gösterildiği gibi.  
  
```vb  
Dim anyForm As System.Windows.Forms.Form  
```  
  
 Önceki örnekte bildirimi için uygulamanızda herhangi bir biçimde atamanıza olanak sağlar `anyForm`. Ancak, ancak `anyForm` sınıfın tüm üyeleri erişebilir <xref:System.Windows.Forms.Form>, herhangi bir ek yöntemleri veya özellikleri gibi özel formlar için tanımlanan kullanamazsınız `specialForm`.  
  
 Türetilen sınıflar için bir taban sınıfın tüm üyeleri kullanılabilir, ancak ek üyeler türetilmiş bir sınıfın temel sınıf için kullanılamaz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nesne Değişkenleri](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Nesne Değişkeni Ataması](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [Nesne Değişkeni Değerleri](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [Nasıl yapılır: Bir nesne değişkeni bildirme ve Visual Basic'te bir nesne atama](../../../../visual-basic/programming-guide/language-features/variables/how-to-declare-an-object-variable-and-assign-an-object-to-it.md)
- [Nasıl yapılır: Bir nesnenin üyelerine erişim](../../../../visual-basic/programming-guide/language-features/variables/how-to-access-members-of-an-object.md)
- [New İşleci](../../../../visual-basic/language-reference/operators/new-operator.md)
- [Option Strict Deyimi](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [Yerel Çıkarım](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
