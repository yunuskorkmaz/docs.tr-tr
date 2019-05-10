---
title: Donatıcılara Genel Bakış
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adorners [WPF], about adorners
ms.assetid: 33d4c5c2-2daf-4e45-ba9a-5b673e2b8280
ms.openlocfilehash: b5788b3ddb14b1acae9c6661420ab439205d000b
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64591248"
---
# <a name="adorners-overview"></a><span data-ttu-id="c5e53-102">Donatıcılara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="c5e53-102">Adorners Overview</span></span>
<span data-ttu-id="c5e53-103">Donatıcıları, özel bir tür <xref:System.Windows.FrameworkElement>görsel ipuçları kullanıcıya sağlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c5e53-103">Adorners are a special type of <xref:System.Windows.FrameworkElement>, used to provide visual cues to a user.</span></span> <span data-ttu-id="c5e53-104">Diğer kullanımının yanı sıra donatıcıları işlevsel tanıtıcıları öğeleri ekleyin ya da bir denetimi hakkındaki durum bilgilerini sağlamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c5e53-104">Among other uses, Adorners can be used to add functional handles to elements or provide state information about a control.</span></span>  

<a name="about_Adorners"></a>   
## <a name="about-adorners"></a><span data-ttu-id="c5e53-105">Donatıcılar hakkında</span><span class="sxs-lookup"><span data-stu-id="c5e53-105">About Adorners</span></span>  
 <span data-ttu-id="c5e53-106">Bir <xref:System.Windows.Documents.Adorner> özel <xref:System.Windows.FrameworkElement> bağlanan bir <xref:System.Windows.UIElement>.</span><span class="sxs-lookup"><span data-stu-id="c5e53-106">An <xref:System.Windows.Documents.Adorner> is a custom <xref:System.Windows.FrameworkElement> that is bound to a <xref:System.Windows.UIElement>.</span></span> <span data-ttu-id="c5e53-107">Donatıcıları oluşturulur bir <xref:System.Windows.Documents.AdornerLayer>, her zaman donatılmış öğe veya donatılmış öğelerinin bir koleksiyonunu en üstünde olan bir işleme yüzeyi olduğu.</span><span class="sxs-lookup"><span data-stu-id="c5e53-107">Adorners are rendered in an <xref:System.Windows.Documents.AdornerLayer>, which is a rendering surface that is always on top of the adorned element or a collection of adorned elements.</span></span> <span data-ttu-id="c5e53-108">İşleme, bağımsız bir donatıcının <xref:System.Windows.UIElement> donatıcı bağlı.</span><span class="sxs-lookup"><span data-stu-id="c5e53-108">Rendering of an adorner is independent from rendering of the <xref:System.Windows.UIElement> that the adorner is bound to.</span></span> <span data-ttu-id="c5e53-109">Öğeye bir donatıcı genellikle, bu, donatılmış öğenin sol bulunan standart 2B koordinat kaynağını kullanarak bağlı olduğu öğe göre konumlandırılır.</span><span class="sxs-lookup"><span data-stu-id="c5e53-109">An adorner is typically positioned relative to the element to which it is bound, using the standard 2-D coordinate origin located at the upper-left of the adorned element.</span></span>  
  
 <span data-ttu-id="c5e53-110">Donatıcılar için ortak uygulamalar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="c5e53-110">Common applications for adorners include:</span></span>  
  
- <span data-ttu-id="c5e53-111">İşlev tanıtıcıları ekleyerek bir <xref:System.Windows.UIElement> öğeyi (yeniden boyutlandırma, döndürme, yeniden konumlandırma, vb.) bir şekilde işlemek bir kullanıcı etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="c5e53-111">Adding functional handles to a <xref:System.Windows.UIElement> that enable a user to manipulate the element in some way (resize, rotate, reposition, etc.).</span></span>  
  
- <span data-ttu-id="c5e53-112">Çeşitli durumları göstermek için görsel geri bildirim sağlamak veya çeşitli olaylara yanıt vermek.</span><span class="sxs-lookup"><span data-stu-id="c5e53-112">Provide visual feedback to indicate various states, or in response to various events.</span></span>  
  
