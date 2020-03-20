---
ms.openlocfilehash: dbe96abebdc61fae469f7727673e6fcb93cbc739
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67803159"
---
### <a name="no-longer-able-to-set-enableviewstatemac-to-false"></a>EnableViewStateMac'i artık false olarak ayarlayama

|   |   |
|---|---|
|Ayrıntılar|ASP.NET artık geliştiricilerin <code>&lt;pages enableViewStateMac=&quot;false&quot;/&gt;</code> belirtmesine veya <code>&lt;@Page EnableViewStateMac=&quot;false&quot; %&gt;</code>. Görünüm durumu iletikimlik doğrulama kodu (MAC) şimdi katıştırılmış görünüm durumu olan tüm istekler için zorlanır. Yalnızca EnableViewStateMac özelliğini <code>false</code> açıkça ayarlayan uygulamalar etkilenir.|
|Öneri|EnableViewStateMac'in doğru olduğu varsayılmalıdır ve ortaya çıkan MAC hataları çözülmelidir [(bu kılavuzda](https://support.microsoft.com/kb/2915218)açıklandığı gibi, MAC hatalarına neyin neden olduğuna bağlı olarak birden çok çözünürlük içerir).|
|Kapsam|Ana|
|Sürüm|4.5.2|
|Tür|Çalışma Zamanı|
