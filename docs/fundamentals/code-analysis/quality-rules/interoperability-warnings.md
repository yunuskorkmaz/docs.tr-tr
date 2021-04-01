---
title: Taşınabilirlik ve birlikte çalışabilirlik kuralları (kod analizi)
description: Kod Analizi kuralı taşınabilirlik ve birlikte çalışabilirlik kuralları hakkında bilgi edinin
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.Portablityrules
- vs.codeanalysis.Interoperabilityrules
helpviewer_keywords:
- managed code analysis rules, interoperability rules, portability rules
- portability rules
- warnings, portability
- interoperability rules
- warnings, interoperability
author: gewarren
ms.author: gewarren
ms.openlocfilehash: a20cd77e13c4a8b95633d129990667f0a8de3ee8
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/30/2021
ms.locfileid: "96588821"
---
# <a name="portability-and-interoperability-rules"></a>Taşınabilirlik ve birlikte çalışabilirlik kuralları

Taşınabilirlik kuralları farklı platformlarda taşınabilirliği destekler. Birlikte çalışabilirlik kuralları COM istemcileriyle etkileşimi destekler.

## <a name="in-this-section"></a>Bu bölümde

| Kural | Description |
| - | - |
| [CA1401: P/Invoke görünür olmamalıdır](ca1401.md) | Ortak bir türdeki ortak veya korumalı yöntemin System.Runtime.InteropServices.DllImportAttribute özniteliği vardır (Ayrıca, Visual Basic Declare anahtar sözcüğü tarafından uygulanır). Bu tür yöntemler açıkta kalmamalıdır. |
| [CA1416: Platform uyumluluğunu doğrula](ca1416.md) | Bir bileşende platforma bağımlı API 'Lerin kullanılması, kodun artık tüm platformlarda çalışmamasına neden olur. |
| [CA1417: `OutAttribute` P/Invoke için dize parametrelerinde kullanmayın](ca1417.md) | Değeri ile geçirilen dize parametreleri, `OutAttribute` dize birbirine bağlı bir dizeyse çalışma zamanının kararlılığını bozabilir. |
