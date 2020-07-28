---
title: Donatıcılara Genel Bakış
description: Bir kullanıcıya, öğelerin işlevsel tutamaçları gibi ipuçları sağlayan özel bir FrameworkElement türü olan Windows Presentation Foundation donatıcıları hakkında bilgi edinin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adorners [WPF], about adorners
ms.assetid: 33d4c5c2-2daf-4e45-ba9a-5b673e2b8280
ms.openlocfilehash: 43d4af9f86c6ae72a61f86d1ca19405c2dcc6cc8
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87167727"
---
# <a name="adorners-overview"></a>Donatıcılara Genel Bakış

Donatıcılar <xref:System.Windows.FrameworkElement> , bir kullanıcıya görsel ipuçları sağlamak için kullanılan özel bir türüdür. Diğer kullanımlar arasında, Donatıcılar, öğelere işlevsel işleyiciler eklemek veya bir denetimle ilgili durum bilgilerini sağlamak için kullanılabilir.

## <a name="about-adorners"></a>Donatıcılar hakkında

<xref:System.Windows.Documents.Adorner>, <xref:System.Windows.FrameworkElement> Bir öğesine bağlanan özel bir <xref:System.Windows.UIElement> . Donatıcılar <xref:System.Windows.Documents.AdornerLayer> , her zaman donatılan veya donatılan bir öğe koleksiyonu olan bir işleme yüzeyi olan bir üzerinde işlenir. Donatıcının işlenmesi, donatıcının bağlandığı öğenin işlenmesinin bağımsızdır <xref:System.Windows.UIElement> . Bir donatıcı genellikle, ilişkili olduğu öğeye göre konumlandırılır ve donatılan öğenin sol üst kısmında bulunan standart 2B koordinat başlangıcını kullanarak konumlandırılır.

Donatıcılar için ortak uygulamalar şunlardır:

- Bir <xref:System.Windows.UIElement> kullanıcının öğeyi bir şekilde (yeniden boyutlandırma, döndürme, yeniden konumlandırma, vb.) işlemesini sağlayan bir öğesine işlevsel işleyiciler ekleme.
- Çeşitli durumları veya çeşitli olaylara yanıt olarak göstermek için görsel geri bildirim sağlayın.
- Görsel süslemeleri bir üzerinde kaplama <xref:System.Windows.UIElement> .
- Bir kısmını veya tümünü görsel olarak maskesini veya geçersiz kılın <xref:System.Windows.UIElement> .

[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]görsel öğeleri donatma için temel bir çerçeve sağlar. Aşağıdaki tabloda, nesneleri donatma ve amaçlarına göre kullanılan birincil türler listelenmektedir. Birçok kullanım örneği aşağıda verilmiştir:

|||
|-|-|
|<xref:System.Windows.Documents.Adorner>|Tüm somut donatıcı uygulamalarının devraldığı soyut temel sınıf.|
|<xref:System.Windows.Documents.AdornerLayer>|Bir veya daha fazla donatılan öğenin donatıcı için işleme katmanını temsil eden bir sınıf.|
|<xref:System.Windows.Documents.AdornerDecorator>|Bir donatıcı katmanının bir öğe koleksiyonuyla ilişkilendirilmesini sağlayan bir sınıf.|

## <a name="implementing-a-custom-adorner"></a>Özel Donatıcı Uygulama

Tarafından sunulan Donatıcılar çerçevesi [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] öncelikle özel donatıcıları oluşturmayı desteklemek üzere tasarlanmıştır. Özel bir donatıcı, soyut sınıftan devralan bir sınıf uygulayarak oluşturulur <xref:System.Windows.Documents.Adorner> .

> [!NOTE]
> Öğesinin üst öğesi, <xref:System.Windows.Documents.Adorner> <xref:System.Windows.Documents.AdornerLayer> <xref:System.Windows.Documents.Adorner> donatılan öğeyi değil öğesini işleyen öğesidir.

Aşağıdaki örnek, basit bir donatıcı uygulayan bir sınıfı gösterir. Örnek donatıcı, bir çemberin köşelerini bir daire içinde donatır <xref:System.Windows.UIElement> .

[!code-csharp[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_simplecircleadornerbody)]
[!code-vb[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_simplecircleadornerbody)]
  
Aşağıdaki görüntüde, öğesine uygulanan SimpleCircleAdorner gösterilmektedir <xref:System.Windows.Controls.TextBox> :

![Donatılan metin kutusunu gösteren ekran görüntüsü.](./media/adorners-overview/simplecircleadorner-textbox.png)

## <a name="rendering-behavior-for-adorners"></a>Donatıcılar için işleme davranışı

