---
ms.openlocfilehash: ed526095459a48aa37b585dfed79cc12b9fb9e56
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622142"
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

-<xref:System.Diagnostics.Debug.Assert(System.Boolean)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Debug.Assert(System.Boolean,System.String)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Debug.Assert(System.Boolean,System.String,System.String)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Debug.Assert(System.Boolean,System.String,System.String,System.Object[])?displayProperty=nameWithType></li><li><xref:System.Xml.Serialization.XmlSerializer.%23ctor(System.Type)></li></ul>|
