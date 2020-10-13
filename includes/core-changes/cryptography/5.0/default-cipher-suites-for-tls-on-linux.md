---
ms.openlocfilehash: d312ba2a22797ff6afff6b893f998c965e68e86e
ms.sourcegitcommit: e078b7540a8293ca1b604c9c0da1ff1506f0170b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/13/2020
ms.locfileid: "91997768"
---
### <a name="default-tls-cipher-suites-for-net-on-linux"></a><span data-ttu-id="83fa6-101">Linux 'ta .NET için varsayılan TLS şifre paketleri</span><span class="sxs-lookup"><span data-stu-id="83fa6-101">Default TLS cipher suites for .NET on Linux</span></span>

<span data-ttu-id="83fa6-102">.NET, Linux 'ta, sınıf <xref:System.Net.Security.SslStream> veya daha yüksek düzey işlemler aracılığıyla (örneğin, sınıfı aracılığıyla) TLS/SSL yaparken varsayılan şifre paketleri Için OpenSSL yapılandırmasına uyar <xref:System.Net.Http.HttpClient> .</span><span class="sxs-lookup"><span data-stu-id="83fa6-102">.NET, on Linux, now respects the OpenSSL configuration for default cipher suites when doing TLS/SSL via the <xref:System.Net.Security.SslStream> class or higher-level operations, such as HTTPS via the <xref:System.Net.Http.HttpClient> class.</span></span> <span data-ttu-id="83fa6-103">Varsayılan şifre paketleri açık olarak yapılandırılmamışsa, Linux üzerinde .NET, izin verilen şifre paketlerinin sıkı bir listesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="83fa6-103">When default cipher suites aren't explicitly configured, .NET on Linux uses a tightly restricted list of permitted cipher suites.</span></span>

#### <a name="change-description"></a><span data-ttu-id="83fa6-104">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="83fa6-104">Change description</span></span>

<span data-ttu-id="83fa6-105">Önceki .NET sürümlerinde, .NET varsayılan şifre paketlerinin sistem yapılandırmasına uymaz.</span><span class="sxs-lookup"><span data-stu-id="83fa6-105">In previous .NET versions, .NET does not respect system configuration for default cipher suites.</span></span> <span data-ttu-id="83fa6-106">Linux 'ta .NET için varsayılan şifre paketi listesi çok daha fazla izne sahiptir.</span><span class="sxs-lookup"><span data-stu-id="83fa6-106">The default cipher suite list for .NET on Linux is very permissive.</span></span>

<span data-ttu-id="83fa6-107">.NET 5,0 ' den başlayarak, Linux 'ta .NET, *OpenSSL. cnf*dosyasında belirtildiğinde varsayılan şifre paketleri Için OpenSSL yapılandırmasına uyar.</span><span class="sxs-lookup"><span data-stu-id="83fa6-107">Starting in .NET 5.0, .NET on Linux respects the OpenSSL configuration for default cipher suites when it's specified in *openssl.cnf*.</span></span> <span data-ttu-id="83fa6-108">Şifre paketleri açık olarak yapılandırılmamışsa, izin verilen şifre paketleri aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="83fa6-108">When cipher suites aren't explicitly configured, the only permitted cipher suites are as follows:</span></span>

- <span data-ttu-id="83fa6-109">TLS 1,3 şifre paketleri</span><span class="sxs-lookup"><span data-stu-id="83fa6-109">TLS 1.3 cipher suites</span></span>
- <span data-ttu-id="83fa6-110">TLS_ECDHE_ECDSA_WITH_AES_256_GCM_SHA384</span><span class="sxs-lookup"><span data-stu-id="83fa6-110">TLS_ECDHE_ECDSA_WITH_AES_256_GCM_SHA384</span></span>
- <span data-ttu-id="83fa6-111">TLS_ECDHE_ECDSA_WITH_AES_128_GCM_SHA256</span><span class="sxs-lookup"><span data-stu-id="83fa6-111">TLS_ECDHE_ECDSA_WITH_AES_128_GCM_SHA256</span></span>
- <span data-ttu-id="83fa6-112">TLS_ECDHE_RSA_WITH_AES_256_GCM_SHA384</span><span class="sxs-lookup"><span data-stu-id="83fa6-112">TLS_ECDHE_RSA_WITH_AES_256_GCM_SHA384</span></span>
- <span data-ttu-id="83fa6-113">TLS_ECDHE_RSA_WITH_AES_128_GCM_SHA256</span><span class="sxs-lookup"><span data-stu-id="83fa6-113">TLS_ECDHE_RSA_WITH_AES_128_GCM_SHA256</span></span>
- <span data-ttu-id="83fa6-114">TLS_ECDHE_ECDSA_WITH_AES_256_CBC_SHA384</span><span class="sxs-lookup"><span data-stu-id="83fa6-114">TLS_ECDHE_ECDSA_WITH_AES_256_CBC_SHA384</span></span>
- <span data-ttu-id="83fa6-115">TLS_ECDHE_ECDSA_WITH_AES_128_CBC_SHA256</span><span class="sxs-lookup"><span data-stu-id="83fa6-115">TLS_ECDHE_ECDSA_WITH_AES_128_CBC_SHA256</span></span>
- <span data-ttu-id="83fa6-116">TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA384</span><span class="sxs-lookup"><span data-stu-id="83fa6-116">TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA384</span></span>
- <span data-ttu-id="83fa6-117">TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA256</span><span class="sxs-lookup"><span data-stu-id="83fa6-117">TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA256</span></span>

<span data-ttu-id="83fa6-118">Bu geri dönüş varsayılanı TLS 1,0 veya TLS 1,1 ile uyumlu herhangi bir şifre paketi içermediğinden, bu eski protokol sürümleri varsayılan olarak etkin bir şekilde devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="83fa6-118">Since this fallback default doesn't include any cipher suites that are compatible with TLS 1.0 or TLS 1.1, these older protocol versions are effectively disabled by default.</span></span>

