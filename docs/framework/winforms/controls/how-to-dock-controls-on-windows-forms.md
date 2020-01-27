---
title: Denetimleri Yerleştirme
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], docking
- Explorer-style applications [Windows Forms], creating
- Windows Forms controls, filling client area
ms.assetid: bc11f2e4-e90a-4830-b0e2-f43b6e2b8bec
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 02f1c26dcb322a39c41781c83d8c820bd2fd27e0
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745514"
---
# <a name="how-to-dock-controls-on-windows-forms"></a>Nasıl yapılır: Windows Forms denetimleri yerleştirme

Denetimleri formunuzun kenarlarına yerleştirebilirsiniz veya denetimin kapsayıcısını (form veya kapsayıcı denetimi) doldurmasını sağlayabilirsiniz. Örneğin, Windows Gezgini <xref:System.Windows.Forms.TreeView> denetimini pencerenin sol tarafına ve <xref:System.Windows.Forms.ListView> denetimini pencerenin sağ tarafına kadar denetler. Yerleştirme modunu tanımlamak için tüm görünür Windows Forms denetimleri için <xref:System.Windows.Forms.Control.Dock%2A> özelliğini kullanın.

> [!NOTE]
> Denetimler ters z düzeninde yerleşiktir.

<xref:System.Windows.Forms.Control.Dock%2A> özelliği <xref:System.Windows.Forms.Control.AutoSize%2A> özelliği ile etkileşime girer. Daha fazla bilgi için bkz. [AutoSize özelliğine genel bakış](autosize-property-overview.md).

## <a name="to-dock-a-control"></a>Bir denetimi sabitlemek için

1. Visual Studio 'da, sabitlemek istediğiniz denetimi seçin.

2. **Özellikler** penceresinde <xref:System.Windows.Forms.Control.Dock%2A> özelliğinin sağ tarafındaki oka tıklayın.

   Bir düzenleyici görüntülenir ve bu, formun kenarlarını ve merkezini temsil eden bir kutu dizisini gösterir.

3. Denetimin sabitlemek istediğiniz yerdeki formun kenarını temsil eden düğmeye tıklayın. Denetimin formunun veya kapsayıcı denetiminin içeriğini dolduracak Merkez kutusuna tıklayın. Yerleştirmeyi devre dışı bırakmak için **(yok)** seçeneğine tıklayın.

   Denetim, yerleşik kenarın sınırlarına uyacak şekilde otomatik olarak yeniden boyutlandırılır.

   > [!NOTE]
   > Devralınan denetimlerin sabitlenebilir olması için `Protected` olması gerekir. Bir denetimin erişim düzeyini değiştirmek için, **Özellikler** penceresinde **değiştirici** özelliğini ayarlayın.

## <a name="see-also"></a>Ayrıca bkz.

- [Windows Forms Denetimleri](index.md)
- [Ayrı Windows Forms Denetimlerini Etiketleme ve Kısayollarını Sunma](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [Windows Forms'da Kullanılacak Denetimler](controls-to-use-on-windows-forms.md)
- [İşleve Göre Windows Forms Denetimleri](windows-forms-controls-by-function.md)
- [Nasıl yapılır: FlowLayoutPanel Denetiminde Alt Denetimleri Sabitleme ve Yerleştirme](how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control.md)
- [Nasıl yapılır: TableLayoutPanel Denetiminde Alt Denetimleri Sabitleme ve Yerleştirme](how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [AutoSize Özelliğine Genel Bakış](autosize-property-overview.md)
- [Nasıl yapılır: Windows Forms’da Denetimleri Bağlama](how-to-anchor-controls-on-windows-forms.md)
