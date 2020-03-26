---
title: Donatıcılara Genel Bakış
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adorners [WPF], about adorners
ms.assetid: 33d4c5c2-2daf-4e45-ba9a-5b673e2b8280
ms.openlocfilehash: b41c1f10f7e1b7c1799fd27270a3eeb9899ceeb6
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80111185"
---
# <a name="adorners-overview"></a>Donatıcılara Genel Bakış

Süsleri özel bir <xref:System.Windows.FrameworkElement>türüdür, bir kullanıcıya görsel ipuçları sağlamak için kullanılır. Diğer kullanımların yanı sıra, Süsleyiciler öğelere işlevsel tutamaçları eklemek veya denetim hakkında durum bilgileri sağlamak için kullanılabilir.

## <a name="about-adorners"></a>Adorners Hakkında

Bir' <xref:System.Windows.Documents.Adorner> e <xref:System.Windows.FrameworkElement> bağlı bir <xref:System.Windows.UIElement>gelenektir. Süsleyiciler, <xref:System.Windows.Documents.AdornerLayer>her zaman süslenmiş elementin veya süslenmiş öğelerin bir koleksiyonunun üzerinde bulunan bir işleme yüzeyi olarak işlenir. Bir süsleyicinin işlenmesi, süsleyicinin <xref:System.Windows.UIElement> bağlı olduğu şeyin işlenmesinden bağımsızdır. Bir süsleyici genellikle, süslenmiş öğenin üst-sol kısmında bulunan standart 2B koordinat kökeni kullanılarak bağlı olduğu elemana göre konumlandırılır.

Süsleyiciler için ortak uygulamalar şunlardır:

- Bir kullanıcının öğeyi bir şekilde işlemesini sağlayan bir <xref:System.Windows.UIElement> işleme işletti (yeniden boyutlandırma, döndürme, yeniden konumlandırma, vb.) işlevsel tutamaçları ekleme.
- Çeşitli durumları belirtmek veya çeşitli olaylara yanıt olarak görsel geri bildirim sağlayın.
- Bir üzerinde bindirme <xref:System.Windows.UIElement>görsel süslemeleri .
- Görsel olarak maske veya bir kısmını <xref:System.Windows.UIElement>veya tamamını geçersiz kılar.

[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]görsel öğeleri süslemek için temel bir çerçeve sağlar. Aşağıdaki tabloda nesneleri süslerken kullanılan birincil türleri ve bunların amacı listelenerilmiştir. Çeşitli kullanım örnekleri aşağıdaki gibidir:

|||
|-|-|
|<xref:System.Windows.Documents.Adorner>|Tüm somut süsleyici uygulamalarının devraldığı soyut bir taban sınıfı.|
|<xref:System.Windows.Documents.AdornerLayer>|Bir veya daha fazla süslü öğenin süsleyicisi(ler) için bir işleme katmanını temsil eden bir sınıf.|
|<xref:System.Windows.Documents.AdornerDecorator>|Bir süsleyici katmanının öğeler topluluğuyla ilişkilendirilmesini sağlayan bir sınıf.|

## <a name="implementing-a-custom-adorner"></a>Özel Süsleyici Uygulama

Tarafından [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] sağlanan süsleyiciler çerçevesi öncelikle özel süsleyiciler oluşturulmasını desteklemek için tasarlanmıştır. Soyut <xref:System.Windows.Documents.Adorner> sınıftan devralan bir sınıf uygulanarak özel bir süsleyici oluşturulur.

> [!NOTE]
> Bir'in <xref:System.Windows.Documents.Adorner> üst <xref:System.Windows.Documents.AdornerLayer> öğesi, süslenen öğeyi <xref:System.Windows.Documents.Adorner>değil, öğeyi işleyendir.

Aşağıdaki örnek, basit bir süsleyici uygulayan bir sınıf gösterir. Örnek süsleyici sadece daireler ile <xref:System.Windows.UIElement> bir köşeleri süslüyor.

[!code-csharp[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_simplecircleadornerbody)]
[!code-vb[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_simplecircleadornerbody)]
  
Aşağıdaki resim simplecircleadorner uygulanan gösterir: <xref:System.Windows.Controls.TextBox>

![Süslü bir metin kutusunu gösteren ekran görüntüsü.](./media/adorners-overview/simplecircleadorner-textbox.png)

## <a name="rendering-behavior-for-adorners"></a>Süsleyiciler için Rendering Davranış

