---
ms.openlocfilehash: d80eb6923b1cafee248c25748915166bafd64817
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117201"
---
### <a name="net-core-30-prefers-openssl-11x-to-openssl-10x"></a>.NET Core 3,0 OpenSSL 1.1. x ile OpenSSL 1.0. x tercih eder

Birden çok Linux dağıtımı arasında çalışarak Linux için .NET Core, hem OpenSSL 1.0. x hem de OpenSSL 1.1. x ' i destekleyebilir.  .NET Core 2,1 ve .NET Core 2,2 önce 1.0. x için arama yapın ve ardından 1.1. x ' e geri dönün ve .NET Core 3,0, önce 1.1. x için arama yapar. Yeni şifreleme standartları desteği eklemek için bu değişiklik yapılmıştır.

Bu değişiklik, .NET Core 'da OpenSSL 'e özgü birlikte çalışma türleriyle platform birlikte çalışabilirliğine yönelik kitaplıkları veya uygulamaları etkileyebilir.

#### <a name="change-description"></a>Açıklamayı Değiştir

.NET Core 2,2 ve önceki sürümlerinde, çalışma zamanı OpenSSL 1.0. x sürümünü 1.1. x üzerinden yüklemeyi tercih eder. Bu, <xref:System.IntPtr> OpenSSL ile <xref:System.Runtime.InteropServices.SafeHandle> birlikte çalışabilirlik için ve türlerinin libşifre ile kullanıldığı anlamına gelir. bu nedenle. 1.0.0/libşifre. so. 1.0/libşifre. so. 10 tercihe göre.

.NET Core 3,0 ile başlayarak, çalışma zamanı OpenSSL 1.0. x üzerinden OpenSSL 1.1. x yüklemesini tercih eder, bu <xref:System.IntPtr> nedenle <xref:System.Runtime.InteropServices.SafeHandle> OpenSSL ile birlikte çalışabilirlik için ve türleri libşifre ile birlikte kullanılır. bu nedenle. 1.1/libşifre. so. 11/libşifre. so. 1.1.0/libşifre. bu so. 1.1.1 tercih. Sonuç olarak, OpenSSL ile birlikte çalışan kitaplıklar ve uygulamalar, .NET Core 2,1 veya .NET Core 2,2 ' den yükseltirken .NET Core tarafından sunulan değerlerle uyumsuz işaretçilere sahip olabilir.

#### <a name="version-introduced"></a>Sunulan sürüm

3.0

#### <a name="recommended-action"></a>Önerilen eylem

OpenSSL ile doğrudan işlem yapan kitaplıklar ve uygulamaların, .NET Core çalışma zamanı ile aynı OpenSSL sürümünü kullandığından emin olmak için dikkatli olması gerekir.

Doğrudan OpenSSL ile .NET Core <xref:System.IntPtr> şifreleme <xref:System.Runtime.InteropServices.SafeHandle> türlerindeki veya kullanan tüm kitaplıklar veya uygulamalar, işaretçilerin şu şekilde olduğundan emin olmak için yeni <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> özellik ile birlikte kullandıkları kitaplığın sürümünü karşılaştırmalıdır Uyumluluk.

#### <a name="category"></a>Kategori

To

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