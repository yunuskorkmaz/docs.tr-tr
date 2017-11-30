---
title: "Nasıl yapılır: Bir UserControl Denetiminin Çalışma Zamanı Davranışını Sınama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UserControl class [Windows Forms], testing
- user controls [Windows Forms], testing
- composite controls [Windows Forms], testing
- UserControl Test Container
- UserControl class [Windows Forms], run-time behavior
ms.assetid: 4e4d5c49-1346-40ac-9d96-40211b573583
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2ce4f821a7b964b3ed2e03c795346b47bb88d618
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-test-the-run-time-behavior-of-a-usercontrol"></a>Nasıl yapılır: Bir UserControl Denetiminin Çalışma Zamanı Davranışını Sınama
Geliştirirken bir <xref:System.Windows.Forms.UserControl>, çalışma zamanı davranışını sınama gerekir. Ayrı Windows tabanlı uygulama projesi oluşturun ve test form üzerindeki denetiminizi yerleştirin, ancak bu yordam, kullanışsız kullanılır. Daha hızlı ve kolay bir yolu kullanmaktır **UserControl Test kapsayıcısı** Visual Studio tarafından sağlanan. Bu test kapsayıcısı doğrudan Windows Denetim Kitaplığı projenizden başlatır.  
  
> [!IMPORTANT]
>  Yüklemek test kapsayıcısı için <xref:System.Windows.Forms.UserControl>, Denetim en az bir public oluşturucuya sahip olmalıdır.  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
> [!NOTE]
>  Kullanarak bir Visual C++ denetimi sınanamıyor **UserControl Test kapsayıcısı**.  
  
### <a name="to-test-the-run-time-behavior-of-a-usercontrol"></a>Bir UserControl denetiminin çalışma zamanı davranışını sınamak için  
  
1.  Adlı Windows Denetim Kitaplığı projesi oluşturma **TestContainerExample**. Ayrıntılar için bkz [Windows Denetim Kitaplığı şablonu](http://msdn.microsoft.com/en-us/722f4e2d-1310-4ed5-8f33-593337ab66b4).  
  
2.  İçinde **Windows Form Tasarımcısı**, sürükleyin bir <xref:System.Windows.Forms.Label> gelen denetim **araç** denetimin tasarım yüzeyine.  
  
3.  Projeyi derlemek ve çalıştırmak için F5 tuşuna basın **UserControl Test kapsayıcısı**. Test kapsayıcısı olarak görünür, <xref:System.Windows.Forms.UserControl> içinde **Önizleme** bölmesi.  
  
4.  Seçin <xref:System.Windows.Forms.Control.BackColor%2A> görüntülenen özelliği <xref:System.Windows.Forms.PropertyGrid> sağındaki denetim **Önizleme** bölmesi. Değerine değiştirmek `ControlDark`. Denetim koyu renge dönüşür gözlemleyin. Diğer özellik değerleri değiştirmeyi deneyin ve denetiminizin üzerindeki etkisini gözlemleyin.  
  
5.  Tıklatın **yerleştirme doldurun kullanıcı denetimi** aşağıdaki onay kutusunu **Önizleme** bölmesi. Denetim bölmesinde doldurmak için boyutlandırılır gözlemleyin. Test kapsayıcısı yeniden boyutlandırma ve denetim bölmesiyle boyutlandırılır gözlemleyin.  
  
6.  Test kapsayıcısı kapatın.  
  
7.  Başka bir kullanıcı denetimi Ekle **TestContainerExample** projesi. Ayrıntılar için bkz [NIB: nasıl yapılır: varolan bir proje öğeleri Ekle](http://msdn.microsoft.com/en-us/15f4cfb7-78ab-457f-9f14-099a25a6a2d3).  
  
8.  İçinde **Windows Form Tasarımcısı**, sürükleyin bir <xref:System.Windows.Forms.Button> gelen denetim **araç** denetimin tasarım yüzeyine.  
  
9. Projeyi derlemek ve test kapsayıcısı çalıştırmak için F5 tuşuna basın.  
  
10. Tıklatın **kullanıcı denetimi seçin** <xref:System.Windows.Forms.ComboBox> iki kullanıcı denetimleri arasında geçiş yapmak için.  
  
## <a name="testing-user-controls-from-another-project"></a>Kullanıcı denetimleri başka bir projeden test etme  
 Kullanıcı denetimleri diğer projelerden geçerli projenizin test kapsayıcısında test edebilirsiniz.  
  
#### <a name="to-test-user-controls-from-another-project"></a>Test kullanıcısı için başka bir projeden denetler.  
  
1.  Adlı Windows Denetim Kitaplığı projesi oluşturma **TestContainerExample2**. Ayrıntılar için bkz [Windows Denetim Kitaplığı şablonu](http://msdn.microsoft.com/en-us/722f4e2d-1310-4ed5-8f33-593337ab66b4).  
  
2.  İçinde **Windows Form Tasarımcısı**, sürükleyin bir <xref:System.Windows.Forms.RadioButton> gelen denetim **araç** denetimin tasarım yüzeyine.  
  
3.  Projeyi derlemek ve test kapsayıcısı çalıştırmak için F5 tuşuna basın. Test kapsayıcısı olarak görünür, <xref:System.Windows.Forms.UserControl> içinde **Önizleme** bölmesi.  
  
4.  Tıklatın **yük** düğmesi.  
  
5.  İçinde **açık** iletişim kutusunda, gitmek **TestContainerExample**önceki yordamda oluşturduğunuz .dll. Seçin **TestContainerExample**.dll ve tıklatın **açık** kullanıcı denetimleri yüklemek için düğmeyi  
  
6.  Kullanım **kullanıcı denetimi seçin** <xref:System.Windows.Forms.ComboBox> iki kullanıcı denetimlerden arasında geçiş yapmak için **TestContainerExample** projesi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.UserControl>  
 [Nasıl yapılır: bileşik denetimler yazma](../../../../docs/framework/winforms/controls/how-to-author-composite-controls.md)  
 [İzlenecek yol: Visual Basic ile bileşik denetim yazma](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-basic.md)  
 [İzlenecek yol: Visual C# ile bileşik denetim yazma](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-csharp.md)  
 [Kullanıcı denetimi Tasarımcısı](http://msdn.microsoft.com/en-us/2abb9eec-ba32-45cb-b73d-8b52a8bd6bf1)
