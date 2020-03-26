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
# <a name="adorners-overview"></a><span data-ttu-id="46280-102">Donatıcılara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="46280-102">Adorners Overview</span></span>

<span data-ttu-id="46280-103">Süsleri özel bir <xref:System.Windows.FrameworkElement>türüdür, bir kullanıcıya görsel ipuçları sağlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="46280-103">Adorners are a special type of <xref:System.Windows.FrameworkElement>, used to provide visual cues to a user.</span></span> <span data-ttu-id="46280-104">Diğer kullanımların yanı sıra, Süsleyiciler öğelere işlevsel tutamaçları eklemek veya denetim hakkında durum bilgileri sağlamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="46280-104">Among other uses, Adorners can be used to add functional handles to elements or provide state information about a control.</span></span>

## <a name="about-adorners"></a><span data-ttu-id="46280-105">Adorners Hakkında</span><span class="sxs-lookup"><span data-stu-id="46280-105">About Adorners</span></span>

<span data-ttu-id="46280-106">Bir' <xref:System.Windows.Documents.Adorner> e <xref:System.Windows.FrameworkElement> bağlı bir <xref:System.Windows.UIElement>gelenektir.</span><span class="sxs-lookup"><span data-stu-id="46280-106">An <xref:System.Windows.Documents.Adorner> is a custom <xref:System.Windows.FrameworkElement> that is bound to a <xref:System.Windows.UIElement>.</span></span> <span data-ttu-id="46280-107">Süsleyiciler, <xref:System.Windows.Documents.AdornerLayer>her zaman süslenmiş elementin veya süslenmiş öğelerin bir koleksiyonunun üzerinde bulunan bir işleme yüzeyi olarak işlenir.</span><span class="sxs-lookup"><span data-stu-id="46280-107">Adorners are rendered in an <xref:System.Windows.Documents.AdornerLayer>, which is a rendering surface that is always on top of the adorned element or a collection of adorned elements.</span></span> <span data-ttu-id="46280-108">Bir süsleyicinin işlenmesi, süsleyicinin <xref:System.Windows.UIElement> bağlı olduğu şeyin işlenmesinden bağımsızdır.</span><span class="sxs-lookup"><span data-stu-id="46280-108">Rendering of an adorner is independent from rendering of the <xref:System.Windows.UIElement> that the adorner is bound to.</span></span> <span data-ttu-id="46280-109">Bir süsleyici genellikle, süslenmiş öğenin üst-sol kısmında bulunan standart 2B koordinat kökeni kullanılarak bağlı olduğu elemana göre konumlandırılır.</span><span class="sxs-lookup"><span data-stu-id="46280-109">An adorner is typically positioned relative to the element to which it is bound, using the standard 2D coordinate origin located at the upper-left of the adorned element.</span></span>

<span data-ttu-id="46280-110">Süsleyiciler için ortak uygulamalar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="46280-110">Common applications for adorners include:</span></span>

- <span data-ttu-id="46280-111">Bir kullanıcının öğeyi bir şekilde işlemesini sağlayan bir <xref:System.Windows.UIElement> işleme işletti (yeniden boyutlandırma, döndürme, yeniden konumlandırma, vb.) işlevsel tutamaçları ekleme.</span><span class="sxs-lookup"><span data-stu-id="46280-111">Adding functional handles to a <xref:System.Windows.UIElement> that enable a user to manipulate the element in some way (resize, rotate, reposition, etc.).</span></span>
- <span data-ttu-id="46280-112">Çeşitli durumları belirtmek veya çeşitli olaylara yanıt olarak görsel geri bildirim sağlayın.</span><span class="sxs-lookup"><span data-stu-id="46280-112">Provide visual feedback to indicate various states, or in response to various events.</span></span>
- <span data-ttu-id="46280-113">Bir üzerinde bindirme <xref:System.Windows.UIElement>görsel süslemeleri .</span><span class="sxs-lookup"><span data-stu-id="46280-113">Overlay visual decorations on a <xref:System.Windows.UIElement>.</span></span>
- <span data-ttu-id="46280-114">Görsel olarak maske veya bir kısmını <xref:System.Windows.UIElement>veya tamamını geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="46280-114">Visually mask or override part or all of a <xref:System.Windows.UIElement>.</span></span>

[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]<span data-ttu-id="46280-115">görsel öğeleri süslemek için temel bir çerçeve sağlar.</span><span class="sxs-lookup"><span data-stu-id="46280-115">provides a basic framework for adorning visual elements.</span></span> <span data-ttu-id="46280-116">Aşağıdaki tabloda nesneleri süslerken kullanılan birincil türleri ve bunların amacı listelenerilmiştir.</span><span class="sxs-lookup"><span data-stu-id="46280-116">The following table lists the primary types used when adorning objects, and their purpose.</span></span> <span data-ttu-id="46280-117">Çeşitli kullanım örnekleri aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="46280-117">Several usage examples follow:</span></span>

