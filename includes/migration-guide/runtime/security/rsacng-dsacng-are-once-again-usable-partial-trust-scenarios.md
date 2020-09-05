---
ms.openlocfilehash: 4788f5b80306116e63ee56584d65b862ce0606ee
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496596"
---
### <a name="rsacng-and-dsacng-are-once-again-usable-in-partial-trust-scenarios"></a><span data-ttu-id="59543-101">RSACng ve DSACng kısmi güven senaryolarında yeniden kullanılabilir</span><span class="sxs-lookup"><span data-stu-id="59543-101">RSACng and DSACng are once again usable in Partial Trust scenarios</span></span>

#### <a name="details"></a><span data-ttu-id="59543-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="59543-102">Details</span></span>

<span data-ttu-id="59543-103">Cngmaitipon (gibi, daha üst düzey şifreleme API 'lerinde kullanılır <xref:System.Security.Cryptography.Xml.EncryptedXml?displayProperty=nameWithType> ) ve <xref:System.Security.Cryptography.RSACng?displayProperty=nameWithType> bazı durumlarda tam güvenle yararlanır.</span><span class="sxs-lookup"><span data-stu-id="59543-103">CngLightup (used in several higher-level crypto apis, such as <xref:System.Security.Cryptography.Xml.EncryptedXml?displayProperty=nameWithType>) and <xref:System.Security.Cryptography.RSACng?displayProperty=nameWithType> in some cases rely on full trust.</span></span> <span data-ttu-id="59543-104">Bunlar, izinleri belirtmeden P/Invoke <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode?displayProperty=nameWithType> ve <xref:System.Security.Cryptography.CngKey?displayProperty=nameWithType> için izin taleplerine sahip olan kod yollarını içerir <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="59543-104">These include P/Invokes without asserting <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode?displayProperty=nameWithType> permissions, and code paths where <xref:System.Security.Cryptography.CngKey?displayProperty=nameWithType> has permission demands for <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode?displayProperty=nameWithType>.</span></span> <span data-ttu-id="59543-105">.NET Framework 4.6.2 ile başlayarak, mümkün olan her yerde geçiş yapmak için Cngaçıklabir şekilde kullanılmıştı <xref:System.Security.Cryptography.RSACng?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="59543-105">Starting with the .NET Framework 4.6.2, CngLightup was used to switch to <xref:System.Security.Cryptography.RSACng?displayProperty=nameWithType> wherever possible.</span></span> <span data-ttu-id="59543-106">Sonuç olarak, başarıyla kullanılan kısmi güven uygulamaları <xref:System.Security.Cryptography.Xml.EncryptedXml?displayProperty=nameWithType> başarısız olur ve <xref:System.Security.SecurityException> özel durumlar oluşturur. Bu değişiklik, Cngışıklı kullanan tüm işlevlerin gerekli izinlere sahip olması için gerekli onayları ekler.</span><span class="sxs-lookup"><span data-stu-id="59543-106">As a result, partial trust apps that successfully used <xref:System.Security.Cryptography.Xml.EncryptedXml?displayProperty=nameWithType> began to fail and throw <xref:System.Security.SecurityException> exceptions.This change adds the required asserts so that all functions using CngLightup have the required permissions.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="59543-107">Öneri</span><span class="sxs-lookup"><span data-stu-id="59543-107">Suggestion</span></span>

<span data-ttu-id="59543-108">.NET Framework 4.6.2 Bu değişiklik, kısmi güven uygulamalarınızı olumsuz yönde etkileirse, .NET Framework 4.7.1 ' ye yükseltin.</span><span class="sxs-lookup"><span data-stu-id="59543-108">If this change in the .NET Framework 4.6.2 has negatively impacted your partial trust apps, upgrade to the .NET Framework 4.7.1.</span></span>

| <span data-ttu-id="59543-109">Name</span><span class="sxs-lookup"><span data-stu-id="59543-109">Name</span></span>    | <span data-ttu-id="59543-110">Değer</span><span class="sxs-lookup"><span data-stu-id="59543-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="59543-111">Kapsam</span><span class="sxs-lookup"><span data-stu-id="59543-111">Scope</span></span>   |<span data-ttu-id="59543-112">Edge</span><span class="sxs-lookup"><span data-stu-id="59543-112">Edge</span></span>|
|<span data-ttu-id="59543-113">Sürüm</span><span class="sxs-lookup"><span data-stu-id="59543-113">Version</span></span>|<span data-ttu-id="59543-114">4.6.2</span><span class="sxs-lookup"><span data-stu-id="59543-114">4.6.2</span></span>|
|<span data-ttu-id="59543-115">Tür</span><span class="sxs-lookup"><span data-stu-id="59543-115">Type</span></span>|<span data-ttu-id="59543-116">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="59543-116">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="59543-117">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="59543-117">Affected APIs</span></span>

- <xref:System.Security.Cryptography.DSACng.%23ctor(System.Security.Cryptography.CngKey)>
- <xref:System.Security.Cryptography.DSACng.Key?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.DSACng.LegalKeySizes?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.DSACng.CreateSignature(System.Byte[])?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.DSACng.VerifySignature(System.Byte[],System.Byte[])?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RSACng.%23ctor(System.Security.Cryptography.CngKey)>
- <xref:System.Security.Cryptography.RSACng.Key?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RSACng.Decrypt(System.Byte[],System.Security.Cryptography.RSAEncryptionPadding)?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RSACng.SignHash(System.Byte[],System.Security.Cryptography.HashAlgorithmName,System.Security.Cryptography.RSASignaturePadding)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Security.Cryptography.DSACng.#ctor(System.Security.Cryptography.CngKey)`
- `P:System.Security.Cryptography.DSACng.Key`
- `P:System.Security.Cryptography.DSACng.LegalKeySizes`
- `M:System.Security.Cryptography.DSACng.CreateSignature(System.Byte[])`
- `M:System.Security.Cryptography.DSACng.VerifySignature(System.Byte[],System.Byte[])`
- `M:System.Security.Cryptography.RSACng.#ctor(System.Security.Cryptography.CngKey)`
- `P:System.Security.Cryptography.RSACng.Key`
- `M:System.Security.Cryptography.RSACng.Decrypt(System.Byte[],System.Security.Cryptography.RSAEncryptionPadding)`
- `M:System.Security.Cryptography.RSACng.SignHash(System.Byte[],System.Security.Cryptography.HashAlgorithmName,System.Security.Cryptography.RSASignaturePadding)`

-->
