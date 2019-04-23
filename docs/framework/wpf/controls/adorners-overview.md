---
title: Donatıcılara Genel Bakış
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adorners [WPF], about adorners
ms.assetid: 33d4c5c2-2daf-4e45-ba9a-5b673e2b8280
ms.openlocfilehash: 6b710df45379ccce4daf340b4dbe2701d3c96604
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59320476"
---
# <a name="adorners-overview"></a>Donatıcılara Genel Bakış
Donatıcıları, özel bir tür <xref:System.Windows.FrameworkElement>görsel ipuçları kullanıcıya sağlamak için kullanılır. Diğer kullanımının yanı sıra donatıcıları işlevsel tanıtıcıları öğeleri ekleyin ya da bir denetimi hakkındaki durum bilgilerini sağlamak için kullanılabilir.  

<a name="about_Adorners"></a>   
## <a name="about-adorners"></a>Donatıcılar hakkında  
 Bir <xref:System.Windows.Documents.Adorner> özel <xref:System.Windows.FrameworkElement> bağlanan bir <xref:System.Windows.UIElement>. Donatıcıları oluşturulur bir <xref:System.Windows.Documents.AdornerLayer>, her zaman donatılmış öğe veya donatılmış öğelerinin bir koleksiyonunu en üstünde olan bir işleme yüzeyi olduğu. İşleme, bağımsız bir donatıcının <xref:System.Windows.UIElement> donatıcı bağlı. Öğeye bir donatıcı genellikle, bu, donatılmış öğenin sol bulunan standart 2B koordinat kaynağını kullanarak bağlı olduğu öğe göre konumlandırılır.  
  
 Donatıcılar için ortak uygulamalar şunlardır:  
  
-   İşlev tanıtıcıları ekleyerek bir <xref:System.Windows.UIElement> öğeyi (yeniden boyutlandırma, döndürme, yeniden konumlandırma, vb.) bir şekilde işlemek bir kullanıcı etkinleştirin.  
  
-   Çeşitli durumları göstermek için görsel geri bildirim sağlamak veya çeşitli olaylara yanıt vermek.  
  
-   Görsel süslemeleri yer paylaşımı üzerindeki bir <xref:System.Windows.UIElement>.  
  
-   Görsel olarak maskelemek veya bölümünü veya tümünü geçersiz bir <xref:System.Windows.UIElement>.  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] görsel öğeler donatmak için temel çerçeveyi sağlar. Aşağıdaki tabloda, nesneleri ve bunların amacı donatmak olduğunda kullanılan birincil türlerini listeler. Çeşitli kullanım örnekleri izleyin.  
  
|||  
|-|-|  
|<xref:System.Windows.Documents.Adorner>|Tüm somut donatıcı uygulamaların devraldığı bir soyut temel sınıf.|  
|<xref:System.Windows.Documents.AdornerLayer>|Bir veya daha fazla donatılmış öğeleri donatıcı(ları) için işleme katmanını temsil eden sınıf.|  
|<xref:System.Windows.Documents.AdornerDecorator>|Öğelerinin bir koleksiyonunu ile ilişkilendirilecek bir donatıcı katmanı sağlayan bir sınıf.|  
  
<a name="implement_custom_Adorner"></a>   
## <a name="implementing-a-custom-adorner"></a>Özel bir donatıcı uygulama  
 Donatıcıları framework tarafından sağlanan [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] öncelikle özel donatıcıları oluşturulmasını desteklemek için tasarlanmıştır. Özet devralan bir sınıf uygulama tarafından oluşturulan özel bir donatıcı <xref:System.Windows.Documents.Adorner> sınıfı.  
  
> [!NOTE]
>  Üst öğesi bir <xref:System.Windows.Documents.Adorner> olduğu <xref:System.Windows.Documents.AdornerLayer> işleyen <xref:System.Windows.Documents.Adorner>, donatılan öğe değil.  
  
 Aşağıdaki örnek, basit bir donatıcı uygulayan bir sınıfı gösterir. Örnek donatıcı köşelerini yalnızca daireler donatır bir <xref:System.Windows.UIElement> daireler ile.  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_simplecircleadornerbody)]
 [!code-vb[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_simplecircleadornerbody)]  
  
 Aşağıdaki görüntüde uygulanan SimpleCircleAdorner gösterir bir <xref:System.Windows.Controls.TextBox>.  
  
 ![Donatılmış metin kutusunu gösteren ekran görüntüsü.](./media/adorners-overview/simplecircleadorner-textbox.png)  
  
