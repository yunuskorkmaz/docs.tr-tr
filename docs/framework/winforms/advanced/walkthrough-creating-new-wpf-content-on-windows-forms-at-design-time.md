---
title: "İzlenecek yol: Windows Forms'da Tasarım Zamanında Yeni WPF İçeriği Oluşturma"
ms.date: 08/18/2018
helpviewer_keywords:
- interoperability [Windows Forms], WPF and Windows Forms
- WPF content [Windows Forms], hosting in Windows Forms
- hosting WPF content in Windows Forms
- ElementHost control
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: 2e92d8e8-f0e4-4df7-9f07-2acf35cd798c
ms.openlocfilehash: 889e81053d4e2264755468446a4e1681216ae22e
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040372"
---
# <a name="walkthrough-create-new-wpf-content-on-windows-forms-at-design-time"></a>İzlenecek yol: Tasarım zamanında Windows Forms yeni WPF içeriği oluşturma

Bu makalede, Windows Forms tabanlı uygulamalarınızda kullanılmak üzere bir Windows Presentation Foundation (WPF) denetimi oluşturma konusu gösterilmektedir.

Bu kılavuzda, aşağıdaki görevleri gerçekleştirirsiniz:

- Projeyi oluşturun.

- Yeni bir WPF denetimi oluşturun.

- Yeni WPF denetimini bir Windows form 'a ekleyin. WPF denetimi bir <xref:System.Windows.Forms.Integration.ElementHost> denetimde barındırılır.

## <a name="prerequisites"></a>Önkoşullar

Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- Visual Studio

## <a name="create-the-project"></a>Projeyi oluşturma

İlk adım Windows Forms projesi oluşturmaktır. Visual Studio 'Yu açın ve Visual Basic ya da görsel C# adında `HostingWpf`yeni bir **Windows Forms App (.NET Framework)** projesi oluşturun.

> [!NOTE]
> WPF içeriği barındırırken yalnızca C# ve Visual Basic projeleri desteklenir.

## <a name="create-a-new-wpf-control"></a>Yeni bir WPF denetimi oluşturma

Yeni bir WPF denetimi oluşturmak ve projenize eklemek, projenize başka herhangi bir öğe eklemek kadar kolaydır. Windows Form Tasarımcısı, *bileşik denetim*veya *Kullanıcı denetimi*olarak adlandırılan belirli bir denetim türü ile birlikte kullanılabilir. WPF Kullanıcı denetimleri hakkında daha fazla bilgi için bkz <xref:System.Windows.Controls.UserControl>.

> [!NOTE]
> WPF türü, olarak da adlandırılan <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>Windows Forms tarafından belirtilen kullanıcı denetim türünden farklıdır. <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType>

Yeni bir WPF denetimi oluşturmak için:

1. **Çözüm Gezgini**, çözüme yeni bir **WPF Kullanıcı denetimi kitaplığı (.NET Framework)** projesi ekleyin. Denetim kitaplığı için varsayılan adı kullanın, `WpfControlLibrary1`. Varsayılan denetim adı `UserControl1.xaml`.

     Yeni denetimin eklenmesi aşağıdaki etkilere sahiptir:

    - Dosya UserControl1. xaml eklendi.

    - Ya UserControl1.xaml.cs veya UserControl1. xaml. vb dosyası eklendi. Bu dosya olay işleyicileri ve diğer uygulama için arka plan kodu içerir.

    - WPF derlemelerinin başvuruları eklendi.

    - Dosya UserControl1. xaml içinde [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)]açılır.

2. Tasarım görünümü ' de, ' `UserControl1` nin seçili olduğundan emin olun. Daha fazla bilgi için [nasıl yapılır: Tasarım Yüzeyi](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb514527(v=vs.100))öğeleri seçin ve taşıyın.

3. **Özellikler** penceresinde, <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> özelliklerinin değerini **200**olarak ayarlayın.

4. **Araç kutusundan**tasarım yüzeyine bir <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> denetim sürükleyin.

5. **Özellikler** penceresinde, <xref:System.Windows.Controls.TextBox.Text%2A> özelliğin değerini **barındırılan içerik**olarak ayarlayın.

    > [!NOTE]
    > Genel olarak, daha karmaşık WPF içeriğini barındırmalısınız. <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> Denetim burada yalnızca tanım amacıyla kullanılır.

6. Projeyi oluşturun.

## <a name="add-a-wpf-control-to-a-windows-form"></a>Windows formuna WPF denetimi ekleme

Yeni WPF denetiminiz form üzerinde kullanıma yönelik kullanıma yöneliktir. Windows Forms WPF içeriğini <xref:System.Windows.Forms.Integration.ElementHost> barındırmak için denetimi kullanır.

Bir Windows formuna WPF denetimi eklemek için:

1. Windows Form Tasarımcısı `Form1` açın.

2. **Araç kutusunda**, **WPFUSERCONTROLLIBRARY WPF Kullanıcı denetimleri**etiketli sekmeyi bulun.

3. Bir örneğini `UserControl1` formun üzerine sürükleyin.

    - WPF <xref:System.Windows.Forms.Integration.ElementHost> denetimini barındırmak için formda otomatik olarak bir denetim oluşturulur.

    - `elementHost1` <xref:System.Windows.Forms.Integration.ElementHost.Child%2A>Denetim olarak adlandırılır ve Özellikler penceresinde, özelliğin UserControl1 olarak ayarlandığını görebilirsiniz. <xref:System.Windows.Forms.Integration.ElementHost>

    - WPF derlemelerine başvurular projeye eklenir.

    - `elementHost1` Denetimde, kullanılabilir barındırma seçeneklerini gösteren bir akıllı etiket paneli bulunur.

4. **ElementHost görevleri** akıllı etiketi panelinde **üst kapsayıcıda yerleştir**' i seçin.

5. Uygulamayı derlemek ve çalıştırmak için **F5** tuşuna basın.

## <a name="next-steps"></a>Sonraki adımlar

Windows Forms ve WPF farklı teknolojilerdir, ancak yakından birlikte çalışmak üzere tasarlanmıştır. Uygulamalarınızda daha zengin görünüm ve davranış sağlamak için aşağıdakileri deneyin:

- WPF sayfasında bir Windows Forms denetimi barındırın. Daha fazla bilgi için bkz [. İzlenecek yol: WPF](../../wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md)'de Windows Forms denetimini barındırma.

- Windows Forms Görsel stilleri WPF içeriğinize uygulayın. Daha fazla bilgi için [nasıl yapılır: Karma uygulamada](../../wpf/advanced/how-to-enable-visual-styles-in-a-hybrid-application.md)görsel stilleri etkinleştirin.

- WPF içeriğinizin stilini değiştirin. Daha fazla bilgi için bkz [. İzlenecek yol: WPF Içeriğini](walkthrough-styling-wpf-content.md)stillendirme.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Geçiş ve Birlikte Çalışabilirlik](../../wpf/advanced/migration-and-interoperability.md)
- [WPF Denetimlerini Kullanma](using-wpf-controls.md)
- [Visual Studio’da XAML tasarlama](/visualstudio/designers/designing-xaml-in-visual-studio)
