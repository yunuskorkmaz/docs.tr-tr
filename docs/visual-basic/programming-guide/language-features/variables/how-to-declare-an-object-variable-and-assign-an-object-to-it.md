---
title: 'Nasıl yapılır: Bir nesne değişkeni bildirin ve Visual Basic bir nesne atayın'
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], declaring
- declaring object variables [Visual Basic]
ms.assetid: 2fa77dde-1fb2-439a-80d4-3e9787649fad
ms.openlocfilehash: 71949d50b01d7f252a988e86ca259261086d3b3b
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630877"
---
# <a name="how-to-declare-an-object-variable-and-assign-an-object-to-it-in-visual-basic"></a>Nasıl yapılır: Bir nesne değişkeni bildirin ve Visual Basic bir nesne atayın

Bir [Dim ifadesinde](../../../../visual-basic/language-reference/statements/dim-statement.md)belirterek `As Object` [nesne veri türünde](../../../../visual-basic/language-reference/data-types/object-data-type.md) bir değişken bildirirsiniz. Bir atama deyimi veya başlatma yan tümcesindeki eşittir işaretinden (`=`) sonra nesneyi yerleştirerek bu tür bir değişkene bir nesne atarsınız.

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

## <a name="compiling-the-code"></a>Kod Derleniyor

Bu örnek şunları gerektirir:

- <xref:System> Ad alanına başvuru.

- `Dim` İfadeye yerleştirilecek bir sınıf, yapı veya modül.

- Atama ekstresini koyabileceğiniz bir yordam.

## <a name="see-also"></a>Ayrıca bkz.

- [Değişken Bildirimi](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [Nesne Değişkenleri](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Nesne Değişken Bildirimi](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [Object Veri Türü](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [Dim Deyimi](../../../../visual-basic/language-reference/statements/dim-statement.md)
- [Yerel Çıkarım](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Option Strict Deyimi](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
