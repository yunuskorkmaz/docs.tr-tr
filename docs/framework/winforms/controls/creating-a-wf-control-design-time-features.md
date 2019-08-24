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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: b72c449ab68c9bb2ceea6f8ee78abe6771b9a8bd
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/24/2019
ms.locfileid: "70016004"
---
# <a name="walkthrough-create-a-control-that-takes-advantage-of-design-time-features"></a>İzlenecek yol: Tasarım zamanı özelliklerinden faydalanan bir denetim oluşturma

Özel bir denetim için tasarım zamanı deneyimi, ilişkili bir özel tasarımcı Authoring ile geliştirilebilir.

Bu makalede özel bir denetim için nasıl özel tasarımcı oluşturacağınız açıklanmıştır. `MarqueeControl` Adlı`MarqueeControlRootDesigner`bir tür ve ilişkili tasarımcı sınıfını uygulayacaksınız.

Türü `MarqueeControl` , animasyonlu ışıklar ve yanıp sönen metinle benzer bir tiyatro çerçevesine benzer bir ekran uygular.

Bu denetim için tasarımcı, tasarım ortamıyla birlikte etkileşimde bulunur ve özel bir tasarım zamanı deneyimi sağlar. Özel tasarımcı sayesinde, bir özel `MarqueeControl` uygulamayı animasyonlu ışıklar ve yanıp sönen metni birçok birleşimde bir araya getirebilirsiniz. Bir form üzerinde, diğer Windows Forms denetimleri gibi, birleştirilmiş denetimi kullanabilirsiniz.

Bu yönergeyi tamamladığınızda, özel denetiminiz aşağıdakine benzer şekilde görünür:

![Metin ve Başlat ve Durdur düğmelerini gösteren bir kayan yazıyı gösteren uygulama.](./media/creating-a-wf-control-design-time-features/demo-marquee-control.gif)

Tüm kod listesi için bkz [. nasıl yapılır: Tasarım zamanı özelliklerinden](/previous-versions/visualstudio/visual-studio-2013/307hck25(v=vs.120))faydalanan bir Windows Forms denetimi oluşturun.

## <a name="prerequisites"></a>Önkoşullar

Bu izlenecek yolu tamamlamak için Visual Studio gerekir.

## <a name="create-the-project"></a>Projeyi oluşturma

İlk adım uygulama projesini oluşturmaktır. Bu projeyi, özel denetimi barındıran uygulamayı oluşturmak için kullanacaksınız.

Visual Studio 'da yeni bir Windows Forms uygulama projesi oluşturun ve **MarqueeControlTest**olarak adlandırın.

## <a name="create-the-control-library-project"></a>Denetim kitaplığı projesi oluşturma

1. Çözüme bir Windows Forms denetim kitaplığı projesi ekleyin. Projeyi **MarqueeControlLibrary**olarak adlandırın.

2. **Çözüm Gezgini**kullanarak, tercih ettiğiniz dile bağlı olarak, "UserControl1.cs" veya "UserControl1. vb" adlı kaynak dosyayı silerek projenin varsayılan denetimini silin.

3. `MarqueeControlLibrary` Projeye yeni <xref:System.Windows.Forms.UserControl> bir öğe ekleyin. Yeni kaynak dosyasına **MarqueeControl**temel adını verin.

4. **Çözüm Gezgini**kullanarak `MarqueeControlLibrary` projede yeni bir klasör oluşturun.

5. **Tasarım** klasörüne sağ tıklayın ve yeni bir sınıf ekleyin. **MarqueeControlRootDesigner**olarak adlandırın.

6. System. Design derlemesinden türler kullanmanız gerekir, bu nedenle bu başvuruyu `MarqueeControlLibrary` projeye ekleyin.

## <a name="reference-the-custom-control-project"></a>Özel denetim projesine başvur

Bu `MarqueeControlTest` projeyi, özel denetimi test etmek için kullanacaksınız. `MarqueeControlLibrary` Derlemeye bir proje başvurusu eklediğinizde test projesi özel denetimden haberdar olur.

Projede, `MarqueeControlLibrary` derlemeye bir proje başvurusu ekleyin. `MarqueeControlTest` `MarqueeControlLibrary` Derlemeye doğrudan başvurmak yerine **Başvuru Ekle** iletişim kutusundaki **Projeler** sekmesini kullandığınızdan emin olun.

## <a name="define-a-custom-control-and-its-custom-designer"></a>Özel bir denetim ve kendi özel tasarımcısını tanımlama

Özel denetiminiz <xref:System.Windows.Forms.UserControl> sınıfından türecektir. Bu, denetiminizin diğer denetimleri içermesini sağlar ve denetimi, varsayılan işlevselliğin harika olmasını sağlar.

Özel denetiminizin ilişkili bir özel Tasarımcısı olacak. Bu, özel denetiminiz için özel olarak uyarlanmış benzersiz bir tasarım deneyimi oluşturmanıza olanak sağlar.

<xref:System.ComponentModel.DesignerAttribute> Sınıfını kullanarak denetimi Tasarımcı ile ilişkilendirirsiniz. Özel denetiminizin tüm tasarım zamanı davranışını geliştirmekte olduğunuzdan, özel tasarımcı <xref:System.ComponentModel.Design.IRootDesigner> arabirimini uygular.

### <a name="to-define-a-custom-control-and-its-custom-designer"></a>Özel bir denetim ve özel tasarımcı tanımlamak için

1. Kaynak dosyasını kod düzenleyicisinde açın. `MarqueeControl` Dosyanın en üstüne aşağıdaki ad alanlarını içeri aktarın:

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#220](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#220)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#220](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#220)]

2. <xref:System.ComponentModel.DesignerAttribute> Sınıfını`MarqueeControl` sınıf bildirimine ekleyin. Bu, özel denetimi Tasarımcı ile ilişkilendirir.

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#240](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#240)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#240](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#240)]

