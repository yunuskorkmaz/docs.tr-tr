---
title: Donatıcılara Genel Bakış
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adorners [WPF], about adorners
ms.assetid: 33d4c5c2-2daf-4e45-ba9a-5b673e2b8280
ms.openlocfilehash: 6dd38b9e24b42de8945c0e9729f8f30cf901fc3a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="adorners-overview"></a>Donatıcılara Genel Bakış
Donatıcılar, özel bir tür <xref:System.Windows.FrameworkElement>, bir kullanıcı için görsel ipuçları sağlamak için kullanılan. Diğer kullanımlar arasında Donatıcılar işlevsel tanıtıcıları öğelere eklemek ya da bir denetimi hakkındaki durum bilgilerini sağlamak için kullanılabilir.  
  
  
  
<a name="about_Adorners"></a>   
## <a name="about-adorners"></a>Donatıcılar hakkında  
 Bir <xref:System.Windows.Documents.Adorner> özel <xref:System.Windows.FrameworkElement> için bağlı bir <xref:System.Windows.UIElement>. Donatıcılar işlenir bir <xref:System.Windows.Documents.AdornerLayer>, her zaman donatılmış öğesi donatılmış öğe koleksiyonunu en üstünde mi işleme yüzeyi olduğu. Bir donatıcının, işleme bağımsız <xref:System.Windows.UIElement> donatıcı bağlı. Donatıcı genellikle, bu, sol üst donatılmış öğesinin bulunan standart 2B koordinat kaynağını kullanarak bağlı olduğu öğesi göre konumlandırıldı.  
  
 Donatıcılar için ortak uygulamalar şunlardır:  
  
-   İşlev işleyicilerine ekleme bir <xref:System.Windows.UIElement> öğeyi bazı şekilde (yeniden boyutlandırma, döndürme, yeniden konumlandırmak, vb.) işlemek bir kullanıcı etkinleştirin.  
  
-   Çeşitli durumlarını belirtmek için görsel geribildirim sağlamak veya çeşitli olaylarına yanıt olarak.  
  
-   Üzerinde Visual düzenlemelerinin kaplama bir <xref:System.Windows.UIElement>.  
  
-   Görsel olarak maskeleme veya bölümünü veya tümünü geçersiz kılma bir <xref:System.Windows.UIElement>.  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] görsel öğeler eklemek için temel bir çerçeve sağlar. Aşağıdaki tabloda, nesneleri ve bunların amaçla eklemek kullanılan birincil türleri listelenmektedir. Birkaç kullanım örnekleri izleyin.  
  
|||  
|-|-|  
|<xref:System.Windows.Documents.Adorner>|Tüm donatıcı uygulamaların somut Özet temel sınıf devralır.|  
|<xref:System.Windows.Documents.AdornerLayer>|Bir veya daha fazla donatılmış öğelerin donatıcı(ları) için işleme katmanını temsil eden sınıf.|  
|<xref:System.Windows.Documents.AdornerDecorator>|Öğe koleksiyonunu ile ilişkilendirilecek bir donatıcı katmanı sağlayan sınıf.|  
  
<a name="implement_custom_Adorner"></a>   
## <a name="implementing-a-custom-adorner"></a>Özel donatıcı uygulama  
 Tarafından sağlanan donatıcılar çerçevesi [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] öncelikle özel donatıcıların oluşturulmasını desteklemek üzere tasarlanmıştır. Özel bir donatıcı Özet devralan bir sınıf uygulama tarafından oluşturulan <xref:System.Windows.Documents.Adorner> sınıfı.  
  
> [!NOTE]
>  Üst bir <xref:System.Windows.Documents.Adorner> olan <xref:System.Windows.Documents.AdornerLayer> işleyen <xref:System.Windows.Documents.Adorner>, donatılmakta öğesi değil.  
  
 Aşağıdaki örnekte basit bir donatıcı uygulayan bir sınıfı gösterir. Örnek donatıcı yalnızca köşelerinde daireler donatır bir <xref:System.Windows.UIElement> daireler ile.  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_simplecircleadornerbody)]
 [!code-vb[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_simplecircleadornerbody)]  
  
 Aşağıdaki resimde uygulanan SimpleCircleAdorner gösterilmiştir bir <xref:System.Windows.Controls.TextBox>.  
  
 ![Donatıcılar örneği: Donatılmış bir metin kutusu](../../../../docs/framework/wpf/controls/media/adornedtextbox.png "AdornedTextBox")  
  
