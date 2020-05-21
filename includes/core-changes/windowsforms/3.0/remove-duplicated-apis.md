---
ms.openlocfilehash: 3dfacadb5127319d4ce27f367803637cfb1ed00f
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721579"
---
### <a name="duplicated-apis-removed-from-windows-forms"></a>Yinelenen API 'Ler Windows Forms kaldırıldı

.NET Core 3,0 Preview 4 ' te başlayan ad alanında yanlışlıkla çoğaltılan bir dizi API 'Ler <xref:System.Windows.Forms?displayProperty=fullName> .net core 3,0 RC1 sürümünde kaldırılmıştır.

#### <a name="change-description"></a>Açıklamayı Değiştir

.NET Core 3,0 Preview 4 istenmeden yinelenen ad alanında zaten varolan bir tür türü <xref:System.Windows.Forms?displayProperty=fullName> <xref:System.ComponentModel.Design?displayProperty=fullName> . .NET Core 3,0 RC1 ile başlayarak, bu yinelenen türler artık kullanılamaz. Aşağıdaki tabloda, özgün tür ve onun yinelenen türü listelenmektedir:

> [!div class="mx-tdCol2BreakAll"]
> |Özgün tür|Yinelenen tür|
> |---|---|
> |<xref:System.ComponentModel.Design.DesignerActionListsChangedEventArgs?displayProperty=fullName>|`System.Windows.Forms.DesignerActionListsChangedEventArgs`|
> |<xref:System.ComponentModel.Design.DesignerActionListsChangedEventHandler?displayProperty=fullName>|`System.Windows.Forms.DesignerActionListsChangedEventHandler`|
> |<xref:System.ComponentModel.Design.DesignerActionListsChangedType?displayProperty=fullName>|`System.Windows.Forms.DesignerActionListsChangedType`|
> |<xref:System.ComponentModel.Design.DesignerActionUIService?displayProperty=fullName>|`System.Windows.Forms.DesignerActionUIService`|
> |<xref:System.ComponentModel.Design.DesignerCommandSet?displayProperty=fullName>|`System.Windows.Forms.DesignerCommandSet`|

#### <a name="version-introduced"></a>Sunulan sürüm

3,0 RC1

#### <a name="recommended-action"></a>Önerilen eylem

Kodu, tablonun **özgün tür** sütununda gösterildiği gibi özgün türe başvuracak şekilde güncelleştirin.

#### <a name="category"></a>Kategori

Windows Forms

#### <a name="affected-apis"></a>Etkilenen API’ler

- Yok.

<!--

#### Affected APIs

- Not detectable via API analysis.

-->
