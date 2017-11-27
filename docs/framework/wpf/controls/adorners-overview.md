---
title: "Donatıcılara Genel Bakış"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: adorners [WPF], about adorners
ms.assetid: 33d4c5c2-2daf-4e45-ba9a-5b673e2b8280
caps.latest.revision: "35"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 42e37a1a1c00ab1a2039eba5f310cadf9a2175c1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="adorners-overview"></a><span data-ttu-id="3b9d1-102">Donatıcılara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="3b9d1-102">Adorners Overview</span></span>
<span data-ttu-id="3b9d1-103">Donatıcılar, özel bir tür <xref:System.Windows.FrameworkElement>, bir kullanıcı için görsel ipuçları sağlamak için kullanılan.</span><span class="sxs-lookup"><span data-stu-id="3b9d1-103">Adorners are a special type of <xref:System.Windows.FrameworkElement>, used to provide visual cues to a user.</span></span> <span data-ttu-id="3b9d1-104">Diğer kullanımlar arasında Donatıcılar işlevsel tanıtıcıları öğelere eklemek ya da bir denetimi hakkındaki durum bilgilerini sağlamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3b9d1-104">Among other uses, Adorners can be used to add functional handles to elements or provide state information about a control.</span></span>  
  
  
  
<a name="about_Adorners"></a>   
## <a name="about-adorners"></a><span data-ttu-id="3b9d1-105">Donatıcılar hakkında</span><span class="sxs-lookup"><span data-stu-id="3b9d1-105">About Adorners</span></span>  
 <span data-ttu-id="3b9d1-106">Bir <xref:System.Windows.Documents.Adorner> özel <xref:System.Windows.FrameworkElement> için bağlı bir <xref:System.Windows.UIElement>.</span><span class="sxs-lookup"><span data-stu-id="3b9d1-106">An <xref:System.Windows.Documents.Adorner> is a custom <xref:System.Windows.FrameworkElement> that is bound to a <xref:System.Windows.UIElement>.</span></span> <span data-ttu-id="3b9d1-107">Donatıcılar işlenir bir <xref:System.Windows.Documents.AdornerLayer>, her zaman donatılmış öğesi donatılmış öğe koleksiyonunu en üstünde mi işleme yüzeyi olduğu.</span><span class="sxs-lookup"><span data-stu-id="3b9d1-107">Adorners are rendered in an <xref:System.Windows.Documents.AdornerLayer>, which is a rendering surface that is always on top of the adorned element or a collection of adorned elements.</span></span> <span data-ttu-id="3b9d1-108">Bir donatıcının, işleme bağımsız <xref:System.Windows.UIElement> donatıcı bağlı.</span><span class="sxs-lookup"><span data-stu-id="3b9d1-108">Rendering of an adorner is independent from rendering of the <xref:System.Windows.UIElement> that the adorner is bound to.</span></span> <span data-ttu-id="3b9d1-109">Donatıcı genellikle, bu, sol üst donatılmış öğesinin bulunan standart 2B koordinat kaynağını kullanarak bağlı olduğu öğesi göre konumlandırıldı.</span><span class="sxs-lookup"><span data-stu-id="3b9d1-109">An adorner is typically positioned relative to the element to which it is bound, using the standard 2-D coordinate origin located at the upper-left of the adorned element.</span></span>  
  
 <span data-ttu-id="3b9d1-110">Donatıcılar için ortak uygulamalar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="3b9d1-110">Common applications for adorners include:</span></span>  
  
-   <span data-ttu-id="3b9d1-111">İşlev işleyicilerine ekleme bir <xref:System.Windows.UIElement> öğeyi bazı şekilde (yeniden boyutlandırma, döndürme, yeniden konumlandırmak, vb.) işlemek bir kullanıcı etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="3b9d1-111">Adding functional handles to a <xref:System.Windows.UIElement> that enable a user to manipulate the element in some way (resize, rotate, reposition, etc.).</span></span>  
  
-   <span data-ttu-id="3b9d1-112">Çeşitli durumlarını belirtmek için görsel geribildirim sağlamak veya çeşitli olaylarına yanıt olarak.</span><span class="sxs-lookup"><span data-stu-id="3b9d1-112">Provide visual feedback to indicate various states, or in response to various events.</span></span>  
  
