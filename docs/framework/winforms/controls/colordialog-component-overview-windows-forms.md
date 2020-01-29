---
title: ColorDialog Bileşenine Genel Bakış
ms.date: 03/30/2017
f1_keywords:
- ColorDialog
helpviewer_keywords:
- color dialog box [Windows Forms], about color dialog box
- ColorDialog component [Windows Forms], about ColorDialog
ms.assetid: 6dbdd8f0-f697-4728-bb09-7ea156f6d800
ms.openlocfilehash: 48d9d5072335908f85e65933dadafb1b69f28528
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736969"
---
# <a name="colordialog-component-overview-windows-forms"></a>ColorDialog Bileşenine Genel Bakış (Windows Forms)
Windows Forms <xref:System.Windows.Forms.ColorDialog> bileşeni, kullanıcının bir paletten renk seçmesini ve bu palete özel renkler eklemesini sağlayan önceden yapılandırılmış bir iletişim kutusudur. Renk seçmek için diğer Windows tabanlı uygulamalarda gördüğünüz iletişim kutusudur. Kendi iletişim kutusunu yapılandırmak yerine, bunu Windows tabanlı uygulamanızda basit bir çözüm olarak kullanın.  
  
 İletişim kutusunda seçilen renk <xref:System.Windows.Forms.ColorDialog.Color%2A> özelliğinde döndürülür. <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A> özelliği `false`olarak ayarlanırsa, "özel renkleri tanımla" düğmesi devre dışıdır ve Kullanıcı paletteki önceden tanımlanmış renklerle kısıtlıdır. <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A> özelliği `true`olarak ayarlanırsa, Kullanıcı titremeli renklerini seçemezsiniz. İletişim kutusunu göstermek için <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> yöntemini çağırmanız gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.ColorDialog>
- [ColorDialog Bileşeni](colordialog-component-windows-forms.md)
- [İletişim Kutusu Denetimleri ve Bileşenleri](dialog-box-controls-and-components-windows-forms.md)
- [Nasıl yapılır: Windows Forms ColorDialog Bileşeninin Görünüşünü Değiştirme](how-to-change-the-appearance-of-the-windows-forms-colordialog-component.md)
