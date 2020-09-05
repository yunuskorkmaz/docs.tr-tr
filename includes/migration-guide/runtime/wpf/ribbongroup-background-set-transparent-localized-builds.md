---
ms.openlocfilehash: d6405573e476ce18513938b500041adefbeeef1b
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496901"
---
### <a name="ribbongroup-background-is-set-to-transparent-in-localized-builds"></a>RibbonGroup arka planı yerelleştirilmiş derlemelerde saydam olarak ayarlandı

#### <a name="details"></a>Ayrıntılar

<xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=fullName> yerelleştirilmiş derlemelerin arka planı her zaman saydam fırçayla boyanmıştır ve bu, kötü Kullanıcı arabirimi deneyimine yol açar. Bu, için yerelleştirilmiş kaynakları güncelleştirerek .NET Framework 4,7 WPF düzeltmesinde düzeltilir, bu da <xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=fullName> doğru fırçanın seçili olmasını sağlar.

#### <a name="suggestion"></a>Öneri

.NET Framework 4,7 ' ye yükseltin

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |Edge|
|Sürüm|4.6.2|
|Tür|Çalışma Zamanı|

#### <a name="affected-apis"></a>Etkilenen API’ler

API analizi aracılığıyla algılanamaz.

<!--

#### Affected APIs

Not detectable via API analysis.

-->
