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
ms.openlocfilehash: 3ca322da4e5f0edcbe12bf29bded863daabffe3d
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90867694"
---
# <a name="readonly-visual-basic"></a>ReadOnly (Visual Basic)

Bir değişkenin veya özelliğin okunup yazılamayacağını belirtir.

## <a name="remarks"></a>Açıklamalar

## <a name="rules"></a>Kurallar

- **Bildirim bağlamı.** `ReadOnly`Yalnızca modül düzeyinde kullanabilirsiniz. Diğer bir deyişle, bir öğe için bildirim bağlamı `ReadOnly` bir sınıf, yapı veya modül olmalıdır ve kaynak dosya, ad alanı veya yordam olamaz.

- **Birleşik değiştiriciler.** `ReadOnly`Aynı bildirimde ile birlikte belirtemezsiniz `Static` .

- **Değer atama.** Bir özelliği kullanan kod `ReadOnly` , değerini ayarlayamadı. Ancak, temel alınan depolamaya erişimi olan kod herhangi bir zamanda değeri atayabilir veya değiştirebilir.

     Bir `ReadOnly` değişkene yalnızca bildiriminde veya tanımlandığı bir sınıf veya yapının oluşturucusunda bir değer atayabilirsiniz.

## <a name="when-to-use-a-readonly-variable"></a>Salt okunur değişken ne zaman kullanılır?

Sabit bir değer bildirmek ve atamak için [const bildirimini](../statements/const-statement.md) kullanamadığınız durumlar vardır. Örneğin, `Const` deyimi atamak istediğiniz veri türünü kabul etmeyebilir veya bir sabit ifadeyle derleme zamanında değeri hesaplamayabilir. Derleme zamanında değeri bile bilmiyor olabilirsiniz. Bu durumlarda, `ReadOnly` sabit bir değeri tutmak için bir değişken kullanabilirsiniz.

> [!IMPORTANT]
> Değişkenin veri türü bir dizi veya sınıf örneği gibi bir başvuru türü ise, bu değişkenin kendisi olsa bile üyeleri değiştirilebilir `ReadOnly` . Aşağıdaki örnek bunu göstermektedir.

```vb
ReadOnly characterArray() As Char = {"x"c, "y"c, "z"c}
Sub ChangeArrayElement()
    characterArray(1) = "M"c
End Sub
```

Başlatıldığında, tarafından işaret edilen dizi `characterArray()` "x", "y" ve "z" barındırır. Değişken olduğundan `characterArray` `ReadOnly` , değeri başlatıldıktan sonra değiştiremezsiniz; diğer bir deyişle, buna yeni bir dizi atayamazsınız. Ancak, bir veya daha fazla dizi üyesinin değerlerini değiştirebilirsiniz. Yordama yapılan bir çağrıdan `ChangeArrayElement` sonra, işaret eden dizi `characterArray()` "x", "e" ve "z" barındırır.

Bunun, yordamın, çağıran bağımsız değişkenin kendisini değiştirmesini engelleyen bir yordam parametresi olarak bildirilmesinin benzer olduğuna, ancak onun üyelerini değiştirmesine izin verdiğinden [emin olun.](byval.md)

## <a name="example"></a>Örnek

Aşağıdaki örnek, bir `ReadOnly` çalışanın işe alındığı tarih için bir özelliği tanımlar. Sınıfı, özellik değerini dahili olarak bir değişken olarak depolar `Private` ve yalnızca sınıfın içindeki kod bu değeri değiştirebilir. Ancak, özelliği olur `Public` ve sınıfa erişebilen tüm kodlar özelliği okuyabilir.

[!code-vb[VbVbalrKeywords#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#4)]

`ReadOnly`Değiştirici şu bağlamlarda kullanılabilir:

- [Dim Deyimi](../statements/dim-statement.md)
- [Property Deyimi](../statements/property-statement.md)

## <a name="see-also"></a>Ayrıca bkz.

- [WriteOnly](writeonly.md)
- [Anahtar sözcükler](../keywords/index.md)
