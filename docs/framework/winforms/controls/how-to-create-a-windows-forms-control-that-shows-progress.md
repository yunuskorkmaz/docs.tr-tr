---
title: Ilerlemeyi gösteren denetim oluşturma
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
ms.openlocfilehash: 9d2cf353ba2309380221bb51733baaca1b81a5d5
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76731181"
---
# <a name="how-to-create-a-windows-forms-control-that-shows-progress"></a><span data-ttu-id="5431a-102">Nasıl yapılır: İlerleme Durumunu Gösteren Windows Forms Denetimi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="5431a-102">How to: Create a Windows Forms Control That Shows Progress</span></span>
<span data-ttu-id="5431a-103">Aşağıdaki kod örneği, kullanıcının bir uygulamanın düzeyini veya ilerlemesini göstermek için kullanılabilecek `FlashTrackBar` adlı özel bir denetimi gösterir.</span><span class="sxs-lookup"><span data-stu-id="5431a-103">The following code example shows a custom control called `FlashTrackBar` that can be used to show the user the level or the progress of an application.</span></span> <span data-ttu-id="5431a-104">İlerlemeyi görsel olarak göstermek için bir gradyan kullanır.</span><span class="sxs-lookup"><span data-stu-id="5431a-104">It uses a gradient to visually represent progress.</span></span>  
  
 <span data-ttu-id="5431a-105">`FlashTrackBar` denetimi aşağıdaki kavramları gösterir:</span><span class="sxs-lookup"><span data-stu-id="5431a-105">The `FlashTrackBar` control illustrates the following concepts:</span></span>  
  
- <span data-ttu-id="5431a-106">Özel özellikleri tanımlama.</span><span class="sxs-lookup"><span data-stu-id="5431a-106">Defining custom properties.</span></span>  
  
- <span data-ttu-id="5431a-107">Özel olayları tanımlama.</span><span class="sxs-lookup"><span data-stu-id="5431a-107">Defining custom events.</span></span> <span data-ttu-id="5431a-108">(`FlashTrackBar` `ValueChanged` olayını tanımlar.)</span><span class="sxs-lookup"><span data-stu-id="5431a-108">(`FlashTrackBar` defines the `ValueChanged` event.)</span></span>  
  
- <span data-ttu-id="5431a-109">Denetimi çizmek için mantık sağlamak üzere <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemini geçersiz kılma.</span><span class="sxs-lookup"><span data-stu-id="5431a-109">Overriding the <xref:System.Windows.Forms.Control.OnPaint%2A> method to provide logic to draw the control.</span></span>  
  
- <span data-ttu-id="5431a-110"><xref:System.Windows.Forms.Control.ClientRectangle%2A> özelliğini kullanarak, denetimi çizmek için kullanılabilir alan hesaplanıyor.</span><span class="sxs-lookup"><span data-stu-id="5431a-110">Computing the area available for drawing the control by using its <xref:System.Windows.Forms.Control.ClientRectangle%2A> property.</span></span> <span data-ttu-id="5431a-111">Bunu `OptimizedInvalidate` yönteminde `FlashTrackBar`.</span><span class="sxs-lookup"><span data-stu-id="5431a-111">`FlashTrackBar` does this in its `OptimizedInvalidate` method.</span></span>  
  
- <span data-ttu-id="5431a-112">Windows Form Tasarımcısı değiştirildiğinde bir özellik için serileştirme veya kalıcılık uygulama.</span><span class="sxs-lookup"><span data-stu-id="5431a-112">Implementing serialization or persistence for a property when it is changed in the Windows Forms Designer.</span></span> <span data-ttu-id="5431a-113">`FlashTrackBar`, `StartColor` ve `EndColor` özelliklerini serileştirmek için `ShouldSerializeStartColor` ve `ShouldSerializeEndColor` yöntemlerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="5431a-113">`FlashTrackBar` defines the `ShouldSerializeStartColor` and `ShouldSerializeEndColor` methods for serializing its `StartColor` and `EndColor` properties.</span></span>  
  
 <span data-ttu-id="5431a-114">Aşağıdaki tabloda `FlashTrackBar`tarafından tanımlanan özel özellikler gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="5431a-114">The following table shows the custom properties defined by `FlashTrackBar`.</span></span>  
  
