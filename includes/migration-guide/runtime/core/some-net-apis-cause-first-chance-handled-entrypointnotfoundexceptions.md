---
ms.openlocfilehash: b23f06ec5b27fbd7976a4b62ba6105c607eaee39
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61664336"
---
### <a name="some-net-apis-cause-first-chance-handled-entrypointnotfoundexceptions"></a>Bazı .NET API'lerini neden ilk fırsat (EntryPointNotFoundExceptions işlenen)

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.5, .NET yöntemleri az sayıda ilk fırsat özel durum atma başlangıcından <xref:System.EntryPointNotFoundException?displayProperty=name>s. Bu özel durumlar, .NET Framework içinde işlendi, ancak ilk fırsat özel beklenmiyordu test Otomasyonu uğratabilir. HighVersionLie etkinleştirildiğinde bu API'leri bazı ApiVerifier senaryoları bölün.|
|Öneri|Bu hata, .NET Framework 4.5.1 yükselterek önlenebilir. Alternatif olarak, test Otomasyonu ilk şans kesmemesi için güncelleştirilebilir <xref:System.EntryPointNotFoundException?displayProperty=name>s.|
|Kapsam|Kenar|
|Sürüm|4,5|
|Tür|Çalışma zamanı|
|Etkilenen API’ler|<ul><li><xref:System.Diagnostics.Debug.Assert(System.Boolean)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Debug.Assert(System.Boolean,System.String)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Debug.Assert(System.Boolean,System.String,System.String)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Debug.Assert(System.Boolean,System.String,System.String,System.Object[])?displayProperty=nameWithType></li><li><xref:System.Xml.Serialization.XmlSerializer.%23ctor(System.Type)?displayProperty=nameWithType></li></ul>|
