---
title: "İzlenecek yol: Visual Basic ile beraber Windows Forms Denetimi'nden Devralma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: vb
helpviewer_keywords:
- inheritance [Windows Forms], custom controls
- inheritance [Windows Forms], control
- Windows Forms controls, inheritance
- inheritance [Windows Forms], walkthroughs
- custom controls [Windows Forms], inheritance
ms.assetid: fb58d7c8-b702-4478-ad31-b00cae118882
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0625695933b776b8cdbe5488adc116723b930dd0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic"></a><span data-ttu-id="2acd7-102">İzlenecek yol: Visual Basic ile beraber Windows Forms Denetimi'nden Devralma</span><span class="sxs-lookup"><span data-stu-id="2acd7-102">Walkthrough: Inheriting from a Windows Forms Control with Visual Basic</span></span>
<span data-ttu-id="2acd7-103">İle [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)], güçlü özel denetimlerde oluşturabilirsiniz *devralma*.</span><span class="sxs-lookup"><span data-stu-id="2acd7-103">With [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)], you can create powerful custom controls through *inheritance*.</span></span> <span data-ttu-id="2acd7-104">Devralma sayesinde, tüm standart Windows Forms denetimleri devralınmış işlevselliğini korur, ancak ayrıca özel işlevselliğine sahiptir denetimleri oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2acd7-104">Through inheritance you are able to create controls that retain all of the inherent functionality of standard Windows Forms controls but also incorporate custom functionality.</span></span> <span data-ttu-id="2acd7-105">Bu kılavuzda, adlı basit bir devralınan denetim oluşturacak `ValueButton`.</span><span class="sxs-lookup"><span data-stu-id="2acd7-105">In this walkthrough, you will create a simple inherited control called `ValueButton`.</span></span> <span data-ttu-id="2acd7-106">Bu düğme standart Windows formlarının dışında işlevselliği devralır <xref:System.Windows.Forms.Button> denetlemek ve adlı özel bir özellik kullanıma `ButtonValue`.</span><span class="sxs-lookup"><span data-stu-id="2acd7-106">This button will inherit functionality from the standard Windows Forms <xref:System.Windows.Forms.Button> control, and will expose a custom property called `ButtonValue`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2acd7-107">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="2acd7-107">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="2acd7-108">Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="2acd7-108">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="2acd7-109">Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="2acd7-109">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="2acd7-110">Projeyi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="2acd7-110">Creating the Project</span></span>  
 <span data-ttu-id="2acd7-111">Yeni bir proje oluşturduğunuzda, kök ad alanı, derleme adı ve proje adı ayarlamak için ve varsayılan bileşen doğru ad alanında olduğundan emin olmak için adını belirtin.</span><span class="sxs-lookup"><span data-stu-id="2acd7-111">When you create a new project, you specify its name in order to set the root namespace, assembly name, and project name, and to ensure that the default component will be in the correct namespace.</span></span>  
  
#### <a name="to-create-the-valuebuttonlib-control-library-and-the-valuebutton-control"></a><span data-ttu-id="2acd7-112">ValueButtonLib denetim kitaplığı ve ValueButton denetimi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="2acd7-112">To create the ValueButtonLib control library and the ValueButton control</span></span>  
  
1.  <span data-ttu-id="2acd7-113">Üzerinde **dosya** menüsündeki **yeni** ve ardından **proje** açmak için **yeni proje** iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="2acd7-113">On the **File** menu, point to **New** and then click **Project** to open the **New Project** dialog box.</span></span>  
  
