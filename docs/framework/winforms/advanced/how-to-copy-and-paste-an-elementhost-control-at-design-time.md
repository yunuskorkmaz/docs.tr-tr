---
title: 'Nasıl yapılır: Tasarım Zamanında bir ElementHost Denetimini Kopyalayıp Yapıştırma'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, content copying and pasting
- interoperability [WPF]
- ElementHost control [Windows Forms], copying and pasting at design time
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: e570375d-2a68-44ba-b4f7-c781af2d20e8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 3d1887eb1161f714962c2c26d6fe618749b26c0f
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73197483"
---
# <a name="how-to-copy-and-paste-an-elementhost-control"></a>Nasıl yapılır: bir ElementHost denetimini kopyalayıp yapıştırma

Bu yordamda, Visual Studio 'da bir Windows formunda Windows Presentation Foundation (WPF) denetiminin nasıl kopyalanacağı gösterilmektedir.

1. Visual Studio 'da, bir Windows Forms projesine yeni bir WPF <xref:System.Windows.Controls.UserControl> ekleyin. Denetim türü için varsayılan adı kullanın, `UserControl1.xaml`. Daha fazla bilgi için bkz. [Izlenecek yol: tasarım zamanında Windows Forms yenı WPF Içeriği oluşturma](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).

2. **Özellikler** penceresinde `UserControl1` <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> özelliklerinin değerini **200**olarak ayarlayın.

3. <xref:System.Windows.Controls.Control.Background%2A> özelliğinin değerini **mavi**olarak ayarlayın.

4. Projeyi oluşturun.

5. Windows Form Tasarımcısı `Form1` açın.

6. **Araç kutusundan**bir `UserControl1` örneğini form üzerine sürükleyin.

   `UserControl1` örneği, `elementHost1`adlı yeni bir <xref:System.Windows.Forms.Integration.ElementHost> denetiminde barındırılır.

7. `elementHost1` seçili olduğunda, panoya kopyalamak için **Ctrl**+**C** tuşlarına basın.

8. Kopyalanmış denetimi forma yapıştırmak için **Ctrl**+**V** tuşlarına basın.

   Form üzerinde `elementHost2` adlı yeni bir <xref:System.Windows.Forms.Integration.ElementHost> denetimi oluşturulur.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Geçiş ve Birlikte Çalışabilirlik](../../wpf/advanced/migration-and-interoperability.md)
- [WPF Denetimlerini Kullanma](using-wpf-controls.md)
- [Visual Studio’da XAML tasarlama](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
