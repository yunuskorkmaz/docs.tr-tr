---
ms.openlocfilehash: 3db4b0b42a154c5bc9296889ae9dc4b7ecf1e58e
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556235"
---
### <a name="allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported"></a>AllowUpdateChildControlIndexForTabControls uyumluluk anahtarı desteklenmiyor

`Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls`Uyumluluk anahtarı .NET Framework 4,6 ve sonraki sürümlerde Windows Forms desteklenir, ancak .NET Core veya .net 5,0 ve sonrasında desteklenmez.

#### <a name="change-description"></a>Açıklamayı Değiştir

.NET Framework 4,6 ve sonraki sürümlerde, bir sekmeyi seçmek denetim koleksiyonunu yeniden sıralar. `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls`Uyumluluk anahtarı, bu davranış istenmeyen olduğunda bir uygulamanın bu yeniden sıralamayı atlamasına izin verir.

.NET Core ve .NET 5,0 ve üzeri sürümlerde, `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` anahtar desteklenmez.

#### <a name="version-introduced"></a>Sunulan sürüm

3,0

#### <a name="recommended-action"></a>Önerilen eylem

Anahtarı kaldırın. Anahtar desteklenmez ve alternatif bir işlev kullanılamaz.

#### <a name="category"></a>Kategori

Windows Forms

#### <a name="affected-apis"></a>Etkilenen API’ler

- Hiçbiri

<!-- 

#### Affected APIs

- Not detectable via API analysis

-->
