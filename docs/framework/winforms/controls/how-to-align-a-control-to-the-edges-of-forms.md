---
title: 'Nasıl yapılır: Denetimi Formların Kenarlarına Hizalama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Dock property [Windows Forms], aligning controls (using code)
- forms [Windows Forms], aligning controls
- controls [Windows Forms], aligning on forms
- custom controls [Windows Forms], docking using code
ms.assetid: 5994cb59-242b-4e75-bd0e-62879c34d702
ms.openlocfilehash: 5d662489b7e31f391bbd508409e69c091a25592c
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015940"
---
# <a name="how-to-align-a-control-to-the-edges-of-forms"></a>Nasıl yapılır: Denetimi Formların Kenarlarına Hizalama

<xref:System.Windows.Forms.Control.Dock%2A> Özelliğini ayarlayarak denetiminizi formlarınızın kenarına hizalayın. Bu özellik, denetiminizin formda nerede olduğunu belirler. <xref:System.Windows.Forms.Control.Dock%2A> Özelliği aşağıdaki değerlere ayarlanabilir:

|Ayar|Denetiminizin etkisi|
|-------------|----------------------------|
|<xref:System.Windows.Forms.DockStyle.Bottom>|Formun altına noktaları.|
|<xref:System.Windows.Forms.DockStyle.Fill>|Formdaki kalan tüm alanı doldurur.|
|<xref:System.Windows.Forms.DockStyle.Left>|Formun sol tarafına noktaları.|
|<xref:System.Windows.Forms.DockStyle.None>|Herhangi bir yere sabitlemez ve <xref:System.Windows.Forms.Control.Location%2A> özelliği tarafından belirtilen konumda görüntülenir.|
|<xref:System.Windows.Forms.DockStyle.Right>|Formun sağ tarafına noktaları.|
|<xref:System.Windows.Forms.DockStyle.Top>|Formun üst kısmına noktaları.|

Visual Studio 'da bu özellik için tasarım zamanı desteği vardır.

## <a name="set-the-dock-property-for-your-control-at-run-time"></a>Çalışma zamanında denetiminizin Dock özelliğini ayarlayın

Özelliği, <xref:System.Windows.Forms.Control.Dock%2A> koddaki uygun değere ayarlayın.

```vb
' To set the Dock property internally.
Me.Dock = DockStyle.Top
' To set the Dock property from another object.
UserControl1.Dock = DockStyle.Top
```

```csharp
// To set the Dock property internally.
this.Dock = DockStyle.Top;
// To set the Dock property from another object.
UserControl1.Dock = DockStyle.Top;
```

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.Control.Dock%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.Anchor%2A?displayProperty=nameWithType>
- [.NET Framework ile Özel Windows Forms Denetimleri Geliştirme](developing-custom-windows-forms-controls.md)
- [Nasıl yapılır: FlowLayoutPanel denetiminde alt denetimleri sabitleme ve yerleştirme](how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control.md)
- [Nasıl yapılır: TableLayoutPanel denetiminde alt denetimleri sabitleme ve yerleştirme](how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [AutoSize Özelliğine Genel Bakış](autosize-property-overview.md)