<a name="rendering_behavior_for_Adorners"></a>   
## <a name="rendering-behavior-for-adorners"></a>Donatıcılar için işleme davranışı  
 Donatıcılar herhangi devralınmış işleme davranışını içermez dikkate almak önemlidir; donatıcı işler sağlama donatıcı uygulayan sorumluluğundadır.   İşleme davranışını uygulamanın en yaygın yolu geçersiz kılmaktır <xref:System.Windows.UIElement.OnRender%2A> yöntemi ve bir veya daha fazla <xref:System.Windows.Media.DrawingContext> donatıcının (yukarıdaki örnekte gösterildiği gibi) gereken görsellerini işlemek için nesneleri.  
  
> [!NOTE]
>  Donatıcı katmanında yerleştirilen herhangi bir şey, ayarladığınız stilleri rest üstünde işlenir. Diğer bir deyişle, Donatıcılar her zaman görsel olarak üsttedir ve z düzenini kullanarak geçersiz kılınamaz.  
  
<a name="adorner_events_hittest"></a>   
## <a name="events-and-hit-testing"></a>Olaylar ve isabet testi  
 Donatıcılar alma gibi diğer giriş olaylarını <xref:System.Windows.FrameworkElement>.  Donatıcı her zaman daha yüksek bir z-sırası öğeden olduğundan, donatıcı giriş olaylarını alır (gibi <xref:System.Windows.UIElement.Drop> veya <xref:System.Windows.UIElement.MouseMove>) donattığı donatılan öğeye yönelik.  Donatıcı belirli giriş olaylarını dinleme ve bunlar temel donatılmış öğesi açın olay yeniden yükselterek geçirin.  
  
 Geçiş isabet donatıcı altında öğelerinin testlerini etkinleştirmek için isabet testi ayarlama <xref:System.Windows.UIElement.IsHitTestVisible%2A> özelliğine **false** donatıcı üzerinde.  İsabet testi hakkında daha fazla bilgi için bkz:  
  
 [Görsel katmanda isabet sınaması](../../../../docs/framework/wpf/graphics-multimedia/hit-testing-in-the-visual-layer.md).  
  
<a name="adorn_single_element"></a>   
## <a name="adorning-a-single-uielement"></a>Tek bir UIElement eklemek  
 Belirli bir donatıcı bağlamak için <xref:System.Windows.UIElement>, şu adımları izleyin:  
  
1.  Statik metodunu çağırın <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> almak için bir <xref:System.Windows.Documents.AdornerLayer> için nesne <xref:System.Windows.UIElement> donatılacak. <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> Belirtilen başlangıç görsel ağaç anlatılmaktadır <xref:System.Windows.UIElement>ve bulduğu ilk donatıcı katmanı döndürür. (Hiçbir donatıcı katman bulunamazsa, yöntem null değeri döndürür.)  
  
2.  Çağrı <xref:System.Windows.Documents.AdornerLayer.Add%2A> donatıcıyı hedef bağlamak için yöntemi <xref:System.Windows.UIElement>.  
  
 Aşağıdaki örnekte (yukarıda gösterilen) SimpleCircleAdorner bağlanır bir <xref:System.Windows.Controls.TextBox> adlı *myTextBox*.  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornSingleElement](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornsingleelement)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornSingleElement](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornsingleelement)]  
  
> [!NOTE]
>  Kullanarak [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] donatıcı başka bir öğeye bağlamak için şu anda desteklenmiyor.  
  
<a name="adorn_children_panel"></a>   
## <a name="adorning-the-children-of-a-panel"></a>Bir panelinin alt eklemek  
 Alt öğelerinin donatıcı bağlamak için bir <xref:System.Windows.Controls.Panel>, şu adımları izleyin:  
  
1.  Çağrı `static` yöntemi <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> alt öğeleri olan donatılacak öğe için donatıcı katmanı bulunamıyor.  
  
2.  Çağrı ve üst öğenin alt öğeleri listeleme <xref:System.Windows.Documents.AdornerLayer.Add%2A> donatıcı her alt öğeye bağlamak için yöntem.  
  
 Aşağıdaki örnek bir SimpleCircleAdorner (yukarıda alt öğelerinin gösterilen) bağlanır bir <xref:System.Windows.Controls.StackPanel> adlı *myStackPanel*.  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornChildren](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornchildren)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornChildren](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornchildren)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Media.AdornerHitTestResult>  
 [WPF’de Şekiller ve Temel Çizimlere Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)  
 [Görüntüler, Çizimler ve Görsellerle Boyama](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)  
 [Çizim Nesnelerine Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)  
 [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/controls/adorners-how-to-topics.md)
