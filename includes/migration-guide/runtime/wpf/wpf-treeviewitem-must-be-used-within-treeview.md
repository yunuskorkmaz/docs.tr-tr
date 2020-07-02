---
ms.openlocfilehash: af8cb9435be078351e3430dc8ded3f7cac377948
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620723"
---
### <a name="wpf-treeviewitem-must-be-used-within-a-treeview"></a>WPF TreeViewItem bir TreeView içinde kullanılmalıdır

#### <a name="details"></a>Ayrıntılar

4,5 içinde, dışındaki öğelerin kullanımını sınırlayan bir değişiklik yapılmıştır <xref:System.Windows.Controls.TreeViewItem?displayProperty=fullName> <xref:System.Windows.Controls.TreeView?displayProperty=fullName> . Bu bildirimler aşağıdaki koşullarda verilmiştir:<ul><li><xref:System.Windows.Controls.TreeViewItem?displayProperty=fullName>öğesinin görsel üst öğesi bir panel değil. ( <xref:System.Windows.Controls.TreeViewItem?displayProperty=fullName> Bir için üretilen, <xref:System.Windows.Controls.TreeView?displayProperty=fullName> üst öğesi olarak bir panele sahip olacaktır)</li><li>, Bir <xref:System.Windows.Controls.TreeViewItem?displayProperty=fullName> <xref:System.Windows.Controls.VirtualizingStackPanel?displayProperty=fullName> &quot; &quot; liste denetimi (ListBox, DataGrid, ListView, vb.) için öğeler ana bilgisayarı görevi gören bir alt öğesi. Sanallaştırmanın etkinleştirilmesi gerekmez.</li><li><xref:System.Windows.Controls.VirtualizingStackPanel?displayProperty=fullName>Öğesi-kaydırma ( <code>ScrollUnit=&quot;Item&quot;</code> ).</li><li>Birisi <code>VirtualizingStackPanel.MakeVisible(v)</code> bir öğeyi görünüme kaydırmak için çağırır <code>v</code> . Bu, açıkça veya örtük olarak çeşitli yollarla yapılabilir; Belki de en yaygın yol, <code>v</code> klavye odağı sağlamak için açık ' a tıklamaktır.</li><li>Üzerinde yapılan görsel üst öğe, öğesinden <code>v</code> <xref:System.Windows.Controls.VirtualizingStackPanel?displayProperty=fullName> geçer <xref:System.Windows.Controls.TreeViewItem?displayProperty=fullName> .</li></ul>Diğer bir deyişle, bir, bir <xref:System.Windows.Controls.TreeViewItem?displayProperty=fullName> ' ın dışında kullanıldığında <xref:System.Windows.Controls.TreeView?displayProperty=fullName> ve Kullanıcı <xref:System.Windows.Controls.TreeViewItem?displayProperty=fullName> onu görünüme getirmek için bir alt öğesine tıkladığı zaman görülür. <xref:System.Windows.Controls.TreeViewItem?displayProperty=fullName>Odaksız alt öğeleri yoksa, bu sorunu hiçbir şekilde görmezsiniz. Bu, bir bir <xref:System.Windows.Controls.TreeViewItem?displayProperty=fullName> DataTemplate 'in köküdür. Bu sorun isabet edildiğinde, WPF çerçevesinde oluşan bir InvalidCastException vardır.

#### <a name="suggestion"></a>Öneri

Bunun için bir düzeltme kullanıma sunulacaktır.

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |İkincil|
|Sürüm|4,5|
|Tür|Çalışma Zamanı|
