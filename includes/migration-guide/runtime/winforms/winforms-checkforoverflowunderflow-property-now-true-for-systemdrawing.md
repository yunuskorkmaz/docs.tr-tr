---
ms.openlocfilehash: 8b2a01eb6dfdd5bd2bcbef6014d4edeb3ec82ac1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "66379629"
---
### <a name="winforms-checkforoverflowunderflow-property-is-now-true-for-systemdrawing"></a>WinForm'ın CheckForOverflowUnderflow özelliği için System.Drawing geçerlidir

|   |   |
|---|---|
|Ayrıntılar|System.Drawing.dll derleme CheckForOverflowUnderflow özellik ayarlanmışsa true.|
|Öneri|Daha önce taşmalar oluştuğunda, sonuç sessizce kesilebilir. Artık bir <xref:System.OverflowException?displayProperty=name> özel durumu oluşturulur.|
|Kapsam|Kenar|
|Sürüm|4,5|
|Tür|Çalışma zamanı|
