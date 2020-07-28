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
# <a name="adorners-overview"></a><span data-ttu-id="83e56-103">Donatıcılara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="83e56-103">Adorners Overview</span></span>

<span data-ttu-id="83e56-104">Donatıcılar <xref:System.Windows.FrameworkElement> , bir kullanıcıya görsel ipuçları sağlamak için kullanılan özel bir türüdür.</span><span class="sxs-lookup"><span data-stu-id="83e56-104">Adorners are a special type of <xref:System.Windows.FrameworkElement>, used to provide visual cues to a user.</span></span> <span data-ttu-id="83e56-105">Diğer kullanımlar arasında, Donatıcılar, öğelere işlevsel işleyiciler eklemek veya bir denetimle ilgili durum bilgilerini sağlamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="83e56-105">Among other uses, Adorners can be used to add functional handles to elements or provide state information about a control.</span></span>

## <a name="about-adorners"></a><span data-ttu-id="83e56-106">Donatıcılar hakkında</span><span class="sxs-lookup"><span data-stu-id="83e56-106">About Adorners</span></span>

<span data-ttu-id="83e56-107"><xref:System.Windows.Documents.Adorner>, <xref:System.Windows.FrameworkElement> Bir öğesine bağlanan özel bir <xref:System.Windows.UIElement> .</span><span class="sxs-lookup"><span data-stu-id="83e56-107">An <xref:System.Windows.Documents.Adorner> is a custom <xref:System.Windows.FrameworkElement> that is bound to a <xref:System.Windows.UIElement>.</span></span> <span data-ttu-id="83e56-108">Donatıcılar <xref:System.Windows.Documents.AdornerLayer> , her zaman donatılan veya donatılan bir öğe koleksiyonu olan bir işleme yüzeyi olan bir üzerinde işlenir.</span><span class="sxs-lookup"><span data-stu-id="83e56-108">Adorners are rendered in an <xref:System.Windows.Documents.AdornerLayer>, which is a rendering surface that is always on top of the adorned element or a collection of adorned elements.</span></span> <span data-ttu-id="83e56-109">Donatıcının işlenmesi, donatıcının bağlandığı öğenin işlenmesinin bağımsızdır <xref:System.Windows.UIElement> .</span><span class="sxs-lookup"><span data-stu-id="83e56-109">Rendering of an adorner is independent from rendering of the <xref:System.Windows.UIElement> that the adorner is bound to.</span></span> <span data-ttu-id="83e56-110">Bir donatıcı genellikle, ilişkili olduğu öğeye göre konumlandırılır ve donatılan öğenin sol üst kısmında bulunan standart 2B koordinat başlangıcını kullanarak konumlandırılır.</span><span class="sxs-lookup"><span data-stu-id="83e56-110">An adorner is typically positioned relative to the element to which it is bound, using the standard 2D coordinate origin located at the upper-left of the adorned element.</span></span>

<span data-ttu-id="83e56-111">Donatıcılar için ortak uygulamalar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="83e56-111">Common applications for adorners include:</span></span>

- <span data-ttu-id="83e56-112">Bir <xref:System.Windows.UIElement> kullanıcının öğeyi bir şekilde (yeniden boyutlandırma, döndürme, yeniden konumlandırma, vb.) işlemesini sağlayan bir öğesine işlevsel işleyiciler ekleme.</span><span class="sxs-lookup"><span data-stu-id="83e56-112">Adding functional handles to a <xref:System.Windows.UIElement> that enable a user to manipulate the element in some way (resize, rotate, reposition, etc.).</span></span>
- <span data-ttu-id="83e56-113">Çeşitli durumları veya çeşitli olaylara yanıt olarak göstermek için görsel geri bildirim sağlayın.</span><span class="sxs-lookup"><span data-stu-id="83e56-113">Provide visual feedback to indicate various states, or in response to various events.</span></span>
- <span data-ttu-id="83e56-114">Görsel süslemeleri bir üzerinde kaplama <xref:System.Windows.UIElement> .</span><span class="sxs-lookup"><span data-stu-id="83e56-114">Overlay visual decorations on a <xref:System.Windows.UIElement>.</span></span>
- <span data-ttu-id="83e56-115">Bir kısmını veya tümünü görsel olarak maskesini veya geçersiz kılın <xref:System.Windows.UIElement> .</span><span class="sxs-lookup"><span data-stu-id="83e56-115">Visually mask or override part or all of a <xref:System.Windows.UIElement>.</span></span>

[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]<span data-ttu-id="83e56-116">görsel öğeleri donatma için temel bir çerçeve sağlar.</span><span class="sxs-lookup"><span data-stu-id="83e56-116">provides a basic framework for adorning visual elements.</span></span> <span data-ttu-id="83e56-117">Aşağıdaki tabloda, nesneleri donatma ve amaçlarına göre kullanılan birincil türler listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="83e56-117">The following table lists the primary types used when adorning objects, and their purpose.</span></span> <span data-ttu-id="83e56-118">Birçok kullanım örneği aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="83e56-118">Several usage examples follow:</span></span>