|||
|-|-|
|<xref:System.Windows.Documents.Adorner>|<span data-ttu-id="46280-118">Tüm somut süsleyici uygulamalarının devraldığı soyut bir taban sınıfı.</span><span class="sxs-lookup"><span data-stu-id="46280-118">An abstract base class from which all concrete adorner implementations inherit.</span></span>|
|<xref:System.Windows.Documents.AdornerLayer>|<span data-ttu-id="46280-119">Bir veya daha fazla süslü öğenin süsleyicisi(ler) için bir işleme katmanını temsil eden bir sınıf.</span><span class="sxs-lookup"><span data-stu-id="46280-119">A class representing a rendering layer for the adorner(s) of one or more adorned elements.</span></span>|
|<xref:System.Windows.Documents.AdornerDecorator>|<span data-ttu-id="46280-120">Bir süsleyici katmanının öğeler topluluğuyla ilişkilendirilmesini sağlayan bir sınıf.</span><span class="sxs-lookup"><span data-stu-id="46280-120">A class that enables an adorner layer to be associated with a collection of elements.</span></span>|

## <a name="implementing-a-custom-adorner"></a><span data-ttu-id="46280-121">Özel Süsleyici Uygulama</span><span class="sxs-lookup"><span data-stu-id="46280-121">Implementing a Custom Adorner</span></span>

<span data-ttu-id="46280-122">Tarafından [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] sağlanan süsleyiciler çerçevesi öncelikle özel süsleyiciler oluşturulmasını desteklemek için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="46280-122">The adorners framework provided by [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] is intended primarily to support the creation of custom adorners.</span></span> <span data-ttu-id="46280-123">Soyut <xref:System.Windows.Documents.Adorner> sınıftan devralan bir sınıf uygulanarak özel bir süsleyici oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="46280-123">A custom adorner is created by implementing a class that inherits from the abstract <xref:System.Windows.Documents.Adorner> class.</span></span>

> [!NOTE]
> <span data-ttu-id="46280-124">Bir'in <xref:System.Windows.Documents.Adorner> üst <xref:System.Windows.Documents.AdornerLayer> öğesi, süslenen öğeyi <xref:System.Windows.Documents.Adorner>değil, öğeyi işleyendir.</span><span class="sxs-lookup"><span data-stu-id="46280-124">The parent of an <xref:System.Windows.Documents.Adorner> is the <xref:System.Windows.Documents.AdornerLayer> that renders the <xref:System.Windows.Documents.Adorner>, not the element being adorned.</span></span>

<span data-ttu-id="46280-125">Aşağıdaki örnek, basit bir süsleyici uygulayan bir sınıf gösterir.</span><span class="sxs-lookup"><span data-stu-id="46280-125">The following example shows a class that implements a simple adorner.</span></span> <span data-ttu-id="46280-126">Örnek süsleyici sadece daireler ile <xref:System.Windows.UIElement> bir köşeleri süslüyor.</span><span class="sxs-lookup"><span data-stu-id="46280-126">The example adorner simply adorns the corners of a <xref:System.Windows.UIElement> with circles.</span></span>

[!code-csharp[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_simplecircleadornerbody)]
[!code-vb[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_simplecircleadornerbody)]
  
<span data-ttu-id="46280-127">Aşağıdaki resim simplecircleadorner uygulanan gösterir: <xref:System.Windows.Controls.TextBox></span><span class="sxs-lookup"><span data-stu-id="46280-127">The following image shows the SimpleCircleAdorner applied to a <xref:System.Windows.Controls.TextBox>:</span></span>

![Süslü bir metin kutusunu gösteren ekran görüntüsü.](./media/adorners-overview/simplecircleadorner-textbox.png)

## <a name="rendering-behavior-for-adorners"></a><span data-ttu-id="46280-129">Süsleyiciler için Rendering Davranış</span><span class="sxs-lookup"><span data-stu-id="46280-129">Rendering Behavior for Adorners</span></span>

<span data-ttu-id="46280-130">Bu süsleyiciler herhangi bir doğal render davranışı içermez dikkat etmek önemlidir; bir süsleyicinin işlemesini sağlamak, süsleyici uygulayıcının sorumluluğundadır.</span><span class="sxs-lookup"><span data-stu-id="46280-130">It is important to note that adorners do not include any inherent rendering behavior; ensuring that an adorner renders is the responsibility of the adorner implementer.</span></span> <span data-ttu-id="46280-131">Oluşturma davranışı uygulamanın yaygın bir yolu <xref:System.Windows.UIElement.OnRender%2A> yöntemi geçersiz kılmak ve <xref:System.Windows.Media.DrawingContext> bir veya daha fazla nesne kullanarak süsleyicinin görsellerini gerektiği gibi işlemektir (yukarıdaki örnekte gösterildiği gibi).</span><span class="sxs-lookup"><span data-stu-id="46280-131">A common way of implementing rendering behavior is to override the <xref:System.Windows.UIElement.OnRender%2A> method and use one or more <xref:System.Windows.Media.DrawingContext> objects to render the adorner's visuals as needed (as shown in the example above).</span></span>

