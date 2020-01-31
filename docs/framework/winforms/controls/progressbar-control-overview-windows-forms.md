---
title: ProgressBar Denetimine Genel Bakış
ms.date: 03/30/2017
f1_keywords:
- ProgressBar
helpviewer_keywords:
- ProgressBar control [Windows Forms], about ProgressBar control
- progress controls [Windows Forms], about progress controls
ms.assetid: a05d9cba-3a6a-4f8f-94b8-8ec12799fb80
ms.openlocfilehash: a0c4a0401d06614ab3ad148b932ebc64080c592c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741284"
---
# <a name="progressbar-control-overview-windows-forms"></a>ProgressBar Denetimine Genel Bakış (Windows Forms)
> [!IMPORTANT]
> <xref:System.Windows.Forms.ToolStripProgressBar> denetimi yerini alır ve <xref:System.Windows.Forms.ProgressBar> denetimine işlevsellik ekler; Ancak, ' yi seçerseniz, <xref:System.Windows.Forms.ProgressBar> denetimi hem geri uyumluluk hem de gelecekte kullanılmak üzere korunur.  
  
 Windows Forms <xref:System.Windows.Forms.ProgressBar> denetimi, yatay bir çubukta düzenlenmiş uygun sayıda dikdörtgeni görüntüleyerek bir işlemin ilerlemesini gösterir. İşlem tamamlandığında çubuk doldurulur. İlerleme çubukları genellikle kullanıcıya bir işlemin ne kadar bekleneceği hakkında fikir vermek için kullanılır; Örneğin, büyük bir dosya yüklenirken.  
  
> [!NOTE]
> <xref:System.Windows.Forms.ProgressBar> denetimi yalnızca form üzerinde yatay olarak yönetilebilir.  
  
## <a name="key-properties-and-methods"></a>Anahtar özellikleri ve yöntemleri  
 <xref:System.Windows.Forms.ProgressBar> denetiminin temel özellikleri <xref:System.Windows.Forms.ProgressBar.Value%2A>, <xref:System.Windows.Forms.ProgressBar.Minimum%2A>ve <xref:System.Windows.Forms.ProgressBar.Maximum%2A>. <xref:System.Windows.Forms.ProgressBar.Minimum%2A> ve <xref:System.Windows.Forms.ProgressBar.Maximum%2A> özellikleri, ilerleme çubuğunun görüntüleyeceği maksimum ve minimum değerleri ayarlar. <xref:System.Windows.Forms.ProgressBar.Value%2A> özelliği, işlemi tamamlamaya yönelik ilerleme durumunu temsil eder. Denetimde görünen çubuk bloklardan oluştuğu için, <xref:System.Windows.Forms.ProgressBar> denetimi tarafından görünen değer yalnızca <xref:System.Windows.Forms.ProgressBar.Value%2A> özelliğinin geçerli değerine yaklaştırır. <xref:System.Windows.Forms.ProgressBar> denetiminin boyutuna bağlı olarak, <xref:System.Windows.Forms.ProgressBar.Value%2A> özelliği bir sonraki bloğun ne zaman görüntüleneceğini belirler.  
  
 Geçerli ilerleme değerini güncelleştirmenin en yaygın yolu <xref:System.Windows.Forms.ProgressBar.Value%2A> özelliğini ayarlamak için kod yazmaktır. Büyük bir dosya yükleme örneğinde, en yüksek değeri kilobayt cinsinden dosyanın boyutuna ayarlayabilirsiniz. Örneğin, <xref:System.Windows.Forms.ProgressBar.Maximum%2A> özelliği 100 olarak ayarlanırsa, <xref:System.Windows.Forms.ProgressBar.Minimum%2A> özelliği 10 olarak ayarlanır ve <xref:System.Windows.Forms.ProgressBar.Value%2A> özelliği 50 olarak ayarlanır, 5 dikdörtgenleri görüntülenecektir. Bu, görüntülenebilecek sayının yarısıdır.  
  
 Ancak, <xref:System.Windows.Forms.ProgressBar.Value%2A> özelliğinin doğrudan ayarından sonra <xref:System.Windows.Forms.ProgressBar> denetimi tarafından görüntülenen değeri değiştirmek için başka yollar vardır. <xref:System.Windows.Forms.ProgressBar.Step%2A> özelliği, <xref:System.Windows.Forms.ProgressBar.Value%2A> özelliğinin artırılacağı bir değer belirtmek için kullanılabilir. Sonra, <xref:System.Windows.Forms.ProgressBar.PerformStep%2A> yöntemini çağırmak değeri artacaktır. Artış değerini değiştirmek için <xref:System.Windows.Forms.ProgressBar.Increment%2A> yöntemini kullanabilir ve <xref:System.Windows.Forms.ProgressBar.Value%2A> özelliğinin artırılacağı bir değer belirtebilirsiniz.  
  
 Kullanıcıyı geçerli bir eylem hakkında grafiksel olarak bildiren başka bir denetim <xref:System.Windows.Forms.StatusBar> denetimidir.  
  
> [!IMPORTANT]
> <xref:System.Windows.Forms.StatusStrip> ve <xref:System.Windows.Forms.ToolStripStatusLabel> denetimleri yerini alır ve <xref:System.Windows.Forms.StatusBar> ve <xref:System.Windows.Forms.StatusBarPanel> denetimlerine işlevsellik ekler; Ancak, <xref:System.Windows.Forms.StatusBar> ve <xref:System.Windows.Forms.StatusBarPanel> denetimleri hem geri uyumluluk hem de gelecekteki kullanım için korunur.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.ProgressBar>
- [ProgressBar Denetimi](progressbar-control-windows-forms.md)
