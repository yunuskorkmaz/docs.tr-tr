---
title: "İzlenecek yol: Visual Studio Tasarım-Zamanı Özellikleri'nden Faydalanan Windows Forms Denetimi Oluşturma"
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
ms.openlocfilehash: 10905df76f2b638c10b14c1dd8c181b9652ea963
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-creating-a-windows-forms-control-that-takes-advantage-of-visual-studio-design-time-features"></a>İzlenecek yol: Visual Studio Tasarım-Zamanı Özellikleri'nden Faydalanan Windows Forms Denetimi Oluşturma
Özel bir denetim için tasarım zamanı deneyimi ilişkili bir özel Tasarımcısı yazarak geliştirilebilir.  
  
 Bu kılavuzda nasıl özel bir denetim için özel bir tasarımcı oluşturulacağı gösterilmektedir. U uygulayacaksınız bir `MarqueeControl` türü ve adlı bir ilişkili bir tasarımcı sınıfını `MarqueeControlRootDesigner`.  
  
 `MarqueeControl` Tür animasyonlu ışık ve yanıp sönen metinle birlikte bir tiyatro çerçevesi benzeyen bir görüntü uygular.  
  
 Bu denetim için tasarımcı özel bir tasarım zamanı deneyimi sağlamak için tasarım ortamı ile etkileşime girer. Özel Tasarımcısı ile özel bir araya `MarqueeControl` uygulamasıyla animasyonlu ışık ve birçok birleşimleri yanıp sönen metni. Herhangi bir Windows Forms denetimi gibi bir form üzerinde birleştirilmiş denetimi kullanabilirsiniz.  
  
 Bu örneklerde gösterilen görevler aşağıdakileri içerir:  
  
-   Projeyi Oluşturma  
  
-   Bir denetim kitaplığı projesi oluşturma  
  
-   Özel denetim projesine başvurma  
  
-   Özel bir denetim ve kendi özel Tasarımcısı tanımlama  
  
-   Özel denetim örneği oluşturma  
  
-   Tasarım zamanı hata ayıklama için proje ayarlama  
  
-   Özel Denetim uygulama  
  
-   Özel denetim için bir alt denetimi oluşturma  
  
-   MarqueeBorder alt denetimi oluşturma  
  
-   Özel bir tasarımcı gölge ve filtre özellikleri oluşturma  
  
-   Bileşen değişiklikleri işleme  
  
-   Özel Designer'a tasarımcısı fiilleri ekleme  
  
-   Özel UITypeEditor oluşturma  
  
