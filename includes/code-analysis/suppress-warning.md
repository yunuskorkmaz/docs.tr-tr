---
ms.openlocfilehash: b26e346f7076a57aef8ae7587ab1222b4100a323
ms.sourcegitcommit: 7e42488c2f8f63f6d499b5f8fb1dec5bac9ad254
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2021
ms.locfileid: "98957942"
---
## <a name="suppress-a-warning"></a>Bir uyarıyı gösterme

Bir kural ihlalini gizlemek için, belirli bir kural KIMLIĞI için önem derecesi seçeneğini `none` bir EditorConfig dosyasında olarak ayarlayın. Örneğin:

```ini
[*.{cs,vb}]
dotnet_diagnostic.CA1822.severity = none
```

Visual Studio, kod analizi kurallarından gelen uyarıları bastırmak için ek yollar sağlar. Daha fazla bilgi için bkz. [Ihlalleri gösterme](/visualstudio/code-quality/use-roslyn-analyzers#suppress-violations).

Kural özellikleri hakkında daha fazla bilgi için bkz. [kural önem derecesini yapılandırma](~/docs/fundamentals/code-analysis/configuration-options.md#severity-level).