-   <span data-ttu-id="3b9d1-113">Üzerinde Visual düzenlemelerinin kaplama bir <xref:System.Windows.UIElement>.</span><span class="sxs-lookup"><span data-stu-id="3b9d1-113">Overlay visual decorations on a <xref:System.Windows.UIElement>.</span></span>  
  
-   <span data-ttu-id="3b9d1-114">Görsel olarak maskeleme veya bölümünü veya tümünü geçersiz kılma bir <xref:System.Windows.UIElement>.</span><span class="sxs-lookup"><span data-stu-id="3b9d1-114">Visually mask or override part or all of a <xref:System.Windows.UIElement>.</span></span>  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]<span data-ttu-id="3b9d1-115">görsel öğeler eklemek için temel bir çerçeve sağlar.</span><span class="sxs-lookup"><span data-stu-id="3b9d1-115"> provides a basic framework for adorning visual elements.</span></span> <span data-ttu-id="3b9d1-116">Aşağıdaki tabloda, nesneleri ve bunların amaçla eklemek kullanılan birincil türleri listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="3b9d1-116">The following table lists the primary types used when adorning objects, and their purpose.</span></span> <span data-ttu-id="3b9d1-117">Birkaç kullanım örnekleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="3b9d1-117">Several usage examples follow.</span></span>  
  
|||  
|-|-|  
|<xref:System.Windows.Documents.Adorner>|<span data-ttu-id="3b9d1-118">Tüm donatıcı uygulamaların somut Özet temel sınıf devralır.</span><span class="sxs-lookup"><span data-stu-id="3b9d1-118">An abstract base class from which all concrete adorner implementations inherit.</span></span>|  
|<xref:System.Windows.Documents.AdornerLayer>|<span data-ttu-id="3b9d1-119">Bir veya daha fazla donatılmış öğelerin donatıcı(ları) için işleme katmanını temsil eden sınıf.</span><span class="sxs-lookup"><span data-stu-id="3b9d1-119">A class representing a rendering layer for the adorner(s) of one or more adorned elements.</span></span>|  
|<xref:System.Windows.Documents.AdornerDecorator>|<span data-ttu-id="3b9d1-120">Öğe koleksiyonunu ile ilişkilendirilecek bir donatıcı katmanı sağlayan sınıf.</span><span class="sxs-lookup"><span data-stu-id="3b9d1-120">A class that enables an adorner layer to be associated with a collection of elements.</span></span>|  
  
<a name="implement_custom_Adorner"></a>   
## <a name="implementing-a-custom-adorner"></a><span data-ttu-id="3b9d1-121">Özel donatıcı uygulama</span><span class="sxs-lookup"><span data-stu-id="3b9d1-121">Implementing a Custom Adorner</span></span>  
 <span data-ttu-id="3b9d1-122">Tarafından sağlanan donatıcılar çerçevesi [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] öncelikle özel donatıcıların oluşturulmasını desteklemek üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="3b9d1-122">The adorners framework provided by [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] is intended primarily to support the creation of custom adorners.</span></span> <span data-ttu-id="3b9d1-123">Özel bir donatıcı Özet devralan bir sınıf uygulama tarafından oluşturulan <xref:System.Windows.Documents.Adorner> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="3b9d1-123">A custom adorner is created by implementing a class that inherits from the abstract <xref:System.Windows.Documents.Adorner> class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3b9d1-124">Üst bir <xref:System.Windows.Documents.Adorner> olan <xref:System.Windows.Documents.AdornerLayer> işleyen <xref:System.Windows.Documents.Adorner>, donatılmakta öğesi değil.</span><span class="sxs-lookup"><span data-stu-id="3b9d1-124">The parent of an <xref:System.Windows.Documents.Adorner> is the <xref:System.Windows.Documents.AdornerLayer> that renders the <xref:System.Windows.Documents.Adorner>, not the element being adorned.</span></span>  
  
 <span data-ttu-id="3b9d1-125">Aşağıdaki örnekte basit bir donatıcı uygulayan bir sınıfı gösterir.</span><span class="sxs-lookup"><span data-stu-id="3b9d1-125">The following example shows a class that implements a simple adorner.</span></span> <span data-ttu-id="3b9d1-126">Örnek donatıcı yalnızca köşelerinde daireler donatır bir <xref:System.Windows.UIElement> daireler ile.</span><span class="sxs-lookup"><span data-stu-id="3b9d1-126">The example adorner simply adorns the corners of a <xref:System.Windows.UIElement> with circles.</span></span>  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_simplecircleadornerbody)]
 [!code-vb[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_simplecircleadornerbody)]  
  
 <span data-ttu-id="3b9d1-127">Aşağıdaki resimde uygulanan SimpleCircleAdorner gösterilmiştir bir <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="3b9d1-127">The following image shows the SimpleCircleAdorner applied to a <xref:System.Windows.Controls.TextBox>.</span></span>  
  
 <span data-ttu-id="3b9d1-128">![Donatıcılar örneği: Donatılmış bir metin kutusu](../../../../docs/framework/wpf/controls/media/adornedtextbox.png "AdornedTextBox")</span><span class="sxs-lookup"><span data-stu-id="3b9d1-128">![Adorners Example: An adorned TextBox](../../../../docs/framework/wpf/controls/media/adornedtextbox.png "AdornedTextBox")</span></span>  
  
