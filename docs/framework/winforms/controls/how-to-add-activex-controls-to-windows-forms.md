---
title: "Nasıl yapılır: Windows Forms'a ActiveX denetimleri ekleme"
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls, ActiveX controls
- forms [Windows Forms], adding ActiveX controls
- ActiveX controls [Windows Forms], adding
ms.assetid: 54a61e5b-555e-4887-b41e-6244fed271eb
ms.openlocfilehash: 2fa5d81c196e1730eafb177b20b5cba64b2daae1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54721155"
---
# <a name="how-to-add-activex-controls-to-windows-forms"></a>Nasıl yapılır: Windows Forms'a ActiveX denetimleri ekleme
Windows Form Tasarımcısı ana bilgisayar Windows Forms denetimleri için iyileştirilmiştir, ancak Windows Forms ActiveX denetimleri de koyabilirsiniz.  
  
> [!CAUTION]
>  ActiveX denetimleri kendilerine eklenen zaman Windows Forms için performans sınırlamalar vardır.  
  
 ActiveX denetimleri formunuza eklemeden önce araç kutusuna eklemeniz gerekir. Daha fazla bilgi için [COM bileşenlerini, özelleştirme araç kutusu iletişim kutusunda](https://msdn.microsoft.com/library/171333f3-f207-4e02-bbdc-17862556212c).  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için tıklayın **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-add-an-activex-control-to-your-windows-form"></a>ActiveX denetimi Windows formunuza eklemek için  
  
-   Araç kutusu denetimi çift tıklatın.  
  
     Visual Studio denetim için tüm başvuruları projenize ekler. Windows Forms ActiveX denetimlerinde kullanırken göz önünde bulundurmanız gereken noktalar hakkında daha fazla bilgi için bkz. [bir Windows formunda bir ActiveX denetimi Barındırmayla ilgili konular](../../../../docs/framework/winforms/controls/considerations-when-hosting-an-activex-control-on-a-windows-form.md).  
  
    > [!NOTE]
    >  Windows Forms ActiveX denetim içeri Aktarıcı (AxImp.exe) ActiveX dinamik bağlantı kitaplıkları içeri aktarma sırasında beklenenden farklı türde olay bağımsız değişkenlerini oluşturur. AxImp.exe tarafından oluşturulan bağımsız değişkenleri aşağıdakine benzer: `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEvent e)`, `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEventArgs e)` beklenir. Bu tutarsızlığı kod normal çalışmasını engellemez olduğunu unutmayın. Ayrıntılar için bkz [Windows Forms ActiveX denetim içeri Aktarıcı (Aximp.exe)](../../../../docs/framework/tools/aximp-exe-windows-forms-activex-control-importer.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Windows Forms Denetimleri](../../../../docs/framework/winforms/controls/index.md)
- [Denetimler ve programlanabilir nesneler çeşitli dillerde ve kitaplıklarda karşılaştırılan](https://msdn.microsoft.com/library/021f2a1b-8247-4348-a5ad-e1d9ab23004b)
- [Nasıl yapılır: Windows Forms'a denetimler ekleme](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)
- [Windows Forms’da Denetimleri Düzenleme](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)
- [Ayrı Windows Forms Denetimlerini Etiketleme ve Kısayollarını Sunma](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [Windows Forms'da Kullanılacak Denetimler](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
- [İşleve Göre Windows Forms Denetimleri](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)
