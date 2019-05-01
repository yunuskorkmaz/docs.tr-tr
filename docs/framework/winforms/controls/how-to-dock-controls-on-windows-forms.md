---
title: "Nasıl yapılır: Windows Forms'a Denetimler Yerleştirme"
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], docking
- Explorer-style applications [Windows Forms], creating
- Windows Forms controls, filling client area
ms.assetid: bc11f2e4-e90a-4830-b0e2-f43b6e2b8bec
ms.openlocfilehash: d015dce7307bec092f6da1dc5ee31691a6baf1f0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61941511"
---
# <a name="how-to-dock-controls-on-windows-forms"></a>Nasıl yapılır: Windows Forms'a Denetimler Yerleştirme
Formunuza kenarlarına denetimleri yerleştirme veya onlara denetimin kapsayıcı (bir form veya bir kapsayıcı denetimi) doldurun. Örneğin, Windows Gezgini noktaları kendi <xref:System.Windows.Forms.TreeView> pencerenin sol tarafındaki denetim ve kendi <xref:System.Windows.Forms.ListView> penceresinin sağ tarafındaki denetimi. Kullanım <xref:System.Windows.Forms.Control.Dock%2A> yerleştirme modu tanımlamak, tüm görünür Windows Forms denetimleri için özellik.  
  
> [!NOTE]
>  Denetimleri ters z düzeninde sabitlenir.  
  
 <xref:System.Windows.Forms.Control.Dock%2A> Özelliği etkileşim <xref:System.Windows.Forms.Control.AutoSize%2A> özelliği. Daha fazla bilgi için [AutoSize özelliğine genel bakış](autosize-property-overview.md).  
  
### <a name="to-dock-a-control"></a>Bir denetim sabitlemek için  
  
1. Sabitlemek istediğiniz denetimi seçin.  
  
2. Özellikler penceresinde sağındaki oku <xref:System.Windows.Forms.Control.Dock%2A> özelliği.  
  
     Bir düzenleyici gösteren bir dizi kenarları ve form merkezini temsil eden kutu görüntülenir.  
  
3. Edge denetim sabitlemek istediğiniz formun temsil eden düğmeye tıklayın. Denetimin form veya denetim kapsayıcı içeriğini doldurmak için merkezi kutusuna tıklayın. Tıklayın **(hiçbiri)** yerleştirme devre dışı bırakmak için.  
  
     Denetim, yerleşik uç sınırlarına uyacak şekilde otomatik olarak boyutlandırılır.  
  
    > [!NOTE]
    >  Devralınan denetimler olmalıdır `Protected` sabitlenebilir yapabilmek için. Bir denetim erişim düzeyini değiştirmek için Ayarla kendi **değiştiricisi** Özellikler penceresindeki özellik.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Windows Forms Denetimleri](index.md)
- [Windows Forms’da Denetimleri Düzenleme](arranging-controls-on-windows-forms.md)
- [Ayrı Windows Forms Denetimlerini Etiketleme ve Kısayollarını Sunma](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [Windows Forms'da Kullanılacak Denetimler](controls-to-use-on-windows-forms.md)
- [İşleve Göre Windows Forms Denetimleri](windows-forms-controls-by-function.md)
- [Nasıl yapılır: Sabitleme ve FlowLayoutPanel denetiminde alt denetimleri yerleştirme](how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control.md)
- [Nasıl yapılır: Sabitleme ve TableLayoutPanel denetiminde alt denetimleri yerleştirme](how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [AutoSize Özelliğine Genel Bakış](autosize-property-overview.md)
- [Nasıl yapılır: Windows Forms'da denetimleri](how-to-anchor-controls-on-windows-forms.md)
