---
title: "İzlenecek yol: Visual Basic ile beraber Windows Forms Denetimi'nden Devralma"
ms.date: 03/30/2017
dev_langs:
- vb
helpviewer_keywords:
- inheritance [Windows Forms], custom controls
- inheritance [Windows Forms], control
- Windows Forms controls, inheritance
- inheritance [Windows Forms], walkthroughs
- custom controls [Windows Forms], inheritance
ms.assetid: fb58d7c8-b702-4478-ad31-b00cae118882
ms.openlocfilehash: b606de4b7cf4648fdc7ada3c1f6faec81342d02c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61792190"
---
# <a name="walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic"></a><span data-ttu-id="9ad5c-102">İzlenecek yol: Visual Basic ile beraber Windows Forms Denetimi'nden Devralma</span><span class="sxs-lookup"><span data-stu-id="9ad5c-102">Walkthrough: Inheriting from a Windows Forms Control with Visual Basic</span></span>
<span data-ttu-id="9ad5c-103">Visual Basic ile aracılığıyla güçlü özel denetimler oluşturabilirsiniz *devralma*.</span><span class="sxs-lookup"><span data-stu-id="9ad5c-103">With Visual Basic, you can create powerful custom controls through *inheritance*.</span></span> <span data-ttu-id="9ad5c-104">Devralma üzerinden tüm standart Windows Forms denetimleri devralınan işlevlerini korur, ancak özel işlevler de dahil denetimleri oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9ad5c-104">Through inheritance you are able to create controls that retain all of the inherent functionality of standard Windows Forms controls but also incorporate custom functionality.</span></span> <span data-ttu-id="9ad5c-105">Bu izlenecek yolda, adlı basit bir devralınan denetim oluşturacaksınız `ValueButton`.</span><span class="sxs-lookup"><span data-stu-id="9ad5c-105">In this walkthrough, you will create a simple inherited control called `ValueButton`.</span></span> <span data-ttu-id="9ad5c-106">Bu düğme, standart Windows Forms işlevselliği devralır <xref:System.Windows.Forms.Button> denetlemek ve adlı bir özel özellik açığa çıkarır `ButtonValue`.</span><span class="sxs-lookup"><span data-stu-id="9ad5c-106">This button will inherit functionality from the standard Windows Forms <xref:System.Windows.Forms.Button> control, and will expose a custom property called `ButtonValue`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9ad5c-107">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="9ad5c-107">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="9ad5c-108">Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="9ad5c-108">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="9ad5c-109">Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="9ad5c-109">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="9ad5c-110">Projeyi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="9ad5c-110">Creating the Project</span></span>  
 <span data-ttu-id="9ad5c-111">Yeni bir proje oluşturduğunuzda, kök ad alanı, derleme adı ve proje adını ayarlayın ve varsayılan bileşeni doğru ad alanı içinde olmasını sağlamak için adını belirtin.</span><span class="sxs-lookup"><span data-stu-id="9ad5c-111">When you create a new project, you specify its name in order to set the root namespace, assembly name, and project name, and to ensure that the default component will be in the correct namespace.</span></span>  
  
#### <a name="to-create-the-valuebuttonlib-control-library-and-the-valuebutton-control"></a><span data-ttu-id="9ad5c-112">ValueButtonLib denetim kitaplığı ve ValueButton denetimi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="9ad5c-112">To create the ValueButtonLib control library and the ValueButton control</span></span>  
  
1. <span data-ttu-id="9ad5c-113">Üzerinde **dosya** menüsünde **yeni** ve ardından **proje** açmak için **yeni proje** iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="9ad5c-113">On the **File** menu, point to **New** and then click **Project** to open the **New Project** dialog box.</span></span>  
  