> [!NOTE]
> <span data-ttu-id="46280-132">Süsleyici katmanına yerleştirilen her şey, ayarladığınız stillerin geri kalanının üzerine işlenir.</span><span class="sxs-lookup"><span data-stu-id="46280-132">Anything placed in the adorner layer is rendered on top of the rest of any styles you have set.</span></span> <span data-ttu-id="46280-133">Başka bir deyişle, süsleyiciler her zaman görsel olarak üsttedir ve z-order kullanılarak geçersiz kılınamaz.</span><span class="sxs-lookup"><span data-stu-id="46280-133">In other words, adorners are always visually on top and cannot be overridden using z-order.</span></span>

## <a name="events-and-hit-testing"></a><span data-ttu-id="46280-134">Olaylar ve Hit Test</span><span class="sxs-lookup"><span data-stu-id="46280-134">Events and Hit Testing</span></span>

<span data-ttu-id="46280-135">Süsleri diğer gibi <xref:System.Windows.FrameworkElement>giriş olayları alırsınız.</span><span class="sxs-lookup"><span data-stu-id="46280-135">Adorners receive input events just like any other <xref:System.Windows.FrameworkElement>.</span></span>  <span data-ttu-id="46280-136">Bir süsleyici nin her zaman süslediği öğeden daha yüksek bir z sırası olduğundan, süsleyici, temel süslenmiş öğe için tasarlanmış olabilecek giriş olayları (örneğin <xref:System.Windows.UIElement.Drop> veya) <xref:System.Windows.UIElement.MouseMove>alır.</span><span class="sxs-lookup"><span data-stu-id="46280-136">Because an adorner always has a higher z-order than the element it adorns, the adorner receives input events (such as <xref:System.Windows.UIElement.Drop> or <xref:System.Windows.UIElement.MouseMove>) that may be intended for the underlying adorned element.</span></span>  <span data-ttu-id="46280-137">Bir süsleyici belirli giriş olaylarını dinleyebilir ve bunları olayı yeniden yükselterek temel süslenmiş öğeye aktarabilir.</span><span class="sxs-lookup"><span data-stu-id="46280-137">An adorner can listen for certain input events and pass these on to the underlying adorned element by re-raising the event.</span></span>

<span data-ttu-id="46280-138">Bir süsleyici altında elemanların geçiş isabet testi sağlamak <xref:System.Windows.UIElement.IsHitTestVisible%2A> için, adorner **üzerinde yanlış** isabet test özelliği ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="46280-138">To enable pass-through hit testing of elements under an adorner, set the hit test <xref:System.Windows.UIElement.IsHitTestVisible%2A> property to **false** on the adorner.</span></span>  <span data-ttu-id="46280-139">Isabet testi hakkında daha fazla bilgi için [Görsel Katman'daki Hit Testi'ne](../graphics-multimedia/hit-testing-in-the-visual-layer.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="46280-139">For more information about hit testing, see [Hit Testing in the Visual Layer](../graphics-multimedia/hit-testing-in-the-visual-layer.md).</span></span>

## <a name="adorning-a-single-uielement"></a><span data-ttu-id="46280-140">Tek Bir UIElement'i Süsleme</span><span class="sxs-lookup"><span data-stu-id="46280-140">Adorning a Single UIElement</span></span>

<span data-ttu-id="46280-141">Bir süsleyiciyi belirli <xref:System.Windows.UIElement>bir zamana bağlamak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="46280-141">To bind an adorner to a particular <xref:System.Windows.UIElement>, follow these steps:</span></span>

1. <span data-ttu-id="46280-142">Süslüolması için <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> bir <xref:System.Windows.Documents.AdornerLayer> nesne almak <xref:System.Windows.UIElement> için statik yöntemi arayın.</span><span class="sxs-lookup"><span data-stu-id="46280-142">Call the static method <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> to get an <xref:System.Windows.Documents.AdornerLayer> object for the <xref:System.Windows.UIElement> to be adorned.</span></span> <span data-ttu-id="46280-143"><xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A>belirtilenden <xref:System.Windows.UIElement>başlayarak görsel ağaca doğru yürür ve bulduğu ilk süsleyici katmanını döndürür.</span><span class="sxs-lookup"><span data-stu-id="46280-143"><xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> walks up the visual tree, starting at the specified <xref:System.Windows.UIElement>, and returns the first adorner layer it finds.</span></span> <span data-ttu-id="46280-144">(Hiçbir süsleyici katmanları bulunursa, yöntem null döndürür.)</span><span class="sxs-lookup"><span data-stu-id="46280-144">(If no adorner layers are found, the method returns null.)</span></span>

2. <span data-ttu-id="46280-145">Süsleyiciyi <xref:System.Windows.Documents.AdornerLayer.Add%2A> hedefe <xref:System.Windows.UIElement>bağlamak için yöntemi arayın.</span><span class="sxs-lookup"><span data-stu-id="46280-145">Call the <xref:System.Windows.Documents.AdornerLayer.Add%2A> method to bind the adorner to the target <xref:System.Windows.UIElement>.</span></span>

 <span data-ttu-id="46280-146">Aşağıdaki örnek, bir SimpleCircleAdorner (yukarıda gösterilen) <xref:System.Windows.Controls.TextBox> adlı *myTextBox*bağlar:</span><span class="sxs-lookup"><span data-stu-id="46280-146">The following example binds a SimpleCircleAdorner (shown above) to a <xref:System.Windows.Controls.TextBox> named *myTextBox*:</span></span>

 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornsingleelement)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornsingleelement)]

