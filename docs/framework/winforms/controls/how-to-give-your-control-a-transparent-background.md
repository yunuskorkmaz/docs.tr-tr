---
title: "Nasıl yapılır: Denetiminize Saydam Arka Plan Verme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- transparent backgrounds [Windows Forms], custom controls
- custom controls [Windows Forms], transparent background
- transparency [Windows Forms], Windows Forms custom controls
ms.assetid: 32433e63-f4e9-4305-9857-6de3edeb944a
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a5ec2c353a960626c54c05009393bcd80dac1b38
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-give-your-control-a-transparent-background"></a>Nasıl yapılır: Denetiminize Saydam Arka Plan Verme
Önceki sürümlerde .NET Framework'ün, ilk ayarlamadan saydam backcolors ayarlama denetimleri desteklemekteydi <xref:System.Windows.Forms.Control.SetStyle%2A> formları 's Oluşturucusu yöntemi. Geçerli framework sürümünde çoğu denetimleri için backcolor ayarlanabilir <xref:System.Drawing.Color.Transparent%2A> içinde **özellikleri** penceresi tasarım zamanında ya da formun oluşturucuda kod.  
  
> [!NOTE]
>  Windows Forms denetimleri true saydamlığı desteklemez. Arka plan saydam bir Windows Forms denetiminin üst tarafından boyanır.  
  
> [!NOTE]
>  <xref:System.Windows.Controls.Button> Denetim saydam backcolor desteklemiyor bile <xref:System.Windows.Forms.ButtonBase.BackColor%2A> özelliği ayarlanmış <xref:System.Drawing.Color.Transparent%2A>.  
  
### <a name="to-give-your-control-a-transparent-backcolor"></a>Saydam arka plan rengi, denetim sağlamak için  
  
-   Özellikler penceresinde seçin <xref:System.Windows.Forms.ButtonBase.BackColor%2A> özelliği ve ayarlayın<xref:System.Drawing.Color.Transparent%2A>  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Drawing.Color.FromArgb%2A>  
 [Özel Windows Forms denetimleri .NET Framework ile geliştirme](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)  
 [Yönetilen grafik sınıflarını kullanma](../../../../docs/framework/winforms/advanced/using-managed-graphics-classes.md)  
 [Nasıl yapılır: donuk ve yarı saydam çizgiler çizme](../../../../docs/framework/winforms/advanced/how-to-draw-opaque-and-semitransparent-lines.md)
