---
ms.openlocfilehash: 92210f6becb5a5a43893ee0fd51ef51e2ddd7f8d
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325236"
---
### <a name="kestrel-http2-disabled-over-tls-on-incompatible-windows-versions"></a><span data-ttu-id="a7e6e-101">Kestrel: HTTP/2 uyumsuz Windows sürümlerinde TLS üzerinden devre dışı bırakıldı</span><span class="sxs-lookup"><span data-stu-id="a7e6e-101">Kestrel: HTTP/2 disabled over TLS on incompatible Windows versions</span></span>

<span data-ttu-id="a7e6e-102">Windows üzerinde Aktarım Katmanı Güvenliği (TLS) üzerinden HTTP/2 ' yi etkinleştirmek için iki gereksinimin karşılanması gerekir:</span><span class="sxs-lookup"><span data-stu-id="a7e6e-102">To enable HTTP/2 over Transport Layer Security (TLS) on Windows, two requirements need to be met:</span></span>

- <span data-ttu-id="a7e6e-103">Windows 8.1 ve Windows Server 2012 R2 ile başlayarak kullanılabilen uygulama katmanı protokol anlaşması (ALPN) desteği.</span><span class="sxs-lookup"><span data-stu-id="a7e6e-103">Application-Layer Protocol Negotiation (ALPN) support, which is available starting with Windows 8.1 and Windows Server 2012 R2.</span></span>
- <span data-ttu-id="a7e6e-104">Windows 10 ve Windows Server 2016 ile başlayarak kullanılabilen, HTTP/2 ile uyumlu olan bir şifre kümesi.</span><span class="sxs-lookup"><span data-stu-id="a7e6e-104">A set of ciphers compatible with HTTP/2, which is available starting with Windows 10 and Windows Server 2016.</span></span>

<span data-ttu-id="a7e6e-105">Bu nedenle, TLS üzerinden HTTP/2 yapılandırıldığında Kestrel davranışı şu şekilde değişir:</span><span class="sxs-lookup"><span data-stu-id="a7e6e-105">As such, Kestrel's behavior when HTTP/2 over TLS is configured has changed to:</span></span>

- <span data-ttu-id="a7e6e-106">`Http1` `Information` [Listenoptions. httpprotocols](/dotnet/api/microsoft.aspnetcore.server.kestrel.core.httpprotocols) olarak ayarlandığında bir iletiyi alçaltma ve bu düzeyde günlüğe kaydetme `Http1AndHttp2` .</span><span class="sxs-lookup"><span data-stu-id="a7e6e-106">Downgrade to `Http1` and log a message at the `Information` level when [ListenOptions.HttpProtocols](/dotnet/api/microsoft.aspnetcore.server.kestrel.core.httpprotocols) is set to `Http1AndHttp2`.</span></span> <span data-ttu-id="a7e6e-107">`Http1AndHttp2` , için varsayılan değerdir `ListenOptions.HttpProtocols` .</span><span class="sxs-lookup"><span data-stu-id="a7e6e-107">`Http1AndHttp2` is the default value for `ListenOptions.HttpProtocols`.</span></span>
- <span data-ttu-id="a7e6e-108">`NotSupportedException` `ListenOptions.HttpProtocols` Olarak ayarlandığında bir oluşturun `Http2` .</span><span class="sxs-lookup"><span data-stu-id="a7e6e-108">Throw a `NotSupportedException` when `ListenOptions.HttpProtocols` is set to `Http2`.</span></span>