3. Kaynak dosyasını kod düzenleyicisinde açın. `MarqueeControlRootDesigner` Dosyanın en üstüne aşağıdaki ad alanlarını içeri aktarın:

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#520](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#520)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#520](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#520)]

4. Bildirimini `MarqueeControlRootDesigner` <xref:System.Windows.Forms.Design.DocumentDesigner> sınıfından devralacak şekilde değiştirin. **Araç kutusu**ile tasarımcı etkileşimini belirtmek içinöğesiniuygulayın.<xref:System.ComponentModel.ToolboxItemFilterAttribute>

   > [!NOTE]
   > `MarqueeControlRootDesigner` Sınıfının tanımı, MarqueeControlLibrary. Design adlı bir ad alanı içine alınmıştır. Bu bildirim, tasarımcıyı tasarımla ilgili türler için ayrılmış özel bir ad alanına koyar.

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#530](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#530)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#530](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#530)]

5. `MarqueeControlRootDesigner` Sınıf için oluşturucuyu tanımlayın. Oluşturucu gövdesine <xref:System.Diagnostics.Trace.WriteLine%2A> bir ifade ekleyin. Bu, hata ayıklama için yararlı olacaktır.

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#540](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#540)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#540](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#540)]

## <a name="create-an-instance-of-your-custom-control"></a>Özel denetiminizin bir örneğini oluşturma

1. `MarqueeControlTest` Projeye yeni <xref:System.Windows.Forms.UserControl> bir öğe ekleyin. Yeni kaynak dosyasına **DemoMarqueeControl**temel adını verin.

2. Dosyayı kod düzenleyicisinde açın. `DemoMarqueeControl` Dosyanın en üstünde, `MarqueeControlLibrary` ad alanını içeri aktarın:

   ```vb
   Imports MarqueeControlLibrary
   ```

   ```csharp
   using MarqueeControlLibrary;
   ```

3. Bildirimini `DemoMarqueeControl` `MarqueeControl` sınıfından devralacak şekilde değiştirin.

4. Projeyi oluşturun.

5. Windows Form Tasarımcısı Form1 ' i açın.

6. **Araç kutusunda** **MarqueeControlTest Components** sekmesini bulun ve açın. `DemoMarqueeControl` **Araç kutusundan** bir öğesini formunuza sürükleyin.

7. Projeyi oluşturun.

## <a name="set-up-the-project-for-design-time-debugging"></a>Projeyi tasarım zamanı hata ayıklama için ayarlama

Özel bir tasarım zamanı deneyimi geliştirirken, denetimlerinizin ve bileşenlerinizin hata ayıklaması gerekir. Projenizi tasarım zamanında hata ayıklamaya izin verecek şekilde kurmak için basit bir yol vardır. Daha fazla bilgi için bkz [. İzlenecek yol: Tasarım zamanında](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)özel Windows Forms Denetimlerinde hata ayıklama.

1. `MarqueeControlLibrary` Projeye sağ tıklayın ve **Özellikler**' i seçin.

2. **MarqueeControlLibrary Özellik sayfaları** Iletişim kutusunda **hata ayıklama** sayfasını seçin.

3. **Başlangıç eylemi** bölümünde **dış program Başlat**' ı seçin. Visual Studio 'nun ayrı bir örneğinde hata ayıkladığınızda, Visual Studio IDE 'ye gitmek için![üç nokta (Visual Studio](./media/visual-studio-ellipsis-button.png)'nun Özellikler penceresi) düğmesine tıklayın. Yürütülebilir dosyanın adı devenv. exe ' dir ve varsayılan konuma yüklediyseniz, yolu *% ProgramFiles (x86)% \ Microsoft Visual studio\2019\\\<Edition > \Common7\IDE\devenv.exe*olur.

4. İletişim kutusunu kapatmak için **Tamam ' ı** seçin.

5. Bu hata ayıklama yapılandırmasını etkinleştirmek için MarqueeControlLibrary projesine sağ tıklayın ve **Başlangıç projesi olarak ayarla** ' yı seçin.

## <a name="checkpoint"></a>Checkpoint

Artık özel denetiminizin tasarım zamanı davranışını hata ayıklamaya hazırsınız. Hata ayıklama ortamının doğru şekilde ayarlandığını belirledikten sonra, özel denetim ve özel tasarımcı arasındaki ilişkilendirmeyi test edersiniz.

### <a name="to-test-the-debugging-environment-and-the-designer-association"></a>Hata ayıklama ortamını ve tasarımcı ilişkilendirmesini test etmek için

1. **Kod düzenleyicisinde** MarqueeControlRootDesigner kaynak dosyasını açın ve <xref:System.Diagnostics.Trace.WriteLine%2A> deyime bir kesme noktası yerleştirin.

2. Hata ayıklama oturumu başlatmak için **F5** tuşuna basın.

   Visual Studio 'nun yeni bir örneği oluşturulur.

3. Visual Studio 'nun yeni örneğinde, MarqueeControlTest çözümünü açın. **Dosya** menüsünden **son projeler** ' i seçerek çözümü kolayca bulabilirsiniz. MarqueeControlTest. sln çözüm dosyası en son kullanılan dosya olarak listelenecektir.

4. `DemoMarqueeControl` Öğesini tasarımcıda açın.

   Visual Studio 'nun hata ayıklama örneği, kesme noktasında odak ve yürütme işlemini alır. Hata ayıklama oturumuna devam etmek için **F5** tuşuna basın.

Bu noktada, özel denetiminizi ve onunla ilişkili özel tasarımcıyı geliştirip hata ayıklamanızın her şey vardır. Bu makalenin geri kalanında, denetimin ve tasarımcının özelliklerini uygulama ayrıntılarına yoğunlaşmaktadır.

## <a name="implement-the-custom-control"></a>Özel denetimi uygulama

