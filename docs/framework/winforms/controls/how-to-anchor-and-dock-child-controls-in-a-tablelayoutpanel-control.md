---
title: 'Nasıl yapılır: TableLayoutPanel Denetiminde Alt Denetimleri Sabitleme ve Yerleştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
f1_keywords:
- net.ComponentModel.StyleCollectionEditor.TLP.AnchorDock
helpviewer_keywords:
- layout [Windows Forms], child controls
- controls [Windows Forms], child
- child controls [Windows Forms], anchoring and docking
- TableLayoutPanel control [Windows Forms], child controls
ms.assetid: 0d267c35-25f1-49b8-8976-c64e8f0ddc0b
ms.openlocfilehash: 82d75559260292476d81e4440280efb46bfd86c9
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64613017"
---
# <a name="how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control"></a>Nasıl yapılır: TableLayoutPanel Denetiminde Alt Denetimleri Sabitleme ve Yerleştirme
<xref:System.Windows.Forms.TableLayoutPanel> Denetim destekler <xref:System.Windows.Forms.Control.Anchor%2A> ve <xref:System.Windows.Forms.Control.Dock%2A> kendi alt denetimlerindeki özellikler.  
  
### <a name="to-align-a-child-control-in-a-tablelayoutpanel-cell"></a>Bir alt denetimin TableLayoutPanel hücredeki hizalamak için  
  
1. Oluşturma bir <xref:System.Windows.Forms.TableLayoutPanel> formunuzdaki denetimi.  
  
2. Değerini <xref:System.Windows.Forms.TableLayoutPanel> denetimin <xref:System.Windows.Forms.TableLayoutPanel.ColumnCount%2A> ve <xref:System.Windows.Forms.TableLayoutPanel.RowCount%2A> özelliklerine **1**.  
  
3. Oluşturma bir <xref:System.Windows.Forms.Button> denetim <xref:System.Windows.Forms.TableLayoutPanel> denetimi. <xref:System.Windows.Forms.Button> Hücresinin sol üst köşesinin kaplar.  
  
4. Değiştirin <xref:System.Windows.Forms.Button> denetimin <xref:System.Windows.Forms.Control.Anchor%2A> özelliğini `Left`. <xref:System.Windows.Forms.Button> Hücresinin sol kenarlık ile hizalamak denetimi taşır.  
  
    > [!NOTE]
    >  Bu davranış, diğer kapsayıcı denetimlerin davranışından farklıdır. Diğer kapsayıcı denetimlerinde ne zaman alt denetimin taşımaz <xref:System.Windows.Forms.Control.Anchor%2A> özelliği ayarlanır ve bağlantılı denetim ile üst kapsayıcının sınırları arasındaki uzaklığı zaman sabittir <xref:System.Windows.Forms.Control.Anchor%2A> özelliği ayarlanmış.  
  
5. Değiştirin <xref:System.Windows.Forms.Button> denetimin <xref:System.Windows.Forms.Control.Anchor%2A> özelliğini `Top, Left`. <xref:System.Windows.Forms.Button> Hücresinin sol üst köşedeki kaplaması denetimi taşır.  
  
6. Yineleme 5. adımı bir değerle `Top, Right` taşımak <xref:System.Windows.Forms.Button> hücrenin sağ üst köşedeki denetimi. Yineleme değerleriyle `Bottom, Left` ve `Bottom, Right`.  
  
### <a name="to-stretch-a-child-control-in-a-tablelayoutpanel-cell"></a>Bir alt denetimin TableLayoutPanel hücredeki uzatmak için  
  
1. Değiştirin <xref:System.Windows.Forms.Button> denetimin <xref:System.Windows.Forms.Control.Anchor%2A> özelliğini `Left, Right`. <xref:System.Windows.Forms.Button> Denetimi yeniden boyutlandırılır hücre arasında esnetme için.  
  
    > [!NOTE]
    >  Bu davranış, diğer kapsayıcı denetimlerin davranışından farklıdır. Diğer kapsayıcı denetimlerinde alt denetim değil ne zaman yeniden boyutlandırılmış <xref:System.Windows.Forms.Control.Anchor%2A> özelliği `Left, Right` veya `Top, Bottom`.  
  
