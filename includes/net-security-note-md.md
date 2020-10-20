---
ms.openlocfilehash: 3164233f1ac056de385faa119143d75d3c2dc50c
ms.sourcegitcommit: 67ebdb695fd017d79d9f1f7f35d145042d5a37f7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/20/2020
ms.locfileid: "92224341"
---
> [!CAUTION]
> <span data-ttu-id="b99a2-101">Kod erişim güvenliği (CAS) ve kısmen güvenilen kod</span><span class="sxs-lookup"><span data-stu-id="b99a2-101">Code Access Security (CAS) and Partially Trusted Code</span></span>
>
> <span data-ttu-id="b99a2-102">.NET Framework, Kod Erişimi Güvenliği (CAS) olarak adlandırılan ve aynı uygulamada çalıştırılan farklı kodlara farklı güven düzeyleri uygulayan bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="b99a2-102">The .NET Framework provides a mechanism for the enforcement of varying levels of trust on different code running in the same application called Code Access Security (CAS).</span></span>
>
> <span data-ttu-id="b99a2-103">**CA 'LAR .NET Core, .NET 5 veya sonraki sürümlerde desteklenmez. CA 'LAR 7,0 ' den sonraki C# sürümleri tarafından desteklenmez.**</span><span class="sxs-lookup"><span data-stu-id="b99a2-103">**CAS is not supported in .NET Core, .NET 5, or later versions. CAS is not supported by versions of C# later than 7.0.**</span></span>
>
> <span data-ttu-id="b99a2-104">.NET Framework içindeki CA 'LAR, kod kaynağına veya diğer kimlik özelliklerine göre güvenlik sınırları zorlama mekanizması olarak kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="b99a2-104">CAS in .NET Framework should not be used as a mechanism for enforcing security boundaries based on code origination or other identity aspects.</span></span> <span data-ttu-id="b99a2-105">CA 'LAR ve Security-Transparent kodu, kısmen güvenilen koda sahip bir güvenlik sınırı olarak desteklenmez, özellikle bilinmeyen kaynak kodu.</span><span class="sxs-lookup"><span data-stu-id="b99a2-105">CAS and Security-Transparent Code are not supported as a security boundary with partially trusted code, especially code of unknown origin.</span></span> <span data-ttu-id="b99a2-106">Bilinmeyen kaynaklardan gelen kodların, alternatif güvenlik önlemleri alınmadan yüklenmesi ve yürütülmesi önerilmez.</span><span class="sxs-lookup"><span data-stu-id="b99a2-106">We advise against loading and executing code of unknown origins without putting alternative security measures in place.</span></span> <span data-ttu-id="b99a2-107">.NET Framework, CAS korumalı alanında keşfedilmiş tüm ayrıcalık yükselmesi açıklarına yönelik güvenlik düzeltme ekleri yayınmayacak.</span><span class="sxs-lookup"><span data-stu-id="b99a2-107">.NET Framework will not issue security patches for any elevation-of-privilege exploits that might be discovered against the CAS sandbox.</span></span>
>
> <span data-ttu-id="b99a2-108">Bu ilke tüm .NET Framework sürümleri için geçerlidir, ancak Silverlight’ta bulunan .NET Framework için geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="b99a2-108">This policy applies to all versions of .NET Framework, but does not apply to the .NET Framework included in Silverlight.</span></span>