- <span data-ttu-id="c5e53-113">Görsel süslemeleri yer paylaşımı üzerindeki bir <xref:System.Windows.UIElement>.</span><span class="sxs-lookup"><span data-stu-id="c5e53-113">Overlay visual decorations on a <xref:System.Windows.UIElement>.</span></span>  
  
- <span data-ttu-id="c5e53-114">Görsel olarak maskelemek veya bölümünü veya tümünü geçersiz bir <xref:System.Windows.UIElement>.</span><span class="sxs-lookup"><span data-stu-id="c5e53-114">Visually mask or override part or all of a <xref:System.Windows.UIElement>.</span></span>  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <span data-ttu-id="c5e53-115">görsel öğeler donatmak için temel çerçeveyi sağlar.</span><span class="sxs-lookup"><span data-stu-id="c5e53-115">provides a basic framework for adorning visual elements.</span></span> <span data-ttu-id="c5e53-116">Aşağıdaki tabloda, nesneleri ve bunların amacı donatmak olduğunda kullanılan birincil türlerini listeler.</span><span class="sxs-lookup"><span data-stu-id="c5e53-116">The following table lists the primary types used when adorning objects, and their purpose.</span></span> <span data-ttu-id="c5e53-117">Çeşitli kullanım örnekleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="c5e53-117">Several usage examples follow.</span></span>  
  
|||  
|-|-|  
|<xref:System.Windows.Documents.Adorner>|<span data-ttu-id="c5e53-118">Tüm somut donatıcı uygulamaların devraldığı bir soyut temel sınıf.</span><span class="sxs-lookup"><span data-stu-id="c5e53-118">An abstract base class from which all concrete adorner implementations inherit.</span></span>|  
|<xref:System.Windows.Documents.AdornerLayer>|<span data-ttu-id="c5e53-119">Bir veya daha fazla donatılmış öğeleri donatıcı(ları) için işleme katmanını temsil eden sınıf.</span><span class="sxs-lookup"><span data-stu-id="c5e53-119">A class representing a rendering layer for the adorner(s) of one or more adorned elements.</span></span>|  
|<xref:System.Windows.Documents.AdornerDecorator>|<span data-ttu-id="c5e53-120">Öğelerinin bir koleksiyonunu ile ilişkilendirilecek bir donatıcı katmanı sağlayan bir sınıf.</span><span class="sxs-lookup"><span data-stu-id="c5e53-120">A class that enables an adorner layer to be associated with a collection of elements.</span></span>|  
  
<a name="implement_custom_Adorner"></a>   
## <a name="implementing-a-custom-adorner"></a><span data-ttu-id="c5e53-121">Özel bir donatıcı uygulama</span><span class="sxs-lookup"><span data-stu-id="c5e53-121">Implementing a Custom Adorner</span></span>  
 <span data-ttu-id="c5e53-122">Donatıcıları framework tarafından sağlanan [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] öncelikle özel donatıcıları oluşturulmasını desteklemek için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="c5e53-122">The adorners framework provided by [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] is intended primarily to support the creation of custom adorners.</span></span> <span data-ttu-id="c5e53-123">Özet devralan bir sınıf uygulama tarafından oluşturulan özel bir donatıcı <xref:System.Windows.Documents.Adorner> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="c5e53-123">A custom adorner is created by implementing a class that inherits from the abstract <xref:System.Windows.Documents.Adorner> class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c5e53-124">Üst öğesi bir <xref:System.Windows.Documents.Adorner> olduğu <xref:System.Windows.Documents.AdornerLayer> işleyen <xref:System.Windows.Documents.Adorner>, donatılan öğe değil.</span><span class="sxs-lookup"><span data-stu-id="c5e53-124">The parent of an <xref:System.Windows.Documents.Adorner> is the <xref:System.Windows.Documents.AdornerLayer> that renders the <xref:System.Windows.Documents.Adorner>, not the element being adorned.</span></span>  
  
 <span data-ttu-id="c5e53-125">Aşağıdaki örnek, basit bir donatıcı uygulayan bir sınıfı gösterir.</span><span class="sxs-lookup"><span data-stu-id="c5e53-125">The following example shows a class that implements a simple adorner.</span></span> <span data-ttu-id="c5e53-126">Örnek donatıcı köşelerini yalnızca daireler donatır bir <xref:System.Windows.UIElement> daireler ile.</span><span class="sxs-lookup"><span data-stu-id="c5e53-126">The example adorner simply adorns the corners of a <xref:System.Windows.UIElement> with circles.</span></span>  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_simplecircleadornerbody)]
 [!code-vb[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_simplecircleadornerbody)]  
  
 <span data-ttu-id="c5e53-127">Aşağıdaki görüntüde uygulanan SimpleCircleAdorner gösterir bir <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="c5e53-127">The following image shows the SimpleCircleAdorner applied to a <xref:System.Windows.Controls.TextBox>.</span></span>  
  
 ![Donatılmış metin kutusunu gösteren ekran görüntüsü.](./media/adorners-overview/simplecircleadorner-textbox.png)  
  
