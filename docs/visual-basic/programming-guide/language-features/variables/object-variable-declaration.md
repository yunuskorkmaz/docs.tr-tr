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
ms.openlocfilehash: b6de52cf738a56a42c82978b54cef31574ab0bcb
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410367"
---
# <a name="object-variable-declaration-visual-basic"></a>Nesne Değişken Bildirimi (Visual Basic)
Bir nesne değişkeni bildirmek için normal bir bildirim bildirimi kullanın. Veri türü için, `Object` (yani, [nesne veri türü](../../../language-reference/data-types/object-data-type.md)) ya da nesnenin oluşturulacağı daha belirli bir sınıf belirtirsiniz.  
  
 Bir değişkeni olarak bildirme `Object` ile aynı şekilde bildirme <xref:System.Object?displayProperty=nameWithType> .  
  
 Belirli bir nesne sınıfıyla bir değişken bildirdiğinizde, bu sınıf ve devraldığı sınıflar tarafından sunulan tüm yöntemlere ve özelliklere erişebilir. Değişkenini ile bildirirseniz <xref:System.Object> , <xref:System.Object> `Option Strict Off` geç bağlamaya izin vermeyi yüklemediğiniz müddetçe yalnızca sınıfın üyelerine erişebilir.  
  
## <a name="declaration-syntax"></a>Bildirim Sözdizimi  
 Bir nesne değişkenini bildirmek için aşağıdaki sözdizimini kullanın:  
  
```vb  
Dim variablename As [New] { objectclass | Object }  
```  
  
 Bildirimde [ortak](../../../language-reference/modifiers/public.md), [korumalı](../../../language-reference/modifiers/protected.md), [arkadaş](../../../language-reference/modifiers/friend.md), `Protected Friend` , [özel](../../../language-reference/modifiers/private.md), [paylaşılan](../../../language-reference/modifiers/shared.md)veya [statik](../../../language-reference/modifiers/static.md) de belirtebilirsiniz. Aşağıdaki örnek bildirimler geçerlidir:  
  
```vb  
Private objA As Object  
Static objB As System.Windows.Forms.Label  
Dim objC As System.OperatingSystem  
```  
  
## <a name="late-binding-and-early-binding"></a>Geç bağlama ve erken bağlama  
 Bazen, kodunuz çalışana kadar belirli bir sınıf bilinmez. Bu durumda, nesne değişkenini `Object` veri türüyle bildirmeniz gerekir. Bu, herhangi bir nesne türüne genel bir başvuru oluşturur ve belirli bir sınıf çalışma zamanında atanır. Bu, *geç bağlama*olarak adlandırılır. Geç bağlama ek yürütme süresi gerektirir. Ayrıca, kodunuzu en son atadığınız sınıfın yöntemleriyle ve özellikleriyle da sınırlandırır. Bu, kodunuzun farklı bir sınıfın üyelerine erişmeye çalışırsa çalışma zamanı hatalarına neden olabilir.  
  
 Derleme zamanında belirli bir sınıfı bildiğinizde, nesne değişkenini bu sınıftan olacak şekilde bildirmeniz gerekir. Bu, *erken bağlama*olarak adlandırılır. Erken bağlama performansı iyileştirir ve kodun tüm yöntemlerine ve özelliklerine yönelik kod erişiminizi güvence altına alır. Önceki örnek bildirimlerinde, değişken `objA` yalnızca sınıfının nesnelerini kullanıyorsa <xref:System.Windows.Forms.Label?displayProperty=nameWithType> , bildiriminde belirtmeniz gerekir `As System.Windows.Forms.Label` .  
  
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
 `Option Strict`Açık olduğunda `On` , bir nesne değişkeni yalnızca, onu bildirdiğiniz sınıfın yöntemlerine ve özelliklerine erişebilir. Aşağıdaki örnek bunu göstermektedir.  
  
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
  
 Bu örnekte, `p` yalnızca <xref:System.Object> sınıfının kendisini, özelliğini içermeyen üyelerini kullanabilir `Left` . Diğer taraftan, türü olarak `q` bildirildi <xref:System.Windows.Forms.Label> , bu nedenle <xref:System.Windows.Forms.Label> ad alanındaki sınıfının tüm yöntemlerini ve özelliklerini kullanabilir <xref:System.Windows.Forms> .  
  
## <a name="flexibility-of-object-variables"></a>Nesne değişkenlerinin esnekliği  
 Devralma hiyerarşisinde nesnelerle çalışırken, nesne değişkenlerinizi bildirirken hangi sınıftan kullanacağınızı tercih edersiniz. Bu seçimi yaparken, bir sınıfın üyelerine erişim için nesne atamasının esnekliğini dengeetmeniz gerekir. Örneğin, sınıfına yol gösteren devralma hiyerarşisini göz önünde bulundurun <xref:System.Windows.Forms.Form?displayProperty=nameWithType> :  
  
 <xref:System.Object>  
  
 &nbsp;&nbsp;<xref:System.MarshalByRefObject>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;<xref:System.ComponentModel.Component>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.Control>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.ScrollableControl>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.ContainerControl>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.Form>  
  
 Uygulamanızın sınıfından devralan adlı bir form sınıfını tanımladığını varsayalım `specialForm` <xref:System.Windows.Forms.Form> . Aşağıdaki örnekte gösterildiği gibi, özellikle öğesine başvuran bir nesne değişkeni bildirebilirsiniz `specialForm` .  
  
```vb  
Public Class specialForm  
    Inherits System.Windows.Forms.Form  
    ' Insert code defining methods and properties of specialForm.  
End Class  
Dim nextForm As New specialForm  
```  
  
 Önceki örnekteki bildirim, değişkenini `nextForm` sınıfının nesneleriyle sınırlandırır `specialForm` , ancak aynı zamanda `specialForm` , devralınan tüm sınıfların tüm üyelerini ve bu özelliklerin tümünü de kullanılabilir hale getirir `nextForm` `specialForm` .  
  
 Aşağıdaki örnekte gösterildiği gibi, bir nesne değişkenini türünde olmasına bildirerek daha genel hale getirebilirsiniz <xref:System.Windows.Forms.Form> .  
  
```vb  
Dim anyForm As System.Windows.Forms.Form  
```  
  
 Yukarıdaki örnekteki bildirim, uygulamanızdaki herhangi bir formu uygulamasına atamanıza olanak tanır `anyForm` . Ancak, `anyForm` tüm sınıf üyelerine erişebilse de, gibi <xref:System.Windows.Forms.Form> belirli formlar için tanımlanan ek yöntemlerin veya özelliklerin hiçbirini kullanamaz `specialForm` .  
  
 Bir taban sınıfın tüm üyeleri türetilmiş sınıflar için kullanılabilir, ancak türetilmiş bir sınıfın ek üyeleri temel sınıf için kullanılamaz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nesne Değişkenleri](object-variables.md)
- [Nesne Değişkeni Ataması](object-variable-assignment.md)
- [Nesne Değişkeni Değerleri](object-variable-values.md)
- [Nasıl yapılır: Visual Basic'de Bir Nesne Değişkeni Bildirme ve bir Nesne Atama](how-to-declare-an-object-variable-and-assign-an-object-to-it.md)
- [Nasıl yapılır: Bir Nesnenin Üyelerine Erişme](how-to-access-members-of-an-object.md)
- [New Işleci](../../../language-reference/operators/new-operator.md)
- [Option Strict Deyimi](../../../language-reference/statements/option-strict-statement.md)
- [Yerel Tür Arabirimi](local-type-inference.md)
