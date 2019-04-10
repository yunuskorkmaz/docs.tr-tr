---
ms.openlocfilehash: 8b2a01eb6dfdd5bd2bcbef6014d4edeb3ec82ac1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235847"
---
### <a name="winforms-checkforoverflowunderflow-property-is-now-true-for-systemdrawing"></a>WinForm'ın CheckForOverflowUnderflow özelliği için System.Drawing geçerlidir

|   |   |
|---|---|
|Ayrıntılar|System.Drawing.dll derleme CheckForOverflowUnderflow özellik ayarlanmışsa true.|
|Öneri|Daha önce taşmalar oluştuğunda, sonuç sessizce kesilebilir. Artık bir <xref:System.OverflowException?displayProperty=name> özel durumu oluşturulur.|
|Kapsam|Kenar|
|Sürüm|4,5|
|Tür|Çalışma zamanı|
