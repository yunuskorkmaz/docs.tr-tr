---
title: 'İzlenecek yol: Kullanıcı Denetiminde Sürükleme ve Bırakmayı Etkinleştirme'
description: Windows Presentation Foundation ' de sürükle ve bırak veri aktarımına katılabilen özel bir kullanıcı denetimi oluşturmayı öğrenin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- walkthrough [WPF], drag-and-drop
- drag-and-drop [WPF], walkthrough
ms.assetid: cc844419-1a77-4906-95d9-060d79107fc7
ms.openlocfilehash: 12ad47035a09995094014841b083062743fc2574
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168284"
---
# <a name="walkthrough-enabling-drag-and-drop-on-a-user-control"></a>İzlenecek yol: Kullanıcı Denetiminde Sürükleme ve Bırakmayı Etkinleştirme

Bu izlenecek yol, ' de sürükle ve bırak veri aktarımına katılabilen özel bir kullanıcı denetiminin nasıl oluşturulduğunu gösterir [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] .

Bu izlenecek yolda, <xref:System.Windows.Controls.UserControl> bir daire şeklini temsil eden özel bır WPF oluşturacaksınız. Sürükle ve bırak ile veri aktarımını etkinleştirmek için denetime işlevsellik uygulayacaksınız. Örneğin, bir daire denetiminden diğerine sürüklerseniz, Fill Color verileri kaynak çemberden hedefe kopyalanır. Bir daire denetiminden öğesine sürüklerseniz <xref:System.Windows.Controls.TextBox> , Fill renginin dize temsili öğesine kopyalanır <xref:System.Windows.Controls.TextBox> . Ayrıca, <xref:System.Windows.Controls.TextBox> sürükle ve bırak işlevlerini test etmek için iki panel denetimi içeren küçük bir uygulama da oluşturacaksınız. Panellerin bırakılan daire verilerini işlemesini sağlayan bir kod yazacaksınız. Bu, bir panelin alt öğe koleksiyonundan daireler taşımanızı veya kopyalamanızı sağlar.

Bu izlenecek yol aşağıdaki görevleri gösterir:

- Özel Kullanıcı denetimi oluşturun.

- Kullanıcı denetimini Sürükle kaynağı olacak şekilde etkinleştirin.

- Kullanıcı denetiminin bir bırakma hedefi olmasını sağlar.

- Kullanıcı denetiminden bırakılan verileri almak için bir paneli etkinleştirin.

## <a name="prerequisites"></a>Ön koşullar

Bu yönergeyi tamamlamak için Visual Studio gerekir.

## <a name="create-the-application-project"></a>Uygulama projesi oluşturma
 Bu bölümde, iki panel ve içeren bir ana sayfa içeren uygulama altyapısını oluşturacaksınız <xref:System.Windows.Controls.TextBox> .

1. Visual Basic veya Visual C# ' de adlı yeni bir WPF uygulama projesi oluşturun `DragDropExample` . Daha fazla bilgi için bkz. [Izlenecek yol: Ilk WPF Masaüstü](../getting-started/walkthrough-my-first-wpf-desktop-application.md)Uygulamam.

2. MainWindow. xaml ' i açın.

