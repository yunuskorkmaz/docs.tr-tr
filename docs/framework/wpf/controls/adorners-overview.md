---
title: Donatıcılara Genel Bakış
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adorners [WPF], about adorners
ms.assetid: 33d4c5c2-2daf-4e45-ba9a-5b673e2b8280
ms.openlocfilehash: 22d9b1eddbb6db47fb15deebf94cfc5f8d37a380
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040843"
---
# <a name="adorners-overview"></a>Donatıcılara Genel Bakış

Donatıcılar, bir kullanıcıya görsel ipuçları sağlamak için kullanılan özel bir <xref:System.Windows.FrameworkElement>türüdür. Diğer kullanımlar arasında, Donatıcılar, öğelere işlevsel işleyiciler eklemek veya bir denetimle ilgili durum bilgilerini sağlamak için kullanılabilir.

## <a name="about-adorners"></a>Donatıcılar hakkında

<xref:System.Windows.Documents.Adorner>, bir <xref:System.Windows.UIElement>bağlanan özel bir <xref:System.Windows.FrameworkElement>. Donatıcılar, donatılan öğenin veya donatılan öğelerin bir koleksiyonunun her zaman üzerinde olan bir işleme yüzeyi olan bir <xref:System.Windows.Documents.AdornerLayer>işlenir. Bir donatıcının işlenmesi, donatıcının bağlandığı <xref:System.Windows.UIElement> işlemeden bağımsızdır. Bir donatıcı, genellikle, ilişkili olduğu öğeye göre konumlandırılır ve donatılan öğenin sol üst kısmında bulunan standart 2-b koordinat başlangıcını kullanarak konumlandırılır.

Donatıcılar için ortak uygulamalar şunlardır:

- Bir kullanıcının öğeyi bir şekilde (yeniden boyutlandırma, döndürme, yeniden konumlandırma, vb.) işlemesini sağlayan bir <xref:System.Windows.UIElement> işlevsel işleyiciler ekleme.
- Çeşitli durumları veya çeşitli olaylara yanıt olarak göstermek için görsel geri bildirim sağlayın.
- <xref:System.Windows.UIElement>görsel süslemeleri kaplama.
- Bir <xref:System.Windows.UIElement>kısmını veya tamamını görsel olarak maskesini veya geçersiz kılın.

[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] görsel öğeleri donatma için temel bir çerçeve sağlar. Aşağıdaki tabloda, nesneleri donatma ve amaçlarına göre kullanılan birincil türler listelenmektedir. Birçok kullanım örneği aşağıda verilmiştir:

|||
|-|-|
|<xref:System.Windows.Documents.Adorner>|Tüm somut donatıcı uygulamalarının devraldığı soyut temel sınıf.|
|<xref:System.Windows.Documents.AdornerLayer>|Bir veya daha fazla donatılan öğenin donatıcı için işleme katmanını temsil eden bir sınıf.|
|<xref:System.Windows.Documents.AdornerDecorator>|Bir donatıcı katmanının bir öğe koleksiyonuyla ilişkilendirilmesini sağlayan bir sınıf.|

## <a name="implementing-a-custom-adorner"></a>Özel Donatıcı Uygulama

[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] tarafından sunulan Donatıcılar çerçevesi öncelikle özel donatıcıları oluşturmayı desteklemek üzere tasarlanmıştır. Özel bir donatıcı, soyut <xref:System.Windows.Documents.Adorner> sınıfından devralan bir sınıf uygulayarak oluşturulur.

> [!NOTE]
> Bir <xref:System.Windows.Documents.Adorner> üst öğesi, donatılan öğeyi değil <xref:System.Windows.Documents.Adorner>işleyen <xref:System.Windows.Documents.AdornerLayer>.

Aşağıdaki örnek, basit bir donatıcı uygulayan bir sınıfı gösterir. Örnek donatıcı, bir <xref:System.Windows.UIElement> köşelerini çevrelerle donatır.

[!code-csharp[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_simplecircleadornerbody)]
[!code-vb[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_simplecircleadornerbody)]
  
Aşağıdaki görüntüde, bir <xref:System.Windows.Controls.TextBox>uygulanan SimpleCircleAdorner gösterilmektedir:

![Donatılan metin kutusunu gösteren ekran görüntüsü.](./media/adorners-overview/simplecircleadorner-textbox.png)

## <a name="rendering-behavior-for-adorners"></a>Donatıcılar için işleme davranışı

