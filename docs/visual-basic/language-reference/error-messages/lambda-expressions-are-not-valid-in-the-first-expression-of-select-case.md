---
description: "Hakkında daha fazla bilgi edinin: BC36635: lambda ifadeleri bir ' Select Case ' deyiminin ilk ifadesinde geçerli değildir"
title: Bir 'Select Case' deyiminin ilk ifadesinde lambda ifadeleri geçerli değildir
ms.date: 07/20/2015
f1_keywords:
- bc36635
- vbc36635
helpviewer_keywords:
- BC36635
ms.assetid: 74609979-9c03-4864-bbce-f588aa2e0917
ms.openlocfilehash: e0c388db7164f6c9f99ba917109593a796f7b23b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795943"
---
# <a name="bc36635-lambda-expressions-are-not-valid-in-the-first-expression-of-a-select-case-statement"></a>BC36635: lambda ifadeleri bir ' Select Case ' deyiminin ilk ifadesinde geçerli değildir

Bir deyimde test ifadesi için lambda ifadesi kullanamazsınız `Select Case` . Lambda ifade tanımları dönüş işlevleri ve bir deyimin test ifadesi bir `Select Case` Öğesel veri türü olmalıdır.

 Aşağıdaki kod bu hataya neden olur:

```vb
' Select Case (Function(arg) arg Is Nothing)
    ' List of the cases.
' End Select
```

 **Hata kimliği:** BC36635

## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

- Bir bildirim gibi farklı bir koşullu oluşturma sizin için çalışıp çalışmadığını anlamak için kodunuzu inceleyin `If...Then...Else` .

- Aşağıdaki kodda gösterildiği gibi, işlevini çağırmanız istenebilir:

```vb
Dim num? As Integer
Select Case ((Function(arg? As Integer) arg Is Nothing)(num))
    ' List of the cases
End Select
```

## <a name="see-also"></a>Ayrıca bkz.

- [Lambda Ifadeleri](../../programming-guide/language-features/procedures/lambda-expressions.md)
- [If...Then...Else Deyimi](../statements/if-then-else-statement.md)
- [Select...Case Deyimi](../statements/select-case-statement.md)
