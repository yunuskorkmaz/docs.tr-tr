---
title: "Son değişiklik: tanımlama bilgisi yolu işleme artık RFC 6265 ' e uyar"
description: .NET 5,0 ' de, RFC 6265 ' de tanımlanan yol işleme algoritmalarının tanımlama bilgisi ve tanımlama bilgisi ve tanımlama bilgileri için uygulanan en son değişiklik hakkında bilgi edinin.
ms.date: 08/18/2020
ms.openlocfilehash: 4aea06f434c4bbbef7d94b4b39ff647dd954745e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761449"
---
# <a name="cookie-path-handling-now-conforms-to-rfc-6265"></a><span data-ttu-id="cdc90-103">Tanımlama bilgisi yol işleme artık RFC 6265 ' e uyar</span><span class="sxs-lookup"><span data-stu-id="cdc90-103">Cookie path handling now conforms to RFC 6265</span></span>

<span data-ttu-id="cdc90-104">[RFC 6265](https://tools.ietf.org/html/rfc6265) ' de tanımlanan yol işleme algoritmaları ve sınıfları için uygulandı <xref:System.Net.Cookie> <xref:System.Net.CookieContainer> .</span><span class="sxs-lookup"><span data-stu-id="cdc90-104">Path-handling algorithms defined in [RFC 6265](https://tools.ietf.org/html/rfc6265) were implemented for the <xref:System.Net.Cookie> and <xref:System.Net.CookieContainer> classes.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="cdc90-105">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="cdc90-105">Version introduced</span></span>

<span data-ttu-id="cdc90-106">5.0</span><span class="sxs-lookup"><span data-stu-id="cdc90-106">5.0</span></span>

## <a name="change-description"></a><span data-ttu-id="cdc90-107">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="cdc90-107">Change description</span></span>

- <span data-ttu-id="cdc90-108"><xref:System.Net.Cookie.Path>Özelliğin artık istek yolunun öneki olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="cdc90-108">The <xref:System.Net.Cookie.Path> property is no longer required to be a prefix of the request path.</span></span>
- <span data-ttu-id="cdc90-109">Varsayılan değer <xref:System.Net.Cookie.Path> ve yol eşleştirme algoritmalarının hesaplanması, [5.1.4](https://tools.ietf.org/html/rfc6265#section-5.1.4) of RFC 6265 bölümünde tanımlandığı şekilde uygulanmıştır.</span><span class="sxs-lookup"><span data-stu-id="cdc90-109">The calculation of the default value of <xref:System.Net.Cookie.Path> and path-matching algorithms were implemented as defined in [section 5.1.4](https://tools.ietf.org/html/rfc6265#section-5.1.4) of RFC 6265.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="cdc90-110">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="cdc90-110">Recommended action</span></span>

<span data-ttu-id="cdc90-111">Çoğu durumda, herhangi bir işlem yapmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="cdc90-111">In most cases, you won't need to take any action.</span></span> <span data-ttu-id="cdc90-112">Ancak, kodunuz doğrulamaya bağımlıysa <xref:System.Net.Cookie.Path> kodunuzda gerekli doğrulamayı uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="cdc90-112">However, if your code was dependent on <xref:System.Net.Cookie.Path> validation, you'll need to implement required validation in your code.</span></span> <span data-ttu-id="cdc90-113">Kodunuz için varsayılan değer hesaplamasına bağımlıysa <xref:System.Net.Cookie.Path> , <xref:System.Net.Cookie.Path> varsayılan değeri kullanmak yerine değeri el ile sağlamayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="cdc90-113">If your code was dependent on default value calculation for <xref:System.Net.Cookie.Path>, consider supplying the <xref:System.Net.Cookie.Path> value manually instead of using the default value.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="cdc90-114">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="cdc90-114">Affected APIs</span></span>

- <xref:System.Net.Cookie?displayProperty=fullName>
- <xref:System.Net.CookieContainer?displayProperty=fullName>

<!--

### Affected APIs

- `T:System.Net.Cookie`
- `T:System.Net.CookieContainer`

### Category

Networking

-->