<span data-ttu-id="a7e6e-109">Tartışma için bkz. sorun [DotNet/aspnetcore # 23068](https://github.com/dotnet/aspnetcore/issues/23068).</span><span class="sxs-lookup"><span data-stu-id="a7e6e-109">For discussion, see issue [dotnet/aspnetcore#23068](https://github.com/dotnet/aspnetcore/issues/23068).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="a7e6e-110">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="a7e6e-110">Version introduced</span></span>

<span data-ttu-id="a7e6e-111">ASP.NET Core 5,0 Preview 7</span><span class="sxs-lookup"><span data-stu-id="a7e6e-111">ASP.NET Core 5.0 Preview 7</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="a7e6e-112">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="a7e6e-112">Old behavior</span></span>

<span data-ttu-id="a7e6e-113">Aşağıdaki tabloda, TLS üzerinden HTTP/2 yapılandırıldığında davranış özetlenmektedir.</span><span class="sxs-lookup"><span data-stu-id="a7e6e-113">The following table outlines the behavior when HTTP/2 over TLS is configured.</span></span>

| <span data-ttu-id="a7e6e-114">Protokoller</span><span class="sxs-lookup"><span data-stu-id="a7e6e-114">Protocols</span></span> | <span data-ttu-id="a7e6e-115">Windows 7,</span><span class="sxs-lookup"><span data-stu-id="a7e6e-115">Windows 7,</span></span><br /><span data-ttu-id="a7e6e-116">Windows Server 2008 R2,</span><span class="sxs-lookup"><span data-stu-id="a7e6e-116">Windows Server 2008 R2,</span></span><br /><span data-ttu-id="a7e6e-117">veya daha önceki bir sürümü</span><span class="sxs-lookup"><span data-stu-id="a7e6e-117">or earlier</span></span> | <span data-ttu-id="a7e6e-118">Windows 8,</span><span class="sxs-lookup"><span data-stu-id="a7e6e-118">Windows 8,</span></span><br /><span data-ttu-id="a7e6e-119">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="a7e6e-119">Windows Server 2012</span></span> | <span data-ttu-id="a7e6e-120">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="a7e6e-120">Windows 8.1,</span></span><br /><span data-ttu-id="a7e6e-121">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="a7e6e-121">Windows Server 2012 R2</span></span> | <span data-ttu-id="a7e6e-122">Windows 10,</span><span class="sxs-lookup"><span data-stu-id="a7e6e-122">Windows 10,</span></span><br /><span data-ttu-id="a7e6e-123">Windows Server 2016,</span><span class="sxs-lookup"><span data-stu-id="a7e6e-123">Windows Server 2016,</span></span><br /><span data-ttu-id="a7e6e-124">veya daha yeni</span><span class="sxs-lookup"><span data-stu-id="a7e6e-124">or newer</span></span> |
|---------------|-----------------------------------------------|--------------------------------|-------------------------------------|------------------------------------------|
| `Http2`         | <span data-ttu-id="a7e6e-125">Yaratır `NotSupportedException`</span><span class="sxs-lookup"><span data-stu-id="a7e6e-125">Throw `NotSupportedException`</span></span>                   | <span data-ttu-id="a7e6e-126">TLS el sıkışması sırasında hata</span><span class="sxs-lookup"><span data-stu-id="a7e6e-126">Error during TLS handshake</span></span>     | <span data-ttu-id="a7e6e-127">TLS el sıkışması sırasında hata &ast;</span><span class="sxs-lookup"><span data-stu-id="a7e6e-127">Error during TLS handshake &ast;</span></span>     | <span data-ttu-id="a7e6e-128">Hata yok</span><span class="sxs-lookup"><span data-stu-id="a7e6e-128">No error</span></span> |
| `Http1AndHttp2` | <span data-ttu-id="a7e6e-129">Düşürme `Http1`</span><span class="sxs-lookup"><span data-stu-id="a7e6e-129">Downgrade to `Http1`</span></span>                    | <span data-ttu-id="a7e6e-130">Düşürme `Http1`</span><span class="sxs-lookup"><span data-stu-id="a7e6e-130">Downgrade to `Http1`</span></span>     | <span data-ttu-id="a7e6e-131">TLS el sıkışması sırasında hata &ast;</span><span class="sxs-lookup"><span data-stu-id="a7e6e-131">Error during TLS handshake &ast;</span></span>     | <span data-ttu-id="a7e6e-132">Hata yok</span><span class="sxs-lookup"><span data-stu-id="a7e6e-132">No error</span></span> |

<span data-ttu-id="a7e6e-133">&ast; Bu senaryoları etkinleştirmek için uyumlu şifre paketlerini yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="a7e6e-133">&ast; Configure compatible cipher suites to enable these scenarios.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="a7e6e-134">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="a7e6e-134">New behavior</span></span>

<span data-ttu-id="a7e6e-135">Aşağıdaki tabloda, TLS üzerinden HTTP/2 yapılandırıldığında davranış özetlenmektedir.</span><span class="sxs-lookup"><span data-stu-id="a7e6e-135">The following table outlines the behavior when HTTP/2 over TLS is configured.</span></span>

| <span data-ttu-id="a7e6e-136">Protokoller</span><span class="sxs-lookup"><span data-stu-id="a7e6e-136">Protocols</span></span> | <span data-ttu-id="a7e6e-137">Windows 7,</span><span class="sxs-lookup"><span data-stu-id="a7e6e-137">Windows 7,</span></span><br /><span data-ttu-id="a7e6e-138">Windows Server 2008 R2,</span><span class="sxs-lookup"><span data-stu-id="a7e6e-138">Windows Server 2008 R2,</span></span><br /><span data-ttu-id="a7e6e-139">veya daha önceki bir sürümü</span><span class="sxs-lookup"><span data-stu-id="a7e6e-139">or earlier</span></span> | <span data-ttu-id="a7e6e-140">Windows 8,</span><span class="sxs-lookup"><span data-stu-id="a7e6e-140">Windows 8,</span></span><br /><span data-ttu-id="a7e6e-141">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="a7e6e-141">Windows Server 2012</span></span> | <span data-ttu-id="a7e6e-142">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="a7e6e-142">Windows 8.1,</span></span><br /><span data-ttu-id="a7e6e-143">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="a7e6e-143">Windows Server 2012 R2</span></span> | <span data-ttu-id="a7e6e-144">Windows 10,</span><span class="sxs-lookup"><span data-stu-id="a7e6e-144">Windows 10,</span></span><br /><span data-ttu-id="a7e6e-145">Windows Server 2016,</span><span class="sxs-lookup"><span data-stu-id="a7e6e-145">Windows Server 2016,</span></span><br /><span data-ttu-id="a7e6e-146">veya daha yeni</span><span class="sxs-lookup"><span data-stu-id="a7e6e-146">or newer</span></span> |
|---------------|-----------------------------------------------|--------------------------------|-------------------------------------|------------------------------------------|
| `Http2`         | <span data-ttu-id="a7e6e-147">Yaratır `NotSupportedException`</span><span class="sxs-lookup"><span data-stu-id="a7e6e-147">Throw `NotSupportedException`</span></span>                   | <span data-ttu-id="a7e6e-148">Yaratır `NotSupportedException`</span><span class="sxs-lookup"><span data-stu-id="a7e6e-148">Throw `NotSupportedException`</span></span>     | <span data-ttu-id="a7e6e-149">Throw `NotSupportedException`&ast;&ast;</span><span class="sxs-lookup"><span data-stu-id="a7e6e-149">Throw `NotSupportedException` &ast;&ast;</span></span>     | <span data-ttu-id="a7e6e-150">Hata yok</span><span class="sxs-lookup"><span data-stu-id="a7e6e-150">No error</span></span> |
| `Http1AndHttp2` | <span data-ttu-id="a7e6e-151">Düşürme `Http1`</span><span class="sxs-lookup"><span data-stu-id="a7e6e-151">Downgrade to `Http1`</span></span>                    | <span data-ttu-id="a7e6e-152">Düşürme `Http1`</span><span class="sxs-lookup"><span data-stu-id="a7e6e-152">Downgrade to `Http1`</span></span>     | <span data-ttu-id="a7e6e-153">`Http1`Düşürme&ast;&ast;</span><span class="sxs-lookup"><span data-stu-id="a7e6e-153">Downgrade to `Http1` &ast;&ast;</span></span>     | <span data-ttu-id="a7e6e-154">Hata yok</span><span class="sxs-lookup"><span data-stu-id="a7e6e-154">No error</span></span> |

<span data-ttu-id="a7e6e-155">&ast;&ast; Uyumlu şifre paketlerini yapılandırın ve `Microsoft.AspNetCore.Server.Kestrel.EnableWindows81Http2` `true` Bu senaryoları etkinleştirmek için uygulama bağlam anahtarını olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="a7e6e-155">&ast;&ast; Configure compatible cipher suites and set the app context switch `Microsoft.AspNetCore.Server.Kestrel.EnableWindows81Http2` to `true` to enable these scenarios.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="a7e6e-156">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="a7e6e-156">Reason for change</span></span>

<span data-ttu-id="a7e6e-157">Bu değişiklik, eski Windows sürümlerindeki TLS üzerinden HTTP/2 uyumluluk hatalarının erken ve mümkün olduğunca net bir şekilde ortaya geçmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="a7e6e-157">This change ensures compatibility errors for HTTP/2 over TLS on older Windows versions are surfaced as early and as clearly as possible.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="a7e6e-158">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="a7e6e-158">Recommended action</span></span>

<span data-ttu-id="a7e6e-159">Uyumsuz Windows sürümlerinde TLS üzerinden HTTP/2 devre dışı bırakıldığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="a7e6e-159">Ensure HTTP/2 over TLS is disabled on incompatible Windows versions.</span></span> <span data-ttu-id="a7e6e-160">Windows 8.1 ve Windows Server 2012 R2, varsayılan olarak gerekli şifrelemeleri olmadığından uyumsuzdur.</span><span class="sxs-lookup"><span data-stu-id="a7e6e-160">Windows 8.1 and Windows Server 2012 R2 are incompatible since they lack the necessary ciphers by default.</span></span> <span data-ttu-id="a7e6e-161">Ancak, bilgisayar yapılandırma ayarlarını HTTP/2 ile uyumlu şifrelemeleri kullanacak şekilde güncelleştirmek mümkündür.</span><span class="sxs-lookup"><span data-stu-id="a7e6e-161">However, it's possible to update the Computer Configuration settings to use HTTP/2 compatible ciphers.</span></span> <span data-ttu-id="a7e6e-162">Daha fazla bilgi için bkz. [Windows 8.1 'de TLS şifre paketleri](/windows/win32/secauthn/tls-cipher-suites-in-windows-8-1).</span><span class="sxs-lookup"><span data-stu-id="a7e6e-162">For more information, see [TLS cipher suites in Windows 8.1](/windows/win32/secauthn/tls-cipher-suites-in-windows-8-1).</span></span> <span data-ttu-id="a7e6e-163">Yapılandırıldıktan sonra Kestrel üzerinde TLS üzerinden HTTP/2, uygulama bağlamı anahtarı ayarlanarak etkinleştirilmelidir `Microsoft.AspNetCore.Server.Kestrel.EnableWindows81Http2` .</span><span class="sxs-lookup"><span data-stu-id="a7e6e-163">Once configured, HTTP/2 over TLS on Kestrel must be enabled by setting the app context switch `Microsoft.AspNetCore.Server.Kestrel.EnableWindows81Http2`.</span></span> <span data-ttu-id="a7e6e-164">Örnek:</span><span class="sxs-lookup"><span data-stu-id="a7e6e-164">For example:</span></span>

