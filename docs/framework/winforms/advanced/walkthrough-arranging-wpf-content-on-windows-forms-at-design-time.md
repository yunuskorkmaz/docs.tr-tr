---
title: Tasarım zamanında Windows Forms WPF içeriğini düzenleme
titleSuffix: ''
ms.date: 03/30/2017
helpviewer_keywords:
- WPF user control [Windows Forms], hosting in a layout panel
- WPF content [Windows Forms], arranging at design time
- Windows Forms, arranging WPF content at design time
- WPF content [Windows Forms], hosting in Windows Forms
- Windows Forms, anchoring and docking WPF content
- interoperability [WPF]
ms.assetid: 5efb1c53-1484-43d6-aa8a-f4861b99bb8a
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5a6b12def45052e117fb149555946ea42d6cd3c2
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746823"
---
# <a name="walkthrough-arrange-wpf-content-on-windows-forms-at-design-time"></a>İzlenecek yol: tasarım zamanında Windows Forms WPF içeriğini düzenleme

Bu makalede, Windows Presentation Foundation (WPF) denetimlerini düzenlemek için bağlama ve yama çizgileri gibi Windows Forms düzen özelliklerinin nasıl kullanılacağı gösterilmektedir.

## <a name="prerequisites"></a>Prerequisites

Bu yönergeyi tamamlamak için Visual Studio gerekir.

## <a name="create-the-project"></a>Projeyi oluşturma

Visual Studio 'Yu açın ve Visual Basic veya görsel C# adlı `ArrangeElementHost`Windows Forms uygulama projesi oluşturun.

> [!NOTE]
> WPF içeriği barındırırken yalnızca C# ve Visual Basic projeleri desteklenir.

## <a name="create-the-wpf-control"></a>WPF denetimini oluşturma

Projeye bir WPF denetimi ekledikten sonra bunu form üzerinde düzenleyebilirsiniz.

1. Projeye yeni bir WPF <xref:System.Windows.Controls.UserControl> ekleyin. Denetim türü için varsayılan adı kullanın, `UserControl1.xaml`. Daha fazla bilgi için bkz. [Izlenecek yol: tasarım zamanında Windows Forms yenı WPF Içeriği oluşturma](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).

2. Tasarım görünümü ' de `UserControl1` ' nin seçili olduğundan emin olun.

3. **Özellikler** penceresinde <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> özelliklerinin değerini **200**olarak ayarlayın.

4. <xref:System.Windows.Controls.Control.Background%2A> özelliğinin değerini **mavi**olarak ayarlayın.

5. Projeyi oluşturun.

## <a name="host-wpf-controls-in-a-layout-panel"></a>Düzen panelinde WPF denetimleri barındırma

Düzen panellerinde WPF denetimlerini, diğer Windows Forms denetimlerini kullandığınız şekilde kullanabilirsiniz.

1. Windows Form Tasarımcısı `Form1` açın.

2. **Araç kutusunda**bir <xref:System.Windows.Forms.TableLayoutPanel> denetimini form üzerine sürükleyin.

3. <xref:System.Windows.Forms.TableLayoutPanel> denetimin akıllı etiket panelinde **son satırı Kaldır**' ı seçin.

4. <xref:System.Windows.Forms.TableLayoutPanel> denetimini daha büyük bir genişlik ve yükseklik olarak yeniden boyutlandırın.

5. **Araç kutusunda**, <xref:System.Windows.Forms.TableLayoutPanel> denetiminin ilk hücresinde bir `UserControl1` örneği oluşturmak için `UserControl1` ' a çift tıklayın.

   `UserControl1` örneği, `elementHost1`adlı yeni bir <xref:System.Windows.Forms.Integration.ElementHost> denetiminde barındırılır.

6. **Araç kutusunda**, <xref:System.Windows.Forms.TableLayoutPanel> denetiminin ikinci hücresinde başka bir örnek oluşturmak için `UserControl1` ' a çift tıklayın.

7. **Belge Anahattı** penceresinde `tableLayoutPanel1`' yi seçin.

8. **Özellikler** penceresinde, <xref:System.Windows.Forms.Control.Padding%2A> özelliğinin değerini **10, 10, 10, 10**olarak ayarlayın.

   <xref:System.Windows.Forms.Integration.ElementHost> denetimlerinin her ikisi de yeni düzene sığacak şekilde yeniden boyutlandırılır.

## <a name="use-snaplines-to-align-wpf-controls"></a>WPF denetimlerini hizalamak için dayama çizgileri kullanma