<a name="rendering_behavior_for_Adorners"></a>   
## <a name="rendering-behavior-for-adorners"></a><span data-ttu-id="c5e53-129">Donatıcılar işleme davranışı</span><span class="sxs-lookup"><span data-stu-id="c5e53-129">Rendering Behavior for Adorners</span></span>  
 <span data-ttu-id="c5e53-130">Donatıcıları herhangi devralınan işleme davranışını içermez dikkat edin önemlidir; öğeye bir donatıcı oluşturulduğunu sağlama donatıcı uygulayan sorumluluğundadır.</span><span class="sxs-lookup"><span data-stu-id="c5e53-130">It is important to note that adorners do not include any inherent rendering behavior; ensuring that an adorner renders is the responsibility of the adorner implementer.</span></span>   <span data-ttu-id="c5e53-131">Geçersiz kılmak için işleme davranışını uygulamanın yaygın bir yolu olan <xref:System.Windows.UIElement.OnRender%2A> yöntemi ve bir veya daha fazla <xref:System.Windows.Media.DrawingContext> (yukarıdaki örnekte gösterildiği gibi) gerektiği gibi donatıcının görseller oluşturmak için nesne.</span><span class="sxs-lookup"><span data-stu-id="c5e53-131">A common way of implementing rendering behavior is to override the <xref:System.Windows.UIElement.OnRender%2A> method and use one or more <xref:System.Windows.Media.DrawingContext> objects to render the adorner's visuals as needed (as shown in the example above).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c5e53-132">Herhangi bir şey donatıcı katmanında yerleştirilen ayarladığınız stilleri geri kalanı üstünde işlenir.</span><span class="sxs-lookup"><span data-stu-id="c5e53-132">Anything placed in the adorner layer is rendered on top of the rest of any styles you have set.</span></span> <span data-ttu-id="c5e53-133">Diğer bir deyişle, donatıcıları her zaman üstte görsel olarak sunulan ve z düzenini kullanarak geçersiz kılınamaz.</span><span class="sxs-lookup"><span data-stu-id="c5e53-133">In other words, adorners are always visually on top and cannot be overridden using z-order.</span></span>  
  
