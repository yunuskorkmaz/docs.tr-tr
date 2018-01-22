---
title: "İzlenecek yol: Tasarım Zamanında Barındırılan bir WPF Öğesinin Özelliklerini Değiştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WPF content [Windows Forms], changing properties at design time
- Windows Forms, changing properties of WPF content at design time
- WPF content [Windows Forms], hosting in Windows Forms
- interoperability [WPF]
ms.assetid: a1f7a90c-0bbb-4781-8c3c-8cc8bef2488d
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 46b80ee0c74da7371ac8f7a16d3430b5b753059d
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="walkthrough-changing-properties-of-a-hosted-wpf-element-at-design-time"></a>İzlenecek yol: Tasarım Zamanında Barındırılan bir WPF Öğesinin Özelliklerini Değiştirme
Bu kılavuz, bir Windows formunda barındırılan bir Windows Presentation Foundation (WPF) denetiminin özellik değerlerini değiştirmek nasıl gösterir.  
  
 Bu kılavuzda, aşağıdaki görevleri gerçekleştirin:  
  
-   Projesi oluşturun.  
  
-   WPF denetimi oluşturun.  
  
-   Bir Windows formunda WPF denetimleri barındırır.  
  
-   Visual Studio için WPF Tasarımcısı özellik değerlerini değiştirmek için kullanın.  
  
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
  
-   Visual Basic veya Visual C# adlı yeni bir Windows Forms uygulaması projesi oluşturma `WpfHost`.  
  
## <a name="creating-the-wpf-control"></a>WPF denetimi oluşturma  
 Projeye bir WPF denetimi ekledikten sonra formdaki düzenleyebilirsiniz.  
  
#### <a name="to-create-wpf-controls"></a>WPF denetimleri oluşturmak için  
  
1.  Yeni bir WPF eklemek <xref:System.Windows.Controls.UserControl> projeye. Denetim türü için varsayılan adı kullanacak `UserControl1.xaml`. Daha fazla bilgi için bkz: [izlenecek yol: oluşturma yeni WPF içeriği Windows formlarında tasarım zamanında](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).  
  
2.  İçinde **özellikleri** penceresindeki değerini ayarlayın <xref:System.Windows.Controls.Control.Background%2A> özelliğine `Blue`.  
  
3.  Projeyi oluşturun.  
  
## <a name="changing-property-values-on-the-wpf-control"></a>WPF denetimi özellik değerlerini değiştirme  
 <xref:System.Windows.Forms.Integration.ElementHost> Akıllı etiket kolaylaştırır barındırılan WPF özelliklerini değiştirmek içerik WPF Tasarımcısı kullanarak.  
  
#### <a name="to-host-a-wpf-control"></a>WPF denetimi barındırma  
  
1.  Açık `Form1` Windows Forms Tasarımcısı'nda.  
  
2.  İçinde **araç**, **WPF kullanıcı denetimi** sekmesinde, çift `UserControl1` bir örneğini oluşturmak için `UserControl1` form üzerinde.  
  
     Örneğinin `UserControl1` yeni bir barındırılan <xref:System.Windows.Forms.Integration.ElementHost> adlı Denetim `elementHost1`.  
  
3.  İçinde **ElementHost görevleri** akıllı etiket paneli, select **barındırılan içeriği Düzenle**.  
  
     WPF Tasarımcısı'nda da UserControl1.XAML'i açar.  
  
4.  İçinde **özellikleri** penceresindeki değerini ayarlayın <xref:System.Windows.Controls.Control.Background%2A> özelliğine `Red`.  
  
5.  Projeyi yeniden oluşturun.  
  
6.  Açık `Form1` Windows Forms Tasarımcısı'nda.  
  
     Örneğinin `UserControl1` kırmızı bir arka plana sahip.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [Nasıl yapılır: TableLayoutPanel Denetiminde Alt Denetimleri Sabitleme ve Yerleştirme](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)  
 [Nasıl yapılır: Tasarım Zamanında Denetimi Formların Kenarlarına Hizalama](../../../../docs/framework/winforms/controls/how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)  
 [İzlenecek yol: Dayama Çizgileri Kullanarak Windows Forms'da Denetimleri Düzenleme](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)  
 [Geçiş ve Birlikte Çalışabilirlik](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)  
 [WPF Denetimlerini Kullanma](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)  
 [WPF Tasarımcısı](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)