Anlık görüntü çizgileri, bir formdaki denetimlerin kolay hizalamasını etkinleştirir. WPF denetimlerinizi de hizalamak için Snapın çizgilerini kullanabilirsiniz. Daha fazla bilgi için bkz. [Izlenecek yol: Windows Forms denetimleri yerleştirme, yama çizgileri kullanarak](../controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).

1. **Araç kutusundan**bir `UserControl1` örneğini form üzerine sürükleyin ve <xref:System.Windows.Forms.TableLayoutPanel> denetiminin altındaki alana yerleştirin.

   `UserControl1` örneği, `elementHost3`adlı yeni bir <xref:System.Windows.Forms.Integration.ElementHost> denetiminde barındırılır.

2. Anlık görüntü çizgilerini kullanarak `elementHost3` sol kenarını <xref:System.Windows.Forms.TableLayoutPanel> denetiminin sol kenarıyla hizalayın.

3. Snaplines, boyut `elementHost3` <xref:System.Windows.Forms.TableLayoutPanel> denetimiyle aynı genişliğe sahip olacak şekilde kullanma.

4. Denetimler arasında bir merkez ek çizgi görünene kadar `elementHost3` <xref:System.Windows.Forms.TableLayoutPanel> denetimine doğru taşıyın.

5. **Özellikler** penceresinde, Margin özelliğinin değerini **20, 20, 20, 20**olarak ayarlayın.

6. Center Snapın satırı yeniden görünene kadar `elementHost3` <xref:System.Windows.Forms.TableLayoutPanel> denetiminden uzağa taşıyın. Center Snapın çizgisi artık 20 ' nin bir kenar boşluğunu gösterir.

7. Sol kenarı `elementHost1`sol kenarıyla hizalanana kadar `elementHost3` sağa taşıyın.

8. Sağ kenarı `elementHost2`sağ kenarıyla hizalanana kadar `elementHost3` genişliğini değiştirin.

## <a name="anchor-and-dock-wpf-controls"></a>WPF denetimlerini sabitleme ve yerleştirme

Bir form üzerinde barındırılan WPF denetimi, diğer Windows Forms denetimleriyle aynı sabitleme ve yerleştirme davranışına sahiptir.

1. `elementHost1` öğesini seçin.

2. **Özellikler** penceresinde, <xref:System.Windows.Forms.Control.Anchor%2A> özelliğini **üst, alt, sol, sağ**olarak ayarlayın.

3. <xref:System.Windows.Forms.TableLayoutPanel> denetimini daha büyük bir boyutla yeniden boyutlandırın.

   `elementHost1` denetim hücreyi dolduracak şekilde yeniden boyutlandırır.

4. `elementHost2` öğesini seçin.

5. **Özellikler** penceresinde <xref:System.Windows.Forms.Control.Dock%2A> özelliğinin değerini <xref:System.Windows.Forms.DockStyle.Fill>olarak ayarlayın.

   `elementHost2` denetim hücreyi dolduracak şekilde yeniden boyutlandırır.

6. <xref:System.Windows.Forms.TableLayoutPanel> denetimini seçin.

7. <xref:System.Windows.Forms.Control.Dock%2A> özelliğinin değerini <xref:System.Windows.Forms.DockStyle.Top>olarak ayarlayın.

8. `elementHost3` öğesini seçin.

9. <xref:System.Windows.Forms.Control.Dock%2A> özelliğinin değerini <xref:System.Windows.Forms.DockStyle.Fill>olarak ayarlayın.

   `elementHost3` denetim, formdaki kalan alanı dolduracak şekilde yeniden boyutlandırır.

10. Formu yeniden boyutlandırın.

    Her üç <xref:System.Windows.Forms.Integration.ElementHost> denetimi uygun şekilde yeniden boyutlandırılır.

    Daha fazla bilgi için bkz. [nasıl yapılır: bir TableLayoutPanel denetiminde alt denetimleri sabitleme ve yerleştirme](../controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md).

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Nasıl yapılır: TableLayoutPanel Denetiminde Alt Denetimleri Sabitleme ve Yerleştirme](../controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [Nasıl yapılır: Tasarım Zamanında Denetimi Formların Kenarlarına Hizalama](../controls/how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)
- [İzlenecek yol: Dayama Çizgileri Kullanarak Windows Forms'da Denetimleri Düzenleme](../controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
- [Geçiş ve Birlikte Çalışabilirlik](../../wpf/advanced/migration-and-interoperability.md)
- [WPF Denetimlerini Kullanma](using-wpf-controls.md)
- [Visual Studio’da XAML tasarlama](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