2.  <span data-ttu-id="2acd7-114">Seçin **Windows Forms Denetim Kitaplığı** proje şablonu listesinden [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] projeleri ve türü `ValueButtonLib` içinde **adı** kutusu.</span><span class="sxs-lookup"><span data-stu-id="2acd7-114">Select the **Windows Forms Control Library** project template from the list of [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] projects, and type `ValueButtonLib` in the **Name** box.</span></span>  
  
     <span data-ttu-id="2acd7-115">Proje adı `ValueButtonLib`, kök ad alanı için varsayılan olarak da atanmış.</span><span class="sxs-lookup"><span data-stu-id="2acd7-115">The project name, `ValueButtonLib`, is also assigned to the root namespace by default.</span></span> <span data-ttu-id="2acd7-116">Kök ad derleme bileşenlerinde adlarını nitelemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2acd7-116">The root namespace is used to qualify the names of components in the assembly.</span></span> <span data-ttu-id="2acd7-117">Örneğin, iki derleme adlı bileşenleri sağlarsanız `ValueButton`, belirtebilirsiniz, `ValueButton` bileşenini kullanarak `ValueButtonLib.ValueButton`.</span><span class="sxs-lookup"><span data-stu-id="2acd7-117">For example, if two assemblies provide components named `ValueButton`, you can specify your `ValueButton` component using `ValueButtonLib.ValueButton`.</span></span> <span data-ttu-id="2acd7-118">Daha fazla bilgi için bkz: [Visual Basic'de ad alanları](~/docs/visual-basic/programming-guide/program-structure/namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="2acd7-118">For more information, see [Namespaces in Visual Basic](~/docs/visual-basic/programming-guide/program-structure/namespaces.md).</span></span>  
  
3.  <span data-ttu-id="2acd7-119">İçinde **Çözüm Gezgini**, sağ **UserControl1.vb**, ardından **yeniden adlandırmak** kısayol menüsünden.</span><span class="sxs-lookup"><span data-stu-id="2acd7-119">In **Solution Explorer**, right-click **UserControl1.vb**, then choose **Rename** from the shortcut menu.</span></span> <span data-ttu-id="2acd7-120">Dosya adını değiştirmek `ValueButton.vb`.</span><span class="sxs-lookup"><span data-stu-id="2acd7-120">Change the file name to `ValueButton.vb`.</span></span> <span data-ttu-id="2acd7-121">Tıklatın **Evet** düğmesini code öğesi 'UserControl1' yapılan tüm başvuruları yeniden adlandırmak istediğiniz sorulduğunda.</span><span class="sxs-lookup"><span data-stu-id="2acd7-121">Click the **Yes** button when you are asked if you want to rename all references to the code element 'UserControl1'.</span></span>  
  
4.  <span data-ttu-id="2acd7-122">İçinde **Çözüm Gezgini**, tıklatın **tüm dosyaları göster** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="2acd7-122">In **Solution Explorer**, click the **Show All Files** button.</span></span>  
  
5.  <span data-ttu-id="2acd7-123">Açık **ValueButton.vb** Tasarımcısı ile oluşturulan kodun dosyayı görüntülemek için düğümü **ValueButton.Designer.vb**.</span><span class="sxs-lookup"><span data-stu-id="2acd7-123">Open the **ValueButton.vb** node to display the designer-generated code file, **ValueButton.Designer.vb**.</span></span> <span data-ttu-id="2acd7-124">Bu dosyayı açmak **Kod düzenleyicisinde**.</span><span class="sxs-lookup"><span data-stu-id="2acd7-124">Open this file in the **Code Editor**.</span></span>  
  
6.  <span data-ttu-id="2acd7-125">Bulun `Class` deyimi, `Partial Public Class ValueButton`, bu denetim devraldığı türünü değiştirip <xref:System.Windows.Forms.UserControl> için <xref:System.Windows.Forms.Button>.</span><span class="sxs-lookup"><span data-stu-id="2acd7-125">Locate the `Class` statement, `Partial Public Class ValueButton`, and change the type from which this control inherits from <xref:System.Windows.Forms.UserControl> to <xref:System.Windows.Forms.Button>.</span></span> <span data-ttu-id="2acd7-126">Bu, tüm işlevselliğini devralmak, devralınan denetimi sağlar <xref:System.Windows.Forms.Button> denetim.</span><span class="sxs-lookup"><span data-stu-id="2acd7-126">This allows your inherited control to inherit all the functionality of the <xref:System.Windows.Forms.Button> control.</span></span>  
  
7.  <span data-ttu-id="2acd7-127">Bulun `InitializeComponent` yöntemi ekleme ve kaldırma atar satır <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="2acd7-127">Locate the `InitializeComponent` method and remove the line that assigns the <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> property.</span></span> <span data-ttu-id="2acd7-128">Bu özellik yok <xref:System.Windows.Forms.Button> denetim.</span><span class="sxs-lookup"><span data-stu-id="2acd7-128">This property does not exist in the <xref:System.Windows.Forms.Button> control.</span></span>  
  