```csharp
AppContext.SetSwitch("Microsoft.AspNetCore.Server.Kestrel.EnableWindows81Http2", true);
```

<span data-ttu-id="a7e6e-165">Temel alınan destek değiştirilmedi.</span><span class="sxs-lookup"><span data-stu-id="a7e6e-165">No underlying support has changed.</span></span> <span data-ttu-id="a7e6e-166">Örneğin, TLS üzerinden HTTP/2, Windows 8 veya Windows Server 2012 ' de hiç çalışmadı.</span><span class="sxs-lookup"><span data-stu-id="a7e6e-166">For example, HTTP/2 over TLS has never worked on Windows 8 or Windows Server 2012.</span></span> <span data-ttu-id="a7e6e-167">Bu değişiklik, bu desteklenmeyen senaryolardaki hataların sunulma şeklini değiştirir.</span><span class="sxs-lookup"><span data-stu-id="a7e6e-167">This change modifies how errors in these unsupported scenarios are presented.</span></span>

#### <a name="category"></a><span data-ttu-id="a7e6e-168">Kategori</span><span class="sxs-lookup"><span data-stu-id="a7e6e-168">Category</span></span>

<span data-ttu-id="a7e6e-169">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="a7e6e-169">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="a7e6e-170">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="a7e6e-170">Affected APIs</span></span>

<span data-ttu-id="a7e6e-171">Yok</span><span class="sxs-lookup"><span data-stu-id="a7e6e-171">None</span></span>

<!--

#### Affected APIs

Not detectable via API analysis

-->
