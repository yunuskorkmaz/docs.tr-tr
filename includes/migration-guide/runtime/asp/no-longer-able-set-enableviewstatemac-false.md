---
ms.openlocfilehash: dbe96abebdc61fae469f7727673e6fcb93cbc739
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59236667"
---
### <a name="no-longer-able-to-set-enableviewstatemac-to-false"></a>Artık şunları EnableViewStateMac false olarak ayarlayın.

|   |   |
|---|---|
|Ayrıntılar|ASP.NET belirlemek geliştiriciler artık sağlayan <code>&lt;pages enableViewStateMac=&quot;false&quot;/&gt;</code> veya <code>&lt;@Page EnableViewStateMac=&quot;false&quot; %&gt;</code>. Görünüm durumu ileti kimlik doğrulama kodu (MAC), artık katıştırılmış görünüm durumuna sahip tüm istekler için zorlanır. Yalnızca açıkça EnableViewStateMac özellik kümesine uygulamaların <code>false</code> etkilenir.|
|Öneri|EnableViewStateMac varsayıldı, doğru olmasını ve ortaya çıkan MAC hataları çözümlenemedi. (açıklandığı şekilde [bu kılavuz](https://support.microsoft.com/kb/2915218), MAC hataları neden olan özelliklerini bağlı olarak birden çok çözümler içerir).|
|Kapsam|Ana|
|Sürüm|4.5.2|
|Tür|Çalışma zamanı|
