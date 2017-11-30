---
title: "Nasıl yapılır: Windows Formlarına ActiveX Denetimleri Ekleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms controls, ActiveX controls
- forms [Windows Forms], adding ActiveX controls
- ActiveX controls [Windows Forms], adding
ms.assetid: 54a61e5b-555e-4887-b41e-6244fed271eb
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: afee07f2f5009abb6cf8facc94b138f4ea2a11fd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-activex-controls-to-windows-forms"></a>Nasıl yapılır: Windows Formlarına ActiveX Denetimleri Ekleme
Windows Form Tasarımcısı ana bilgisayar Windows Forms denetimleri için optimize edilmiş, ancak Windows Forms ActiveX denetimlerinde de yerleştirebilirsiniz.  
  
> [!CAUTION]
>  ActiveX denetimleri için eklendiğinde Windows Forms için performans sınırlamalar vardır.  
  
 ActiveX denetimleri formunuza eklemeden önce araç kutusu eklemeniz gerekir. Daha fazla bilgi için bkz: [COM bileşenlerini, özelleştirme araç iletişim kutusu](http://msdn.microsoft.com/en-us/171333f3-f207-4e02-bbdc-17862556212c).  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için tıklatın. **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-add-an-activex-control-to-your-windows-form"></a>ActiveX denetimi Windows formunuza eklemek için  
  
-   Araç kutusu denetimi çift tıklatın.  
  
     [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)]denetimin tüm başvuruları projenize ekler. Windows Forms ActiveX denetimlerinde kullanırken göz önünde bulundurmanız gerekenler hakkında daha fazla bilgi için bkz: [bir Windows formunda bir ActiveX denetimi Barındırmayla ilgili konular](../../../../docs/framework/winforms/controls/considerations-when-hosting-an-activex-control-on-a-windows-form.md).  
  
    > [!NOTE]
    >  Windows Forms ActiveX denetim içeri Aktarıcı (AxImp.exe) ActiveX dinamik bağlantı kitaplıkları içe aktarılmasını beklenenden farklı türde olay bağımsız oluşturur. AxImp.exe tarafından oluşturulan değişkenleri aşağıdakine benzer: `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEvent e)`, `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEventArgs e)` beklenir. Bu tutarsızlığı kod normal çalışmasını engellemez olduğunu unutmayın. Ayrıntılar için bkz [Windows Forms ActiveX denetim içeri Aktarıcı (Aximp.exe)](../../../../docs/framework/tools/aximp-exe-windows-forms-activex-control-importer.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows Forms denetimleri](../../../../docs/framework/winforms/controls/index.md)  
 [Denetimleri ve çeşitli diller ve kitaplıkları karşılaştırıldığında programlanabilir nesneleri](http://msdn.microsoft.com/en-us/021f2a1b-8247-4348-a5ad-e1d9ab23004b)  
 [Nasıl yapılır: Windows formlarına denetimler ekleme](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)  
 [Windows Forms'ta denetimleri düzenleme](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [Ayrı Windows Forms denetimlerini etiketleme ve kısayollarını sunma](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)  
 [Windows Forms'ta kullanılacak denetimler](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 [Windows Forms denetimleri işlevi](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)
