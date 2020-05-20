---
title: Genelleştirme son değişiklikleri
description: .NET Core 'da Genelleştirme 'deki son değişiklikleri listeler.
ms.date: 04/07/2020
ms.openlocfilehash: 0c3367cb3515c6f473f53be6062b54f2e836b8c5
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83702318"
---
# <a name="globalization-breaking-changes"></a>Genelleştirme son değişiklikleri

Aşağıdaki son değişiklikler bu sayfada belgelenmiştir:

| Son değişiklik | Sunulan sürüm |
| - | :-: |
| [Genelleştirme API 'Leri Windows üzerinde ıCU kitaplıklarını kullanır](#globalization-apis-use-icu-libraries-on-windows) | 5.0 |
| [StringInfo ve TextElementEnumerator artık UAX29 uyumlu](#stringinfo-and-textelementenumerator-are-now-uax29-compliant) | 5.0 |
| ["C" yerel ayarı, sabit yerel ayara eşlenir](#c-locale-maps-to-the-invariant-locale) | 3.0 |

## <a name="net-50"></a>.NET 5,0

[!INCLUDE [icu-globalization-api](../../../includes/core-changes/globalization/5.0/icu-globalization-api.md)]

***

[!INCLUDE [uax29-compliant-grapheme-enumeration](../../../includes/core-changes/globalization/5.0/uax29-compliant-grapheme-enumeration.md)]

***

## <a name="net-core-30"></a>.NET Core 3.0

[!INCLUDE["C" locale maps to the invariant locale](~/includes/core-changes/globalization/3.0/c-locale-maps-to-invariant-locale.md)]

***
