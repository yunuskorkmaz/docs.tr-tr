---
title: Visual Studio tasarım zamanı özelliklerinden faydalanan bir denetim oluşturma
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7166b4203c54ab31f1d929c85cf1e6481ff120f8
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744083"
---
# <a name="walkthrough-create-a-control-that-takes-advantage-of-design-time-features"></a>İzlenecek yol: tasarım zamanı özelliklerinden faydalanan bir denetim oluşturma

Özel bir denetim için tasarım zamanı deneyimi, ilişkili bir özel tasarımcı Authoring ile geliştirilebilir.

Bu makalede özel bir denetim için nasıl özel tasarımcı oluşturacağınız açıklanmıştır. `MarqueeControl` bir türü ve `MarqueeControlRootDesigner`adlı ilişkili tasarımcı sınıfını uygulayacaksınız.

`MarqueeControl` türü, animasyonlu ışıklar ve yanıp sönen metinle benzer bir tiyatro çerçevesine benzer bir ekran uygular.

Bu denetim için tasarımcı, tasarım ortamıyla birlikte etkileşimde bulunur ve özel bir tasarım zamanı deneyimi sağlar. Özel tasarımcı sayesinde, bir özel `MarqueeControl` uygulamasını animasyonlu ışıklar ve yanıp sönen metni birçok birleşimde bir araya getirebilirsiniz. Bir form üzerinde, diğer Windows Forms denetimleri gibi, birleştirilmiş denetimi kullanabilirsiniz.

Bu yönergeyi tamamladığınızda, özel denetiminiz aşağıdakine benzer şekilde görünür:

![Metin ve Başlat ve Durdur düğmelerini gösteren bir kayan yazıyı gösteren uygulama.](./media/creating-a-wf-control-design-time-features/demo-marquee-control.gif)

Tam kod listesi için, bkz. [nasıl yapılır: tasarım zamanı özelliklerinden faydalanan Windows Forms denetimi oluşturma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/307hck25(v=vs.120)).

## <a name="prerequisites"></a>Prerequisites

Bu izlenecek yolu tamamlamak için Visual Studio gerekir.

## <a name="create-the-project"></a>Projeyi oluşturma

İlk adım uygulama projesini oluşturmaktır. Bu projeyi, özel denetimi barındıran uygulamayı oluşturmak için kullanacaksınız.

Visual Studio 'da yeni bir Windows Forms uygulama projesi oluşturun ve **MarqueeControlTest**olarak adlandırın.

## <a name="create-the-control-library-project"></a>Denetim kitaplığı projesi oluşturma

1. Çözüme bir Windows Forms denetim kitaplığı projesi ekleyin. Projeyi **MarqueeControlLibrary**olarak adlandırın.

2. **Çözüm Gezgini**kullanarak, tercih ettiğiniz dile bağlı olarak, "UserControl1.cs" veya "UserControl1. vb" adlı kaynak dosyayı silerek projenin varsayılan denetimini silin.

3. `MarqueeControlLibrary` projesine yeni bir <xref:System.Windows.Forms.UserControl> öğesi ekleyin. Yeni kaynak dosyasına **MarqueeControl**temel adını verin.

4. **Çözüm Gezgini**kullanarak, `MarqueeControlLibrary` projesinde yeni bir klasör oluşturun.

5. **Tasarım** klasörüne sağ tıklayın ve yeni bir sınıf ekleyin. **MarqueeControlRootDesigner**olarak adlandırın.

6. System. Design derlemesinden türler kullanmanız gerekir, bu nedenle bu başvuruyu `MarqueeControlLibrary` projesine ekleyin.

## <a name="reference-the-custom-control-project"></a>Özel denetim projesine başvur

Özel denetimi test etmek için `MarqueeControlTest` projesi kullanacaksınız. `MarqueeControlLibrary` derlemesine bir proje başvurusu eklediğinizde test projesi özel denetimden haberdar olur.

`MarqueeControlTest` projesinde, `MarqueeControlLibrary` derlemesine bir proje başvurusu ekleyin. `MarqueeControlLibrary` derlemesine doğrudan başvurmak yerine **Başvuru Ekle** Iletişim kutusundaki **Projeler** sekmesini kullandığınızdan emin olun.

## <a name="define-a-custom-control-and-its-custom-designer"></a>Özel bir denetim ve kendi özel tasarımcısını tanımlama

Özel denetiminiz <xref:System.Windows.Forms.UserControl> sınıfından türecektir. Bu, denetiminizin diğer denetimleri içermesini sağlar ve denetimi, varsayılan işlevselliğin harika olmasını sağlar.

Özel denetiminizin ilişkili bir özel Tasarımcısı olacak. Bu, özel denetiminiz için özel olarak uyarlanmış benzersiz bir tasarım deneyimi oluşturmanıza olanak sağlar.

<xref:System.ComponentModel.DesignerAttribute> sınıfını kullanarak denetimi Tasarımcı ile ilişkilendirirsiniz. Özel denetiminizin tüm tasarım zamanı davranışını geliştirmekte olduğunuzdan, özel tasarımcı <xref:System.ComponentModel.Design.IRootDesigner> arabirimini uygular.

### <a name="to-define-a-custom-control-and-its-custom-designer"></a>Özel bir denetim ve özel tasarımcı tanımlamak için

1. `MarqueeControl` kaynak dosyasını **kod düzenleyicisinde**açın. Dosyanın en üstüne aşağıdaki ad alanlarını içeri aktarın:

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#220](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#220)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#220](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#220)]

2. `MarqueeControl` sınıfı bildirimine <xref:System.ComponentModel.DesignerAttribute> ekleyin. Bu, özel denetimi Tasarımcı ile ilişkilendirir.

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#240](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#240)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#240](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#240)]