|||
|-|-|
|<xref:System.Windows.Documents.Adorner>|<span data-ttu-id="83e56-119">Tüm somut donatıcı uygulamalarının devraldığı soyut temel sınıf.</span><span class="sxs-lookup"><span data-stu-id="83e56-119">An abstract base class from which all concrete adorner implementations inherit.</span></span>|
|<xref:System.Windows.Documents.AdornerLayer>|<span data-ttu-id="83e56-120">Bir veya daha fazla donatılan öğenin donatıcı için işleme katmanını temsil eden bir sınıf.</span><span class="sxs-lookup"><span data-stu-id="83e56-120">A class representing a rendering layer for the adorner(s) of one or more adorned elements.</span></span>|
|<xref:System.Windows.Documents.AdornerDecorator>|<span data-ttu-id="83e56-121">Bir donatıcı katmanının bir öğe koleksiyonuyla ilişkilendirilmesini sağlayan bir sınıf.</span><span class="sxs-lookup"><span data-stu-id="83e56-121">A class that enables an adorner layer to be associated with a collection of elements.</span></span>|

## <a name="implementing-a-custom-adorner"></a><span data-ttu-id="83e56-122">Özel Donatıcı Uygulama</span><span class="sxs-lookup"><span data-stu-id="83e56-122">Implementing a Custom Adorner</span></span>

<span data-ttu-id="83e56-123">Tarafından sunulan Donatıcılar çerçevesi [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] öncelikle özel donatıcıları oluşturmayı desteklemek üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="83e56-123">The adorners framework provided by [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] is intended primarily to support the creation of custom adorners.</span></span> <span data-ttu-id="83e56-124">Özel bir donatıcı, soyut sınıftan devralan bir sınıf uygulayarak oluşturulur <xref:System.Windows.Documents.Adorner> .</span><span class="sxs-lookup"><span data-stu-id="83e56-124">A custom adorner is created by implementing a class that inherits from the abstract <xref:System.Windows.Documents.Adorner> class.</span></span>

> [!NOTE]
> <span data-ttu-id="83e56-125">Öğesinin üst öğesi, <xref:System.Windows.Documents.Adorner> <xref:System.Windows.Documents.AdornerLayer> <xref:System.Windows.Documents.Adorner> donatılan öğeyi değil öğesini işleyen öğesidir.</span><span class="sxs-lookup"><span data-stu-id="83e56-125">The parent of an <xref:System.Windows.Documents.Adorner> is the <xref:System.Windows.Documents.AdornerLayer> that renders the <xref:System.Windows.Documents.Adorner>, not the element being adorned.</span></span>

<span data-ttu-id="83e56-126">Aşağıdaki örnek, basit bir donatıcı uygulayan bir sınıfı gösterir.</span><span class="sxs-lookup"><span data-stu-id="83e56-126">The following example shows a class that implements a simple adorner.</span></span> <span data-ttu-id="83e56-127">Örnek donatıcı, bir çemberin köşelerini bir daire içinde donatır <xref:System.Windows.UIElement> .</span><span class="sxs-lookup"><span data-stu-id="83e56-127">The example adorner simply adorns the corners of a <xref:System.Windows.UIElement> with circles.</span></span>

[!code-csharp[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_simplecircleadornerbody)]
[!code-vb[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_simplecircleadornerbody)]
  
<span data-ttu-id="83e56-128">Aşağıdaki görüntüde, öğesine uygulanan SimpleCircleAdorner gösterilmektedir <xref:System.Windows.Controls.TextBox> :</span><span class="sxs-lookup"><span data-stu-id="83e56-128">The following image shows the SimpleCircleAdorner applied to a <xref:System.Windows.Controls.TextBox>:</span></span>

![Donatılan metin kutusunu gösteren ekran görüntüsü.](./media/adorners-overview/simplecircleadorner-textbox.png)

## <a name="rendering-behavior-for-adorners"></a><span data-ttu-id="83e56-130">Donatıcılar için işleme davranışı</span><span class="sxs-lookup"><span data-stu-id="83e56-130">Rendering Behavior for Adorners</span></span>

