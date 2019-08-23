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
ms.openlocfilehash: f0d4b99f9ee0134fc7334a941dd5ef4fd7ba3df3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69930187"
---
# <a name="controls-with-built-in-owner-drawing-support"></a><span data-ttu-id="64868-102">Yerleşik Sahip Çizimi Destekli Denetimler</span><span class="sxs-lookup"><span data-stu-id="64868-102">Controls with Built-In Owner-Drawing Support</span></span>
<span data-ttu-id="64868-103">Özel çizim olarak da bilinen Windows Forms sahip çizimi, belirli denetimlerin görsel görünümünü değiştirmek için bir tekniktir.</span><span class="sxs-lookup"><span data-stu-id="64868-103">Owner drawing in Windows Forms, which is also known as custom drawing, is a technique for changing the visual appearance of certain controls.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="64868-104">Bu konudaki "Control" sözcüğü ya <xref:System.Windows.Forms.Control> <xref:System.ComponentModel.Component>da ' den türetilen sınıfların anlamı için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="64868-104">The word "control" in this topic is used to mean classes that derive from either <xref:System.Windows.Forms.Control> or <xref:System.ComponentModel.Component>.</span></span>  
  
 <span data-ttu-id="64868-105">Genellikle, Windows, bir denetimin görünüşünü belirleme gibi özellik ayarlarını <xref:System.Windows.Forms.Control.BackColor%2A> kullanarak boyamayı otomatik olarak gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="64868-105">Typically, Windows handles painting automatically by using property settings such as <xref:System.Windows.Forms.Control.BackColor%2A> to determine the appearance of a control.</span></span> <span data-ttu-id="64868-106">Sahip çizimi ile boyama işlemini gerçekleştirerek, özellikler kullanılarak kullanılamayan görünüm öğelerini değiştirmiş olursunuz.</span><span class="sxs-lookup"><span data-stu-id="64868-106">With owner drawing, you take over the painting process, changing elements of appearance that are not available by using properties.</span></span> <span data-ttu-id="64868-107">Örneğin, birçok denetim görüntülenen metnin rengini ayarlamanıza izin verir, ancak tek bir renkle sınırlı olursunuz.</span><span class="sxs-lookup"><span data-stu-id="64868-107">For example, many controls let you set the color of the text that is displayed, but you are limited to a single color.</span></span> <span data-ttu-id="64868-108">Sahip çizimi, metnin bir kısmını siyah ve kırmızı renkte görüntüleme gibi işlemleri yapmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="64868-108">Owner drawing enables you to do things like display part of the text in black and part in red.</span></span>  
  
 <span data-ttu-id="64868-109">Uygulamada, sahip çizimi, grafikleri bir biçimde çizmekle benzerdir.</span><span class="sxs-lookup"><span data-stu-id="64868-109">In practice, owner drawing is similar to drawing graphics on a form.</span></span> <span data-ttu-id="64868-110">Örneğin, bir <xref:System.Windows.Forms.Control.Paint> `ListBox` denetime öykünmek için formun olayına yönelik bir işleyicide grafik yöntemlerini kullanabilirsiniz, ancak tüm kullanıcı etkileşimini işlemek için kendi kodunuzu yazmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="64868-110">For example, you could use graphics methods in a handler for the form's <xref:System.Windows.Forms.Control.Paint> event to emulate a `ListBox` control, but you would have to write your own code to handle all user interaction.</span></span> <span data-ttu-id="64868-111">Sahip çizimi ile denetim, kendi içeriğini çizmek için kodunuzu kullanır, aksi halde tüm iç özelliklerini korur.</span><span class="sxs-lookup"><span data-stu-id="64868-111">With owner drawing, the control uses your code to draw its contents but otherwise retains all its intrinsic capabilities.</span></span> <span data-ttu-id="64868-112">Her bir öğenin diğer yönleri için varsayılan görünümü kullanırken, denetimdeki her öğeyi çizmek veya her öğenin bazı yönlerini özelleştirmek için grafik yöntemlerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="64868-112">You can use graphics methods to draw each item in the control or to customize some aspects of each item while you use the default appearance for other aspects of each item.</span></span>  
  
