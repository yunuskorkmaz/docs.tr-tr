---
title: "Yerleşik Sahip Çizimi Destekli Denetimler"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- drawing [Windows Forms], owner
- drawing [Windows Forms], custom
- controls [Windows Forms], changing appearance
- custom drawing
- owner drawing
ms.assetid: 3823d01e-9610-43e6-864d-99f9b7c2b351
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: efd297dcc11005d6b6d47bb9ce3853a757046e8f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="controls-with-built-in-owner-drawing-support"></a><span data-ttu-id="ba122-102">Yerleşik Sahip Çizimi Destekli Denetimler</span><span class="sxs-lookup"><span data-stu-id="ba122-102">Controls with Built-In Owner-Drawing Support</span></span>
<span data-ttu-id="ba122-103">Sahip çizimi olarak da bilinen özel çizim olduğundan, Windows Forms içinde belirli denetimleri görsel görünümünü değiştirmek için bir tekniktir.</span><span class="sxs-lookup"><span data-stu-id="ba122-103">Owner drawing in Windows Forms, which is also known as custom drawing, is a technique for changing the visual appearance of certain controls.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ba122-104">Bu konudaki "Denetim" word herhangi birinden türetilen sınıflar anlamına kullanılacak <xref:System.Windows.Forms.Control> veya <xref:System.ComponentModel.Component>.</span><span class="sxs-lookup"><span data-stu-id="ba122-104">The word "control" in this topic is used to mean classes that derive from either <xref:System.Windows.Forms.Control> or <xref:System.ComponentModel.Component>.</span></span>  
  
 <span data-ttu-id="ba122-105">Genellikle, Windows boyama otomatik olarak özellik ayarları gibi kullanarak işler <xref:System.Windows.Forms.Control.BackColor%2A> denetiminin görünümünü belirlemek için.</span><span class="sxs-lookup"><span data-stu-id="ba122-105">Typically, Windows handles painting automatically by using property settings such as <xref:System.Windows.Forms.Control.BackColor%2A> to determine the appearance of a control.</span></span> <span data-ttu-id="ba122-106">Sahip çizimi ile özelliklerini kullanarak kullanılabilir olmayan öğeler görünümünü değiştirme boyama işleminin alın.</span><span class="sxs-lookup"><span data-stu-id="ba122-106">With owner drawing, you take over the painting process, changing elements of appearance that are not available by using properties.</span></span> <span data-ttu-id="ba122-107">Örneğin, birçok denetimler görüntülenen metnin rengini ayarlamanıza olanak sağlar, ancak tek bir rengi sınırlı olur.</span><span class="sxs-lookup"><span data-stu-id="ba122-107">For example, many controls let you set the color of the text that is displayed, but you are limited to a single color.</span></span> <span data-ttu-id="ba122-108">Sahip çizimi metnin bir bölümünü siyah ve kırmızı bölümünde görüntülemek gibi şeyler olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="ba122-108">Owner drawing enables you to do things like display part of the text in black and part in red.</span></span>  
  
 <span data-ttu-id="ba122-109">Uygulamada, grafik bir form üzerinde çizim sahip çizimi benzer.</span><span class="sxs-lookup"><span data-stu-id="ba122-109">In practice, owner drawing is similar to drawing graphics on a form.</span></span> <span data-ttu-id="ba122-110">Örneğin, grafik yöntemlerini işleyici formun için kullanabileceğinizi <xref:System.Windows.Forms.Control.Paint> benzetmek için olay bir `ListBox` denetimi, ancak sahip olabilir tüm kullanıcı etkileşimi işlemek için kendi kod yazmak.</span><span class="sxs-lookup"><span data-stu-id="ba122-110">For example, you could use graphics methods in a handler for the form's <xref:System.Windows.Forms.Control.Paint> event to emulate a `ListBox` control, but you would have to write your own code to handle all user interaction.</span></span> <span data-ttu-id="ba122-111">Çizim sahibi olan denetim içeriğini çizmek için kodunuzu kullanır, ancak Aksi takdirde tüm iç yeteneklerini korur.</span><span class="sxs-lookup"><span data-stu-id="ba122-111">With owner drawing, the control uses your code to draw its contents but otherwise retains all its intrinsic capabilities.</span></span> <span data-ttu-id="ba122-112">Her öğe, denetimi çizmek için veya diğer yönlerini her öğe için varsayılan görünümünü kullanırken her öğe bazı yönlerini özelleştirmek için grafik yöntemlerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ba122-112">You can use graphics methods to draw each item in the control or to customize some aspects of each item while you use the default appearance for other aspects of each item.</span></span>  
  
