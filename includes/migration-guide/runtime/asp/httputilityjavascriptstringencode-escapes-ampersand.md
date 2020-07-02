---
ms.openlocfilehash: d587e542a72d584502ac3ac892619cc38b88ef77
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620535"
---
### <a name="httputilityjavascriptstringencode-escapes-ampersand"></a>HttpUtility. JavaScriptStringEncode kaçış ve amperde

#### <a name="details"></a>Ayrıntılar

4,5 .NET Framework başlayarak, <xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String)?displayProperty=fullName> ve işareti ( &amp; ) karakteri çıkar.

#### <a name="suggestion"></a>Öneri

Uygulamanız bu yöntemin önceki davranışına bağımlıysa, yapılandırma dosyanızdaki [ASP.net appSettings öğesine](https://docs.microsoft.com/previous-versions/aspnet/hh975440(v=vs.120)) bir ASPNET: Javascriptdonotencodeamperu ayarı ekleyebilirsiniz.

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |İkincil|
|Sürüm|4,5|
|Tür|Çalışma Zamanı

#### <a name="affected-apis"></a>Etkilenen API’ler

-<xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String)?displayProperty=nameWithType></li><li><xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String,System.Boolean)?displayProperty=nameWithType></li></ul>|
