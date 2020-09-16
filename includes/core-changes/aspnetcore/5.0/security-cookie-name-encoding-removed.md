---
ms.openlocfilehash: 492d3e61acff31d3d6858a1c27cf353b04a05e36
ms.sourcegitcommit: d4f7ba08f2a45a9dbef53be597eed6d4a9410f29
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/15/2020
ms.locfileid: "86401984"
---
### <a name="security-cookie-name-encoding-removed"></a>Güvenlik: tanımlama bilgisi ad kodlaması kaldırıldı

[Http tanımlama bilgisi standardı](https://tools.ietf.org/html/rfc6265#section-4.1.1) , tanımlama bilgisi adlarında ve değerlerinde yalnızca belirli karakterlere izin verir. İzin verilmeyen karakterleri desteklemek için ASP.NET Core:

* Yanıt tanımlama bilgisi oluştururken kodlama.
* İstek tanımlama bilgisini okurken kodunu çözer.

ASP.NET Core 5,0 ' de, bu kodlama davranışı güvenlik kaygıına yanıt olarak değiştirilmiştir.

Tartışma için bkz. GitHub sorunu [DotNet/aspnetcore # 23578](https://github.com/dotnet/aspnetcore/issues/23578).

#### <a name="version-introduced"></a>Sunulan sürüm

5,0 Preview 8

#### <a name="old-behavior"></a>Eski davranış

Yanıt tanımlama bilgisi adları kodlanır. İstek tanımlama bilgisi adlarının kodu çözüldü.

#### <a name="new-behavior"></a>Yeni davranış

Tanımlama bilgisi adlarının kodlama ve kod çözme işlemi kaldırılmıştır. ASP.NET Core önceki [desteklenen sürümleri](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) için, takım, kod çözme sorununu yerinde azaltmanızı planlıyor. Ayrıca, <xref:Microsoft.AspNetCore.Http.IResponseCookies.Append%2A?displayProperty=nameWithType> geçersiz bir tanımlama bilgisi adıyla çağırmak, türünde bir özel durum oluşturur <xref:System.ArgumentException> . Tanımlama bilgisi değerlerinin kodlama ve kod çözme değişmeden kalır.

#### <a name="reason-for-change"></a>Değişiklik nedeni

[Birden çok Web](https://github.com/advisories/GHSA-j6w9-fv6q-3q52)çerçevesi içinde bir sorun bulundu. Kodlama ve kod çözme, bir saldırganın, gibi kodlanmış değerler ile gibi ayrılmış önekleri yanıltarak [tanımlama bilgisi önekleri](https://tools.ietf.org/html/draft-ietf-httpbis-cookie-prefixes-00) adlı bir güvenlik özelliğini atlamasına izin verebilir `__Host-` `__%48ost-` . Saldırı, Web sitesinde siteler arası betik oluşturma (XSS) güvenlik açığı gibi sahte tanımlama bilgilerini eklemek için ikincil bir yararlanma gerektirir. Bu ön ekler, ASP.NET Core veya `Microsoft.Owin` kitaplıklarda ya da şablonlarda varsayılan olarak kullanılmaz.

#### <a name="recommended-action"></a>Önerilen eylem

Projeleri ASP.NET Core 5,0 veya üzeri bir sürüme taşıyorsanız, tanımlama bilgisi adlarının [belirteç belirtim gereksinimlerine](https://tools.ietf.org/html/rfc2616#section-2.2)uygun olduğundan emin olun: denetimler ve ayırıcılar hariç ASCII karakterleri `"(" | ")" | "<" | ">" | "@" | "," | ";" | ":" | "\" | <"> | "/" | "[" | "]" | "?" | "=" | "{" | "}" | SP | HT` . Tanımlama bilgisi adlarında ASCII olmayan karakterlerin kullanılması veya diğer HTTP üstbilgileri, sunucudan bir özel duruma neden olabilir veya istemci tarafından doğru şekilde yuvarlak bir şekilde yuvarlamayabilir.

#### <a name="category"></a>Kategori

ASP.NET Core

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:Microsoft.AspNetCore.Http.HttpRequest.Cookies%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.HttpResponse.Cookies%2A?displayProperty=nameWithType>
- <xref:Microsoft.Owin.IOwinRequest.Cookies?displayProperty=nameWithType>
- <xref:Microsoft.Owin.IOwinResponse.Cookies?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:Microsoft.AspNetCore.Http.HttpRequest.Cookies`
- `Overload:Microsoft.AspNetCore.Http.HttpResponse.Cookies`
- `P:Microsoft.Owin.IOwinRequest.Cookies`
- `P:Microsoft.Owin.IOwinResponse.Cookies`

-->