<a name="adorner_events_hittest"></a>   
## <a name="events-and-hit-testing"></a><span data-ttu-id="c5e53-134">Olaylar ve isabet sınaması</span><span class="sxs-lookup"><span data-stu-id="c5e53-134">Events and Hit Testing</span></span>  
 <span data-ttu-id="c5e53-135">Donatıcıları alma gibi diğer giriş olaylarını <xref:System.Windows.FrameworkElement>.</span><span class="sxs-lookup"><span data-stu-id="c5e53-135">Adorners receive input events just like any other <xref:System.Windows.FrameworkElement>.</span></span>  <span data-ttu-id="c5e53-136">Öğeye bir donatıcı her zaman öğeden daha yüksek bir z düzenini olduğundan, giriş olaylarını donatıcı alır (gibi <xref:System.Windows.UIElement.Drop> veya <xref:System.Windows.UIElement.MouseMove>), amaçlanan donatılan öğeye için.</span><span class="sxs-lookup"><span data-stu-id="c5e53-136">Because an adorner always has a higher z-order than the element it adorns, the adorner receives input events (such as <xref:System.Windows.UIElement.Drop> or <xref:System.Windows.UIElement.MouseMove>) that may be intended for the underlying adorned element.</span></span>  <span data-ttu-id="c5e53-137">Öğeye bir donatıcı, belirli giriş olaylarını dinlemek ve bunların temelde donatılan öğeye açın olay yeniden oluşturularak geçirin.</span><span class="sxs-lookup"><span data-stu-id="c5e53-137">An adorner can listen for certain input events and pass these on to the underlying adorned element by re-raising the event.</span></span>  
  
 <span data-ttu-id="c5e53-138">İsabet öğeye bir donatıcı altındaki öğeleri sınamasına etkinleştirmek için isabet testi ayarlama <xref:System.Windows.UIElement.IsHitTestVisible%2A> özelliğini **false** donatıcı üzerinde.</span><span class="sxs-lookup"><span data-stu-id="c5e53-138">To enable pass-through hit testing of elements under an adorner, set the hit test <xref:System.Windows.UIElement.IsHitTestVisible%2A> property to **false** on the adorner.</span></span>  <span data-ttu-id="c5e53-139">İsabet testi hakkında daha fazla bilgi için bkz.</span><span class="sxs-lookup"><span data-stu-id="c5e53-139">For more information about hit testing, see</span></span>  
  
 <span data-ttu-id="c5e53-140">[Görsel katmanda tıklama testi](../graphics-multimedia/hit-testing-in-the-visual-layer.md).</span><span class="sxs-lookup"><span data-stu-id="c5e53-140">[Hit Testing in the Visual Layer](../graphics-multimedia/hit-testing-in-the-visual-layer.md).</span></span>  
  
<a name="adorn_single_element"></a>   
## <a name="adorning-a-single-uielement"></a><span data-ttu-id="c5e53-141">Tek bir UIElement Donatma</span><span class="sxs-lookup"><span data-stu-id="c5e53-141">Adorning a Single UIElement</span></span>  
 <span data-ttu-id="c5e53-142">Belirli bir öğeye bir donatıcı bağlama için <xref:System.Windows.UIElement>, şu adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="c5e53-142">To bind an adorner to a particular <xref:System.Windows.UIElement>, follow these steps:</span></span>  
  
1. <span data-ttu-id="c5e53-143">Statik metodunu çağırın <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> almak için bir <xref:System.Windows.Documents.AdornerLayer> nesnesi <xref:System.Windows.UIElement> donatılmış için.</span><span class="sxs-lookup"><span data-stu-id="c5e53-143">Call the static method <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> to get an <xref:System.Windows.Documents.AdornerLayer> object for the <xref:System.Windows.UIElement> to be adorned.</span></span> <span data-ttu-id="c5e53-144"><xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> Belirtilen adreste başlayan görsel ağaç'kurmak gezer <xref:System.Windows.UIElement>ve bulduğu ilk donatıcı katmanı döndürür.</span><span class="sxs-lookup"><span data-stu-id="c5e53-144"><xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> walks up the visual tree, starting at the specified <xref:System.Windows.UIElement>, and returns the first adorner layer it finds.</span></span> <span data-ttu-id="c5e53-145">(Hiçbir donatıcı katman bulunursa, yöntem null değeri döndürür.)</span><span class="sxs-lookup"><span data-stu-id="c5e53-145">(If no adorner layers are found, the method returns null.)</span></span>  
  