## <a name="owner-drawing-in-windows-forms-controls"></a><span data-ttu-id="64868-113">Windows Forms Denetimlerinde sahip çizimi</span><span class="sxs-lookup"><span data-stu-id="64868-113">Owner Drawing in Windows Forms Controls</span></span>  
 <span data-ttu-id="64868-114">Kendisini destekleyen denetimlerde sahip çizimi gerçekleştirmek için, genellikle bir özellik ayarlarsınız ve bir veya daha fazla olayı idare edersiniz.</span><span class="sxs-lookup"><span data-stu-id="64868-114">To perform owner drawing in controls that support it, you will typically set one property and handle one or more events.</span></span>  
  
 <span data-ttu-id="64868-115">Sahip çizimi destekleyen çoğu denetim, denetimin, `OwnerDraw` kendisini `DrawMode` boyayan çizimle ilgili olay veya olaylarını yapıp oluşturmayacağını belirten bir veya özelliğine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="64868-115">Most controls that support owner drawing have an `OwnerDraw` or `DrawMode` property that indicates whether the control will raise its drawing-related event or events when it paints itself.</span></span>  
  
 <span data-ttu-id="64868-116">Veya `OwnerDraw` `DataGridView` `ToolStrip` özelliğine sahip olmayan denetimler, otomatik olarak oluşan çizim olayları ve kendi kendine sahip bir dış işleme sınıfı kullanılarak çizilen denetim gibi bir denetimi içermez. `DrawMode` çizimlerle ilgili olaylar.</span><span class="sxs-lookup"><span data-stu-id="64868-116">Controls that do not have an `OwnerDraw` or `DrawMode` property include the `DataGridView` control, which provides drawing events that occur automatically, and the `ToolStrip` control, which is drawn using an external rendering class that has its own drawing-related events.</span></span>  
  
 <span data-ttu-id="64868-117">Birçok farklı çizim olayı türü vardır, ancak denetim içinde tek bir öğe çizmek için tipik bir çizim olayı oluşur.</span><span class="sxs-lookup"><span data-stu-id="64868-117">There are many different kinds of drawing events, but a typical drawing event occurs in order to draw a single item within a control.</span></span> <span data-ttu-id="64868-118">Olay işleyicisi, çizmekte `EventArgs` olan öğe ve araç çizmek için kullanabileceğiniz araçlar hakkında bilgi içeren bir nesnesi alır.</span><span class="sxs-lookup"><span data-stu-id="64868-118">The event handler receives an `EventArgs` object that contains information about the item being drawn and tools you can use to draw it.</span></span> <span data-ttu-id="64868-119">Örneğin, bu nesne genellikle öğenin kendi üst koleksiyonundaki dizin numarasını, <xref:System.Drawing.Rectangle> öğenin görüntü sınırlarını <xref:System.Drawing.Graphics> ve Paint yöntemlerini çağırmak için bir nesneyi içerir.</span><span class="sxs-lookup"><span data-stu-id="64868-119">For example, this object typically contains the item's index number within its parent collection, a <xref:System.Drawing.Rectangle> that indicates the item's display boundaries, and a <xref:System.Drawing.Graphics> object for calling paint methods.</span></span> <span data-ttu-id="64868-120">Bu `EventArgs` nesne, bazı olaylar için, arka plan veya odak dikdörtgeni gibi, varsayılan olarak öğenin bazı yönlerini boyamak için çağırabilmeniz gereken öğe ve yöntemler hakkında ek bilgiler sağlar.</span><span class="sxs-lookup"><span data-stu-id="64868-120">For some events, the `EventArgs` object provides additional information about the item and methods that you can call to paint some aspects of the item by default, such as the background or a focus rectangle.</span></span>  
  
 <span data-ttu-id="64868-121">Sahip tarafından çizilmiş özelleştirmeleri içeren yeniden kullanılabilir bir denetim oluşturmak için, sahip çizimi destekleyen bir denetim sınıfından türetilen yeni bir sınıf oluşturun.</span><span class="sxs-lookup"><span data-stu-id="64868-121">To create a reusable control that contains your owner-drawn customizations, create a new class that derives from a control class that supports owner drawing.</span></span> <span data-ttu-id="64868-122">Çizim olaylarını işlemek yerine, yeni sınıftaki uygun `On` *EventName* yöntemi veya yöntemleri için sahip çizim kodunuzu geçersiz kılmalara ekleyin.</span><span class="sxs-lookup"><span data-stu-id="64868-122">Rather than handling drawing events, include your owner-drawing code in overrides for the appropriate `On`*EventName* method or methods in the new class.</span></span> <span data-ttu-id="64868-123">Denetiminizin kullanıcılarının sahip çizim olaylarını işleyebilmesi ve `On`ek özelleştirme sağlaması için bu durumda temel sınıf *EventName* metodunu veya yöntemlerini çağırdığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="64868-123">Make sure that you call the base class `On`*EventName* method or methods in this case so that users of your control can handle owner-drawing events and provide additional customization.</span></span>  
  
 <span data-ttu-id="64868-124">Aşağıdaki Windows Forms denetimleri, tüm .NET Framework sürümlerindeki sahip çizimini destekler:</span><span class="sxs-lookup"><span data-stu-id="64868-124">The following Windows Forms controls support owner drawing in all versions of the .NET Framework:</span></span>  
  