, `MarqueeControl` Bir<xref:System.Windows.Forms.UserControl> özelleştirme biraz daha vardır. İki yöntem sunar: `Start`, kayan yazı animasyonunu başlatan ve `Stop`animasyonu durduran. , `MarqueeControl` `StopMarquee` `StartMarquee` Arabirimini `IMarqueeWidget` uygulayanaltdenetimleriçerdiğindenveherbiraltdenetimivesırasıylaveyöntemleriniherbiraltdenetimdesırasıylaçağırmak`Start`için `Stop` uygulayan `IMarqueeWidget`.

`MarqueeBorder` Ve `MarqueeControl` denetimleriningörünümü<xref:System.Windows.Forms.Control.OnLayout%2A> düzene bağlıdır, bu nedenle yöntemi ve bu türün alt denetimlerinde yapılan çağrıları <xref:System.Windows.Forms.Control.PerformLayout%2A> geçersiz kılar. `MarqueeText`

Bu, `MarqueeControl` özelleştirmelerin bir kapsamını. Çalışma zamanı özellikleri `MarqueeBorder` ve `MarqueeText` denetimleri tarafından uygulanır ve tasarım zamanı `MarqueeBorderDesigner` özellikleri ve `MarqueeControlRootDesigner` sınıfları tarafından uygulanır.

### <a name="to-implement-your-custom-control"></a>Özel denetiminizi uygulamak için

1. Kaynak dosyasını kod düzenleyicisinde açın. `MarqueeControl` `Start` Ve`Stop` yöntemlerini uygulayın.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#260](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#260)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#260](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#260)]

2. Geçersiz kılma <xref:System.Windows.Forms.Control.OnLayout%2A> yöntemi.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#270](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#270)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#270](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#270)]

## <a name="create-a-child-control-for-your-custom-control"></a>Özel denetiminiz için bir alt denetim oluşturma

İki tür alt denetimi barındırır `MarqueeBorder` : denetim ve `MarqueeText` denetim. `MarqueeControl`

- `MarqueeBorder`: Bu denetim, kenarları etrafında "ışıklar" kenarlığını boyar. Kenarlıkta bulunan ışıklar, kenarlık etrafında taşınıyor gibi görünürler. Işıklarının flaşın, çağrılan `UpdatePeriod`bir özellik tarafından denetlenme hızı. Diğer birçok özel özellik, denetimin görünümünün diğer yönlerini tespit. Animasyon başladığında ve durdurulduğunda `StartMarquee` denetim `StopMarquee`olarak adlandırılan iki yöntem.

- `MarqueeText`: Bu denetim yanıp sönen bir dizeyi boyar. Denetim gibi, metnin yanıp sönebileceği hız, `UpdatePeriod` özelliği tarafından kontrol edilir. `MarqueeBorder` Denetim Ayrıca, `StartMarquee` denetimiyle`MarqueeBorder` ortak olan `StopMarquee` ve yöntemlerine sahiptir. `MarqueeText`

Tasarım zamanında `MarqueeControlRootDesigner` , bu iki denetim türünün herhangi bir `MarqueeControl` kombinasyonda içine eklenmesine izin verir.

İki denetimin ortak özellikleri, adlı `IMarqueeWidget`bir arabirimle birleştirilir. Bu, `MarqueeControl` bir seçim çerçevesinin ilgili alt denetimleri bulmasını ve özel bir işleme vermesini sağlar.

Düzenli animasyon özelliğini uygulamak için, <xref:System.ComponentModel.BackgroundWorker> <xref:System.ComponentModel?displayProperty=nameWithType> ad alanındaki nesneleri kullanacaksınız. Nesneleri kullanabilirsiniz <xref:System.Windows.Forms.Timer> , ancak birçok `IMarqueeWidget` nesne mevcut olduğunda, tek UI iş parçacığı animasyonla birlikte tutulamayabilir.

### <a name="to-create-a-child-control-for-your-custom-control"></a>Özel denetiminiz için bir alt denetim oluşturmak için

1. `MarqueeControlLibrary` Projeye yeni bir sınıf öğesi ekleyin. Yeni kaynak dosyasına "Imarqueepencere öğesi" için temel adı verin.

2. Kaynak dosyasını **kod düzenleyicisinde** açın ve bildirimi ' den `class` ' e `interface`değiştirin: `IMarqueeWidget`

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/imarqueewidget.cs#2)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/imarqueewidget.vb#2)]

3. İki yöntemi ve kayan yazı animasyonunu `IMarqueeWidget` işleyen bir özelliği göstermek için aşağıdaki kodu arabirimine ekleyin:

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/imarqueewidget.cs#3)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/imarqueewidget.vb#3)]

4. `MarqueeControlLibrary` Projeye yeni bir **özel denetim** öğesi ekleyin. Yeni kaynak dosyasına "MarqueeText" temel adını verin.

5. **Araç kutusundan** bir <xref:System.ComponentModel.BackgroundWorker> bileşeni denetimüzerinesürükleyin.`MarqueeText` Bu bileşen `MarqueeText` denetimin kendisini zaman uyumsuz olarak güncelleştirmesine izin verir.

6. **Özellikler** penceresinde <xref:System.ComponentModel.BackgroundWorker> , bileşen `WorkerReportsProgress` ve <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> özelliklerini **doğru**olarak ayarlayın. Bu ayarlar, <xref:System.ComponentModel.BackgroundWorker> bileşenin düzenli olarak <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> olayı kullanmasına ve zaman uyumsuz güncelleştirmeleri iptal edebilmesini sağlar.

   Daha fazla bilgi için bkz. [BackgroundWorker Component](backgroundworker-component.md).

7. Kaynak dosyasını kod düzenleyicisinde açın. `MarqueeText` Dosyanın en üstüne aşağıdaki ad alanlarını içeri aktarın:

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#120](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#120)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#120](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#120)]

8. ' Dan `MarqueeText` <xref:System.Windows.Forms.Label> devralması için bildirimini değiştirin ve `IMarqueeWidget` arabirimini uygulayın:

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#130](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#130)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#130](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#130)]

