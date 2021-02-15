---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: bir değişkende birden fazla değer tutma (Visual Basic)'
title: 'Nasıl yapılır: Değişkende Birden Fazla Değer Tutma'
ms.date: 07/20/2015
helpviewer_keywords:
- classes [Visual Basic], composite data types
- composite types [Visual Basic]
- composite data types [Visual Basic]
- data types [Visual Basic], composite
- arrays [Visual Basic], composite data types
- structures [Visual Basic], composite data types
- arrays [Visual Basic], compilation errors
- types [Visual Basic], composite
ms.assetid: 5fe0e558-aac2-4a40-b7f2-7cfea7336917
ms.openlocfilehash: 5248bc29f58cccf3b8ced95d3fba8f0d39033a83
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100484008"
---
# <a name="how-to-hold-more-than-one-value-in-a-variable-visual-basic"></a>Nasıl yapılır: Değişkende Birden Fazla Değer Tutma (Visual Basic)

Bir değişken, *bileşik veri türünde* olduğunu bildirirseniz birden fazla değeri tutar.

[Bileşik veri türleri](composite-data-types.md) yapılar, diziler ve sınıflar içerir. Bileşik veri türünün bir değişkeni, Öğesel veri türlerinin ve diğer bileşik türlerin bir birleşimini tutabilir. Yapılar ve sınıflar, kodu ve verileri içerebilir.

## <a name="to-hold-more-than-one-value-in-a-variable"></a>Bir değişkende birden fazla değeri tutmak için

1. Değişkeniniz için kullanmak istediğiniz bileşik veri türünü saptayın.

2. Bileşik veri türü önceden tanımlanmamışsa, değişkeninizin onu kullanabilmesi için onu tanımlayın.

    - [Structure ifadesiyle](../../../language-reference/statements/structure-statement.md)bir yapı tanımlayın.

    - [Dim ifadesiyle](../../../language-reference/statements/dim-statement.md)bir dizi tanımlayın.

    - [Sınıf ifadesiyle](../../../language-reference/statements/class-statement.md)bir sınıf tanımlayın.

3. Değişkeninizi bir ifadesiyle bildirin `Dim` .

4. Bir yan tümcesiyle değişken adını izleyin `As` .

5. `As`Uygun bileşik veri türünün adı ile anahtar sözcüğünü izleyin.

## <a name="see-also"></a>Ayrıca bkz.

- [Veri türleri](../../../language-reference/data-types/index.md)
- [Tür Karakterleri](type-characters.md)
- [Bileşik Veri Türleri](composite-data-types.md)
- [Yapılar](structures.md)
- [Diziler](../arrays/index.md)
- [Nesneler ve sınıflar](../objects-and-classes/index.md)
- [Değer türleri ve başvuru türleri](value-types-and-reference-types.md)