Bu süsleyiciler herhangi bir doğal render davranışı içermez dikkat etmek önemlidir; bir süsleyicinin işlemesini sağlamak, süsleyici uygulayıcının sorumluluğundadır. Oluşturma davranışı uygulamanın yaygın bir yolu <xref:System.Windows.UIElement.OnRender%2A> yöntemi geçersiz kılmak ve <xref:System.Windows.Media.DrawingContext> bir veya daha fazla nesne kullanarak süsleyicinin görsellerini gerektiği gibi işlemektir (yukarıdaki örnekte gösterildiği gibi).

> [!NOTE]
> Süsleyici katmanına yerleştirilen her şey, ayarladığınız stillerin geri kalanının üzerine işlenir. Başka bir deyişle, süsleyiciler her zaman görsel olarak üsttedir ve z-order kullanılarak geçersiz kılınamaz.

## <a name="events-and-hit-testing"></a>Olaylar ve Hit Test

Süsleri diğer gibi <xref:System.Windows.FrameworkElement>giriş olayları alırsınız.  Bir süsleyici nin her zaman süslediği öğeden daha yüksek bir z sırası olduğundan, süsleyici, temel süslenmiş öğe için tasarlanmış olabilecek giriş olayları (örneğin <xref:System.Windows.UIElement.Drop> veya) <xref:System.Windows.UIElement.MouseMove>alır.  Bir süsleyici belirli giriş olaylarını dinleyebilir ve bunları olayı yeniden yükselterek temel süslenmiş öğeye aktarabilir.

Bir süsleyici altında elemanların geçiş isabet testi sağlamak <xref:System.Windows.UIElement.IsHitTestVisible%2A> için, adorner **üzerinde yanlış** isabet test özelliği ayarlayın.  Isabet testi hakkında daha fazla bilgi için [Görsel Katman'daki Hit Testi'ne](../graphics-multimedia/hit-testing-in-the-visual-layer.md)bakın.

## <a name="adorning-a-single-uielement"></a>Tek Bir UIElement'i Süsleme

Bir süsleyiciyi belirli <xref:System.Windows.UIElement>bir zamana bağlamak için aşağıdaki adımları izleyin:

1. Süslüolması için <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> bir <xref:System.Windows.Documents.AdornerLayer> nesne almak <xref:System.Windows.UIElement> için statik yöntemi arayın. <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A>belirtilenden <xref:System.Windows.UIElement>başlayarak görsel ağaca doğru yürür ve bulduğu ilk süsleyici katmanını döndürür. (Hiçbir süsleyici katmanları bulunursa, yöntem null döndürür.)

2. Süsleyiciyi <xref:System.Windows.Documents.AdornerLayer.Add%2A> hedefe <xref:System.Windows.UIElement>bağlamak için yöntemi arayın.

 Aşağıdaki örnek, bir SimpleCircleAdorner (yukarıda gösterilen) <xref:System.Windows.Controls.TextBox> adlı *myTextBox*bağlar:

 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornsingleelement)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornsingleelement)]

> [!NOTE]
> Bir [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] süsleyiciyi başka bir öğeye bağlamak için kullanmak şu anda desteklenmez.

## <a name="adorning-the-children-of-a-panel"></a>Panelin Çocuklarını Süslemek

Bir süsleyiciyi çocuklarına <xref:System.Windows.Controls.Panel>bağlamak için aşağıdaki adımları izleyin:

1. Çocukları `static` süslenecek olan element için bir süsleyici katmanı bulmak için yöntemi <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> arayın.

2. Ana öğenin alt ları aracılığıyla sayısala <xref:System.Windows.Documents.AdornerLayer.Add%2A> ve her alt öğeye bir süsleyici bağlamak için yöntemi arayın.

Aşağıdaki örnek bir SimpleCircleAdorner (yukarıda gösterilen) <xref:System.Windows.Controls.StackPanel> *myStackPanel*adlı çocuklarına bağlar:

[!code-csharp[Adorners_SimpleCircleAdorner#_AdornChildren](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornchildren)]
[!code-vb[Adorners_SimpleCircleAdorner#_AdornChildren](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornchildren)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Media.AdornerHitTestResult>
- [WPF Genel Bakışı İçinde Şekiller ve Temel Çizimler](../graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)
- [Görüntüler, Çizimler ve Görsellerle Boyama](../graphics-multimedia/painting-with-images-drawings-and-visuals.md)
- [Çizim Nesnelerine Genel Bakış](../graphics-multimedia/drawing-objects-overview.md)
- [Nasıl Dır Konular](adorners-how-to-topics.md)