2. <span data-ttu-id="9ad5c-114">Seçin **Windows Forms Denetim Kitaplığı** proje şablonu Visual Basic projeleri ve türü listesinden `ValueButtonLib` içinde **adı** kutusu.</span><span class="sxs-lookup"><span data-stu-id="9ad5c-114">Select the **Windows Forms Control Library** project template from the list of Visual Basic projects, and type `ValueButtonLib` in the **Name** box.</span></span>  
  
     <span data-ttu-id="9ad5c-115">Proje adı `ValueButtonLib`, aynı zamanda kök ad alanı için varsayılan olarak atanır.</span><span class="sxs-lookup"><span data-stu-id="9ad5c-115">The project name, `ValueButtonLib`, is also assigned to the root namespace by default.</span></span> <span data-ttu-id="9ad5c-116">Kök ad alanı, bileşenleri derleme içindeki adlarını nitelemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9ad5c-116">The root namespace is used to qualify the names of components in the assembly.</span></span> <span data-ttu-id="9ad5c-117">Örneğin, iki derleme adlı bileşenleri sağlarsanız `ValueButton`, belirtebilirsiniz, `ValueButton` bileşenini kullanarak `ValueButtonLib.ValueButton`.</span><span class="sxs-lookup"><span data-stu-id="9ad5c-117">For example, if two assemblies provide components named `ValueButton`, you can specify your `ValueButton` component using `ValueButtonLib.ValueButton`.</span></span> <span data-ttu-id="9ad5c-118">Daha fazla bilgi için [Visual Basic'de ad alanları](~/docs/visual-basic/programming-guide/program-structure/namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="9ad5c-118">For more information, see [Namespaces in Visual Basic](~/docs/visual-basic/programming-guide/program-structure/namespaces.md).</span></span>  
  
3. <span data-ttu-id="9ad5c-119">İçinde **Çözüm Gezgini**, sağ **UserControl1.vb**, ardından **Yeniden Adlandır** kısayol menüsünden.</span><span class="sxs-lookup"><span data-stu-id="9ad5c-119">In **Solution Explorer**, right-click **UserControl1.vb**, then choose **Rename** from the shortcut menu.</span></span> <span data-ttu-id="9ad5c-120">İçin dosya adını değiştirerek `ValueButton.vb`.</span><span class="sxs-lookup"><span data-stu-id="9ad5c-120">Change the file name to `ValueButton.vb`.</span></span> <span data-ttu-id="9ad5c-121">Tıklayın **Evet** yaptığınız 'UserControl1' kod öğesi için tüm başvuruları yeniden adlandırmak isteyip istemediğiniz sorulduğunda düğmesi.</span><span class="sxs-lookup"><span data-stu-id="9ad5c-121">Click the **Yes** button when you are asked if you want to rename all references to the code element 'UserControl1'.</span></span>  
  
4. <span data-ttu-id="9ad5c-122">İçinde **Çözüm Gezgini**, tıklayın **tüm dosyaları göster** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="9ad5c-122">In **Solution Explorer**, click the **Show All Files** button.</span></span>  
  
5. <span data-ttu-id="9ad5c-123">Açık **ValueButton.vb** kod tasarımcı tarafından oluşturulan dosya görüntülenecek düğümü **ValueButton.Designer.vb**.</span><span class="sxs-lookup"><span data-stu-id="9ad5c-123">Open the **ValueButton.vb** node to display the designer-generated code file, **ValueButton.Designer.vb**.</span></span> <span data-ttu-id="9ad5c-124">Bu dosyayı açmak **Kod Düzenleyicisi**.</span><span class="sxs-lookup"><span data-stu-id="9ad5c-124">Open this file in the **Code Editor**.</span></span>  
  
6. <span data-ttu-id="9ad5c-125">Bulun `Class` deyimi `Partial Public Class ValueButton`, bu denetim devraldığı türünü değiştirip <xref:System.Windows.Forms.UserControl> için <xref:System.Windows.Forms.Button>.</span><span class="sxs-lookup"><span data-stu-id="9ad5c-125">Locate the `Class` statement, `Partial Public Class ValueButton`, and change the type from which this control inherits from <xref:System.Windows.Forms.UserControl> to <xref:System.Windows.Forms.Button>.</span></span> <span data-ttu-id="9ad5c-126">Böylece tüm işlevlerini devralmak devralınan denetim <xref:System.Windows.Forms.Button> denetimi.</span><span class="sxs-lookup"><span data-stu-id="9ad5c-126">This allows your inherited control to inherit all the functionality of the <xref:System.Windows.Forms.Button> control.</span></span>  
  
