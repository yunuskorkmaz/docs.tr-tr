---
ms.openlocfilehash: c967a5b09b5e9ffeee7bff046f0c96469bc7fb02
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615745"
---
### <a name="clickonce-supports-sha-256-on-40-targeted-apps"></a>ClickOnce, 4,0 hedefli uygulamalarda SHA-256 ' i destekler

#### <a name="details"></a>Ayrıntılar

Daha önce, SHA-256 ile imzalanmış bir sertifika olan bir ClickOnce uygulaması, uygulama ' i 4,0 hedeflese bile .NET Framework 4,5 veya üzeri bir sürümü gerektirir. Şimdi, .NET Framework 4,0-hedeflenen ClickOnce uygulamaları SHA-256 ile imzalanmış olsa bile .NET Framework 4,0 üzerinde çalışabilir.

#### <a name="suggestion"></a>Öneri

Bu değişiklik, bu bağımlılığı ortadan kaldırır ve .NET Framework 4 ve önceki sürümleri hedefleyen ClickOnce uygulamalarını imzalamak için SHA-256 sertifikalarının kullanılmasına izin verir.

| Name    | Değer       |
|:--------|:------------|
| Kapsam   | İkincil       |
| Sürüm | 4.6         |
| Tür    | Yeniden Hedefleme |
