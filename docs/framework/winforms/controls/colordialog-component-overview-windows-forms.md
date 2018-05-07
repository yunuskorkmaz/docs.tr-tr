---
title: ColorDialog Bileşenine Genel Bakış (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- ColorDialog
helpviewer_keywords:
- color dialog box [Windows Forms], about color dialog box
- ColorDialog component [Windows Forms], about ColorDialog
ms.assetid: 6dbdd8f0-f697-4728-bb09-7ea156f6d800
ms.openlocfilehash: 9b4fb545a2ed35a9c7bad5e28c28d3ec42870860
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="colordialog-component-overview-windows-forms"></a>ColorDialog Bileşenine Genel Bakış (Windows Forms)
Windows Forms <xref:System.Windows.Forms.ColorDialog> bir paletinden bir renk seçin ve bu paleti özel renkler eklemek için kullanıcı sağlayan bir önceden yapılandırılmış iletişim kutusu bir bileşendir. Diğer gördüğünüz aynı iletişim kutusu olan Windows tabanlı uygulamalar renklerini seçin. Kendi iletişim kutusu yapılandırma yerine basit bir çözüm olarak, Windows tabanlı uygulamanızda kullanın.  
  
 İletişim kutusunda seçili renk döndürülür <xref:System.Windows.Forms.ColorDialog.Color%2A> özelliği. Varsa <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A> özelliği ayarlanmış `false`, "Özel renk tanımla" düğmesi devre dışı bırakılır ve kullanıcı önceden tanımlanmış renk paletindeki sınırlıdır. Varsa <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A> özelliği ayarlanmış `true`, kullanıcı Titremeli renk seçemezsiniz. İletişim kutusunu görüntülemek için çağırmalısınız kendi <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> yöntemi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.ColorDialog>  
 [ColorDialog Bileşeni](../../../../docs/framework/winforms/controls/colordialog-component-windows-forms.md)  
 [İletişim Kutusu Denetimleri ve Bileşenleri](../../../../docs/framework/winforms/controls/dialog-box-controls-and-components-windows-forms.md)  
 [Nasıl yapılır: Windows Forms ColorDialog Bileşeninin Görünüşünü Değiştirme](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-colordialog-component.md)
