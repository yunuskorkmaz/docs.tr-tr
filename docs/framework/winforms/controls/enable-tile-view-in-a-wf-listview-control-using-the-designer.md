---
title: 'Nasıl yapılır: Tasarımcı Kullanarak Windows Forms ListView Denetiminde Döşeme Görünümünü Etkinleştirme'
ms.date: 03/30/2017
helpviewer_keywords:
- tile view feature
- ListView control [Windows Forms], tile view
- tiling [Windows Forms], Windows Forms, controls
ms.assetid: 12f0816a-52b8-41ee-a6d9-ded3a8a5817a
ms.openlocfilehash: f8c8a1b2e3d2adfa7daadd609051ffc304150efe
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59300599"
---
# <a name="how-to-enable-tile-view-in-a-windows-forms-listview-control-using-the-designer"></a>Nasıl yapılır: Tasarımcı Kullanarak Windows Forms ListView Denetiminde Döşeme Görünümünü Etkinleştirme
Döşeme görünümü özelliği <xref:System.Windows.Forms.ListView> , grafik ve metinsel bilgileri arasında görsel bir denge sağlamak denetim olanağı sağlar. Kutucuk görünümde bir öğe için görüntülenen metin tabanlı bilgiler tanımlanan ayrıntı görünümü için sütun bilgileri ile aynıdır. Kutucuk görünümü işlevleri gruplandırma veya ekleme ile birlikte özellikleri işaretle <xref:System.Windows.Forms.ListView> denetimi.  
  
 Kutucuk görünümü 32 x 32 bir simge ve birkaç satırlık metin, aşağıdaki görüntüde gösterildiği gibi kullanır.  
  
 ![Görünüm ListView denetiminde döşeme](./media/enable-tile-view-in-a-wf-listview-control-using-the-designer/tile-view-in-listview-control.gif "döşeme görünümü simge ve metin")  
  
 Döşeme görünümü özellikleri ve yöntemleri, her öğe için görüntülenecek ve topluca bir kutucuk Görünümü penceresi içindeki tüm öğelerin görünümünü ve boyutunu denetlemek için hangi sütun alanları belirtmenize olanak verir. Açıklık için bir döşeme içindeki metnin ilk satırı her zaman öğenin adıdır; değiştirilemez.  
  
 Aşağıdaki yordam gerektirir bir **Windows uygulama** proje içeren bir form içeren bir <xref:System.Windows.Forms.ListView> denetimi. Bu tür bir proje ayarlama hakkında daha fazla bilgi için bkz: [nasıl yapılır: Bir Windows Forms uygulaması projesi oluşturma](/visualstudio/ide/step-1-create-a-windows-forms-application-project) ve [nasıl yapılır: Windows Forms'a denetimler ekleme](how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  Kutucuk görünümü yalnızca üzerinde kullanılabilir [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] uygulamanızı çağırdığında <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> yöntemi. Önceki işletim sistemlerinde kutucuk görünümüne ilgili herhangi bir kod bir etkisi yoktur ve <xref:System.Windows.Forms.ListView> denetimi büyük simge görünümünde görüntüler. Daha fazla bilgi için bkz. <xref:System.Windows.Forms.ListView.View%2A?displayProperty=nameWithType>.  
>   
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-set-tile-view-in-the-designer"></a>Kutucuk görünümü Tasarımcısı'nda ayarlamak için  
  
1. Seçin <xref:System.Windows.Forms.ListView> formunuzdaki denetimi.  
  
2. İçinde **özellikleri** penceresinde <xref:System.Windows.Forms.ListView.View%2A> özelliği ve **kutucuk**.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.ListView.TileSize%2A>
- [ListView Denetimine Genel Bakış](listview-control-overview-windows-forms.md)
