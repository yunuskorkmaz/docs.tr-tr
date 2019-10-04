---
title: Windows Forms'ta Fare Olayları
ms.date: 03/30/2017
helpviewer_keywords:
- MouseLeave event [Windows Forms]
- events [Windows Forms], mouse
- Click event [Windows Forms], raising order
- Windows Forms controls, click events
- MouseDoubleClick event [Windows Forms]
- MouseEnter event [Windows Forms]
- MouseHover event [Windows Forms]
- MouseDown event [Windows Forms]
- MouseClick event [Windows Forms]
- MouseMove event [Windows Forms]
- mouse [Windows Forms], events
- MouseUp event
ms.assetid: 8cf0070d-793b-4876-b09e-d20d28280fab
ms.openlocfilehash: a61f4eedde611cfb7598d55465103924516e06c6
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834603"
---
# <a name="mouse-events-in-windows-forms"></a><span data-ttu-id="ab685-102">Windows Forms'ta Fare Olayları</span><span class="sxs-lookup"><span data-stu-id="ab685-102">Mouse Events in Windows Forms</span></span>

<span data-ttu-id="ab685-103">Fare girişini işlerken, genellikle fare işaretçisinin konumunu ve fare düğmelerinin durumunu bilmek istersiniz.</span><span class="sxs-lookup"><span data-stu-id="ab685-103">When you handle mouse input, you usually want to know the location of the mouse pointer and the state of the mouse buttons.</span></span> <span data-ttu-id="ab685-104">Bu konu, fare olaylarından bu bilgilerin nasıl alınacağı hakkında ayrıntılar sağlar ve Windows Forms Denetimlerinde fare tıklaması olaylarının nasıl oluşturulduğu sırasını açıklar.</span><span class="sxs-lookup"><span data-stu-id="ab685-104">This topic provides details on how to get this information from mouse events, and explains the order in which mouse click events are raised in Windows Forms controls.</span></span> <span data-ttu-id="ab685-105">Tüm fare olaylarının listesi ve açıklaması için bkz. [fare girişinin Windows Forms nasıl çalıştığı](how-mouse-input-works-in-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="ab685-105">For a list and description of all of the mouse events, see [How Mouse Input Works in Windows Forms](how-mouse-input-works-in-windows-forms.md).</span></span>  <span data-ttu-id="ab685-106">Ayrıca bkz. [olay Işleyicilerine genel bakış (Windows Forms)](event-handlers-overview-windows-forms.md) ve [olaylara genel bakış (Windows Forms)](events-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="ab685-106">Also see [Event Handlers Overview (Windows Forms)](event-handlers-overview-windows-forms.md) and [Events Overview (Windows Forms)](events-overview-windows-forms.md).</span></span>

## <a name="mouse-information"></a><span data-ttu-id="ab685-107">Fare bilgileri</span><span class="sxs-lookup"><span data-stu-id="ab685-107">Mouse Information</span></span>

<span data-ttu-id="ab685-108">Bir <xref:System.Windows.Forms.MouseEventArgs>, fare düğmesine tıklanması ve fare hareketlerini izlemek için ilgili fare olaylarının işleyicilerine gönderilir.</span><span class="sxs-lookup"><span data-stu-id="ab685-108">A <xref:System.Windows.Forms.MouseEventArgs> is sent to the handlers of mouse events related to clicking a mouse button and tracking mouse movements.</span></span> <span data-ttu-id="ab685-109"><xref:System.Windows.Forms.MouseEventArgs>, fare işaretçisinin istemci koordinatlarındaki konumunu, hangi fare düğmelerine basıldığını ve fare tekerinin kaydırılmadığını de içeren, işaretçinin geçerli durumu hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="ab685-109"><xref:System.Windows.Forms.MouseEventArgs> provides information about the current state of the mouse, including the location of the mouse pointer in client coordinates, which mouse buttons are pressed, and whether the mouse wheel has scrolled.</span></span> <span data-ttu-id="ab685-110">Fare işaretçisi bir denetimin sınırları girildiğinde veya sol tarafında bilgilendirenler gibi birçok fare olayı, daha fazla bilgi olmadan olay işleyicisine bir <xref:System.EventArgs> gönderin.</span><span class="sxs-lookup"><span data-stu-id="ab685-110">Several mouse events, such as those that simply notify when the mouse pointer has entered or left the bounds of a control, send an <xref:System.EventArgs> to the event handler with no further information.</span></span>

<span data-ttu-id="ab685-111">Fare düğmelerinin geçerli durumunu veya fare işaretçisinin konumunu biliyorsanız ve bir fare olayını işlemeyi önlemek istiyorsanız, <xref:System.Windows.Forms.Control> sınıfının <xref:System.Windows.Forms.Control.MouseButtons%2A> ve <xref:System.Windows.Forms.Control.MousePosition%2A> özelliklerini de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ab685-111">If you want to know the current state of the mouse buttons or the location of the mouse pointer, and you want to avoid handling a mouse event, you can also use the <xref:System.Windows.Forms.Control.MouseButtons%2A> and <xref:System.Windows.Forms.Control.MousePosition%2A> properties of the <xref:System.Windows.Forms.Control> class.</span></span> <span data-ttu-id="ab685-112"><xref:System.Windows.Forms.Control.MouseButtons%2A>, şu anda basılan fare düğmelerine ilişkin bilgileri döndürür.</span><span class="sxs-lookup"><span data-stu-id="ab685-112"><xref:System.Windows.Forms.Control.MouseButtons%2A> returns information about which mouse buttons are currently pressed.</span></span> <span data-ttu-id="ab685-113">@No__t-0, fare işaretçisinin ekran koordinatlarını döndürür ve <xref:System.Windows.Forms.Cursor.Position%2A> tarafından döndürülen değere eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="ab685-113">The <xref:System.Windows.Forms.Control.MousePosition%2A> returns the screen coordinates of the mouse pointer and is equivalent to the value returned by <xref:System.Windows.Forms.Cursor.Position%2A>.</span></span>

## <a name="converting-between-screen-and-client-coordinates"></a><span data-ttu-id="ab685-114">Ekran ve Istemci koordinatları arasında dönüştürme</span><span class="sxs-lookup"><span data-stu-id="ab685-114">Converting Between Screen and Client Coordinates</span></span>

<span data-ttu-id="ab685-115">Bazı fare konum bilgileri istemci koordinatlarındaki ve bazıları ekran koordinatlarından olduğundan, bir noktayı bir koordinat sisteminden diğerine dönüştürmeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="ab685-115">Because some mouse location information is in client coordinates and some is in screen coordinates, you may need to convert a point from one coordinate system to the other.</span></span> <span data-ttu-id="ab685-116">Bunu, <xref:System.Windows.Forms.Control> sınıfında bulunan <xref:System.Windows.Forms.Control.PointToClient%2A> ve <xref:System.Windows.Forms.Control.PointToScreen%2A> yöntemlerini kullanarak kolayca yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ab685-116">You can do this easily by using the <xref:System.Windows.Forms.Control.PointToClient%2A> and <xref:System.Windows.Forms.Control.PointToScreen%2A> methods available on the <xref:System.Windows.Forms.Control> class.</span></span>

## <a name="standard-click-event-behavior"></a><span data-ttu-id="ab685-117">Standart tıklama olayı davranışı</span><span class="sxs-lookup"><span data-stu-id="ab685-117">Standard Click Event Behavior</span></span>

<span data-ttu-id="ab685-118">Fare tıklaması olaylarını uygun sırada işlemek istiyorsanız, Windows Forms Denetimlerinde tıklama olaylarının nasıl oluşturulduğu sırayı bilmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="ab685-118">If you want to handle mouse click events in the proper order, you need to know the order in which click events are raised in Windows Forms controls.</span></span> <span data-ttu-id="ab685-119">Tüm Windows Forms denetimleri, bir fare düğmesine basıldığında ve serbest bırakıldığında (hangi fare düğmesinden bağımsız olarak), her bir denetim için aşağıdaki listede belirtilenler dışında, tıklama olaylarını aynı sırada yükseltir.</span><span class="sxs-lookup"><span data-stu-id="ab685-119">All Windows Forms controls raise click events in the same order when a mouse button is pressed and released (regardless of which mouse button), except where noted in the following list for individual controls.</span></span> <span data-ttu-id="ab685-120">Aşağıdaki listede, tek bir fare düğmesine tıklama için oluşturulan olayların sırası gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="ab685-120">The following list shows the order of events raised for a single mouse-button click:</span></span>

1. <span data-ttu-id="ab685-121"><xref:System.Windows.Forms.Control.MouseDown> olayı.</span><span class="sxs-lookup"><span data-stu-id="ab685-121"><xref:System.Windows.Forms.Control.MouseDown> event.</span></span>

2. <span data-ttu-id="ab685-122"><xref:System.Windows.Forms.Control.Click> olayı.</span><span class="sxs-lookup"><span data-stu-id="ab685-122"><xref:System.Windows.Forms.Control.Click> event.</span></span>

3. <span data-ttu-id="ab685-123"><xref:System.Windows.Forms.Control.MouseClick> olayı.</span><span class="sxs-lookup"><span data-stu-id="ab685-123"><xref:System.Windows.Forms.Control.MouseClick> event.</span></span>

4. <span data-ttu-id="ab685-124"><xref:System.Windows.Forms.Control.MouseUp> olayı.</span><span class="sxs-lookup"><span data-stu-id="ab685-124"><xref:System.Windows.Forms.Control.MouseUp> event.</span></span>

<span data-ttu-id="ab685-125">Bir çift fare düğmesi için oluşturulan olayların sırası aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="ab685-125">The following is the order of events raised for a double mouse-button click:</span></span>

1. <span data-ttu-id="ab685-126"><xref:System.Windows.Forms.Control.MouseDown> olayı.</span><span class="sxs-lookup"><span data-stu-id="ab685-126"><xref:System.Windows.Forms.Control.MouseDown> event.</span></span>

2. <span data-ttu-id="ab685-127"><xref:System.Windows.Forms.Control.Click> olayı.</span><span class="sxs-lookup"><span data-stu-id="ab685-127"><xref:System.Windows.Forms.Control.Click> event.</span></span>

3. <span data-ttu-id="ab685-128"><xref:System.Windows.Forms.Control.MouseClick> olayı.</span><span class="sxs-lookup"><span data-stu-id="ab685-128"><xref:System.Windows.Forms.Control.MouseClick> event.</span></span>

4. <span data-ttu-id="ab685-129"><xref:System.Windows.Forms.Control.MouseUp> olayı.</span><span class="sxs-lookup"><span data-stu-id="ab685-129"><xref:System.Windows.Forms.Control.MouseUp> event.</span></span>

5. <span data-ttu-id="ab685-130"><xref:System.Windows.Forms.Control.MouseDown> olayı.</span><span class="sxs-lookup"><span data-stu-id="ab685-130"><xref:System.Windows.Forms.Control.MouseDown> event.</span></span>

6. <span data-ttu-id="ab685-131"><xref:System.Windows.Forms.Control.DoubleClick> olayı.</span><span class="sxs-lookup"><span data-stu-id="ab685-131"><xref:System.Windows.Forms.Control.DoubleClick> event.</span></span> <span data-ttu-id="ab685-132">(Bu, söz konusu denetimin <xref:System.Windows.Forms.ControlStyles.StandardDoubleClick> stil biti `true` olarak ayarlanmış olmasına bağlı olarak farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="ab685-132">(This can vary, depending on whether the control in question has the <xref:System.Windows.Forms.ControlStyles.StandardDoubleClick> style bit set to `true`.</span></span> <span data-ttu-id="ab685-133">@No__t-0 biti ayarlama hakkında daha fazla bilgi için, <xref:System.Windows.Forms.Control.SetStyle%2A> yöntemine bakın.)</span><span class="sxs-lookup"><span data-stu-id="ab685-133">For more information about how to set a <xref:System.Windows.Forms.ControlStyles> bit, see the <xref:System.Windows.Forms.Control.SetStyle%2A> method.)</span></span>

7. <span data-ttu-id="ab685-134"><xref:System.Windows.Forms.Control.MouseDoubleClick> olayı.</span><span class="sxs-lookup"><span data-stu-id="ab685-134"><xref:System.Windows.Forms.Control.MouseDoubleClick> event.</span></span>

8. <span data-ttu-id="ab685-135"><xref:System.Windows.Forms.Control.MouseUp> olayı.</span><span class="sxs-lookup"><span data-stu-id="ab685-135"><xref:System.Windows.Forms.Control.MouseUp> event.</span></span>

<span data-ttu-id="ab685-136">Fare tıklama olaylarının sırasını gösteren bir kod örneği için bkz. [nasıl yapılır: Windows Forms Denetimlerinde Kullanıcı giriş olaylarını işleme](how-to-handle-user-input-events-in-windows-forms-controls.md).</span><span class="sxs-lookup"><span data-stu-id="ab685-136">For a code example that demonstrates the order of the mouse click events, see [How to: Handle User Input Events in Windows Forms Controls](how-to-handle-user-input-events-in-windows-forms-controls.md).</span></span>

### <a name="individual-controls"></a><span data-ttu-id="ab685-137">Bireysel denetimler</span><span class="sxs-lookup"><span data-stu-id="ab685-137">Individual Controls</span></span>

<span data-ttu-id="ab685-138">Aşağıdaki denetimler standart fare tıklaması olay davranışına uymuyor:</span><span class="sxs-lookup"><span data-stu-id="ab685-138">The following controls do not conform to the standard mouse click event behavior:</span></span>

- <xref:System.Windows.Forms.Button>
- <xref:System.Windows.Forms.CheckBox>
- <xref:System.Windows.Forms.ComboBox>
- <xref:System.Windows.Forms.RadioButton>

  > [!NOTE]
  > <span data-ttu-id="ab685-139">@No__t-0 denetimi için, daha sonra Kullanıcı düzenleme alanına, düğmeye veya listedeki bir öğeye tıkladığı takdirde ayrıntılı olay davranışı oluşur.</span><span class="sxs-lookup"><span data-stu-id="ab685-139">For the <xref:System.Windows.Forms.ComboBox> control, the event behavior detailed later occurs if the user clicks on the edit field, the button, or on an item within the list.</span></span>

  - <span data-ttu-id="ab685-140">Sol tıklama: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="ab685-140">Left click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>

  - <span data-ttu-id="ab685-141">Sağ tıklama: hiçbir tıklama olayı tetiklendi</span><span class="sxs-lookup"><span data-stu-id="ab685-141">Right click: No click events raised</span></span>

  - <span data-ttu-id="ab685-142">Sol çift tıklama: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="ab685-142">Left double-click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>

  - <span data-ttu-id="ab685-143">Sağ çift tıklama: hiçbir tıklama olayı tetiklendi</span><span class="sxs-lookup"><span data-stu-id="ab685-143">Right double-click: No click events raised</span></span>

- <span data-ttu-id="ab685-144"><xref:System.Windows.Forms.TextBox>, <xref:System.Windows.Forms.RichTextBox>, <xref:System.Windows.Forms.ListBox>, <xref:System.Windows.Forms.MaskedTextBox> ve <xref:System.Windows.Forms.CheckedListBox> denetimleri</span><span class="sxs-lookup"><span data-stu-id="ab685-144"><xref:System.Windows.Forms.TextBox>, <xref:System.Windows.Forms.RichTextBox>, <xref:System.Windows.Forms.ListBox>, <xref:System.Windows.Forms.MaskedTextBox>, and <xref:System.Windows.Forms.CheckedListBox> controls</span></span>

  > [!NOTE]
  > <span data-ttu-id="ab685-145">Daha sonra ayrıntılı olay davranışı Kullanıcı bu denetimlerin içinde herhangi bir yere tıkladığında oluşur.</span><span class="sxs-lookup"><span data-stu-id="ab685-145">The event behavior detailed later occurs when the user clicks anywhere within these controls.</span></span>

  - <span data-ttu-id="ab685-146">Sol tıklama: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="ab685-146">Left click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>

  - <span data-ttu-id="ab685-147">Sağ tıklama: hiçbir tıklama olayı tetiklendi</span><span class="sxs-lookup"><span data-stu-id="ab685-147">Right click: No click events raised</span></span>

  - <span data-ttu-id="ab685-148">Sol çift tıklama: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>, <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span><span class="sxs-lookup"><span data-stu-id="ab685-148">Left double-click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>, <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span></span>

  - <span data-ttu-id="ab685-149">Sağ çift tıklama: hiçbir tıklama olayı tetiklendi</span><span class="sxs-lookup"><span data-stu-id="ab685-149">Right double-click: No click events raised</span></span>

- <span data-ttu-id="ab685-150"><xref:System.Windows.Forms.ListView> denetimi</span><span class="sxs-lookup"><span data-stu-id="ab685-150"><xref:System.Windows.Forms.ListView> control</span></span>

  > [!NOTE]
  > <span data-ttu-id="ab685-151">Daha sonra ayrıntılı olay davranışı yalnızca Kullanıcı <xref:System.Windows.Forms.ListView> denetimindeki öğelerin tıkladığı zaman oluşur.</span><span class="sxs-lookup"><span data-stu-id="ab685-151">The event behavior detailed later occurs only when the user clicks on the items in the <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="ab685-152">Denetimde başka herhangi bir yere tıklama için hiçbir olay oluşturulmaz.</span><span class="sxs-lookup"><span data-stu-id="ab685-152">No events are raised for clicks anywhere else on the control.</span></span> <span data-ttu-id="ab685-153">Daha sonra açıklanan olaylara ek olarak, <xref:System.Windows.Forms.ListView> denetimiyle doğrulamayı kullanmak istiyorsanız, sizi ilgilendiren <xref:System.Windows.Forms.ListView.BeforeLabelEdit> ve <xref:System.Windows.Forms.ListView.AfterLabelEdit> olayları vardır.</span><span class="sxs-lookup"><span data-stu-id="ab685-153">In addition to the events described later, there are the <xref:System.Windows.Forms.ListView.BeforeLabelEdit> and <xref:System.Windows.Forms.ListView.AfterLabelEdit> events, which may be of interest to you if you want to use validation with the <xref:System.Windows.Forms.ListView> control.</span></span>

  - <span data-ttu-id="ab685-154">Sol tıklama: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="ab685-154">Left click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>

  - <span data-ttu-id="ab685-155">Sağ tıklama: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="ab685-155">Right click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>

  - <span data-ttu-id="ab685-156">Sol çift tıklama: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span><span class="sxs-lookup"><span data-stu-id="ab685-156">Left double-click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span></span>

  - <span data-ttu-id="ab685-157">Sağ çift tıklama: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span><span class="sxs-lookup"><span data-stu-id="ab685-157">Right double-click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span></span>

- <span data-ttu-id="ab685-158"><xref:System.Windows.Forms.TreeView> denetimi</span><span class="sxs-lookup"><span data-stu-id="ab685-158"><xref:System.Windows.Forms.TreeView> control</span></span>

  > [!NOTE]
  > <span data-ttu-id="ab685-159">Daha sonra ayrıntılı olay davranışı yalnızca Kullanıcı öğelerin kendilerini tıkladığı veya <xref:System.Windows.Forms.TreeView> denetimindeki öğelerin sağında oluşur.</span><span class="sxs-lookup"><span data-stu-id="ab685-159">The event behavior detailed later occurs only when the user clicks on the items themselves or to the right of the items in the <xref:System.Windows.Forms.TreeView> control.</span></span> <span data-ttu-id="ab685-160">Denetimde başka herhangi bir yere tıklama için hiçbir olay oluşturulmaz.</span><span class="sxs-lookup"><span data-stu-id="ab685-160">No events are raised for clicks anywhere else on the control.</span></span> <span data-ttu-id="ab685-161">Daha sonra açıklananlara ek olarak, <xref:System.Windows.Forms.TreeView> denetimiyle doğrulamayı kullanmak istiyorsanız, sizi ilgilendiren <xref:System.Windows.Forms.TreeView.BeforeCheck>, <xref:System.Windows.Forms.TreeView.BeforeSelect>, <xref:System.Windows.Forms.TreeView.BeforeLabelEdit>, <xref:System.Windows.Forms.TreeView.AfterSelect>, <xref:System.Windows.Forms.TreeView.AfterCheck> ve <xref:System.Windows.Forms.TreeView.AfterLabelEdit> olayları vardır.</span><span class="sxs-lookup"><span data-stu-id="ab685-161">In addition to those described later, there are the <xref:System.Windows.Forms.TreeView.BeforeCheck>, <xref:System.Windows.Forms.TreeView.BeforeSelect>, <xref:System.Windows.Forms.TreeView.BeforeLabelEdit>, <xref:System.Windows.Forms.TreeView.AfterSelect>, <xref:System.Windows.Forms.TreeView.AfterCheck>, and <xref:System.Windows.Forms.TreeView.AfterLabelEdit> events, which may be of interest to you if you want to use validation with the <xref:System.Windows.Forms.TreeView> control.</span></span>

  - <span data-ttu-id="ab685-162">Sol tıklama: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="ab685-162">Left click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>

  - <span data-ttu-id="ab685-163">Sağ tıklama: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="ab685-163">Right click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>

  - <span data-ttu-id="ab685-164">Sol çift tıklama: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span><span class="sxs-lookup"><span data-stu-id="ab685-164">Left double-click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span></span>

  - <span data-ttu-id="ab685-165">Sağ çift tıklama: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span><span class="sxs-lookup"><span data-stu-id="ab685-165">Right double-click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span></span>

### <a name="painting-behavior-of-toggle-controls"></a><span data-ttu-id="ab685-166">İki durumlu denetimlerin boyama davranışı</span><span class="sxs-lookup"><span data-stu-id="ab685-166">Painting behavior of toggle controls</span></span>

<span data-ttu-id="ab685-167">@No__t-0 sınıfından türetilen denetimler gibi geçiş denetimleri, fare tıklama olayları ile birlikte aşağıdaki farklı boyama davranışına sahiptir:</span><span class="sxs-lookup"><span data-stu-id="ab685-167">Toggle controls, such as the controls deriving from the <xref:System.Windows.Forms.ButtonBase> class, have the following distinctive painting behavior in combination with mouse click events:</span></span>

1. <span data-ttu-id="ab685-168">Kullanıcı fare düğmesine basar.</span><span class="sxs-lookup"><span data-stu-id="ab685-168">The user presses the mouse button.</span></span>

2. <span data-ttu-id="ab685-169">Denetim, basılan durumu boyar.</span><span class="sxs-lookup"><span data-stu-id="ab685-169">The control paints in the pressed state.</span></span>

3. <span data-ttu-id="ab685-170">@No__t-0 olayı tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="ab685-170">The <xref:System.Windows.Forms.Control.MouseDown> event is raised.</span></span>

4. <span data-ttu-id="ab685-171">Kullanıcı fare düğmesini serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="ab685-171">The user releases the mouse button.</span></span>

5. <span data-ttu-id="ab685-172">Denetim, oluşturulan durumu boyar.</span><span class="sxs-lookup"><span data-stu-id="ab685-172">The control paints in the raised state.</span></span>

6. <span data-ttu-id="ab685-173">@No__t-0 olayı tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="ab685-173">The <xref:System.Windows.Forms.Control.Click> event is raised.</span></span>

7. <span data-ttu-id="ab685-174">@No__t-0 olayı tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="ab685-174">The <xref:System.Windows.Forms.Control.MouseClick> event is raised.</span></span>

8. <span data-ttu-id="ab685-175">@No__t-0 olayı tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="ab685-175">The <xref:System.Windows.Forms.Control.MouseUp> event is raised.</span></span>

    > [!NOTE]
    > <span data-ttu-id="ab685-176">Fare düğmesi kapalıyken Kullanıcı işaretçiyi geçiş denetiminin dışına taşımışsa (örneğin, fareyi basıldığında <xref:System.Windows.Forms.Button> denetimi dışına taşıma gibi), iki durumlu denetim, ortaya çıkan ve yalnızca <xref:System.Windows.Forms.Control.MouseUp> olayı oluşur.</span><span class="sxs-lookup"><span data-stu-id="ab685-176">If the user moves the pointer out of the toggle control while the mouse button is down (such as moving the mouse off the <xref:System.Windows.Forms.Button> control while it is pressed), the toggle control will paint in the raised state and only the <xref:System.Windows.Forms.Control.MouseUp> event occurs.</span></span> <span data-ttu-id="ab685-177">@No__t-0 veya <xref:System.Windows.Forms.Control.MouseClick> olayları bu durumda gerçekleşmeyecektir.</span><span class="sxs-lookup"><span data-stu-id="ab685-177">The <xref:System.Windows.Forms.Control.Click> or <xref:System.Windows.Forms.Control.MouseClick> events will not occur in this situation.</span></span>

## <a name="see-also"></a><span data-ttu-id="ab685-178">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ab685-178">See also</span></span>

- [<span data-ttu-id="ab685-179">Bir Windows Forms Uygulamasında Fare Girdisi</span><span class="sxs-lookup"><span data-stu-id="ab685-179">Mouse Input in a Windows Forms Application</span></span>](mouse-input-in-a-windows-forms-application.md)
