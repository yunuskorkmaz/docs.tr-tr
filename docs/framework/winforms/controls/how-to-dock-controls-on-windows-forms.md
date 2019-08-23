---
title: "Nasıl yapılır: Windows Forms'a Denetimler Yerleştirme"
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], docking
- Explorer-style applications [Windows Forms], creating
- Windows Forms controls, filling client area
ms.assetid: bc11f2e4-e90a-4830-b0e2-f43b6e2b8bec
ms.openlocfilehash: dc514fd8b9b7a17bf07a878e42729db4187d2b82
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963622"
---
# <a name="how-to-dock-controls-on-windows-forms"></a>Nasıl yapılır: Windows Forms'a Denetimler Yerleştirme
Denetimleri formunuzun kenarlarına yerleştirebilirsiniz veya denetimin kapsayıcısını (form veya kapsayıcı denetimi) doldurmasını sağlayabilirsiniz. Örneğin, Windows Gezgini <xref:System.Windows.Forms.TreeView> , denetimini pencerenin sol tarafına <xref:System.Windows.Forms.ListView> ve denetimini pencerenin sağ tarafına göre denetler. Yerleştirme modunu tanımlamak için tüm görünür Windows Forms denetimlerinin özelliğinikullanın.<xref:System.Windows.Forms.Control.Dock%2A>  
  
> [!NOTE]
> Denetimler ters z düzeninde yerleşiktir.  
  
 <xref:System.Windows.Forms.Control.Dock%2A> Özelliği özelliği<xref:System.Windows.Forms.Control.AutoSize%2A> ile etkileşime girer. Daha fazla bilgi için bkz. [AutoSize özelliğine genel bakış](autosize-property-overview.md).  
  
### <a name="to-dock-a-control"></a>Bir denetimi sabitlemek için  
  
1. Sabitlemek istediğiniz denetimi seçin.  
  
2. Özellikler penceresi, <xref:System.Windows.Forms.Control.Dock%2A> özelliğin sağ tarafındaki oka tıklayın.  
  
     Bir düzenleyici görüntülenir ve bu, formun kenarlarını ve merkezini temsil eden bir kutu dizisini gösterir.  
  
3. Denetimin sabitlemek istediğiniz yerdeki formun kenarını temsil eden düğmeye tıklayın. Denetimin formunun veya kapsayıcı denetiminin içeriğini dolduracak Merkez kutusuna tıklayın. Yerleştirmeyi devre dışı bırakmak için **(yok)** seçeneğine tıklayın.  
  
     Denetim, yerleşik kenarın sınırlarına uyacak şekilde otomatik olarak yeniden boyutlandırılır.  
  
    > [!NOTE]
    > Devralınan denetimlerin yerleştirilamayacak `Protected` olması gerekir. Bir denetimin erişim düzeyini değiştirmek için Özellikler penceresi **değiştirici** özelliğini ayarlayın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Windows Forms Denetimleri](index.md)
- [Windows Forms’da Denetimleri Düzenleme](arranging-controls-on-windows-forms.md)
- [Ayrı Windows Forms Denetimlerini Etiketleme ve Kısayollarını Sunma](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [Windows Forms'da Kullanılacak Denetimler](controls-to-use-on-windows-forms.md)
- [İşleve Göre Windows Forms Denetimleri](windows-forms-controls-by-function.md)
- [Nasıl yapılır: FlowLayoutPanel denetiminde alt denetimleri sabitleme ve yerleştirme](how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control.md)
- [Nasıl yapılır: TableLayoutPanel denetiminde alt denetimleri sabitleme ve yerleştirme](how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [AutoSize Özelliğine Genel Bakış](autosize-property-overview.md)
- [Nasıl yapılır: Windows Forms üzerinde geçiş denetimleri](how-to-anchor-controls-on-windows-forms.md)
