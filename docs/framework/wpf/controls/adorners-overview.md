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
# <a name="adorners-overview"></a><span data-ttu-id="5e326-102">Donatıcılara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="5e326-102">Adorners Overview</span></span>
<span data-ttu-id="5e326-103">Donatıcılar <xref:System.Windows.FrameworkElement>, bir kullanıcıya görsel ipuçları sağlamak için kullanılan özel bir türüdür.</span><span class="sxs-lookup"><span data-stu-id="5e326-103">Adorners are a special type of <xref:System.Windows.FrameworkElement>, used to provide visual cues to a user.</span></span> <span data-ttu-id="5e326-104">Diğer kullanımlar arasında, Donatıcılar, öğelere işlevsel işleyiciler eklemek veya bir denetimle ilgili durum bilgilerini sağlamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5e326-104">Among other uses, Adorners can be used to add functional handles to elements or provide state information about a control.</span></span>  

<a name="about_Adorners"></a>   
## <a name="about-adorners"></a><span data-ttu-id="5e326-105">Donatıcılar hakkında</span><span class="sxs-lookup"><span data-stu-id="5e326-105">About Adorners</span></span>  
 <span data-ttu-id="5e326-106"><xref:System.Windows.Documents.Adorner> , <xref:System.Windows.FrameworkElement> Bir öğesine<xref:System.Windows.UIElement>bağlanan özel bir.</span><span class="sxs-lookup"><span data-stu-id="5e326-106">An <xref:System.Windows.Documents.Adorner> is a custom <xref:System.Windows.FrameworkElement> that is bound to a <xref:System.Windows.UIElement>.</span></span> <span data-ttu-id="5e326-107">Donatıcılar, her zaman <xref:System.Windows.Documents.AdornerLayer>donatılan veya donatılan bir öğe koleksiyonu olan bir işleme yüzeyi olan bir üzerinde işlenir.</span><span class="sxs-lookup"><span data-stu-id="5e326-107">Adorners are rendered in an <xref:System.Windows.Documents.AdornerLayer>, which is a rendering surface that is always on top of the adorned element or a collection of adorned elements.</span></span> <span data-ttu-id="5e326-108">Donatıcının işlenmesi, donatıcının bağlandığı öğenin <xref:System.Windows.UIElement> işlenmesinin bağımsızdır.</span><span class="sxs-lookup"><span data-stu-id="5e326-108">Rendering of an adorner is independent from rendering of the <xref:System.Windows.UIElement> that the adorner is bound to.</span></span> <span data-ttu-id="5e326-109">Bir donatıcı, genellikle, ilişkili olduğu öğeye göre konumlandırılır ve donatılan öğenin sol üst kısmında bulunan standart 2-b koordinat başlangıcını kullanarak konumlandırılır.</span><span class="sxs-lookup"><span data-stu-id="5e326-109">An adorner is typically positioned relative to the element to which it is bound, using the standard 2-D coordinate origin located at the upper-left of the adorned element.</span></span>  
  
 <span data-ttu-id="5e326-110">Donatıcılar için ortak uygulamalar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="5e326-110">Common applications for adorners include:</span></span>  
  
- <span data-ttu-id="5e326-111">Bir kullanıcının öğeyi bir şekilde <xref:System.Windows.UIElement> (yeniden boyutlandırma, döndürme, yeniden konumlandırma, vb.) işlemesini sağlayan bir öğesine işlevsel işleyiciler ekleme.</span><span class="sxs-lookup"><span data-stu-id="5e326-111">Adding functional handles to a <xref:System.Windows.UIElement> that enable a user to manipulate the element in some way (resize, rotate, reposition, etc.).</span></span>  
  
- <span data-ttu-id="5e326-112">Çeşitli durumları veya çeşitli olaylara yanıt olarak göstermek için görsel geri bildirim sağlayın.</span><span class="sxs-lookup"><span data-stu-id="5e326-112">Provide visual feedback to indicate various states, or in response to various events.</span></span>  
  