<span data-ttu-id="83e56-131">Donatıcıların herhangi bir devralınan işleme davranışı içermediğinden emin olmak önemlidir; bir donatıcının işleme, donatıcı uygulayıcının sorumluluğunda olmasını sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="83e56-131">It is important to note that adorners do not include any inherent rendering behavior; ensuring that an adorner renders is the responsibility of the adorner implementer.</span></span> <span data-ttu-id="83e56-132">İşleme davranışını uygulamanın yaygın bir yolu, yöntemi geçersiz kılmak <xref:System.Windows.UIElement.OnRender%2A> ve bir veya daha fazla <xref:System.Windows.Media.DrawingContext> nesneyi, donatıcının gerektiğinde (Yukarıdaki örnekte gösterildiği gibi) işlemek için bir veya daha fazla nesne kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="83e56-132">A common way of implementing rendering behavior is to override the <xref:System.Windows.UIElement.OnRender%2A> method and use one or more <xref:System.Windows.Media.DrawingContext> objects to render the adorner's visuals as needed (as shown in the example above).</span></span>

> [!NOTE]
> <span data-ttu-id="83e56-133">Donatıcı katmanına yerleştirilmiş herhangi bir şey, ayarlamış olduğunuz stillerin en üstünde işlenir.</span><span class="sxs-lookup"><span data-stu-id="83e56-133">Anything placed in the adorner layer is rendered on top of the rest of any styles you have set.</span></span> <span data-ttu-id="83e56-134">Diğer bir deyişle, Donatıcılar her zaman görsel olarak açıktır ve z sırası kullanılarak geçersiz kılınamaz.</span><span class="sxs-lookup"><span data-stu-id="83e56-134">In other words, adorners are always visually on top and cannot be overridden using z-order.</span></span>

## <a name="events-and-hit-testing"></a><span data-ttu-id="83e56-135">Olaylar ve Isabet testi</span><span class="sxs-lookup"><span data-stu-id="83e56-135">Events and Hit Testing</span></span>

<span data-ttu-id="83e56-136">Donatıcılar, tıpkı diğer gibi giriş olayları alır <xref:System.Windows.FrameworkElement> .</span><span class="sxs-lookup"><span data-stu-id="83e56-136">Adorners receive input events just like any other <xref:System.Windows.FrameworkElement>.</span></span>  <span data-ttu-id="83e56-137">Bir donatıcı her zaman, donatıladığı öğeden daha yüksek bir z düzeninde olduğundan, donatıcı, <xref:System.Windows.UIElement.Drop> <xref:System.Windows.UIElement.MouseMove> temel alınan donatılan öğeye yönelik olarak giriş olayları (veya gibi) alır.</span><span class="sxs-lookup"><span data-stu-id="83e56-137">Because an adorner always has a higher z-order than the element it adorns, the adorner receives input events (such as <xref:System.Windows.UIElement.Drop> or <xref:System.Windows.UIElement.MouseMove>) that may be intended for the underlying adorned element.</span></span>  <span data-ttu-id="83e56-138">Bir donatıcı, belirli giriş olaylarını dinleyebilir ve olayı yeniden oluşturarak bunları temel donatılan öğeye geçirebilir.</span><span class="sxs-lookup"><span data-stu-id="83e56-138">An adorner can listen for certain input events and pass these on to the underlying adorned element by re-raising the event.</span></span>

<span data-ttu-id="83e56-139">Bir donatıcı kapsamındaki öğelerin doğrudan isabet sınamasını etkinleştirmek için, <xref:System.Windows.UIElement.IsHitTestVisible%2A> donatıcı üzerinde isabet testi özelliğini **false** olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="83e56-139">To enable pass-through hit testing of elements under an adorner, set the hit test <xref:System.Windows.UIElement.IsHitTestVisible%2A> property to **false** on the adorner.</span></span>  <span data-ttu-id="83e56-140">İsabet testi hakkında daha fazla bilgi için bkz. [görsel katmandaki Isabet testi](../graphics-multimedia/hit-testing-in-the-visual-layer.md).</span><span class="sxs-lookup"><span data-stu-id="83e56-140">For more information about hit testing, see [Hit Testing in the Visual Layer](../graphics-multimedia/hit-testing-in-the-visual-layer.md).</span></span>

## <a name="adorning-a-single-uielement"></a><span data-ttu-id="83e56-141">Tek bir UIElement 'i donatma</span><span class="sxs-lookup"><span data-stu-id="83e56-141">Adorning a Single UIElement</span></span>

<span data-ttu-id="83e56-142">Bir donatıcıyı belirli bir nesneye bağlamak için <xref:System.Windows.UIElement> şu adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="83e56-142">To bind an adorner to a particular <xref:System.Windows.UIElement>, follow these steps:</span></span>

