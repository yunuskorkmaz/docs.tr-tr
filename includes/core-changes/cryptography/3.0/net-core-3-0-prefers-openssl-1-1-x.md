---
ms.openlocfilehash: 65d8ca480d41a3807473583355fe8be41e0e9701
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81275095"
---
### <a name="net-core-30-prefers-openssl-11x-to-openssl-10x"></a>.NET Core 3.0 OpenSSL 1.1.x openssl 1.0.x tercih

Birden fazla Linux dağıtımında çalışan .NET Core for Linux, OpenSSL 1.0.x ve OpenSSL 1.1.x'i destekleyebilir.  .NET Core 2.1 ve .NET Core 2.2 önce 1.0.x arayın, sonra 1.1.x'e geri düşer; .NET Core 3.0 önce 1.1.x arar. Bu değişiklik, yeni şifreleme standartları için destek eklemek için yapıldı.

Bu değişiklik, .NET Core'daki OpenSSL'ye özgü interop türleri ile platform interop yapan kitaplıkları veya uygulamaları etkileyebilir.

#### <a name="change-description"></a>Açıklamayı değiştir

.NET Core 2.2 ve önceki sürümlerde, çalışma zamanı OpenSSL 1.0.x'i 1.1.x'in üzerine yüklemeyi tercih eder. Bu openssl ile interop için <xref:System.IntPtr> <xref:System.Runtime.InteropServices.SafeHandle> türleri ve libcrypto.so.1.0.0 / libcrypto.so.1.0 / libcrypto.so.10 tercihe göre kullanılır anlamına gelir.

.NET Core 3.0 ile başlayarak, çalışma zamanı OpenSSL 1.0.x üzerinden OpenSSL <xref:System.IntPtr> 1.1.x yüklemeyi tercih eder, bu nedenle OpenSSL ile interop <xref:System.Runtime.InteropServices.SafeHandle> türleri libcrypto.so.1.1 / libcrypto.so.11 / libcrypto.so.1.1.1.0 / crypto lib.so.so.1.1.1.1.1 tercihe göre kullanılır. Sonuç olarak, OpenSSL ile doğrudan çalışan kitaplıklar ve uygulamalar,.NET Core 2.1 veya .NET Core 2.2'den yükseltme yaparken .NET Core'a maruz kalan değerlerle uyumsuz işaretçilere sahip olabilir.

#### <a name="version-introduced"></a>Sürüm tanıtıldı

3,0

#### <a name="recommended-action"></a>Önerilen eylem

OpenSSL ile doğrudan işlem yapan kitaplıklar ve uygulamalar, OpenSSL'nin .NET Core çalışma zamanı ile aynı sürümünü kullandıklarından emin olmak için dikkatli olmalıdır.

.NET Core şifreleme <xref:System.IntPtr> türlerini doğrudan OpenSSL ile kullanan <xref:System.Runtime.InteropServices.SafeHandle> tüm kitaplıklar veya uygulamalar, işaretçilerin <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> uyumlu olduğundan emin olmak için kullandıkları kitaplığın sürümünü yeni özellik ile karşılaştırmalıdır.

#### <a name="category"></a>Kategori

Şifreleme

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Security.Cryptography.SafeEvpPKeyHandle.%23ctor%2A>
- <xref:System.Security.Cryptography.RSAOpenSsl.%23ctor(System.IntPtr)>
- <xref:System.Security.Cryptography.RSAOpenSsl.%23ctor(System.Security.Cryptography.SafeEvpPKeyHandle)>
- <xref:System.Security.Cryptography.RSAOpenSsl.DuplicateKeyHandle?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.DSAOpenSsl.%23ctor(System.IntPtr)>
- <xref:System.Security.Cryptography.DSAOpenSsl.%23ctor(System.Security.Cryptography.SafeEvpPKeyHandle)>
- <xref:System.Security.Cryptography.DSAOpenSsl.DuplicateKeyHandle?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.ECDsaOpenSsl.%23ctor(System.IntPtr)>
- <xref:System.Security.Cryptography.ECDsaOpenSsl.%23ctor(System.Security.Cryptography.SafeEvpPKeyHandle)>
- <xref:System.Security.Cryptography.ECDsaOpenSsl.DuplicateKeyHandle?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl.%23ctor(System.IntPtr)>
- <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl.%23ctor(System.Security.Cryptography.SafeEvpPKeyHandle)>
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