- <xref:System.Windows.Forms.ListBox>  
  
- <xref:System.Windows.Forms.ComboBox>  
  
- <span data-ttu-id="64868-125"><xref:System.Windows.Forms.MenuItem>(ve <xref:System.Windows.Forms.MainMenu> <xref:System.Windows.Forms.ContextMenu>tarafından kullanılır)</span><span class="sxs-lookup"><span data-stu-id="64868-125"><xref:System.Windows.Forms.MenuItem> (used by <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu>)</span></span>  
  
- <xref:System.Windows.Forms.TabControl>  
  
 <span data-ttu-id="64868-126">Aşağıdaki denetimler yalnızca .NET Framework 2,0 ' de sahip çizimi destekler:</span><span class="sxs-lookup"><span data-stu-id="64868-126">The following controls support owner drawing only in .NET Framework 2.0:</span></span>  
  
- <xref:System.Windows.Forms.ToolTip>  
  
- <xref:System.Windows.Forms.ListView>  
  
- <xref:System.Windows.Forms.TreeView>  
  
 <span data-ttu-id="64868-127">Aşağıdaki denetimler sahip çizimi destekler ve .NET Framework 2,0 ' de yenidir:</span><span class="sxs-lookup"><span data-stu-id="64868-127">The following controls support owner drawing and are new in .NET Framework 2.0:</span></span>  
  
- <xref:System.Windows.Forms.DataGridView>  
  
- <xref:System.Windows.Forms.ToolStrip>  
  
 <span data-ttu-id="64868-128">Aşağıdaki bölümlerde bu denetimlerin her biri için ek ayrıntılar sağlanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="64868-128">The following sections provide additional details for each of these controls.</span></span>  
  
