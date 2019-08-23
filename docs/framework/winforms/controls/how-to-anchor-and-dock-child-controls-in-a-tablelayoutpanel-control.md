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
ms.openlocfilehash: 0e565b56c31d0776f6e89bbbe0b0681ae184758e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69922816"
---
# <a name="how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control"></a>Nasıl yapılır: TableLayoutPanel Denetiminde Alt Denetimleri Sabitleme ve Yerleştirme
Denetim, <xref:System.Windows.Forms.Control.Anchor%2A> alt denetimlerinde ve <xref:System.Windows.Forms.Control.Dock%2A> özelliklerini destekler. <xref:System.Windows.Forms.TableLayoutPanel>  
  
### <a name="to-align-a-child-control-in-a-tablelayoutpanel-cell"></a>TableLayoutPanel hücresindeki bir alt denetimi hizalamak için  
  
1. Formunuzda bir <xref:System.Windows.Forms.TableLayoutPanel> denetim oluşturun.  
  
2. <xref:System.Windows.Forms.TableLayoutPanel> Denetimin ve özelliklerinin<xref:System.Windows.Forms.TableLayoutPanel.RowCount%2A> değerini 1 olarak ayarlayın. <xref:System.Windows.Forms.TableLayoutPanel.ColumnCount%2A>  
  
3. <xref:System.Windows.Forms.TableLayoutPanel> Denetimde bir <xref:System.Windows.Forms.Button> denetim oluşturun. Hücrenin sol üst köşesini kaplar.<xref:System.Windows.Forms.Button>  
  
4. <xref:System.Windows.Forms.Button> Denetimin özelliğinin değerini olarak`Left`değiştirin. <xref:System.Windows.Forms.Control.Anchor%2A> Denetim <xref:System.Windows.Forms.Button> , hücrenin sol kenarlığına göre hizalanacak şekilde gider.  
  
    > [!NOTE]
    > Bu davranış, diğer kapsayıcı denetimlerinin davranışından farklıdır. Diğer kapsayıcı denetimlerinde, <xref:System.Windows.Forms.Control.Anchor%2A> özellik ayarlandığında alt denetim hareket etmez ve bağlantılı denetim ile üst kapsayıcının sınırı arasındaki mesafe, <xref:System.Windows.Forms.Control.Anchor%2A> özelliğin ayarlandığı zamanda düzeltilir.  
  
5. <xref:System.Windows.Forms.Button> Denetimin özelliğinin değerini olarak`Top, Left`değiştirin. <xref:System.Windows.Forms.Control.Anchor%2A> Denetim <xref:System.Windows.Forms.Button> , hücrenin sol üst köşesinin kaplamasına karşı gider.  
  
6. <xref:System.Windows.Forms.Button> Denetimi hücrenin sağ üst köşesine taşımak `Top, Right` için değeri olan 5. adımı yineleyin. `Bottom, Left` Ve`Bottom, Right`değerleri ile tekrarlayın.  
  
### <a name="to-stretch-a-child-control-in-a-tablelayoutpanel-cell"></a>TableLayoutPanel hücresindeki bir alt denetimi uzatmak için  
  
1. <xref:System.Windows.Forms.Button> Denetimin özelliğinin değerini olarak`Left, Right`değiştirin. <xref:System.Windows.Forms.Control.Anchor%2A> <xref:System.Windows.Forms.Button> Denetim hücre üzerinde uzatmak için yeniden boyutlandırılır.  
  
    > [!NOTE]
    > Bu davranış, diğer kapsayıcı denetimlerinin davranışından farklıdır. Diğer kapsayıcı denetimlerinde, <xref:System.Windows.Forms.Control.Anchor%2A> özelliği veya `Top, Bottom`olarak `Left, Right` ayarlandığında alt denetim yeniden boyutlandırılmaz.  
  
2. <xref:System.Windows.Forms.Button> Denetimin özelliğinin değerini olarak`Top, Bottom`değiştirin. <xref:System.Windows.Forms.Control.Anchor%2A> <xref:System.Windows.Forms.Button> Denetim, hücrenin en üstünden aşağı doğru uzatmak için yeniden boyutlandırılır.  
  
3. <xref:System.Windows.Forms.Button> Denetimin özelliğinin değerini olarak`Top, Bottom, Left, Right`değiştirin. <xref:System.Windows.Forms.Control.Anchor%2A> <xref:System.Windows.Forms.Button> Denetim hücreyi dolduracak şekilde yeniden boyutlandırılır.  
  
4. <xref:System.Windows.Forms.Button> Denetimin özelliğinin değerini olarak`None`değiştirin. <xref:System.Windows.Forms.Control.Anchor%2A> <xref:System.Windows.Forms.Button> Denetim yeniden boyutlandırıldı ve hücrede ortalandı.  
  
5. <xref:System.Windows.Forms.Button> Denetimin özelliğinin değerini olarak<xref:System.Windows.Forms.DockStyle.Left>değiştirin. <xref:System.Windows.Forms.Control.Dock%2A> Denetim <xref:System.Windows.Forms.Button> , hücrenin sol kenarlığına göre hizalanacak şekilde gider. <xref:System.Windows.Forms.Button> Denetim genişliğini korur, ancak yüksekliği hücreyi dikey olarak dolduracak şekilde yeniden boyutlandırılır.  
  
    > [!NOTE]
    > Bu, diğer kapsayıcı denetimlerinde gerçekleşen davranıştır.  
  
6. <xref:System.Windows.Forms.Button> Denetimin özelliğinin değerini olarak<xref:System.Windows.Forms.DockStyle.Fill>değiştirin. <xref:System.Windows.Forms.Control.Dock%2A> <xref:System.Windows.Forms.Button> Denetim hücreyi dolduracak şekilde yeniden boyutlandırılır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki çizimde beş ayrı <xref:System.Windows.Forms.TableLayoutPanel> hücrede sabitlenmiş beş düğme gösterilmektedir.  
  
 ![TableLayoutPanel sabitleme](./media/vs-tlpanchor.gif "VS_TLPanchor")  
  
 Aşağıdaki çizimde dört ayrı <xref:System.Windows.Forms.TableLayoutPanel> hücrenin köşelerinde sabitlenmiş dört düğme gösterilmektedir.  
  
 ![TableLayoutPanel sabitleme](./media/vs-tlpanchor2.gif "VS_TLPanchor2")  
  
 Aşağıdaki çizimde üç ayrı <xref:System.Windows.Forms.TableLayoutPanel> hücrede sabitleme ile uzatılmış üç düğme gösterilmektedir.  
  
 ![TableLayoutPanel sabitleme](./media/vs-tlpanchor3.gif "VS_TLPAnchor3")  
  
 Aşağıdaki kod örneği, bir <xref:System.Windows.Forms.Control.Anchor%2A> <xref:System.Windows.Forms.TableLayoutPanel> denetimdeki <xref:System.Windows.Forms.Button> denetim için özellik değerlerinin tüm birleşimlerini gösterir.  
  
 [!code-csharp[System.Windows.Forms.TableLayoutPanel.AnchorExampleForm#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.AnchorExampleForm/CS/TlpAnchorExampleForm.cs#1)]
 [!code-vb[System.Windows.Forms.TableLayoutPanel.AnchorExampleForm#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.AnchorExampleForm/VB/TlpAnchorExampleForm.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek şunları gerektirir:  
  
- System, System. Data, System. Drawing ve System. Windows. Forms derlemelerine başvurular.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.TableLayoutPanel>
- [TableLayoutPanel Denetimi](tablelayoutpanel-control-windows-forms.md)
