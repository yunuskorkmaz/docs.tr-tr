---
ms.openlocfilehash: 0b62eff8d70873293aafa539f40bf032672df57a
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616288"
---
### <a name="managed-cryptography-classes-do-not-throw-a-cryptographyexception-in-fips-mode"></a><span data-ttu-id="e9db1-101">Yönetilen şifreleme sınıfları FIPS modunda Cryptographyıexception oluşturmaz</span><span class="sxs-lookup"><span data-stu-id="e9db1-101">Managed cryptography classes do not throw a CryptographyException in FIPS mode</span></span>

#### <a name="details"></a><span data-ttu-id="e9db1-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="e9db1-102">Details</span></span>

<span data-ttu-id="e9db1-103">.NET Framework 4.7.2 ve önceki sürümlerde, <xref:System.Security.Cryptography.SHA256Managed> <xref:System.Security.Cryptography.CryptographicException> sistem ŞIFRELEME kitaplıkları FIPS modunda yapılandırıldığında bir oluşturma gibi yönetilen şifreleme sağlayıcısı sınıfları.</span><span class="sxs-lookup"><span data-stu-id="e9db1-103">In .NET Framework 4.7.2 and earlier versions, managed cryptographic provider classes such as <xref:System.Security.Cryptography.SHA256Managed> throw a <xref:System.Security.Cryptography.CryptographicException> when the system cryptographic libraries are configured in FIPS mode.</span></span> <span data-ttu-id="e9db1-104">Bu özel durumlar, yönetilen sürümlerin FIPS (Federal bilgi Işleme standartları) 140-2 sertifikası ve FIPS kurallarına göre onaylanmak üzere değerlendirilmediği şifreleme algoritmalarını engellemek için oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="e9db1-104">These exceptions are thrown because the managed versions have not undergone FIPS (Federal Information Processing Standards) 140-2 certification, as well as to block cryptographic algorithms that were not considered to be approved based on the FIPS rules.</span></span>  <span data-ttu-id="e9db1-105">Bazı geliştiricilerin geliştirme makineleri FIPS modunda olduğundan, bu özel durumlar genellikle yalnızca üretim sistemlerinde oluşturulur. .NET Framework 4,8 ve sonraki sürümleri hedefleyen uygulamalar otomatik olarak daha yeni ve gevşek ilkeye geçiş yapar, böylece bu, <xref:System.Security.Cryptography.CryptographicException> Varsayılan olarak böyle durumlarda varsayılan olarak oluşturulmaz.</span><span class="sxs-lookup"><span data-stu-id="e9db1-105">Because few developers have their development machines in FIPS mode, these exceptions are frequently thrown only on production systems.Applications that target .NET Framework 4.8 and later versions automatically switch to the newer, relaxed policy, so that a <xref:System.Security.Cryptography.CryptographicException> is no longer thrown by default in such cases.</span></span> <span data-ttu-id="e9db1-106">Bunun yerine, yönetilen şifreleme sınıfları şifreleme işlemlerini bir sistem şifreleme kitaplığına yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="e9db1-106">Instead, the managed cryptography classes redirect cryptographic operations to a system cryptography library.</span></span> <span data-ttu-id="e9db1-107">Bu ilke değişikliği, geliştirici ortamları ve üretim ortamları arasındaki kafa karıştırıcı bir farkı etkili bir şekilde kaldırır ve yerel bileşenlerin ve yönetilen bileşenlerin aynı şifreleme ilkesi altında çalışmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="e9db1-107">This policy change effectively removes a potentially confusing difference between developer environments and the production environments and makes native components and managed components operate under the same cryptographic policy.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="e9db1-108">Öneri</span><span class="sxs-lookup"><span data-stu-id="e9db1-108">Suggestion</span></span>

<span data-ttu-id="e9db1-109">Bu davranış istenmeyen bir davranışsa, <xref:System.Security.Cryptography.CryptographicException> uygulama yapılandırma dosyanızın bölümüne aşağıdaki [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) yapılandırma ayarını ekleyerek FIPS modunda bir, bir önceki davranışı geri yükleyebilirsiniz [\<runtime>](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) .</span><span class="sxs-lookup"><span data-stu-id="e9db1-109">If this behavior is undesirable, you can opt out of it and restore the previous behavior so that a <xref:System.Security.Cryptography.CryptographicException> is thrown in FIPS mode by adding the following [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) configuration setting to the [\<runtime>](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of your application configuration file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Security.Cryptography.UseLegacyFipsThrow=true" />
</runtime>
```

<span data-ttu-id="e9db1-110">Uygulamanız .NET Framework 4.7.2 veya daha önceki bir sürümü hedefliyorsa, [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) [\<runtime>](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) uygulama yapılandırma dosyanızın bölümüne aşağıdaki AppContextSwitchOverrides yapılandırma ayarını ekleyerek da bu değişikliği tercih edebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e9db1-110">If your application targets .NET Framework 4.7.2 or earlier, you can also opt in to this change by adding the following [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) configuration setting to the [\<runtime>](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of your application configuration file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Security.Cryptography.UseLegacyFipsThrow=false" />
</runtime>
```

| <span data-ttu-id="e9db1-111">Name</span><span class="sxs-lookup"><span data-stu-id="e9db1-111">Name</span></span>    | <span data-ttu-id="e9db1-112">Değer</span><span class="sxs-lookup"><span data-stu-id="e9db1-112">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="e9db1-113">Kapsam</span><span class="sxs-lookup"><span data-stu-id="e9db1-113">Scope</span></span>   | <span data-ttu-id="e9db1-114">Edge</span><span class="sxs-lookup"><span data-stu-id="e9db1-114">Edge</span></span>        |
| <span data-ttu-id="e9db1-115">Sürüm</span><span class="sxs-lookup"><span data-stu-id="e9db1-115">Version</span></span> | <span data-ttu-id="e9db1-116">4,8</span><span class="sxs-lookup"><span data-stu-id="e9db1-116">4.8</span></span>         |
| <span data-ttu-id="e9db1-117">Tür</span><span class="sxs-lookup"><span data-stu-id="e9db1-117">Type</span></span>    | <span data-ttu-id="e9db1-118">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="e9db1-118">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="e9db1-119">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="e9db1-119">Affected APIs</span></span>

- <xref:System.Security.Cryptography.AesManaged?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.MD5Cng?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.MD5CryptoServiceProvider?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RC2CryptoServiceProvider?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RijndaelManaged?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RIPEMD160Managed?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.SHA1Managed?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.SHA256Managed?displayProperty=nameWithType>