### <a name="listbox-and-combobox-controls"></a><span data-ttu-id="64868-129">ListBox ve ComboBox denetimleri</span><span class="sxs-lookup"><span data-stu-id="64868-129">ListBox and ComboBox Controls</span></span>  
 <span data-ttu-id="64868-130"><xref:System.Windows.Forms.ListBox> Ve<xref:System.Windows.Forms.ComboBox> denetimleri, tek bir boyutta ya da değişen boyutlarda denetimdeki tek tek öğeleri çizmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="64868-130">The <xref:System.Windows.Forms.ListBox> and <xref:System.Windows.Forms.ComboBox> controls enable you to draw individual items in the control either all in one size, or in varying sizes.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="64868-131"><xref:System.Windows.Forms.CheckedListBox> Denetim <xref:System.Windows.Forms.ListBox> denetimden türetilse de, sahip çizimi desteklemez.</span><span class="sxs-lookup"><span data-stu-id="64868-131">Although the <xref:System.Windows.Forms.CheckedListBox> control is derived from the <xref:System.Windows.Forms.ListBox> control, it does not support owner drawing.</span></span>  
  
 <span data-ttu-id="64868-132">Her öğeyi aynı boyutta çizmek için `DrawMode` özelliği olarak <xref:System.Windows.Forms.DrawMode.OwnerDrawFixed> ayarlayın ve `DrawItem` olayı işleyin.</span><span class="sxs-lookup"><span data-stu-id="64868-132">To draw each item the same size, set the `DrawMode` property to <xref:System.Windows.Forms.DrawMode.OwnerDrawFixed> and handle the `DrawItem` event.</span></span>  
  
 <span data-ttu-id="64868-133">Her bir öğeyi farklı bir boyut kullanarak çizmek `DrawMode` için, özelliğini `MeasureItem` ve olaylarını <xref:System.Windows.Forms.DrawMode.OwnerDrawVariable> ve `DrawItem` işlemek için öğesini olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="64868-133">To draw each item using a different size, set the `DrawMode` property to <xref:System.Windows.Forms.DrawMode.OwnerDrawVariable> and handle both the `MeasureItem` and `DrawItem` events.</span></span> <span data-ttu-id="64868-134">Olay, bu öğe için `DrawItem` olay gerçekleşmeden önce bir öğenin boyutunu belirtmenize olanak sağlar. `MeasureItem`</span><span class="sxs-lookup"><span data-stu-id="64868-134">The `MeasureItem` event lets you indicate the size of an item before the `DrawItem` event occurs for that item.</span></span>  
  
 <span data-ttu-id="64868-135">Kod örnekleri de dahil olmak üzere daha fazla bilgi için aşağıdaki konulara bakın:</span><span class="sxs-lookup"><span data-stu-id="64868-135">For more information, including code examples, see the following topics:</span></span>  
  
- <xref:System.Windows.Forms.ListBox.DrawMode%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ListBox.MeasureItem?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ListBox.DrawItem?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ComboBox.DrawMode%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ComboBox.MeasureItem?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ComboBox.DrawItem?displayProperty=nameWithType>  
  
- [<span data-ttu-id="64868-136">Nasıl yapılır: ComboBox denetiminde değişken boyutlu metin oluşturma</span><span class="sxs-lookup"><span data-stu-id="64868-136">How to: Create Variable Sized Text in a ComboBox Control</span></span>](how-to-create-variable-sized-text-in-a-combobox-control.md)  
  
### <a name="menuitem-component"></a><span data-ttu-id="64868-137">MenuItem bileşeni</span><span class="sxs-lookup"><span data-stu-id="64868-137">MenuItem Component</span></span>  
 <span data-ttu-id="64868-138">Bileşen bir <xref:System.Windows.Forms.MainMenu> veya<xref:System.Windows.Forms.ContextMenu> bileşenindeki tek bir menü öğesini temsil eder. <xref:System.Windows.Forms.MenuItem></span><span class="sxs-lookup"><span data-stu-id="64868-138">The <xref:System.Windows.Forms.MenuItem> component represents a single menu item in a <xref:System.Windows.Forms.MainMenu> or <xref:System.Windows.Forms.ContextMenu> component.</span></span>  
  
 <span data-ttu-id="64868-139">Bir <xref:System.Windows.Forms.MenuItem>çizmek için, `OwnerDraw` `true`özelliğiniolarak ayarlayın ve olayınıişleyin.`DrawItem`</span><span class="sxs-lookup"><span data-stu-id="64868-139">To draw a <xref:System.Windows.Forms.MenuItem>, set its `OwnerDraw` property to `true` and handle its `DrawItem` event.</span></span> <span data-ttu-id="64868-140">`DrawItem` Olay gerçekleşmeden önce menü öğesinin boyutunu özelleştirmek için, `MeasureItem` öğenin olayını işleyin.</span><span class="sxs-lookup"><span data-stu-id="64868-140">To customize the size of the menu item before the `DrawItem` event occurs, handle the item's `MeasureItem` event.</span></span>  
  
 <span data-ttu-id="64868-141">Kod örnekleri de dahil olmak üzere daha fazla bilgi için aşağıdaki başvuru konularına bakın:</span><span class="sxs-lookup"><span data-stu-id="64868-141">For more information, including code examples, see the following reference topics:</span></span>  
  