3. `MarqueeControlRootDesigner` kaynak dosyasını **kod düzenleyicisinde**açın. Dosyanın en üstüne aşağıdaki ad alanlarını içeri aktarın:

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#520](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#520)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#520](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#520)]

4. `MarqueeControlRootDesigner` bildirimini <xref:System.Windows.Forms.Design.DocumentDesigner> sınıfından devralacak şekilde değiştirin. **Araç kutusu**ile tasarımcı etkileşimini belirtmek için <xref:System.ComponentModel.ToolboxItemFilterAttribute> uygulayın.

   > [!NOTE]
   > `MarqueeControlRootDesigner` sınıfının tanımı, MarqueeControlLibrary. Design adlı bir ad alanı içine alınmıştır. Bu bildirim, tasarımcıyı tasarımla ilgili türler için ayrılmış özel bir ad alanına koyar.

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#530](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#530)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#530](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#530)]

5. `MarqueeControlRootDesigner` sınıfı için oluşturucuyu tanımlayın. Oluşturucu gövdesine <xref:System.Diagnostics.Trace.WriteLine%2A> bir ifade ekleyin. Bu, hata ayıklama için yararlı olacaktır.

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#540](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#540)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#540](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#540)]

## <a name="create-an-instance-of-your-custom-control"></a>Özel denetiminizin bir örneğini oluşturma

1. `MarqueeControlTest` projesine yeni bir <xref:System.Windows.Forms.UserControl> öğesi ekleyin. Yeni kaynak dosyasına **DemoMarqueeControl**temel adını verin.

2. **Kod düzenleyicisinde**`DemoMarqueeControl` dosyasını açın. Dosyanın en üstüne `MarqueeControlLibrary` ad alanını içeri aktarın:

   ```vb
   Imports MarqueeControlLibrary
   ```

   ```csharp
   using MarqueeControlLibrary;
   ```

3. `DemoMarqueeControl` bildirimini `MarqueeControl` sınıfından devralacak şekilde değiştirin.

4. Projeyi oluşturun.

5. Windows Form Tasarımcısı Form1 ' i açın.

6. **Araç kutusunda** **MarqueeControlTest Components** sekmesini bulun ve açın. **Araç kutusundan** bir `DemoMarqueeControl` form üzerine sürükleyin.

7. Projeyi oluşturun.

## <a name="set-up-the-project-for-design-time-debugging"></a>Projeyi tasarım zamanı hata ayıklama için ayarlama

Özel bir tasarım zamanı deneyimi geliştirirken, denetimlerinizin ve bileşenlerinizin hata ayıklaması gerekir. Projenizi tasarım zamanında hata ayıklamaya izin verecek şekilde kurmak için basit bir yol vardır. Daha fazla bilgi için bkz. [Izlenecek yol: tasarım zamanında özel Windows Forms Denetimlerinde hata ayıklama](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md).

1. `MarqueeControlLibrary` projesine sağ tıklayın ve **Özellikler**' i seçin.

2. **MarqueeControlLibrary Özellik sayfaları** Iletişim kutusunda **hata ayıklama** sayfasını seçin.

3. **Başlangıç eylemi** bölümünde **dış program Başlat**' ı seçin. Visual Studio 'nun ayrı bir örneğinde hata ayıkladığınızda, Visual Studio IDE 'ye gözatabilmek için üç nokta (Visual](./media/visual-studio-ellipsis-button.png)Studio 'nun Özellikler penceresi![) düğmesini tıklatın. Yürütülebilir dosyanın adı devenv. exe ' dir ve varsayılan konuma yüklediyseniz, yolu *% ProgramFiles (x86)% \ Microsoft Visual Studio\2019\\\<edition > \Common7\IDE\devenv.exe*olur.

4. İletişim kutusunu kapatmak için **Tamam ' ı** seçin.

5. Bu hata ayıklama yapılandırmasını etkinleştirmek için MarqueeControlLibrary projesine sağ tıklayın ve **Başlangıç projesi olarak ayarla** ' yı seçin.

## <a name="checkpoint"></a>Checkpoint

Artık özel denetiminizin tasarım zamanı davranışını hata ayıklamaya hazırsınız. Hata ayıklama ortamının doğru şekilde ayarlandığını belirledikten sonra, özel denetim ve özel tasarımcı arasındaki ilişkilendirmeyi test edersiniz.

### <a name="to-test-the-debugging-environment-and-the-designer-association"></a>Hata ayıklama ortamını ve tasarımcı ilişkilendirmesini test etmek için

1. **Kod düzenleyicisinde** MarqueeControlRootDesigner kaynak dosyasını açın ve <xref:System.Diagnostics.Trace.WriteLine%2A> ifadesine bir kesme noktası yerleştirin.

2. Hata ayıklama oturumu başlatmak için **F5** tuşuna basın.

   Visual Studio 'nun yeni bir örneği oluşturulur.

3. Visual Studio 'nun yeni örneğinde, MarqueeControlTest çözümünü açın. **Dosya** menüsünden **son projeler** ' i seçerek çözümü kolayca bulabilirsiniz. MarqueeControlTest. sln çözüm dosyası en son kullanılan dosya olarak listelenecektir.

4. Tasarımcıda `DemoMarqueeControl` açın.

   Visual Studio 'nun hata ayıklama örneği, kesme noktasında odak ve yürütme işlemini alır. Hata ayıklama oturumuna devam etmek için **F5** tuşuna basın.

Bu noktada, özel denetiminizi ve onunla ilişkili özel tasarımcıyı geliştirip hata ayıklamanızın her şey vardır. Bu makalenin geri kalanında, denetimin ve tasarımcının özelliklerini uygulama ayrıntılarına yoğunlaşmaktadır.

## <a name="implement-the-custom-control"></a>Özel denetimi uygulama

