---
title: 'Nasıl yapılır: Denetiminize saydam arka plan verme'
ms.date: 03/30/2017
helpviewer_keywords:
- transparent backgrounds [Windows Forms], custom controls
- custom controls [Windows Forms], transparent background
- transparency [Windows Forms], Windows Forms custom controls
ms.assetid: 32433e63-f4e9-4305-9857-6de3edeb944a
ms.openlocfilehash: 20815518c2a683878e0d3adf6a4bdc9261b614d4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54644619"
---
# <a name="how-to-give-your-control-a-transparent-background"></a>Nasıl yapılır: Denetiminize saydam arka plan verme
Önceki .NET Framework sürümlerinde ilk ayarlamadan saydam backcolors ayarı denetimleri desteklemekteydi <xref:System.Windows.Forms.Control.SetStyle%2A> yöntemi Formlar'ın Oluşturucusu. Geçerli framework sürümü backcolor çoğu denetimleri için ayarlanabilir <xref:System.Drawing.Color.Transparent%2A> içinde **özellikleri** tasarım zamanında ya da formun Oluşturucusu kodunda penceresi.  
  
> [!NOTE]
>  Windows Forms denetimleri gerçek saydamlık desteklemez. Üst öğesi tarafından saydam bir Windows Forms denetiminin arka planı boyanmadan.  
  
> [!NOTE]
>  <xref:System.Windows.Controls.Button> Denetim saydam bir arka plan rengi desteklemiyorsa bile <xref:System.Windows.Forms.ButtonBase.BackColor%2A> özelliği <xref:System.Drawing.Color.Transparent%2A>.  
  
### <a name="to-give-your-control-a-transparent-backcolor"></a>Saydam bir arka plan rengi, denetim sağlamak için  
  
-   Özellikler penceresinde <xref:System.Windows.Forms.ButtonBase.BackColor%2A> özelliği ve ayarlayın <xref:System.Drawing.Color.Transparent%2A>  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Drawing.Color.FromArgb%2A>
- [.NET Framework ile Özel Windows Forms Denetimleri Geliştirme](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)
- [Yönetilen Grafik Sınıflarını Kullanma](../../../../docs/framework/winforms/advanced/using-managed-graphics-classes.md)
- [Nasıl yapılır: Donuk ve yarı saydam çizgiler çizme](../../../../docs/framework/winforms/advanced/how-to-draw-opaque-and-semitransparent-lines.md)
