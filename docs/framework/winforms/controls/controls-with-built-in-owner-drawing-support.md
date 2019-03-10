---
title: Yerleşik Sahip Çizimi Destekli Denetimler
ms.date: 03/30/2017
helpviewer_keywords:
- drawing [Windows Forms], owner
- drawing [Windows Forms], custom
- controls [Windows Forms], changing appearance
- custom drawing
- owner drawing
ms.assetid: 3823d01e-9610-43e6-864d-99f9b7c2b351
ms.openlocfilehash: 50f180f2f3fe825f617ae441906a7414a6b8bced
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57707367"
---
# <a name="controls-with-built-in-owner-drawing-support"></a><span data-ttu-id="72312-102">Yerleşik Sahip Çizimi Destekli Denetimler</span><span class="sxs-lookup"><span data-stu-id="72312-102">Controls with Built-In Owner-Drawing Support</span></span>
<span data-ttu-id="72312-103">Sahip çizim olarak da bilinen özel çizim olduğundan, Windows Forms içinde belirli denetimlerin görünümünü değiştirmek için kullanılan bir tekniktir.</span><span class="sxs-lookup"><span data-stu-id="72312-103">Owner drawing in Windows Forms, which is also known as custom drawing, is a technique for changing the visual appearance of certain controls.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="72312-104">Öğesinden türetilen sınıfları birlikte kullanıldığı senaryolar için bu konudaki "control" sözcüğü kullanılan <xref:System.Windows.Forms.Control> veya <xref:System.ComponentModel.Component>.</span><span class="sxs-lookup"><span data-stu-id="72312-104">The word "control" in this topic is used to mean classes that derive from either <xref:System.Windows.Forms.Control> or <xref:System.ComponentModel.Component>.</span></span>  
  
 <span data-ttu-id="72312-105">Genellikle, Windows boyama otomatik olarak özellik ayarları gibi kullanarak işler <xref:System.Windows.Forms.Control.BackColor%2A> denetiminin görünümünü belirlemek için.</span><span class="sxs-lookup"><span data-stu-id="72312-105">Typically, Windows handles painting automatically by using property settings such as <xref:System.Windows.Forms.Control.BackColor%2A> to determine the appearance of a control.</span></span> <span data-ttu-id="72312-106">Sahip çizim özelliklerini kullanarak mevcut olmayan öğeleri görünümünü değiştirme boyama işleminin yararlanın.</span><span class="sxs-lookup"><span data-stu-id="72312-106">With owner drawing, you take over the painting process, changing elements of appearance that are not available by using properties.</span></span> <span data-ttu-id="72312-107">Örneğin, çoğu denetim görüntülenen metnin rengini ayarlamanıza olanak tanıyan, ancak tek bir renge sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="72312-107">For example, many controls let you set the color of the text that is displayed, but you are limited to a single color.</span></span> <span data-ttu-id="72312-108">Sahip çizim, metnin bir bölümünü siyah ve kırmızı bir bölümü görüntüleme gibi işlemler yapmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="72312-108">Owner drawing enables you to do things like display part of the text in black and part in red.</span></span>  
  
 <span data-ttu-id="72312-109">Uygulamada, sahip çizim grafik bir form üzerinde çizim benzerdir.</span><span class="sxs-lookup"><span data-stu-id="72312-109">In practice, owner drawing is similar to drawing graphics on a form.</span></span> <span data-ttu-id="72312-110">Örneğin, grafik yöntemlerini işleyici formun için kullanabileceğinizi <xref:System.Windows.Forms.Control.Paint> benzetmek için olay bir `ListBox` denetimidir, ancak sahip tüm kullanıcı etkileşimi işlemek için kendi kodunuzu yazma.</span><span class="sxs-lookup"><span data-stu-id="72312-110">For example, you could use graphics methods in a handler for the form's <xref:System.Windows.Forms.Control.Paint> event to emulate a `ListBox` control, but you would have to write your own code to handle all user interaction.</span></span> <span data-ttu-id="72312-111">Sahip çizim denetimi içeriğini çizmek için kodunuzu kullanır ancak Aksi takdirde tüm iç özellikleri korur.</span><span class="sxs-lookup"><span data-stu-id="72312-111">With owner drawing, the control uses your code to draw its contents but otherwise retains all its intrinsic capabilities.</span></span> <span data-ttu-id="72312-112">Her öğesi denetiminde çizin veya diğer yönleri her öğe için varsayılan görünümünü kullanırken her öğe bazı yönlerini özelleştirmek için grafik yöntemlerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="72312-112">You can use graphics methods to draw each item in the control or to customize some aspects of each item while you use the default appearance for other aspects of each item.</span></span>  
  
