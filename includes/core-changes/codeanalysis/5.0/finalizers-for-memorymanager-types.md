---
ms.openlocfilehash: 4fc31f75e8f8cdd50abebd399d9749688e6faa5a
ms.sourcegitcommit: e7acba36517134238065e4d50bb4a1cfe47ebd06
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2020
ms.locfileid: "89465604"
---
### <a name="ca2015-do-not-define-finalizers-for-types-derived-from-memorymanagert"></a>CA2015: MemoryManager’dan türetilen türler için sonlandırıcılar tanımlama\<T>

.Net Code Analyzer Rule [CA2015](/visualstudio/code-quality/ca2015) , varsayılan olarak .NET 5,0 ' den başlayarak etkindir. Sonlandırıcıyı tanımlayan herhangi bir tür için derleme uyarısı oluşturur <xref:System.Buffers.MemoryManager%601> .

#### <a name="change-description"></a>Açıklamayı Değiştir

.NET SDK, .NET 5,0 'den başlayarak [.net kaynak kodu Çözümleyicileri](../../../../docs/fundamentals/productivity/code-analysis.md)içerir. Bu kuralların bazıları varsayılan olarak [CA2015](/visualstudio/code-quality/ca2015)dahil olmak üzere etkindir. Projeniz bu kuralı ihlal eden ve uyarıları hata olarak işleyecek şekilde yapılandırılan kodu içeriyorsa, bu değişiklik yapınızı bozabilir.

Bir Sonlandırıcı tanımlatan türetilen kural CA2015 Flags türleri <xref:System.Buffers.MemoryManager%601> . ' Dan türetilen bir türe Sonlandırıcı eklemek <xref:System.Buffers.MemoryManager%601> , büyük olasılıkla bir hatanın göstergesidir. Bir içinde elde edilen yerel bir kaynağın <xref:System.Span%601> temizlenmesinin yanı da hala tarafından kullanılıyor olması önerilir <xref:System.Span%601> .

#### <a name="version-introduced"></a>Sunulan sürüm

5,0 Preview 8

#### <a name="recommended-action"></a>Önerilen eylem

- Sonlandırıcı tanımını kaldırın. Daha fazla bilgi için bkz. [CA2015](/visualstudio/code-quality/ca2015).

- Kod analizini tamamen devre dışı bırakmak için `EnableNETAnalyzers` , `false` proje dosyanızda olarak ayarlayın. Daha fazla bilgi için bkz. [Enablenetçözümleyiciler](../../../../docs/core/project-sdk/msbuild-props.md#enablenetanalyzers).

#### <a name="category"></a>Kategori

Kod analizi

#### <a name="affected-apis"></a>Etkilenen API’ler

API analizi aracılığıyla algılanamaz.

<!--

#### Affected APIs

Not detectable via API analysis.

-->