- <xref:System.Windows.Forms.MenuItem.OwnerDraw%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.MenuItem.DrawItem?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.MenuItem.MeasureItem?displayProperty=nameWithType>  
  
### <a name="tabcontrol-control"></a><span data-ttu-id="64868-142">TabControl Denetimi</span><span class="sxs-lookup"><span data-stu-id="64868-142">TabControl Control</span></span>  
 <span data-ttu-id="64868-143"><xref:System.Windows.Forms.TabControl> Denetim, denetimde ayrı sekmeler çizmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="64868-143">The <xref:System.Windows.Forms.TabControl> control enables you to draw individual tabs in the control.</span></span> <span data-ttu-id="64868-144">Sahip çizimi yalnızca sekmeleri etkiler; <xref:System.Windows.Forms.TabPage> içerik etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="64868-144">Owner drawing affects only the tabs; the <xref:System.Windows.Forms.TabPage> contents are not affected.</span></span>  
  
 <span data-ttu-id="64868-145">İçindeki her bir <xref:System.Windows.Forms.TabControl>sekmeyi çizmek için, `DrawMode` `DrawItem` özelliğini olarak <xref:System.Windows.Forms.TabDrawMode.OwnerDrawFixed> ayarlayın ve olayı işleyin.</span><span class="sxs-lookup"><span data-stu-id="64868-145">To draw each tab in a <xref:System.Windows.Forms.TabControl>, set the `DrawMode` property to <xref:System.Windows.Forms.TabDrawMode.OwnerDrawFixed> and handle the `DrawItem` event.</span></span> <span data-ttu-id="64868-146">Bu olay, her sekme için yalnızca sekme denetimde görünür olduğunda gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="64868-146">This event occurs once for each tab only when the tab is visible in the control.</span></span>  
  
 <span data-ttu-id="64868-147">Kod örnekleri de dahil olmak üzere daha fazla bilgi için aşağıdaki başvuru konularına bakın:</span><span class="sxs-lookup"><span data-stu-id="64868-147">For more information, including code examples, see the following reference topics:</span></span>  
  
- <xref:System.Windows.Forms.TabControl.DrawMode%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.TabControl.DrawItem?displayProperty=nameWithType>  
  
### <a name="tooltip-component"></a><span data-ttu-id="64868-148">ToolTip Bileşeni</span><span class="sxs-lookup"><span data-stu-id="64868-148">ToolTip Component</span></span>  
 <span data-ttu-id="64868-149"><xref:System.Windows.Forms.ToolTip> Bileşeni, görüntülendiğinde araç ipucunun tamamını çizmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="64868-149">The <xref:System.Windows.Forms.ToolTip> component enables you to draw the entire ToolTip when it is displayed.</span></span>  
  
 <span data-ttu-id="64868-150">Bir <xref:System.Windows.Forms.ToolTip>çizmek için, `OwnerDraw` `true`özelliğiniolarak ayarlayın ve olayınıişleyin.`Draw`</span><span class="sxs-lookup"><span data-stu-id="64868-150">To draw a <xref:System.Windows.Forms.ToolTip>, set its `OwnerDraw` property to `true` and handle its `Draw` event.</span></span> <span data-ttu-id="64868-151">Olay gerçekleşmeden <xref:System.Windows.Forms.ToolTip>önceöğesinin boyutunu özelleştirmek için <xref:System.Windows.Forms.PopupEventArgs.ToolTipSize%2A> olayıişleyinveolayişleyicisindekiözelliğiayarlayın.`Popup` `Draw`</span><span class="sxs-lookup"><span data-stu-id="64868-151">To customize the size of the <xref:System.Windows.Forms.ToolTip> before the `Draw` event occurs, handle the `Popup` event and set the <xref:System.Windows.Forms.PopupEventArgs.ToolTipSize%2A> property in the event handler.</span></span>  
  
 <span data-ttu-id="64868-152">Kod örnekleri de dahil olmak üzere daha fazla bilgi için aşağıdaki başvuru konularına bakın:</span><span class="sxs-lookup"><span data-stu-id="64868-152">For more information, including code examples, see the following reference topics:</span></span>  
  
