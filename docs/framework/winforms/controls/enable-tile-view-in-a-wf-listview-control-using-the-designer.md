---
title: Tasarımcı kullanarak ListView denetiminde kutucuk görünümünü etkinleştirme
ms.date: 03/30/2017
helpviewer_keywords:
- tile view feature
- ListView control [Windows Forms], tile view
- tiling [Windows Forms], Windows Forms, controls
ms.assetid: 12f0816a-52b8-41ee-a6d9-ded3a8a5817a
ms.openlocfilehash: a0429efaab14995ab1e3f3b0dfd91db61de72fbf
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745810"
---
# <a name="how-to-enable-tile-view-in-a-windows-forms-listview-control-using-the-designer"></a>Nasıl yapılır: Tasarımcı Kullanarak Windows Formları ListView Denetiminde Döşeme Görünümünü Etkinleştirme
<xref:System.Windows.Forms.ListView> denetiminin kutucuk görünümü özelliği, grafik ve metin bilgileri arasında görsel bir denge sağlamanıza olanak sağlar. Kutucuk görünümündeki bir öğe için görünen metin bilgileri, Ayrıntılar görünümü için tanımlanan sütun bilgileri ile aynıdır. Kutucuk görünümü, <xref:System.Windows.Forms.ListView> denetimindeki gruplandırma ya da ekleme işareti özellikleriyle birlikte işlev görür.

 Kutucuk görünümü, aşağıdaki görüntüde gösterildiği gibi bir 32 x 32 simgesi ve birkaç satırlık metin kullanır.

 ![ListView denetimindeki kutucuk görünümü](./media/enable-tile-view-in-a-wf-listview-control-using-the-designer/tile-view-in-listview-control.gif "Kutucuk görünümü simgeleri ve metni")

 Kutucuk görünümü özellikleri ve yöntemleri her öğe için hangi sütun alanlarının gösterileceğini belirtmenize ve bir kutucuk görünümü penceresindeki tüm öğelerin boyutunu ve görünümünü topluca denetleyebilmesini sağlar. Açıklık açısından, bir kutucukta metnin ilk satırı her zaman öğenin adıdır; değiştirilemez.

 Aşağıdaki yordam, bir <xref:System.Windows.Forms.ListView> denetimi içeren bir form ile **Windows uygulama** projesi gerektirir. Böyle bir projeyi ayarlama hakkında daha fazla bilgi için bkz. [nasıl yapılır: oluşturma Windows Forms uygulama projesi](/visualstudio/ide/step-1-create-a-windows-forms-application-project) ve [nasıl yapılır: Windows Forms denetim ekleme](how-to-add-controls-to-windows-forms.md).

## <a name="to-set-tile-view-in-the-designer"></a>Tasarımcıda kutucuk görünümünü ayarlamak için

1. Visual Studio 'da, formunuzdaki <xref:System.Windows.Forms.ListView> denetimini seçin.

2. **Özellikler** penceresinde <xref:System.Windows.Forms.ListView.View%2A> özelliğini seçin ve **kutucuk**' i seçin.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.ListView.TileSize%2A>
- [ListView Denetimine Genel Bakış](listview-control-overview-windows-forms.md)