- <span data-ttu-id="5e326-113">Görsel süslemeleri bir <xref:System.Windows.UIElement>üzerinde kaplama.</span><span class="sxs-lookup"><span data-stu-id="5e326-113">Overlay visual decorations on a <xref:System.Windows.UIElement>.</span></span>  
  
- <span data-ttu-id="5e326-114">Bir <xref:System.Windows.UIElement>kısmını veya tümünü görsel olarak maskesini veya geçersiz kılın.</span><span class="sxs-lookup"><span data-stu-id="5e326-114">Visually mask or override part or all of a <xref:System.Windows.UIElement>.</span></span>  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]<span data-ttu-id="5e326-115">görsel öğeleri donatma için temel bir çerçeve sağlar.</span><span class="sxs-lookup"><span data-stu-id="5e326-115">provides a basic framework for adorning visual elements.</span></span> <span data-ttu-id="5e326-116">Aşağıdaki tabloda, nesneleri donatma ve amaçlarına göre kullanılan birincil türler listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="5e326-116">The following table lists the primary types used when adorning objects, and their purpose.</span></span> <span data-ttu-id="5e326-117">Birçok kullanım örneği aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="5e326-117">Several usage examples follow.</span></span>  
  
|||  
|-|-|  
|<xref:System.Windows.Documents.Adorner>|<span data-ttu-id="5e326-118">Tüm somut donatıcı uygulamalarının devraldığı soyut temel sınıf.</span><span class="sxs-lookup"><span data-stu-id="5e326-118">An abstract base class from which all concrete adorner implementations inherit.</span></span>|  
|<xref:System.Windows.Documents.AdornerLayer>|<span data-ttu-id="5e326-119">Bir veya daha fazla donatılan öğenin donatıcı için işleme katmanını temsil eden bir sınıf.</span><span class="sxs-lookup"><span data-stu-id="5e326-119">A class representing a rendering layer for the adorner(s) of one or more adorned elements.</span></span>|  
|<xref:System.Windows.Documents.AdornerDecorator>|<span data-ttu-id="5e326-120">Bir donatıcı katmanının bir öğe koleksiyonuyla ilişkilendirilmesini sağlayan bir sınıf.</span><span class="sxs-lookup"><span data-stu-id="5e326-120">A class that enables an adorner layer to be associated with a collection of elements.</span></span>|  
  
<a name="implement_custom_Adorner"></a>   
## <a name="implementing-a-custom-adorner"></a><span data-ttu-id="5e326-121">Özel Donatıcı Uygulama</span><span class="sxs-lookup"><span data-stu-id="5e326-121">Implementing a Custom Adorner</span></span>  
 <span data-ttu-id="5e326-122">Tarafından [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] sunulan Donatıcılar çerçevesi öncelikle özel donatıcıları oluşturmayı desteklemek üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="5e326-122">The adorners framework provided by [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] is intended primarily to support the creation of custom adorners.</span></span> <span data-ttu-id="5e326-123">Özel bir donatıcı, soyut <xref:System.Windows.Documents.Adorner> sınıftan devralan bir sınıf uygulayarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="5e326-123">A custom adorner is created by implementing a class that inherits from the abstract <xref:System.Windows.Documents.Adorner> class.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5e326-124">Öğesinin üst <xref:System.Windows.Documents.Adorner> <xref:System.Windows.Documents.AdornerLayer> öğesi, donatılan öğeyi değil <xref:System.Windows.Documents.Adorner>öğesini işleyen öğesidir.</span><span class="sxs-lookup"><span data-stu-id="5e326-124">The parent of an <xref:System.Windows.Documents.Adorner> is the <xref:System.Windows.Documents.AdornerLayer> that renders the <xref:System.Windows.Documents.Adorner>, not the element being adorned.</span></span>  
  
 <span data-ttu-id="5e326-125">Aşağıdaki örnek, basit bir donatıcı uygulayan bir sınıfı gösterir.</span><span class="sxs-lookup"><span data-stu-id="5e326-125">The following example shows a class that implements a simple adorner.</span></span> <span data-ttu-id="5e326-126">Örnek donatıcı, bir çemberin köşelerini bir <xref:System.Windows.UIElement> daire içinde donatır.</span><span class="sxs-lookup"><span data-stu-id="5e326-126">The example adorner simply adorns the corners of a <xref:System.Windows.UIElement> with circles.</span></span>  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_simplecircleadornerbody)]
 [!code-vb[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_simplecircleadornerbody)]  
  
 <span data-ttu-id="5e326-127">Aşağıdaki görüntüde, öğesine <xref:System.Windows.Controls.TextBox>uygulanan SimpleCircleAdorner gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="5e326-127">The following image shows the SimpleCircleAdorner applied to a <xref:System.Windows.Controls.TextBox>.</span></span>  
  
 ![Donatılan metin kutusunu gösteren ekran görüntüsü.](./media/adorners-overview/simplecircleadorner-textbox.png)  
  
