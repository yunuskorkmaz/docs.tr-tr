---
ms.openlocfilehash: 69b25db88c7580787bbb47fb0902b6bb072f8dde
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235945"
---
### <a name="assemblies-compiled-with-regexcompiletoassembly-breaks-between-40-and-45"></a>4.0 ve 4.5 arasındaki Regex.CompileToAssembly sonları ile derlenmiş bütünleştirilmiş kodları

|   |   |
|---|---|
|Ayrıntılar|Derlenmiş normal ifadelerin bir derleme .NET Framework 4.5 ancak hedef .NET Framework 4 ile oluşturulmuşsa, içeren derlemeyi bir sistemde .NET Framework 4 yüklü bir normal ifade kullanan bir özel durum oluşturur.|
|Öneri|Bu sorunu çözmek için şunlardan birini yapabilirsiniz:<ul><li>.NET Framework 4 ile normal ifadeler içeren derleme.</li><li>Yorumlanan normal ifade kullanın.</li></ul>|
|Kapsam|İkincil|
|Sürüm|4,5|
|Tür|Çalışma zamanı|
|Etkilenen API’ler|<ul><li><xref:System.Text.RegularExpressions.Regex.CompileToAssembly(System.Text.RegularExpressions.RegexCompilationInfo[],System.Reflection.AssemblyName)?displayProperty=nameWithType></li><li><xref:System.Text.RegularExpressions.Regex.CompileToAssembly(System.Text.RegularExpressions.RegexCompilationInfo[],System.Reflection.AssemblyName,System.Reflection.Emit.CustomAttributeBuilder[])?displayProperty=nameWithType></li><li><xref:System.Text.RegularExpressions.Regex.CompileToAssembly(System.Text.RegularExpressions.RegexCompilationInfo[],System.Reflection.AssemblyName,System.Reflection.Emit.CustomAttributeBuilder[],System.String)?displayProperty=nameWithType></li></ul>|
