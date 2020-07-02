---
ms.openlocfilehash: 4a65e721e5639f12445a9a44f46baa0d26898a88
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615752"
---
### <a name="il-ret-not-allowed-in-a-try-region"></a>Bir TRY bölgesinde Il ret 'ye izin verilmiyor

#### <a name="details"></a>Ayrıntılar

JıT64 Just-In-Time derleyicisinden farklı olarak, RyuJIT (.NET Framework 4,6 ' de kullanılır), bir TRY bölgesinde Il ret yönergesine izin vermez. Bir TRY bölgesinden dönerek ECMA-335 belirtimine izin verilmez ve bilinen yönetilen derleyici böyle bir Il oluşturmaz. Ancak, JıT64 derleyicisi, yansıma yayma kullanılarak oluşturulduysa bu Il 'yi yürütür.

#### <a name="suggestion"></a>Öneri

Bir uygulama bir TRY bölgesinde ret Opcode içeren Il oluşturuyorsa, uygulama eski JıT 'i kullanmak için .NET Framework 4,5 ' i hedefleyebilir ve bu kesmeyi önleyin. Alternatif olarak, üretilen IL, TRY bölgesinden sonra döndürülecek şekilde güncelleştirilebilen olabilir.

| Name    | Değer       |
|:--------|:------------|
| Kapsam   | Edge        |
| Sürüm | 4.6         |
| Tür    | Yeniden Hedefleme |
