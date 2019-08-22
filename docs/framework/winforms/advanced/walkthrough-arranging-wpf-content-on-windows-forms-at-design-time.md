---
title: "İzlenecek yol: Windows Forms'da Tasarım Zamanında WPF İçeriğini Düzenleme"
ms.date: 03/30/2017
helpviewer_keywords:
- WPF user control [Windows Forms], hosting in a layout panel
- WPF content [Windows Forms], arranging at design time
- Windows Forms, arranging WPF content at design time
- WPF content [Windows Forms], hosting in Windows Forms
- Windows Forms, anchoring and docking WPF content
- interoperability [WPF]
ms.assetid: 5efb1c53-1484-43d6-aa8a-f4861b99bb8a
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 7858ffd708c78d6397d533f613ccc2ea78d6cbed
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69658517"
---
# <a name="walkthrough-arrange-wpf-content-on-windows-forms-at-design-time"></a>İzlenecek yol: Tasarım zamanında Windows Forms WPF içeriğini düzenleme

Bu makalede, Windows Presentation Foundation (WPF) denetimlerini düzenlemek için bağlama ve yama çizgileri gibi Windows Forms düzen özelliklerinin nasıl kullanılacağı gösterilmektedir.

## <a name="prerequisites"></a>Önkoşullar

Bu yönergeyi tamamlamak için Visual Studio gerekir.

## <a name="create-the-project"></a>Projeyi oluşturma

Visual Studio 'Yu açın ve Visual Basic veya görsel C# adlı `ArrangeElementHost`yeni bir Windows Forms uygulama projesi oluşturun.

> [!NOTE]
> WPF içeriği barındırırken yalnızca C# ve Visual Basic projeleri desteklenir.

## <a name="create-the-wpf-control"></a>WPF denetimini oluşturma

Projeye bir WPF denetimi ekledikten sonra bunu form üzerinde düzenleyebilirsiniz.

1. Projeye yeni bir WPF <xref:System.Windows.Controls.UserControl> ekleyin. Denetim türü için varsayılan adı kullanın, `UserControl1.xaml`. Daha fazla bilgi için bkz [. İzlenecek yol: Tasarım zamanında](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md)Windows Forms yeni WPF içeriği oluşturuluyor.

2. Tasarım görünümü ' de, ' `UserControl1` nin seçili olduğundan emin olun.

3. **Özellikler** penceresinde, <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> özelliklerinin değerini **200**olarak ayarlayın.

4. <xref:System.Windows.Controls.Control.Background%2A> Özelliğin değerini **mavi**olarak ayarlayın.

5. Projeyi oluşturun.

## <a name="host-wpf-controls-in-a-layout-panel"></a>Düzen panelinde WPF denetimleri barındırma

Düzen panellerinde WPF denetimlerini, diğer Windows Forms denetimlerini kullandığınız şekilde kullanabilirsiniz.

1. Windows Form Tasarımcısı `Form1` açın.

2. **Araç kutusunda**form üzerine bir <xref:System.Windows.Forms.TableLayoutPanel> denetim sürükleyin.

3. Denetimin akıllı etiket panelinde **son satırı Kaldır**' ı seçin. <xref:System.Windows.Forms.TableLayoutPanel>

4. <xref:System.Windows.Forms.TableLayoutPanel> Denetimi daha büyük bir genişlik ve yüksekliğe yeniden boyutlandırın.

5. **Araç kutusunda**, <xref:System.Windows.Forms.TableLayoutPanel> denetimin ilk hücresinde bir `UserControl1` örneği `UserControl1` oluşturmak için çift tıklayın.

   Örneği `UserControl1` <xref:System.Windows.Forms.Integration.ElementHost> adlı Yeni`elementHost1`bir denetimde barındırılır.

6. **Araç kutusunda**, <xref:System.Windows.Forms.TableLayoutPanel> denetimin ikinci hücresinde başka `UserControl1` bir örnek oluşturmak için çift tıklayın.

7. **Belge Anahattı** penceresinde, öğesini seçin `tableLayoutPanel1`.

8. **Özellikler** penceresinde, <xref:System.Windows.Forms.Control.Padding%2A> özelliğinin değerini **10, 10, 10, 10**olarak ayarlayın.

   Her <xref:System.Windows.Forms.Integration.ElementHost> iki denetim de yeni düzene sığacak şekilde yeniden boyutlandırılır.

## <a name="use-snaplines-to-align-wpf-controls"></a>WPF denetimlerini hizalamak için dayama çizgileri kullanma

