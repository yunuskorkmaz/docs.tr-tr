---
ms.openlocfilehash: fdbe8ca9b6dbf24c08a2d041c5c7f2e869995f69
ms.sourcegitcommit: b1f4756120deaecb8b554477bb040620f69a4209
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/03/2020
ms.locfileid: "89414466"
---
### <a name="cookie-path-handling-now-conforms-to-rfc-6265"></a>Tanımlama bilgisi yol işleme artık RFC 6265 ' e uyar

[RFC 6265](https://tools.ietf.org/html/rfc6265) ' de tanımlanan yol işleme algoritmaları `Cookie` ve sınıfları için uygulandı `CookieContainer` .

#### <a name="version-introduced"></a>Sunulan sürüm

5.0

#### <a name="change-description"></a>Açıklamayı Değiştir

- `Path`Öznitelik kısıtlaması kaldırıldı (artık, istek yolunun öneki olması beklenmez).
- Varsayılan değer `Path` ve yol eşleştirme algoritmalarının hesaplanması, [5.1.4](https://tools.ietf.org/html/rfc6265#section-5.1.4) of RFC 6265 bölümünde tanımlandığı şekilde uygulanmıştır.

#### <a name="recommended-action"></a>Önerilen eylem

Çoğu durumda, herhangi bir işlem yapmanız gerekmez. Ancak, kodunuz doğrulamaya bağımlıysa `Path` kodunuzda gerekli doğrulamayı uygulamanız gerekir; Aksi takdirde kodunuz `Path` varsayılan değer hesaplamasına bağımlıysa, `Path` varsayılan değeri kullanmak yerine değeri el ile sağlamak isteyebilirsiniz.

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