## <a name="owner-drawing-in-windows-forms-controls"></a><span data-ttu-id="ba122-113">Sahip çizimi Windows Forms denetimleri</span><span class="sxs-lookup"><span data-stu-id="ba122-113">Owner Drawing in Windows Forms Controls</span></span>  
 <span data-ttu-id="ba122-114">Sahip çizimi destekleyen denetimleri gerçekleştirmek için genellikle bir özellik ayarlama ve bir veya daha fazla olayları işlemek.</span><span class="sxs-lookup"><span data-stu-id="ba122-114">To perform owner drawing in controls that support it, you will typically set one property and handle one or more events.</span></span>  
  
 <span data-ttu-id="ba122-115">Çoğu denetim çizim Bu destek sahip bir `OwnerDraw` veya `DrawMode` denetimi çizim ilgili olay veya kendisi boyar olduğunda olayları oluşturup oluşturmayacağını belirten özellik.</span><span class="sxs-lookup"><span data-stu-id="ba122-115">Most controls that support owner drawing have an `OwnerDraw` or `DrawMode` property that indicates whether the control will raise its drawing-related event or events when it paints itself.</span></span>  
  
 <span data-ttu-id="ba122-116">Olmayan denetimleri bir `OwnerDraw` veya `DrawMode` özelliği `DataGridView` otomatik olarak gerçekleşir çizim olayları sağlar, Denetim ve `ToolStrip` kendi olan bir dış işleme sınıfı kullanılarak çizilip denetimi Çizim ilgili olaylar.</span><span class="sxs-lookup"><span data-stu-id="ba122-116">Controls that do not have an `OwnerDraw` or `DrawMode` property include the `DataGridView` control, which provides drawing events that occur automatically, and the `ToolStrip` control, which is drawn using an external rendering class that has its own drawing-related events.</span></span>  
  
 <span data-ttu-id="ba122-117">Olayları çizim birçok farklı türdeki vardır, ancak bir denetim içindeki tek bir öğe çizmek için tipik bir çizim olayı oluşur.</span><span class="sxs-lookup"><span data-stu-id="ba122-117">There are many different kinds of drawing events, but a typical drawing event occurs in order to draw a single item within a control.</span></span> <span data-ttu-id="ba122-118">Olay işleyicisini alır bir `EventArgs` çizilen öğeyle ilgili bilgiler içeren ve kullandığınız araçlara nesne çizmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ba122-118">The event handler receives an `EventArgs` object that contains information about the item being drawn and tools you can use to draw it.</span></span> <span data-ttu-id="ba122-119">Örneğin, bu nesne öğesi'nin dizin numarasını kendi üst koleksiyonundaki genellikle içeren bir <xref:System.Drawing.Rectangle> belirten öğesi'nin sınırları, görüntülemek ve bir <xref:System.Drawing.Graphics> boyama yöntemleri çağırmak için nesne.</span><span class="sxs-lookup"><span data-stu-id="ba122-119">For example, this object typically contains the item's index number within its parent collection, a <xref:System.Drawing.Rectangle> that indicates the item's display boundaries, and a <xref:System.Drawing.Graphics> object for calling paint methods.</span></span> <span data-ttu-id="ba122-120">Bazı olaylar için `EventArgs` nesnesi öğesi ve varsayılan olarak, arka plan veya odak dikdörtgeni gibi bazı yönlerini öğesi boyamak için çağırabilirsiniz yöntemleri hakkında ek bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="ba122-120">For some events, the `EventArgs` object provides additional information about the item and methods that you can call to paint some aspects of the item by default, such as the background or a focus rectangle.</span></span>  
  
 <span data-ttu-id="ba122-121">Sahip tarafından çizilmiş özelleştirmelerinizi içeren yeniden kullanılabilir bir denetim oluşturmak için sahip çizimi destekleyen bir denetim sınıfından türetilen yeni bir sınıf oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ba122-121">To create a reusable control that contains your owner-drawn customizations, create a new class that derives from a control class that supports owner drawing.</span></span> <span data-ttu-id="ba122-122">Çizim olayları işleme yerine çizimi kodunuzu geçersiz kılma işlemleri için uygun dahil `On` *EventName* yöntemini veya yöntemlerini Yeni sınıfta.</span><span class="sxs-lookup"><span data-stu-id="ba122-122">Rather than handling drawing events, include your owner-drawing code in overrides for the appropriate `On`*EventName* method or methods in the new class.</span></span> <span data-ttu-id="ba122-123">Taban sınıfı çağrı emin olun `On` *EventName* yöntemini veya yöntemlerini bu durumda böylece kullanıcılar denetiminizin çizimi olayları işlemek ve ek özelleştirme sağlar.</span><span class="sxs-lookup"><span data-stu-id="ba122-123">Make sure that you call the base class `On`*EventName* method or methods in this case so that users of your control can handle owner-drawing events and provide additional customization.</span></span>  
  
 <span data-ttu-id="ba122-124">.NET Framework'ün tüm sürümlerinde aşağıdaki Windows Forms denetimleri destek sahip çizimi:</span><span class="sxs-lookup"><span data-stu-id="ba122-124">The following Windows Forms controls support owner drawing in all versions of the .NET Framework:</span></span>  
  