7. <span data-ttu-id="9ad5c-127">Bulun `InitializeComponent` yöntemi ekleme ve kaldırma atar satırı <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="9ad5c-127">Locate the `InitializeComponent` method and remove the line that assigns the <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> property.</span></span> <span data-ttu-id="9ad5c-128">Bu özellik yok <xref:System.Windows.Forms.Button> denetimi.</span><span class="sxs-lookup"><span data-stu-id="9ad5c-128">This property does not exist in the <xref:System.Windows.Forms.Button> control.</span></span>  
  
8. <span data-ttu-id="9ad5c-129">Gelen **dosya** menüsünde seçin **Tümünü Kaydet** projeyi kaydetmek için.</span><span class="sxs-lookup"><span data-stu-id="9ad5c-129">From the **File** menu, choose **Save All** to save the project.</span></span>  
  
     <span data-ttu-id="9ad5c-130">Bir görsel tasarımcı artık kullanılabilir olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="9ad5c-130">Note that a visual designer is no longer available.</span></span> <span data-ttu-id="9ad5c-131">Çünkü <xref:System.Windows.Forms.Button> netimi kendi boyama, Tasarımcı içinde görünümünü değiştirilemedi.</span><span class="sxs-lookup"><span data-stu-id="9ad5c-131">Because the <xref:System.Windows.Forms.Button> control does its own painting, you are unable to modify its appearance in the designer.</span></span> <span data-ttu-id="9ad5c-132">Görsel gösterimine tam olarak aynı sınıfından devralan sınıf olacaktır (diğer bir deyişle, <xref:System.Windows.Forms.Button>) kodda değiştirilmediği sürece.</span><span class="sxs-lookup"><span data-stu-id="9ad5c-132">Its visual representation will be exactly the same as that of the class it inherits from (that is, <xref:System.Windows.Forms.Button>) unless modified in the code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9ad5c-133">Tasarım yüzeyine UI öğesi içermeyen olan bileşenleri eklemeye devam edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9ad5c-133">You can still add components, which have no UI elements, to the design surface.</span></span>  
  
## <a name="adding-a-property-to-your-inherited-control"></a><span data-ttu-id="9ad5c-134">Devralınan denetiminize özellik ekleme</span><span class="sxs-lookup"><span data-stu-id="9ad5c-134">Adding a Property to Your Inherited Control</span></span>  
 <span data-ttu-id="9ad5c-135">Bir olası devralınan Windows Forms denetimleri, standart Windows Forms denetimlerine görünümünü ve davranışını (Görünüm) içinde aynıdır, ancak özel özellikler kullanıma denetimleri oluşturulmasını kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9ad5c-135">One possible use of inherited Windows Forms controls is the creation of controls that are identical in appearance and behavior (look and feel) to standard Windows Forms controls, but expose custom properties.</span></span> <span data-ttu-id="9ad5c-136">Bu bölümde, adlı bir özellik ekleyeceksiniz `ButtonValue` denetiminiz için.</span><span class="sxs-lookup"><span data-stu-id="9ad5c-136">In this section, you will add a property called `ButtonValue` to your control.</span></span>  
  
#### <a name="to-add-the-value-property"></a><span data-ttu-id="9ad5c-137">Value özelliği eklemek için</span><span class="sxs-lookup"><span data-stu-id="9ad5c-137">To add the Value property</span></span>  
  
1. <span data-ttu-id="9ad5c-138">İçinde **Çözüm Gezgini**, sağ **ValueButton.vb**ve ardından **kodu görüntüle** kısayol menüsünden.</span><span class="sxs-lookup"><span data-stu-id="9ad5c-138">In **Solution Explorer**, right-click **ValueButton.vb**, and then click **View Code** from the shortcut menu.</span></span>  
  
2. <span data-ttu-id="9ad5c-139">Bulun `Public Class ValueButton` deyimi.</span><span class="sxs-lookup"><span data-stu-id="9ad5c-139">Locate the `Public Class ValueButton` statement.</span></span> <span data-ttu-id="9ad5c-140">Hemen bu bildirimi, aşağıdaki kodu yazın:</span><span class="sxs-lookup"><span data-stu-id="9ad5c-140">Immediately beneath this statement, type the following code:</span></span>  
  
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
  
     <span data-ttu-id="9ad5c-141">Bu kod yöntemleri olarak ayarlar `ButtonValue` özelliği depolanır ve alınır.</span><span class="sxs-lookup"><span data-stu-id="9ad5c-141">This code sets the methods by which the `ButtonValue` property is stored and retrieved.</span></span> <span data-ttu-id="9ad5c-142">`Get` Deyimi ayarlar özel bir değişkende depolanan değere döndürülen değer `varValue`ve `Set` deyimi kullanarak özel bir değişken değerini ayarlar `Value` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="9ad5c-142">The `Get` statement sets the value returned to the value that is stored in the private variable `varValue`, and the `Set` statement sets the value of the private variable by use of the `Value` keyword.</span></span>  
  
