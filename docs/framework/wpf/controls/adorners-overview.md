---
title: Donatıcılara Genel Bakış
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adorners [WPF], about adorners
ms.assetid: 33d4c5c2-2daf-4e45-ba9a-5b673e2b8280
ms.openlocfilehash: d8e6e53edc92a2847c001377706d313cf97cced5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956102"
---
# <a name="adorners-overview"></a>Donatıcılara Genel Bakış
Donatıcılar <xref:System.Windows.FrameworkElement>, bir kullanıcıya görsel ipuçları sağlamak için kullanılan özel bir türüdür. Diğer kullanımlar arasında, Donatıcılar, öğelere işlevsel işleyiciler eklemek veya bir denetimle ilgili durum bilgilerini sağlamak için kullanılabilir.  

<a name="about_Adorners"></a>   
## <a name="about-adorners"></a>Donatıcılar hakkında  
 <xref:System.Windows.Documents.Adorner> , <xref:System.Windows.FrameworkElement> Bir öğesine<xref:System.Windows.UIElement>bağlanan özel bir. Donatıcılar, her zaman <xref:System.Windows.Documents.AdornerLayer>donatılan veya donatılan bir öğe koleksiyonu olan bir işleme yüzeyi olan bir üzerinde işlenir. Donatıcının işlenmesi, donatıcının bağlandığı öğenin <xref:System.Windows.UIElement> işlenmesinin bağımsızdır. Bir donatıcı, genellikle, ilişkili olduğu öğeye göre konumlandırılır ve donatılan öğenin sol üst kısmında bulunan standart 2-b koordinat başlangıcını kullanarak konumlandırılır.  
  
 Donatıcılar için ortak uygulamalar şunlardır:  
  
- Bir kullanıcının öğeyi bir şekilde <xref:System.Windows.UIElement> (yeniden boyutlandırma, döndürme, yeniden konumlandırma, vb.) işlemesini sağlayan bir öğesine işlevsel işleyiciler ekleme.  
  
- Çeşitli durumları veya çeşitli olaylara yanıt olarak göstermek için görsel geri bildirim sağlayın.  
  
- Görsel süslemeleri bir <xref:System.Windows.UIElement>üzerinde kaplama.  
  
- Bir <xref:System.Windows.UIElement>kısmını veya tümünü görsel olarak maskesini veya geçersiz kılın.  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]görsel öğeleri donatma için temel bir çerçeve sağlar. Aşağıdaki tabloda, nesneleri donatma ve amaçlarına göre kullanılan birincil türler listelenmektedir. Birçok kullanım örneği aşağıda verilmiştir.  
  
|||  
|-|-|  
|<xref:System.Windows.Documents.Adorner>|Tüm somut donatıcı uygulamalarının devraldığı soyut temel sınıf.|  
|<xref:System.Windows.Documents.AdornerLayer>|Bir veya daha fazla donatılan öğenin donatıcı için işleme katmanını temsil eden bir sınıf.|  
|<xref:System.Windows.Documents.AdornerDecorator>|Bir donatıcı katmanının bir öğe koleksiyonuyla ilişkilendirilmesini sağlayan bir sınıf.|  
  
<a name="implement_custom_Adorner"></a>   
## <a name="implementing-a-custom-adorner"></a>Özel Donatıcı Uygulama  
 Tarafından [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] sunulan Donatıcılar çerçevesi öncelikle özel donatıcıları oluşturmayı desteklemek üzere tasarlanmıştır. Özel bir donatıcı, soyut <xref:System.Windows.Documents.Adorner> sınıftan devralan bir sınıf uygulayarak oluşturulur.  
  
> [!NOTE]
> Öğesinin üst <xref:System.Windows.Documents.Adorner> <xref:System.Windows.Documents.AdornerLayer> öğesi, donatılan öğeyi değil <xref:System.Windows.Documents.Adorner>öğesini işleyen öğesidir.  
  
 Aşağıdaki örnek, basit bir donatıcı uygulayan bir sınıfı gösterir. Örnek donatıcı, bir çemberin köşelerini bir <xref:System.Windows.UIElement> daire içinde donatır.  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_simplecircleadornerbody)]
 [!code-vb[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_simplecircleadornerbody)]  
  
 Aşağıdaki görüntüde, öğesine <xref:System.Windows.Controls.TextBox>uygulanan SimpleCircleAdorner gösterilmektedir.  
  
 ![Donatılan metin kutusunu gösteren ekran görüntüsü.](./media/adorners-overview/simplecircleadorner-textbox.png)  
  
