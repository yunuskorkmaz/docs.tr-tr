---
title: "Nasıl Yapılır: TabControl ile Yana Hizalanmış Sekmeler Görüntüleme"
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
helpviewer_keywords:
- tab pages [Windows Forms], displaying side-aligned tabs
- tabs [Windows Forms], displaying side-aligned tabs
- TabControl control [Windows Forms], displaying side-aligned tabs
ms.assetid: 110d5abd-3ae3-4ded-95bf-778aaac798a0
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8d95e2aace6dc50b16aeea0fca02f0a27c37322c
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-display-side-aligned-tabs-with-tabcontrol"></a>Nasıl Yapılır: TabControl ile Yana Hizalanmış Sekmeler Görüntüleme
<xref:System.Windows.Forms.TabControl.Alignment%2A> Özelliği <xref:System.Windows.Forms.TabControl> yatay (üst veya alt denetim) tersine dikey (sol veya sağ kenarı boyunca denetimi), sekmeler görüntüleme destekler. Varsayılan olarak, çünkü bir zayıf bir kullanıcı deneyimi bu dikey görüntü yapılandırmayı sağlar. <xref:System.Windows.Forms.TabPage.Text%2A> özelliği <xref:System.Windows.Forms.TabPage> nesne görsel stiller etkinken sekmesinde görüntülemez. Sekme içindeki metnin yönünü denetlemek için doğrudan yolu yoktur. Sahibi kullanabilirsiniz Çiz <xref:System.Windows.Forms.TabControl> bu deneyimini geliştirmek için.  
  
 Aşağıdaki yordam nasıl "sahibi çizin" özelliğini kullanarak soldan sağa çalıştıran sekmesini metinle sağa hizalı sekmeler işleneceğini gösterir.  
  
### <a name="to-display-right-aligned-tabs"></a>Sağa hizalı sekmelerini görüntülemek için  
  
1.  Ekleme bir <xref:System.Windows.Forms.TabControl> formunuza.  
  
2.  Ayarlama <xref:System.Windows.Forms.TabControl.Alignment%2A> özelliğine <xref:System.Windows.Forms.TabAlignment.Right>.  
  
3.  Ayarlama <xref:System.Windows.Forms.TabControl.SizeMode%2A> özelliğine <xref:System.Windows.Forms.TabSizeMode.Fixed>, böylece tüm sekmeler aynı genişliği.  
  
4.  Ayarlama <xref:System.Windows.Forms.TabControl.ItemSize%2A> tercih edilen özelliğine sabit sekmeleri boyutu. Aklınızda <xref:System.Windows.Forms.TabControl.ItemSize%2A> özelliği, sekmeler en üstte, gibi davranarak sağa hizalı olsa davranır. Sonuç olarak, daha geniş sekmeleri yapmak için değiştirmelisiniz <xref:System.Drawing.Size.Height%2A> özelliği ve bunları eninden yapmak için değiştirmelisiniz <xref:System.Drawing.Size.Width%2A> özelliği.  
  
     Aşağıdaki kod örneği ile en iyi sonuç için kümesi <xref:System.Drawing.Size.Width%2A> 25 sekmelerinin ve <xref:System.Drawing.Size.Height%2A> 100.  
  
5.  Ayarlama <xref:System.Windows.Forms.TabControl.DrawMode%2A> özelliğine <xref:System.Windows.Forms.TabDrawMode.OwnerDrawFixed>.  
  
6.  Tanımlamak için bir işleyici <xref:System.Windows.Forms.TabControl.DrawItem> olayı <xref:System.Windows.Forms.TabControl> soldan sağa metnin işler.  
  
     [!code-csharp[TabControl.RightAlignedTabs#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/TabControl.RightAlignedTabs/CS/Form1.cs#1)]
     [!code-vb[TabControl.RightAlignedTabs#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/TabControl.RightAlignedTabs/VB/Form1.vb#1)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [TabControl denetimi](../../../../docs/framework/winforms/controls/tabcontrol-control-windows-forms.md)