- <xref:System.Windows.Forms.ToolTip.OwnerDraw%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ToolTip.Draw?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ToolTip.Popup?displayProperty=nameWithType>  
  
### <a name="listview-control"></a><span data-ttu-id="64868-153">ListView Denetimi</span><span class="sxs-lookup"><span data-stu-id="64868-153">ListView Control</span></span>  
 <span data-ttu-id="64868-154"><xref:System.Windows.Forms.ListView> Denetim, denetimdeki öğeleri, alt öğeleri ve sütun üstbilgilerini tek tek çizmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="64868-154">The <xref:System.Windows.Forms.ListView> control enables you to draw individual items, subitems, and column headers in the control.</span></span>  
  
 <span data-ttu-id="64868-155">Denetimde sahip çizimi etkinleştirmek için `OwnerDraw` özelliğini olarak `true`ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="64868-155">To enable owner drawing in the control, set the `OwnerDraw` property to `true`.</span></span>  
  
 <span data-ttu-id="64868-156">Denetimdeki her öğeyi çizmek için `DrawItem` olayı işleyin.</span><span class="sxs-lookup"><span data-stu-id="64868-156">To draw each item in the control, handle the `DrawItem` event.</span></span>  
  
 <span data-ttu-id="64868-157"><xref:System.Windows.Forms.ListView.View%2A> Özelliği olarak <xref:System.Windows.Forms.View.Details>ayarlandığında, denetimde her alt öğe veya sütun üstbilgisini çizmek için `DrawSubItem` ve `DrawColumnHeader` olaylarını işleyin.</span><span class="sxs-lookup"><span data-stu-id="64868-157">To draw each subitem or column header in the control when the <xref:System.Windows.Forms.ListView.View%2A> property is set to <xref:System.Windows.Forms.View.Details>, handle the `DrawSubItem` and `DrawColumnHeader` events.</span></span>  
  
 <span data-ttu-id="64868-158">Kod örnekleri de dahil olmak üzere daha fazla bilgi için aşağıdaki başvuru konularına bakın:</span><span class="sxs-lookup"><span data-stu-id="64868-158">For more information, including code examples, see the following reference topics:</span></span>  
  
- <xref:System.Windows.Forms.ListView.OwnerDraw%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ListView.DrawItem?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ListView.DrawSubItem?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ListView.DrawColumnHeader?displayProperty=nameWithType>  
  
### <a name="treeview-control"></a><span data-ttu-id="64868-159">TreeView Denetimi</span><span class="sxs-lookup"><span data-stu-id="64868-159">TreeView Control</span></span>  
 <span data-ttu-id="64868-160"><xref:System.Windows.Forms.TreeView> Denetim, denetimde tek tek düğümler çizmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="64868-160">The <xref:System.Windows.Forms.TreeView> control enables you to draw individual nodes in the control.</span></span>  
  
 <span data-ttu-id="64868-161">Yalnızca her düğümde görüntülenecek metni çizmek için, `DrawMode` özelliğini olarak <xref:System.Windows.Forms.TreeViewDrawMode.OwnerDrawText> ayarlayın ve metni çizmek için `DrawNode` olayı işleyin.</span><span class="sxs-lookup"><span data-stu-id="64868-161">To draw only the text displayed in each node, set the `DrawMode` property to <xref:System.Windows.Forms.TreeViewDrawMode.OwnerDrawText> and handle the `DrawNode` event to draw the text.</span></span>  
  
 <span data-ttu-id="64868-162">Her bir düğümün tüm öğelerini çizmek için, `DrawMode` <xref:System.Windows.Forms.TreeViewDrawMode.OwnerDrawAll> özelliği olarak ayarlayın ve istediğiniz öğeleri ( `DrawNode` metin, simgeler, onay kutuları, artı eksi işaretleri ve düğümleri bağlayan çizgiler) çizmek için olayı işleyin.</span><span class="sxs-lookup"><span data-stu-id="64868-162">To draw all elements of each node, set the `DrawMode` property to <xref:System.Windows.Forms.TreeViewDrawMode.OwnerDrawAll> and handle the `DrawNode` event to draw whichever elements you need, such as text, icons, check boxes, plus and minus signs, and lines connecting the nodes.</span></span>  
  
 <span data-ttu-id="64868-163">Kod örnekleri de dahil olmak üzere daha fazla bilgi için aşağıdaki başvuru konularına bakın:</span><span class="sxs-lookup"><span data-stu-id="64868-163">For more information, including code examples, see the following reference topics:</span></span>  
  