<a name="rendering_behavior_for_Adorners"></a>   
## <a name="rendering-behavior-for-adorners"></a><span data-ttu-id="5e326-129">Donatıcılar için işleme davranışı</span><span class="sxs-lookup"><span data-stu-id="5e326-129">Rendering Behavior for Adorners</span></span>  
 <span data-ttu-id="5e326-130">Donatıcıların herhangi bir devralınan işleme davranışı içermediğinden emin olmak önemlidir; bir donatıcının işleme, donatıcı uygulayıcının sorumluluğunda olmasını sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="5e326-130">It is important to note that adorners do not include any inherent rendering behavior; ensuring that an adorner renders is the responsibility of the adorner implementer.</span></span>   <span data-ttu-id="5e326-131">İşleme davranışını uygulamanın yaygın bir yolu, <xref:System.Windows.UIElement.OnRender%2A> yöntemi geçersiz kılmak ve bir veya daha fazla nesneyi, donatıcının gerektiğinde (Yukarıdaki örnekte gösterildiği gibi) işlemek için bir veya daha fazla <xref:System.Windows.Media.DrawingContext> nesne kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="5e326-131">A common way of implementing rendering behavior is to override the <xref:System.Windows.UIElement.OnRender%2A> method and use one or more <xref:System.Windows.Media.DrawingContext> objects to render the adorner's visuals as needed (as shown in the example above).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5e326-132">Donatıcı katmanına yerleştirilmiş herhangi bir şey, ayarlamış olduğunuz stillerin en üstünde işlenir.</span><span class="sxs-lookup"><span data-stu-id="5e326-132">Anything placed in the adorner layer is rendered on top of the rest of any styles you have set.</span></span> <span data-ttu-id="5e326-133">Diğer bir deyişle, Donatıcılar her zaman görsel olarak açıktır ve z sırası kullanılarak geçersiz kılınamaz.</span><span class="sxs-lookup"><span data-stu-id="5e326-133">In other words, adorners are always visually on top and cannot be overridden using z-order.</span></span>  
  