Donatıcıların herhangi bir devralınan işleme davranışı içermediğinden emin olmak önemlidir; bir donatıcının işleme, donatıcı uygulayıcının sorumluluğunda olmasını sağlamaktır. İşleme davranışını uygulamanın yaygın bir yolu <xref:System.Windows.UIElement.OnRender%2A> yöntemi geçersiz kılmanın yanı sıra bir veya daha fazla <xref:System.Windows.Media.DrawingContext> nesnesini kullanarak (Yukarıdaki örnekte gösterildiği gibi) donatıcının görsellerini oluşturmak için bir veya daha fazla nesne kullanmaktır.

> [!NOTE]
> Donatıcı katmanına yerleştirilmiş herhangi bir şey, ayarlamış olduğunuz stillerin en üstünde işlenir. Diğer bir deyişle, Donatıcılar her zaman görsel olarak açıktır ve z sırası kullanılarak geçersiz kılınamaz.

## <a name="events-and-hit-testing"></a>Olaylar ve Isabet testi

Donatıcılar, tıpkı diğer <xref:System.Windows.FrameworkElement>benzer şekilde giriş olayları alır.  Bir donatıcı her zaman, donatıladığı öğeden daha yüksek bir z düzeninde olduğundan, donatıcı, temel alınan donatılan öğeye yönelik olarak giriş olayları (<xref:System.Windows.UIElement.Drop> veya <xref:System.Windows.UIElement.MouseMove>gibi) alır.  Bir donatıcı, belirli giriş olaylarını dinleyebilir ve olayı yeniden oluşturarak bunları temel donatılan öğeye geçirebilir.

Bir donatıcı kapsamındaki öğelerin doğrudan isabet sınamasını etkinleştirmek için, donatıcı üzerinde isabet testi <xref:System.Windows.UIElement.IsHitTestVisible%2A> özelliğini **false** olarak ayarlayın.  İsabet testi hakkında daha fazla bilgi için bkz. [görsel katmandaki Isabet testi](../graphics-multimedia/hit-testing-in-the-visual-layer.md).

## <a name="adorning-a-single-uielement"></a>Tek bir UIElement 'i donatma

Bir donatıcıyı belirli bir <xref:System.Windows.UIElement>bağlamak için şu adımları izleyin:

1. <xref:System.Windows.UIElement> donatılacak bir <xref:System.Windows.Documents.AdornerLayer> nesnesi almak için <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> statik yöntemi çağırın. <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A>, belirtilen <xref:System.Windows.UIElement>başlayarak görsel ağacı gösterir ve bulduğu ilk donatıcı katmanını döndürür. (Bir donatıcı katmanı bulunmazsa, yöntem null döndürür.)

2. Donatıcıyı hedef <xref:System.Windows.UIElement>bağlamak için <xref:System.Windows.Documents.AdornerLayer.Add%2A> yöntemi çağırın.

 Aşağıdaki örnek bir SimpleCircleAdorner 'ı (yukarıda gösterilen) *myTextBox*adlı <xref:System.Windows.Controls.TextBox> bağlar:

 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornsingleelement)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornsingleelement)]

> [!NOTE]
> Bir donatıcıyı başka bir öğeye bağlamak için [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] kullanımı Şu anda desteklenmiyor.

## <a name="adorning-the-children-of-a-panel"></a>Panelin alt öğelerini donatma

Bir donatıcıyı bir <xref:System.Windows.Controls.Panel>alt öğesine bağlamak için şu adımları izleyin:

1. Alt öğeleri donatılacak olan öğe için bir donatıcı katmanı bulmak için <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> `static` yöntemi çağırın.

2. Üst öğenin alt öğelerini numaralandırın ve her bir alt öğeye bir donatıcı bağlamak için <xref:System.Windows.Documents.AdornerLayer.Add%2A> yöntemi çağırın.

Aşağıdaki örnek, *myStackPanel*adlı bir <xref:System.Windows.Controls.StackPanel> alt öğelerine bir SimpleCircleAdorner (yukarıda gösterilen) bağlar:

[!code-csharp[Adorners_SimpleCircleAdorner#_AdornChildren](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornchildren)]
[!code-vb[Adorners_SimpleCircleAdorner#_AdornChildren](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornchildren)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Media.AdornerHitTestResult>
- [WPF’de Şekiller ve Temel Çizimlere Genel Bakış](../graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)
- [Görüntüler, Çizimler ve Görsellerle Boyama](../graphics-multimedia/painting-with-images-drawings-and-visuals.md)
- [Çizim Nesnelerine Genel Bakış](../graphics-multimedia/drawing-objects-overview.md)
- [Nasıl Yapılır Konuları](adorners-how-to-topics.md)