- <xref:System.Windows.Forms.TreeView.DrawMode%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.TreeView.DrawNode?displayProperty=nameWithType>  
  
### <a name="datagridview-control"></a><span data-ttu-id="64868-164">DataGridView Denetimi</span><span class="sxs-lookup"><span data-stu-id="64868-164">DataGridView Control</span></span>  
 <span data-ttu-id="64868-165"><xref:System.Windows.Forms.DataGridView> Denetim, denetimde tek tek hücreler ve satırlar çizmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="64868-165">The <xref:System.Windows.Forms.DataGridView> control enables you to draw individual cells and rows in the control.</span></span>  
  
 <span data-ttu-id="64868-166">Ayrı hücreler çizmek için `CellPainting` olayı işleyin.</span><span class="sxs-lookup"><span data-stu-id="64868-166">To draw individual cells, handle the `CellPainting` event.</span></span>  
  
 <span data-ttu-id="64868-167">Tek tek satırları veya satır öğelerini çizmek için `RowPrePaint` ve `RowPostPaint` olaylarını bir veya her ikisini de işleyin.</span><span class="sxs-lookup"><span data-stu-id="64868-167">To draw individual rows or elements of rows, handle one or both of the `RowPrePaint` and `RowPostPaint` events.</span></span> <span data-ttu-id="64868-168">Olay, bir satırdaki hücreler boyanmadan önce oluşur `RowPostPaint` ve bu olay, hücreler boyandıktan sonra gerçekleşir. `RowPrePaint`</span><span class="sxs-lookup"><span data-stu-id="64868-168">The `RowPrePaint` event occurs before the cells in a row are painted, and the `RowPostPaint` event occurs after the cells are painted.</span></span> <span data-ttu-id="64868-169">Satır arka planı, tek tek hücreler `CellPainting` ve satır ön planını ayrı olarak boyamak için hem olayları hem de olayı işleyebilirsiniz veya ihtiyacınız olan özel özelleştirmeler sağlayabilir ve bu, satırın diğer öğeleri için varsayılan ekranı kullanır.</span><span class="sxs-lookup"><span data-stu-id="64868-169">You can handle both events and the `CellPainting` event to paint row background, individual cells, and row foreground separately, or you can provide specific customizations where you need them and use the default display for other elements of the row.</span></span>  
  
 <span data-ttu-id="64868-170">Kod örnekleri de dahil olmak üzere daha fazla bilgi için aşağıdaki konulara bakın:</span><span class="sxs-lookup"><span data-stu-id="64868-170">For more information, including code examples, see the following topics:</span></span>  
  
- <xref:System.Windows.Forms.DataGridView.CellPainting>  
  
- <xref:System.Windows.Forms.DataGridView.RowPrePaint>  
  
- <xref:System.Windows.Forms.DataGridView.RowPostPaint>  
  
- [<span data-ttu-id="64868-171">Nasıl yapılır: Windows Forms DataGridView Denetimindeki hücrelerin görünümünü özelleştirme</span><span class="sxs-lookup"><span data-stu-id="64868-171">How to: Customize the Appearance of Cells in the Windows Forms DataGridView Control</span></span>](customize-the-appearance-of-cells-in-the-datagrid.md)  
  
