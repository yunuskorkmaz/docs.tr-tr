---
ms.openlocfilehash: f70452cbadc8927521f0fcfda693586c277e4d0f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "70041157"
---
> [!CAUTION]
> <span data-ttu-id="9a169-101">Kod Erişimi Güvenliği ve Kısmen Güvenilen Kod</span><span class="sxs-lookup"><span data-stu-id="9a169-101">Code Access Security and Partially Trusted Code</span></span>
>
> <span data-ttu-id="9a169-102">.NET Framework, Kod Erişimi Güvenliği (CAS) olarak adlandırılan ve aynı uygulamada çalıştırılan farklı kodlara farklı güven düzeyleri uygulayan bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="9a169-102">The .NET Framework provides a mechanism for the enforcement of varying levels of trust on different code running in the same application called Code Access Security (CAS).</span></span>  <span data-ttu-id="9a169-103">.NET Framework’te Kod Erişimi Güvenliği, kod kaynağına veya diğer kimlik özelliklerine dayanan güvenlik sınırları uygulamaya yönelik bir mekanizma olarak kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="9a169-103">Code Access Security in .NET Framework should not  be used as a mechanism for enforcing security boundaries based on code origination or other identity aspects.</span></span> <span data-ttu-id="9a169-104">Kod Erişimi Güvenliği ve Güvenlik Açısından Saydam Kodun, kısmen güvenilir kodlarla birlikte (özellikle bilinmeyen kaynaklardan gelen kodlar) güvenlik sınırı olarak desteklenmeyeceğini duyurmak amacıyla kılavuzumuzu güncelleştiriyoruz.</span><span class="sxs-lookup"><span data-stu-id="9a169-104">We are updating our guidance to reflect that Code Access Security and Security-Transparent Code will not be supported as a security boundary with partially trusted code, especially code of unknown origin.</span></span> <span data-ttu-id="9a169-105">Bilinmeyen kaynaklardan gelen kodların, alternatif güvenlik önlemleri alınmadan yüklenmesi ve yürütülmesi önerilmez.</span><span class="sxs-lookup"><span data-stu-id="9a169-105">We advise against loading and executing code of unknown origins without putting alternative security measures in place.</span></span>
>
> <span data-ttu-id="9a169-106">Bu ilke tüm .NET Framework sürümleri için geçerlidir, ancak Silverlight’ta bulunan .NET Framework için geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="9a169-106">This policy applies to all versions of .NET Framework, but does not apply to the .NET Framework included in Silverlight.</span></span>
