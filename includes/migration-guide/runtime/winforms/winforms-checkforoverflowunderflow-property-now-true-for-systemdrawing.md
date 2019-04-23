---
ms.openlocfilehash: 8b2a01eb6dfdd5bd2bcbef6014d4edeb3ec82ac1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59805321"
---
### <a name="winforms-checkforoverflowunderflow-property-is-now-true-for-systemdrawing"></a>WinForm'ın CheckForOverflowUnderflow özelliği için System.Drawing geçerlidir

|   |   |
|---|---|
|Ayrıntılar|System.Drawing.dll derleme CheckForOverflowUnderflow özellik ayarlanmışsa true.|
|Öneri|Daha önce taşmalar oluştuğunda, sonuç sessizce kesilebilir. Artık bir <xref:System.OverflowException?displayProperty=name> özel durumu oluşturulur.|
|Kapsam|Kenar|
|Sürüm|4,5|
|Tür|Çalışma zamanı|
