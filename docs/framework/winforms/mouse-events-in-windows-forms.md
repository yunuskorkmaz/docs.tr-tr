---
title: "Windows Forms'ta Fare Olayları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 803f2daab5b8f6e216effe4a9ae9f34752d24e70
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="mouse-events-in-windows-forms"></a><span data-ttu-id="aef00-102">Windows Forms'ta Fare Olayları</span><span class="sxs-lookup"><span data-stu-id="aef00-102">Mouse Events in Windows Forms</span></span>
<span data-ttu-id="aef00-103">Fare girişi uyguluyorsanız, genellikle fare konumunu işaretçi ve fare düğmelerinin durumunu bilmek ister.</span><span class="sxs-lookup"><span data-stu-id="aef00-103">When you handle mouse input, you usually want to know the location of the mouse pointer and the state of the mouse buttons.</span></span> <span data-ttu-id="aef00-104">Bu konuda ayrıntıları fare olayları bu bilgilerin nasıl alınacağını sağlar ve hangi fare tıklatma Windows Forms denetimlerindeki olaylar oluşturulur sipariş açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="aef00-104">This topic provides details on how to get this information from mouse events, and explains the order in which mouse click events are raised in Windows Forms controls.</span></span> <span data-ttu-id="aef00-105">Liste ve tüm fare olayları açıklaması için bkz: [nasıl fare giriş çalışır Windows Forms'ta](../../../docs/framework/winforms/how-mouse-input-works-in-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="aef00-105">For a list and description of all of the mouse events, see [How Mouse Input Works in Windows Forms](../../../docs/framework/winforms/how-mouse-input-works-in-windows-forms.md).</span></span>  <span data-ttu-id="aef00-106">Ayrıca bkz. [olay işleyicilerine genel bakış (Windows Forms)](http://msdn.microsoft.com/library/be6fx1bb\(v=vs.110\)), [olaylara genel bakış (Windows Forms)](http://msdn.microsoft.com/library/1h12f09z\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="aef00-106">Also see [Event Handlers Overview (Windows Forms)](http://msdn.microsoft.com/library/be6fx1bb\(v=vs.110\)), [Events Overview (Windows Forms)](http://msdn.microsoft.com/library/1h12f09z\(v=vs.110\))</span></span>  
  
## <a name="mouse-information"></a><span data-ttu-id="aef00-107">Fare bilgileri</span><span class="sxs-lookup"><span data-stu-id="aef00-107">Mouse Information</span></span>  
 <span data-ttu-id="aef00-108">A <xref:System.Windows.Forms.MouseEventArgs> fare düğmesini tıklatarak ve fare hareketleri izleme ile ilgili fare olayları işleyicileri gönderilir.</span><span class="sxs-lookup"><span data-stu-id="aef00-108">A <xref:System.Windows.Forms.MouseEventArgs> is sent to the handlers of mouse events related to clicking a mouse button and tracking mouse movements.</span></span> <span data-ttu-id="aef00-109"><xref:System.Windows.Forms.MouseEventArgs>Fare işaretçisini konumunu fare düğmelere basıldığında ve fare tekerleği olup kaydırılan istemci koordinatlarında dahil olmak üzere fareyi geçerli durumu hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="aef00-109"><xref:System.Windows.Forms.MouseEventArgs> provides information about the current state of the mouse, including the location of the mouse pointer in client coordinates, which mouse buttons are pressed, and whether the mouse wheel has scrolled.</span></span> <span data-ttu-id="aef00-110">Birkaç fare olayları, yalnızca bildir olanlar gibi fare işaretçisini girilen veya bir denetim sınırlarının sol, gönderme bir <xref:System.EventArgs> olay işleyici ile daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="aef00-110">Several mouse events, such as those that simply notify when the mouse pointer has entered or left the bounds of a control, send an <xref:System.EventArgs> to the event handler with no further information.</span></span>  
  
 <span data-ttu-id="aef00-111">Fare düğmeleri veya fare işaretçisini konumunu geçerli durumunu bilmek ister ve fare olayı işleme önlemek istiyorsanız, de kullanabilirsiniz, <xref:System.Windows.Forms.Control.MouseButtons%2A> ve <xref:System.Windows.Forms.Control.MousePosition%2A> özelliklerini <xref:System.Windows.Forms.Control> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="aef00-111">If you want to know the current state of the mouse buttons or the location of the mouse pointer, and you want to avoid handling a mouse event, you can also use the <xref:System.Windows.Forms.Control.MouseButtons%2A> and <xref:System.Windows.Forms.Control.MousePosition%2A> properties of the <xref:System.Windows.Forms.Control> class.</span></span> <span data-ttu-id="aef00-112"><xref:System.Windows.Forms.Control.MouseButtons%2A>hakkında şu anda fare düğmelere basıldığında bilgileri döndürür.</span><span class="sxs-lookup"><span data-stu-id="aef00-112"><xref:System.Windows.Forms.Control.MouseButtons%2A> returns information about which mouse buttons are currently pressed.</span></span> <span data-ttu-id="aef00-113"><xref:System.Windows.Forms.Control.MousePosition%2A> Fare işaretçisini ekran koordinatları döndürür ve tarafından döndürülen değer eşdeğerdir <xref:System.Windows.Forms.Cursor.Position%2A>.</span><span class="sxs-lookup"><span data-stu-id="aef00-113">The <xref:System.Windows.Forms.Control.MousePosition%2A> returns the screen coordinates of the mouse pointer and is equivalent to the value returned by <xref:System.Windows.Forms.Cursor.Position%2A>.</span></span>  
  
## <a name="converting-between-screen-and-client-coordinates"></a><span data-ttu-id="aef00-114">Ekran ve istemci arasında dönüştürme koordinatları</span><span class="sxs-lookup"><span data-stu-id="aef00-114">Converting Between Screen and Client Coordinates</span></span>  
 <span data-ttu-id="aef00-115">Bazı fare konum bilgileri istemci koordinatlarında ve bazı ekran koordinatları olarak olduğundan, bir noktayı bir koordinat sistemi dönüştürmek gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="aef00-115">Because some mouse location information is in client coordinates and some is in screen coordinates, you may need to convert a point from one coordinate system to the other.</span></span> <span data-ttu-id="aef00-116">Kolayca kullanarak bunu yapabilirsiniz <xref:System.Windows.Forms.Control.PointToClient%2A> ve <xref:System.Windows.Forms.Control.PointToScreen%2A> yöntemleri kullanılabilir <xref:System.Windows.Forms.Control> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="aef00-116">You can do this easily by using the <xref:System.Windows.Forms.Control.PointToClient%2A> and <xref:System.Windows.Forms.Control.PointToScreen%2A> methods available on the <xref:System.Windows.Forms.Control> class.</span></span>  
  
## <a name="standard-click-event-behavior"></a><span data-ttu-id="aef00-117">Standart tıklatma olay davranışı</span><span class="sxs-lookup"><span data-stu-id="aef00-117">Standard Click Event Behavior</span></span>  
 <span data-ttu-id="aef00-118">İşlemek istiyorsanız, fare tıklatma olayları doğru sırayla, hangi tıklatın Windows Forms denetimlerindeki olaylar oluşturulur sipariş bilmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="aef00-118">If you want to handle mouse click events in the proper order, you need to know the order in which click events are raised in Windows Forms controls.</span></span> <span data-ttu-id="aef00-119">Fare düğmesini basılı ve ayrı ayrı denetimler için aşağıdaki listedeki belirtilmedikçe (hangi fare düğmesini bağımsız olarak), yayımlanan tüm Windows Forms denetimleri Yükselt olayların aynı sırayla'yi tıklatın.</span><span class="sxs-lookup"><span data-stu-id="aef00-119">All Windows Forms controls raise click events in the same order when a mouse button is pressed and released (regardless of which mouse button), except where noted in the following list for individual controls.</span></span> <span data-ttu-id="aef00-120">Aşağıdaki liste için tek fare düğmesini tıklatın başlatılan olayları sırasını göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="aef00-120">The following list shows the order of events raised for a single mouse-button click:</span></span>  
  
1.  <span data-ttu-id="aef00-121"><xref:System.Windows.Forms.Control.MouseDown>olay.</span><span class="sxs-lookup"><span data-stu-id="aef00-121"><xref:System.Windows.Forms.Control.MouseDown> event.</span></span>  
  
2.  <span data-ttu-id="aef00-122"><xref:System.Windows.Forms.Control.Click>olay.</span><span class="sxs-lookup"><span data-stu-id="aef00-122"><xref:System.Windows.Forms.Control.Click> event.</span></span>  
  
3.  <span data-ttu-id="aef00-123"><xref:System.Windows.Forms.Control.MouseClick>olay.</span><span class="sxs-lookup"><span data-stu-id="aef00-123"><xref:System.Windows.Forms.Control.MouseClick> event.</span></span>  
  
4.  <span data-ttu-id="aef00-124"><xref:System.Windows.Forms.Control.MouseUp>olay.</span><span class="sxs-lookup"><span data-stu-id="aef00-124"><xref:System.Windows.Forms.Control.MouseUp> event.</span></span>  
  
 <span data-ttu-id="aef00-125">İçin bir çift fare düğmesini tıklatın başlatılan olayları sırasını aşağıdadır:</span><span class="sxs-lookup"><span data-stu-id="aef00-125">Following is the order of events raised for a double mouse-button click:</span></span>  
  
1.  <span data-ttu-id="aef00-126"><xref:System.Windows.Forms.Control.MouseDown>olay.</span><span class="sxs-lookup"><span data-stu-id="aef00-126"><xref:System.Windows.Forms.Control.MouseDown> event.</span></span>  
  
2.  <span data-ttu-id="aef00-127"><xref:System.Windows.Forms.Control.Click>olay.</span><span class="sxs-lookup"><span data-stu-id="aef00-127"><xref:System.Windows.Forms.Control.Click> event.</span></span>  
  
3.  <span data-ttu-id="aef00-128"><xref:System.Windows.Forms.Control.MouseClick>olay.</span><span class="sxs-lookup"><span data-stu-id="aef00-128"><xref:System.Windows.Forms.Control.MouseClick> event.</span></span>  
  
4.  <span data-ttu-id="aef00-129"><xref:System.Windows.Forms.Control.MouseUp>olay.</span><span class="sxs-lookup"><span data-stu-id="aef00-129"><xref:System.Windows.Forms.Control.MouseUp> event.</span></span>  
  
5.  <span data-ttu-id="aef00-130"><xref:System.Windows.Forms.Control.MouseDown>olay.</span><span class="sxs-lookup"><span data-stu-id="aef00-130"><xref:System.Windows.Forms.Control.MouseDown> event.</span></span>  
  
6.  <span data-ttu-id="aef00-131"><xref:System.Windows.Forms.Control.DoubleClick>olay.</span><span class="sxs-lookup"><span data-stu-id="aef00-131"><xref:System.Windows.Forms.Control.DoubleClick> event.</span></span> <span data-ttu-id="aef00-132">(Bu, söz konusu denetim olup bağlı olarak değişebilir <xref:System.Windows.Forms.ControlStyles.StandardDoubleClick> stili biti ayarlanmış `true`.</span><span class="sxs-lookup"><span data-stu-id="aef00-132">(This can vary, depending on whether the control in question has the <xref:System.Windows.Forms.ControlStyles.StandardDoubleClick> style bit set to `true`.</span></span> <span data-ttu-id="aef00-133">Nasıl oluşturulacağı hakkında daha fazla bilgi için bir <xref:System.Windows.Forms.ControlStyles> bit bkz <xref:System.Windows.Forms.Control.SetStyle%2A> yöntemi.)</span><span class="sxs-lookup"><span data-stu-id="aef00-133">For more information about how to set a <xref:System.Windows.Forms.ControlStyles> bit, see the <xref:System.Windows.Forms.Control.SetStyle%2A> method.)</span></span>  
  
7.  <span data-ttu-id="aef00-134"><xref:System.Windows.Forms.Control.MouseDoubleClick>olay.</span><span class="sxs-lookup"><span data-stu-id="aef00-134"><xref:System.Windows.Forms.Control.MouseDoubleClick> event.</span></span>  
  
8.  <span data-ttu-id="aef00-135"><xref:System.Windows.Forms.Control.MouseUp>olay.</span><span class="sxs-lookup"><span data-stu-id="aef00-135"><xref:System.Windows.Forms.Control.MouseUp> event.</span></span>  
  
 <span data-ttu-id="aef00-136">Tıklama fare sırasını gösteren bir kod örneği için olayları, bkz: [nasıl yapılır: Windows Forms denetimlerindeki kullanıcı girdi olaylarını işlemek](../../../docs/framework/winforms/how-to-handle-user-input-events-in-windows-forms-controls.md).</span><span class="sxs-lookup"><span data-stu-id="aef00-136">For a code example that demonstrates the order of the mouse click events, see [How to: Handle User Input Events in Windows Forms Controls](../../../docs/framework/winforms/how-to-handle-user-input-events-in-windows-forms-controls.md).</span></span>  
  
### <a name="individual-controls"></a><span data-ttu-id="aef00-137">Tek denetimleri</span><span class="sxs-lookup"><span data-stu-id="aef00-137">Individual Controls</span></span>  
 <span data-ttu-id="aef00-138">Aşağıdaki denetimleri standart fare uymayan olay davranışını tıklatın:</span><span class="sxs-lookup"><span data-stu-id="aef00-138">The following controls do not conform to the standard mouse click event behavior:</span></span>  
  
-   <span data-ttu-id="aef00-139"><xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.CheckBox>, <xref:System.Windows.Forms.ComboBox>, ve <xref:System.Windows.Forms.RadioButton> denetimleri</span><span class="sxs-lookup"><span data-stu-id="aef00-139"><xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.CheckBox>, <xref:System.Windows.Forms.ComboBox>, and <xref:System.Windows.Forms.RadioButton> controls</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="aef00-140">İçin <xref:System.Windows.Forms.ComboBox> denetim, daha sonra ayrıntılı olay davranış oluşursa düğmesi düzenleme alanı ya da bir öğe listesi içindeki kullanıcı.</span><span class="sxs-lookup"><span data-stu-id="aef00-140">For the <xref:System.Windows.Forms.ComboBox> control, the event behavior detailed later occurs if the user clicks on the edit field, the button, or on an item within the list.</span></span>  
  
    -   <span data-ttu-id="aef00-141">Sol tıklama: <xref:System.Windows.Forms.Control.Click>,<xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="aef00-141">Left click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>  
  
    -   <span data-ttu-id="aef00-142">Sağ tıklayın: hiçbir tıklama olaylarını gerçekleşti</span><span class="sxs-lookup"><span data-stu-id="aef00-142">Right click: No click events raised</span></span>  
  
    -   <span data-ttu-id="aef00-143">Sol çift: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.Click>,<xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="aef00-143">Left double-click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>  
  
    -   <span data-ttu-id="aef00-144">Sağ çift: hiçbir tıklama olaylarını gerçekleşti</span><span class="sxs-lookup"><span data-stu-id="aef00-144">Right double-click: No click events raised</span></span>  
  
-   <span data-ttu-id="aef00-145"><xref:System.Windows.Forms.TextBox>, <xref:System.Windows.Forms.RichTextBox>, <xref:System.Windows.Forms.ListBox>, <xref:System.Windows.Forms.MaskedTextBox>, ve <xref:System.Windows.Forms.CheckedListBox> denetimleri</span><span class="sxs-lookup"><span data-stu-id="aef00-145"><xref:System.Windows.Forms.TextBox>, <xref:System.Windows.Forms.RichTextBox>, <xref:System.Windows.Forms.ListBox>, <xref:System.Windows.Forms.MaskedTextBox>, and <xref:System.Windows.Forms.CheckedListBox> controls</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="aef00-146">Kullanıcı bu denetimleri içinde herhangi bir yere tıklattığında daha sonra ayrıntılı olay davranış oluşur.</span><span class="sxs-lookup"><span data-stu-id="aef00-146">The event behavior detailed later occurs when the user clicks anywhere within these controls.</span></span>  
  
    -   <span data-ttu-id="aef00-147">Sol tıklama: <xref:System.Windows.Forms.Control.Click>,<xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="aef00-147">Left click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>  
  
    -   <span data-ttu-id="aef00-148">Sağ tıklayın: hiçbir tıklama olaylarını gerçekleşti</span><span class="sxs-lookup"><span data-stu-id="aef00-148">Right click: No click events raised</span></span>  
  
    -   <span data-ttu-id="aef00-149">Sol çift: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>, <xref:System.Windows.Forms.Control.DoubleClick>,<xref:System.Windows.Forms.Control.MouseDoubleClick></span><span class="sxs-lookup"><span data-stu-id="aef00-149">Left double-click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>, <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span></span>  
  
    -   <span data-ttu-id="aef00-150">Sağ çift: hiçbir tıklama olaylarını gerçekleşti</span><span class="sxs-lookup"><span data-stu-id="aef00-150">Right double-click: No click events raised</span></span>  
  
-   <span data-ttu-id="aef00-151"><xref:System.Windows.Forms.ListView>denetimi</span><span class="sxs-lookup"><span data-stu-id="aef00-151"><xref:System.Windows.Forms.ListView> control</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="aef00-152">Daha sonra ayrıntılı olay yalnızca kullanıcı öğelerde tıkladığında davranış <xref:System.Windows.Forms.ListView> denetim.</span><span class="sxs-lookup"><span data-stu-id="aef00-152">The event behavior detailed later occurs only when the user clicks on the items in the <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="aef00-153">Hiçbir olaylar tıklama denetimi başka bir yerde için oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="aef00-153">No events are raised for clicks anywhere else on the control.</span></span> <span data-ttu-id="aef00-154">Daha sonra açıklanan olaylar ek olarak, var olan <xref:System.Windows.Forms.ListView.BeforeLabelEdit> ve <xref:System.Windows.Forms.ListView.AfterLabelEdit> doğrulama ile kullanmak istiyorsanız, size ilgilendirebilecek olayları <xref:System.Windows.Forms.ListView> denetim.</span><span class="sxs-lookup"><span data-stu-id="aef00-154">In addition to the events described later, there are the <xref:System.Windows.Forms.ListView.BeforeLabelEdit> and <xref:System.Windows.Forms.ListView.AfterLabelEdit> events, which may be of interest to you if you want to use validation with the <xref:System.Windows.Forms.ListView> control.</span></span>  
  
    -   <span data-ttu-id="aef00-155">Sol tıklama: <xref:System.Windows.Forms.Control.Click>,<xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="aef00-155">Left click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>  
  
    -   <span data-ttu-id="aef00-156">Sağ tıklayın: <xref:System.Windows.Forms.Control.Click>,<xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="aef00-156">Right click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>  
  
    -   <span data-ttu-id="aef00-157">Sol çift: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>,<xref:System.Windows.Forms.Control.MouseDoubleClick></span><span class="sxs-lookup"><span data-stu-id="aef00-157">Left double-click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span></span>  
  
    -   <span data-ttu-id="aef00-158">Sağ çift: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>,<xref:System.Windows.Forms.Control.MouseDoubleClick></span><span class="sxs-lookup"><span data-stu-id="aef00-158">Right double-click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span></span>  
  
-   <span data-ttu-id="aef00-159"><xref:System.Windows.Forms.TreeView>denetimi</span><span class="sxs-lookup"><span data-stu-id="aef00-159"><xref:System.Windows.Forms.TreeView> control</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="aef00-160">Daha sonra ayrıntılı olay yalnızca kullanıcı öğeleri kendilerini veya öğeleri sağındaki tıkladığında davranış <xref:System.Windows.Forms.TreeView> denetim.</span><span class="sxs-lookup"><span data-stu-id="aef00-160">The event behavior detailed later occurs only when the user clicks on the items themselves or to the right of the items in the <xref:System.Windows.Forms.TreeView> control.</span></span> <span data-ttu-id="aef00-161">Hiçbir olaylar tıklama denetimi başka bir yerde için oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="aef00-161">No events are raised for clicks anywhere else on the control.</span></span> <span data-ttu-id="aef00-162">Bu ek olarak daha sonra açıklanan, vardır <xref:System.Windows.Forms.TreeView.BeforeCheck>, <xref:System.Windows.Forms.TreeView.BeforeSelect>, <xref:System.Windows.Forms.TreeView.BeforeLabelEdit>, <xref:System.Windows.Forms.TreeView.AfterSelect>, <xref:System.Windows.Forms.TreeView.AfterCheck>, ve <xref:System.Windows.Forms.TreeView.AfterLabelEdit> doğrulama ile kullanmak istiyorsanız, size ilgilendirebilecek olayları <xref:System.Windows.Forms.TreeView> denetimi .</span><span class="sxs-lookup"><span data-stu-id="aef00-162">In addition to those described later, there are the <xref:System.Windows.Forms.TreeView.BeforeCheck>, <xref:System.Windows.Forms.TreeView.BeforeSelect>, <xref:System.Windows.Forms.TreeView.BeforeLabelEdit>, <xref:System.Windows.Forms.TreeView.AfterSelect>, <xref:System.Windows.Forms.TreeView.AfterCheck>, and <xref:System.Windows.Forms.TreeView.AfterLabelEdit> events, which may be of interest to you if you want to use validation with the <xref:System.Windows.Forms.TreeView> control.</span></span>  
  
    -   <span data-ttu-id="aef00-163">Sol tıklama: <xref:System.Windows.Forms.Control.Click>,<xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="aef00-163">Left click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>  
  
    -   <span data-ttu-id="aef00-164">Sağ tıklayın: <xref:System.Windows.Forms.Control.Click>,<xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="aef00-164">Right click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>  
  
    -   <span data-ttu-id="aef00-165">Sol çift: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>,<xref:System.Windows.Forms.Control.MouseDoubleClick></span><span class="sxs-lookup"><span data-stu-id="aef00-165">Left double-click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span></span>  
  
    -   <span data-ttu-id="aef00-166">Sağ çift: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>,<xref:System.Windows.Forms.Control.MouseDoubleClick></span><span class="sxs-lookup"><span data-stu-id="aef00-166">Right double-click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span></span>  
  
### <a name="painting-behavior-of-toggle-controls"></a><span data-ttu-id="aef00-167">İki durumlu denetimleri davranışını boyama</span><span class="sxs-lookup"><span data-stu-id="aef00-167">Painting Behavior of Toggle Controls</span></span>  
 <span data-ttu-id="aef00-168">Geçiş denetimleri türetme denetimleri gibi <xref:System.Windows.Forms.ButtonBase> sınıfı, tıklama olayları aşağıdaki ayırıcı boyama davranış fare birlikte sahiptir:</span><span class="sxs-lookup"><span data-stu-id="aef00-168">Toggle controls, such as the controls deriving from the <xref:System.Windows.Forms.ButtonBase> class, have the following distinctive painting behavior in combination with mouse click events:</span></span>  
  
1.  <span data-ttu-id="aef00-169">Kullanıcının fare düğmesini basar.</span><span class="sxs-lookup"><span data-stu-id="aef00-169">The user presses the mouse button.</span></span>  
  
2.  <span data-ttu-id="aef00-170">Denetim basılı durumda boyar.</span><span class="sxs-lookup"><span data-stu-id="aef00-170">The control paints in the pressed state.</span></span>  
  
3.  <span data-ttu-id="aef00-171"><xref:System.Windows.Forms.Control.MouseDown> Olayı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="aef00-171">The <xref:System.Windows.Forms.Control.MouseDown> event is raised.</span></span>  
  
4.  <span data-ttu-id="aef00-172">Kullanıcının fare düğmesini serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="aef00-172">The user releases the mouse button.</span></span>  
  
5.  <span data-ttu-id="aef00-173">Denetim gerçekleştiği durumda boyar.</span><span class="sxs-lookup"><span data-stu-id="aef00-173">The control paints in the raised state.</span></span>  
  
6.  <span data-ttu-id="aef00-174"><xref:System.Windows.Forms.Control.Click> Olayı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="aef00-174">The <xref:System.Windows.Forms.Control.Click> event is raised.</span></span>  
  
7.  <span data-ttu-id="aef00-175"><xref:System.Windows.Forms.Control.MouseClick> Olayı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="aef00-175">The <xref:System.Windows.Forms.Control.MouseClick> event is raised.</span></span>  
  
8.  <span data-ttu-id="aef00-176"><xref:System.Windows.Forms.Control.MouseUp> Olayı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="aef00-176">The <xref:System.Windows.Forms.Control.MouseUp> event is raised.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="aef00-177">Kullanıcının fare düğmesini basılı olsa işaretçiyi iki durumlu düğme denetim dışında taşınırsa (fareyi hareket gibi <xref:System.Windows.Forms.Button> , basıldığında kontrol), iki durumlu düğme denetim gerçekleştiği yer boyamak durum ve yalnızca <xref:System.Windows.Forms.Control.MouseUp> olayı oluşur.</span><span class="sxs-lookup"><span data-stu-id="aef00-177">If the user moves the pointer out of the toggle control while the mouse button is down (such as moving the mouse off the <xref:System.Windows.Forms.Button> control while it is pressed), the toggle control will paint in the raised state and only the <xref:System.Windows.Forms.Control.MouseUp> event occurs.</span></span> <span data-ttu-id="aef00-178"><xref:System.Windows.Forms.Control.Click> Veya <xref:System.Windows.Forms.Control.MouseClick> olayları, bu durumda gerçekleşmez.</span><span class="sxs-lookup"><span data-stu-id="aef00-178">The <xref:System.Windows.Forms.Control.Click> or <xref:System.Windows.Forms.Control.MouseClick> events will not occur in this situation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aef00-179">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="aef00-179">See Also</span></span>  
 [<span data-ttu-id="aef00-180">Forms bir Windows uygulamasında fare girdisi</span><span class="sxs-lookup"><span data-stu-id="aef00-180">Mouse Input in a Windows Forms Application</span></span>](../../../docs/framework/winforms/mouse-input-in-a-windows-forms-application.md)