<a name="rendering_behavior_for_Adorners"></a>   
## <a name="rendering-behavior-for-adorners"></a><span data-ttu-id="3b9d1-129">Donatıcılar için işleme davranışı</span><span class="sxs-lookup"><span data-stu-id="3b9d1-129">Rendering Behavior for Adorners</span></span>  
 <span data-ttu-id="3b9d1-130">Donatıcılar herhangi devralınmış işleme davranışını içermez dikkate almak önemlidir; donatıcı işler sağlama donatıcı uygulayan sorumluluğundadır.</span><span class="sxs-lookup"><span data-stu-id="3b9d1-130">It is important to note that adorners do not include any inherent rendering behavior; ensuring that an adorner renders is the responsibility of the adorner implementer.</span></span>   <span data-ttu-id="3b9d1-131">İşleme davranışını uygulamanın en yaygın yolu geçersiz kılmaktır <xref:System.Windows.UIElement.OnRender%2A> yöntemi ve bir veya daha fazla <xref:System.Windows.Media.DrawingContext> donatıcının (yukarıdaki örnekte gösterildiği gibi) gereken görsellerini işlemek için nesneleri.</span><span class="sxs-lookup"><span data-stu-id="3b9d1-131">A common way of implementing rendering behavior is to override the <xref:System.Windows.UIElement.OnRender%2A> method and use one or more <xref:System.Windows.Media.DrawingContext> objects to render the adorner's visuals as needed (as shown in the example above).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3b9d1-132">Donatıcı katmanında yerleştirilen herhangi bir şey, ayarladığınız stilleri rest üstünde işlenir.</span><span class="sxs-lookup"><span data-stu-id="3b9d1-132">Anything placed in the adorner layer is rendered on top of the rest of any styles you have set.</span></span> <span data-ttu-id="3b9d1-133">Diğer bir deyişle, Donatıcılar her zaman görsel olarak üsttedir ve z düzenini kullanarak geçersiz kılınamaz.</span><span class="sxs-lookup"><span data-stu-id="3b9d1-133">In other words, adorners are always visually on top and cannot be overridden using z-order.</span></span>  
  