9. Gösterilen özelliklere karşılık gelen örnek değişkenlerini bildirin ve bunları oluşturucuda başlatın. Alan, metnin `LightColor` özelliği tarafından verilen renkte boyanmış olup olmayacağını belirler. `isLit`

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#140](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#140)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#140](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#140)]

10. `IMarqueeWidget` arabirimini gerçekleştirin.

    Ve `StartMarquee` yöntemleri,<xref:System.ComponentModel.BackgroundWorker> animasyonu başlatmak ve durdurmak için <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> bileşenin veyöntemleriniçağırır.<xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> `StopMarquee`

    <xref:System.ComponentModel.CategoryAttribute.Category%2A> Ve<xref:System.ComponentModel.BrowsableAttribute.Browsable%2A>öznitelikleri, "kayan yazı" adlı Özellikler penceresi özel bir bölümünde görünmesi için özelliğineuygulanır.`UpdatePeriod`

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#150](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#150)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#150](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#150)]

11. Özellik erişimcileri uygulayın. İstemciler için iki özelliği kullanıma sunacaksınız: `LightColor` ve `DarkColor`. <xref:System.ComponentModel.CategoryAttribute.Category%2A> Ve<xref:System.ComponentModel.BrowsableAttribute.Browsable%2A> öznitelikleri bu özelliklere uygulanır, bu nedenle Özellikler "kayan yazı" adlı Özellikler penceresi özel bir bölümünde görüntülenir.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#160](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#160)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#160](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#160)]

12. <xref:System.ComponentModel.BackgroundWorker> Bileşen ve Olaylar<xref:System.ComponentModel.BackgroundWorker.ProgressChanged> için işleyicileri uygulayın. <xref:System.ComponentModel.BackgroundWorker.DoWork>

    Olay işleyicisi, tarafından `UpdatePeriod` <xref:System.ComponentModel.BackgroundWorker.ProgressChanged>belirtilenmilisaniye sayısı için uyku moduna geçer. <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> <xref:System.ComponentModel.BackgroundWorker.DoWork>

    <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> Olay işleyicisi, yanıp sönmeye yönelik görünümü sağlamak için açık ve koyu durumu arasındaki metni değiştirir.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#180](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#180)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#180](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#180)]

13. Animasyonu etkinleştirmek için yöntemini geçersiz kılın. <xref:System.Windows.Forms.Control.OnPaint%2A>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#170](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#170)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#170](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#170)]

14. Çözümü derlemek için **F6** tuşuna basın.

## <a name="create-the-marqueeborder-child-control"></a>MarqueeBorder alt denetimini oluşturma

Denetim, `MarqueeText` denetimden biraz daha karmaşıktır. `MarqueeBorder` Daha fazla özelliğe sahiptir ve <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemdeki animasyon daha fazla yer alır. Prensibi, `MarqueeText` denetime oldukça benzer.

Denetimde alt denetimler olabileceğinden, <xref:System.Windows.Forms.Control.Layout> olayların farkında olması gerekir. `MarqueeBorder`

### <a name="to-create-the-marqueeborder-control"></a>MarqueeBorder denetimini oluşturmak için

1. `MarqueeControlLibrary` Projeye yeni bir **özel denetim** öğesi ekleyin. Yeni kaynak dosyasına "MarqueeBorder" temel adını verin.

2. **Araç kutusundan** bir <xref:System.ComponentModel.BackgroundWorker> bileşeni denetimüzerinesürükleyin.`MarqueeBorder` Bu bileşen `MarqueeBorder` denetimin kendisini zaman uyumsuz olarak güncelleştirmesine izin verir.

3. **Özellikler** penceresinde <xref:System.ComponentModel.BackgroundWorker> , bileşen `WorkerReportsProgress` ve <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> özelliklerini **doğru**olarak ayarlayın. Bu ayarlar, <xref:System.ComponentModel.BackgroundWorker> bileşenin düzenli olarak <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> olayı kullanmasına ve zaman uyumsuz güncelleştirmeleri iptal edebilmesini sağlar. Daha fazla bilgi için bkz. [BackgroundWorker Component](backgroundworker-component.md).

4. **Özellikler** penceresinde, **Olaylar** düğmesini seçin. <xref:System.ComponentModel.BackgroundWorker.DoWork> Ve<xref:System.ComponentModel.BackgroundWorker.ProgressChanged> olayları için işleyiciler iliştirin.

5. Kaynak dosyasını kod düzenleyicisinde açın. `MarqueeBorder` Dosyanın en üstüne aşağıdaki ad alanlarını içeri aktarın:

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#20)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#20)]

6. ' Dan `MarqueeBorder` <xref:System.Windows.Forms.Panel> devralması için bildirimini değiştirin ve `IMarqueeWidget` arabirimini uygulayın.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#30)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#30)]

7. `MarqueeBorder` Denetimin durumunu yönetmek için iki numaralandırma bildirin: `MarqueeSpinDirection`, ışıklarının etrafında "döndürme" ve `MarqueeLightShape`ışıklarının şeklini (kare veya dairesel) belirleyen yönü belirleyen yönü belirler. Bu bildirimleri `MarqueeBorder` Sınıf bildiriminden önce yerleştirin.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#97](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#97)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#97](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#97)]

8. Gösterilen özelliklere karşılık gelen örnek değişkenlerini bildirin ve bunları oluşturucuda başlatın.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#40](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#40)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#40](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#40)]

9. `IMarqueeWidget` arabirimini gerçekleştirin.

    Ve `StartMarquee` yöntemleri,<xref:System.ComponentModel.BackgroundWorker> animasyonu başlatmak ve durdurmak için <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> bileşenin veyöntemleriniçağırır.<xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> `StopMarquee`

    Denetim alt denetimler içerebildiğinden `StartMarquee` , yöntemi, uygulamalarındaki `IMarqueeWidget`tüm alt denetimleri ve çağrıları `StartMarquee` numaralandırır. `MarqueeBorder` `StopMarquee` Yönteminde benzer bir uygulama vardır.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#50](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#50)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#50](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#50)]

