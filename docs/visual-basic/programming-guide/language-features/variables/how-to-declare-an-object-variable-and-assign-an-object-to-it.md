---
title: 'Nasıl yapılır: bir nesne değişkeni bildirme ve ona bir nesne atama'
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], declaring
- declaring object variables [Visual Basic]
ms.assetid: 2fa77dde-1fb2-439a-80d4-3e9787649fad
ms.openlocfilehash: 4cfad1d820b584d4610d24c392b14ac3958471b7
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352899"
---
# <a name="how-to-declare-an-object-variable-and-assign-an-object-to-it-in-visual-basic"></a>Nasıl yapılır: Visual Basic'de Bir Nesne Değişkeni Bildirme ve bir Nesne Atama

Bir [Dim ifadesinde](../../../../visual-basic/language-reference/statements/dim-statement.md)`As Object` belirterek [nesne veri türünde](../../../../visual-basic/language-reference/data-types/object-data-type.md) bir değişken bildirirsiniz. Bir atama deyimi veya başlatma yan tümcesindeki eşittir işaretinden (`=`) sonra nesneyi yerleştirerek bu tür bir değişkene bir nesne atarsınız.

## <a name="example"></a>Örnek

Aşağıdaki örnek bir `Object` değişken bildirir ve geçerli örneği buna atar.

```vb
Dim thisObject As Object
thisObject = "This is an Object"
```

Bildirimi ve atamayı, bildiriminin parçası olarak değişkeni başlatarak birleştirebilirsiniz. Aşağıdaki örnek, önceki örneğe eşdeğerdir.

```vb
Dim thisObject As Object= "This is an Object"
```

## <a name="compiling-the-code"></a>Kod Derleme

Bu örnek şunları gerektirir:

- <xref:System> ad alanına bir başvuru.

- `Dim` deyimin konulacağı bir sınıf, yapı veya modül.

- Atama ekstresini koyabileceğiniz bir yordam.

## <a name="see-also"></a>Ayrıca bkz.

- [Değişken Bildirimi](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [Nesne Değişkenleri](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Nesne Değişken Bildirimi](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [Object Veri Türü](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [Dim Deyimi](../../../../visual-basic/language-reference/statements/dim-statement.md)
- [Yerel Çıkarım](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Option Strict Deyimi](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
