---
ms.openlocfilehash: 38c35f3f6f2262d06409690d2326d9b982e1ec86
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59805225"
---
### <a name="managed-browser-hosting-controls-from-the-net-framework-11-and-20-are-blocked"></a>Yönetilen tarayıcı barındırma denetimleri .NET Framework 1.1 ve 2.0 engellenir

|   |   |
|---|---|
|Ayrıntılar|Bu kontrollerin barındırılması Internet Explorer'da engellenir.|
|Öneri|Internet Explorer tarayıcı barındırma kontrollerini kullanan bir uygulamayı başlatmakta başarısız olacaktır. Kayıt defteri alt anahtarı değerini ayarlayarak önceki davranış geri yüklenebilir <code>HKLM/SOFTWARE/MICROSOFT/.NETFramework</code> için <code>1</code> x86 için sistemleri ve x64 32 bitlik işlemler için sistemleri ve ayarlayarak <code>EnableIEHosting</code> kayıtdefterialtanahtarınındeğerini<code>HKLM/SOFTWARE/Wow6432Node/Microsoft/.NETFramework</code>için <code>1</code> x64 64 bitlik işlemler için sistemler.|
|Kapsam|İkincil|
|Sürüm|4,5|
|Tür|Çalışma zamanı|
