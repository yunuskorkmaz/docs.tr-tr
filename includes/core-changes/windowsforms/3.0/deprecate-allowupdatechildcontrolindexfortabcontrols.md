---
ms.openlocfilehash: 7e76c32ddeb50eaf1ee93d7cf3cac7469187cc41
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937075"
---
### <a name="allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported"></a>AllowUpdateChildControlIndexForTabControls uyumluluk anahtarı desteklenmiyor

Uyumluluk `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` anahtarı .NET Framework 4.6 ve sonraki sürümlerde Windows Formlar'da desteklenir, ancak .NET Core 3.0 ile başlayan Windows Formlar'da desteklenmez.

#### <a name="change-description"></a>Açıklamayı değiştir

.NET Framework 4.6 ve sonraki sürümlerinde, bir sekme seçilerek denetim koleksiyonunu yeniden sipariş eder. Uyumluluk `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` anahtarı, bu davranış istenmediğinde bir uygulamanın bu yeniden sıralamayı atlamasına olanak tanır.

.NET Core'da `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` anahtar desteklenmez.

#### <a name="version-introduced"></a>Sürüm tanıtıldı

3.0 Önizleme 9

#### <a name="recommended-action"></a>Önerilen eylem

Anahtarı çıkarın. Anahtar desteklenmez ve alternatif bir işlevsellik yok.

#### <a name="category"></a>Kategori

Windows Forms

#### <a name="affected-apis"></a>Etkilenen API’ler

- None

<!-- 

### Affected APIs

- Not detectable via API analysis

-->
