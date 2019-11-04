---
title: 'İzlenecek yol: Windows Formlarında Tasarım Zamanında WPF İçeriği Atama'
ms.date: 03/30/2017
helpviewer_keywords:
- WPF content [Windows Forms], assigning at design time
- ElementHost control [Windows Forms], assigning WPF content at design time
- interoperability [WPF]
- Windows Forms, content assignments
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: b3e9ef93-7e0f-4a2f-8f1e-3437609a1eb7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0c1e0c91b7ab8bded677a86b597b02b9cb442d98
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460663"
---
# <a name="walkthrough-assign-wpf-content-on-windows-forms-at-design-time"></a>İzlenecek yol: tasarım zamanında Windows Forms WPF içeriği atama

Bu makalede, formunuzda görüntülemek istediğiniz Windows Presentation Foundation (WPF) denetim türlerini seçme gösterilmektedir. Projenize dahil olan herhangi bir WPF denetim türünü seçebilirsiniz.

## <a name="prerequisites"></a>Prerequisites

Bu yönergeyi tamamlamak için Visual Studio gerekir.

## <a name="create-the-project"></a>Projeyi oluşturma

Visual Studio 'Yu açın ve Visual Basic veya görsel C# adlı `SelectingWpfContent`Windows Forms uygulama projesi oluşturun.

> [!NOTE]
> WPF içeriği barındırırken yalnızca C# ve Visual Basic projeleri desteklenir.

## <a name="create-the-wpf-control-types"></a>WPF denetim türlerini oluşturma

Projeye WPF denetim türlerini ekledikten sonra, bunları farklı <xref:System.Windows.Forms.Integration.ElementHost> denetimlerinde barındırabilirsiniz.

1. Çözüme yeni bir WPF <xref:System.Windows.Controls.UserControl> projesi ekleyin. Denetim türü için varsayılan adı kullanın, `UserControl1.xaml`. Daha fazla bilgi için bkz. [Izlenecek yol: tasarım zamanında Windows Forms yenı WPF Içeriği oluşturma](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).

2. Tasarım görünümü ' de `UserControl1` ' nin seçili olduğundan emin olun.

3. **Özellikler** penceresinde <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> özelliklerinin değerini **200**olarak ayarlayın.

4. <xref:System.Windows.Controls.UserControl> <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> bir denetim ekleyin ve <xref:System.Windows.Controls.TextBox.Text%2A> özelliğinin değerini **barındırılan içerik**olarak ayarlayın.

5. Projeye ikinci bir WPF <xref:System.Windows.Controls.UserControl> ekleyin. Denetim türü için varsayılan adı kullanın, `UserControl2.xaml`.

6. **Özellikler** penceresinde <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> özelliklerinin değerini **200**olarak ayarlayın.

7. <xref:System.Windows.Controls.UserControl> <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> bir denetim ekleyin ve <xref:System.Windows.Controls.TextBox.Text%2A> özelliğinin değerini **barındırılan içerik 2**olarak ayarlayın.

   > [!NOTE]
   > Genel olarak, daha karmaşık WPF içeriğini barındırmalısınız. <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> denetimi yalnızca tanım amacıyla kullanılır.

8. Projeyi oluşturun.

## <a name="select-wpf-controls"></a>WPF denetimlerini seçin

Zaten barındırma içeriği olan bir <xref:System.Windows.Forms.Integration.ElementHost> denetimine farklı WPF içeriği atayabilirsiniz.

1. Windows Form Tasarımcısı `Form1` açın.

2. **Araç kutusunda**`UserControl1` ' ye çift tıklayarak formda `UserControl1` bir örneğini oluşturun.

   `UserControl1` örneği, `elementHost1`adlı yeni bir <xref:System.Windows.Forms.Integration.ElementHost> denetiminde barındırılır.

3. `elementHost1`için akıllı etiket panelinde **barındırılan Içerik Seç** açılan listesini açın.

4. Açılan liste kutusundan **UserControl2** öğesini seçin.

   `elementHost1` denetimi artık `UserControl2` türünün bir örneğini barındırır.

5. **Özellikler** penceresinde, <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> özelliğinin **UserControl2**olarak ayarlandığını doğrulayın.

6. **Araç kutusundan** **WPF birlikte çalışabilirlik** grubunda, form üzerine bir <xref:System.Windows.Forms.Integration.ElementHost> denetimi sürükleyin.

   Yeni denetim için varsayılan ad `elementHost2`.

7. `elementHost2`için akıllı etiket panelinde **barındırılan Içerik Seç** açılan listesini açın.

8. Açılan listeden **UserControl1** ' i seçin.

9. `elementHost2` denetimi artık `UserControl1` türünün bir örneğini barındırır.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Geçiş ve Birlikte Çalışabilirlik](../../wpf/advanced/migration-and-interoperability.md)
- [WPF Denetimlerini Kullanma](using-wpf-controls.md)
- [Visual Studio’da XAML tasarlama](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