10. Özellik erişimcileri uygulayın. `MarqueeBorder` Denetimde, görünümünü denetlemek için çeşitli özellikler vardır.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#60](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#60)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#60](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#60)]

11. <xref:System.ComponentModel.BackgroundWorker> Bileşen ve Olaylar<xref:System.ComponentModel.BackgroundWorker.ProgressChanged> için işleyicileri uygulayın. <xref:System.ComponentModel.BackgroundWorker.DoWork>

    Olay işleyicisi, tarafından `UpdatePeriod` <xref:System.ComponentModel.BackgroundWorker.ProgressChanged>belirtilenmilisaniye sayısı için uyku moduna geçer. <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> <xref:System.ComponentModel.BackgroundWorker.DoWork>

    Olay işleyicisi, diğer ışıklarının açık/koyu durumunun belirlendiği "temel" Işığın konumunu artırır ve denetimin kendisini yeniden çizmeyi sağlamak için <xref:System.Windows.Forms.Control.Refresh%2A> yöntemini çağırır. <xref:System.ComponentModel.BackgroundWorker.ProgressChanged>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#90](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#90)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#90](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#90)]

12. Yardımcı yöntemleri ve `DrawLight`' yi `IsLit` uygulayın.

    Yöntemi `IsLit` , belirli bir konumdaki ışığın rengini belirler. "Açık" olan ışıklar `LightColor` özelliği tarafından verilen renkte çizilir ve "koyu" olan ışıklar `DarkColor` özelliği tarafından verilen renkte çizilir.

    `DrawLight` Yöntemi uygun renk, şekil ve konumu kullanarak bir ışık çizer.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#80](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#80)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#80](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#80)]

13. <xref:System.Windows.Forms.Control.OnLayout%2A> Ve<xref:System.Windows.Forms.Control.OnPaint%2A> yöntemlerini geçersiz kılın.

    Yöntemi, `MarqueeBorder` denetimin kenarları üzerinde ışıkları çizer. <xref:System.Windows.Forms.Control.OnPaint%2A>

    <xref:System.Windows.Forms.Control.OnPaint%2A> Yöntem `MarqueeBorder` denetimin boyutlarına bağlı olduğundan, düzen her değiştiğinde onu çağırmanız gerekir. Bunu başarmak için, öğesini <xref:System.Windows.Forms.Control.OnLayout%2A> geçersiz kılın <xref:System.Windows.Forms.Control.Refresh%2A>ve çağırın.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#70](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#70)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#70](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#70)]

## <a name="create-a-custom-designer-to-shadow-and-filter-properties"></a>Gölge ve filtre özelliklerine özel tasarımcı oluşturma

`MarqueeControlRootDesigner` Sınıfı, kök Tasarımcı için uygulama sağlar. Üzerinde `MarqueeControl`çalışan bu tasarımcıya ek olarak, özellikle `MarqueeBorder` denetimle ilişkili özel bir tasarımcı gerekir. Bu tasarımcı, özel kök tasarlayıcı bağlamında uygun olan özel davranışı sağlar.

Özellikle, "gölgelendir" ve `MarqueeBorder` denetimdeki belirli özellikleri filtreleyerek tasarım ortamıyla etkileşimini değiştirmiş olacak.`MarqueeBorderDesigner`

Bir bileşenin Özellik erişimcisine yönelik kesintiye uğratan çağrı, "gölgeleme" olarak bilinir. Bir tasarımcının Kullanıcı tarafından ayarlanan değeri izlemesine ve isteğe bağlı olarak bu değeri tasarlanmakta olan bileşene iletmenize olanak tanır.

Bu örnekte <xref:System.Windows.Forms.Control.Visible%2A> , ve <xref:System.Windows.Forms.Control.Enabled%2A> özellikleri, `MarqueeBorderDesigner`kullanıcının tasarım zamanı sırasında `MarqueeBorder` denetimi görünmez veya devre dışı yapmasını önleyen tarafından gölgelenir.

Tasarımcılar Ayrıca özellikler ekleyebilir ve kaldırabilir. Bu örnekte, <xref:System.Windows.Forms.Control.Padding%2A> özellik tasarım zamanında kaldırılacak, `MarqueeBorder` çünkü denetim program aracılığıyla, `LightSize` özelliği tarafından belirtilen ışıklarının boyutuna göre doldurma ayarlıyor.

`MarqueeBorderDesigner` İçin<xref:System.ComponentModel.Design.ComponentDesigner>temel sınıf, tasarım zamanında bir denetim tarafından açığa çıkarılan öznitelikleri, özellikleri ve olayları değiştirebilen yöntemler içerir:

- <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterProperties%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PostFilterProperties%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterAttributes%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PostFilterAttributes%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterEvents%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PostFilterEvents%2A>

Bu yöntemleri kullanarak bir bileşenin genel arabirimini değiştirirken bu kuralları izleyin:

- Yalnızca `PreFilter` metotlarda öğe ekleme veya kaldırma

- Yalnızca `PostFilter` metotlarda bulunan öğeleri değiştir

- Her zaman ilk olarak `PreFilter` metotlarda temel uygulamayı çağırın

- Her zaman, `PostFilter` metotlarda en son temel uygulamayı çağırın

Bu kurallara uymak, tasarım zamanı ortamındaki tüm tasarımcılarının tasarlanmakta olan tüm bileşenlerin tutarlı bir görünümüne sahip olmasını sağlar.

<xref:System.ComponentModel.Design.ComponentDesigner> Sınıfı, gölgelendirilmiş özelliklerin değerlerini yönetmek için bir sözlük sağlar, bu da size belirli örnek değişkenleri oluşturma gereksinimini sizi maliyetinden kurtarır.

### <a name="to-create-a-custom-designer-to-shadow-and-filter-properties"></a>Gölge ve filtre özelliklerine özel bir tasarımcı oluşturmak için

