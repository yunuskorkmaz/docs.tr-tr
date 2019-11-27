---
title: ReadOnly
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
ms.openlocfilehash: 8c7e7e7c1571fd7c595ebfd54fb5767078ef41f8
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351273"
---
# <a name="readonly-visual-basic"></a>ReadOnly (Visual Basic)
Bir değişkenin veya özelliğin okunup yazılamayacağını belirtir.

## <a name="remarks"></a>Açıklamalar

## <a name="rules"></a>Kurallar

- **Bildirim bağlamı.** Yalnızca modül düzeyinde `ReadOnly` kullanabilirsiniz. Bu, bir `ReadOnly` öğesi için bildirim bağlamının bir sınıf, yapı veya modül olması ve kaynak dosya, ad alanı veya yordam olması gerektiği anlamına gelir.

- **Birleşik değiştiriciler.** Aynı bildirimde `Static` birlikte `ReadOnly` belirtemezsiniz.

- **Değer atama.** `ReadOnly` bir özelliği kullanan kod, değerini ayarlayamadı. Ancak, temel alınan depolamaya erişimi olan kod herhangi bir zamanda değeri atayabilir veya değiştirebilir.

     Bir `ReadOnly` değişkenine bir değeri yalnızca bildiriminde veya tanımlandığı bir sınıfın veya yapının oluşturucusunda atayabilirsiniz.

## <a name="when-to-use-a-readonly-variable"></a>Salt okunur değişken ne zaman kullanılır?

Sabit bir değer bildirmek ve atamak için [const bildirimini](../../../visual-basic/language-reference/statements/const-statement.md) kullanamadığınız durumlar vardır. Örneğin, `Const` deyimi atamak istediğiniz veri türünü kabul etmeyebilir veya bir sabit ifadeyle derleme zamanında değeri hesaplamayabilir. Derleme zamanında değeri bile bilmiyor olabilirsiniz. Bu durumlarda, sabit bir değeri tutmak için bir `ReadOnly` değişkeni kullanabilirsiniz.

> [!IMPORTANT]
> Değişkenin veri türü bir dizi veya sınıf örneği gibi bir başvuru türü ise, değişkenin kendisi `ReadOnly`olsa bile üyeleri değiştirilebilir. Aşağıdaki örnek bunu göstermektedir.

```vb
ReadOnly characterArray() As Char = {"x"c, "y"c, "z"c}
Sub ChangeArrayElement()
    characterArray(1) = "M"c
End Sub
```

Başlatıldığında, `characterArray()` tarafından işaret edilen dizi "x", "y" ve "z" ' i barındırır. `characterArray` değişken `ReadOnly`olduğundan, değerini başlatıldıktan sonra değiştiremezsiniz; diğer bir deyişle, buna yeni bir dizi atayamazsınız. Ancak, bir veya daha fazla dizi üyesinin değerlerini değiştirebilirsiniz. Yordam `ChangeArrayElement`çağrısı sonrasında, `characterArray()` tarafından işaret edilen dizi "x", "e" ve "z" karakterlerini tutar.

Bunun, yordamın, çağıran bağımsız değişkenin kendisini değiştirmesini engelleyen bir yordam parametresi olarak bildirilmesinin benzer olduğuna, ancak onun üyelerini değiştirmesine izin verdiğinden [emin olun.](byval.md)

## <a name="example"></a>Örnek

Aşağıdaki örnek, bir çalışanın işe alındığı tarih için bir `ReadOnly` özelliğini tanımlar. Sınıfı, özellik değerini dahili olarak bir `Private` değişkeni olarak depolar ve yalnızca sınıfın içindeki kod bu değeri değiştirebilir. Ancak, özelliği `Public`ve sınıfa erişebilen tüm kodlar özelliği okuyabilir.

[!code-vb[VbVbalrKeywords#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#4)]

`ReadOnly` değiştiricisi şu bağlamlarda kullanılabilir:

- [Dim Deyimi](../statements/dim-statement.md)
- [Property Deyimi](../statements/property-statement.md)

## <a name="see-also"></a>Ayrıca bkz.

- [WriteOnly](writeonly.md)
- [Anahtar Sözcükler](../keywords/index.md)
