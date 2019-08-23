---
title: 'Nasıl yapılır: Denetiminize Saydam Arka Plan Verme'
ms.date: 03/30/2017
helpviewer_keywords:
- transparent backgrounds [Windows Forms], custom controls
- custom controls [Windows Forms], transparent background
- transparency [Windows Forms], Windows Forms custom controls
ms.assetid: 32433e63-f4e9-4305-9857-6de3edeb944a
ms.openlocfilehash: a82807ea3873b2217d1f05f6c720c599ea79abdd
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966646"
---
# <a name="how-to-give-your-control-a-transparent-background"></a>Nasıl yapılır: Denetiminize Saydam Arka Plan Verme
.NET Framework önceki sürümlerinde denetimler, önce formların oluşturucusunda <xref:System.Windows.Forms.Control.SetStyle%2A> yöntemi ayarlamadan saydam geri renklerin ayarlanmasını desteklemezler. Geçerli Framework sürümünde, çoğu denetim için BackColor, tasarım zamanında **Özellikler** penceresinde veya formun <xref:System.Drawing.Color.Transparent%2A> oluşturucusunda kodda olarak ayarlanabilir.  
  
> [!NOTE]
> Windows Forms denetimleri gerçek saydamlığı desteklemez. Saydam Windows Forms denetiminin arka planı üst öğesi tarafından boyanmıştır.  
  
> [!NOTE]
> Denetim, <xref:System.Windows.Forms.ButtonBase.BackColor%2A> özelliği olarak<xref:System.Drawing.Color.Transparent%2A>ayarlanmış olsa bile saydam BackColor 'ı desteklemez. <xref:System.Windows.Controls.Button>  
  
### <a name="to-give-your-control-a-transparent-backcolor"></a>Denetimine saydam bir BackColor sağlamak için  
  
- Özellikler penceresi, <xref:System.Windows.Forms.ButtonBase.BackColor%2A> özelliğini seçin ve<xref:System.Drawing.Color.Transparent%2A>  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Drawing.Color.FromArgb%2A>
- [.NET Framework ile Özel Windows Forms Denetimleri Geliştirme](developing-custom-windows-forms-controls.md)
- [Yönetilen Grafik Sınıflarını Kullanma](../advanced/using-managed-graphics-classes.md)
- [Nasıl yapılır: Donuk ve yarı saydam çizgiler çizme](../advanced/how-to-draw-opaque-and-semitransparent-lines.md)
