---
title: Nesne Değişken Bildirimi
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
ms.openlocfilehash: d1964e3768124dde1deeabfada9006ff5a59def0
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351809"
---
# <a name="object-variable-declaration-visual-basic"></a>Nesne Değişken Bildirimi (Visual Basic)
Bir nesne değişkeni bildirmek için normal bir bildirim bildirimi kullanın. Veri türü için, `Object` (yani, [nesne veri türü](../../../../visual-basic/language-reference/data-types/object-data-type.md)) ya da nesnenin oluşturulacağı daha belirli bir sınıf belirtirsiniz.  
  
 Bir değişkeni `Object` olarak bildirmek, <xref:System.Object?displayProperty=nameWithType>olarak bildirme ile aynıdır.  
  
 Belirli bir nesne sınıfıyla bir değişken bildirdiğinizde, bu sınıf ve devraldığı sınıflar tarafından sunulan tüm yöntemlere ve özelliklere erişebilir. Değişkeni <xref:System.Object>ile bildirirseniz, `Option Strict Off` geç bağlamaya izin vermediğiniz müddetçe, yalnızca <xref:System.Object> sınıfının üyelerine erişebilir.  
  
## <a name="declaration-syntax"></a>Bildirim Söz Dizimi  
 Bir nesne değişkenini bildirmek için aşağıdaki sözdizimini kullanın:  
  
```vb  
Dim variablename As [New] { objectclass | Object }  
```  
  
 Ayrıca bildirimde [ortak](../../../../visual-basic/language-reference/modifiers/public.md), [korumalı](../../../../visual-basic/language-reference/modifiers/protected.md), [arkadaş](../../../../visual-basic/language-reference/modifiers/friend.md), `Protected Friend`, [özel](../../../../visual-basic/language-reference/modifiers/private.md), [paylaşılan](../../../../visual-basic/language-reference/modifiers/shared.md)veya [statik](../../../../visual-basic/language-reference/modifiers/static.md) de belirtebilirsiniz. Aşağıdaki örnek bildirimler geçerlidir:  
  
```vb  
Private objA As Object  
Static objB As System.Windows.Forms.Label  
Dim objC As System.OperatingSystem  
```  
  
## <a name="late-binding-and-early-binding"></a>Geç bağlama ve erken bağlama  
 Bazen, kodunuz çalışana kadar belirli bir sınıf bilinmez. Bu durumda, nesne değişkenini `Object` veri türüyle bildirmeniz gerekir. Bu, herhangi bir nesne türüne genel bir başvuru oluşturur ve belirli bir sınıf çalışma zamanında atanır. Bu, *geç bağlama*olarak adlandırılır. Geç bağlama ek yürütme süresi gerektirir. Ayrıca, kodunuzu en son atadığınız sınıfın yöntemleriyle ve özellikleriyle da sınırlandırır. Bu, kodunuzun farklı bir sınıfın üyelerine erişmeye çalışırsa çalışma zamanı hatalarına neden olabilir.  
  
 Derleme zamanında belirli bir sınıfı bildiğinizde, nesne değişkenini bu sınıftan olacak şekilde bildirmeniz gerekir. Bu, *erken bağlama*olarak adlandırılır. Erken bağlama performansı iyileştirir ve kodun tüm yöntemlerine ve özelliklerine yönelik kod erişiminizi güvence altına alır. Önceki örnek bildirimlerinde, değişkeni `objA` yalnızca <xref:System.Windows.Forms.Label?displayProperty=nameWithType>sınıfının nesnelerini kullanıyorsa, bildiriminde `As System.Windows.Forms.Label` belirtmeniz gerekir.  
  
### <a name="advantages-of-early-binding"></a>Erken bağlamanın avantajları  
 Bir nesne değişkeninin belirli bir sınıf olarak bildirilmesi çeşitli avantajlar sunar:  
  
- Otomatik tür denetimi  
  
- Belirli bir sınıfın tüm üyelerine garantili erişim  
  
- Kod düzenleyicisinde Microsoft IntelliSense desteği  
  
- Kodunuzun okunabilirliğini geliştirildi  
  
- Kodunuzda daha az hata var  
  
