---
title: 'Nasıl yapılır: Tasarım Zamanında Denetimi Formların Kenarlarına Hizalama'
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], docking using designer
- Dock property [Windows Forms], aligning controls (using designer)
ms.assetid: 51f08998-5e3b-4330-be58-a4edd0eb60f4
ms.openlocfilehash: b08e01eb9adb984a32a8fc435cf1f3b93b159a14
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65210377"
---
# <a name="how-to-align-a-control-to-the-edges-of-forms-at-design-time"></a>Nasıl yapılır: Tasarım Zamanında Denetimi Formların Kenarlarına Hizalama

Denetiminiz değerini ayarlayarak formlarınızı kenarına hizalama yapabileceğiniz <xref:System.Windows.Forms.Control.Dock%2A> özelliği. Bu özellik, denetimi forma bulunduğu belirler. <xref:System.Windows.Forms.Control.Dock%2A> Özelliği aşağıdaki değerlere ayarlanabilir:

|Ayar|Denetiminiz etkisi|
|-------------|----------------------------|
|<xref:System.Windows.Forms.DockStyle.Bottom>|Formun altına noktaları.|
|<xref:System.Windows.Forms.DockStyle.Fill>|Formdaki tüm kalan alanı doldurur.|
|<xref:System.Windows.Forms.DockStyle.Left>|Formun sol tarafına noktaları.|
|<xref:System.Windows.Forms.DockStyle.None>|Her yerden ve bunu görünür tarafından belirtilen konumda dock yoksa kendi <xref:System.Windows.Forms.Control.Location%2A>.|
|<xref:System.Windows.Forms.DockStyle.Right>|Formun sağ tarafına noktaları.|
|<xref:System.Windows.Forms.DockStyle.Top>|Üst formun noktaları.|

Bu değerleri de kod içinde ayarlayabilirsiniz. Daha fazla bilgi için [nasıl yapılır: Bir denetimi formların kenarlarına hizalama](how-to-align-a-control-to-the-edges-of-forms.md).

## <a name="set-the-dock-property-for-your-control-at-design-time"></a>Tasarım zamanında denetiminizi Dock özelliğini ayarlama

1. Windows Form Tasarımcısı'nda Visual Studio'da denetiminizi seçin.

2. İçinde **özellikleri** penceresinde, aşağı açılan kutusunda sonraki tıklatın <xref:System.Windows.Forms.Control.Dock%2A> özelliği.

     Altı olası temsil eden bir grafik arabirim <xref:System.Windows.Forms.Control.Dock%2A> ayarları görüntülenir.

3. Uygun ayarı seçin.

4. Denetiminiz artık ayarı tarafından belirlenen şekilde dock.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.Control.Dock%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.Anchor%2A?displayProperty=nameWithType>
- [Nasıl yapılır: Bir denetimi formların kenarlarına hizalama](how-to-align-a-control-to-the-edges-of-forms.md)
- [İzlenecek yol: Dayama çizgileri kullanarak Windows Forms'da denetimleri düzenleme](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
- [Nasıl yapılır: Windows Forms'da denetimleri](how-to-anchor-controls-on-windows-forms.md)
- [Nasıl yapılır: Sabitleme ve TableLayoutPanel denetiminde alt denetimleri yerleştirme](how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [Nasıl yapılır: Sabitleme ve FlowLayoutPanel denetiminde alt denetimleri yerleştirme](how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control.md)
- [İzlenecek yol: TableLayoutPanel kullanarak Windows Forms'da denetimleri düzenleme](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [İzlenecek yol: FlowLayoutPanel kullanarak Windows Forms'da denetimleri düzenleme](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [Tasarım Zamanında Windows Forms Denetimleri Geliştirme](developing-windows-forms-controls-at-design-time.md)