|<span data-ttu-id="5431a-115">Özellik</span><span class="sxs-lookup"><span data-stu-id="5431a-115">Property</span></span>|<span data-ttu-id="5431a-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5431a-116">Description</span></span>|  
|--------------|-----------------|  
|`AllowUserEdit`|<span data-ttu-id="5431a-117">Kullanıcının, Flash izleme çubuğunun değerini tıklatıp sürükleyerek değiştirip değiştiremeyeceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="5431a-117">Indicates whether the user can change the value of the flash track bar by clicking and dragging it.</span></span>|  
|`EndColor`|<span data-ttu-id="5431a-118">İzleme çubuğunun bitiş rengini belirtir.</span><span class="sxs-lookup"><span data-stu-id="5431a-118">Specifies the ending color of the track bar.</span></span>|  
|`DarkenBy`|<span data-ttu-id="5431a-119">Ön plan degradeyle ilgili olarak arka planın ne kadar koyulaştıralınacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="5431a-119">Specifies how much to darken the background with respect to the foreground gradient.</span></span>|  
|`Max`|<span data-ttu-id="5431a-120">İzleme çubuğunun en büyük değerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="5431a-120">Specifies the maximum value of the track bar.</span></span>|  
|`Min`|<span data-ttu-id="5431a-121">İzleme çubuğunun en küçük değerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="5431a-121">Specifies the minimum value of the track bar.</span></span>|  
|`StartColor`|<span data-ttu-id="5431a-122">Degradenin başlangıç rengini belirtir.</span><span class="sxs-lookup"><span data-stu-id="5431a-122">Specifies the starting color of the gradient.</span></span>|  
|`ShowPercentage`|<span data-ttu-id="5431a-123">Gradyan üzerinde bir yüzde görüntülenip görüntülenmeyeceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="5431a-123">Indicates whether to display a percentage over the gradient.</span></span>|  
|`ShowValue`|<span data-ttu-id="5431a-124">Geçerli değerin gradyan üzerinde görüntülenip görüntülenmeyeceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="5431a-124">Indicates whether to display the current value over the gradient.</span></span>|  
|`ShowGradient`|<span data-ttu-id="5431a-125">İzleme çubuğunun geçerli değeri gösteren bir renk gradyanı görüntülenip görüntülenmeyeceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="5431a-125">Indicates whether the track bar should display a color gradient showing the current value.</span></span>|  
|-   `Value`|<span data-ttu-id="5431a-126">İzleme çubuğunun geçerli değerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="5431a-126">Specifies the current value of the track bar.</span></span>|  
  
 <span data-ttu-id="5431a-127">Aşağıdaki tabloda, özellik değiştirilen olay ve olayı oluşturan yöntemi `FlashTrackBar:` tarafından tanımlanan ek Üyeler gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="5431a-127">The following table shows additional members defined by `FlashTrackBar:` the property-changed event and the method that raises the event.</span></span>  
  
