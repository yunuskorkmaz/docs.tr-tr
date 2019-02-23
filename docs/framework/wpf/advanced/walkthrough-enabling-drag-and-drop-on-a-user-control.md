---
title: 'İzlenecek yol: Sürükleme ve bırakmayı kullanıcı denetiminde etkinleştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- walkthrough [WPF], drag-and-drop
- drag-and-drop [WPF], walkthrough
ms.assetid: cc844419-1a77-4906-95d9-060d79107fc7
ms.openlocfilehash: a2aa1d09b922809f42fe14bd674c2a87b9e5a3f8
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/23/2019
ms.locfileid: "56747801"
---
# <a name="walkthrough-enabling-drag-and-drop-on-a-user-control"></a>İzlenecek yol: Sürükleme ve bırakmayı kullanıcı denetiminde etkinleştirme

Bu izlenecek yol, sürükle ve bırak veri aktarımı katılabilen özel bir kullanıcı denetimi oluşturmak gösterilmiştir [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].

Bu kılavuzda, özel bir WPF oluşturacağınız <xref:System.Windows.Controls.UserControl> temsil eden bir daire şeklinde. Sürükle ve bırak aracılığıyla veri aktarımı etkinleştirmeyi denetimi işlevselliğini uygular. Örneğin, başka bir daire denetimden sürüklerseniz, dolgu rengi veri daire kaynaktan hedefe kopyalanır. İçin bir daire denetiminden sürüklerseniz bir <xref:System.Windows.Controls.TextBox>, dolgu rengi dize gösterimini kopyalanır <xref:System.Windows.Controls.TextBox>. Ayrıca iki panel denetimleri içeren küçük bir uygulama oluşturacak ve bir <xref:System.Windows.Controls.TextBox> sürükle ve bırak işlevselliğini test etmek için. Paneller, taşıyabilir veya daireler bir panelin alt öğeleri koleksiyondan kopyalayabilirsiniz sağlayacak bırakılan daire veriyi işlemek sağlayan bir kod yazacaksınız.

Bu izlenecek yol aşağıdaki görevleri gösterir:

-   Özel bir kullanıcı denetimi oluşturun.

-   Bir sürükleme kaynağı olması kullanıcı denetimi etkinleştirin.

-   Bir bırakma hedefi olarak kullanıcı denetimini etkinleştirin.

-   Kullanıcı denetimi bırakılan veri almak bir panel etkinleştirin.

## <a name="prerequisites"></a>Önkoşullar

Bu izlenecek yolu tamamlamak için Visual Studio ihtiyacınız vardır.

## <a name="create-the-application-project"></a>Uygulama projesini oluşturun
 Bu bölümde, bir ana sayfa ile iki panel içerir uygulama altyapısı oluşturacak ve bir <xref:System.Windows.Controls.TextBox>.

1.  Visual Basic veya Visual C# adlı yeni bir WPF uygulaması projesi oluşturma `DragDropExample`. Daha fazla bilgi için [izlenecek yol: İlk WPF Masaüstü Uygulamam](../getting-started/walkthrough-my-first-wpf-desktop-application.md).

2.  Open MainWindow.xaml.