`MarqueeControl`, çok sayıda özelleştirmeye sahip bir <xref:System.Windows.Forms.UserControl>. İki yöntem sunar: kayan yazı animasyonunu Başlatan `Start`ve animasyonu durduran `Stop`. `MarqueeControl`, `IMarqueeWidget` arabirimini uygulayan alt denetimler içerdiğinden, her bir alt denetimi `Start` ve `StartMarquee` uygulayan her bir alt denetimde sırasıyla `StopMarquee` ve `IMarqueeWidget`yöntemlerini çağıran `Stop`.

`MarqueeBorder` ve `MarqueeText` denetimlerinin görünümü düzene bağlıdır, bu nedenle `MarqueeControl` <xref:System.Windows.Forms.Control.OnLayout%2A> yöntemini geçersiz kılar ve bu türün alt denetimlerinde <xref:System.Windows.Forms.Control.PerformLayout%2A> çağırır.

Bu, `MarqueeControl` özelleştirmelerin bir kapsamını. Çalışma zamanı özellikleri `MarqueeBorder` ve `MarqueeText` denetimleri tarafından uygulanır ve tasarım zamanı özellikleri `MarqueeBorderDesigner` ve `MarqueeControlRootDesigner` sınıfları tarafından uygulanır.

### <a name="to-implement-your-custom-control"></a>Özel denetiminizi uygulamak için

1. `MarqueeControl` kaynak dosyasını **kod düzenleyicisinde**açın. `Start` ve `Stop` yöntemlerini uygulayın.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#260](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#260)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#260](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#260)]

2. Geçersiz kılma <xref:System.Windows.Forms.Control.OnLayout%2A> yöntemi.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#270](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#270)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#270](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#270)]

## <a name="create-a-child-control-for-your-custom-control"></a>Özel denetiminiz için bir alt denetim oluşturma

`MarqueeControl` iki tür alt denetimi barındırır: `MarqueeBorder` denetimi ve `MarqueeText` denetimi.

- `MarqueeBorder`: Bu denetim, kenarları etrafında "ışıklar" kenarlığını boyar. Kenarlıkta bulunan ışıklar, kenarlık etrafında taşınıyor gibi görünürler. Işıklarının flaşın `UpdatePeriod`adlı bir özellik tarafından denetlenme hızı. Diğer birçok özel özellik, denetimin görünümünün diğer yönlerini tespit. `StartMarquee` ve `StopMarquee`olarak adlandırılan iki yöntem animasyonun ne zaman başlayacağını ve durdurduğunu denetler.

- `MarqueeText`: Bu denetim yanıp sönen bir dizeyi boyar. `MarqueeBorder` denetimi gibi, metnin yanıp sönebileceği hız, `UpdatePeriod` özelliği tarafından kontrol edilir. `MarqueeText` denetimde Ayrıca, `MarqueeBorder` denetimiyle ortak olan `StartMarquee` ve `StopMarquee` yöntemleri de vardır.

Tasarım zamanında `MarqueeControlRootDesigner`, bu iki denetim türünün herhangi bir kombinasyondaki bir `MarqueeControl` eklenmesine izin verir.

İki denetimin ortak özellikleri, `IMarqueeWidget`adlı bir arabirimle birleştirilir. Bu, `MarqueeControl` tüm seçim çerçevesine ilişkin alt denetimleri bulmasını ve özel bir işleme sunmasını sağlar.

Düzenli animasyon özelliğini uygulamak için, <xref:System.ComponentModel?displayProperty=nameWithType> ad alanındaki <xref:System.ComponentModel.BackgroundWorker> nesneleri kullanacaksınız. <xref:System.Windows.Forms.Timer> nesneleri kullanabilirsiniz, ancak birçok `IMarqueeWidget` nesnesi mevcut olduğunda, tek kullanıcı arabirimi iş parçacığı animasyonla devam edemiyor olabilir.

### <a name="to-create-a-child-control-for-your-custom-control"></a>Özel denetiminiz için bir alt denetim oluşturmak için

1. `MarqueeControlLibrary` projesine yeni bir sınıf öğesi ekleyin. Yeni kaynak dosyasına "Imarqueepencere öğesi" için temel adı verin.

2. **Kod düzenleyicisinde** `IMarqueeWidget` kaynak dosyasını açın ve `class` bildirimi `interface`olarak değiştirin:

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/imarqueewidget.cs#2)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/imarqueewidget.vb#2)]

3. İki yöntemi ve kayan yazı animasyonunu işleyen bir özelliği göstermek için `IMarqueeWidget` arabirimine aşağıdaki kodu ekleyin:

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/imarqueewidget.cs#3)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/imarqueewidget.vb#3)]

4. `MarqueeControlLibrary` projesine yeni bir **özel denetim** öğesi ekleyin. Yeni kaynak dosyasına "MarqueeText" temel adını verin.

5. **Araç kutusundan** bir <xref:System.ComponentModel.BackgroundWorker> bileşenini `MarqueeText` denetimine sürükleyin. Bu bileşen `MarqueeText` denetiminin kendisini zaman uyumsuz olarak güncelleştirmesine izin verir.

6. **Özellikler** penceresinde, <xref:System.ComponentModel.BackgroundWorker> bileşenin `WorkerReportsProgress` ve <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> özelliklerini **doğru**olarak ayarlayın. Bu ayarlar <xref:System.ComponentModel.BackgroundWorker> bileşeninin düzenli olarak <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> olayını kullanmasına ve zaman uyumsuz güncelleştirmeleri iptal edebilmesini sağlar.

   Daha fazla bilgi için bkz. [BackgroundWorker Component](backgroundworker-component.md).

7. `MarqueeText` kaynak dosyasını **kod düzenleyicisinde**açın. Dosyanın en üstüne aşağıdaki ad alanlarını içeri aktarın:

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#120](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#120)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#120](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#120)]

