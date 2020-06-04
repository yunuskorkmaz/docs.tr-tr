---
title: "Nasıl yapılır: Visual Basic'te Bir Nesne Değişkeni Bildirme ve bir Nesne Atama"
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], declaring
- declaring object variables [Visual Basic]
ms.assetid: 2fa77dde-1fb2-439a-80d4-3e9787649fad
ms.openlocfilehash: d9a8c1fb30bfa5988d48202e41202e7ede0f5f27
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410509"
---
# <a name="how-to-declare-an-object-variable-and-assign-an-object-to-it-in-visual-basic"></a>Nasıl yapılır: Visual Basic'de Bir Nesne Değişkeni Bildirme ve bir Nesne Atama

Bir Dim Ifadesinde belirterek [nesne veri türünde](../../../language-reference/data-types/object-data-type.md) bir değişken bildirirsiniz `As Object` [Dim Statement](../../../language-reference/statements/dim-statement.md). Bir `=` atama deyimi veya başlatma yan tümcesindeki eşittir işaretinden () sonra nesneyi yerleştirerek bu tür bir değişkene bir nesne atarsınız.

## <a name="example"></a>Örnek

Aşağıdaki örnek bir değişken bildirir `Object` ve geçerli örneği buna atar.

```vb
Dim thisObject As Object
thisObject = "This is an Object"
```

Bildirimi ve atamayı, bildiriminin parçası olarak değişkeni başlatarak birleştirebilirsiniz. Aşağıdaki örnek, önceki örneğe eşdeğerdir.

```vb
Dim thisObject As Object= "This is an Object"
```

## <a name="compile-the-code"></a>Kodu derle

Bu örnek şunları gerektirir:

- <xref:System>Ad alanına başvuru.

- İfadeye yerleştirilecek bir sınıf, yapı veya modül `Dim` .

- Atama ekstresini koyabileceğiniz bir yordam.

## <a name="see-also"></a>Ayrıca bkz.

- [Değişken Bildirimi](variable-declaration.md)
- [Nesne Değişkenleri](object-variables.md)
- [Nesne Değişken Bildirimi](object-variable-declaration.md)
- [Nesne Veri Türü](../../../language-reference/data-types/object-data-type.md)
- [Dim Deyimi](../../../language-reference/statements/dim-statement.md)
- [Yerel Tür Arabirimi](local-type-inference.md)
- [Option Strict Deyimi](../../../language-reference/statements/option-strict-statement.md)
