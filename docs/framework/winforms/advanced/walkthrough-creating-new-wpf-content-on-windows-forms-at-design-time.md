---
title: 'İzlenecek yol: Windows Formlarında Tasarım Zamanında Yeni bir WPF İçeriği Oluşturma'
ms.date: 08/18/2018
helpviewer_keywords:
- interoperability [Windows Forms], WPF and Windows Forms
- WPF content [Windows Forms], hosting in Windows Forms
- hosting WPF content in Windows Forms
- ElementHost control
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: 2e92d8e8-f0e4-4df7-9f07-2acf35cd798c
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: fc6f988d6ffd270eba4abe277ca34fa2eeec56fd
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73197431"
---
# <a name="walkthrough-create-new-wpf-content-on-windows-forms-at-design-time"></a>İzlenecek yol: tasarım zamanında Windows Forms yeni WPF içeriği oluşturma

Bu makalede, Windows Forms tabanlı uygulamalarınızda kullanılmak üzere bir Windows Presentation Foundation (WPF) denetimi oluşturma konusu gösterilmektedir.

## <a name="prerequisites"></a>Prerequisites

Bu yönergeyi tamamlamak için Visual Studio gerekir.

## <a name="create-the-project"></a>Projeyi oluşturma

Visual Studio 'Yu açın ve Visual Basic ya da görsel C# olarak adlandırılan `HostingWpf`yeni bir **Windows Forms App (.NET Framework)** projesi oluşturun.

> [!NOTE]
> WPF içeriği barındırırken yalnızca C# ve Visual Basic projeleri desteklenir.

## <a name="create-a-new-wpf-control"></a>Yeni bir WPF denetimi oluşturma

Yeni bir WPF denetimi oluşturmak ve projenize eklemek, projenize başka herhangi bir öğe eklemek kadar kolaydır. Windows Form Tasarımcısı, *bileşik denetim*veya *Kullanıcı denetimi*olarak adlandırılan belirli bir denetim türü ile birlikte kullanılabilir. WPF Kullanıcı denetimleri hakkında daha fazla bilgi için bkz. <xref:System.Windows.Controls.UserControl>.

> [!NOTE]
> WPF <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType> türü, Windows Forms tarafından sunulan Kullanıcı denetim türünden farklıdır, bu da <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>olarak adlandırılır.

Yeni bir WPF denetimi oluşturmak için:

1. **Çözüm Gezgini**, çözüme yeni bir **WPF Kullanıcı denetimi kitaplığı (.NET Framework)** projesi ekleyin. Denetim kitaplığı için varsayılan adı kullanın, `WpfControlLibrary1`. Varsayılan denetim adı `UserControl1.xaml`.

   Yeni denetimin eklenmesi aşağıdaki etkilere sahiptir:

   - Dosya UserControl1. xaml eklendi.

   - UserControl1.xaml.cs (veya UserControl1. xaml. vb) dosyası eklendi. Bu dosya olay işleyicileri ve diğer uygulama için arka plan kodu içerir.

   - WPF derlemelerinin başvuruları eklendi.

   - Dosya UserControl1. xaml, Visual Studio için WPF Tasarımcısı 'nda açılır.

2. Tasarım görünümü ' de `UserControl1` ' nin seçili olduğundan emin olun.

3. **Özellikler** penceresinde <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> özelliklerinin değerini **200**olarak ayarlayın.

4. **Araç kutusundan**bir <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> denetimini tasarım yüzeyine sürükleyin.

5. **Özellikler** penceresinde, <xref:System.Windows.Controls.TextBox.Text%2A> özelliğinin değerini **barındırılan içerik**olarak ayarlayın.

   > [!NOTE]
   > Genel olarak, daha karmaşık WPF içeriğini barındırmalısınız. <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> denetimi yalnızca tanım amacıyla kullanılır.

6. Projeyi oluşturun.

## <a name="add-a-wpf-control-to-a-windows-form"></a>Windows formuna WPF denetimi ekleme

Yeni WPF denetiminiz form üzerinde kullanıma yönelik kullanıma yöneliktir. Windows Forms WPF içeriğini barındırmak için <xref:System.Windows.Forms.Integration.ElementHost> denetimini kullanır.

Bir Windows formuna WPF denetimi eklemek için:

1. Windows Form Tasarımcısı `Form1` açın.

2. **Araç kutusunda**, **WPFUSERCONTROLLIBRARY WPF Kullanıcı denetimleri**etiketli sekmeyi bulun.

3. Bir `UserControl1` örneğini form üzerine sürükleyin.

    - WPF denetimini barındırmak için form üzerinde otomatik olarak bir <xref:System.Windows.Forms.Integration.ElementHost> denetimi oluşturulur.

    - <xref:System.Windows.Forms.Integration.ElementHost> denetim `elementHost1` olarak adlandırılır ve **Özellikler** penceresinde, <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> özelliğinin **UserControl1**olarak ayarlandığını görebilirsiniz.

    - WPF derlemelerine başvurular projeye eklenir.

    - `elementHost1` denetimi, kullanılabilir barındırma seçeneklerini gösteren bir akıllı etiket paneline sahiptir.

4. **ElementHost görevleri** akıllı etiketi panelinde **üst kapsayıcıda yerleştir**' i seçin.

5. Uygulamayı derlemek ve çalıştırmak için **F5** tuşuna basın.

## <a name="next-steps"></a>Sonraki adımlar

Windows Forms ve WPF farklı teknolojilerdir, ancak yakından birlikte çalışmak üzere tasarlanmıştır. Uygulamalarınızda daha zengin görünüm ve davranış sağlamak için aşağıdakileri deneyin:

- WPF sayfasında bir Windows Forms denetimi barındırın. Daha fazla bilgi için bkz. [Izlenecek yol: WPF 'de Windows Forms denetimi barındırma](../../wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md).

- Windows Forms Görsel stilleri WPF içeriğinize uygulayın. Daha fazla bilgi için bkz. [nasıl yapılır: karma uygulamada görsel stilleri etkinleştirme](../../wpf/advanced/how-to-enable-visual-styles-in-a-hybrid-application.md).

- WPF içeriğinizin stilini değiştirin. Daha fazla bilgi için bkz. [Izlenecek yol: WPF Içeriğini stillendirme](walkthrough-styling-wpf-content.md).

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Geçiş ve Birlikte Çalışabilirlik](../../wpf/advanced/migration-and-interoperability.md)
- [WPF Denetimlerini Kullanma](using-wpf-controls.md)
- [Visual Studio’da XAML tasarlama](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