8.  <span data-ttu-id="2acd7-129">Gelen **dosya** menüsünde seçin **Tümünü Kaydet** projeyi kaydetmek için.</span><span class="sxs-lookup"><span data-stu-id="2acd7-129">From the **File** menu, choose **Save All** to save the project.</span></span>  
  
     <span data-ttu-id="2acd7-130">Görsel Tasarımcı artık kullanılabilir olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="2acd7-130">Note that a visual designer is no longer available.</span></span> <span data-ttu-id="2acd7-131">Çünkü <xref:System.Windows.Forms.Button> denetim kendi boyama yok, görünümünü Tasarımcısı'nda değiştiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="2acd7-131">Because the <xref:System.Windows.Forms.Button> control does its own painting, you are unable to modify its appearance in the designer.</span></span> <span data-ttu-id="2acd7-132">Görsel gösterimi tam olarak bunu devraldığı sınıfı, aynı olacaktır (diğer bir deyişle, <xref:System.Windows.Forms.Button>) kodda değişiklik sürece.</span><span class="sxs-lookup"><span data-stu-id="2acd7-132">Its visual representation will be exactly the same as that of the class it inherits from (that is, <xref:System.Windows.Forms.Button>) unless modified in the code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2acd7-133">Tasarım yüzeyine hiçbir kullanıcı Arabirimi öğeleri olan bileşenleri eklemeye devam edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2acd7-133">You can still add components, which have no UI elements, to the design surface.</span></span>  
  
## <a name="adding-a-property-to-your-inherited-control"></a><span data-ttu-id="2acd7-134">Devralınan denetiminizi özellik ekleme</span><span class="sxs-lookup"><span data-stu-id="2acd7-134">Adding a Property to Your Inherited Control</span></span>  
 <span data-ttu-id="2acd7-135">Bir olası devralınan Windows Forms denetimleri, standart Windows Forms denetimlerine görünümünü ve davranışını (Görünüm) aynıdır, ancak özel özelliklerini ortaya denetimleri oluşturulmasını kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2acd7-135">One possible use of inherited Windows Forms controls is the creation of controls that are identical in appearance and behavior (look and feel) to standard Windows Forms controls, but expose custom properties.</span></span> <span data-ttu-id="2acd7-136">Bu bölümde, adlı bir özellik ekleyecek `ButtonValue` denetiminiz için.</span><span class="sxs-lookup"><span data-stu-id="2acd7-136">In this section, you will add a property called `ButtonValue` to your control.</span></span>  
  
#### <a name="to-add-the-value-property"></a><span data-ttu-id="2acd7-137">Value özelliği eklemek için</span><span class="sxs-lookup"><span data-stu-id="2acd7-137">To add the Value property</span></span>  
  
1.  <span data-ttu-id="2acd7-138">İçinde **Çözüm Gezgini**, sağ **ValueButton.vb**ve ardından **görünümü kodu** kısayol menüsünden.</span><span class="sxs-lookup"><span data-stu-id="2acd7-138">In **Solution Explorer**, right-click **ValueButton.vb**, and then click **View Code** from the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="2acd7-139">Bulun `Public Class ValueButton` deyimi.</span><span class="sxs-lookup"><span data-stu-id="2acd7-139">Locate the `Public Class ValueButton` statement.</span></span> <span data-ttu-id="2acd7-140">Hemen bu bildirimi aşağıdaki kodu yazın:</span><span class="sxs-lookup"><span data-stu-id="2acd7-140">Immediately beneath this statement, type the following code:</span></span>  
  
    ```vb  
    ' Creates the private variable that will store the value of your   
    ' property.  
    Private varValue as integer  
    ' Declares the property.  
    Property ButtonValue() as Integer  
    ' Sets the method for retrieving the value of your property.  
       Get  
          Return varValue  
       End Get  
    ' Sets the method for setting the value of your property.  
       Set(ByVal Value as Integer)  
          varValue = Value  
       End Set  
    End Property  
    ```  
  
     <span data-ttu-id="2acd7-141">Bu kod yöntemleri olarak ayarlar `ButtonValue` özelliği depolanır ve alınır.</span><span class="sxs-lookup"><span data-stu-id="2acd7-141">This code sets the methods by which the `ButtonValue` property is stored and retrieved.</span></span> <span data-ttu-id="2acd7-142">`Get` Deyimi ayarlar özel değişkeninde depolanan değere döndürülen değer `varValue`ve `Set` deyimi kullanarak özel değişkenin değerini ayarlar `Value` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="2acd7-142">The `Get` statement sets the value returned to the value that is stored in the private variable `varValue`, and the `Set` statement sets the value of the private variable by use of the `Value` keyword.</span></span>  
  