1. **Tasarım** klasörüne sağ tıklayın ve yeni bir sınıf ekleyin. Kaynak dosyaya **MarqueeBorderDesigner**temel adını verin.

2. MarqueeBorderDesigner kaynak dosyasını **kod düzenleyicisinde**açın. Dosyanın en üstüne aşağıdaki ad alanlarını içeri aktarın:

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#420](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#420)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#420](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#420)]

3. Bildirimini `MarqueeBorderDesigner` öğesinden<xref:System.Windows.Forms.Design.ParentControlDesigner>devralacak şekilde değiştirin.

    Denetim alt denetimler içerebildiğinden, üst-alt etkileşimini <xref:System.Windows.Forms.Design.ParentControlDesigner>işleyen öğesinden devralır.`MarqueeBorderDesigner` `MarqueeBorder`

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#430](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#430)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#430](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#430)]

4. Temel uygulamasını <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterProperties%2A>geçersiz kılın.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#450](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#450)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#450](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#450)]

5. <xref:System.Windows.Forms.Control.Enabled%2A> Ve<xref:System.Windows.Forms.Control.Visible%2A> özelliklerini uygulayın. Bu uygulamalar, denetimin özelliklerini gölgelendir.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#440](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#440)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#440](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#440)]

## <a name="handle-component-changes"></a>Bileşen değişikliklerini işle

Sınıfı, örneklerinizin `MarqueeControl` özel tasarım zamanı deneyimini sağlar. `MarqueeControlRootDesigner` Tasarım zamanı işlevlerinin çoğu <xref:System.Windows.Forms.Design.DocumentDesigner> sınıfından devralınır. Kodunuz iki özel özelleştirme uygular: bileşen değişikliklerini işleme ve tasarımcı fiilleri ekleme.

Kullanıcılar `MarqueeControl` örneklerini tasarlarsa, kök tasarlayıcı, `MarqueeControl` ve alt denetimlerinde yapılan değişiklikleri izler. Tasarım zamanı ortamı, bileşen durumundaki değişiklikleri izlemek için uygun <xref:System.ComponentModel.Design.IComponentChangeService>bir hizmet sunar.

Ortamı <xref:System.ComponentModel.Design.ComponentDesigner.GetService%2A> yöntemiyle sorgulayarak bu hizmete bir başvuru elde edersiniz. Sorgu başarılı olursa, tasarımcı <xref:System.ComponentModel.Design.IComponentChangeService.ComponentChanged> olay için bir işleyici iliştirebilir ve tasarım zamanında tutarlı bir durumu korumak için gereken görevleri gerçekleştirebilir.

`MarqueeControlRootDesigner` Sınıfı söz konusu olduğunda, <xref:System.Windows.Forms.Control.Refresh%2A> yöntemi tarafından içerilen `MarqueeControl`her `IMarqueeWidget` bir nesne üzerinde çağıracaksınız. Bu, `IMarqueeWidget` <xref:System.Windows.Forms.Control.Size%2A> üst öğesi gibi özellikler değiştirildiğinde nesnenin kendisini uygun şekilde yeniden görüntülemesine neden olur.

### <a name="to-handle-component-changes"></a>Bileşen değişikliklerini işlemek için

1. Kaynak dosyasını **kod düzenleyicisinde** açın ve <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> metodunu geçersiz kılın. `MarqueeControlRootDesigner` İçin temel uygulamasını <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> çağırın ve için sorgulayın. <xref:System.ComponentModel.Design.IComponentChangeService>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#580](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#580)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#580](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#580)]

2. <xref:System.ComponentModel.Design.IComponentChangeService.OnComponentChanged%2A> Olay işleyicisini uygulayın. Gönderen bileşenin türünü test edin ve bir `IMarqueeWidget`ise <xref:System.Windows.Forms.Control.Refresh%2A> yöntemini çağırın.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#560](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#560)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#560](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#560)]

## <a name="add-designer-verbs-to-your-custom-designer"></a>Özel tasarımcıya tasarımcı fiilleri ekleme

Tasarımcı fiili, olay işleyicisine bağlı bir menü komutu olur. Tasarımcı fiilleri, tasarım zamanında bir bileşenin kısayol menüsüne eklenir. Daha fazla bilgi için bkz. <xref:System.ComponentModel.Design.DesignerVerb>.

Tasarımcılara iki tasarımcı fiilleri ekleyeceksiniz: **Testi Çalıştır** ve **testi durdur**. Bu fiiller, `MarqueeControl` tasarım zamanının çalışma zamanı davranışını görüntülemenize olanak sağlayacak. Bu fiiller öğesine `MarqueeControlRootDesigner`eklenecektir.

**Çalıştırma testi** çağrıldığında, fiil olay işleyicisi üzerinde `StartMarquee` `MarqueeControl`yöntemini çağırır. **Testi durdur** çağrıldığında, fiil olay işleyicisi üzerinde `StopMarquee` `MarqueeControl`yöntemini çağırır. `StartMarquee` Ve `IMarqueeWidget` `IMarqueeWidget` yöntemlerinin uygulaması, uygulayan içerilen denetimler üzerinde bu yöntemleri çağırır, bu nedenle içerilen denetimlerin de teste katılması gerekir. `StopMarquee`

### <a name="to-add-designer-verbs-to-your-custom-designers"></a>Özel tasarımcılara tasarımcı fiilleri eklemek için

1. Sınıfında, `OnVerbRunTest` ve`OnVerbStopTest`adlı olay işleyicileri ekleyin. `MarqueeControlRootDesigner`

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#570](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#570)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#570](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#570)]

2. Bu olay işleyicilerini ilgili tasarımcı fiillerine bağlayın. `MarqueeControlRootDesigner`kendi temel <xref:System.ComponentModel.Design.DesignerVerbCollection> sınıfından bir devralır. İki yeni <xref:System.ComponentModel.Design.DesignerVerb> nesne oluşturacak ve bu koleksiyona, <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> yöntemi içinde ekleyecek.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#590](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#590)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#590](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#590)]

