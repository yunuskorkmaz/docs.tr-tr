---
title: 'İzlenecek yol: Kullanıcı Denetiminde Sürükleme ve Bırakmayı Etkinleştirme'
description: Windows Presentation Foundation ' de sürükle ve bırak veri aktarımına katılabilen özel bir kullanıcı denetimi oluşturmayı öğrenin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- walkthrough [WPF], drag-and-drop
- drag-and-drop [WPF], walkthrough
ms.assetid: cc844419-1a77-4906-95d9-060d79107fc7
ms.openlocfilehash: 12ad47035a09995094014841b083062743fc2574
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168284"
---
# <a name="walkthrough-enabling-drag-and-drop-on-a-user-control"></a><span data-ttu-id="2c63f-103">İzlenecek yol: Kullanıcı Denetiminde Sürükleme ve Bırakmayı Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="2c63f-103">Walkthrough: Enabling Drag and Drop on a User Control</span></span>

<span data-ttu-id="2c63f-104">Bu izlenecek yol, ' de sürükle ve bırak veri aktarımına katılabilen özel bir kullanıcı denetiminin nasıl oluşturulduğunu gösterir [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="2c63f-104">This walkthrough demonstrates how to create a custom user control that can participate in drag-and-drop data transfer in [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].</span></span>

<span data-ttu-id="2c63f-105">Bu izlenecek yolda, <xref:System.Windows.Controls.UserControl> bir daire şeklini temsil eden özel bır WPF oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="2c63f-105">In this walkthrough, you will create a custom WPF <xref:System.Windows.Controls.UserControl> that represents a circle shape.</span></span> <span data-ttu-id="2c63f-106">Sürükle ve bırak ile veri aktarımını etkinleştirmek için denetime işlevsellik uygulayacaksınız.</span><span class="sxs-lookup"><span data-stu-id="2c63f-106">You will implement functionality on the control to enable data transfer through drag-and-drop.</span></span> <span data-ttu-id="2c63f-107">Örneğin, bir daire denetiminden diğerine sürüklerseniz, Fill Color verileri kaynak çemberden hedefe kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="2c63f-107">For example, if you drag from one Circle control to another, the Fill color data is copied from the source Circle to the target.</span></span> <span data-ttu-id="2c63f-108">Bir daire denetiminden öğesine sürüklerseniz <xref:System.Windows.Controls.TextBox> , Fill renginin dize temsili öğesine kopyalanır <xref:System.Windows.Controls.TextBox> .</span><span class="sxs-lookup"><span data-stu-id="2c63f-108">If you drag from a Circle control to a <xref:System.Windows.Controls.TextBox>, the string representation of the Fill color is copied to the <xref:System.Windows.Controls.TextBox>.</span></span> <span data-ttu-id="2c63f-109">Ayrıca, <xref:System.Windows.Controls.TextBox> sürükle ve bırak işlevlerini test etmek için iki panel denetimi içeren küçük bir uygulama da oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="2c63f-109">You will also create a small application that contains two panel controls and a <xref:System.Windows.Controls.TextBox> to test the drag-and-drop functionality.</span></span> <span data-ttu-id="2c63f-110">Panellerin bırakılan daire verilerini işlemesini sağlayan bir kod yazacaksınız. Bu, bir panelin alt öğe koleksiyonundan daireler taşımanızı veya kopyalamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="2c63f-110">You will write code that enables the panels to process dropped Circle data, which will enable you to move or copy Circles from the Children collection of one panel to the other.</span></span>

<span data-ttu-id="2c63f-111">Bu izlenecek yol aşağıdaki görevleri gösterir:</span><span class="sxs-lookup"><span data-stu-id="2c63f-111">This walkthrough illustrates the following tasks:</span></span>

- <span data-ttu-id="2c63f-112">Özel Kullanıcı denetimi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="2c63f-112">Create a custom user control.</span></span>

- <span data-ttu-id="2c63f-113">Kullanıcı denetimini Sürükle kaynağı olacak şekilde etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="2c63f-113">Enable the user control to be a drag source.</span></span>

- <span data-ttu-id="2c63f-114">Kullanıcı denetiminin bir bırakma hedefi olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="2c63f-114">Enable the user control to be a drop target.</span></span>

- <span data-ttu-id="2c63f-115">Kullanıcı denetiminden bırakılan verileri almak için bir paneli etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="2c63f-115">Enable a panel to receive data dropped from the user control.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="2c63f-116">Ön koşullar</span><span class="sxs-lookup"><span data-stu-id="2c63f-116">Prerequisites</span></span>

<span data-ttu-id="2c63f-117">Bu yönergeyi tamamlamak için Visual Studio gerekir.</span><span class="sxs-lookup"><span data-stu-id="2c63f-117">You need Visual Studio to complete this walkthrough.</span></span>

## <a name="create-the-application-project"></a><span data-ttu-id="2c63f-118">Uygulama projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="2c63f-118">Create the Application Project</span></span>
 <span data-ttu-id="2c63f-119">Bu bölümde, iki panel ve içeren bir ana sayfa içeren uygulama altyapısını oluşturacaksınız <xref:System.Windows.Controls.TextBox> .</span><span class="sxs-lookup"><span data-stu-id="2c63f-119">In this section, you will create the application infrastructure, which includes a main page with two panels and a <xref:System.Windows.Controls.TextBox>.</span></span>

1. <span data-ttu-id="2c63f-120">Visual Basic veya Visual C# ' de adlı yeni bir WPF uygulama projesi oluşturun `DragDropExample` .</span><span class="sxs-lookup"><span data-stu-id="2c63f-120">Create a new WPF Application project in Visual Basic or Visual C# named `DragDropExample`.</span></span> <span data-ttu-id="2c63f-121">Daha fazla bilgi için bkz. [Izlenecek yol: Ilk WPF Masaüstü](../getting-started/walkthrough-my-first-wpf-desktop-application.md)Uygulamam.</span><span class="sxs-lookup"><span data-stu-id="2c63f-121">For more information, see [Walkthrough: My first WPF desktop application](../getting-started/walkthrough-my-first-wpf-desktop-application.md).</span></span>

2. <span data-ttu-id="2c63f-122">MainWindow. xaml ' i açın.</span><span class="sxs-lookup"><span data-stu-id="2c63f-122">Open MainWindow.xaml.</span></span>