3. <span data-ttu-id="9ad5c-143">Gelen **dosya** menüsünde seçin **Tümünü Kaydet** projeyi kaydetmek için.</span><span class="sxs-lookup"><span data-stu-id="9ad5c-143">From the **File** menu, choose **Save All** to save the project.</span></span>  
  
## <a name="testing-your-control"></a><span data-ttu-id="9ad5c-144">Denetiminiz test etme</span><span class="sxs-lookup"><span data-stu-id="9ad5c-144">Testing Your Control</span></span>  
 <span data-ttu-id="9ad5c-145">Denetimler, tek başına projeleri değildir; Bunlar, bir kapsayıcıda barındırılan gerekir.</span><span class="sxs-lookup"><span data-stu-id="9ad5c-145">Controls are not stand-alone projects; they must be hosted in a container.</span></span> <span data-ttu-id="9ad5c-146">Denetiminiz test etmek için bir test projesi için bunu çalıştırmak için sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="9ad5c-146">In order to test your control, you must provide a test project for it to run in.</span></span> <span data-ttu-id="9ad5c-147">Ayrıca, Denetim test projesi için erişilebilir (derleme) oluşturarak yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="9ad5c-147">You must also make your control accessible to the test project by building (compiling) it.</span></span> <span data-ttu-id="9ad5c-148">Bu bölümde, denetiminizi oluşturup bir Windows formunda test.</span><span class="sxs-lookup"><span data-stu-id="9ad5c-148">In this section, you will build your control and test it in a Windows Form.</span></span>  
  
#### <a name="to-build-your-control"></a><span data-ttu-id="9ad5c-149">Denetim oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="9ad5c-149">To build your control</span></span>  
  
1. <span data-ttu-id="9ad5c-150">Üzerinde **derleme** menüsünde tıklatın **Çözümü Derle**.</span><span class="sxs-lookup"><span data-stu-id="9ad5c-150">On the **Build** menu, click **Build Solution**.</span></span>  
  
     <span data-ttu-id="9ad5c-151">Derleme, derleyici hata veya uyarılar ile başarılı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9ad5c-151">The build should be successful with no compiler errors or warnings.</span></span>  
  
#### <a name="to-create-a-test-project"></a><span data-ttu-id="9ad5c-152">Bir test projesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="9ad5c-152">To create a test project</span></span>  
  
1. <span data-ttu-id="9ad5c-153">Üzerinde **dosya** menüsünde **Ekle** ve ardından **yeni proje** açmak için **Yeni Proje Ekle** iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="9ad5c-153">On the **File** menu, point to **Add** and then click **New Project** to open the **Add New Project** dialog box.</span></span>  
  
2. <span data-ttu-id="9ad5c-154">Visual Basic projeleri düğümünü seçin ve tıklayın **Windows Forms uygulaması**.</span><span class="sxs-lookup"><span data-stu-id="9ad5c-154">Select the Visual Basic projects node, and click **Windows Forms Application**.</span></span>  
  
3. <span data-ttu-id="9ad5c-155">İçinde **adı** kutusuna `Test`.</span><span class="sxs-lookup"><span data-stu-id="9ad5c-155">In the **Name** box, type `Test`.</span></span>  
  
4. <span data-ttu-id="9ad5c-156">İçinde **Çözüm Gezgini**, tıklayın **tüm dosyaları göster** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="9ad5c-156">In **Solution Explorer**, click the **Show All Files** button.</span></span>  
  
5. <span data-ttu-id="9ad5c-157">İçinde **Çözüm Gezgini**, sağ **başvuruları** ardından düğümü test projeniz için **Başvuru Ekle** görüntülemek için kısayol menüsünden  **Başvuru ekleme** iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="9ad5c-157">In **Solution Explorer**, right-click the **References** node for your test project, then select **Add Reference** from the shortcut menu to display the **Add Reference** dialog box.</span></span>  
  
