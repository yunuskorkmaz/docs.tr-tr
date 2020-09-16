---
ms.openlocfilehash: b648aee35ff44730f545f0fa06f4e0a86615dece
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90606771"
---
### <a name="httputilityjavascriptstringencode-escapes-ampersand"></a>HttpUtility. JavaScriptStringEncode kaçış ve amperde

#### <a name="details"></a>Ayrıntılar

4,5 .NET Framework başlayarak, <xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String)?displayProperty=fullName> ve işareti ( &amp; ) karakteri çıkar.

#### <a name="suggestion"></a>Öneri

Uygulamanız bu yöntemin önceki davranışına bağımlıysa, yapılandırma dosyanızdaki [ASP.net appSettings öğesine](/previous-versions/aspnet/hh975440(v=vs.120)) bir ASPNET: Javascriptdonotencodeamperu ayarı ekleyebilirsiniz.

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |İkincil|
|Sürüm|4,5|
|Tür|Çalışma Zamanı|

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String)?displayProperty=nameWithType>
- <xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String,System.Boolean)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Web.HttpUtility.JavaScriptStringEncode(System.String)`
- `M:System.Web.HttpUtility.JavaScriptStringEncode(System.String,System.Boolean)`

-->
