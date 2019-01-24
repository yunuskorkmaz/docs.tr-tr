---
title: "İzlenecek yol: Windows Forms'ta tasarım zamanında yeni WPF içeriği oluşturma"
ms.date: 08/18/2018
helpviewer_keywords:
- interoperability [Windows Forms], WPF and Windows Forms
- WPF content [Windows Forms], hosting in Windows Forms
- hosting WPF content in Windows Forms
- ElementHost control
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: 2e92d8e8-f0e4-4df7-9f07-2acf35cd798c
ms.openlocfilehash: 9414eb8edc839b109aafa0c98fa3ed74a34a7d62
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54500505"
---
# <a name="walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time"></a>İzlenecek yol: Windows Forms'ta tasarım zamanında yeni WPF içeriği oluşturma

Bu konuda kullanım için bir Windows Presentation Foundation (WPF) denetimini Windows Forms tabanlı uygulamalarınızı oluşturma işlemini gösterir.

Bu kılavuzda, aşağıdaki görevleri gerçekleştirin:

- Projeyi oluşturun.

- Yeni bir WPF denetiminde oluşturun.

- Yeni WPF denetimi için bir Windows formu ekleyin. WPF denetiminde barındırılan bir <xref:System.Windows.Forms.Integration.ElementHost> denetimi.

## <a name="prerequisites"></a>Önkoşullar

Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- Visual Studio 2017

## <a name="creating-the-project"></a>Projeyi Oluşturma

İlk adım Windows Forms projesi oluşturmaktır. Visual Studio'yu açın ve yeni bir **Windows Forms uygulaması (.NET Framework)** Visual Basic veya Visual C# adlı proje `HostingWpf`.

> [!NOTE]
> WPF içeriği barındırma, yalnızca C# ve Visual Basic projelerinde desteklenir.

## <a name="creating-a-new-wpf-control"></a>Yeni bir WPF denetim oluşturma

Yeni bir WPF denetim oluşturma ve bunu projenize ekleyerek herhangi bir öğeyi projenize eklemek kadar kolaydır. Windows Form Tasarımcısı adlı Denetim belirli bir türünü çalışır *bileşik denetim*, veya *kullanıcı denetimi*. WPF kullanıcı denetimleri hakkında daha fazla bilgi için bkz: <xref:System.Windows.Controls.UserControl>.

> [!NOTE]
> <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType> WPF farklı olarak da adlandırılır Windows Forms tarafından sağlanan kullanıcı Denetim türü için tür <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>.

### <a name="to-create-a-new-wpf-control"></a>Yeni bir WPF denetimi oluşturmak için

1. İçinde **Çözüm Gezgini**, yeni bir **WPF kullanıcı denetimi kitaplığı (.NET Framework)** çözüme bir proje. Denetim Kitaplığı için varsayılan adı kullanın `WpfControlLibrary1`. Varsayılan Denetim adı `UserControl1.xaml`.

     Yeni denetim ekleme, aşağıdaki etkileri gösterir:

    - Dosya UserControl1.xaml eklenir.

    - Dosya UserControl1.xaml.cs veya UserControl1.xaml.vb eklenir. Bu dosya, arka plan kod olay işleyicileri ve diğer uygulaması içerir.

    - WPF derlemelerine başvurular eklenir.

    - Dosya UserControl1.xaml açılır [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)].

2. Tasarım görünümünde emin `UserControl1` seçilir. Daha fazla bilgi için [nasıl yapılır: Seçin ve tasarım yüzeyine öğeleri Taşı](https://msdn.microsoft.com/library/54cb70b6-b35b-46e4-a0cc-65189399c474).

3. İçinde **özellikleri** penceresinde değerini ayarlayın <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> özelliklerine **200**.

4. Gelen **araç kutusu**, sürükleyin bir <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> denetimi tasarım yüzeyine sürükleyin.

5. İçinde **özellikleri** penceresinde değerini ayarlayın <xref:System.Windows.Controls.TextBox.Text%2A> özelliğini **barındırılan içerik**.

    > [!NOTE]
    > Genel olarak, daha karmaşık bir WPF içeriği barındırmamalısınız. <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> Denetimi yalnızca yalnızca tanım amaçlıdır için burada kullanılır.

6. Projeyi oluşturun.

## <a name="adding-a-wpf-control-to-a-windows-form"></a>Bir Windows forma bir WPF denetimi ekleme

Yeni WPF denetimi form üzerinde kullanılmaya hazırdır. Windows Forms kullanan <xref:System.Windows.Forms.Integration.ElementHost> konak WPF içeriği için denetim.

### <a name="to-add-a-wpf-control-to-a-windows-form"></a>Bir WPF denetiminde bir Windows forma eklemek için

1. Açık `Form1` Windows Forms Tasarımcısı'nda.

2. İçinde **araç kutusu**, etiketlenmiş sekmeyi bulun **WPFUserControlLibrary WPF kullanıcı denetimleri**.

3. Örneği sürükleyin `UserControl1` forma.

    - Bir <xref:System.Windows.Forms.Integration.ElementHost> denetimi WPF denetimini barındırmak için bir form üzerinde otomatik olarak oluşturulur.

    - <xref:System.Windows.Forms.Integration.ElementHost> Denetimine `elementHost1` ve **özellikleri** penceresinde görebilirsiniz, <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> özelliği **UserControl1**.

    - WPF derlemelerine başvurular projeye eklenir.

    - `elementHost1` Denetim barındırma seçeneklerini gösteren bir akıllı etiket paneli sahiptir.

4. İçinde **ElementHost görevleri** akıllı etiket paneli, select **üst kapsayıcıya Yerleştir**.

5. Tuşuna **F5** oluşturun ve uygulamayı çalıştırın.

## <a name="next-steps"></a>Sonraki Adımlar

Windows Forms ve WPF farklı teknolojilerdir, ancak yakın çalışmak için tasarlanmıştır. Daha zengin görünümünü ve davranışını uygulamalarınızda sağlamak için aşağıdakileri deneyin:

- Bir WPF sayfasındaki bir Windows Forms denetimi barındırma. Daha fazla bilgi için [izlenecek yol: WPF içinde Forms Denetimi'ne bir Windows barındırma](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md).

- Windows Forms görsel stiller, WPF içeriği için geçerlidir. Daha fazla bilgi için [nasıl yapılır: Karma uygulamada görsel stilleri etkinleştirme](../../../../docs/framework/wpf/advanced/how-to-enable-visual-styles-in-a-hybrid-application.md).

- WPF İçerik stilini değiştirin. Daha fazla bilgi için [izlenecek yol: WPF içeriği için stil oluşturma](../../../../docs/framework/winforms/advanced/walkthrough-styling-wpf-content.md).

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Geçiş ve Birlikte Çalışabilirlik](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)
- [WPF Denetimlerini Kullanma](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)
- [Visual Studio’da XAML tasarlama](/visualstudio/designers/designing-xaml-in-visual-studio)
