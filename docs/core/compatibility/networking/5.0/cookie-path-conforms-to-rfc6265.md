---
title: "Son değişiklik: tanımlama bilgisi yolu işleme artık RFC 6265 ' e uyar"
description: .NET 5 ' teki önemli değişiklik hakkında bilgi edinmek için RFC 6265 ' de tanımlanan yol işleme algoritmalarının tanımlama bilgisi ve tanımlama, ıecontainer sınıfları için uygulanmış olduğunu öğrenin.
ms.date: 08/18/2020
ms.openlocfilehash: 5ee1bccc79a5ac271904dd3223b58cc168f18cfa
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256471"
---
# <a name="cookie-path-handling-now-conforms-to-rfc-6265"></a>Tanımlama bilgisi yol işleme artık RFC 6265 ' e uyar

[RFC 6265](https://tools.ietf.org/html/rfc6265) ' de tanımlanan yol işleme algoritmaları ve sınıfları için uygulandı <xref:System.Net.Cookie> <xref:System.Net.CookieContainer> .

## <a name="version-introduced"></a>Sunulan sürüm

5.0

## <a name="change-description"></a>Açıklamayı Değiştir

- <xref:System.Net.Cookie.Path>Özelliğin artık istek yolunun öneki olması gerekmez.
- Varsayılan değer <xref:System.Net.Cookie.Path> ve yol eşleştirme algoritmalarının hesaplanması, [5.1.4](https://tools.ietf.org/html/rfc6265#section-5.1.4) of RFC 6265 bölümünde tanımlandığı şekilde uygulanmıştır.

## <a name="recommended-action"></a>Önerilen eylem

Çoğu durumda, herhangi bir işlem yapmanız gerekmez. Ancak, kodunuz doğrulamaya bağımlıysa <xref:System.Net.Cookie.Path> kodunuzda gerekli doğrulamayı uygulamanız gerekir. Kodunuz için varsayılan değer hesaplamasına bağımlıysa <xref:System.Net.Cookie.Path> , <xref:System.Net.Cookie.Path> varsayılan değeri kullanmak yerine değeri el ile sağlamayı düşünün.

## <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Net.Cookie?displayProperty=fullName>
- <xref:System.Net.CookieContainer?displayProperty=fullName>

<!--

### Affected APIs

- `T:System.Net.Cookie`
- `T:System.Net.CookieContainer`

### Category

Networking

-->
