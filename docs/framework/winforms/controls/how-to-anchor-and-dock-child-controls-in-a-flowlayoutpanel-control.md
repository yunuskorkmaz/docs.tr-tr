---
title: 'Nasıl yapılır: FlowLayoutPanel Denetiminde Alt Denetimleri Sabitleme ve Yerleştirme'
ms.date: 03/30/2017
helpviewer_keywords:
- layout [Windows Forms], child controls
- FlowLayoutPanel control [Windows Forms], child controls
- controls [Windows Forms], child
- child controls [Windows Forms], anchoring and docking
ms.assetid: a2bcdfca-9b63-45e6-9c0e-3411015cba98
ms.openlocfilehash: 2c8cb2d89ffaedde59d54edf6cae1f8c47548680
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control"></a>Nasıl yapılır: FlowLayoutPanel Denetiminde Alt Denetimleri Sabitleme ve Yerleştirme
<xref:System.Windows.Forms.FlowLayoutPanel> Kontrol destekler <xref:System.Windows.Forms.Control.Anchor%2A> ve <xref:System.Windows.Forms.Control.Dock%2A> alt denetimlerinden özelliklerinde.  
  
### <a name="to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control"></a>Sabitleme ve yerleştirme FlowLayoutPanel denetiminde alt denetimleri için  
  
1.  Oluşturma bir <xref:System.Windows.Forms.FlowLayoutPanel> formunuzda denetim.  
  
2.  Ayarlama <xref:System.Windows.Forms.Control.Width%2A> , <xref:System.Windows.Forms.FlowLayoutPanel> denetimini **300**ve kendi <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> için <xref:System.Windows.Forms.FlowDirection.TopDown>.  
  
3.  İki oluşturmak <xref:System.Windows.Forms.Button> denetler ve bunların içine yerleştirin <xref:System.Windows.Forms.FlowLayoutPanel> denetim.  
  
4.  Ayarlama <xref:System.Windows.Forms.Control.Width%2A> için ilk düğmesinin **200**.  
  
5.  Ayarlama <xref:System.Windows.Forms.Control.Dock%2A> ikinci düğme özelliğinin <xref:System.Windows.Forms.DockStyle.Fill>.  
  
    > [!NOTE]
    >  İkinci düğme ilk düğme aynı genişliğe varsayar. Genişliği boyunca genişlemez <xref:System.Windows.Forms.FlowLayoutPanel> denetim.  
  
6.  Ayarlama <xref:System.Windows.Forms.Control.Dock%2A> ikinci düğme özelliğinin `None`. Bu, özgün genişliğinin varsaymak düğmesi neden olur.  
  
7.  Ayarlama <xref:System.Windows.Forms.Control.Anchor%2A> ikinci düğme özelliğinin `Left, Right`.  
  
    > [!IMPORTANT]
    >  İkinci düğme ilk düğme aynı genişliğe varsayar. Genişliği boyunca genişlemez <xref:System.Windows.Forms.FlowLayoutPanel> denetim. Sabitleme ve yerleştirme içinde için genel kural budur <xref:System.Windows.Forms.FlowLayoutPanel> denetimi: dikey akış yönleri için <xref:System.Windows.Forms.FlowLayoutPanel> denetim hesaplar sütun geniş alt denetiminden kapsanan bir sütunun genişliği. Tüm bu sütunla denetimlerinde <xref:System.Windows.Forms.Control.Anchor%2A> veya <xref:System.Windows.Forms.Control.Dock%2A> hizalı ya da örtük bu sütunu sığdırmak için uzatılmış özellikleri. Davranış yatay akış yönleri için benzer şekilde çalışır. <xref:System.Windows.Forms.FlowLayoutPanel> Denetim satırda en uzun alt denetiminden kapsanan bir satırın yüksekliğini hesaplar ve tüm yerleşik veya bağlantılı alt denetimleri bu satırda hizalı veya örtük satır sığacak şekilde boyutlandırılmış.  
  
## <a name="example"></a>Örnek  
 Bağlantılı ve mavi düğmesini göre sabitlenmiş dört düğme aşağıdaki çizimde gösterilmektedir bir <xref:System.Windows.Forms.FlowLayoutPanel>. <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> Olan <xref:System.Windows.Forms.FlowDirection.LeftToRight>.  
  
 ![FlowLayoutPanel bağlama](../../../../docs/framework/winforms/controls/media/net-flpanchorexp.gif "NET_FLPanchorExp")  
  
 Bağlantılı ve mavi düğmesini göre sabitlenmiş dört düğme aşağıdaki çizimde gösterilmektedir bir <xref:System.Windows.Forms.FlowLayoutPanel>. <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> Olan <xref:System.Windows.Forms.FlowDirection.TopDown>.  
  
 ![FlowLayoutPanel bağlama](../../../../docs/framework/winforms/controls/media/vs-flpanchor2.gif "VS_FLPanchor2")  
  
 Aşağıdaki kod örneğinde çeşitli gösterilmektedir <xref:System.Windows.Forms.Control.Anchor%2A> özellik değerleri için bir <xref:System.Windows.Forms.Button> denetim bir <xref:System.Windows.Forms.FlowLayoutPanel> denetim.  
  
 [!code-csharp[System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm/CS/FlpAnchorExampleForm.cs#1)]
 [!code-vb[System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm/VB/FlpAnchorExampleForm.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   Sistem, System.Data, System.Drawing ve System.Windows.Forms derlemelerine başvurular.  
  
 Visual Basic veya Visual C# için bu örnek komut satırından oluşturma hakkında daha fazla bilgi için bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [komut satırı derleme ile csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Bu örnek Visual Studio'da yeni bir projeye kod yapıştırılarak de oluşturabilirsiniz.  Ayrıca bkz. [nasıl yapılır: derleme ve çalıştırma bir tam Windows Forms kod örneği kullanarak Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.FlowLayoutPanel>  
 [FlowLayoutPanel Denetimine Genel Bakış](../../../../docs/framework/winforms/controls/flowlayoutpanel-control-overview.md)