- [<span data-ttu-id="64868-172">Nasıl yapılır: Windows Forms DataGridView Denetimindeki satırların görünümünü özelleştirme</span><span class="sxs-lookup"><span data-stu-id="64868-172">How to: Customize the Appearance of Rows in the Windows Forms DataGridView Control</span></span>](customize-the-appearance-of-rows-in-the-datagrid.md)  
  
### <a name="toolstrip-control"></a><span data-ttu-id="64868-173">ToolStrip Denetimi</span><span class="sxs-lookup"><span data-stu-id="64868-173">ToolStrip Control</span></span>  
 <span data-ttu-id="64868-174"><xref:System.Windows.Forms.ToolStrip>ve türetilmiş denetimler, görünüşlerinin herhangi bir yönünü özelleştirmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="64868-174"><xref:System.Windows.Forms.ToolStrip> and derived controls enable you to customize any aspect of their appearance.</span></span>  
  
 <span data-ttu-id="64868-175">Denetimler için <xref:System.Windows.Forms.ToolStrip> özel işleme sağlamak üzere, bir <xref:System.Windows.Forms.ToolStripManager> <xref:System.Windows.Forms.ToolStrip> `Renderer` <xref:System.Windows.Forms.ToolStripPanel>,, veya <xref:System.Windows.Forms.ToolStripContentPanel> 'ibirnesnesineayarlayınvebirveyadahafazlaçizimolayınınsağladığı`ToolStripRenderer` `ToolStripRenderer` sınıf.</span><span class="sxs-lookup"><span data-stu-id="64868-175">To provide custom rendering for <xref:System.Windows.Forms.ToolStrip> controls, set the `Renderer` property of a <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.ToolStripManager>, <xref:System.Windows.Forms.ToolStripPanel>, or <xref:System.Windows.Forms.ToolStripContentPanel> to a `ToolStripRenderer` object and handle one or more of the many drawing events provided by the `ToolStripRenderer` class.</span></span> <span data-ttu-id="64868-176">Alternatif olarak, bir `Renderer` özelliği `ToolStripRenderer`, <xref:System.Windows.Forms.ToolStripProfessionalRenderer>ya <xref:System.Windows.Forms.ToolStripSystemRenderer> da belirli `On`bir *EventName* yöntemini uygulayan veya geçersiz kılan kendi sınıfınızın bir örneğine ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="64868-176">Alternatively, set a `Renderer` property to an instance of your own class derived from `ToolStripRenderer`, <xref:System.Windows.Forms.ToolStripProfessionalRenderer>, or <xref:System.Windows.Forms.ToolStripSystemRenderer> that implements or overrides specific `On`*EventName* methods.</span></span>  
  
 <span data-ttu-id="64868-177">Kod örnekleri de dahil olmak üzere daha fazla bilgi için aşağıdaki konulara bakın:</span><span class="sxs-lookup"><span data-stu-id="64868-177">For more information, including code examples, see the following topics:</span></span>  
  
- <xref:System.Windows.Forms.ToolStripRenderer>  
  
- [<span data-ttu-id="64868-178">Nasıl yapılır: Windows Forms ToolStrip denetimi için özel Oluşturucu oluşturma ve ayarlama</span><span class="sxs-lookup"><span data-stu-id="64868-178">How to: Create and Set a Custom Renderer for the ToolStrip Control in Windows Forms</span></span>](create-and-set-a-custom-renderer-for-the-toolstrip-control-in-wf.md)  
  
- [<span data-ttu-id="64868-179">Nasıl yapılır: ToolStrip denetimi özel çizimi</span><span class="sxs-lookup"><span data-stu-id="64868-179">How to: Custom Draw a ToolStrip Control</span></span>](how-to-custom-draw-a-toolstrip-control.md)  
  
## <a name="see-also"></a><span data-ttu-id="64868-180">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="64868-180">See also</span></span>

- [<span data-ttu-id="64868-181">Windows Forms'da Kullanılacak Denetimler</span><span class="sxs-lookup"><span data-stu-id="64868-181">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
