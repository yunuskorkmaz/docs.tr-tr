---
title: SaveFileDialog Bileşenine Genel Bakış
ms.date: 03/30/2017
f1_keywords:
- SaveFileDialog
helpviewer_keywords:
- Save File dialog box [Windows Forms], displaying
- SaveFileDialog component [Windows Forms], about SaveFileDialog
ms.assetid: be7a625f-46fd-4d06-9985-b613dcbf9bd2
ms.openlocfilehash: 7609c29b7e932ecee7dc8a289617094bd8d480e2
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743104"
---
# <a name="savefiledialog-component-overview-windows-forms"></a>SaveFileDialog Bileşenine Genel Bakış (Windows Forms)

Windows Forms <xref:System.Windows.Forms.SaveFileDialog> bileşeni önceden yapılandırılmış bir iletişim kutusudur. Windows tarafından kullanılan standart **Dosya Kaydet** iletişim kutusuyla aynıdır. <xref:System.Windows.Forms.CommonDialog> sınıfından devralır.

## <a name="working-with-the-savefiledialog-component"></a>SaveFileDialog bileşeniyle çalışma

Bu uygulamayı, kullanıcıların kendi iletişim kutusunu yapılandırmak yerine dosyaları kaydetmesine olanak tanımak için basit bir çözüm olarak kullanın. Standart Windows iletişim kutularına bağlı olarak, oluşturduğunuz uygulamaların temel işlevleri kullanıcılara hemen tanıdık gelecektir. Ancak, <xref:System.Windows.Forms.SaveFileDialog> bileşenini kullanırken kendi dosya kaydetme mantığınızı yazmanız gerektiğini unutmayın.

Çalışma zamanında iletişim kutusunu göstermek için <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> yöntemini kullanabilirsiniz. <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> yöntemi kullanarak okuma/yazma modunda bir dosya açabilirsiniz.

Bir forma eklendiğinde <xref:System.Windows.Forms.SaveFileDialog> bileşeni, Visual Studio 'daki Windows Form Tasarımcısı alt kısmındaki tepside görüntülenir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.SaveFileDialog>
- [SaveFileDialog Bileşeni](savefiledialog-component-windows-forms.md)