## <a name="create-a-custom-uitypeeditor"></a>Özel bir Uııtypeınfo Düzenleyicisi oluşturun

Kullanıcılar için özel bir tasarım zamanı deneyimi oluşturduğunuzda, genellikle Özellikler penceresi özel bir etkileşim oluşturmak tercih edilir. Bunu oluşturarak <xref:System.Drawing.Design.UITypeEditor>yapabilirsiniz.

`MarqueeBorder` Denetim Özellikler penceresi çeşitli özellikleri kullanıma sunar. Bu özelliklerden `MarqueeSpinDirection` ikisi ve `MarqueeLightShape` numaralandırmalar tarafından temsil edilir. Kullanıcı arabirimi türü düzenleyicisinin kullanımını göstermek için, `MarqueeLightShape` özelliği ilişkili <xref:System.Drawing.Design.UITypeEditor> bir sınıfa sahip olur.

### <a name="to-create-a-custom-ui-type-editor"></a>Özel bir kullanıcı arabirimi tür Düzenleyicisi oluşturmak için

1. Kaynak dosyasını kod düzenleyicisinde açın. `MarqueeBorder`

2. `MarqueeBorder` Sınıfının tanımında, öğesinden `LightShapeEditor` <xref:System.Drawing.Design.UITypeEditor>türetilen adlı bir sınıf bildirin.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#96](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#96)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#96](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#96)]

3. <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> Adlı`editorService`bir örnek değişkeni bildirin.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#92](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#92)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#92](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#92)]

4. Geçersiz kılma <xref:System.Drawing.Design.UITypeEditor.GetEditStyle%2A> yöntemi. Bu uygulama, <xref:System.Drawing.Design.UITypeEditorEditStyle.DropDown>tasarım ortamına nasıl `LightShapeEditor`görüntüleneceğini bildiren, öğesini döndürür.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#93](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#93)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#93](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#93)]

5. Geçersiz kılma <xref:System.Drawing.Design.UITypeEditor.EditValue%2A> yöntemi. Bu uygulama, bir <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> nesnenin tasarım ortamını sorgular. Başarılı olursa, bir `LightShapeSelectionControl`oluşturur. Yöntemi başlatmak için çağrılır. `LightShapeEditor` <xref:System.Windows.Forms.Design.IWindowsFormsEditorService.DropDownControl%2A> Bu çağrıdan gelen dönüş değeri tasarım ortamına döndürülür.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#94](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#94)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#94](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#94)]

## <a name="create-a-view-control-for-your-custom-uitypeeditor"></a>Özel Uııtypeınfo Düzenleyicisi için bir görünüm denetimi oluşturma

Özelliği iki tür açık şekli destekler: `Square` ve `Circle`. `MarqueeLightShape` Yalnızca bu değerleri Özellikler penceresi grafik olarak görüntülemek için kullanılan özel bir denetim oluşturacaksınız. Bu özel denetim, Özellikler penceresi etkileşimde bulunmak için <xref:System.Drawing.Design.UITypeEditor> sizin tarafınızdan kullanılacaktır.

### <a name="to-create-a-view-control-for-your-custom-ui-type-editor"></a>Özel UI türü düzenleyiciniz için bir görünüm denetimi oluşturmak için

1. `MarqueeControlLibrary` Projeye yeni <xref:System.Windows.Forms.UserControl> bir öğe ekleyin. Yeni kaynak dosyasına, **Açık Shapeselectioncontrol**temel adını verin.

2. Araç kutusundan <xref:System.Windows.Forms.Panel> iki denetimi üzerine sürükleyin. `LightShapeSelectionControl` Onları `squarePanel` ve`circlePanel`olarak adlandırın. Yan yana düzenleyin. Her iki <xref:System.Windows.Forms.Control.Size%2A> <xref:System.Windows.Forms.Panel> denetimin özelliğini **(60, 60)** olarak ayarlayın. Denetimin özelliğini **(8, 10)** olarak ayarlayın. <xref:System.Windows.Forms.Control.Location%2A> `squarePanel` Denetimin özelliğini **(80, 10)** olarak ayarlayın. <xref:System.Windows.Forms.Control.Location%2A> `circlePanel` Son olarak, `LightShapeSelectionControl` öğesinin <xref:System.Windows.Forms.Control.Size%2A> özelliğini olarak ayarlayın **(150, 80)** .

3. Kaynak dosyasını kod düzenleyicisinde açın. `LightShapeSelectionControl` Dosyanın en üstünde, <xref:System.Windows.Forms.Design?displayProperty=nameWithType> ad alanını içeri aktarın:

   ```vb
   Imports System.Windows.Forms.Design
   ```

   ```csharp
   using System.Windows.Forms.Design;
   ```

4. Ve`squarePanel` <xref:System.Windows.Forms.Control.Click> denetimleriiçin`circlePanel` olay işleyicileri uygulayın. Bu yöntemler, <xref:System.Windows.Forms.Design.IWindowsFormsEditorService.CloseDropDown%2A> özel <xref:System.Drawing.Design.UITypeEditor> Düzenle oturumunu sona erdirmek için çağırır.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#390](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#390)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#390](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#390)]

5. <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> Adlı`editorService`bir örnek değişkeni bildirin.

   ```vb
   Private editorService As IWindowsFormsEditorService
   ```

   ```csharp
   private IWindowsFormsEditorService editorService;
   ```

6. `MarqueeLightShape` Adlı`lightShapeValue`bir örnek değişkeni bildirin.

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#330](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#330)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#330](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#330)]

7. `LightShapeSelectionControl` Oluşturucuda, <xref:System.Windows.Forms.Control.Click> olay işleyicilerini `squarePanel` ve `circlePanel` denetimlerin olaylarınaekleyin.<xref:System.Windows.Forms.Control.Click> Ayrıca, tasarım ortamından `MarqueeLightShape` `lightShapeValue` alana değeri atayan bir Oluşturucu aşırı yüklemesi tanımlayın.

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#340](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#340)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#340](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#340)]

