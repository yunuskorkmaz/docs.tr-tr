---
title: İsteğe Bağlı (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Optional
- vb.optional
helpviewer_keywords:
- Optional keyword [Visual Basic], contexts
- Optional keyword [Visual Basic]
ms.assetid: 4571ce88-a539-4115-b230-54eb277c6aa7
ms.openlocfilehash: 3758f17634395236abf2cd7059418bf6f8b6c062
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630925"
---
# <a name="optional-visual-basic"></a>İsteğe Bağlı (Visual Basic)

Yordam çağrıldığında bir yordam bağımsız değişkeninin atlanabileceğini belirtir.

## <a name="remarks"></a>Açıklamalar

Her isteğe bağlı parametre için, bu parametrenin varsayılan değeri olarak bir sabit ifade belirtmeniz gerekir. İfade [Nothing](../../../visual-basic/language-reference/nothing.md)olarak değerlendirilirse, değer veri türünün varsayılan değeri parametrenin varsayılan değeri olarak kullanılır.

Parametre listesi isteğe bağlı bir parametre içeriyorsa, izleyen her parametrenin de isteğe bağlı olması gerekir.

`Optional` Değiştirici şu bağlamlarda kullanılabilir:

- [Declare Deyimi](../../../visual-basic/language-reference/statements/declare-statement.md)

- [Function Deyimi](../../../visual-basic/language-reference/statements/function-statement.md)

- [Property Deyimi](../../../visual-basic/language-reference/statements/property-statement.md)

- [Sub Deyimi](../../../visual-basic/language-reference/statements/sub-statement.md)

> [!NOTE]
> İsteğe bağlı parametreleri olan veya içermeyen bir yordamı çağırırken bağımsız değişkenleri konuma veya ada göre geçirebilirsiniz. Daha fazla bilgi için bkz. [bağımsız değişkenleri konuma ve ada göre geçirme](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md).

> [!NOTE]
> Ayrıca, aşırı yükleme kullanarak isteğe bağlı parametrelerle bir yordam tanımlayabilirsiniz. İsteğe bağlı bir parametreye sahipseniz, yordamın parametresini kabul eden bir tane olan biri olan iki aşırı yüklenmiş sürümü tanımlayabilirsiniz. Daha fazla bilgi için bkz. [yordam aşırı yüklemesi](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md).

## <a name="example"></a>Örnek

Aşağıdaki örnek, isteğe bağlı parametresine sahip bir yordamı tanımlar.

```vb
Public Function FindMatches(ByRef values As List(Of String),
                            ByVal searchString As String,
                            Optional ByVal matchCase As Boolean = False) As List(Of String)

    Dim results As IEnumerable(Of String)

    If matchCase Then
        results = From v In values
                  Where v.Contains(searchString)
    Else
        results = From v In values
                  Where UCase(v).Contains(UCase(searchString))
    End If

    Return results.ToList()
End Function
```

## <a name="example"></a>Örnek

Aşağıdaki örnek, konumundan geçirilen bağımsız değişkenlerle ve ad ile geçirilen bağımsız değişkenlerle bir yordamın nasıl çağrılacağını gösterir. Yordamda iki isteğe bağlı parametre vardır.

[!code-vb[VbVbalrKeywords#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/class8.vb#21)]

## <a name="see-also"></a>Ayrıca bkz.

- [Parametre Listesi](../../../visual-basic/language-reference/statements/parameter-list.md)
- [İsteğe Bağlı Parametreler](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)
- [Anahtar Sözcükler](../../../visual-basic/language-reference/keywords/index.md)
