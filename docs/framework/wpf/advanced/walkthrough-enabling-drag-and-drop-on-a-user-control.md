---
title: 'İzlenecek yol: Kullanıcı Denetiminde Sürükleme ve Bırakmayı Etkinleştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- walkthrough [WPF], drag-and-drop
- drag-and-drop [WPF], walkthrough
ms.assetid: cc844419-1a77-4906-95d9-060d79107fc7
ms.openlocfilehash: 80fd55be9230729cb8336be91c1d8fb4f7f3f080
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/20/2019
ms.locfileid: "68364256"
---
# <a name="walkthrough-enabling-drag-and-drop-on-a-user-control"></a>İzlenecek yol: Kullanıcı Denetiminde Sürükleme ve Bırakmayı Etkinleştirme

Bu izlenecek yol, ' de [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]sürükle ve bırak veri aktarımına katılabilen özel bir kullanıcı denetiminin nasıl oluşturulduğunu gösterir.

Bu izlenecek yolda, bir daire şeklini temsil eden özel <xref:System.Windows.Controls.UserControl> bir WPF oluşturacaksınız. Sürükle ve bırak ile veri aktarımını etkinleştirmek için denetime işlevsellik uygulayacaksınız. Örneğin, bir daire denetiminden diğerine sürüklerseniz, Fill Color verileri kaynak çemberden hedefe kopyalanır. Bir daire denetiminden öğesine <xref:System.Windows.Controls.TextBox>sürüklerseniz, Fill renginin dize temsili <xref:System.Windows.Controls.TextBox>öğesine kopyalanır. Ayrıca, sürükle ve bırak işlevlerini test <xref:System.Windows.Controls.TextBox> etmek için iki panel denetimi içeren küçük bir uygulama da oluşturacaksınız. Panellerin bırakılan daire verilerini işlemesini sağlayan bir kod yazacaksınız. Bu, bir panelin alt öğe koleksiyonundan daireler taşımanızı veya kopyalamanızı sağlar.

Bu izlenecek yol aşağıdaki görevleri gösterir:

- Özel Kullanıcı denetimi oluşturun.

- Kullanıcı denetimini Sürükle kaynağı olacak şekilde etkinleştirin.

- Kullanıcı denetiminin bir bırakma hedefi olmasını sağlar.

- Kullanıcı denetiminden bırakılan verileri almak için bir paneli etkinleştirin.

## <a name="prerequisites"></a>Önkoşullar

Bu yönergeyi tamamlamak için Visual Studio gerekir.

## <a name="create-the-application-project"></a>Uygulama projesi oluşturma
 Bu bölümde, iki panel ve <xref:System.Windows.Controls.TextBox>içeren bir ana sayfa içeren uygulama altyapısını oluşturacaksınız.

1. Visual Basic veya görsel C# adında `DragDropExample`yeni bir WPF uygulama projesi oluşturun. Daha fazla bilgi için bkz [. İzlenecek yol: İlk WPF Masaüstü](../getting-started/walkthrough-my-first-wpf-desktop-application.md)Uygulamam.

2. MainWindow. xaml ' i açın.

