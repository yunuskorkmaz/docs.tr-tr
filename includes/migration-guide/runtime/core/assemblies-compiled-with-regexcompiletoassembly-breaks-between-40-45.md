---
ms.openlocfilehash: 0bd90b3d479a7e0897aaf78b7718ae156a4a239f
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620551"
---
### <a name="assemblies-compiled-with-regexcompiletoassembly-breaks-between-40-and-45"></a>4,0 ile 4,5 arasında Regex. CompileToAssembly sonları ile derlenen derlemeler

#### <a name="details"></a>Ayrıntılar

Derlenmiş normal ifadelerin bir derlemesi .NET Framework 4,5 ile derlenirse, ancak .NET Framework 4 ' ü hedefliyorsa, bu derlemede bulunan ve .NET Framework 4 yüklü olan bir sistemdeki normal ifadelerden birini kullanmaya çalışmak bir özel durum oluşturur.

#### <a name="suggestion"></a>Öneri

Bu sorunu geçici olarak çözmek için aşağıdakilerden birini yapabilirsiniz:<ul><li>.NET Framework 4 ile normal ifadeleri içeren derlemeyi oluşturun.</li><li>Yorumlanan bir normal ifade kullanın.</li></ul>

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |İkincil|
|Sürüm|4,5|
|Tür|Çalışma Zamanı

#### <a name="affected-apis"></a>Etkilenen API’ler

-<xref:System.Text.RegularExpressions.Regex.CompileToAssembly(System.Text.RegularExpressions.RegexCompilationInfo[],System.Reflection.AssemblyName)?displayProperty=nameWithType></li><li><xref:System.Text.RegularExpressions.Regex.CompileToAssembly(System.Text.RegularExpressions.RegexCompilationInfo[],System.Reflection.AssemblyName,System.Reflection.Emit.CustomAttributeBuilder[])?displayProperty=nameWithType></li><li><xref:System.Text.RegularExpressions.Regex.CompileToAssembly(System.Text.RegularExpressions.RegexCompilationInfo[],System.Reflection.AssemblyName,System.Reflection.Emit.CustomAttributeBuilder[],System.String)?displayProperty=nameWithType></li></ul>|
