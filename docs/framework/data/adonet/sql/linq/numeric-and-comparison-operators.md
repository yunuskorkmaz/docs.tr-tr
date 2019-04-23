---
title: Sayısal ve Karşılaştırma İşleçleri
ms.date: 03/30/2017
ms.assetid: 25b4a26a-06f2-4f80-87a9-76705ed46197
ms.openlocfilehash: b29f78a13d6d0313e0ad29754f6d13ac08be1092
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59973349"
---
# <a name="numeric-and-comparison-operators"></a>Sayısal ve Karşılaştırma İşleçleri

Aritmetik ve Karşılaştırma işleçleri dışında ortak dil çalışma zamanı (CLR) gibi beklendiği gibi çalışmayabilir:

- SQL, kayan nokta numaralarını modulus işleci desteklemez.

- SQL denetlenmeyen aritmetiğini desteklemez.

- SQL'de çoğaltılır ve bu nedenle, desteklenmiyor ifadelerde kullandığınızda artırma ve azaltma işleçleri yan etkilere neden.

## <a name="supported-operators"></a>Desteklenen işleçleri

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Aşağıdaki işleçleri destekler.

- Temel aritmetik işleçler:

  - `+`

  - `-` (çıkarma)

  - `*`

  - `/`

  - Visual Basic tamsayı bölme (`\`)

  - `%` (Visual Basic `Mod`)

  - `<<`

  - `>>`

  - `-` (birli olumsuzlama)

- Temel Karşılaştırma işleçleri:

  - Visual Basic `=` ve C# `==`

  - Visual Basic `<>` ve C# `!=`

  - Visual Basic `Is/IsNot`

  - `<`

  - `<=`

  - `>`

  - `>=`

## <a name="see-also"></a>Ayrıca bkz.

- [Veri Türleri ve İşlevleri](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
- [C# İşleçleri](../../../../../../docs/csharp/language-reference/operators/index.md)
- [İşleçler](../../../../../visual-basic/language-reference/operators/index.md)
