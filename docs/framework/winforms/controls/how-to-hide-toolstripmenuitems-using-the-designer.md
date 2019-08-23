---
title: 'Nasıl yapılır: Tasarımcıyı Kullanarak ToolStripMenuItems’ı Gizleme'
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStripMenuItems [Windows Forms], hiding menu items in designer
- MenuStrip control [Windows Forms], hiding menu items in designer
- menu items [Windows Forms], hiding
ms.assetid: 8f1b057e-3d8a-4f11-88df-935f7b29a836
ms.openlocfilehash: 0e1cd7d1868adabd4d3eec9510f6ee567ba3867d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966610"
---
# <a name="how-to-hide-toolstripmenuitems-using-the-designer"></a>Nasıl yapılır: Tasarımcıyı Kullanarak ToolStripMenuItems’ı Gizleme
Menü öğelerini gizlemek, uygulamanızın kullanıcı arabirimini (UI) denetlemek ve Kullanıcı komutlarını kısıtlamak için bir yoldur. Genellikle, üzerindeki tüm menü öğeleri kullanılamadığında, tüm menüyü gizlemek isteyeceksiniz. Bu, Kullanıcı için daha az ayırt eden olanaklar sunar. Ayrıca, menüyü veya menü öğesini de gizlemek ve devre dışı bırakmak isteyebilirsiniz, tek başına gizleme, kullanıcının bir kısayol tuşu kullanarak bir menü komutuna erişmesini engellemez. Menü öğelerini devre dışı bırakma hakkında daha fazla bilgi [için bkz. nasıl yapılır: Tasarımcıyı](how-to-disable-toolstripmenuitems-using-the-designer.md)kullanarak ToolStripMenuItems 'ı devre dışı bırakın.

## <a name="to-hide-a-top-level-menu-and-its-submenu-items"></a>Üst düzey menüyü ve alt menü öğelerini gizlemek için

1. Üst düzey menü öğesini seçin ve <xref:System.Windows.Forms.ToolStripItem.Visible%2A> veya <xref:System.Windows.Forms.ToolStripItem.Available%2A> özelliğini olarak `false`ayarlayın.

     Üst düzey menü öğesini gizlediğinizde, bu menüdeki tüm menü öğeleri de gizlenir. ' Den <xref:System.Windows.Forms.MenuStrip> `false`sonra ' i ' den sonra biryeretıkladığınızda,enüstdüzeymenüöğesivealtmenüöğeleriformdankaybolurvebusayedeeyleminiziçinçalışmazamanıetkisinigösterir.<xref:System.Windows.Forms.ToolStripItem.Visible%2A> Gizli üst düzey menü öğesini tasarım zamanında göstermek için **bileşen tepsisinde**, **belge anahattından**veya <xref:System.Windows.Forms.MenuStrip> Özellik kılavuzunun en üstünde bulunan öğesine tıklayın.

> [!NOTE]
> Birleştirme senaryosunda birden çok belge arabirimi (MDI) alt menüleri hariç, tüm menüyü nadiren gizlemeniz gerekir.

## <a name="to-hide-a-submenu-item"></a>Bir alt menü öğesini gizlemek için

1. Alt menü öğesini seçin ve <xref:System.Windows.Forms.ToolStripItem.Visible%2A> özelliğini olarak `false`ayarlayın.

     Bir alt menü öğesini gizlediğinizde, tasarım zamanında formunuzda görünür kalır, böylece daha fazla iş için kolayca seçim yapabilirsiniz. Çalışma zamanında gizli olmayacak.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.ToolStripItem.Visible%2A>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A>
- <xref:System.Windows.Forms.ToolStripItem.Available%2A>
- <xref:System.Windows.Forms.ToolStripMenuItem.Overflow%2A>
- [MenuStrip Denetimine Genel Bakış](menustrip-control-overview-windows-forms.md)
- [Nasıl yapılır: Tasarımcıyı kullanarak ToolStripMenuItems 'ı devre dışı bırakma](how-to-disable-toolstripmenuitems-using-the-designer.md)
