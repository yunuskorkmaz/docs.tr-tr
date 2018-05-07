---
title: ProgressBar Denetimine Genel Bakış (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- ProgressBar
helpviewer_keywords:
- ProgressBar control [Windows Forms], about ProgressBar control
- progress controls [Windows Forms], about progress controls
ms.assetid: a05d9cba-3a6a-4f8f-94b8-8ec12799fb80
ms.openlocfilehash: bd2b9615b0061a8f2133229edb49357cde69b39e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="progressbar-control-overview-windows-forms"></a>ProgressBar Denetimine Genel Bakış (Windows Forms)
> [!IMPORTANT]
>  <xref:System.Windows.Forms.ToolStripProgressBar> Denetimi değiştirir ve işlevlerini ekler <xref:System.Windows.Forms.ProgressBar> kontrol; ancak, <xref:System.Windows.Forms.ProgressBar> denetim tutulur geriye dönük uyumluluk ve gelecekte kullanım için seçerseniz.  
  
 Windows Forms <xref:System.Windows.Forms.ProgressBar> denetim yatay çubuğunda düzenlenmiş dikdörtgenler uygun sayıda görüntüleyerek bir işlemin ilerlemesini gösterir. İşlem tamamlandığında çubuğu girilir. İlerleme çubukları kullanıcıya nasıl hakkında bir fikir vermek için yaygın olarak kullanılır; bir işlemin tamamlanmasını beklemek için uzun Örneğin, ne zaman büyük bir dosya yükleniyor.  
  
> [!NOTE]
>  <xref:System.Windows.Forms.ProgressBar> Denetimi yalnızca yönelik yatay olarak form üzerinde.  
  
## <a name="key-properties-and-methods"></a>Anahtar özellikleri ve yöntemleri  
 Anahtar özelliklerini <xref:System.Windows.Forms.ProgressBar> denetim <xref:System.Windows.Forms.ProgressBar.Value%2A>, <xref:System.Windows.Forms.ProgressBar.Minimum%2A>, ve <xref:System.Windows.Forms.ProgressBar.Maximum%2A>. <xref:System.Windows.Forms.ProgressBar.Minimum%2A> Ve <xref:System.Windows.Forms.ProgressBar.Maximum%2A> özellikleri ilerleme çubuğu görüntüleyebilir maksimum ve minimum değerler ayarlayın. <xref:System.Windows.Forms.ProgressBar.Value%2A> Özelliği işleminin tamamlanmasına yönelik yapılan ilerleme durumunu temsil eder. Denetiminde gösterilen çubuğu bloklardan oluşan olduğundan, değer tarafından görüntülenen <xref:System.Windows.Forms.ProgressBar> denetimi yalnızca yakın <xref:System.Windows.Forms.ProgressBar.Value%2A> özelliğin geçerli değeri. Boyutuna göre <xref:System.Windows.Forms.ProgressBar> denetimi <xref:System.Windows.Forms.ProgressBar.Value%2A> özelliği sonraki bloğu görüntülemek ne zaman belirler.  
  
 Geçerli ilerleme değeri güncelleştirmek için en yaygın şekilde ayarlamak için kod yazmaktır <xref:System.Windows.Forms.ProgressBar.Value%2A> özelliği. Büyük bir dosya yükleniyor örnekte, kilobayt cinsinden dosyasının boyutu için en fazla ayarlayabilir. Örneğin, varsa <xref:System.Windows.Forms.ProgressBar.Maximum%2A> özelliği 100'e ayarlanmış <xref:System.Windows.Forms.ProgressBar.Minimum%2A> özelliği, 10'a ayarlanır ve <xref:System.Windows.Forms.ProgressBar.Value%2A> özelliği ayarlanmış 50'ye 5 dikdörtgenler görüntülenir. Görüntülenebilir numarası yarısı budur.  
  
 Ancak, tarafından görüntülenen değeri değiştirmek için diğer yolları vardır <xref:System.Windows.Forms.ProgressBar> ayarı yanı sıra denetim <xref:System.Windows.Forms.ProgressBar.Value%2A> doğrudan özelliği. <xref:System.Windows.Forms.ProgressBar.Step%2A> Özelliği, artırmak için bir değer belirtmek için kullanılabilir <xref:System.Windows.Forms.ProgressBar.Value%2A> özelliği tarafından. Ardından, çağırma <xref:System.Windows.Forms.ProgressBar.PerformStep%2A> yöntemi, değeri artırmak. Artış değerini değiştirmek için kullanabileceğiniz <xref:System.Windows.Forms.ProgressBar.Increment%2A> yöntemi ve hangi artırmak bir değer belirtin <xref:System.Windows.Forms.ProgressBar.Value%2A> özelliği.  
  
 Grafik kullanıcı geçerli bir eylem hakkında bilgilendirir başka bir denetim <xref:System.Windows.Forms.StatusBar> denetim.  
  
> [!IMPORTANT]
>  <xref:System.Windows.Forms.StatusStrip> Ve <xref:System.Windows.Forms.ToolStripStatusLabel> denetimleri değiştirin ve işlevsellik eklemek <xref:System.Windows.Forms.StatusBar> ve <xref:System.Windows.Forms.StatusBarPanel> denetler; ancak, <xref:System.Windows.Forms.StatusBar> ve <xref:System.Windows.Forms.StatusBarPanel> denetimleri korunur geriye dönük uyumluluk ve gelecekte kullanım için ise, ' ı seçin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.ProgressBar>  
 [ProgressBar Denetimi](../../../../docs/framework/winforms/controls/progressbar-control-windows-forms.md)