8. <xref:System.Windows.Forms.Label> devralması ve `IMarqueeWidget` arabirimini uygulamak için `MarqueeText` bildirimini değiştirin:

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#130](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#130)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#130](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#130)]

9. Gösterilen özelliklere karşılık gelen örnek değişkenlerini bildirin ve bunları oluşturucuda başlatın. `isLit` alanı, metnin `LightColor` özelliği tarafından verilen renkte boyanmış olup olmayacağını belirler.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#140](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#140)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#140](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#140)]

10. Uygulama `IMarqueeWidget` arabirimi.

    `StartMarquee` ve `StopMarquee` yöntemleri, animasyonu başlatmak ve durdurmak için <xref:System.ComponentModel.BackgroundWorker> bileşenin <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> ve <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> yöntemlerini çağırır.

    <xref:System.ComponentModel.CategoryAttribute.Category%2A> ve <xref:System.ComponentModel.BrowsableAttribute.Browsable%2A> öznitelikleri `UpdatePeriod` özelliğine uygulanır, bu nedenle "kayan yazı" adlı Özellikler penceresi özel bir bölümünde görünür.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#150](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#150)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#150](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#150)]

11. Özellik erişimcileri uygulayın. İstemciler için iki özelliği kullanıma sunacaksınız: `LightColor` ve `DarkColor`. <xref:System.ComponentModel.CategoryAttribute.Category%2A> ve <xref:System.ComponentModel.BrowsableAttribute.Browsable%2A> öznitelikleri bu özelliklere uygulanır, bu nedenle Özellikler "kayan yazı" adlı Özellikler penceresi özel bir bölümünde görüntülenir.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#160](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#160)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#160](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#160)]

12. <xref:System.ComponentModel.BackgroundWorker> bileşenin <xref:System.ComponentModel.BackgroundWorker.DoWork> ve <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> olayları için işleyicileri uygulayın.

    <xref:System.ComponentModel.BackgroundWorker.DoWork> olay işleyicisi, `UpdatePeriod` tarafından belirtilen milisaniye sayısı için uyku moduna geçer, kodunuz <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>çağırarak animasyonu durdurana kadar <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> olayını oluşturur.

    <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> olay işleyicisi, yanıp sönünün görünümünü sağlamak için ışığın ve koyu durumunun arasındaki metni değiştirir.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#180](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#180)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#180](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#180)]

13. Animasyonu etkinleştirmek için <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemini geçersiz kılın.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#170](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#170)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#170](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#170)]

14. Çözümü derlemek için **F6** tuşuna basın.

## <a name="create-the-marqueeborder-child-control"></a>MarqueeBorder alt denetimini oluşturma

`MarqueeBorder` denetimi `MarqueeText` denetiminden biraz daha karmaşıktır. Daha fazla özelliğe sahiptir ve <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemindeki animasyon daha fazla yer alır. Prensibi, `MarqueeText` denetimine oldukça benzerdir.

`MarqueeBorder` denetimin alt denetimleri olabileceğinden, bu, <xref:System.Windows.Forms.Control.Layout> olaylarının farkında olması gerekir.

### <a name="to-create-the-marqueeborder-control"></a>MarqueeBorder denetimini oluşturmak için

1. `MarqueeControlLibrary` projesine yeni bir **özel denetim** öğesi ekleyin. Yeni kaynak dosyasına "MarqueeBorder" temel adını verin.

2. **Araç kutusundan** bir <xref:System.ComponentModel.BackgroundWorker> bileşenini `MarqueeBorder` denetimine sürükleyin. Bu bileşen `MarqueeBorder` denetiminin kendisini zaman uyumsuz olarak güncelleştirmesine izin verir.

3. **Özellikler** penceresinde, <xref:System.ComponentModel.BackgroundWorker> bileşenin `WorkerReportsProgress` ve <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> özelliklerini **doğru**olarak ayarlayın. Bu ayarlar <xref:System.ComponentModel.BackgroundWorker> bileşeninin düzenli olarak <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> olayını kullanmasına ve zaman uyumsuz güncelleştirmeleri iptal edebilmesini sağlar. Daha fazla bilgi için bkz. [BackgroundWorker Component](backgroundworker-component.md).

4. **Özellikler** penceresinde, **Olaylar** düğmesini seçin. <xref:System.ComponentModel.BackgroundWorker.DoWork> ve <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> olayları için işleyiciler iliştirin.

5. `MarqueeBorder` kaynak dosyasını **kod düzenleyicisinde**açın. Dosyanın en üstüne aşağıdaki ad alanlarını içeri aktarın:

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#20)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#20)]

6. `MarqueeBorder` bildirimini <xref:System.Windows.Forms.Panel> ve `IMarqueeWidget` arabirimini uygulayacak şekilde değiştirin.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#30)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#30)]

7. `MarqueeBorder` denetiminin durumunu yönetmek için iki sabit listesi bildirin: `MarqueeSpinDirection`, ışıklarının etrafında "döndürme" ve ışıklarının şeklini belirleyen `MarqueeLightShape`(kare veya dairesel) belirleyen yönü belirler. Bu bildirimleri `MarqueeBorder` Sınıf bildiriminden önce yerleştirin.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#97](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#97)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#97](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#97)]

8. Gösterilen özelliklere karşılık gelen örnek değişkenlerini bildirin ve bunları oluşturucuda başlatın.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#40](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#40)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#40](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#40)]

9. Uygulama `IMarqueeWidget` arabirimi.

    `StartMarquee` ve `StopMarquee` yöntemleri, animasyonu başlatmak ve durdurmak için <xref:System.ComponentModel.BackgroundWorker> bileşenin <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> ve <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> yöntemlerini çağırır.

    `MarqueeBorder` denetimi alt denetimler içerebildiğinden, `StartMarquee` yöntemi tüm alt denetimleri numaralandırır ve `IMarqueeWidget`uygulamalarındaki `StartMarquee` çağırır. `StopMarquee` yöntemi benzer bir uygulamaya sahiptir.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#50](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#50)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#50](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#50)]

