---
title: "İzlenecek yol: Windows Forms'da Tasarım Zamanında WPF İçeriği Atama"
ms.date: 03/30/2017
helpviewer_keywords:
- WPF content [Windows Forms], assigning at design time
- ElementHost control [Windows Forms], assigning WPF content at design time
- interoperability [WPF]
- Windows Forms, content assignments
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: b3e9ef93-7e0f-4a2f-8f1e-3437609a1eb7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: bc5f5e2d8808c0a60df721bf2c0ed76b45ef49a0
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666255"
---
# <a name="walkthrough-assign-wpf-content-on-windows-forms-at-design-time"></a>İzlenecek yol: Tasarım zamanında Windows Forms WPF içeriği atama

Bu makalede, formunuzda görüntülemek istediğiniz Windows Presentation Foundation (WPF) denetim türlerini seçme gösterilmektedir. Projenize dahil olan herhangi bir WPF denetim türünü seçebilirsiniz.

## <a name="prerequisites"></a>Önkoşullar

Bu yönergeyi tamamlamak için Visual Studio gerekir.

## <a name="create-the-project"></a>Projeyi oluşturma

Visual Studio 'Yu açın ve Visual Basic veya görsel C# adlı `SelectingWpfContent`yeni bir Windows Forms uygulama projesi oluşturun.

> [!NOTE]
> WPF içeriği barındırırken yalnızca C# ve Visual Basic projeleri desteklenir.

## <a name="create-the-wpf-control-types"></a>WPF denetim türlerini oluşturma

Projeye wpf denetim türlerini ekledikten sonra, bunları farklı <xref:System.Windows.Forms.Integration.ElementHost> denetimlerde barındırabilirsiniz.

1. Çözüme yeni bir WPF <xref:System.Windows.Controls.UserControl> projesi ekleyin. Denetim türü için varsayılan adı kullanın, `UserControl1.xaml`. Daha fazla bilgi için bkz [. İzlenecek yol: Tasarım zamanında](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md)Windows Forms yeni WPF içeriği oluşturuluyor.

2. Tasarım görünümü ' de, ' `UserControl1` nin seçili olduğundan emin olun.

3. **Özellikler** penceresinde, <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> özelliklerinin değerini **200**olarak ayarlayın.

4. Öğesine bir <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> denetim ekleyin <xref:System.Windows.Controls.TextBox.Text%2A>ve özelliğin değerini barındırılan içerik olarak ayarlayın <xref:System.Windows.Controls.UserControl> .

5. Projeye ikinci bir WPF <xref:System.Windows.Controls.UserControl> ekleyin. Denetim türü için varsayılan adı kullanın, `UserControl2.xaml`.

6. **Özellikler** penceresinde, <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> özelliklerinin değerini **200**olarak ayarlayın.

7. Öğesine bir <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> denetim ekleyin <xref:System.Windows.Controls.TextBox.Text%2A>ve özelliğin değerini barındırılan içerik 2 olarak ayarlayın <xref:System.Windows.Controls.UserControl> .

   > [!NOTE]
   > Genel olarak, daha karmaşık WPF içeriğini barındırmalısınız. <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> Denetim burada yalnızca tanım amacıyla kullanılır.

8. Projeyi oluşturun.

## <a name="select-wpf-controls"></a>WPF denetimlerini seçin

Zaten barındıran içeriği olan bir <xref:System.Windows.Forms.Integration.ElementHost> denetime farklı WPF içeriği atayabilirsiniz.

1. Windows Form Tasarımcısı `Form1` açın.

2. **Araç kutusunda**, form `UserControl1` üzerinde bir örnek `UserControl1` oluşturmak için çift tıklayın.

   Bir örneği `UserControl1` adlı <xref:System.Windows.Forms.Integration.ElementHost> Yeni`elementHost1`bir denetimde barındırılır.

3. İçin `elementHost1`akıllı etiket panelinde **barındırılan içerik Seç** açılan listesini açın.

4. Açılan liste kutusundan **UserControl2** öğesini seçin.

   Denetim artık `UserControl2` türün bir örneğini barındırır. `elementHost1`

5. **Özellikler** penceresinde, <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> özelliğinin **UserControl2**olarak ayarlandığını doğrulayın.

6. **Araç kutusu**' nda, **WPF birlikte çalışabilirlik** grubunda bir <xref:System.Windows.Forms.Integration.ElementHost> denetimi form üzerine sürükleyin.

   Yeni denetim `elementHost2`için varsayılan ad.

7. İçin `elementHost2`akıllı etiket panelinde **barındırılan içerik Seç** açılan listesini açın.

8. Açılan listeden **UserControl1** ' i seçin.

9. Denetim artık `UserControl1` türün bir örneğini barındırır. `elementHost2`

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Geçiş ve Birlikte Çalışabilirlik](../../wpf/advanced/migration-and-interoperability.md)
- [WPF Denetimlerini Kullanma](using-wpf-controls.md)
- [Visual Studio’da XAML tasarlama](/visualstudio/designers/designing-xaml-in-visual-studio)