8. <xref:System.ComponentModel.Component.Dispose%2A> Yönteminde <xref:System.Windows.Forms.Control.Click> olay işleyicilerini ayırın.

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#350](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#350)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#350](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#350)]

9. **Çözüm Gezgini**, **tüm dosyaları göster** düğmesine tıklayın. LightShapeSelectionControl.Designer.cs veya LightShapeSelectionControl. Designer. vb dosyasını açın ve <xref:System.ComponentModel.Component.Dispose%2A> yönteminin varsayılan tanımını kaldırın.

10. `LightShape` Özelliğini uygulayın.

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#360](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#360)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#360](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#360)]

11. Geçersiz kılma <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemi. Bu uygulama doldurulmuş bir kare ve daire çizecek. Ayrıca, bir şekil ya da diğeri etrafında kenarlık çizerek seçili değeri vurgulayacaktır.

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#380](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#380)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#380](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#380)]

## <a name="test-your-custom-control-in-the-designer"></a>Tasarımcıda özel denetiminizi test etme

Bu noktada, `MarqueeControlLibrary` projeyi derleyebilirsiniz. `MarqueeControl` Sınıfından devralan bir denetim oluşturarak ve onu bir formda kullanarak uygulamanızı test edin.

### <a name="to-create-a-custom-marqueecontrol-implementation"></a>Özel bir MarqueeControl uygulamasını oluşturmak için

1. Windows Form Tasarımcısı `DemoMarqueeControl` açın. Bu, `DemoMarqueeControl` türün bir örneğini oluşturur ve `MarqueeControlRootDesigner` türün bir örneğinde görüntüler.

2. **Araç kutusunda** **MarqueeControlLibrary Components** sekmesini açın. Seçim için kullanılabilir `MarqueeBorder` ve `MarqueeText` denetimleri görürsünüz.

3. `MarqueeBorder` Denetimin`DemoMarqueeControl` bir örneğini tasarım yüzeyine sürükleyin. Bu `MarqueeBorder` denetimi üst denetime yerleştir.

4. `MarqueeText` Denetimin`DemoMarqueeControl` bir örneğini tasarım yüzeyine sürükleyin.

5. Çözümü oluşturun.

6. Sağ tıklayıp kısayol menüsünden `DemoMarqueeControl` , animasyonu başlatmak için **Test Çalıştır** seçeneğini belirleyin. Animasyonu durdurmak için **Sınamayı Durdur** ' a tıklayın.

7. Tasarım görünümü 'da **Form1** ' i açın.

8. Forma iki <xref:System.Windows.Forms.Button> denetim koyun. Onları `startButton` ve <xref:System.Windows.Forms.Control.Text%2A>olarak adlandırın ve sırasıyla başlangıç ve durdurma özelliği değerlerini değiştirin. `stopButton`

9. Her <xref:System.Windows.Forms.Control.Click> iki denetim için de <xref:System.Windows.Forms.Button> olay işleyicileri uygulayın.

10. **Araç kutusunda** **MarqueeControlTest Components** sekmesini açın. Seçim için `DemoMarqueeControl` kullanılabilir seçeneğini görürsünüz.

11. Bir örneğini `DemoMarqueeControl` **Form1** tasarım yüzeyine sürükleyin.

12. Olay işleyicilerinde, `Start` ve `Stop` üzerindeki `DemoMarqueeControl`yöntemlerini çağırın. <xref:System.Windows.Forms.Control.Click>

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

13. `MarqueeControlTest` Projeyi başlangıç projesi olarak ayarlayın ve çalıştırın. Formunu görüntüleyen `DemoMarqueeControl`formu görürsünüz. Animasyonu başlatmak için **Başlat** düğmesini seçin. Metnin yanıp sönmesi ve kenarlığın etrafında hareket eden ışıklar görmeniz gerekir.

## <a name="next-steps"></a>Sonraki adımlar

, `MarqueeControlLibrary` Özel denetimlerin ve ilişkili tasarımcılarının basit bir uygulamasını gösterir. Bu örneği çeşitli yollarla daha karmaşık hale getirebilirsiniz:

- Tasarımcı `DemoMarqueeControl` içindeki için özellik değerlerini değiştirin. Daha fazla `MarqueBorder` denetim ekleyin ve iç içe geçmiş bir efekt oluşturmak için bunları üst örnekleri içine yerleştirin. `UpdatePeriod` Ve ışığıyla ilgili özellikler için farklı ayarlarla denemeler yapın.

- Kendi uygulamalarınızı yazar `IMarqueeWidget`. Örneğin, yanıp sönen bir "Neon Sign" veya birden çok görüntüde animasyonlu bir işaret oluşturabilirsiniz.

- Tasarım zamanı deneyimini daha da özelleştirin. <xref:System.Windows.Forms.Control.Enabled%2A> Ve<xref:System.Windows.Forms.Control.Visible%2A>' den daha fazla özelliği gölgelendirmeyi deneyebilirsiniz ve yeni özellikler ekleyebilirsiniz. Alt öğe denetimleri yerleştirme gibi yaygın görevleri basitleştirmek için yeni tasarımcı fiilleri ekleyin.

- Lisansına sahip `MarqueeControl`.

- Denetimlerinizin serileştirilme şeklini ve kodun onlar için nasıl oluşturulduğunu denetleyin. Daha fazla bilgi için bkz. [dinamik kaynak kodu oluşturma ve derleme](../../reflection-and-codedom/dynamic-source-code-generation-and-compilation.md).

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.UserControl>
- <xref:System.Windows.Forms.Design.ParentControlDesigner>
- <xref:System.Windows.Forms.Design.DocumentDesigner>
- <xref:System.ComponentModel.Design.IRootDesigner>
- <xref:System.ComponentModel.Design.DesignerVerb>
- <xref:System.Drawing.Design.UITypeEditor>
- <xref:System.ComponentModel.BackgroundWorker>
