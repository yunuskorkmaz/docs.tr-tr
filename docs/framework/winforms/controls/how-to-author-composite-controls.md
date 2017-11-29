---
title: "Nasıl yapılır: Bileşik Denetimler Yazma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UserControl class [Windows Forms], creating composite controls
- user controls [Windows Forms], creating
- user controls [Windows Forms], inheriting from
- composite controls [Windows Forms], creating
ms.assetid: 79c9cf05-5ab6-4a18-886d-88a64748b098
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 72c68568f0178956d6154f0b3a070e69b6ff0502
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-author-composite-controls"></a>Nasıl yapılır: Bileşik Denetimler Yazma
Bileşik denetimler birçok yolla değişiklik. Windows masaüstü uygulaması projesi parçası olarak bunları yazar ve bunları yalnızca projesinde formlarda kullanabilirsiniz. Veya Windows Denetim Kitaplığı projede yazar, bir derlemeye Projeyi derlemek ve diğer projelerinde denetimleri kullanın. Bile, bunları devralır ve görsel devralma bunları hızlı bir şekilde özel amaçlarla özelleştirmek için kullanın.  
  
> [!NOTE]
>  Web Forms kullanmak için bkz: bileşik denetim yazma istiyorsanız [özel ASP.NET sunucu denetimleri geliştirme](http://msdn.microsoft.com/library/fbe26c16-cff4-4089-b3dd-877411f0c0ef).  
>   
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-author-a-composite-control"></a>Bileşik denetim yazma  
  
1.  Yeni bir **Windows uygulaması** adlı proje `DemoControlHost`.  
  
2.  Üzerinde **proje**menüsünde tıklatın **kullanıcı denetimi Ekle**.  
  
3.  İçinde **Yeni Öğe Ekle** iletişim kutusu, sınıf dosya (.vb veya .cs dosyası) için bileşik denetim istediğiniz adı verin.  
  
4.  Tıklatın **Ekle** bileşik denetim için sınıf dosyası oluşturmak için düğmesi.  
  
5.  Denetimleri ekleme **araç** bileşik denetim yüzeye.  
  
6.  Bileşik denetim veya onun bağlı denetimler tarafından başlatılan olayları işlemek için olay yordamları kodu yerleştirin.  
  
7.  Bileşik Denetim Tasarımcı kapatın ve sorulduğunda, dosyayı kaydedin.  
  
8.  Üzerinde **yapı** menüsünde tıklatın **yapı çözümü**.  
  
     Proje görünmesi özel denetimler için sırada oluşturulmalıdır **araç**.  
  
9. Kullanım **DemoControlHost** sekmesinde **araç** denetiminize örneklerini eklemek için `Form1`.  
  
### <a name="to-author-a-control-class-library"></a>Yazar denetim sınıf kitaplığı  
  
1.  Yeni bir **Windows Denetim Kitaplığı** projesi.  
  
     Varsayılan olarak, projeyi bileşik denetim içerir.  
  
2.  Denetimleri ve yukarıdaki yordamda açıklandığı şekilde kodu ekleyin.  
  
3.  İstemiyorsanız değiştirin ve ayarlamak için sınıflar devralan bir denetim seçin **değiştiricileri** bu denetimin özelliğini **özel**.  
  
4.  Dll dosyasını oluşturun.  
  
### <a name="to-inherit-from-a-composite-control-in-a-control-class-library"></a>Bir denetim Sınıf Kitaplığı'nda bileşik denetim devralmak için  
  
1.  Üzerinde **dosya** menüsündeki **Ekle** seçip **yeni proje** yeni eklemek için **Windows uygulaması** çözüme proje.  
  
2.  İçinde **Çözüm Gezgini**, sağ **başvuruları** yeni klasör proje ve seçin **Başvuru Ekle** açmak için **Başvuru Ekle**iletişim kutusu.  
  
3.  Seçin **projeleri** sekmesinde ve denetim kitaplığı projenizin çift tıklayın.  
  
4.  Üzerinde **yapı** menüsünde tıklatın **yapı çözümü**.  
  
5.  İçinde **Çözüm Gezgini**, Denetim kitaplığını projenize sağ tıklayın ve seçin **Yeni Öğe Ekle** kısayol menüsünden.  
  
6.  Seçin **devralınan kullanıcı denetimi** şablondan **Yeni Öğe Ekle** iletişim kutusu.  
  
7.  İçinde **devralma Seçici** iletişim kutusunda, istediğiniz devralmak için denetimi çift tıklatın.  
  
     Yeni bir denetim projenize eklenir.  
  
8.  Yeni denetim için görsel tasarımcı açın ve ek bağlı denetimler ekleyin.  
  
     DLL bileşik denetiminden devralındığını bağlı denetimler görebilir ve denetimlerin özelliklerini değiştirebilir, **değiştiricileri** özelliği **ortak**. Denetim özelliklerini değiştiremezsiniz, **değiştiricileri** özelliği **özel**.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İzlenecek yol: Visual Basic ile bileşik denetim yazma](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-basic.md)  
 [İzlenecek yol: Visual C# ile bileşik denetim yazma](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-csharp.md)  
 [İzlenecek yol: Visual Basic ile beraber Windows Forms Denetimi'nden devralma](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic.md)  
 [İzlenecek yol: Visual C# ile bir Windows Forms Denetimi'nden devralma](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)  
 [Denetim türü önerileri](../../../../docs/framework/winforms/controls/control-type-recommendations.md)  
 [Nasıl yapılır: Windows formları için denetimler yazma](../../../../docs/framework/winforms/controls/how-to-author-controls-for-windows-forms.md)  
 [Özel denetim çeşitleri](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)