3. Açılış ve kapanış etiketleri arasına aşağıdaki biçimlendirmeyi ekleyin <xref:System.Windows.Controls.Grid> .

     Bu biçimlendirme, test uygulaması için Kullanıcı arabirimi oluşturur.

     [!code-xaml[DragDropWalkthrough#PanelsStep1XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#panelsstep1xaml)]

## <a name="add-a-new-user-control-to-the-project"></a>Projeye yeni bir kullanıcı denetimi Ekle
 Bu bölümde, projeye yeni bir kullanıcı denetimi ekleyeceksiniz.

1. Proje menüsünde **Kullanıcı denetimi Ekle**' yi seçin.

2. **Yeni öğe Ekle** iletişim kutusunda, adı olarak değiştirin `Circle.xaml` ve **Ekle**' ye tıklayın.

     Circle. xaml ve arka plan kodu projeye eklenir.

3. Circle. xaml açın.

     Bu dosya, Kullanıcı denetiminin Kullanıcı arabirimi öğelerini içerir.

4. <xref:System.Windows.Controls.Grid>Kullanıcı arabirimi olarak mavi bir daire bulunan basit bir kullanıcı denetimi oluşturmak için aşağıdaki biçimlendirmeyi köke ekleyin.

     [!code-xaml[DragDropWalkthrough#EllipseXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml#ellipsexaml)]

5. Open Circle.xaml.cs veya Circle. xaml. vb.

6. C# dilinde, bir kopya Oluşturucu oluşturmak için parametresiz oluşturucudan sonra aşağıdaki kodu ekleyin. Visual Basic, hem parametresiz bir Oluşturucu hem de kopya Oluşturucu oluşturmak için aşağıdaki kodu ekleyin.

     Kullanıcı denetiminin kopyalanmasına izin vermek için, arka plan kod dosyasına bir kopya Oluşturucu yöntemi eklersiniz. Basitleştirilmiş daire Kullanıcı denetiminde, yalnızca Kullanıcı denetiminin dolgusunu ve boyutunu kopyalayacaksınız.

     [!code-csharp[DragDropWalkthrough#CopyCtor](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#copyctor)]
     [!code-vb[DragDropWalkthrough#CopyCtor](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#copyctor)]

## <a name="add-the-user-control-to-the-main-window"></a>Kullanıcı denetimini ana pencereye ekleme

1. MainWindow. xaml ' i açın.

2. <xref:System.Windows.Window>Geçerli uygulamaya BIR XML ad alanı başvurusu oluşturmak için AŞAĞıDAKI xaml 'yi açılış etiketine ekleyin.

    ```xaml
    xmlns:local="clr-namespace:DragDropExample"
    ```

3. İlk panelde, <xref:System.Windows.Controls.StackPanel> Circle Kullanıcı denetiminin iki örneğini oluşturmak için önce AŞAĞıDAKI xaml 'yi ekleyin.

     [!code-xaml[DragDropWalkthrough#CirclesXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#circlesxaml)]

     Panelin tam XAML aşağıdaki gibi görünür.

     [!code-xaml[DragDropWalkthrough#PanelsStep2XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#panelsstep2xaml)]

## <a name="implement-drag-source-events-in-the-user-control"></a>Kullanıcı denetimindeki Sürükle kaynak olaylarını Uygula
 Bu bölümde, yöntemi geçersiz kılacak <xref:System.Windows.UIElement.OnMouseMove%2A> ve sürükle ve bırak işlemini başlatacaksınız.

 Bir sürükleme başlatılırsa (bir fare düğmesine basıldığında ve fare taşındığında), verileri bir içine aktarılacak şekilde paketleyecaksınız <xref:System.Windows.DataObject> . Bu durumda, Circle denetimi üç veri öğesini paketleyebilir; kendi renk gösterimi ve kendi bir kopyası olan Fill Color dize gösterimi.

### <a name="to-initiate-a-drag-and-drop-operation"></a>Sürükle ve bırak işlemini başlatmak için

1. Open Circle.xaml.cs veya Circle. xaml. vb.

2. <xref:System.Windows.UIElement.OnMouseMove%2A>Olay için sınıf işleme sağlamak için aşağıdaki geçersiz kılmayı ekleyin <xref:System.Windows.UIElement.MouseMove> .

     [!code-csharp[DragDropWalkthrough#OnMouseMove](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#onmousemove)]
     [!code-vb[DragDropWalkthrough#OnMouseMove](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#onmousemove)]

     Bu <xref:System.Windows.UIElement.OnMouseMove%2A> geçersiz kılma aşağıdaki görevleri gerçekleştirir:

    - Fare hareket ettirirken sol fare düğmesine basıldığını denetler.

    - Daire verisini bir olarak paketler <xref:System.Windows.DataObject> . Bu durumda, daire denetimi üç veri öğesini paketler; kendi renk gösterimi ve kendi bir kopyası olan Fill Color dize gösterimi.

    - <xref:System.Windows.DragDrop.DoDragDrop%2A?displayProperty=nameWithType>Sürükle ve bırak işlemini başlatmak için statik yöntemi çağırır. Aşağıdaki üç parametreyi <xref:System.Windows.DragDrop.DoDragDrop%2A> yöntemine geçirirsiniz:

        - `dragSource`– Bu denetime bir başvuru.

        - `data`– <xref:System.Windows.DataObject> Önceki kodda oluşturulur.

        - `allowedEffects`– Veya olan izin verilen sürükle ve bırak işlemleri <xref:System.Windows.DragDropEffects.Copy> <xref:System.Windows.DragDropEffects.Move> .

3. Uygulamayı derlemek ve çalıştırmak için **F5** tuşuna basın.

4. Daire denetimlerinden birine tıklayın ve panelleri, diğer daireyi ve ' nin üzerine sürükleyin <xref:System.Windows.Controls.TextBox> . Üzerinde sürükleme yaparken <xref:System.Windows.Controls.TextBox> , imleç bir taşımayı belirtecek şekilde değişir.

5. Bir daireyi üzerine sürüklerken <xref:System.Windows.Controls.TextBox> **CTRL** tuşuna basın. İmlecin bir kopyayı göstermek için nasıl değiştiği hakkında dikkat edin.

6. Üzerine bir daire sürükleyip bırakın <xref:System.Windows.Controls.TextBox> . Dairenin dolgusu renginin dize temsili öğesine eklenir <xref:System.Windows.Controls.TextBox> .

     ![Dairenin dolgusu renginin dize temsili](./media/dragdrop-colorstring.png "DragDrop_ColorString")

Varsayılan olarak, imleç bir sürükle ve bırak işlemi sırasında, verilerin hangi etkiyle sonuçlandığını belirten şekilde değişir. <xref:System.Windows.UIElement.GiveFeedback>Olayı işleyerek ve farklı bir imleç ayarlayarak kullanıcıya verilen geri bildirimleri özelleştirebilirsiniz.

## <a name="give-feedback-to-the-user"></a>Kullanıcıya geri bildirimde bulunun

1. Open Circle.xaml.cs veya Circle. xaml. vb.

2. <xref:System.Windows.UIElement.OnGiveFeedback%2A>Olay için sınıf işleme sağlamak için aşağıdaki geçersiz kılmayı ekleyin <xref:System.Windows.UIElement.GiveFeedback> .

     [!code-csharp[DragDropWalkthrough#OnGiveFeedback](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ongivefeedback)]
     [!code-vb[DragDropWalkthrough#OnGiveFeedback](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ongivefeedback)]

     Bu <xref:System.Windows.UIElement.OnGiveFeedback%2A> geçersiz kılma aşağıdaki görevleri gerçekleştirir:

    - <xref:System.Windows.GiveFeedbackEventArgs.Effects%2A>Bırakma hedefinin olay işleyicisinde ayarlanan değerleri denetler <xref:System.Windows.UIElement.DragOver> .

    - Değere göre özel bir imleç ayarlar <xref:System.Windows.GiveFeedbackEventArgs.Effects%2A> . İmlecin, kullanıcıya verilerin ne kadar yürürlükte olacağı hakkında görsel geri bildirim vermesi amaçlanmıştır.

3. Uygulamayı derlemek ve çalıştırmak için **F5** tuşuna basın.

4. Panel, diğer daire ve için daire denetimlerinden birini sürükleyin <xref:System.Windows.Controls.TextBox> . İmleçlerin artık geçersiz kılmada belirttiğiniz özel imleçler olduğuna dikkat edin <xref:System.Windows.UIElement.OnGiveFeedback%2A> .

     ![Özel imleçlerle sürükleyip bırakma](./media/dragdrop-customcursor.png "DragDrop_CustomCursor")

5. Öğesinden metni seçin `green` <xref:System.Windows.Controls.TextBox> .

6. `green`Metni bir daire denetimine sürükleyin. Sürükle ve bırak işleminin etkilerini belirtmek için varsayılan imleçlerin gösterildiğine dikkat edin. Geri bildirim imleci her zaman Sürükle kaynağı tarafından ayarlanır.

## <a name="implement-drop-target-events-in-the-user-control"></a>Kullanıcı denetiminde bırakma hedefi olaylarını uygulama
 Bu bölümde, Kullanıcı denetiminin bir bırakma hedefi olduğunu, Kullanıcı denetiminin bir bırakma hedefi olmasını sağlayan yöntemleri geçersiz kılacaksınız ve üzerinde bırakılan verileri işleyecek şekilde belirtirsiniz.

### <a name="to-enable-the-user-control-to-be-a-drop-target"></a>Kullanıcı denetiminin bir bırakma hedefi olmasını sağlamak için

1. Circle. xaml açın.

2. Açma <xref:System.Windows.Controls.UserControl> etiketinde <xref:System.Windows.UIElement.AllowDrop%2A> özelliği ekleyin ve olarak ayarlayın `true` .

     [!code-xaml[DragDropWalkthrough#UCTagXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml#uctagxaml)]

<xref:System.Windows.UIElement.OnDrop%2A>Yöntemi, <xref:System.Windows.UIElement.AllowDrop%2A> özelliği olarak ayarlandığında `true` ve sürükleme kaynağındaki veriler daire Kullanıcı denetiminde bırakıldığında çağrılır. Bu yöntemde, bırakılan verileri işleyecek ve verileri daireye uygulamanız gerekecektir.

### <a name="to-process-the-dropped-data"></a>Bırakılan verileri işlemek için

1. Open Circle.xaml.cs veya Circle. xaml. vb.

2. <xref:System.Windows.UIElement.OnDrop%2A>Olay için sınıf işleme sağlamak için aşağıdaki geçersiz kılmayı ekleyin <xref:System.Windows.UIElement.Drop> .

     [!code-csharp[DragDropWalkthrough#OnDrop](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondrop)]
     [!code-vb[DragDropWalkthrough#OnDrop](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondrop)]

     Bu <xref:System.Windows.UIElement.OnDrop%2A> geçersiz kılma aşağıdaki görevleri gerçekleştirir:

    - , <xref:System.Windows.DataObject.GetDataPresent%2A> Sürüklenen verilerin bir dize nesnesi içerip içermediğinden emin olmak için yöntemini kullanır.

    - , Varsa <xref:System.Windows.DataObject.GetData%2A> dize verilerini ayıklamak için yöntemini kullanır.

    - <xref:System.Windows.Media.BrushConverter>Dizeyi öğesine dönüştürmeyi denemek için öğesini kullanır <xref:System.Windows.Media.Brush> .

    - Dönüştürme başarılı olursa, ' <xref:System.Windows.Shapes.Shape.Fill%2A> nin, <xref:System.Windows.Shapes.Ellipse> daire denetiminin Kullanıcı arabirimini sağlayan öğesine fırça uygular.

    - <xref:System.Windows.UIElement.Drop>Olayı işlenmiş olarak işaretler. Bu olayı alan diğer öğelerin, Circle Kullanıcı denetiminin bunu ele aldığından emin olmak için bırakma olayını işlenmiş olarak işaretlemelisiniz.

3. Uygulamayı derlemek ve çalıştırmak için **F5** tuşuna basın.

4. İçindeki metni seçin `green` <xref:System.Windows.Controls.TextBox> .

5. Metni bir daire denetimine sürükleyin ve bırakın. Daire mavi ile yeşil arasında değişir.

     ![Bir dizeyi fırçaya Dönüştür](./media/dragdrop-dropgreentext.png "DragDrop_DropGreenText")

6. Metni içine yazın `green` <xref:System.Windows.Controls.TextBox> .

7. İçindeki metni seçin `gre` <xref:System.Windows.Controls.TextBox> .

8. Bir daire denetimine sürükleyin ve bırakın. İmlecin, bırakmaya izin verildiğini belirtmek için değiştiği, ancak dairenin rengi geçerli bir renk olmadığından, bu değişikliğin değişmediğine dikkat edin `gre` .

9. Yeşil daire denetiminden sürükleyin ve mavi daire denetiminin üzerine bırakın. Daire mavi ile yeşil arasında değişir. Hangi imlecin gösterildiğine dikkat edin, <xref:System.Windows.Controls.TextBox> ya da dairenin Sürükle kaynağı olup olmamasına bağlıdır.

<xref:System.Windows.UIElement.AllowDrop%2A>Özelliği `true` bırakılan verileri olarak ayarlamak ve işlemek bir öğenin bir bırakma hedefi olmasını sağlamak için gereklidir. Ancak, daha iyi bir kullanıcı deneyimi sağlamak için,, ve olaylarını da işlemeniz gerekir <xref:System.Windows.UIElement.DragEnter> <xref:System.Windows.UIElement.DragLeave> <xref:System.Windows.UIElement.DragOver> . Bu olaylarda, denetimler gerçekleştirebilir ve veriler kesilmeden önce kullanıcıya ek geri bildirim sağlayabilirsiniz.

Veriler, Circle Kullanıcı denetiminin üzerine sürüklendiğinde denetim, sürüklenen verileri işleip işleyemeyeceğini, sürükleme kaynağını bilgilendirmelidir. Denetim, verilerin nasıl işleyeceğini bilmez ise, bırakmayı reddetmelidir. Bunu yapmak için, <xref:System.Windows.UIElement.DragOver> olayı işleyecek ve özelliğini ayarlayacaksınız <xref:System.Windows.DragEventArgs.Effects%2A> .

### <a name="to-verify-that-the-data-drop-is-allowed"></a>Veri bırakmaya izin verildiğini doğrulamak için

1. Open Circle.xaml.cs veya Circle. xaml. vb.

2. <xref:System.Windows.UIElement.OnDragOver%2A>Olay için sınıf işleme sağlamak için aşağıdaki geçersiz kılmayı ekleyin <xref:System.Windows.UIElement.DragOver> .

     [!code-csharp[DragDropWalkthrough#OnDragOver](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragover)]
     [!code-vb[DragDropWalkthrough#OnDragOver](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragover)]

     Bu <xref:System.Windows.UIElement.OnDragOver%2A> geçersiz kılma aşağıdaki görevleri gerçekleştirir:

    - <xref:System.Windows.DragEventArgs.Effects%2A>Özelliğini olarak ayarlar <xref:System.Windows.DragDropEffects.None> .

    - <xref:System.Windows.UIElement.OnDrop%2A>Circle Kullanıcı denetiminin sürüklenen verileri işleyemeyeceğini anlamak için yönteminde gerçekleştirilen denetimleri gerçekleştirir.

    - Kullanıcı denetimi verileri işleyebiliyorsanız, <xref:System.Windows.DragEventArgs.Effects%2A> özelliğini veya olarak ayarlar <xref:System.Windows.DragDropEffects.Copy> <xref:System.Windows.DragDropEffects.Move> .

3. Uygulamayı derlemek ve çalıştırmak için **F5** tuşuna basın.

4. İçindeki metni seçin `gre` <xref:System.Windows.Controls.TextBox> .

5. Metni bir daire denetimine sürükleyin. İmlecin şimdi, geçerli bir renk olmadığından, bırakmaya izin verilmediğini göstermek için değişiklik olduğuna dikkat edin `gre` .

 Bırakma işleminin önizlemesini uygulayarak Kullanıcı deneyimini daha da geliştirebilirsiniz. Circle Kullanıcı denetimi için ve yöntemlerini geçersiz kılacaksınız <xref:System.Windows.UIElement.OnDragEnter%2A> <xref:System.Windows.UIElement.OnDragLeave%2A> . Veriler denetimin üzerine sürüklendiğinde, geçerli arka plan <xref:System.Windows.Shapes.Shape.Fill%2A> bir yer tutucu değişkenine kaydedilir. Daha sonra dize bir fırçaya dönüştürülüp <xref:System.Windows.Shapes.Ellipse> dairenin Kullanıcı arabirimini sağlayan öğesine uygulanır. Verilerin bırakılmadan dışına sürüklenmesi durumunda özgün <xref:System.Windows.Shapes.Shape.Fill%2A> değer, daireye yeniden uygulanır.

### <a name="to-preview-the-effects-of-the-drag-and-drop-operation"></a>Sürükle ve bırak işleminin etkilerini önizlemek için

1. Open Circle.xaml.cs veya Circle. xaml. vb.

2. Circle sınıfında adlı bir özel <xref:System.Windows.Media.Brush> değişken bildirin `_previousFill` ve bunu olarak başlatın `null` .

     [!code-csharp[DragDropWalkthrough#Brush](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#brush)]
     [!code-vb[DragDropWalkthrough#Brush](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#brush)]

3. <xref:System.Windows.UIElement.OnDragEnter%2A>Olay için sınıf işleme sağlamak için aşağıdaki geçersiz kılmayı ekleyin <xref:System.Windows.UIElement.DragEnter> .

     [!code-csharp[DragDropWalkthrough#OnDragEnter](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragenter)]
     [!code-vb[DragDropWalkthrough#OnDragEnter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragenter)]

     Bu <xref:System.Windows.UIElement.OnDragEnter%2A> geçersiz kılma aşağıdaki görevleri gerçekleştirir:

    - <xref:System.Windows.Shapes.Shape.Fill%2A>Öğesinin özelliğini <xref:System.Windows.Shapes.Ellipse> `_previousFill` değişkenine kaydeder.

    - <xref:System.Windows.UIElement.OnDrop%2A>Verilerin bir öğesine dönüştürülüp dönüştürülmeyeceğini anlamak için yönteminde gerçekleştirilen denetimleri gerçekleştirir <xref:System.Windows.Media.Brush> .

    - Veriler geçerli bir değerine dönüştürülürse, <xref:System.Windows.Media.Brush> ' nin öğesine uygular <xref:System.Windows.Shapes.Shape.Fill%2A> <xref:System.Windows.Shapes.Ellipse> .

4. <xref:System.Windows.UIElement.OnDragLeave%2A>Olay için sınıf işleme sağlamak için aşağıdaki geçersiz kılmayı ekleyin <xref:System.Windows.UIElement.DragLeave> .

     [!code-csharp[DragDropWalkthrough#OnDragLeave](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragleave)]
     [!code-vb[DragDropWalkthrough#OnDragLeave](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragleave)]

     Bu <xref:System.Windows.UIElement.OnDragLeave%2A> geçersiz kılma aşağıdaki görevleri gerçekleştirir:

    - Değişkenine, <xref:System.Windows.Media.Brush> `_previousFill` <xref:System.Windows.Shapes.Shape.Fill%2A> <xref:System.Windows.Shapes.Ellipse> Circle Kullanıcı denetiminin Kullanıcı arabirimini sağlayan öğesine uygular.

5. Uygulamayı derlemek ve çalıştırmak için **F5** tuşuna basın.

6. İçindeki metni seçin `green` <xref:System.Windows.Controls.TextBox> .

7. Metni bırakmadan bir daire denetiminin üzerine sürükleyin. Daire mavi ile yeşil arasında değişir.

     ![Bir sürükle&#45;ve&#45;bırakma işleminin etkilerini önizleyin](./media/dragdrop-previeweffects.png "DragDrop_PreviewEffects")

8. Metni daire denetiminden uzağa sürükleyin. Daire, yeşil ve mavi arasında değişir.

## <a name="enable-a-panel-to-receive-dropped-data"></a>Bir paneli bırakılan verileri alacak şekilde etkinleştirme

Bu bölümde, daire kullanıcı denetimlerini barındıran bölmeleri, sürüklenen daire verileri için bırakma hedefleri olarak davranacak şekilde etkinleştirirsiniz. Bir daireyi bir panelden diğerine taşımanızı veya bir daireyi Sürükleyip bırakırken **CTRL** tuşunu basılı tutarak bir daire denetiminin kopyasını yapmanızı sağlayan kodu uygulayacaksınız.

1. MainWindow. xaml ' i açın.

2. Aşağıdaki XAML 'de gösterildiği gibi, denetimlerin her birinde <xref:System.Windows.Controls.StackPanel> ve olayları için işleyiciler ekleyin <xref:System.Windows.UIElement.DragOver> <xref:System.Windows.UIElement.Drop> . <xref:System.Windows.UIElement.DragOver>Olay işleyicisini adlandırın, `panel_DragOver` ve <xref:System.Windows.UIElement.Drop> olay işleyicisini adlandırın `panel_Drop` .

     [!code-xaml[DragDropWalkthrough#PanelsXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml#panelsxaml)]

3. MainWindows.xaml.cs veya MainWindow. xaml. vb dosyasını açın.

4. Olay işleyicisi için aşağıdaki kodu ekleyin <xref:System.Windows.UIElement.DragOver> .

     [!code-csharp[DragDropWalkthrough#PanelDragOver](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml.cs#paneldragover)]
     [!code-vb[DragDropWalkthrough#PanelDragOver](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/MainWindow.xaml.vb#paneldragover)]

     Bu <xref:System.Windows.UIElement.DragOver> olay işleyicisi aşağıdaki görevleri gerçekleştirir:

    - Sürüklenen verilerin, <xref:System.Windows.DataObject> Circle Kullanıcı denetimiyle paketlenmiş ve çağrısına geçilen "nesne" verilerini içerip içermediğini denetler <xref:System.Windows.DragDrop.DoDragDrop%2A> .

    - "Nesne" verileri mevcutsa, **CTRL** tuşuna basıldığını denetler.

    - **CTRL** tuşuna basıldığında <xref:System.Windows.DragEventArgs.Effects%2A> özelliğini olarak ayarlar <xref:System.Windows.DragDropEffects.Copy> . Aksi takdirde, <xref:System.Windows.DragEventArgs.Effects%2A> özelliğini olarak ayarlayın <xref:System.Windows.DragDropEffects.Move> .

5. Olay işleyicisi için aşağıdaki kodu ekleyin <xref:System.Windows.UIElement.Drop> .

     [!code-csharp[DragDropWalkthrough#PanelDrop](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml.cs#paneldrop)]
     [!code-vb[DragDropWalkthrough#PanelDrop](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/MainWindow.xaml.vb#paneldrop)]

     Bu <xref:System.Windows.UIElement.Drop> olay işleyicisi aşağıdaki görevleri gerçekleştirir:

    - <xref:System.Windows.UIElement.Drop>Etkinliğin zaten işlenmiş olup olmadığını denetler. Örneğin, bir daire olayı işleyen başka bir daire üzerinde bırakıldığında <xref:System.Windows.UIElement.Drop> , daireyi içeren panelin da işlenmesi için bu işleci istemezsiniz.

    - <xref:System.Windows.UIElement.Drop>Olay işlenmezse, **CTRL** tuşuna basıldığını denetler.

    - Oluştuğunda **CTRL** tuşuna basıldığında <xref:System.Windows.UIElement.Drop> , daire denetiminin bir kopyasını oluşturur ve <xref:System.Windows.Controls.Panel.Children%2A> koleksiyonuna ekler <xref:System.Windows.Controls.StackPanel> .

    - **CTRL** tuşuna basılsa, daireyi <xref:System.Windows.Controls.Panel.Children%2A> üst bölmesinin koleksiyonundan, <xref:System.Windows.Controls.Panel.Children%2A> üzerinde bırakılan panelin koleksiyonuna taşımış olur.

    - Yöntemi, <xref:System.Windows.DragEventArgs.Effects%2A> <xref:System.Windows.DragDrop.DoDragDrop%2A> bir taşıma veya kopyalama işleminin gerçekleştirilip gerçekleştirilmediğini bildirmek için özelliği ayarlar.

6. Uygulamayı derlemek ve çalıştırmak için **F5** tuşuna basın.

7. Öğesinden metni seçin `green` <xref:System.Windows.Controls.TextBox> .

8. Metni bir daire denetiminin üzerine sürükleyin ve bırakın.

9. Sol panelden bir daire denetimini sağ panele sürükleyin ve bırakın. Daire, <xref:System.Windows.Controls.Panel.Children%2A> sol bölmenin koleksiyonundan kaldırılır ve sağ bölmenin alt öğe koleksiyonuna eklenir.

10. Bir daire denetimini, içindeki panelden diğer panele sürükleyin ve **CTRL** tuşuna basarak bırakın. Daire kopyalanır ve kopya, <xref:System.Windows.Controls.Panel.Children%2A> alan paneli koleksiyonuna eklenir.

     ![CTRL tuşuna basıldığında bir daireyi sürükleme](./media/dragdrop-paneldrop.png "DragDrop_PanelDrop")

## <a name="see-also"></a>Ayrıca bkz.

- [Sürükleme ve Bırakmaya Genel Bakış](drag-and-drop-overview.md)
