---
title: Sayısal ve Karşılaştırma İşleçleri
ms.date: 03/30/2017
ms.assetid: 25b4a26a-06f2-4f80-87a9-76705ed46197
ms.openlocfilehash: 7e7af725864aa191f092055fa32b403093321aa5
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781289"
---
# <a name="numeric-and-comparison-operators"></a>Sayısal ve Karşılaştırma İşleçleri

Aritmetik ve karşılaştırma işleçleri, ortak dil çalışma zamanında (CLR) beklenen şekilde aşağıdaki gibi çalışır:

- SQL, kayan nokta numaralarında mod işlecini desteklemez.

- SQL Denetlenmemiş aritmetiğini desteklemez.

- Artırma ve azaltma işleçleri, SQL 'de çoğaltılabilen ve bu nedenle desteklenmeyen ifadelerde kullandığınızda yan etkilere neden olur.

## <a name="supported-operators"></a>Desteklenen Işleçler

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]aşağıdaki işleçleri destekler.

- Temel aritmetik işleçler:

  - `+`

  - `-`strA

  - `*`

  - `/`

  - Visual Basic tamsayı bölümü (`\`)

  - `%`(Visual Basic `Mod`)

  - `<<`

  - `>>`

  - `-`(birli olumsuzlama)

- Temel karşılaştırma işleçleri:

  - Visual Basic `=` ve C#`==`

  - Visual Basic `<>` ve C#`!=`

  - Visual Basic`Is/IsNot`

  - `<`

  - `<=`

  - `>`

  - `>=`

## <a name="see-also"></a>Ayrıca bkz.

- [Veri Türleri ve İşlevleri](data-types-and-functions.md)
- [C# İşleçleri](../../../../../csharp/language-reference/operators/index.md)
- [İşleçler](../../../../../visual-basic/language-reference/operators/index.md)