10. Özellik erişimcileri uygulayın. `MarqueeBorder` denetiminin görünümünü denetlemek için birkaç özelliği vardır.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#60](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#60)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#60](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#60)]

11. <xref:System.ComponentModel.BackgroundWorker> bileşenin <xref:System.ComponentModel.BackgroundWorker.DoWork> ve <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> olayları için işleyicileri uygulayın.

    <xref:System.ComponentModel.BackgroundWorker.DoWork> olay işleyicisi, `UpdatePeriod` tarafından belirtilen milisaniye sayısı için uyku moduna geçer, kodunuz <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>çağırarak animasyonu durdurana kadar <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> olayını oluşturur.

    <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> olay işleyicisi, diğer ışıklarının açık/koyu durumunun belirlendiği "temel" Işığın konumunu arttırır ve denetimin kendisini yeniden çizmeyi sağlamak için <xref:System.Windows.Forms.Control.Refresh%2A> yöntemini çağırır.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#90](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#90)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#90](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#90)]

12. Yardımcı yöntemleri `IsLit` ve `DrawLight`uygulayın.

    `IsLit` yöntemi, belirli bir konumdaki ışığın rengini belirler. "Aydınlatmalı" olan ışıklar `LightColor` özelliği tarafından verilen renkte çizilir ve "koyu" olanlar `DarkColor` özelliği tarafından verilen renkte çizilir.

    `DrawLight` yöntemi uygun renk, şekil ve konumu kullanarak bir ışık çizer.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#80](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#80)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#80](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#80)]

13. <xref:System.Windows.Forms.Control.OnLayout%2A> ve <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemlerini geçersiz kılın.

    <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemi, ışıkları `MarqueeBorder` denetiminin kenarları üzerinde çizer.

    <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemi `MarqueeBorder` denetiminin boyutlarına bağlı olduğundan, düzen her değiştiğinde onu çağırmanız gerekir. Bunu başarmak için <xref:System.Windows.Forms.Control.OnLayout%2A> geçersiz kılın ve <xref:System.Windows.Forms.Control.Refresh%2A>çağırın.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#70](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#70)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#70](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#70)]

## <a name="create-a-custom-designer-to-shadow-and-filter-properties"></a>Gölge ve filtre özelliklerine özel tasarımcı oluşturma

`MarqueeControlRootDesigner` sınıfı kök Tasarımcı için uygulama sağlar. `MarqueeControl`üzerinde çalışan bu tasarımcıya ek olarak, `MarqueeBorder` denetimiyle özellikle ilişkilendirilmiş özel bir tasarımcı gerekir. Bu tasarımcı, özel kök tasarlayıcı bağlamında uygun olan özel davranışı sağlar.

Özellikle, `MarqueeBorderDesigner`, `MarqueeBorder` denetimindeki belirli özellikleri "gölgeleyip" filtreleyecek ve tasarım ortamıyla etkileşimini değiştirmiş.

Bir bileşenin Özellik erişimcisine yönelik kesintiye uğratan çağrı, "gölgeleme" olarak bilinir. Bir tasarımcının Kullanıcı tarafından ayarlanan değeri izlemesine ve isteğe bağlı olarak bu değeri tasarlanmakta olan bileşene iletmenize olanak tanır.

Bu örnekte, <xref:System.Windows.Forms.Control.Visible%2A> ve <xref:System.Windows.Forms.Control.Enabled%2A> özellikleri `MarqueeBorderDesigner`tarafından gölgelendirilecektir. Bu, kullanıcının tasarım zamanı sırasında `MarqueeBorder` denetimini görünmez veya devre dışı yapmasını engeller.

Tasarımcılar Ayrıca özellikler ekleyebilir ve kaldırabilir. Bu örnekte, <xref:System.Windows.Forms.Control.Padding%2A> özelliği tasarım zamanında kaldırılacak, çünkü `MarqueeBorder` denetimi program aracılığıyla `LightSize` özelliği tarafından belirtilen ışıklarının boyutuna göre doldurma ayarlıyor.

`MarqueeBorderDesigner` için temel sınıf, tasarım zamanında bir denetim tarafından açığa çıkarılan öznitelikleri, özellikleri ve olayları değiştirebilen Yöntemler içeren <xref:System.ComponentModel.Design.ComponentDesigner>.

- <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterProperties%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PostFilterProperties%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterAttributes%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PostFilterAttributes%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterEvents%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PostFilterEvents%2A>

Bu yöntemleri kullanarak bir bileşenin genel arabirimini değiştirirken bu kuralları izleyin:

- Yalnızca `PreFilter` metotlarda öğe ekleme veya kaldırma

- Yalnızca `PostFilter` metotlarda bulunan öğeleri değiştir

- `PreFilter` metotlarında her zaman temel uygulamayı çağır

- `PostFilter` metotlarında her zaman temel uygulamayı çağırın

Bu kurallara uymak, tasarım zamanı ortamındaki tüm tasarımcılarının tasarlanmakta olan tüm bileşenlerin tutarlı bir görünümüne sahip olmasını sağlar.

<xref:System.ComponentModel.Design.ComponentDesigner> sınıfı, gölgelendirilmiş özelliklerin değerlerini yönetmeye yönelik bir sözlük sağlar, bu da size belirli örnek değişkenleri oluşturma gereksinimini sizi maliyetinden kurtarır.

### <a name="to-create-a-custom-designer-to-shadow-and-filter-properties"></a>Gölge ve filtre özelliklerine özel bir tasarımcı oluşturmak için

1. **Tasarım** klasörüne sağ tıklayın ve yeni bir sınıf ekleyin. Kaynak dosyaya **MarqueeBorderDesigner**temel adını verin.

