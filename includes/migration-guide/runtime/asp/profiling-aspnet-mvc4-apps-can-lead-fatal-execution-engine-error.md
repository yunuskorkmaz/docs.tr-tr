---
ms.openlocfilehash: 439a4976482639cd2e4e17315ec1a53ca54aa477
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67803267"
---
### <a name="profiling-aspnet-mvc4-apps-can-lead-to-fatal-execution-engine-error"></a>MVC4 uygulamaları ASP.Net profil oluşturma Ölümcül Yürütme Motoru Hatasına yol açabilir

|   |   |
|---|---|
|Ayrıntılar|NGEN /Profil montajları kullanan profilciler, başlangıç ASP.NET MVC4 uygulamalarında profillenmiş olarak 'Fatal Execution Engine Exception' ile çökebilir|
|Öneri|Bu sorun .NET Framework 4.5.2'de giderilmiştir. Alternatif olarak, profil oluşturucu olay maskesini belirterek <code>COR_PRF_DISABLE_ALL_NGEN_IMAGES</code> bu sorunu önleyebilir.|
|Kapsam|Edge|
|Sürüm|4,5|
|Tür|Çalışma Zamanı|
