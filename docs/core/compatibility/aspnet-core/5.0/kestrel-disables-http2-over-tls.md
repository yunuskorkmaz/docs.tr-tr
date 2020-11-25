---
title: 'Son değişiklik: Kestrel: HTTP/2 uyumsuz Windows sürümlerinde TLS üzerinden devre dışı bırakıldı'
description: "Kestrel başlıklı ASP.NET Core 5,0 ' deki Son değişiklik hakkında bilgi edinin: HTTP/2 uyumsuz Windows sürümlerinde TLS üzerinden devre dışı bırakıldı"
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: befd393795f3e1859d391bca513dd9856101d295
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761593"
---
# <a name="kestrel-http2-disabled-over-tls-on-incompatible-windows-versions"></a><span data-ttu-id="d6f16-103">Kestrel: HTTP/2 uyumsuz Windows sürümlerinde TLS üzerinden devre dışı bırakıldı</span><span class="sxs-lookup"><span data-stu-id="d6f16-103">Kestrel: HTTP/2 disabled over TLS on incompatible Windows versions</span></span>

<span data-ttu-id="d6f16-104">Windows üzerinde Aktarım Katmanı Güvenliği (TLS) üzerinden HTTP/2 ' yi etkinleştirmek için iki gereksinimin karşılanması gerekir:</span><span class="sxs-lookup"><span data-stu-id="d6f16-104">To enable HTTP/2 over Transport Layer Security (TLS) on Windows, two requirements need to be met:</span></span>

- <span data-ttu-id="d6f16-105">Windows 8.1 ve Windows Server 2012 R2 ile başlayarak kullanılabilen protokol anlaşması (ALPN) desteğini Application-Layer.</span><span class="sxs-lookup"><span data-stu-id="d6f16-105">Application-Layer Protocol Negotiation (ALPN) support, which is available starting with Windows 8.1 and Windows Server 2012 R2.</span></span>
- <span data-ttu-id="d6f16-106">Windows 10 ve Windows Server 2016 ile başlayarak kullanılabilen, HTTP/2 ile uyumlu olan bir şifre kümesi.</span><span class="sxs-lookup"><span data-stu-id="d6f16-106">A set of ciphers compatible with HTTP/2, which is available starting with Windows 10 and Windows Server 2016.</span></span>

<span data-ttu-id="d6f16-107">Bu nedenle, TLS üzerinden HTTP/2 yapılandırıldığında Kestrel davranışı şu şekilde değişir:</span><span class="sxs-lookup"><span data-stu-id="d6f16-107">As such, Kestrel's behavior when HTTP/2 over TLS is configured has changed to:</span></span>

- <span data-ttu-id="d6f16-108">`Http1` `Information` [Listenoptions. httpprotocols](/dotnet/api/microsoft.aspnetcore.server.kestrel.core.httpprotocols) olarak ayarlandığında bir iletiyi alçaltma ve bu düzeyde günlüğe kaydetme `Http1AndHttp2` .</span><span class="sxs-lookup"><span data-stu-id="d6f16-108">Downgrade to `Http1` and log a message at the `Information` level when [ListenOptions.HttpProtocols](/dotnet/api/microsoft.aspnetcore.server.kestrel.core.httpprotocols) is set to `Http1AndHttp2`.</span></span> <span data-ttu-id="d6f16-109">`Http1AndHttp2` , için varsayılan değerdir `ListenOptions.HttpProtocols` .</span><span class="sxs-lookup"><span data-stu-id="d6f16-109">`Http1AndHttp2` is the default value for `ListenOptions.HttpProtocols`.</span></span>
- <span data-ttu-id="d6f16-110">`NotSupportedException` `ListenOptions.HttpProtocols` Olarak ayarlandığında bir oluşturun `Http2` .</span><span class="sxs-lookup"><span data-stu-id="d6f16-110">Throw a `NotSupportedException` when `ListenOptions.HttpProtocols` is set to `Http2`.</span></span>

