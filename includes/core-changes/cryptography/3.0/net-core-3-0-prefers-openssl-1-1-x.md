---
ms.openlocfilehash: b49b2f88b130bb952b77964d5bf38374dc606385
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74567966"
---
### <a name="net-core-30-prefers-openssl-11x-to-openssl-10x"></a>.NET Core 3,0 OpenSSL 1.1. x ile OpenSSL 1.0. x tercih eder

Birden çok Linux dağıtımı arasında çalışarak Linux için .NET Core, hem OpenSSL 1.0. x hem de OpenSSL 1.1. x ' i destekleyebilir.  .NET Core 2,1 ve .NET Core 2,2 önce 1.0. x için arama yapın ve ardından 1.1. x ' e geri dönün ve .NET Core 3,0, önce 1.1. x için arama yapar. Yeni şifreleme standartları desteği eklemek için bu değişiklik yapılmıştır.

Bu değişiklik, .NET Core 'da OpenSSL 'e özgü birlikte çalışma türleriyle platform birlikte çalışabilirliğine yönelik kitaplıkları veya uygulamaları etkileyebilir.

#### <a name="change-description"></a>Açıklamayı Değiştir

.NET Core 2,2 ve önceki sürümlerinde, çalışma zamanı OpenSSL 1.0. x sürümünü 1.1. x üzerinden yüklemeyi tercih eder. Bu, OpenSSL ile birlikte çalışabilirlik için <xref:System.IntPtr> ve <xref:System.Runtime.InteropServices.SafeHandle> türlerinin libşifre ile birlikte kullanıldığı anlamına gelir. bu nedenle. 1.0.0/libşifre. so. 1.0/libşifre. so. 10 tercihe göre.

.NET Core 3,0 ile başlayarak, çalışma zamanı OpenSSL 1.0. x üzerinden OpenSSL 1.1. x ' i yüklemeyi tercih eder, bu nedenle OpenSSL ile birlikte çalışma için <xref:System.IntPtr> ve <xref:System.Runtime.InteropServices.SafeHandle> türleri libşifre ile birlikte kullanılır. bu nedenle. 1.1/libşifre. so. 11/libşifre. so. 1.1.0/libşifre. bu so. 1.1.1 tercihe göre. Sonuç olarak, OpenSSL ile birlikte çalışan kitaplıklar ve uygulamalar, .NET Core 2,1 veya .NET Core 2,2 ' den yükseltirken .NET Core tarafından sunulan değerlerle uyumsuz işaretçilere sahip olabilir.

#### <a name="version-introduced"></a>Sunulan sürüm

3.0

#### <a name="recommended-action"></a>Önerilen eylem

OpenSSL ile doğrudan işlem yapan kitaplıklar ve uygulamaların, .NET Core çalışma zamanı ile aynı OpenSSL sürümünü kullandığından emin olmak için dikkatli olması gerekir.

.NET Core şifreleme türlerinden doğrudan OpenSSL ile <xref:System.IntPtr> veya <xref:System.Runtime.InteropServices.SafeHandle> değerlerini kullanan tüm kitaplıklar veya uygulamalar, işaretçilerin uyumlu olduğundan emin olmak için yeni <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> özelliğiyle kullandıkları kitaplığın sürümünü karşılaştırmalıdır.

#### <a name="category"></a>Kategori

Şifreleme

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Security.Cryptography.SafeEvpPKeyHandle.%23ctor%2A?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RSAOpenSsl.%23ctor(System.IntPtr)?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RSAOpenSsl.%23ctor(System.Security.Cryptography.SafeEvpPKeyHandle)?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RSAOpenSsl.DuplicateKeyHandle?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.DSAOpenSsl.%23ctor(System.IntPtr)?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.DSAOpenSsl.%23ctor(System.Security.Cryptography.SafeEvpPKeyHandle)?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.DSAOpenSsl.DuplicateKeyHandle?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.ECDsaOpenSsl.%23ctor(System.IntPtr)?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.ECDsaOpenSsl.%23ctor(System.Security.Cryptography.SafeEvpPKeyHandle)?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.ECDsaOpenSsl.DuplicateKeyHandle?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl.%23ctor(System.IntPtr)?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl.%23ctor(System.Security.Cryptography.SafeEvpPKeyHandle)?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl.DuplicateKeyHandle?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.X509Certificates.X509Certificate.Handle?displayProperty=nameWithType>

<!--

### Affected APIs

- `Overload:System.Security.Cryptography.SafeEvpPKeyHandle.#ctor`
- `M:System.Security.Cryptography.RSAOpenSsl.#ctor(System.IntPtr)`
- `M:System.Security.Cryptography.RSAOpenSsl.#ctor(System.Security.Cryptography.SafeEvpPKeyHandle)`
- `M:System.Security.Cryptography.RSAOpenSsl.DuplicateKeyHandle`
- `M:System.Security.Cryptography.DSAOpenSsl.#ctor(System.IntPtr)`
- `M:System.Security.Cryptography.DSAOpenSsl.#ctor(System.Security.Cryptography.SafeEvpPKeyHandle)`
- `M:System.Security.Cryptography.DSAOpenSsl.DuplicateKeyHandle`
- `M:System.Security.Cryptography.ECDsaOpenSsl.#ctor(System.IntPtr)`
- `M:System.Security.Cryptography.ECDsaOpenSsl.#ctor(System.Security.CryptographySafeEvpPKeyHandle)`
- `M:System.Security.Cryptography.ECDsaOpenSsl.DuplicateKeyHandle`
- `M:System.Security.Cryptography.ECDiffieHellmanOpenSsl.#ctor(System.IntPtr)`
- `M:System.Security.Cryptography.ECDiffieHellmanOpenSsl.#ctor(System.Security.Cryptography.SafeEvpPKeyHandle)`
- `M:System.Security.Cryptography.ECDiffieHellmanOpenSsl.DuplicateKeyHandle`
- `P:System.Security.Cryptography.X509Certificates.X509Certificate.Handle`

-->
