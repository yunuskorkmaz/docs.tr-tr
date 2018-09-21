---
title: 'Nasıl yapılır: Bileşik Denetimler Yazma'
ms.date: 03/30/2017
helpviewer_keywords:
- UserControl class [Windows Forms], creating composite controls
- user controls [Windows Forms], creating
- user controls [Windows Forms], inheriting from
- composite controls [Windows Forms], creating
ms.assetid: 79c9cf05-5ab6-4a18-886d-88a64748b098
ms.openlocfilehash: 7abdeae4d19ceb6425f85e3cdd28f565a03d7ea4
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/21/2018
ms.locfileid: "46537871"
---
# <a name="how-to-author-composite-controls"></a>Nasıl yapılır: Bileşik Denetimler Yazma
Bileşik denetimler, birçok bakımdan çalıştırılacağı. Bir Windows masaüstü uygulaması projesi bir parçası olarak bunları yazar ve bunları yalnızca projedeki formlarında kullanabilirsiniz. Veya bunları Windows Denetim Kitaplığı projesinde yazar, projenin bir derlemeye derlemek ve diğer projelerde denetimleri kullanın. Bile, bunları devralır ve bunları hızlı bir şekilde özel amaçlarla özelleştirmek için görsel devralma kullanın.  
  
> [!NOTE]
>  Web formlarında kullanmak üzere bileşik denetim yazma istiyorsanız [özel ASP.NET sunucu denetimleri geliştirme](https://msdn.microsoft.com/library/fbe26c16-cff4-4089-b3dd-877411f0c0ef).  
>   
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-author-a-composite-control"></a>Bileşik denetim yazma  
  
1.  Yeni bir **Windows uygulama** adlı proje `DemoControlHost`.  
  
2.  Üzerinde **proje** menüsünü tıklatın **kullanıcı denetimi Ekle**.  
  
3.  İçinde **Yeni Öğe Ekle** iletişim kutusu, sınıf dosyası (.vb veya .cs dosyası) bileşik denetime sahip olmasını istediğiniz adı verin.  
  
4.  Seçin **Ekle** bileşik denetim için sınıf dosyası oluşturmak için.  
  
5.  Ekleme denetimlerini **araç kutusu** bileşik denetim yüzeyine bırakın.  
  
6.  Olay yordamlar, bileşik denetim veya onun bağlı denetimler tarafından başlatılan olayları işlemek için kod yerleştirin.  
  
7.  Bileşik denetim için tasarımcı kapatın ve sorulduğunda dosyayı kaydedin.  
  
8.  Üzerinde **derleme** menüsünde tıklatın **Çözümü Derle**.  
  
     Sırada görünmesini özel denetimler için projenin derlenmesi **araç kutusu**.  
  
9. Kullanım **DemoControlHost** sekmesinde **araç kutusu** denetiminize örneklerini eklemek için `Form1`.  
  
### <a name="to-author-a-control-class-library"></a>Bir denetim sınıf kitaplığı oluşturmak için  
  
1.  Yeni bir **Windows Denetim Kitaplığı** proje.  
  
     Varsayılan olarak, projeyi bileşik denetim içerir.  
  
2.  Denetimleri ve yukarıdaki yordamda anlatıldığı gibi kodu ekleyin.  
  
3.  İstemediğiniz değiştirmek ve ayarlamak için sınıflar devralan bir denetim seçin **değiştiriciler** bu denetimin özellik **özel**.  
  
4.  DLL oluşturun.  
  
### <a name="to-inherit-from-a-composite-control-in-a-control-class-library"></a>Bileşik Denetim denetim Sınıf Kitaplığı'nda devralınacak  
  
1.  Üzerinde **dosya** menüsünde **Ekle** seçip **yeni proje** yeni bir **Windows uygulama** çözüme bir proje.  
  
2.  İçinde **Çözüm Gezgini**, sağ **başvuruları** yeni klasör projesini ve ardından **Başvuru Ekle** açmak için **Add Reference**iletişim kutusu.  
  
3.  Seçin **projeleri** sekmesini ve Denetim Kitaplığı projenize çift tıklayın.  
  
4.  Üzerinde **derleme** menüsünde tıklatın **Çözümü Derle**.  
  
5.  İçinde **Çözüm Gezgini**, Denetim Kitaplığı projenize sağ tıklayıp **Yeni Öğe Ekle** kısayol menüsünden.  
  
6.  Seçin **devralınan kullanıcı denetimi** şablondan **Yeni Öğe Ekle** iletişim kutusu.  
  
7.  İçinde **devralma Seçici** iletişim kutusunda, istediğiniz devralınacak denetimi çift tıklayın.  
  
     Yeni bir denetim projenize eklenir.  
  
8.  Yeni denetim için görsel tasarımcı açın ve ek bağlı denetimler ekleme.  
  
     Bileşik Denetim DLL dosyanız içinde öğesinden devralınan bağlı denetimler görebilir ve denetimlerin özelliklerini değiştirebilir, **değiştiriciler** özelliği **genel**. Denetimin özelliklerini değiştiremezsiniz, **değiştiriciler** özelliği **özel**.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İzlenecek yol: Visual Basic İle Bileşik Denetim Yazma](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-basic.md)  
 [İzlenecek yol: Visual C# İle Bileşik Denetim Yazma](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-csharp.md)  
 [İzlenecek yol: Visual Basic ile beraber Windows Forms Denetimi'nden Devralma](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic.md)  
 [İzlenecek yol: Visual C# ile beraber Windows Forms Denetimi'nden Devralma](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)  
 [Denetim Türü Önerileri](../../../../docs/framework/winforms/controls/control-type-recommendations.md)  
 [Nasıl yapılır: Windows Forms için Denetimler Yazma](../../../../docs/framework/winforms/controls/how-to-author-controls-for-windows-forms.md)  
 [Özel Denetim Çeşitleri](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)