3.  <span data-ttu-id="2acd7-143">Gelen **dosya** menüsünde seçin **Tümünü Kaydet** projeyi kaydetmek için.</span><span class="sxs-lookup"><span data-stu-id="2acd7-143">From the **File** menu, choose **Save All** to save the project.</span></span>  
  
## <a name="testing-your-control"></a><span data-ttu-id="2acd7-144">Denetim test etme</span><span class="sxs-lookup"><span data-stu-id="2acd7-144">Testing Your Control</span></span>  
 <span data-ttu-id="2acd7-145">Denetimleri tek başına projeleri değildir; bir kapsayıcıda barındırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2acd7-145">Controls are not stand-alone projects; they must be hosted in a container.</span></span> <span data-ttu-id="2acd7-146">Denetim test etmek amacıyla çalıştırmak için test projesi için bu sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="2acd7-146">In order to test your control, you must provide a test project for it to run in.</span></span> <span data-ttu-id="2acd7-147">Ayrıca, Denetim test projesi için erişilebilir (derleme) oluşturarak yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="2acd7-147">You must also make your control accessible to the test project by building (compiling) it.</span></span> <span data-ttu-id="2acd7-148">Bu bölümde, denetiminizi oluşturabilirsiniz ve bir Windows formunda sınayın.</span><span class="sxs-lookup"><span data-stu-id="2acd7-148">In this section, you will build your control and test it in a Windows Form.</span></span>  
  
#### <a name="to-build-your-control"></a><span data-ttu-id="2acd7-149">Denetim oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="2acd7-149">To build your control</span></span>  
  
1.  <span data-ttu-id="2acd7-150">Üzerinde **yapı** menüsünde tıklatın **yapı çözümü**.</span><span class="sxs-lookup"><span data-stu-id="2acd7-150">On the **Build** menu, click **Build Solution**.</span></span>  
  
     <span data-ttu-id="2acd7-151">Yapı hiçbir derleyici hataları veya uyarılarla başarılı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="2acd7-151">The build should be successful with no compiler errors or warnings.</span></span>  
  
#### <a name="to-create-a-test-project"></a><span data-ttu-id="2acd7-152">Bir test projesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="2acd7-152">To create a test project</span></span>  
  
1.  <span data-ttu-id="2acd7-153">Üzerinde **dosya** menüsündeki **Ekle** ve ardından **yeni proje** açmak için **Yeni Proje Ekle** iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="2acd7-153">On the **File** menu, point to **Add** and then click **New Project** to open the **Add New Project** dialog box.</span></span>  
  
2.  <span data-ttu-id="2acd7-154">Seçin [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] Projeleri düğümü ve tıklatın **Windows Forms uygulaması**.</span><span class="sxs-lookup"><span data-stu-id="2acd7-154">Select the [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] projects node, and click **Windows Forms Application**.</span></span>  
  
3.  <span data-ttu-id="2acd7-155">İçinde **adı** kutusuna `Test`.</span><span class="sxs-lookup"><span data-stu-id="2acd7-155">In the **Name** box, type `Test`.</span></span>  
  
4.  <span data-ttu-id="2acd7-156">İçinde **Çözüm Gezgini**, tıklatın **tüm dosyaları göster** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="2acd7-156">In **Solution Explorer**, click the **Show All Files** button.</span></span>  
  
5.  <span data-ttu-id="2acd7-157">İçinde **Çözüm Gezgini**, sağ **başvuruları** , test projeniz için düğümü seçip **Başvuru Ekle** görüntülemek için kısayol menüsünden  **Başvuru ekleme** iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="2acd7-157">In **Solution Explorer**, right-click the **References** node for your test project, then select **Add Reference** from the shortcut menu to display the **Add Reference** dialog box.</span></span>  
  
