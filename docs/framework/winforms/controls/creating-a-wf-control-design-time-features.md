---
title: 'İzlenecek yol: Visual Studio tasarım zamanı özelliklerinden faydalanan Windows Forms denetimi oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms controls, creating
- design-time functionality [Windows Forms], Windows Forms
- DocumentDesigner class [Windows Forms]
- walkthroughs [Windows Forms], controls
ms.assetid: 6f487c59-cb38-4afa-ad2e-95edacb1d626
ms.openlocfilehash: 8c5ab9ac832ebf98584273bb8c4a7de12b3b8085
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54595285"
---
# <a name="walkthrough-creating-a-windows-forms-control-that-takes-advantage-of-visual-studio-design-time-features"></a>İzlenecek yol: Visual Studio tasarım zamanı özelliklerinden faydalanan Windows Forms denetimi oluşturma
Özel denetim için tasarım zamanı deneyimi, ilişkili bir özel Tasarımcı yazma tarafından geliştirilebilir.  
  
 Bu izlenecek yol, özel bir denetim için özel bir tasarımcı oluşturma işlemini gösterir. Uygulamadan bir `MarqueeControl` türü ve adlı bir ilişkili bir tasarımcı sınıfını `MarqueeControlRootDesigner`.  
  
 `MarqueeControl` Tür tiyatro kayan animasyonlu ışıkları ve yanıp sönen metin ile benzer bir ekran uygular.  
  
 Bu denetim için tasarımcı, bir özel tasarım zamanı deneyimi sağlamak için tasarım ortamı ile etkileşime girer. Özel tasarımcı ile özel bir araya `MarqueeControl` uygulamasıyla animasyonlu ışıkları ve birçok birleşimleri yanıp sönen metni. Herhangi bir Windows Forms denetimi gibi bir form üzerinde oluşturulmuş denetimini kullanabilirsiniz.  
  
 Bu kılavuzda gösterilen görevler aşağıdakileri içerir:  
  
-   Projeyi Oluşturma  
  
-   Bir denetim kitaplığı projesi oluşturma  
  
-   Özel denetim projesine başvurma  
  
-   Özel bir denetim ve özel iş Tasarımcısı tanımlama  
  
-   Özel denetim örneği oluşturma  
  
-   Tasarım zamanı hata ayıklama için projeyi ayarlama  
  
-   Özel denetiminizi uygulama  
  
-   Özel denetim için bir alt denetimi oluşturma  
  
-   MarqueeBorder alt denetimi oluşturma  
  
-   Özel bir tasarımcı gölge ve filtre özellikleri oluşturma  
  
-   Bileşen değişiklikleri işleme  
  
-   Tasarımcı fiilleri özel Tasarımcınıza ekleme  
  
-   Özel UITypeEditor oluşturma  
  
-   Özel Denetim Tasarımcısı'nda test etme  
  
 İşlemi tamamladığınızda, özel denetiminizi aşağıdaki gibi görünür:  
  
 ![Olası MarqueeControl yerleşimi](../../../../docs/framework/winforms/controls/media/demomarqueecontrol.gif "DemoMarqueeControl")  
  
 Tam kod listesi için bkz: [nasıl yapılır: Tasarım zamanı özelliklerinden faydalanan Windows Forms denetimi oluşturma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/307hck25(v=vs.120)).  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolu tamamlamak için şunlar gerekir:  
  
-   Oluşturma ve Windows Forms application projesi Visual Studio'nun yüklü bilgisayarda çalıştırmak için yeterli izinleri yok.  
  
## <a name="creating-the-project"></a>Projeyi Oluşturma  
 İlk adım, uygulama projesi oluşturmaktır. Bu proje, özel denetimin barındıran uygulaması oluşturmak için kullanır.  
  
#### <a name="to-create-the-project"></a>Proje oluşturmak için  
  
