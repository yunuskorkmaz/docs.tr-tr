---
title: "İzlenecek yol: Bir ElementHost Denetimini Ayrı Windows Formlarına Kopyalama ve Yapıştırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms, content copying and pasting
- interoperability [WPF]
- ElementHost control [Windows Forms], copying and pasting at design time
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: 6e81bb13-577c-46c3-a1cf-8d15969fb83e
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 65882925c6fbe3e9b393b139a937bc9a1f95ed04
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-copying-and-pasting-an-elementhost-control-into-separate-windows-forms"></a>İzlenecek yol: Bir ElementHost Denetimini Ayrı Windows Formlarına Kopyalama ve Yapıştırma
Bu kılavuz bir Windows Presentation Foundation (WPF) denetimi bir Windows formundan kopyalama gösterilmektedir.  
  
 Bu kılavuzda, aşağıdaki görevleri gerçekleştirin:  
  
-   Projesi oluşturun.  
  
-   WPF denetimi kopyalayın.  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:  
  
-   [!INCLUDE[vs_dev11_long](../../../../includes/vs-dev11-long-md.md)].  
  
## <a name="creating-the-project"></a>Projeyi Oluşturma  
 Windows Forms projesi oluşturmak için ilk adımdır bakın.  
  
> [!NOTE]
>  WPF içeriği barındırma, yalnızca C# ve Visual Basic projeleri desteklenir.  
  
#### <a name="to-create-the-project"></a>Proje oluşturmak için  
  
-   Visual Basic veya Visual C# adlı yeni bir Windows Forms uygulaması projesi oluşturma `CopyElementHost`.  
  
## <a name="copying-a-wpf-control"></a>WPF denetimi kopyalama  
 Projeye bir WPF denetimi ekledikten sonra projeyi diğer formlara kopyalayabilirsiniz.  
  
#### <a name="to-copy-a-wpf-control"></a>WPF denetimi kopyalamak için  
  
1.  Yeni bir WPF eklemek <xref:System.Windows.Controls.UserControl> çözüme proje. Denetim türü için varsayılan adı kullanacak `UserControl1.xaml`. Daha fazla bilgi için bkz: [izlenecek yol: oluşturma yeni WPF içeriği Windows formlarında tasarım zamanında](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).  
  
2.  Projeyi oluşturun.  
  
3.  Açık `Form1` Windows Forms Tasarımcısı'nda.  
  
4.  Gelen **araç**, bir örneğini sürükleyin `UserControl1` forma.  
  
     Örneği `UserControl1` yeni bir barındırılan <xref:System.Windows.Forms.Integration.ElementHost> adlı Denetim `elementHost1`.  
  
5.  İle `elementHost1` seçili panoya kopyalamak için CTRL + C tuşlarına basın.  
  
6.  Yeni bir Windows Form projeye ekleyin. Form türü için varsayılan adı kullanacak `Form2`.  
  
7.  İle `Form2` bir kopyasını yapıştırmak için CTRL + V tuşlarına basın Windows Forms Tasarımcısı'nda açmak `elementHost1` forma.  
  
     Kopyalanan denetimi olarak da adlandırılır `elementHost1`, özel alanı olduğundan `Form2` sınıfı. Hiçbir ad çakışması olan yoktur `elementHost1` içinde `Form1` sınıfı.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [Geçiş ve birlikte çalışabilirlik](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)  
 [WPF denetimlerini kullanma](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)  
 [WPF Tasarımcısı](http://msdn.microsoft.com/en-us/c6c65214-8411-4e16-b254-163ed4099c26)
