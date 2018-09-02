---
title: 'Nasıl yapılır: Bir UserControl Denetiminin Çalışma Zamanı Davranışını Sınama'
ms.date: 03/30/2017
helpviewer_keywords:
- UserControl class [Windows Forms], testing
- user controls [Windows Forms], testing
- composite controls [Windows Forms], testing
- UserControl Test Container
- UserControl class [Windows Forms], run-time behavior
ms.assetid: 4e4d5c49-1346-40ac-9d96-40211b573583
ms.openlocfilehash: 40ec136a86b52dcb007d15d5a2917212745961f2
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43392910"
---
# <a name="how-to-test-the-run-time-behavior-of-a-usercontrol"></a>Nasıl yapılır: Bir UserControl Denetiminin Çalışma Zamanı Davranışını Sınama
Geliştirirken bir <xref:System.Windows.Forms.UserControl>, çalışma zamanı davranışını sınama gerekir. Ayrı Windows tabanlı uygulama projesi oluşturun ve test form üzerindeki denetiminizi yerleştirin, ancak bu zor bir işlemdir. Daha hızlı ve kolay bir yolu **UserControl Test kapsayıcısı** Visual Studio tarafından sağlanan. Bu test kapsayıcısında, doğrudan Windows Denetim Kitaplığı projenizden başlatır.  
  
> [!IMPORTANT]
>  Yüklemek test kapsayıcısı için <xref:System.Windows.Forms.UserControl>, denetimin en az bir ortak oluşturucuya sahip olmalıdır.  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
> [!NOTE]
>  Visual C++ denetimi kullanarak sınanamıyor **UserControl Test kapsayıcısı**.  
  
### <a name="to-test-the-run-time-behavior-of-a-usercontrol"></a>Bir UserControl denetiminin çalışma zamanı davranışını sınama  
  
1.  Adlı bir Windows Denetim Kitaplığı projesi oluşturun **TestContainerExample**. Ayrıntılar için bkz [Windows Denetim Kitaplığı şablonu](https://msdn.microsoft.com/library/722f4e2d-1310-4ed5-8f33-593337ab66b4).  
  
2.  İçinde **Windows Form Tasarımcısı**, sürükleyin bir <xref:System.Windows.Forms.Label> denetimi **araç kutusu** denetimin tasarım yüzeyine.  
  
3.  Projeyi derlemek ve çalıştırmak için F5 tuşuna basın **UserControl Test kapsayıcısı**. Test kapsayıcısı ile görünür, <xref:System.Windows.Forms.UserControl> içinde **Önizleme** bölmesi.  
  
4.  Seçin <xref:System.Windows.Forms.Control.BackColor%2A> görüntülenen özelliği <xref:System.Windows.Forms.PropertyGrid> denetim sağındaki **Önizleme** bölmesi. Değerine değiştirmek `ControlDark`. Denetim daha koyu bir renge dönüşür gözlemleyin. Diğer özellik değerleri değiştirmeyi deneyin ve denetim üzerindeki etkisini inceleyin.  
  
5.  Tıklayın **Dock dolgu kullanıcı denetimi** aşağıdaki onay kutularından **Önizleme** bölmesi. Denetim bölmesinde doldurmak için boyutlandırılır gözlemleyin. Test kapsayıcı yeniden boyutlandırma ve Denetim ile bölmesinde yeniden boyutlandırılır gözlemleyin.  
  
6.  Test kapsayıcısını kapatın.  
  
7.  Başka bir kullanıcı denetimine ekleme **TestContainerExample** proje. Ayrıntılar için bkz [NIB: nasıl yapılır: varolan bir proje öğeleri Ekle](https://msdn.microsoft.com/library/15f4cfb7-78ab-457f-9f14-099a25a6a2d3).  
  
8.  İçinde **Windows Form Tasarımcısı**, sürükleyin bir <xref:System.Windows.Forms.Button> denetimi **araç kutusu** denetimin tasarım yüzeyine.  
  
9. Projeyi oluşturmak ve test kapsayıcıyı çalıştırmak için F5 tuşuna basın.  
  
10. Tıklayın **kullanıcı denetimi seçin** <xref:System.Windows.Forms.ComboBox> iki kullanıcı denetimler arasında geçiş yapmak için.  
  
## <a name="testing-user-controls-from-another-project"></a>Kullanıcı denetimleri başka bir projeden test  
 Kullanıcı denetimleri diğer projelerden geçerli projenin test kapsayıcısında test edebilirsiniz.  
  
#### <a name="to-test-user-controls-from-another-project"></a>Kullanıcı denetimleri başka bir projeden test etmek için  
  
1.  Adlı bir Windows Denetim Kitaplığı projesi oluşturun **TestContainerExample2**. Ayrıntılar için bkz [Windows Denetim Kitaplığı şablonu](https://msdn.microsoft.com/library/722f4e2d-1310-4ed5-8f33-593337ab66b4).  
  
2.  İçinde **Windows Form Tasarımcısı**, sürükleyin bir <xref:System.Windows.Forms.RadioButton> denetimi **araç kutusu** denetimin tasarım yüzeyine.  
  
3.  Projeyi oluşturmak ve test kapsayıcıyı çalıştırmak için F5 tuşuna basın. Test kapsayıcısı ile görünür, <xref:System.Windows.Forms.UserControl> içinde **Önizleme** bölmesi.  
  
4.  Tıklayın **yük** düğmesi.  
  
5.  İçinde **açık** iletişim kutusunda, gitmek **TestContainerExample**önceki yordamda oluşturulan .dll,. Seçin **TestContainerExample**tıklayın ve .dll **açık** yük kullanıcı denetimleri için düğme  
  
6.  Kullanım **kullanıcı denetimi seçin** <xref:System.Windows.Forms.ComboBox> iki kullanıcı denetimlerini arasında geçiş yapmak için **TestContainerExample** proje.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.UserControl>  
 [Nasıl yapılır: Bileşik Denetimler Yazma](../../../../docs/framework/winforms/controls/how-to-author-composite-controls.md)  
 [İzlenecek yol: Visual Basic İle Bileşik Denetim Yazma](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-basic.md)  
 [İzlenecek yol: Visual C# İle Bileşik Denetim Yazma](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-csharp.md)  
 [Kullanıcı denetimi Tasarımcısı](https://msdn.microsoft.com/library/2abb9eec-ba32-45cb-b73d-8b52a8bd6bf1)
