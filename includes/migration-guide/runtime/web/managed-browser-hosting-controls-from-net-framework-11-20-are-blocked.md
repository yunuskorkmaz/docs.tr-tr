---
ms.openlocfilehash: 83d3f24680531d1e447f047151a28c98ce0da04b
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620670"
---
### <a name="managed-browser-hosting-controls-from-the-net-framework-11-and-20-are-blocked"></a>.NET Framework 1,1 ve 2,0 ' den yönetilen tarayıcı barındıran denetimler engelleniyor

#### <a name="details"></a>Ayrıntılar

Bu kontrollerin barındırılması Internet Explorer'da engellenir.

#### <a name="suggestion"></a>Öneri

Internet Explorer tarayıcı barındırma kontrollerini kullanan bir uygulamayı başlatmakta başarısız olacaktır. Önceki davranış, kayıt defteri alt anahtarının EnableIEHosting değerini <code>HKLM/SOFTWARE/MICROSOFT/.NETFramework</code> <code>1</code> x86 sistemleri için ve x64 sistemlerinde 32 bitlik süreçler için ve <code>EnableIEHosting</code> kayıt defteri alt anahtarının değerini <code>HKLM/SOFTWARE/Wow6432Node/Microsoft/.NETFramework</code> <code>1</code> x64 sistemlerinde 64 bit işlemlere ayarlayarak geri yüklenebilir.

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |İkincil|
|Sürüm|4,5|
|Tür|Çalışma Zamanı|
