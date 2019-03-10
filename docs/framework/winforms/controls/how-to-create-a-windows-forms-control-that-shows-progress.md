---
title: 'Nasıl yapılır: İlerleme durumunu gösteren Windows Forms denetimi oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], progress tracking
- controls [Windows Forms], creating
- progress [Windows Forms], reporting [Windows Forms]
- FlashTrackBar custom control
ms.assetid: 24c5a2e3-058c-4b8d-a217-c06e6a130c2f
ms.openlocfilehash: 6910a7e2e68a3807e08a8b196dde003e1d5bc9af
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57720258"
---
# <a name="how-to-create-a-windows-forms-control-that-shows-progress"></a><span data-ttu-id="63424-102">Nasıl yapılır: İlerleme durumunu gösteren Windows Forms denetimi oluşturma</span><span class="sxs-lookup"><span data-stu-id="63424-102">How to: Create a Windows Forms Control That Shows Progress</span></span>
<span data-ttu-id="63424-103">Aşağıdaki kod örneğinde adlı özel bir denetimi gösterir `FlashTrackBar` kullanıcı düzeyi veya bir uygulamanın ilerleme durumunu göstermek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="63424-103">The following code example shows a custom control called `FlashTrackBar` that can be used to show the user the level or the progress of an application.</span></span> <span data-ttu-id="63424-104">Gradyan ilerlemesini görsel olarak göstermek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="63424-104">It uses a gradient to visually represent progress.</span></span>  
  
 <span data-ttu-id="63424-105">`FlashTrackBar` Denetimi aşağıdaki kavramları göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="63424-105">The `FlashTrackBar` control illustrates the following concepts:</span></span>  
  
-   <span data-ttu-id="63424-106">Özel özellikler tanımlama.</span><span class="sxs-lookup"><span data-stu-id="63424-106">Defining custom properties.</span></span>  
  
-   <span data-ttu-id="63424-107">Özel olaylar tanımlama.</span><span class="sxs-lookup"><span data-stu-id="63424-107">Defining custom events.</span></span> <span data-ttu-id="63424-108">(`FlashTrackBar` tanımlar `ValueChanged` olay.)</span><span class="sxs-lookup"><span data-stu-id="63424-108">(`FlashTrackBar` defines the `ValueChanged` event.)</span></span>  
  
-   <span data-ttu-id="63424-109">Geçersiz kılma <xref:System.Windows.Forms.Control.OnPaint%2A> denetimi çizmek için mantığını sağlamak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="63424-109">Overriding the <xref:System.Windows.Forms.Control.OnPaint%2A> method to provide logic to draw the control.</span></span>  
  
-   <span data-ttu-id="63424-110">Alan kullanan denetimi çizmek için kullanılabilir bilgi işlem, <xref:System.Windows.Forms.Control.ClientRectangle%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="63424-110">Computing the area available for drawing the control by using its <xref:System.Windows.Forms.Control.ClientRectangle%2A> property.</span></span> <span data-ttu-id="63424-111">`FlashTrackBar` bunu yapar, `OptimizedInvalidate` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="63424-111">`FlashTrackBar` does this in its `OptimizedInvalidate` method.</span></span>  
  
-   <span data-ttu-id="63424-112">Windows Form Tasarımcısı'nda değiştirildiğinde serileştirme veya Kalıcılık bir özellik için uygulama.</span><span class="sxs-lookup"><span data-stu-id="63424-112">Implementing serialization or persistence for a property when it is changed in the Windows Forms Designer.</span></span> <span data-ttu-id="63424-113">`FlashTrackBar` tanımlar `ShouldSerializeStartColor` ve `ShouldSerializeEndColor` serileştirmeye yönelik yöntemleri kendi `StartColor` ve `EndColor` özellikleri.</span><span class="sxs-lookup"><span data-stu-id="63424-113">`FlashTrackBar` defines the `ShouldSerializeStartColor` and `ShouldSerializeEndColor` methods for serializing its `StartColor` and `EndColor` properties.</span></span>  
  
 <span data-ttu-id="63424-114">Tarafından tanımlanan özel özellikler aşağıdaki tabloda gösterilmektedir `FlashTrackBar`.</span><span class="sxs-lookup"><span data-stu-id="63424-114">The following table shows the custom properties defined by `FlashTrackBar`.</span></span>  
  