Donatıcıların herhangi bir devralınan işleme davranışı içermediğinden emin olmak önemlidir; bir donatıcının işleme, donatıcı uygulayıcının sorumluluğunda olmasını sağlamaktır. İşleme davranışını uygulamanın yaygın bir yolu, yöntemi geçersiz kılmak <xref:System.Windows.UIElement.OnRender%2A> ve bir veya daha fazla <xref:System.Windows.Media.DrawingContext> nesneyi, donatıcının gerektiğinde (Yukarıdaki örnekte gösterildiği gibi) işlemek için bir veya daha fazla nesne kullanmaktır.

> [!NOTE]
> Donatıcı katmanına yerleştirilmiş herhangi bir şey, ayarlamış olduğunuz stillerin en üstünde işlenir. Diğer bir deyişle, Donatıcılar her zaman görsel olarak açıktır ve z sırası kullanılarak geçersiz kılınamaz.

## <a name="events-and-hit-testing"></a>Olaylar ve Isabet testi

Donatıcılar, tıpkı diğer gibi giriş olayları alır <xref:System.Windows.FrameworkElement> .  Bir donatıcı her zaman, donatıladığı öğeden daha yüksek bir z düzeninde olduğundan, donatıcı, <xref:System.Windows.UIElement.Drop> <xref:System.Windows.UIElement.MouseMove> temel alınan donatılan öğeye yönelik olarak giriş olayları (veya gibi) alır.  Bir donatıcı, belirli giriş olaylarını dinleyebilir ve olayı yeniden oluşturarak bunları temel donatılan öğeye geçirebilir.

Bir donatıcı kapsamındaki öğelerin doğrudan isabet sınamasını etkinleştirmek için, <xref:System.Windows.UIElement.IsHitTestVisible%2A> donatıcı üzerinde isabet testi özelliğini **false** olarak ayarlayın.  İsabet testi hakkında daha fazla bilgi için bkz. [görsel katmandaki Isabet testi](../graphics-multimedia/hit-testing-in-the-visual-layer.md).

## <a name="adorning-a-single-uielement"></a>Tek bir UIElement 'i donatma

Bir donatıcıyı belirli bir nesneye bağlamak için <xref:System.Windows.UIElement> şu adımları izleyin:

1. ' Nin <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> donatılacak bir nesne almak için static yöntemi çağırın <xref:System.Windows.Documents.AdornerLayer> <xref:System.Windows.UIElement> . <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A>görsel ağacı, belirtilen ' dan başlayarak <xref:System.Windows.UIElement> ve bulduğu ilk donatıcı katmanını döndürür. (Bir donatıcı katmanı bulunmazsa, yöntem null döndürür.)

2. <xref:System.Windows.Documents.AdornerLayer.Add%2A>Donatıcıyı hedefe bağlamak için yöntemini çağırın <xref:System.Windows.UIElement> .

 Aşağıdaki örnek bir SimpleCircleAdorner 'ı (yukarıda gösterilen) <xref:System.Windows.Controls.TextBox> adlandırılmış bir *myTextBox*'a bağlar:

 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornsingleelement)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornsingleelement)]

> [!NOTE]
> Bir [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] donatıcıyı başka bir öğeye bağlamak için kullanılması şu anda desteklenmiyor.

## <a name="adorning-the-children-of-a-panel"></a>Panelin alt öğelerini donatma

Bir donatıcıyı a 'nın alt öğelerine bağlamak için <xref:System.Windows.Controls.Panel> şu adımları izleyin:

1. `static` <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> Alt öğeleri donatılacak olan öğe için bir donatıcı katmanı bulmak için yöntemini çağırın.

2. Üst öğenin alt öğelerini numaralandırın ve <xref:System.Windows.Documents.AdornerLayer.Add%2A> her bir alt öğeye bir donatıcı bağlamak için yöntemini çağırın.

Aşağıdaki örnek bir SimpleCircleAdorner (yukarıda gösterilen) <xref:System.Windows.Controls.StackPanel> adlı bir *myStackPanel*alt öğesine bağlar:

[!code-csharp[Adorners_SimpleCircleAdorner#_AdornChildren](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornchildren)]
[!code-vb[Adorners_SimpleCircleAdorner#_AdornChildren](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornchildren)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Media.AdornerHitTestResult>
- [WPF Genel Bakışı İçinde Şekiller ve Temel Çizimler](../graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)
- [Görüntüler, Çizimler ve Görsellerle Boyama](../graphics-multimedia/painting-with-images-drawings-and-visuals.md)
- [Çizim Nesnelerine Genel Bakış](../graphics-multimedia/drawing-objects-overview.md)
- [Nasıl Yapılır Konuları](adorners-how-to-topics.md)
