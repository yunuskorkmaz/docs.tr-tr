---
ms.openlocfilehash: 36a9db601f7637185bf48dfcbe2233b4489fcdcf
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614655"
---
### <a name="aescryptoserviceprovider-decryptor-provides-a-reusable-transform"></a><span data-ttu-id="12c99-101">AesCryptoServiceProvider şifre çözücü yeniden kullanılabilir bir dönüşüm sağlar</span><span class="sxs-lookup"><span data-stu-id="12c99-101">AesCryptoServiceProvider decryptor provides a reusable transform</span></span>

#### <a name="details"></a><span data-ttu-id="12c99-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="12c99-102">Details</span></span>

<span data-ttu-id="12c99-103">.NET Framework 4.6.2 hedefleyen uygulamalarla başlayarak, <xref:System.Security.Cryptography.AesCryptoServiceProvider> şifre çözücü yeniden kullanılabilir bir dönüşüm sağlar.</span><span class="sxs-lookup"><span data-stu-id="12c99-103">Starting with apps that target the .NET Framework 4.6.2, the <xref:System.Security.Cryptography.AesCryptoServiceProvider> decryptor provides a reusable transform.</span></span> <span data-ttu-id="12c99-104">Bir çağrısından sonra <xref:System.Security.Cryptography.CryptoAPITransform.TransformFinalBlock(System.Byte[],System.Int32,System.Int32)?displayProperty=fullName> dönüşüm yeniden başlatılır ve yeniden kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="12c99-104">After a call to <xref:System.Security.Cryptography.CryptoAPITransform.TransformFinalBlock(System.Byte[],System.Int32,System.Int32)?displayProperty=fullName>, the transform is reinitialized and can be reused.</span></span> <span data-ttu-id="12c99-105">.NET Framework önceki sürümlerini hedefleyen uygulamalar için, bir çağrısından sonra çağrı yaparak şifre çözücü yeniden kullanılmaya çalışılıyor <xref:System.Security.Cryptography.CryptoAPITransform.TransformBlock(System.Byte[],System.Int32,System.Int32,System.Byte[],System.Int32)?displayProperty=fullName> <xref:System.Security.Cryptography.CryptoAPITransform.TransformFinalBlock(System.Byte[],System.Int32,System.Int32)?displayProperty=fullName> <xref:System.Security.Cryptography.CryptographicException> veya bozuk veriler oluşturur.</span><span class="sxs-lookup"><span data-stu-id="12c99-105">For apps that target earlier versions of the .NET Framework, attempting to reuse the decryptor by calling <xref:System.Security.Cryptography.CryptoAPITransform.TransformBlock(System.Byte[],System.Int32,System.Int32,System.Byte[],System.Int32)?displayProperty=fullName> after a call to <xref:System.Security.Cryptography.CryptoAPITransform.TransformFinalBlock(System.Byte[],System.Int32,System.Int32)?displayProperty=fullName> throws a <xref:System.Security.Cryptography.CryptographicException> or produces corrupted data.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="12c99-106">Öneri</span><span class="sxs-lookup"><span data-stu-id="12c99-106">Suggestion</span></span>

<span data-ttu-id="12c99-107">Beklenen davranış olduğundan bu değişikliğin etkisi en az olmalıdır. Önceki davranışa bağımlı olan uygulamalar `<runtime>` , uygulamanın yapılandırma dosyasının bölümüne aşağıdaki yapılandırma ayarını ekleyerek onu kullanarak devre dışı bırakabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="12c99-107">The impact of this change should be minimal, since this is the expected behavior.Applications that depend on the previous behavior can opt out of it using it by adding the following configuration setting to the `<runtime>` section of the application's configuration file:</span></span>

```xml
<runtime>
<AppContextSwitchOverrides value="Switch.System.Security.Cryptography.AesCryptoServiceProvider.DontCorrectlyResetDecryptor=true"/>
</runtime>
```

<span data-ttu-id="12c99-108">Ayrıca, .NET Framework önceki bir sürümünü hedefleyen, ancak .NET Framework bir sürümü altında çalışan uygulamalar .NET Framework 4.6.2, `<runtime>` uygulamanın yapılandırma dosyasının bölümüne aşağıdaki yapılandırma ayarını ekleyerek bunu kabul edebilir:</span><span class="sxs-lookup"><span data-stu-id="12c99-108">In addition, applications that target a previous version of the .NET Framework but are running under a version of the .NET Framework starting with .NET Framework 4.6.2 can opt in to it by adding the following configuration setting to the `<runtime>` section of the application's configuration file:</span></span>

```xml
<runtime>
<AppContextSwitchOverrides value="Switch.System.Security.Cryptography.AesCryptoServiceProvider.DontCorrectlyResetDecryptor=false"/>
</runtime>
```

| <span data-ttu-id="12c99-109">Name</span><span class="sxs-lookup"><span data-stu-id="12c99-109">Name</span></span>    | <span data-ttu-id="12c99-110">Değer</span><span class="sxs-lookup"><span data-stu-id="12c99-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="12c99-111">Kapsam</span><span class="sxs-lookup"><span data-stu-id="12c99-111">Scope</span></span>   | <span data-ttu-id="12c99-112">İkincil</span><span class="sxs-lookup"><span data-stu-id="12c99-112">Minor</span></span>       |
| <span data-ttu-id="12c99-113">Sürüm</span><span class="sxs-lookup"><span data-stu-id="12c99-113">Version</span></span> | <span data-ttu-id="12c99-114">4.6.2</span><span class="sxs-lookup"><span data-stu-id="12c99-114">4.6.2</span></span>       |
| <span data-ttu-id="12c99-115">Tür</span><span class="sxs-lookup"><span data-stu-id="12c99-115">Type</span></span>    | <span data-ttu-id="12c99-116">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="12c99-116">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="12c99-117">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="12c99-117">Affected APIs</span></span>

- <xref:System.Security.Cryptography.AesCryptoServiceProvider.CreateDecryptor?displayProperty=nameWithType>
