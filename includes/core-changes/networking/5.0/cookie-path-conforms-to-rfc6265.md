---
ms.openlocfilehash: 7140f6d4cac063088b3663ab98d292104218b542
ms.sourcegitcommit: e7acba36517134238065e4d50bb4a1cfe47ebd06
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2020
ms.locfileid: "89465525"
---
### <a name="cookie-path-handling-now-conforms-to-rfc-6265"></a>Tanımlama bilgisi yol işleme artık RFC 6265 ' e uyar

[RFC 6265](https://tools.ietf.org/html/rfc6265) ' de tanımlanan yol işleme algoritmaları ve sınıfları için uygulandı <xref:System.Net.Cookie> <xref:System.Net.CookieContainer> .

#### <a name="version-introduced"></a>Sunulan sürüm

5.0

#### <a name="change-description"></a>Açıklamayı Değiştir

- <xref:System.Net.Cookie.Path>Özelliğin artık istek yolunun öneki olması gerekmez.
- Varsayılan değer <xref:System.Net.Cookie.Path> ve yol eşleştirme algoritmalarının hesaplanması, [5.1.4](https://tools.ietf.org/html/rfc6265#section-5.1.4) of RFC 6265 bölümünde tanımlandığı şekilde uygulanmıştır.

#### <a name="recommended-action"></a>Önerilen eylem

Çoğu durumda, herhangi bir işlem yapmanız gerekmez. Ancak, kodunuz doğrulamaya bağımlıysa <xref:System.Net.Cookie.Path> kodunuzda gerekli doğrulamayı uygulamanız gerekir. Kodunuz için varsayılan değer hesaplamasına bağımlıysa <xref:System.Net.Cookie.Path> , <xref:System.Net.Cookie.Path> varsayılan değeri kullanmak yerine değeri el ile sağlamayı düşünün.

#### <a name="category"></a>Kategori

Ağ

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Net.Cookie?displayProperty=fullName>
- <xref:System.Net.CookieContainer?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.Net.Cookie`
- `T:System.Net.CookieContainer`

-->
