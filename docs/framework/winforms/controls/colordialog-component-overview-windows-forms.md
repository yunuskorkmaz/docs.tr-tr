---
title: "ColorDialog Bileşenine Genel Bakış (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: ColorDialog
helpviewer_keywords:
- color dialog box [Windows Forms], about color dialog box
- ColorDialog component [Windows Forms], about ColorDialog
ms.assetid: 6dbdd8f0-f697-4728-bb09-7ea156f6d800
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5df0d7ddd16de5bd8bb052c09731df6583ca4903
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="colordialog-component-overview-windows-forms"></a>ColorDialog Bileşenine Genel Bakış (Windows Forms)
Windows Forms <xref:System.Windows.Forms.ColorDialog> bir paletinden bir renk seçin ve bu paleti özel renkler eklemek için kullanıcı sağlayan bir önceden yapılandırılmış iletişim kutusu bir bileşendir. Diğer gördüğünüz aynı iletişim kutusu olan Windows tabanlı uygulamalar renklerini seçin. Kendi iletişim kutusu yapılandırma yerine basit bir çözüm olarak, Windows tabanlı uygulamanızda kullanın.  
  
 İletişim kutusunda seçili renk döndürülür <xref:System.Windows.Forms.ColorDialog.Color%2A> özelliği. Varsa <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A> özelliği ayarlanmış `false`, "Özel renk tanımla" düğmesi devre dışı bırakılır ve kullanıcı önceden tanımlanmış renk paletindeki sınırlıdır. Varsa <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A> özelliği ayarlanmış `true`, kullanıcı Titremeli renk seçemezsiniz. İletişim kutusunu görüntülemek için çağırmalısınız kendi <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> yöntemi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.ColorDialog>  
 [ColorDialog Bileşeni](../../../../docs/framework/winforms/controls/colordialog-component-windows-forms.md)  
 [İletişim Kutusu Denetimleri ve Bileşenleri](../../../../docs/framework/winforms/controls/dialog-box-controls-and-components-windows-forms.md)  
 [Nasıl yapılır: Windows Forms ColorDialog Bileşeninin Görünüşünü Değiştirme](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-colordialog-component.md)
