---
title: 'Nasıl yapılır: TabControl ile Yana Hizalanmış Sekmeler Görüntüleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tab pages [Windows Forms], displaying side-aligned tabs
- tabs [Windows Forms], displaying side-aligned tabs
- TabControl control [Windows Forms], displaying side-aligned tabs
ms.assetid: 110d5abd-3ae3-4ded-95bf-778aaac798a0
ms.openlocfilehash: ce0c7d48f053094d0026348fea8221ea80ccca59
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59142902"
---
# <a name="how-to-display-side-aligned-tabs-with-tabcontrol"></a>Nasıl yapılır: TabControl ile Yana Hizalanmış Sekmeler Görüntüleme
<xref:System.Windows.Forms.TabControl.Alignment%2A> Özelliği <xref:System.Windows.Forms.TabControl> yatay (üst veya alt denetimin) olarak, dikey (sol veya sağ kenarı boyunca denetimi), sekmeler görüntüleme destekler. Varsayılan olarak, çünkü bu dikey ekran bir kullanıcı deneyimi zayıf içinde sonuçları <xref:System.Windows.Forms.TabPage.Text%2A> özelliği <xref:System.Windows.Forms.TabPage> nesne görsel stiller etkinken sekmede görüntülemez. Sekme içindeki metnin yönünü denetlemek için doğrudan bir yol yoktur. Sahibi kullanabileceğiniz üzerine çizileceği <xref:System.Windows.Forms.TabControl> iyi bir deneyim sunmak için.  
  
 Aşağıdaki yordam, soldan sağa "sahibi Çiz" özelliğini kullanarak çalışan sekmesini metin içeren sağa hizalanmış sekmeler, nasıl oluşturulacağını gösterir.  
  
### <a name="to-display-right-aligned-tabs"></a>Sağa hizalı sekmelerini görüntülemek için  
  
1.  Ekleme bir <xref:System.Windows.Forms.TabControl> formunuza.  
  
2.  Ayarlama <xref:System.Windows.Forms.TabControl.Alignment%2A> özelliğini <xref:System.Windows.Forms.TabAlignment.Right>.  
  
3.  Ayarlama <xref:System.Windows.Forms.TabControl.SizeMode%2A> özelliğini <xref:System.Windows.Forms.TabSizeMode.Fixed>, böylece tüm sekmeler aynı genişliktedir.  
  
4.  Ayarlama <xref:System.Windows.Forms.TabControl.ItemSize%2A> özelliği tercih edilen sekmeleri boyutu sabit. Aklınızda <xref:System.Windows.Forms.TabControl.ItemSize%2A> özelliği, sekmeleri en üstte gibi davranarak sağa hizalı olmasına rağmen davranır. Sonuç olarak, sekmeleri geniş hale getirmek için değiştirmeniz gerekir <xref:System.Drawing.Size.Height%2A> özelliği ve uzun hale getirmek için değiştirmelisiniz <xref:System.Drawing.Size.Width%2A> özelliği.  
  
     Aşağıdaki kod örneği ile en iyi sonuç için kümesi <xref:System.Drawing.Size.Width%2A> 25 sekmeleri ve <xref:System.Drawing.Size.Height%2A> 100.  
  
5.  Ayarlama <xref:System.Windows.Forms.TabControl.DrawMode%2A> özelliğini <xref:System.Windows.Forms.TabDrawMode.OwnerDrawFixed>.  
  
6.  Tanımlamak için bir işleyici <xref:System.Windows.Forms.TabControl.DrawItem> olayı <xref:System.Windows.Forms.TabControl> , soldan sağa metnin işler.  
  
     [!code-csharp[TabControl.RightAlignedTabs#1](~/samples/snippets/csharp/VS_Snippets_Winforms/TabControl.RightAlignedTabs/CS/Form1.cs#1)]
     [!code-vb[TabControl.RightAlignedTabs#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/TabControl.RightAlignedTabs/VB/Form1.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [TabControl Denetimi](tabcontrol-control-windows-forms.md)
