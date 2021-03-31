---
title: Bakım kuralları (kod analizi)
description: Kod Analizi bakım kuralları hakkında bilgi edinin.
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.maintainabilityrules
helpviewer_keywords:
- rules, maintainability
- managed code analysis rules, maintainability rules
- maintainability rules
author: gewarren
ms.author: gewarren
ms.openlocfilehash: fc2ef2b42eeba241b7af66b579a60365ad2b88c7
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/30/2021
ms.locfileid: "96588820"
---
# <a name="maintainability-rules"></a>Bakım kuralları

Bakımlama kuralları kitaplığı ve uygulama bakımını destekler.

## <a name="in-this-section"></a>Bu bölümde

| Kural | Description |
|-----------|-----------------------------------|
| [CA1501: Aşırı devralmadan kaçının](ca1501.md) | Devralma hiyerarşisinde düzeyleri dörtten fazla olan türdür. İç içe yuvalanmış hiyerarşileri izlemek, anlamak ve muhafaza etmek zor olabilir. |
| [CA1502: Aşırı karmaşıklıktan kaçının](ca1502.md) | Bu kural, sayılarla ve şartlı şubelerle tanımlanan, yönteme giden doğrusal bağımsız yolların sayısını ölçer. |
| [CA1505: Bakımı yapılamayan kodlardan kaçının](ca1505.md) | Bir tür veya yöntemin düşük bakım dizin değeri vardır. Düşük bakım dizini muhtemelen koruması zor olan ve yeniden tasarım için iyi bir aday olan tür veya yöntemi içerir. |
| [CA1506: Aşırı sınıf bağlantısından kaçının](ca1506.md) | Bu kural türü veya yöntemini içeren benzersiz türde başvuru sayısı belirlenerek eşlenmesiyle sınıfı ölçer. |
| [CA1507: Dize yerine nameof kullanma](ca1507.md) | Bir dize sabit değeri, bir ifadenin kullanılabileceği bir bağımsız değişken olarak kullanılır `nameof` . |
| [CA1508: Ölü koşullu kodlardan kaçının](ca1508.md) | Bir yöntemde, her zaman çalışma zamanında olarak değerlendirilen koşullu kod bulunur `true` `false` . Bu `false` , koşulun dalındaki ölü koda yol açar. |
| [CA1509: Kod ölçümleri yapılandırma dosyasında geçersiz girdi](ca1509.md) | [CA1501](ca1501.md), [CA1502](ca1502.md), [CA1505](ca1505.md) ve [CA1506](ca1506.md)gibi kod ölçüm kuralları, geçersiz bir girişi olan adlı bir yapılandırma dosyası sağladı `CodeMetricsConfig.txt` . |

## <a name="see-also"></a>Ayrıca bkz.

- [Yönetilen kodun ölçüm karmaşıklığı ve Bakımma](/visualstudio/code-quality/code-metrics-values)