6. <span data-ttu-id="9ad5c-158">Tıklayın **projeleri** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="9ad5c-158">Click the **Projects** tab.</span></span>  
  
7. <span data-ttu-id="9ad5c-159">Etiketli sekmesini **projeleri**.</span><span class="sxs-lookup"><span data-stu-id="9ad5c-159">Click the tab labeled **Projects**.</span></span> <span data-ttu-id="9ad5c-160">`ValueButtonLib` Projesi altında listelenir **proje adı**.</span><span class="sxs-lookup"><span data-stu-id="9ad5c-160">Your `ValueButtonLib` project will be listed under **Project Name**.</span></span> <span data-ttu-id="9ad5c-161">Projeyi test projesinin başvuru eklemek için çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="9ad5c-161">Double-click the project to add the reference to the test project.</span></span>  
  
8. <span data-ttu-id="9ad5c-162">İçinde **Çözüm Gezgini** sağ **Test** seçip **yapı**.</span><span class="sxs-lookup"><span data-stu-id="9ad5c-162">In **Solution Explorer,** right-click **Test** and select **Build**.</span></span>  
  
#### <a name="to-add-your-control-to-the-form"></a><span data-ttu-id="9ad5c-163">Forma denetim ekleme</span><span class="sxs-lookup"><span data-stu-id="9ad5c-163">To add your control to the form</span></span>  
  
1. <span data-ttu-id="9ad5c-164">İçinde **Çözüm Gezgini**, sağ **Form1.vb** ve **Görünüm Tasarımcısı** kısayol menüsünden.</span><span class="sxs-lookup"><span data-stu-id="9ad5c-164">In **Solution Explorer**, right-click **Form1.vb** and choose **View Designer** from the shortcut menu.</span></span>  
  
2. <span data-ttu-id="9ad5c-165">İçinde **araç kutusu**, tıklayın **ValueButtonLib bileşenleri**.</span><span class="sxs-lookup"><span data-stu-id="9ad5c-165">In the **Toolbox**, click **ValueButtonLib Components**.</span></span> <span data-ttu-id="9ad5c-166">Çift **ValueButton**.</span><span class="sxs-lookup"><span data-stu-id="9ad5c-166">Double-click **ValueButton**.</span></span>  
  
     <span data-ttu-id="9ad5c-167">A **ValueButton** formda görünür.</span><span class="sxs-lookup"><span data-stu-id="9ad5c-167">A **ValueButton** appears on the form.</span></span>  
  
3. <span data-ttu-id="9ad5c-168">Sağ **ValueButton** seçip **özellikleri** kısayol menüsünden.</span><span class="sxs-lookup"><span data-stu-id="9ad5c-168">Right-click the **ValueButton** and select **Properties** from the shortcut menu.</span></span>  
  
4. <span data-ttu-id="9ad5c-169">İçinde **özellikleri** penceresinde, bu denetimin özelliklerini inceleyin.</span><span class="sxs-lookup"><span data-stu-id="9ad5c-169">In the **Properties** window, examine the properties of this control.</span></span> <span data-ttu-id="9ad5c-170">Ek bir özellik olduğundan dışında standart bir düğme tarafından kullanıma sunulan özellikleri aynı olduklarını unutmayın `ButtonValue`.</span><span class="sxs-lookup"><span data-stu-id="9ad5c-170">Note that they are identical to the properties exposed by a standard button, except that there is an additional property, `ButtonValue`.</span></span>  
  
5. <span data-ttu-id="9ad5c-171">Ayarlama `ButtonValue` özelliğini `5`.</span><span class="sxs-lookup"><span data-stu-id="9ad5c-171">Set the `ButtonValue` property to `5`.</span></span>  
  
6. <span data-ttu-id="9ad5c-172">Üzerinde **tüm Windows Formları** sekmesinde **araç kutusu**, çift **etiket** eklemek için bir <xref:System.Windows.Forms.Label> form denetimi.</span><span class="sxs-lookup"><span data-stu-id="9ad5c-172">On the **All Windows Forms** tab of the **Toolbox**, double-click **Label** to add a <xref:System.Windows.Forms.Label> control to your form.</span></span>  
  
