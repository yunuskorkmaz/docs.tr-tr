---
ms.openlocfilehash: 1d01de4b978309e05a6036953f2a6909628a2480
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74644000"
---
### <a name="switchsystemwindowsformsallowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported"></a>Switch. System. Windows. Forms. Allowupdatechıldcontrolindexfortabcontrols uyumluluk anahtarı desteklenmiyor

`Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` uyumluluk anahtarı .NET Framework 4,6 ve sonraki sürümlerde Windows Forms desteklenir, ancak .NET Core 3,0 ' den itibaren Windows Forms desteklenmez.

#### <a name="change-description"></a>Açıklamayı Değiştir

.NET Framework 4,6 ve sonraki sürümlerde, bir sekmeyi seçmek denetim koleksiyonunu yeniden sıralar. `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` uyumluluk anahtarı, bu davranış istenmeyen olduğunda bir uygulamanın bu yeniden sıralamayı atlamasına izin verir.

.NET Core 'da `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` anahtarı desteklenmez.

#### <a name="version-introduced"></a>Sunulan sürüm

3,0 Preview 9

#### <a name="recommended-action"></a>Önerilen eylem

Anahtarı kaldırın. Anahtar desteklenmez ve alternatif bir işlev kullanılamaz.

#### <a name="category"></a>Kategori

Windows Forms

#### <a name="affected-apis"></a>Etkilenen API’ler

- Yok.

<!-- 

### Affected APIs

- Not detectable via API analysis

-->
