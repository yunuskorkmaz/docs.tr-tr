---
ms.openlocfilehash: 1be68c2968d0eaa9024007bcf37abf9e44c36f1c
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622152"
---
### <a name="scrolling-a-wpf-treeview-or-grouped-listbox-in-a-virtualizingstackpanel-can-cause-a-hang"></a>Bir VirtualizingStackPanel içindeki WPF TreeView veya gruplanmış ListBox 'ın kaydırılacağı bir askıda kalmasına neden olabilir

#### <a name="details"></a>Ayrıntılar

.NET Framework v 4.5 ' te, bir sanallaştırılmış yığın panelinde bir WPF kaydırmak, <xref:System.Windows.Controls.TreeView?displayProperty=fullName> Görünüm penceresinde ( <xref:System.Windows.Controls.TreeView?displayProperty=fullName> Örneğin, veya bir ItemsPresenter öğesinde bulunan öğeler arasında) kenar boşlukları varsa askıda kalmasına neden olabilir. Ayrıca, bazı durumlarda görünümdeki farklı boyutlardaki öğeler, kenar boşluğu olmasa bile kararsızlığa neden olabilir.

#### <a name="suggestion"></a>Öneri

.NET Framework 4.5.1 ' e yükselterek bu hataya kaçınılabilir. Alternatif olarak, <xref:System.Windows.Controls.TreeView?displayProperty=fullName> içerilen tüm öğelerin aynı boyutta olması halinde, sanallaştırılmış yığın panellerinde (gibi), kenar boşlukları kaldırılabilir.

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |Ana|
|Sürüm|4,5|
|Tür|Çalışma Zamanı

#### <a name="affected-apis"></a>Etkilenen API’ler

-<xref:System.Windows.Controls.VirtualizingStackPanel.SetIsVirtualizing(System.Windows.DependencyObject,System.Boolean)?displayProperty=nameWithType></li></ul>|
