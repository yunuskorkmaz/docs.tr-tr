---
title: ProgressBar Denetimine Genel Bakış (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- ProgressBar
helpviewer_keywords:
- ProgressBar control [Windows Forms], about ProgressBar control
- progress controls [Windows Forms], about progress controls
ms.assetid: a05d9cba-3a6a-4f8f-94b8-8ec12799fb80
ms.openlocfilehash: 7dd434492cd688527ddbce5aaffa442a0b40a9e4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968312"
---
# <a name="progressbar-control-overview-windows-forms"></a>ProgressBar Denetimine Genel Bakış (Windows Forms)
> [!IMPORTANT]
> Denetim yerini alır ve <xref:System.Windows.Forms.ProgressBar> <xref:System.Windows.Forms.ProgressBar> denetime işlevsellik ekler; ancak, isterseniz denetim hem geri uyumluluk hem de gelecekteki kullanım için korunur. <xref:System.Windows.Forms.ToolStripProgressBar>  
  
 Windows Forms <xref:System.Windows.Forms.ProgressBar> denetim, yatay bir çubukta düzenlenmiş uygun sayıda dikdörtgeni görüntüleyerek bir işlemin ilerlemesini gösterir. İşlem tamamlandığında çubuk doldurulur. İlerleme çubukları genellikle kullanıcıya bir işlemin ne kadar bekleneceği hakkında fikir vermek için kullanılır; Örneğin, büyük bir dosya yüklenirken.  
  
> [!NOTE]
> <xref:System.Windows.Forms.ProgressBar> Denetim, form üzerinde yalnızca yatay olarak yönetilebilir.  
  
## <a name="key-properties-and-methods"></a>Anahtar özellikleri ve yöntemleri  
 <xref:System.Windows.Forms.ProgressBar> Denetimin anahtar özellikleri, <xref:System.Windows.Forms.ProgressBar.Value%2A> <xref:System.Windows.Forms.ProgressBar.Minimum%2A>ve 'dir.<xref:System.Windows.Forms.ProgressBar.Maximum%2A> <xref:System.Windows.Forms.ProgressBar.Minimum%2A> Ve<xref:System.Windows.Forms.ProgressBar.Maximum%2A> özellikleri, ilerleme çubuğunun görüntüleyeceği maksimum ve minimum değerleri ayarlar. <xref:System.Windows.Forms.ProgressBar.Value%2A> Özelliği, işlemi tamamlamaya yönelik ilerleme durumunu temsil eder. Denetimde görünen çubuk bloklardan oluştuğu için, <xref:System.Windows.Forms.ProgressBar> denetim tarafından görünen değer yalnızca <xref:System.Windows.Forms.ProgressBar.Value%2A> özelliğin geçerli değerine yaklaştırır. <xref:System.Windows.Forms.ProgressBar> Denetimin boyutuna bağlı <xref:System.Windows.Forms.ProgressBar.Value%2A> olarak, özelliği sonraki bloğun ne zaman görüntüleneceğini belirler.  
  
 Geçerli ilerleme değerini güncelleştirmenin en yaygın yolu, <xref:System.Windows.Forms.ProgressBar.Value%2A> özelliği ayarlamak için kod yazmaktır. Büyük bir dosya yükleme örneğinde, en yüksek değeri kilobayt cinsinden dosyanın boyutuna ayarlayabilirsiniz. Örneğin, <xref:System.Windows.Forms.ProgressBar.Maximum%2A> özelliği 100 olarak ayarlanırsa <xref:System.Windows.Forms.ProgressBar.Minimum%2A> , özelliği 10 olarak ayarlanır ve <xref:System.Windows.Forms.ProgressBar.Value%2A> Özellik 50 olarak ayarlanır, 5 dikdörtgenleri görüntülenecektir. Bu, görüntülenebilecek sayının yarısıdır.  
  
 Ancak, <xref:System.Windows.Forms.ProgressBar> <xref:System.Windows.Forms.ProgressBar.Value%2A> özelliği doğrudan ayarlamanın yanı sıra, denetim tarafından görüntülenen değeri değiştirmek için başka yollar vardır. Özelliği, <xref:System.Windows.Forms.ProgressBar.Value%2A> özelliği tarafından arttırılacağı bir değer belirtmek için kullanılabilir. <xref:System.Windows.Forms.ProgressBar.Step%2A> Daha sonra, <xref:System.Windows.Forms.ProgressBar.PerformStep%2A> yöntemini çağırmak değeri artacaktır. Artış değerini değiştirmek için <xref:System.Windows.Forms.ProgressBar.Increment%2A> yöntemini kullanabilir ve <xref:System.Windows.Forms.ProgressBar.Value%2A> özelliğinin artırılacağı bir değer belirtebilirsiniz.  
  
 Kullanıcıyı geçerli bir eylem hakkında grafiksel olarak bildiren başka bir denetim <xref:System.Windows.Forms.StatusBar> denetim olur.  
  
> [!IMPORTANT]
> <xref:System.Windows.Forms.StatusStrip> <xref:System.Windows.Forms.StatusBar> <xref:System.Windows.Forms.StatusBarPanel> Ve denetimleri, vedenetimlerine<xref:System.Windows.Forms.StatusBarPanel> işlevsellik ekler ve bunları ekler; ancak, ve denetimleri hem geri uyumluluk hem de gelecekteki kullanım için korunur. <xref:System.Windows.Forms.StatusBar> <xref:System.Windows.Forms.ToolStripStatusLabel> 'yu.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.ProgressBar>
- [ProgressBar Denetimi](progressbar-control-windows-forms.md)
