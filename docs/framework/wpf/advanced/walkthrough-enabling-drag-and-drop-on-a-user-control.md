---
title: 'İzlenecek yol: Kullanıcı Denetiminde Sürükleme ve Bırakmayı Etkinleştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- walkthrough [WPF], drag-and-drop
- drag-and-drop [WPF], walkthrough
ms.assetid: cc844419-1a77-4906-95d9-060d79107fc7
ms.openlocfilehash: 172e49c2c255db4d24d2180f919b1305326b5e82
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991805"
---
# <a name="walkthrough-enabling-drag-and-drop-on-a-user-control"></a><span data-ttu-id="7c778-102">İzlenecek yol: Kullanıcı Denetiminde Sürükleme ve Bırakmayı Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="7c778-102">Walkthrough: Enabling Drag and Drop on a User Control</span></span>

<span data-ttu-id="7c778-103">Bu izlenecek yol, ' de [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]sürükle ve bırak veri aktarımına katılabilen özel bir kullanıcı denetiminin nasıl oluşturulduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="7c778-103">This walkthrough demonstrates how to create a custom user control that can participate in drag-and-drop data transfer in [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].</span></span>

<span data-ttu-id="7c778-104">Bu izlenecek yolda, bir daire şeklini temsil eden özel <xref:System.Windows.Controls.UserControl> bir WPF oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="7c778-104">In this walkthrough, you will create a custom WPF <xref:System.Windows.Controls.UserControl> that represents a circle shape.</span></span> <span data-ttu-id="7c778-105">Sürükle ve bırak ile veri aktarımını etkinleştirmek için denetime işlevsellik uygulayacaksınız.</span><span class="sxs-lookup"><span data-stu-id="7c778-105">You will implement functionality on the control to enable data transfer through drag-and-drop.</span></span> <span data-ttu-id="7c778-106">Örneğin, bir daire denetiminden diğerine sürüklerseniz, Fill Color verileri kaynak çemberden hedefe kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="7c778-106">For example, if you drag from one Circle control to another, the Fill color data is copied from the source Circle to the target.</span></span> <span data-ttu-id="7c778-107">Bir daire denetiminden öğesine <xref:System.Windows.Controls.TextBox>sürüklerseniz, Fill renginin dize temsili <xref:System.Windows.Controls.TextBox>öğesine kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="7c778-107">If you drag from a Circle control to a <xref:System.Windows.Controls.TextBox>, the string representation of the Fill color is copied to the <xref:System.Windows.Controls.TextBox>.</span></span> <span data-ttu-id="7c778-108">Ayrıca, sürükle ve bırak işlevlerini test <xref:System.Windows.Controls.TextBox> etmek için iki panel denetimi içeren küçük bir uygulama da oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="7c778-108">You will also create a small application that contains two panel controls and a <xref:System.Windows.Controls.TextBox> to test the drag-and-drop functionality.</span></span> <span data-ttu-id="7c778-109">Panellerin bırakılan daire verilerini işlemesini sağlayan bir kod yazacaksınız. Bu, bir panelin alt öğe koleksiyonundan daireler taşımanızı veya kopyalamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="7c778-109">You will write code that enables the panels to process dropped Circle data, which will enable you to move or copy Circles from the Children collection of one panel to the other.</span></span>

<span data-ttu-id="7c778-110">Bu izlenecek yol aşağıdaki görevleri gösterir:</span><span class="sxs-lookup"><span data-stu-id="7c778-110">This walkthrough illustrates the following tasks:</span></span>

- <span data-ttu-id="7c778-111">Özel Kullanıcı denetimi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="7c778-111">Create a custom user control.</span></span>

- <span data-ttu-id="7c778-112">Kullanıcı denetimini Sürükle kaynağı olacak şekilde etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="7c778-112">Enable the user control to be a drag source.</span></span>

- <span data-ttu-id="7c778-113">Kullanıcı denetiminin bir bırakma hedefi olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="7c778-113">Enable the user control to be a drop target.</span></span>

- <span data-ttu-id="7c778-114">Kullanıcı denetiminden bırakılan verileri almak için bir paneli etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="7c778-114">Enable a panel to receive data dropped from the user control.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="7c778-115">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="7c778-115">Prerequisites</span></span>

<span data-ttu-id="7c778-116">Bu yönergeyi tamamlamak için Visual Studio gerekir.</span><span class="sxs-lookup"><span data-stu-id="7c778-116">You need Visual Studio to complete this walkthrough.</span></span>

## <a name="create-the-application-project"></a><span data-ttu-id="7c778-117">Uygulama projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="7c778-117">Create the Application Project</span></span>
 <span data-ttu-id="7c778-118">Bu bölümde, iki panel ve <xref:System.Windows.Controls.TextBox>içeren bir ana sayfa içeren uygulama altyapısını oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="7c778-118">In this section, you will create the application infrastructure, which includes a main page with two panels and a <xref:System.Windows.Controls.TextBox>.</span></span>

1. <span data-ttu-id="7c778-119">Visual Basic veya görsel C# adında `DragDropExample`yeni bir WPF uygulama projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="7c778-119">Create a new WPF Application project in Visual Basic or Visual C# named `DragDropExample`.</span></span> <span data-ttu-id="7c778-120">Daha fazla bilgi için bkz [. İzlenecek yol: İlk WPF Masaüstü](../getting-started/walkthrough-my-first-wpf-desktop-application.md)Uygulamam.</span><span class="sxs-lookup"><span data-stu-id="7c778-120">For more information, see [Walkthrough: My first WPF desktop application](../getting-started/walkthrough-my-first-wpf-desktop-application.md).</span></span>

2. <span data-ttu-id="7c778-121">MainWindow. xaml ' i açın.</span><span class="sxs-lookup"><span data-stu-id="7c778-121">Open MainWindow.xaml.</span></span>