|<span data-ttu-id="5431a-128">Üye</span><span class="sxs-lookup"><span data-stu-id="5431a-128">Member</span></span>|<span data-ttu-id="5431a-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5431a-129">Description</span></span>|  
|------------|-----------------|  
|`ValueChanged`|<span data-ttu-id="5431a-130">İzleme çubuğunun `Value` özelliği değiştiğinde harekete geçirilen olay.</span><span class="sxs-lookup"><span data-stu-id="5431a-130">The event that is raised when the `Value` property of the track bar changes.</span></span>|  
|`OnValueChanged`|<span data-ttu-id="5431a-131">`ValueChanged` olayını oluşturan yöntem.</span><span class="sxs-lookup"><span data-stu-id="5431a-131">The method that raises the `ValueChanged` event.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="5431a-132">`FlashTrackBar`, olay verileri için <xref:System.EventArgs> sınıfını ve olay temsilcisi için <xref:System.EventHandler> kullanır.</span><span class="sxs-lookup"><span data-stu-id="5431a-132">`FlashTrackBar` uses the <xref:System.EventArgs> class for event data and <xref:System.EventHandler> for the event delegate.</span></span>  
  
 <span data-ttu-id="5431a-133">Karşılık gelen *EventName* olaylarını işlemek için `FlashTrackBar` <xref:System.Windows.Forms.Control?displayProperty=nameWithType>devralan aşağıdaki yöntemleri geçersiz kılar:</span><span class="sxs-lookup"><span data-stu-id="5431a-133">To handle the corresponding *EventName* events, `FlashTrackBar` overrides the following methods that it inherits from <xref:System.Windows.Forms.Control?displayProperty=nameWithType>:</span></span>  
  
- <xref:System.Windows.Forms.Control.OnPaint%2A>  
  
- <xref:System.Windows.Forms.Control.OnMouseDown%2A>  
  
- <xref:System.Windows.Forms.Control.OnMouseMove%2A>  
  
- <xref:System.Windows.Forms.Control.OnMouseUp%2A>  
  
- <xref:System.Windows.Forms.Control.OnResize%2A>  
  
 <span data-ttu-id="5431a-134">Karşılık gelen özellik tarafından değiştirilen olayları işlemek için `FlashTrackBar` <xref:System.Windows.Forms.Control?displayProperty=nameWithType>devraldığı aşağıdaki yöntemleri geçersiz kılar:</span><span class="sxs-lookup"><span data-stu-id="5431a-134">To handle the corresponding property-changed events, `FlashTrackBar` overrides the following methods that it inherits from <xref:System.Windows.Forms.Control?displayProperty=nameWithType>:</span></span>  
  
- <xref:System.Windows.Forms.Control.OnBackColorChanged%2A>  
  
- <xref:System.Windows.Forms.Control.OnBackgroundImageChanged%2A>  
  
- <xref:System.Windows.Forms.Control.OnTextChanged%2A>  
  
## <a name="example"></a><span data-ttu-id="5431a-135">Örnek</span><span class="sxs-lookup"><span data-stu-id="5431a-135">Example</span></span>  
 <span data-ttu-id="5431a-136">`FlashTrackBar` denetimi, aşağıdaki kod listelerinde gösterilen iki UI türü düzenleyicilerini `FlashTrackBarValueEditor` ve `FlashTrackBarDarkenByEditor`tanımlar.</span><span class="sxs-lookup"><span data-stu-id="5431a-136">The `FlashTrackBar` control defines two UI type editors, `FlashTrackBarValueEditor` and `FlashTrackBarDarkenByEditor`, which are shown in the following code listings.</span></span> <span data-ttu-id="5431a-137">`HostApp` sınıfı bir Windows formunda `FlashTrackBar` denetimini kullanır.</span><span class="sxs-lookup"><span data-stu-id="5431a-137">The `HostApp` class uses the `FlashTrackBar` control on a Windows Form.</span></span>  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#1)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#1)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBarDarkenByEditor.cs#10)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBarDarkenByEditor.vb#10)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBarValueEditor.cs#20)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBarValueEditor.vb#20)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/HostApp.cs#30)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/HostApp.vb#30)]  
  
## <a name="see-also"></a><span data-ttu-id="5431a-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5431a-138">See also</span></span>

- <span data-ttu-id="5431a-139">[Tasarım zamanı desteğini genişletme](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="5431a-139">[Extending Design-Time Support](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))</span></span>
- [<span data-ttu-id="5431a-140">Windows Forms Denetimi Geliştirmenin Esasları</span><span class="sxs-lookup"><span data-stu-id="5431a-140">Windows Forms Control Development Basics</span></span>](windows-forms-control-development-basics.md)