-   Özel Denetim Tasarımcısı'nda test etme  
  
 İşiniz bittiğinde, özel denetim aşağıdakine benzer görünecektir:  
  
 ![Olası MarqueeControl yerleşimi](../../../../docs/framework/winforms/controls/media/demomarqueecontrol.gif "DemoMarqueeControl")  
  
 Tam kod listesi için bkz: [nasıl yapılır: bir Windows Forms denetimi, geçen avantajı, tasarım-zamanı özellikleri oluşturma](http://msdn.microsoft.com/library/8e0bad0e-56f3-43d2-bf63-a945c654d97c).  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu kılavuzu tamamlamak için gerekir:  
  
-   Oluşturma ve Windows Forms uygulaması projeleri, Visual Studio yüklü olduğu bilgisayarda çalıştırmak için yeterli izinleri yok.  
  
## <a name="creating-the-project"></a>Projeyi Oluşturma  
 İlk adım, uygulama projesi oluşturmaktır. Özel denetim barındıran uygulama oluşturmak için bu proje kullanır.  
  
#### <a name="to-create-the-project"></a>Proje oluşturmak için  
  
-   "MarqueeControlTest." adlı bir Windows Forms uygulaması projesi oluşturma Daha fazla bilgi için bkz: [nasıl yapılır: bir Windows uygulaması projesi oluşturduğunuzda](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa).  
  
## <a name="creating-a-control-library-project"></a>Bir denetim kitaplığı projesi oluşturma  
 Sonraki adım, denetim kitaplığı projesi oluşturmaktır. Yeni bir özel denetim ve karşılık gelen kendi özel Tasarımcısı oluşturur.  
  
#### <a name="to-create-the-control-library-project"></a>Denetim Kitaplığı projesi oluşturmak için  
  
1.  Bir Windows Forms Denetim Kitaplığı proje çözüme ekleyin. "MarqueeControlLibrary." proje adı  
  
2.  Kullanarak **Çözüm Gezgini**, projenin varsayılan denetim seçim dilinizi bağlı olarak "UserControl1.cs" veya "UserControl1.vb" adlı kaynak dosya silerek silin. Daha fazla bilgi için bkz: [NIB: nasıl yapılır: Kaldır, silme ve dışlama öğeleri](http://msdn.microsoft.com/library/6dffdc86-29c8-4eff-bcd8-e3a0dd9e9a73).  
  
3.  Yeni bir ekleme <xref:System.Windows.Forms.UserControl> öğesinin `MarqueeControlLibrary` projesi. Yeni kaynak dosyası "MarqueeControl.", temel bir ad verin  
  
4.  Kullanarak **Çözüm Gezgini**, yeni bir klasör oluşturun `MarqueeControlLibrary` projesi. Daha fazla bilgi için bkz: [NIB: nasıl yapılır: Yeni proje öğeleri Ekle](http://msdn.microsoft.com/library/63d3e16b-de6e-4bb5-a0e3-ecec762201ce). Yeni bir klasör adı "Tasarım."  
  
5.  Sağ **tasarım** klasörü ve yeni bir sınıf ekleyin. Kaynak dosya "MarqueeControlRootDesigner.", temel bir ad verin  
  
6.  System.Design derleme türlerinden kullanın, böylece bu başvuru eklemek gerekir `MarqueeControlLibrary` projesi.  
  
    > [!NOTE]
    >  System.Design derleme kullanmak için projenize değil .NET Framework istemci profili .NET Framework'ün tam sürümünü hedeflemesi gerekir. Hedef Framework'ü değiştirmek için bkz: [nasıl yapılır: .NET Framework sürümü hedef](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework).  
  
## <a name="referencing-the-custom-control-project"></a>Özel denetim projesine başvurma  
 Kullanacağınız `MarqueeControlTest` özel denetim test etmek için proje. Proje başvurusu eklediğinizde test projesi özel denetimin haberdar edilir `MarqueeControlLibrary` derleme.  
  
#### <a name="to-reference-the-custom-control-project"></a>Özel denetim Proje referansı  
  
-   İçinde `MarqueeControlTest` proje, proje başvurusu Ekle `MarqueeControlLibrary` derleme. Kullandığınızdan emin olun **projeleri** sekmesinde **Başvuru Ekle** başvuran yerine iletişim kutusu `MarqueeControlLibrary` doğrudan derleme.  
  
## <a name="defining-a-custom-control-and-its-custom-designer"></a>Özel bir denetim ve kendi özel Tasarımcısı tanımlama  
 Özel denetim öğesinden türetilen <xref:System.Windows.Forms.UserControl> sınıfı. Bu denetim birbirini dışlayan sağlar ve varsayılan işlevsellik büyük bir bölümünü, denetim sağlar.  
  
 Özel denetim ilişkili bir özel Tasarımcısı sahip olur. Bu, özellikle özel denetim için özel olarak hazırlanmış bir benzersiz tasarım deneyimi oluşturmanıza olanak sağlar.  
  
 Denetim kullanarak kendi Tasarımcısı ile ilişkilendirebileceğiniz <xref:System.ComponentModel.DesignerAttribute> sınıfı. Özel denetim tüm tasarım zamanı davranışını geliştirdiğiniz çünkü özel Tasarımcısı gerçekleştireceksiniz <xref:System.ComponentModel.Design.IRootDesigner> arabirimi.  
  
#### <a name="to-define-a-custom-control-and-its-custom-designer"></a>Özel bir denetim ve kendi özel Tasarımcısı tanımlamak için  
  
1.  Açık `MarqueeControl` kaynak dosyasında **Kod düzenleyicisinde**. Dosyanın üst kısmında, şu ad alanlarından içeri aktarın:  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#220](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#220)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#220](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#220)]  
  
2.  Ekleme <xref:System.ComponentModel.DesignerAttribute> için `MarqueeControl` sınıf bildiriminin. Bu, özel denetimin kendi Tasarımcısı ile ilişkilendirir.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#240](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#240)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#240](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#240)]  
  
3.  Açık `MarqueeControlRootDesigner` kaynak dosyasında **Kod düzenleyicisinde**. Dosyanın üst kısmında, şu ad alanlarından içeri aktarın:  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#520](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#520)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#520](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#520)]  
  
4.  Bildirimi değiştirme `MarqueeControlRootDesigner` devralınacak <xref:System.Windows.Forms.Design.DocumentDesigner> sınıfı. Uygulama <xref:System.ComponentModel.ToolboxItemFilterAttribute> Tasarımcı etkileşim belirtmek için **araç**.  
  
     **Not** tanımı `MarqueeControlRootDesigner` sınıfı, "MarqueeControlLibrary.Design." adlı bir ad alanındaki içine Bu bildirim Tasarımcısı tasarım ilgili türler için ayrılmış, özel bir ad alanında yerleştirir.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#530](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#530)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#530](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#530)]  
  
5.  Oluşturucusu tanımlamak `MarqueeControlRootDesigner` sınıfı. INSERT bir <xref:System.Diagnostics.Trace.WriteLine%2A> Oluşturucusu gövde deyiminde. Hata ayıklama amacıyla yararlı olacaktır.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#540](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#540)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#540](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#540)]  
  
## <a name="creating-an-instance-of-your-custom-control"></a>Özel denetim örneği oluşturma  
 Özel tasarım zamanı davranışını izlemek için biçiminde denetiminizde örneği yerleştirir `MarqueeControlTest` projesi.  
  
#### <a name="to-create-an-instance-of-your-custom-control"></a>Özel denetim örneği oluşturmak için  
  
1.  Yeni bir ekleme <xref:System.Windows.Forms.UserControl> öğesinin `MarqueeControlTest` projesi. Yeni kaynak dosyası "DemoMarqueeControl.", temel bir ad verin  
  
2.  Açık `DemoMarqueeControl` dosyasını **Kod düzenleyicisinde**. Dosyanın üst kısmında, içeri aktarma `MarqueeControlLibrary` ad alanı:  
  
```vb  
Imports MarqueeControlLibrary  
```  
  
```csharp  
using MarqueeControlLibrary;  
```  
  
1.  Bildirimi değiştirme `DemoMarqueeControl` devralınacak `MarqueeControl` sınıfı.  
  
2.  Projeyi oluşturun.  
  
3.  Açık `Form1` Windows Forms Tasarımcısı'nda.  
  
4.  Bul **MarqueeControlTest bileşenleri** sekmesinde **araç** ve açın. Sürükleme bir `DemoMarqueeControl` gelen **araç** formunuza.  
  
5.  Projeyi oluşturun.  
  
## <a name="setting-up-the-project-for-design-time-debugging"></a>Tasarım zamanı hata ayıklama için proje ayarlama  
 Özel bir tasarım zamanı deneyimi geliştirirken denetimleri ve bileşenleri hata ayıklamak gerekli olacaktır. Tasarım zamanında hata ayıklama izin vermek için projenizi ayarlamak için basit bir yolu yoktur. Daha fazla bilgi için bkz: [izlenecek yol: tasarım zamanında özel Windows Forms denetimleri hata ayıklama](../../../../docs/framework/winforms/controls/walkthrough-debugging-custom-windows-forms-controls-at-design-time.md).  
  
#### <a name="to-set-up-the-project-for-design-time-debugging"></a>Tasarım zamanı hata ayıklama için proje ayarlamak için  
  
1.  Sağ `MarqueeControlLibrary` proje ve seçin **özellikleri**.  
  
2.  "MarqueeControlLibrary özellik sayfaları" iletişim kutusunda seçin **hata ayıklama** sayfası.  
  
3.  İçinde **eylemi Başlat** bölümünde, select **Başlat Dış Program**. Size Visual Studio, ayrı bir örneğini hata ayıklama böylece tıklatın üç nokta (![VisualStudioEllipsesButton ekran](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) için Visual Studio IDE gözatmak için düğmeyi. Devenv.exe yürütülebilir dosyanın adıdır ve varsayılan konuma geri yüklediyseniz, %programfiles%\Microsoft Visual Studio 9.0\Common7\IDE\devenv.exe yoludur.  
  
4.  İletişim kutusunu kapatmak için Tamam'ı tıklatın.  
  
5.  Sağ `MarqueeControlLibrary` proje ve "Başlangıç projesi olarak ayarla bu hata ayıklama yapılandırmasını etkinleştirmek için"'i seçin.  
  
## <a name="checkpoint"></a>Denetim noktası  
 Özel Denetim tasarım zamanı davranışını hata ayıklamak artık hazırsınız. Hata ayıklama ortamı doğru şekilde kurulduğundan emin belirledikten sonra özel denetimin özel Tasarımcısı arasındaki ilişkiyi test edeceğiz.  
  
#### <a name="to-test-the-debugging-environment-and-the-designer-association"></a>Hata ayıklama ortamı ve tasarımcı ilişkilendirme sınamak için  
  
1.  Açık `MarqueeControlRootDesigner` kaynak dosyasında **Kod düzenleyicisinde** ve bir kesme noktası yerleştirmek <xref:System.Diagnostics.Trace.WriteLine%2A> deyimi.  
  
2.  Hata ayıklama oturumu başlatmak için F5 tuşuna basın. Visual Studio yeni bir örneğini oluşturulduğunu unutmayın.  
  
3.  Visual Studio yeni örneğini "MarqueeControlTest" çözümü açın. Seçerek kolayca çözüm bulabilirsiniz **son projeler** gelen **dosya** menüsü. En son kullanılan dosya "MarqueeControlTest.sln" çözüm dosyasını listelenir.  
  
4.  Açık `DemoMarqueeControl` Tasarımcısı'nda. Visual Studio hata ayıklama örneğini odağı alması ve yürütme, kesme noktasında durur unutmayın. Hata ayıklama oturumunun devam etmek için F5 tuşuna basın.  
  
 Bu noktada, her şeyi geliştirmek ve özel denetim ve onun ilişkili özel Tasarımcısı hata ayıklamak için yerinde değil. Bu kılavuzda kalan denetim ve tasarımcı özelliklerini uygulama ayrıntılarını odaklanacaktır.  
  
## <a name="implementing-your-custom-control"></a>Özel Denetim uygulama  
 `MarqueeControl` Olan bir <xref:System.Windows.Forms.UserControl> biraz özelleştirme ile. İki yöntem sunar: `Start`, kayan animasyon başlar ve `Stop`, animasyonun durdurur. Çünkü `MarqueeControl` uygulamak alt denetimleri içeren `IMarqueeWidget` arabirimi, `Start` ve `Stop` her alt denetim ve çağrı listeleme `StartMarquee` ve `StopMarquee` yöntemleri, sırasıyla, her alt denetimi hakkında uygulayan `IMarqueeWidget`.  
  
 Görünümünü `MarqueeBorder` ve `MarqueeText` denetimleri düzeni, bağımlı şekilde `MarqueeControl` geçersiz kılmaları <xref:System.Windows.Forms.Control.OnLayout%2A> yöntemi ve çağrıları <xref:System.Windows.Forms.Control.PerformLayout%2A> alt denetimleri bu tür.  
  
 Kapsamını budur `MarqueeControl` özelleştirmeleri. Çalışma zamanı özellikleri tarafından uygulanan `MarqueeBorder` ve `MarqueeText` denetimleri ve tasarım-zamanı özellikleri tarafından uygulanır `MarqueeBorderDesigner` ve `MarqueeControlRootDesigner` sınıfları.  
  
#### <a name="to-implement-your-custom-control"></a>Özel denetim uygulamak için  
  
1.  Açık `MarqueeControl` kaynak dosyasında **Kod düzenleyicisinde**. Uygulama `Start` ve `Stop` yöntemleri.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#260](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#260)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#260](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#260)]  
  
2.  Geçersiz kılma <xref:System.Windows.Forms.Control.OnLayout%2A> yöntemi.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#270](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#270)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#270](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#270)]  
  
## <a name="creating-a-child-control-for-your-custom-control"></a>Özel denetim için bir alt denetimi oluşturma  
 `MarqueeControl` Alt denetim iki tür barındıracak: `MarqueeBorder` denetim ve `MarqueeText` denetim.  
  
-   `MarqueeBorder`: Bu denetim "ışık" kendi köşelerindeki kenarlığın boyar. Kenarlığın taşıma göründükleri şekilde ışık sırayla, flash. Hangi ışık flash hızı adlı bir özellik tarafından denetlenen `UpdatePeriod`. Diğer özel bazı özellikleri denetimin görünümünü diğer yönlerini belirler. Adlı iki yöntem `StartMarquee` ve `StopMarquee`, ne zaman animasyon başlatır ve durdurur denetim.  
  
-   `MarqueeText`: Bu denetim yanıp sönen bir dize boyar. Gibi `MarqueeBorder` denetim, hangi metni yanıp sönen hızı tarafından denetlenir `UpdatePeriod` özelliği. `MarqueeText` Denetimi de sahip `StartMarquee` ve `StopMarquee` yöntemleri common ile `MarqueeBorder` denetim.  
  
 Tasarım zamanında `MarqueeControlRootDesigner` eklenecek bu iki denetim türlerine izin verir bir `MarqueeControl` herhangi bir arada.  
  
 Adlı bir arabirim iki denetimlerinin ortak özellikleri hesaba katıldığında `IMarqueeWidget`. Böylece `MarqueeControl` herhangi bir seçim çerçevesi ile ilgili alt denetim bulmak ve özel işleme vermek için.  
  
 Dönemsel animasyon özelliği uygulamak için kullanacağınız <xref:System.ComponentModel.BackgroundWorker> nesnelerin <xref:System.ComponentModel?displayProperty=nameWithType> ad alanı. Kullanabileceğinizi <xref:System.Windows.Forms.Timer> nesneleri, ne zaman ancak birçok `IMarqueeWidget` nesneleri, tek kullanıcı Arabirimi iş parçacığı ile animasyonu yetişemiyor olabilir.  
  
#### <a name="to-create-a-child-control-for-your-custom-control"></a>Özel denetim için bir alt denetim oluşturmak için  
  
1.  Yeni bir sınıf öğesine ekleyebilir `MarqueeControlLibrary` projesi. Yeni kaynak dosyası "IMarqueeWidget.", temel bir ad verin  
  
2.  Açık `IMarqueeWidget` kaynak dosyasında **Kod düzenleyicisinde** bildiriminden değiştirip `class` için `interface`:  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/imarqueewidget.cs#2)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/imarqueewidget.vb#2)]  
  
3.  Aşağıdaki kodu ekleyin `IMarqueeWidget` arabirimi iki yöntem ve kayan animasyon işleyen bir özellik kullanıma sunmak için:  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/imarqueewidget.cs#3)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/imarqueewidget.vb#3)]  
  
4.  Yeni bir ekleme **özel denetimi** öğesinin `MarqueeControlLibrary` projesi. Yeni kaynak dosyası "MarqueeText.", temel bir ad verin  
  
5.  Sürükleme bir <xref:System.ComponentModel.BackgroundWorker> gelen bileşen **araç** üzerine, `MarqueeText` denetim. Bu bileşen sağlayacak `MarqueeText` kendisini zaman uyumsuz olarak güncelleştirmek için denetim.  
  
6.  Özellikler penceresinde ayarlayın <xref:System.ComponentModel.BackgroundWorker> bileşenin `WorkerReportsProgess` ve <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> özelliklerine `true`. Bu ayarları izin <xref:System.ComponentModel.BackgroundWorker> düzenli aralıklarla yükseltmek için bileşen <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> olay ve zaman uyumsuz güncelleştirmeleri iptal etmek için. Daha fazla bilgi için bkz: [BackgroundWorker bileşeni](../../../../docs/framework/winforms/controls/backgroundworker-component.md).  
  
7.  Açık `MarqueeText` kaynak dosyasında **Kod düzenleyicisinde**. Dosyanın üst kısmında, şu ad alanlarından içeri aktarın:  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#120](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#120)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#120](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#120)]  
  
8.  Bildirimi değiştirme `MarqueeText` devralınacak <xref:System.Windows.Forms.Label> ve uygulamak için `IMarqueeWidget` arabirimi:  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#130](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#130)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#130](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#130)]  
  
9. Sunulan özellikler karşılık gelen örnek değişkenleri bildirme ve oluşturucuda başlatmaktır. `isLit` Alanı, metin tarafından verilen renk boyandığında olup olmadığını belirler `LightColor` özelliği.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#140](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#140)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#140](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#140)]  
  
10. Uygulama `IMarqueeWidget` arabirimi.  
  
     `StartMarquee` Ve `StopMarquee` yöntemleri çağırma <xref:System.ComponentModel.BackgroundWorker> bileşenin <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> ve <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> animasyon durdurmak ve başlatmak için yöntemleri.  
  
     <xref:System.ComponentModel.CategoryAttribute.Category%2A> Ve <xref:System.ComponentModel.BrowsableAttribute.Browsable%2A> öznitelikler uygulanır `UpdatePeriod` özel bir "Çerçevesi." olarak adlandırılan Özellikler penceresini bölümünde görünmesi özelliği  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#150](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#150)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#150](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#150)]  
  
11. Özellik erişimcisi uygulayın. İstemciler için iki özellikleri açığa çıkarır: `LightColor` ve `DarkColor`. <xref:System.ComponentModel.CategoryAttribute.Category%2A> Ve <xref:System.ComponentModel.BrowsableAttribute.Browsable%2A> öznitelikleri, bu özellikler için uygulanır, özel bir "Çerçevesi." olarak adlandırılan Özellikler penceresini bölümünde özellikleri görünmesi için  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#160](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#160)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#160](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#160)]  
  
12. İşleyicileri uygulamak <xref:System.ComponentModel.BackgroundWorker> bileşenin <xref:System.ComponentModel.BackgroundWorker.DoWork> ve <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> olaylar.  
  
     <xref:System.ComponentModel.BackgroundWorker.DoWork> Olay işleyicisi uykuya geçme tarafından belirtilen milisaniye sayısı için `UpdatePeriod` ardından başlatır <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> çağırarak animasyonun kodunuzu durdurur kadar olay <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>.  
  
     <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> Olay işleyicisi metni yanıp görünümünü sağlamak için açık ve koyu durumu arasında geçiş yapar.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#180](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#180)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#180](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#180)]  
  
13. Geçersiz kılma <xref:System.Windows.Forms.Control.OnPaint%2A> animasyon etkinleştirmek için yöntemi.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#170](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#170)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#170](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#170)]  
  
14. Çözümü derlemek için F6 tuşuna basın.  
  
## <a name="create-the-marqueeborder-child-control"></a>MarqueeBorder alt denetimi oluşturma  
 `MarqueeBorder` Denetimidir biraz daha karmaşık `MarqueeText` denetim. Daha fazla özellik ve animasyon sahip <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemdir daha karmaşık. Temelde oldukça benzer `MarqueeText` denetim.  
  
 Çünkü `MarqueeBorder` denetim alt denetimleri sahip olabilir, farkında olması gereken <xref:System.Windows.Forms.Control.Layout> olaylar.  
  
#### <a name="to-create-the-marqueeborder-control"></a>MarqueeBorder denetimi oluşturmak için  
  
1.  Yeni bir ekleme **özel denetimi** öğesinin `MarqueeControlLibrary` projesi. Yeni kaynak dosyası "MarqueeBorder.", temel bir ad verin  
  
2.  Sürükleme bir <xref:System.ComponentModel.BackgroundWorker> gelen bileşen **araç** üzerine, `MarqueeBorder` denetim. Bu bileşen sağlayacak `MarqueeBorder` kendisini zaman uyumsuz olarak güncelleştirmek için denetim.  
  
3.  Özellikler penceresinde ayarlayın <xref:System.ComponentModel.BackgroundWorker> bileşenin `WorkerReportsProgess` ve <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> özelliklerine `true`. Bu ayarları izin <xref:System.ComponentModel.BackgroundWorker> düzenli aralıklarla yükseltmek için bileşen <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> olay ve zaman uyumsuz güncelleştirmeleri iptal etmek için. Daha fazla bilgi için bkz: [BackgroundWorker bileşeni](../../../../docs/framework/winforms/controls/backgroundworker-component.md).  
  
4.  Özellikler penceresinde Events düğmesini tıklayın. İşleyicileri ekleme <xref:System.ComponentModel.BackgroundWorker.DoWork> ve <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> olaylar.  
  
5.  Açık `MarqueeBorder` kaynak dosyasında **Kod düzenleyicisinde**. Dosyanın üst kısmında, şu ad alanlarından içeri aktarın:  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#20)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#20)]  
  
6.  Bildirimi değiştirme `MarqueeBorder` devralınacak <xref:System.Windows.Forms.Panel> ve uygulamak için `IMarqueeWidget` arabirimi.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#30](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#30)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#30](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#30)]  
  
7.  Yönetmek için iki numaralandırmaları bildirme `MarqueeBorder` denetimin durumunu: `MarqueeSpinDirection`, hangi ışık "Döndür" kenarlık yönünü belirler ve `MarqueeLightShape`, ışık (kare veya döngüsel) şeklini belirler. Bu bildirimler önce yerleştirin `MarqueeBorder` sınıf bildiriminin.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#97](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#97)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#97](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#97)]  
  
8.  Sunulan özellikler karşılık gelen örnek değişkenleri bildirme ve oluşturucuda başlatmaktır.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#40](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#40)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#40](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#40)]  
  
9. Uygulama `IMarqueeWidget` arabirimi.  
  
     `StartMarquee` Ve `StopMarquee` yöntemleri çağırma <xref:System.ComponentModel.BackgroundWorker> bileşenin <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> ve <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> animasyon durdurmak ve başlatmak için yöntemleri.  
  
     Çünkü `MarqueeBorder` denetim alt denetimleri içerebilir `StartMarquee` yöntemi numaralandırır tüm alt denetimleri ve çağrıları `StartMarquee` uygulayan bu `IMarqueeWidget`. `StopMarquee` Yöntemi benzer bir uygulama vardır.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#50](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#50)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#50](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#50)]  
  
10. Özellik erişimcisi uygulayın. `MarqueeBorder` Denetimi görünümünü denetlemek için çeşitli özellikler vardır.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#60](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#60)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#60](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#60)]  
  
11. İşleyicileri uygulamak <xref:System.ComponentModel.BackgroundWorker> bileşenin <xref:System.ComponentModel.BackgroundWorker.DoWork> ve <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> olaylar.  
  
     <xref:System.ComponentModel.BackgroundWorker.DoWork> Olay işleyicisi uykuya geçme tarafından belirtilen milisaniye sayısı için `UpdatePeriod` ardından başlatır <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> çağırarak animasyonun kodunuzu durdurur kadar olay <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>.  
  
     <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> Olay işleyicisi artırır, diğer ışık açık/koyu durumunu belirlenir, "temel" açık ve çağrıları konumunu <xref:System.Windows.Forms.Control.Refresh%2A> kendisini çizilecek denetimi neden yöntemi.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#90](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#90)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#90](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#90)]  
  
12. Yardımcı yöntemler uygulama `IsLit` ve `DrawLight`.  
  
     `IsLit` Yöntemi verilen konumda ışık rengini belirler. "Yakılan başlatma" ışık tarafından verilen renkte çizilir `LightColor` özelliği ve "koyu" olanlar tarafından verilen renkte çizilir `DarkColor` özelliği.  
  
     `DrawLight` Yöntemi uygun renk, Şekil ve konumu kullanarak ışık çizer.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#80](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#80)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#80](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#80)]  
  
13. Geçersiz kılma <xref:System.Windows.Forms.Control.OnLayout%2A> ve <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemleri.  
  
     <xref:System.Windows.Forms.Control.OnPaint%2A> Yöntemi çizer kenarlarında ışık `MarqueeBorder` denetim.  
  
     Çünkü <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemi bağlıdır boyutlarında `MarqueeBorder` denetime ihtiyacınız Düzen değiştirdiğinde çağırmak. Bunu başarmak için geçersiz kılma <xref:System.Windows.Forms.Control.OnLayout%2A> ve arama <xref:System.Windows.Forms.Control.Refresh%2A>.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#70](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#70)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#70](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#70)]  
  
## <a name="creating-a-custom-designer-to-shadow-and-filter-properties"></a>Özel bir tasarımcı gölge ve filtre özellikleri oluşturma  
 `MarqueeControlRootDesigner` Sınıfı kök Tasarımcısı uygulamasını sağlar. Bu tasarımcı yanı sıra Faaliyet üzerinde `MarqueeControl`, özellikle ile ilişkili bir özel Tasarımcı gerekir `MarqueeBorder` denetim. Bu tasarımcı özel kök Tasarımcısı bağlamında uygun olan özel bir davranış sağlar.  
  
 Özellikle, `MarqueeBorderDesigner` "gölge" ve belirli özellikleri filtre `MarqueeBorder` denetim, tasarım ortamı kendi etkileşim değiştirme.  
  
 Bir bileşenin özelliği erişimcisi çağrıları kesintiye uğratan "gölgeleme olarak." adı verilir Kullanıcı tarafından ayarlanan değer izlemek bir tasarımcı sağlar ve isteğe bağlı olarak bu değer tasarlanmış bileşen geçirin.  
  
 Bu örnek için <xref:System.Windows.Forms.Control.Visible%2A> ve <xref:System.Windows.Forms.Control.Enabled%2A> özellikleri gölgeli tarafından `MarqueeBorderDesigner`, gelen yapma kullanıcı engeller `MarqueeBorder` denetim görünmez ya da Tasarım zamanı sırasında devre dışı.  
  
 Tasarımcılar ayrıca ekleyebilir ve özellikleri Kaldır. Bu örnek için <xref:System.Windows.Forms.Control.Padding%2A> özelliği için tasarım zamanında kaldırılacak `MarqueeBorder` denetimi programlı olarak ayarlar tarafından belirtilen ışık boyutuna göre doldurma `LightSize` özelliği.  
  
 İçin temel sınıf `MarqueeBorderDesigner` olan <xref:System.ComponentModel.Design.ComponentDesigner>, öznitelikler, özellikleri ve olayları tasarım zamanında denetimi tarafından sunulan değiştirebilirsiniz yöntemleri vardır:  
  
-   <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterProperties%2A>  
  
-   <xref:System.ComponentModel.Design.ComponentDesigner.PostFilterProperties%2A>  
  
-   <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterAttributes%2A>  
  
-   <xref:System.ComponentModel.Design.ComponentDesigner.PostFilterAttributes%2A>  
  
-   <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterEvents%2A>  
  
-   <xref:System.ComponentModel.Design.ComponentDesigner.PostFilterEvents%2A>  
  
 Bir bileşenin bu yöntemleri kullanarak ortak arabirimi değiştirirken, bu kurallara uymalıdır:  
  
-   Ekleme veya öğeleri kaldırma `PreFilter` yalnızca yöntemleri  
  
-   Varolan öğeleri değiştirmek `PostFilter` yalnızca yöntemleri  
  
-   Her zaman temel uygulamayı ilk Çağır `PreFilter` yöntemleri  
  
-   Her zaman temel uygulamayı son Çağır `PostFilter` yöntemleri  
  
 Bu kurallar uymak tasarım zamanı ortamında tüm tasarımcıları tasarlanmış tüm bileşenleri tutarlı bir görünümünü sağlar.  
  
 <xref:System.ComponentModel.Design.ComponentDesigner> Sınıfı gölgeli özelliklerinin değerlerini, belirli bir kopya değişkenleri oluşturmak üzere ihtiyacına hafifletir yönetmek için bir sözlük sağlar.  
  
#### <a name="to-create-a-custom-designer-to-shadow-and-filter-properties"></a>Özel bir tasarımcı gölge ve filtre özelliklerine oluşturmak için  
  
1.  Sağ **tasarım** klasörü ve yeni bir sınıf ekleyin. Kaynak dosya "MarqueeBorderDesigner.", temel bir ad verin  
  
2.  Açık `MarqueeBorderDesigner` kaynak dosyasında **Kod düzenleyicisinde**. Dosyanın üst kısmında, şu ad alanlarından içeri aktarın:  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#420](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#420)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#420](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#420)]  
  
3.  Bildirimi değiştirme `MarqueeBorderDesigner` devralınacak <xref:System.Windows.Forms.Design.ParentControlDesigner>.  
  
     Çünkü `MarqueeBorder` denetim alt denetimleri içerebilir `MarqueeBorderDesigner` devraldığı <xref:System.Windows.Forms.Design.ParentControlDesigner>, üst-alt etkileşim işler.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#430](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#430)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#430](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#430)]  
  
4.  Temel uygulanması geçersiz kılma <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterProperties%2A>.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#450](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#450)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#450](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#450)]  
  
5.  Uygulama <xref:System.Windows.Forms.Control.Enabled%2A> ve <xref:System.Windows.Forms.Control.Visible%2A> özellikleri. Bu uygulamalar denetimin özelliklerini gölge.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#440](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#440)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#440](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#440)]  
  
## <a name="handling-component-changes"></a>Bileşen değişiklikleri işleme  
 `MarqueeControlRootDesigner` Sınıfı için özel tasarım zamanı deneyimi sağlar, `MarqueeControl` örnekleri. Tasarım zamanı işlevselliği çoğunu devralınır <xref:System.Windows.Forms.Design.DocumentDesigner> sınıfı; iki belirli özelleştirmeler uygulamak, kod olacaktır: bileşen değişiklikleri işleme ve tasarımcısı fiilleri ekleme.  
  
 Kullanıcılar Tasarım olarak kendi `MarqueeControl` örnekleri, kök Tasarımcısı değişiklikler izleyecek `MarqueeControl` ve onun alt denetimleri. Tasarım zamanı ortamı bir uygun hizmeti sunan <xref:System.ComponentModel.Design.IComponentChangeService>, bileşen durumu için izleme dönüşür.  
  
 Ortamıyla sorgulayarak bu hizmetine başvuru elde <xref:System.ComponentModel.Design.ComponentDesigner.GetService%2A> yöntemi. Sorgu başarılı olursa, Tasarımcısı için bir işleyici iliştirebilirsiniz <xref:System.ComponentModel.Design.IComponentChangeService.ComponentChanged> olay ve hangi görevleri tutarlı bir duruma tasarım zamanında korumak için gerekli olan gerçekleştirin.  
  
 Durumunda `MarqueeControlRootDesigner` sınıfı, çağıracaktır <xref:System.Windows.Forms.Control.Refresh%2A> yöntemi her `IMarqueeWidget` tarafından bulunan nesne `MarqueeControl`. Bu neden olacak `IMarqueeWidget` ana öğenin özelliklerini istediğiniz zaman kendisini uygun şekilde çizilecek nesnenin <xref:System.Windows.Forms.Control.Size%2A> değiştirilir.  
  
#### <a name="to-handle-component-changes"></a>Bileşen değişiklikleri işlemeye  
  
1.  Açık `MarqueeControlRootDesigner` kaynak dosyasında **Kod düzenleyicisinde** ve geçersiz kılma <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> yöntemi. Temel uygulamayı çağırması <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> ve sorgulama <xref:System.ComponentModel.Design.IComponentChangeService>.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#580](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#580)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#580](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#580)]  
  
2.  Uygulama <xref:System.ComponentModel.Design.IComponentChangeService.OnComponentChanged%2A> olay işleyicisi. Gönderen bileşenin türü, test ve onu ise bir `IMarqueeWidget`, çağrı kendi <xref:System.Windows.Forms.Control.Refresh%2A> yöntemi.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#560](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#560)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#560](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#560)]  
  
## <a name="adding-designer-verbs-to-your-custom-designer"></a>Özel Designer'a tasarımcısı fiilleri ekleme  
 Tasarımcı fiil, bir olay işleyicisi bağlantılı bir menü komutudur. Tasarımcı fiiller tasarım zamanında bir bileşenin kısayol menüsüne eklenir. Daha fazla bilgi için bkz. <xref:System.ComponentModel.Design.DesignerVerb>.  
  
 İki tasarımcısı fiilleri, tasarımcıları ekleyeceksiniz: **testi** ve **durdurmak Test**. Çalışma zamanı davranışını görüntülemek bu fiiller sağlayacak `MarqueeControl` tasarım zamanında. Bu eylemler eklenecek `MarqueeControlRootDesigner`.  
  
 Zaman **testi** olan çağrılan fiil olay işleyiciyi çağırır `StartMarquee` yöntemi `MarqueeControl`. Zaman **durdurmak Test** olan çağrılan fiil olay işleyiciyi çağırır `StopMarquee` yöntemi `MarqueeControl`. Uygulaması `StartMarquee` ve `StopMarquee` yöntemlerini çağıran bu yöntemleri uygulayan kapsanan denetimleri `IMarqueeWidget`, böylece her kapsanan `IMarqueeWidget` denetimleri de test katılmak.  
  
#### <a name="to-add-designer-verbs-to-your-custom-designers"></a>Özel, tasarımcıları tasarımcısı fiilleri eklemek için  
  
1.  İçinde `MarqueeControlRootDesigner` sınıf, olay işleyicileri adlı eklemek `OnVerbRunTest` ve `OnVerbStopTest`.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#570](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#570)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#570](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#570)]  
  
2.  Bu olay işleyicileri için karşılık gelen kendi tasarımcısı fiilleri bağlayın. `MarqueeControlRootDesigner` devralınan bir <xref:System.ComponentModel.Design.DesignerVerbCollection> kendi taban sınıfından. İki yeni oluşturacak <xref:System.ComponentModel.Design.DesignerVerb> nesneleri ve bunları bu koleksiyonda ekleyin <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> yöntemi.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#590](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#590)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#590](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#590)]  
  
## <a name="creating-a-custom-uitypeeditor"></a>Özel UITypeEditor oluşturma  
 Kullanıcılar için özel bir tasarım zamanı deneyimi oluşturduğunuzda, genellikle Özellikler penceresi ile özel bir etkileşim oluşturmak için tercih edilir. Oluşturarak bunu gerçekleştirebilirsiniz bir <xref:System.Drawing.Design.UITypeEditor>. Daha fazla bilgi için bkz: [nasıl yapılır: bir UI türü düzenleyici oluşturma](http://msdn.microsoft.com/library/292c6e33-8d85-4012-9b51-05835a6f6dfd).  
  
 `MarqueeBorder` Denetim Özellikleri penceresinde çeşitli özellikler sunar. Bu özelliklerin ikisi `MarqueeSpinDirection` ve `MarqueeLightShape` tarafından numaralandırmaları temsil edilir. UI türü Düzenleyici kullanımını göstermek için `MarqueeLightShape` özelliği ilişkili bir olacaktır <xref:System.Drawing.Design.UITypeEditor> sınıfı.  
  
#### <a name="to-create-a-custom-ui-type-editor"></a>Özel bir UI türü düzenleyici oluşturmak için  
  
1.  Açık `MarqueeBorder` kaynak dosyasında **Kod düzenleyicisinde**.  
  
2.  Tanımında `MarqueeBorder` sınıfı, adlı bir sınıf bildirme `LightShapeEditor` , türetilen <xref:System.Drawing.Design.UITypeEditor>.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#96](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#96)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#96](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#96)]  
  
3.  Bildirme bir <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> adlı örnek değişken `editorService`.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#92](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#92)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#92](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#92)]  
  
4.  Geçersiz kılma <xref:System.Drawing.Design.UITypeEditor.GetEditStyle%2A> yöntemi. Bu uygulama döndürür <xref:System.Drawing.Design.UITypeEditorEditStyle.DropDown>, görüntülemek nasıl Tasarım ortamını söyler `LightShapeEditor`.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#93](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#93)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#93](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#93)]  
  
5.  Geçersiz kılma <xref:System.Drawing.Design.UITypeEditor.EditValue%2A> yöntemi. Bu uygulama için tasarım ortamında sorgular bir <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> nesnesi. Başarılı, oluşturur, bir `LightShapeSelectionControl`. <xref:System.Windows.Forms.Design.IWindowsFormsEditorService.DropDownControl%2A> Yöntemi çağrılır başlatmak için `LightShapeEditor`. Bu çağrıyı yönteminden döndürülen değer tasarım ortamına döndürülür.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#94](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#94)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#94](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#94)]  
  
## <a name="creating-a-view-control-for-your-custom-uitypeeditor"></a>Bir görünümü denetimi, özel UITypeEditor için oluşturma  
  
1.  `MarqueeLightShape` Özelliğini destekleyen açık şekiller iki tür: `Square` ve `Circle`. Bu değerleri Özellikler penceresinde görüntüleme grafik ile amacıyla yalnızca kullanılan özel bir denetim oluşturur. Bu özel denetimi tarafından kullanılan, <xref:System.Drawing.Design.UITypeEditor> Özellikler penceresi ile etkileşim kurmak için.  
  
#### <a name="to-create-a-view-control-for-your-custom-ui-type-editor"></a>Bir görünüm denetimi türü Düzenleyici, özel kullanıcı Arabirimi oluşturmak için  
  
1.  Yeni bir ekleme <xref:System.Windows.Forms.UserControl> öğesinin `MarqueeControlLibrary` projesi. Yeni kaynak dosyası "LightShapeSelectionControl.", temel bir ad verin  
  
2.  İki <xref:System.Windows.Forms.Panel> gelen denetimleri **araç** üzerine `LightShapeSelectionControl`. Bunları `squarePanel` ve `circlePanel`. Yan yana düzenleyin. Ayarlama <xref:System.Windows.Forms.Control.Size%2A> özelliği hem <xref:System.Windows.Forms.Panel> için denetimler (60, 60). Ayarlama <xref:System.Windows.Forms.Control.Location%2A> özelliği `squarePanel` denetimini (8, 10). Ayarlama <xref:System.Windows.Forms.Control.Location%2A> özelliği `circlePanel` denetimini (80, 10). Son olarak, ayarlamak <xref:System.Windows.Forms.Control.Size%2A> özelliği `LightShapeSelectionControl` için (150, 80).  
  
3.  Açık `LightShapeSelectionControl` kaynak dosyasında **Kod düzenleyicisinde**. Dosyanın üst kısmında, içeri aktarma <xref:System.Windows.Forms.Design?displayProperty=nameWithType> ad alanı:  
  
```vb  
Imports System.Windows.Forms.Design  
```  
  
```csharp  
using System.Windows.Forms.Design;  
```  
  
1.  Uygulama <xref:System.Windows.Forms.Control.Click> olay işleyicileri için `squarePanel` ve `circlePanel` kontrol eder. Bu yöntemleri çağırma <xref:System.Windows.Forms.Design.IWindowsFormsEditorService.CloseDropDown%2A> özel sonuna <xref:System.Drawing.Design.UITypeEditor> oturum düzenleme.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#390](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#390)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#390](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#390)]  
  
2.  Bildirme bir <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> adlı örnek değişken `editorService`.  
  
```vb  
Private editorService As IWindowsFormsEditorService  
```  
  
```csharp  
private IWindowsFormsEditorService editorService;  
```  
  
1.  Bildirme bir `MarqueeLightShape` adlı örnek değişken `lightShapeValue`.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#330](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#330)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#330](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#330)]  
  
2.  İçinde `LightShapeSelectionControl` oluşturucusu, attach <xref:System.Windows.Forms.Control.Click> olay işleyicilerine `squarePanel` ve `circlePanel` denetimleri <xref:System.Windows.Forms.Control.Click> olaylar. Ayrıca atayan bir oluşturucu aşırı tanımlayan `MarqueeLightShape` tasarım ortamına değerinden `lightShapeValue` alan.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#340](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#340)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#340](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#340)]  
  
3.  İçinde <xref:System.ComponentModel.Component.Dispose%2A> yöntemi, detach <xref:System.Windows.Forms.Control.Click> olay işleyicileri.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#350](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#350)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#350](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#350)]  
  
4.  İçinde **Çözüm Gezgini**, tıklatın **tüm dosyaları göster** düğmesi. LightShapeSelectionControl.Designer.cs veya LightShapeSelectionControl.Designer.vb dosyasını açın ve varsayılan tanımını Kaldır <xref:System.ComponentModel.Component.Dispose%2A> yöntemi.  
  
5.  Uygulama `LightShape` özelliği.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#360](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#360)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#360](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#360)]  
  
6.  Geçersiz kılma <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemi. Bu uygulama doldurulmuş kare ve daire çizer. Bir şekli veya diğer çevresinde kenarlık çizerek, seçilen değeri vurgulayın.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#380](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#380)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#380](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#380)]  
  
## <a name="testing-your-custom-control-in-the-designer"></a>Özel Denetim Tasarımcısı'nda test etme  
 Bu noktada, yapı `MarqueeControlLibrary` projesi. Öğesinden devralan bir denetim oluşturarak, uygulamanızı test `MarqueeControl` sınıfı ve bir form üzerinde kullanma.  
  
#### <a name="to-create-a-custom-marqueecontrol-implementation"></a>Özel bir MarqueeControl uygulamasını oluşturmak için  
  
1.  Açık `DemoMarqueeControl` Windows Forms Tasarımcısı'nda. Bunun bir örneğini oluşturur `DemoMarqueeControl` yazın ve bir örnekte görüntüler `MarqueeControlRootDesigner` türü.  
  
2.  İçinde **araç**, açık **MarqueeControlLibrary bileşenleri** sekmesi. Göreceğiniz `MarqueeBorder` ve `MarqueeText` denetimleri seçilebilir.  
  
3.  Bir örneğini sürükleyin `MarqueeBorder` üzerine kontrol `DemoMarqueeControl` tasarım yüzeyi. Bu yerleştirme `MarqueeBorder` üst denetim denetimine.  
  
4.  Bir örneğini sürükleyin `MarqueeText` üzerine kontrol `DemoMarqueeControl` tasarım yüzeyi.  
  
5.  Çözümü oluşturun.  
  
6.  Sağ `DemoMarqueeControl` ve kısayol menüsünden öğesini seçin **testi** animasyonu başlatmak için seçeneği. Tıklatın **durdurmak Test** animasyonu durdurmak için.  
  
7.  Açık **Form1** Tasarım görünümünde.  
  
8.  İki yerleştirin <xref:System.Windows.Forms.Button> form üzerinde denetimleri. Bunları `startButton` ve `stopButton`, değiştirip <xref:System.Windows.Forms.Control.Text%2A> değerlerini özellik **Başlat** ve **durdurmak**sırasıyla.  
  
9. Uygulama <xref:System.Windows.Forms.Control.Click> olay işleyicileri her ikisi için de <xref:System.Windows.Forms.Button> kontrol eder.  
  
10. İçinde **araç**, açık **MarqueeControlTest bileşenleri** sekmesi. Göreceğiniz `DemoMarqueeControl` seçim için kullanılabilir.  
  
11. Bir örneğini sürükleyin `DemoMarqueeControl` üzerine **Form1** tasarım yüzeyi.  
  
12. İçinde <xref:System.Windows.Forms.Control.Click> olay işleyicilerini çağırma `Start` ve `Stop` yöntemlere `DemoMarqueeControl`.  
  
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
  
1.  Ayarlama `MarqueeControlTest` proje başlangıç projesi olarak ve çalıştırın. Form görüntüleme görürsünüz, `DemoMarqueeControl`. Tıklatın **Başlat** animasyon başlamak için Başlat. Yanıp metin ve kenarlığın taşıma ışık görmeniz gerekir.  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 `MarqueeControlLibrary` Basit bir uygulama özel denetimler ve ilişkili tasarımcıları ortaya koyar. Bu örnek daha karmaşık birkaç şekilde yapabilirsiniz:  
  
-   Özellik değerlerini değiştirmek `DemoMarqueeControl` Tasarımcısı'nda. Daha fazla Ekle `MarqueBorder` denetler ve iç içe geçmiş efekti oluşturmak için üst örneklerini içinde yerleştirme. Deneme için farklı ayarlarla `UpdatePeriod` ve açık ilgili özellikler.  
  
-   Kendi uygulamalarında Yazar `IMarqueeWidget`. Örneğin, yanıp sönen "neon işareti" veya animasyonlu bir oturum ile birden fazla görüntü oluşturduğunuz olabilir.  
  
-   Tasarım zamanı deneyimi özelleştirin. ' Den daha fazla özellik gölgeleme çalışabilir <xref:System.Windows.Forms.Control.Enabled%2A> ve <xref:System.Windows.Forms.Control.Visible%2A>, ve yeni özellikleri ekleyebilirsiniz. Alt denetimler yerleştirme gibi genel görevleri basitleştirmek için yeni tasarımcısı fiilleri ekleyin.  
  
-   Lisans `MarqueeControl`. Daha fazla bilgi için bkz: [nasıl yapılır: Lisans bileşenleri ve denetimleri](http://msdn.microsoft.com/library/8e66c1ed-a445-4b26-8185-990b6e2bbd57).  
  
-   Denetimlerinizin nasıl serileştirilen ve kod kendileri için nasıl oluşturulacağını denetler. Daha fazla bilgi için bkz: [dinamik kaynak kodu oluşturma ve derleme](../../../../docs/framework/reflection-and-codedom/dynamic-source-code-generation-and-compilation.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.UserControl>  
 <xref:System.Windows.Forms.Design.ParentControlDesigner>  
 <xref:System.Windows.Forms.Design.DocumentDesigner>  
 <xref:System.ComponentModel.Design.IRootDesigner>  
 <xref:System.ComponentModel.Design.DesignerVerb>  
 <xref:System.Drawing.Design.UITypeEditor>  
 <xref:System.ComponentModel.BackgroundWorker>  
 [Nasıl yapılır: tasarım-zamanı özellikleri yararlanan bir Windows Forms denetimi oluşturma](http://msdn.microsoft.com/library/8e0bad0e-56f3-43d2-bf63-a945c654d97c)  
 [Tasarım zamanı desteği genişletme](http://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)  
 [Özel tasarımcıları](http://msdn.microsoft.com/library/ca11988e-d38e-44d8-a05d-71362ae7844d)  
 [.NET şekli kitaplığı: Örnek Tasarımcısı](http://windowsforms.net/articles/shapedesigner.aspx)
