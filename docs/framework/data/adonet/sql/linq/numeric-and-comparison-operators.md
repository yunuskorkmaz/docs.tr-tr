---
description: 'Daha fazla bilgi edinin: sayısal ve karşılaştırma Işleçleri'
title: Sayısal ve Karşılaştırma İşleçleri
ms.date: 03/30/2017
ms.assetid: 25b4a26a-06f2-4f80-87a9-76705ed46197
ms.openlocfilehash: 5b17f19769436ac4e575ac974668eadc3b17b8f6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99695534"
---
# <a name="numeric-and-comparison-operators"></a>Sayısal ve Karşılaştırma İşleçleri

Aritmetik ve karşılaştırma işleçleri, ortak dil çalışma zamanında (CLR) beklenen şekilde aşağıdaki gibi çalışır:

- SQL, kayan nokta numaralarında mod işlecini desteklemez.

- SQL Denetlenmemiş aritmetiğini desteklemez.

- Artırma ve azaltma işleçleri, SQL 'de çoğaltılabilen ve bu nedenle desteklenmeyen ifadelerde kullandığınızda yan etkilere neden olur.

## <a name="supported-operators"></a>Desteklenen Işleçler

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] aşağıdaki işleçleri destekler.

- Temel aritmetik işleçler:

  - `+`

  - `-` strA

  - `*`

  - `/`

  - Visual Basic tamsayı bölümü ( `\` )

  - `%` (Visual Basic `Mod` )

  - `<<`

  - `>>`

  - `-` (birli olumsuzlama)

- Temel karşılaştırma işleçleri:

  - Visual Basic `=` ve C # `==`

  - Visual Basic `<>` ve C # `!=`

  - Visual Basic `Is/IsNot`

  - `<`

  - `<=`

  - `>`

  - `>=`

## <a name="see-also"></a>Ayrıca bkz.

- [Veri Türleri ve İşlevleri](data-types-and-functions.md)
- [C# işleçleri](../../../../../csharp/language-reference/operators/index.md)
- [İşleçler](../../../../../visual-basic/language-reference/operators/index.md)
