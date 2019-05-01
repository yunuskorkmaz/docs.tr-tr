---
ms.openlocfilehash: 0dfc87201b9b31cd9d936f2c965c7d0ca0140cab
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61664546"
---
### <a name="x509certificate2tostringboolean-does-not-throw-now-when-net-cannot-handle-the-certificate"></a><span data-ttu-id="7d156-101">Artık .NET sertifika olduğunda işleyemiyor X509Certificate2.ToString(Boolean) oluşturmaz</span><span class="sxs-lookup"><span data-stu-id="7d156-101">X509Certificate2.ToString(Boolean) does not throw now when .NET cannot handle the certificate</span></span>

|   |   |
|---|---|
|<span data-ttu-id="7d156-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="7d156-102">Details</span></span>|<span data-ttu-id="7d156-103">.NET Framework 4.5.2 ve önceki sürümlerinde, bu yöntem, alanlarına <code>true</code> ayrıntılı parametresi için geçirilen ve yüklü olan ve .NET Framework tarafından desteklenen olmayan sertifikalar.</span><span class="sxs-lookup"><span data-stu-id="7d156-103">In .NET Framework 4.5.2 and earlier versions, this method would throw if <code>true</code> was passed for the verbose parameter and there were certificates installed that weren't supported by the .NET Framework.</span></span> <span data-ttu-id="7d156-104">Şimdi, yöntem başarılı ve sertifika erişilemez kısımlarını atlayarak geçerli bir dize döndürür.</span><span class="sxs-lookup"><span data-stu-id="7d156-104">Now, the method will succeed and return a valid string that omits the inaccessible portions of the certificate.</span></span>|
|<span data-ttu-id="7d156-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="7d156-105">Suggestion</span></span>|<span data-ttu-id="7d156-106">Bağlı herhangi bir kod <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString(System.Boolean)?displayProperty=nameWithType> döndürülen dizeyi bazı sertifika verilerini (örneğin, ortak anahtar, özel anahtarı ve Uzantılar) hariç tutabilir, API daha önce oluşturulan bazı durumlarda beklediğiniz şekilde güncelleştirilmesi.</span><span class="sxs-lookup"><span data-stu-id="7d156-106">Any code depending on <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString(System.Boolean)?displayProperty=nameWithType> should be updated to expect that the returned string may exclude some certificate data (such as public key, private key, and extensions) in some cases in which the API would have previously thrown.</span></span>|
|<span data-ttu-id="7d156-107">Kapsam</span><span class="sxs-lookup"><span data-stu-id="7d156-107">Scope</span></span>|<span data-ttu-id="7d156-108">Kenar</span><span class="sxs-lookup"><span data-stu-id="7d156-108">Edge</span></span>|
|<span data-ttu-id="7d156-109">Sürüm</span><span class="sxs-lookup"><span data-stu-id="7d156-109">Version</span></span>|<span data-ttu-id="7d156-110">4.6</span><span class="sxs-lookup"><span data-stu-id="7d156-110">4.6</span></span>|
|<span data-ttu-id="7d156-111">Tür</span><span class="sxs-lookup"><span data-stu-id="7d156-111">Type</span></span>|<span data-ttu-id="7d156-112">Çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="7d156-112">Runtime</span></span>|
|<span data-ttu-id="7d156-113">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="7d156-113">Affected APIs</span></span>|<ul><li><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString(System.Boolean)?displayProperty=nameWithType></li></ul>|