2. MarqueeBorderDesigner kaynak dosyasını **kod düzenleyicisinde**açın. Dosyanın en üstüne aşağıdaki ad alanlarını içeri aktarın:

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#420](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#420)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#420](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#420)]

3. `MarqueeBorderDesigner` bildirimi <xref:System.Windows.Forms.Design.ParentControlDesigner>' dan devralacak şekilde değiştirin.

    `MarqueeBorder` denetim alt denetimler içerebildiğinden, `MarqueeBorderDesigner` üst-alt etkileşimi işleyen <xref:System.Windows.Forms.Design.ParentControlDesigner>devralır.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#430](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#430)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#430](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#430)]

4. <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterProperties%2A>temel uygulamasını geçersiz kılın.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#450](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#450)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#450](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#450)]

5. <xref:System.Windows.Forms.Control.Enabled%2A> ve <xref:System.Windows.Forms.Control.Visible%2A> özelliklerini uygulayın. Bu uygulamalar, denetimin özelliklerini gölgelendir.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#440](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#440)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#440](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#440)]

## <a name="handle-component-changes"></a>Bileşen değişikliklerini işle

`MarqueeControlRootDesigner` sınıfı, `MarqueeControl` örneklerinizin özel tasarım zamanı deneyimini sağlar. Tasarım zamanı işlevlerinin çoğu <xref:System.Windows.Forms.Design.DocumentDesigner> sınıfından devralınır. Kodunuz iki özel özelleştirme uygular: bileşen değişikliklerini işleme ve tasarımcı fiilleri ekleme.

Kullanıcılar `MarqueeControl` örneklerini tasarlarsa, kök tasarlayıcı `MarqueeControl` ve onun alt denetimlerinde yapılan değişiklikleri izler. Tasarım zamanı ortamı, bileşen durumundaki değişiklikleri izlemek için <xref:System.ComponentModel.Design.IComponentChangeService>uygun bir hizmet sunar.

<xref:System.ComponentModel.Design.ComponentDesigner.GetService%2A> yöntemiyle ortamı sorgulayarak bu hizmete bir başvuru elde edersiniz. Sorgu başarılı olursa, tasarımcı <xref:System.ComponentModel.Design.IComponentChangeService.ComponentChanged> olayı için bir işleyici iliştirebilir ve tasarım zamanında tutarlı bir durumu korumak için gereken görevleri gerçekleştirebilir.

`MarqueeControlRootDesigner` sınıfı söz konusu olduğunda, `MarqueeControl`bulunan her bir `IMarqueeWidget` nesnesi üzerinde <xref:System.Windows.Forms.Control.Refresh%2A> yöntemini çağıracaksınız. Bu, üst öğesi <xref:System.Windows.Forms.Control.Size%2A> gibi özellikler değiştirildiğinde `IMarqueeWidget` nesnenin kendisini uygun şekilde yeniden görüntülemesine neden olur.

### <a name="to-handle-component-changes"></a>Bileşen değişikliklerini işlemek için

1. `MarqueeControlRootDesigner` kaynak dosyasını **kod düzenleyicisinde** açın ve <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> metodunu geçersiz kılın. <xref:System.ComponentModel.Design.IComponentChangeService><xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> ve sorgusunun temel uygulamasını çağırın.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#580](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#580)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#580](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#580)]

2. <xref:System.ComponentModel.Design.IComponentChangeService.OnComponentChanged%2A> olay işleyicisini uygulayın. Gönderen bileşenin türünü test edin ve bir `IMarqueeWidget`, <xref:System.Windows.Forms.Control.Refresh%2A> yöntemini çağırın.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#560](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#560)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#560](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#560)]

## <a name="add-designer-verbs-to-your-custom-designer"></a>Özel tasarımcıya tasarımcı fiilleri ekleme

Tasarımcı fiili, olay işleyicisine bağlı bir menü komutu olur. Tasarımcı fiilleri, tasarım zamanında bir bileşenin kısayol menüsüne eklenir. Daha fazla bilgi için bkz. <xref:System.ComponentModel.Design.DesignerVerb>.

Tasarımcılara iki tasarımcı fiilleri ekleyeceksiniz: **Testi Çalıştır** ve **testi durdur**. Bu fiiller, tasarım zamanında `MarqueeControl` çalışma zamanı davranışını görüntülemenize izin verir. Bu fiiller `MarqueeControlRootDesigner`eklenecektir.

**Çalıştırma testi** çağrıldığında, fiil olay işleyicisi `MarqueeControl``StartMarquee` yöntemini çağırır. **Test durdurma** çağrıldığında, fiil olay işleyicisi `MarqueeControl``StopMarquee` yöntemini çağırır. `StartMarquee` ve `StopMarquee` yöntemlerinin uygulanması, `IMarqueeWidget`uygulayan içerilen denetimlerde bu yöntemleri çağırır, bu nedenle içerilen `IMarqueeWidget` denetimlerinin de teste katılması gerekir.

### <a name="to-add-designer-verbs-to-your-custom-designers"></a>Özel tasarımcılara tasarımcı fiilleri eklemek için

1. `MarqueeControlRootDesigner` sınıfında, `OnVerbRunTest` ve `OnVerbStopTest`adlı olay işleyicileri ekleyin.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#570](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#570)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#570](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#570)]

2. Bu olay işleyicilerini ilgili tasarımcı fiillerine bağlayın. `MarqueeControlRootDesigner`, temel sınıfından bir <xref:System.ComponentModel.Design.DesignerVerbCollection> devralır. İki yeni <xref:System.ComponentModel.Design.DesignerVerb> nesnesi oluşturacak ve bunları <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> yönteminde bu koleksiyona ekleyecek.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#590](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#590)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#590](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#590)]

## <a name="create-a-custom-uitypeeditor"></a>Özel bir Uııtypeınfo Düzenleyicisi oluşturun

