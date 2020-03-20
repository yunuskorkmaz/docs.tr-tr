---
ms.openlocfilehash: da79a19b3276f6fd2d679eb98406dd85e2a19948
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "70997741"
---
### <a name="apps-published-with-clickonce-that-use-a-sha-256-code-signing-certificate-may-fail-on-windows-2003"></a>Sha-256 kod imzalama sertifikası kullanan ClickOnce ile yayınlanan uygulamalar Windows 2003'te başarısız olabilir

|   |   |
|---|---|
|Ayrıntılar|Yürütülebilir SHA256 ile imzalanır. Daha önce, kod imzalama sertifikasısha-1 veya SHA-256 olup olmadığına bakılmaksızın SHA1 ile imzalanmıştır. Bu, aşağıdakiler için geçerlidir:<ul><li>Tüm uygulamalar Visual Studio 2012 veya sonrası ile oluşturulmuş.</li><li>.NET Framework 4.5 mevcut sistemlerde Visual Studio 2010 veya daha önceki sistemlerde yapılan uygulamalar.</li></ul>Ayrıca, .NET Framework 4.5 veya daha sonra varsa, ClickOnce manifestosu, derlendiği .NET Framework sürümüne bakılmaksızın SHA-256 sertifikaları için SHA-256 ile de imzalanır.|
|Öneri|ClickOnce yürütülebilir imzalama değişikliği yalnızca Windows Server 2003 sistemlerini etkiler; kb 938397 yüklü olması gerekir. Bir uygulama .NET Framework 4.0 veya önceki sürümleri hedeflediğinde bile manifestoyu SHA-256 ile imzalamadaki değişiklik,.NET Framework 4.5 veya daha sonraki sürümlere çalışma zamanı bağımlılığı nı ortaya çıkartır.|
|Kapsam|Edge|
|Sürüm|4,5|
|Tür|Yeniden Hedefleme|
