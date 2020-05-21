---
ms.openlocfilehash: e1c55eab0b968daab7322350e201b49149e63215
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721315"
---
### <a name="allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported"></a>AllowUpdateChildControlIndexForTabControls uyumluluk anahtarı desteklenmiyor

`Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls`Uyumluluk anahtarı .NET Framework 4,6 ve sonraki sürümlerde Windows Forms desteklenir, ancak .NET Core 3,0 ' den başlayarak Windows Forms desteklenmez.

#### <a name="change-description"></a>Açıklamayı Değiştir

.NET Framework 4,6 ve sonraki sürümlerde, bir sekmeyi seçmek denetim koleksiyonunu yeniden sıralar. `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls`Uyumluluk anahtarı, bu davranış istenmeyen olduğunda bir uygulamanın bu yeniden sıralamayı atlamasına izin verir.

.NET Core 'da, `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` anahtar desteklenmez.

#### <a name="version-introduced"></a>Sunulan sürüm

3,0 Preview 9

#### <a name="recommended-action"></a>Önerilen eylem

Anahtarı kaldırın. Anahtar desteklenmez ve alternatif bir işlev kullanılamaz.

#### <a name="category"></a>Kategori

Windows Forms

#### <a name="affected-apis"></a>Etkilenen API’ler

- Yok

<!-- 

#### Affected APIs

- Not detectable via API analysis

-->