## <a name="owner-drawing-in-windows-forms-controls"></a><span data-ttu-id="72312-113">Sahip çizim Windows Forms denetimleri</span><span class="sxs-lookup"><span data-stu-id="72312-113">Owner Drawing in Windows Forms Controls</span></span>  
 <span data-ttu-id="72312-114">Sahip çizim destekleyen denetimleri gerçekleştirmek için genellikle bir özellik kümesi ve bir veya daha fazla olayları işlemek.</span><span class="sxs-lookup"><span data-stu-id="72312-114">To perform owner drawing in controls that support it, you will typically set one property and handle one or more events.</span></span>  
  
 <span data-ttu-id="72312-115">Çoğu denetim çizme, destek sahip bir `OwnerDraw` veya `DrawMode` denetimi, çizim ilgili olay veya olay kendisini boyar oluşturup oluşturmayacağını belirten özellik.</span><span class="sxs-lookup"><span data-stu-id="72312-115">Most controls that support owner drawing have an `OwnerDraw` or `DrawMode` property that indicates whether the control will raise its drawing-related event or events when it paints itself.</span></span>  
  
 <span data-ttu-id="72312-116">Sahip olmayan denetimleri bir `OwnerDraw` veya `DrawMode` özelliği `DataGridView` otomatik olarak gerçekleşen çizim olayları sağlayan bir denetimi ve `ToolStrip` kendi bir dış işleme sınıfı kullanılarak çizilir denetimi Çizim ile ilgili olayları.</span><span class="sxs-lookup"><span data-stu-id="72312-116">Controls that do not have an `OwnerDraw` or `DrawMode` property include the `DataGridView` control, which provides drawing events that occur automatically, and the `ToolStrip` control, which is drawn using an external rendering class that has its own drawing-related events.</span></span>  
  
 <span data-ttu-id="72312-117">Olayları çizim birçok farklı türdeki vardır, ancak tek bir öğe içinde bir denetim çizmek için tipik bir çizim olayı oluşur.</span><span class="sxs-lookup"><span data-stu-id="72312-117">There are many different kinds of drawing events, but a typical drawing event occurs in order to draw a single item within a control.</span></span> <span data-ttu-id="72312-118">Olay işleyicisini alır bir `EventArgs` çizilen öğe hakkında bilgiler içerir ve kullandığınız araçlara nesne çizmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="72312-118">The event handler receives an `EventArgs` object that contains information about the item being drawn and tools you can use to draw it.</span></span> <span data-ttu-id="72312-119">Örneğin, bu nesnenin üst koleksiyon içindeki öğenin dizin numarasını genellikle içerir bir <xref:System.Drawing.Rectangle> belirten öğenin sınırları görüntülemek ve <xref:System.Drawing.Graphics> Boya yöntemleri çağırmak için nesne.</span><span class="sxs-lookup"><span data-stu-id="72312-119">For example, this object typically contains the item's index number within its parent collection, a <xref:System.Drawing.Rectangle> that indicates the item's display boundaries, and a <xref:System.Drawing.Graphics> object for calling paint methods.</span></span> <span data-ttu-id="72312-120">Bazı olaylar için `EventArgs` nesne öğesi ve varsayılan olarak arka plan ya da bir odak dikdörtgeni gibi bazı yönlerini öğesi boyamak için çağırabileceğiniz yöntemler hakkında ek bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="72312-120">For some events, the `EventArgs` object provides additional information about the item and methods that you can call to paint some aspects of the item by default, such as the background or a focus rectangle.</span></span>  
  
 <span data-ttu-id="72312-121">Sahip tarafından çizilmiş özelleştirmelerinizi içeren yeniden kullanılabilir bir denetim oluşturmak için sahip çizim destekleyen bir denetim sınıfından türeyen yeni bir sınıf oluşturun.</span><span class="sxs-lookup"><span data-stu-id="72312-121">To create a reusable control that contains your owner-drawn customizations, create a new class that derives from a control class that supports owner drawing.</span></span> <span data-ttu-id="72312-122">Çizim olayları işleme yerine sahip çizimi kodunuzu geçersiz kılmalar için uygun dahil `On` *EventName* yöntemi veya yeni yöntemler.</span><span class="sxs-lookup"><span data-stu-id="72312-122">Rather than handling drawing events, include your owner-drawing code in overrides for the appropriate `On`*EventName* method or methods in the new class.</span></span> <span data-ttu-id="72312-123">Temel sınıfı çağırın emin `On` *EventName* yöntemini veya yöntemlerini bu durumda kullanıcı denetiminizin sahip çizimi olayları işlemek ve ek özelleştirme sağlayın.</span><span class="sxs-lookup"><span data-stu-id="72312-123">Make sure that you call the base class `On`*EventName* method or methods in this case so that users of your control can handle owner-drawing events and provide additional customization.</span></span>  
  
 <span data-ttu-id="72312-124">Tüm .NET Framework sürümlerinde çizim aşağıdaki Windows Forms denetimleri destek sahibi:</span><span class="sxs-lookup"><span data-stu-id="72312-124">The following Windows Forms controls support owner drawing in all versions of the .NET Framework:</span></span>  
  