<a name="adorner_events_hittest"></a>   
## <a name="events-and-hit-testing"></a><span data-ttu-id="5e326-134">Olaylar ve Isabet testi</span><span class="sxs-lookup"><span data-stu-id="5e326-134">Events and Hit Testing</span></span>  
 <span data-ttu-id="5e326-135">Donatıcılar, tıpkı diğer <xref:System.Windows.FrameworkElement>gibi giriş olayları alır.</span><span class="sxs-lookup"><span data-stu-id="5e326-135">Adorners receive input events just like any other <xref:System.Windows.FrameworkElement>.</span></span>  <span data-ttu-id="5e326-136">Bir donatıcı her zaman, donatıladığı öğeden daha yüksek bir z düzeninde olduğundan, donatıcı, temel alınan donatılan öğeye yönelik olarak <xref:System.Windows.UIElement.Drop> giriş olayları (veya <xref:System.Windows.UIElement.MouseMove>gibi) alır.</span><span class="sxs-lookup"><span data-stu-id="5e326-136">Because an adorner always has a higher z-order than the element it adorns, the adorner receives input events (such as <xref:System.Windows.UIElement.Drop> or <xref:System.Windows.UIElement.MouseMove>) that may be intended for the underlying adorned element.</span></span>  <span data-ttu-id="5e326-137">Bir donatıcı, belirli giriş olaylarını dinleyebilir ve olayı yeniden oluşturarak bunları temel donatılan öğeye geçirebilir.</span><span class="sxs-lookup"><span data-stu-id="5e326-137">An adorner can listen for certain input events and pass these on to the underlying adorned element by re-raising the event.</span></span>  
  
 <span data-ttu-id="5e326-138">Bir donatıcı kapsamındaki öğelerin doğrudan isabet sınamasını etkinleştirmek için, donatıcı üzerinde isabet testi <xref:System.Windows.UIElement.IsHitTestVisible%2A> özelliğini **false** olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="5e326-138">To enable pass-through hit testing of elements under an adorner, set the hit test <xref:System.Windows.UIElement.IsHitTestVisible%2A> property to **false** on the adorner.</span></span>  <span data-ttu-id="5e326-139">İsabet testi hakkında daha fazla bilgi için bkz.</span><span class="sxs-lookup"><span data-stu-id="5e326-139">For more information about hit testing, see</span></span>  
  
 <span data-ttu-id="5e326-140">[Görsel katmandaki Isabet testi](../graphics-multimedia/hit-testing-in-the-visual-layer.md).</span><span class="sxs-lookup"><span data-stu-id="5e326-140">[Hit Testing in the Visual Layer](../graphics-multimedia/hit-testing-in-the-visual-layer.md).</span></span>  
  
<a name="adorn_single_element"></a>   
## <a name="adorning-a-single-uielement"></a><span data-ttu-id="5e326-141">Tek bir UIElement 'i donatma</span><span class="sxs-lookup"><span data-stu-id="5e326-141">Adorning a Single UIElement</span></span>  
 <span data-ttu-id="5e326-142">Bir donatıcıyı belirli <xref:System.Windows.UIElement>bir nesneye bağlamak için şu adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="5e326-142">To bind an adorner to a particular <xref:System.Windows.UIElement>, follow these steps:</span></span>  
  
1. <span data-ttu-id="5e326-143">' Nin donatılacak <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> bir <xref:System.Windows.Documents.AdornerLayer> nesne <xref:System.Windows.UIElement> almak için static yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="5e326-143">Call the static method <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> to get an <xref:System.Windows.Documents.AdornerLayer> object for the <xref:System.Windows.UIElement> to be adorned.</span></span> <span data-ttu-id="5e326-144"><xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A>görsel ağacı, belirtilen <xref:System.Windows.UIElement>' dan başlayarak ve bulduğu ilk donatıcı katmanını döndürür.</span><span class="sxs-lookup"><span data-stu-id="5e326-144"><xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> walks up the visual tree, starting at the specified <xref:System.Windows.UIElement>, and returns the first adorner layer it finds.</span></span> <span data-ttu-id="5e326-145">(Bir donatıcı katmanı bulunmazsa, yöntem null döndürür.)</span><span class="sxs-lookup"><span data-stu-id="5e326-145">(If no adorner layers are found, the method returns null.)</span></span>  
  
