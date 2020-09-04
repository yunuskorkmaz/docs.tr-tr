---
ms.openlocfilehash: a51160a8ab5a4b437e51db31def577f8d8f50182
ms.sourcegitcommit: e7acba36517134238065e4d50bb4a1cfe47ebd06
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2020
ms.locfileid: "89465602"
---
### <a name="ca2014-do-not-use-stackalloc-in-loops"></a>CA2014: Döngülerde stackalloc kullanmayın

.Net Code Analyzer Rule [CA2014](/visualstudio/code-quality/ca2014) , varsayılan olarak .NET 5,0 ' den başlayarak etkindir. Bir döngü içinde [stackalloc](../../../../docs/csharp/language-reference/operators/stackalloc.md) ifadesinin kullanıldığı herhangi bir C# kodu için derleme uyarısı oluşturur.

#### <a name="change-description"></a>Açıklamayı Değiştir

.NET SDK, .NET 5,0 'den başlayarak [.net kaynak kodu Çözümleyicileri](../../../../docs/fundamentals/productivity/code-analysis.md)içerir. Bu kuralların bazıları varsayılan olarak [CA2014](/visualstudio/code-quality/ca2014)dahil olmak üzere etkindir. Projeniz bu kuralı ihlal eden ve uyarıları hata olarak işleyecek şekilde yapılandırılan kodu içeriyorsa, bu değişiklik yapınızı bozabilir.

Rule CA2014, bir [stackalloc ifadesinin](../../../../docs/csharp/language-reference/operators/stackalloc.md) bir döngü Içinde kullanıldığı C# kodunu arar. [stackalloc](../../../../docs/csharp/language-reference/operators/stackalloc.md) , geçerli yığın çerçevesindeki belleği ayırır. Geçerli yöntem çağrısı döndürülünceye kadar bellek serbest bırakılana kadar, yığın taşlarına yol açabilir. Yığın taşması özel durumlarını yakalayamayacak, yığın taşması durumunda uygulama sonlandırılacak.

#### <a name="version-introduced"></a>Sunulan sürüm

5,0 Preview 8

#### <a name="recommended-action"></a>Önerilen eylem

- Döngüler içinde [stackalloc](../../../../docs/csharp/language-reference/operators/stackalloc.md) kullanmaktan kaçının. Bellek bloğunu döngü dışında ayırın ve döngü içinde yeniden kullanın. Daha fazla bilgi için bkz. [CA2014](/visualstudio/code-quality/ca2014).

- Kod analizini tamamen devre dışı bırakmak için `EnableNETAnalyzers` , `false` proje dosyanızda olarak ayarlayın. Daha fazla bilgi için bkz. [Enablenetçözümleyiciler](../../../../docs/core/project-sdk/msbuild-props.md#enablenetanalyzers).

#### <a name="category"></a>Kategori

Kod analizi

#### <a name="affected-apis"></a>Etkilenen API’ler

API analizi aracılığıyla algılanamaz.

<!--

#### Affected APIs

Not detectable via API analysis.

-->
