---
ms.openlocfilehash: a3ba42868577ac20ea2e082f90fc4973a1bfe108
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622385"
---
### <a name="ribbongroup-background-is-set-to-transparent-in-localized-builds"></a>RibbonGroup arka planı yerelleştirilmiş derlemelerde saydam olarak ayarlandı

#### <a name="details"></a>Ayrıntılar

<xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=fullName>yerelleştirilmiş derlemelerin arka planı her zaman saydam fırçayla boyanmıştır ve bu, kötü Kullanıcı arabirimi deneyimine yol açar. Bu, için yerelleştirilmiş kaynakları güncelleştirerek .NET Framework 4,7 WPF düzeltmesinde düzeltilir, bu da <xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=fullName> doğru fırçanın seçili olmasını sağlar.

#### <a name="suggestion"></a>Öneri

.NET Framework 4,7 ' ye yükseltin

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |Edge|
|Sürüm|4.6.2|
|Tür|Çalışma Zamanı|
