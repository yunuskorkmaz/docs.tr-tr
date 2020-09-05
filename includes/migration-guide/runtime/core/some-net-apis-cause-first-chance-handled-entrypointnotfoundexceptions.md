---
ms.openlocfilehash: 6431f3b4d0983c44629e4fe760c75adcc277ddd4
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497198"
---
### <a name="some-net-apis-cause-first-chance-handled-entrypointnotfoundexceptions"></a>Bazı .NET API 'Leri ilk şans (işlenmiş) EntryPointNotFoundExceptions olur

#### <a name="details"></a>Ayrıntılar

.NET Framework 4,5 ' de, az sayıda .NET yöntemi ilk şans sunmaya başladı <xref:System.EntryPointNotFoundException?displayProperty=fullName> . Bu özel durumlar .NET Framework içinde işlendi, ancak ilk fırsat özel durumlarını beklememiş olan test otomasyonunu kesintiye uğratacaktır. Bu aynı API 'Ler, HighVersionLie etkinken bazı ApiVerifier senaryolarını keser.

#### <a name="suggestion"></a>Öneri

.NET Framework 4.5.1 ' e yükselterek bu hataya kaçınılabilir. Alternatif olarak, test Otomasyonu ilk şans üzerinde kesintiye uğramayan şekilde güncelleştirilemeyebilir <xref:System.EntryPointNotFoundException?displayProperty=fullName> .

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |Edge|
|Sürüm|4,5|
|Tür|Çalışma Zamanı

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Diagnostics.Debug.Assert(System.Boolean)?displayProperty=nameWithType>
- <xref:System.Diagnostics.Debug.Assert(System.Boolean,System.String)?displayProperty=nameWithType>
- <xref:System.Diagnostics.Debug.Assert(System.Boolean,System.String,System.String)?displayProperty=nameWithType>
- <xref:System.Diagnostics.Debug.Assert(System.Boolean,System.String,System.String,System.Object[])?displayProperty=nameWithType>
- <xref:System.Xml.Serialization.XmlSerializer.%23ctor(System.Type)>

<!--

#### Affected APIs

- `M:System.Diagnostics.Debug.Assert(System.Boolean)`
- `M:System.Diagnostics.Debug.Assert(System.Boolean,System.String)`
- `M:System.Diagnostics.Debug.Assert(System.Boolean,System.String,System.String)`
- `M:System.Diagnostics.Debug.Assert(System.Boolean,System.String,System.String,System.Object[])`
- `M:System.Xml.Serialization.XmlSerializer.#ctor(System.Type)`

-->
