---
title: OpenFileDialog Bileşenine Genel Bakış
ms.date: 03/30/2017
f1_keywords:
- OpenFileDialog
helpviewer_keywords:
- OpenFileDialog component [Windows Forms], about OpenFileDialog
- Open File dialog box [Windows Forms], displaying in Windows Forms
ms.assetid: cd717300-46b6-4f82-8207-b218fa7fa407
ms.openlocfilehash: c519b373150a49ee41dbb0c503f7d5a4862477d5
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728442"
---
# <a name="openfiledialog-component-overview-windows-forms"></a>OpenFileDialog Bileşenine Genel Bakış (Windows Forms)

Windows Forms <xref:System.Windows.Forms.OpenFileDialog> bileşeni önceden yapılandırılmış bir iletişim kutusudur. Windows işletim sistemi tarafından kullanıma sunulan aynı **Açık dosya** iletişim kutusudur. <xref:System.Windows.Forms.CommonDialog> sınıfından devralır.

## <a name="use-this-component"></a>Bu bileşeni kullan

Bu bileşeni, kendi iletişim kutusunu yapılandırmak yerine, dosya seçimi için basit bir çözüm olarak Windows tabanlı uygulamanızda kullanın. Standart Windows iletişim kutularına bağlı olarak, temel işlevselliği kullanıcılara hemen tanıdık olan uygulamalar oluşturursunuz. Ancak <xref:System.Windows.Forms.OpenFileDialog> bileşeni kullanılırken kendi dosya açma mantığınızı yazmanız gerektiğini unutmayın.

Çalışma zamanında iletişim kutusunu göstermek için <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> yöntemini kullanın. Kullanıcıların <xref:System.Windows.Forms.OpenFileDialog.Multiselect%2A> özelliği ile açılacak birden çok seçim dosyaları sağlayabilirsiniz. Ayrıca, iletişim kutusunda salt okuma onay kutusunun görünüp göründüğünü anlamak için <xref:System.Windows.Forms.OpenFileDialog.ShowReadOnly%2A> özelliğini kullanabilirsiniz. <xref:System.Windows.Forms.OpenFileDialog.ReadOnlyChecked%2A> özelliği salt okunurdur onay kutusunun seçili olup olmadığını gösterir. Son olarak, <xref:System.Windows.Forms.FileDialog.Filter%2A> özelliği, iletişim kutusundaki "tür dosyaları" kutusunda görünen seçimleri belirleyen geçerli dosya adı filtre dizesini ayarlar.

Bir forma eklendiğinde <xref:System.Windows.Forms.OpenFileDialog> bileşeni, Visual Studio 'daki Windows Form Tasarımcısı alt kısmındaki tepside görüntülenir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.OpenFileDialog>
- [OpenFileDialog Bileşeni](openfiledialog-component-windows-forms.md)
