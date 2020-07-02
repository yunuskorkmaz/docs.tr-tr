---
ms.openlocfilehash: 51208762cea2a5688c5d43e5d444d4e014e5f0b4
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621429"
---
### <a name="x509certificate2tostringboolean-does-not-throw-now-when-net-cannot-handle-the-certificate"></a><span data-ttu-id="3e5ba-101">.NET sertifikayı işleyemezse X509Certificate2. ToString (Boolean) şimdi oluşturmaz</span><span class="sxs-lookup"><span data-stu-id="3e5ba-101">X509Certificate2.ToString(Boolean) does not throw now when .NET cannot handle the certificate</span></span>

#### <a name="details"></a><span data-ttu-id="3e5ba-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="3e5ba-102">Details</span></span>

<span data-ttu-id="3e5ba-103">.NET Framework 4.5.2 ve önceki sürümlerde, bu yöntem <code>true</code> verbose parametresi için başarılı olduysa ve .NET Framework tarafından desteklenmeyen sertifikalar yüklüyse, bu yöntem oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3e5ba-103">In .NET Framework 4.5.2 and earlier versions, this method would throw if <code>true</code> was passed for the verbose parameter and there were certificates installed that weren't supported by the .NET Framework.</span></span> <span data-ttu-id="3e5ba-104">Şimdi Yöntem başarılı olur ve sertifikanın erişilemeyen bölümlerini atlayacak geçerli bir dize döndürür.</span><span class="sxs-lookup"><span data-stu-id="3e5ba-104">Now, the method will succeed and return a valid string that omits the inaccessible portions of the certificate.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="3e5ba-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="3e5ba-105">Suggestion</span></span>

<span data-ttu-id="3e5ba-106"><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString(System.Boolean)?displayProperty=nameWithType>Döndürülen dizenin, API 'nin daha önce oluşturulduğu bazı durumlarda bazı sertifika verilerini (ortak anahtar, özel anahtar ve uzantılar gibi) Dışlamayacağını beklemek için güncelleştirilmeleri gerekir.</span><span class="sxs-lookup"><span data-stu-id="3e5ba-106">Any code depending on <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString(System.Boolean)?displayProperty=nameWithType> should be updated to expect that the returned string may exclude some certificate data (such as public key, private key, and extensions) in some cases in which the API would have previously thrown.</span></span>

| <span data-ttu-id="3e5ba-107">Name</span><span class="sxs-lookup"><span data-stu-id="3e5ba-107">Name</span></span>    | <span data-ttu-id="3e5ba-108">Değer</span><span class="sxs-lookup"><span data-stu-id="3e5ba-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="3e5ba-109">Kapsam</span><span class="sxs-lookup"><span data-stu-id="3e5ba-109">Scope</span></span>   |<span data-ttu-id="3e5ba-110">Edge</span><span class="sxs-lookup"><span data-stu-id="3e5ba-110">Edge</span></span>|
|<span data-ttu-id="3e5ba-111">Sürüm</span><span class="sxs-lookup"><span data-stu-id="3e5ba-111">Version</span></span>|<span data-ttu-id="3e5ba-112">4.6</span><span class="sxs-lookup"><span data-stu-id="3e5ba-112">4.6</span></span>|
|<span data-ttu-id="3e5ba-113">Tür</span><span class="sxs-lookup"><span data-stu-id="3e5ba-113">Type</span></span>|<span data-ttu-id="3e5ba-114">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="3e5ba-114">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="3e5ba-115">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="3e5ba-115">Affected APIs</span></span>

-<xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString(System.Boolean)?displayProperty=nameWithType></li></ul>|