2. Değiştirin <xref:System.Windows.Forms.Button> denetimin <xref:System.Windows.Forms.Control.Anchor%2A> özelliğini `Top, Bottom`. <xref:System.Windows.Forms.Button> Denetimi yeniden boyutlandırılır hücrenin en altına üstten esnetme için.  
  
3. Değiştirin <xref:System.Windows.Forms.Button> denetimin <xref:System.Windows.Forms.Control.Anchor%2A> özelliğini `Top, Bottom, Left, Right`. <xref:System.Windows.Forms.Button> Denetim hücreyi dolduracak şekilde yeniden boyutlandırılmış.  
  
4. Değiştirin <xref:System.Windows.Forms.Button> denetimin <xref:System.Windows.Forms.Control.Anchor%2A> özelliğini `None`. <xref:System.Windows.Forms.Button> Denetimi yeniden boyutlandırıldı ve hücreye ortalanmış.  
  
5. Değiştirin <xref:System.Windows.Forms.Button> denetimin <xref:System.Windows.Forms.Control.Dock%2A> özelliğini <xref:System.Windows.Forms.DockStyle.Left>. <xref:System.Windows.Forms.Button> Hücresinin sol kenarlık ile hizalamak denetimi taşır. <xref:System.Windows.Forms.Button> Denetiminin genişliğini korur, ancak yükseklik hücreyi dikey olarak doldurmak için boyutlandırılır.  
  
    > [!NOTE]
    >  Diğer kapsayıcı denetimlerinde oluşan aynı davranış budur.  
  
6. Değiştirin <xref:System.Windows.Forms.Button> denetimin <xref:System.Windows.Forms.Control.Dock%2A> özelliğini <xref:System.Windows.Forms.DockStyle.Fill>. <xref:System.Windows.Forms.Button> Denetim hücreyi dolduracak şekilde yeniden boyutlandırılmış.  
  
## <a name="example"></a>Örnek  
 Beş düğmeden beş ayrı bağlantılı aşağıdaki çizimde <xref:System.Windows.Forms.TableLayoutPanel> hücreleri.  
  
 ![TableLayoutPanel Bağlama](./media/vs-tlpanchor.gif "VS_TLPanchor")  
  
 Aşağıdaki çizimde dört ayrı köşelerini bağlantılı dört düğme <xref:System.Windows.Forms.TableLayoutPanel> hücreleri.  
  
 ![TableLayoutPanel Bağlama](./media/vs-tlpanchor2.gif "VS_TLPanchor2")  
  
 Üç ayrı bağlama tarafından esnetilmiş üç düğme aşağıdaki çizimde <xref:System.Windows.Forms.TableLayoutPanel> hücreleri.  
  
 ![TableLayoutPanel Bağlama](./media/vs-tlpanchor3.gif "VS_TLPAnchor3")  
  
 Aşağıdaki kod örneği, tüm bileşimleri gösterir <xref:System.Windows.Forms.Control.Anchor%2A> özellik değerleri için bir <xref:System.Windows.Forms.Button> denetimine bir <xref:System.Windows.Forms.TableLayoutPanel> denetimi.  
  
 [!code-csharp[System.Windows.Forms.TableLayoutPanel.AnchorExampleForm#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.AnchorExampleForm/CS/TlpAnchorExampleForm.cs#1)]
 [!code-vb[System.Windows.Forms.TableLayoutPanel.AnchorExampleForm#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.AnchorExampleForm/VB/TlpAnchorExampleForm.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
- Sistem, System.Data System.Drawing ve System.Windows.Forms derlemelere başvuruları.  
  
 Visual Basic veya Visual C# için bu örnek komut satırından derleme hakkında daha fazla bilgi için bkz: [komut satırından derleme](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [oluşturma ile komut satırı csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Visual Studio bu örnekte yeni bir projeye kod yapıştırarak da oluşturabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.TableLayoutPanel>
- [TableLayoutPanel Denetimi](tablelayoutpanel-control-windows-forms.md)