3. <span data-ttu-id="2c63f-123">Açılış ve kapanış etiketleri arasına aşağıdaki biçimlendirmeyi ekleyin <xref:System.Windows.Controls.Grid> .</span><span class="sxs-lookup"><span data-stu-id="2c63f-123">Add the following markup between the opening and closing <xref:System.Windows.Controls.Grid> tags.</span></span>

     <span data-ttu-id="2c63f-124">Bu biçimlendirme, test uygulaması için Kullanıcı arabirimi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2c63f-124">This markup creates the user interface for the test application.</span></span>

     [!code-xaml[DragDropWalkthrough#PanelsStep1XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#panelsstep1xaml)]

## <a name="add-a-new-user-control-to-the-project"></a><span data-ttu-id="2c63f-125">Projeye yeni bir kullanıcı denetimi Ekle</span><span class="sxs-lookup"><span data-stu-id="2c63f-125">Add a New User Control to the Project</span></span>
 <span data-ttu-id="2c63f-126">Bu bölümde, projeye yeni bir kullanıcı denetimi ekleyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="2c63f-126">In this section, you will add a new user control to the project.</span></span>

1. <span data-ttu-id="2c63f-127">Proje menüsünde **Kullanıcı denetimi Ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="2c63f-127">On the Project menu, select **Add User Control**.</span></span>

2. <span data-ttu-id="2c63f-128">**Yeni öğe Ekle** iletişim kutusunda, adı olarak değiştirin `Circle.xaml` ve **Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="2c63f-128">In the **Add New Item** dialog box, change the name to `Circle.xaml`, and click **Add**.</span></span>

     <span data-ttu-id="2c63f-129">Circle. xaml ve arka plan kodu projeye eklenir.</span><span class="sxs-lookup"><span data-stu-id="2c63f-129">Circle.xaml and its code-behind is added to the project.</span></span>

3. <span data-ttu-id="2c63f-130">Circle. xaml açın.</span><span class="sxs-lookup"><span data-stu-id="2c63f-130">Open Circle.xaml.</span></span>

     <span data-ttu-id="2c63f-131">Bu dosya, Kullanıcı denetiminin Kullanıcı arabirimi öğelerini içerir.</span><span class="sxs-lookup"><span data-stu-id="2c63f-131">This file will contain the user interface elements of the user control.</span></span>

4. <span data-ttu-id="2c63f-132"><xref:System.Windows.Controls.Grid>Kullanıcı arabirimi olarak mavi bir daire bulunan basit bir kullanıcı denetimi oluşturmak için aşağıdaki biçimlendirmeyi köke ekleyin.</span><span class="sxs-lookup"><span data-stu-id="2c63f-132">Add the following markup to the root <xref:System.Windows.Controls.Grid> to create a simple user control that has a blue circle as its UI.</span></span>

     [!code-xaml[DragDropWalkthrough#EllipseXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml#ellipsexaml)]

5. <span data-ttu-id="2c63f-133">Open Circle.xaml.cs veya Circle. xaml. vb.</span><span class="sxs-lookup"><span data-stu-id="2c63f-133">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>

6. <span data-ttu-id="2c63f-134">C# dilinde, bir kopya Oluşturucu oluşturmak için parametresiz oluşturucudan sonra aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="2c63f-134">In C#, add the following code after the parameterless constructor to create a copy constructor.</span></span> <span data-ttu-id="2c63f-135">Visual Basic, hem parametresiz bir Oluşturucu hem de kopya Oluşturucu oluşturmak için aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="2c63f-135">In Visual Basic, add the following code to create both a parameterless constructor and a copy constructor.</span></span>

     <span data-ttu-id="2c63f-136">Kullanıcı denetiminin kopyalanmasına izin vermek için, arka plan kod dosyasına bir kopya Oluşturucu yöntemi eklersiniz.</span><span class="sxs-lookup"><span data-stu-id="2c63f-136">In order to allow the user control to be copied, you add a copy constructor method in the code-behind file.</span></span> <span data-ttu-id="2c63f-137">Basitleştirilmiş daire Kullanıcı denetiminde, yalnızca Kullanıcı denetiminin dolgusunu ve boyutunu kopyalayacaksınız.</span><span class="sxs-lookup"><span data-stu-id="2c63f-137">In the simplified Circle user control, you will only copy the Fill and the size of the of the user control.</span></span>

     [!code-csharp[DragDropWalkthrough#CopyCtor](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#copyctor)]
     [!code-vb[DragDropWalkthrough#CopyCtor](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#copyctor)]

## <a name="add-the-user-control-to-the-main-window"></a><span data-ttu-id="2c63f-138">Kullanıcı denetimini ana pencereye ekleme</span><span class="sxs-lookup"><span data-stu-id="2c63f-138">Add the user control to the main window</span></span>

1. <span data-ttu-id="2c63f-139">MainWindow. xaml ' i açın.</span><span class="sxs-lookup"><span data-stu-id="2c63f-139">Open MainWindow.xaml.</span></span>

2. <span data-ttu-id="2c63f-140"><xref:System.Windows.Window>Geçerli uygulamaya BIR XML ad alanı başvurusu oluşturmak için AŞAĞıDAKI xaml 'yi açılış etiketine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="2c63f-140">Add the following XAML to the opening <xref:System.Windows.Window> tag to create an XML namespace reference to the current application.</span></span>

    ```xaml
    xmlns:local="clr-namespace:DragDropExample"
    ```

3. <span data-ttu-id="2c63f-141">İlk panelde, <xref:System.Windows.Controls.StackPanel> Circle Kullanıcı denetiminin iki örneğini oluşturmak için önce AŞAĞıDAKI xaml 'yi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="2c63f-141">In the first <xref:System.Windows.Controls.StackPanel>, add the following XAML to create two instances of the Circle user control in the first panel.</span></span>

     [!code-xaml[DragDropWalkthrough#CirclesXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#circlesxaml)]

     <span data-ttu-id="2c63f-142">Panelin tam XAML aşağıdaki gibi görünür.</span><span class="sxs-lookup"><span data-stu-id="2c63f-142">The full XAML for the panel looks like the following.</span></span>

     [!code-xaml[DragDropWalkthrough#PanelsStep2XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#panelsstep2xaml)]

## <a name="implement-drag-source-events-in-the-user-control"></a><span data-ttu-id="2c63f-143">Kullanıcı denetimindeki Sürükle kaynak olaylarını Uygula</span><span class="sxs-lookup"><span data-stu-id="2c63f-143">Implement Drag Source Events in the User Control</span></span>
 <span data-ttu-id="2c63f-144">Bu bölümde, yöntemi geçersiz kılacak <xref:System.Windows.UIElement.OnMouseMove%2A> ve sürükle ve bırak işlemini başlatacaksınız.</span><span class="sxs-lookup"><span data-stu-id="2c63f-144">In this section, you will override the <xref:System.Windows.UIElement.OnMouseMove%2A> method and initiate the drag-and-drop operation.</span></span>

 <span data-ttu-id="2c63f-145">Bir sürükleme başlatılırsa (bir fare düğmesine basıldığında ve fare taşındığında), verileri bir içine aktarılacak şekilde paketleyecaksınız <xref:System.Windows.DataObject> .</span><span class="sxs-lookup"><span data-stu-id="2c63f-145">If a drag is started (a mouse button is pressed and the mouse is moved), you will package the data to be transferred into a <xref:System.Windows.DataObject>.</span></span> <span data-ttu-id="2c63f-146">Bu durumda, Circle denetimi üç veri öğesini paketleyebilir; kendi renk gösterimi ve kendi bir kopyası olan Fill Color dize gösterimi.</span><span class="sxs-lookup"><span data-stu-id="2c63f-146">In this case, the Circle control will package three data items; a string representation of its Fill color, a double representation of its height, and a copy of itself.</span></span>

### <a name="to-initiate-a-drag-and-drop-operation"></a><span data-ttu-id="2c63f-147">Sürükle ve bırak işlemini başlatmak için</span><span class="sxs-lookup"><span data-stu-id="2c63f-147">To initiate a drag-and-drop operation</span></span>

1. <span data-ttu-id="2c63f-148">Open Circle.xaml.cs veya Circle. xaml. vb.</span><span class="sxs-lookup"><span data-stu-id="2c63f-148">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>

2. <span data-ttu-id="2c63f-149"><xref:System.Windows.UIElement.OnMouseMove%2A>Olay için sınıf işleme sağlamak için aşağıdaki geçersiz kılmayı ekleyin <xref:System.Windows.UIElement.MouseMove> .</span><span class="sxs-lookup"><span data-stu-id="2c63f-149">Add the following <xref:System.Windows.UIElement.OnMouseMove%2A> override to provide class handling for the <xref:System.Windows.UIElement.MouseMove> event.</span></span>

     [!code-csharp[DragDropWalkthrough#OnMouseMove](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#onmousemove)]
     [!code-vb[DragDropWalkthrough#OnMouseMove](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#onmousemove)]

     <span data-ttu-id="2c63f-150">Bu <xref:System.Windows.UIElement.OnMouseMove%2A> geçersiz kılma aşağıdaki görevleri gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="2c63f-150">This <xref:System.Windows.UIElement.OnMouseMove%2A> override performs the following tasks:</span></span>

    - <span data-ttu-id="2c63f-151">Fare hareket ettirirken sol fare düğmesine basıldığını denetler.</span><span class="sxs-lookup"><span data-stu-id="2c63f-151">Checks whether the left mouse button is pressed while the mouse is moving.</span></span>

    - <span data-ttu-id="2c63f-152">Daire verisini bir olarak paketler <xref:System.Windows.DataObject> .</span><span class="sxs-lookup"><span data-stu-id="2c63f-152">Packages the Circle data into a <xref:System.Windows.DataObject>.</span></span> <span data-ttu-id="2c63f-153">Bu durumda, daire denetimi üç veri öğesini paketler; kendi renk gösterimi ve kendi bir kopyası olan Fill Color dize gösterimi.</span><span class="sxs-lookup"><span data-stu-id="2c63f-153">In this case, the Circle control packages three data items; a string representation of its Fill color, a double representation of its height, and a copy of itself.</span></span>

    - <span data-ttu-id="2c63f-154"><xref:System.Windows.DragDrop.DoDragDrop%2A?displayProperty=nameWithType>Sürükle ve bırak işlemini başlatmak için statik yöntemi çağırır.</span><span class="sxs-lookup"><span data-stu-id="2c63f-154">Calls the static <xref:System.Windows.DragDrop.DoDragDrop%2A?displayProperty=nameWithType> method to initiate the drag-and-drop operation.</span></span> <span data-ttu-id="2c63f-155">Aşağıdaki üç parametreyi <xref:System.Windows.DragDrop.DoDragDrop%2A> yöntemine geçirirsiniz:</span><span class="sxs-lookup"><span data-stu-id="2c63f-155">You pass the following three parameters to the <xref:System.Windows.DragDrop.DoDragDrop%2A> method:</span></span>

        - <span data-ttu-id="2c63f-156">`dragSource`– Bu denetime bir başvuru.</span><span class="sxs-lookup"><span data-stu-id="2c63f-156">`dragSource` – A reference to this control.</span></span>

        - <span data-ttu-id="2c63f-157">`data`– <xref:System.Windows.DataObject> Önceki kodda oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="2c63f-157">`data` – The <xref:System.Windows.DataObject> created in the previous code.</span></span>

        - <span data-ttu-id="2c63f-158">`allowedEffects`– Veya olan izin verilen sürükle ve bırak işlemleri <xref:System.Windows.DragDropEffects.Copy> <xref:System.Windows.DragDropEffects.Move> .</span><span class="sxs-lookup"><span data-stu-id="2c63f-158">`allowedEffects` – The allowed drag-and-drop operations, which are <xref:System.Windows.DragDropEffects.Copy> or <xref:System.Windows.DragDropEffects.Move>.</span></span>

3. <span data-ttu-id="2c63f-159">Uygulamayı derlemek ve çalıştırmak için **F5** tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="2c63f-159">Press **F5** to build and run the application.</span></span>

4. <span data-ttu-id="2c63f-160">Daire denetimlerinden birine tıklayın ve panelleri, diğer daireyi ve ' nin üzerine sürükleyin <xref:System.Windows.Controls.TextBox> .</span><span class="sxs-lookup"><span data-stu-id="2c63f-160">Click one of the Circle controls and drag it over the panels, the other Circle, and the <xref:System.Windows.Controls.TextBox>.</span></span> <span data-ttu-id="2c63f-161">Üzerinde sürükleme yaparken <xref:System.Windows.Controls.TextBox> , imleç bir taşımayı belirtecek şekilde değişir.</span><span class="sxs-lookup"><span data-stu-id="2c63f-161">When dragging over the <xref:System.Windows.Controls.TextBox>, the cursor changes to indicate a move.</span></span>

5. <span data-ttu-id="2c63f-162">Bir daireyi üzerine sürüklerken <xref:System.Windows.Controls.TextBox> **CTRL** tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="2c63f-162">While dragging a Circle over the <xref:System.Windows.Controls.TextBox>, press the **Ctrl** key.</span></span> <span data-ttu-id="2c63f-163">İmlecin bir kopyayı göstermek için nasıl değiştiği hakkında dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="2c63f-163">Notice how the cursor changes to indicate a copy.</span></span>

6. <span data-ttu-id="2c63f-164">Üzerine bir daire sürükleyip bırakın <xref:System.Windows.Controls.TextBox> .</span><span class="sxs-lookup"><span data-stu-id="2c63f-164">Drag and drop a Circle onto the <xref:System.Windows.Controls.TextBox>.</span></span> <span data-ttu-id="2c63f-165">Dairenin dolgusu renginin dize temsili öğesine eklenir <xref:System.Windows.Controls.TextBox> .</span><span class="sxs-lookup"><span data-stu-id="2c63f-165">The string representation of the Circle’s fill color is appended to the <xref:System.Windows.Controls.TextBox>.</span></span>

     <span data-ttu-id="2c63f-166">![Dairenin dolgusu renginin dize temsili](./media/dragdrop-colorstring.png "DragDrop_ColorString")</span><span class="sxs-lookup"><span data-stu-id="2c63f-166">![String representation of Circle's fill color](./media/dragdrop-colorstring.png "DragDrop_ColorString")</span></span>

<span data-ttu-id="2c63f-167">Varsayılan olarak, imleç bir sürükle ve bırak işlemi sırasında, verilerin hangi etkiyle sonuçlandığını belirten şekilde değişir.</span><span class="sxs-lookup"><span data-stu-id="2c63f-167">By default, the cursor will change during a drag-and-drop operation to indicate what effect dropping the data will have.</span></span> <span data-ttu-id="2c63f-168"><xref:System.Windows.UIElement.GiveFeedback>Olayı işleyerek ve farklı bir imleç ayarlayarak kullanıcıya verilen geri bildirimleri özelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2c63f-168">You can customize the feedback given to the user by handling the <xref:System.Windows.UIElement.GiveFeedback> event and setting a different cursor.</span></span>

## <a name="give-feedback-to-the-user"></a><span data-ttu-id="2c63f-169">Kullanıcıya geri bildirimde bulunun</span><span class="sxs-lookup"><span data-stu-id="2c63f-169">Give feedback to the user</span></span>

1. <span data-ttu-id="2c63f-170">Open Circle.xaml.cs veya Circle. xaml. vb.</span><span class="sxs-lookup"><span data-stu-id="2c63f-170">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>

2. <span data-ttu-id="2c63f-171"><xref:System.Windows.UIElement.OnGiveFeedback%2A>Olay için sınıf işleme sağlamak için aşağıdaki geçersiz kılmayı ekleyin <xref:System.Windows.UIElement.GiveFeedback> .</span><span class="sxs-lookup"><span data-stu-id="2c63f-171">Add the following <xref:System.Windows.UIElement.OnGiveFeedback%2A> override to provide class handling for the <xref:System.Windows.UIElement.GiveFeedback> event.</span></span>

     [!code-csharp[DragDropWalkthrough#OnGiveFeedback](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ongivefeedback)]
     [!code-vb[DragDropWalkthrough#OnGiveFeedback](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ongivefeedback)]

     <span data-ttu-id="2c63f-172">Bu <xref:System.Windows.UIElement.OnGiveFeedback%2A> geçersiz kılma aşağıdaki görevleri gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="2c63f-172">This <xref:System.Windows.UIElement.OnGiveFeedback%2A> override performs the following tasks:</span></span>

    - <span data-ttu-id="2c63f-173"><xref:System.Windows.GiveFeedbackEventArgs.Effects%2A>Bırakma hedefinin olay işleyicisinde ayarlanan değerleri denetler <xref:System.Windows.UIElement.DragOver> .</span><span class="sxs-lookup"><span data-stu-id="2c63f-173">Checks the <xref:System.Windows.GiveFeedbackEventArgs.Effects%2A> values that are set in the drop target's <xref:System.Windows.UIElement.DragOver> event handler.</span></span>

    - <span data-ttu-id="2c63f-174">Değere göre özel bir imleç ayarlar <xref:System.Windows.GiveFeedbackEventArgs.Effects%2A> .</span><span class="sxs-lookup"><span data-stu-id="2c63f-174">Sets a custom cursor based on the <xref:System.Windows.GiveFeedbackEventArgs.Effects%2A> value.</span></span> <span data-ttu-id="2c63f-175">İmlecin, kullanıcıya verilerin ne kadar yürürlükte olacağı hakkında görsel geri bildirim vermesi amaçlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="2c63f-175">The cursor is intended to give visual feedback to the user about what effect dropping the data will have.</span></span>

3. <span data-ttu-id="2c63f-176">Uygulamayı derlemek ve çalıştırmak için **F5** tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="2c63f-176">Press **F5** to build and run the application.</span></span>

4. <span data-ttu-id="2c63f-177">Panel, diğer daire ve için daire denetimlerinden birini sürükleyin <xref:System.Windows.Controls.TextBox> .</span><span class="sxs-lookup"><span data-stu-id="2c63f-177">Drag one of the Circle controls over the panels, the other Circle, and the <xref:System.Windows.Controls.TextBox>.</span></span> <span data-ttu-id="2c63f-178">İmleçlerin artık geçersiz kılmada belirttiğiniz özel imleçler olduğuna dikkat edin <xref:System.Windows.UIElement.OnGiveFeedback%2A> .</span><span class="sxs-lookup"><span data-stu-id="2c63f-178">Notice that the cursors are now the custom cursors that you specified in the <xref:System.Windows.UIElement.OnGiveFeedback%2A> override.</span></span>

     <span data-ttu-id="2c63f-179">![Özel imleçlerle sürükleyip bırakma](./media/dragdrop-customcursor.png "DragDrop_CustomCursor")</span><span class="sxs-lookup"><span data-stu-id="2c63f-179">![Drag and drop with custom cursors](./media/dragdrop-customcursor.png "DragDrop_CustomCursor")</span></span>

5. <span data-ttu-id="2c63f-180">Öğesinden metni seçin `green` <xref:System.Windows.Controls.TextBox> .</span><span class="sxs-lookup"><span data-stu-id="2c63f-180">Select the text `green` from the <xref:System.Windows.Controls.TextBox>.</span></span>

6. <span data-ttu-id="2c63f-181">`green`Metni bir daire denetimine sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="2c63f-181">Drag the `green` text to a Circle control.</span></span> <span data-ttu-id="2c63f-182">Sürükle ve bırak işleminin etkilerini belirtmek için varsayılan imleçlerin gösterildiğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="2c63f-182">Notice that the default cursors are shown to indicate the effects of the drag-and-drop operation.</span></span> <span data-ttu-id="2c63f-183">Geri bildirim imleci her zaman Sürükle kaynağı tarafından ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="2c63f-183">The feedback cursor is always set by the drag source.</span></span>

## <a name="implement-drop-target-events-in-the-user-control"></a><span data-ttu-id="2c63f-184">Kullanıcı denetiminde bırakma hedefi olaylarını uygulama</span><span class="sxs-lookup"><span data-stu-id="2c63f-184">Implement Drop Target Events in the User Control</span></span>
 <span data-ttu-id="2c63f-185">Bu bölümde, Kullanıcı denetiminin bir bırakma hedefi olduğunu, Kullanıcı denetiminin bir bırakma hedefi olmasını sağlayan yöntemleri geçersiz kılacaksınız ve üzerinde bırakılan verileri işleyecek şekilde belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2c63f-185">In this section, you will specify that the user control is a drop target, override the methods that enable the user control to be a drop target, and process the data that is dropped on it.</span></span>

### <a name="to-enable-the-user-control-to-be-a-drop-target"></a><span data-ttu-id="2c63f-186">Kullanıcı denetiminin bir bırakma hedefi olmasını sağlamak için</span><span class="sxs-lookup"><span data-stu-id="2c63f-186">To enable the user control to be a drop target</span></span>

1. <span data-ttu-id="2c63f-187">Circle. xaml açın.</span><span class="sxs-lookup"><span data-stu-id="2c63f-187">Open Circle.xaml.</span></span>

2. <span data-ttu-id="2c63f-188">Açma <xref:System.Windows.Controls.UserControl> etiketinde <xref:System.Windows.UIElement.AllowDrop%2A> özelliği ekleyin ve olarak ayarlayın `true` .</span><span class="sxs-lookup"><span data-stu-id="2c63f-188">In the opening <xref:System.Windows.Controls.UserControl> tag, add the <xref:System.Windows.UIElement.AllowDrop%2A> property and set it to `true`.</span></span>

     [!code-xaml[DragDropWalkthrough#UCTagXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml#uctagxaml)]

<span data-ttu-id="2c63f-189"><xref:System.Windows.UIElement.OnDrop%2A>Yöntemi, <xref:System.Windows.UIElement.AllowDrop%2A> özelliği olarak ayarlandığında `true` ve sürükleme kaynağındaki veriler daire Kullanıcı denetiminde bırakıldığında çağrılır.</span><span class="sxs-lookup"><span data-stu-id="2c63f-189">The <xref:System.Windows.UIElement.OnDrop%2A> method is called when the <xref:System.Windows.UIElement.AllowDrop%2A> property is set to `true` and data from the drag source is dropped on the Circle user control.</span></span> <span data-ttu-id="2c63f-190">Bu yöntemde, bırakılan verileri işleyecek ve verileri daireye uygulamanız gerekecektir.</span><span class="sxs-lookup"><span data-stu-id="2c63f-190">In this method, you will process the data that was dropped and apply the data to the Circle.</span></span>

### <a name="to-process-the-dropped-data"></a><span data-ttu-id="2c63f-191">Bırakılan verileri işlemek için</span><span class="sxs-lookup"><span data-stu-id="2c63f-191">To process the dropped data</span></span>

1. <span data-ttu-id="2c63f-192">Open Circle.xaml.cs veya Circle. xaml. vb.</span><span class="sxs-lookup"><span data-stu-id="2c63f-192">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>

2. <span data-ttu-id="2c63f-193"><xref:System.Windows.UIElement.OnDrop%2A>Olay için sınıf işleme sağlamak için aşağıdaki geçersiz kılmayı ekleyin <xref:System.Windows.UIElement.Drop> .</span><span class="sxs-lookup"><span data-stu-id="2c63f-193">Add the following <xref:System.Windows.UIElement.OnDrop%2A> override to provide class handling for the <xref:System.Windows.UIElement.Drop> event.</span></span>

     [!code-csharp[DragDropWalkthrough#OnDrop](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondrop)]
     [!code-vb[DragDropWalkthrough#OnDrop](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondrop)]

     <span data-ttu-id="2c63f-194">Bu <xref:System.Windows.UIElement.OnDrop%2A> geçersiz kılma aşağıdaki görevleri gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="2c63f-194">This <xref:System.Windows.UIElement.OnDrop%2A> override performs the following tasks:</span></span>

    - <span data-ttu-id="2c63f-195">, <xref:System.Windows.DataObject.GetDataPresent%2A> Sürüklenen verilerin bir dize nesnesi içerip içermediğinden emin olmak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="2c63f-195">Uses the <xref:System.Windows.DataObject.GetDataPresent%2A> method to check if the dragged data contains a string object.</span></span>

    - <span data-ttu-id="2c63f-196">, Varsa <xref:System.Windows.DataObject.GetData%2A> dize verilerini ayıklamak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="2c63f-196">Uses the <xref:System.Windows.DataObject.GetData%2A> method to extract the string data if it is present.</span></span>

    - <span data-ttu-id="2c63f-197"><xref:System.Windows.Media.BrushConverter>Dizeyi öğesine dönüştürmeyi denemek için öğesini kullanır <xref:System.Windows.Media.Brush> .</span><span class="sxs-lookup"><span data-stu-id="2c63f-197">Uses a <xref:System.Windows.Media.BrushConverter> to try to convert the string to a <xref:System.Windows.Media.Brush>.</span></span>

    - <span data-ttu-id="2c63f-198">Dönüştürme başarılı olursa, ' <xref:System.Windows.Shapes.Shape.Fill%2A> nin, <xref:System.Windows.Shapes.Ellipse> daire denetiminin Kullanıcı arabirimini sağlayan öğesine fırça uygular.</span><span class="sxs-lookup"><span data-stu-id="2c63f-198">If the conversion is successful, applies the brush to the <xref:System.Windows.Shapes.Shape.Fill%2A> of the <xref:System.Windows.Shapes.Ellipse> that provides the UI of the Circle control.</span></span>

    - <span data-ttu-id="2c63f-199"><xref:System.Windows.UIElement.Drop>Olayı işlenmiş olarak işaretler.</span><span class="sxs-lookup"><span data-stu-id="2c63f-199">Marks the <xref:System.Windows.UIElement.Drop> event as handled.</span></span> <span data-ttu-id="2c63f-200">Bu olayı alan diğer öğelerin, Circle Kullanıcı denetiminin bunu ele aldığından emin olmak için bırakma olayını işlenmiş olarak işaretlemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="2c63f-200">You should mark the drop event as handled so that other elements that receive this event know that the Circle user control handled it.</span></span>

3. <span data-ttu-id="2c63f-201">Uygulamayı derlemek ve çalıştırmak için **F5** tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="2c63f-201">Press **F5** to build and run the application.</span></span>

4. <span data-ttu-id="2c63f-202">İçindeki metni seçin `green` <xref:System.Windows.Controls.TextBox> .</span><span class="sxs-lookup"><span data-stu-id="2c63f-202">Select the text `green` in the <xref:System.Windows.Controls.TextBox>.</span></span>

5. <span data-ttu-id="2c63f-203">Metni bir daire denetimine sürükleyin ve bırakın.</span><span class="sxs-lookup"><span data-stu-id="2c63f-203">Drag the text to a Circle control and drop it.</span></span> <span data-ttu-id="2c63f-204">Daire mavi ile yeşil arasında değişir.</span><span class="sxs-lookup"><span data-stu-id="2c63f-204">The Circle changes from blue to green.</span></span>

     <span data-ttu-id="2c63f-205">![Bir dizeyi fırçaya Dönüştür](./media/dragdrop-dropgreentext.png "DragDrop_DropGreenText")</span><span class="sxs-lookup"><span data-stu-id="2c63f-205">![Convert a string to a brush](./media/dragdrop-dropgreentext.png "DragDrop_DropGreenText")</span></span>

6. <span data-ttu-id="2c63f-206">Metni içine yazın `green` <xref:System.Windows.Controls.TextBox> .</span><span class="sxs-lookup"><span data-stu-id="2c63f-206">Type the text `green` in the <xref:System.Windows.Controls.TextBox>.</span></span>

7. <span data-ttu-id="2c63f-207">İçindeki metni seçin `gre` <xref:System.Windows.Controls.TextBox> .</span><span class="sxs-lookup"><span data-stu-id="2c63f-207">Select the text `gre` in the <xref:System.Windows.Controls.TextBox>.</span></span>

8. <span data-ttu-id="2c63f-208">Bir daire denetimine sürükleyin ve bırakın.</span><span class="sxs-lookup"><span data-stu-id="2c63f-208">Drag it to a Circle control and drop it.</span></span> <span data-ttu-id="2c63f-209">İmlecin, bırakmaya izin verildiğini belirtmek için değiştiği, ancak dairenin rengi geçerli bir renk olmadığından, bu değişikliğin değişmediğine dikkat edin `gre` .</span><span class="sxs-lookup"><span data-stu-id="2c63f-209">Notice that the cursor changes to indicate that the drop is allowed, but the color of the Circle does not change because `gre` is not a valid color.</span></span>

9. <span data-ttu-id="2c63f-210">Yeşil daire denetiminden sürükleyin ve mavi daire denetiminin üzerine bırakın.</span><span class="sxs-lookup"><span data-stu-id="2c63f-210">Drag from the green Circle control and drop on the blue Circle control.</span></span> <span data-ttu-id="2c63f-211">Daire mavi ile yeşil arasında değişir.</span><span class="sxs-lookup"><span data-stu-id="2c63f-211">The Circle changes from blue to green.</span></span> <span data-ttu-id="2c63f-212">Hangi imlecin gösterildiğine dikkat edin, <xref:System.Windows.Controls.TextBox> ya da dairenin Sürükle kaynağı olup olmamasına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="2c63f-212">Notice that which cursor is shown depends on whether the <xref:System.Windows.Controls.TextBox> or the Circle is the drag source.</span></span>

<span data-ttu-id="2c63f-213"><xref:System.Windows.UIElement.AllowDrop%2A>Özelliği `true` bırakılan verileri olarak ayarlamak ve işlemek bir öğenin bir bırakma hedefi olmasını sağlamak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="2c63f-213">Setting the <xref:System.Windows.UIElement.AllowDrop%2A> property to `true` and processing the dropped data is all that is required to enable an element to be a drop target.</span></span> <span data-ttu-id="2c63f-214">Ancak, daha iyi bir kullanıcı deneyimi sağlamak için,, ve olaylarını da işlemeniz gerekir <xref:System.Windows.UIElement.DragEnter> <xref:System.Windows.UIElement.DragLeave> <xref:System.Windows.UIElement.DragOver> .</span><span class="sxs-lookup"><span data-stu-id="2c63f-214">However, to provide a better user experience, you should also handle the <xref:System.Windows.UIElement.DragEnter>, <xref:System.Windows.UIElement.DragLeave>, and <xref:System.Windows.UIElement.DragOver> events.</span></span> <span data-ttu-id="2c63f-215">Bu olaylarda, denetimler gerçekleştirebilir ve veriler kesilmeden önce kullanıcıya ek geri bildirim sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2c63f-215">In these events, you can perform checks and provide additional feedback to the user before the data is dropped.</span></span>

<span data-ttu-id="2c63f-216">Veriler, Circle Kullanıcı denetiminin üzerine sürüklendiğinde denetim, sürüklenen verileri işleip işleyemeyeceğini, sürükleme kaynağını bilgilendirmelidir.</span><span class="sxs-lookup"><span data-stu-id="2c63f-216">When data is dragged over the Circle user control, the control should notify the drag source whether it can process the data that is being dragged.</span></span> <span data-ttu-id="2c63f-217">Denetim, verilerin nasıl işleyeceğini bilmez ise, bırakmayı reddetmelidir.</span><span class="sxs-lookup"><span data-stu-id="2c63f-217">If the control does not know how to process the data, it should refuse the drop.</span></span> <span data-ttu-id="2c63f-218">Bunu yapmak için, <xref:System.Windows.UIElement.DragOver> olayı işleyecek ve özelliğini ayarlayacaksınız <xref:System.Windows.DragEventArgs.Effects%2A> .</span><span class="sxs-lookup"><span data-stu-id="2c63f-218">To do this, you will handle the <xref:System.Windows.UIElement.DragOver> event and set the <xref:System.Windows.DragEventArgs.Effects%2A> property.</span></span>

### <a name="to-verify-that-the-data-drop-is-allowed"></a><span data-ttu-id="2c63f-219">Veri bırakmaya izin verildiğini doğrulamak için</span><span class="sxs-lookup"><span data-stu-id="2c63f-219">To verify that the data drop is allowed</span></span>

1. <span data-ttu-id="2c63f-220">Open Circle.xaml.cs veya Circle. xaml. vb.</span><span class="sxs-lookup"><span data-stu-id="2c63f-220">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>

2. <span data-ttu-id="2c63f-221"><xref:System.Windows.UIElement.OnDragOver%2A>Olay için sınıf işleme sağlamak için aşağıdaki geçersiz kılmayı ekleyin <xref:System.Windows.UIElement.DragOver> .</span><span class="sxs-lookup"><span data-stu-id="2c63f-221">Add the following <xref:System.Windows.UIElement.OnDragOver%2A> override to provide class handling for the <xref:System.Windows.UIElement.DragOver> event.</span></span>

     [!code-csharp[DragDropWalkthrough#OnDragOver](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragover)]
     [!code-vb[DragDropWalkthrough#OnDragOver](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragover)]

     <span data-ttu-id="2c63f-222">Bu <xref:System.Windows.UIElement.OnDragOver%2A> geçersiz kılma aşağıdaki görevleri gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="2c63f-222">This <xref:System.Windows.UIElement.OnDragOver%2A> override performs the following tasks:</span></span>

    - <span data-ttu-id="2c63f-223"><xref:System.Windows.DragEventArgs.Effects%2A>Özelliğini olarak ayarlar <xref:System.Windows.DragDropEffects.None> .</span><span class="sxs-lookup"><span data-stu-id="2c63f-223">Sets the <xref:System.Windows.DragEventArgs.Effects%2A> property to <xref:System.Windows.DragDropEffects.None>.</span></span>

    - <span data-ttu-id="2c63f-224"><xref:System.Windows.UIElement.OnDrop%2A>Circle Kullanıcı denetiminin sürüklenen verileri işleyemeyeceğini anlamak için yönteminde gerçekleştirilen denetimleri gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="2c63f-224">Performs the same checks that are performed in the <xref:System.Windows.UIElement.OnDrop%2A> method to determine whether the Circle user control can process the dragged data.</span></span>

    - <span data-ttu-id="2c63f-225">Kullanıcı denetimi verileri işleyebiliyorsanız, <xref:System.Windows.DragEventArgs.Effects%2A> özelliğini veya olarak ayarlar <xref:System.Windows.DragDropEffects.Copy> <xref:System.Windows.DragDropEffects.Move> .</span><span class="sxs-lookup"><span data-stu-id="2c63f-225">If the user control can process the data, sets the <xref:System.Windows.DragEventArgs.Effects%2A> property to <xref:System.Windows.DragDropEffects.Copy> or <xref:System.Windows.DragDropEffects.Move>.</span></span>

3. <span data-ttu-id="2c63f-226">Uygulamayı derlemek ve çalıştırmak için **F5** tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="2c63f-226">Press **F5** to build and run the application.</span></span>

4. <span data-ttu-id="2c63f-227">İçindeki metni seçin `gre` <xref:System.Windows.Controls.TextBox> .</span><span class="sxs-lookup"><span data-stu-id="2c63f-227">Select the text `gre` in the <xref:System.Windows.Controls.TextBox>.</span></span>

5. <span data-ttu-id="2c63f-228">Metni bir daire denetimine sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="2c63f-228">Drag the text to a Circle control.</span></span> <span data-ttu-id="2c63f-229">İmlecin şimdi, geçerli bir renk olmadığından, bırakmaya izin verilmediğini göstermek için değişiklik olduğuna dikkat edin `gre` .</span><span class="sxs-lookup"><span data-stu-id="2c63f-229">Notice that the cursor now changes to indicate that the drop is not allowed because `gre` is not a valid color.</span></span>

 <span data-ttu-id="2c63f-230">Bırakma işleminin önizlemesini uygulayarak Kullanıcı deneyimini daha da geliştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2c63f-230">You can further enhance the user experience by applying a preview of the drop operation.</span></span> <span data-ttu-id="2c63f-231">Circle Kullanıcı denetimi için ve yöntemlerini geçersiz kılacaksınız <xref:System.Windows.UIElement.OnDragEnter%2A> <xref:System.Windows.UIElement.OnDragLeave%2A> .</span><span class="sxs-lookup"><span data-stu-id="2c63f-231">For the Circle user control, you will override the <xref:System.Windows.UIElement.OnDragEnter%2A> and <xref:System.Windows.UIElement.OnDragLeave%2A> methods.</span></span> <span data-ttu-id="2c63f-232">Veriler denetimin üzerine sürüklendiğinde, geçerli arka plan <xref:System.Windows.Shapes.Shape.Fill%2A> bir yer tutucu değişkenine kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="2c63f-232">When the data is dragged over the control, the current background <xref:System.Windows.Shapes.Shape.Fill%2A> is saved in a placeholder variable.</span></span> <span data-ttu-id="2c63f-233">Daha sonra dize bir fırçaya dönüştürülüp <xref:System.Windows.Shapes.Ellipse> dairenin Kullanıcı arabirimini sağlayan öğesine uygulanır.</span><span class="sxs-lookup"><span data-stu-id="2c63f-233">The string is then converted to a brush and applied to the <xref:System.Windows.Shapes.Ellipse> that provides the Circle's UI.</span></span> <span data-ttu-id="2c63f-234">Verilerin bırakılmadan dışına sürüklenmesi durumunda özgün <xref:System.Windows.Shapes.Shape.Fill%2A> değer, daireye yeniden uygulanır.</span><span class="sxs-lookup"><span data-stu-id="2c63f-234">If the data is dragged out of the Circle without being dropped, the original <xref:System.Windows.Shapes.Shape.Fill%2A> value is re-applied to the Circle.</span></span>

### <a name="to-preview-the-effects-of-the-drag-and-drop-operation"></a><span data-ttu-id="2c63f-235">Sürükle ve bırak işleminin etkilerini önizlemek için</span><span class="sxs-lookup"><span data-stu-id="2c63f-235">To preview the effects of the drag-and-drop operation</span></span>

1. <span data-ttu-id="2c63f-236">Open Circle.xaml.cs veya Circle. xaml. vb.</span><span class="sxs-lookup"><span data-stu-id="2c63f-236">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>

2. <span data-ttu-id="2c63f-237">Circle sınıfında adlı bir özel <xref:System.Windows.Media.Brush> değişken bildirin `_previousFill` ve bunu olarak başlatın `null` .</span><span class="sxs-lookup"><span data-stu-id="2c63f-237">In the Circle class, declare a private <xref:System.Windows.Media.Brush> variable named `_previousFill` and initialize it to `null`.</span></span>

     [!code-csharp[DragDropWalkthrough#Brush](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#brush)]
     [!code-vb[DragDropWalkthrough#Brush](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#brush)]

3. <span data-ttu-id="2c63f-238"><xref:System.Windows.UIElement.OnDragEnter%2A>Olay için sınıf işleme sağlamak için aşağıdaki geçersiz kılmayı ekleyin <xref:System.Windows.UIElement.DragEnter> .</span><span class="sxs-lookup"><span data-stu-id="2c63f-238">Add the following <xref:System.Windows.UIElement.OnDragEnter%2A> override to provide class handling for the <xref:System.Windows.UIElement.DragEnter> event.</span></span>

     [!code-csharp[DragDropWalkthrough#OnDragEnter](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragenter)]
     [!code-vb[DragDropWalkthrough#OnDragEnter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragenter)]

     <span data-ttu-id="2c63f-239">Bu <xref:System.Windows.UIElement.OnDragEnter%2A> geçersiz kılma aşağıdaki görevleri gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="2c63f-239">This <xref:System.Windows.UIElement.OnDragEnter%2A> override performs the following tasks:</span></span>

    - <span data-ttu-id="2c63f-240"><xref:System.Windows.Shapes.Shape.Fill%2A>Öğesinin özelliğini <xref:System.Windows.Shapes.Ellipse> `_previousFill` değişkenine kaydeder.</span><span class="sxs-lookup"><span data-stu-id="2c63f-240">Saves the <xref:System.Windows.Shapes.Shape.Fill%2A> property of the <xref:System.Windows.Shapes.Ellipse> in the `_previousFill` variable.</span></span>

    - <span data-ttu-id="2c63f-241"><xref:System.Windows.UIElement.OnDrop%2A>Verilerin bir öğesine dönüştürülüp dönüştürülmeyeceğini anlamak için yönteminde gerçekleştirilen denetimleri gerçekleştirir <xref:System.Windows.Media.Brush> .</span><span class="sxs-lookup"><span data-stu-id="2c63f-241">Performs the same checks that are performed in the <xref:System.Windows.UIElement.OnDrop%2A> method to determine whether the data can be converted to a <xref:System.Windows.Media.Brush>.</span></span>

    - <span data-ttu-id="2c63f-242">Veriler geçerli bir değerine dönüştürülürse, <xref:System.Windows.Media.Brush> ' nin öğesine uygular <xref:System.Windows.Shapes.Shape.Fill%2A> <xref:System.Windows.Shapes.Ellipse> .</span><span class="sxs-lookup"><span data-stu-id="2c63f-242">If the data is converted to a valid <xref:System.Windows.Media.Brush>, applies it to the <xref:System.Windows.Shapes.Shape.Fill%2A> of the <xref:System.Windows.Shapes.Ellipse>.</span></span>

4. <span data-ttu-id="2c63f-243"><xref:System.Windows.UIElement.OnDragLeave%2A>Olay için sınıf işleme sağlamak için aşağıdaki geçersiz kılmayı ekleyin <xref:System.Windows.UIElement.DragLeave> .</span><span class="sxs-lookup"><span data-stu-id="2c63f-243">Add the following <xref:System.Windows.UIElement.OnDragLeave%2A> override to provide class handling for the <xref:System.Windows.UIElement.DragLeave> event.</span></span>

     [!code-csharp[DragDropWalkthrough#OnDragLeave](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragleave)]
     [!code-vb[DragDropWalkthrough#OnDragLeave](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragleave)]

     <span data-ttu-id="2c63f-244">Bu <xref:System.Windows.UIElement.OnDragLeave%2A> geçersiz kılma aşağıdaki görevleri gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="2c63f-244">This <xref:System.Windows.UIElement.OnDragLeave%2A> override performs the following tasks:</span></span>

    - <span data-ttu-id="2c63f-245">Değişkenine, <xref:System.Windows.Media.Brush> `_previousFill` <xref:System.Windows.Shapes.Shape.Fill%2A> <xref:System.Windows.Shapes.Ellipse> Circle Kullanıcı denetiminin Kullanıcı arabirimini sağlayan öğesine uygular.</span><span class="sxs-lookup"><span data-stu-id="2c63f-245">Applies the <xref:System.Windows.Media.Brush> saved in the `_previousFill` variable to the <xref:System.Windows.Shapes.Shape.Fill%2A> of the <xref:System.Windows.Shapes.Ellipse> that provides the UI of the Circle user control.</span></span>

5. <span data-ttu-id="2c63f-246">Uygulamayı derlemek ve çalıştırmak için **F5** tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="2c63f-246">Press **F5** to build and run the application.</span></span>

6. <span data-ttu-id="2c63f-247">İçindeki metni seçin `green` <xref:System.Windows.Controls.TextBox> .</span><span class="sxs-lookup"><span data-stu-id="2c63f-247">Select the text `green` in the <xref:System.Windows.Controls.TextBox>.</span></span>

7. <span data-ttu-id="2c63f-248">Metni bırakmadan bir daire denetiminin üzerine sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="2c63f-248">Drag the text over a Circle control without dropping it.</span></span> <span data-ttu-id="2c63f-249">Daire mavi ile yeşil arasında değişir.</span><span class="sxs-lookup"><span data-stu-id="2c63f-249">The Circle changes from blue to green.</span></span>

     <span data-ttu-id="2c63f-250">![Bir sürükle&#45;ve&#45;bırakma işleminin etkilerini önizleyin](./media/dragdrop-previeweffects.png "DragDrop_PreviewEffects")</span><span class="sxs-lookup"><span data-stu-id="2c63f-250">![Preview the effects of a drag&#45;and&#45;drop operation](./media/dragdrop-previeweffects.png "DragDrop_PreviewEffects")</span></span>

8. <span data-ttu-id="2c63f-251">Metni daire denetiminden uzağa sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="2c63f-251">Drag the text away from the Circle control.</span></span> <span data-ttu-id="2c63f-252">Daire, yeşil ve mavi arasında değişir.</span><span class="sxs-lookup"><span data-stu-id="2c63f-252">The Circle changes from green back to blue.</span></span>

## <a name="enable-a-panel-to-receive-dropped-data"></a><span data-ttu-id="2c63f-253">Bir paneli bırakılan verileri alacak şekilde etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="2c63f-253">Enable a Panel to Receive Dropped Data</span></span>

<span data-ttu-id="2c63f-254">Bu bölümde, daire kullanıcı denetimlerini barındıran bölmeleri, sürüklenen daire verileri için bırakma hedefleri olarak davranacak şekilde etkinleştirirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2c63f-254">In this section, you enable the panels that host the Circle user controls to act as drop targets for dragged Circle data.</span></span> <span data-ttu-id="2c63f-255">Bir daireyi bir panelden diğerine taşımanızı veya bir daireyi Sürükleyip bırakırken **CTRL** tuşunu basılı tutarak bir daire denetiminin kopyasını yapmanızı sağlayan kodu uygulayacaksınız.</span><span class="sxs-lookup"><span data-stu-id="2c63f-255">You will implement code that enables you to move a Circle from one panel to another, or to make a copy of a Circle control by holding down the **Ctrl** key while dragging and dropping a Circle.</span></span>

1. <span data-ttu-id="2c63f-256">MainWindow. xaml ' i açın.</span><span class="sxs-lookup"><span data-stu-id="2c63f-256">Open MainWindow.xaml.</span></span>

2. <span data-ttu-id="2c63f-257">Aşağıdaki XAML 'de gösterildiği gibi, denetimlerin her birinde <xref:System.Windows.Controls.StackPanel> ve olayları için işleyiciler ekleyin <xref:System.Windows.UIElement.DragOver> <xref:System.Windows.UIElement.Drop> .</span><span class="sxs-lookup"><span data-stu-id="2c63f-257">As shown in the following XAML, in each of the <xref:System.Windows.Controls.StackPanel> controls, add handlers for the <xref:System.Windows.UIElement.DragOver> and <xref:System.Windows.UIElement.Drop> events.</span></span> <span data-ttu-id="2c63f-258"><xref:System.Windows.UIElement.DragOver>Olay işleyicisini adlandırın, `panel_DragOver` ve <xref:System.Windows.UIElement.Drop> olay işleyicisini adlandırın `panel_Drop` .</span><span class="sxs-lookup"><span data-stu-id="2c63f-258">Name the <xref:System.Windows.UIElement.DragOver> event handler, `panel_DragOver`, and name the <xref:System.Windows.UIElement.Drop> event handler, `panel_Drop`.</span></span>

     [!code-xaml[DragDropWalkthrough#PanelsXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml#panelsxaml)]

3. <span data-ttu-id="2c63f-259">MainWindows.xaml.cs veya MainWindow. xaml. vb dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="2c63f-259">Open MainWindows.xaml.cs or MainWindow.xaml.vb.</span></span>

4. <span data-ttu-id="2c63f-260">Olay işleyicisi için aşağıdaki kodu ekleyin <xref:System.Windows.UIElement.DragOver> .</span><span class="sxs-lookup"><span data-stu-id="2c63f-260">Add the following code for the <xref:System.Windows.UIElement.DragOver> event handler.</span></span>

     [!code-csharp[DragDropWalkthrough#PanelDragOver](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml.cs#paneldragover)]
     [!code-vb[DragDropWalkthrough#PanelDragOver](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/MainWindow.xaml.vb#paneldragover)]

     <span data-ttu-id="2c63f-261">Bu <xref:System.Windows.UIElement.DragOver> olay işleyicisi aşağıdaki görevleri gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="2c63f-261">This <xref:System.Windows.UIElement.DragOver> event handler performs the following tasks:</span></span>

    - <span data-ttu-id="2c63f-262">Sürüklenen verilerin, <xref:System.Windows.DataObject> Circle Kullanıcı denetimiyle paketlenmiş ve çağrısına geçilen "nesne" verilerini içerip içermediğini denetler <xref:System.Windows.DragDrop.DoDragDrop%2A> .</span><span class="sxs-lookup"><span data-stu-id="2c63f-262">Checks that the dragged data contains the "Object" data that was packaged in the <xref:System.Windows.DataObject> by the Circle user control and passed in the call to <xref:System.Windows.DragDrop.DoDragDrop%2A>.</span></span>

    - <span data-ttu-id="2c63f-263">"Nesne" verileri mevcutsa, **CTRL** tuşuna basıldığını denetler.</span><span class="sxs-lookup"><span data-stu-id="2c63f-263">If the "Object" data is present, checks whether the **Ctrl** key is pressed.</span></span>

    - <span data-ttu-id="2c63f-264">**CTRL** tuşuna basıldığında <xref:System.Windows.DragEventArgs.Effects%2A> özelliğini olarak ayarlar <xref:System.Windows.DragDropEffects.Copy> .</span><span class="sxs-lookup"><span data-stu-id="2c63f-264">If the **Ctrl** key is pressed, sets the <xref:System.Windows.DragEventArgs.Effects%2A> property to <xref:System.Windows.DragDropEffects.Copy>.</span></span> <span data-ttu-id="2c63f-265">Aksi takdirde, <xref:System.Windows.DragEventArgs.Effects%2A> özelliğini olarak ayarlayın <xref:System.Windows.DragDropEffects.Move> .</span><span class="sxs-lookup"><span data-stu-id="2c63f-265">Otherwise, set the <xref:System.Windows.DragEventArgs.Effects%2A> property to <xref:System.Windows.DragDropEffects.Move>.</span></span>

5. <span data-ttu-id="2c63f-266">Olay işleyicisi için aşağıdaki kodu ekleyin <xref:System.Windows.UIElement.Drop> .</span><span class="sxs-lookup"><span data-stu-id="2c63f-266">Add the following code for the <xref:System.Windows.UIElement.Drop> event handler.</span></span>

     [!code-csharp[DragDropWalkthrough#PanelDrop](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml.cs#paneldrop)]
     [!code-vb[DragDropWalkthrough#PanelDrop](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/MainWindow.xaml.vb#paneldrop)]

     <span data-ttu-id="2c63f-267">Bu <xref:System.Windows.UIElement.Drop> olay işleyicisi aşağıdaki görevleri gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="2c63f-267">This <xref:System.Windows.UIElement.Drop> event handler performs the following tasks:</span></span>

    - <span data-ttu-id="2c63f-268"><xref:System.Windows.UIElement.Drop>Etkinliğin zaten işlenmiş olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="2c63f-268">Checks whether the <xref:System.Windows.UIElement.Drop> event has already been handled.</span></span> <span data-ttu-id="2c63f-269">Örneğin, bir daire olayı işleyen başka bir daire üzerinde bırakıldığında <xref:System.Windows.UIElement.Drop> , daireyi içeren panelin da işlenmesi için bu işleci istemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="2c63f-269">For instance, if a Circle is dropped on another Circle which handles the <xref:System.Windows.UIElement.Drop> event, you do not want the panel that contains the Circle to also handle it.</span></span>

    - <span data-ttu-id="2c63f-270"><xref:System.Windows.UIElement.Drop>Olay işlenmezse, **CTRL** tuşuna basıldığını denetler.</span><span class="sxs-lookup"><span data-stu-id="2c63f-270">If the <xref:System.Windows.UIElement.Drop> event is not handled, checks whether the **Ctrl** key is pressed.</span></span>

    - <span data-ttu-id="2c63f-271">Oluştuğunda **CTRL** tuşuna basıldığında <xref:System.Windows.UIElement.Drop> , daire denetiminin bir kopyasını oluşturur ve <xref:System.Windows.Controls.Panel.Children%2A> koleksiyonuna ekler <xref:System.Windows.Controls.StackPanel> .</span><span class="sxs-lookup"><span data-stu-id="2c63f-271">If the **Ctrl** key is pressed when the <xref:System.Windows.UIElement.Drop> happens, makes a copy of the Circle control and add it to the <xref:System.Windows.Controls.Panel.Children%2A> collection of the <xref:System.Windows.Controls.StackPanel>.</span></span>

    - <span data-ttu-id="2c63f-272">**CTRL** tuşuna basılsa, daireyi <xref:System.Windows.Controls.Panel.Children%2A> üst bölmesinin koleksiyonundan, <xref:System.Windows.Controls.Panel.Children%2A> üzerinde bırakılan panelin koleksiyonuna taşımış olur.</span><span class="sxs-lookup"><span data-stu-id="2c63f-272">If the **Ctrl** key is not pressed, moves the Circle from the <xref:System.Windows.Controls.Panel.Children%2A> collection of its parent panel to the <xref:System.Windows.Controls.Panel.Children%2A> collection of the panel that it was dropped on.</span></span>

    - <span data-ttu-id="2c63f-273">Yöntemi, <xref:System.Windows.DragEventArgs.Effects%2A> <xref:System.Windows.DragDrop.DoDragDrop%2A> bir taşıma veya kopyalama işleminin gerçekleştirilip gerçekleştirilmediğini bildirmek için özelliği ayarlar.</span><span class="sxs-lookup"><span data-stu-id="2c63f-273">Sets the <xref:System.Windows.DragEventArgs.Effects%2A> property to notify the <xref:System.Windows.DragDrop.DoDragDrop%2A> method whether a move or copy operation was performed.</span></span>

6. <span data-ttu-id="2c63f-274">Uygulamayı derlemek ve çalıştırmak için **F5** tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="2c63f-274">Press **F5** to build and run the application.</span></span>

7. <span data-ttu-id="2c63f-275">Öğesinden metni seçin `green` <xref:System.Windows.Controls.TextBox> .</span><span class="sxs-lookup"><span data-stu-id="2c63f-275">Select the text `green` from the <xref:System.Windows.Controls.TextBox>.</span></span>

8. <span data-ttu-id="2c63f-276">Metni bir daire denetiminin üzerine sürükleyin ve bırakın.</span><span class="sxs-lookup"><span data-stu-id="2c63f-276">Drag the text over a Circle control and drop it.</span></span>

9. <span data-ttu-id="2c63f-277">Sol panelden bir daire denetimini sağ panele sürükleyin ve bırakın.</span><span class="sxs-lookup"><span data-stu-id="2c63f-277">Drag a Circle control from the left panel to the right panel and drop it.</span></span> <span data-ttu-id="2c63f-278">Daire, <xref:System.Windows.Controls.Panel.Children%2A> sol bölmenin koleksiyonundan kaldırılır ve sağ bölmenin alt öğe koleksiyonuna eklenir.</span><span class="sxs-lookup"><span data-stu-id="2c63f-278">The Circle is removed from the <xref:System.Windows.Controls.Panel.Children%2A> collection of the left panel and added to the Children collection of the right panel.</span></span>

10. <span data-ttu-id="2c63f-279">Bir daire denetimini, içindeki panelden diğer panele sürükleyin ve **CTRL** tuşuna basarak bırakın.</span><span class="sxs-lookup"><span data-stu-id="2c63f-279">Drag a Circle control from the panel it is in to the other panel and drop it while pressing the **Ctrl** key.</span></span> <span data-ttu-id="2c63f-280">Daire kopyalanır ve kopya, <xref:System.Windows.Controls.Panel.Children%2A> alan paneli koleksiyonuna eklenir.</span><span class="sxs-lookup"><span data-stu-id="2c63f-280">The Circle is copied and the copy is added to the <xref:System.Windows.Controls.Panel.Children%2A> collection of the receiving panel.</span></span>

     <span data-ttu-id="2c63f-281">![CTRL tuşuna basıldığında bir daireyi sürükleme](./media/dragdrop-paneldrop.png "DragDrop_PanelDrop")</span><span class="sxs-lookup"><span data-stu-id="2c63f-281">![Dragging a Circle while pressing the CTRL key](./media/dragdrop-paneldrop.png "DragDrop_PanelDrop")</span></span>

## <a name="see-also"></a><span data-ttu-id="2c63f-282">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2c63f-282">See also</span></span>

- [<span data-ttu-id="2c63f-283">Sürükleme ve Bırakmaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="2c63f-283">Drag and Drop Overview</span></span>](drag-and-drop-overview.md)