<a name="rendering_behavior_for_Adorners"></a>   
## <a name="rendering-behavior-for-adorners"></a>Donatıcılar için işleme davranışı  
 Donatıcıların herhangi bir devralınan işleme davranışı içermediğinden emin olmak önemlidir; bir donatıcının işleme, donatıcı uygulayıcının sorumluluğunda olmasını sağlamaktır.   İşleme davranışını uygulamanın yaygın bir yolu, <xref:System.Windows.UIElement.OnRender%2A> yöntemi geçersiz kılmak ve bir veya daha fazla nesneyi, donatıcının gerektiğinde (Yukarıdaki örnekte gösterildiği gibi) işlemek için bir veya daha fazla <xref:System.Windows.Media.DrawingContext> nesne kullanmaktır.  
  
> [!NOTE]
> Donatıcı katmanına yerleştirilmiş herhangi bir şey, ayarlamış olduğunuz stillerin en üstünde işlenir. Diğer bir deyişle, Donatıcılar her zaman görsel olarak açıktır ve z sırası kullanılarak geçersiz kılınamaz.  
  
<a name="adorner_events_hittest"></a>   
## <a name="events-and-hit-testing"></a>Olaylar ve Isabet testi  
 Donatıcılar, tıpkı diğer <xref:System.Windows.FrameworkElement>gibi giriş olayları alır.  Bir donatıcı her zaman, donatıladığı öğeden daha yüksek bir z düzeninde olduğundan, donatıcı, temel alınan donatılan öğeye yönelik olarak <xref:System.Windows.UIElement.Drop> giriş olayları (veya <xref:System.Windows.UIElement.MouseMove>gibi) alır.  Bir donatıcı, belirli giriş olaylarını dinleyebilir ve olayı yeniden oluşturarak bunları temel donatılan öğeye geçirebilir.  
  
 Bir donatıcı kapsamındaki öğelerin doğrudan isabet sınamasını etkinleştirmek için, donatıcı üzerinde isabet testi <xref:System.Windows.UIElement.IsHitTestVisible%2A> özelliğini **false** olarak ayarlayın.  İsabet testi hakkında daha fazla bilgi için bkz.  
  
 [Görsel katmandaki Isabet testi](../graphics-multimedia/hit-testing-in-the-visual-layer.md).  
  
<a name="adorn_single_element"></a>   
## <a name="adorning-a-single-uielement"></a>Tek bir UIElement 'i donatma  
 Bir donatıcıyı belirli <xref:System.Windows.UIElement>bir nesneye bağlamak için şu adımları izleyin:  
  
1. ' Nin donatılacak <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> bir <xref:System.Windows.Documents.AdornerLayer> nesne <xref:System.Windows.UIElement> almak için static yöntemi çağırın. <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A>görsel ağacı, belirtilen <xref:System.Windows.UIElement>' dan başlayarak ve bulduğu ilk donatıcı katmanını döndürür. (Bir donatıcı katmanı bulunmazsa, yöntem null döndürür.)  
  
2. Donatıcıyı hedefe <xref:System.Windows.UIElement>bağlamak için yönteminiçağırın.<xref:System.Windows.Documents.AdornerLayer.Add%2A>  
  
 Aşağıdaki örnek, bir SimpleCircleAdorner 'ı (yukarıda gösterilen) adlandırılmış bir <xref:System.Windows.Controls.TextBox> *myTextBox*öğesine bağlar.  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornsingleelement)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornsingleelement)]  
  
> [!NOTE]
> Bir [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] donatıcıyı başka bir öğeye bağlamak için kullanılması şu anda desteklenmiyor.  
  
<a name="adorn_children_panel"></a>   
## <a name="adorning-the-children-of-a-panel"></a>Panelin alt öğelerini donatma  
 Bir donatıcıyı a <xref:System.Windows.Controls.Panel>'nın alt öğelerine bağlamak için şu adımları izleyin:  
  
1. Alt öğeleri donatılacak olan öğe için bir donatıcı katmanı bulmak için <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> yönteminiçağırın.`static`  
  
2. Üst öğenin alt öğelerini numaralandırın ve her bir alt öğeye bir <xref:System.Windows.Documents.AdornerLayer.Add%2A> donatıcı bağlamak için yöntemini çağırın.  
  
 Aşağıdaki örnek bir SimpleCircleAdorner (yukarıda gösterilen) <xref:System.Windows.Controls.StackPanel> adlı bir *myStackPanel*alt öğesine bağlar.  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornChildren](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornchildren)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornChildren](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornchildren)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Media.AdornerHitTestResult>
- [WPF’de Şekiller ve Temel Çizimlere Genel Bakış](../graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)
- [Görüntüler, Çizimler ve Görsellerle Boyama](../graphics-multimedia/painting-with-images-drawings-and-visuals.md)
- [Çizim Nesnelerine Genel Bakış](../graphics-multimedia/drawing-objects-overview.md)
- [Nasıl Yapılır Konuları](adorners-how-to-topics.md)
