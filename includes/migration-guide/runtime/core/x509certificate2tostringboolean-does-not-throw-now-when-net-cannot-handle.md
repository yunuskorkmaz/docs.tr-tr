---
ms.openlocfilehash: 7f8f97adcca7e66fa5756212bb977daadd92b8b6
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496283"
---
### <a name="x509certificate2tostringboolean-does-not-throw-now-when-net-cannot-handle-the-certificate"></a><span data-ttu-id="2c50e-101">.NET sertifikayı işleyemezse X509Certificate2. ToString (Boolean) şimdi oluşturmaz</span><span class="sxs-lookup"><span data-stu-id="2c50e-101">X509Certificate2.ToString(Boolean) does not throw now when .NET cannot handle the certificate</span></span>

#### <a name="details"></a><span data-ttu-id="2c50e-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="2c50e-102">Details</span></span>

<span data-ttu-id="2c50e-103">.NET Framework 4.5.2 ve önceki sürümlerde, bu yöntem <code>true</code> verbose parametresi için başarılı olduysa ve .NET Framework tarafından desteklenmeyen sertifikalar yüklüyse, bu yöntem oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2c50e-103">In .NET Framework 4.5.2 and earlier versions, this method would throw if <code>true</code> was passed for the verbose parameter and there were certificates installed that weren't supported by the .NET Framework.</span></span> <span data-ttu-id="2c50e-104">Şimdi Yöntem başarılı olur ve sertifikanın erişilemeyen bölümlerini atlayacak geçerli bir dize döndürür.</span><span class="sxs-lookup"><span data-stu-id="2c50e-104">Now, the method will succeed and return a valid string that omits the inaccessible portions of the certificate.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="2c50e-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="2c50e-105">Suggestion</span></span>

<span data-ttu-id="2c50e-106"><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString(System.Boolean)?displayProperty=nameWithType>Döndürülen dizenin, API 'nin daha önce oluşturulduğu bazı durumlarda bazı sertifika verilerini (ortak anahtar, özel anahtar ve uzantılar gibi) Dışlamayacağını beklemek için güncelleştirilmeleri gerekir.</span><span class="sxs-lookup"><span data-stu-id="2c50e-106">Any code depending on <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString(System.Boolean)?displayProperty=nameWithType> should be updated to expect that the returned string may exclude some certificate data (such as public key, private key, and extensions) in some cases in which the API would have previously thrown.</span></span>

| <span data-ttu-id="2c50e-107">Name</span><span class="sxs-lookup"><span data-stu-id="2c50e-107">Name</span></span>    | <span data-ttu-id="2c50e-108">Değer</span><span class="sxs-lookup"><span data-stu-id="2c50e-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="2c50e-109">Kapsam</span><span class="sxs-lookup"><span data-stu-id="2c50e-109">Scope</span></span>   |<span data-ttu-id="2c50e-110">Edge</span><span class="sxs-lookup"><span data-stu-id="2c50e-110">Edge</span></span>|
|<span data-ttu-id="2c50e-111">Sürüm</span><span class="sxs-lookup"><span data-stu-id="2c50e-111">Version</span></span>|<span data-ttu-id="2c50e-112">4.6</span><span class="sxs-lookup"><span data-stu-id="2c50e-112">4.6</span></span>|
|<span data-ttu-id="2c50e-113">Tür</span><span class="sxs-lookup"><span data-stu-id="2c50e-113">Type</span></span>|<span data-ttu-id="2c50e-114">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="2c50e-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="2c50e-115">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="2c50e-115">Affected APIs</span></span>

- <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString(System.Boolean)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString(System.Boolean)`

-->
