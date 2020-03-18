---
ms.openlocfilehash: e609b8006846cd202a6a7eeec2529cf1fbb09e7c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937090"
---
### <a name="duplicated-apis-removed-from-windows-forms"></a>Windows Formlarından Kaldırılan Yinelenen API'ler

.NET Core 3.0 Preview <xref:System.Windows.Forms?displayProperty=fullName> 4'ten başlayarak ad alanında yanlışlıkla yinelenen bir dizi API ,NET Core 3.0 RC1'de kaldırıldı.

#### <a name="change-description"></a>Açıklamayı değiştir

.NET Core 3.0 Preview 4, <xref:System.Windows.Forms?displayProperty=fullName> <xref:System.ComponentModel.Design?displayProperty=fullName> ad alanında zaten var olan ad alanında yanlışlıkla bir dizi türü yineledi. .NET Core 3.0 RC1 ile başlayarak, bu yinelenen türleri artık kullanılamaz. Aşağıdaki tabloda özgün türü ve yinelenen türü listelenir:

> [!div class="mx-tdCol2BreakAll"]
> |Orijinal tür|Yinelenen tür|
> |---|---|
> |<xref:System.ComponentModel.Design.DesignerActionListsChangedEventArgs?displayProperty=fullName>|`System.Windows.Forms.DesignerActionListsChangedEventArgs`|
> |<xref:System.ComponentModel.Design.DesignerActionListsChangedEventHandler?displayProperty=fullName>|`System.Windows.Forms.DesignerActionListsChangedEventHandler`|
> |<xref:System.ComponentModel.Design.DesignerActionListsChangedType?displayProperty=fullName>|`System.Windows.Forms.DesignerActionListsChangedType`|
> |<xref:System.ComponentModel.Design.DesignerActionUIService?displayProperty=fullName>|`System.Windows.Forms.DesignerActionUIService`|
> |<xref:System.ComponentModel.Design.DesignerCommandSet?displayProperty=fullName>|`System.Windows.Forms.DesignerCommandSet`|

#### <a name="version-introduced"></a>Sürüm tanıtıldı

3.0 RC1

#### <a name="recommended-action"></a>Önerilen eylem

Tablonun **Özgün türü** sütununda gösterildiği gibi, özgün türe başvurmak için kodu güncelleştirin.

#### <a name="category"></a>Kategori

Windows Forms

#### <a name="affected-apis"></a>Etkilenen API’ler

- API analizi ile tespit edilemez.

<!--

### Affected APIs

- Not detectable via API analysis.

-->
