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
ms.openlocfilehash: 6db75e9d8ec5aeb1a0c7310d39391f8f264649d3
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/11/2018
ms.locfileid: "44368331"
---
# <a name="walkthrough-assigning-wpf-content-on-windows-forms-at-design-time"></a>İzlenecek yol: Windows Formlarında Tasarım Zamanında WPF İçeriği Atama
Bu izlenecek yol, formu görüntülemek istediğiniz Windows Presentation Foundation (WPF) denetim türlerini seçmek nasıl gösterir. Projenize dahil tüm WPF denetim türlerini seçebilirsiniz.  
  
 Bu kılavuzda, aşağıdaki görevleri gerçekleştirin:  
  
-   Projeyi oluşturun.  
  
-   WPF denetim türlerini oluşturun.  
  
-   WPF denetimleri seçin.  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:  
  
-   [!INCLUDE[vs_dev11_long](../../../../includes/vs-dev11-long-md.md)].  
  
## <a name="creating-the-project"></a>Projeyi Oluşturma  
 İlk adım Windows Forms projesi oluşturmaktır.  
  
> [!NOTE]
>  WPF içeriği barındırma, yalnızca C# ve Visual Basic projelerinde desteklenir.  
  
#### <a name="to-create-the-project"></a>Proje oluşturmak için  
  
-   Visual Basic veya Visual C# adlı yeni bir Windows Forms uygulaması projesi oluşturma `SelectingWpfContent`.  
  
## <a name="creating-the-wpf-control-types"></a>WPF denetim türleri oluşturma  
 WPF denetim türleri projeye ekledikten sonra bunları farklı barındırabilirsiniz <xref:System.Windows.Forms.Integration.ElementHost> kontrol eder.  
  
#### <a name="to-create-wpf-control-types"></a>WPF denetim türleri oluşturmak için  
  
1.  Yeni bir WPF ekleme <xref:System.Windows.Controls.UserControl> çözüme bir proje. Denetim türü için varsayılan adı kullanacak `UserControl1.xaml`. Daha fazla bilgi için [izlenecek yol: oluşturma yeni WPF içeriği Windows Forms'ta tasarım zamanında](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).  
  
2.  Tasarım görünümünde emin `UserControl1` seçilir. Daha fazla bilgi için [nasıl yapılır: seçin ve tasarım yüzeyinde taşımak öğeleri](https://msdn.microsoft.com/library/54cb70b6-b35b-46e4-a0cc-65189399c474).  
  
3.  İçinde **özellikleri** penceresinde değerini ayarlayın <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> özelliklerine `200`.  
  
4.  Ekleme bir <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> denetimini <xref:System.Windows.Controls.UserControl> ve değerini ayarlama <xref:System.Windows.Controls.TextBox.Text%2A> özelliğini **barındırılan içerik**.  
  
5.  İkinci bir WPF ekleme <xref:System.Windows.Controls.UserControl> projeye. Denetim türü için varsayılan adı kullanacak `UserControl2.xaml`.  
  
6.  İçinde **özellikleri** penceresinde değerini ayarlayın <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> özelliklerine `200`.  
  
7.  Ekleme bir <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> denetimini <xref:System.Windows.Controls.UserControl> ve değerini ayarlama <xref:System.Windows.Controls.TextBox.Text%2A> özelliğini **barındırılan içerik 2**.  
  
 **Not** genel olarak, daha karmaşık bir WPF içeriği barındırmamalısınız. <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> Denetimi yalnızca yalnızca tanım amaçlıdır için burada kullanılır.  
  
1.  Projeyi oluşturun.  
  
## <a name="selecting-wpf-controls"></a>WPF denetimleri seçme  
 Farklı bir WPF içeriği için atayabileceğiniz bir <xref:System.Windows.Forms.Integration.ElementHost> içerik barındırma zaten denetimi.  
  
#### <a name="to-select-wpf-controls"></a>WPF denetimleri seçin  
  
1.  Açık `Form1` Windows Forms Tasarımcısı'nda.  
  
2.  İçinde **araç kutusu**, çift `UserControl1` bir örneğini oluşturmak için `UserControl1` form üzerinde.  
  
     Örneği `UserControl1` yeni bir barındırılan <xref:System.Windows.Forms.Integration.ElementHost> adlı Denetim `elementHost1`.  
  
3.  Akıllı etiket panelinde `elementHost1`açın **barındırılan içerik Seç** aşağı açılan listesi.  
  
4.  Seçin **UserControl 2** aşağı açılan liste kutusundan.  
  
     `elementHost1` Denetimi artık bir örneğini barındıran `UserControl2` türü.  
  
5.  İçinde **özellikleri** penceresinde onaylayın <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> özelliği **UserControl 2**.  
  
6.  Gelen **araç kutusu**, **WPF birlikte çalışabilirliği** grubundan bir <xref:System.Windows.Forms.Integration.ElementHost> forma denetim.  
  
     Yeni denetim için varsayılan ad `elementHost2`.  
  
7.  Akıllı etiket panelinde `elementHost2`açın **barındırılan içerik Seç** aşağı açılan listesi.  
  
8.  Seçin **UserControl1** aşağı açılan listeden.  
  
9. `elementHost2` Denetimi artık bir örneğini barındıran `UserControl1` türü.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [Geçiş ve Birlikte Çalışabilirlik](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)  
 [WPF Denetimlerini Kullanma](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)  
 [Visual Studio’da XAML tasarlama](/visualstudio/designers/designing-xaml-in-visual-studio)
