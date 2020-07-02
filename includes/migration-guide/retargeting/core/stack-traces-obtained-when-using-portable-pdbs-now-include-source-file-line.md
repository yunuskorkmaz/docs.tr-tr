---
ms.openlocfilehash: c7500550cd9714a9788a7dea68af04823f000f7f
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614800"
---
### <a name="stack-traces-obtained-when-using-portable-pdbs-now-include-source-file-and-line-information-if-requested"></a>Taşınabilir pdb 'leri kullanıldığında elde edilen yığın izlemeleri artık, istenirse kaynak dosya ve satır bilgilerini içerir

#### <a name="details"></a>Ayrıntılar

.NET Framework 4.7.2 ile başlayarak, taşınabilir pdb 'leri dahil edildiğinde yığın izlemeleri, istendiğinde kaynak dosya ve satır bilgilerini içerir. .NET Framework 4.7.2 ' den önceki sürümlerde, açık bir şekilde istenmiş olsa bile taşınabilir pdb 'leri kullanılırken kaynak dosya ve satır bilgileri kullanılamaz.

#### <a name="suggestion"></a>Öneri

.NET Framework 4.7.2 ' i hedefleyen uygulamalar için, taşınabilir pdb 'leri kullanırken, dosyanın bölümüne aşağıdakileri ekleyerek kaynak dosya ve satır bilgilerini devre dışı bırakabilirsiniz `<runtime>` `app.config` :

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Diagnostics.IgnorePortablePDBsInStackTraces=true" />
</runtime>
```

.NET Framework önceki sürümlerini hedefleyen, ancak .NET Framework 4.7.2 veya sonraki sürümlerde çalışan uygulamalar için, dosyanızın bölümüne aşağıdakileri ekleyerek taşınabilir pdb 'leri kullanırken kaynak dosya ve satır bilgilerini kabul edebilirsiniz `<runtime>` `app.config` :

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Diagnostics.IgnorePortablePDBsInStackTraces=false" />
</runtime>
```

| Name    | Değer       |
|:--------|:------------|
| Kapsam   | Edge        |
| Sürüm | 4.7.2       |
| Tür    | Yeniden Hedefleme |

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Diagnostics.StackTrace.%23ctor(System.Boolean)>
- <xref:System.Diagnostics.StackTrace.%23ctor(System.Exception,System.Boolean)>
- <xref:System.Diagnostics.StackTrace.%23ctor(System.Exception,System.Int32,System.Boolean)>
