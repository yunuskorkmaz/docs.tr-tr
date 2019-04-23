---
title: 'Nasıl yapılır: Sistem Fırçası ile bir Alanı Boyama'
ms.date: 03/30/2017
helpviewer_keywords:
- system brushes [WPF], painting with
- painting [WPF], with system brushes
- brushes [WPF], painting with system brushes [WPF]
ms.assetid: 5141a763-9235-42cb-a6bb-afc75513eac7
ms.openlocfilehash: e713903e2cfbb63cb64ceb94621317f9e76dea70
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59195052"
---
# <a name="how-to-paint-an-area-with-a-system-brush"></a><span data-ttu-id="66a48-102">Nasıl yapılır: Sistem Fırçası ile bir Alanı Boyama</span><span class="sxs-lookup"><span data-stu-id="66a48-102">How to: Paint an Area with a System Brush</span></span>
<span data-ttu-id="66a48-103"><xref:System.Windows.SystemColors> Sınıfı sağlar sistem fırçaları ve renkler, erişim gibi <xref:System.Windows.SystemColors.ControlBrush%2A>, <xref:System.Windows.SystemColors.ControlBrushKey%2A>, ve <xref:System.Windows.SystemColors.DesktopBrush%2A>.</span><span class="sxs-lookup"><span data-stu-id="66a48-103">The <xref:System.Windows.SystemColors> class provides access to system brushes and colors, such as <xref:System.Windows.SystemColors.ControlBrush%2A>, <xref:System.Windows.SystemColors.ControlBrushKey%2A>, and <xref:System.Windows.SystemColors.DesktopBrush%2A>.</span></span> <span data-ttu-id="66a48-104">Sistem Fırçası olduğu bir <xref:System.Windows.Media.SolidColorBrush> nesnesini belirtilen sistem renk ile bir alanı boyar.</span><span class="sxs-lookup"><span data-stu-id="66a48-104">A system brush is a <xref:System.Windows.Media.SolidColorBrush> object that paints an area with the specified system color.</span></span> <span data-ttu-id="66a48-105">Sistem Fırçası her zaman bir tek renk dolgu üretir; gradyan oluşturmak için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="66a48-105">A system brush always produces a solid fill; it can't be used to create a gradient.</span></span>  
  
 <span data-ttu-id="66a48-106">Sistem fırçaları statik veya dinamik bir kaynak kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="66a48-106">You can use system brushes as either a static or a dynamic resource.</span></span> <span data-ttu-id="66a48-107">Kullanıcı sistem fırçası değiştirirse uygulama çalışırken otomatik olarak güncelleştirilecek fırça istiyorsanız bir dinamik kaynak kullanın. Aksi takdirde, bir statik kaynak kullanın.</span><span class="sxs-lookup"><span data-stu-id="66a48-107">Use a dynamic resource if you want the brush to update automatically if the user changes the system brush as the application is running; otherwise, use a static resource.</span></span> <span data-ttu-id="66a48-108">SystemColors sınıfı çeşitli katı bir adlandırma kuralını uyguladığınızdan statik özellikler içerir:</span><span class="sxs-lookup"><span data-stu-id="66a48-108">The SystemColors class contains a variety of static properties that follow a strict naming convention:</span></span>  
  
-   <span data-ttu-id="66a48-109">*\<SystemColor>* Brush</span><span class="sxs-lookup"><span data-stu-id="66a48-109">*\<SystemColor>* Brush</span></span>  
  
     <span data-ttu-id="66a48-110">Statik başvuru alır bir <xref:System.Windows.Media.SolidColorBrush> belirtilen sistem renk.</span><span class="sxs-lookup"><span data-stu-id="66a48-110">Gets a static reference to a <xref:System.Windows.Media.SolidColorBrush> of the specified system color.</span></span>  
  
-   <span data-ttu-id="66a48-111">*\<SystemColor >* BrushKey</span><span class="sxs-lookup"><span data-stu-id="66a48-111">*\<SystemColor>* BrushKey</span></span>  
  
     <span data-ttu-id="66a48-112">Dinamik başvuru alır bir <xref:System.Windows.Media.SolidColorBrush> belirtilen sistem renk.</span><span class="sxs-lookup"><span data-stu-id="66a48-112">Gets a dynamic reference to a <xref:System.Windows.Media.SolidColorBrush> of the specified system color.</span></span>  
  
