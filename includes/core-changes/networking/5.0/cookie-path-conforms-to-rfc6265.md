---
ms.openlocfilehash: fdbe8ca9b6dbf24c08a2d041c5c7f2e869995f69
ms.sourcegitcommit: b1f4756120deaecb8b554477bb040620f69a4209
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/03/2020
ms.locfileid: "89414466"
---
### <a name="cookie-path-handling-now-conforms-to-rfc-6265"></a><span data-ttu-id="88385-101">Tanımlama bilgisi yol işleme artık RFC 6265 ' e uyar</span><span class="sxs-lookup"><span data-stu-id="88385-101">Cookie Path handling now conforms to RFC 6265</span></span>

<span data-ttu-id="88385-102">[RFC 6265](https://tools.ietf.org/html/rfc6265) ' de tanımlanan yol işleme algoritmaları `Cookie` ve sınıfları için uygulandı `CookieContainer` .</span><span class="sxs-lookup"><span data-stu-id="88385-102">Path handling algorithms defined in [RFC 6265](https://tools.ietf.org/html/rfc6265) were implemented for `Cookie` and `CookieContainer` classes.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="88385-103">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="88385-103">Version introduced</span></span>

<span data-ttu-id="88385-104">5.0</span><span class="sxs-lookup"><span data-stu-id="88385-104">5.0</span></span>

#### <a name="change-description"></a><span data-ttu-id="88385-105">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="88385-105">Change description</span></span>

- <span data-ttu-id="88385-106">`Path`Öznitelik kısıtlaması kaldırıldı (artık, istek yolunun öneki olması beklenmez).</span><span class="sxs-lookup"><span data-stu-id="88385-106">Restriction for the `Path` attribute is removed (it's no longer expected to be a prefix of the request path).</span></span>
- <span data-ttu-id="88385-107">Varsayılan değer `Path` ve yol eşleştirme algoritmalarının hesaplanması, [5.1.4](https://tools.ietf.org/html/rfc6265#section-5.1.4) of RFC 6265 bölümünde tanımlandığı şekilde uygulanmıştır.</span><span class="sxs-lookup"><span data-stu-id="88385-107">Calculation of the default value of `Path` and path matching algorithms were implemented as defined in [section 5.1.4](https://tools.ietf.org/html/rfc6265#section-5.1.4) of RFC 6265.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="88385-108">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="88385-108">Recommended action</span></span>

<span data-ttu-id="88385-109">Çoğu durumda, herhangi bir işlem yapmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="88385-109">In most cases, you won't need to take any action.</span></span> <span data-ttu-id="88385-110">Ancak, kodunuz doğrulamaya bağımlıysa `Path` kodunuzda gerekli doğrulamayı uygulamanız gerekir; Aksi takdirde kodunuz `Path` varsayılan değer hesaplamasına bağımlıysa, `Path` varsayılan değeri kullanmak yerine değeri el ile sağlamak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="88385-110">However, if your code was dependent on `Path` validation you would need to implement required validation in your code; or if your code was dependent on `Path`'s default value calculation, you might want to supply the `Path` value manually instead of using the default value.</span></span>

#### <a name="category"></a><span data-ttu-id="88385-111">Kategori</span><span class="sxs-lookup"><span data-stu-id="88385-111">Category</span></span>

<span data-ttu-id="88385-112">Ağ</span><span class="sxs-lookup"><span data-stu-id="88385-112">Networking</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="88385-113">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="88385-113">Affected APIs</span></span>

- <xref:System.Net.Cookie?displayProperty=fullName>
- <xref:System.Net.CookieContainer?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.Net.Cookie`
- `T:System.Net.CookieContainer`

-->
