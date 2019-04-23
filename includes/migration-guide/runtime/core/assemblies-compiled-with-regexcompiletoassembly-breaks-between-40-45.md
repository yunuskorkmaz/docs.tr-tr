---
ms.openlocfilehash: 69b25db88c7580787bbb47fb0902b6bb072f8dde
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59981646"
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