<a name="adorner_events_hittest"></a>   
## <a name="events-and-hit-testing"></a><span data-ttu-id="3b9d1-134">Olaylar ve isabet testi</span><span class="sxs-lookup"><span data-stu-id="3b9d1-134">Events and Hit Testing</span></span>  
 <span data-ttu-id="3b9d1-135">Donatıcılar alma gibi diğer giriş olaylarını <xref:System.Windows.FrameworkElement>.</span><span class="sxs-lookup"><span data-stu-id="3b9d1-135">Adorners receive input events just like any other <xref:System.Windows.FrameworkElement>.</span></span>  <span data-ttu-id="3b9d1-136">Donatıcı her zaman daha yüksek bir z-sırası öğeden olduğundan, donatıcı giriş olaylarını alır (gibi <xref:System.Windows.UIElement.Drop> veya <xref:System.Windows.UIElement.MouseMove>) donattığı donatılan öğeye yönelik.</span><span class="sxs-lookup"><span data-stu-id="3b9d1-136">Because an adorner always has a higher z-order than the element it adorns, the adorner receives input events (such as <xref:System.Windows.UIElement.Drop> or <xref:System.Windows.UIElement.MouseMove>) that may be intended for the underlying adorned element.</span></span>  <span data-ttu-id="3b9d1-137">Donatıcı belirli giriş olaylarını dinleme ve bunlar temel donatılmış öğesi açın olay yeniden yükselterek geçirin.</span><span class="sxs-lookup"><span data-stu-id="3b9d1-137">An adorner can listen for certain input events and pass these on to the underlying adorned element by re-raising the event.</span></span>  
  
 <span data-ttu-id="3b9d1-138">Geçiş isabet donatıcı altında öğelerinin testlerini etkinleştirmek için isabet testi ayarlama <xref:System.Windows.UIElement.IsHitTestVisible%2A> özelliğine **false** donatıcı üzerinde.</span><span class="sxs-lookup"><span data-stu-id="3b9d1-138">To enable pass-through hit testing of elements under an adorner, set the hit test <xref:System.Windows.UIElement.IsHitTestVisible%2A> property to **false** on the adorner.</span></span>  <span data-ttu-id="3b9d1-139">İsabet testi hakkında daha fazla bilgi için bkz:</span><span class="sxs-lookup"><span data-stu-id="3b9d1-139">For more information about hit testing, see</span></span>  
  
 <span data-ttu-id="3b9d1-140">[Görsel katmanda isabet sınaması](../../../../docs/framework/wpf/graphics-multimedia/hit-testing-in-the-visual-layer.md).</span><span class="sxs-lookup"><span data-stu-id="3b9d1-140">[Hit Testing in the Visual Layer](../../../../docs/framework/wpf/graphics-multimedia/hit-testing-in-the-visual-layer.md).</span></span>  
  
<a name="adorn_single_element"></a>   
## <a name="adorning-a-single-uielement"></a><span data-ttu-id="3b9d1-141">Tek bir UIElement eklemek</span><span class="sxs-lookup"><span data-stu-id="3b9d1-141">Adorning a Single UIElement</span></span>  
 <span data-ttu-id="3b9d1-142">Belirli bir donatıcı bağlamak için <xref:System.Windows.UIElement>, şu adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="3b9d1-142">To bind an adorner to a particular <xref:System.Windows.UIElement>, follow these steps:</span></span>  
  
1.  <span data-ttu-id="3b9d1-143">Statik metodunu çağırın <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> almak için bir <xref:System.Windows.Documents.AdornerLayer> için nesne <xref:System.Windows.UIElement> donatılacak.</span><span class="sxs-lookup"><span data-stu-id="3b9d1-143">Call the static method <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> to get an <xref:System.Windows.Documents.AdornerLayer> object for the <xref:System.Windows.UIElement> to be adorned.</span></span> <span data-ttu-id="3b9d1-144"><xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A>Belirtilen başlangıç görsel ağaç anlatılmaktadır <xref:System.Windows.UIElement>ve bulduğu ilk donatıcı katmanı döndürür.</span><span class="sxs-lookup"><span data-stu-id="3b9d1-144"><xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> walks up the visual tree, starting at the specified <xref:System.Windows.UIElement>, and returns the first adorner layer it finds.</span></span> <span data-ttu-id="3b9d1-145">(Hiçbir donatıcı katman bulunamazsa, yöntem null değeri döndürür.)</span><span class="sxs-lookup"><span data-stu-id="3b9d1-145">(If no adorner layers are found, the method returns null.)</span></span>  
  
