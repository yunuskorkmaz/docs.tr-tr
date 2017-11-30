---
title: "İzlenecek yol: Kullanıcı Denetiminde Sürükleme ve Bırakmayı Etkinleştirme"
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
helpviewer_keywords:
- walkthrough [WPF], drag-and-drop
- drag-and-drop [WPF], walkthrough
ms.assetid: cc844419-1a77-4906-95d9-060d79107fc7
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 360b453b2a25b6822485f18cc81cb43e313949eb
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="walkthrough-enabling-drag-and-drop-on-a-user-control"></a><span data-ttu-id="95d77-102">İzlenecek yol: Kullanıcı Denetiminde Sürükleme ve Bırakmayı Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="95d77-102">Walkthrough: Enabling Drag and Drop on a User Control</span></span>
<span data-ttu-id="95d77-103">Bu anlatımda sürükle ve bırak veri aktarımı katılabilmesi için özel bir kullanıcı denetimi oluşturmak nasıl gösterilir [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="95d77-103">This walkthrough demonstrates how to create a custom user control that can participate in drag-and-drop data transfer in [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].</span></span>  
  
 <span data-ttu-id="95d77-104">Bu kılavuzda, özel bir WPF oluşturacak <xref:System.Windows.Controls.UserControl> temsil eden bir daire şekli.</span><span class="sxs-lookup"><span data-stu-id="95d77-104">In this walkthrough, you will create a custom WPF <xref:System.Windows.Controls.UserControl> that represents a circle shape.</span></span> <span data-ttu-id="95d77-105">Veri Aktarımı Sürükle ve bırak aracılığıyla etkinleştirmek için denetimindeki işlevselliği gerçekleştireceksiniz.</span><span class="sxs-lookup"><span data-stu-id="95d77-105">You will implement functionality on the control to enable data transfer through drag-and-drop.</span></span> <span data-ttu-id="95d77-106">Örneğin, başka bir daire denetimden sürüklediğinizde, dolgu rengi veri daire kaynaktan hedefe kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="95d77-106">For example, if you drag from one Circle control to another, the Fill color data is copied from the source Circle to the target.</span></span> <span data-ttu-id="95d77-107">Bir daire kontrolü sürüklediğinizde bir <xref:System.Windows.Controls.TextBox>, dolgu rengi dize gösterimini kopyalanır <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="95d77-107">If you drag from a Circle control to a <xref:System.Windows.Controls.TextBox>, the string representation of the Fill color is copied to the <xref:System.Windows.Controls.TextBox>.</span></span> <span data-ttu-id="95d77-108">Ayrıca iki panel denetimleri içeren küçük bir uygulama oluşturulur ve bir <xref:System.Windows.Controls.TextBox> sürükle ve bırak işlevselliğini test etmek için.</span><span class="sxs-lookup"><span data-stu-id="95d77-108">You will also create a small application that contains two panel controls and a <xref:System.Windows.Controls.TextBox> to test the drag-and-drop functionality.</span></span> <span data-ttu-id="95d77-109">Taşıma veya daireler bir panelinin alt koleksiyondan kopyalama sağlayacak bırakılan daire verileri işlemek paneller etkinleştirir kod yazacaksınız.</span><span class="sxs-lookup"><span data-stu-id="95d77-109">You will write code that enables the panels to process dropped Circle data, which will enable you to move or copy Circles from the Children collection of one panel to the other.</span></span>  
  
 <span data-ttu-id="95d77-110">Bu izlenecek yol aşağıdaki görevleri gösterir:</span><span class="sxs-lookup"><span data-stu-id="95d77-110">This walkthrough illustrates the following tasks:</span></span>  
  
-   <span data-ttu-id="95d77-111">Özel bir kullanıcı denetimi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="95d77-111">Create a custom user control.</span></span>  
  
-   <span data-ttu-id="95d77-112">Sürükleme kaynağı olması kullanıcı denetimini etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="95d77-112">Enable the user control to be a drag source.</span></span>  
  
-   <span data-ttu-id="95d77-113">Bırakma hedefi kullanıcı denetimini etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="95d77-113">Enable the user control to be a drop target.</span></span>  
  
-   <span data-ttu-id="95d77-114">Kullanıcı denetiminden bırakılan veri almak bir panel etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="95d77-114">Enable a panel to receive data dropped from the user control.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="95d77-115">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="95d77-115">Prerequisites</span></span>  
 <span data-ttu-id="95d77-116">Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:</span><span class="sxs-lookup"><span data-stu-id="95d77-116">You need the following components to complete this walkthrough:</span></span>  
  
-   <span data-ttu-id="95d77-117">Visual Studio 2010</span><span class="sxs-lookup"><span data-stu-id="95d77-117">Visual Studio 2010</span></span>  
  
## <a name="creating-the-application-project"></a><span data-ttu-id="95d77-118">Uygulama projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="95d77-118">Creating the Application Project</span></span>  
 <span data-ttu-id="95d77-119">Bu bölümde, bir ana sayfa ile iki bölme içerir uygulama altyapısı oluşturacak ve bir <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="95d77-119">In this section, you will create the application infrastructure, which includes a main page with two panels and a <xref:System.Windows.Controls.TextBox>.</span></span>  
  
### <a name="to-create-the-project"></a><span data-ttu-id="95d77-120">Proje oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="95d77-120">To create the project</span></span>  
  
1.  <span data-ttu-id="95d77-121">Visual Basic veya Visual C# adlı yeni bir WPF uygulaması projesi oluşturduğunuzda `DragDropExample`.</span><span class="sxs-lookup"><span data-stu-id="95d77-121">Create a new WPF Application project in Visual Basic or Visual C# named `DragDropExample`.</span></span> <span data-ttu-id="95d77-122">Daha fazla bilgi için bkz: [nasıl yapılır: yeni bir WPF uygulaması projesi oluşturduğunuzda](http://msdn.microsoft.com/en-us/1f6aea7a-33e1-4d3f-8555-1daa42e95d82).</span><span class="sxs-lookup"><span data-stu-id="95d77-122">For more information, see [How to: Create a New WPF Application Project](http://msdn.microsoft.com/en-us/1f6aea7a-33e1-4d3f-8555-1daa42e95d82).</span></span>  
  
2.  <span data-ttu-id="95d77-123">MainWindow.xaml açın.</span><span class="sxs-lookup"><span data-stu-id="95d77-123">Open MainWindow.xaml.</span></span>  
  
3.  <span data-ttu-id="95d77-124">Açma ve kapatma arasında aşağıdaki biçimlendirmeleri eklemek <xref:System.Windows.Controls.Grid> etiketler.</span><span class="sxs-lookup"><span data-stu-id="95d77-124">Add the following markup between the opening and closing <xref:System.Windows.Controls.Grid> tags.</span></span>  
  
     <span data-ttu-id="95d77-125">Bu biçimlendirme test uygulaması için kullanıcı arabirimi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="95d77-125">This markup creates the user interface for the test application.</span></span>  
  
     [!code-xaml[DragDropWalkthrough#PanelsStep1XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#panelsstep1xaml)]  
  
## <a name="adding-a-new-user-control-to-the-project"></a><span data-ttu-id="95d77-126">Projeye yeni bir kullanıcı denetimi ekleme</span><span class="sxs-lookup"><span data-stu-id="95d77-126">Adding a New User Control to the Project</span></span>  
 <span data-ttu-id="95d77-127">Bu bölümde, projeye yeni bir kullanıcı denetimi ekleyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="95d77-127">In this section, you will add a new user control to the project.</span></span>  
  
### <a name="to-add-a-new-user-control"></a><span data-ttu-id="95d77-128">Yeni bir kullanıcı denetimi eklemek için</span><span class="sxs-lookup"><span data-stu-id="95d77-128">To add a new user control</span></span>  
  
1.  <span data-ttu-id="95d77-129">Proje menüsünde seçin **kullanıcı denetimi Ekle**.</span><span class="sxs-lookup"><span data-stu-id="95d77-129">On the Project menu, select **Add User Control**.</span></span>  
  
2.  <span data-ttu-id="95d77-130">Yeni Öğe Ekle iletişim kutusunda adına değiştirin `Circle.xaml`, tıklatıp **Ekle**.</span><span class="sxs-lookup"><span data-stu-id="95d77-130">In the Add New Item dialog box, change the name to `Circle.xaml`, and click **Add**.</span></span>  
  
     <span data-ttu-id="95d77-131">Circle.XAML ve kendi arka plan kodu projeye eklendi.</span><span class="sxs-lookup"><span data-stu-id="95d77-131">Circle.xaml and its code-behind is added to the project.</span></span>  
  
3.  <span data-ttu-id="95d77-132">Circle.xaml açın.</span><span class="sxs-lookup"><span data-stu-id="95d77-132">Open Circle.xaml.</span></span>  
  
     <span data-ttu-id="95d77-133">Bu dosya kullanıcı denetiminin kullanıcı arabirimi öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="95d77-133">This file will contain the user interface elements of the user control.</span></span>  
  
4.  <span data-ttu-id="95d77-134">Aşağıdaki biçimlendirmede kök dizinine ekleme <xref:System.Windows.Controls.Grid> mavi bir daire olarak kullanıcı Arabiriminde sahip basit kullanıcı denetimi oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="95d77-134">Add the following markup to the root <xref:System.Windows.Controls.Grid> to create a simple user control that has a blue circle as its UI.</span></span>  
  
     [!code-xaml[DragDropWalkthrough#EllipseXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml#ellipsexaml)]  
  
5.  <span data-ttu-id="95d77-135">Circle.xaml.cs veya Circle.xaml.vb açın.</span><span class="sxs-lookup"><span data-stu-id="95d77-135">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>  
  
6.  <span data-ttu-id="95d77-136">C# ' ta kopya Oluşturucu oluşturmak için varsayılan oluşturucu sonra aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="95d77-136">In C#, add the following code after the default constructor to create a copy constructor.</span></span> <span data-ttu-id="95d77-137">Visual Basic'te, varsayılan bir oluşturucu ve kopya Oluşturucu oluşturmak için aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="95d77-137">In Visual Basic, add the following code to create both a default constructor and a copy constructor.</span></span>  
  
     <span data-ttu-id="95d77-138">Kopyalanacak kullanıcı denetimi izin vermek üzere bir kopya Oluşturucu yöntemi arka plan kod dosyasına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="95d77-138">In order to allow the user control to be copied, you add a copy constructor method in the code-behind file.</span></span> <span data-ttu-id="95d77-139">Basitleştirilmiş daire kullanıcı denetiminde, yalnızca dolgu ve boyutunu kopyalayacak kullanıcı denetiminin.</span><span class="sxs-lookup"><span data-stu-id="95d77-139">In the simplified Circle user control, you will only copy the Fill and the size of the of the user control.</span></span>  
  
     [!code-csharp[DragDropWalkthrough#CopyCtor](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#copyctor)]
     [!code-vb[DragDropWalkthrough#CopyCtor](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#copyctor)]  
  
### <a name="to-add-the-user-control-to-the-main-window"></a><span data-ttu-id="95d77-140">Kullanıcı Denetimi ana pencereyi eklemek için</span><span class="sxs-lookup"><span data-stu-id="95d77-140">To add the user control to the main window</span></span>  
  
1.  <span data-ttu-id="95d77-141">MainWindow.xaml açın.</span><span class="sxs-lookup"><span data-stu-id="95d77-141">Open MainWindow.xaml.</span></span>  
  
2.  <span data-ttu-id="95d77-142">Aşağıdaki XAML eklemek için açılış <xref:System.Windows.Window> bir XML ad alanı başvurusu geçerli uygulama oluşturmak için etiketi.</span><span class="sxs-lookup"><span data-stu-id="95d77-142">Add the following XAML to the opening <xref:System.Windows.Window> tag to create an XML namespace reference to the current application.</span></span>  
  
    ```  
    xmlns:local="clr-namespace:DragDropExample"  
    ```  
  
3.  <span data-ttu-id="95d77-143">İlk <xref:System.Windows.Controls.StackPanel>, ilk panelinde daire kullanıcı denetimi iki örneğini oluşturmak için aşağıdaki XAML'i ekleyin.</span><span class="sxs-lookup"><span data-stu-id="95d77-143">In the first <xref:System.Windows.Controls.StackPanel>, add the following XAML to create two instances of the Circle user control in the first panel.</span></span>  
  
     [!code-xaml[DragDropWalkthrough#CirclesXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#circlesxaml)]  
  
     <span data-ttu-id="95d77-144">Pano için tam XAML aşağıdaki gibi görünür.</span><span class="sxs-lookup"><span data-stu-id="95d77-144">The full XAML for the panel looks like the following.</span></span>  
  
     [!code-xaml[DragDropWalkthrough#PanelsStep2XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#panelsstep2xaml)]  
  
## <a name="implementing-drag-source-events-in-the-user-control"></a><span data-ttu-id="95d77-145">Kullanıcı denetimi sürükleme kaynağı olayları uygulama</span><span class="sxs-lookup"><span data-stu-id="95d77-145">Implementing Drag Source Events in the User Control</span></span>  
 <span data-ttu-id="95d77-146">Bu bölümde, geçersiz kılar <xref:System.Windows.UIElement.OnMouseMove%2A> yöntemi ve başlatma sürükle ve bırak işlemi.</span><span class="sxs-lookup"><span data-stu-id="95d77-146">In this section, you will override the <xref:System.Windows.UIElement.OnMouseMove%2A> method and initiate the drag-and-drop operation.</span></span>  
  
 <span data-ttu-id="95d77-147">Bir Sürükle başladıysanız (fare düğmesini basılı ve fare taşınır), verilerin içine aktarılması için paket oluşturur bir <xref:System.Windows.DataObject>.</span><span class="sxs-lookup"><span data-stu-id="95d77-147">If a drag is started (a mouse button is pressed and the mouse is moved), you will package the data to be transferred into a <xref:System.Windows.DataObject>.</span></span> <span data-ttu-id="95d77-148">Bu durumda, daire denetim üç veri öğeleri paket oluşturur; Dolgu rengini, gerekse boyu çift gösterimini ve kendisi bir kopyasını bir dize gösterimi.</span><span class="sxs-lookup"><span data-stu-id="95d77-148">In this case, the Circle control will package three data items; a string representation of its Fill color, a double representation of its height, and a copy of itself.</span></span>  
  
### <a name="to-initiate-a-drag-and-drop-operation"></a><span data-ttu-id="95d77-149">Sürükle ve bırak işlemi başlatmak için</span><span class="sxs-lookup"><span data-stu-id="95d77-149">To initiate a drag-and-drop operation</span></span>  
  
1.  <span data-ttu-id="95d77-150">Circle.xaml.cs veya Circle.xaml.vb açın.</span><span class="sxs-lookup"><span data-stu-id="95d77-150">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>  
  
2.  <span data-ttu-id="95d77-151">Aşağıdakileri ekleyin <xref:System.Windows.UIElement.OnMouseMove%2A> sınıfı için işleme sağlamak üzere geçersiz kılma <xref:System.Windows.UIElement.MouseMove> olay.</span><span class="sxs-lookup"><span data-stu-id="95d77-151">Add the following <xref:System.Windows.UIElement.OnMouseMove%2A> override to provide class handling for the <xref:System.Windows.UIElement.MouseMove> event.</span></span>  
  
     [!code-csharp[DragDropWalkthrough#OnMouseMove](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#onmousemove)]
     [!code-vb[DragDropWalkthrough#OnMouseMove](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#onmousemove)]  
  
     <span data-ttu-id="95d77-152">Bu <xref:System.Windows.UIElement.OnMouseMove%2A> geçersiz kılma aşağıdaki görevleri gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="95d77-152">This <xref:System.Windows.UIElement.OnMouseMove%2A> override performs the following tasks:</span></span>  
  
    -   <span data-ttu-id="95d77-153">Fareyi hareket ederken sol fare düğmesini basılı olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="95d77-153">Checks whether the left mouse button is pressed while the mouse is moving.</span></span>  
  
    -   <span data-ttu-id="95d77-154">Daire verileri paketleri bir <xref:System.Windows.DataObject>.</span><span class="sxs-lookup"><span data-stu-id="95d77-154">Packages the Circle data into a <xref:System.Windows.DataObject>.</span></span> <span data-ttu-id="95d77-155">Bu durumda, üç veri öğeleri daire denetim paketleri; Dolgu rengini, gerekse boyu çift gösterimini ve kendisi bir kopyasını bir dize gösterimi.</span><span class="sxs-lookup"><span data-stu-id="95d77-155">In this case, the Circle control packages three data items; a string representation of its Fill color, a double representation of its height, and a copy of itself.</span></span>  
  
    -   <span data-ttu-id="95d77-156">Statik çağırır <xref:System.Windows.DragDrop.DoDragDrop%2A?displayProperty=nameWithType> sürükle ve bırak işlemi başlatmak için yöntem.</span><span class="sxs-lookup"><span data-stu-id="95d77-156">Calls the static <xref:System.Windows.DragDrop.DoDragDrop%2A?displayProperty=nameWithType> method to initiate the drag-and-drop operation.</span></span> <span data-ttu-id="95d77-157">Aşağıdaki üç parametre geçirdiğiniz <xref:System.Windows.DragDrop.DoDragDrop%2A> yöntemi:</span><span class="sxs-lookup"><span data-stu-id="95d77-157">You pass the following three parameters to the <xref:System.Windows.DragDrop.DoDragDrop%2A> method:</span></span>  
  
        -   <span data-ttu-id="95d77-158">`dragSource`– Bu denetimi bir başvuru.</span><span class="sxs-lookup"><span data-stu-id="95d77-158">`dragSource` – A reference to this control.</span></span>  
  
        -   <span data-ttu-id="95d77-159">`data`– <xref:System.Windows.DataObject> Önceki kodda oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="95d77-159">`data` – The <xref:System.Windows.DataObject> created in the previous code.</span></span>  
  
        -   <span data-ttu-id="95d77-160">`allowedEffects`– Olan izin verilen sürükle ve bırak işlemleri <xref:System.Windows.DragDropEffects.Copy> veya <xref:System.Windows.DragDropEffects.Move>.</span><span class="sxs-lookup"><span data-stu-id="95d77-160">`allowedEffects` – The allowed drag-and-drop operations, which are <xref:System.Windows.DragDropEffects.Copy> or <xref:System.Windows.DragDropEffects.Move>.</span></span>  
  
3.  <span data-ttu-id="95d77-161">Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="95d77-161">Press F5 to build and run the application.</span></span>  
  
4.  <span data-ttu-id="95d77-162">Daire denetimleri birini tıklatın ve başka bir daire paneller sürükleyin ve <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="95d77-162">Click one of the Circle controls and drag it over the panels, the other Circle, and the <xref:System.Windows.Controls.TextBox>.</span></span> <span data-ttu-id="95d77-163">Üzerinden sürüklendiğinde <xref:System.Windows.Controls.TextBox>, bir taşıma belirtmek için imleç değişir.</span><span class="sxs-lookup"><span data-stu-id="95d77-163">When dragging over the <xref:System.Windows.Controls.TextBox>, the cursor changes to indicate a move.</span></span>  
  
5.  <span data-ttu-id="95d77-164">Üzerinden bir daire sürükleme sırasında <xref:System.Windows.Controls.TextBox>, CTRL tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="95d77-164">While dragging a Circle over the <xref:System.Windows.Controls.TextBox>, press the CTRL key.</span></span> <span data-ttu-id="95d77-165">Nasıl bir kopyasını belirtmek için imleci değiştiğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="95d77-165">Notice how the cursor changes to indicate a copy.</span></span>  
  
6.  <span data-ttu-id="95d77-166">Sürükleme ve bırakma üzerine bir daire <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="95d77-166">Drag and drop a Circle onto the <xref:System.Windows.Controls.TextBox>.</span></span> <span data-ttu-id="95d77-167">Dairenin dolgu rengi dize gösterimini eklenir <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="95d77-167">The string representation of the Circle’s fill color is appended to the <xref:System.Windows.Controls.TextBox>.</span></span>  
  
     <span data-ttu-id="95d77-168">![Dize olarak dairenin dolgu rengi gösterimi](../../../../docs/framework/wpf/advanced/media/dragdrop-colorstring.png "DragDrop_ColorString")</span><span class="sxs-lookup"><span data-stu-id="95d77-168">![String representation of Circle's fill color](../../../../docs/framework/wpf/advanced/media/dragdrop-colorstring.png "DragDrop_ColorString")</span></span>  
  
 <span data-ttu-id="95d77-169">Varsayılan olarak, imleç veri bırakma hangi etkisi olmayacaktır belirtmek için bir Sürükle ve bırak işlemi sırasında değiştirir.</span><span class="sxs-lookup"><span data-stu-id="95d77-169">By default, the cursor will change during a drag-and-drop operation to indicate what effect dropping the data will have.</span></span> <span data-ttu-id="95d77-170">İşleyerek kullanıcıya verilen görüşü özelleştirebilirsiniz <xref:System.Windows.UIElement.GiveFeedback> olay ve farklı bir imleç ayarlama.</span><span class="sxs-lookup"><span data-stu-id="95d77-170">You can customize the feedback given to the user by handling the <xref:System.Windows.UIElement.GiveFeedback> event and setting a different cursor.</span></span>  
  
### <a name="to-give-feedback-to-the-user"></a><span data-ttu-id="95d77-171">Kullanıcıya geribildirim vermek için</span><span class="sxs-lookup"><span data-stu-id="95d77-171">To give feedback to the user</span></span>  
  
1.  <span data-ttu-id="95d77-172">Circle.xaml.cs veya Circle.xaml.vb açın.</span><span class="sxs-lookup"><span data-stu-id="95d77-172">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>  
  
2.  <span data-ttu-id="95d77-173">Aşağıdakileri ekleyin <xref:System.Windows.UIElement.OnGiveFeedback%2A> sınıfı için işleme sağlamak üzere geçersiz kılma <xref:System.Windows.UIElement.GiveFeedback> olay.</span><span class="sxs-lookup"><span data-stu-id="95d77-173">Add the following <xref:System.Windows.UIElement.OnGiveFeedback%2A> override to provide class handling for the <xref:System.Windows.UIElement.GiveFeedback> event.</span></span>  
  
     [!code-csharp[DragDropWalkthrough#OnGiveFeedback](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ongivefeedback)]
     [!code-vb[DragDropWalkthrough#OnGiveFeedback](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ongivefeedback)]  
  
     <span data-ttu-id="95d77-174">Bu <xref:System.Windows.UIElement.OnGiveFeedback%2A> geçersiz kılma aşağıdaki görevleri gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="95d77-174">This <xref:System.Windows.UIElement.OnGiveFeedback%2A> override performs the following tasks:</span></span>  
  
    -   <span data-ttu-id="95d77-175">Denetler <xref:System.Windows.GiveFeedbackEventArgs.Effects%2A> açılan hedef ayarlanan değerlerle <xref:System.Windows.UIElement.DragOver> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="95d77-175">Checks the <xref:System.Windows.GiveFeedbackEventArgs.Effects%2A> values that are set in the drop target's <xref:System.Windows.UIElement.DragOver> event handler.</span></span>  
  
    -   <span data-ttu-id="95d77-176">Dayalı özel bir imleç ayarlar <xref:System.Windows.GiveFeedbackEventArgs.Effects%2A> değeri.</span><span class="sxs-lookup"><span data-stu-id="95d77-176">Sets a custom cursor based on the <xref:System.Windows.GiveFeedbackEventArgs.Effects%2A> value.</span></span> <span data-ttu-id="95d77-177">İmleç veri bırakma hangi etkisi hakkında kullanıcıya görsel geribildirim sağlamak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="95d77-177">The cursor is intended to give visual feedback to the user about what effect dropping the data will have.</span></span>  
  
3.  <span data-ttu-id="95d77-178">Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="95d77-178">Press F5 to build and run the application.</span></span>  
  
4.  <span data-ttu-id="95d77-179">Daireye birini denetimleri diğer daireye paneller sürükleyin ve <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="95d77-179">Drag one of the Circle controls over the panels, the other Circle, and the <xref:System.Windows.Controls.TextBox>.</span></span> <span data-ttu-id="95d77-180">İmleçler şimdi belirttiğiniz özel imleçler olduğunu fark <xref:System.Windows.UIElement.OnGiveFeedback%2A> geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="95d77-180">Notice that the cursors are now the custom cursors that you specified in the <xref:System.Windows.UIElement.OnGiveFeedback%2A> override.</span></span>  
  
     <span data-ttu-id="95d77-181">![Sürükleme ve bırakma özel imleçlerle](../../../../docs/framework/wpf/advanced/media/dragdrop-customcursor.png "DragDrop_CustomCursor")</span><span class="sxs-lookup"><span data-stu-id="95d77-181">![Drag and drop with custom cursors](../../../../docs/framework/wpf/advanced/media/dragdrop-customcursor.png "DragDrop_CustomCursor")</span></span>  
  
5.  <span data-ttu-id="95d77-182">Metni seçin `green` gelen <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="95d77-182">Select the text `green` from the <xref:System.Windows.Controls.TextBox>.</span></span>  
  
6.  <span data-ttu-id="95d77-183">Sürükleme `green` bir daire denetime metin.</span><span class="sxs-lookup"><span data-stu-id="95d77-183">Drag the `green` text to a Circle control.</span></span> <span data-ttu-id="95d77-184">Sürükle ve bırak işlemi etkilerini göstermek için varsayılan imleçler gösterilen dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="95d77-184">Notice that the default cursors are shown to indicate the effects of the drag-and-drop operation.</span></span> <span data-ttu-id="95d77-185">Geri bildirim imleci her zaman Sürükle kaynağı tarafından ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="95d77-185">The feedback cursor is always set by the drag source.</span></span>  
  
## <a name="implementing-drop-target-events-in-the-user-control"></a><span data-ttu-id="95d77-186">Bırakma hedefi olayları, kullanıcı denetimi uygulama</span><span class="sxs-lookup"><span data-stu-id="95d77-186">Implementing Drop Target Events in the User Control</span></span>  
 <span data-ttu-id="95d77-187">Bu bölümde, kullanıcı denetimi kullanıcı sağlayan yöntemler bir bırakma hedefi olarak denetlemek ve üzerinde bırakılan veri işleme geçersiz kılma bir bırakma hedefi olduğunu belirteceksiniz.</span><span class="sxs-lookup"><span data-stu-id="95d77-187">In this section, you will specify that the user control is a drop target, override the methods that enable the user control to be a drop target, and process the data that is dropped on it.</span></span>  
  
### <a name="to-enable-the-user-control-to-be-a-drop-target"></a><span data-ttu-id="95d77-188">Bırakma hedefi kullanıcı denetimini etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="95d77-188">To enable the user control to be a drop target</span></span>  
  
1.  <span data-ttu-id="95d77-189">Circle.xaml açın.</span><span class="sxs-lookup"><span data-stu-id="95d77-189">Open Circle.xaml.</span></span>  
  
2.  <span data-ttu-id="95d77-190">Açılışında <xref:System.Windows.Controls.UserControl> etiketi, add <xref:System.Windows.UIElement.AllowDrop%2A> özelliği ve ayarlamak `true`.</span><span class="sxs-lookup"><span data-stu-id="95d77-190">In the opening <xref:System.Windows.Controls.UserControl> tag, add the <xref:System.Windows.UIElement.AllowDrop%2A> property and set it to `true`.</span></span>  
  
     [!code-xaml[DragDropWalkthrough#UCTagXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml#uctagxaml)]  
  
 <span data-ttu-id="95d77-191"><xref:System.Windows.UIElement.OnDrop%2A> Yöntemi çağrılır <xref:System.Windows.UIElement.AllowDrop%2A> özelliği ayarlanmış `true` ve veriler sürükleme kaynağından daire kullanıcı denetiminde bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="95d77-191">The <xref:System.Windows.UIElement.OnDrop%2A> method is called when the <xref:System.Windows.UIElement.AllowDrop%2A> property is set to `true` and data from the drag source is dropped on the Circle user control.</span></span> <span data-ttu-id="95d77-192">Bu yöntemde bırakılmış verileri işlemek ve dairenin veri uygulayın.</span><span class="sxs-lookup"><span data-stu-id="95d77-192">In this method, you will process the data that was dropped and apply the data to the Circle.</span></span>  
  
### <a name="to-process-the-dropped-data"></a><span data-ttu-id="95d77-193">Bırakılan verileri işlemek için</span><span class="sxs-lookup"><span data-stu-id="95d77-193">To process the dropped data</span></span>  
  
1.  <span data-ttu-id="95d77-194">Circle.xaml.cs veya Circle.xaml.vb açın.</span><span class="sxs-lookup"><span data-stu-id="95d77-194">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>  
  
2.  <span data-ttu-id="95d77-195">Aşağıdakileri ekleyin <xref:System.Windows.UIElement.OnDrop%2A> sınıfı için işleme sağlamak üzere geçersiz kılma <xref:System.Windows.UIElement.Drop> olay.</span><span class="sxs-lookup"><span data-stu-id="95d77-195">Add the following <xref:System.Windows.UIElement.OnDrop%2A> override to provide class handling for the <xref:System.Windows.UIElement.Drop> event.</span></span>  
  
     [!code-csharp[DragDropWalkthrough#OnDrop](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondrop)]
     [!code-vb[DragDropWalkthrough#OnDrop](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondrop)]  
  
     <span data-ttu-id="95d77-196">Bu <xref:System.Windows.UIElement.OnDrop%2A> geçersiz kılma aşağıdaki görevleri gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="95d77-196">This <xref:System.Windows.UIElement.OnDrop%2A> override performs the following tasks:</span></span>  
  
    -   <span data-ttu-id="95d77-197">Kullanan <xref:System.Windows.DataObject.GetDataPresent%2A> sürüklenen veri bir dize nesnesi içerip içermediğini denetlemek için yöntem.</span><span class="sxs-lookup"><span data-stu-id="95d77-197">Uses the <xref:System.Windows.DataObject.GetDataPresent%2A> method to check if the dragged data contains a string object.</span></span>  
  
    -   <span data-ttu-id="95d77-198">Kullanan <xref:System.Windows.DataObject.GetData%2A> varsa, dize verilerini ayıklamak için yöntem.</span><span class="sxs-lookup"><span data-stu-id="95d77-198">Uses the <xref:System.Windows.DataObject.GetData%2A> method to extract the string data if it is present.</span></span>  
  
    -   <span data-ttu-id="95d77-199">Kullanan bir <xref:System.Windows.Media.BrushConverter> dizeye dönüştürmek denemek için bir <xref:System.Windows.Media.Brush>.</span><span class="sxs-lookup"><span data-stu-id="95d77-199">Uses a <xref:System.Windows.Media.BrushConverter> to try to convert the string to a <xref:System.Windows.Media.Brush>.</span></span>  
  
    -   <span data-ttu-id="95d77-200">Dönüştürme başarılı olursa, fırça geçerlidir <xref:System.Windows.Shapes.Shape.Fill%2A> , <xref:System.Windows.Shapes.Ellipse> daire denetiminin kullanıcı Arabirimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="95d77-200">If the conversion is successful, applies the brush to the <xref:System.Windows.Shapes.Shape.Fill%2A> of the <xref:System.Windows.Shapes.Ellipse> that provides the UI of the Circle control.</span></span>  
  
    -   <span data-ttu-id="95d77-201">İşaretleri <xref:System.Windows.UIElement.Drop> işlenmiş olarak olay.</span><span class="sxs-lookup"><span data-stu-id="95d77-201">Marks the <xref:System.Windows.UIElement.Drop> event as handled.</span></span> <span data-ttu-id="95d77-202">Bu olay alırsınız diğer öğeleri daire kullanıcı denetimi, işlenen bilmesi işlenmiş olarak açılan olay işaretlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="95d77-202">You should mark the drop event as handled so that other elements that receive this event know that the Circle user control handled it.</span></span>  
  
3.  <span data-ttu-id="95d77-203">Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="95d77-203">Press F5 to build and run the application.</span></span>  
  
4.  <span data-ttu-id="95d77-204">Metni seçin `green` içinde <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="95d77-204">Select the text `green` in the <xref:System.Windows.Controls.TextBox>.</span></span>  
  
5.  <span data-ttu-id="95d77-205">Metin bir daire denetimine sürükleyin ve bırakın.</span><span class="sxs-lookup"><span data-stu-id="95d77-205">Drag the text to a Circle control and drop it.</span></span> <span data-ttu-id="95d77-206">Mavi yeşil daire değişiklikler.</span><span class="sxs-lookup"><span data-stu-id="95d77-206">The Circle changes from blue to green.</span></span>  
  
     <span data-ttu-id="95d77-207">![Bir dizeyi bir fırça dönüştürme](../../../../docs/framework/wpf/advanced/media/dragdrop-dropgreentext.png "DragDrop_DropGreenText")</span><span class="sxs-lookup"><span data-stu-id="95d77-207">![Convert a string to a brush](../../../../docs/framework/wpf/advanced/media/dragdrop-dropgreentext.png "DragDrop_DropGreenText")</span></span>  
  
6.  <span data-ttu-id="95d77-208">Bir metin yazın `green` içinde <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="95d77-208">Type the text `green` in the <xref:System.Windows.Controls.TextBox>.</span></span>  
  
7.  <span data-ttu-id="95d77-209">Metni seçin `gre` içinde <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="95d77-209">Select the text `gre` in the <xref:System.Windows.Controls.TextBox>.</span></span>  
  
8.  <span data-ttu-id="95d77-210">Bir daire denetimine sürükleyin ve bırakın.</span><span class="sxs-lookup"><span data-stu-id="95d77-210">Drag it to a Circle control and drop it.</span></span> <span data-ttu-id="95d77-211">İmleç değişimleri açılır izin verilir, ancak daire rengi değiştirmez çünkü belirtmek için bildirim `gre` geçerli bir renk değil.</span><span class="sxs-lookup"><span data-stu-id="95d77-211">Notice that the cursor changes to indicate that the drop is allowed, but the color of the Circle does not change because `gre` is not a valid color.</span></span>  
  
9. <span data-ttu-id="95d77-212">Yeşil daire denetiminden sürükleyip mavi daire denetimi.</span><span class="sxs-lookup"><span data-stu-id="95d77-212">Drag from the green Circle control and drop on the blue Circle control.</span></span> <span data-ttu-id="95d77-213">Mavi yeşil daire değişiklikler.</span><span class="sxs-lookup"><span data-stu-id="95d77-213">The Circle changes from blue to green.</span></span> <span data-ttu-id="95d77-214">Hangi imleç gösterilir bağlıdır dikkat edin <xref:System.Windows.Controls.TextBox> veya daireyi sürükleyin kaynağıdır.</span><span class="sxs-lookup"><span data-stu-id="95d77-214">Notice that which cursor is shown depends on whether the <xref:System.Windows.Controls.TextBox> or the Circle is the drag source.</span></span>  
  
 <span data-ttu-id="95d77-215">Ayarı <xref:System.Windows.UIElement.AllowDrop%2A> özelliğine `true` ve bırakılan veri işleme, bir bırakma hedefi olarak bir öğeyi etkinleştirmek için gerekli olan.</span><span class="sxs-lookup"><span data-stu-id="95d77-215">Setting the <xref:System.Windows.UIElement.AllowDrop%2A> property to `true` and processing the dropped data is all that is required to enable an element to be a drop target.</span></span> <span data-ttu-id="95d77-216">Ancak, daha iyi bir kullanıcı deneyimi sağlamak için aynı zamanda işlemelidir <xref:System.Windows.UIElement.DragEnter>, <xref:System.Windows.UIElement.DragLeave>, ve <xref:System.Windows.UIElement.DragOver> olaylar.</span><span class="sxs-lookup"><span data-stu-id="95d77-216">However, to provide a better user experience, you should also handle the <xref:System.Windows.UIElement.DragEnter>, <xref:System.Windows.UIElement.DragLeave>, and <xref:System.Windows.UIElement.DragOver> events.</span></span> <span data-ttu-id="95d77-217">Bu olaylar, denetimleri gerçekleştirmek ve veri kesilmeden önce kullanıcıya ek geri bildirim sağlayın.</span><span class="sxs-lookup"><span data-stu-id="95d77-217">In these events, you can perform checks and provide additional feedback to the user before the data is dropped.</span></span>  
  
 <span data-ttu-id="95d77-218">Veri üzerinde daire kullanıcı denetimini sürüklendiğinde denetimi sürüklenen veri işlem olup olmadığını sürükleme kaynağı haber vermelisiniz.</span><span class="sxs-lookup"><span data-stu-id="95d77-218">When data is dragged over the Circle user control, the control should notify the drag source whether it can process the data that is being dragged.</span></span> <span data-ttu-id="95d77-219">Denetim verileri işlemek nasıl bilmiyorsa açılır reddetme.</span><span class="sxs-lookup"><span data-stu-id="95d77-219">If the control does not know how to process the data, it should refuse the drop.</span></span> <span data-ttu-id="95d77-220">Bunu yapmak için işleyecek <xref:System.Windows.UIElement.DragOver> olay ve kümesi <xref:System.Windows.DragEventArgs.Effects%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="95d77-220">To do this, you will handle the <xref:System.Windows.UIElement.DragOver> event and set the <xref:System.Windows.DragEventArgs.Effects%2A> property.</span></span>  
  
### <a name="to-verify-that-the-data-drop-is-allowed"></a><span data-ttu-id="95d77-221">Veri bırakma izin verildiğini doğrulamak için</span><span class="sxs-lookup"><span data-stu-id="95d77-221">To verify that the data drop is allowed</span></span>  
  
1.  <span data-ttu-id="95d77-222">Circle.xaml.cs veya Circle.xaml.vb açın.</span><span class="sxs-lookup"><span data-stu-id="95d77-222">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>  
  
2.  <span data-ttu-id="95d77-223">Aşağıdakileri ekleyin <xref:System.Windows.UIElement.OnDragOver%2A> sınıfı için işleme sağlamak üzere geçersiz kılma <xref:System.Windows.UIElement.DragOver> olay.</span><span class="sxs-lookup"><span data-stu-id="95d77-223">Add the following <xref:System.Windows.UIElement.OnDragOver%2A> override to provide class handling for the <xref:System.Windows.UIElement.DragOver> event.</span></span>  
  
     [!code-csharp[DragDropWalkthrough#OnDragOver](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragover)]
     [!code-vb[DragDropWalkthrough#OnDragOver](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragover)]  
  
     <span data-ttu-id="95d77-224">Bu <xref:System.Windows.UIElement.OnDragOver%2A> geçersiz kılma aşağıdaki görevleri gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="95d77-224">This <xref:System.Windows.UIElement.OnDragOver%2A> override performs the following tasks:</span></span>  
  
    -   <span data-ttu-id="95d77-225">Ayarlar <xref:System.Windows.DragEventArgs.Effects%2A> özelliğine <xref:System.Windows.DragDropEffects.None>.</span><span class="sxs-lookup"><span data-stu-id="95d77-225">Sets the <xref:System.Windows.DragEventArgs.Effects%2A> property to <xref:System.Windows.DragDropEffects.None>.</span></span>  
  
    -   <span data-ttu-id="95d77-226">İçinde gerçekleştirilen aynı denetimleri gerçekleştirir <xref:System.Windows.UIElement.OnDrop%2A> daire kullanıcı denetimi sürüklenen veri işleyebilir olup olmadığını belirlemek amacıyla yöntemi.</span><span class="sxs-lookup"><span data-stu-id="95d77-226">Performs the same checks that are performed in the <xref:System.Windows.UIElement.OnDrop%2A> method to determine whether the Circle user control can process the dragged data.</span></span>  
  
    -   <span data-ttu-id="95d77-227">Kullanıcı denetiminin veri işleyebilmesi için ayarlar <xref:System.Windows.DragEventArgs.Effects%2A> özelliğine <xref:System.Windows.DragDropEffects.Copy> veya <xref:System.Windows.DragDropEffects.Move>.</span><span class="sxs-lookup"><span data-stu-id="95d77-227">If the user control can process the data, sets the <xref:System.Windows.DragEventArgs.Effects%2A> property to <xref:System.Windows.DragDropEffects.Copy> or <xref:System.Windows.DragDropEffects.Move>.</span></span>  
  
3.  <span data-ttu-id="95d77-228">Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="95d77-228">Press F5 to build and run the application.</span></span>  
  
4.  <span data-ttu-id="95d77-229">Metni seçin `gre` içinde <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="95d77-229">Select the text `gre` in the <xref:System.Windows.Controls.TextBox>.</span></span>  
  
5.  <span data-ttu-id="95d77-230">Metin bir daire denetimi sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="95d77-230">Drag the text to a Circle control.</span></span> <span data-ttu-id="95d77-231">İmleç şimdi açılır olduğundan izin verilmiyor değişimleri belirtmek için bildirim `gre` geçerli bir renk değil.</span><span class="sxs-lookup"><span data-stu-id="95d77-231">Notice that the cursor now changes to indicate that the drop is not allowed because `gre` is not a valid color.</span></span>  
  
 <span data-ttu-id="95d77-232">Bırakma işlemi önizlemesini uygulayarak daha fazla kullanıcı deneyimini geliştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="95d77-232">You can further enhance the user experience by applying a preview of the drop operation.</span></span> <span data-ttu-id="95d77-233">Daire kullanıcı denetimi için geçersiz kılar <xref:System.Windows.UIElement.OnDragEnter%2A> ve <xref:System.Windows.UIElement.OnDragLeave%2A> yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="95d77-233">For the Circle user control, you will override the <xref:System.Windows.UIElement.OnDragEnter%2A> and <xref:System.Windows.UIElement.OnDragLeave%2A> methods.</span></span> <span data-ttu-id="95d77-234">Ne zaman veri sürüklenen geçerli arka plan denetim üzerinde <xref:System.Windows.Shapes.Shape.Fill%2A> bir yer tutucu değişkende kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="95d77-234">When the data is dragged over the control, the current background <xref:System.Windows.Shapes.Shape.Fill%2A> is saved in a placeholder variable.</span></span> <span data-ttu-id="95d77-235">Dize sonra bir fırça dönüştürülür ve uygulanan <xref:System.Windows.Shapes.Ellipse> dairenin sağlayan kullanıcı Arabirimi.</span><span class="sxs-lookup"><span data-stu-id="95d77-235">The string is then converted to a brush and applied to the <xref:System.Windows.Shapes.Ellipse> that provides the Circle's UI.</span></span> <span data-ttu-id="95d77-236">Veri daire dışında ' bırakılan olmadan, özgün sürüklediyseniz <xref:System.Windows.Shapes.Shape.Fill%2A> değeri dairenin yeniden uygulanır.</span><span class="sxs-lookup"><span data-stu-id="95d77-236">If the data is dragged out of the Circle without being dropped, the original <xref:System.Windows.Shapes.Shape.Fill%2A> value is re-applied to the Circle.</span></span>  
  
### <a name="to-preview-the-effects-of-the-drag-and-drop-operation"></a><span data-ttu-id="95d77-237">Sürükle ve bırak işlemi etkilerini önizlemek için</span><span class="sxs-lookup"><span data-stu-id="95d77-237">To preview the effects of the drag-and-drop operation</span></span>  
  
1.  <span data-ttu-id="95d77-238">Circle.xaml.cs veya Circle.xaml.vb açın.</span><span class="sxs-lookup"><span data-stu-id="95d77-238">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>  
  
2.  <span data-ttu-id="95d77-239">Özel bir daire sınıfında bildirin <xref:System.Windows.Media.Brush> adlı değişken `_previousFill` ve kendisine başlatma `null`.</span><span class="sxs-lookup"><span data-stu-id="95d77-239">In the Circle class, declare a private <xref:System.Windows.Media.Brush> variable named `_previousFill` and initialize it to `null`.</span></span>  
  
     [!code-csharp[DragDropWalkthrough#Brush](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#brush)]
     [!code-vb[DragDropWalkthrough#Brush](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#brush)]  
  
3.  <span data-ttu-id="95d77-240">Aşağıdakileri ekleyin <xref:System.Windows.UIElement.OnDragEnter%2A> sınıfı için işleme sağlamak üzere geçersiz kılma <xref:System.Windows.UIElement.DragEnter> olay.</span><span class="sxs-lookup"><span data-stu-id="95d77-240">Add the following <xref:System.Windows.UIElement.OnDragEnter%2A> override to provide class handling for the <xref:System.Windows.UIElement.DragEnter> event.</span></span>  
  
     [!code-csharp[DragDropWalkthrough#OnDragEnter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragenter)]
     [!code-vb[DragDropWalkthrough#OnDragEnter](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragenter)]  
  
     <span data-ttu-id="95d77-241">Bu <xref:System.Windows.UIElement.OnDragEnter%2A> geçersiz kılma aşağıdaki görevleri gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="95d77-241">This <xref:System.Windows.UIElement.OnDragEnter%2A> override performs the following tasks:</span></span>  
  
    -   <span data-ttu-id="95d77-242">Kaydeder <xref:System.Windows.Shapes.Shape.Fill%2A> özelliği <xref:System.Windows.Shapes.Ellipse> içinde `_previousFill` değişkeni.</span><span class="sxs-lookup"><span data-stu-id="95d77-242">Saves the <xref:System.Windows.Shapes.Shape.Fill%2A> property of the <xref:System.Windows.Shapes.Ellipse> in the `_previousFill` variable.</span></span>  
  
    -   <span data-ttu-id="95d77-243">İçinde gerçekleştirilen aynı denetimleri gerçekleştirir <xref:System.Windows.UIElement.OnDrop%2A> yöntemi için veri dönüştürülüp dönüştürülemeyeceğini belirlemek için bir <xref:System.Windows.Media.Brush>.</span><span class="sxs-lookup"><span data-stu-id="95d77-243">Performs the same checks that are performed in the <xref:System.Windows.UIElement.OnDrop%2A> method to determine whether the data can be converted to a <xref:System.Windows.Media.Brush>.</span></span>  
  
    -   <span data-ttu-id="95d77-244">Veriler geçerli bir dönüştürülürse <xref:System.Windows.Media.Brush>, uygular <xref:System.Windows.Shapes.Shape.Fill%2A> , <xref:System.Windows.Shapes.Ellipse>.</span><span class="sxs-lookup"><span data-stu-id="95d77-244">If the data is converted to a valid <xref:System.Windows.Media.Brush>, applies it to the <xref:System.Windows.Shapes.Shape.Fill%2A> of the <xref:System.Windows.Shapes.Ellipse>.</span></span>  
  
4.  <span data-ttu-id="95d77-245">Aşağıdakileri ekleyin <xref:System.Windows.UIElement.OnDragLeave%2A> sınıfı için işleme sağlamak üzere geçersiz kılma <xref:System.Windows.UIElement.DragLeave> olay.</span><span class="sxs-lookup"><span data-stu-id="95d77-245">Add the following <xref:System.Windows.UIElement.OnDragLeave%2A> override to provide class handling for the <xref:System.Windows.UIElement.DragLeave> event.</span></span>  
  
     [!code-csharp[DragDropWalkthrough#OnDragLeave](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragleave)]
     [!code-vb[DragDropWalkthrough#OnDragLeave](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragleave)]  
  
     <span data-ttu-id="95d77-246">Bu <xref:System.Windows.UIElement.OnDragLeave%2A> geçersiz kılma aşağıdaki görevleri gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="95d77-246">This <xref:System.Windows.UIElement.OnDragLeave%2A> override performs the following tasks:</span></span>  
  
    -   <span data-ttu-id="95d77-247">Geçerlidir <xref:System.Windows.Media.Brush> kaydedilen `_previousFill` değişkenini <xref:System.Windows.Shapes.Shape.Fill%2A> , <xref:System.Windows.Shapes.Ellipse> daire kullanıcı denetiminin kullanıcı Arabirimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="95d77-247">Applies the <xref:System.Windows.Media.Brush> saved in the `_previousFill` variable to the <xref:System.Windows.Shapes.Shape.Fill%2A> of the <xref:System.Windows.Shapes.Ellipse> that provides the UI of the Circle user control.</span></span>  
  
5.  <span data-ttu-id="95d77-248">Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="95d77-248">Press F5 to build and run the application.</span></span>  
  
6.  <span data-ttu-id="95d77-249">Metni seçin `green` içinde <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="95d77-249">Select the text `green` in the <xref:System.Windows.Controls.TextBox>.</span></span>  
  
7.  <span data-ttu-id="95d77-250">Metnin bırakmadan olmadan bir daire denetime sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="95d77-250">Drag the text over a Circle control without dropping it.</span></span> <span data-ttu-id="95d77-251">Mavi yeşil daire değişiklikler.</span><span class="sxs-lookup"><span data-stu-id="95d77-251">The Circle changes from blue to green.</span></span>  
  
     <span data-ttu-id="95d77-252">![Bir Sürükle &#45; etkilerini önizleme ve &#45; bırakma işlemi](../../../../docs/framework/wpf/advanced/media/dragdrop-previeweffects.png "DragDrop_PreviewEffects")</span><span class="sxs-lookup"><span data-stu-id="95d77-252">![Preview the effects of a drag&#45;and&#45;drop operation](../../../../docs/framework/wpf/advanced/media/dragdrop-previeweffects.png "DragDrop_PreviewEffects")</span></span>  
  
8.  <span data-ttu-id="95d77-253">Metnin daire denetim uzağa doğru sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="95d77-253">Drag the text away from the Circle control.</span></span> <span data-ttu-id="95d77-254">Daireye mavi için yeşil geri değiştirir.</span><span class="sxs-lookup"><span data-stu-id="95d77-254">The Circle changes from green back to blue.</span></span>  
  
## <a name="enabling-a-panel-to-receive-dropped-data"></a><span data-ttu-id="95d77-255">Bırakılan veri almak bir Panel etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="95d77-255">Enabling a Panel to Receive Dropped Data</span></span>  
 <span data-ttu-id="95d77-256">Bu bölümde, sürüklenen daire veri bırakma hedeflerini olarak davranmak üzere daire kullanıcı denetimleri konak paneller olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="95d77-256">In this section, you will enable the panels that host the Circle user controls to act as drop targets for dragged Circle data.</span></span> <span data-ttu-id="95d77-257">Bir daire bir panelinden taşıyın ya da bir daire sürükleyip sırasında CTRL tuşunu basılı tutarak bir daire denetiminin bir kopya yapmak için sağlayan kod gerçekleştireceksiniz.</span><span class="sxs-lookup"><span data-stu-id="95d77-257">You will implement code that enables you to move a Circle from one panel to another, or to make a copy of a Circle control by holding down the CTRL key while dragging and dropping a Circle.</span></span>  
  
### <a name="to-enable-the-panel-to-be-a-drop-target"></a><span data-ttu-id="95d77-258">Bırakma hedefi için Denetim Masası etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="95d77-258">To enable the panel to be a drop target</span></span>  
  
1.  <span data-ttu-id="95d77-259">MainWindow.xaml açın.</span><span class="sxs-lookup"><span data-stu-id="95d77-259">Open MainWindow.xaml.</span></span>  
  
2.  <span data-ttu-id="95d77-260">Her birinde aşağıdaki XAML gösterildiği gibi <xref:System.Windows.Controls.StackPanel> denetimleri eklemek için işleyiciler <xref:System.Windows.UIElement.DragOver> ve <xref:System.Windows.UIElement.Drop> olaylar.</span><span class="sxs-lookup"><span data-stu-id="95d77-260">As shown in the following XAML, in each of the <xref:System.Windows.Controls.StackPanel> controls, add handlers for the <xref:System.Windows.UIElement.DragOver> and <xref:System.Windows.UIElement.Drop> events.</span></span> <span data-ttu-id="95d77-261">Ad <xref:System.Windows.UIElement.DragOver> olay işleyicisi `panel_DragOver`ve ad <xref:System.Windows.UIElement.Drop> olay işleyicisi `panel_Drop`.</span><span class="sxs-lookup"><span data-stu-id="95d77-261">Name the <xref:System.Windows.UIElement.DragOver> event handler, `panel_DragOver`, and name the <xref:System.Windows.UIElement.Drop> event handler, `panel_Drop`.</span></span>  
  
     [!code-xaml[DragDropWalkthrough#PanelsXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml#panelsxaml)]  
  
3.  <span data-ttu-id="95d77-262">MainWindows.xaml.cs veya MainWindow.xaml.vb açın.</span><span class="sxs-lookup"><span data-stu-id="95d77-262">Open MainWindows.xaml.cs or MainWindow.xaml.vb.</span></span>  
  
4.  <span data-ttu-id="95d77-263">İçin aşağıdaki kodu ekleyip <xref:System.Windows.UIElement.DragOver> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="95d77-263">Add the following code for the <xref:System.Windows.UIElement.DragOver> event handler.</span></span>  
  
     [!code-csharp[DragDropWalkthrough#PanelDragOver](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml.cs#paneldragover)]
     [!code-vb[DragDropWalkthrough#PanelDragOver](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/MainWindow.xaml.vb#paneldragover)]  
  
     <span data-ttu-id="95d77-264">Bu <xref:System.Windows.UIElement.DragOver> olay işleyicisi aşağıdaki görevleri gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="95d77-264">This <xref:System.Windows.UIElement.DragOver> event handler performs the following tasks:</span></span>  
  
    -   <span data-ttu-id="95d77-265">Sürüklenen veri içinde paketlenmiş "Nesne" veri içerip içermediğini denetler <xref:System.Windows.DataObject> daire kullanıcı denetimi tarafından ve çağrısında geçirilen <xref:System.Windows.DragDrop.DoDragDrop%2A>.</span><span class="sxs-lookup"><span data-stu-id="95d77-265">Checks that the dragged data contains the "Object" data that was packaged in the <xref:System.Windows.DataObject> by the Circle user control and passed in the call to <xref:System.Windows.DragDrop.DoDragDrop%2A>.</span></span>  
  
    -   <span data-ttu-id="95d77-266">"Nesne" veri varsa, CTRL tuşunu basılı olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="95d77-266">If the "Object" data is present, checks whether the CTRL key is pressed.</span></span>  
  
    -   <span data-ttu-id="95d77-267">CTRL tuşunu basılı, ayarlar <xref:System.Windows.DragEventArgs.Effects%2A> özelliğine <xref:System.Windows.DragDropEffects.Copy>.</span><span class="sxs-lookup"><span data-stu-id="95d77-267">If the CTRL key is pressed, sets the <xref:System.Windows.DragEventArgs.Effects%2A> property to <xref:System.Windows.DragDropEffects.Copy>.</span></span> <span data-ttu-id="95d77-268">Aksi takdirde ayarlamak <xref:System.Windows.DragEventArgs.Effects%2A> özelliğine <xref:System.Windows.DragDropEffects.Move>.</span><span class="sxs-lookup"><span data-stu-id="95d77-268">Otherwise, set the <xref:System.Windows.DragEventArgs.Effects%2A> property to <xref:System.Windows.DragDropEffects.Move>.</span></span>  
  
5.  <span data-ttu-id="95d77-269">İçin aşağıdaki kodu ekleyip <xref:System.Windows.UIElement.Drop> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="95d77-269">Add the following code for the <xref:System.Windows.UIElement.Drop> event handler.</span></span>  
  
     [!code-csharp[DragDropWalkthrough#PanelDrop](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml.cs#paneldrop)]
     [!code-vb[DragDropWalkthrough#PanelDrop](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/MainWindow.xaml.vb#paneldrop)]  
  
     <span data-ttu-id="95d77-270">Bu <xref:System.Windows.UIElement.Drop> olay işleyicisi aşağıdaki görevleri gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="95d77-270">This <xref:System.Windows.UIElement.Drop> event handler performs the following tasks:</span></span>  
  
    -   <span data-ttu-id="95d77-271">Denetler olup olmadığını <xref:System.Windows.UIElement.Drop> olay zaten işlenmiş.</span><span class="sxs-lookup"><span data-stu-id="95d77-271">Checks whether the <xref:System.Windows.UIElement.Drop> event has already been handled.</span></span> <span data-ttu-id="95d77-272">Başka bir daire kesilirse, örneğin, yuvarlak tanıtıcıları <xref:System.Windows.UIElement.Drop> olayı istemediğiniz ayrıca işlemek için bir daire içeren paneli.</span><span class="sxs-lookup"><span data-stu-id="95d77-272">For instance, if a Circle is dropped on another Circle which handles the <xref:System.Windows.UIElement.Drop> event, you do not want the panel that contains the Circle to also handle it.</span></span>  
  
    -   <span data-ttu-id="95d77-273">Varsa <xref:System.Windows.UIElement.Drop> olay işlenmez, denetimleri CTRL tuşunu basılı olup olmadığını.</span><span class="sxs-lookup"><span data-stu-id="95d77-273">If the <xref:System.Windows.UIElement.Drop> event is not handled, checks whether the CTRL key is pressed.</span></span>  
  
    -   <span data-ttu-id="95d77-274">Ne zaman CTRL tuşunu basılı, <xref:System.Windows.UIElement.Drop> olduğunda, bir daire kopyasını yapar denetlemek ve ekleyin <xref:System.Windows.Controls.Panel.Children%2A> koleksiyonu <xref:System.Windows.Controls.StackPanel>.</span><span class="sxs-lookup"><span data-stu-id="95d77-274">If the CTRL key is pressed when the <xref:System.Windows.UIElement.Drop> happens, makes a copy of the Circle control and add it to the <xref:System.Windows.Controls.Panel.Children%2A> collection of the <xref:System.Windows.Controls.StackPanel>.</span></span>  
  
    -   <span data-ttu-id="95d77-275">CTRL tuşunu basılı değilse, gelen daire taşır <xref:System.Windows.Controls.Panel.Children%2A> kendi üst paneline koleksiyonunu <xref:System.Windows.Controls.Panel.Children%2A> bırakılmış paneli koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="95d77-275">If the CTRL key is not pressed, moves the Circle from the <xref:System.Windows.Controls.Panel.Children%2A> collection of its parent panel to the <xref:System.Windows.Controls.Panel.Children%2A> collection of the panel that it was dropped on.</span></span>  
  
    -   <span data-ttu-id="95d77-276">Kümeleri <xref:System.Windows.DragEventArgs.Effects%2A> bildirmek için özellik <xref:System.Windows.DragDrop.DoDragDrop%2A> yöntemi olup olmadığını taşıma veya kopyalama işlemi gerçekleştirildi.</span><span class="sxs-lookup"><span data-stu-id="95d77-276">Sets the <xref:System.Windows.DragEventArgs.Effects%2A> property to notify the <xref:System.Windows.DragDrop.DoDragDrop%2A> method whether a move or copy operation was performed.</span></span>  
  
6.  <span data-ttu-id="95d77-277">Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="95d77-277">Press F5 to build and run the application.</span></span>  
  
7.  <span data-ttu-id="95d77-278">Metni seçin `green` gelen <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="95d77-278">Select the text `green` from the <xref:System.Windows.Controls.TextBox>.</span></span>  
  
8.  <span data-ttu-id="95d77-279">Metin üzerinde bir daire denetim sürükleyip bırakın.</span><span class="sxs-lookup"><span data-stu-id="95d77-279">Drag the text over a Circle control and drop it.</span></span>  
  
9. <span data-ttu-id="95d77-280">Bir daire denetimi sol panelden sağ panelde sürükleyip bırakın.</span><span class="sxs-lookup"><span data-stu-id="95d77-280">Drag a Circle control from the left panel to the right panel and drop it.</span></span> <span data-ttu-id="95d77-281">Daireye kaldırılır <xref:System.Windows.Controls.Panel.Children%2A> sol panelde koleksiyonunu ve sağ panelde alt koleksiyona eklenir.</span><span class="sxs-lookup"><span data-stu-id="95d77-281">The Circle is removed from the <xref:System.Windows.Controls.Panel.Children%2A> collection of the left panel and added to the Children collection of the right panel.</span></span>  
  
10. <span data-ttu-id="95d77-282">Başka bir panele olarak panelinden bir daire denetimi sürükleyin ve CTRL tuşunu basılı tutarken bırakın.</span><span class="sxs-lookup"><span data-stu-id="95d77-282">Drag a Circle control from the panel it is in to the other panel and drop it while pressing the CTRL key.</span></span> <span data-ttu-id="95d77-283">Daireye kopyalanır ve kopyayı eklenir <xref:System.Windows.Controls.Panel.Children%2A> alma panelini koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="95d77-283">The Circle is copied and the copy is added to the <xref:System.Windows.Controls.Panel.Children%2A> collection of the receiving panel.</span></span>  
  
     <span data-ttu-id="95d77-284">![CTRL tuşunu basılı tutarken bir daire sürükleyerek](../../../../docs/framework/wpf/advanced/media/dragdrop-paneldrop.png "DragDrop_PanelDrop")</span><span class="sxs-lookup"><span data-stu-id="95d77-284">![Dragging a Circle while pressing the CTRL key](../../../../docs/framework/wpf/advanced/media/dragdrop-paneldrop.png "DragDrop_PanelDrop")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95d77-285">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="95d77-285">See Also</span></span>  
 [<span data-ttu-id="95d77-286">Sürükle ve bırak genel bakış</span><span class="sxs-lookup"><span data-stu-id="95d77-286">Drag and Drop Overview</span></span>](../../../../docs/framework/wpf/advanced/drag-and-drop-overview.md)
