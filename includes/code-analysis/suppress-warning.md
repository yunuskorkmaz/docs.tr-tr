---
ms.openlocfilehash: b26e346f7076a57aef8ae7587ab1222b4100a323
ms.sourcegitcommit: 7e42488c2f8f63f6d499b5f8fb1dec5bac9ad254
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2021
ms.locfileid: "98957942"
---
## <a name="suppress-a-warning"></a><span data-ttu-id="6d0db-101">Bir uyarıyı gösterme</span><span class="sxs-lookup"><span data-stu-id="6d0db-101">Suppress a warning</span></span>

<span data-ttu-id="6d0db-102">Bir kural ihlalini gizlemek için, belirli bir kural KIMLIĞI için önem derecesi seçeneğini `none` bir EditorConfig dosyasında olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="6d0db-102">To suppress a rule violation, set the severity option for the specific rule ID to `none` in an EditorConfig file.</span></span> <span data-ttu-id="6d0db-103">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="6d0db-103">For example:</span></span>

```ini
[*.{cs,vb}]
dotnet_diagnostic.CA1822.severity = none
```

<span data-ttu-id="6d0db-104">Visual Studio, kod analizi kurallarından gelen uyarıları bastırmak için ek yollar sağlar.</span><span class="sxs-lookup"><span data-stu-id="6d0db-104">Visual Studio provides additional ways to suppress warnings from code analysis rules.</span></span> <span data-ttu-id="6d0db-105">Daha fazla bilgi için bkz. [Ihlalleri gösterme](/visualstudio/code-quality/use-roslyn-analyzers#suppress-violations).</span><span class="sxs-lookup"><span data-stu-id="6d0db-105">For more information, see [Suppress violations](/visualstudio/code-quality/use-roslyn-analyzers#suppress-violations).</span></span>

<span data-ttu-id="6d0db-106">Kural özellikleri hakkında daha fazla bilgi için bkz. [kural önem derecesini yapılandırma](~/docs/fundamentals/code-analysis/configuration-options.md#severity-level).</span><span class="sxs-lookup"><span data-stu-id="6d0db-106">For more information about rule severities, see [Configure rule severity](~/docs/fundamentals/code-analysis/configuration-options.md#severity-level).</span></span>
