---
title: SaveFileDialog Bileşenine Genel Bakış (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- SaveFileDialog
helpviewer_keywords:
- Save File dialog box [Windows Forms], displaying
- SaveFileDialog component [Windows Forms], about SaveFileDialog
ms.assetid: be7a625f-46fd-4d06-9985-b613dcbf9bd2
ms.openlocfilehash: ab8eb5409d017c6ea73a44e4e57ccec9cece4824
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54631067"
---
# <a name="savefiledialog-component-overview-windows-forms"></a>SaveFileDialog Bileşenine Genel Bakış (Windows Forms)
Windows Forms <xref:System.Windows.Forms.SaveFileDialog> bir önceden yapılandırılmış bir iletişim kutusu bir bileşendir. Standart ile aynı olduğu **dosyayı Kaydet** Windows tarafından kullanılan iletişim kutusu. Devraldığı <xref:System.Windows.Forms.CommonDialog> sınıfı.  
  
## <a name="working-with-the-savefiledialog-component"></a>SaveFileDialog bileşeni ile çalışma  
 Basit bir çözüm, kullanıcıların kendi iletişim kutusu yapılandırmak yerine dosyaları kaydetmeyi etkinleştirmek için kullanın. Standart Windows iletişim kutularında bağlı olan temel işlevleri oluşturduğunuz uygulamaların kullanıcılarına hemen tanıdık gelir. Ancak, unutmayın olduğunda kullanarak <xref:System.Windows.Forms.SaveFileDialog> bileşeni, kendi dosya kaydetme mantıksal yazmalıdır.  
  
 Kullanabileceğiniz <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> çalışma zamanında iletişim kutusunu görüntülemek için yöntemi. Okuma/yazma modu kullanarak bir dosyayı açabilirsiniz <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> yöntemi.  
  
 Bir forma eklendiğinde <xref:System.Windows.Forms.SaveFileDialog> bileşeni Tepsi Windows Form Tasarımcısı'nın altındaki görünür.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Forms.SaveFileDialog>
- [SaveFileDialog Bileşeni](../../../../docs/framework/winforms/controls/savefiledialog-component-windows-forms.md)
