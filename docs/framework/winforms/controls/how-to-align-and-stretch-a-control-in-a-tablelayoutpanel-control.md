---
title: "Nasıl yapılır: TableLayoutPanel Denetiminde Bir Denetimi Hizalama ve Uzatma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: net.ComponentModel.StyleCollectionEditor.TLP.AlignStretchCtrl
helpviewer_keywords:
- TableLayoutPanel control [Windows Forms], stretching controls
- controls [Windows Forms], stretching
- controls [Windows Forms], aligning
ms.assetid: 7dc1a157-6fee-4995-8ebc-b65bdc0909a8
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bfc1c64bc0bd9cbebad44193fb5adbe529877487
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-align-and-stretch-a-control-in-a-tablelayoutpanel-control"></a>Nasıl yapılır: TableLayoutPanel Denetiminde Bir Denetimi Hizalama ve Uzatma
Hizalama ve uzatma denetimlerinde bir <xref:System.Windows.Forms.TableLayoutPanel> ile <xref:System.Windows.Forms.Control.Anchor%2A> ve <xref:System.Windows.Forms.Control.Dock%2A> özellikleri.  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-align-and-stretch-a-control"></a>Hizalama ve uzatma bir denetim için  
  
1.  Sürükleme bir <xref:System.Windows.Forms.TableLayoutPanel> gelen denetim **araç** formunuza.  
  
2.  Sürükleme bir <xref:System.Windows.Forms.Button> gelen denetim **araç** sol üst hücresine <xref:System.Windows.Forms.TableLayoutPanel> denetim. <xref:System.Windows.Forms.Button> Denetim hücrede ortalanır.  
  
3.  Değerini <xref:System.Windows.Forms.Button> denetimin <xref:System.Windows.Forms.Control.Anchor%2A> özelliğine `Left,Right`. <xref:System.Windows.Forms.Button> Denetim hücrenin genişliği eşleşecek şekilde uzatır.  
  
4.  Değerini <xref:System.Windows.Forms.Button> denetimin <xref:System.Windows.Forms.Control.Anchor%2A> özelliğine `Top,Bottom`. <xref:System.Windows.Forms.Button> Denetim hücre yüksekliği eşleşecek şekilde uzatır.  
  
5.  Değerini <xref:System.Windows.Forms.Button> denetimin <xref:System.Windows.Forms.Control.Dock%2A> özelliğine <xref:System.Windows.Forms.DockStyle.Fill>. <xref:System.Windows.Forms.Button> Denetimini genişleten hücreyi doldurmak için.  
  
6.  Değerini <xref:System.Windows.Forms.Button> denetimin <xref:System.Windows.Forms.Control.Dock%2A> özelliğine <xref:System.Windows.Forms.DockStyle.None>. <xref:System.Windows.Forms.Button> Denetimi özgün boyutuna döndürür ve hücrenin sol üst köşesinde taşır. **Windows Form Tasarımcısı** ayarlanmış <xref:System.Windows.Forms.Control.Anchor%2A> özelliğine `Top, Left`.  
  
7.  Değerini <xref:System.Windows.Forms.Button> denetimin <xref:System.Windows.Forms.Control.Anchor%2A> özelliğine `Bottom,Right`. <xref:System.Windows.Forms.Button> Denetimi hücrenin sağ alt köşedeki taşır.  
  
8.  Değerini <xref:System.Windows.Forms.Button> denetimin <xref:System.Windows.Forms.Control.Anchor%2A> özelliğine <xref:System.Windows.Forms.AnchorStyles.None>. <xref:System.Windows.Forms.Button> Denetimi hücrenin merkezine taşır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [TableLayoutPanel Denetimi](../../../../docs/framework/winforms/controls/tablelayoutpanel-control-windows-forms.md)
