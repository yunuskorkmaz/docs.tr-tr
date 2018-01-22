---
title: "İzlenecek yol: Windows Formlarında Tasarım Zamanında WPF İçeriği Atama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WPF content [Windows Forms], assigning at design time
- ElementHost control [Windows Forms], assigning WPF content at design time
- interoperability [WPF]
- Windows Forms, content assignments
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: b3e9ef93-7e0f-4a2f-8f1e-3437609a1eb7
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 93ff6f39f4d8bcdd037d373f8bd26cbb3c32c125
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="walkthrough-assigning-wpf-content-on-windows-forms-at-design-time"></a>İzlenecek yol: Windows Formlarında Tasarım Zamanında WPF İçeriği Atama
Bu kılavuz, Windows Presentation Foundation (WPF) denetim türlerini formunuzda görüntülemek istediğinizi seçmek nasıl gösterir. Projenizde dahil tüm WPF denetim türlerini seçebilirsiniz.  
  
 Bu kılavuzda, aşağıdaki görevleri gerçekleştirin:  
  
-   Projesi oluşturun.  
  
-   WPF denetim türlerini oluşturun.  
  
-   WPF denetimleri seçin.  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:  
  
-   [!INCLUDE[vs_dev11_long](../../../../includes/vs-dev11-long-md.md)].  
  
## <a name="creating-the-project"></a>Projeyi Oluşturma  
 Windows Forms projesi oluşturmak için ilk adımdır bakın.  
  
> [!NOTE]
>  WPF içeriği barındırma, yalnızca C# ve Visual Basic projeleri desteklenir.  
  
#### <a name="to-create-the-project"></a>Proje oluşturmak için  
  
-   Visual Basic veya Visual C# adlı yeni bir Windows Forms uygulaması projesi oluşturma `SelectingWpfContent`.  
  
## <a name="creating-the-wpf-control-types"></a>WPF denetim türleri oluşturma  
 WPF denetim türleri projeye ekledikten sonra bunları farklı barındırabilir <xref:System.Windows.Forms.Integration.ElementHost> kontrol eder.  
  
#### <a name="to-create-wpf-control-types"></a>WPF denetim türleri oluşturmak için  
  
1.  Yeni bir WPF eklemek <xref:System.Windows.Controls.UserControl> çözüme proje. Denetim türü için varsayılan adı kullanacak `UserControl1.xaml`. Daha fazla bilgi için bkz: [izlenecek yol: oluşturma yeni WPF içeriği Windows formlarında tasarım zamanında](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).  
  
2.  Tasarım görünümü içinde olduğundan emin olun `UserControl1` seçilir. Daha fazla bilgi için bkz: [nasıl yapılır: seçin ve tasarım yüzeyine taşıma öğelerde](http://msdn.microsoft.com/library/54cb70b6-b35b-46e4-a0cc-65189399c474).  
  
3.  İçinde **özellikleri** penceresindeki değerini ayarlayın <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> özelliklerine `200`.  
  
4.  Ekleme bir <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> denetimini <xref:System.Windows.Controls.UserControl> ve değeri ayarlayın <xref:System.Windows.Controls.TextBox.Text%2A> özelliğine **barındırılan içerik**.  
  
5.  İkinci bir WPF eklemek <xref:System.Windows.Controls.UserControl> projeye. Denetim türü için varsayılan adı kullanacak `UserControl2.xaml`.  
  
6.  İçinde **özellikleri** penceresindeki değerini ayarlayın <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> özelliklerine `200`.  
  
7.  Ekleme bir <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> denetimini <xref:System.Windows.Controls.UserControl> ve değeri ayarlayın <xref:System.Windows.Controls.TextBox.Text%2A> özelliğine **barındırılan içerik 2**.  
  
 **Not** genel olarak, daha karmaşık WPF içeriği barındırma. <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> Denetimi yalnızca tanım yalnızca amacıyla burada kullanılır.  
  
1.  Projeyi oluşturun.  
  
## <a name="selecting-wpf-controls"></a>WPF denetimleri seçme  
 Farklı WPF İçerik atayabileceğiniz bir <xref:System.Windows.Forms.Integration.ElementHost> içeriği zaten barındırma denetim.  
  
#### <a name="to-select-wpf-controls"></a>WPF denetimleri seçmek için  
  
1.  Açık `Form1` Windows Forms Tasarımcısı'nda.  
  
2.  İçinde **araç**, çift `UserControl1` bir örneğini oluşturmak için `UserControl1` form üzerinde.  
  
     Örneği `UserControl1` yeni bir barındırılan <xref:System.Windows.Forms.Integration.ElementHost> adlı Denetim `elementHost1`.  
  
3.  İçin akıllı etiket panelinde `elementHost1`, açık **barındırılan içerik Seç** aşağı açılan liste.  
  
4.  Seçin **UserControl 2** aşağı açılan liste kutusundan.  
  
     `elementHost1` Denetimi artık bir örneğini barındıran `UserControl2` türü.  
  
5.  İçinde **özellikleri** penceresinde onaylayın <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> özelliği ayarlanmış **UserControl 2**.  
  
6.  Gelen **araç**, **WPF birlikte çalışabilirliği** grubunda, sürükleyin bir <xref:System.Windows.Forms.Integration.ElementHost> forma denetim.  
  
     Yeni denetim için varsayılan ad `elementHost2`.  
  
7.  İçin akıllı etiket panelinde `elementHost2`, açık **barındırılan içerik Seç** aşağı açılan liste.  
  
8.  Seçin **UserControl1** aşağı açılan listeden.  
  
9. `elementHost2` Denetimi artık bir örneğini barındıran `UserControl1` türü.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [Geçiş ve Birlikte Çalışabilirlik](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)  
 [WPF Denetimlerini Kullanma](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)  
 [WPF Tasarımcısı](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)
