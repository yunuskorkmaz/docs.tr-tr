---
title: "Son değişiklik: Linux 'ta .NET için varsayılan TLS şifre paketleri"
description: Linux 'ta .NET 5 ' teki önemli değişiklik hakkında bilgi edinin ve artık TLS/SSL yaparken varsayılan şifre paketleri için OpenSSL yapılandırmasına uyar.
ms.date: 10/16/2020
ms.openlocfilehash: c28207aa5bf4324a7921deb006c57fbd5e1d6f5f
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256822"
---
# <a name="default-tls-cipher-suites-for-net-on-linux"></a><span data-ttu-id="f9d8a-103">Linux 'ta .NET için varsayılan TLS şifre paketleri</span><span class="sxs-lookup"><span data-stu-id="f9d8a-103">Default TLS cipher suites for .NET on Linux</span></span>

<span data-ttu-id="f9d8a-104">.NET, Linux 'ta, sınıf <xref:System.Net.Security.SslStream> veya daha yüksek düzey işlemler aracılığıyla (örneğin, sınıfı aracılığıyla) TLS/SSL yaparken varsayılan şifre paketleri Için OpenSSL yapılandırmasına uyar <xref:System.Net.Http.HttpClient> .</span><span class="sxs-lookup"><span data-stu-id="f9d8a-104">.NET, on Linux, now respects the OpenSSL configuration for default cipher suites when doing TLS/SSL via the <xref:System.Net.Security.SslStream> class or higher-level operations, such as HTTPS via the <xref:System.Net.Http.HttpClient> class.</span></span> <span data-ttu-id="f9d8a-105">Varsayılan şifre paketleri açık olarak yapılandırılmamışsa, Linux üzerinde .NET, izin verilen şifre paketlerinin sıkı bir listesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="f9d8a-105">When default cipher suites aren't explicitly configured, .NET on Linux uses a tightly restricted list of permitted cipher suites.</span></span>

## <a name="change-description"></a><span data-ttu-id="f9d8a-106">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="f9d8a-106">Change description</span></span>

<span data-ttu-id="f9d8a-107">Önceki .NET sürümlerinde, .NET varsayılan şifre paketlerinin sistem yapılandırmasına uymaz.</span><span class="sxs-lookup"><span data-stu-id="f9d8a-107">In previous .NET versions, .NET does not respect system configuration for default cipher suites.</span></span> <span data-ttu-id="f9d8a-108">Linux 'ta .NET için varsayılan şifre paketi listesi çok daha fazla izne sahiptir.</span><span class="sxs-lookup"><span data-stu-id="f9d8a-108">The default cipher suite list for .NET on Linux is very permissive.</span></span>

<span data-ttu-id="f9d8a-109">.NET 5 ' ten itibaren, Linux 'ta .NET, *OpenSSL. cnf* içinde belirtildiğinde varsayılan şifre paketleri Için OpenSSL yapılandırmasına uyar.</span><span class="sxs-lookup"><span data-stu-id="f9d8a-109">Starting in .NET 5, .NET on Linux respects the OpenSSL configuration for default cipher suites when it's specified in *openssl.cnf*.</span></span> <span data-ttu-id="f9d8a-110">Şifre paketleri açık olarak yapılandırılmamışsa, izin verilen şifre paketleri aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="f9d8a-110">When cipher suites aren't explicitly configured, the only permitted cipher suites are as follows:</span></span>

- <span data-ttu-id="f9d8a-111">TLS 1,3 şifre paketleri</span><span class="sxs-lookup"><span data-stu-id="f9d8a-111">TLS 1.3 cipher suites</span></span>
- <span data-ttu-id="f9d8a-112">TLS_ECDHE_ECDSA_WITH_AES_256_GCM_SHA384</span><span class="sxs-lookup"><span data-stu-id="f9d8a-112">TLS_ECDHE_ECDSA_WITH_AES_256_GCM_SHA384</span></span>
- <span data-ttu-id="f9d8a-113">TLS_ECDHE_ECDSA_WITH_AES_128_GCM_SHA256</span><span class="sxs-lookup"><span data-stu-id="f9d8a-113">TLS_ECDHE_ECDSA_WITH_AES_128_GCM_SHA256</span></span>
- <span data-ttu-id="f9d8a-114">TLS_ECDHE_RSA_WITH_AES_256_GCM_SHA384</span><span class="sxs-lookup"><span data-stu-id="f9d8a-114">TLS_ECDHE_RSA_WITH_AES_256_GCM_SHA384</span></span>
- <span data-ttu-id="f9d8a-115">TLS_ECDHE_RSA_WITH_AES_128_GCM_SHA256</span><span class="sxs-lookup"><span data-stu-id="f9d8a-115">TLS_ECDHE_RSA_WITH_AES_128_GCM_SHA256</span></span>
- <span data-ttu-id="f9d8a-116">TLS_ECDHE_ECDSA_WITH_AES_256_CBC_SHA384</span><span class="sxs-lookup"><span data-stu-id="f9d8a-116">TLS_ECDHE_ECDSA_WITH_AES_256_CBC_SHA384</span></span>
- <span data-ttu-id="f9d8a-117">TLS_ECDHE_ECDSA_WITH_AES_128_CBC_SHA256</span><span class="sxs-lookup"><span data-stu-id="f9d8a-117">TLS_ECDHE_ECDSA_WITH_AES_128_CBC_SHA256</span></span>
- <span data-ttu-id="f9d8a-118">TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA384</span><span class="sxs-lookup"><span data-stu-id="f9d8a-118">TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA384</span></span>
- <span data-ttu-id="f9d8a-119">TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA256</span><span class="sxs-lookup"><span data-stu-id="f9d8a-119">TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA256</span></span>

