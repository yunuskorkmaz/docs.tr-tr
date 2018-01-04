---
title: "İzlenecek yol: Windows Formlarında Tasarım Zamanında Yeni bir WPF İçeriği Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- interoperability [Windows Forms], WPF and Windows Forms
- WPF content [Windows Forms], hosting in Windows Forms
- hosting WPF content in Windows Forms
- ElementHost control
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: 2e92d8e8-f0e4-4df7-9f07-2acf35cd798c
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ba7731456cfcf35cd16b1df304fee4f4c138db84
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time"></a>İzlenecek yol: Windows Formlarında Tasarım Zamanında Yeni bir WPF İçeriği Oluşturma
Bu konu, Windows Forms tabanlı uygulamalarda kullanım için bir Windows Presentation Foundation (WPF) denetimini oluşturulacağını gösterir.  
  
 Bu kılavuzda, aşağıdaki görevleri gerçekleştirin:  
  
-   Projesi oluşturun.  
  
-   Yeni bir WPF denetim oluşturun.  
  
-   Yeni WPF denetimi için Windows formu ekleyin. WPF denetimi içinde barındırılan bir <xref:System.Windows.Forms.Integration.ElementHost> denetim.  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:  
  
-   [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)].  
  
## <a name="creating-the-project"></a>Projeyi Oluşturma  
 Windows Forms projesi oluşturmak için ilk adımdır bakın.  
  
> [!NOTE]
>  WPF içeriği barındırma, yalnızca C# ve Visual Basic projeleri desteklenir.  
  
#### <a name="to-create-the-project"></a>Proje oluşturmak için  
  
-   Visual Basic veya Visual C# adlı yeni bir Windows Forms uygulaması projesi oluşturma `HostingWpf`.  
  
## <a name="creating-a-new-wpf-control"></a>Yeni bir WPF denetim oluşturma  
 Yeni bir WPF denetim oluşturma ve projenize ekleme projenize başka bir öğe ekleme olarak kadar kolaydır. Belirli bir tür adlı denetimi ile Windows Form Tasarımcısı çalışır *bileşik denetim*, veya *kullanıcı denetimi*. WPF kullanıcı denetimi hakkında daha fazla bilgi için bkz: <xref:System.Windows.Controls.UserControl>.  
  
> [!NOTE]
>  <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType> WPF olarak da adlandırılır Windows Forms tarafından sağlanan kullanıcı denetimi türü farklıdır türüyle <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>.  
  
#### <a name="to-create-a-new-wpf-control"></a>Yeni bir WPF denetimi oluşturmak için  
  
1.  İçinde **Çözüm Gezgini**, yeni bir ekleme **WPF kullanıcı denetimi Kitaplığı** çözüme proje. Denetim Kitaplığı için varsayılan adı kullanacak `WpfControlLibrary1`. Varsayılan Denetim adı `UserControl1.xaml`.  
  
     Yeni denetim ekleme aşağıdaki etkileri gösterir.  
  
    -   Dosya da UserControl1.XAML'i eklenir.  
  
    -   Dosya UserControl1.xaml.cs veya UserControl1.xaml.vb eklenir. Bu dosya, arka plan koduna olay işleyicileri ve diğer uygulama içerir.  
  
    -   WPF derlemelerine başvurular eklenir.  
  
    -   Dosya da UserControl1.XAML'i açılır [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)].  
  
2.  Tasarım görünümü içinde olduğundan emin olun `UserControl1` seçilir. Daha fazla bilgi için bkz: [nasıl yapılır: seçin ve tasarım yüzeyine taşıma öğelerde](http://msdn.microsoft.com/en-us/54cb70b6-b35b-46e4-a0cc-65189399c474).  
  
3.  İçinde **özellikleri** penceresindeki değerini ayarlayın <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> özelliklerine `200`.  
  
4.  Gelen **araç**, sürükleyin bir <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> tasarım yüzeyine denetim.  
  
5.  İçinde **özellikleri** penceresindeki değerini ayarlayın <xref:System.Windows.Controls.TextBox.Text%2A> özelliğine **barındırılan içerik**.  
  
    > [!NOTE]
    >  Genel olarak, daha karmaşık WPF içeriği barındırma. <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> Denetimi yalnızca tanım yalnızca amacıyla burada kullanılır.  
  
6.  Projeyi oluşturun.  
  
## <a name="adding-a-wpf-control-to-a-windows-form"></a>Bir Windows formu WPF denetim ekleme  
 Yeni WPF denetiminizi formdaki kullanılmaya hazırdır. Windows Forms kullanan <xref:System.Windows.Forms.Integration.ElementHost> denetlemek için konak WPF içeriği  
  
#### <a name="to-add-a-wpf-control-to-a-windows-form"></a>Bir WPF denetimi için Windows formu eklemek için  
  
1.  Açık `Form1` Windows Forms Tasarımcısı'nda.  
  
2.  İçinde **araç**, etiketli sekmesini bulmak **WPFUserControlLibrary WPF kullanıcı denetimi**.  
  
3.  Bir örneğini sürükleyin `UserControl1` forma.  
  
    -   Bir <xref:System.Windows.Forms.Integration.ElementHost> denetimi WPF denetimi barındırmak için form üzerinde otomatik olarak oluşturulur.  
  
    -   <xref:System.Windows.Forms.Integration.ElementHost> Denetim adlandırılan `elementHost1` ve **özellikleri** penceresinde görebilirsiniz kendi <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> özelliği ayarlanmış **UserControl1**.  
  
    -   WPF derlemelerine başvurular projeye eklenir.  
  
    -   `elementHost1` Denetim kullanılabilir barındırma seçenekleri gösterilir bir akıllı etiket panel sahiptir.  
  
4.  İçinde **ElementHost görevleri** akıllı etiket paneli, select **Ana kapsayıcıda yerleştir**.  
  
5.  Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın.  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 Windows Forms ve WPF farklı teknolojilerdir ancak yakından birlikte çalışmak üzere tasarlanmıştır. Daha zengin bir görünüm ve davranış uygulamalarınızda sağlamak için aşağıdakileri deneyin.  
  
-   Windows Forms denetimini bir WPF sayfada barındırır. Daha fazla bilgi için bkz: [izlenecek yol: WPF bir Windows Forms denetimi barındırma](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md).  
  
-   Windows Forms görsel stiller, WPF içeriği için geçerlidir. Daha fazla bilgi için bkz: [nasıl yapılır: görsel stiller etkinleştirmek karma uygulamada](../../../../docs/framework/wpf/advanced/how-to-enable-visual-styles-in-a-hybrid-application.md).  
  
-   WPF içeriği stilini değiştirin. Daha fazla bilgi için bkz: [izlenecek yol: WPF içeriği stil oluşturma](../../../../docs/framework/winforms/advanced/walkthrough-styling-wpf-content.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [Geçiş ve Birlikte Çalışabilirlik](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)  
 [WPF Denetimlerini Kullanma](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)  
 [WPF Tasarımcısı](http://msdn.microsoft.com/en-us/c6c65214-8411-4e16-b254-163ed4099c26)
