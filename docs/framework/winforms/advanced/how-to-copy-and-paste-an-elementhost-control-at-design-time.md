---
title: 'Nasıl yapılır: Tasarım zamanında bir ElementHost denetimini yapıştırın'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, content copying and pasting
- interoperability [WPF]
- ElementHost control [Windows Forms], copying and pasting at design time
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: e570375d-2a68-44ba-b4f7-c781af2d20e8
ms.openlocfilehash: 203a01ef82554bf4104f3000c0821cceeafac9f7
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57710426"
---
# <a name="how-to-copy-and-paste-an-elementhost-control-at-design-time"></a>Nasıl yapılır: Tasarım zamanında bir ElementHost denetimini yapıştırın
Bu yordam Windows formunda bir Windows Presentation Foundation (WPF) denetimi kopyalamak nasıl gösterir.  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-copy-and-paste-an-elementhost-control-at-design-time"></a>Kopyalayıp tasarım zamanında bir ElementHost denetimini yapıştırmak için  
  
1.  Yeni bir WPF ekleme <xref:System.Windows.Controls.UserControl> Windows Forms projenize. Denetim türü için varsayılan adı kullanacak `UserControl1.xaml`. Daha fazla bilgi için [izlenecek yol: Yeni bir WPF içeriği Windows formlarında tasarım zamanında oluşturma](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).  
  
2.  İçinde **özellikleri** penceresinde değerini ayarlayın <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> özelliklerini `UserControl1` için `200`.  
  
3.  Değerini <xref:System.Windows.Controls.Control.Background%2A> özelliğini `Blue`.  
  
4.  Projeyi oluşturun.  
  
5.  Açık `Form1` Windows Forms Tasarımcısı'nda.  
  
6.  Gelen **araç kutusu**, örneği sürükleyin `UserControl1` forma.  
  
     Örneği `UserControl1` yeni bir barındırılan <xref:System.Windows.Forms.Integration.ElementHost> adlı Denetim `elementHost1`.  
  
7.  İle `elementHost1` seçili panoya kopyalamak için CTRL + C tuşlarına basın.  
  
8.  Kopyalanan denetimi forma yapıştırmak için CTRL + V tuşlarına basın.  
  
     Yeni bir <xref:System.Windows.Forms.Integration.ElementHost> adlı Denetim `elementHost2` form üzerinde oluşturulur.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Geçiş ve Birlikte Çalışabilirlik](../../wpf/advanced/migration-and-interoperability.md)
- [WPF Denetimlerini Kullanma](using-wpf-controls.md)
- [Visual Studio’da XAML tasarlama](/visualstudio/designers/designing-xaml-in-visual-studio)