<span data-ttu-id="83fa6-119">Belirli bir oturumun SslStream 'e CipherSuitePolicy değeri sağlamak hala yapılandırma dosyası içeriğini ve/veya .NET geri dönüş varsayılanını değiştirecek.</span><span class="sxs-lookup"><span data-stu-id="83fa6-119">Supplying a CipherSuitePolicy value to SslStream for a specific session will still replace the configuration file content and/or .NET fallback default.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="83fa6-120">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="83fa6-120">Reason for change</span></span>

<span data-ttu-id="83fa6-121">Linux üzerinde .NET çalıştıran kullanıcılar, varsayılan yapılandırmasının <xref:System.Net.Security.SslStream> üçüncü taraf değerlendirme araçlarından yüksek bir güvenlik derecelendirmesi sağlayan bir olarak değiştirilmesini istedi.</span><span class="sxs-lookup"><span data-stu-id="83fa6-121">Users running .NET on Linux requested that the default configuration for <xref:System.Net.Security.SslStream> be changed to one that provided a high security rating from third-party assessment tools.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="83fa6-122">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="83fa6-122">Version introduced</span></span>

<span data-ttu-id="83fa6-123">5,0 RC1</span><span class="sxs-lookup"><span data-stu-id="83fa6-123">5.0 RC1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="83fa6-124">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="83fa6-124">Recommended action</span></span>

<span data-ttu-id="83fa6-125">Yeni varsayılanlar, modern istemcilerle veya sunucularla iletişim kurarken çalışıyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="83fa6-125">The new defaults are likely to work when communicating with modern clients or servers.</span></span> <span data-ttu-id="83fa6-126">Eski istemcileri kabul etmek için (veya eski sunucularla iletişim kurmak için) varsayılan şifre paketi listesini genişletmeniz gerekiyorsa, bir `CipherSuitePolicy` değer belirtin veya OpenSSL yapılandırma dosyasını değiştirin.</span><span class="sxs-lookup"><span data-stu-id="83fa6-126">If you need to expand the default cipher suite list to accept legacy clients (or to contact legacy servers), either specify a `CipherSuitePolicy` value or change the OpenSSL configuration file.</span></span> <span data-ttu-id="83fa6-127">Birçok Linux dağıtımlarında, OpenSSL yapılandırma dosyası */etc/SSL/OpenSSL.exe. cnf*' de bulunur.</span><span class="sxs-lookup"><span data-stu-id="83fa6-127">On many Linux distributions, the OpenSSL configuration file is at */etc/ssl/openssl.cnf*.</span></span>

<span data-ttu-id="83fa6-128">Bu örnek *OpenSSL. cnf* dosyası, Linux üzerinde .NET 5,0 ve üzeri için varsayılan şifre paketleri ilkesi ile eşdeğer olan minimal bir dosyadır.</span><span class="sxs-lookup"><span data-stu-id="83fa6-128">This sample *openssl.cnf* file is a minimal file that's equivalent to the default cipher suites policy for .NET 5.0 and later on Linux.</span></span> <span data-ttu-id="83fa6-129">Sistem dosyasını değiştirmek yerine, bu kavramları sisteminizde bulunan dosyayla birleştirin.</span><span class="sxs-lookup"><span data-stu-id="83fa6-129">Instead of replacing the system file, merge these concepts with the file that's present on your system.</span></span>

```ini
openssl_conf = default_conf

[default_conf]
ssl_conf = ssl_sect

[ssl_sect]
system_default = system_default_sect

[system_default_sect]
CipherString = ECDHE-ECDSA-AES256-GCM-SHA384:ECDHE-ECDSA-AES128-GCM-SHA256:ECDHE-RSA-AES256-GCM-SHA384:ECDHE-RSA-AES128-GCM-SHA256:ECDHE-ECDSA-AES256-SHA384:ECDHE-ECDSA-AES128-SHA256:ECDHE-RSA-AES256-SHA384:ECDHE-RSA-AES128-SHA256
```

<span data-ttu-id="83fa6-130">Red Hat Enterprise Linux, CentOS ve Fedora dağıtımları, .NET uygulamaları, sistem genelinde şifreleme ilkeleri tarafından izin verilen şifre paketlerine varsayılan olarak yapılır.</span><span class="sxs-lookup"><span data-stu-id="83fa6-130">On the Red Hat Enterprise Linux, CentOS, and Fedora distributions, .NET applications default to the cipher suites permitted by the system-wide cryptographic policies.</span></span> <span data-ttu-id="83fa6-131">Bu dağıtımlardan, *OpenSSL. cnf*yerine şifre ilkeleri yapılandırmasını kullanın.</span><span class="sxs-lookup"><span data-stu-id="83fa6-131">On these distributions, use the crypto-policies configuration instead of *openssl.cnf*.</span></span>

#### <a name="category"></a><span data-ttu-id="83fa6-132">Kategori</span><span class="sxs-lookup"><span data-stu-id="83fa6-132">Category</span></span>

- <span data-ttu-id="83fa6-133">Şifreleme</span><span class="sxs-lookup"><span data-stu-id="83fa6-133">Cryptography</span></span>
- <span data-ttu-id="83fa6-134">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="83fa6-134">Security</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="83fa6-135">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="83fa6-135">Affected APIs</span></span>

<span data-ttu-id="83fa6-136">API analizi aracılığıyla algılayıcısı yok.</span><span class="sxs-lookup"><span data-stu-id="83fa6-136">Not detectible via API analysis.</span></span>

<!--

#### Affected APIs

- Not detectible via API analysis.

-->