|<span data-ttu-id="63424-115">Özellik</span><span class="sxs-lookup"><span data-stu-id="63424-115">Property</span></span>|<span data-ttu-id="63424-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="63424-116">Description</span></span>|  
|--------------|-----------------|  
|`AllowUserEdit`|<span data-ttu-id="63424-117">Kullanıcının tıklatarak ve sürükleyerek flash izleme çubuğu değerini değiştirip değiştiremeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="63424-117">Indicates whether the user can change the value of the flash track bar by clicking and dragging it.</span></span>|  
|`EndColor`|<span data-ttu-id="63424-118">İzleme çubuğu Bitiş rengini belirtir.</span><span class="sxs-lookup"><span data-stu-id="63424-118">Specifies the ending color of the track bar.</span></span>|  
|`DarkenBy`|<span data-ttu-id="63424-119">Ne kadar arka planda ön plan gradyan göre koyu belirtir.</span><span class="sxs-lookup"><span data-stu-id="63424-119">Specifies how much to darken the background with respect to the foreground gradient.</span></span>|  
|`Max`|<span data-ttu-id="63424-120">İzleme çubuğu en büyük değerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="63424-120">Specifies the maximum value of the track bar.</span></span>|  
|`Min`|<span data-ttu-id="63424-121">İzleme çubuğu en küçük değerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="63424-121">Specifies the minimum value of the track bar.</span></span>|  
|`StartColor`|<span data-ttu-id="63424-122">Gradyan başlangıç rengi belirtir.</span><span class="sxs-lookup"><span data-stu-id="63424-122">Specifies the starting color of the gradient.</span></span>|  
|`ShowPercentage`|<span data-ttu-id="63424-123">Gradyan yüzde görüntülenip görüntülenmeyeceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="63424-123">Indicates whether to display a percentage over the gradient.</span></span>|  
|`ShowValue`|<span data-ttu-id="63424-124">Geçerli değer geçişin görüntülenip görüntülenmeyeceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="63424-124">Indicates whether to display the current value over the gradient.</span></span>|  
|`ShowGradient`|<span data-ttu-id="63424-125">İzleme çubuğu geçerli değerini gösteren bir renk gradyanı görüntülemesi gerekip gerekmediğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="63424-125">Indicates whether the track bar should display a color gradient showing the current value.</span></span>|  
|-   `Value`|<span data-ttu-id="63424-126">İzleme çubuğu geçerli değerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="63424-126">Specifies the current value of the track bar.</span></span>|  
  
 <span data-ttu-id="63424-127">Aşağıdaki tablo diğer üyeleri tarafından tanımlanan gösterir `FlashTrackBar:` özellik değişti olayı ve olayı başlatan yöntem.</span><span class="sxs-lookup"><span data-stu-id="63424-127">The following table shows additional members defined by `FlashTrackBar:` the property-changed event and the method that raises the event.</span></span>  
  