3.  Açılış ve kapanış arasında aşağıdaki işaretlemeyi ekleyin <xref:System.Windows.Controls.Grid> etiketler.

     Bu işaretleme, kullanıcı arabirimi test uygulaması oluşturur.

     [!code-xaml[DragDropWalkthrough#PanelsStep1XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#panelsstep1xaml)]

## <a name="add-a-new-user-control-to-the-project"></a>Projeye yeni bir kullanıcı denetimi Ekle
 Bu bölümde, projeye yeni bir kullanıcı denetimi ekleyeceksiniz.

1.  Proje menüsünde **kullanıcı denetimi Ekle**.

2.  İçinde **Yeni Öğe Ekle** iletişim kutusunda, ada değiştirin `Circle.xaml`, tıklatıp **Ekle**.

     Circle.XAML ve kendi arka plan kod projesine eklenir.

3.  Circle.xaml açın.

     Bu dosya kullanıcı denetiminin kullanıcı arabirimi öğeleri içerir.

4.  Kök aşağıdaki işaretlemeyi ekleyin <xref:System.Windows.Controls.Grid> mavi bir daire olarak kullanıcı arabirimini sahip basit bir kullanıcı denetimi oluşturmak için.

     [!code-xaml[DragDropWalkthrough#EllipseXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml#ellipsexaml)]

5.  Circle.xaml.cs veya Circle.xaml.vb açın.

6.  C# ' ta bir kopya Oluşturucu oluşturmak için varsayılan oluşturucu sonra aşağıdaki kodu ekleyin. Visual Basic'te, bir kopya oluşturucu ve bir varsayılan oluşturucu oluşturmak için aşağıdaki kodu ekleyin.

     Kopyalanacak kullanıcı denetimi izin vermek üzere arka plan kod dosyasında bir kopya Oluşturucu yöntemi ekleyin. Basitleştirilmiş daire kullanıcı denetiminde yalnızca dolgu ve boyutunu kopyalayacağınız kullanıcı denetimi.

     [!code-csharp[DragDropWalkthrough#CopyCtor](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#copyctor)]
     [!code-vb[DragDropWalkthrough#CopyCtor](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#copyctor)]

## <a name="add-the-user-control-to-the-main-window"></a>Kullanıcı denetiminin ana penceresine ekleme

1.  Open MainWindow.xaml.

2.  Aşağıdaki XAML açılış ekleme <xref:System.Windows.Window> bir XML ad alanı başvurusu geçerli uygulamaya etiket.

    ```
    xmlns:local="clr-namespace:DragDropExample"
    ```

3.  İlk <xref:System.Windows.Controls.StackPanel>, ilk panelindeki daire kullanıcı denetimi iki örneğini oluşturmak için aşağıdaki XAML ekleyin.

     [!code-xaml[DragDropWalkthrough#CirclesXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#circlesxaml)]

     Tam XAML paneli aşağıdaki gibi görünür.

     [!code-xaml[DragDropWalkthrough#PanelsStep2XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#panelsstep2xaml)]

## <a name="implement-drag-source-events-in-the-user-control"></a>Kullanıcı denetiminde sürükleme kaynağı olayları uygulama
 Bu bölümde, geçersiz kılar <xref:System.Windows.UIElement.OnMouseMove%2A> yöntemi ve sürükle ve bırak işlemi Başlat.

 Bir sürükleme başladıysanız (fare taşınır ve bir fare düğmesi basılı), verileri içine aktarılacak paket oluşturur bir <xref:System.Windows.DataObject>. Bu durumda, daire denetim, üç veri öğeleri paket oluşturur; Dolgu rengini, yükseklik çift temsili ve kendisini bir kopyasını bir dize açıklaması.

### <a name="to-initiate-a-drag-and-drop-operation"></a>Bir Sürükle ve bırak işlemi başlatmak için

1.  Circle.xaml.cs veya Circle.xaml.vb açın.

2.  Aşağıdaki <xref:System.Windows.UIElement.OnMouseMove%2A> sınıf için işleme sağlamak için geçersiz kılma <xref:System.Windows.UIElement.MouseMove> olay.

     [!code-csharp[DragDropWalkthrough#OnMouseMove](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#onmousemove)]
     [!code-vb[DragDropWalkthrough#OnMouseMove](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#onmousemove)]

     Bu <xref:System.Windows.UIElement.OnMouseMove%2A> geçersiz kılma aşağıdaki görevleri gerçekleştirir:

    -   Fareyi hareket ederken, farenin sol düğmesine basıldığında olup olmadığını denetler.

    -   Daire verileri paketleri bir <xref:System.Windows.DataObject>. Bu durumda, daire denetim, üç veri öğeleri paketleri; Dolgu rengini, yükseklik çift temsili ve kendisini bir kopyasını bir dize açıklaması.

    -   Statik çağırır <xref:System.Windows.DragDrop.DoDragDrop%2A?displayProperty=nameWithType> sürükle ve bırak işlemi başlatmak için yöntem. Şu üç parametreyi için geçirdiğiniz <xref:System.Windows.DragDrop.DoDragDrop%2A> yöntemi:

        -   `dragSource` – Bu denetimi bir başvuru.

        -   `data` – <xref:System.Windows.DataObject> Önceki kod içinde oluşturulur.

        -   `allowedEffects` – Olan izin verilen sürükle ve bırak işlemleri <xref:System.Windows.DragDropEffects.Copy> veya <xref:System.Windows.DragDropEffects.Move>.

3.  Tuşuna **F5** oluşturun ve uygulamayı çalıştırın.

4.  Daire denetimlerden birini tıklatın ve başka bir daire, panellerin üzerine sürükleyin ve <xref:System.Windows.Controls.TextBox>. Üzerine sürüklerken <xref:System.Windows.Controls.TextBox>, taşıma belirtecek şekilde imleç değişir.

5.  Bir dairenin üzerine sürüklerken <xref:System.Windows.Controls.TextBox>, basın **Ctrl** anahtarı. Nasıl bir kopyasını belirtmek için imleç değiştiğine dikkat edin.

6.  Bir dairenin üzerine sürükleyip <xref:System.Windows.Controls.TextBox>. Dairenin dolgu rengi dize gösterimini eklenir <xref:System.Windows.Controls.TextBox>.

     ![Dize gösterimini dairenin dolgu rengi](../../../../docs/framework/wpf/advanced/media/dragdrop-colorstring.png "DragDrop_ColorString")

Varsayılan olarak, imleç bir Sürükle ve bırak işlemi sırasında veri bırakarak hangi etkisi olmayacak göstermek için değiştirir. Kullanıcıya verilen işleyerek geri bildirim özelleştirebilirsiniz <xref:System.Windows.UIElement.GiveFeedback> olay ve farklı bir imleç ayarlama.

## <a name="give-feedback-to-the-user"></a>Kullanıcıya geri bildirimde bulunun

1.  Circle.xaml.cs veya Circle.xaml.vb açın.

2.  Aşağıdaki <xref:System.Windows.UIElement.OnGiveFeedback%2A> sınıf için işleme sağlamak için geçersiz kılma <xref:System.Windows.UIElement.GiveFeedback> olay.

     [!code-csharp[DragDropWalkthrough#OnGiveFeedback](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ongivefeedback)]
     [!code-vb[DragDropWalkthrough#OnGiveFeedback](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ongivefeedback)]

     Bu <xref:System.Windows.UIElement.OnGiveFeedback%2A> geçersiz kılma aşağıdaki görevleri gerçekleştirir:

    -   Denetler <xref:System.Windows.GiveFeedbackEventArgs.Effects%2A> bırakma hedef ayarlanan değerlerle <xref:System.Windows.UIElement.DragOver> olay işleyicisi.

    -   Temel özel bir imleç ayarlar <xref:System.Windows.GiveFeedbackEventArgs.Effects%2A> değeri. İmleç, verileri bırakmayı hangi etkisi hakkında kullanıcıya görsel geribildirim vermek için tasarlanmıştır.

3.  Tuşuna **F5** oluşturun ve uygulamayı çalıştırın.

4.  Bir dairenin denetimleri başka bir daire, panellerin üzerine sürükleyin ve <xref:System.Windows.Controls.TextBox>. İmleçler artık, belirttiğiniz özel işaretçiler olduğunu fark <xref:System.Windows.UIElement.OnGiveFeedback%2A> geçersiz kılar.

     ![Sürükle ve bırak ile özel işaretçiler](../../../../docs/framework/wpf/advanced/media/dragdrop-customcursor.png "DragDrop_CustomCursor")

5.  Metni seçin `green` gelen <xref:System.Windows.Controls.TextBox>.

6.  Sürükleme `green` bir daire denetime metin. Sürükle ve bırak işlemi etkilerini belirtmek için gösterilen varsayılan imleçler dikkat edin. Geri bildirim imleci her zaman sürükleme kaynağı tarafından ayarlanır.

## <a name="implement-drop-target-events-in-the-user-control"></a>Bırakma hedefi olayları kullanıcı denetimi uygulayın
 Bu bölümde, kullanıcı denetiminin bir bırakma hedefi, kullanıcı etkinleştirme yöntemleri bir bırakma hedefi olarak denetlemek ve üzerinde bırakılan veri işlem geçersiz kılma olduğunu belirtin.

### <a name="to-enable-the-user-control-to-be-a-drop-target"></a>Bir bırakma hedefi olarak kullanıcı denetimini etkinleştirme

1.  Circle.xaml açın.

2.  Açılışında <xref:System.Windows.Controls.UserControl> etiketinde, ekleyin <xref:System.Windows.UIElement.AllowDrop%2A> özelliği ve değerini `true`.

     [!code-xaml[DragDropWalkthrough#UCTagXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml#uctagxaml)]

<xref:System.Windows.UIElement.OnDrop%2A> Yöntemi çağrılır <xref:System.Windows.UIElement.AllowDrop%2A> özelliği `true` ve daire kullanıcı denetiminde sürükleme kaynağından bırakıldı. Bu yöntemde, bırakılmış verileri işleme ve veri dairenin uygulayın.

### <a name="to-process-the-dropped-data"></a>Bırakılan veri işlemek için

1.  Circle.xaml.cs veya Circle.xaml.vb açın.

2.  Aşağıdaki <xref:System.Windows.UIElement.OnDrop%2A> sınıf için işleme sağlamak için geçersiz kılma <xref:System.Windows.UIElement.Drop> olay.

     [!code-csharp[DragDropWalkthrough#OnDrop](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondrop)]
     [!code-vb[DragDropWalkthrough#OnDrop](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondrop)]

     Bu <xref:System.Windows.UIElement.OnDrop%2A> geçersiz kılma aşağıdaki görevleri gerçekleştirir:

    -   Kullanan <xref:System.Windows.DataObject.GetDataPresent%2A> sürüklenen verileri bir dize nesnesi içerip içermediğini denetlemek için yöntem.

    -   Kullanan <xref:System.Windows.DataObject.GetData%2A> varsa, dize verilerini ayıklamak için yöntemi.

    -   Kullanan bir <xref:System.Windows.Media.BrushConverter> dizeye dönüştürülecek denemek için bir <xref:System.Windows.Media.Brush>.

    -   Dönüştürme başarılı ise fırçaya uygulanır <xref:System.Windows.Shapes.Shape.Fill%2A> , <xref:System.Windows.Shapes.Ellipse> daire denetimin kullanıcı Arabirimi sağlar.

    -   İşaretleri <xref:System.Windows.UIElement.Drop> işlenmiş olarak olay. Bırakma olayını daire kullanıcı denetimi, işlenen Bu etkinliğin diğer öğeleri öğrenmek için işlenmiş olarak işaretlemeniz gerekir.

3.  Tuşuna **F5** oluşturun ve uygulamayı çalıştırın.

4.  Metni seçin `green` içinde <xref:System.Windows.Controls.TextBox>.

5.  Bir daire denetime metin sürükleyin ve bırakın. Mavi yeşil daire değişiklikleri.

     ![Bir dize dönüştürmek için bir fırça](../../../../docs/framework/wpf/advanced/media/dragdrop-dropgreentext.png "DragDrop_DropGreenText")

6.  Bir metin yazın `green` içinde <xref:System.Windows.Controls.TextBox>.

7.  Metni seçin `gre` içinde <xref:System.Windows.Controls.TextBox>.

8.  Bir daire denetimine sürükleyin ve bırakın. Açılan izin verilir, ancak dairenin rengi, çünkü değiştirmez belirtmek için imleç değiştiğine dikkat edin `gre` geçerli bir renk değil.

9. Yeşil daire denetiminden sürükleyip mavi daire denetimi. Mavi yeşil daire değişiklikleri. Hangi imleç gösterilir bağlıdır dikkat edin <xref:System.Windows.Controls.TextBox> veya daire sürükleme kaynağı.

Ayarı <xref:System.Windows.UIElement.AllowDrop%2A> özelliğini `true` ve bırakılan verilerin işlenmesi tüm bir bırakma hedefi olarak bir öğeyi etkinleştirmek için gereklidir. Ancak, daha iyi bir kullanıcı deneyimi sağlamak için ayrıca işleyeceğini <xref:System.Windows.UIElement.DragEnter>, <xref:System.Windows.UIElement.DragLeave>, ve <xref:System.Windows.UIElement.DragOver> olayları. Bu olayları, denetimleri gerçekleştirir ve veri kesilmeden önce kullanıcıya ek geri bildirim sağlayın.

Veri daire kullanıcı denetime sürüklendiğinde denetimin sürüklenen veri işleme olup olmadığını sürükleme kaynağı bildirmelisiniz. Denetim verileri işlemek nasıl emin değilseniz açılan reddeder. Bunu yapmak için işleyecek <xref:System.Windows.UIElement.DragOver> olay ve kümesi <xref:System.Windows.DragEventArgs.Effects%2A> özelliği.

### <a name="to-verify-that-the-data-drop-is-allowed"></a>Veri bırakma izin verildiğini doğrulamak için

1.  Circle.xaml.cs veya Circle.xaml.vb açın.

2.  Aşağıdaki <xref:System.Windows.UIElement.OnDragOver%2A> sınıf için işleme sağlamak için geçersiz kılma <xref:System.Windows.UIElement.DragOver> olay.

     [!code-csharp[DragDropWalkthrough#OnDragOver](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragover)]
     [!code-vb[DragDropWalkthrough#OnDragOver](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragover)]

     Bu <xref:System.Windows.UIElement.OnDragOver%2A> geçersiz kılma aşağıdaki görevleri gerçekleştirir:

    -   Kümeleri <xref:System.Windows.DragEventArgs.Effects%2A> özelliğini <xref:System.Windows.DragDropEffects.None>.

    -   Gerçekleştirilir aynı denetimleri gerçekleştirir <xref:System.Windows.UIElement.OnDrop%2A> daire kullanıcı denetimi sürüklenen verileri işleyebildiğinden olup olmadığını belirlemek için yöntemi.

    -   Kullanıcı denetimi verileri işleyebildiğinden, ayarlar <xref:System.Windows.DragEventArgs.Effects%2A> özelliğini <xref:System.Windows.DragDropEffects.Copy> veya <xref:System.Windows.DragDropEffects.Move>.

3.  Tuşuna **F5** oluşturun ve uygulamayı çalıştırın.

4.  Metni seçin `gre` içinde <xref:System.Windows.Controls.TextBox>.

5.  Metin bir daire denetimi sürükleyin. İmleç açılan olduğundan izin verilmiyor belirtmek için hemen değiştiğine dikkat edin `gre` geçerli bir renk değil.

 Kullanıcı deneyimini daha fazla bırakma işlemi önizlemesini uygulayarak da geliştirebilirsiniz. Daire kullanıcı denetimi için geçersiz kılar <xref:System.Windows.UIElement.OnDragEnter%2A> ve <xref:System.Windows.UIElement.OnDragLeave%2A> yöntemleri. Ne zaman veri sürüklediğiniz geçerli arka plan denetimin üzerine <xref:System.Windows.Shapes.Shape.Fill%2A> bir yer tutucu değişkende kaydedilir. Dize ardından fırçaya dönüştürülür ve uygulanan <xref:System.Windows.Shapes.Ellipse> dairenin sağlayan kullanıcı Arabirimi. Veri daire dışında ' bırakılan olmadan, özgün sürüklediyseniz <xref:System.Windows.Shapes.Shape.Fill%2A> değeri dairenin yeniden uygulanır.

### <a name="to-preview-the-effects-of-the-drag-and-drop-operation"></a>Sürükle ve bırak işlemi etkilerini önizlemesini görüntülemek için

1.  Circle.xaml.cs veya Circle.xaml.vb açın.

2.  Özel bir daire sınıfında bildirmek <xref:System.Windows.Media.Brush> adlı değişken `_previousFill` ve kendisine başlatma `null`.

     [!code-csharp[DragDropWalkthrough#Brush](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#brush)]
     [!code-vb[DragDropWalkthrough#Brush](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#brush)]

3.  Aşağıdaki <xref:System.Windows.UIElement.OnDragEnter%2A> sınıf için işleme sağlamak için geçersiz kılma <xref:System.Windows.UIElement.DragEnter> olay.

     [!code-csharp[DragDropWalkthrough#OnDragEnter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragenter)]
     [!code-vb[DragDropWalkthrough#OnDragEnter](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragenter)]

     Bu <xref:System.Windows.UIElement.OnDragEnter%2A> geçersiz kılma aşağıdaki görevleri gerçekleştirir:

    -   Kaydeder <xref:System.Windows.Shapes.Shape.Fill%2A> özelliği <xref:System.Windows.Shapes.Ellipse> içinde `_previousFill` değişkeni.

    -   Gerçekleştirilir aynı denetimleri gerçekleştirir <xref:System.Windows.UIElement.OnDrop%2A> verileri için dönüştürülüp dönüştürülemeyeceğini belirlemek için yöntemi bir <xref:System.Windows.Media.Brush>.

    -   Geçerli bir veri dönüştürülürse <xref:System.Windows.Media.Brush>, uygular <xref:System.Windows.Shapes.Shape.Fill%2A> , <xref:System.Windows.Shapes.Ellipse>.

4.  Aşağıdaki <xref:System.Windows.UIElement.OnDragLeave%2A> sınıf için işleme sağlamak için geçersiz kılma <xref:System.Windows.UIElement.DragLeave> olay.

     [!code-csharp[DragDropWalkthrough#OnDragLeave](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragleave)]
     [!code-vb[DragDropWalkthrough#OnDragLeave](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragleave)]

     Bu <xref:System.Windows.UIElement.OnDragLeave%2A> geçersiz kılma aşağıdaki görevleri gerçekleştirir:

    -   Geçerli <xref:System.Windows.Media.Brush> kaydedilmiş `_previousFill` değişkenini <xref:System.Windows.Shapes.Shape.Fill%2A> , <xref:System.Windows.Shapes.Ellipse> daire kullanıcı denetiminin kullanıcı Arabirimi sağlar.

5.  Tuşuna **F5** oluşturun ve uygulamayı çalıştırın.

6.  Metni seçin `green` içinde <xref:System.Windows.Controls.TextBox>.

7.  Metin, sürükleyip bırakarak olmadan bir daire denetimin üzerine sürükleyin. Mavi yeşil daire değişiklikleri.

     ![Bir sürükleme etkilerini önizleme&#45;ve&#45;bırakma işlemi](../../../../docs/framework/wpf/advanced/media/dragdrop-previeweffects.png "DragDrop_PreviewEffects")

8.  Metin daire denetim uzağa sürükleyin. Mavi yeşil arka daireye dönüşür.

## <a name="enable-a-panel-to-receive-dropped-data"></a>Bırakılan veri almak bir Panel etkinleştir

Bu bölümde, sürüklenen daire veriler için bırakma hedefleri olarak davranmak üzere daire kullanıcı denetimleri barındıran paneller etkinleştirin. Bir daire bir panelden diğerine taşımak için ya da basılı tutarak bir daire denetimin bir kopyasını yapmak sağlayan kodu gerçekleştireceksiniz **Ctrl** tuşunu sürükleyip bırakarak bir daire.

1.  Open MainWindow.xaml.

2.  Her birinde aşağıdaki XAML gösterildiği <xref:System.Windows.Controls.StackPanel> denetimler eklemek için işleyiciler <xref:System.Windows.UIElement.DragOver> ve <xref:System.Windows.UIElement.Drop> olayları. Adı <xref:System.Windows.UIElement.DragOver> olay işleyicisi `panel_DragOver`ve ad <xref:System.Windows.UIElement.Drop> olay işleyicisi `panel_Drop`.

     [!code-xaml[DragDropWalkthrough#PanelsXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml#panelsxaml)]

3.  MainWindows.xaml.cs veya MainWindow.xaml.vb açın.

4.  İçin aşağıdaki kodu ekleyin <xref:System.Windows.UIElement.DragOver> olay işleyicisi.

     [!code-csharp[DragDropWalkthrough#PanelDragOver](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml.cs#paneldragover)]
     [!code-vb[DragDropWalkthrough#PanelDragOver](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/MainWindow.xaml.vb#paneldragover)]

     Bu <xref:System.Windows.UIElement.DragOver> olay işleyicisi aşağıdaki görevleri gerçekleştirir:

    -   Sürüklenen veri içinde paketlendi "Nesne" veri içerip içermediğini denetler <xref:System.Windows.DataObject> daire kullanıcı denetimi tarafından ve çağrısına geçirilen <xref:System.Windows.DragDrop.DoDragDrop%2A>.

    -   "Nesne" veri yoksa, denetimleri olup **Ctrl** tuşuna basıldığında.

    -   Varsa **Ctrl** tuşuna basıldığında, ayarlar <xref:System.Windows.DragEventArgs.Effects%2A> özelliğini <xref:System.Windows.DragDropEffects.Copy>. Aksi takdirde, ayarlama <xref:System.Windows.DragEventArgs.Effects%2A> özelliğini <xref:System.Windows.DragDropEffects.Move>.

5.  İçin aşağıdaki kodu ekleyin <xref:System.Windows.UIElement.Drop> olay işleyicisi.

     [!code-csharp[DragDropWalkthrough#PanelDrop](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml.cs#paneldrop)]
     [!code-vb[DragDropWalkthrough#PanelDrop](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/MainWindow.xaml.vb#paneldrop)]

     Bu <xref:System.Windows.UIElement.Drop> olay işleyicisi aşağıdaki görevleri gerçekleştirir:

    -   Denetler olmadığını <xref:System.Windows.UIElement.Drop> olay zaten işlenir. Başka bir daire kesilirse, örneğin, yuvarlak tanıtıcıları <xref:System.Windows.UIElement.Drop> olay istemediğiniz ayrıca işlemek için daire içeren paneli.

    -   Varsa <xref:System.Windows.UIElement.Drop> olay işlenmez, denetimleri olup **Ctrl** tuşuna basıldığında.

    -   Varsa **Ctrl** anahtar bilgisi basıldığında <xref:System.Windows.UIElement.Drop> olduğunda, dairenin kopyasını hale denetlemek ve ekleyin <xref:System.Windows.Controls.Panel.Children%2A> koleksiyonunu <xref:System.Windows.Controls.StackPanel>.

    -   Varsa **Ctrl** değil tuşuna basıldığında, gelen daire taşır <xref:System.Windows.Controls.Panel.Children%2A> kendi üst paneline koleksiyonunu <xref:System.Windows.Controls.Panel.Children%2A> bırakılmış paneli koleksiyonu.

    -   Kümeleri <xref:System.Windows.DragEventArgs.Effects%2A> bildirmek için özellik <xref:System.Windows.DragDrop.DoDragDrop%2A> yöntemi olup olmadığını taşıma veya kopyalama işlemi gerçekleştirildi.

6.  Tuşuna **F5** oluşturun ve uygulamayı çalıştırın.

7.  Metni seçin `green` gelen <xref:System.Windows.Controls.TextBox>.

8.  Metin bir daire denetimin üzerine sürükleyin ve bırakın.

9. Bir daire denetimi sol panelden sağ bölmenin sürükleyip bırakın. Daire kaldırılır <xref:System.Windows.Controls.Panel.Children%2A> sol panelde koleksiyonunu ve sağ alt koleksiyona eklenir.

10. Bulunduğu diğer panele panelindeki daire denetimi sürükleyin ve tuşlarına basarak ederken bırakma **Ctrl** anahtarı. Daire kopyalanır ve kopyayı eklendiğinden <xref:System.Windows.Controls.Panel.Children%2A> alma panelini koleksiyonu.

     ![Bir daire CTRL tuşunu basılı tutarak sürükleyerek](../../../../docs/framework/wpf/advanced/media/dragdrop-paneldrop.png "DragDrop_PanelDrop")

## <a name="see-also"></a>Ayrıca bkz.

- [Sürükleme ve Bırakmaya Genel Bakış](../../../../docs/framework/wpf/advanced/drag-and-drop-overview.md)