7. <span data-ttu-id="9ad5c-173">Etiket biçiminin merkezine taşımanızı.</span><span class="sxs-lookup"><span data-stu-id="9ad5c-173">Relocate the label to the center of the form.</span></span>  
  
8. <span data-ttu-id="9ad5c-174">Çift `ValueButton1`.</span><span class="sxs-lookup"><span data-stu-id="9ad5c-174">Double-click `ValueButton1`.</span></span>  
  
     <span data-ttu-id="9ad5c-175">**Kod Düzenleyicisi** açılır `ValueButton1_Click` olay.</span><span class="sxs-lookup"><span data-stu-id="9ad5c-175">The **Code Editor** opens to the `ValueButton1_Click` event.</span></span>  
  
9. <span data-ttu-id="9ad5c-176">Aşağıdaki kod satırını yazın.</span><span class="sxs-lookup"><span data-stu-id="9ad5c-176">Type the following line of code.</span></span>  
  
    ```vb  
    Label1.Text = CStr(ValueButton1.ButtonValue)  
    ```  
  
10. <span data-ttu-id="9ad5c-177">İçinde **Çözüm Gezgini**, sağ **Test**ve **başlangıç projesi olarak ayarla** kısayol menüsünden.</span><span class="sxs-lookup"><span data-stu-id="9ad5c-177">In **Solution Explorer**, right-click **Test**, and choose **Set as Startup Project** from the shortcut menu.</span></span>  
  
11. <span data-ttu-id="9ad5c-178">Gelen **hata ayıklama** menüsünde **hata ayıklamayı Başlat**.</span><span class="sxs-lookup"><span data-stu-id="9ad5c-178">From the **Debug** menu, select **Start Debugging**.</span></span>  
  
     <span data-ttu-id="9ad5c-179">`Form1` görünür.</span><span class="sxs-lookup"><span data-stu-id="9ad5c-179">`Form1` appears.</span></span>  
  
12. <span data-ttu-id="9ad5c-180">Tıklatın `Valuebutton1`.</span><span class="sxs-lookup"><span data-stu-id="9ad5c-180">Click `Valuebutton1`.</span></span>  
  
     <span data-ttu-id="9ad5c-181">'5' sayısal görüntülenen `Label1`elde, `ButtonValue` devralınan denetim özelliği için geçirilmiş `Label1` aracılığıyla `ValueButton1_Click` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="9ad5c-181">The numeral '5' is displayed in `Label1`, demonstrating that the `ButtonValue` property of your inherited control has been passed to `Label1` through the `ValueButton1_Click` method.</span></span> <span data-ttu-id="9ad5c-182">Bu nedenle, `ValueButton` denetimi, standart Windows Forms düğmesini tüm işlevlerini devralır, ancak ek, özel bir özellik sunar.</span><span class="sxs-lookup"><span data-stu-id="9ad5c-182">Thus your `ValueButton` control inherits all the functionality of the standard Windows Forms button, but exposes an additional, custom property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ad5c-183">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9ad5c-183">See also</span></span>

- [<span data-ttu-id="9ad5c-184">İzlenecek yol: Visual Basic ile bileşik denetim yazma</span><span class="sxs-lookup"><span data-stu-id="9ad5c-184">Walkthrough: Authoring a Composite Control with Visual Basic</span></span>](walkthrough-authoring-a-composite-control-with-visual-basic.md)
- [<span data-ttu-id="9ad5c-185">Nasıl yapılır: Bir denetimi görüntüleme araç kutusu öğelerini Seç iletişim kutusu</span><span class="sxs-lookup"><span data-stu-id="9ad5c-185">How to: Display a Control in the Choose Toolbox Items Dialog Box</span></span>](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)
- [<span data-ttu-id="9ad5c-186">.NET Framework ile Özel Windows Forms Denetimleri Geliştirme</span><span class="sxs-lookup"><span data-stu-id="9ad5c-186">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](developing-custom-windows-forms-controls.md)
- [<span data-ttu-id="9ad5c-187">Devralma temelleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9ad5c-187">Inheritance basics (Visual Basic)</span></span>](~/docs/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
