---
title: ProgressBar Denetimine Genel Bakış (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- ProgressBar
helpviewer_keywords:
- ProgressBar control [Windows Forms], about ProgressBar control
- progress controls [Windows Forms], about progress controls
ms.assetid: a05d9cba-3a6a-4f8f-94b8-8ec12799fb80
ms.openlocfilehash: db0a43534080d630323d8c1c95759fd2dcc04a85
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57707953"
---
# <a name="progressbar-control-overview-windows-forms"></a>ProgressBar Denetimine Genel Bakış (Windows Forms)
> [!IMPORTANT]
>  <xref:System.Windows.Forms.ToolStripProgressBar> Denetimi değiştirir ve işlevsellik ekler <xref:System.Windows.Forms.ProgressBar> denetler; ancak, <xref:System.Windows.Forms.ProgressBar> denetim korunur geriye dönük uyumluluk ve gelecekte kullanım için seçerseniz.  
  
 Windows Forms <xref:System.Windows.Forms.ProgressBar> denetimi yatay bir çubuk düzenlenmiş dikdörtgenler uygun sayıda görüntüleyerek bir işlemin ilerleme durumunu gösterir. İşlem tamamlandığında çubuğu doldurulur. İlerleme çubukları kullanıcıya nasıl hakkında bir fikir vermek için kullanılan yaygın olarak tamamlamak; bir işlem için uzun Örneğin, büyük bir dosya yükleniyor.  
  
> [!NOTE]
>  <xref:System.Windows.Forms.ProgressBar> Denetimi yalnızca yönelik yatay olarak form üzerinde.  
  
## <a name="key-properties-and-methods"></a>Anahtar özellikleri ve yöntemleri  
 Anahtar özelliklerini <xref:System.Windows.Forms.ProgressBar> denetimi <xref:System.Windows.Forms.ProgressBar.Value%2A>, <xref:System.Windows.Forms.ProgressBar.Minimum%2A>, ve <xref:System.Windows.Forms.ProgressBar.Maximum%2A>. <xref:System.Windows.Forms.ProgressBar.Minimum%2A> Ve <xref:System.Windows.Forms.ProgressBar.Maximum%2A> özellikleri ilerleme çubuğu görüntüler maksimum ve minimum değerleri ayarlayın. <xref:System.Windows.Forms.ProgressBar.Value%2A> Özelliğini işlemi tamamlamaya yönelik yapılan ilerleme durumunu temsil eder. Denetimde görüntülenen çubuğu bloklarını oluştuğu için değer tarafından görüntülenen <xref:System.Windows.Forms.ProgressBar> denetimi yalnızca yakın <xref:System.Windows.Forms.ProgressBar.Value%2A> özelliğinin geçerli değeri. Boyutuna göre <xref:System.Windows.Forms.ProgressBar> denetimi <xref:System.Windows.Forms.ProgressBar.Value%2A> özelliği zaman sonraki bloğu görüntülenecek belirler.  
  
 En yaygın yolu geçerli ilerleme değerini ayarlamak üzere kod yazmak için olan <xref:System.Windows.Forms.ProgressBar.Value%2A> özelliği. Büyük bir dosya yükleme, örnekte kilobayt cinsinden dosyasının boyutu için üst sınırı ayarlayabilirsiniz. Örneğin, varsa <xref:System.Windows.Forms.ProgressBar.Maximum%2A> özelliği, 100'e ayarlandığında <xref:System.Windows.Forms.ProgressBar.Minimum%2A> özelliği, 10'a ayarlanır ve <xref:System.Windows.Forms.ProgressBar.Value%2A> özelliği 5 dikdörtgenler 50 olarak görüntülenir. Yarı görüntülenebilen sayının budur.  
  
 Ancak, tarafından görüntülenen değeri değiştirmek için farklı yöntemleri vardır <xref:System.Windows.Forms.ProgressBar> ayarı yanı sıra denetim <xref:System.Windows.Forms.ProgressBar.Value%2A> özelliği doğrudan. <xref:System.Windows.Forms.ProgressBar.Step%2A> Özelliği artırmak için bir değer belirtmek için kullanılabilir <xref:System.Windows.Forms.ProgressBar.Value%2A> özelliği tarafından. Ardından, arama <xref:System.Windows.Forms.ProgressBar.PerformStep%2A> yöntemi değer artış. Değeri Artır değiştirmek için kullanabileceğiniz <xref:System.Windows.Forms.ProgressBar.Increment%2A> yöntemi ve hangi artırmak bir değer belirtin <xref:System.Windows.Forms.ProgressBar.Value%2A> özelliği.  
  
 Grafik kullanıcı geçerli bir eylem hakkında bilgilendiren başka bir denetimi <xref:System.Windows.Forms.StatusBar> denetimi.  
  
> [!IMPORTANT]
>  <xref:System.Windows.Forms.StatusStrip> Ve <xref:System.Windows.Forms.ToolStripStatusLabel> denetimleri değiştirin ve işlevsellik eklemek <xref:System.Windows.Forms.StatusBar> ve <xref:System.Windows.Forms.StatusBarPanel> denetler; ancak, <xref:System.Windows.Forms.StatusBar> ve <xref:System.Windows.Forms.StatusBarPanel> denetimleri korunur geriye dönük uyumluluk ve gelecekte kullanım için varsa, ' ı seçin.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Forms.ProgressBar>
- [ProgressBar Denetimi](progressbar-control-windows-forms.md)
