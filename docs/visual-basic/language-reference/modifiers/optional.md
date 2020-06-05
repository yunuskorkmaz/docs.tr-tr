---
title: İsteğe Bağlı
ms.date: 07/20/2015
f1_keywords:
- vb.Optional
- vb.optional
helpviewer_keywords:
- Optional keyword [Visual Basic], contexts
- Optional keyword [Visual Basic]
ms.assetid: 4571ce88-a539-4115-b230-54eb277c6aa7
ms.openlocfilehash: c46d06dba61158d7362d736731161be306af3f10
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84392151"
---
# <a name="optional-visual-basic"></a>İsteğe Bağlı (Visual Basic)

Yordam çağrıldığında bir yordam bağımsız değişkeninin atlanabileceğini belirtir.

## <a name="remarks"></a>Açıklamalar

Her isteğe bağlı parametre için, bu parametrenin varsayılan değeri olarak bir sabit ifade belirtmeniz gerekir. İfade [Nothing](../nothing.md)olarak değerlendirilirse, değer veri türünün varsayılan değeri parametrenin varsayılan değeri olarak kullanılır.

Parametre listesi isteğe bağlı bir parametre içeriyorsa, izleyen her parametrenin de isteğe bağlı olması gerekir.

`Optional`Değiştirici şu bağlamlarda kullanılabilir:

- [Declare Deyimi](../statements/declare-statement.md)

- [Function Deyimi](../statements/function-statement.md)

- [Property Deyimi](../statements/property-statement.md)

- [Sub Deyimi](../statements/sub-statement.md)

> [!NOTE]
> İsteğe bağlı parametreleri olan veya içermeyen bir yordamı çağırırken bağımsız değişkenleri konuma veya ada göre geçirebilirsiniz. Daha fazla bilgi için bkz. [bağımsız değişkenleri konuma ve ada göre geçirme](../../programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md).

> [!NOTE]
> Ayrıca, aşırı yükleme kullanarak isteğe bağlı parametrelerle bir yordam tanımlayabilirsiniz. İsteğe bağlı bir parametreye sahipseniz, yordamın parametresini kabul eden bir tane olan biri olan iki aşırı yüklenmiş sürümü tanımlayabilirsiniz. Daha fazla bilgi için bkz. [yordam aşırı yüklemesi](../../programming-guide/language-features/procedures/procedure-overloading.md).

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

- [Parametre Listesi](../statements/parameter-list.md)
- [İsteğe Bağlı Parametreler](../../programming-guide/language-features/procedures/optional-parameters.md)
- [Anahtar sözcükler](../keywords/index.md)