Kullanıcılar için özel bir tasarım zamanı deneyimi oluşturduğunuzda, genellikle Özellikler penceresi özel bir etkileşim oluşturmak tercih edilir. Bunu, bir <xref:System.Drawing.Design.UITypeEditor>oluşturarak gerçekleştirebilirsiniz.

`MarqueeBorder` denetimi Özellikler penceresi çeşitli özellikleri kullanıma sunar. Bu özelliklerden ikisi, `MarqueeSpinDirection` ve `MarqueeLightShape` numaralandırmalar tarafından temsil edilir. Kullanıcı arabirimi türü düzenleyicisinin kullanımını göstermek için `MarqueeLightShape` özelliği ilişkili bir <xref:System.Drawing.Design.UITypeEditor> sınıfına sahip olur.

### <a name="to-create-a-custom-ui-type-editor"></a>Özel bir kullanıcı arabirimi tür Düzenleyicisi oluşturmak için

1. `MarqueeBorder` kaynak dosyasını **kod düzenleyicisinde**açın.

2. `MarqueeBorder` sınıfının tanımında, <xref:System.Drawing.Design.UITypeEditor>türetilen `LightShapeEditor` adlı bir sınıf bildirin.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#96](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#96)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#96](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#96)]

3. `editorService`adlı bir <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> örnek değişkeni bildirin.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#92](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#92)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#92](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#92)]

4. Geçersiz kılma <xref:System.Drawing.Design.UITypeEditor.GetEditStyle%2A> yöntemi. Bu uygulama, tasarım ortamına `LightShapeEditor`nasıl görüntüleneceğini bildiren <xref:System.Drawing.Design.UITypeEditorEditStyle.DropDown>döndürür.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#93](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#93)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#93](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#93)]

5. Geçersiz kılma <xref:System.Drawing.Design.UITypeEditor.EditValue%2A> yöntemi. Bu uygulama, <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> nesnesi için tasarım ortamını sorgular. Başarılı olursa, bir `LightShapeSelectionControl`oluşturur. <xref:System.Windows.Forms.Design.IWindowsFormsEditorService.DropDownControl%2A> yöntemi `LightShapeEditor`başlatılacak şekilde çağrılır. Bu çağrıdan gelen dönüş değeri tasarım ortamına döndürülür.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#94](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#94)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#94](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#94)]

## <a name="create-a-view-control-for-your-custom-uitypeeditor"></a>Özel Uııtypeınfo Düzenleyicisi için bir görünüm denetimi oluşturma

`MarqueeLightShape` özelliği iki tür ışık şeklini destekler: `Square` ve `Circle`. Yalnızca bu değerleri Özellikler penceresi grafik olarak görüntülemek için kullanılan özel bir denetim oluşturacaksınız. Bu özel denetim, Özellikler penceresi etkileşimde bulunmak için <xref:System.Drawing.Design.UITypeEditor> tarafından kullanılacaktır.

### <a name="to-create-a-view-control-for-your-custom-ui-type-editor"></a>Özel UI türü düzenleyiciniz için bir görünüm denetimi oluşturmak için

1. `MarqueeControlLibrary` projesine yeni bir <xref:System.Windows.Forms.UserControl> öğesi ekleyin. Yeni kaynak dosyasına, **Açık Shapeselectioncontrol**temel adını verin.

2. **Araç kutusundan** iki <xref:System.Windows.Forms.Panel> denetimini `LightShapeSelectionControl`üzerine sürükleyin. `squarePanel` ve `circlePanel`adlandırın. Yan yana düzenleyin. Her iki <xref:System.Windows.Forms.Panel> denetiminin <xref:System.Windows.Forms.Control.Size%2A> özelliğini **(60, 60)** olarak ayarlayın. `squarePanel` denetiminin <xref:System.Windows.Forms.Control.Location%2A> özelliğini **(8, 10)** olarak ayarlayın. `circlePanel` denetiminin <xref:System.Windows.Forms.Control.Location%2A> özelliğini **(80, 10)** olarak ayarlayın. Son olarak, `LightShapeSelectionControl` <xref:System.Windows.Forms.Control.Size%2A> özelliğini **(150, 80)** olarak ayarlayın.

3. `LightShapeSelectionControl` kaynak dosyasını **kod düzenleyicisinde**açın. Dosyanın en üstüne <xref:System.Windows.Forms.Design?displayProperty=nameWithType> ad alanını içeri aktarın:

   ```vb
   Imports System.Windows.Forms.Design
   ```

   ```csharp
   using System.Windows.Forms.Design;
   ```

4. `squarePanel` ve `circlePanel` denetimleri için <xref:System.Windows.Forms.Control.Click> olay işleyicileri uygulayın. Bu yöntemler, özel <xref:System.Drawing.Design.UITypeEditor> Düzenle oturumunun sona erdirmek için <xref:System.Windows.Forms.Design.IWindowsFormsEditorService.CloseDropDown%2A> çağırır.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#390](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#390)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#390](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#390)]

5. `editorService`adlı bir <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> örnek değişkeni bildirin.

   ```vb
   Private editorService As IWindowsFormsEditorService
   ```

   ```csharp
   private IWindowsFormsEditorService editorService;
   ```

6. `lightShapeValue`adlı bir `MarqueeLightShape` örnek değişkeni bildirin.

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#330](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#330)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#330](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#330)]

7. `LightShapeSelectionControl` oluşturucuda, <xref:System.Windows.Forms.Control.Click> olay işleyicilerini `squarePanel` ve `circlePanel` denetimlerin ' <xref:System.Windows.Forms.Control.Click> olaylarını ekleyin. Ayrıca, tasarım ortamından `lightShapeValue` alanına `MarqueeLightShape` değerini atayan bir Oluşturucu aşırı yüklemesi tanımlayın.

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#340](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#340)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#340](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#340)]