<span data-ttu-id="f9d8a-120">Bu geri dönüş varsayılanı TLS 1,0 veya TLS 1,1 ile uyumlu herhangi bir şifre paketi içermediğinden, bu eski protokol sürümleri varsayılan olarak etkin bir şekilde devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="f9d8a-120">Since this fallback default doesn't include any cipher suites that are compatible with TLS 1.0 or TLS 1.1, these older protocol versions are effectively disabled by default.</span></span>

<span data-ttu-id="f9d8a-121">Belirli bir oturumun SslStream 'e CipherSuitePolicy değeri sağlamak hala yapılandırma dosyası içeriğini ve/veya .NET geri dönüş varsayılanını değiştirecek.</span><span class="sxs-lookup"><span data-stu-id="f9d8a-121">Supplying a CipherSuitePolicy value to SslStream for a specific session will still replace the configuration file content and/or .NET fallback default.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="f9d8a-122">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="f9d8a-122">Reason for change</span></span>

<span data-ttu-id="f9d8a-123">Linux üzerinde .NET çalıştıran kullanıcılar, varsayılan yapılandırmasının <xref:System.Net.Security.SslStream> üçüncü taraf değerlendirme araçlarından yüksek bir güvenlik derecelendirmesi sağlayan bir olarak değiştirilmesini istedi.</span><span class="sxs-lookup"><span data-stu-id="f9d8a-123">Users running .NET on Linux requested that the default configuration for <xref:System.Net.Security.SslStream> be changed to one that provided a high security rating from third-party assessment tools.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="f9d8a-124">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="f9d8a-124">Version introduced</span></span>

<span data-ttu-id="f9d8a-125">5.0</span><span class="sxs-lookup"><span data-stu-id="f9d8a-125">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="f9d8a-126">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="f9d8a-126">Recommended action</span></span>

<span data-ttu-id="f9d8a-127">Yeni varsayılanlar, modern istemcilerle veya sunucularla iletişim kurarken çalışıyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="f9d8a-127">The new defaults are likely to work when communicating with modern clients or servers.</span></span> <span data-ttu-id="f9d8a-128">Eski istemcileri kabul etmek için (veya eski sunucularla iletişim kurmak için) varsayılan şifre paketi listesini genişletmeniz gerekiyorsa, bir `CipherSuitePolicy` değer belirtin veya OpenSSL yapılandırma dosyasını değiştirin.</span><span class="sxs-lookup"><span data-stu-id="f9d8a-128">If you need to expand the default cipher suite list to accept legacy clients (or to contact legacy servers), either specify a `CipherSuitePolicy` value or change the OpenSSL configuration file.</span></span> <span data-ttu-id="f9d8a-129">Birçok Linux dağıtımlarında, OpenSSL yapılandırma dosyası */etc/SSL/OpenSSL.exe. cnf*' de bulunur.</span><span class="sxs-lookup"><span data-stu-id="f9d8a-129">On many Linux distributions, the OpenSSL configuration file is at */etc/ssl/openssl.cnf*.</span></span>

<span data-ttu-id="f9d8a-130">Bu örnek *OpenSSL. cnf* dosyası, Linux üzerinde .NET 5 ve üzeri için varsayılan şifre paketleri ilkesi ile eşdeğer olan minimal bir dosyadır.</span><span class="sxs-lookup"><span data-stu-id="f9d8a-130">This sample *openssl.cnf* file is a minimal file that's equivalent to the default cipher suites policy for .NET 5 and later on Linux.</span></span> <span data-ttu-id="f9d8a-131">Sistem dosyasını değiştirmek yerine, bu kavramları sisteminizde bulunan dosyayla birleştirin.</span><span class="sxs-lookup"><span data-stu-id="f9d8a-131">Instead of replacing the system file, merge these concepts with the file that's present on your system.</span></span>

```ini
openssl_conf = default_conf

[default_conf]
ssl_conf = ssl_sect

[ssl_sect]
system_default = system_default_sect

[system_default_sect]
CipherString = ECDHE-ECDSA-AES256-GCM-SHA384:ECDHE-ECDSA-AES128-GCM-SHA256:ECDHE-RSA-AES256-GCM-SHA384:ECDHE-RSA-AES128-GCM-SHA256:ECDHE-ECDSA-AES256-SHA384:ECDHE-ECDSA-AES128-SHA256:ECDHE-RSA-AES256-SHA384:ECDHE-RSA-AES128-SHA256
```

<span data-ttu-id="f9d8a-132">Red Hat Enterprise Linux, CentOS ve Fedora dağıtımları, .NET uygulamaları, sistem genelinde şifreleme ilkeleri tarafından izin verilen şifre paketlerine varsayılan olarak yapılır.</span><span class="sxs-lookup"><span data-stu-id="f9d8a-132">On the Red Hat Enterprise Linux, CentOS, and Fedora distributions, .NET applications default to the cipher suites permitted by the system-wide cryptographic policies.</span></span> <span data-ttu-id="f9d8a-133">Bu dağıtımlardan, *OpenSSL. cnf* yerine şifre ilkeleri yapılandırmasını kullanın.</span><span class="sxs-lookup"><span data-stu-id="f9d8a-133">On these distributions, use the crypto-policies configuration instead of *openssl.cnf*.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="f9d8a-134">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="f9d8a-134">Affected APIs</span></span>

<span data-ttu-id="f9d8a-135">API analizi aracılığıyla algılayıcısı yok.</span><span class="sxs-lookup"><span data-stu-id="f9d8a-135">Not detectible via API analysis.</span></span>

<!--

### Affected APIs

- Not detectible via API analysis.

### Category

- Cryptography
- Security

-->
