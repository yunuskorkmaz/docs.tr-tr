---
ms.openlocfilehash: 492d3e61acff31d3d6858a1c27cf353b04a05e36
ms.sourcegitcommit: d4f7ba08f2a45a9dbef53be597eed6d4a9410f29
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/15/2020
ms.locfileid: "86401984"
---
### <a name="security-cookie-name-encoding-removed"></a><span data-ttu-id="4ad8a-101">Güvenlik: tanımlama bilgisi ad kodlaması kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="4ad8a-101">Security: Cookie name encoding removed</span></span>

<span data-ttu-id="4ad8a-102">[Http tanımlama bilgisi standardı](https://tools.ietf.org/html/rfc6265#section-4.1.1) , tanımlama bilgisi adlarında ve değerlerinde yalnızca belirli karakterlere izin verir.</span><span class="sxs-lookup"><span data-stu-id="4ad8a-102">The [HTTP cookie standard](https://tools.ietf.org/html/rfc6265#section-4.1.1) allows only specific characters in cookie names and values.</span></span> <span data-ttu-id="4ad8a-103">İzin verilmeyen karakterleri desteklemek için ASP.NET Core:</span><span class="sxs-lookup"><span data-stu-id="4ad8a-103">To support disallowed characters, ASP.NET Core:</span></span>

* <span data-ttu-id="4ad8a-104">Yanıt tanımlama bilgisi oluştururken kodlama.</span><span class="sxs-lookup"><span data-stu-id="4ad8a-104">Encodes when creating a response cookie.</span></span>
* <span data-ttu-id="4ad8a-105">İstek tanımlama bilgisini okurken kodunu çözer.</span><span class="sxs-lookup"><span data-stu-id="4ad8a-105">Decodes when reading a request cookie.</span></span>

<span data-ttu-id="4ad8a-106">ASP.NET Core 5,0 ' de, bu kodlama davranışı güvenlik kaygıına yanıt olarak değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="4ad8a-106">In ASP.NET Core 5.0, this encoding behavior changed in response to a security concern.</span></span>

<span data-ttu-id="4ad8a-107">Tartışma için bkz. GitHub sorunu [DotNet/aspnetcore # 23578](https://github.com/dotnet/aspnetcore/issues/23578).</span><span class="sxs-lookup"><span data-stu-id="4ad8a-107">For discussion, see GitHub issue [dotnet/aspnetcore#23578](https://github.com/dotnet/aspnetcore/issues/23578).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="4ad8a-108">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="4ad8a-108">Version introduced</span></span>

<span data-ttu-id="4ad8a-109">5,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="4ad8a-109">5.0 Preview 8</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="4ad8a-110">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="4ad8a-110">Old behavior</span></span>

<span data-ttu-id="4ad8a-111">Yanıt tanımlama bilgisi adları kodlanır.</span><span class="sxs-lookup"><span data-stu-id="4ad8a-111">Response cookie names are encoded.</span></span> <span data-ttu-id="4ad8a-112">İstek tanımlama bilgisi adlarının kodu çözüldü.</span><span class="sxs-lookup"><span data-stu-id="4ad8a-112">Request cookie names are decoded.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="4ad8a-113">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="4ad8a-113">New behavior</span></span>

<span data-ttu-id="4ad8a-114">Tanımlama bilgisi adlarının kodlama ve kod çözme işlemi kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="4ad8a-114">Encoding and decoding of cookie names was removed.</span></span> <span data-ttu-id="4ad8a-115">ASP.NET Core önceki [desteklenen sürümleri](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) için, takım, kod çözme sorununu yerinde azaltmanızı planlıyor.</span><span class="sxs-lookup"><span data-stu-id="4ad8a-115">For prior [supported versions](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) of ASP.NET Core, the team plans to mitigate the decoding issue in-place.</span></span> <span data-ttu-id="4ad8a-116">Ayrıca, <xref:Microsoft.AspNetCore.Http.IResponseCookies.Append%2A?displayProperty=nameWithType> geçersiz bir tanımlama bilgisi adıyla çağırmak, türünde bir özel durum oluşturur <xref:System.ArgumentException> .</span><span class="sxs-lookup"><span data-stu-id="4ad8a-116">Additionally, calling <xref:Microsoft.AspNetCore.Http.IResponseCookies.Append%2A?displayProperty=nameWithType> with an invalid cookie name throws an exception of type <xref:System.ArgumentException>.</span></span> <span data-ttu-id="4ad8a-117">Tanımlama bilgisi değerlerinin kodlama ve kod çözme değişmeden kalır.</span><span class="sxs-lookup"><span data-stu-id="4ad8a-117">Encoding and decoding of cookie values remains unchanged.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="4ad8a-118">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="4ad8a-118">Reason for change</span></span>

<span data-ttu-id="4ad8a-119">[Birden çok Web](https://github.com/advisories/GHSA-j6w9-fv6q-3q52)çerçevesi içinde bir sorun bulundu.</span><span class="sxs-lookup"><span data-stu-id="4ad8a-119">An issue was discovered in [multiple web frameworks](https://github.com/advisories/GHSA-j6w9-fv6q-3q52).</span></span> <span data-ttu-id="4ad8a-120">Kodlama ve kod çözme, bir saldırganın, gibi kodlanmış değerler ile gibi ayrılmış önekleri yanıltarak [tanımlama bilgisi önekleri](https://tools.ietf.org/html/draft-ietf-httpbis-cookie-prefixes-00) adlı bir güvenlik özelliğini atlamasına izin verebilir `__Host-` `__%48ost-` .</span><span class="sxs-lookup"><span data-stu-id="4ad8a-120">The encoding and decoding could allow an attacker to bypass a security feature called [cookie prefixes](https://tools.ietf.org/html/draft-ietf-httpbis-cookie-prefixes-00) by spoofing reserved prefixes like `__Host-` with encoded values like `__%48ost-`.</span></span> <span data-ttu-id="4ad8a-121">Saldırı, Web sitesinde siteler arası betik oluşturma (XSS) güvenlik açığı gibi sahte tanımlama bilgilerini eklemek için ikincil bir yararlanma gerektirir.</span><span class="sxs-lookup"><span data-stu-id="4ad8a-121">The attack requires a secondary exploit to inject the spoofed cookies, such as a cross-site scripting (XSS) vulnerability, in the website.</span></span> <span data-ttu-id="4ad8a-122">Bu ön ekler, ASP.NET Core veya `Microsoft.Owin` kitaplıklarda ya da şablonlarda varsayılan olarak kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="4ad8a-122">These prefixes aren't used by default in ASP.NET Core or `Microsoft.Owin` libraries or templates.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="4ad8a-123">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="4ad8a-123">Recommended action</span></span>

<span data-ttu-id="4ad8a-124">Projeleri ASP.NET Core 5,0 veya üzeri bir sürüme taşıyorsanız, tanımlama bilgisi adlarının [belirteç belirtim gereksinimlerine](https://tools.ietf.org/html/rfc2616#section-2.2)uygun olduğundan emin olun: denetimler ve ayırıcılar hariç ASCII karakterleri `"(" | ")" | "<" | ">" | "@" | "," | ";" | ":" | "\" | <"> | "/" | "[" | "]" | "?" | "=" | "{" | "}" | SP | HT` .</span><span class="sxs-lookup"><span data-stu-id="4ad8a-124">If you're moving projects to ASP.NET Core 5.0 or later, ensure that their cookie names conform to the [token specification requirements](https://tools.ietf.org/html/rfc2616#section-2.2): ASCII characters excluding controls and separators `"(" | ")" | "<" | ">" | "@" | "," | ";" | ":" | "\" | <"> | "/" | "[" | "]" | "?" | "=" | "{" | "}" | SP | HT`.</span></span> <span data-ttu-id="4ad8a-125">Tanımlama bilgisi adlarında ASCII olmayan karakterlerin kullanılması veya diğer HTTP üstbilgileri, sunucudan bir özel duruma neden olabilir veya istemci tarafından doğru şekilde yuvarlak bir şekilde yuvarlamayabilir.</span><span class="sxs-lookup"><span data-stu-id="4ad8a-125">The use of non-ASCII characters in cookie names or other HTTP headers may cause an exception from the server or be improperly round-tripped by the client.</span></span>

#### <a name="category"></a><span data-ttu-id="4ad8a-126">Kategori</span><span class="sxs-lookup"><span data-stu-id="4ad8a-126">Category</span></span>

<span data-ttu-id="4ad8a-127">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="4ad8a-127">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="4ad8a-128">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="4ad8a-128">Affected APIs</span></span>

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
