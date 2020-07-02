---
ms.openlocfilehash: e9d34465970287ed94c0f0373ee4ae94d55aa1ff
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617267"
---
### <a name="machinekeyencode-and-machinekeydecode-methods-are-now-obsolete"></a>MachineKey. Encode ve MachineKey. kodunu çözme yöntemleri artık kullanılmıyor

#### <a name="details"></a>Ayrıntılar

Bu yöntemler artık kullanım dışıdır. Bu yöntemleri çağıran kodun derlemesi bir derleyici uyarısı meydana getirir.

#### <a name="suggestion"></a>Öneri

Önerilen alternatifler <xref:System.Web.Security.MachineKey.Protect(System.Byte[],System.String[])> ve ' dir <xref:System.Web.Security.MachineKey.Unprotect(System.Byte[],System.String[])> . Alternatif olarak, derleme uyarıları bastırılabilir veya eski bir derleyici kullanılarak kaçınılabilir. API 'Ler hala desteklenmektedir.

| Name    | Değer       |
|:--------|:------------|
| Kapsam   | İkincil       |
| Sürüm | 4,5         |
| Tür    | Yeniden Hedefleme |

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Web.Security.MachineKey.Encode(System.Byte[],System.Web.Security.MachineKeyProtection)?displayProperty=nameWithType>
- <xref:System.Web.Security.MachineKey.Decode(System.String,System.Web.Security.MachineKeyProtection)?displayProperty=nameWithType>