> [!NOTE]
> <span data-ttu-id="46280-147">Bir [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] süsleyiciyi başka bir öğeye bağlamak için kullanmak şu anda desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="46280-147">Using [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] to bind an adorner to another element is currently not supported.</span></span>

## <a name="adorning-the-children-of-a-panel"></a><span data-ttu-id="46280-148">Panelin Çocuklarını Süslemek</span><span class="sxs-lookup"><span data-stu-id="46280-148">Adorning the Children of a Panel</span></span>

<span data-ttu-id="46280-149">Bir süsleyiciyi çocuklarına <xref:System.Windows.Controls.Panel>bağlamak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="46280-149">To bind an adorner to the children of a <xref:System.Windows.Controls.Panel>, follow these steps:</span></span>

1. <span data-ttu-id="46280-150">Çocukları `static` süslenecek olan element için bir süsleyici katmanı bulmak için yöntemi <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> arayın.</span><span class="sxs-lookup"><span data-stu-id="46280-150">Call the `static` method <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> to find an adorner layer for the element whose children are to be adorned.</span></span>

2. <span data-ttu-id="46280-151">Ana öğenin alt ları aracılığıyla sayısala <xref:System.Windows.Documents.AdornerLayer.Add%2A> ve her alt öğeye bir süsleyici bağlamak için yöntemi arayın.</span><span class="sxs-lookup"><span data-stu-id="46280-151">Enumerate through the children of the parent element and call the <xref:System.Windows.Documents.AdornerLayer.Add%2A> method to bind an adorner to each child element.</span></span>

<span data-ttu-id="46280-152">Aşağıdaki örnek bir SimpleCircleAdorner (yukarıda gösterilen) <xref:System.Windows.Controls.StackPanel> *myStackPanel*adlı çocuklarına bağlar:</span><span class="sxs-lookup"><span data-stu-id="46280-152">The following example binds a SimpleCircleAdorner (shown above) to the children of a <xref:System.Windows.Controls.StackPanel> named *myStackPanel*:</span></span>

[!code-csharp[Adorners_SimpleCircleAdorner#_AdornChildren](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornchildren)]
[!code-vb[Adorners_SimpleCircleAdorner#_AdornChildren](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornchildren)]

## <a name="see-also"></a><span data-ttu-id="46280-153">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="46280-153">See also</span></span>

- <xref:System.Windows.Media.AdornerHitTestResult>
- [<span data-ttu-id="46280-154">WPF Genel Bakışı İçinde Şekiller ve Temel Çizimler</span><span class="sxs-lookup"><span data-stu-id="46280-154">Shapes and Basic Drawing in WPF Overview</span></span>](../graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)
- [<span data-ttu-id="46280-155">Görüntüler, Çizimler ve Görsellerle Boyama</span><span class="sxs-lookup"><span data-stu-id="46280-155">Painting with Images, Drawings, and Visuals</span></span>](../graphics-multimedia/painting-with-images-drawings-and-visuals.md)
- [<span data-ttu-id="46280-156">Çizim Nesnelerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="46280-156">Drawing Objects Overview</span></span>](../graphics-multimedia/drawing-objects-overview.md)
- [<span data-ttu-id="46280-157">Nasıl Dır Konular</span><span class="sxs-lookup"><span data-stu-id="46280-157">How-to Topics</span></span>](adorners-how-to-topics.md)