-   "MarqueeControlTest" adlı bir Windows Forms uygulaması projesi oluşturun (**dosya** > **yeni** > **proje**  >   **Visual C#** veya **Visual Basic** > **Klasik Masaüstü** > **Windows Forms uygulamalarındaki**).  
  
## <a name="creating-a-control-library-project"></a>Bir denetim kitaplığı projesi oluşturma  
 Sonraki adım, denetim kitaplığı projesi oluşturmaktır. Yeni özel denetim ve karşılık gelen kendi özel Tasarımcısı oluşturacaksınız.  
  
#### <a name="to-create-the-control-library-project"></a>Denetim Kitaplığı projesini oluşturmak için  
  
1.  Bir Windows Forms Denetim Kitaplığı projesi çözüme ekleyin. "MarqueeControlLibrary." proje adı  
  
2.  Kullanarak **Çözüm Gezgini**, istediğiniz dilde bağlı olarak "UserControl1.cs" veya "UserControl1.vb" adlı kaynak dosyası silerek projenin varsayılan denetimini silin. Daha fazla bilgi için [nasıl yapılır: , Silme, kaldırmak ve öğeleri hariç](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/0ebzhwsk(v=vs.100)).  
  
3.  Yeni bir <xref:System.Windows.Forms.UserControl> öğesinin `MarqueeControlLibrary` proje. Yeni kaynak dosyası bir temel "MarqueeControl." adını verin  
  
4.  Kullanarak **Çözüm Gezgini**, yeni bir klasör oluşturun `MarqueeControlLibrary` proje. Daha fazla bilgi için [nasıl yapılır: Yeni proje öğeleri ekleme](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w0572c5b(v=vs.100)). Yeni klasörü "Tasarım" olarak adlandırın.  
  
5.  Sağ **tasarım** klasör ve bir yeni sınıf ekleyin. Kaynak dosyanın temel adı "MarqueeControlRootDesigner." verin  
  
6.  İhtiyacınız olacak System.Design derlemesinden türleri kullanın, böylece bu referansı eklemek `MarqueeControlLibrary` proje.  
  
    > [!NOTE]
    >  System.Design derleme kullanmak için projenizi değil .NET Framework istemci profili .NET Framework'ün tam sürümünü hedeflemesi gerekir. Hedef Framework'ü değiştirmek için bkz: [nasıl yapılır: .NET Framework sürümü hedefleme](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework).  
  
## <a name="referencing-the-custom-control-project"></a>Özel denetim projesine başvurma  
 Kullanacağınız `MarqueeControlTest` özel denetim test etmek için proje. Bir proje başvurusu eklediğinizde, test projesi özel kontrolünü farkına varır `MarqueeControlLibrary` derleme.  
  
#### <a name="to-reference-the-custom-control-project"></a>Özel denetim projesine başvuruda bulunmak için  
  
-   İçinde `MarqueeControlTest` projesi, bir proje başvurusu Ekle `MarqueeControlLibrary` derleme. Kullandığınızdan emin olun **projeleri** sekmesinde **Başvuru Ekle** başvuran yerine iletişim kutusu `MarqueeControlLibrary` doğrudan derleme.  
  
## <a name="defining-a-custom-control-and-its-custom-designer"></a>Özel bir denetim ve özel iş Tasarımcısı tanımlama  
 Öğesinden türetilen özel denetiminizi <xref:System.Windows.Forms.UserControl> sınıfı. Bu diğer denetimleri içeren denetim sağlar ve denetiminizi varsayılan işlevsellik harika bir fırsat sağlar.  
  
 Özel denetim, ilişkili bir özel Tasarımcı sahip olur. Bu özel denetim için özel olarak uyarlanmış bir benzersiz tasarım deneyimi oluşturmanıza olanak sağlar.  
  
 Denetim kullanarak kendi Tasarımcısı ile ilişkilendirebileceğiniz <xref:System.ComponentModel.DesignerAttribute> sınıfı. Özel denetiminizi tüm tasarım zamanı davranışını geliştiriyorsunuz çünkü özel Tasarımcı uygulayacak <xref:System.ComponentModel.Design.IRootDesigner> arabirimi.  
  
#### <a name="to-define-a-custom-control-and-its-custom-designer"></a>Özel bir denetim ve özel iş Tasarımcısı tanımlamak için  
  
1.  Açık `MarqueeControl` kaynak dosyada **Kod Düzenleyicisi**. Dosyasının en üstüne aşağıdaki ad alanlarını içeri aktarın:  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#220](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#220)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#220](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#220)]  
  
2.  Ekleme <xref:System.ComponentModel.DesignerAttribute> için `MarqueeControl` sınıfının bildirimi. Bu özel denetimi iş Tasarımcısı ile ilişkilendirir.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#240](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#240)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#240](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#240)]  
  
3.  Açık `MarqueeControlRootDesigner` kaynak dosyada **Kod Düzenleyicisi**. Dosyasının en üstüne aşağıdaki ad alanlarını içeri aktarın:  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#520](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#520)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#520](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#520)]  
  
4.  Bildirimini değiştirmek `MarqueeControlRootDesigner` devralınacak <xref:System.Windows.Forms.Design.DocumentDesigner> sınıfı. Uygulama <xref:System.ComponentModel.ToolboxItemFilterAttribute> Tasarımcı etkileşimi belirtmek için **araç kutusu**.  
  
     **Not** tanımı `MarqueeControlRootDesigner` sınıfı, "MarqueeControlLibrary.Design." adlı bir ad alanında alınmış Bu bildirim Tasarımcısı tasarım ilgili türler için ayrılmış, özel bir isim uzayında yerleştirir.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#530](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#530)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#530](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#530)]  
  
5.  Tanımlamak için oluşturucu `MarqueeControlRootDesigner` sınıfı. INSERT bir <xref:System.Diagnostics.Trace.WriteLine%2A> Oluşturucu gövdesinde deyimi. Bu, hata ayıklama amacıyla yararlı olacaktır.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#540](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#540)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#540](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#540)]  
  
## <a name="creating-an-instance-of-your-custom-control"></a>Özel denetim örneği oluşturma  
 Özel tasarım zamanı davranışını gözlemlemek için denetiminizi biçiminde örneğini yerleştireceğiniz `MarqueeControlTest` proje.  
  
#### <a name="to-create-an-instance-of-your-custom-control"></a>Özel denetim örneği oluşturmak için  
  
1.  Yeni bir <xref:System.Windows.Forms.UserControl> öğesinin `MarqueeControlTest` proje. Yeni kaynak dosyası bir temel "DemoMarqueeControl." adını verin  
  
2.  Açık `DemoMarqueeControl` dosyası **Kod Düzenleyicisi**. İçeri aktarma dosyasının en üstüne `MarqueeControlLibrary` ad alanı:  
  
```vb  
Imports MarqueeControlLibrary  
```  
  
```csharp  
using MarqueeControlLibrary;  
```  
  
1.  Bildirimini değiştirmek `DemoMarqueeControl` devralınacak `MarqueeControl` sınıfı.  
  
2.  Projeyi oluşturun.  
  
3.  Açık `Form1` Windows Forms Tasarımcısı'nda.  
  
4.  Bulma **MarqueeControlTest bileşenleri** sekmesinde **araç kutusu** ve açın. Sürükleme bir `DemoMarqueeControl` gelen **araç kutusu** formunuza.  
  
5.  Projeyi oluşturun.  
  
## <a name="setting-up-the-project-for-design-time-debugging"></a>Tasarım zamanı hata ayıklama için projeyi ayarlama  
 Özel bir tasarım zamanı deneyimi geliştirirken, denetimleri ve bileşenleri hata ayıklamak gerekli olacaktır. Projenizi tasarım zamanında hata ayıklamaya izin verecek şekilde ayarlamak için basit bir yolu yoktur. Daha fazla bilgi için [izlenecek yol: Tasarım zamanında Forms denetimleri özel Windows hata ayıklama](../../../../docs/framework/winforms/controls/walkthrough-debugging-custom-windows-forms-controls-at-design-time.md).  
  
#### <a name="to-set-up-the-project-for-design-time-debugging"></a>Tasarım zamanı hata ayıklama için projeyi ayarlamak için  
  
1.  Sağ `MarqueeControlLibrary` seçin ve proje **özellikleri**.  
  
2.  "MarqueeControlLibrary özellik sayfaları" iletişim kutusunda **hata ayıklama** sayfası.  
  
3.  İçinde **başlatma eylemi** bölümünden **harici Program Başlat**. Artık Visual Studio, ayrı bir örneğini hata ayıklama şekilde üç nokta simgesine tıklayın (![VisualStudioEllipsesButton ekran](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) Visual Studio IDE için Gözat düğmesini. Devenv.exe yürütülebilir dosya adıdır ve varsayılan bir konuma yüklediyseniz, %programfiles%\Microsoft Visual Studio 9.0\Common7\IDE\devenv.exe yoludur.  
  
4.  İletişim kutusunu kapatmak için Tamam'a tıklayın.  
  
5.  Sağ `MarqueeControlLibrary` proje ve "Başlangıç projesi olarak ayarla bu hata ayıklama yapılandırmasını etkinleştirmek için"'i seçin.  
  
## <a name="checkpoint"></a>Checkpoint  
 Özel denetiminizi tasarım zamanı davranışını hata ayıklamak artık hazırsınız. Hata ayıklama ortamında doğru şekilde ayarlandığını belirledikten sonra özel denetimin özel Tasarımcı arasındaki ilişkiyi test eder.  
  
#### <a name="to-test-the-debugging-environment-and-the-designer-association"></a>Hata ayıklama ortamını ve tasarımcı ilişkilendirme test etmek için  
  
1.  Açık `MarqueeControlRootDesigner` kaynak dosyada **Kod Düzenleyicisi** ve bir kesme noktası yerleştirmek <xref:System.Diagnostics.Trace.WriteLine%2A> deyimi.  
  
2.  Hata ayıklama oturumu başlatmak için F5 tuşuna basın. Visual Studio'nun yeni bir örneğini oluşturulduğunu unutmayın.  
  
3.  Visual Studio'nun yeni örneğini "MarqueeControlTest" çözümü açın. Çözüm seçerek kolayca bulabilirsiniz **son projeler** gelen **dosya** menüsü. En son dosya kullanılan "MarqueeControlTest.sln" Çözüm dosyası listelenir.  
  
4.  Açık `DemoMarqueeControl` Tasarımcısı'nda. Visual Studio hata ayıklama örneğindeki odağı alır ve yürütmeyi, kesme noktasında durur unutmayın. Hata ayıklama oturumu devam etmek için F5 tuşuna basın.  
  
 Bu noktada, gereken her şey, geliştirme ve özel denetiminizi ve onun ilişkili özel Tasarımcı hata ayıklama vardır. Bu kılavuzda kalan denetim ve tasarımcı özelliklerini uygulama konusunda ayrıntılı bilgi odaklanacaktır.  
  
## <a name="implementing-your-custom-control"></a>Özel denetiminizi uygulama  
 `MarqueeControl` Olduğu bir <xref:System.Windows.Forms.UserControl> ufak bir özelleştirme. İki yöntem sunar: `Start`, kayan animasyon başlar ve `Stop`, animasyon durdurur. Çünkü `MarqueeControl` uygulayan alt denetimler de içerir `IMarqueeWidget` arabirimi `Start` ve `Stop` her bir alt denetimin ve çağrı listeleme `StartMarquee` ve `StopMarquee` yöntemleri, sırasıyla her alt denetimi hakkında uygulayan `IMarqueeWidget`.  
  
 Görünümünü `MarqueeBorder` ve `MarqueeText` denetimleri düzen, bağımlı şekilde `MarqueeControl` geçersiz kılmalar <xref:System.Windows.Forms.Control.OnLayout%2A> yöntemi ve çağrıları <xref:System.Windows.Forms.Control.PerformLayout%2A> alt denetimleri bu tür.  
  
 Bu kapsamı, `MarqueeControl` özelleştirmeler. Çalışma zamanı özellikleri tarafından uygulanan `MarqueeBorder` ve `MarqueeText` denetimleri ve tasarım-zamanı özellikleri tarafından uygulanır `MarqueeBorderDesigner` ve `MarqueeControlRootDesigner` sınıfları.  
  
#### <a name="to-implement-your-custom-control"></a>Özel denetim uygulamak için  
  
1.  Açık `MarqueeControl` kaynak dosyada **Kod Düzenleyicisi**. Uygulama `Start` ve `Stop` yöntemleri.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#260](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#260)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#260](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#260)]  
  
2.  Geçersiz kılma <xref:System.Windows.Forms.Control.OnLayout%2A> yöntemi.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#270](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#270)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#270](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#270)]  
  
## <a name="creating-a-child-control-for-your-custom-control"></a>Özel denetim için bir alt denetimi oluşturma  
 `MarqueeControl` İki tür alt denetimin barındıracak: `MarqueeBorder` denetimi ve `MarqueeText` denetimi.  
  
-   `MarqueeBorder`: Bu denetimi "ışıkları" kendi köşelerindeki kenarlığın boyar. Kenarlık taşıma olması görünmesini ışıkları sırayla flash. Başlangıçtan ışıkları flash hızlı adlı bir özellik tarafından denetlenir `UpdatePeriod`. Diğer özel bazı özellikleri denetimin görünümünü diğer yönlerini belirler. Adlı iki yöntem `StartMarquee` ve `StopMarquee`, animasyon zaman başlatır ve durdurur denetim.  
  
-   `MarqueeText`: Bu denetim, yanıp sönen bir dize boyar. Gibi `MarqueeBorder` denetimi, metin yanıp hızı tarafından denetlenir `UpdatePeriod` özelliği. `MarqueeText` Denetimi de sahip `StartMarquee` ve `StopMarquee` yöntemleri common ile `MarqueeBorder` denetimi.  
  
 Tasarım zamanında `MarqueeControlRootDesigner` eklenmesi bu iki denetim türlerini sağlar bir `MarqueeControl` herhangi bir birleşimini.  
  
 İki denetimin ortak özelliklerini adlı bir arabirim factored `IMarqueeWidget`. Böylece `MarqueeControl` tüm kayan ilgili alt denetimler bulmak ve onlara özel olarak değerlendirilmesi için.  
  
 Dönemsel animasyon özelliği uygulamak için kullanacağınız <xref:System.ComponentModel.BackgroundWorker> nesnelerin <xref:System.ComponentModel?displayProperty=nameWithType> ad alanı. Kullanabileceğinizi <xref:System.Windows.Forms.Timer> nesneleri, ne zaman ancak birçok `IMarqueeWidget` nesneleri, tek kullanıcı Arabirimi iş parçacığı ile animasyon yetişemiyor olabilir.  
  
#### <a name="to-create-a-child-control-for-your-custom-control"></a>Özel denetim için bir alt denetimin oluşturmak için  
  
1.  Yeni bir sınıf öğe ekleme `MarqueeControlLibrary` proje. Yeni kaynak dosyası bir temel "IMarqueeWidget." adını verin  
  
2.  Açık `IMarqueeWidget` kaynak dosyada **Kod Düzenleyicisi** bildirimden değiştirip `class` için `interface`:  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/imarqueewidget.cs#2)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/imarqueewidget.vb#2)]  
  
3.  Aşağıdaki kodu ekleyin `IMarqueeWidget` arabirimi iki yöntem ve kayan animasyon işleme bir özelliği göstermek için:  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/imarqueewidget.cs#3)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/imarqueewidget.vb#3)]  
  
4.  Yeni bir **özel denetim** öğesinin `MarqueeControlLibrary` proje. Yeni kaynak dosyası bir temel "MarqueeText." adını verin  
  
5.  Sürükleme bir <xref:System.ComponentModel.BackgroundWorker> bileşenini **araç kutusu** üzerine, `MarqueeText` denetimi. Bu bileşen sağlayacak `MarqueeText` kendisini zaman uyumsuz olarak güncelleştirmek için denetimi.  
  
6.  Özellikler penceresinde ayarlayın <xref:System.ComponentModel.BackgroundWorker> bileşenin `WorkerReportsProgess` ve <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> özelliklerine `true`. Bu ayarlar sağlar. <xref:System.ComponentModel.BackgroundWorker> düzenli aralıklarla yükseltmek için bileşen <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> olay ve zaman uyumsuz güncelleştirmeleri iptal etmek için. Daha fazla bilgi için [BackgroundWorker bileşeni](../../../../docs/framework/winforms/controls/backgroundworker-component.md).  
  
7.  Açık `MarqueeText` kaynak dosyada **Kod Düzenleyicisi**. Dosyasının en üstüne aşağıdaki ad alanlarını içeri aktarın:  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#120](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#120)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#120](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#120)]  
  
8.  Bildirimini değiştirmek `MarqueeText` devralınacak <xref:System.Windows.Forms.Label> ve uygulamak için `IMarqueeWidget` arabirimi:  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#130](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#130)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#130](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#130)]  
  
9. Kullanıma sunulan özelliklere karşılık gelen örnek değişkenleri tanımlayın ve bunları oluşturucuda başlatmak. `isLit` Alanı, metin rengi tarafından verilen boyanacak olup olmadığını belirler `LightColor` özelliği.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#140](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#140)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#140](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#140)]  
  
10. `IMarqueeWidget` arabirimini gerçekleştirin.  
  
     `StartMarquee` Ve `StopMarquee` yöntemleri çağırma <xref:System.ComponentModel.BackgroundWorker> bileşenin <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> ve <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> yöntemleri animasyon durdurmak ve başlatmak.  
  
     <xref:System.ComponentModel.CategoryAttribute.Category%2A> Ve <xref:System.ComponentModel.BrowsableAttribute.Browsable%2A> öznitelikler uygulanır `UpdatePeriod` Özellikler penceresinin "Çerçevesi." adlı özel bir bölümde görüntülenecek şekilde özelliği  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#150](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#150)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#150](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#150)]  
  
11. Özellik erişimcisi uygulayın. İstemciler için iki özellik açığa çıkarır: `LightColor` ve `DarkColor`. <xref:System.ComponentModel.CategoryAttribute.Category%2A> Ve <xref:System.ComponentModel.BrowsableAttribute.Browsable%2A> özelliklerini Özellikler penceresinde "Çerçevesi." adlı özel bir kısmında görünmesini öznitelikler bu özellikler için uygulanır  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#160](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#160)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#160](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#160)]  
  
12. İşleyicileri uygulamak <xref:System.ComponentModel.BackgroundWorker> bileşenin <xref:System.ComponentModel.BackgroundWorker.DoWork> ve <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> olayları.  
  
     <xref:System.ComponentModel.BackgroundWorker.DoWork> Olay işleyicisi uyku tarafından belirtilen milisaniye sayısı `UpdatePeriod` ardından başlatır <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> çağırarak animasyon kodunuzu durdurur kadar olay <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>.  
  
     <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> Olay işleyicisi yanıp görünümünü sağlamak için açık ve koyu durumuna arasındaki metni değiştirir.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#180](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#180)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#180](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#180)]  
  
13. Geçersiz kılma <xref:System.Windows.Forms.Control.OnPaint%2A> animasyon etkinleştirmek için yöntemi.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#170](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#170)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#170](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#170)]  
  
14. Çözümü derlemek için F6 tuşuna basın.  
  
## <a name="create-the-marqueeborder-child-control"></a>MarqueeBorder alt denetimi oluşturma  
 `MarqueeBorder` Denetimidir biraz daha karmaşık `MarqueeText` denetimi. Daha fazla özellik ve animasyon sahip <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemdir daha karmaşık. İlkesi, oldukça benzer `MarqueeText` denetimi.  
  
 Çünkü `MarqueeBorder` denetimi alt denetimler sahip olabilir, farkında olmanız gereken <xref:System.Windows.Forms.Control.Layout> olayları.  
  
#### <a name="to-create-the-marqueeborder-control"></a>MarqueeBorder denetimi oluşturmak için  
  
1.  Yeni bir **özel denetim** öğesinin `MarqueeControlLibrary` proje. Yeni kaynak dosyası bir temel "MarqueeBorder." adını verin  
  
2.  Sürükleme bir <xref:System.ComponentModel.BackgroundWorker> bileşenini **araç kutusu** üzerine, `MarqueeBorder` denetimi. Bu bileşen sağlayacak `MarqueeBorder` kendisini zaman uyumsuz olarak güncelleştirmek için denetimi.  
  
3.  Özellikler penceresinde ayarlayın <xref:System.ComponentModel.BackgroundWorker> bileşenin `WorkerReportsProgess` ve <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> özelliklerine `true`. Bu ayarlar sağlar. <xref:System.ComponentModel.BackgroundWorker> düzenli aralıklarla yükseltmek için bileşen <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> olay ve zaman uyumsuz güncelleştirmeleri iptal etmek için. Daha fazla bilgi için [BackgroundWorker bileşeni](../../../../docs/framework/winforms/controls/backgroundworker-component.md).  
  
4.  Özellikler penceresinde olayları düğmesine tıklayın. İşleyicileri eklemek <xref:System.ComponentModel.BackgroundWorker.DoWork> ve <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> olayları.  
  
5.  Açık `MarqueeBorder` kaynak dosyada **Kod Düzenleyicisi**. Dosyasının en üstüne aşağıdaki ad alanlarını içeri aktarın:  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#20)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#20)]  
  
6.  Bildirimini değiştirmek `MarqueeBorder` devralınacak <xref:System.Windows.Forms.Panel> ve uygulamak için `IMarqueeWidget` arabirimi.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#30](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#30)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#30](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#30)]  
  
7.  Yönetmek için iki sabit listesi bildirme `MarqueeBorder` denetimin durumunu: `MarqueeSpinDirection`, hangi ışıkları "döndürme" kenarlık yönü belirler ve `MarqueeLightShape`, ışıkları (kare veya döngüsel) şeklini belirler. Bu bildirimler önce yerleştirin `MarqueeBorder` sınıfının bildirimi.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#97](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#97)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#97](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#97)]  
  
8.  Kullanıma sunulan özelliklere karşılık gelen örnek değişkenleri tanımlayın ve bunları oluşturucuda başlatmak.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#40](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#40)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#40](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#40)]  
  
9. `IMarqueeWidget` arabirimini gerçekleştirin.  
  
     `StartMarquee` Ve `StopMarquee` yöntemleri çağırma <xref:System.ComponentModel.BackgroundWorker> bileşenin <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> ve <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> yöntemleri animasyon durdurmak ve başlatmak.  
  
     Çünkü `MarqueeBorder` denetimi alt denetimler içerebilir `StartMarquee` yöntemi, tüm alt denetimleri ve çağrıları numaralandırır `StartMarquee` uygulayan bu `IMarqueeWidget`. `StopMarquee` Yöntemi benzer bir uygulaması vardır.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#50](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#50)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#50](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#50)]  
  
10. Özellik erişimcisi uygulayın. `MarqueeBorder` Denetiminin görünümünü denetlemek için çeşitli özelliklere sahiptir.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#60](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#60)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#60](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#60)]  
  
11. İşleyicileri uygulamak <xref:System.ComponentModel.BackgroundWorker> bileşenin <xref:System.ComponentModel.BackgroundWorker.DoWork> ve <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> olayları.  
  
     <xref:System.ComponentModel.BackgroundWorker.DoWork> Olay işleyicisi uyku tarafından belirtilen milisaniye sayısı `UpdatePeriod` ardından başlatır <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> çağırarak animasyon kodunuzu durdurur kadar olay <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>.  
  
     <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> Olay işleyicisi, diğer ışıkları açık/koyu durumu belirlenir, "temel" ışık ve çağrıları konumunu artırır <xref:System.Windows.Forms.Control.Refresh%2A> kendisini çizilecek denetimi neden için yöntemi.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#90](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#90)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#90](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#90)]  
  
12. Yardımcı yöntemler uygulamak `IsLit` ve `DrawLight`.  
  
     `IsLit` Yöntemi, belirtilen konumda bir ışığın rengini belirler. "Aydınlatma" ışık rengi tarafından verilen çizilmiştir `LightColor` özellik ve "koyu" olanlar tarafından verilen renkli çizilmiştir `DarkColor` özelliği.  
  
     `DrawLight` Yöntemi bir ışık uygun rengini, Şekil ve konumu kullanarak çizer.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#80](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#80)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#80](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#80)]  
  
13. Geçersiz kılma <xref:System.Windows.Forms.Control.OnLayout%2A> ve <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemleri.  
  
     <xref:System.Windows.Forms.Control.OnPaint%2A> Yöntemi çizer kenarlarında ışıkları `MarqueeBorder` denetimi.  
  
     Çünkü <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemi bağlıdır boyutlarını üzerinde `MarqueeBorder` denetime ihtiyacınız düzeni değiştiğinde çağırmak. Bunu başarmak için geçersiz kılma <xref:System.Windows.Forms.Control.OnLayout%2A> ve çağrı <xref:System.Windows.Forms.Control.Refresh%2A>.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#70](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#70)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#70](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#70)]  
  
## <a name="creating-a-custom-designer-to-shadow-and-filter-properties"></a>Özel bir tasarımcı gölge ve filtre özellikleri oluşturma  
 `MarqueeControlRootDesigner` Sınıfı kök Tasarımcısı uygulamasını sağlar. Bu tasarımcı yanı sıra çalıştığı üzerinde `MarqueeControl`, özellikle ile ilişkili özel bir tasarımcı ihtiyacınız olacak `MarqueeBorder` denetimi. Bu tasarımcı özel kök Tasarımcı bağlamında uygun özel davranış sağlar.  
  
 Özellikle, `MarqueeBorderDesigner` "gölge" ve belirli özellikleri üzerinde filtre `MarqueeBorder` denetimi tasarım ortamı ile kendi etkileşimi değiştirme.  
  
 Bir bileşenin özellik erişimcisi çağrıları kesintiye "gölgeleme olarak." adı verilir Bu kullanıcı tarafından ayarlanan değer izlemek bir tasarımcı sağlar ve isteğe bağlı olarak bu değeri tasarlanmakta bileşenine geçirin.  
  
 Bu örnekte, <xref:System.Windows.Forms.Control.Visible%2A> ve <xref:System.Windows.Forms.Control.Enabled%2A> özellikleri gölgeli tarafından `MarqueeBorderDesigner`, gelen yapma kullanıcı engeller `MarqueeBorder` görünmez ya da devre dışı tasarım zamanında denetimi.  
  
 Tasarımcılar, ayrıca ekleyebilir ve özellikleri Kaldır. Bu örnekte, <xref:System.Windows.Forms.Control.Padding%2A> özelliği için tasarım zamanında kaldırılacak `MarqueeBorder` denetimi program aracılığıyla doldurma tarafından belirtilen ışıkları boyutuna göre ayarlar `LightSize` özelliği.  
  
 Temel sınıfı `MarqueeBorderDesigner` olduğu <xref:System.ComponentModel.Design.ComponentDesigner>, öznitelikler, özellikleri ve olayları tasarım zamanında denetimi tarafından kullanıma sunulan değiştirebilirsiniz yöntemleri vardır:  
  
-   <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterProperties%2A>  
  
-   <xref:System.ComponentModel.Design.ComponentDesigner.PostFilterProperties%2A>  
  
-   <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterAttributes%2A>  
  
-   <xref:System.ComponentModel.Design.ComponentDesigner.PostFilterAttributes%2A>  
  
-   <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterEvents%2A>  
  
-   <xref:System.ComponentModel.Design.ComponentDesigner.PostFilterEvents%2A>  
  
 Bu yöntemleri kullanarak bir bileşenin genel arabirimi değiştirilirken şu kurallara uymalıdır:  
  
-   Ekleme veya öğeleri kaldırma `PreFilter` yalnızca yöntemleri  
  
-   Mevcut öğelerini `PostFilter` yalnızca yöntemleri  
  
-   Her zaman temel uygulamayı ilk kez çağırmak `PreFilter` yöntemleri  
  
-   Her zaman temel uygulamayı son çağırması `PostFilter` yöntemleri  
  
 Bu kurallarına uymak için tasarım zamanı ortamında tüm tasarımcıları tasarlanmakta olan tüm bileşenlerin tutarlı bir görünüm sahip olmasını sağlar.  
  
 <xref:System.ComponentModel.Design.ComponentDesigner> Sınıfı gölgeli özelliklerinin değerleri, belirli bir örneği değişkenleri oluşturmak üzere gerek kalmamasını yönetmek için bir sözlüğünü sağlar.  
  
#### <a name="to-create-a-custom-designer-to-shadow-and-filter-properties"></a>Gölge ve filtre özellikleri için özel bir tasarımcı oluşturmak için  
  
1.  Sağ **tasarım** klasör ve bir yeni sınıf ekleyin. Kaynak dosyanın temel adı "MarqueeBorderDesigner." verin  
  
2.  Açık `MarqueeBorderDesigner` kaynak dosyada **Kod Düzenleyicisi**. Dosyasının en üstüne aşağıdaki ad alanlarını içeri aktarın:  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#420](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#420)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#420](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#420)]  
  
3.  Bildirimini değiştirmek `MarqueeBorderDesigner` devralınacak <xref:System.Windows.Forms.Design.ParentControlDesigner>.  
  
     Çünkü `MarqueeBorder` denetimi alt denetimler içerebilir `MarqueeBorderDesigner` devraldığı <xref:System.Windows.Forms.Design.ParentControlDesigner>, üst-alt etkileşimini işler.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#430](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#430)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#430](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#430)]  
  
4.  Taban uygulamasını geçersiz kılma <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterProperties%2A>.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#450](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#450)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#450](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#450)]  
  
5.  Uygulama <xref:System.Windows.Forms.Control.Enabled%2A> ve <xref:System.Windows.Forms.Control.Visible%2A> özellikleri. Bu uygulamalar, denetimin özelliklerini gölge.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#440](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#440)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#440](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#440)]  
  
## <a name="handling-component-changes"></a>Bileşen değişiklikleri işleme  
 `MarqueeControlRootDesigner` Sınıfı için özel tasarım zamanı deneyimi sağlar, `MarqueeControl` örnekleri. Tasarım zamanı işlevselliği çoğunu devralınır <xref:System.Windows.Forms.Design.DocumentDesigner> sınıfı; iki belirli özelleştirmeleri uygulamak, kod olacaktır: bileşen değişiklikleri işleme ve tasarımcı fiilleri ekleme.  
  
 Kullanıcıların tasarım olarak kendi `MarqueeControl` örnekleri, kök tasarımcınıza değişiklikleri izleyecek `MarqueeControl` ve onun alt denetimler. Tasarım zamanı ortamında uygun bir hizmet sunar <xref:System.ComponentModel.Design.IComponentChangeService>, bileşen durumu için izleme dönüşür.  
  
 Ortamıyla sorgulayarak bu hizmet için bir başvuru alma <xref:System.ComponentModel.Design.ComponentDesigner.GetService%2A> yöntemi. Sorgu başarılı olursa, tasarımcınıza bir işleyici ekleyebilirsiniz <xref:System.ComponentModel.Design.IComponentChangeService.ComponentChanged> olay ve tutarlı bir duruma tasarım zamanında korumak için gerekli tüm görevleri gerçekleştirin.  
  
 Durumunda, `MarqueeControlRootDesigner` sınıfı çağıracaktır <xref:System.Windows.Forms.Control.Refresh%2A> yöntemi her `IMarqueeWidget` nesnesi tarafından içerilen `MarqueeControl`. Bu neden `IMarqueeWidget` nesnenin kendisini uygun özellikler, üst beğendiğinizde repaint <xref:System.Windows.Forms.Control.Size%2A> değiştirilir.  
  
#### <a name="to-handle-component-changes"></a>Bileşen değişiklikleri işlemek için  
  
1.  Açık `MarqueeControlRootDesigner` kaynak dosyada **Kod Düzenleyicisi** ve geçersiz kılma <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> yöntemi. ' In temel uygulamayı çağırması <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> ve sorgu <xref:System.ComponentModel.Design.IComponentChangeService>.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#580](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#580)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#580](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#580)]  
  
2.  Uygulama <xref:System.ComponentModel.Design.IComponentChangeService.OnComponentChanged%2A> olay işleyicisi. Test gönderen bileşenin türü ve ise bir `IMarqueeWidget`, arama, <xref:System.Windows.Forms.Control.Refresh%2A> yöntemi.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#560](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#560)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#560](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#560)]  
  
## <a name="adding-designer-verbs-to-your-custom-designer"></a>Tasarımcı fiilleri özel Tasarımcınıza ekleme  
 Tasarımcı fiil bir olay işleyicisi için bağlı bir menü komutu ' dir. Tasarımcı fiilleri tasarım zamanında bir bileşenin kısayol menüsüne eklenir. Daha fazla bilgi için bkz. <xref:System.ComponentModel.Design.DesignerVerb>.  
  
 Tasarımcılar, iki Tasarımcı fiilleri ekler: **Test çalıştırması** ve **durdurma Test**. Bu Eylemler, çalışma zamanı davranışını görüntülemenize olanak sağlayacak `MarqueeControl` tasarım zamanında. Bu eylemler eklenecek `MarqueeControlRootDesigner`.  
  
 Zaman **Test çalıştırması** olan çağrılır, fiil olay işleyiciyi çağırır `StartMarquee` metodunda `MarqueeControl`. Zaman **durdurma Test** olan çağrılır, fiil olay işleyiciyi çağırır `StopMarquee` metodunda `MarqueeControl`. Uygulamasını `StartMarquee` ve `StopMarquee` uygulayan içerdiği denetimlerle üzerinde yöntemleri çağırmak bu yöntemleri `IMarqueeWidget`, bu nedenle tüm kapsanan `IMarqueeWidget` denetimleri de test katılın.  
  
#### <a name="to-add-designer-verbs-to-your-custom-designers"></a>Özel, tasarımcılar için tasarımcı fiilleri eklemek için  
  
1.  İçinde `MarqueeControlRootDesigner` sınıf, olay işleyicileri adlı ekleme `OnVerbRunTest` ve `OnVerbStopTest`.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#570](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#570)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#570](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#570)]  
  
2.  Bu olay işleyicileri için karşılık gelen, Tasarımcı fiilleri bağlanın. `MarqueeControlRootDesigner` devralınan bir <xref:System.ComponentModel.Design.DesignerVerbCollection> taban sınıfından. İki yeni oluşturacak <xref:System.ComponentModel.Design.DesignerVerb> nesneleri ve bu koleksiyonda ekleme <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> yöntemi.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#590](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#590)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#590](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#590)]  
  
## <a name="creating-a-custom-uitypeeditor"></a>Özel UITypeEditor oluşturma  
 Kullanıcılar için özel bir tasarım zamanı deneyimi oluşturduğunuzda, genellikle bir özel özellikler penceresini etkileşim oluşturmak için tercih edilir. Oluşturarak bunu gerçekleştirebilirsiniz bir <xref:System.Drawing.Design.UITypeEditor>. Daha fazla bilgi için [nasıl yapılır: UI türü düzenleyici oluşturma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/fd3kt7d5(v=vs.120)).  
  
 `MarqueeBorder` Denetimi Özellikler penceresindeki çeşitli özellikler sunar. Bu özelliklerin iki `MarqueeSpinDirection` ve `MarqueeLightShape` numaralandırmalar tarafından temsil edilir. UI türü Düzenleyici kullanımını göstermek için `MarqueeLightShape` özellik ilişkili bir olacaktır <xref:System.Drawing.Design.UITypeEditor> sınıfı.  
  
#### <a name="to-create-a-custom-ui-type-editor"></a>Özel bir UI türü düzenleyici oluşturmak için  
  
1.  Açık `MarqueeBorder` kaynak dosyada **Kod Düzenleyicisi**.  
  
2.  Tanımındaki `MarqueeBorder` sınıfı, adında bir sınıf bildirme `LightShapeEditor` türetilen <xref:System.Drawing.Design.UITypeEditor>.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#96](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#96)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#96](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#96)]  
  
3.  Bildirme bir <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> adlı örnek değişkeni `editorService`.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#92](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#92)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#92](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#92)]  
  
4.  Geçersiz kılma <xref:System.Drawing.Design.UITypeEditor.GetEditStyle%2A> yöntemi. Bu uygulama döndürür <xref:System.Drawing.Design.UITypeEditorEditStyle.DropDown>, nasıl görüntüleneceğini tasarım ortamı söyler `LightShapeEditor`.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#93](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#93)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#93](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#93)]  
  
5.  Geçersiz kılma <xref:System.Drawing.Design.UITypeEditor.EditValue%2A> yöntemi. Bu uygulama için tasarım ortamı sorgular bir <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> nesne. Başarılı oluşturur, bir `LightShapeSelectionControl`. <xref:System.Windows.Forms.Design.IWindowsFormsEditorService.DropDownControl%2A> Metodunu çağırmak başlatmak için `LightShapeEditor`. Bu çağrıyı dönüş değeri, tasarım ortama döndürülür.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#94](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#94)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#94](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#94)]  
  
## <a name="creating-a-view-control-for-your-custom-uitypeeditor"></a>Bir View denetimi için özel UITypeEditor oluşturma  
  
1.  `MarqueeLightShape` Özelliğini destekleyen iki tür açık şekiller: `Square` ve `Circle`. Bu değerleri Özellikler penceresinde görüntüleme grafik ile amacıyla yalnızca kullanılan özel bir denetim oluşturacaksınız. Bu özel denetimi tarafından kullanılan, <xref:System.Drawing.Design.UITypeEditor> Özellikler penceresi ile etkileşim kurmak için.  
  
#### <a name="to-create-a-view-control-for-your-custom-ui-type-editor"></a>Bir görünüm denetimi türü düzenleyici için özel kullanıcı Arabirimi oluşturmak için  
  
1.  Yeni bir <xref:System.Windows.Forms.UserControl> öğesinin `MarqueeControlLibrary` proje. Yeni kaynak dosyası bir temel "LightShapeSelectionControl." adını verin  
  
2.  İki <xref:System.Windows.Forms.Panel> denetimler **araç kutusu** üzerine `LightShapeSelectionControl`. Bunları `squarePanel` ve `circlePanel`. Yan yana düzenleyin. Ayarlama <xref:System.Windows.Forms.Control.Size%2A> her iki özellik <xref:System.Windows.Forms.Panel> için denetimler (60, 60). Ayarlama <xref:System.Windows.Forms.Control.Location%2A> özelliği `squarePanel` denetimi (8, 10). Ayarlama <xref:System.Windows.Forms.Control.Location%2A> özelliği `circlePanel` denetimi (80, 10). Son olarak, ayarlama <xref:System.Windows.Forms.Control.Size%2A> özelliği `LightShapeSelectionControl` için (150, 80).  
  
3.  Açık `LightShapeSelectionControl` kaynak dosyada **Kod Düzenleyicisi**. İçeri aktarma dosyasının en üstüne <xref:System.Windows.Forms.Design?displayProperty=nameWithType> ad alanı:  
  
```vb  
Imports System.Windows.Forms.Design  
```  
  
```csharp  
using System.Windows.Forms.Design;  
```  
  
1.  Uygulama <xref:System.Windows.Forms.Control.Click> için olay işleyicileri `squarePanel` ve `circlePanel` kontrol eder. Bu yöntemleri çağırmak <xref:System.Windows.Forms.Design.IWindowsFormsEditorService.CloseDropDown%2A> özel sonuna <xref:System.Drawing.Design.UITypeEditor> oturumu düzenleme.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#390](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#390)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#390](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#390)]  
  
2.  Bildirme bir <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> adlı örnek değişkeni `editorService`.  
  
```vb  
Private editorService As IWindowsFormsEditorService  
```  
  
```csharp  
private IWindowsFormsEditorService editorService;  
```  
  
1.  Bildirme bir `MarqueeLightShape` adlı örnek değişkeni `lightShapeValue`.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#330](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#330)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#330](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#330)]  
  
2.  İçinde `LightShapeSelectionControl` oluşturucusu, ekleme <xref:System.Windows.Forms.Control.Click> olay işleyicilerine `squarePanel` ve `circlePanel` denetimleri <xref:System.Windows.Forms.Control.Click> olayları. Ayrıca atayan bir yapıcı yeniden yüklemesi tanımlayan `MarqueeLightShape` tasarım ortamı değerinden `lightShapeValue` alan.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#340](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#340)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#340](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#340)]  
  
3.  İçinde <xref:System.ComponentModel.Component.Dispose%2A> yöntemi ayırma <xref:System.Windows.Forms.Control.Click> olay işleyicileri.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#350](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#350)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#350](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#350)]  
  
4.  İçinde **Çözüm Gezgini**, tıklayın **tüm dosyaları göster** düğmesi. LightShapeSelectionControl.Designer.cs veya LightShapeSelectionControl.Designer.vb dosyasını açın ve öğenin varsayılan tanımını Kaldır <xref:System.ComponentModel.Component.Dispose%2A> yöntemi.  
  
5.  Uygulama `LightShape` özelliği.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#360](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#360)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#360](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#360)]  
  
6.  Geçersiz kılma <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemi. Bu uygulama bir dolu bir kare ve daire çizer. Bir şekil veya diğer çevresine bir kenarlık çizerek, seçili değer ayrıca vurgulanır.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#380](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#380)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#380](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#380)]  
  
## <a name="testing-your-custom-control-in-the-designer"></a>Özel Denetim Tasarımcısı'nda test etme  
 Bu noktada, yapı `MarqueeControlLibrary` proje. Devralınan bir denetim oluşturarak uygulamanızı test `MarqueeControl` sınıf ve form üzerinde kullanarak.  
  
#### <a name="to-create-a-custom-marqueecontrol-implementation"></a>Özel bir MarqueeControl uygulaması oluşturmak için  
  
1.  Açık `DemoMarqueeControl` Windows Forms Tasarımcısı'nda. Bu örneği oluşturur `DemoMarqueeControl` yazın ve örneğinde görüntüler `MarqueeControlRootDesigner` türü.  
  
2.  İçinde **araç kutusu**açın **MarqueeControlLibrary bileşenleri** sekmesi. Göreceğiniz `MarqueeBorder` ve `MarqueeText` denetimleri seçilebilir.  
  
3.  Örneği sürükleyin `MarqueeBorder` denetimi `DemoMarqueeControl` tasarım yüzeyi. Bu dock `MarqueeBorder` denetimin üst denetimine.  
  
4.  Örneği sürükleyin `MarqueeText` denetimi `DemoMarqueeControl` tasarım yüzeyi.  
  
5.  Çözümü oluşturun.  
  
6.  Sağ `DemoMarqueeControl` kısayol menüsünü seçin ve **Test çalıştırması** animasyonu başlatmak için seçeneği. Tıklayın **durdurma Test** animasyonu durdurmak için.  
  
7.  Açık **Form1** Tasarım görünümünde.  
  
8.  İki <xref:System.Windows.Forms.Button> form üzerinde denetimleri. Bunları `startButton` ve `stopButton`, değiştirip <xref:System.Windows.Forms.Control.Text%2A> değerlerini özellik **Başlat** ve **Durdur**sırasıyla.  
  
9. Uygulama <xref:System.Windows.Forms.Control.Click> her ikisi için olay işleyicileri <xref:System.Windows.Forms.Button> kontrol eder.  
  
10. İçinde **araç kutusu**açın **MarqueeControlTest bileşenleri** sekmesi. Göreceğiniz `DemoMarqueeControl` seçim için kullanılabilir.  
  
11. Örneği sürükleyin `DemoMarqueeControl` üzerine **Form1** tasarım yüzeyi.  
  
12. İçinde <xref:System.Windows.Forms.Control.Click> olay işleyicilerini çağırma `Start` ve `Stop` yöntemlerde `DemoMarqueeControl`.  
  
```vb  
Private Sub startButton_Click(sender As Object, e As System.EventArgs)  
    Me.demoMarqueeControl1.Start()  
End Sub 'startButton_Click  
  
Private Sub stopButton_Click(sender As Object, e As System.EventArgs)  
Me.demoMarqueeControl1.Stop()  
End Sub 'stopButton_Click  
```  
  
```csharp  
private void startButton_Click(object sender, System.EventArgs e)  
{  
    this.demoMarqueeControl1.Start();  
}  
  
private void stopButton_Click(object sender, System.EventArgs e)  
{  
    this.demoMarqueeControl1.Stop();  
}  
```  
  
1.  Ayarlama `MarqueeControlTest` projesini başlangıç projesi olarak ve çalıştırın. Görüntüleme formu görürsünüz, `DemoMarqueeControl`. Tıklayın **Başlat** animasyonu başlatmak için düğme. Yanıp metin ve kenarlık taşıma ışıkları görmeniz gerekir.  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 `MarqueeControlLibrary` Özel denetimler ve ilişkili tasarımcıları basit bir uygulamasını gösterir. Bu örnek daha karmaşık çeşitli şekillerde yapabilirsiniz:  
  
-   Özellik değerlerini değiştirmek `DemoMarqueeControl` Tasarımcısı'nda. Daha fazla Ekle `MarqueBorder` denetler ve bunları bir iç içe geçmiş etkisi oluşturmak için üst örneklerinden yerleştir. Deneme için farklı ayarlarla `UpdatePeriod` ve ışık güvenlikle ilgili özellikler.  
  
-   Kendi uygulamalarını Yazar `IMarqueeWidget`. Örneğin, bir yanıp sönen "neon işareti" veya bir animasyonlu işareti ile birden çok görüntü oluşturabilirsiniz.  
  
-   Tasarım zamanı deneyimi özelleştirin. Daha fazla özellik gölgeleme deneyebilirsiniz <xref:System.Windows.Forms.Control.Enabled%2A> ve <xref:System.Windows.Forms.Control.Visible%2A>, ve yeni özellikleri ekleyebilirsiniz. Alt denetimler yerleştirme gibi genel görevleri basitleştirmek için yeni Tasarımcı fiilleri ekleyin.  
  
-   Lisans `MarqueeControl`. Daha fazla bilgi için [nasıl yapılır: Lisans bileşenleri ve denetimleri](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/fe8b1eh9(v=vs.120)).  
  
-   Denetimlerinizi nasıl sıralanır ve kod için bunları nasıl oluşturulacağını denetler. Daha fazla bilgi için [dinamik kaynak kodu oluşturma ve derleme](../../../../docs/framework/reflection-and-codedom/dynamic-source-code-generation-and-compilation.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.UserControl>
- <xref:System.Windows.Forms.Design.ParentControlDesigner>
- <xref:System.Windows.Forms.Design.DocumentDesigner>
- <xref:System.ComponentModel.Design.IRootDesigner>
- <xref:System.ComponentModel.Design.DesignerVerb>
- <xref:System.Drawing.Design.UITypeEditor>
- <xref:System.ComponentModel.BackgroundWorker>
- [Nasıl yapılır: Tasarım zamanı özelliklerinden faydalanan Windows Forms denetimi oluşturma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/307hck25(v=vs.120))
- [Tasarım zamanı desteği sunma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))
- [Özel tasarımcılar](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/h51z5c0x(v=vs.120))
