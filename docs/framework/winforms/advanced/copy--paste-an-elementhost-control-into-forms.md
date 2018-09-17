---
title: 'İzlenecek yol: Bir ElementHost Denetimini Ayrı Windows Formlarına Kopyalama ve Yapıştırma'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, content copying and pasting
- interoperability [WPF]
- ElementHost control [Windows Forms], copying and pasting at design time
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: 6e81bb13-577c-46c3-a1cf-8d15969fb83e
ms.openlocfilehash: 55b426fbe95bac269183a649ecd839175a8cbdda
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45964104"
---
# <a name="walkthrough-copying-and-pasting-an-elementhost-control-into-separate-windows-forms"></a>İzlenecek yol: Bir ElementHost Denetimini Ayrı Windows Formlarına Kopyalama ve Yapıştırma
Bu izlenecek yol, bir Windows formdan başka bir Windows Presentation Foundation (WPF) denetimi kopyalamak nasıl gösterir.  
  
 Bu kılavuzda, aşağıdaki görevleri gerçekleştirin:  
  
-   Projeyi oluşturun.  
  
-   Bir WPF denetiminde kopyalayın.  
  
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
  
-   Visual Basic veya Visual C# adlı yeni bir Windows Forms uygulaması projesi oluşturma `CopyElementHost`.  
  
## <a name="copying-a-wpf-control"></a>Bir WPF denetiminde kopyalama  
 Bir WPF denetiminde projeye ekledikten sonra projedeki diğer formlara kopyalayabilirsiniz.  
  
#### <a name="to-copy-a-wpf-control"></a>Bir WPF denetiminde kopyalamak için  
  
1.  Yeni bir WPF ekleme <xref:System.Windows.Controls.UserControl> çözüme bir proje. Denetim türü için varsayılan adı kullanacak `UserControl1.xaml`. Daha fazla bilgi için [izlenecek yol: oluşturma yeni WPF içeriği Windows Forms'ta tasarım zamanında](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).  
  
2.  Projeyi oluşturun.  
  
3.  Açık `Form1` Windows Forms Tasarımcısı'nda.  
  
4.  Gelen **araç kutusu**, örneği sürükleyin `UserControl1` forma.  
  
     Örneği `UserControl1` yeni bir barındırılan <xref:System.Windows.Forms.Integration.ElementHost> adlı Denetim `elementHost1`.  
  
5.  İle `elementHost1` seçili panoya kopyalamak için CTRL + C tuşlarına basın.  
  
6.  Projeye yeni bir Windows formu ekleyin. Form türü için varsayılan adı kullanacak `Form2`.  
  
7.  İle `Form2` Windows Form Tasarımcısı'nda bir kopyasını yapıştırmak için CTRL + V tuşlarına basarak açın `elementHost1` forma.  
  
     Kopyalanan denetimi olarak da adlandırılır `elementHost1`, özel bir alan olduğundan `Form2` sınıfı. İle hiçbir ad çakışması var. `elementHost1` içinde `Form1` sınıfı.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [Geçiş ve Birlikte Çalışabilirlik](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)  
 [WPF Denetimlerini Kullanma](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)  
 [Visual Studio’da XAML tasarlama](/visualstudio/designers/designing-xaml-in-visual-studio)
