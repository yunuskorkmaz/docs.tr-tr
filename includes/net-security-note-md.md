---
ms.openlocfilehash: 8b0edd9a49ca431355ab4f57fa041c5d1756d7eb
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/06/2020
ms.locfileid: "87855678"
---
> [!CAUTION]
> <span data-ttu-id="16709-101">Kod erişim güvenliği (CAS) ve kısmen güvenilen kod</span><span class="sxs-lookup"><span data-stu-id="16709-101">Code Access Security (CAS) and Partially Trusted Code</span></span>
>
> <span data-ttu-id="16709-102">.NET Framework, Kod Erişimi Güvenliği (CAS) olarak adlandırılan ve aynı uygulamada çalıştırılan farklı kodlara farklı güven düzeyleri uygulayan bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="16709-102">The .NET Framework provides a mechanism for the enforcement of varying levels of trust on different code running in the same application called Code Access Security (CAS).</span></span>
>
> <span data-ttu-id="16709-103">**CA 'LAR .NET Core, .NET 5 veya sonraki sürümlerde desteklenmez. CA 'LAR 7,0 ' den sonraki C# sürümleri tarafından desteklenmez.**</span><span class="sxs-lookup"><span data-stu-id="16709-103">**CAS is not supported in .NET Core, .NET 5, or later versions. CAS is not supported by versions of C# later than 7.0.**</span></span>
>
> <span data-ttu-id="16709-104">.NET Framework içindeki CA 'LAR, kod kaynağına veya diğer kimlik özelliklerine göre güvenlik sınırları zorlama mekanizması olarak kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="16709-104">CAS in .NET Framework should not be used as a mechanism for enforcing security boundaries based on code origination or other identity aspects.</span></span> <span data-ttu-id="16709-105">CA 'LAR ve güvenlik saydam kod, kısmen güvenilen koda sahip bir güvenlik sınırı olarak desteklenmez, özellikle bilinmeyen kaynak kodu.</span><span class="sxs-lookup"><span data-stu-id="16709-105">CAS and Security-Transparent Code are not supported as a security boundary with partially trusted code, especially code of unknown origin.</span></span> <span data-ttu-id="16709-106">Bilinmeyen kaynaklardan gelen kodların, alternatif güvenlik önlemleri alınmadan yüklenmesi ve yürütülmesi önerilmez.</span><span class="sxs-lookup"><span data-stu-id="16709-106">We advise against loading and executing code of unknown origins without putting alternative security measures in place.</span></span>
>
> <span data-ttu-id="16709-107">Bu ilke tüm .NET Framework sürümleri için geçerlidir, ancak Silverlight’ta bulunan .NET Framework için geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="16709-107">This policy applies to all versions of .NET Framework, but does not apply to the .NET Framework included in Silverlight.</span></span>
