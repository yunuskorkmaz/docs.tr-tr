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
ms.openlocfilehash: e4dba856b973f1210f2d088de3ed8ae5df2c6988
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33549756"
---
# <a name="walkthrough-enabling-drag-and-drop-on-a-user-control"></a>İzlenecek yol: Kullanıcı Denetiminde Sürükleme ve Bırakmayı Etkinleştirme
Bu anlatımda sürükle ve bırak veri aktarımı katılabilmesi için özel bir kullanıcı denetimi oluşturmak nasıl gösterilir [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  
  
 Bu kılavuzda, özel bir WPF oluşturacak <xref:System.Windows.Controls.UserControl> temsil eden bir daire şekli. Veri Aktarımı Sürükle ve bırak aracılığıyla etkinleştirmek için denetimindeki işlevselliği gerçekleştireceksiniz. Örneğin, başka bir daire denetimden sürüklediğinizde, dolgu rengi veri daire kaynaktan hedefe kopyalanır. Bir daire kontrolü sürüklediğinizde bir <xref:System.Windows.Controls.TextBox>, dolgu rengi dize gösterimini kopyalanır <xref:System.Windows.Controls.TextBox>. Ayrıca iki panel denetimleri içeren küçük bir uygulama oluşturulur ve bir <xref:System.Windows.Controls.TextBox> sürükle ve bırak işlevselliğini test etmek için. Taşıma veya daireler bir panelinin alt koleksiyondan kopyalama sağlayacak bırakılan daire verileri işlemek paneller etkinleştirir kod yazacaksınız.  
  
 Bu izlenecek yol aşağıdaki görevleri gösterir:  
  
-   Özel bir kullanıcı denetimi oluşturun.  
  
-   Sürükleme kaynağı olması kullanıcı denetimini etkinleştirin.  
  
-   Bırakma hedefi kullanıcı denetimini etkinleştirin.  
  
-   Kullanıcı denetiminden bırakılan veri almak bir panel etkinleştirin.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:  
  
-   Visual Studio 2010  
  
## <a name="creating-the-application-project"></a>Uygulama projesi oluşturma  
 Bu bölümde, bir ana sayfa ile iki bölme içerir uygulama altyapısı oluşturacak ve bir <xref:System.Windows.Controls.TextBox>.  
  
### <a name="to-create-the-project"></a>Proje oluşturmak için  
  
1.  Visual Basic veya Visual C# adlı yeni bir WPF uygulaması projesi oluşturduğunuzda `DragDropExample`. Daha fazla bilgi için bkz: [nasıl yapılır: yeni bir WPF uygulaması projesi oluşturduğunuzda](http://msdn.microsoft.com/library/1f6aea7a-33e1-4d3f-8555-1daa42e95d82).  
  
2.  MainWindow.xaml açın.  
  
3.  Açma ve kapatma arasında aşağıdaki biçimlendirmeleri eklemek <xref:System.Windows.Controls.Grid> etiketler.  
  
     Bu biçimlendirme test uygulaması için kullanıcı arabirimi oluşturur.  
  
     [!code-xaml[DragDropWalkthrough#PanelsStep1XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#panelsstep1xaml)]  
  
## <a name="adding-a-new-user-control-to-the-project"></a>Projeye yeni bir kullanıcı denetimi ekleme  
 Bu bölümde, projeye yeni bir kullanıcı denetimi ekleyeceksiniz.  
  
### <a name="to-add-a-new-user-control"></a>Yeni bir kullanıcı denetimi eklemek için  
  
1.  Proje menüsünde seçin **kullanıcı denetimi Ekle**.  
  
2.  Yeni Öğe Ekle iletişim kutusunda adına değiştirin `Circle.xaml`, tıklatıp **Ekle**.  
  
     Circle.XAML ve kendi arka plan kodu projeye eklendi.  
  
3.  Circle.xaml açın.  
  
     Bu dosya kullanıcı denetiminin kullanıcı arabirimi öğeleri içerir.  
  
4.  Aşağıdaki biçimlendirmede kök dizinine ekleme <xref:System.Windows.Controls.Grid> mavi bir daire olarak kullanıcı Arabiriminde sahip basit kullanıcı denetimi oluşturmak için.  
  
     [!code-xaml[DragDropWalkthrough#EllipseXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml#ellipsexaml)]  
  
5.  Circle.xaml.cs veya Circle.xaml.vb açın.  
  
6.  C# ' ta kopya Oluşturucu oluşturmak için varsayılan oluşturucu sonra aşağıdaki kodu ekleyin. Visual Basic'te, varsayılan bir oluşturucu ve kopya Oluşturucu oluşturmak için aşağıdaki kodu ekleyin.  
  
     Kopyalanacak kullanıcı denetimi izin vermek üzere bir kopya Oluşturucu yöntemi arka plan kod dosyasına ekleyin. Basitleştirilmiş daire kullanıcı denetiminde, yalnızca dolgu ve boyutunu kopyalayacak kullanıcı denetiminin.  
  
     [!code-csharp[DragDropWalkthrough#CopyCtor](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#copyctor)]
     [!code-vb[DragDropWalkthrough#CopyCtor](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#copyctor)]  
  
### <a name="to-add-the-user-control-to-the-main-window"></a>Kullanıcı Denetimi ana pencereyi eklemek için  
  
1.  MainWindow.xaml açın.  
  
2.  Aşağıdaki XAML eklemek için açılış <xref:System.Windows.Window> bir XML ad alanı başvurusu geçerli uygulama oluşturmak için etiketi.  
  
    ```  
    xmlns:local="clr-namespace:DragDropExample"  
    ```  
  
3.  İlk <xref:System.Windows.Controls.StackPanel>, ilk panelinde daire kullanıcı denetimi iki örneğini oluşturmak için aşağıdaki XAML'i ekleyin.  
  
     [!code-xaml[DragDropWalkthrough#CirclesXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#circlesxaml)]  
  
     Pano için tam XAML aşağıdaki gibi görünür.  
  
     [!code-xaml[DragDropWalkthrough#PanelsStep2XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#panelsstep2xaml)]  
  
## <a name="implementing-drag-source-events-in-the-user-control"></a>Kullanıcı denetimi sürükleme kaynağı olayları uygulama  
 Bu bölümde, geçersiz kılar <xref:System.Windows.UIElement.OnMouseMove%2A> yöntemi ve başlatma sürükle ve bırak işlemi.  
  
 Bir Sürükle başladıysanız (fare düğmesini basılı ve fare taşınır), verilerin içine aktarılması için paket oluşturur bir <xref:System.Windows.DataObject>. Bu durumda, daire denetim üç veri öğeleri paket oluşturur; Dolgu rengini, gerekse boyu çift gösterimini ve kendisi bir kopyasını bir dize gösterimi.  
  
### <a name="to-initiate-a-drag-and-drop-operation"></a>Sürükle ve bırak işlemi başlatmak için  
  
1.  Circle.xaml.cs veya Circle.xaml.vb açın.  
  
2.  Aşağıdakileri ekleyin <xref:System.Windows.UIElement.OnMouseMove%2A> sınıfı için işleme sağlamak üzere geçersiz kılma <xref:System.Windows.UIElement.MouseMove> olay.  
  
     [!code-csharp[DragDropWalkthrough#OnMouseMove](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#onmousemove)]
     [!code-vb[DragDropWalkthrough#OnMouseMove](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#onmousemove)]  
  
     Bu <xref:System.Windows.UIElement.OnMouseMove%2A> geçersiz kılma aşağıdaki görevleri gerçekleştirir:  
  
    -   Fareyi hareket ederken sol fare düğmesini basılı olup olmadığını denetler.  
  
    -   Daire verileri paketleri bir <xref:System.Windows.DataObject>. Bu durumda, üç veri öğeleri daire denetim paketleri; Dolgu rengini, gerekse boyu çift gösterimini ve kendisi bir kopyasını bir dize gösterimi.  
  
    -   Statik çağırır <xref:System.Windows.DragDrop.DoDragDrop%2A?displayProperty=nameWithType> sürükle ve bırak işlemi başlatmak için yöntem. Aşağıdaki üç parametre geçirdiğiniz <xref:System.Windows.DragDrop.DoDragDrop%2A> yöntemi:  
  
        -   `dragSource` – Bu denetimi bir başvuru.  
  
        -   `data` – <xref:System.Windows.DataObject> Önceki kodda oluşturuldu.  
  
        -   `allowedEffects` – Olan izin verilen sürükle ve bırak işlemleri <xref:System.Windows.DragDropEffects.Copy> veya <xref:System.Windows.DragDropEffects.Move>.  
  
3.  Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın.  
  
4.  Daire denetimleri birini tıklatın ve başka bir daire paneller sürükleyin ve <xref:System.Windows.Controls.TextBox>. Üzerinden sürüklendiğinde <xref:System.Windows.Controls.TextBox>, bir taşıma belirtmek için imleç değişir.  
  
5.  Üzerinden bir daire sürükleme sırasında <xref:System.Windows.Controls.TextBox>, CTRL tuşuna basın. Nasıl bir kopyasını belirtmek için imleci değiştiğine dikkat edin.  
  
6.  Sürükleme ve bırakma üzerine bir daire <xref:System.Windows.Controls.TextBox>. Dairenin dolgu rengi dize gösterimini eklenir <xref:System.Windows.Controls.TextBox>.  
  
     ![Dize olarak dairenin dolgu rengi gösterimi](../../../../docs/framework/wpf/advanced/media/dragdrop-colorstring.png "DragDrop_ColorString")  
  
 Varsayılan olarak, imleç veri bırakma hangi etkisi olmayacaktır belirtmek için bir Sürükle ve bırak işlemi sırasında değiştirir. İşleyerek kullanıcıya verilen görüşü özelleştirebilirsiniz <xref:System.Windows.UIElement.GiveFeedback> olay ve farklı bir imleç ayarlama.  
  
### <a name="to-give-feedback-to-the-user"></a>Kullanıcıya geribildirim vermek için  
  
1.  Circle.xaml.cs veya Circle.xaml.vb açın.  
  
2.  Aşağıdakileri ekleyin <xref:System.Windows.UIElement.OnGiveFeedback%2A> sınıfı için işleme sağlamak üzere geçersiz kılma <xref:System.Windows.UIElement.GiveFeedback> olay.  
  
     [!code-csharp[DragDropWalkthrough#OnGiveFeedback](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ongivefeedback)]
     [!code-vb[DragDropWalkthrough#OnGiveFeedback](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ongivefeedback)]  
  
     Bu <xref:System.Windows.UIElement.OnGiveFeedback%2A> geçersiz kılma aşağıdaki görevleri gerçekleştirir:  
  
    -   Denetler <xref:System.Windows.GiveFeedbackEventArgs.Effects%2A> açılan hedef ayarlanan değerlerle <xref:System.Windows.UIElement.DragOver> olay işleyicisi.  
  
    -   Dayalı özel bir imleç ayarlar <xref:System.Windows.GiveFeedbackEventArgs.Effects%2A> değeri. İmleç veri bırakma hangi etkisi hakkında kullanıcıya görsel geribildirim sağlamak üzere tasarlanmıştır.  
  
3.  Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın.  
  
4.  Daireye birini denetimleri diğer daireye paneller sürükleyin ve <xref:System.Windows.Controls.TextBox>. İmleçler şimdi belirttiğiniz özel imleçler olduğunu fark <xref:System.Windows.UIElement.OnGiveFeedback%2A> geçersiz kılar.  
  
     ![Sürükleme ve bırakma özel imleçlerle](../../../../docs/framework/wpf/advanced/media/dragdrop-customcursor.png "DragDrop_CustomCursor")  
  
5.  Metni seçin `green` gelen <xref:System.Windows.Controls.TextBox>.  
  
6.  Sürükleme `green` bir daire denetime metin. Sürükle ve bırak işlemi etkilerini göstermek için varsayılan imleçler gösterilen dikkat edin. Geri bildirim imleci her zaman Sürükle kaynağı tarafından ayarlanır.  
  
## <a name="implementing-drop-target-events-in-the-user-control"></a>Bırakma hedefi olayları, kullanıcı denetimi uygulama  
 Bu bölümde, kullanıcı denetimi kullanıcı sağlayan yöntemler bir bırakma hedefi olarak denetlemek ve üzerinde bırakılan veri işleme geçersiz kılma bir bırakma hedefi olduğunu belirteceksiniz.  
  
### <a name="to-enable-the-user-control-to-be-a-drop-target"></a>Bırakma hedefi kullanıcı denetimini etkinleştirmek için  
  
1.  Circle.xaml açın.  
  
2.  Açılışında <xref:System.Windows.Controls.UserControl> etiketi, add <xref:System.Windows.UIElement.AllowDrop%2A> özelliği ve ayarlamak `true`.  
  
     [!code-xaml[DragDropWalkthrough#UCTagXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml#uctagxaml)]  
  
 <xref:System.Windows.UIElement.OnDrop%2A> Yöntemi çağrılır <xref:System.Windows.UIElement.AllowDrop%2A> özelliği ayarlanmış `true` ve veriler sürükleme kaynağından daire kullanıcı denetiminde bırakıldı. Bu yöntemde bırakılmış verileri işlemek ve dairenin veri uygulayın.  
  
### <a name="to-process-the-dropped-data"></a>Bırakılan verileri işlemek için  
  
1.  Circle.xaml.cs veya Circle.xaml.vb açın.  
  
2.  Aşağıdakileri ekleyin <xref:System.Windows.UIElement.OnDrop%2A> sınıfı için işleme sağlamak üzere geçersiz kılma <xref:System.Windows.UIElement.Drop> olay.  
  
     [!code-csharp[DragDropWalkthrough#OnDrop](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondrop)]
     [!code-vb[DragDropWalkthrough#OnDrop](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondrop)]  
  
     Bu <xref:System.Windows.UIElement.OnDrop%2A> geçersiz kılma aşağıdaki görevleri gerçekleştirir:  
  
    -   Kullanan <xref:System.Windows.DataObject.GetDataPresent%2A> sürüklenen veri bir dize nesnesi içerip içermediğini denetlemek için yöntem.  
  
    -   Kullanan <xref:System.Windows.DataObject.GetData%2A> varsa, dize verilerini ayıklamak için yöntem.  
  
    -   Kullanan bir <xref:System.Windows.Media.BrushConverter> dizeye dönüştürmek denemek için bir <xref:System.Windows.Media.Brush>.  
  
    -   Dönüştürme başarılı olursa, fırça geçerlidir <xref:System.Windows.Shapes.Shape.Fill%2A> , <xref:System.Windows.Shapes.Ellipse> daire denetiminin kullanıcı Arabirimi sağlar.  
  
    -   İşaretleri <xref:System.Windows.UIElement.Drop> işlenmiş olarak olay. Bu olay alırsınız diğer öğeleri daire kullanıcı denetimi, işlenen bilmesi işlenmiş olarak açılan olay işaretlemeniz gerekir.  
  
3.  Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın.  
  
4.  Metni seçin `green` içinde <xref:System.Windows.Controls.TextBox>.  
  
5.  Metin bir daire denetimine sürükleyin ve bırakın. Mavi yeşil daire değişiklikler.  
  
     ![Bir dizeyi bir fırça dönüştürme](../../../../docs/framework/wpf/advanced/media/dragdrop-dropgreentext.png "DragDrop_DropGreenText")  
  
6.  Bir metin yazın `green` içinde <xref:System.Windows.Controls.TextBox>.  
  
7.  Metni seçin `gre` içinde <xref:System.Windows.Controls.TextBox>.  
  
8.  Bir daire denetimine sürükleyin ve bırakın. İmleç değişimleri açılır izin verilir, ancak daire rengi değiştirmez çünkü belirtmek için bildirim `gre` geçerli bir renk değil.  
  
9. Yeşil daire denetiminden sürükleyip mavi daire denetimi. Mavi yeşil daire değişiklikler. Hangi imleç gösterilir bağlıdır dikkat edin <xref:System.Windows.Controls.TextBox> veya daireyi sürükleyin kaynağıdır.  
  
 Ayarı <xref:System.Windows.UIElement.AllowDrop%2A> özelliğine `true` ve bırakılan veri işleme, bir bırakma hedefi olarak bir öğeyi etkinleştirmek için gerekli olan. Ancak, daha iyi bir kullanıcı deneyimi sağlamak için aynı zamanda işlemelidir <xref:System.Windows.UIElement.DragEnter>, <xref:System.Windows.UIElement.DragLeave>, ve <xref:System.Windows.UIElement.DragOver> olaylar. Bu olaylar, denetimleri gerçekleştirmek ve veri kesilmeden önce kullanıcıya ek geri bildirim sağlayın.  
  
 Veri üzerinde daire kullanıcı denetimini sürüklendiğinde denetimi sürüklenen veri işlem olup olmadığını sürükleme kaynağı haber vermelisiniz. Denetim verileri işlemek nasıl bilmiyorsa açılır reddetme. Bunu yapmak için işleyecek <xref:System.Windows.UIElement.DragOver> olay ve kümesi <xref:System.Windows.DragEventArgs.Effects%2A> özelliği.  
  
### <a name="to-verify-that-the-data-drop-is-allowed"></a>Veri bırakma izin verildiğini doğrulamak için  
  
1.  Circle.xaml.cs veya Circle.xaml.vb açın.  
  
2.  Aşağıdakileri ekleyin <xref:System.Windows.UIElement.OnDragOver%2A> sınıfı için işleme sağlamak üzere geçersiz kılma <xref:System.Windows.UIElement.DragOver> olay.  
  
     [!code-csharp[DragDropWalkthrough#OnDragOver](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragover)]
     [!code-vb[DragDropWalkthrough#OnDragOver](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragover)]  
  
     Bu <xref:System.Windows.UIElement.OnDragOver%2A> geçersiz kılma aşağıdaki görevleri gerçekleştirir:  
  
    -   Ayarlar <xref:System.Windows.DragEventArgs.Effects%2A> özelliğine <xref:System.Windows.DragDropEffects.None>.  
  
    -   İçinde gerçekleştirilen aynı denetimleri gerçekleştirir <xref:System.Windows.UIElement.OnDrop%2A> daire kullanıcı denetimi sürüklenen veri işleyebilir olup olmadığını belirlemek amacıyla yöntemi.  
  
    -   Kullanıcı denetiminin veri işleyebilmesi için ayarlar <xref:System.Windows.DragEventArgs.Effects%2A> özelliğine <xref:System.Windows.DragDropEffects.Copy> veya <xref:System.Windows.DragDropEffects.Move>.  
  
3.  Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın.  
  
4.  Metni seçin `gre` içinde <xref:System.Windows.Controls.TextBox>.  
  
5.  Metin bir daire denetimi sürükleyin. İmleç şimdi açılır olduğundan izin verilmiyor değişimleri belirtmek için bildirim `gre` geçerli bir renk değil.  
  
 Bırakma işlemi önizlemesini uygulayarak daha fazla kullanıcı deneyimini geliştirebilirsiniz. Daire kullanıcı denetimi için geçersiz kılar <xref:System.Windows.UIElement.OnDragEnter%2A> ve <xref:System.Windows.UIElement.OnDragLeave%2A> yöntemleri. Ne zaman veri sürüklenen geçerli arka plan denetim üzerinde <xref:System.Windows.Shapes.Shape.Fill%2A> bir yer tutucu değişkende kaydedilir. Dize sonra bir fırça dönüştürülür ve uygulanan <xref:System.Windows.Shapes.Ellipse> dairenin sağlayan kullanıcı Arabirimi. Veri daire dışında ' bırakılan olmadan, özgün sürüklediyseniz <xref:System.Windows.Shapes.Shape.Fill%2A> değeri dairenin yeniden uygulanır.  
  
### <a name="to-preview-the-effects-of-the-drag-and-drop-operation"></a>Sürükle ve bırak işlemi etkilerini önizlemek için  
  
1.  Circle.xaml.cs veya Circle.xaml.vb açın.  
  
2.  Özel bir daire sınıfında bildirin <xref:System.Windows.Media.Brush> adlı değişken `_previousFill` ve kendisine başlatma `null`.  
  
     [!code-csharp[DragDropWalkthrough#Brush](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#brush)]
     [!code-vb[DragDropWalkthrough#Brush](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#brush)]  
  
3.  Aşağıdakileri ekleyin <xref:System.Windows.UIElement.OnDragEnter%2A> sınıfı için işleme sağlamak üzere geçersiz kılma <xref:System.Windows.UIElement.DragEnter> olay.  
  
     [!code-csharp[DragDropWalkthrough#OnDragEnter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragenter)]
     [!code-vb[DragDropWalkthrough#OnDragEnter](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragenter)]  
  
     Bu <xref:System.Windows.UIElement.OnDragEnter%2A> geçersiz kılma aşağıdaki görevleri gerçekleştirir:  
  
    -   Kaydeder <xref:System.Windows.Shapes.Shape.Fill%2A> özelliği <xref:System.Windows.Shapes.Ellipse> içinde `_previousFill` değişkeni.  
  
    -   İçinde gerçekleştirilen aynı denetimleri gerçekleştirir <xref:System.Windows.UIElement.OnDrop%2A> yöntemi için veri dönüştürülüp dönüştürülemeyeceğini belirlemek için bir <xref:System.Windows.Media.Brush>.  
  
    -   Veriler geçerli bir dönüştürülürse <xref:System.Windows.Media.Brush>, uygular <xref:System.Windows.Shapes.Shape.Fill%2A> , <xref:System.Windows.Shapes.Ellipse>.  
  
4.  Aşağıdakileri ekleyin <xref:System.Windows.UIElement.OnDragLeave%2A> sınıfı için işleme sağlamak üzere geçersiz kılma <xref:System.Windows.UIElement.DragLeave> olay.  
  
     [!code-csharp[DragDropWalkthrough#OnDragLeave](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragleave)]
     [!code-vb[DragDropWalkthrough#OnDragLeave](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragleave)]  
  
     Bu <xref:System.Windows.UIElement.OnDragLeave%2A> geçersiz kılma aşağıdaki görevleri gerçekleştirir:  
  
    -   Geçerlidir <xref:System.Windows.Media.Brush> kaydedilen `_previousFill` değişkenini <xref:System.Windows.Shapes.Shape.Fill%2A> , <xref:System.Windows.Shapes.Ellipse> daire kullanıcı denetiminin kullanıcı Arabirimi sağlar.  
  
5.  Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın.  
  
6.  Metni seçin `green` içinde <xref:System.Windows.Controls.TextBox>.  
  
7.  Metnin bırakmadan olmadan bir daire denetime sürükleyin. Mavi yeşil daire değişiklikler.  
  
     ![Bir Sürükle etkilerini önizleme&#45;ve&#45;bırakma işlemi](../../../../docs/framework/wpf/advanced/media/dragdrop-previeweffects.png "DragDrop_PreviewEffects")  
  
8.  Metnin daire denetim uzağa doğru sürükleyin. Daireye mavi için yeşil geri değiştirir.  
  
## <a name="enabling-a-panel-to-receive-dropped-data"></a>Bırakılan veri almak bir Panel etkinleştirme  
 Bu bölümde, sürüklenen daire veri bırakma hedeflerini olarak davranmak üzere daire kullanıcı denetimleri konak paneller olanak sağlar. Bir daire bir panelinden taşıyın ya da bir daire sürükleyip sırasında CTRL tuşunu basılı tutarak bir daire denetiminin bir kopya yapmak için sağlayan kod gerçekleştireceksiniz.  
  
### <a name="to-enable-the-panel-to-be-a-drop-target"></a>Bırakma hedefi için Denetim Masası etkinleştirmek için  
  
1.  MainWindow.xaml açın.  
  
2.  Her birinde aşağıdaki XAML gösterildiği gibi <xref:System.Windows.Controls.StackPanel> denetimleri eklemek için işleyiciler <xref:System.Windows.UIElement.DragOver> ve <xref:System.Windows.UIElement.Drop> olaylar. Ad <xref:System.Windows.UIElement.DragOver> olay işleyicisi `panel_DragOver`ve ad <xref:System.Windows.UIElement.Drop> olay işleyicisi `panel_Drop`.  
  
     [!code-xaml[DragDropWalkthrough#PanelsXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml#panelsxaml)]  
  
3.  MainWindows.xaml.cs veya MainWindow.xaml.vb açın.  
  
4.  İçin aşağıdaki kodu ekleyip <xref:System.Windows.UIElement.DragOver> olay işleyicisi.  
  
     [!code-csharp[DragDropWalkthrough#PanelDragOver](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml.cs#paneldragover)]
     [!code-vb[DragDropWalkthrough#PanelDragOver](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/MainWindow.xaml.vb#paneldragover)]  
  
     Bu <xref:System.Windows.UIElement.DragOver> olay işleyicisi aşağıdaki görevleri gerçekleştirir:  
  
    -   Sürüklenen veri içinde paketlenmiş "Nesne" veri içerip içermediğini denetler <xref:System.Windows.DataObject> daire kullanıcı denetimi tarafından ve çağrısında geçirilen <xref:System.Windows.DragDrop.DoDragDrop%2A>.  
  
    -   "Nesne" veri varsa, CTRL tuşunu basılı olup olmadığını denetler.  
  
    -   CTRL tuşunu basılı, ayarlar <xref:System.Windows.DragEventArgs.Effects%2A> özelliğine <xref:System.Windows.DragDropEffects.Copy>. Aksi takdirde ayarlamak <xref:System.Windows.DragEventArgs.Effects%2A> özelliğine <xref:System.Windows.DragDropEffects.Move>.  
  
5.  İçin aşağıdaki kodu ekleyip <xref:System.Windows.UIElement.Drop> olay işleyicisi.  
  
     [!code-csharp[DragDropWalkthrough#PanelDrop](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml.cs#paneldrop)]
     [!code-vb[DragDropWalkthrough#PanelDrop](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/MainWindow.xaml.vb#paneldrop)]  
  
     Bu <xref:System.Windows.UIElement.Drop> olay işleyicisi aşağıdaki görevleri gerçekleştirir:  
  
    -   Denetler olup olmadığını <xref:System.Windows.UIElement.Drop> olay zaten işlenmiş. Başka bir daire kesilirse, örneğin, yuvarlak tanıtıcıları <xref:System.Windows.UIElement.Drop> olayı istemediğiniz ayrıca işlemek için bir daire içeren paneli.  
  
    -   Varsa <xref:System.Windows.UIElement.Drop> olay işlenmez, denetimleri CTRL tuşunu basılı olup olmadığını.  
  
    -   Ne zaman CTRL tuşunu basılı, <xref:System.Windows.UIElement.Drop> olduğunda, bir daire kopyasını yapar denetlemek ve ekleyin <xref:System.Windows.Controls.Panel.Children%2A> koleksiyonu <xref:System.Windows.Controls.StackPanel>.  
  
    -   CTRL tuşunu basılı değilse, gelen daire taşır <xref:System.Windows.Controls.Panel.Children%2A> kendi üst paneline koleksiyonunu <xref:System.Windows.Controls.Panel.Children%2A> bırakılmış paneli koleksiyonu.  
  
    -   Kümeleri <xref:System.Windows.DragEventArgs.Effects%2A> bildirmek için özellik <xref:System.Windows.DragDrop.DoDragDrop%2A> yöntemi olup olmadığını taşıma veya kopyalama işlemi gerçekleştirildi.  
  
6.  Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın.  
  
7.  Metni seçin `green` gelen <xref:System.Windows.Controls.TextBox>.  
  
8.  Metin üzerinde bir daire denetim sürükleyip bırakın.  
  
9. Bir daire denetimi sol panelden sağ panelde sürükleyip bırakın. Daireye kaldırılır <xref:System.Windows.Controls.Panel.Children%2A> sol panelde koleksiyonunu ve sağ panelde alt koleksiyona eklenir.  
  
10. Başka bir panele olarak panelinden bir daire denetimi sürükleyin ve CTRL tuşunu basılı tutarken bırakın. Daireye kopyalanır ve kopyayı eklenir <xref:System.Windows.Controls.Panel.Children%2A> alma panelini koleksiyonu.  
  
     ![CTRL tuşunu basılı tutarken bir daire sürükleyerek](../../../../docs/framework/wpf/advanced/media/dragdrop-paneldrop.png "DragDrop_PanelDrop")  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Sürükleme ve Bırakmaya Genel Bakış](../../../../docs/framework/wpf/advanced/drag-and-drop-overview.md)
