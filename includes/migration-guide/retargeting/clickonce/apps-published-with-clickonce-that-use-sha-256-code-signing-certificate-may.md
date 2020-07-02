---
ms.openlocfilehash: 416590c7bd959eea011b7e7c5db48f22d349d0f5
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615746"
---
### <a name="apps-published-with-clickonce-that-use-a-sha-256-code-signing-certificate-may-fail-on-windows-2003"></a>SHA-256 kod imzalama sertifikası kullanan ClickOnce ile yayımlanan uygulamalar Windows 2003 ' de başarısız olabilir

#### <a name="details"></a>Ayrıntılar

Yürütülebilir dosya SHA256 ile imzalanır. Daha önce, kod imzalama sertifikasının SHA-1 veya SHA-256 olmasına bakılmaksızın SHA1 ile imzalanmıştı. Bu için geçerlidir:

- Visual Studio 2012 veya üzeri ile oluşturulan tüm uygulamalar.
- .NET Framework 4,5 olan sistemlerde Visual Studio 2010 veya daha önceki bir sürümü ile oluşturulan uygulamalar.
Ayrıca, .NET Framework 4,5 veya üzeri bir sürüm varsa, derlenen .NET Framework sürümden bağımsız olarak SHA-256 sertifikaları için de ClickOnce bildirimi de 256 imzalanır.

#### <a name="suggestion"></a>Öneri

ClickOnce yürütülebiliri imzalanırken değişiklik yalnızca Windows Server 2003 sistemlerini etkiler; Bu, KB 938397 ' nin yüklü olmasını gerektirir. Bir uygulama .NET Framework 4,0 veya önceki sürümleri hedefliyorsa, .NET Framework 4,5 veya sonraki bir sürümde bir çalışma zamanı bağımlılığı sunarak, bildirimi SHA-256 ile imzalamada değişiklik.

| Name    | Değer       |
|:--------|:------------|
| Kapsam   | Edge        |
| Sürüm | 4,5         |
| Tür    | Yeniden Hedefleme |