<a name="rendering_behavior_for_Adorners"></a>   
## <a name="rendering-behavior-for-adorners"></a>Donatıcılar işleme davranışı  
 Donatıcıları herhangi devralınan işleme davranışını içermez dikkat edin önemlidir; öğeye bir donatıcı oluşturulduğunu sağlama donatıcı uygulayan sorumluluğundadır.   Geçersiz kılmak için işleme davranışını uygulamanın yaygın bir yolu olan <xref:System.Windows.UIElement.OnRender%2A> yöntemi ve bir veya daha fazla <xref:System.Windows.Media.DrawingContext> (yukarıdaki örnekte gösterildiği gibi) gerektiği gibi donatıcının görseller oluşturmak için nesne.  
  
> [!NOTE]
>  Herhangi bir şey donatıcı katmanında yerleştirilen ayarladığınız stilleri geri kalanı üstünde işlenir. Diğer bir deyişle, donatıcıları her zaman üstte görsel olarak sunulan ve z düzenini kullanarak geçersiz kılınamaz.  
  
<a name="adorner_events_hittest"></a>   
## <a name="events-and-hit-testing"></a>Olaylar ve isabet sınaması  
 Donatıcıları alma gibi diğer giriş olaylarını <xref:System.Windows.FrameworkElement>.  Öğeye bir donatıcı her zaman öğeden daha yüksek bir z düzenini olduğundan, giriş olaylarını donatıcı alır (gibi <xref:System.Windows.UIElement.Drop> veya <xref:System.Windows.UIElement.MouseMove>), amaçlanan donatılan öğeye için.  Öğeye bir donatıcı, belirli giriş olaylarını dinlemek ve bunların temelde donatılan öğeye açın olay yeniden oluşturularak geçirin.  
  
 İsabet öğeye bir donatıcı altındaki öğeleri sınamasına etkinleştirmek için isabet testi ayarlama <xref:System.Windows.UIElement.IsHitTestVisible%2A> özelliğini **false** donatıcı üzerinde.  İsabet testi hakkında daha fazla bilgi için bkz.  
  
 [Görsel katmanda tıklama testi](../graphics-multimedia/hit-testing-in-the-visual-layer.md).  
  
<a name="adorn_single_element"></a>   
## <a name="adorning-a-single-uielement"></a>Tek bir UIElement Donatma  
 Belirli bir öğeye bir donatıcı bağlama için <xref:System.Windows.UIElement>, şu adımları izleyin:  
  
1. Statik metodunu çağırın <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> almak için bir <xref:System.Windows.Documents.AdornerLayer> nesnesi <xref:System.Windows.UIElement> donatılmış için. <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> Belirtilen adreste başlayan görsel ağaç'kurmak gezer <xref:System.Windows.UIElement>ve bulduğu ilk donatıcı katmanı döndürür. (Hiçbir donatıcı katman bulunursa, yöntem null değeri döndürür.)  
  
2. Çağrı <xref:System.Windows.Documents.AdornerLayer.Add%2A> donatıcıyı hedefe bağlamak için yöntemi <xref:System.Windows.UIElement>.  
  
 Aşağıdaki örnekte (yukarıda gösterilen) SimpleCircleAdorner bağlayan bir <xref:System.Windows.Controls.TextBox> adlı *myTextBox*.  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornsingleelement)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornsingleelement)]  
  
> [!NOTE]
>  Kullanarak [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] başka bir öğeye bir donatıcı bağlamak için şu anda desteklenmiyor.  
  
<a name="adorn_children_panel"></a>   
## <a name="adorning-the-children-of-a-panel"></a>Panelin alt öğelerini Donatma  
 Alt öğeye bir donatıcı bağlama için bir <xref:System.Windows.Controls.Panel>, şu adımları izleyin:  
  
1. Çağrı `static` yöntemi <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> alt öğeleri donatılmış için öğeye bir donatıcı katmanı bulunacak.  
  
2. Çağrı ve üst öğenin alt öğelerini numaralandırın <xref:System.Windows.Documents.AdornerLayer.Add%2A> her alt öğeye bir donatıcı bağlama için yöntemi.  
  
 Aşağıdaki örnek SimpleCircleAdorner (yukarıda alt için gösterilen) bağlanır bir <xref:System.Windows.Controls.StackPanel> adlı *myStackPanel*.  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornChildren](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornchildren)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornChildren](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornchildren)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Media.AdornerHitTestResult>
- [WPF’de Şekiller ve Temel Çizimlere Genel Bakış](../graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)
- [Görüntüler, Çizimler ve Görsellerle Boyama](../graphics-multimedia/painting-with-images-drawings-and-visuals.md)
- [Çizim Nesnelerine Genel Bakış](../graphics-multimedia/drawing-objects-overview.md)
- [Nasıl Yapılır Konuları](adorners-how-to-topics.md)
