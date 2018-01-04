---
title: "Nasıl yapılır: Tasarım Zamanında Denetimi Formların Kenarlarına Hizalama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- custom controls [Windows Forms], docking using designer
- Dock property [Windows Forms], aligning controls (using designer)
ms.assetid: 51f08998-5e3b-4330-be58-a4edd0eb60f4
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3ca5f32d95ddaa2dac03ad55e2599bafe5af502f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-align-a-control-to-the-edges-of-forms-at-design-time"></a>Nasıl yapılır: Tasarım Zamanında Denetimi Formların Kenarlarına Hizalama
Formlarınızı için ayarlayarak hizalar denetiminizi yapabileceğiniz <xref:System.Windows.Forms.Control.Dock%2A>. Bu özellik, Denetim biçiminde bulunduğu belirler. <xref:System.Windows.Forms.Control.Dock%2A> Özelliği aşağıdaki değerlere ayarlanabilir:  
  
|Ayar|Denetim etkisi|  
|-------------|----------------------------|  
|<xref:System.Windows.Forms.DockStyle.Bottom>|Formun altına noktaları.|  
|<xref:System.Windows.Forms.DockStyle.Fill>|Formdaki tüm kalan alanı doldurur.|  
|<xref:System.Windows.Forms.DockStyle.Left>|Formun sol tarafına noktaları.|  
|<xref:System.Windows.Forms.DockStyle.None>|Yoksa her yerden ve onu görünen tarafından belirtilen konumda yerleştirme kendi <xref:System.Windows.Forms.Control.Location%2A>.|  
|<xref:System.Windows.Forms.DockStyle.Right>|Formun sağ tarafındaki noktaları.|  
|<xref:System.Windows.Forms.DockStyle.Top>|Formun üstüne noktaları.|  
  
 Bu değerleri kodda de ayarlanabilir. Daha fazla bilgi için bkz: [nasıl yapılır: biçimlerine kenarları denetimi hizalama](../../../../docs/framework/winforms/controls/how-to-align-a-control-to-the-edges-of-forms.md).  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-set-the-dock-property-for-your-control-at-design-time"></a>Tasarım zamanında denetiminizi Dock özelliğini ayarlamak için  
  
1.  Windows Forms Tasarımcısı'nda, denetimi seçin.  
  
2.  İçinde **özellikleri** penceresinde, aşağı açılan kutusu sonraki tıklatın <xref:System.Windows.Forms.Control.Dock%2A> özelliği.  
  
     Altı olası temsil eden bir grafik arabirim <xref:System.Windows.Forms.Control.Dock%2A> ayarları görüntülenir.  
  
3.  Uygun ayarı seçin.  
  
4.  Denetim şimdi ayarı tarafından belirlenen şekilde yerleştirme.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.Control.Dock%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.Control.Anchor%2A?displayProperty=nameWithType>  
 [Nasıl yapılır: Denetimi Formların Kenarlarına Hizalama](../../../../docs/framework/winforms/controls/how-to-align-a-control-to-the-edges-of-forms.md)  
 [İzlenecek yol: Dayama Çizgileri Kullanarak Windows Forms'da Denetimleri Düzenleme](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)  
 [Nasıl yapılır: Windows Forms’da Denetimleri Bağlama](../../../../docs/framework/winforms/controls/how-to-anchor-controls-on-windows-forms.md)  
 [Nasıl yapılır: TableLayoutPanel Denetiminde Alt Denetimleri Sabitleme ve Yerleştirme](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)  
 [Nasıl yapılır: FlowLayoutPanel Denetiminde Alt Denetimleri Sabitleme ve Yerleştirme](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control.md)  
 [İzlenecek yol: TableLayoutPanel Kullanarak Windows Forms'da Denetimleri Düzenleme](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)  
 [İzlenecek yol: FlowLayoutPanel Kullanarak Windows Forms'da Denetimleri Düzenleme](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)  
 [Tasarım Zamanında Windows Forms Denetimleri Geliştirme](../../../../docs/framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)
