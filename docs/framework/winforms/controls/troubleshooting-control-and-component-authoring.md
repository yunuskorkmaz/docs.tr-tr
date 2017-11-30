---
title: "Denetim ve Bileşen Yazmada Sorun Giderme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3e027a5b60e066a8d38db530c37a394227f2e892
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="troubleshooting-control-and-component-authoring"></a>Denetim ve Bileşen Yazmada Sorun Giderme
Bu konu, bileşenleri ve denetimleri geliştirirken ortaya aşağıdaki ortak sorunları listeler. Daha fazla bilgi için bkz: [bileşenlerle programlama](http://msdn.microsoft.com/library/d4d4fcb4-e0b8-46b3-b679-7ee0026eb9e3).  
  
-   Denetim araç kutusuna eklenemiyor  
  
-   Windows Forms kullanıcı denetimi veya bileşeni hata ayıklaması yapılamıyor  
  
-   İki kez devralınan denetimi veya bileşeni olay tetiklenir  
  
-   Tasarım zamanı hata: "bileşeni oluşturulamadı '*bileşen adı*'"  
  
-   STAThreadAttribute  
  
-   Bileşen simgesi Araç Kutusu'nda görünmez  
  
## <a name="cannot-add-control-to-toolbox"></a>Denetim araç kutusuna eklenemiyor  
 Başka bir projede oluşturulan özel bir denetim veya bir üçüncü taraf denetimine eklemek isteyip istemediğinizi **araç**, bunu el ile yapmanız gerekir. Geçerli projenin denetimi veya bileşeni içeriyorsa, bu görüntülenmelidir **araç** otomatik olarak. Daha fazla bilgi için bkz: [izlenecek yol: araç kutusunu özel bileşenlerle'otomatik olarak doldurma](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md).  
  
#### <a name="to-add-a-control-to-the-toolbox"></a>Araç kutusu denetim eklemek için  
  
1.  Sağ **araç** ve kısayol menüsünden seçin **öğeleri Seç**.  
  
2.  İçinde **araç kutusu öğelerini Seç** iletişim kutusunda, bileşen ekleyin:  
  
    -   Bir .NET Framework bileşenini veya denetim eklemek istiyorsanız, **.NET Framework bileşenlerini** sekmesi.  
  
         – veya –  
  
    -   Bir COM bileşeni veya ActiveX denetimi eklemek istiyorsanız, **COM bileşenlerini** sekmesi.  
  
3.  İletişim kutusunda, Denetim listeleniyorsa, seçilir ve ardından onaylamak **Tamam**.  
  
     Denetim eklenir **araç**.  
  
4.  Denetim iletişim kutusunda listede yoksa, aşağıdakileri yapın:  
  
    1.  Tıklatın **Gözat** düğmesi.  
  
    2.  Denetim içeren .dll dosyasını içeren klasöre göz atın.  
  
    3.  .Dll dosyasını tıklatıp **açık**.  
  
         Denetim iletişim kutusunda görüntülenir.  
  
    4.  Denetim seçilir ve ardından onaylamak **Tamam**.  
  
         Denetim eklenen **araç**.  
  
## <a name="cannot-debug-the-windows-forms-user-control-or-component"></a>Windows Forms kullanıcı denetimi veya bileşeni hata ayıklaması yapılamıyor  
 Denetim türetilen varsa <xref:System.Windows.Forms.UserControl> sınıfı, çalışma zamanı davranışını test kapsayıcısı ile ayıklayabilirsiniz. Daha fazla bilgi için bkz: [nasıl yapılır: bir UserControl denetiminin çalışma zamanı davranışını sınama](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).  
  
 Diğer özel denetimleri ve bileşenleri tek başına projeleri değildir. Bir Windows Forms projesi gibi bir uygulama tarafından barındırılmalıdır. Bir denetimi veya bileşeni hata ayıklamak için bir Windows Forms projesine eklemeniz gerekir.  
  
#### <a name="to-debug-a-control-or-component"></a>Bir denetimi veya bileşeni hata ayıklamak için  
  
1.  Gelen **yapı** menüsünde tıklatın **yapı çözümü** çözümünüzü derlemek için.  
  
2.  Gelen **dosya** menüsünde seçin **Ekle**ve ardından **yeni proje** uygulamanız için bir test projesi eklemek için.  
  
3.  İçinde **Yeni Proje Ekle** Seç iletişim kutusu **Windows uygulaması** proje türü.  
  
4.  İçinde **Çözüm Gezgini**, sağ **başvuruları** yeni proje için düğüm. Kısayol menüsünde **Başvuru Ekle** denetimi veya bileşeni içeren projeyi bir başvuru eklemek için.  
  
5.  Test projesinde denetimi veya bileşeni örneği oluşturun. Bileşeniniz ise **araç**Tasarımcı yüzeyine sürükleyin ya da örneği aşağıdaki kod örneğinde gösterildiği gibi program aracılığıyla oluşturabilirsiniz.  
  
    ```vb  
    Dim Component1 As New MyNeatComponent()  
    ```  
  
    ```csharp  
    MyNeatComponent Component1 = new MyNeatComponent();  
    ```  
  
     Artık denetimi veya bileşeni zamanki ayıklayabilirsiniz.  
  
 Hata ayıklama hakkında daha fazla bilgi için bkz: [Visual Studio'da hata ayıklamayı](/visualstudio/debugger/debugging-in-visual-studio) ve [izlenecek yol: tasarım zamanında özel Windows Forms denetimleri hata ayıklama](../../../../docs/framework/winforms/controls/walkthrough-debugging-custom-windows-forms-controls-at-design-time.md).  
  
## <a name="event-is-raised-twice-in-inherited-control-or-component"></a>İki kez devralınan denetimi veya bileşeni olay tetiklenir  
 Bu yinelenen bir nedeniyle olasıdır `Handles` yan tümcesi. Daha fazla bilgi için bkz: [sorun giderme devralınmış olay işleyicileri Visual Basic'te](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md).  
  
## <a name="design-time-error-failed-to-create-component-component-name"></a>Tasarım zamanı hata: "başarısız bileşeni 'Bileşen adı' oluşturmak için"  
 Hiçbir parametre varsayılan bir oluşturucu bileşeni veya denetimi sağlamanız gerekir. Tasarım ortamında bileşeni veya denetimi örneğini oluşturduğunda, herhangi bir parametre için parametre almaz Oluşturucusu aşırı sağlamak denemez.  
  
## <a name="stathreadattribute"></a>STAThreadAttribute  
 <xref:System.STAThreadAttribute> Windows Forms tek iş parçacıklı model kullanan ortak dil çalışma zamanı (CLR) bildirir. Windows Forms uygulamanızın için bu öznitelik uygulamazsanız beklenmedik davranışlara karşılaşabilirsiniz `Main` yöntemi. Gibi denetimlerin için arka plan görüntüleri gibi görünmeyebilir <xref:System.Windows.Forms.ListView>. Bazı denetimler de doğru otomatik tamamlama ve sürükle ve bırak davranışı için bu öznitelik gerektirebilir.  
  
## <a name="component-icon-does-not-appear-in-toolbox"></a>Bileşen simgesi Araç Kutusu'nda görünmez  
 Kullandığınızda <xref:System.Drawing.ToolboxBitmapAttribute> özel bileşeni ile bir simge ilişkilendirmek için bit eşlem araç kutusunu otomatik olarak oluşturulur bileşenleri için görünmez. Bit eşlem görmek için denetimi kullanarak yeniden **araç kutusu öğelerini Seç** iletişim kutusu. Daha fazla bilgi için bkz: [nasıl yapılır: bir denetim için araç kutusu bit eşlemi sağlamak](../../../../docs/framework/winforms/controls/how-to-provide-a-toolbox-bitmap-for-a-control.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows Forms denetimleri geliştirme tasarım zamanında](../../../../docs/framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)  
 [İzlenecek yol: Araç kutusunu özel bileşenlerle otomatik olarak doldurma](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md)  
 [Nasıl yapılır: bir UserControl denetiminin çalışma zamanı davranışını sınama](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md)  
 [İzlenecek yol: Özel Windows hata ayıklama tasarım zamanında Forms denetimleri](../../../../docs/framework/winforms/controls/walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)  
 [Bileşen yazma](http://msdn.microsoft.com/library/4a5a5e49-0378-4a31-83bc-24da0f1a727d)  
 [Tasarım zamanı geliştirme sorunlarını giderme](http://msdn.microsoft.com/library/e048d08e-fa7c-4be8-b238-4abaa199a0a6)  
 [Bileşenleri ile programlama](http://msdn.microsoft.com/library/d4d4fcb4-e0b8-46b3-b679-7ee0026eb9e3)