-   <xref:System.Windows.Forms.ListBox>  
  
-   <xref:System.Windows.Forms.ComboBox>  
  
-   <span data-ttu-id="72312-125"><xref:System.Windows.Forms.MenuItem> (tarafından kullanılan <xref:System.Windows.Forms.MainMenu> ve <xref:System.Windows.Forms.ContextMenu>)</span><span class="sxs-lookup"><span data-stu-id="72312-125"><xref:System.Windows.Forms.MenuItem> (used by <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu>)</span></span>  
  
-   <xref:System.Windows.Forms.TabControl>  
  
 <span data-ttu-id="72312-126">Sahip çizim yalnızca aşağıdaki denetimleri desteği [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="72312-126">The following controls support owner drawing only in [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]:</span></span>  
  
-   <xref:System.Windows.Forms.ToolTip>  
  
-   <xref:System.Windows.Forms.ListView>  
  
-   <xref:System.Windows.Forms.TreeView>  
  
 <span data-ttu-id="72312-127">Sahip çizim ve yeni olan aşağıdaki denetimleri desteği [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="72312-127">The following controls support owner drawing and are new in [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]:</span></span>  
  
-   <xref:System.Windows.Forms.DataGridView>  
  
-   <xref:System.Windows.Forms.ToolStrip>  
  
 <span data-ttu-id="72312-128">Aşağıdaki bölümlerde her bu denetimleri için ek ayrıntılar sağlayın.</span><span class="sxs-lookup"><span data-stu-id="72312-128">The following sections provide additional details for each of these controls.</span></span>  
  
### <a name="listbox-and-combobox-controls"></a><span data-ttu-id="72312-129">ListBox ve ComboBox denetimleri</span><span class="sxs-lookup"><span data-stu-id="72312-129">ListBox and ComboBox Controls</span></span>  
 <span data-ttu-id="72312-130"><xref:System.Windows.Forms.ListBox> Ve <xref:System.Windows.Forms.ComboBox> denetimlerini bir boyutu da şirket içinde veya farklı boyutlarda denetimindeki öğeyi çizmek etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="72312-130">The <xref:System.Windows.Forms.ListBox> and <xref:System.Windows.Forms.ComboBox> controls enable you to draw individual items in the control either all in one size, or in varying sizes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="72312-131">Ancak <xref:System.Windows.Forms.CheckedListBox> denetim türetilen <xref:System.Windows.Forms.ListBox> denetimi, bunu desteklemiyor sahip çizimi.</span><span class="sxs-lookup"><span data-stu-id="72312-131">Although the <xref:System.Windows.Forms.CheckedListBox> control is derived from the <xref:System.Windows.Forms.ListBox> control, it does not support owner drawing.</span></span>  
  
 <span data-ttu-id="72312-132">Her bir öğe aynı boyutta çizmek için ayarlanmış `DrawMode` özelliğini <xref:System.Windows.Forms.DrawMode.OwnerDrawFixed> ve işleme `DrawItem` olay.</span><span class="sxs-lookup"><span data-stu-id="72312-132">To draw each item the same size, set the `DrawMode` property to <xref:System.Windows.Forms.DrawMode.OwnerDrawFixed> and handle the `DrawItem` event.</span></span>  
  
 <span data-ttu-id="72312-133">Başka bir boyutu kullanarak her bir öğeyi çizmek için ayarlanmış `DrawMode` özelliğini <xref:System.Windows.Forms.DrawMode.OwnerDrawVariable> ve her ikisini birden işlemek `MeasureItem` ve `DrawItem` olayları.</span><span class="sxs-lookup"><span data-stu-id="72312-133">To draw each item using a different size, set the `DrawMode` property to <xref:System.Windows.Forms.DrawMode.OwnerDrawVariable> and handle both the `MeasureItem` and `DrawItem` events.</span></span> <span data-ttu-id="72312-134">`MeasureItem` Olayı sağlar, önce bir öğenin boyutunu belirtmek `DrawItem` olayı, o öğe için oluşur.</span><span class="sxs-lookup"><span data-stu-id="72312-134">The `MeasureItem` event lets you indicate the size of an item before the `DrawItem` event occurs for that item.</span></span>  
  
 <span data-ttu-id="72312-135">Kod örnekleri dahil olmak üzere daha fazla bilgi için aşağıdaki konulara bakın:</span><span class="sxs-lookup"><span data-stu-id="72312-135">For more information, including code examples, see the following topics:</span></span>  
  
-   <xref:System.Windows.Forms.ListBox.DrawMode%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ListBox.MeasureItem?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ListBox.DrawItem?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ComboBox.DrawMode%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ComboBox.MeasureItem?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ComboBox.DrawItem?displayProperty=nameWithType>  
  
-   [<span data-ttu-id="72312-136">Nasıl yapılır: Bir ComboBox denetiminde değişken boyutlu metin oluşturma</span><span class="sxs-lookup"><span data-stu-id="72312-136">How to: Create Variable Sized Text in a ComboBox Control</span></span>](how-to-create-variable-sized-text-in-a-combobox-control.md)  
  
### <a name="menuitem-component"></a><span data-ttu-id="72312-137">MenuItem bileşeni</span><span class="sxs-lookup"><span data-stu-id="72312-137">MenuItem Component</span></span>  
 <span data-ttu-id="72312-138"><xref:System.Windows.Forms.MenuItem> Bileşenini temsil eder, bir tek menü öğesi bir <xref:System.Windows.Forms.MainMenu> veya <xref:System.Windows.Forms.ContextMenu> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="72312-138">The <xref:System.Windows.Forms.MenuItem> component represents a single menu item in a <xref:System.Windows.Forms.MainMenu> or <xref:System.Windows.Forms.ContextMenu> component.</span></span>  
  
 <span data-ttu-id="72312-139">Çizmek için bir <xref:System.Windows.Forms.MenuItem>ayarlayın, `OwnerDraw` özelliğini `true` ve işlemek, `DrawItem` olay.</span><span class="sxs-lookup"><span data-stu-id="72312-139">To draw a <xref:System.Windows.Forms.MenuItem>, set its `OwnerDraw` property to `true` and handle its `DrawItem` event.</span></span> <span data-ttu-id="72312-140">Önce menü öğesinin boyutunu özelleştirmek için `DrawItem` bir olay oluşursa, öğenin işlemek `MeasureItem` olay.</span><span class="sxs-lookup"><span data-stu-id="72312-140">To customize the size of the menu item before the `DrawItem` event occurs, handle the item's `MeasureItem` event.</span></span>  
  
 <span data-ttu-id="72312-141">Kod örnekleri dahil olmak üzere daha fazla bilgi için aşağıdaki başvuru konularına bakın:</span><span class="sxs-lookup"><span data-stu-id="72312-141">For more information, including code examples, see the following reference topics:</span></span>  
  
-   <xref:System.Windows.Forms.MenuItem.OwnerDraw%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.MenuItem.DrawItem?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.MenuItem.MeasureItem?displayProperty=nameWithType>  
  
### <a name="tabcontrol-control"></a><span data-ttu-id="72312-142">TabControl Denetimi</span><span class="sxs-lookup"><span data-stu-id="72312-142">TabControl Control</span></span>  
 <span data-ttu-id="72312-143"><xref:System.Windows.Forms.TabControl> Denetim ayrı sekmeler denetimi çizmek sağlar.</span><span class="sxs-lookup"><span data-stu-id="72312-143">The <xref:System.Windows.Forms.TabControl> control enables you to draw individual tabs in the control.</span></span> <span data-ttu-id="72312-144">Sahip çizim yalnızca sekmeler etkiler; <xref:System.Windows.Forms.TabPage> içeriği etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="72312-144">Owner drawing affects only the tabs; the <xref:System.Windows.Forms.TabPage> contents are not affected.</span></span>  
  
 <span data-ttu-id="72312-145">Her sekme çizim için bir <xref:System.Windows.Forms.TabControl>ayarlayın `DrawMode` özelliğini <xref:System.Windows.Forms.TabDrawMode.OwnerDrawFixed> ve işleme `DrawItem` olay.</span><span class="sxs-lookup"><span data-stu-id="72312-145">To draw each tab in a <xref:System.Windows.Forms.TabControl>, set the `DrawMode` property to <xref:System.Windows.Forms.TabDrawMode.OwnerDrawFixed> and handle the `DrawItem` event.</span></span> <span data-ttu-id="72312-146">Sekme denetimi görünür olduğunda bu olay her sekme için bir kez gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="72312-146">This event occurs once for each tab only when the tab is visible in the control.</span></span>  
  
 <span data-ttu-id="72312-147">Kod örnekleri dahil olmak üzere daha fazla bilgi için aşağıdaki başvuru konularına bakın:</span><span class="sxs-lookup"><span data-stu-id="72312-147">For more information, including code examples, see the following reference topics:</span></span>  
  
-   <xref:System.Windows.Forms.TabControl.DrawMode%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.TabControl.DrawItem?displayProperty=nameWithType>  
  
### <a name="tooltip-component"></a><span data-ttu-id="72312-148">ToolTip Bileşeni</span><span class="sxs-lookup"><span data-stu-id="72312-148">ToolTip Component</span></span>  
 <span data-ttu-id="72312-149"><xref:System.Windows.Forms.ToolTip> Bileşeni tüm araç ipucu görüntülendiğinde çizmek etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="72312-149">The <xref:System.Windows.Forms.ToolTip> component enables you to draw the entire ToolTip when it is displayed.</span></span>  
  
 <span data-ttu-id="72312-150">Çizmek için bir <xref:System.Windows.Forms.ToolTip>ayarlayın, `OwnerDraw` özelliğini `true` ve işlemek, `Draw` olay.</span><span class="sxs-lookup"><span data-stu-id="72312-150">To draw a <xref:System.Windows.Forms.ToolTip>, set its `OwnerDraw` property to `true` and handle its `Draw` event.</span></span> <span data-ttu-id="72312-151">Boyutunu özelleştirmek için <xref:System.Windows.Forms.ToolTip> önce `Draw` olay geçildikten tanıtıcı `Popup` olay ve kümesi <xref:System.Windows.Forms.PopupEventArgs.ToolTipSize%2A> olay işleyicisi özelliği.</span><span class="sxs-lookup"><span data-stu-id="72312-151">To customize the size of the <xref:System.Windows.Forms.ToolTip> before the `Draw` event occurs, handle the `Popup` event and set the <xref:System.Windows.Forms.PopupEventArgs.ToolTipSize%2A> property in the event handler.</span></span>  
  
 <span data-ttu-id="72312-152">Kod örnekleri dahil olmak üzere daha fazla bilgi için aşağıdaki başvuru konularına bakın:</span><span class="sxs-lookup"><span data-stu-id="72312-152">For more information, including code examples, see the following reference topics:</span></span>  
  
-   <xref:System.Windows.Forms.ToolTip.OwnerDraw%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ToolTip.Draw?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ToolTip.Popup?displayProperty=nameWithType>  
  
### <a name="listview-control"></a><span data-ttu-id="72312-153">ListView Denetimi</span><span class="sxs-lookup"><span data-stu-id="72312-153">ListView Control</span></span>  
 <span data-ttu-id="72312-154"><xref:System.Windows.Forms.ListView> , Tek tek öğeleri, alt öğeler ve sütun üst bilgilerini denetimi çizmek denetim olanağı sağlar.</span><span class="sxs-lookup"><span data-stu-id="72312-154">The <xref:System.Windows.Forms.ListView> control enables you to draw individual items, subitems, and column headers in the control.</span></span>  
  
 <span data-ttu-id="72312-155">Sahip çizim denetiminde etkinleştirmek için `OwnerDraw` özelliğini `true`.</span><span class="sxs-lookup"><span data-stu-id="72312-155">To enable owner drawing in the control, set the `OwnerDraw` property to `true`.</span></span>  
  
 <span data-ttu-id="72312-156">Her öğesi denetiminde çizmek için tanıtıcı `DrawItem` olay.</span><span class="sxs-lookup"><span data-stu-id="72312-156">To draw each item in the control, handle the `DrawItem` event.</span></span>  
  
 <span data-ttu-id="72312-157">Her alt veya sütun başlığı denetimi çizmek için zaman <xref:System.Windows.Forms.ListView.View%2A> özelliği <xref:System.Windows.Forms.View.Details>, tanıtıcı `DrawSubItem` ve `DrawColumnHeader` olayları.</span><span class="sxs-lookup"><span data-stu-id="72312-157">To draw each subitem or column header in the control when the <xref:System.Windows.Forms.ListView.View%2A> property is set to <xref:System.Windows.Forms.View.Details>, handle the `DrawSubItem` and `DrawColumnHeader` events.</span></span>  
  
 <span data-ttu-id="72312-158">Kod örnekleri dahil olmak üzere daha fazla bilgi için aşağıdaki başvuru konularına bakın:</span><span class="sxs-lookup"><span data-stu-id="72312-158">For more information, including code examples, see the following reference topics:</span></span>  
  
-   <xref:System.Windows.Forms.ListView.OwnerDraw%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ListView.DrawItem?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ListView.DrawSubItem?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ListView.DrawColumnHeader?displayProperty=nameWithType>  
  
### <a name="treeview-control"></a><span data-ttu-id="72312-159">TreeView Denetimi</span><span class="sxs-lookup"><span data-stu-id="72312-159">TreeView Control</span></span>  
 <span data-ttu-id="72312-160"><xref:System.Windows.Forms.TreeView> , Tek tek düğümlere denetimi çizmek denetim olanağı sağlar.</span><span class="sxs-lookup"><span data-stu-id="72312-160">The <xref:System.Windows.Forms.TreeView> control enables you to draw individual nodes in the control.</span></span>  
  
 <span data-ttu-id="72312-161">Yalnızca her bir düğümünde görüntülenen metni çizmek için ayarlanmış `DrawMode` özelliğini <xref:System.Windows.Forms.TreeViewDrawMode.OwnerDrawText> ve işleme `DrawNode` metnini çizmek için olay.</span><span class="sxs-lookup"><span data-stu-id="72312-161">To draw only the text displayed in each node, set the `DrawMode` property to <xref:System.Windows.Forms.TreeViewDrawMode.OwnerDrawText> and handle the `DrawNode` event to draw the text.</span></span>  
  
 <span data-ttu-id="72312-162">Her düğümün tüm öğelerini çizmek için ayarlanmış `DrawMode` özelliğini <xref:System.Windows.Forms.TreeViewDrawMode.OwnerDrawAll> ve işleme `DrawNode` ihtiyacınız kutuları, artı ve eksi işaretlerine, metni, simgeler denetlemek gibi ve düğümlerini bağlayan satırları hangi öğelerini çizmek için olay.</span><span class="sxs-lookup"><span data-stu-id="72312-162">To draw all elements of each node, set the `DrawMode` property to <xref:System.Windows.Forms.TreeViewDrawMode.OwnerDrawAll> and handle the `DrawNode` event to draw whichever elements you need, such as text, icons, check boxes, plus and minus signs, and lines connecting the nodes.</span></span>  
  
 <span data-ttu-id="72312-163">Kod örnekleri dahil olmak üzere daha fazla bilgi için aşağıdaki başvuru konularına bakın:</span><span class="sxs-lookup"><span data-stu-id="72312-163">For more information, including code examples, see the following reference topics:</span></span>  
  
-   <xref:System.Windows.Forms.TreeView.DrawMode%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.TreeView.DrawNode?displayProperty=nameWithType>  
  
### <a name="datagridview-control"></a><span data-ttu-id="72312-164">DataGridView Denetimi</span><span class="sxs-lookup"><span data-stu-id="72312-164">DataGridView Control</span></span>  
 <span data-ttu-id="72312-165"><xref:System.Windows.Forms.DataGridView> Denetimi denetiminde ayrı hücrelere ve satırları çizmek sağlar.</span><span class="sxs-lookup"><span data-stu-id="72312-165">The <xref:System.Windows.Forms.DataGridView> control enables you to draw individual cells and rows in the control.</span></span>  
  
 <span data-ttu-id="72312-166">Tek tek hücrelere çizmek için tanıtıcı `CellPainting` olay.</span><span class="sxs-lookup"><span data-stu-id="72312-166">To draw individual cells, handle the `CellPainting` event.</span></span>  
  
 <span data-ttu-id="72312-167">Tek bir satır veya satır öğelerini çizmek için birini veya ikisini birden işlemek `RowPrePaint` ve `RowPostPaint` olayları.</span><span class="sxs-lookup"><span data-stu-id="72312-167">To draw individual rows or elements of rows, handle one or both of the `RowPrePaint` and `RowPostPaint` events.</span></span> <span data-ttu-id="72312-168">`RowPrePaint` Olayı, bir satır hücrelerde boyanır önce oluşur ve `RowPostPaint` olay hücreleri boyanır sonra oluşur.</span><span class="sxs-lookup"><span data-stu-id="72312-168">The `RowPrePaint` event occurs before the cells in a row are painted, and the `RowPostPaint` event occurs after the cells are painted.</span></span> <span data-ttu-id="72312-169">Her iki olayları işleyebilir ve `CellPainting` satır arka plan, tek tek hücrelere ve satır ön plan ayrı olarak boyamak için olay veya burada ihtiyacınız ve varsayılan görüntüyü satırın diğer öğeleri kullanmak belirli özelleştirmeleri sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="72312-169">You can handle both events and the `CellPainting` event to paint row background, individual cells, and row foreground separately, or you can provide specific customizations where you need them and use the default display for other elements of the row.</span></span>  
  
 <span data-ttu-id="72312-170">Kod örnekleri dahil olmak üzere daha fazla bilgi için aşağıdaki konulara bakın:</span><span class="sxs-lookup"><span data-stu-id="72312-170">For more information, including code examples, see the following topics:</span></span>  
  
-   <xref:System.Windows.Forms.DataGridView.CellPainting>  
  
-   <xref:System.Windows.Forms.DataGridView.RowPrePaint>  
  
-   <xref:System.Windows.Forms.DataGridView.RowPostPaint>  
  
-   [<span data-ttu-id="72312-171">Nasıl yapılır: Windows Forms DataGridView denetiminde hücrelerin görünüşünü özelleştirme</span><span class="sxs-lookup"><span data-stu-id="72312-171">How to: Customize the Appearance of Cells in the Windows Forms DataGridView Control</span></span>](customize-the-appearance-of-cells-in-the-datagrid.md)  
  
-   [<span data-ttu-id="72312-172">Nasıl yapılır: Windows Forms DataGridView denetiminde satırların görünüşünü özelleştirme</span><span class="sxs-lookup"><span data-stu-id="72312-172">How to: Customize the Appearance of Rows in the Windows Forms DataGridView Control</span></span>](customize-the-appearance-of-rows-in-the-datagrid.md)  
  
### <a name="toolstrip-control"></a><span data-ttu-id="72312-173">ToolStrip Denetimi</span><span class="sxs-lookup"><span data-stu-id="72312-173">ToolStrip Control</span></span>  
 <span data-ttu-id="72312-174"><xref:System.Windows.Forms.ToolStrip> ve türetilen denetimler görünümlerini herhangi bir özelliği özelleştirmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="72312-174"><xref:System.Windows.Forms.ToolStrip> and derived controls enable you to customize any aspect of their appearance.</span></span>  
  
 <span data-ttu-id="72312-175">Özel işleme sağlamak için <xref:System.Windows.Forms.ToolStrip> denetimleri ayarlayın `Renderer` özelliği bir <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.ToolStripManager>, <xref:System.Windows.Forms.ToolStripPanel>, veya <xref:System.Windows.Forms.ToolStripContentPanel> için bir `ToolStripRenderer` nesnesi ve bir veya daha çok sayıda çizim olaylarının tarafından sağlanan işleme `ToolStripRenderer` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="72312-175">To provide custom rendering for <xref:System.Windows.Forms.ToolStrip> controls, set the `Renderer` property of a <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.ToolStripManager>, <xref:System.Windows.Forms.ToolStripPanel>, or <xref:System.Windows.Forms.ToolStripContentPanel> to a `ToolStripRenderer` object and handle one or more of the many drawing events provided by the `ToolStripRenderer` class.</span></span> <span data-ttu-id="72312-176">Alternatif olarak ayarlanmış bir `Renderer` kendi sınıfının bir örneğini özelliğini türetilen `ToolStripRenderer`, <xref:System.Windows.Forms.ToolStripProfessionalRenderer>, veya <xref:System.Windows.Forms.ToolStripSystemRenderer> uygulayan veya özel geçersiz kılar `On` *EventName* yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="72312-176">Alternatively, set a `Renderer` property to an instance of your own class derived from `ToolStripRenderer`, <xref:System.Windows.Forms.ToolStripProfessionalRenderer>, or <xref:System.Windows.Forms.ToolStripSystemRenderer> that implements or overrides specific `On`*EventName* methods.</span></span>  
  
 <span data-ttu-id="72312-177">Kod örnekleri dahil olmak üzere daha fazla bilgi için aşağıdaki konulara bakın:</span><span class="sxs-lookup"><span data-stu-id="72312-177">For more information, including code examples, see the following topics:</span></span>  
  
-   <xref:System.Windows.Forms.ToolStripRenderer>  
  
-   [<span data-ttu-id="72312-178">Nasıl yapılır: Windows Forms'ta ToolStrip denetimi için özel Oluşturucu Oluşturma ve</span><span class="sxs-lookup"><span data-stu-id="72312-178">How to: Create and Set a Custom Renderer for the ToolStrip Control in Windows Forms</span></span>](create-and-set-a-custom-renderer-for-the-toolstrip-control-in-wf.md)  
  
-   [<span data-ttu-id="72312-179">Nasıl yapılır: Bir ToolStrip denetimini özel olarak çizme</span><span class="sxs-lookup"><span data-stu-id="72312-179">How to: Custom Draw a ToolStrip Control</span></span>](how-to-custom-draw-a-toolstrip-control.md)  
  
## <a name="see-also"></a><span data-ttu-id="72312-180">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="72312-180">See also</span></span>
- [<span data-ttu-id="72312-181">Windows Forms'da Kullanılacak Denetimler</span><span class="sxs-lookup"><span data-stu-id="72312-181">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
