---
title: "Nasıl yapılır: TableLayoutPanel Denetiminde Alt Denetimleri Sabitleme ve Yerleştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
f1_keywords: net.ComponentModel.StyleCollectionEditor.TLP.AnchorDock
helpviewer_keywords:
- layout [Windows Forms], child controls
- controls [Windows Forms], child
- child controls [Windows Forms], anchoring and docking
- TableLayoutPanel control [Windows Forms], child controls
ms.assetid: 0d267c35-25f1-49b8-8976-c64e8f0ddc0b
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 56909c823beca99d277bfbf7a20d39663bcd44ae
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control"></a>Nasıl yapılır: TableLayoutPanel Denetiminde Alt Denetimleri Sabitleme ve Yerleştirme
<xref:System.Windows.Forms.TableLayoutPanel> Kontrol destekler <xref:System.Windows.Forms.Control.Anchor%2A> ve <xref:System.Windows.Forms.Control.Dock%2A> alt denetimlerinden özelliklerinde.  
  
### <a name="to-align-a-child-control-in-a-tablelayoutpanel-cell"></a>TableLayoutPanel hücre alt denetiminde hizalamak için  
  
1.  Oluşturma bir <xref:System.Windows.Forms.TableLayoutPanel> formunuzda denetim.  
  
2.  Değerini <xref:System.Windows.Forms.TableLayoutPanel> denetimin <xref:System.Windows.Forms.TableLayoutPanel.ColumnCount%2A> ve <xref:System.Windows.Forms.TableLayoutPanel.RowCount%2A> özelliklerine **1**.  
  
3.  Oluşturma bir <xref:System.Windows.Forms.Button> denetim <xref:System.Windows.Forms.TableLayoutPanel> denetim. <xref:System.Windows.Forms.Button> Hücrenin sol üst köşesinde yer kaplar.  
  
4.  Değerini değiştirme <xref:System.Windows.Forms.Button> denetimin <xref:System.Windows.Forms.Control.Anchor%2A> özelliğine `Left`. <xref:System.Windows.Forms.Button> Denetimi taşır hücrenin sol kenarlık ile hizalamak.  
  
    > [!NOTE]
    >  Bu davranış diğer kapsayıcı denetimleri davranışından farklıdır. Kapsayıcı denetimleri, ne zaman alt denetim taşımaz <xref:System.Windows.Forms.Control.Anchor%2A> özelliği ayarlanmış ve bağlantılı denetim ile üst kapsayıcının sınır arasındaki uzaklığı zaman sabit <xref:System.Windows.Forms.Control.Anchor%2A> özelliği ayarlanmış.  
  
5.  Değerini değiştirme <xref:System.Windows.Forms.Button> denetimin <xref:System.Windows.Forms.Control.Anchor%2A> özelliğine `Top, Left`. <xref:System.Windows.Forms.Button> Denetim hücrenin sol üst köşesinde kaplar taşır.  
  
6.  Yineleme 5. adımını bir değerle `Top, Right` taşımak için <xref:System.Windows.Forms.Button> hücrenin sağ üst köşesinde denetimine. Yineleme değerlerle `Bottom, Left` ve `Bottom, Right`.  
  
### <a name="to-stretch-a-child-control-in-a-tablelayoutpanel-cell"></a>TableLayoutPanel hücre alt denetiminde uzatmak için  
  
1.  Değerini değiştirme <xref:System.Windows.Forms.Button> denetimin <xref:System.Windows.Forms.Control.Anchor%2A> özelliğine `Left, Right`. <xref:System.Windows.Forms.Button> Denetim yeniden boyutlandırılır hücre boyunca uzatmak için.  
  
    > [!NOTE]
    >  Bu davranış diğer kapsayıcı denetimleri davranışından farklıdır. Diğer kapsayıcı denetimleri alt denetim değil ne zaman yeniden boyutlandırılabilir <xref:System.Windows.Forms.Control.Anchor%2A> özelliği ayarlanmış `Left, Right` veya `Top, Bottom`.  
  
