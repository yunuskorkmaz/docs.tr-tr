---
ms.openlocfilehash: 0dfc87201b9b31cd9d936f2c965c7d0ca0140cab
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67858473"
---
### <a name="x509certificate2tostringboolean-does-not-throw-now-when-net-cannot-handle-the-certificate"></a><span data-ttu-id="97ab1-101">X509Certificate2.ToString(Boolean) şimdi atmıyor .NET sertifikayı işleyemiyor</span><span class="sxs-lookup"><span data-stu-id="97ab1-101">X509Certificate2.ToString(Boolean) does not throw now when .NET cannot handle the certificate</span></span>

|   |   |
|---|---|
|<span data-ttu-id="97ab1-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="97ab1-102">Details</span></span>|<span data-ttu-id="97ab1-103">.NET Framework 4.5.2 ve önceki sürümlerinde, <code>true</code> ayrıntılı parametre için geçirilen ve .NET Framework tarafından desteklenmeyen sertifikalar yüklüyse, bu yöntem atılır.</span><span class="sxs-lookup"><span data-stu-id="97ab1-103">In .NET Framework 4.5.2 and earlier versions, this method would throw if <code>true</code> was passed for the verbose parameter and there were certificates installed that weren't supported by the .NET Framework.</span></span> <span data-ttu-id="97ab1-104">Şimdi, yöntem başarılı olacak ve sertifikanın erişilemeyen bölümlerini atlayan geçerli bir dize döndürecek.</span><span class="sxs-lookup"><span data-stu-id="97ab1-104">Now, the method will succeed and return a valid string that omits the inaccessible portions of the certificate.</span></span>|
|<span data-ttu-id="97ab1-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="97ab1-105">Suggestion</span></span>|<span data-ttu-id="97ab1-106">Bağlı olarak herhangi <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString(System.Boolean)?displayProperty=nameWithType> bir kod, döndürülen dize, API'nin daha önce atmış olacağı bazı durumlarda bazı sertifika verilerini (ortak anahtar, özel anahtar ve uzantılar gibi) dışlayabilen bir şekilde güncelleştirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="97ab1-106">Any code depending on <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString(System.Boolean)?displayProperty=nameWithType> should be updated to expect that the returned string may exclude some certificate data (such as public key, private key, and extensions) in some cases in which the API would have previously thrown.</span></span>|
|<span data-ttu-id="97ab1-107">Kapsam</span><span class="sxs-lookup"><span data-stu-id="97ab1-107">Scope</span></span>|<span data-ttu-id="97ab1-108">Edge</span><span class="sxs-lookup"><span data-stu-id="97ab1-108">Edge</span></span>|
|<span data-ttu-id="97ab1-109">Sürüm</span><span class="sxs-lookup"><span data-stu-id="97ab1-109">Version</span></span>|<span data-ttu-id="97ab1-110">4.6</span><span class="sxs-lookup"><span data-stu-id="97ab1-110">4.6</span></span>|
|<span data-ttu-id="97ab1-111">Tür</span><span class="sxs-lookup"><span data-stu-id="97ab1-111">Type</span></span>|<span data-ttu-id="97ab1-112">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="97ab1-112">Runtime</span></span>|
|<span data-ttu-id="97ab1-113">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="97ab1-113">Affected APIs</span></span>|<ul><li><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString(System.Boolean)?displayProperty=nameWithType></li></ul>|
