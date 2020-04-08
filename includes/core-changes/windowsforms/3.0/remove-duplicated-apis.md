---
ms.openlocfilehash: 0be59258df10aa13920551f011d68bc8efe20b93
ms.sourcegitcommit: 2b3b2d684259463ddfc76ad680e5e09fdc1984d2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80888154"
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

- Yok.

<!--

### Affected APIs

- Not detectable via API analysis.

-->