<span data-ttu-id="d6f16-111">Tartışma için bkz. sorun [DotNet/aspnetcore # 23068](https://github.com/dotnet/aspnetcore/issues/23068).</span><span class="sxs-lookup"><span data-stu-id="d6f16-111">For discussion, see issue [dotnet/aspnetcore#23068](https://github.com/dotnet/aspnetcore/issues/23068).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="d6f16-112">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="d6f16-112">Version introduced</span></span>

<span data-ttu-id="d6f16-113">ASP.NET Core 5,0 Preview 7</span><span class="sxs-lookup"><span data-stu-id="d6f16-113">ASP.NET Core 5.0 Preview 7</span></span>

## <a name="old-behavior"></a><span data-ttu-id="d6f16-114">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="d6f16-114">Old behavior</span></span>

<span data-ttu-id="d6f16-115">Aşağıdaki tabloda, TLS üzerinden HTTP/2 yapılandırıldığında davranış özetlenmektedir.</span><span class="sxs-lookup"><span data-stu-id="d6f16-115">The following table outlines the behavior when HTTP/2 over TLS is configured.</span></span>

| <span data-ttu-id="d6f16-116">Protokoller</span><span class="sxs-lookup"><span data-stu-id="d6f16-116">Protocols</span></span> | <span data-ttu-id="d6f16-117">Windows 7,</span><span class="sxs-lookup"><span data-stu-id="d6f16-117">Windows 7,</span></span><br /><span data-ttu-id="d6f16-118">Windows Server 2008 R2,</span><span class="sxs-lookup"><span data-stu-id="d6f16-118">Windows Server 2008 R2,</span></span><br /><span data-ttu-id="d6f16-119">veya daha önceki bir sürümü</span><span class="sxs-lookup"><span data-stu-id="d6f16-119">or earlier</span></span> | <span data-ttu-id="d6f16-120">Windows 8,</span><span class="sxs-lookup"><span data-stu-id="d6f16-120">Windows 8,</span></span><br /><span data-ttu-id="d6f16-121">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="d6f16-121">Windows Server 2012</span></span> | <span data-ttu-id="d6f16-122">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="d6f16-122">Windows 8.1,</span></span><br /><span data-ttu-id="d6f16-123">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="d6f16-123">Windows Server 2012 R2</span></span> | <span data-ttu-id="d6f16-124">Windows 10,</span><span class="sxs-lookup"><span data-stu-id="d6f16-124">Windows 10,</span></span><br /><span data-ttu-id="d6f16-125">Windows Server 2016,</span><span class="sxs-lookup"><span data-stu-id="d6f16-125">Windows Server 2016,</span></span><br /><span data-ttu-id="d6f16-126">veya daha yeni</span><span class="sxs-lookup"><span data-stu-id="d6f16-126">or newer</span></span> |
|---------------|-----------------------------------------------|--------------------------------|-------------------------------------|------------------------------------------|
| `Http2`         | <span data-ttu-id="d6f16-127">Yaratır `NotSupportedException`</span><span class="sxs-lookup"><span data-stu-id="d6f16-127">Throw `NotSupportedException`</span></span>                   | <span data-ttu-id="d6f16-128">TLS el sıkışması sırasında hata</span><span class="sxs-lookup"><span data-stu-id="d6f16-128">Error during TLS handshake</span></span>     | <span data-ttu-id="d6f16-129">TLS el sıkışması sırasında hata &ast;</span><span class="sxs-lookup"><span data-stu-id="d6f16-129">Error during TLS handshake &ast;</span></span>     | <span data-ttu-id="d6f16-130">Hata yok</span><span class="sxs-lookup"><span data-stu-id="d6f16-130">No error</span></span> |
| `Http1AndHttp2` | <span data-ttu-id="d6f16-131">Düşürme `Http1`</span><span class="sxs-lookup"><span data-stu-id="d6f16-131">Downgrade to `Http1`</span></span>                    | <span data-ttu-id="d6f16-132">Düşürme `Http1`</span><span class="sxs-lookup"><span data-stu-id="d6f16-132">Downgrade to `Http1`</span></span>     | <span data-ttu-id="d6f16-133">TLS el sıkışması sırasında hata &ast;</span><span class="sxs-lookup"><span data-stu-id="d6f16-133">Error during TLS handshake &ast;</span></span>     | <span data-ttu-id="d6f16-134">Hata yok</span><span class="sxs-lookup"><span data-stu-id="d6f16-134">No error</span></span> |

<span data-ttu-id="d6f16-135">&ast; Bu senaryoları etkinleştirmek için uyumlu şifre paketlerini yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="d6f16-135">&ast; Configure compatible cipher suites to enable these scenarios.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="d6f16-136">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="d6f16-136">New behavior</span></span>

<span data-ttu-id="d6f16-137">Aşağıdaki tabloda, TLS üzerinden HTTP/2 yapılandırıldığında davranış özetlenmektedir.</span><span class="sxs-lookup"><span data-stu-id="d6f16-137">The following table outlines the behavior when HTTP/2 over TLS is configured.</span></span>

| <span data-ttu-id="d6f16-138">Protokoller</span><span class="sxs-lookup"><span data-stu-id="d6f16-138">Protocols</span></span> | <span data-ttu-id="d6f16-139">Windows 7,</span><span class="sxs-lookup"><span data-stu-id="d6f16-139">Windows 7,</span></span><br /><span data-ttu-id="d6f16-140">Windows Server 2008 R2,</span><span class="sxs-lookup"><span data-stu-id="d6f16-140">Windows Server 2008 R2,</span></span><br /><span data-ttu-id="d6f16-141">veya daha önceki bir sürümü</span><span class="sxs-lookup"><span data-stu-id="d6f16-141">or earlier</span></span> | <span data-ttu-id="d6f16-142">Windows 8,</span><span class="sxs-lookup"><span data-stu-id="d6f16-142">Windows 8,</span></span><br /><span data-ttu-id="d6f16-143">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="d6f16-143">Windows Server 2012</span></span> | <span data-ttu-id="d6f16-144">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="d6f16-144">Windows 8.1,</span></span><br /><span data-ttu-id="d6f16-145">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="d6f16-145">Windows Server 2012 R2</span></span> | <span data-ttu-id="d6f16-146">Windows 10,</span><span class="sxs-lookup"><span data-stu-id="d6f16-146">Windows 10,</span></span><br /><span data-ttu-id="d6f16-147">Windows Server 2016,</span><span class="sxs-lookup"><span data-stu-id="d6f16-147">Windows Server 2016,</span></span><br /><span data-ttu-id="d6f16-148">veya daha yeni</span><span class="sxs-lookup"><span data-stu-id="d6f16-148">or newer</span></span> |
|---------------|-----------------------------------------------|--------------------------------|-------------------------------------|------------------------------------------|
| `Http2`         | <span data-ttu-id="d6f16-149">Yaratır `NotSupportedException`</span><span class="sxs-lookup"><span data-stu-id="d6f16-149">Throw `NotSupportedException`</span></span>                   | <span data-ttu-id="d6f16-150">Yaratır `NotSupportedException`</span><span class="sxs-lookup"><span data-stu-id="d6f16-150">Throw `NotSupportedException`</span></span>     | <span data-ttu-id="d6f16-151">Throw `NotSupportedException`&ast;&ast;</span><span class="sxs-lookup"><span data-stu-id="d6f16-151">Throw `NotSupportedException` &ast;&ast;</span></span>     | <span data-ttu-id="d6f16-152">Hata yok</span><span class="sxs-lookup"><span data-stu-id="d6f16-152">No error</span></span> |
| `Http1AndHttp2` | <span data-ttu-id="d6f16-153">Düşürme `Http1`</span><span class="sxs-lookup"><span data-stu-id="d6f16-153">Downgrade to `Http1`</span></span>                    | <span data-ttu-id="d6f16-154">Düşürme `Http1`</span><span class="sxs-lookup"><span data-stu-id="d6f16-154">Downgrade to `Http1`</span></span>     | <span data-ttu-id="d6f16-155">`Http1`Düşürme&ast;&ast;</span><span class="sxs-lookup"><span data-stu-id="d6f16-155">Downgrade to `Http1` &ast;&ast;</span></span>     | <span data-ttu-id="d6f16-156">Hata yok</span><span class="sxs-lookup"><span data-stu-id="d6f16-156">No error</span></span> |

<span data-ttu-id="d6f16-157">&ast;&ast; Uyumlu şifre paketlerini yapılandırın ve `Microsoft.AspNetCore.Server.Kestrel.EnableWindows81Http2` `true` Bu senaryoları etkinleştirmek için uygulama bağlam anahtarını olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d6f16-157">&ast;&ast; Configure compatible cipher suites and set the app context switch `Microsoft.AspNetCore.Server.Kestrel.EnableWindows81Http2` to `true` to enable these scenarios.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="d6f16-158">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="d6f16-158">Reason for change</span></span>

<span data-ttu-id="d6f16-159">Bu değişiklik, eski Windows sürümlerindeki TLS üzerinden HTTP/2 uyumluluk hatalarının erken ve mümkün olduğunca net bir şekilde ortaya geçmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="d6f16-159">This change ensures compatibility errors for HTTP/2 over TLS on older Windows versions are surfaced as early and as clearly as possible.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="d6f16-160">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="d6f16-160">Recommended action</span></span>

<span data-ttu-id="d6f16-161">Uyumsuz Windows sürümlerinde TLS üzerinden HTTP/2 devre dışı bırakıldığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="d6f16-161">Ensure HTTP/2 over TLS is disabled on incompatible Windows versions.</span></span> <span data-ttu-id="d6f16-162">Windows 8.1 ve Windows Server 2012 R2, varsayılan olarak gerekli şifrelemeleri olmadığından uyumsuzdur.</span><span class="sxs-lookup"><span data-stu-id="d6f16-162">Windows 8.1 and Windows Server 2012 R2 are incompatible since they lack the necessary ciphers by default.</span></span> <span data-ttu-id="d6f16-163">Ancak, bilgisayar yapılandırma ayarlarını HTTP/2 ile uyumlu şifrelemeleri kullanacak şekilde güncelleştirmek mümkündür.</span><span class="sxs-lookup"><span data-stu-id="d6f16-163">However, it's possible to update the Computer Configuration settings to use HTTP/2 compatible ciphers.</span></span> <span data-ttu-id="d6f16-164">Daha fazla bilgi için bkz. [Windows 8.1 'de TLS şifre paketleri](/windows/win32/secauthn/tls-cipher-suites-in-windows-8-1).</span><span class="sxs-lookup"><span data-stu-id="d6f16-164">For more information, see [TLS cipher suites in Windows 8.1](/windows/win32/secauthn/tls-cipher-suites-in-windows-8-1).</span></span> <span data-ttu-id="d6f16-165">Yapılandırıldıktan sonra Kestrel üzerinde TLS üzerinden HTTP/2, uygulama bağlamı anahtarı ayarlanarak etkinleştirilmelidir `Microsoft.AspNetCore.Server.Kestrel.EnableWindows81Http2` .</span><span class="sxs-lookup"><span data-stu-id="d6f16-165">Once configured, HTTP/2 over TLS on Kestrel must be enabled by setting the app context switch `Microsoft.AspNetCore.Server.Kestrel.EnableWindows81Http2`.</span></span> <span data-ttu-id="d6f16-166">Örnek:</span><span class="sxs-lookup"><span data-stu-id="d6f16-166">For example:</span></span>

```csharp
AppContext.SetSwitch("Microsoft.AspNetCore.Server.Kestrel.EnableWindows81Http2", true);
```

<span data-ttu-id="d6f16-167">Temel alınan destek değiştirilmedi.</span><span class="sxs-lookup"><span data-stu-id="d6f16-167">No underlying support has changed.</span></span> <span data-ttu-id="d6f16-168">Örneğin, TLS üzerinden HTTP/2, Windows 8 veya Windows Server 2012 ' de hiç çalışmadı.</span><span class="sxs-lookup"><span data-stu-id="d6f16-168">For example, HTTP/2 over TLS has never worked on Windows 8 or Windows Server 2012.</span></span> <span data-ttu-id="d6f16-169">Bu değişiklik, bu desteklenmeyen senaryolardaki hataların sunulma şeklini değiştirir.</span><span class="sxs-lookup"><span data-stu-id="d6f16-169">This change modifies how errors in these unsupported scenarios are presented.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="d6f16-170">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="d6f16-170">Affected APIs</span></span>

<span data-ttu-id="d6f16-171">Yok</span><span class="sxs-lookup"><span data-stu-id="d6f16-171">None</span></span>

<!--

### Category

ASP.NET Core

### Affected APIs

Not detectable via API analysis

-->
