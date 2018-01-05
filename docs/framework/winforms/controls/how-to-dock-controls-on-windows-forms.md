---
title: "Nasıl yapılır: Windows Formlarına Denetimleri Yerleştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [Windows Forms], docking
- Explorer-style applications [Windows Forms], creating
- Windows Forms controls, filling client area
ms.assetid: bc11f2e4-e90a-4830-b0e2-f43b6e2b8bec
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fc7227ee46f127070b44771a56a89b82bd0930ca
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-dock-controls-on-windows-forms"></a>Nasıl yapılır: Windows Formlarına Denetimleri Yerleştirme
Denetimleri form kenarlarına yerleştirme ya da bunları denetimin kapsayıcı (bir form veya bir kapsayıcı denetiminin) doldurun. Örneğin, Windows Gezgini noktalarını kendi <xref:System.Windows.Forms.TreeView> pencerenin sol tarafında denetimine ve kendi <xref:System.Windows.Forms.ListView> pencerenin sağ tarafında denetimine. Kullanım <xref:System.Windows.Forms.Control.Dock%2A> takma modunu tanımlamak tüm görünür Windows Forms denetimleri için özelliği.  
  
> [!NOTE]
>  Denetimleri ters z-sırada sabitlenir.  
  
 <xref:System.Windows.Forms.Control.Dock%2A> Özelliği etkileşime <xref:System.Windows.Forms.Control.AutoSize%2A> özelliği. Daha fazla bilgi için bkz: [AutoSize özelliğine genel bakış](../../../../docs/framework/winforms/controls/autosize-property-overview.md).  
  
### <a name="to-dock-a-control"></a>Bir denetim sabitlemek için  
  
1.  Sabitlemek istediğiniz denetimi seçin.  
  
2.  Özellikler penceresinde sağındaki oku <xref:System.Windows.Forms.Control.Dock%2A> özelliği.  
  
     Bir düzenleyici kutuları kenarları ve form merkezini temsil eden bir dizi gösteren görüntülenir.  
  
3.  Denetimi yerleştirmek istediğiniz formun kenarına temsil eden düğmesini tıklatın. Denetimin form veya kapsayıcı denetiminin içeriğini doldurmak için merkezi kutuyu tıklatın. Tıklatın **(hiçbiri)** yerleştirme devre dışı bırakmak için.  
  
     Denetim yerleşik kenar sınırlarına uyacak şekilde otomatik olarak boyutlandırılır.  
  
    > [!NOTE]
    >  Devralınan denetimleri olmalıdır `Protected` yerleşik için. Bir denetim erişim düzeyini değiştirmek için ayarlayın, **değiştiricisi** Özellikleri penceresinde özelliği.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows Forms Denetimleri](../../../../docs/framework/winforms/controls/index.md)  
 [Windows Forms’da Denetimleri Düzenleme](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [Ayrı Windows Forms Denetimlerini Etiketleme ve Kısayollarını Sunma](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)  
 [Windows Forms'da Kullanılacak Denetimler](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 [İşleve Göre Windows Forms Denetimleri](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)  
 [Nasıl yapılır: FlowLayoutPanel Denetiminde Alt Denetimleri Sabitleme ve Yerleştirme](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control.md)  
 [Nasıl yapılır: TableLayoutPanel Denetiminde Alt Denetimleri Sabitleme ve Yerleştirme](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)  
 [AutoSize Özelliğine Genel Bakış](../../../../docs/framework/winforms/controls/autosize-property-overview.md)  
 [Nasıl yapılır: Windows Forms’da Denetimleri Bağlama](../../../../docs/framework/winforms/controls/how-to-anchor-controls-on-windows-forms.md)