|<span data-ttu-id="63424-128">Üye</span><span class="sxs-lookup"><span data-stu-id="63424-128">Member</span></span>|<span data-ttu-id="63424-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="63424-129">Description</span></span>|  
|------------|-----------------|  
|`ValueChanged`|<span data-ttu-id="63424-130">Olay arandığında `Value` çubuğu değişiklikleri izleme özelliği.</span><span class="sxs-lookup"><span data-stu-id="63424-130">The event that is raised when the `Value` property of the track bar changes.</span></span>|  
|`OnValueChanged`|<span data-ttu-id="63424-131">Başlatan yöntem `ValueChanged` olay.</span><span class="sxs-lookup"><span data-stu-id="63424-131">The method that raises the `ValueChanged` event.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="63424-132">`FlashTrackBar` kullanan <xref:System.EventArgs> olay veri sınıfı ve <xref:System.EventHandler> olay temsilci için.</span><span class="sxs-lookup"><span data-stu-id="63424-132">`FlashTrackBar` uses the <xref:System.EventArgs> class for event data and <xref:System.EventHandler> for the event delegate.</span></span>  
  
 <span data-ttu-id="63424-133">Buna karşılık gelen işlemek için *EventName* olayları `FlashTrackBar` devraldığı aşağıdaki yöntemleri geçersiz kılan <xref:System.Windows.Forms.Control?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="63424-133">To handle the corresponding *EventName* events, `FlashTrackBar` overrides the following methods that it inherits from <xref:System.Windows.Forms.Control?displayProperty=nameWithType>:</span></span>  
  
-   <xref:System.Windows.Forms.Control.OnPaint%2A>  
  
-   <xref:System.Windows.Forms.Control.OnMouseDown%2A>  
  
-   <xref:System.Windows.Forms.Control.OnMouseMove%2A>  
  
-   <xref:System.Windows.Forms.Control.OnMouseUp%2A>  
  
-   <xref:System.Windows.Forms.Control.OnResize%2A>  
  
 <span data-ttu-id="63424-134">Karşılık gelen özellik değişti olayları işlemek için `FlashTrackBar` devraldığı aşağıdaki yöntemleri geçersiz kılan <xref:System.Windows.Forms.Control?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="63424-134">To handle the corresponding property-changed events, `FlashTrackBar` overrides the following methods that it inherits from <xref:System.Windows.Forms.Control?displayProperty=nameWithType>:</span></span>  
  
-   <xref:System.Windows.Forms.Control.OnBackColorChanged%2A>  
  
-   <xref:System.Windows.Forms.Control.OnBackgroundImageChanged%2A>  
  
-   <xref:System.Windows.Forms.Control.OnTextChanged%2A>  
  
## <a name="example"></a><span data-ttu-id="63424-135">Örnek</span><span class="sxs-lookup"><span data-stu-id="63424-135">Example</span></span>  
 <span data-ttu-id="63424-136">`FlashTrackBar` Denetimi tanımlayan iki kullanıcı Arabirimi tür düzenleyicileri `FlashTrackBarValueEditor` ve `FlashTrackBarDarkenByEditor`, aşağıdaki kod listelerinde gösterilir.</span><span class="sxs-lookup"><span data-stu-id="63424-136">The `FlashTrackBar` control defines two UI type editors, `FlashTrackBarValueEditor` and `FlashTrackBarDarkenByEditor`, which are shown in the following code listings.</span></span> <span data-ttu-id="63424-137">`HostApp` Sınıfının kullandığı `FlashTrackBar` bir Windows formunda denetimi.</span><span class="sxs-lookup"><span data-stu-id="63424-137">The `HostApp` class uses the `FlashTrackBar` control on a Windows Form.</span></span>  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#1)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#1)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBarDarkenByEditor.cs#10)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBarDarkenByEditor.vb#10)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBarValueEditor.cs#20)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBarValueEditor.vb#20)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/HostApp.cs#30)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/HostApp.vb#30)]  
  
## <a name="see-also"></a><span data-ttu-id="63424-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="63424-138">See also</span></span>
- <span data-ttu-id="63424-139">[Tasarım zamanı desteği sunma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="63424-139">[Extending Design-Time Support](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))</span></span>
- [<span data-ttu-id="63424-140">Windows Forms Denetimi Geliştirmenin Esasları</span><span class="sxs-lookup"><span data-stu-id="63424-140">Windows Forms Control Development Basics</span></span>](windows-forms-control-development-basics.md)