6.  <span data-ttu-id="2acd7-158">Tıklatın **projeleri** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="2acd7-158">Click the **Projects** tab.</span></span>  
  
7.  <span data-ttu-id="2acd7-159">Etiketli sekmesini **projeleri**.</span><span class="sxs-lookup"><span data-stu-id="2acd7-159">Click the tab labeled **Projects**.</span></span> <span data-ttu-id="2acd7-160">`ValueButtonLib` Proje altında listelenir **proje adı**.</span><span class="sxs-lookup"><span data-stu-id="2acd7-160">Your `ValueButtonLib` project will be listed under **Project Name**.</span></span> <span data-ttu-id="2acd7-161">Projeyi test projesinin başvuru eklemek için çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="2acd7-161">Double-click the project to add the reference to the test project.</span></span>  
  
8.  <span data-ttu-id="2acd7-162">İçinde **Çözüm Gezgini** sağ **Test** seçip **yapı**.</span><span class="sxs-lookup"><span data-stu-id="2acd7-162">In **Solution Explorer,** right-click **Test** and select **Build**.</span></span>  
  
#### <a name="to-add-your-control-to-the-form"></a><span data-ttu-id="2acd7-163">Forma denetim ekleme</span><span class="sxs-lookup"><span data-stu-id="2acd7-163">To add your control to the form</span></span>  
  
1.  <span data-ttu-id="2acd7-164">İçinde **Çözüm Gezgini**, sağ **Form1.vb** ve **Görünüm Tasarımcısı** kısayol menüsünden.</span><span class="sxs-lookup"><span data-stu-id="2acd7-164">In **Solution Explorer**, right-click **Form1.vb** and choose **View Designer** from the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="2acd7-165">İçinde **araç**, tıklatın **ValueButtonLib bileşenleri**.</span><span class="sxs-lookup"><span data-stu-id="2acd7-165">In the **Toolbox**, click **ValueButtonLib Components**.</span></span> <span data-ttu-id="2acd7-166">Çift **ValueButton**.</span><span class="sxs-lookup"><span data-stu-id="2acd7-166">Double-click **ValueButton**.</span></span>  
  
     <span data-ttu-id="2acd7-167">A **ValueButton** formda görünür.</span><span class="sxs-lookup"><span data-stu-id="2acd7-167">A **ValueButton** appears on the form.</span></span>  
  
3.  <span data-ttu-id="2acd7-168">Sağ **ValueButton** seçip **özellikleri** kısayol menüsünden.</span><span class="sxs-lookup"><span data-stu-id="2acd7-168">Right-click the **ValueButton** and select **Properties** from the shortcut menu.</span></span>  
  
4.  <span data-ttu-id="2acd7-169">İçinde **özellikleri** penceresinde, bu denetim özelliklerini inceleyin.</span><span class="sxs-lookup"><span data-stu-id="2acd7-169">In the **Properties** window, examine the properties of this control.</span></span> <span data-ttu-id="2acd7-170">Bir ek özellik olmasını dışında bunların özdeş standart bir düğme tarafından kullanıma sunulan özellikler için olduğunu unutmayın `ButtonValue`.</span><span class="sxs-lookup"><span data-stu-id="2acd7-170">Note that they are identical to the properties exposed by a standard button, except that there is an additional property, `ButtonValue`.</span></span>  
  
5.  <span data-ttu-id="2acd7-171">Ayarlama `ButtonValue` özelliğine `5`.</span><span class="sxs-lookup"><span data-stu-id="2acd7-171">Set the `ButtonValue` property to `5`.</span></span>  
  
6.  <span data-ttu-id="2acd7-172">Üzerinde **tüm Windows Forms** sekmesinde **araç**, çift **etiket** eklemek için bir <xref:System.Windows.Forms.Label> Formunuza denetim.</span><span class="sxs-lookup"><span data-stu-id="2acd7-172">On the **All Windows Forms** tab of the **Toolbox**, double-click **Label** to add a <xref:System.Windows.Forms.Label> control to your form.</span></span>  
  