1. <span data-ttu-id="83e56-143">' Nin <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> donatılacak bir nesne almak için static yöntemi çağırın <xref:System.Windows.Documents.AdornerLayer> <xref:System.Windows.UIElement> .</span><span class="sxs-lookup"><span data-stu-id="83e56-143">Call the static method <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> to get an <xref:System.Windows.Documents.AdornerLayer> object for the <xref:System.Windows.UIElement> to be adorned.</span></span> <span data-ttu-id="83e56-144"><xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A>görsel ağacı, belirtilen ' dan başlayarak <xref:System.Windows.UIElement> ve bulduğu ilk donatıcı katmanını döndürür.</span><span class="sxs-lookup"><span data-stu-id="83e56-144"><xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> walks up the visual tree, starting at the specified <xref:System.Windows.UIElement>, and returns the first adorner layer it finds.</span></span> <span data-ttu-id="83e56-145">(Bir donatıcı katmanı bulunmazsa, yöntem null döndürür.)</span><span class="sxs-lookup"><span data-stu-id="83e56-145">(If no adorner layers are found, the method returns null.)</span></span>

2. <span data-ttu-id="83e56-146"><xref:System.Windows.Documents.AdornerLayer.Add%2A>Donatıcıyı hedefe bağlamak için yöntemini çağırın <xref:System.Windows.UIElement> .</span><span class="sxs-lookup"><span data-stu-id="83e56-146">Call the <xref:System.Windows.Documents.AdornerLayer.Add%2A> method to bind the adorner to the target <xref:System.Windows.UIElement>.</span></span>

 <span data-ttu-id="83e56-147">Aşağıdaki örnek bir SimpleCircleAdorner 'ı (yukarıda gösterilen) <xref:System.Windows.Controls.TextBox> adlandırılmış bir *myTextBox*'a bağlar:</span><span class="sxs-lookup"><span data-stu-id="83e56-147">The following example binds a SimpleCircleAdorner (shown above) to a <xref:System.Windows.Controls.TextBox> named *myTextBox*:</span></span>

 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornsingleelement)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornsingleelement)]

> [!NOTE]
> <span data-ttu-id="83e56-148">Bir [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] donatıcıyı başka bir öğeye bağlamak için kullanılması şu anda desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="83e56-148">Using [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] to bind an adorner to another element is currently not supported.</span></span>

## <a name="adorning-the-children-of-a-panel"></a><span data-ttu-id="83e56-149">Panelin alt öğelerini donatma</span><span class="sxs-lookup"><span data-stu-id="83e56-149">Adorning the Children of a Panel</span></span>

<span data-ttu-id="83e56-150">Bir donatıcıyı a 'nın alt öğelerine bağlamak için <xref:System.Windows.Controls.Panel> şu adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="83e56-150">To bind an adorner to the children of a <xref:System.Windows.Controls.Panel>, follow these steps:</span></span>

1. <span data-ttu-id="83e56-151">`static` <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> Alt öğeleri donatılacak olan öğe için bir donatıcı katmanı bulmak için yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="83e56-151">Call the `static` method <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> to find an adorner layer for the element whose children are to be adorned.</span></span>

2. <span data-ttu-id="83e56-152">Üst öğenin alt öğelerini numaralandırın ve <xref:System.Windows.Documents.AdornerLayer.Add%2A> her bir alt öğeye bir donatıcı bağlamak için yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="83e56-152">Enumerate through the children of the parent element and call the <xref:System.Windows.Documents.AdornerLayer.Add%2A> method to bind an adorner to each child element.</span></span>

<span data-ttu-id="83e56-153">Aşağıdaki örnek bir SimpleCircleAdorner (yukarıda gösterilen) <xref:System.Windows.Controls.StackPanel> adlı bir *myStackPanel*alt öğesine bağlar:</span><span class="sxs-lookup"><span data-stu-id="83e56-153">The following example binds a SimpleCircleAdorner (shown above) to the children of a <xref:System.Windows.Controls.StackPanel> named *myStackPanel*:</span></span>

[!code-csharp[Adorners_SimpleCircleAdorner#_AdornChildren](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornchildren)]
[!code-vb[Adorners_SimpleCircleAdorner#_AdornChildren](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornchildren)]

## <a name="see-also"></a><span data-ttu-id="83e56-154">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="83e56-154">See also</span></span>

- <xref:System.Windows.Media.AdornerHitTestResult>
- [<span data-ttu-id="83e56-155">WPF Genel Bakışı İçinde Şekiller ve Temel Çizimler</span><span class="sxs-lookup"><span data-stu-id="83e56-155">Shapes and Basic Drawing in WPF Overview</span></span>](../graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)
- [<span data-ttu-id="83e56-156">Görüntüler, Çizimler ve Görsellerle Boyama</span><span class="sxs-lookup"><span data-stu-id="83e56-156">Painting with Images, Drawings, and Visuals</span></span>](../graphics-multimedia/painting-with-images-drawings-and-visuals.md)
- [<span data-ttu-id="83e56-157">Çizim Nesnelerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="83e56-157">Drawing Objects Overview</span></span>](../graphics-multimedia/drawing-objects-overview.md)
- [<span data-ttu-id="83e56-158">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="83e56-158">How-to Topics</span></span>](adorners-how-to-topics.md)
