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
ms.openlocfilehash: 181d01f6e688b94876f77155bf598aba129e9fbf
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69949907"
---
# <a name="mouse-events-in-windows-forms"></a><span data-ttu-id="6e64a-102">Windows Forms'ta Fare Olayları</span><span class="sxs-lookup"><span data-stu-id="6e64a-102">Mouse Events in Windows Forms</span></span>

<span data-ttu-id="6e64a-103">Fare girişini işlerken, genellikle fare işaretçisinin konumunu ve fare düğmelerinin durumunu bilmek istersiniz.</span><span class="sxs-lookup"><span data-stu-id="6e64a-103">When you handle mouse input, you usually want to know the location of the mouse pointer and the state of the mouse buttons.</span></span> <span data-ttu-id="6e64a-104">Bu konu, fare olaylarından bu bilgilerin nasıl alınacağı hakkında ayrıntılar sağlar ve Windows Forms Denetimlerinde fare tıklaması olaylarının nasıl oluşturulduğu sırasını açıklar.</span><span class="sxs-lookup"><span data-stu-id="6e64a-104">This topic provides details on how to get this information from mouse events, and explains the order in which mouse click events are raised in Windows Forms controls.</span></span> <span data-ttu-id="6e64a-105">Tüm fare olaylarının listesi ve açıklaması için bkz. [fare girişinin Windows Forms nasıl çalıştığı](how-mouse-input-works-in-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="6e64a-105">For a list and description of all of the mouse events, see [How Mouse Input Works in Windows Forms](how-mouse-input-works-in-windows-forms.md).</span></span>  <span data-ttu-id="6e64a-106">Ayrıca bkz. [olay Işleyicilerine genel bakış (Windows Forms)](event-handlers-overview-windows-forms.md) ve [olaylara genel bakış (Windows Forms)](events-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="6e64a-106">Also see [Event Handlers Overview (Windows Forms)](event-handlers-overview-windows-forms.md) and [Events Overview (Windows Forms)](events-overview-windows-forms.md).</span></span>

## <a name="mouse-information"></a><span data-ttu-id="6e64a-107">Fare bilgileri</span><span class="sxs-lookup"><span data-stu-id="6e64a-107">Mouse Information</span></span>

<span data-ttu-id="6e64a-108">Bir <xref:System.Windows.Forms.MouseEventArgs> fare düğmesine tıklanması ve fare hareketlerini izlemek için ilgili fare olaylarının işleyicilerine gönderilir.</span><span class="sxs-lookup"><span data-stu-id="6e64a-108">A <xref:System.Windows.Forms.MouseEventArgs> is sent to the handlers of mouse events related to clicking a mouse button and tracking mouse movements.</span></span> <span data-ttu-id="6e64a-109"><xref:System.Windows.Forms.MouseEventArgs>istemci koordinatlarındaki fare işaretçisinin konumu, fare düğmelerine basılan ve Fare tekerleğinin kaydırılışına dahil olmak üzere, farenin geçerli durumu hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="6e64a-109"><xref:System.Windows.Forms.MouseEventArgs> provides information about the current state of the mouse, including the location of the mouse pointer in client coordinates, which mouse buttons are pressed, and whether the mouse wheel has scrolled.</span></span> <span data-ttu-id="6e64a-110">Yalnızca fare işaretçisi bir denetimin sınırları girildiğinde veya sol tarafta bilgilendirenler gibi birçok fare olayı, daha fazla bilgi olmadan olay işleyicisine gönderin <xref:System.EventArgs> .</span><span class="sxs-lookup"><span data-stu-id="6e64a-110">Several mouse events, such as those that simply notify when the mouse pointer has entered or left the bounds of a control, send an <xref:System.EventArgs> to the event handler with no further information.</span></span>

<span data-ttu-id="6e64a-111">Fare düğmelerinin geçerli durumunu veya fare işaretçisinin konumunu biliyorsanız ve bir fare olayını işlemeyi önlemek istiyorsanız, <xref:System.Windows.Forms.Control.MouseButtons%2A> <xref:System.Windows.Forms.Control> sınıfının ve <xref:System.Windows.Forms.Control.MousePosition%2A> özelliklerini de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6e64a-111">If you want to know the current state of the mouse buttons or the location of the mouse pointer, and you want to avoid handling a mouse event, you can also use the <xref:System.Windows.Forms.Control.MouseButtons%2A> and <xref:System.Windows.Forms.Control.MousePosition%2A> properties of the <xref:System.Windows.Forms.Control> class.</span></span> <span data-ttu-id="6e64a-112"><xref:System.Windows.Forms.Control.MouseButtons%2A>Şu anda basılan fare düğmelerine ilişkin bilgileri döndürür.</span><span class="sxs-lookup"><span data-stu-id="6e64a-112"><xref:System.Windows.Forms.Control.MouseButtons%2A> returns information about which mouse buttons are currently pressed.</span></span> <span data-ttu-id="6e64a-113">, <xref:System.Windows.Forms.Control.MousePosition%2A> Fare işaretçisinin ekran koordinatlarını döndürür ve tarafından <xref:System.Windows.Forms.Cursor.Position%2A>döndürülen değere eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="6e64a-113">The <xref:System.Windows.Forms.Control.MousePosition%2A> returns the screen coordinates of the mouse pointer and is equivalent to the value returned by <xref:System.Windows.Forms.Cursor.Position%2A>.</span></span>

## <a name="converting-between-screen-and-client-coordinates"></a><span data-ttu-id="6e64a-114">Ekran ve Istemci koordinatları arasında dönüştürme</span><span class="sxs-lookup"><span data-stu-id="6e64a-114">Converting Between Screen and Client Coordinates</span></span>

<span data-ttu-id="6e64a-115">Bazı fare konum bilgileri istemci koordinatlarındaki ve bazıları ekran koordinatlarından olduğundan, bir noktayı bir koordinat sisteminden diğerine dönüştürmeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="6e64a-115">Because some mouse location information is in client coordinates and some is in screen coordinates, you may need to convert a point from one coordinate system to the other.</span></span> <span data-ttu-id="6e64a-116">Sınıfı üzerinde <xref:System.Windows.Forms.Control.PointToScreen%2A> <xref:System.Windows.Forms.Control.PointToClient%2A> kullanılabilenveyöntemlerinikullanarakbunukolaycayapabilirsiniz<xref:System.Windows.Forms.Control> .</span><span class="sxs-lookup"><span data-stu-id="6e64a-116">You can do this easily by using the <xref:System.Windows.Forms.Control.PointToClient%2A> and <xref:System.Windows.Forms.Control.PointToScreen%2A> methods available on the <xref:System.Windows.Forms.Control> class.</span></span>

## <a name="standard-click-event-behavior"></a><span data-ttu-id="6e64a-117">Standart tıklama olayı davranışı</span><span class="sxs-lookup"><span data-stu-id="6e64a-117">Standard Click Event Behavior</span></span>

<span data-ttu-id="6e64a-118">Fare tıklaması olaylarını uygun sırada işlemek istiyorsanız, Windows Forms Denetimlerinde tıklama olaylarının nasıl oluşturulduğu sırayı bilmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="6e64a-118">If you want to handle mouse click events in the proper order, you need to know the order in which click events are raised in Windows Forms controls.</span></span> <span data-ttu-id="6e64a-119">Tüm Windows Forms denetimleri, bir fare düğmesine basıldığında ve serbest bırakıldığında (hangi fare düğmesinden bağımsız olarak), her bir denetim için aşağıdaki listede belirtilenler dışında, tıklama olaylarını aynı sırada yükseltir.</span><span class="sxs-lookup"><span data-stu-id="6e64a-119">All Windows Forms controls raise click events in the same order when a mouse button is pressed and released (regardless of which mouse button), except where noted in the following list for individual controls.</span></span> <span data-ttu-id="6e64a-120">Aşağıdaki listede, tek bir fare düğmesine tıklama için oluşturulan olayların sırası gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="6e64a-120">The following list shows the order of events raised for a single mouse-button click:</span></span>

1. <span data-ttu-id="6e64a-121"><xref:System.Windows.Forms.Control.MouseDown>olay.</span><span class="sxs-lookup"><span data-stu-id="6e64a-121"><xref:System.Windows.Forms.Control.MouseDown> event.</span></span>

2. <span data-ttu-id="6e64a-122"><xref:System.Windows.Forms.Control.Click>olay.</span><span class="sxs-lookup"><span data-stu-id="6e64a-122"><xref:System.Windows.Forms.Control.Click> event.</span></span>

3. <span data-ttu-id="6e64a-123"><xref:System.Windows.Forms.Control.MouseClick>olay.</span><span class="sxs-lookup"><span data-stu-id="6e64a-123"><xref:System.Windows.Forms.Control.MouseClick> event.</span></span>

4. <span data-ttu-id="6e64a-124"><xref:System.Windows.Forms.Control.MouseUp>olay.</span><span class="sxs-lookup"><span data-stu-id="6e64a-124"><xref:System.Windows.Forms.Control.MouseUp> event.</span></span>

<span data-ttu-id="6e64a-125">Bir çift fare düğmesine tıklama için oluşturulan olayların sırası aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="6e64a-125">Following is the order of events raised for a double mouse-button click:</span></span>

1. <span data-ttu-id="6e64a-126"><xref:System.Windows.Forms.Control.MouseDown>olay.</span><span class="sxs-lookup"><span data-stu-id="6e64a-126"><xref:System.Windows.Forms.Control.MouseDown> event.</span></span>

2. <span data-ttu-id="6e64a-127"><xref:System.Windows.Forms.Control.Click>olay.</span><span class="sxs-lookup"><span data-stu-id="6e64a-127"><xref:System.Windows.Forms.Control.Click> event.</span></span>

3. <span data-ttu-id="6e64a-128"><xref:System.Windows.Forms.Control.MouseClick>olay.</span><span class="sxs-lookup"><span data-stu-id="6e64a-128"><xref:System.Windows.Forms.Control.MouseClick> event.</span></span>

4. <span data-ttu-id="6e64a-129"><xref:System.Windows.Forms.Control.MouseUp>olay.</span><span class="sxs-lookup"><span data-stu-id="6e64a-129"><xref:System.Windows.Forms.Control.MouseUp> event.</span></span>

5. <span data-ttu-id="6e64a-130"><xref:System.Windows.Forms.Control.MouseDown>olay.</span><span class="sxs-lookup"><span data-stu-id="6e64a-130"><xref:System.Windows.Forms.Control.MouseDown> event.</span></span>

6. <span data-ttu-id="6e64a-131"><xref:System.Windows.Forms.Control.DoubleClick>olay.</span><span class="sxs-lookup"><span data-stu-id="6e64a-131"><xref:System.Windows.Forms.Control.DoubleClick> event.</span></span> <span data-ttu-id="6e64a-132">(Bu, söz konusu <xref:System.Windows.Forms.ControlStyles.StandardDoubleClick> denetimin stil biti olarak `true`ayarlanmış olmasına bağlı olarak farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="6e64a-132">(This can vary, depending on whether the control in question has the <xref:System.Windows.Forms.ControlStyles.StandardDoubleClick> style bit set to `true`.</span></span> <span data-ttu-id="6e64a-133"><xref:System.Windows.Forms.ControlStyles> Bit ayarlama hakkında daha fazla bilgi için <xref:System.Windows.Forms.Control.SetStyle%2A> yöntemine bakın.)</span><span class="sxs-lookup"><span data-stu-id="6e64a-133">For more information about how to set a <xref:System.Windows.Forms.ControlStyles> bit, see the <xref:System.Windows.Forms.Control.SetStyle%2A> method.)</span></span>

7. <span data-ttu-id="6e64a-134"><xref:System.Windows.Forms.Control.MouseDoubleClick>olay.</span><span class="sxs-lookup"><span data-stu-id="6e64a-134"><xref:System.Windows.Forms.Control.MouseDoubleClick> event.</span></span>

8. <span data-ttu-id="6e64a-135"><xref:System.Windows.Forms.Control.MouseUp>olay.</span><span class="sxs-lookup"><span data-stu-id="6e64a-135"><xref:System.Windows.Forms.Control.MouseUp> event.</span></span>

<span data-ttu-id="6e64a-136">Fare tıklama olaylarının sırasını gösteren bir kod örneği için bkz [. nasıl yapılır: Windows Forms denetimlerinde](how-to-handle-user-input-events-in-windows-forms-controls.md)Kullanıcı giriş olaylarını işleyin.</span><span class="sxs-lookup"><span data-stu-id="6e64a-136">For a code example that demonstrates the order of the mouse click events, see [How to: Handle User Input Events in Windows Forms Controls](how-to-handle-user-input-events-in-windows-forms-controls.md).</span></span>

### <a name="individual-controls"></a><span data-ttu-id="6e64a-137">Bireysel denetimler</span><span class="sxs-lookup"><span data-stu-id="6e64a-137">Individual Controls</span></span>

<span data-ttu-id="6e64a-138">Aşağıdaki denetimler standart fare tıklaması olay davranışına uymuyor:</span><span class="sxs-lookup"><span data-stu-id="6e64a-138">The following controls do not conform to the standard mouse click event behavior:</span></span>

- <span data-ttu-id="6e64a-139"><xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.CheckBox>, <xref:System.Windows.Forms.ComboBox>, ve <xref:System.Windows.Forms.RadioButton> denetimleri</span><span class="sxs-lookup"><span data-stu-id="6e64a-139"><xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.CheckBox>, <xref:System.Windows.Forms.ComboBox>, and <xref:System.Windows.Forms.RadioButton> controls</span></span>

  > [!NOTE]
  > <span data-ttu-id="6e64a-140"><xref:System.Windows.Forms.ComboBox> Denetim için, Kullanıcı düzenleme alanına, düğmeye veya listedeki bir öğeye tıkladığında daha sonra ayrıntılı olay davranışı oluşur.</span><span class="sxs-lookup"><span data-stu-id="6e64a-140">For the <xref:System.Windows.Forms.ComboBox> control, the event behavior detailed later occurs if the user clicks on the edit field, the button, or on an item within the list.</span></span>

  - <span data-ttu-id="6e64a-141">Sol tıklama: <xref:System.Windows.Forms.Control.Click>,<xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="6e64a-141">Left click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>

  - <span data-ttu-id="6e64a-142">Sağ tıklayın: Hiçbir tıklama olayı harekete geçirilir</span><span class="sxs-lookup"><span data-stu-id="6e64a-142">Right click: No click events raised</span></span>

  - <span data-ttu-id="6e64a-143">Sol çift tıklama: <xref:System.Windows.Forms.Control.Click>,; <xref:System.Windows.Forms.Control.MouseClick> <xref:System.Windows.Forms.Control.Click>,<xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="6e64a-143">Left double-click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>

  - <span data-ttu-id="6e64a-144">Sağ çift tıklayın: Hiçbir tıklama olayı harekete geçirilir</span><span class="sxs-lookup"><span data-stu-id="6e64a-144">Right double-click: No click events raised</span></span>

- <span data-ttu-id="6e64a-145"><xref:System.Windows.Forms.TextBox>, <xref:System.Windows.Forms.RichTextBox> ,<xref:System.Windows.Forms.ListBox>, ve<xref:System.Windows.Forms.CheckedListBox> denetimleri <xref:System.Windows.Forms.MaskedTextBox></span><span class="sxs-lookup"><span data-stu-id="6e64a-145"><xref:System.Windows.Forms.TextBox>, <xref:System.Windows.Forms.RichTextBox>, <xref:System.Windows.Forms.ListBox>, <xref:System.Windows.Forms.MaskedTextBox>, and <xref:System.Windows.Forms.CheckedListBox> controls</span></span>

  > [!NOTE]
  > <span data-ttu-id="6e64a-146">Daha sonra ayrıntılı olay davranışı Kullanıcı bu denetimlerin içinde herhangi bir yere tıkladığında oluşur.</span><span class="sxs-lookup"><span data-stu-id="6e64a-146">The event behavior detailed later occurs when the user clicks anywhere within these controls.</span></span>

  - <span data-ttu-id="6e64a-147">Sol tıklama: <xref:System.Windows.Forms.Control.Click>,<xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="6e64a-147">Left click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>

  - <span data-ttu-id="6e64a-148">Sağ tıklayın: Hiçbir tıklama olayı harekete geçirilir</span><span class="sxs-lookup"><span data-stu-id="6e64a-148">Right click: No click events raised</span></span>

  - <span data-ttu-id="6e64a-149">Sol çift tıklama: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>, <xref:System.Windows.Forms.Control.DoubleClick>,<xref:System.Windows.Forms.Control.MouseDoubleClick></span><span class="sxs-lookup"><span data-stu-id="6e64a-149">Left double-click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>, <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span></span>

  - <span data-ttu-id="6e64a-150">Sağ çift tıklayın: Hiçbir tıklama olayı harekete geçirilir</span><span class="sxs-lookup"><span data-stu-id="6e64a-150">Right double-click: No click events raised</span></span>

- <span data-ttu-id="6e64a-151"><xref:System.Windows.Forms.ListView>denetimle</span><span class="sxs-lookup"><span data-stu-id="6e64a-151"><xref:System.Windows.Forms.ListView> control</span></span>

  > [!NOTE]
  > <span data-ttu-id="6e64a-152">Daha sonra ayrıntılı olay davranışı yalnızca Kullanıcı <xref:System.Windows.Forms.ListView> denetimdeki öğelere tıkladığı zaman gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="6e64a-152">The event behavior detailed later occurs only when the user clicks on the items in the <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="6e64a-153">Denetimde başka herhangi bir yere tıklama için hiçbir olay oluşturulmaz.</span><span class="sxs-lookup"><span data-stu-id="6e64a-153">No events are raised for clicks anywhere else on the control.</span></span> <span data-ttu-id="6e64a-154">Daha sonra <xref:System.Windows.Forms.ListView.BeforeLabelEdit> açıklanan olaylara ek olarak, <xref:System.Windows.Forms.ListView> denetimi ile doğrulama kullanmak istiyorsanız <xref:System.Windows.Forms.ListView.AfterLabelEdit> , sizi ilgilendirebilecek ve olayları vardır.</span><span class="sxs-lookup"><span data-stu-id="6e64a-154">In addition to the events described later, there are the <xref:System.Windows.Forms.ListView.BeforeLabelEdit> and <xref:System.Windows.Forms.ListView.AfterLabelEdit> events, which may be of interest to you if you want to use validation with the <xref:System.Windows.Forms.ListView> control.</span></span>

  - <span data-ttu-id="6e64a-155">Sol tıklama: <xref:System.Windows.Forms.Control.Click>,<xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="6e64a-155">Left click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>

  - <span data-ttu-id="6e64a-156">Sağ tıklayın: <xref:System.Windows.Forms.Control.Click>,<xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="6e64a-156">Right click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>

  - <span data-ttu-id="6e64a-157">Sol çift tıklama: <xref:System.Windows.Forms.Control.Click>,; <xref:System.Windows.Forms.Control.MouseClick> <xref:System.Windows.Forms.Control.DoubleClick>,<xref:System.Windows.Forms.Control.MouseDoubleClick></span><span class="sxs-lookup"><span data-stu-id="6e64a-157">Left double-click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span></span>

  - <span data-ttu-id="6e64a-158">Sağ çift tıklayın: <xref:System.Windows.Forms.Control.Click>,; <xref:System.Windows.Forms.Control.MouseClick> <xref:System.Windows.Forms.Control.DoubleClick>,<xref:System.Windows.Forms.Control.MouseDoubleClick></span><span class="sxs-lookup"><span data-stu-id="6e64a-158">Right double-click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span></span>

- <span data-ttu-id="6e64a-159"><xref:System.Windows.Forms.TreeView>denetimle</span><span class="sxs-lookup"><span data-stu-id="6e64a-159"><xref:System.Windows.Forms.TreeView> control</span></span>

  > [!NOTE]
  > <span data-ttu-id="6e64a-160">Daha sonra ayrıntılı olay davranışı yalnızca Kullanıcı öğelerin kendilerini tıkladığı veya <xref:System.Windows.Forms.TreeView> denetimdeki öğelerin sağında oluşur.</span><span class="sxs-lookup"><span data-stu-id="6e64a-160">The event behavior detailed later occurs only when the user clicks on the items themselves or to the right of the items in the <xref:System.Windows.Forms.TreeView> control.</span></span> <span data-ttu-id="6e64a-161">Denetimde başka herhangi bir yere tıklama için hiçbir olay oluşturulmaz.</span><span class="sxs-lookup"><span data-stu-id="6e64a-161">No events are raised for clicks anywhere else on the control.</span></span> <span data-ttu-id="6e64a-162"><xref:System.Windows.Forms.TreeView.BeforeCheck>Daha sonra açıklananlara ek olarak, <xref:System.Windows.Forms.TreeView.BeforeLabelEdit> <xref:System.Windows.Forms.TreeView> denetim ile doğrulama kullanmak istiyorsanız, <xref:System.Windows.Forms.TreeView.AfterSelect>,,, <xref:System.Windows.Forms.TreeView.AfterLabelEdit> ve olayları ilginizi çekmiş olabilir. <xref:System.Windows.Forms.TreeView.BeforeSelect> <xref:System.Windows.Forms.TreeView.AfterCheck> .</span><span class="sxs-lookup"><span data-stu-id="6e64a-162">In addition to those described later, there are the <xref:System.Windows.Forms.TreeView.BeforeCheck>, <xref:System.Windows.Forms.TreeView.BeforeSelect>, <xref:System.Windows.Forms.TreeView.BeforeLabelEdit>, <xref:System.Windows.Forms.TreeView.AfterSelect>, <xref:System.Windows.Forms.TreeView.AfterCheck>, and <xref:System.Windows.Forms.TreeView.AfterLabelEdit> events, which may be of interest to you if you want to use validation with the <xref:System.Windows.Forms.TreeView> control.</span></span>

  - <span data-ttu-id="6e64a-163">Sol tıklama: <xref:System.Windows.Forms.Control.Click>,<xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="6e64a-163">Left click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>

  - <span data-ttu-id="6e64a-164">Sağ tıklayın: <xref:System.Windows.Forms.Control.Click>,<xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="6e64a-164">Right click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>

  - <span data-ttu-id="6e64a-165">Sol çift tıklama: <xref:System.Windows.Forms.Control.Click>,; <xref:System.Windows.Forms.Control.MouseClick> <xref:System.Windows.Forms.Control.DoubleClick>,<xref:System.Windows.Forms.Control.MouseDoubleClick></span><span class="sxs-lookup"><span data-stu-id="6e64a-165">Left double-click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span></span>

  - <span data-ttu-id="6e64a-166">Sağ çift tıklayın: <xref:System.Windows.Forms.Control.Click>,; <xref:System.Windows.Forms.Control.MouseClick> <xref:System.Windows.Forms.Control.DoubleClick>,<xref:System.Windows.Forms.Control.MouseDoubleClick></span><span class="sxs-lookup"><span data-stu-id="6e64a-166">Right double-click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span></span>

### <a name="painting-behavior-of-toggle-controls"></a><span data-ttu-id="6e64a-167">Iki durumlu denetimlerin boyama davranışı</span><span class="sxs-lookup"><span data-stu-id="6e64a-167">Painting Behavior of Toggle Controls</span></span>

<span data-ttu-id="6e64a-168"><xref:System.Windows.Forms.ButtonBase> Sınıfından türetilen denetimler gibi geçiş denetimleri, fare tıklama olayları ile birlikte aşağıdaki farklı boyama davranışına sahiptir:</span><span class="sxs-lookup"><span data-stu-id="6e64a-168">Toggle controls, such as the controls deriving from the <xref:System.Windows.Forms.ButtonBase> class, have the following distinctive painting behavior in combination with mouse click events:</span></span>

1. <span data-ttu-id="6e64a-169">Kullanıcı fare düğmesine basar.</span><span class="sxs-lookup"><span data-stu-id="6e64a-169">The user presses the mouse button.</span></span>

2. <span data-ttu-id="6e64a-170">Denetim, basılan durumu boyar.</span><span class="sxs-lookup"><span data-stu-id="6e64a-170">The control paints in the pressed state.</span></span>

3. <span data-ttu-id="6e64a-171"><xref:System.Windows.Forms.Control.MouseDown> Olay tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="6e64a-171">The <xref:System.Windows.Forms.Control.MouseDown> event is raised.</span></span>

4. <span data-ttu-id="6e64a-172">Kullanıcı fare düğmesini serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="6e64a-172">The user releases the mouse button.</span></span>

5. <span data-ttu-id="6e64a-173">Denetim, oluşturulan durumu boyar.</span><span class="sxs-lookup"><span data-stu-id="6e64a-173">The control paints in the raised state.</span></span>

6. <span data-ttu-id="6e64a-174"><xref:System.Windows.Forms.Control.Click> Olay tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="6e64a-174">The <xref:System.Windows.Forms.Control.Click> event is raised.</span></span>

7. <span data-ttu-id="6e64a-175"><xref:System.Windows.Forms.Control.MouseClick> Olay tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="6e64a-175">The <xref:System.Windows.Forms.Control.MouseClick> event is raised.</span></span>

8. <span data-ttu-id="6e64a-176"><xref:System.Windows.Forms.Control.MouseUp> Olay tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="6e64a-176">The <xref:System.Windows.Forms.Control.MouseUp> event is raised.</span></span>

    > [!NOTE]
    > <span data-ttu-id="6e64a-177">Fare düğmesi kapalıyken Kullanıcı işaretçiyi iki durumlu denetimin dışına taşımışsa (basıldığında fareyi <xref:System.Windows.Forms.Button> denetimin dışına taşımak gibi), geçiş denetimi, ortaya çıkan durumu boyar ve <xref:System.Windows.Forms.Control.MouseUp> yalnızca olay meydana gelir.</span><span class="sxs-lookup"><span data-stu-id="6e64a-177">If the user moves the pointer out of the toggle control while the mouse button is down (such as moving the mouse off the <xref:System.Windows.Forms.Button> control while it is pressed), the toggle control will paint in the raised state and only the <xref:System.Windows.Forms.Control.MouseUp> event occurs.</span></span> <span data-ttu-id="6e64a-178"><xref:System.Windows.Forms.Control.Click> Veya<xref:System.Windows.Forms.Control.MouseClick> olayları bu durumda gerçekleşmeyecektir.</span><span class="sxs-lookup"><span data-stu-id="6e64a-178">The <xref:System.Windows.Forms.Control.Click> or <xref:System.Windows.Forms.Control.MouseClick> events will not occur in this situation.</span></span>

## <a name="see-also"></a><span data-ttu-id="6e64a-179">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6e64a-179">See also</span></span>

- [<span data-ttu-id="6e64a-180">Bir Windows Forms Uygulamasında Fare Girdisi</span><span class="sxs-lookup"><span data-stu-id="6e64a-180">Mouse Input in a Windows Forms Application</span></span>](mouse-input-in-a-windows-forms-application.md)