2. <span data-ttu-id="5e326-146">Donatıcıyı hedefe <xref:System.Windows.UIElement>bağlamak için yönteminiçağırın.<xref:System.Windows.Documents.AdornerLayer.Add%2A></span><span class="sxs-lookup"><span data-stu-id="5e326-146">Call the <xref:System.Windows.Documents.AdornerLayer.Add%2A> method to bind the adorner to the target <xref:System.Windows.UIElement>.</span></span>  
  
 <span data-ttu-id="5e326-147">Aşağıdaki örnek, bir SimpleCircleAdorner 'ı (yukarıda gösterilen) adlandırılmış bir <xref:System.Windows.Controls.TextBox> *myTextBox*öğesine bağlar.</span><span class="sxs-lookup"><span data-stu-id="5e326-147">The following example binds a SimpleCircleAdorner (shown above) to a <xref:System.Windows.Controls.TextBox> named *myTextBox*.</span></span>  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornsingleelement)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornsingleelement)]  
  
> [!NOTE]
> <span data-ttu-id="5e326-148">Bir [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] donatıcıyı başka bir öğeye bağlamak için kullanılması şu anda desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="5e326-148">Using [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] to bind an adorner to another element is currently not supported.</span></span>  
  
<a name="adorn_children_panel"></a>   
## <a name="adorning-the-children-of-a-panel"></a><span data-ttu-id="5e326-149">Panelin alt öğelerini donatma</span><span class="sxs-lookup"><span data-stu-id="5e326-149">Adorning the Children of a Panel</span></span>  
 <span data-ttu-id="5e326-150">Bir donatıcıyı a <xref:System.Windows.Controls.Panel>'nın alt öğelerine bağlamak için şu adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="5e326-150">To bind an adorner to the children of a <xref:System.Windows.Controls.Panel>, follow these steps:</span></span>  
  
1. <span data-ttu-id="5e326-151">Alt öğeleri donatılacak olan öğe için bir donatıcı katmanı bulmak için <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> yönteminiçağırın.`static`</span><span class="sxs-lookup"><span data-stu-id="5e326-151">Call the `static` method <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> to find an adorner layer for the element whose children are to be adorned.</span></span>  
  
2. <span data-ttu-id="5e326-152">Üst öğenin alt öğelerini numaralandırın ve her bir alt öğeye bir <xref:System.Windows.Documents.AdornerLayer.Add%2A> donatıcı bağlamak için yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="5e326-152">Enumerate through the children of the parent element and call the <xref:System.Windows.Documents.AdornerLayer.Add%2A> method to bind an adorner to each child element.</span></span>  
  
 <span data-ttu-id="5e326-153">Aşağıdaki örnek bir SimpleCircleAdorner (yukarıda gösterilen) <xref:System.Windows.Controls.StackPanel> adlı bir *myStackPanel*alt öğesine bağlar.</span><span class="sxs-lookup"><span data-stu-id="5e326-153">The following example binds a SimpleCircleAdorner (shown above) to the children of a <xref:System.Windows.Controls.StackPanel> named *myStackPanel*.</span></span>  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornChildren](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornchildren)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornChildren](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornchildren)]  
  
## <a name="see-also"></a><span data-ttu-id="5e326-154">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5e326-154">See also</span></span>

- <xref:System.Windows.Media.AdornerHitTestResult>
- [<span data-ttu-id="5e326-155">WPF’de Şekiller ve Temel Çizimlere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="5e326-155">Shapes and Basic Drawing in WPF Overview</span></span>](../graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)
- [<span data-ttu-id="5e326-156">Görüntüler, Çizimler ve Görsellerle Boyama</span><span class="sxs-lookup"><span data-stu-id="5e326-156">Painting with Images, Drawings, and Visuals</span></span>](../graphics-multimedia/painting-with-images-drawings-and-visuals.md)
- [<span data-ttu-id="5e326-157">Çizim Nesnelerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="5e326-157">Drawing Objects Overview</span></span>](../graphics-multimedia/drawing-objects-overview.md)
- [<span data-ttu-id="5e326-158">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="5e326-158">How-to Topics</span></span>](adorners-how-to-topics.md)