2. <span data-ttu-id="c5e53-146">Çağrı <xref:System.Windows.Documents.AdornerLayer.Add%2A> donatıcıyı hedefe bağlamak için yöntemi <xref:System.Windows.UIElement>.</span><span class="sxs-lookup"><span data-stu-id="c5e53-146">Call the <xref:System.Windows.Documents.AdornerLayer.Add%2A> method to bind the adorner to the target <xref:System.Windows.UIElement>.</span></span>  
  
 <span data-ttu-id="c5e53-147">Aşağıdaki örnekte (yukarıda gösterilen) SimpleCircleAdorner bağlayan bir <xref:System.Windows.Controls.TextBox> adlı *myTextBox*.</span><span class="sxs-lookup"><span data-stu-id="c5e53-147">The following example binds a SimpleCircleAdorner (shown above) to a <xref:System.Windows.Controls.TextBox> named *myTextBox*.</span></span>  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornsingleelement)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornsingleelement)]  
  
> [!NOTE]
>  <span data-ttu-id="c5e53-148">Kullanarak [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] başka bir öğeye bir donatıcı bağlamak için şu anda desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="c5e53-148">Using [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] to bind an adorner to another element is currently not supported.</span></span>  
  
<a name="adorn_children_panel"></a>   
## <a name="adorning-the-children-of-a-panel"></a><span data-ttu-id="c5e53-149">Panelin alt öğelerini Donatma</span><span class="sxs-lookup"><span data-stu-id="c5e53-149">Adorning the Children of a Panel</span></span>  
 <span data-ttu-id="c5e53-150">Alt öğeye bir donatıcı bağlama için bir <xref:System.Windows.Controls.Panel>, şu adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="c5e53-150">To bind an adorner to the children of a <xref:System.Windows.Controls.Panel>, follow these steps:</span></span>  
  
1. <span data-ttu-id="c5e53-151">Çağrı `static` yöntemi <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> alt öğeleri donatılmış için öğeye bir donatıcı katmanı bulunacak.</span><span class="sxs-lookup"><span data-stu-id="c5e53-151">Call the `static` method <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> to find an adorner layer for the element whose children are to be adorned.</span></span>  
  
2. <span data-ttu-id="c5e53-152">Çağrı ve üst öğenin alt öğelerini numaralandırın <xref:System.Windows.Documents.AdornerLayer.Add%2A> her alt öğeye bir donatıcı bağlama için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="c5e53-152">Enumerate through the children of the parent element and call the <xref:System.Windows.Documents.AdornerLayer.Add%2A> method to bind an adorner to each child element.</span></span>  
  
 <span data-ttu-id="c5e53-153">Aşağıdaki örnek SimpleCircleAdorner (yukarıda alt için gösterilen) bağlanır bir <xref:System.Windows.Controls.StackPanel> adlı *myStackPanel*.</span><span class="sxs-lookup"><span data-stu-id="c5e53-153">The following example binds a SimpleCircleAdorner (shown above) to the children of a <xref:System.Windows.Controls.StackPanel> named *myStackPanel*.</span></span>  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornChildren](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornchildren)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornChildren](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornchildren)]  
  
## <a name="see-also"></a><span data-ttu-id="c5e53-154">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c5e53-154">See also</span></span>

- <xref:System.Windows.Media.AdornerHitTestResult>
- [<span data-ttu-id="c5e53-155">WPF’de Şekiller ve Temel Çizimlere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="c5e53-155">Shapes and Basic Drawing in WPF Overview</span></span>](../graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)
- [<span data-ttu-id="c5e53-156">Görüntüler, Çizimler ve Görsellerle Boyama</span><span class="sxs-lookup"><span data-stu-id="c5e53-156">Painting with Images, Drawings, and Visuals</span></span>](../graphics-multimedia/painting-with-images-drawings-and-visuals.md)
- [<span data-ttu-id="c5e53-157">Çizim Nesnelerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="c5e53-157">Drawing Objects Overview</span></span>](../graphics-multimedia/drawing-objects-overview.md)
- [<span data-ttu-id="c5e53-158">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="c5e53-158">How-to Topics</span></span>](adorners-how-to-topics.md)
