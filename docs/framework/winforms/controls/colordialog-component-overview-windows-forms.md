---
title: ColorDialog Bileşenine Genel Bakış (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- ColorDialog
helpviewer_keywords:
- color dialog box [Windows Forms], about color dialog box
- ColorDialog component [Windows Forms], about ColorDialog
ms.assetid: 6dbdd8f0-f697-4728-bb09-7ea156f6d800
ms.openlocfilehash: 7dd48c8df0a36262962df596e8efadf4de1c2cd3
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57713338"
---
# <a name="colordialog-component-overview-windows-forms"></a>ColorDialog Bileşenine Genel Bakış (Windows Forms)
Windows Forms <xref:System.Windows.Forms.ColorDialog> bir paletinden bir renk seçin ve özel renkler paleti bu eklemek için kullanıcıya izin veren bir önceden yapılandırılmış bir iletişim kutusu bir bileşendir. Diğer gördüğünüz aynı iletişim kutusu olan Windows tabanlı uygulamaların renklerini seçin. Windows tabanlı uygulamanızda kendi iletişim kutusu yapılandırma yerine basit bir çözüm olarak kullanın.  
  
 İletişim kutusunda seçilen renk döndürülür <xref:System.Windows.Forms.ColorDialog.Color%2A> özelliği. Varsa <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A> özelliği `false`, "Özel renkler tanımlama" düğmesini devre dışı bırakıldı ve kullanıcının önceden tanımlanmış palet renkleri sınırlıdır. Varsa <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A> özelliği `true`, kullanıcı Titremeli renk seçemezsiniz. İletişim kutusunu görüntülemek için çağırmalıdır kendi <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> yöntemi.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Forms.ColorDialog>
- [ColorDialog Bileşeni](colordialog-component-windows-forms.md)
- [İletişim Kutusu Denetimleri ve Bileşenleri](dialog-box-controls-and-components-windows-forms.md)
- [Nasıl yapılır: Windows Forms ColorDialog bileşeninin görünüşünü değiştirme](how-to-change-the-appearance-of-the-windows-forms-colordialog-component.md)
