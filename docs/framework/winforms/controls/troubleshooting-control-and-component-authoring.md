---
title: Denetim ve Bileşen Yazmada Sorun Giderme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- troubleshooting components
- troubleshooting controls [Windows Forms]
- controls [Windows Forms], troubleshooting
- components [Windows Forms], troubleshooting
- Windows Forms controls, debugging
ms.assetid: e9c8c099-2271-4737-882f-50f336c7a55e
ms.openlocfilehash: caad6a76b52a970e133425c484602deb8801d252
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43670671"
---
# <a name="troubleshooting-control-and-component-authoring"></a>Denetim ve Bileşen Yazmada Sorun Giderme
Bu konu, bileşenlerin ve denetimlerin geliştirme ortaya çıkan aşağıdaki ortak sorunları listeler. Daha fazla bilgi için [bileşenler ile programlama](https://msdn.microsoft.com/library/d4d4fcb4-e0b8-46b3-b679-7ee0026eb9e3).  
  
-   Denetimi araç kutusuna eklenemiyor  
  
-   Windows Forms kullanıcı denetimi veya bileşen hataları ayıklanamıyor  
  
-   İki kez devralınan denetim veya bileşen olay tetiklenir  
  
-   Tasarım zamanı hata: "bileşeni oluşturulamadı. '*bileşen adı*'"  
  
-   STAThreadAttribute  
  
-   Bileşen simgesi Araç Kutusu'nda görünmez  
  
## <a name="cannot-add-control-to-toolbox"></a>Denetimi araç kutusuna eklenemiyor  
 Başka bir proje tarafından oluşturulan özel bir denetim veya üçüncü taraf denetime eklemek isteyip istemediğimi **araç kutusu**, bunu el ile yapmanız gerekir. Geçerli proje denetim veya bileşen içeriyorsa, içinde görünmelidir **araç kutusu** otomatik olarak. Daha fazla bilgi için [izlenecek yol: otomatik olarak, araç kutusunu özel bileşenlerle doldurma](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md).  
  
#### <a name="to-add-a-control-to-the-toolbox"></a>Araç kutusuna denetim ekleme  
  
1.  Sağ **araç kutusu** ve kısayol menüsünden seçin **öğelerini Seç**.  
  
2.  İçinde **araç kutusu öğelerini Seç** iletişim kutusunda, bileşen ekleyin:  
  
    -   Bir .NET Framework bileşeni veya denetimi eklemek istiyorsanız, tıklayın **.NET Framework bileşenlerini** sekmesi.  
  
         – veya –  
  
    -   Bir COM bileşeni ya da ActiveX denetiminden eklemek istiyorsanız, tıklayın **COM bileşenlerini** sekmesi.  
  
3.  Denetim iletişim kutusunda listede yoksa seçilir ve ardından onaylamak **Tamam**.  
  
     Denetim eklenir **araç kutusu**.  
  
4.  Denetim iletişim kutusunda listede yoksa, şunları yapın:  
  
    1.  Tıklayın **Gözat** düğmesi.  
  
    2.  Denetim içeren .dll dosyasını içeren klasöre göz atın.  
  
    3.  .Dll dosyasını seçin ve tıklayın **açık**.  
  
         Denetim iletişim kutusunda görüntülenir.  
  
    4.  Denetiminiz seçilir ve ardından onaylamak **Tamam**.  
  
         Denetim eklenir **araç kutusu**.  
  
## <a name="cannot-debug-the-windows-forms-user-control-or-component"></a>Windows Forms kullanıcı denetimi veya bileşen hataları ayıklanamıyor  
 Türetilen denetiminiz varsa <xref:System.Windows.Forms.UserControl> sınıfı, çalışma zamanı davranışını test kapsayıcısı ile hata ayıklaması yapabilirsiniz. Daha fazla bilgi için [nasıl yapılır: bir UserControl denetiminin çalışma zamanı davranışını sınama](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).  
  
 Diğer özel denetimleri ve bileşenleri tek başına projeleri değildir. Bir Windows Forms projesi gibi bir uygulama tarafından barındırılmalıdır. Bir denetim veya bileşen hatalarını ayıklamak için bir Windows Forms projesine eklemeniz gerekir.  
  
#### <a name="to-debug-a-control-or-component"></a>Bir denetim veya bileşen hatalarını ayıklamak için  
  
1.  Gelen **derleme** menüsünde tıklatın **Çözümü Derle** çözümünüzü derlemek için.  
  
2.  Gelen **dosya** menüsünde seçin **Ekle**, ardından **yeni proje** uygulamanız için bir test projesi eklemek için.  
  
3.  İçinde **Yeni Proje Ekle** Seç iletişim kutusu **Windows uygulama** proje türü için.  
  
4.  İçinde **Çözüm Gezgini**, sağ **başvuruları** yeni proje için düğüm. Kısayol menüsünde **Başvuru Ekle** denetim veya bileşen içeren projeye bir başvuru eklemek için.  
  
5.  Test projesinde bir denetim veya bileşen örneği oluşturun. Bileşeniniz ise **araç kutusu**, Tasarımcı yüzeyine sürükleyin veya örneği aşağıdaki kod örneğinde gösterildiği gibi program aracılığıyla oluşturabilirsiniz.  
  
    ```vb  
    Dim Component1 As New MyNeatComponent()  
    ```  
  
    ```csharp  
    MyNeatComponent Component1 = new MyNeatComponent();  
    ```  
  
     Artık denetim veya bileşen zamanki ayıklayabilirsiniz.  
  
 Hata ayıklama hakkında daha fazla bilgi için bkz. [Visual Studio'da hata ayıklama](/visualstudio/debugger/debugging-in-visual-studio) ve [izlenecek yol: tasarım zamanında özel Windows Forms denetimleri hata ayıklama](../../../../docs/framework/winforms/controls/walkthrough-debugging-custom-windows-forms-controls-at-design-time.md).  
  
## <a name="event-is-raised-twice-in-inherited-control-or-component"></a>İki kez devralınan denetim veya bileşen olay tetiklenir  
 Yinelenen nedeni büyük olasılıkla budur `Handles` yan tümcesi. Daha fazla bilgi için [sorun giderme devralınmış olay işleyicileri Visual Basic'te](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md).  
  
## <a name="design-time-error-failed-to-create-component-component-name"></a>Tasarım zamanı hata: "başarısız bileşen 'Bileşeni adı' oluşturmak için"  
 Varsayılan bir parametresiz oluşturucu bileşeni veya denetimi sağlamanız gerekir. Tasarım ortamı bileşeni veya denetimi örneğini oluşturduğunda, parametre alan bir oluşturucu aşırı yüklemeleri için herhangi bir parametre sağlamak denemez.  
  
## <a name="stathreadattribute"></a>STAThreadAttribute  
 <xref:System.STAThreadAttribute> Windows Forms tek kullanımlık apartman modeli kullanan ortak dil çalışma zamanı (CLR) bildirir. Bu öznitelik Windows Forms uygulamanızın için uygulamazsanız istenmeyen davranışı fark edebilirsiniz `Main` yöntemi. Gibi denetimlerin için arka plan görüntüleri gibi görünmeyebilir <xref:System.Windows.Forms.ListView>. Bazı denetimler de doğru otomatik tamamlama ve sürükle-bırak davranışı için bu öznitelik gerektirebilir.  
  
## <a name="component-icon-does-not-appear-in-toolbox"></a>Bileşen simgesi Araç Kutusu'nda görünmez  
 Kullanırken <xref:System.Drawing.ToolboxBitmapAttribute> özel bileşeniniz ile bir simge ilişkilendirmek için bit eşlem araç kutusunu otomatik olarak oluşturulan bileşenler için görünmez. Bit eşlem görmek için denetimi kullanarak yeniden **araç kutusu öğelerini Seç** iletişim kutusu. Daha fazla bilgi için [nasıl yapılır: bir denetim için araç kutusu bit eşlemi sağlama](../../../../docs/framework/winforms/controls/how-to-provide-a-toolbox-bitmap-for-a-control.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Tasarım Zamanında Windows Forms Denetimleri Geliştirme](../../../../docs/framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)  
 [İzlenecek yol: Araç Kutusunu Otomatik Olarak Özel Bileşenlerle Doldurma](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md)  
 [Nasıl yapılır: Bir UserControl Denetiminin Çalışma Zamanı Davranışını Sınama](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md)  
 [İzlenecek yol: Tasarım Zamanında Özel Windows Forms Denetimleri Hatalarını Ayıklama](../../../../docs/framework/winforms/controls/walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)  
 [Bileşen yazma](https://msdn.microsoft.com/library/4a5a5e49-0378-4a31-83bc-24da0f1a727d)  
 [Tasarım zamanı geliştirme sorunlarını giderme](https://msdn.microsoft.com/library/e048d08e-fa7c-4be8-b238-4abaa199a0a6)  
 [Bileşenler ile programlama](https://msdn.microsoft.com/library/d4d4fcb4-e0b8-46b3-b679-7ee0026eb9e3)