-   <span data-ttu-id="66a48-113">*\<SystemColor >* rengi</span><span class="sxs-lookup"><span data-stu-id="66a48-113">*\<SystemColor>* Color</span></span>  
  
     <span data-ttu-id="66a48-114">Statik başvuru alır bir <xref:System.Windows.Media.Color> belirtilen sistem renk yapısı.</span><span class="sxs-lookup"><span data-stu-id="66a48-114">Gets a static reference to a <xref:System.Windows.Media.Color> structure of the specified system color.</span></span>  
  
-   <span data-ttu-id="66a48-115">*\<SystemColor >* ColorKey</span><span class="sxs-lookup"><span data-stu-id="66a48-115">*\<SystemColor>* ColorKey</span></span>  
  
     <span data-ttu-id="66a48-116">Dinamik bir başvuru edinir <xref:System.Windows.Media.Color> belirtilen sistem renk yapısı.</span><span class="sxs-lookup"><span data-stu-id="66a48-116">Gets a dynamic reference to the <xref:System.Windows.Media.Color> structure of the specified system color.</span></span>  
  
 <span data-ttu-id="66a48-117">Sistem rengi bir <xref:System.Windows.Media.Color> fırça yapılandırmak için kullanılan yapısı.</span><span class="sxs-lookup"><span data-stu-id="66a48-117">A system color is a <xref:System.Windows.Media.Color> structure that can be used to configure a brush.</span></span> <span data-ttu-id="66a48-118">Örneğin, bir gradyan ayarlayarak Sistem renkleri kullanarak oluşturabilirsiniz <xref:System.Windows.Media.GradientStop.Color%2A> özelliklerini bir <xref:System.Windows.Media.LinearGradientBrush> nesnesi gradyan duraklarının sistem renkleri.</span><span class="sxs-lookup"><span data-stu-id="66a48-118">For example, you can create a gradient using system colors by setting the <xref:System.Windows.Media.GradientStop.Color%2A> properties of a <xref:System.Windows.Media.LinearGradientBrush> object's gradient stops with system colors.</span></span> <span data-ttu-id="66a48-119">Bir örnek için bkz. [gradyan içinde kullanımı sistem renkleri](how-to-use-system-colors-in-a-gradient.md).</span><span class="sxs-lookup"><span data-stu-id="66a48-119">For an example, see [Use System Colors in a Gradient](how-to-use-system-colors-in-a-gradient.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="66a48-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="66a48-120">Example</span></span>  
 <span data-ttu-id="66a48-121">Aşağıdaki örnek, bir düğme arka planını ayarlama için dinamik sistem fırçası başvurusu kullanır.</span><span class="sxs-lookup"><span data-stu-id="66a48-121">The following example uses a dynamic system brush reference to set the Background of a button.</span></span>  
  
 [!code-xaml[brushsamples_snip#GraphicsMMDynamicSystemColorDesktopBrushKeyExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/DynamicSystemBrushExample.xaml#graphicsmmdynamicsystemcolordesktopbrushkeyexamplewholepage)]  
  
 <span data-ttu-id="66a48-122">Sonraki örnek, bir düğme arka planını ayarlama için statik sistem fırçası başvurusu kullanır.</span><span class="sxs-lookup"><span data-stu-id="66a48-122">The next example uses a static system brush reference to set the Background of a button.</span></span>  
  
 [!code-xaml[brushsamples_snip#GraphicsMMStaticSystemColorDesktopBrushExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/StaticSystemBrushExample.xaml#graphicsmmstaticsystemcolordesktopbrushexamplewholepage)]  
  
 <span data-ttu-id="66a48-123">Bir sistem renginin gradyan içinde nasıl kullanılacağını gösteren bir örnek için bkz: [Sistem renklerini kullan gradyan](how-to-use-system-colors-in-a-gradient.md).</span><span class="sxs-lookup"><span data-stu-id="66a48-123">For an example showing how to use a system color in a gradient, see [Use System Colors in a Gradient](how-to-use-system-colors-in-a-gradient.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66a48-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="66a48-124">See also</span></span>

- [<span data-ttu-id="66a48-125">Sistem Renklerinin Gradyan İçinde Kullanımı</span><span class="sxs-lookup"><span data-stu-id="66a48-125">Use System Colors in a Gradient</span></span>](how-to-use-system-colors-in-a-gradient.md)
- [<span data-ttu-id="66a48-126">Düz Renkler ve Gradyanlar ile Boyamaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="66a48-126">Painting with Solid Colors and Gradients Overview</span></span>](painting-with-solid-colors-and-gradients-overview.md)