7.  <span data-ttu-id="2acd7-173">Etiket formu merkezine taşımanızı.</span><span class="sxs-lookup"><span data-stu-id="2acd7-173">Relocate the label to the center of the form.</span></span>  
  
8.  <span data-ttu-id="2acd7-174">Çift `ValueButton1`.</span><span class="sxs-lookup"><span data-stu-id="2acd7-174">Double-click `ValueButton1`.</span></span>  
  
     <span data-ttu-id="2acd7-175">**Kod düzenleyicisinde** açılır `ValueButton1_Click` olay.</span><span class="sxs-lookup"><span data-stu-id="2acd7-175">The **Code Editor** opens to the `ValueButton1_Click` event.</span></span>  
  
9. <span data-ttu-id="2acd7-176">Aşağıdaki kod satırını yazın.</span><span class="sxs-lookup"><span data-stu-id="2acd7-176">Type the following line of code.</span></span>  
  
    ```vb  
    Label1.Text = CStr(ValueButton1.ButtonValue)  
    ```  
  
10. <span data-ttu-id="2acd7-177">İçinde **Çözüm Gezgini**, sağ **Test**ve seçin **başlangıç projesi olarak ayarla** kısayol menüsünden.</span><span class="sxs-lookup"><span data-stu-id="2acd7-177">In **Solution Explorer**, right-click **Test**, and choose **Set as Startup Project** from the shortcut menu.</span></span>  
  
11. <span data-ttu-id="2acd7-178">Gelen **hata ayıklama** menüsünde, select **hata ayıklamayı Başlat**.</span><span class="sxs-lookup"><span data-stu-id="2acd7-178">From the **Debug** menu, select **Start Debugging**.</span></span>  
  
     <span data-ttu-id="2acd7-179">`Form1`görünür.</span><span class="sxs-lookup"><span data-stu-id="2acd7-179">`Form1` appears.</span></span>  
  
12. <span data-ttu-id="2acd7-180">Tıklatın `Valuebutton1`.</span><span class="sxs-lookup"><span data-stu-id="2acd7-180">Click `Valuebutton1`.</span></span>  
  
     <span data-ttu-id="2acd7-181">'5' rakamı görüntülenen `Label1`, gösteren, `ButtonValue` devralınan denetiminizin özelliği için geçirilmiş `Label1` aracılığıyla `ValueButton1_Click` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="2acd7-181">The numeral '5' is displayed in `Label1`, demonstrating that the `ButtonValue` property of your inherited control has been passed to `Label1` through the `ValueButton1_Click` method.</span></span> <span data-ttu-id="2acd7-182">Bu nedenle, `ValueButton` denetimi standart Windows Forms düğme tüm işlevselliğini devralır, ancak ek, özel bir özellik sunar.</span><span class="sxs-lookup"><span data-stu-id="2acd7-182">Thus your `ValueButton` control inherits all the functionality of the standard Windows Forms button, but exposes an additional, custom property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2acd7-183">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2acd7-183">See Also</span></span>  
 [<span data-ttu-id="2acd7-184">İzlenecek yol: Visual Basic ile bileşik denetim yazma</span><span class="sxs-lookup"><span data-stu-id="2acd7-184">Walkthrough: Authoring a Composite Control with Visual Basic</span></span>](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-basic.md)  
 [<span data-ttu-id="2acd7-185">Nasıl yapılır: bir denetimi görüntüleme araç kutusu öğelerini Seç iletişim kutusu</span><span class="sxs-lookup"><span data-stu-id="2acd7-185">How to: Display a Control in the Choose Toolbox Items Dialog Box</span></span>](../../../../docs/framework/winforms/controls/how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)  
 [<span data-ttu-id="2acd7-186">Özel Windows Forms denetimleri .NET Framework ile geliştirme</span><span class="sxs-lookup"><span data-stu-id="2acd7-186">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)  
 [<span data-ttu-id="2acd7-187">Devralma temelleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2acd7-187">Inheritance basics (Visual Basic)</span></span>](~/docs/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)  
 [<span data-ttu-id="2acd7-188">Bileşen geliştirme izlenecek yollar</span><span class="sxs-lookup"><span data-stu-id="2acd7-188">Component Authoring Walkthroughs</span></span>](http://msdn.microsoft.com/library/c414cca9-2489-4208-8b38-954586d91c13)
