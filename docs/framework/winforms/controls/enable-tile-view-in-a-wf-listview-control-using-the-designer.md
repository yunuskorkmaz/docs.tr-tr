---
title: 'Nasıl yapılır: Tasarımcı Kullanarak Windows Forms ListView Denetiminde Döşeme Görünümünü Etkinleştirme'
ms.date: 03/30/2017
helpviewer_keywords:
- tile view feature
- ListView control [Windows Forms], tile view
- tiling [Windows Forms], Windows Forms, controls
ms.assetid: 12f0816a-52b8-41ee-a6d9-ded3a8a5817a
ms.openlocfilehash: 8a45a8a484bd373f53585b1b113a51e59b30fca2
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040357"
---
# <a name="how-to-enable-tile-view-in-a-windows-forms-listview-control-using-the-designer"></a>Nasıl yapılır: Tasarımcı Kullanarak Windows Forms ListView Denetiminde Döşeme Görünümünü Etkinleştirme
<xref:System.Windows.Forms.ListView> Denetimin kutucuk görünümü özelliği, grafik ve metin bilgileri arasında görsel bir denge sağlamanıza olanak sağlar. Kutucuk görünümündeki bir öğe için görünen metin bilgileri, Ayrıntılar görünümü için tanımlanan sütun bilgileri ile aynıdır. Döşeme görünümü, <xref:System.Windows.Forms.ListView> denetimdeki gruplandırma ya da ekleme işareti özellikleriyle birlikte işlev görür.

 Kutucuk görünümü, aşağıdaki görüntüde gösterildiği gibi bir 32 x 32 simgesi ve birkaç satırlık metin kullanır.

 ![ListView denetimindeki kutucuk görünümü](./media/enable-tile-view-in-a-wf-listview-control-using-the-designer/tile-view-in-listview-control.gif "Kutucuk görünümü simgeleri ve metni")

 Kutucuk görünümü özellikleri ve yöntemleri her öğe için hangi sütun alanlarının gösterileceğini belirtmenize ve bir kutucuk görünümü penceresindeki tüm öğelerin boyutunu ve görünümünü topluca denetleyebilmesini sağlar. Açıklık açısından, bir kutucukta metnin ilk satırı her zaman öğenin adıdır; değiştirilemez.

 Aşağıdaki yordam, bir <xref:System.Windows.Forms.ListView> denetim içeren bir form ile **Windows uygulama** projesi gerektirir. Böyle bir projeyi ayarlama hakkında daha fazla bilgi için bkz [. nasıl yapılır: Windows Forms bir uygulama projesi](/visualstudio/ide/step-1-create-a-windows-forms-application-project) oluşturun ve [şunları yapın: Windows Forms](how-to-add-controls-to-windows-forms.md)denetimleri ekleyin.

> [!NOTE]
> Kutucuk görünümü yalnızca [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] uygulamanız <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> yöntemi çağırdığında kullanılabilir. Önceki işletim sistemlerinde, kutucuk görünümüyle ilgili tüm kodlar etkisizdir ve <xref:System.Windows.Forms.ListView> denetim büyük simge görünümünde görüntülenir. Daha fazla bilgi için bkz. <xref:System.Windows.Forms.ListView.View%2A?displayProperty=nameWithType>.

## <a name="to-set-tile-view-in-the-designer"></a>Tasarımcıda kutucuk görünümünü ayarlamak için

1. Visual Studio 'da, formunuzdaki <xref:System.Windows.Forms.ListView> denetimi seçin.

2. **Özellikler** penceresinde, <xref:System.Windows.Forms.ListView.View%2A> özelliği seçin ve **kutucuk**' ı seçin.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.ListView.TileSize%2A>
- [ListView Denetimine Genel Bakış](listview-control-overview-windows-forms.md)
