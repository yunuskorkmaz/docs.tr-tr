---
title: "Nesne Değişken Bildirimi (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "33"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: cdca188d778e9884f918d97eba492a29c64af826
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="object-variable-declaration-visual-basic"></a>Nesne Değişken Bildirimi (Visual Basic)
Bir nesne değişkeni bildirme için normal bildirimi deyimini kullanın. Veri türü için ya da belirttiğiniz `Object` (diğer bir deyişle, [nesne veri türü](../../../../visual-basic/language-reference/data-types/object-data-type.md)) ya da nesne olduğu oluşturulacak daha belirli bir sınıf.  
  
 Bir değişken olarak bildirme `Object` olarak bildirme aynı <xref:System.Object?displayProperty=nameWithType>.  
  
 Belirli nesne sınıfı sahip bir değişken bildirirken tüm yöntemleri ve özellikleri o sınıfı ve devraldığı sınıfları tarafından kullanıma sunulan erişebilir. Değişkenle bildirirseniz <xref:System.Object>, yalnızca üyeleri erişebilir <xref:System.Object> sınıfı, açmanız sürece `Option Strict Off` geç bağlama izin vermek için.  
  
## <a name="declaration-syntax"></a>Bildirim Sözdizimi  
 Bir nesne değişkeni bildirmek için aşağıdaki sözdizimini kullanın:  
  
```vb  
Dim variablename As [New] { objectclass | Object }  
```  
  
 Ayrıca belirtebilirsiniz [ortak](../../../../visual-basic/language-reference/modifiers/public.md), [korumalı](../../../../visual-basic/language-reference/modifiers/protected.md), [arkadaş](../../../../visual-basic/language-reference/modifiers/friend.md), `Protected Friend`, [özel](../../../../visual-basic/language-reference/modifiers/private.md), [paylaşılan](../../../../visual-basic/language-reference/modifiers/shared.md), veya [statik](../../../../visual-basic/language-reference/modifiers/static.md) bildirimi. Aşağıdaki örnek bildirimi geçerlidir:  
  
```vb  
Private objA As Object  
Static objB As System.Windows.Forms.Label  
Dim objC As System.OperatingSystem  
```  
  
## <a name="late-binding-and-early-binding"></a>Geç bağlama ve erken bağlama  
 Bazen kodunuzu çalıştırılana kadar belirli bir sınıf bilinmiyor. Bu durumda, ile nesne değişkeni bildirilmelidir `Object` veri türü. Bu genel bir başvuru herhangi türde bir nesne oluşturur ve belirli bir sınıf çalışma zamanında atanır. Bu adlı *geç bağlama*. Geç bağlama ek yürütme süresi gerektirir. Ayrıca, kodunuzu yöntemlere ve en son kendisine atadığınız sınıfının özelliklerini sınırlar. Kodunuzu farklı bir sınıf üyeleri erişmeye çalışırsa bu çalışma zamanı hataları neden olabilir.  
  
 Belirli bir sınıf derleme zamanında bildiğiniz durumlarda bu sınıfının olması gereken nesne değişkeni bildirmeniz gerekir. Bu adlı *erken bağlama*. Erken bağlama performansını artırır ve kod erişiminizi tüm yöntemleri ve özellikleri belirli bir sınıfın güvence altına alır. Yukarıdaki örnek bildirimlerden, değişken varsa `objA` yalnızca sınıfın nesnelerini kullanır <xref:System.Windows.Forms.Label?displayProperty=nameWithType>, belirtmeniz gerekir `As System.Windows.Forms.Label` kendi bildirimi.  
  
### <a name="advantages-of-early-binding"></a>Erken bağlama avantajları  
 Belirli bir sınıf olarak bir nesne değişkeni bildirme çeşitli avantajları sağlar:  
  
-   Otomatik tür denetleme  
  
-   Belirli bir sınıfın tüm üyelerine erişim garanti  
  
-   Kod Düzenleyicisi'nde Microsoft IntelliSense desteği  
  
-   Kodunuzu geliştirilmiş okunabilirliğini  
  
-   Kodunuzu daha az hataları  
  