3. <span data-ttu-id="7c778-122">Açılış ve kapanış <xref:System.Windows.Controls.Grid> etiketleri arasına aşağıdaki biçimlendirmeyi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="7c778-122">Add the following markup between the opening and closing <xref:System.Windows.Controls.Grid> tags.</span></span>

     <span data-ttu-id="7c778-123">Bu biçimlendirme, test uygulaması için Kullanıcı arabirimi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7c778-123">This markup creates the user interface for the test application.</span></span>

     [!code-xaml[DragDropWalkthrough#PanelsStep1XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#panelsstep1xaml)]

## <a name="add-a-new-user-control-to-the-project"></a><span data-ttu-id="7c778-124">Projeye yeni bir kullanıcı denetimi Ekle</span><span class="sxs-lookup"><span data-stu-id="7c778-124">Add a New User Control to the Project</span></span>
 <span data-ttu-id="7c778-125">Bu bölümde, projeye yeni bir kullanıcı denetimi ekleyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="7c778-125">In this section, you will add a new user control to the project.</span></span>

1. <span data-ttu-id="7c778-126">Proje menüsünde **Kullanıcı denetimi Ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="7c778-126">On the Project menu, select **Add User Control**.</span></span>

2. <span data-ttu-id="7c778-127">**Yeni öğe Ekle** iletişim kutusunda, adı olarak `Circle.xaml`değiştirin ve **Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="7c778-127">In the **Add New Item** dialog box, change the name to `Circle.xaml`, and click **Add**.</span></span>

     <span data-ttu-id="7c778-128">Circle. xaml ve arka plan kodu projeye eklenir.</span><span class="sxs-lookup"><span data-stu-id="7c778-128">Circle.xaml and its code-behind is added to the project.</span></span>

3. <span data-ttu-id="7c778-129">Circle. xaml açın.</span><span class="sxs-lookup"><span data-stu-id="7c778-129">Open Circle.xaml.</span></span>

     <span data-ttu-id="7c778-130">Bu dosya, Kullanıcı denetiminin Kullanıcı arabirimi öğelerini içerir.</span><span class="sxs-lookup"><span data-stu-id="7c778-130">This file will contain the user interface elements of the user control.</span></span>

4. <span data-ttu-id="7c778-131">Kullanıcı arabirimi olarak mavi bir daire bulunan <xref:System.Windows.Controls.Grid> basit bir kullanıcı denetimi oluşturmak için aşağıdaki biçimlendirmeyi köke ekleyin.</span><span class="sxs-lookup"><span data-stu-id="7c778-131">Add the following markup to the root <xref:System.Windows.Controls.Grid> to create a simple user control that has a blue circle as its UI.</span></span>

     [!code-xaml[DragDropWalkthrough#EllipseXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml#ellipsexaml)]

5. <span data-ttu-id="7c778-132">Open Circle.xaml.cs veya Circle. xaml. vb.</span><span class="sxs-lookup"><span data-stu-id="7c778-132">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>

6. <span data-ttu-id="7c778-133">İçinde C#, bir kopya Oluşturucu oluşturmak için parametresiz oluşturucudan sonra aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="7c778-133">In C#, add the following code after the parameterless constructor to create a copy constructor.</span></span> <span data-ttu-id="7c778-134">Visual Basic, hem parametresiz bir Oluşturucu hem de kopya Oluşturucu oluşturmak için aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="7c778-134">In Visual Basic, add the following code to create both a parameterless constructor and a copy constructor.</span></span>

     <span data-ttu-id="7c778-135">Kullanıcı denetiminin kopyalanmasına izin vermek için, arka plan kod dosyasına bir kopya Oluşturucu yöntemi eklersiniz.</span><span class="sxs-lookup"><span data-stu-id="7c778-135">In order to allow the user control to be copied, you add a copy constructor method in the code-behind file.</span></span> <span data-ttu-id="7c778-136">Basitleştirilmiş daire Kullanıcı denetiminde, yalnızca Kullanıcı denetiminin dolgusunu ve boyutunu kopyalayacaksınız.</span><span class="sxs-lookup"><span data-stu-id="7c778-136">In the simplified Circle user control, you will only copy the Fill and the size of the of the user control.</span></span>

     [!code-csharp[DragDropWalkthrough#CopyCtor](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#copyctor)]
     [!code-vb[DragDropWalkthrough#CopyCtor](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#copyctor)]

## <a name="add-the-user-control-to-the-main-window"></a><span data-ttu-id="7c778-137">Kullanıcı denetimini ana pencereye ekleme</span><span class="sxs-lookup"><span data-stu-id="7c778-137">Add the user control to the main window</span></span>

1. <span data-ttu-id="7c778-138">MainWindow. xaml ' i açın.</span><span class="sxs-lookup"><span data-stu-id="7c778-138">Open MainWindow.xaml.</span></span>

2. <span data-ttu-id="7c778-139">Geçerli uygulamaya bir XML ad alanı başvurusu <xref:System.Windows.Window> oluşturmak için aşağıdaki xaml 'yi açılış etiketine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="7c778-139">Add the following XAML to the opening <xref:System.Windows.Window> tag to create an XML namespace reference to the current application.</span></span>

    ```xaml
    xmlns:local="clr-namespace:DragDropExample"
    ```

3. <span data-ttu-id="7c778-140">İlk panelde, <xref:System.Windows.Controls.StackPanel>Circle Kullanıcı denetiminin iki örneğini oluşturmak için önce aşağıdaki xaml 'yi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="7c778-140">In the first <xref:System.Windows.Controls.StackPanel>, add the following XAML to create two instances of the Circle user control in the first panel.</span></span>

     [!code-xaml[DragDropWalkthrough#CirclesXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#circlesxaml)]

     <span data-ttu-id="7c778-141">Panelin tam XAML aşağıdaki gibi görünür.</span><span class="sxs-lookup"><span data-stu-id="7c778-141">The full XAML for the panel looks like the following.</span></span>

     [!code-xaml[DragDropWalkthrough#PanelsStep2XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#panelsstep2xaml)]

## <a name="implement-drag-source-events-in-the-user-control"></a><span data-ttu-id="7c778-142">Kullanıcı denetimindeki Sürükle kaynak olaylarını Uygula</span><span class="sxs-lookup"><span data-stu-id="7c778-142">Implement Drag Source Events in the User Control</span></span>
 <span data-ttu-id="7c778-143">Bu bölümde, <xref:System.Windows.UIElement.OnMouseMove%2A> yöntemi geçersiz kılacak ve sürükle ve bırak işlemini başlatacaksınız.</span><span class="sxs-lookup"><span data-stu-id="7c778-143">In this section, you will override the <xref:System.Windows.UIElement.OnMouseMove%2A> method and initiate the drag-and-drop operation.</span></span>

 <span data-ttu-id="7c778-144">Bir sürükleme başlatılırsa (bir fare düğmesine basıldığında ve fare taşındığında), verileri bir <xref:System.Windows.DataObject>içine aktarılacak şekilde paketleyecaksınız.</span><span class="sxs-lookup"><span data-stu-id="7c778-144">If a drag is started (a mouse button is pressed and the mouse is moved), you will package the data to be transferred into a <xref:System.Windows.DataObject>.</span></span> <span data-ttu-id="7c778-145">Bu durumda, Circle denetimi üç veri öğesini paketleyebilir; kendi renk gösterimi ve kendi bir kopyası olan Fill Color dize gösterimi.</span><span class="sxs-lookup"><span data-stu-id="7c778-145">In this case, the Circle control will package three data items; a string representation of its Fill color, a double representation of its height, and a copy of itself.</span></span>

### <a name="to-initiate-a-drag-and-drop-operation"></a><span data-ttu-id="7c778-146">Sürükle ve bırak işlemini başlatmak için</span><span class="sxs-lookup"><span data-stu-id="7c778-146">To initiate a drag-and-drop operation</span></span>

1. <span data-ttu-id="7c778-147">Open Circle.xaml.cs veya Circle. xaml. vb.</span><span class="sxs-lookup"><span data-stu-id="7c778-147">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>

2. <span data-ttu-id="7c778-148">Olay için sınıf <xref:System.Windows.UIElement.OnMouseMove%2A> işleme sağlamak için aşağıdaki geçersiz kılmayı ekleyin. <xref:System.Windows.UIElement.MouseMove></span><span class="sxs-lookup"><span data-stu-id="7c778-148">Add the following <xref:System.Windows.UIElement.OnMouseMove%2A> override to provide class handling for the <xref:System.Windows.UIElement.MouseMove> event.</span></span>

     [!code-csharp[DragDropWalkthrough#OnMouseMove](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#onmousemove)]
     [!code-vb[DragDropWalkthrough#OnMouseMove](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#onmousemove)]

     <span data-ttu-id="7c778-149">Bu <xref:System.Windows.UIElement.OnMouseMove%2A> geçersiz kılma aşağıdaki görevleri gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="7c778-149">This <xref:System.Windows.UIElement.OnMouseMove%2A> override performs the following tasks:</span></span>

    - <span data-ttu-id="7c778-150">Fare hareket ettirirken sol fare düğmesine basıldığını denetler.</span><span class="sxs-lookup"><span data-stu-id="7c778-150">Checks whether the left mouse button is pressed while the mouse is moving.</span></span>

    - <span data-ttu-id="7c778-151">Daire verisini bir <xref:System.Windows.DataObject>olarak paketler.</span><span class="sxs-lookup"><span data-stu-id="7c778-151">Packages the Circle data into a <xref:System.Windows.DataObject>.</span></span> <span data-ttu-id="7c778-152">Bu durumda, daire denetimi üç veri öğesini paketler; kendi renk gösterimi ve kendi bir kopyası olan Fill Color dize gösterimi.</span><span class="sxs-lookup"><span data-stu-id="7c778-152">In this case, the Circle control packages three data items; a string representation of its Fill color, a double representation of its height, and a copy of itself.</span></span>

    - <span data-ttu-id="7c778-153">Sürükle ve bırak <xref:System.Windows.DragDrop.DoDragDrop%2A?displayProperty=nameWithType> işlemini başlatmak için statik yöntemi çağırır.</span><span class="sxs-lookup"><span data-stu-id="7c778-153">Calls the static <xref:System.Windows.DragDrop.DoDragDrop%2A?displayProperty=nameWithType> method to initiate the drag-and-drop operation.</span></span> <span data-ttu-id="7c778-154">Aşağıdaki üç parametreyi <xref:System.Windows.DragDrop.DoDragDrop%2A> yöntemine geçirirsiniz:</span><span class="sxs-lookup"><span data-stu-id="7c778-154">You pass the following three parameters to the <xref:System.Windows.DragDrop.DoDragDrop%2A> method:</span></span>

        - <span data-ttu-id="7c778-155">`dragSource`– Bu denetime bir başvuru.</span><span class="sxs-lookup"><span data-stu-id="7c778-155">`dragSource` – A reference to this control.</span></span>

        - <span data-ttu-id="7c778-156">`data`– Önceki kodda oluşturulur. <xref:System.Windows.DataObject></span><span class="sxs-lookup"><span data-stu-id="7c778-156">`data` – The <xref:System.Windows.DataObject> created in the previous code.</span></span>

        - <span data-ttu-id="7c778-157">`allowedEffects`– Veya <xref:System.Windows.DragDropEffects.Copy> <xref:System.Windows.DragDropEffects.Move>olan izin verilen sürükle ve bırak işlemleri.</span><span class="sxs-lookup"><span data-stu-id="7c778-157">`allowedEffects` – The allowed drag-and-drop operations, which are <xref:System.Windows.DragDropEffects.Copy> or <xref:System.Windows.DragDropEffects.Move>.</span></span>

3. <span data-ttu-id="7c778-158">Uygulamayı derlemek ve çalıştırmak için **F5** tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="7c778-158">Press **F5** to build and run the application.</span></span>

4. <span data-ttu-id="7c778-159">Daire denetimlerinden birine tıklayın ve panelleri, diğer daireyi ve <xref:System.Windows.Controls.TextBox>' nin üzerine sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="7c778-159">Click one of the Circle controls and drag it over the panels, the other Circle, and the <xref:System.Windows.Controls.TextBox>.</span></span> <span data-ttu-id="7c778-160">Üzerinde sürükleme yaparken <xref:System.Windows.Controls.TextBox>, imleç bir taşımayı belirtecek şekilde değişir.</span><span class="sxs-lookup"><span data-stu-id="7c778-160">When dragging over the <xref:System.Windows.Controls.TextBox>, the cursor changes to indicate a move.</span></span>

5. <span data-ttu-id="7c778-161">Bir daireyi üzerine <xref:System.Windows.Controls.TextBox>sürüklerken **CTRL** tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="7c778-161">While dragging a Circle over the <xref:System.Windows.Controls.TextBox>, press the **Ctrl** key.</span></span> <span data-ttu-id="7c778-162">İmlecin bir kopyayı göstermek için nasıl değiştiği hakkında dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="7c778-162">Notice how the cursor changes to indicate a copy.</span></span>

6. <span data-ttu-id="7c778-163">Üzerine bir daire sürükleyip bırakın <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="7c778-163">Drag and drop a Circle onto the <xref:System.Windows.Controls.TextBox>.</span></span> <span data-ttu-id="7c778-164">Dairenin dolgusu renginin dize temsili öğesine <xref:System.Windows.Controls.TextBox>eklenir.</span><span class="sxs-lookup"><span data-stu-id="7c778-164">The string representation of the Circle’s fill color is appended to the <xref:System.Windows.Controls.TextBox>.</span></span>

     <span data-ttu-id="7c778-165">![Dairenin dolgusu renginin dize temsili](./media/dragdrop-colorstring.png "DragDrop_ColorString")</span><span class="sxs-lookup"><span data-stu-id="7c778-165">![String representation of Circle's fill color](./media/dragdrop-colorstring.png "DragDrop_ColorString")</span></span>

<span data-ttu-id="7c778-166">Varsayılan olarak, imleç bir sürükle ve bırak işlemi sırasında, verilerin hangi etkiyle sonuçlandığını belirten şekilde değişir.</span><span class="sxs-lookup"><span data-stu-id="7c778-166">By default, the cursor will change during a drag-and-drop operation to indicate what effect dropping the data will have.</span></span> <span data-ttu-id="7c778-167"><xref:System.Windows.UIElement.GiveFeedback> Olayı işleyerek ve farklı bir imleç ayarlayarak kullanıcıya verilen geri bildirimleri özelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7c778-167">You can customize the feedback given to the user by handling the <xref:System.Windows.UIElement.GiveFeedback> event and setting a different cursor.</span></span>

## <a name="give-feedback-to-the-user"></a><span data-ttu-id="7c778-168">Kullanıcıya geri bildirimde bulunun</span><span class="sxs-lookup"><span data-stu-id="7c778-168">Give feedback to the user</span></span>

1. <span data-ttu-id="7c778-169">Open Circle.xaml.cs veya Circle. xaml. vb.</span><span class="sxs-lookup"><span data-stu-id="7c778-169">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>

2. <span data-ttu-id="7c778-170">Olay için sınıf <xref:System.Windows.UIElement.OnGiveFeedback%2A> işleme sağlamak için aşağıdaki geçersiz kılmayı ekleyin. <xref:System.Windows.UIElement.GiveFeedback></span><span class="sxs-lookup"><span data-stu-id="7c778-170">Add the following <xref:System.Windows.UIElement.OnGiveFeedback%2A> override to provide class handling for the <xref:System.Windows.UIElement.GiveFeedback> event.</span></span>

     [!code-csharp[DragDropWalkthrough#OnGiveFeedback](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ongivefeedback)]
     [!code-vb[DragDropWalkthrough#OnGiveFeedback](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ongivefeedback)]

     <span data-ttu-id="7c778-171">Bu <xref:System.Windows.UIElement.OnGiveFeedback%2A> geçersiz kılma aşağıdaki görevleri gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="7c778-171">This <xref:System.Windows.UIElement.OnGiveFeedback%2A> override performs the following tasks:</span></span>

    - <span data-ttu-id="7c778-172">Bırakma hedefinin olay işleyicisinde ayarlanan <xref:System.Windows.GiveFeedbackEventArgs.Effects%2A> <xref:System.Windows.UIElement.DragOver> değerleri denetler.</span><span class="sxs-lookup"><span data-stu-id="7c778-172">Checks the <xref:System.Windows.GiveFeedbackEventArgs.Effects%2A> values that are set in the drop target's <xref:System.Windows.UIElement.DragOver> event handler.</span></span>

    - <span data-ttu-id="7c778-173"><xref:System.Windows.GiveFeedbackEventArgs.Effects%2A> Değere göre özel bir imleç ayarlar.</span><span class="sxs-lookup"><span data-stu-id="7c778-173">Sets a custom cursor based on the <xref:System.Windows.GiveFeedbackEventArgs.Effects%2A> value.</span></span> <span data-ttu-id="7c778-174">İmlecin, kullanıcıya verilerin ne kadar yürürlükte olacağı hakkında görsel geri bildirim vermesi amaçlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="7c778-174">The cursor is intended to give visual feedback to the user about what effect dropping the data will have.</span></span>

3. <span data-ttu-id="7c778-175">Uygulamayı derlemek ve çalıştırmak için **F5** tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="7c778-175">Press **F5** to build and run the application.</span></span>

4. <span data-ttu-id="7c778-176">Panel, diğer daire ve için <xref:System.Windows.Controls.TextBox>daire denetimlerinden birini sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="7c778-176">Drag one of the Circle controls over the panels, the other Circle, and the <xref:System.Windows.Controls.TextBox>.</span></span> <span data-ttu-id="7c778-177">İmleçlerin artık <xref:System.Windows.UIElement.OnGiveFeedback%2A> geçersiz kılmada belirttiğiniz özel imleçler olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="7c778-177">Notice that the cursors are now the custom cursors that you specified in the <xref:System.Windows.UIElement.OnGiveFeedback%2A> override.</span></span>

     <span data-ttu-id="7c778-178">![Özel imleçlerle sürükleyip bırakma](./media/dragdrop-customcursor.png "DragDrop_CustomCursor")</span><span class="sxs-lookup"><span data-stu-id="7c778-178">![Drag and drop with custom cursors](./media/dragdrop-customcursor.png "DragDrop_CustomCursor")</span></span>

5. <span data-ttu-id="7c778-179">Öğesinden metni `green`seçin. <xref:System.Windows.Controls.TextBox></span><span class="sxs-lookup"><span data-stu-id="7c778-179">Select the text `green` from the <xref:System.Windows.Controls.TextBox>.</span></span>

6. <span data-ttu-id="7c778-180">`green` Metni bir daire denetimine sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="7c778-180">Drag the `green` text to a Circle control.</span></span> <span data-ttu-id="7c778-181">Sürükle ve bırak işleminin etkilerini belirtmek için varsayılan imleçlerin gösterildiğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="7c778-181">Notice that the default cursors are shown to indicate the effects of the drag-and-drop operation.</span></span> <span data-ttu-id="7c778-182">Geri bildirim imleci her zaman Sürükle kaynağı tarafından ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="7c778-182">The feedback cursor is always set by the drag source.</span></span>

## <a name="implement-drop-target-events-in-the-user-control"></a><span data-ttu-id="7c778-183">Kullanıcı denetiminde bırakma hedefi olaylarını uygulama</span><span class="sxs-lookup"><span data-stu-id="7c778-183">Implement Drop Target Events in the User Control</span></span>
 <span data-ttu-id="7c778-184">Bu bölümde, Kullanıcı denetiminin bir bırakma hedefi olduğunu, Kullanıcı denetiminin bir bırakma hedefi olmasını sağlayan yöntemleri geçersiz kılacaksınız ve üzerinde bırakılan verileri işleyecek şekilde belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7c778-184">In this section, you will specify that the user control is a drop target, override the methods that enable the user control to be a drop target, and process the data that is dropped on it.</span></span>

### <a name="to-enable-the-user-control-to-be-a-drop-target"></a><span data-ttu-id="7c778-185">Kullanıcı denetiminin bir bırakma hedefi olmasını sağlamak için</span><span class="sxs-lookup"><span data-stu-id="7c778-185">To enable the user control to be a drop target</span></span>

1. <span data-ttu-id="7c778-186">Circle. xaml açın.</span><span class="sxs-lookup"><span data-stu-id="7c778-186">Open Circle.xaml.</span></span>

2. <span data-ttu-id="7c778-187">Açma <xref:System.Windows.Controls.UserControl> etiketinde <xref:System.Windows.UIElement.AllowDrop%2A> özelliği ekleyin ve olarak `true`ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="7c778-187">In the opening <xref:System.Windows.Controls.UserControl> tag, add the <xref:System.Windows.UIElement.AllowDrop%2A> property and set it to `true`.</span></span>

     [!code-xaml[DragDropWalkthrough#UCTagXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml#uctagxaml)]

<span data-ttu-id="7c778-188">Yöntemi, <xref:System.Windows.UIElement.AllowDrop%2A> özelliği olarak`true` ayarlandığında ve sürükleme kaynağındaki veriler daire Kullanıcı denetiminde bırakıldığında çağrılır. <xref:System.Windows.UIElement.OnDrop%2A></span><span class="sxs-lookup"><span data-stu-id="7c778-188">The <xref:System.Windows.UIElement.OnDrop%2A> method is called when the <xref:System.Windows.UIElement.AllowDrop%2A> property is set to `true` and data from the drag source is dropped on the Circle user control.</span></span> <span data-ttu-id="7c778-189">Bu yöntemde, bırakılan verileri işleyecek ve verileri daireye uygulamanız gerekecektir.</span><span class="sxs-lookup"><span data-stu-id="7c778-189">In this method, you will process the data that was dropped and apply the data to the Circle.</span></span>

### <a name="to-process-the-dropped-data"></a><span data-ttu-id="7c778-190">Bırakılan verileri işlemek için</span><span class="sxs-lookup"><span data-stu-id="7c778-190">To process the dropped data</span></span>

1. <span data-ttu-id="7c778-191">Open Circle.xaml.cs veya Circle. xaml. vb.</span><span class="sxs-lookup"><span data-stu-id="7c778-191">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>

2. <span data-ttu-id="7c778-192">Olay için sınıf <xref:System.Windows.UIElement.OnDrop%2A> işleme sağlamak için aşağıdaki geçersiz kılmayı ekleyin. <xref:System.Windows.UIElement.Drop></span><span class="sxs-lookup"><span data-stu-id="7c778-192">Add the following <xref:System.Windows.UIElement.OnDrop%2A> override to provide class handling for the <xref:System.Windows.UIElement.Drop> event.</span></span>

     [!code-csharp[DragDropWalkthrough#OnDrop](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondrop)]
     [!code-vb[DragDropWalkthrough#OnDrop](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondrop)]

     <span data-ttu-id="7c778-193">Bu <xref:System.Windows.UIElement.OnDrop%2A> geçersiz kılma aşağıdaki görevleri gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="7c778-193">This <xref:System.Windows.UIElement.OnDrop%2A> override performs the following tasks:</span></span>

    - <span data-ttu-id="7c778-194">, Sürüklenen verilerin bir dize nesnesi içerip içermediğinden emin olmak için yönteminikullanır.<xref:System.Windows.DataObject.GetDataPresent%2A></span><span class="sxs-lookup"><span data-stu-id="7c778-194">Uses the <xref:System.Windows.DataObject.GetDataPresent%2A> method to check if the dragged data contains a string object.</span></span>

    - <span data-ttu-id="7c778-195">, Varsa dize verilerini ayıklamak için yönteminikullanır.<xref:System.Windows.DataObject.GetData%2A></span><span class="sxs-lookup"><span data-stu-id="7c778-195">Uses the <xref:System.Windows.DataObject.GetData%2A> method to extract the string data if it is present.</span></span>

    - <span data-ttu-id="7c778-196">Dizeyi öğesine dönüştürmeyi denemek <xref:System.Windows.Media.BrushConverter> için öğesini kullanır <xref:System.Windows.Media.Brush>.</span><span class="sxs-lookup"><span data-stu-id="7c778-196">Uses a <xref:System.Windows.Media.BrushConverter> to try to convert the string to a <xref:System.Windows.Media.Brush>.</span></span>

    - <span data-ttu-id="7c778-197">Dönüştürme başarılı olursa, ' <xref:System.Windows.Shapes.Shape.Fill%2A> <xref:System.Windows.Shapes.Ellipse> nin, daire denetiminin Kullanıcı arabirimini sağlayan öğesine fırça uygular.</span><span class="sxs-lookup"><span data-stu-id="7c778-197">If the conversion is successful, applies the brush to the <xref:System.Windows.Shapes.Shape.Fill%2A> of the <xref:System.Windows.Shapes.Ellipse> that provides the UI of the Circle control.</span></span>

    - <span data-ttu-id="7c778-198"><xref:System.Windows.UIElement.Drop> Olayı işlenmiş olarak işaretler.</span><span class="sxs-lookup"><span data-stu-id="7c778-198">Marks the <xref:System.Windows.UIElement.Drop> event as handled.</span></span> <span data-ttu-id="7c778-199">Bu olayı alan diğer öğelerin, Circle Kullanıcı denetiminin bunu ele aldığından emin olmak için bırakma olayını işlenmiş olarak işaretlemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="7c778-199">You should mark the drop event as handled so that other elements that receive this event know that the Circle user control handled it.</span></span>

3. <span data-ttu-id="7c778-200">Uygulamayı derlemek ve çalıştırmak için **F5** tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="7c778-200">Press **F5** to build and run the application.</span></span>

4. <span data-ttu-id="7c778-201">İçindeki metni `green`seçin. <xref:System.Windows.Controls.TextBox></span><span class="sxs-lookup"><span data-stu-id="7c778-201">Select the text `green` in the <xref:System.Windows.Controls.TextBox>.</span></span>

5. <span data-ttu-id="7c778-202">Metni bir daire denetimine sürükleyin ve bırakın.</span><span class="sxs-lookup"><span data-stu-id="7c778-202">Drag the text to a Circle control and drop it.</span></span> <span data-ttu-id="7c778-203">Daire mavi ile yeşil arasında değişir.</span><span class="sxs-lookup"><span data-stu-id="7c778-203">The Circle changes from blue to green.</span></span>

     <span data-ttu-id="7c778-204">![Bir dizeyi fırçaya Dönüştür](./media/dragdrop-dropgreentext.png "DragDrop_DropGreenText")</span><span class="sxs-lookup"><span data-stu-id="7c778-204">![Convert a string to a brush](./media/dragdrop-dropgreentext.png "DragDrop_DropGreenText")</span></span>

6. <span data-ttu-id="7c778-205">`green` Metni<xref:System.Windows.Controls.TextBox>içine yazın.</span><span class="sxs-lookup"><span data-stu-id="7c778-205">Type the text `green` in the <xref:System.Windows.Controls.TextBox>.</span></span>

7. <span data-ttu-id="7c778-206">İçindeki metni `gre`seçin. <xref:System.Windows.Controls.TextBox></span><span class="sxs-lookup"><span data-stu-id="7c778-206">Select the text `gre` in the <xref:System.Windows.Controls.TextBox>.</span></span>

8. <span data-ttu-id="7c778-207">Bir daire denetimine sürükleyin ve bırakın.</span><span class="sxs-lookup"><span data-stu-id="7c778-207">Drag it to a Circle control and drop it.</span></span> <span data-ttu-id="7c778-208">İmlecin, bırakmaya izin verildiğini belirtmek için değiştiği, ancak dairenin rengi geçerli bir renk olmadığından, bu değişikliğin değişmediğine `gre` dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="7c778-208">Notice that the cursor changes to indicate that the drop is allowed, but the color of the Circle does not change because `gre` is not a valid color.</span></span>

9. <span data-ttu-id="7c778-209">Yeşil daire denetiminden sürükleyin ve mavi daire denetiminin üzerine bırakın.</span><span class="sxs-lookup"><span data-stu-id="7c778-209">Drag from the green Circle control and drop on the blue Circle control.</span></span> <span data-ttu-id="7c778-210">Daire mavi ile yeşil arasında değişir.</span><span class="sxs-lookup"><span data-stu-id="7c778-210">The Circle changes from blue to green.</span></span> <span data-ttu-id="7c778-211">Hangi imlecin gösterildiğine dikkat edin, ya da <xref:System.Windows.Controls.TextBox> dairenin Sürükle kaynağı olup olmamasına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="7c778-211">Notice that which cursor is shown depends on whether the <xref:System.Windows.Controls.TextBox> or the Circle is the drag source.</span></span>

<span data-ttu-id="7c778-212">Özelliği bırakılan verileri olarak `true` ayarlamak ve işlemek bir öğenin bir bırakma hedefi olmasını sağlamak için gereklidir. <xref:System.Windows.UIElement.AllowDrop%2A></span><span class="sxs-lookup"><span data-stu-id="7c778-212">Setting the <xref:System.Windows.UIElement.AllowDrop%2A> property to `true` and processing the dropped data is all that is required to enable an element to be a drop target.</span></span> <span data-ttu-id="7c778-213">Ancak, daha iyi bir kullanıcı deneyimi sağlamak için,, ve <xref:System.Windows.UIElement.DragEnter> <xref:System.Windows.UIElement.DragOver> olaylarını da işlemeniz <xref:System.Windows.UIElement.DragLeave>gerekir.</span><span class="sxs-lookup"><span data-stu-id="7c778-213">However, to provide a better user experience, you should also handle the <xref:System.Windows.UIElement.DragEnter>, <xref:System.Windows.UIElement.DragLeave>, and <xref:System.Windows.UIElement.DragOver> events.</span></span> <span data-ttu-id="7c778-214">Bu olaylarda, denetimler gerçekleştirebilir ve veriler kesilmeden önce kullanıcıya ek geri bildirim sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7c778-214">In these events, you can perform checks and provide additional feedback to the user before the data is dropped.</span></span>

<span data-ttu-id="7c778-215">Veriler, Circle Kullanıcı denetiminin üzerine sürüklendiğinde denetim, sürüklenen verileri işleip işleyemeyeceğini, sürükleme kaynağını bilgilendirmelidir.</span><span class="sxs-lookup"><span data-stu-id="7c778-215">When data is dragged over the Circle user control, the control should notify the drag source whether it can process the data that is being dragged.</span></span> <span data-ttu-id="7c778-216">Denetim, verilerin nasıl işleyeceğini bilmez ise, bırakmayı reddetmelidir.</span><span class="sxs-lookup"><span data-stu-id="7c778-216">If the control does not know how to process the data, it should refuse the drop.</span></span> <span data-ttu-id="7c778-217">Bunu yapmak için, <xref:System.Windows.UIElement.DragOver> olayı işleyecek ve <xref:System.Windows.DragEventArgs.Effects%2A> özelliğini ayarlayacaksınız.</span><span class="sxs-lookup"><span data-stu-id="7c778-217">To do this, you will handle the <xref:System.Windows.UIElement.DragOver> event and set the <xref:System.Windows.DragEventArgs.Effects%2A> property.</span></span>

### <a name="to-verify-that-the-data-drop-is-allowed"></a><span data-ttu-id="7c778-218">Veri bırakmaya izin verildiğini doğrulamak için</span><span class="sxs-lookup"><span data-stu-id="7c778-218">To verify that the data drop is allowed</span></span>

1. <span data-ttu-id="7c778-219">Open Circle.xaml.cs veya Circle. xaml. vb.</span><span class="sxs-lookup"><span data-stu-id="7c778-219">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>

2. <span data-ttu-id="7c778-220">Olay için sınıf <xref:System.Windows.UIElement.OnDragOver%2A> işleme sağlamak için aşağıdaki geçersiz kılmayı ekleyin. <xref:System.Windows.UIElement.DragOver></span><span class="sxs-lookup"><span data-stu-id="7c778-220">Add the following <xref:System.Windows.UIElement.OnDragOver%2A> override to provide class handling for the <xref:System.Windows.UIElement.DragOver> event.</span></span>

     [!code-csharp[DragDropWalkthrough#OnDragOver](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragover)]
     [!code-vb[DragDropWalkthrough#OnDragOver](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragover)]

     <span data-ttu-id="7c778-221">Bu <xref:System.Windows.UIElement.OnDragOver%2A> geçersiz kılma aşağıdaki görevleri gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="7c778-221">This <xref:System.Windows.UIElement.OnDragOver%2A> override performs the following tasks:</span></span>

    - <span data-ttu-id="7c778-222"><xref:System.Windows.DragEventArgs.Effects%2A> Özelliğini olarak<xref:System.Windows.DragDropEffects.None>ayarlar.</span><span class="sxs-lookup"><span data-stu-id="7c778-222">Sets the <xref:System.Windows.DragEventArgs.Effects%2A> property to <xref:System.Windows.DragDropEffects.None>.</span></span>

    - <span data-ttu-id="7c778-223">Circle Kullanıcı denetiminin sürüklenen verileri işleyemeyeceğini anlamak için <xref:System.Windows.UIElement.OnDrop%2A> yönteminde gerçekleştirilen denetimleri gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="7c778-223">Performs the same checks that are performed in the <xref:System.Windows.UIElement.OnDrop%2A> method to determine whether the Circle user control can process the dragged data.</span></span>

    - <span data-ttu-id="7c778-224">Kullanıcı denetimi verileri işleyebiliyorsanız, <xref:System.Windows.DragEventArgs.Effects%2A> özelliğini veya <xref:System.Windows.DragDropEffects.Move>olarak <xref:System.Windows.DragDropEffects.Copy> ayarlar.</span><span class="sxs-lookup"><span data-stu-id="7c778-224">If the user control can process the data, sets the <xref:System.Windows.DragEventArgs.Effects%2A> property to <xref:System.Windows.DragDropEffects.Copy> or <xref:System.Windows.DragDropEffects.Move>.</span></span>

3. <span data-ttu-id="7c778-225">Uygulamayı derlemek ve çalıştırmak için **F5** tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="7c778-225">Press **F5** to build and run the application.</span></span>

4. <span data-ttu-id="7c778-226">İçindeki metni `gre`seçin. <xref:System.Windows.Controls.TextBox></span><span class="sxs-lookup"><span data-stu-id="7c778-226">Select the text `gre` in the <xref:System.Windows.Controls.TextBox>.</span></span>

5. <span data-ttu-id="7c778-227">Metni bir daire denetimine sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="7c778-227">Drag the text to a Circle control.</span></span> <span data-ttu-id="7c778-228">İmlecin şimdi, geçerli bir renk olmadığından, bırakmaya izin verilmediğini `gre` göstermek için değişiklik olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="7c778-228">Notice that the cursor now changes to indicate that the drop is not allowed because `gre` is not a valid color.</span></span>

 <span data-ttu-id="7c778-229">Bırakma işleminin önizlemesini uygulayarak Kullanıcı deneyimini daha da geliştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7c778-229">You can further enhance the user experience by applying a preview of the drop operation.</span></span> <span data-ttu-id="7c778-230">Circle Kullanıcı denetimi için <xref:System.Windows.UIElement.OnDragEnter%2A> ve <xref:System.Windows.UIElement.OnDragLeave%2A> yöntemlerini geçersiz kılacaksınız.</span><span class="sxs-lookup"><span data-stu-id="7c778-230">For the Circle user control, you will override the <xref:System.Windows.UIElement.OnDragEnter%2A> and <xref:System.Windows.UIElement.OnDragLeave%2A> methods.</span></span> <span data-ttu-id="7c778-231">Veriler denetimin üzerine sürüklendiğinde, geçerli arka plan <xref:System.Windows.Shapes.Shape.Fill%2A> bir yer tutucu değişkenine kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="7c778-231">When the data is dragged over the control, the current background <xref:System.Windows.Shapes.Shape.Fill%2A> is saved in a placeholder variable.</span></span> <span data-ttu-id="7c778-232">Daha sonra dize bir fırçaya dönüştürülüp dairenin Kullanıcı arabirimini sağlayan öğesine <xref:System.Windows.Shapes.Ellipse> uygulanır.</span><span class="sxs-lookup"><span data-stu-id="7c778-232">The string is then converted to a brush and applied to the <xref:System.Windows.Shapes.Ellipse> that provides the Circle's UI.</span></span> <span data-ttu-id="7c778-233">Verilerin bırakılmadan dışına sürüklenmesi durumunda özgün <xref:System.Windows.Shapes.Shape.Fill%2A> değer, daireye yeniden uygulanır.</span><span class="sxs-lookup"><span data-stu-id="7c778-233">If the data is dragged out of the Circle without being dropped, the original <xref:System.Windows.Shapes.Shape.Fill%2A> value is re-applied to the Circle.</span></span>

### <a name="to-preview-the-effects-of-the-drag-and-drop-operation"></a><span data-ttu-id="7c778-234">Sürükle ve bırak işleminin etkilerini önizlemek için</span><span class="sxs-lookup"><span data-stu-id="7c778-234">To preview the effects of the drag-and-drop operation</span></span>

1. <span data-ttu-id="7c778-235">Open Circle.xaml.cs veya Circle. xaml. vb.</span><span class="sxs-lookup"><span data-stu-id="7c778-235">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>

2. <span data-ttu-id="7c778-236">Circle sınıfında adlı <xref:System.Windows.Media.Brush> `_previousFill` bir özel değişken bildirin ve bunu olarak `null`başlatın.</span><span class="sxs-lookup"><span data-stu-id="7c778-236">In the Circle class, declare a private <xref:System.Windows.Media.Brush> variable named `_previousFill` and initialize it to `null`.</span></span>

     [!code-csharp[DragDropWalkthrough#Brush](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#brush)]
     [!code-vb[DragDropWalkthrough#Brush](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#brush)]

3. <span data-ttu-id="7c778-237">Olay için sınıf <xref:System.Windows.UIElement.OnDragEnter%2A> işleme sağlamak için aşağıdaki geçersiz kılmayı ekleyin. <xref:System.Windows.UIElement.DragEnter></span><span class="sxs-lookup"><span data-stu-id="7c778-237">Add the following <xref:System.Windows.UIElement.OnDragEnter%2A> override to provide class handling for the <xref:System.Windows.UIElement.DragEnter> event.</span></span>

     [!code-csharp[DragDropWalkthrough#OnDragEnter](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragenter)]
     [!code-vb[DragDropWalkthrough#OnDragEnter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragenter)]

     <span data-ttu-id="7c778-238">Bu <xref:System.Windows.UIElement.OnDragEnter%2A> geçersiz kılma aşağıdaki görevleri gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="7c778-238">This <xref:System.Windows.UIElement.OnDragEnter%2A> override performs the following tasks:</span></span>

    - <span data-ttu-id="7c778-239"><xref:System.Windows.Shapes.Shape.Fill%2A> Öğesinin özelliğini`_previousFill`değişkenine kaydeder. <xref:System.Windows.Shapes.Ellipse></span><span class="sxs-lookup"><span data-stu-id="7c778-239">Saves the <xref:System.Windows.Shapes.Shape.Fill%2A> property of the <xref:System.Windows.Shapes.Ellipse> in the `_previousFill` variable.</span></span>

    - <span data-ttu-id="7c778-240">Verilerin bir <xref:System.Windows.UIElement.OnDrop%2A> <xref:System.Windows.Media.Brush>öğesine dönüştürülüp dönüştürülmeyeceğini anlamak için yönteminde gerçekleştirilen denetimleri gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="7c778-240">Performs the same checks that are performed in the <xref:System.Windows.UIElement.OnDrop%2A> method to determine whether the data can be converted to a <xref:System.Windows.Media.Brush>.</span></span>

    - <span data-ttu-id="7c778-241">Veriler geçerli <xref:System.Windows.Media.Brush>bir değerine dönüştürülürse, ' <xref:System.Windows.Shapes.Shape.Fill%2A> nin <xref:System.Windows.Shapes.Ellipse>öğesine uygular.</span><span class="sxs-lookup"><span data-stu-id="7c778-241">If the data is converted to a valid <xref:System.Windows.Media.Brush>, applies it to the <xref:System.Windows.Shapes.Shape.Fill%2A> of the <xref:System.Windows.Shapes.Ellipse>.</span></span>

4. <span data-ttu-id="7c778-242">Olay için sınıf <xref:System.Windows.UIElement.OnDragLeave%2A> işleme sağlamak için aşağıdaki geçersiz kılmayı ekleyin. <xref:System.Windows.UIElement.DragLeave></span><span class="sxs-lookup"><span data-stu-id="7c778-242">Add the following <xref:System.Windows.UIElement.OnDragLeave%2A> override to provide class handling for the <xref:System.Windows.UIElement.DragLeave> event.</span></span>

     [!code-csharp[DragDropWalkthrough#OnDragLeave](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragleave)]
     [!code-vb[DragDropWalkthrough#OnDragLeave](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragleave)]

     <span data-ttu-id="7c778-243">Bu <xref:System.Windows.UIElement.OnDragLeave%2A> geçersiz kılma aşağıdaki görevleri gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="7c778-243">This <xref:System.Windows.UIElement.OnDragLeave%2A> override performs the following tasks:</span></span>

    - <span data-ttu-id="7c778-244">Değişkenine, Circle Kullanıcı denetiminin Kullanıcı arabirimini sağlayan <xref:System.Windows.Shapes.Shape.Fill%2A> öğesine uygular.<xref:System.Windows.Shapes.Ellipse> <xref:System.Windows.Media.Brush> `_previousFill`</span><span class="sxs-lookup"><span data-stu-id="7c778-244">Applies the <xref:System.Windows.Media.Brush> saved in the `_previousFill` variable to the <xref:System.Windows.Shapes.Shape.Fill%2A> of the <xref:System.Windows.Shapes.Ellipse> that provides the UI of the Circle user control.</span></span>

5. <span data-ttu-id="7c778-245">Uygulamayı derlemek ve çalıştırmak için **F5** tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="7c778-245">Press **F5** to build and run the application.</span></span>

6. <span data-ttu-id="7c778-246">İçindeki metni `green`seçin. <xref:System.Windows.Controls.TextBox></span><span class="sxs-lookup"><span data-stu-id="7c778-246">Select the text `green` in the <xref:System.Windows.Controls.TextBox>.</span></span>

7. <span data-ttu-id="7c778-247">Metni bırakmadan bir daire denetiminin üzerine sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="7c778-247">Drag the text over a Circle control without dropping it.</span></span> <span data-ttu-id="7c778-248">Daire mavi ile yeşil arasında değişir.</span><span class="sxs-lookup"><span data-stu-id="7c778-248">The Circle changes from blue to green.</span></span>

     <span data-ttu-id="7c778-249">![Sürükle&#45;ve&#45;bırak işleminin etkilerini önizleyin](./media/dragdrop-previeweffects.png "DragDrop_PreviewEffects")</span><span class="sxs-lookup"><span data-stu-id="7c778-249">![Preview the effects of a drag&#45;and&#45;drop operation](./media/dragdrop-previeweffects.png "DragDrop_PreviewEffects")</span></span>

8. <span data-ttu-id="7c778-250">Metni daire denetiminden uzağa sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="7c778-250">Drag the text away from the Circle control.</span></span> <span data-ttu-id="7c778-251">Daire, yeşil ve mavi arasında değişir.</span><span class="sxs-lookup"><span data-stu-id="7c778-251">The Circle changes from green back to blue.</span></span>

## <a name="enable-a-panel-to-receive-dropped-data"></a><span data-ttu-id="7c778-252">Bir paneli bırakılan verileri alacak şekilde etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="7c778-252">Enable a Panel to Receive Dropped Data</span></span>

<span data-ttu-id="7c778-253">Bu bölümde, daire kullanıcı denetimlerini barındıran bölmeleri, sürüklenen daire verileri için bırakma hedefleri olarak davranacak şekilde etkinleştirirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7c778-253">In this section, you enable the panels that host the Circle user controls to act as drop targets for dragged Circle data.</span></span> <span data-ttu-id="7c778-254">Bir daireyi bir panelden diğerine taşımanızı veya bir daireyi Sürükleyip bırakırken **CTRL** tuşunu basılı tutarak bir daire denetiminin kopyasını yapmanızı sağlayan kodu uygulayacaksınız.</span><span class="sxs-lookup"><span data-stu-id="7c778-254">You will implement code that enables you to move a Circle from one panel to another, or to make a copy of a Circle control by holding down the **Ctrl** key while dragging and dropping a Circle.</span></span>

1. <span data-ttu-id="7c778-255">MainWindow. xaml ' i açın.</span><span class="sxs-lookup"><span data-stu-id="7c778-255">Open MainWindow.xaml.</span></span>

2. <span data-ttu-id="7c778-256">Aşağıdaki XAML 'de gösterildiği gibi, <xref:System.Windows.Controls.StackPanel> denetimlerin her birinde <xref:System.Windows.UIElement.DragOver> ve <xref:System.Windows.UIElement.Drop> olayları için işleyiciler ekleyin.</span><span class="sxs-lookup"><span data-stu-id="7c778-256">As shown in the following XAML, in each of the <xref:System.Windows.Controls.StackPanel> controls, add handlers for the <xref:System.Windows.UIElement.DragOver> and <xref:System.Windows.UIElement.Drop> events.</span></span> <span data-ttu-id="7c778-257">Olay işleyicisini adlandırın, ve <xref:System.Windows.UIElement.Drop> olay işleyicisini `panel_Drop`adlandırın. `panel_DragOver` <xref:System.Windows.UIElement.DragOver></span><span class="sxs-lookup"><span data-stu-id="7c778-257">Name the <xref:System.Windows.UIElement.DragOver> event handler, `panel_DragOver`, and name the <xref:System.Windows.UIElement.Drop> event handler, `panel_Drop`.</span></span>

     [!code-xaml[DragDropWalkthrough#PanelsXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml#panelsxaml)]

3. <span data-ttu-id="7c778-258">MainWindows.xaml.cs veya MainWindow. xaml. vb dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="7c778-258">Open MainWindows.xaml.cs or MainWindow.xaml.vb.</span></span>

4. <span data-ttu-id="7c778-259"><xref:System.Windows.UIElement.DragOver> Olay işleyicisi için aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="7c778-259">Add the following code for the <xref:System.Windows.UIElement.DragOver> event handler.</span></span>

     [!code-csharp[DragDropWalkthrough#PanelDragOver](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml.cs#paneldragover)]
     [!code-vb[DragDropWalkthrough#PanelDragOver](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/MainWindow.xaml.vb#paneldragover)]

     <span data-ttu-id="7c778-260">Bu <xref:System.Windows.UIElement.DragOver> olay işleyicisi aşağıdaki görevleri gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="7c778-260">This <xref:System.Windows.UIElement.DragOver> event handler performs the following tasks:</span></span>

    - <span data-ttu-id="7c778-261">Sürüklenen verilerin, <xref:System.Windows.DataObject> Circle Kullanıcı denetimiyle paketlenmiş ve <xref:System.Windows.DragDrop.DoDragDrop%2A>çağrısına geçilen "nesne" verilerini içerip içermediğini denetler.</span><span class="sxs-lookup"><span data-stu-id="7c778-261">Checks that the dragged data contains the "Object" data that was packaged in the <xref:System.Windows.DataObject> by the Circle user control and passed in the call to <xref:System.Windows.DragDrop.DoDragDrop%2A>.</span></span>

    - <span data-ttu-id="7c778-262">"Nesne" verileri mevcutsa, **CTRL** tuşuna basıldığını denetler.</span><span class="sxs-lookup"><span data-stu-id="7c778-262">If the "Object" data is present, checks whether the **Ctrl** key is pressed.</span></span>

    - <span data-ttu-id="7c778-263">**CTRL** tuşuna basıldığında <xref:System.Windows.DragEventArgs.Effects%2A> özelliğini olarak <xref:System.Windows.DragDropEffects.Copy>ayarlar.</span><span class="sxs-lookup"><span data-stu-id="7c778-263">If the **Ctrl** key is pressed, sets the <xref:System.Windows.DragEventArgs.Effects%2A> property to <xref:System.Windows.DragDropEffects.Copy>.</span></span> <span data-ttu-id="7c778-264">Aksi takdirde, <xref:System.Windows.DragEventArgs.Effects%2A> özelliğini olarak <xref:System.Windows.DragDropEffects.Move>ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="7c778-264">Otherwise, set the <xref:System.Windows.DragEventArgs.Effects%2A> property to <xref:System.Windows.DragDropEffects.Move>.</span></span>

5. <span data-ttu-id="7c778-265"><xref:System.Windows.UIElement.Drop> Olay işleyicisi için aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="7c778-265">Add the following code for the <xref:System.Windows.UIElement.Drop> event handler.</span></span>

     [!code-csharp[DragDropWalkthrough#PanelDrop](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml.cs#paneldrop)]
     [!code-vb[DragDropWalkthrough#PanelDrop](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/MainWindow.xaml.vb#paneldrop)]

     <span data-ttu-id="7c778-266">Bu <xref:System.Windows.UIElement.Drop> olay işleyicisi aşağıdaki görevleri gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="7c778-266">This <xref:System.Windows.UIElement.Drop> event handler performs the following tasks:</span></span>

    - <span data-ttu-id="7c778-267"><xref:System.Windows.UIElement.Drop> Etkinliğin zaten işlenmiş olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="7c778-267">Checks whether the <xref:System.Windows.UIElement.Drop> event has already been handled.</span></span> <span data-ttu-id="7c778-268">Örneğin, bir daire <xref:System.Windows.UIElement.Drop> olayı işleyen başka bir daire üzerinde bırakıldığında, daireyi içeren panelin da işlenmesi için bu işleci istemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="7c778-268">For instance, if a Circle is dropped on another Circle which handles the <xref:System.Windows.UIElement.Drop> event, you do not want the panel that contains the Circle to also handle it.</span></span>

    - <span data-ttu-id="7c778-269">Olay işlenmezse, CTRL tuşuna basıldığını denetler. <xref:System.Windows.UIElement.Drop></span><span class="sxs-lookup"><span data-stu-id="7c778-269">If the <xref:System.Windows.UIElement.Drop> event is not handled, checks whether the **Ctrl** key is pressed.</span></span>

    - <span data-ttu-id="7c778-270"><xref:System.Windows.UIElement.Drop> Oluştuğunda **CTRL** tuşuna basıldığında, daire denetiminin bir kopyasını oluşturur ve <xref:System.Windows.Controls.Panel.Children%2A> koleksiyonuna <xref:System.Windows.Controls.StackPanel>ekler.</span><span class="sxs-lookup"><span data-stu-id="7c778-270">If the **Ctrl** key is pressed when the <xref:System.Windows.UIElement.Drop> happens, makes a copy of the Circle control and add it to the <xref:System.Windows.Controls.Panel.Children%2A> collection of the <xref:System.Windows.Controls.StackPanel>.</span></span>

    - <span data-ttu-id="7c778-271">**CTRL** tuşuna basılsa, daireyi <xref:System.Windows.Controls.Panel.Children%2A> <xref:System.Windows.Controls.Panel.Children%2A> üst bölmesinin koleksiyonundan, üzerinde bırakılan panelin koleksiyonuna taşımış olur.</span><span class="sxs-lookup"><span data-stu-id="7c778-271">If the **Ctrl** key is not pressed, moves the Circle from the <xref:System.Windows.Controls.Panel.Children%2A> collection of its parent panel to the <xref:System.Windows.Controls.Panel.Children%2A> collection of the panel that it was dropped on.</span></span>

    - <span data-ttu-id="7c778-272">Yöntemi, bir taşıma veya kopyalama işleminin gerçekleştirilip gerçekleştirilmediğini <xref:System.Windows.DragEventArgs.Effects%2A> bildirmek için <xref:System.Windows.DragDrop.DoDragDrop%2A> özelliği ayarlar.</span><span class="sxs-lookup"><span data-stu-id="7c778-272">Sets the <xref:System.Windows.DragEventArgs.Effects%2A> property to notify the <xref:System.Windows.DragDrop.DoDragDrop%2A> method whether a move or copy operation was performed.</span></span>

6. <span data-ttu-id="7c778-273">Uygulamayı derlemek ve çalıştırmak için **F5** tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="7c778-273">Press **F5** to build and run the application.</span></span>

7. <span data-ttu-id="7c778-274">Öğesinden metni `green`seçin. <xref:System.Windows.Controls.TextBox></span><span class="sxs-lookup"><span data-stu-id="7c778-274">Select the text `green` from the <xref:System.Windows.Controls.TextBox>.</span></span>

8. <span data-ttu-id="7c778-275">Metni bir daire denetiminin üzerine sürükleyin ve bırakın.</span><span class="sxs-lookup"><span data-stu-id="7c778-275">Drag the text over a Circle control and drop it.</span></span>

9. <span data-ttu-id="7c778-276">Sol panelden bir daire denetimini sağ panele sürükleyin ve bırakın.</span><span class="sxs-lookup"><span data-stu-id="7c778-276">Drag a Circle control from the left panel to the right panel and drop it.</span></span> <span data-ttu-id="7c778-277">Daire, sol bölmenin <xref:System.Windows.Controls.Panel.Children%2A> koleksiyonundan kaldırılır ve sağ bölmenin alt öğe koleksiyonuna eklenir.</span><span class="sxs-lookup"><span data-stu-id="7c778-277">The Circle is removed from the <xref:System.Windows.Controls.Panel.Children%2A> collection of the left panel and added to the Children collection of the right panel.</span></span>

10. <span data-ttu-id="7c778-278">Bir daire denetimini, içindeki panelden diğer panele sürükleyin ve **CTRL** tuşuna basarak bırakın.</span><span class="sxs-lookup"><span data-stu-id="7c778-278">Drag a Circle control from the panel it is in to the other panel and drop it while pressing the **Ctrl** key.</span></span> <span data-ttu-id="7c778-279">Daire kopyalanır ve kopya, alan paneli <xref:System.Windows.Controls.Panel.Children%2A> koleksiyonuna eklenir.</span><span class="sxs-lookup"><span data-stu-id="7c778-279">The Circle is copied and the copy is added to the <xref:System.Windows.Controls.Panel.Children%2A> collection of the receiving panel.</span></span>

     <span data-ttu-id="7c778-280">![CTRL tuşuna basıldığında bir daireyi sürükleme](./media/dragdrop-paneldrop.png "DragDrop_PanelDrop")</span><span class="sxs-lookup"><span data-stu-id="7c778-280">![Dragging a Circle while pressing the CTRL key](./media/dragdrop-paneldrop.png "DragDrop_PanelDrop")</span></span>

## <a name="see-also"></a><span data-ttu-id="7c778-281">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7c778-281">See also</span></span>

- [<span data-ttu-id="7c778-282">Sürükleme ve Bırakmaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="7c778-282">Drag and Drop Overview</span></span>](drag-and-drop-overview.md)