3. Açılış ve kapanış <xref:System.Windows.Controls.Grid> etiketleri arasına aşağıdaki biçimlendirmeyi ekleyin.

     Bu biçimlendirme, test uygulaması için Kullanıcı arabirimi oluşturur.

     [!code-xaml[DragDropWalkthrough#PanelsStep1XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#panelsstep1xaml)]

## <a name="add-a-new-user-control-to-the-project"></a>Projeye yeni bir kullanıcı denetimi Ekle
 Bu bölümde, projeye yeni bir kullanıcı denetimi ekleyeceksiniz.

1. Proje menüsünde **Kullanıcı denetimi Ekle**' yi seçin.

2. **Yeni öğe Ekle** iletişim kutusunda, adı olarak `Circle.xaml`değiştirin ve **Ekle**' ye tıklayın.

     Circle. xaml ve arka plan kodu projeye eklenir.

3. Circle. xaml açın.

     Bu dosya, Kullanıcı denetiminin Kullanıcı arabirimi öğelerini içerir.

4. Kullanıcı arabirimi olarak mavi bir daire bulunan <xref:System.Windows.Controls.Grid> basit bir kullanıcı denetimi oluşturmak için aşağıdaki biçimlendirmeyi köke ekleyin.

     [!code-xaml[DragDropWalkthrough#EllipseXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml#ellipsexaml)]

5. Open Circle.xaml.cs veya Circle. xaml. vb.

6. İçinde C#, bir kopya Oluşturucu oluşturmak için parametresiz oluşturucudan sonra aşağıdaki kodu ekleyin. Visual Basic, hem parametresiz bir Oluşturucu hem de kopya Oluşturucu oluşturmak için aşağıdaki kodu ekleyin.

     Kullanıcı denetiminin kopyalanmasına izin vermek için, arka plan kod dosyasına bir kopya Oluşturucu yöntemi eklersiniz. Basitleştirilmiş daire Kullanıcı denetiminde, yalnızca Kullanıcı denetiminin dolgusunu ve boyutunu kopyalayacaksınız.

     [!code-csharp[DragDropWalkthrough#CopyCtor](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#copyctor)]
     [!code-vb[DragDropWalkthrough#CopyCtor](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#copyctor)]

## <a name="add-the-user-control-to-the-main-window"></a>Kullanıcı denetimini ana pencereye ekleme

1. MainWindow. xaml ' i açın.

2. Geçerli uygulamaya bir XML ad alanı başvurusu <xref:System.Windows.Window> oluşturmak için aşağıdaki xaml 'yi açılış etiketine ekleyin.

    ```
    xmlns:local="clr-namespace:DragDropExample"
    ```

3. İlk panelde, <xref:System.Windows.Controls.StackPanel>Circle Kullanıcı denetiminin iki örneğini oluşturmak için önce aşağıdaki xaml 'yi ekleyin.

     [!code-xaml[DragDropWalkthrough#CirclesXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#circlesxaml)]

     Panelin tam XAML aşağıdaki gibi görünür.

     [!code-xaml[DragDropWalkthrough#PanelsStep2XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#panelsstep2xaml)]

## <a name="implement-drag-source-events-in-the-user-control"></a>Kullanıcı denetimindeki Sürükle kaynak olaylarını Uygula
 Bu bölümde, <xref:System.Windows.UIElement.OnMouseMove%2A> yöntemi geçersiz kılacak ve sürükle ve bırak işlemini başlatacaksınız.

 Bir sürükleme başlatılırsa (bir fare düğmesine basıldığında ve fare taşındığında), verileri bir <xref:System.Windows.DataObject>içine aktarılacak şekilde paketleyecaksınız. Bu durumda, Circle denetimi üç veri öğesini paketleyebilir; kendi renk gösterimi ve kendi bir kopyası olan Fill Color dize gösterimi.

### <a name="to-initiate-a-drag-and-drop-operation"></a>Sürükle ve bırak işlemini başlatmak için

1. Open Circle.xaml.cs veya Circle. xaml. vb.

2. Olay için sınıf <xref:System.Windows.UIElement.OnMouseMove%2A> işleme sağlamak için aşağıdaki geçersiz kılmayı ekleyin. <xref:System.Windows.UIElement.MouseMove>

     [!code-csharp[DragDropWalkthrough#OnMouseMove](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#onmousemove)]
     [!code-vb[DragDropWalkthrough#OnMouseMove](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#onmousemove)]

     Bu <xref:System.Windows.UIElement.OnMouseMove%2A> geçersiz kılma aşağıdaki görevleri gerçekleştirir:

    - Fare hareket ettirirken sol fare düğmesine basıldığını denetler.

    - Daire verisini bir <xref:System.Windows.DataObject>olarak paketler. Bu durumda, daire denetimi üç veri öğesini paketler; kendi renk gösterimi ve kendi bir kopyası olan Fill Color dize gösterimi.

    - Sürükle ve bırak <xref:System.Windows.DragDrop.DoDragDrop%2A?displayProperty=nameWithType> işlemini başlatmak için statik yöntemi çağırır. Aşağıdaki üç parametreyi <xref:System.Windows.DragDrop.DoDragDrop%2A> yöntemine geçirirsiniz:

        - `dragSource`– Bu denetime bir başvuru.

        - `data`– Önceki kodda oluşturulur. <xref:System.Windows.DataObject>

        - `allowedEffects`– Veya <xref:System.Windows.DragDropEffects.Copy> <xref:System.Windows.DragDropEffects.Move>olan izin verilen sürükle ve bırak işlemleri.

3. Uygulamayı derlemek ve çalıştırmak için **F5** tuşuna basın.

4. Daire denetimlerinden birine tıklayın ve panelleri, diğer daireyi ve <xref:System.Windows.Controls.TextBox>' nin üzerine sürükleyin. Üzerinde sürükleme yaparken <xref:System.Windows.Controls.TextBox>, imleç bir taşımayı belirtecek şekilde değişir.

5. Bir daireyi üzerine <xref:System.Windows.Controls.TextBox>sürüklerken **CTRL** tuşuna basın. İmlecin bir kopyayı göstermek için nasıl değiştiği hakkında dikkat edin.

6. Üzerine bir daire sürükleyip bırakın <xref:System.Windows.Controls.TextBox>. Dairenin dolgusu renginin dize temsili öğesine <xref:System.Windows.Controls.TextBox>eklenir.

     ![Dairenin dolgusu renginin dize temsili](./media/dragdrop-colorstring.png "DragDrop_ColorString")

Varsayılan olarak, imleç bir sürükle ve bırak işlemi sırasında, verilerin hangi etkiyle sonuçlandığını belirten şekilde değişir. <xref:System.Windows.UIElement.GiveFeedback> Olayı işleyerek ve farklı bir imleç ayarlayarak kullanıcıya verilen geri bildirimleri özelleştirebilirsiniz.

## <a name="give-feedback-to-the-user"></a>Kullanıcıya geri bildirimde bulunun

1. Open Circle.xaml.cs veya Circle. xaml. vb.

2. Olay için sınıf <xref:System.Windows.UIElement.OnGiveFeedback%2A> işleme sağlamak için aşağıdaki geçersiz kılmayı ekleyin. <xref:System.Windows.UIElement.GiveFeedback>

     [!code-csharp[DragDropWalkthrough#OnGiveFeedback](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ongivefeedback)]
     [!code-vb[DragDropWalkthrough#OnGiveFeedback](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ongivefeedback)]

     Bu <xref:System.Windows.UIElement.OnGiveFeedback%2A> geçersiz kılma aşağıdaki görevleri gerçekleştirir:

    - Bırakma hedefinin olay işleyicisinde ayarlanan <xref:System.Windows.GiveFeedbackEventArgs.Effects%2A> <xref:System.Windows.UIElement.DragOver> değerleri denetler.

    - <xref:System.Windows.GiveFeedbackEventArgs.Effects%2A> Değere göre özel bir imleç ayarlar. İmlecin, kullanıcıya verilerin ne kadar yürürlükte olacağı hakkında görsel geri bildirim vermesi amaçlanmıştır.

3. Uygulamayı derlemek ve çalıştırmak için **F5** tuşuna basın.

4. Panel, diğer daire ve için <xref:System.Windows.Controls.TextBox>daire denetimlerinden birini sürükleyin. İmleçlerin artık <xref:System.Windows.UIElement.OnGiveFeedback%2A> geçersiz kılmada belirttiğiniz özel imleçler olduğuna dikkat edin.

     ![Özel imleçlerle sürükleyip bırakma](./media/dragdrop-customcursor.png "DragDrop_CustomCursor")

5. Öğesinden metni `green`seçin. <xref:System.Windows.Controls.TextBox>

6. `green` Metni bir daire denetimine sürükleyin. Sürükle ve bırak işleminin etkilerini belirtmek için varsayılan imleçlerin gösterildiğine dikkat edin. Geri bildirim imleci her zaman Sürükle kaynağı tarafından ayarlanır.

## <a name="implement-drop-target-events-in-the-user-control"></a>Kullanıcı denetiminde bırakma hedefi olaylarını uygulama
 Bu bölümde, Kullanıcı denetiminin bir bırakma hedefi olduğunu, Kullanıcı denetiminin bir bırakma hedefi olmasını sağlayan yöntemleri geçersiz kılacaksınız ve üzerinde bırakılan verileri işleyecek şekilde belirtirsiniz.

### <a name="to-enable-the-user-control-to-be-a-drop-target"></a>Kullanıcı denetiminin bir bırakma hedefi olmasını sağlamak için

1. Circle. xaml açın.

2. Açma <xref:System.Windows.Controls.UserControl> etiketinde <xref:System.Windows.UIElement.AllowDrop%2A> özelliği ekleyin ve olarak `true`ayarlayın.

     [!code-xaml[DragDropWalkthrough#UCTagXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml#uctagxaml)]

Yöntemi, <xref:System.Windows.UIElement.AllowDrop%2A> özelliği olarak`true` ayarlandığında ve sürükleme kaynağındaki veriler daire Kullanıcı denetiminde bırakıldığında çağrılır. <xref:System.Windows.UIElement.OnDrop%2A> Bu yöntemde, bırakılan verileri işleyecek ve verileri daireye uygulamanız gerekecektir.

### <a name="to-process-the-dropped-data"></a>Bırakılan verileri işlemek için

1. Open Circle.xaml.cs veya Circle. xaml. vb.

2. Olay için sınıf <xref:System.Windows.UIElement.OnDrop%2A> işleme sağlamak için aşağıdaki geçersiz kılmayı ekleyin. <xref:System.Windows.UIElement.Drop>

     [!code-csharp[DragDropWalkthrough#OnDrop](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondrop)]
     [!code-vb[DragDropWalkthrough#OnDrop](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondrop)]

     Bu <xref:System.Windows.UIElement.OnDrop%2A> geçersiz kılma aşağıdaki görevleri gerçekleştirir:

    - , Sürüklenen verilerin bir dize nesnesi içerip içermediğinden emin olmak için yönteminikullanır.<xref:System.Windows.DataObject.GetDataPresent%2A>

    - , Varsa dize verilerini ayıklamak için yönteminikullanır.<xref:System.Windows.DataObject.GetData%2A>

    - Dizeyi öğesine dönüştürmeyi denemek <xref:System.Windows.Media.BrushConverter> için öğesini kullanır <xref:System.Windows.Media.Brush>.

    - Dönüştürme başarılı olursa, ' <xref:System.Windows.Shapes.Shape.Fill%2A> <xref:System.Windows.Shapes.Ellipse> nin, daire denetiminin Kullanıcı arabirimini sağlayan öğesine fırça uygular.

    - <xref:System.Windows.UIElement.Drop> Olayı işlenmiş olarak işaretler. Bu olayı alan diğer öğelerin, Circle Kullanıcı denetiminin bunu ele aldığından emin olmak için bırakma olayını işlenmiş olarak işaretlemelisiniz.

3. Uygulamayı derlemek ve çalıştırmak için **F5** tuşuna basın.

4. İçindeki metni `green`seçin. <xref:System.Windows.Controls.TextBox>

5. Metni bir daire denetimine sürükleyin ve bırakın. Daire mavi ile yeşil arasında değişir.

     ![Bir dizeyi fırçaya Dönüştür](./media/dragdrop-dropgreentext.png "DragDrop_DropGreenText")

6. `green` Metni<xref:System.Windows.Controls.TextBox>içine yazın.

7. İçindeki metni `gre`seçin. <xref:System.Windows.Controls.TextBox>

8. Bir daire denetimine sürükleyin ve bırakın. İmlecin, bırakmaya izin verildiğini belirtmek için değiştiği, ancak dairenin rengi geçerli bir renk olmadığından, bu değişikliğin değişmediğine `gre` dikkat edin.

9. Yeşil daire denetiminden sürükleyin ve mavi daire denetiminin üzerine bırakın. Daire mavi ile yeşil arasında değişir. Hangi imlecin gösterildiğine dikkat edin, ya da <xref:System.Windows.Controls.TextBox> dairenin Sürükle kaynağı olup olmamasına bağlıdır.

Özelliği bırakılan verileri olarak `true` ayarlamak ve işlemek bir öğenin bir bırakma hedefi olmasını sağlamak için gereklidir. <xref:System.Windows.UIElement.AllowDrop%2A> Ancak, daha iyi bir kullanıcı deneyimi sağlamak için,, ve <xref:System.Windows.UIElement.DragEnter> <xref:System.Windows.UIElement.DragOver> olaylarını da işlemeniz <xref:System.Windows.UIElement.DragLeave>gerekir. Bu olaylarda, denetimler gerçekleştirebilir ve veriler kesilmeden önce kullanıcıya ek geri bildirim sağlayabilirsiniz.

Veriler, Circle Kullanıcı denetiminin üzerine sürüklendiğinde denetim, sürüklenen verileri işleip işleyemeyeceğini, sürükleme kaynağını bilgilendirmelidir. Denetim, verilerin nasıl işleyeceğini bilmez ise, bırakmayı reddetmelidir. Bunu yapmak için, <xref:System.Windows.UIElement.DragOver> olayı işleyecek ve <xref:System.Windows.DragEventArgs.Effects%2A> özelliğini ayarlayacaksınız.

### <a name="to-verify-that-the-data-drop-is-allowed"></a>Veri bırakmaya izin verildiğini doğrulamak için

1. Open Circle.xaml.cs veya Circle. xaml. vb.

2. Olay için sınıf <xref:System.Windows.UIElement.OnDragOver%2A> işleme sağlamak için aşağıdaki geçersiz kılmayı ekleyin. <xref:System.Windows.UIElement.DragOver>

     [!code-csharp[DragDropWalkthrough#OnDragOver](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragover)]
     [!code-vb[DragDropWalkthrough#OnDragOver](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragover)]

     Bu <xref:System.Windows.UIElement.OnDragOver%2A> geçersiz kılma aşağıdaki görevleri gerçekleştirir:

    - <xref:System.Windows.DragEventArgs.Effects%2A> Özelliğini olarak<xref:System.Windows.DragDropEffects.None>ayarlar.

    - Circle Kullanıcı denetiminin sürüklenen verileri işleyemeyeceğini anlamak için <xref:System.Windows.UIElement.OnDrop%2A> yönteminde gerçekleştirilen denetimleri gerçekleştirir.

    - Kullanıcı denetimi verileri işleyebiliyorsanız, <xref:System.Windows.DragEventArgs.Effects%2A> özelliğini veya <xref:System.Windows.DragDropEffects.Move>olarak <xref:System.Windows.DragDropEffects.Copy> ayarlar.

3. Uygulamayı derlemek ve çalıştırmak için **F5** tuşuna basın.

4. İçindeki metni `gre`seçin. <xref:System.Windows.Controls.TextBox>

5. Metni bir daire denetimine sürükleyin. İmlecin şimdi, geçerli bir renk olmadığından, bırakmaya izin verilmediğini `gre` göstermek için değişiklik olduğuna dikkat edin.

 Bırakma işleminin önizlemesini uygulayarak Kullanıcı deneyimini daha da geliştirebilirsiniz. Circle Kullanıcı denetimi için <xref:System.Windows.UIElement.OnDragEnter%2A> ve <xref:System.Windows.UIElement.OnDragLeave%2A> yöntemlerini geçersiz kılacaksınız. Veriler denetimin üzerine sürüklendiğinde, geçerli arka plan <xref:System.Windows.Shapes.Shape.Fill%2A> bir yer tutucu değişkenine kaydedilir. Daha sonra dize bir fırçaya dönüştürülüp dairenin Kullanıcı arabirimini sağlayan öğesine <xref:System.Windows.Shapes.Ellipse> uygulanır. Verilerin bırakılmadan dışına sürüklenmesi durumunda özgün <xref:System.Windows.Shapes.Shape.Fill%2A> değer, daireye yeniden uygulanır.

### <a name="to-preview-the-effects-of-the-drag-and-drop-operation"></a>Sürükle ve bırak işleminin etkilerini önizlemek için

1. Open Circle.xaml.cs veya Circle. xaml. vb.

2. Circle sınıfında adlı <xref:System.Windows.Media.Brush> `_previousFill` bir özel değişken bildirin ve bunu olarak `null`başlatın.

     [!code-csharp[DragDropWalkthrough#Brush](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#brush)]
     [!code-vb[DragDropWalkthrough#Brush](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#brush)]

3. Olay için sınıf <xref:System.Windows.UIElement.OnDragEnter%2A> işleme sağlamak için aşağıdaki geçersiz kılmayı ekleyin. <xref:System.Windows.UIElement.DragEnter>

     [!code-csharp[DragDropWalkthrough#OnDragEnter](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragenter)]
     [!code-vb[DragDropWalkthrough#OnDragEnter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragenter)]

     Bu <xref:System.Windows.UIElement.OnDragEnter%2A> geçersiz kılma aşağıdaki görevleri gerçekleştirir:

    - <xref:System.Windows.Shapes.Shape.Fill%2A> Öğesinin özelliğini`_previousFill`değişkenine kaydeder. <xref:System.Windows.Shapes.Ellipse>

    - Verilerin bir <xref:System.Windows.UIElement.OnDrop%2A> <xref:System.Windows.Media.Brush>öğesine dönüştürülüp dönüştürülmeyeceğini anlamak için yönteminde gerçekleştirilen denetimleri gerçekleştirir.

    - Veriler geçerli <xref:System.Windows.Media.Brush>bir değerine dönüştürülürse, ' <xref:System.Windows.Shapes.Shape.Fill%2A> nin <xref:System.Windows.Shapes.Ellipse>öğesine uygular.

4. Olay için sınıf <xref:System.Windows.UIElement.OnDragLeave%2A> işleme sağlamak için aşağıdaki geçersiz kılmayı ekleyin. <xref:System.Windows.UIElement.DragLeave>

     [!code-csharp[DragDropWalkthrough#OnDragLeave](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragleave)]
     [!code-vb[DragDropWalkthrough#OnDragLeave](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragleave)]

     Bu <xref:System.Windows.UIElement.OnDragLeave%2A> geçersiz kılma aşağıdaki görevleri gerçekleştirir:

    - Değişkenine, Circle Kullanıcı denetiminin Kullanıcı arabirimini sağlayan <xref:System.Windows.Shapes.Shape.Fill%2A> öğesine uygular.<xref:System.Windows.Shapes.Ellipse> <xref:System.Windows.Media.Brush> `_previousFill`

5. Uygulamayı derlemek ve çalıştırmak için **F5** tuşuna basın.

6. İçindeki metni `green`seçin. <xref:System.Windows.Controls.TextBox>

7. Metni bırakmadan bir daire denetiminin üzerine sürükleyin. Daire mavi ile yeşil arasında değişir.

     ![Sürükle&#45;ve&#45;bırak işleminin etkilerini önizleyin](./media/dragdrop-previeweffects.png "DragDrop_PreviewEffects")

8. Metni daire denetiminden uzağa sürükleyin. Daire, yeşil ve mavi arasında değişir.

## <a name="enable-a-panel-to-receive-dropped-data"></a>Bir paneli bırakılan verileri alacak şekilde etkinleştirme

Bu bölümde, daire kullanıcı denetimlerini barındıran bölmeleri, sürüklenen daire verileri için bırakma hedefleri olarak davranacak şekilde etkinleştirirsiniz. Bir daireyi bir panelden diğerine taşımanızı veya bir daireyi Sürükleyip bırakırken **CTRL** tuşunu basılı tutarak bir daire denetiminin kopyasını yapmanızı sağlayan kodu uygulayacaksınız.

1. MainWindow. xaml ' i açın.

2. Aşağıdaki XAML 'de gösterildiği gibi, <xref:System.Windows.Controls.StackPanel> denetimlerin her birinde <xref:System.Windows.UIElement.DragOver> ve <xref:System.Windows.UIElement.Drop> olayları için işleyiciler ekleyin. Olay işleyicisini adlandırın, ve <xref:System.Windows.UIElement.Drop> olay işleyicisini `panel_Drop`adlandırın. `panel_DragOver` <xref:System.Windows.UIElement.DragOver>

     [!code-xaml[DragDropWalkthrough#PanelsXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml#panelsxaml)]

3. MainWindows.xaml.cs veya MainWindow. xaml. vb dosyasını açın.

4. <xref:System.Windows.UIElement.DragOver> Olay işleyicisi için aşağıdaki kodu ekleyin.

     [!code-csharp[DragDropWalkthrough#PanelDragOver](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml.cs#paneldragover)]
     [!code-vb[DragDropWalkthrough#PanelDragOver](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/MainWindow.xaml.vb#paneldragover)]

     Bu <xref:System.Windows.UIElement.DragOver> olay işleyicisi aşağıdaki görevleri gerçekleştirir:

    - Sürüklenen verilerin, <xref:System.Windows.DataObject> Circle Kullanıcı denetimiyle paketlenmiş ve <xref:System.Windows.DragDrop.DoDragDrop%2A>çağrısına geçilen "nesne" verilerini içerip içermediğini denetler.

    - "Nesne" verileri mevcutsa, **CTRL** tuşuna basıldığını denetler.

    - **CTRL** tuşuna basıldığında <xref:System.Windows.DragEventArgs.Effects%2A> özelliğini olarak <xref:System.Windows.DragDropEffects.Copy>ayarlar. Aksi takdirde, <xref:System.Windows.DragEventArgs.Effects%2A> özelliğini olarak <xref:System.Windows.DragDropEffects.Move>ayarlayın.

5. <xref:System.Windows.UIElement.Drop> Olay işleyicisi için aşağıdaki kodu ekleyin.

     [!code-csharp[DragDropWalkthrough#PanelDrop](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml.cs#paneldrop)]
     [!code-vb[DragDropWalkthrough#PanelDrop](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/MainWindow.xaml.vb#paneldrop)]

     Bu <xref:System.Windows.UIElement.Drop> olay işleyicisi aşağıdaki görevleri gerçekleştirir:

    - <xref:System.Windows.UIElement.Drop> Etkinliğin zaten işlenmiş olup olmadığını denetler. Örneğin, bir daire <xref:System.Windows.UIElement.Drop> olayı işleyen başka bir daire üzerinde bırakıldığında, daireyi içeren panelin da işlenmesi için bu işleci istemezsiniz.

    - Olay işlenmezse, CTRL tuşuna basıldığını denetler.  <xref:System.Windows.UIElement.Drop>

    - <xref:System.Windows.UIElement.Drop> Oluştuğunda **CTRL** tuşuna basıldığında, daire denetiminin bir kopyasını oluşturur ve <xref:System.Windows.Controls.Panel.Children%2A> koleksiyonuna <xref:System.Windows.Controls.StackPanel>ekler.

    - **CTRL** tuşuna basılsa, daireyi <xref:System.Windows.Controls.Panel.Children%2A> <xref:System.Windows.Controls.Panel.Children%2A> üst bölmesinin koleksiyonundan, üzerinde bırakılan panelin koleksiyonuna taşımış olur.

    - Yöntemi, bir taşıma veya kopyalama işleminin gerçekleştirilip gerçekleştirilmediğini <xref:System.Windows.DragEventArgs.Effects%2A> bildirmek için <xref:System.Windows.DragDrop.DoDragDrop%2A> özelliği ayarlar.

6. Uygulamayı derlemek ve çalıştırmak için **F5** tuşuna basın.

7. Öğesinden metni `green`seçin. <xref:System.Windows.Controls.TextBox>

8. Metni bir daire denetiminin üzerine sürükleyin ve bırakın.

9. Sol panelden bir daire denetimini sağ panele sürükleyin ve bırakın. Daire, sol bölmenin <xref:System.Windows.Controls.Panel.Children%2A> koleksiyonundan kaldırılır ve sağ bölmenin alt öğe koleksiyonuna eklenir.

10. Bir daire denetimini, içindeki panelden diğer panele sürükleyin ve **CTRL** tuşuna basarak bırakın. Daire kopyalanır ve kopya, alan paneli <xref:System.Windows.Controls.Panel.Children%2A> koleksiyonuna eklenir.

     ![CTRL tuşuna basıldığında bir daireyi sürükleme](./media/dragdrop-paneldrop.png "DragDrop_PanelDrop")

## <a name="see-also"></a>Ayrıca bkz.

- [Sürükleme ve Bırakmaya Genel Bakış](drag-and-drop-overview.md)
