---
title: OpenFileDialog Bileşenine Genel Bakış (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- OpenFileDialog
helpviewer_keywords:
- OpenFileDialog component [Windows Forms], about OpenFileDialog
- Open File dialog box [Windows Forms], displaying in Windows Forms
ms.assetid: cd717300-46b6-4f82-8207-b218fa7fa407
ms.openlocfilehash: ad2fea74f0f3110ab2868064c588a7611d4261e3
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57702912"
---
# <a name="openfiledialog-component-overview-windows-forms"></a>OpenFileDialog Bileşenine Genel Bakış (Windows Forms)
Windows Forms <xref:System.Windows.Forms.OpenFileDialog> bir önceden yapılandırılmış bir iletişim kutusu bir bileşendir. Aynı olan **açık dosya** Windows işletim sistemi tarafından kullanıma sunulan iletişim kutusu. Devraldığı <xref:System.Windows.Forms.CommonDialog> sınıfı.  
  
## <a name="using-this-component"></a>Bu bileşeni kullanma  
 Bu bileşen, Windows tabanlı bir uygulama içinde kendi iletişim kutusu yapılandırma yerine dosya seçimi için basit bir çözüm kullanın. Standart Windows iletişim kutularında bağlı olarak, temel işlevleri kullanıcılarına hemen tanıdık uygulamalar oluşturun. Ancak, unutmayın olduğunda kullanarak <xref:System.Windows.Forms.OpenFileDialog> bileşeni, kendi dosya açma mantığı yazmalıdır.  
  
 Kullanım <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> çalışma zamanında iletişim kutusunu görüntülemek için yöntemi. Çoklu seçim ile açılmasını dosyaya kullanıcılara etkinleştirebilirsiniz <xref:System.Windows.Forms.OpenFileDialog.Multiselect%2A> özelliği. Ayrıca, kullanabileceğiniz <xref:System.Windows.Forms.OpenFileDialog.ShowReadOnly%2A> özelliği salt okunur bir onay kutusu iletişim kutusunda görünüp görünmeyeceğini belirler. <xref:System.Windows.Forms.OpenFileDialog.ReadOnlyChecked%2A> Özelliği salt okunur onay kutusunun seçili olup olmadığını gösterir. Son olarak, <xref:System.Windows.Forms.FileDialog.Filter%2A> özelliğini ayarlar iletişim kutusundaki "Dosya türü" görünen seçenekler belirleyen geçerli dosya adı filtre dizesi,.  
  
 Bir forma eklendiğinde <xref:System.Windows.Forms.OpenFileDialog> bileşeni Tepsi Windows Form Tasarımcısı'nın altındaki görünür.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Forms.OpenFileDialog>
- [OpenFileDialog Bileşeni](openfiledialog-component-windows-forms.md)