-   Hataları sırasında yakalanan derleme zamanı yerine çalışma zamanı  
  
-   Daha hızlı kodu yürütme  
  
## <a name="access-to-object-variable-members"></a>Değişken üyeleri nesne erişimi  
 Zaman `Option Strict` açık `On`, bir nesne değişkeninin yalnızca yöntemleri ve hangi bildirdiğiniz onu sınıfının özelliklerine erişebilir. Aşağıdaki örnek bunu göstermektedir.  
  
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
  
 Bu örnekte, `p` yalnızca üyeleri kullanabilirsiniz <xref:System.Object> sınıfının kendisini, hangi içermeyen `Left` özelliği. Diğer taraftan, `q` türünde olması bildirildi <xref:System.Windows.Forms.Label>, tüm yöntemleri ve özellikleri kullanabilmesi için <xref:System.Windows.Forms.Label> sınıfını <xref:System.Windows.Forms> ad alanı.  
  
## <a name="flexibility-of-object-variables"></a>Nesne değişkenleri esnekliğini  
 Devralma Hiyerarşisi nesneleri ile çalışırken, nesne değişkenlerini bildirme için kullanılacak hangi sınıfı seçimine sahip. Bu seçim yaparken, bir sınıf üyelerine erişimi karşı nesne ataması esnekliğini dengelemeniz gerekir. Örneğin, yol açar Devralma Hiyerarşisi göz önünde bulundurun <xref:System.Windows.Forms.Form?displayProperty=nameWithType> sınıfı:  
  
 <xref:System.Object>  
  
 &nbsp;&nbsp;<xref:System.MarshalByRefObject>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;<xref:System.ComponentModel.Component>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.Control>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.ScrollableControl>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.ContainerControl>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.Form>  
  
 Uygulamanızı form adlı bir sınıf tanımlar varsayalım `specialForm`, sınıfından devralan <xref:System.Windows.Forms.Form>. Özellikle çok başvuran bir nesne değişkeni bildirme `specialForm`, aşağıdaki örnekte gösterildiği gibi.  
  
```vb  
Public Class specialForm  
    Inherits System.Windows.Forms.Form  
    ' Insert code defining methods and properties of specialForm.  
End Class  
Dim nextForm As New specialForm  
```  
  
 Önceki örnekte bildirimi değişkeni sınırlar `nextForm` sınıfındaki nesneler için `specialForm`, ancak tüm yöntemleri ve özellikleri de sağlar `specialForm` kullanılabilir `nextForm`, yanı sıra, tüm sınıflar olarak tüm üyeleri `specialForm` devralır.  
  
 Daha fazla genel bir nesne değişkeninin türü olmasını bildirerek yapabileceğiniz <xref:System.Windows.Forms.Form>, aşağıdaki örnekte gösterildiği gibi.  
  
```vb  
Dim anyForm As System.Windows.Forms.Form  
```  
  
 Önceki örnekte bildirimi için uygulamanızda herhangi bir biçimde atamanıza olanak tanır `anyForm`. Ancak, ancak `anyForm` sınıfın tüm üyeleri erişebilir <xref:System.Windows.Forms.Form>, ek yöntemleri veya gibi belirli formlar için tanımlanan özellikler herhangi birini kullanamazsınız `specialForm`.  
  
 Bir taban sınıfın tüm üyeleri için türetilen sınıflar kullanılabilir, ancak ek türetilmiş bir sınıf üyeleri için temel sınıf kullanılamaz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nesne değişkenleri](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [Nesne değişkeni ataması](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)  
 [Nesne değişkeni değerleri](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)  
 [Nasıl yapılır: bir nesne değişkeni bildirme ve Visual Basic'te bir nesneyi atayın](../../../../visual-basic/programming-guide/language-features/variables/how-to-declare-an-object-variable-and-assign-an-object-to-it.md)  
 [Nasıl yapılır: bir nesnenin üyelerine erişme](../../../../visual-basic/programming-guide/language-features/variables/how-to-access-members-of-an-object.md)  
 [New işleci](../../../../visual-basic/language-reference/operators/new-operator.md)  
 [Option Strict deyimi](../../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [Yerel tür çıkarımı](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
