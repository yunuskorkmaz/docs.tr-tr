---
ms.openlocfilehash: 7140f6d4cac063088b3663ab98d292104218b542
ms.sourcegitcommit: e7acba36517134238065e4d50bb4a1cfe47ebd06
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2020
ms.locfileid: "89465525"
---
### <a name="cookie-path-handling-now-conforms-to-rfc-6265"></a><span data-ttu-id="f3fa4-101">Tanımlama bilgisi yol işleme artık RFC 6265 ' e uyar</span><span class="sxs-lookup"><span data-stu-id="f3fa4-101">Cookie Path handling now conforms to RFC 6265</span></span>

<span data-ttu-id="f3fa4-102">[RFC 6265](https://tools.ietf.org/html/rfc6265) ' de tanımlanan yol işleme algoritmaları ve sınıfları için uygulandı <xref:System.Net.Cookie> <xref:System.Net.CookieContainer> .</span><span class="sxs-lookup"><span data-stu-id="f3fa4-102">Path-handling algorithms defined in [RFC 6265](https://tools.ietf.org/html/rfc6265) were implemented for the <xref:System.Net.Cookie> and <xref:System.Net.CookieContainer> classes.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="f3fa4-103">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="f3fa4-103">Version introduced</span></span>

<span data-ttu-id="f3fa4-104">5.0</span><span class="sxs-lookup"><span data-stu-id="f3fa4-104">5.0</span></span>

#### <a name="change-description"></a><span data-ttu-id="f3fa4-105">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="f3fa4-105">Change description</span></span>

- <span data-ttu-id="f3fa4-106"><xref:System.Net.Cookie.Path>Özelliğin artık istek yolunun öneki olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="f3fa4-106">The <xref:System.Net.Cookie.Path> property is no longer required to be a prefix of the request path.</span></span>
- <span data-ttu-id="f3fa4-107">Varsayılan değer <xref:System.Net.Cookie.Path> ve yol eşleştirme algoritmalarının hesaplanması, [5.1.4](https://tools.ietf.org/html/rfc6265#section-5.1.4) of RFC 6265 bölümünde tanımlandığı şekilde uygulanmıştır.</span><span class="sxs-lookup"><span data-stu-id="f3fa4-107">The calculation of the default value of <xref:System.Net.Cookie.Path> and path-matching algorithms were implemented as defined in [section 5.1.4](https://tools.ietf.org/html/rfc6265#section-5.1.4) of RFC 6265.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="f3fa4-108">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="f3fa4-108">Recommended action</span></span>

<span data-ttu-id="f3fa4-109">Çoğu durumda, herhangi bir işlem yapmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="f3fa4-109">In most cases, you won't need to take any action.</span></span> <span data-ttu-id="f3fa4-110">Ancak, kodunuz doğrulamaya bağımlıysa <xref:System.Net.Cookie.Path> kodunuzda gerekli doğrulamayı uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f3fa4-110">However, if your code was dependent on <xref:System.Net.Cookie.Path> validation, you'll need to implement required validation in your code.</span></span> <span data-ttu-id="f3fa4-111">Kodunuz için varsayılan değer hesaplamasına bağımlıysa <xref:System.Net.Cookie.Path> , <xref:System.Net.Cookie.Path> varsayılan değeri kullanmak yerine değeri el ile sağlamayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="f3fa4-111">If your code was dependent on default value calculation for <xref:System.Net.Cookie.Path>, consider supplying the <xref:System.Net.Cookie.Path> value manually instead of using the default value.</span></span>

#### <a name="category"></a><span data-ttu-id="f3fa4-112">Kategori</span><span class="sxs-lookup"><span data-stu-id="f3fa4-112">Category</span></span>

<span data-ttu-id="f3fa4-113">Ağ</span><span class="sxs-lookup"><span data-stu-id="f3fa4-113">Networking</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="f3fa4-114">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="f3fa4-114">Affected APIs</span></span>

- <xref:System.Net.Cookie?displayProperty=fullName>
- <xref:System.Net.CookieContainer?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.Net.Cookie`
- `T:System.Net.CookieContainer`

-->
