---
ms.openlocfilehash: 4d67da34cf692133df95480a7f0215943337a34e
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72003013"
---
### <a name="duplicated-apis-removed-from-windows-forms"></a>Yinelenen API 'Ler Windows Forms kaldırıldı

.NET Core 3,0 Preview 4 ' te başlayan <xref:System.Windows.Forms?displayProperty=fullName> ad alanında yanlışlıkla çoğaltılan bir dizi API 'Ler .NET Core 3,0 RC1 sürümünde kaldırılmıştır. 

#### <a name="change-description"></a>Açıklamayı Değiştir

.NET Core 3,0 Preview 4 istenmeden yinelenen <xref:System.ComponentModel.Design?displayProperty=fullName> ad alanında zaten bulunan <xref:System.Windows.Forms?displayProperty=fullName> ad alanında bir dizi tür. .NET Core 3,0 RC1 ile başlayarak, bu yinelenen türler artık kullanılamaz. Aşağıdaki tabloda, özgün tür ve onun yinelenen türü listelenmektedir:

|Özgün tür|Yinelenen tür|
|---|---|
|<xref:System.ComponentModel.Design.DesignerActionListsChangedEventArgs?displayProperty=fullName>|`System.Windows.Forms.DesignerActionListsChangedEventArgs`|
|<xref:System.ComponentModel.Design.DesignerActionListsChangedEventHandler?displayProperty=fullName>|`System.Windows.Forms.DesignerActionListsChangedEventHandler`|
|<xref:System.ComponentModel.Design.DesignerActionListsChangedType?displayProperty=fullName>|`System.Windows.Forms.DesignerActionListsChangedType`|
|<xref:System.ComponentModel.Design.DesignerActionUIService?displayProperty=fullName>|`System.Windows.Forms.DesignerActionUIService`|
|<xref:System.ComponentModel.Design.DesignerCommandSet?displayProperty=fullName>|`System.Windows.Forms.DesignerCommandSet`|

#### <a name="version-introduced"></a>Sunulan sürüm

3,0 RC1

#### <a name="recommended-action"></a>Önerilen eylem

Kodu, tablonun **özgün tür** sütununda gösterildiği gibi özgün türe başvuracak şekilde güncelleştirin.

#### <a name="category"></a>Kategori

Windows Forms

#### <a name="affected-apis"></a>Etkilenen API’ler

- API analizi aracılığıyla algılanamaz.

<!-- 

### Affected APIs

- Not detectable via API analysis.

-->