8. <xref:System.ComponentModel.Component.Dispose%2A> yönteminde, <xref:System.Windows.Forms.Control.Click> olay işleyicilerini ayırın.

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#350](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#350)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#350](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#350)]

9. **Çözüm Gezgini**, **tüm dosyaları göster** düğmesine tıklayın. LightShapeSelectionControl.Designer.cs veya LightShapeSelectionControl. Designer. vb dosyasını açın ve <xref:System.ComponentModel.Component.Dispose%2A> yönteminin varsayılan tanımını kaldırın.

10. `LightShape` özelliğini uygulayın.

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#360](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#360)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#360](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#360)]

11. Geçersiz kılma <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemi. Bu uygulama doldurulmuş bir kare ve daire çizecek. Ayrıca, bir şekil ya da diğeri etrafında kenarlık çizerek seçili değeri vurgulayacaktır.

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#380](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#380)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#380](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#380)]

## <a name="test-your-custom-control-in-the-designer"></a>Tasarımcıda özel denetiminizi test etme

Bu noktada, `MarqueeControlLibrary` projesi oluşturabilirsiniz. `MarqueeControl` sınıfından devralan bir denetim oluşturarak ve bunu bir formda kullanarak uygulamanızı test edin.

### <a name="to-create-a-custom-marqueecontrol-implementation"></a>Özel bir MarqueeControl uygulamasını oluşturmak için

1. Windows Form Tasarımcısı `DemoMarqueeControl` açın. Bu, `DemoMarqueeControl` türünün bir örneğini oluşturur ve `MarqueeControlRootDesigner` türünün bir örneğinde görüntüler.

2. **Araç kutusunda** **MarqueeControlLibrary Components** sekmesini açın. `MarqueeBorder` ve `MarqueeText` denetimlerini seçilebilir olarak görürsünüz.

3. `MarqueeBorder` denetiminin bir örneğini `DemoMarqueeControl` tasarım yüzeyine sürükleyin. Bu `MarqueeBorder` denetimini üst denetime yerleştir.

4. `MarqueeText` denetiminin bir örneğini `DemoMarqueeControl` tasarım yüzeyine sürükleyin.

5. Çözümü oluşturun.

6. `DemoMarqueeControl` sağ tıklayın ve kısayol menüsünde, animasyonu başlatmak için **Test Çalıştır** seçeneğini belirleyin. Animasyonu durdurmak için **Sınamayı Durdur** ' a tıklayın.

7. Tasarım görünümü 'da **Form1** ' i açın.

8. Forma iki <xref:System.Windows.Forms.Button> denetimi yerleştirin. `startButton` ve `stopButton`adlandırın ve <xref:System.Windows.Forms.Control.Text%2A> özellik değerlerini sırasıyla **Başlat** ve **Durdur**olarak değiştirin.

9. <xref:System.Windows.Forms.Button> denetimleri için <xref:System.Windows.Forms.Control.Click> olay işleyicileri uygulayın.

10. **Araç kutusunda** **MarqueeControlTest Components** sekmesini açın. `DemoMarqueeControl` seçime uygun olarak görürsünüz.

11. Bir `DemoMarqueeControl` örneğini **Form1** tasarım yüzeyine sürükleyin.

12. <xref:System.Windows.Forms.Control.Click> olay işleyicilerinde, `DemoMarqueeControl`üzerinde `Start` ve `Stop` yöntemlerini çağırın.

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

13. `MarqueeControlTest` projesini başlangıç projesi olarak ayarlayın ve çalıştırın. `DemoMarqueeControl`görüntüleyen formu görürsünüz. Animasyonu başlatmak için **Başlat** düğmesini seçin. Metnin yanıp sönmesi ve kenarlığın etrafında hareket eden ışıklar görmeniz gerekir.

## <a name="next-steps"></a>Sonraki adımlar

`MarqueeControlLibrary`, Özel denetimlerin ve ilişkili tasarımcılarının basit bir uygulamasını gösterir. Bu örneği çeşitli yollarla daha karmaşık hale getirebilirsiniz:

- Tasarımcıda `DemoMarqueeControl` özellik değerlerini değiştirin. Daha fazla `MarqueBorder` denetim ekleyin ve iç içe bir efekt oluşturmak için bunları üst örneklerine yerleştirin. `UpdatePeriod` ve hafif ilgili özellikler için farklı ayarlarla denemeler yapın.

- Kendi `IMarqueeWidget`uygulamalarınızı yazın. Örneğin, yanıp sönen bir "Neon Sign" veya birden çok görüntüde animasyonlu bir işaret oluşturabilirsiniz.

- Tasarım zamanı deneyimini daha da özelleştirin. <xref:System.Windows.Forms.Control.Enabled%2A> ve <xref:System.Windows.Forms.Control.Visible%2A>daha fazla özelliği gölgelendirmeyi deneyebilirsiniz ve yeni özellikler ekleyebilirsiniz. Alt öğe denetimleri yerleştirme gibi yaygın görevleri basitleştirmek için yeni tasarımcı fiilleri ekleyin.

- `MarqueeControl`lisanslayın.

- Denetimlerinizin serileştirilme şeklini ve kodun onlar için nasıl oluşturulduğunu denetleyin. Daha fazla bilgi için bkz. [dinamik kaynak kodu oluşturma ve derleme](../../reflection-and-codedom/dynamic-source-code-generation-and-compilation.md).

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.UserControl>
- <xref:System.Windows.Forms.Design.ParentControlDesigner>
- <xref:System.Windows.Forms.Design.DocumentDesigner>
- <xref:System.ComponentModel.Design.IRootDesigner>
- <xref:System.ComponentModel.Design.DesignerVerb>
- <xref:System.Drawing.Design.UITypeEditor>
- <xref:System.ComponentModel.BackgroundWorker>
