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
ms.workload: dotnet
ms.openlocfilehash: ab2a8562401561cfb2a54d4630e32bf7527da10d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
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
 [.NET Framework ile Özel Windows Forms Denetimleri Geliştirme](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)  
 [Yönetilen Grafik Sınıflarını Kullanma](../../../../docs/framework/winforms/advanced/using-managed-graphics-classes.md)  
 [Nasıl yapılır: Donuk ve Yarı Saydam Çizgiler Çizme](../../../../docs/framework/winforms/advanced/how-to-draw-opaque-and-semitransparent-lines.md)
