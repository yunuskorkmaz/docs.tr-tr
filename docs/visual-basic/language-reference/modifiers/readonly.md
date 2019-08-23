---
title: ReadOnly (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.ReadOnly
helpviewer_keywords:
- ReadOnly keyword [Visual Basic]
- variables [Visual Basic], read-only
- ReadOnly property
- properties [Visual Basic], read-only
- read-only variables
ms.assetid: e868185d-6142-4359-a2fd-a7965cadfce8
ms.openlocfilehash: 01c441576cb4247933c053f2043296733f99fdeb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965416"
---
# <a name="readonly-visual-basic"></a>ReadOnly (Visual Basic)
Bir değişkenin veya özelliğin okunup yazılamayacağını belirtir.  
  
## <a name="remarks"></a>Açıklamalar  
  
## <a name="rules"></a>Kurallar  
  
- **Bildirim bağlamı.** Yalnızca modül düzeyinde `ReadOnly` kullanabilirsiniz. Diğer bir deyişle, bir `ReadOnly` öğe için bildirim bağlamı bir sınıf, yapı veya modül olmalıdır ve kaynak dosya, ad alanı veya yordam olamaz.  
  
- **Birleşik değiştiriciler.** Aynı bildirimde ile `ReadOnly` `Static` birlikte belirtemezsiniz.  
  
- **Değer atama.** Bir `ReadOnly` özelliği kullanan kod, değerini ayarlayamadı. Ancak, temel alınan depolamaya erişimi olan kod herhangi bir zamanda değeri atayabilir veya değiştirebilir.  
  
     Bir `ReadOnly` değişkene yalnızca bildiriminde veya tanımlandığı bir sınıf veya yapının oluşturucusunda bir değer atayabilirsiniz.  
  
## <a name="when-to-use-a-readonly-variable"></a>Salt okunur değişken ne zaman kullanılır?  
 Sabit bir değer bildirmek ve atamak için [const bildirimini](../../../visual-basic/language-reference/statements/const-statement.md) kullanamadığınız durumlar vardır. Örneğin, `Const` deyimi atamak istediğiniz veri türünü kabul etmeyebilir veya bir sabit ifadeyle derleme zamanında değeri hesaplamayabilir. Derleme zamanında değeri bile bilmiyor olabilirsiniz. Bu durumlarda, sabit bir değeri tutmak için `ReadOnly` bir değişken kullanabilirsiniz.  
  
> [!IMPORTANT]
> Değişkenin veri türü bir dizi veya sınıf örneği gibi bir başvuru türü ise, bu değişkenin kendisi `ReadOnly`olsa bile üyeleri değiştirilebilir. Aşağıdaki örnek bunu göstermektedir.  
  
 `ReadOnly characterArray() As Char = {"x"c, "y"c, "z"c}`  
  
 `Sub changeArrayElement()`  
  
 `characterArray(1) = "M"c`  
  
 `End Sub`  
  
 Başlatıldığında, tarafından `characterArray()` işaret edilen dizi "x", "y" ve "z" barındırır. `characterArray` Değişken`ReadOnly`olduğundan, değeri başlatıldıktan sonra değiştiremezsiniz; diğer bir deyişle, buna yeni bir dizi atayamazsınız. Ancak, bir veya daha fazla dizi üyesinin değerlerini değiştirebilirsiniz. Yordama `changeArrayElement`yapılan bir çağrıdan sonra, işaret eden `characterArray()` dizi "x", "e" ve "z" barındırır.  
  
 Bunun, yordamın, çağıran bağımsız değişkenin kendisini değiştirmesini engelleyen bir yordam [](../../../visual-basic/language-reference/modifiers/byval.md)parametresi olarak bildirilmesinin benzer olduğuna, ancak onun üyelerini değiştirmesine izin verdiğinden emin olun.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir çalışanın `ReadOnly` işe alındığı tarih için bir özelliği tanımlar. Sınıfı, özellik değerini dahili olarak bir `Private` değişken olarak depolar ve yalnızca sınıfın içindeki kod bu değeri değiştirebilir. Ancak, özelliği olur `Public`ve sınıfa erişebilen tüm kodlar özelliği okuyabilir.  
  
 [!code-vb[VbVbalrKeywords#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#4)]  
  
 `ReadOnly` Değiştirici şu bağlamlarda kullanılabilir:  
  
 [Dim Deyimi](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Property Deyimi](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WriteOnly](../../../visual-basic/language-reference/modifiers/writeonly.md)
- [Anahtar Sözcükler](../../../visual-basic/language-reference/keywords/index.md)