- Çalışma zamanı yerine derleme sırasında hatalar yakalandı  
  
- Daha hızlı kod yürütme  
  
## <a name="access-to-object-variable-members"></a>Nesne değişkeni üyelerine erişim  
 `Option Strict` `On`açıldığında, bir nesne değişkeni yalnızca bunu bildirdiğiniz sınıfın yöntemlerine ve özelliklerine erişebilir. Aşağıdaki örnek bunu göstermektedir.  
  
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
  
 Bu örnekte `p`, yalnızca <xref:System.Object> sınıfının kendisini `Left` özelliğini içermeyen üyeleri kullanabilir. Diğer taraftan, `q` <xref:System.Windows.Forms.Label>türünde olduğu bildirildi, bu nedenle <xref:System.Windows.Forms> ad alanındaki <xref:System.Windows.Forms.Label> sınıfının tüm yöntemlerini ve özelliklerini kullanabilir.  
  
## <a name="flexibility-of-object-variables"></a>Nesne değişkenlerinin esnekliği  
 Devralma hiyerarşisinde nesnelerle çalışırken, nesne değişkenlerinizi bildirirken hangi sınıftan kullanacağınızı tercih edersiniz. Bu seçimi yaparken, bir sınıfın üyelerine erişim için nesne atamasının esnekliğini dengeetmeniz gerekir. Örneğin, <xref:System.Windows.Forms.Form?displayProperty=nameWithType> sınıfına yol gösteren devralma hiyerarşisini göz önünde bulundurun:  
  
 <xref:System.Object>  
  
 &nbsp;&nbsp;<xref:System.MarshalByRefObject>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;<xref:System.ComponentModel.Component>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.Control>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.ScrollableControl>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.ContainerControl>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.Form>  
  
 Uygulamanızın, <xref:System.Windows.Forms.Form>sınıfından devralan `specialForm`adlı bir form sınıfı tanımladığını varsayalım. Aşağıdaki örnekte gösterildiği gibi, özel olarak `specialForm`başvuran bir nesne değişkeni bildirebilirsiniz.  
  
```vb  
Public Class specialForm  
    Inherits System.Windows.Forms.Form  
    ' Insert code defining methods and properties of specialForm.  
End Class  
Dim nextForm As New specialForm  
```  
  
 Önceki örnekteki bildirim, `nextForm` değişkenini `specialForm`sınıf nesneleriyle sınırlandırır, ancak aynı zamanda `specialForm` devraldığı tüm sınıfların tüm üyelerinin yanı sıra `nextForm``specialForm` tüm yöntemleri ve özellikleri de sağlar.  
  
 Aşağıdaki örnekte gösterildiği gibi, <xref:System.Windows.Forms.Form>türünde olmasına bildirerek bir nesne değişkenini daha genel hale getirebilirsiniz.  
  
```vb  
Dim anyForm As System.Windows.Forms.Form  
```  
  
 Yukarıdaki örnekteki bildirim, `anyForm`uygulamanızdaki herhangi bir formu atamanızı sağlar. Ancak, `anyForm` tüm <xref:System.Windows.Forms.Form>üyelerine erişebilse de, `specialForm`gibi belirli formlar için tanımlanan ek yöntemlerin veya özelliklerden hiçbirini kullanamaz.  
  
 Bir taban sınıfın tüm üyeleri türetilmiş sınıflar için kullanılabilir, ancak türetilmiş bir sınıfın ek üyeleri temel sınıf için kullanılamaz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nesne Değişkenleri](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Nesne Değişkeni Ataması](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [Nesne Değişkeni Değerleri](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [Nasıl yapılır: Visual Basic içinde bir nesne değişkeni bildirme ve bir nesne atama](../../../../visual-basic/programming-guide/language-features/variables/how-to-declare-an-object-variable-and-assign-an-object-to-it.md)
- [Nasıl yapılır: Bir Nesnenin Üyelerine Erişme](../../../../visual-basic/programming-guide/language-features/variables/how-to-access-members-of-an-object.md)
- [New İşleci](../../../../visual-basic/language-reference/operators/new-operator.md)
- [Option Strict Deyimi](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [Yerel Çıkarım](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