2.  <span data-ttu-id="3b9d1-146">Çağrı <xref:System.Windows.Documents.AdornerLayer.Add%2A> donatıcıyı hedef bağlamak için yöntemi <xref:System.Windows.UIElement>.</span><span class="sxs-lookup"><span data-stu-id="3b9d1-146">Call the <xref:System.Windows.Documents.AdornerLayer.Add%2A> method to bind the adorner to the target <xref:System.Windows.UIElement>.</span></span>  
  
 <span data-ttu-id="3b9d1-147">Aşağıdaki örnekte (yukarıda gösterilen) SimpleCircleAdorner bağlanır bir <xref:System.Windows.Controls.TextBox> adlı *myTextBox*.</span><span class="sxs-lookup"><span data-stu-id="3b9d1-147">The following example binds a SimpleCircleAdorner (shown above) to a <xref:System.Windows.Controls.TextBox> named *myTextBox*.</span></span>  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornSingleElement](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornsingleelement)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornSingleElement](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornsingleelement)]  
  
> [!NOTE]
>  <span data-ttu-id="3b9d1-148">Kullanarak [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] donatıcı başka bir öğeye bağlamak için şu anda desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="3b9d1-148">Using [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] to bind an adorner to another element is currently not supported.</span></span>  
  
<a name="adorn_children_panel"></a>   
## <a name="adorning-the-children-of-a-panel"></a><span data-ttu-id="3b9d1-149">Bir panelinin alt eklemek</span><span class="sxs-lookup"><span data-stu-id="3b9d1-149">Adorning the Children of a Panel</span></span>  
 <span data-ttu-id="3b9d1-150">Alt öğelerinin donatıcı bağlamak için bir <xref:System.Windows.Controls.Panel>, şu adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="3b9d1-150">To bind an adorner to the children of a <xref:System.Windows.Controls.Panel>, follow these steps:</span></span>  
  
1.  <span data-ttu-id="3b9d1-151">Çağrı `static` yöntemi <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> alt öğeleri olan donatılacak öğe için donatıcı katmanı bulunamıyor.</span><span class="sxs-lookup"><span data-stu-id="3b9d1-151">Call the `static` method <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> to find an adorner layer for the element whose children are to be adorned.</span></span>  
  
2.  <span data-ttu-id="3b9d1-152">Çağrı ve üst öğenin alt öğeleri listeleme <xref:System.Windows.Documents.AdornerLayer.Add%2A> donatıcı her alt öğeye bağlamak için yöntem.</span><span class="sxs-lookup"><span data-stu-id="3b9d1-152">Enumerate through the children of the parent element and call the <xref:System.Windows.Documents.AdornerLayer.Add%2A> method to bind an adorner to each child element.</span></span>  
  
 <span data-ttu-id="3b9d1-153">Aşağıdaki örnek bir SimpleCircleAdorner (yukarıda alt öğelerinin gösterilen) bağlanır bir <xref:System.Windows.Controls.StackPanel> adlı *myStackPanel*.</span><span class="sxs-lookup"><span data-stu-id="3b9d1-153">The following example binds a SimpleCircleAdorner (shown above) to the children of a <xref:System.Windows.Controls.StackPanel> named *myStackPanel*.</span></span>  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornChildren](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornchildren)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornChildren](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornchildren)]  
  
## <a name="see-also"></a><span data-ttu-id="3b9d1-154">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3b9d1-154">See Also</span></span>  
 <xref:System.Windows.Media.AdornerHitTestResult>  
 [<span data-ttu-id="3b9d1-155">Şekiller ve temel çizim WPF genel bakış</span><span class="sxs-lookup"><span data-stu-id="3b9d1-155">Shapes and Basic Drawing in WPF Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)  
 [<span data-ttu-id="3b9d1-156">Görüntüleri, çizimler ve görsellerle boyama</span><span class="sxs-lookup"><span data-stu-id="3b9d1-156">Painting with Images, Drawings, and Visuals</span></span>](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)  
 [<span data-ttu-id="3b9d1-157">Çizim nesnelerine genel bakış</span><span class="sxs-lookup"><span data-stu-id="3b9d1-157">Drawing Objects Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)  
 [<span data-ttu-id="3b9d1-158">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="3b9d1-158">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/adorners-how-to-topics.md)