-   <xref:System.Windows.Forms.ListBox>  
  
-   <xref:System.Windows.Forms.ComboBox>  
  
-   <span data-ttu-id="ba122-125"><xref:System.Windows.Forms.MenuItem>(tarafından kullanılan <xref:System.Windows.Forms.MainMenu> ve <xref:System.Windows.Forms.ContextMenu>)</span><span class="sxs-lookup"><span data-stu-id="ba122-125"><xref:System.Windows.Forms.MenuItem> (used by <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu>)</span></span>  
  
-   <xref:System.Windows.Forms.TabControl>  
  
 <span data-ttu-id="ba122-126">Sahip çizimi yalnızca aşağıdaki denetimleri Destek [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="ba122-126">The following controls support owner drawing only in [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]:</span></span>  
  
-   <xref:System.Windows.Forms.ToolTip>  
  
-   <xref:System.Windows.Forms.ListView>  
  
-   <xref:System.Windows.Forms.TreeView>  
  
 <span data-ttu-id="ba122-127">Sahip çizimi ve bu yeni aşağıdaki denetimleri Destek [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="ba122-127">The following controls support owner drawing and are new in [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]:</span></span>  
  
-   <xref:System.Windows.Forms.DataGridView>  
  
-   <xref:System.Windows.Forms.ToolStrip>  
  
 <span data-ttu-id="ba122-128">Aşağıdaki bölümlerde her bu denetimleri için ek ayrıntılar sağlanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ba122-128">The following sections provide additional details for each of these controls.</span></span>  
  
### <a name="listbox-and-combobox-controls"></a><span data-ttu-id="ba122-129">ListBox ve ComboBox denetimleri</span><span class="sxs-lookup"><span data-stu-id="ba122-129">ListBox and ComboBox Controls</span></span>  
 <span data-ttu-id="ba122-130"><xref:System.Windows.Forms.ListBox> Ve <xref:System.Windows.Forms.ComboBox> denetimleri ya da tüm bir boyut veya farklı boyutlarda denetiminde ayrı öğeleri Çiz olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="ba122-130">The <xref:System.Windows.Forms.ListBox> and <xref:System.Windows.Forms.ComboBox> controls enable you to draw individual items in the control either all in one size, or in varying sizes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ba122-131">Ancak <xref:System.Windows.Forms.CheckedListBox> denetim türetilir <xref:System.Windows.Forms.ListBox> denetimi, bunu desteklemiyor sahip çizimi.</span><span class="sxs-lookup"><span data-stu-id="ba122-131">Although the <xref:System.Windows.Forms.CheckedListBox> control is derived from the <xref:System.Windows.Forms.ListBox> control, it does not support owner drawing.</span></span>  
  
 <span data-ttu-id="ba122-132">Her bir öğe aynı boyutta çizmek için ayarlanmış `DrawMode` özelliğine <xref:System.Windows.Forms.DrawMode.OwnerDrawFixed> ve işlemek `DrawItem` olay.</span><span class="sxs-lookup"><span data-stu-id="ba122-132">To draw each item the same size, set the `DrawMode` property to <xref:System.Windows.Forms.DrawMode.OwnerDrawFixed> and handle the `DrawItem` event.</span></span>  
  
 <span data-ttu-id="ba122-133">Farklı bir boyut kullanarak her bir öğeyi çizmek için ayarlanmış `DrawMode` özelliğine <xref:System.Windows.Forms.DrawMode.OwnerDrawVariable> ve her ikisi de işlemek `MeasureItem` ve `DrawItem` olaylar.</span><span class="sxs-lookup"><span data-stu-id="ba122-133">To draw each item using a different size, set the `DrawMode` property to <xref:System.Windows.Forms.DrawMode.OwnerDrawVariable> and handle both the `MeasureItem` and `DrawItem` events.</span></span> <span data-ttu-id="ba122-134">`MeasureItem` Olayı sağlar, önce bir öğenin boyutunu belirtmek `DrawItem` olayı, o öğe için oluşur.</span><span class="sxs-lookup"><span data-stu-id="ba122-134">The `MeasureItem` event lets you indicate the size of an item before the `DrawItem` event occurs for that item.</span></span>  
  
 <span data-ttu-id="ba122-135">Kod örnekleri dahil olmak üzere daha fazla bilgi için aşağıdaki konulara bakın:</span><span class="sxs-lookup"><span data-stu-id="ba122-135">For more information, including code examples, see the following topics:</span></span>  
  
-   <xref:System.Windows.Forms.ListBox.DrawMode%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ListBox.MeasureItem?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ListBox.DrawItem?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ComboBox.DrawMode%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ComboBox.MeasureItem?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ComboBox.DrawItem?displayProperty=nameWithType>  
  
-   [<span data-ttu-id="ba122-136">Nasıl yapılır: ComboBox Denetiminde Değişken Boyutlu Metin Oluşturma</span><span class="sxs-lookup"><span data-stu-id="ba122-136">How to: Create Variable Sized Text in a ComboBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-create-variable-sized-text-in-a-combobox-control.md)  
  
### <a name="menuitem-component"></a><span data-ttu-id="ba122-137">MenuItem bileşeni</span><span class="sxs-lookup"><span data-stu-id="ba122-137">MenuItem Component</span></span>  
 <span data-ttu-id="ba122-138"><xref:System.Windows.Forms.MenuItem> Bileşen bir tek menü öğesini temsil eden bir <xref:System.Windows.Forms.MainMenu> veya <xref:System.Windows.Forms.ContextMenu> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="ba122-138">The <xref:System.Windows.Forms.MenuItem> component represents a single menu item in a <xref:System.Windows.Forms.MainMenu> or <xref:System.Windows.Forms.ContextMenu> component.</span></span>  
  
 <span data-ttu-id="ba122-139">Çizmek için bir <xref:System.Windows.Forms.MenuItem>ayarlayın, `OwnerDraw` özelliğine `true` ve işlemek kendi `DrawItem` olay.</span><span class="sxs-lookup"><span data-stu-id="ba122-139">To draw a <xref:System.Windows.Forms.MenuItem>, set its `OwnerDraw` property to `true` and handle its `DrawItem` event.</span></span> <span data-ttu-id="ba122-140">Menü öğesi önce boyutunu özelleştirmek için `DrawItem` olayı oluşur, tanıtıcı öğesi'nin `MeasureItem` olay.</span><span class="sxs-lookup"><span data-stu-id="ba122-140">To customize the size of the menu item before the `DrawItem` event occurs, handle the item's `MeasureItem` event.</span></span>  
  
 <span data-ttu-id="ba122-141">Kod örnekleri dahil olmak üzere daha fazla bilgi için aşağıdaki başvuru konularına bakın:</span><span class="sxs-lookup"><span data-stu-id="ba122-141">For more information, including code examples, see the following reference topics:</span></span>  
  
-   <xref:System.Windows.Forms.MenuItem.OwnerDraw%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.MenuItem.DrawItem?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.MenuItem.MeasureItem?displayProperty=nameWithType>  
  
### <a name="tabcontrol-control"></a><span data-ttu-id="ba122-142">TabControl Denetimi</span><span class="sxs-lookup"><span data-stu-id="ba122-142">TabControl Control</span></span>  
 <span data-ttu-id="ba122-143"><xref:System.Windows.Forms.TabControl> Denetim tek tek sekmeler denetiminde Çiz olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="ba122-143">The <xref:System.Windows.Forms.TabControl> control enables you to draw individual tabs in the control.</span></span> <span data-ttu-id="ba122-144">Sahip çizimi yalnızca sekmeler etkiler; <xref:System.Windows.Forms.TabPage> içeriği etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="ba122-144">Owner drawing affects only the tabs; the <xref:System.Windows.Forms.TabPage> contents are not affected.</span></span>  
  
 <span data-ttu-id="ba122-145">Her sekme çizmek için bir <xref:System.Windows.Forms.TabControl>ayarlayın `DrawMode` özelliğine <xref:System.Windows.Forms.TabDrawMode.OwnerDrawFixed> ve işlemek `DrawItem` olay.</span><span class="sxs-lookup"><span data-stu-id="ba122-145">To draw each tab in a <xref:System.Windows.Forms.TabControl>, set the `DrawMode` property to <xref:System.Windows.Forms.TabDrawMode.OwnerDrawFixed> and handle the `DrawItem` event.</span></span> <span data-ttu-id="ba122-146">Sekme denetimi görünür olduğunda bu olay her sekme için bir kez oluşur.</span><span class="sxs-lookup"><span data-stu-id="ba122-146">This event occurs once for each tab only when the tab is visible in the control.</span></span>  
  
 <span data-ttu-id="ba122-147">Kod örnekleri dahil olmak üzere daha fazla bilgi için aşağıdaki başvuru konularına bakın:</span><span class="sxs-lookup"><span data-stu-id="ba122-147">For more information, including code examples, see the following reference topics:</span></span>  
  
-   <xref:System.Windows.Forms.TabControl.DrawMode%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.TabControl.DrawItem?displayProperty=nameWithType>  
  
### <a name="tooltip-component"></a><span data-ttu-id="ba122-148">ToolTip Bileşeni</span><span class="sxs-lookup"><span data-stu-id="ba122-148">ToolTip Component</span></span>  
 <span data-ttu-id="ba122-149"><xref:System.Windows.Forms.ToolTip> Bileşen görüntülendiğinde tüm araç ipucu Çiz olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="ba122-149">The <xref:System.Windows.Forms.ToolTip> component enables you to draw the entire ToolTip when it is displayed.</span></span>  
  
 <span data-ttu-id="ba122-150">Çizmek için bir <xref:System.Windows.Forms.ToolTip>ayarlayın, `OwnerDraw` özelliğine `true` ve işlemek kendi `Draw` olay.</span><span class="sxs-lookup"><span data-stu-id="ba122-150">To draw a <xref:System.Windows.Forms.ToolTip>, set its `OwnerDraw` property to `true` and handle its `Draw` event.</span></span> <span data-ttu-id="ba122-151">Boyutunu özelleştirmek için <xref:System.Windows.Forms.ToolTip> önce `Draw` olayı oluşur, işleme `Popup` olay ve kümesi <xref:System.Windows.Forms.PopupEventArgs.ToolTipSize%2A> olay işleyicisi özelliği.</span><span class="sxs-lookup"><span data-stu-id="ba122-151">To customize the size of the <xref:System.Windows.Forms.ToolTip> before the `Draw` event occurs, handle the `Popup` event and set the <xref:System.Windows.Forms.PopupEventArgs.ToolTipSize%2A> property in the event handler.</span></span>  
  
 <span data-ttu-id="ba122-152">Kod örnekleri dahil olmak üzere daha fazla bilgi için aşağıdaki başvuru konularına bakın:</span><span class="sxs-lookup"><span data-stu-id="ba122-152">For more information, including code examples, see the following reference topics:</span></span>  
  
-   <xref:System.Windows.Forms.ToolTip.OwnerDraw%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ToolTip.Draw?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ToolTip.Popup?displayProperty=nameWithType>  
  
### <a name="listview-control"></a><span data-ttu-id="ba122-153">ListView Denetimi</span><span class="sxs-lookup"><span data-stu-id="ba122-153">ListView Control</span></span>  
 <span data-ttu-id="ba122-154"><xref:System.Windows.Forms.ListView> Denetimi tek tek öğe, alt öğeler ve sütun üst bilgileri denetiminde çizmek sağlar.</span><span class="sxs-lookup"><span data-stu-id="ba122-154">The <xref:System.Windows.Forms.ListView> control enables you to draw individual items, subitems, and column headers in the control.</span></span>  
  
 <span data-ttu-id="ba122-155">Sahip çizimi, denetimi etkinleştirmek için ayarlanmış `OwnerDraw` özelliğine `true`.</span><span class="sxs-lookup"><span data-stu-id="ba122-155">To enable owner drawing in the control, set the `OwnerDraw` property to `true`.</span></span>  
  
 <span data-ttu-id="ba122-156">Her öğe, denetimi çizmek için tanıtıcı `DrawItem` olay.</span><span class="sxs-lookup"><span data-stu-id="ba122-156">To draw each item in the control, handle the `DrawItem` event.</span></span>  
  
 <span data-ttu-id="ba122-157">Her alt veya sütun üstbilgisini denetiminde çizmek için zaman <xref:System.Windows.Forms.ListView.View%2A> özelliği ayarlanmış <xref:System.Windows.Forms.View.Details>, tanıtıcı `DrawSubItem` ve `DrawColumnHeader` olaylar.</span><span class="sxs-lookup"><span data-stu-id="ba122-157">To draw each subitem or column header in the control when the <xref:System.Windows.Forms.ListView.View%2A> property is set to <xref:System.Windows.Forms.View.Details>, handle the `DrawSubItem` and `DrawColumnHeader` events.</span></span>  
  
 <span data-ttu-id="ba122-158">Kod örnekleri dahil olmak üzere daha fazla bilgi için aşağıdaki başvuru konularına bakın:</span><span class="sxs-lookup"><span data-stu-id="ba122-158">For more information, including code examples, see the following reference topics:</span></span>  
  
-   <xref:System.Windows.Forms.ListView.OwnerDraw%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ListView.DrawItem?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ListView.DrawSubItem?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ListView.DrawColumnHeader?displayProperty=nameWithType>  
  
### <a name="treeview-control"></a><span data-ttu-id="ba122-159">TreeView Denetimi</span><span class="sxs-lookup"><span data-stu-id="ba122-159">TreeView Control</span></span>  
 <span data-ttu-id="ba122-160"><xref:System.Windows.Forms.TreeView> Denetim tek düğümler denetiminde Çiz olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="ba122-160">The <xref:System.Windows.Forms.TreeView> control enables you to draw individual nodes in the control.</span></span>  
  
 <span data-ttu-id="ba122-161">Yalnızca her düğümünde görüntülenen metin çizmek için ayarlanmış `DrawMode` özelliğine <xref:System.Windows.Forms.TreeViewDrawMode.OwnerDrawText> ve işlemek `DrawNode` metnini çizmek için olay.</span><span class="sxs-lookup"><span data-stu-id="ba122-161">To draw only the text displayed in each node, set the `DrawMode` property to <xref:System.Windows.Forms.TreeViewDrawMode.OwnerDrawText> and handle the `DrawNode` event to draw the text.</span></span>  
  
 <span data-ttu-id="ba122-162">Her düğümün tüm öğeleri çizmek için ayarlanmış `DrawMode` özelliğine <xref:System.Windows.Forms.TreeViewDrawMode.OwnerDrawAll> ve işlemek `DrawNode` ihtiyacınız metni, simgeleri denetlemek kutuları, artı ve eksi işaretlerine, gibi ve düğümlerini bağlayan çizgilerin hangi öğeleri çizmek için olay.</span><span class="sxs-lookup"><span data-stu-id="ba122-162">To draw all elements of each node, set the `DrawMode` property to <xref:System.Windows.Forms.TreeViewDrawMode.OwnerDrawAll> and handle the `DrawNode` event to draw whichever elements you need, such as text, icons, check boxes, plus and minus signs, and lines connecting the nodes.</span></span>  
  
 <span data-ttu-id="ba122-163">Kod örnekleri dahil olmak üzere daha fazla bilgi için aşağıdaki başvuru konularına bakın:</span><span class="sxs-lookup"><span data-stu-id="ba122-163">For more information, including code examples, see the following reference topics:</span></span>  
  
-   <xref:System.Windows.Forms.TreeView.DrawMode%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.TreeView.DrawNode?displayProperty=nameWithType>  
  
### <a name="datagridview-control"></a><span data-ttu-id="ba122-164">DataGridView Denetimi</span><span class="sxs-lookup"><span data-stu-id="ba122-164">DataGridView Control</span></span>  
 <span data-ttu-id="ba122-165"><xref:System.Windows.Forms.DataGridView> Denetim tek tek hücre ve satırları denetiminde Çiz olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="ba122-165">The <xref:System.Windows.Forms.DataGridView> control enables you to draw individual cells and rows in the control.</span></span>  
  
 <span data-ttu-id="ba122-166">Tek tek hücreleri çizmek için tanıtıcı `CellPainting` olay.</span><span class="sxs-lookup"><span data-stu-id="ba122-166">To draw individual cells, handle the `CellPainting` event.</span></span>  
  
 <span data-ttu-id="ba122-167">Tek tek satır veya satır öğeleri çizmek için aşağıdakilerden birini veya her ikisini de işlemek `RowPrePaint` ve `RowPostPaint` olaylar.</span><span class="sxs-lookup"><span data-stu-id="ba122-167">To draw individual rows or elements of rows, handle one or both of the `RowPrePaint` and `RowPostPaint` events.</span></span> <span data-ttu-id="ba122-168">`RowPrePaint` Olay, bir satır hücrelerde boyanır önce gerçekleşir ve `RowPostPaint` olay hücreleri boyanır sonra oluşur.</span><span class="sxs-lookup"><span data-stu-id="ba122-168">The `RowPrePaint` event occurs before the cells in a row are painted, and the `RowPostPaint` event occurs after the cells are painted.</span></span> <span data-ttu-id="ba122-169">Her iki olayları işlemek ve `CellPainting` satır arka plan, tek tek hücreler ve satır ön plan ayrı olarak boyamak için olay veya burada gereksinim ve satır diğer öğeler için varsayılan görüntü kullanmak belirli özelleştirmelere sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="ba122-169">You can handle both events and the `CellPainting` event to paint row background, individual cells, and row foreground separately, or you can provide specific customizations where you need them and use the default display for other elements of the row.</span></span>  
  
 <span data-ttu-id="ba122-170">Kod örnekleri dahil olmak üzere daha fazla bilgi için aşağıdaki konulara bakın:</span><span class="sxs-lookup"><span data-stu-id="ba122-170">For more information, including code examples, see the following topics:</span></span>  
  
-   <xref:System.Windows.Forms.DataGridView.CellPainting>  
  
-   <xref:System.Windows.Forms.DataGridView.RowPrePaint>  
  
-   <xref:System.Windows.Forms.DataGridView.RowPostPaint>  
  
-   [<span data-ttu-id="ba122-171">Nasıl yapılır: Windows Forms DataGridView Denetiminde Hücrelerin Görünüşünü Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="ba122-171">How to: Customize the Appearance of Cells in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/customize-the-appearance-of-cells-in-the-datagrid.md)  
  
-   [<span data-ttu-id="ba122-172">Nasıl yapılır: Windows Forms DataGridView Denetiminde Satırların Görünüşünü Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="ba122-172">How to: Customize the Appearance of Rows in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/customize-the-appearance-of-rows-in-the-datagrid.md)  
  
### <a name="toolstrip-control"></a><span data-ttu-id="ba122-173">ToolStrip Denetimi</span><span class="sxs-lookup"><span data-stu-id="ba122-173">ToolStrip Control</span></span>  
 <span data-ttu-id="ba122-174"><xref:System.Windows.Forms.ToolStrip>ve türetilen denetimler herhangi bir değişiklik görünümlerini, özelleştirmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="ba122-174"><xref:System.Windows.Forms.ToolStrip> and derived controls enable you to customize any aspect of their appearance.</span></span>  
  
 <span data-ttu-id="ba122-175">Özel işleme için sağlamak için <xref:System.Windows.Forms.ToolStrip> denetimler, ayarlayın `Renderer` özelliği bir <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.ToolStripManager>, <xref:System.Windows.Forms.ToolStripPanel>, veya <xref:System.Windows.Forms.ToolStripContentPanel> için bir `ToolStripRenderer` nesne ve bir veya daha fazla tarafından sağlanan birçok çizim olay işleme `ToolStripRenderer` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="ba122-175">To provide custom rendering for <xref:System.Windows.Forms.ToolStrip> controls, set the `Renderer` property of a <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.ToolStripManager>, <xref:System.Windows.Forms.ToolStripPanel>, or <xref:System.Windows.Forms.ToolStripContentPanel> to a `ToolStripRenderer` object and handle one or more of the many drawing events provided by the `ToolStripRenderer` class.</span></span> <span data-ttu-id="ba122-176">Alternatif olarak, kümesinin bir `Renderer` kendi sınıfının bir örneği özelliğine türetilen `ToolStripRenderer`, <xref:System.Windows.Forms.ToolStripProfessionalRenderer>, veya <xref:System.Windows.Forms.ToolStripSystemRenderer> uygulayan veya belirli geçersiz kılmaları `On` *EventName* yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="ba122-176">Alternatively, set a `Renderer` property to an instance of your own class derived from `ToolStripRenderer`, <xref:System.Windows.Forms.ToolStripProfessionalRenderer>, or <xref:System.Windows.Forms.ToolStripSystemRenderer> that implements or overrides specific `On`*EventName* methods.</span></span>  
  
 <span data-ttu-id="ba122-177">Kod örnekleri dahil olmak üzere daha fazla bilgi için aşağıdaki konulara bakın:</span><span class="sxs-lookup"><span data-stu-id="ba122-177">For more information, including code examples, see the following topics:</span></span>  
  
-   <xref:System.Windows.Forms.ToolStripRenderer>  
  
-   [<span data-ttu-id="ba122-178">Nasıl yapılır: Windows Forms'da ToolStrip Denetimi için Özel Oluşturucu Oluşturma ve Ayarlama</span><span class="sxs-lookup"><span data-stu-id="ba122-178">How to: Create and Set a Custom Renderer for the ToolStrip Control in Windows Forms</span></span>](../../../../docs/framework/winforms/controls/create-and-set-a-custom-renderer-for-the-toolstrip-control-in-wf.md)  
  
-   [<span data-ttu-id="ba122-179">Nasıl yapılır: Bir ToolStrip Denetimini Özel Olarak Çizme</span><span class="sxs-lookup"><span data-stu-id="ba122-179">How to: Custom Draw a ToolStrip Control</span></span>](../../../../docs/framework/winforms/controls/how-to-custom-draw-a-toolstrip-control.md)  
  
## <a name="see-also"></a><span data-ttu-id="ba122-180">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ba122-180">See Also</span></span>  
 [<span data-ttu-id="ba122-181">Windows Forms'da Kullanılacak Denetimler</span><span class="sxs-lookup"><span data-stu-id="ba122-181">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