Anlık görüntü çizgileri, bir formdaki denetimlerin kolay hizalamasını etkinleştirir. WPF denetimlerinizi de hizalamak için Snapın çizgilerini kullanabilirsiniz. Daha fazla bilgi için bkz [. İzlenecek yol: Windows Forms denetimleri, snaplines](../controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)kullanarak düzenleme.

1. **Araç kutusundan**form `UserControl1` üzerine bir örneğini sürükleyin ve <xref:System.Windows.Forms.TableLayoutPanel> denetimin altındaki alana yerleştirin.

   Örneği `UserControl1` <xref:System.Windows.Forms.Integration.ElementHost> adlı Yeni`elementHost3`bir denetimde barındırılır.

2. Snaplines kullanarak sol kenarını `elementHost3` <xref:System.Windows.Forms.TableLayoutPanel> denetimin sol kenarıyla hizalayın.

3. Anlık görüntü çizgilerini kullanarak, `elementHost3` <xref:System.Windows.Forms.TableLayoutPanel> denetim ile aynı genişliğe göre boyut.

4. Denetimler `elementHost3` arasında bir <xref:System.Windows.Forms.TableLayoutPanel> Merkez ek çizgi görünene kadar denetime doğru ilerleyin.

5. **Özellikler** penceresinde, Margin özelliğinin değerini **20, 20, 20, 20**olarak ayarlayın.

6. Center Snapın satırı yeniden <xref:System.Windows.Forms.TableLayoutPanel> görünene kadar denetimden uzağataşıyın.`elementHost3` Center Snapın çizgisi artık 20 ' nin bir kenar boşluğunu gösterir.

7. Sol `elementHost3` kenarı sol `elementHost1`kenarı ile hizalanana kadar sağa taşı.

8. Sağ kenarı sağ `elementHost2`kenarıyla `elementHost3` hizalanana kadar genişliğini değiştirin.

## <a name="anchor-and-dock-wpf-controls"></a>WPF denetimlerini sabitleme ve yerleştirme

Bir form üzerinde barındırılan WPF denetimi, diğer Windows Forms denetimleriyle aynı sabitleme ve yerleştirme davranışına sahiptir.

1. `elementHost1` öğesini seçin.

2. **Özellikler** penceresinde, <xref:System.Windows.Forms.Control.Anchor%2A> özelliği **üst, alt, sol, sağ**olarak ayarlayın.

3. <xref:System.Windows.Forms.TableLayoutPanel> Denetimi daha büyük bir boyuta göre yeniden boyutlandırın.

   `elementHost1` Denetim hücreyi dolduracak şekilde yeniden boyutlandırır.

4. `elementHost2` öğesini seçin.

5. **Özellikler** penceresinde, <xref:System.Windows.Forms.Control.Dock%2A> özelliğinin değerini olarak <xref:System.Windows.Forms.DockStyle.Fill>ayarlayın.

   `elementHost2` Denetim hücreyi dolduracak şekilde yeniden boyutlandırır.

6. <xref:System.Windows.Forms.TableLayoutPanel> Denetimi seçin.

7. <xref:System.Windows.Forms.Control.Dock%2A> Özelliğinin değerini olarak <xref:System.Windows.Forms.DockStyle.Top>ayarlayın.

8. `elementHost3` öğesini seçin.

9. <xref:System.Windows.Forms.Control.Dock%2A> Özelliğinin değerini olarak <xref:System.Windows.Forms.DockStyle.Fill>ayarlayın.

   `elementHost3` Denetim, formdaki kalan alanı dolduracak şekilde yeniden boyutlandırır.

10. Formu yeniden boyutlandırın.

    Üç <xref:System.Windows.Forms.Integration.ElementHost> denetimin hepsi uygun şekilde yeniden boyutlandırılır.

    Daha fazla bilgi için [nasıl yapılır: TableLayoutPanel denetiminde](../controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)alt denetimleri bağla ve yerleştir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Nasıl yapılır: TableLayoutPanel denetiminde alt denetimleri sabitleme ve yerleştirme](../controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [Nasıl yapılır: Tasarım zamanında form kenarlarına bir denetim hizalayın](../controls/how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)
- [İzlenecek yol: Anlık görüntü çizgilerini kullanarak Windows Forms denetimleri düzenleme](../controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
- [Geçiş ve Birlikte Çalışabilirlik](../../wpf/advanced/migration-and-interoperability.md)
- [WPF Denetimlerini Kullanma](using-wpf-controls.md)
- [Visual Studio’da XAML tasarlama](/visualstudio/designers/designing-xaml-in-visual-studio)