2.  Değerini değiştirme <xref:System.Windows.Forms.Button> denetimin <xref:System.Windows.Forms.Control.Anchor%2A> özelliğine `Top, Bottom`. <xref:System.Windows.Forms.Button> Denetim yeniden boyutlandırılır üstten hücrenin en altına uzatmak için.  
  
3.  Değerini değiştirme <xref:System.Windows.Forms.Button> denetimin <xref:System.Windows.Forms.Control.Anchor%2A> özelliğine `Top, Bottom, Left, Right`. <xref:System.Windows.Forms.Button> Denetim yeniden boyutlandırılır hücreyi doldurmak için.  
  
4.  Değerini değiştirme <xref:System.Windows.Forms.Button> denetimin <xref:System.Windows.Forms.Control.Anchor%2A> özelliğine `None`. <xref:System.Windows.Forms.Button> Denetim yeniden boyutlandırılabilir ve hücrede ortalanır.  
  
5.  Değerini değiştirme <xref:System.Windows.Forms.Button> denetimin <xref:System.Windows.Forms.Control.Dock%2A> özelliğine <xref:System.Windows.Forms.DockStyle.Left>. <xref:System.Windows.Forms.Button> Denetimi taşır hücrenin sol kenarlık ile hizalamak. <xref:System.Windows.Forms.Button> Denetim genişliğini korur, ancak kendi yüksekliğini hücreyi dikey doldurmak için yeniden boyutlandırılmış.  
  
    > [!NOTE]
    >  Kapsayıcı denetimleri oluşan aynı davranış budur.  
  
6.  Değerini değiştirme <xref:System.Windows.Forms.Button> denetimin <xref:System.Windows.Forms.Control.Dock%2A> özelliğine <xref:System.Windows.Forms.DockStyle.Fill>. <xref:System.Windows.Forms.Button> Denetim yeniden boyutlandırılır hücreyi doldurmak için.  
  
## <a name="example"></a>Örnek  
 Beş düğmeden beş ayrı bağlantılı aşağıda gösterilmiştir <xref:System.Windows.Forms.TableLayoutPanel> hücreleri.  
  
 ![TableLayoutPanel Bağlama](../../../../docs/framework/winforms/controls/media/vs-tlpanchor.gif "VS_TLPanchor")  
  
 Aşağıdaki çizimde dört ayrı köşelerinde bağlantılı dört düğme gösterilmektedir <xref:System.Windows.Forms.TableLayoutPanel> hücreleri.  
  
 ![TableLayoutPanel Bağlama](../../../../docs/framework/winforms/controls/media/vs-tlpanchor2.gif "VS_TLPanchor2")  
  
 Aşağıdaki çizim üç ayrı sabitleme tarafından uzatılmış üç düğme göstermektedir <xref:System.Windows.Forms.TableLayoutPanel> hücreleri.  
  
 ![TableLayoutPanel Bağlama](../../../../docs/framework/winforms/controls/media/vs-tlpanchor3.gif "VS_TLPAnchor3")  
  
 Aşağıdaki kod örneğinde tüm bileşimleri gösterilmektedir <xref:System.Windows.Forms.Control.Anchor%2A> özellik değerleri için bir <xref:System.Windows.Forms.Button> denetim bir <xref:System.Windows.Forms.TableLayoutPanel> denetim.  
  
 [!code-csharp[System.Windows.Forms.TableLayoutPanel.AnchorExampleForm#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.AnchorExampleForm/CS/TlpAnchorExampleForm.cs#1)]
 [!code-vb[System.Windows.Forms.TableLayoutPanel.AnchorExampleForm#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.AnchorExampleForm/VB/TlpAnchorExampleForm.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   Sistem, System.Data, System.Drawing ve System.Windows.Forms derlemelerine başvurular.  
  
 Bu örnek için komut satırından oluşturma hakkında bilgi için [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] veya [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [komut satırı derleme ile csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Bu örnek ayrıca oluşturmak [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] yeni bir proje kodunu yapıştırma tarafından.  Ayrıca bkz. [nasıl yapılır: derleme ve çalıştırma bir tam Windows Forms kod örneği kullanarak Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.TableLayoutPanel>  
 [TableLayoutPanel Denetimi](../../../../docs/framework/winforms/controls/tablelayoutpanel-control-windows-forms.md)
