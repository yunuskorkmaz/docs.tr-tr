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
ms.openlocfilehash: 0891b64fdb26953ab90f3da931f04513ac9e8bcf
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040221"
---
# <a name="walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic"></a><span data-ttu-id="92c10-102">İzlenecek yol: Visual Basic ile beraber Windows Forms Denetimi'nden Devralma</span><span class="sxs-lookup"><span data-stu-id="92c10-102">Walkthrough: Inheriting from a Windows Forms Control with Visual Basic</span></span>
<span data-ttu-id="92c10-103">Visual Basic, *Devralma*aracılığıyla güçlü özel denetimler oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="92c10-103">With Visual Basic, you can create powerful custom controls through *inheritance*.</span></span> <span data-ttu-id="92c10-104">Devralma aracılığıyla standart Windows Forms denetimlerinin tüm devralınan işlevlerini koruyan ancak özel işlevleri de birleştiren denetimler oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="92c10-104">Through inheritance you are able to create controls that retain all of the inherent functionality of standard Windows Forms controls but also incorporate custom functionality.</span></span> <span data-ttu-id="92c10-105">Bu kılavuzda, adlı `ValueButton`basit bir devralınmış denetim oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="92c10-105">In this walkthrough, you will create a simple inherited control called `ValueButton`.</span></span> <span data-ttu-id="92c10-106">Bu düğme standart Windows Forms <xref:System.Windows.Forms.Button> denetiminden işlevselliği devralacak ve adlı `ButtonValue`özel bir özelliği kullanıma sunacaktır.</span><span class="sxs-lookup"><span data-stu-id="92c10-106">This button will inherit functionality from the standard Windows Forms <xref:System.Windows.Forms.Button> control, and will expose a custom property called `ButtonValue`.</span></span>

## <a name="creating-the-project"></a><span data-ttu-id="92c10-107">Projeyi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="92c10-107">Creating the Project</span></span>
 <span data-ttu-id="92c10-108">Yeni bir proje oluşturduğunuzda, kök ad alanı, derleme adı ve proje adını ayarlamak ve varsayılan bileşenin doğru ad alanında yer aldığından emin olmak için adını belirtin.</span><span class="sxs-lookup"><span data-stu-id="92c10-108">When you create a new project, you specify its name in order to set the root namespace, assembly name, and project name, and to ensure that the default component will be in the correct namespace.</span></span>

### <a name="to-create-the-valuebuttonlib-control-library-and-the-valuebutton-control"></a><span data-ttu-id="92c10-109">ValueButtonLib denetim kitaplığını ve ValueButton denetimini oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="92c10-109">To create the ValueButtonLib control library and the ValueButton control</span></span>

1. <span data-ttu-id="92c10-110">**Dosya** menüsünde, **Yeni** ' nin üzerine gelin ve ardından **Proje** ' ye tıklayarak **Yeni proje** iletişim kutusunu açın.</span><span class="sxs-lookup"><span data-stu-id="92c10-110">On the **File** menu, point to **New** and then click **Project** to open the **New Project** dialog box.</span></span>

2. <span data-ttu-id="92c10-111">Visual Basic projeleri listesinden **Windows Forms denetim kitaplığı** proje şablonunu seçin ve `ValueButtonLib` **ad** kutusuna yazın.</span><span class="sxs-lookup"><span data-stu-id="92c10-111">Select the **Windows Forms Control Library** project template from the list of Visual Basic projects, and type `ValueButtonLib` in the **Name** box.</span></span>

     <span data-ttu-id="92c10-112">Proje adı `ValueButtonLib`, varsayılan olarak kök ad alanına da atanır.</span><span class="sxs-lookup"><span data-stu-id="92c10-112">The project name, `ValueButtonLib`, is also assigned to the root namespace by default.</span></span> <span data-ttu-id="92c10-113">Kök ad alanı, derlemedeki bileşenlerin adlarını nitelemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="92c10-113">The root namespace is used to qualify the names of components in the assembly.</span></span> <span data-ttu-id="92c10-114">Örneğin, iki derleme adlı `ValueButton`bileşenler içeriyorsa, `ValueButton` bileşenini kullanarak `ValueButtonLib.ValueButton`belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="92c10-114">For example, if two assemblies provide components named `ValueButton`, you can specify your `ValueButton` component using `ValueButtonLib.ValueButton`.</span></span> <span data-ttu-id="92c10-115">Daha fazla bilgi için bkz. [Visual Basic ad alanları](~/docs/visual-basic/programming-guide/program-structure/namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="92c10-115">For more information, see [Namespaces in Visual Basic](~/docs/visual-basic/programming-guide/program-structure/namespaces.md).</span></span>

3. <span data-ttu-id="92c10-116">**Çözüm Gezgini**' de, **UserControl1. vb**öğesine sağ tıklayın ve ardından kısayol menüsünde **Yeniden Adlandır** ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="92c10-116">In **Solution Explorer**, right-click **UserControl1.vb**, then choose **Rename** from the shortcut menu.</span></span> <span data-ttu-id="92c10-117">Dosya adını olarak `ValueButton.vb`değiştirin.</span><span class="sxs-lookup"><span data-stu-id="92c10-117">Change the file name to `ValueButton.vb`.</span></span> <span data-ttu-id="92c10-118">' UserControl1 ' kod öğesiyle tüm başvuruları yeniden adlandırmak isteyip istemediğiniz sorulduğunda **Evet** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="92c10-118">Click the **Yes** button when you are asked if you want to rename all references to the code element 'UserControl1'.</span></span>

4. <span data-ttu-id="92c10-119">**Çözüm Gezgini**, **tüm dosyaları göster** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="92c10-119">In **Solution Explorer**, click the **Show All Files** button.</span></span>

5. <span data-ttu-id="92c10-120">Tasarımcı tarafından oluşturulan kod dosyasını, **ValueButton. Designer. vb**öğesini göstermek Için **ValueButton. vb** düğümünü açın.</span><span class="sxs-lookup"><span data-stu-id="92c10-120">Open the **ValueButton.vb** node to display the designer-generated code file, **ValueButton.Designer.vb**.</span></span> <span data-ttu-id="92c10-121">Bu dosyayı **kod düzenleyicisinde**açın.</span><span class="sxs-lookup"><span data-stu-id="92c10-121">Open this file in the **Code Editor**.</span></span>

6. <span data-ttu-id="92c10-122">İfadesini bulun ve bu denetimin devraldığı <xref:System.Windows.Forms.UserControl> türü olarak <xref:System.Windows.Forms.Button>değiştirin. `Partial Public Class ValueButton` `Class`</span><span class="sxs-lookup"><span data-stu-id="92c10-122">Locate the `Class` statement, `Partial Public Class ValueButton`, and change the type from which this control inherits from <xref:System.Windows.Forms.UserControl> to <xref:System.Windows.Forms.Button>.</span></span> <span data-ttu-id="92c10-123">Bu, <xref:System.Windows.Forms.Button> devralınan denetiminizin tüm denetim işlevlerini devralmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="92c10-123">This allows your inherited control to inherit all the functionality of the <xref:System.Windows.Forms.Button> control.</span></span>

7. <span data-ttu-id="92c10-124">Yöntemini bulun ve <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> özelliği atayan çizgiyi kaldırın. `InitializeComponent`</span><span class="sxs-lookup"><span data-stu-id="92c10-124">Locate the `InitializeComponent` method and remove the line that assigns the <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> property.</span></span> <span data-ttu-id="92c10-125">Bu özellik <xref:System.Windows.Forms.Button> denetimde yok.</span><span class="sxs-lookup"><span data-stu-id="92c10-125">This property does not exist in the <xref:System.Windows.Forms.Button> control.</span></span>

8. <span data-ttu-id="92c10-126">Projeyi kaydetmek için **Dosya** menüsünden **Tümünü Kaydet** ' i seçin.</span><span class="sxs-lookup"><span data-stu-id="92c10-126">From the **File** menu, choose **Save All** to save the project.</span></span>

     <span data-ttu-id="92c10-127">Görsel tasarımcı 'nın artık mevcut olmadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="92c10-127">Note that a visual designer is no longer available.</span></span> <span data-ttu-id="92c10-128"><xref:System.Windows.Forms.Button> Denetim kendi boyadığı için tasarımcıda görünümünü değiştiremedik.</span><span class="sxs-lookup"><span data-stu-id="92c10-128">Because the <xref:System.Windows.Forms.Button> control does its own painting, you are unable to modify its appearance in the designer.</span></span> <span data-ttu-id="92c10-129">Görsel temsili, kodda değiştirilmediği sürece (yani, <xref:System.Windows.Forms.Button>) devraldığı sınıftan tamamen aynı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="92c10-129">Its visual representation will be exactly the same as that of the class it inherits from (that is, <xref:System.Windows.Forms.Button>) unless modified in the code.</span></span>

> [!NOTE]
>  <span data-ttu-id="92c10-130">Tasarım yüzeyine, UI öğesi içermeyen bileşenler ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="92c10-130">You can still add components, which have no UI elements, to the design surface.</span></span>

## <a name="adding-a-property-to-your-inherited-control"></a><span data-ttu-id="92c10-131">Devralınan Denetiecekseniz özellik ekleme</span><span class="sxs-lookup"><span data-stu-id="92c10-131">Adding a Property to Your Inherited Control</span></span>
 <span data-ttu-id="92c10-132">Devralınan Windows Forms denetimlerinin olası bir kullanımı, standart Windows Forms denetimlerine benzer görünüm ve davranışta (göz atın) ve özel özellikleri kullanıma sunan denetimlerin oluşturulması.</span><span class="sxs-lookup"><span data-stu-id="92c10-132">One possible use of inherited Windows Forms controls is the creation of controls that are identical in appearance and behavior (look and feel) to standard Windows Forms controls, but expose custom properties.</span></span> <span data-ttu-id="92c10-133">Bu bölümde, denetimi adlı `ButtonValue` bir özellik ekleyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="92c10-133">In this section, you will add a property called `ButtonValue` to your control.</span></span>

### <a name="to-add-the-value-property"></a><span data-ttu-id="92c10-134">Değer özelliğini eklemek için</span><span class="sxs-lookup"><span data-stu-id="92c10-134">To add the Value property</span></span>

1. <span data-ttu-id="92c10-135">**Çözüm Gezgini**, **ValueButton. vb**öğesine sağ tıklayın ve ardından kısayol menüsünde **kodu görüntüle** ' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="92c10-135">In **Solution Explorer**, right-click **ValueButton.vb**, and then click **View Code** from the shortcut menu.</span></span>

2. <span data-ttu-id="92c10-136">`Public Class ValueButton` İfadesini bulun.</span><span class="sxs-lookup"><span data-stu-id="92c10-136">Locate the `Public Class ValueButton` statement.</span></span> <span data-ttu-id="92c10-137">Bu deyimin hemen altına aşağıdaki kodu yazın:</span><span class="sxs-lookup"><span data-stu-id="92c10-137">Immediately beneath this statement, type the following code:</span></span>

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

     <span data-ttu-id="92c10-138">Bu kod, `ButtonValue` özelliğin depolanacağı ve alındığı yöntemleri ayarlar.</span><span class="sxs-lookup"><span data-stu-id="92c10-138">This code sets the methods by which the `ButtonValue` property is stored and retrieved.</span></span> <span data-ttu-id="92c10-139">İfade, döndürülen değeri özel değişkende `varValue`depolanan değere ayarlar ve `Set` ifade ise `Value` anahtar sözcüğünün kullanımıyla özel değişkenin değerini ayarlar. `Get`</span><span class="sxs-lookup"><span data-stu-id="92c10-139">The `Get` statement sets the value returned to the value that is stored in the private variable `varValue`, and the `Set` statement sets the value of the private variable by use of the `Value` keyword.</span></span>

3. <span data-ttu-id="92c10-140">Projeyi kaydetmek için **Dosya** menüsünden **Tümünü Kaydet** ' i seçin.</span><span class="sxs-lookup"><span data-stu-id="92c10-140">From the **File** menu, choose **Save All** to save the project.</span></span>

## <a name="testing-your-control"></a><span data-ttu-id="92c10-141">Denetiminizi test etme</span><span class="sxs-lookup"><span data-stu-id="92c10-141">Testing Your Control</span></span>
 <span data-ttu-id="92c10-142">Denetimler tek başına projeler değildir; Bunlar bir kapsayıcıda barındırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="92c10-142">Controls are not stand-alone projects; they must be hosted in a container.</span></span> <span data-ttu-id="92c10-143">Denetiminizi test etmek için, içinde çalışması için bir test projesi sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="92c10-143">In order to test your control, you must provide a test project for it to run in.</span></span> <span data-ttu-id="92c10-144">Ayrıca, denetimi (derleyerek) oluşturarak denetiminizi test projesi için de erişilebilir yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="92c10-144">You must also make your control accessible to the test project by building (compiling) it.</span></span> <span data-ttu-id="92c10-145">Bu bölümde, denetiminizi oluşturacak ve bir Windows formunda test edersiniz.</span><span class="sxs-lookup"><span data-stu-id="92c10-145">In this section, you will build your control and test it in a Windows Form.</span></span>

### <a name="to-build-your-control"></a><span data-ttu-id="92c10-146">Denetiminizi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="92c10-146">To build your control</span></span>

1. <span data-ttu-id="92c10-147">Üzerinde **derleme** menüsünde tıklatın **Çözümü Derle**.</span><span class="sxs-lookup"><span data-stu-id="92c10-147">On the **Build** menu, click **Build Solution**.</span></span>

     <span data-ttu-id="92c10-148">Derleme, derleyici hataları veya uyarıları olmadan başarılı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="92c10-148">The build should be successful with no compiler errors or warnings.</span></span>

### <a name="to-create-a-test-project"></a><span data-ttu-id="92c10-149">Bir test projesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="92c10-149">To create a test project</span></span>

1. <span data-ttu-id="92c10-150">**Dosya** menüsünde, **Ekle** ' nin üzerine gelin ve yeni proje ' ye tıklayarak yeni proje **Ekle** iletişim kutusunu açın.</span><span class="sxs-lookup"><span data-stu-id="92c10-150">On the **File** menu, point to **Add** and then click **New Project** to open the **Add New Project** dialog box.</span></span>

2. <span data-ttu-id="92c10-151">Visual Basic projeler düğümünü seçin ve **Windows Forms uygulama**' ya tıklayın.</span><span class="sxs-lookup"><span data-stu-id="92c10-151">Select the Visual Basic projects node, and click **Windows Forms Application**.</span></span>

3. <span data-ttu-id="92c10-152">**Ad** kutusuna yazın `Test`.</span><span class="sxs-lookup"><span data-stu-id="92c10-152">In the **Name** box, type `Test`.</span></span>

4. <span data-ttu-id="92c10-153">**Çözüm Gezgini**, **tüm dosyaları göster** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="92c10-153">In **Solution Explorer**, click the **Show All Files** button.</span></span>

5. <span data-ttu-id="92c10-154">**Çözüm Gezgini**, test projeniz için **Başvurular** düğümüne sağ tıklayın ve ardından kısayol menüsünden **Başvuru Ekle** ' yi seçerek **Başvuru Ekle** iletişim kutusunu görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="92c10-154">In **Solution Explorer**, right-click the **References** node for your test project, then select **Add Reference** from the shortcut menu to display the **Add Reference** dialog box.</span></span>

6. <span data-ttu-id="92c10-155">**Projeler** sekmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="92c10-155">Click the **Projects** tab.</span></span>

7. <span data-ttu-id="92c10-156">Etiketli **Projeler**sekmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="92c10-156">Click the tab labeled **Projects**.</span></span> <span data-ttu-id="92c10-157">Projeniz proje adı altında listelenir. `ValueButtonLib`</span><span class="sxs-lookup"><span data-stu-id="92c10-157">Your `ValueButtonLib` project will be listed under **Project Name**.</span></span> <span data-ttu-id="92c10-158">Başvuruyu test projesine eklemek için projeye çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="92c10-158">Double-click the project to add the reference to the test project.</span></span>

8. <span data-ttu-id="92c10-159">**Çözüm Gezgini** ' de **Test** ' e sağ tıklayın ve **Oluştur**' u seçin.</span><span class="sxs-lookup"><span data-stu-id="92c10-159">In **Solution Explorer,** right-click **Test** and select **Build**.</span></span>

### <a name="to-add-your-control-to-the-form"></a><span data-ttu-id="92c10-160">Formunuza denetim eklemek için</span><span class="sxs-lookup"><span data-stu-id="92c10-160">To add your control to the form</span></span>

1. <span data-ttu-id="92c10-161">**Çözüm Gezgini**, **Form1. vb** öğesine sağ tıklayıp kısayol menüsünden **tasarımcıyı görüntüle** ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="92c10-161">In **Solution Explorer**, right-click **Form1.vb** and choose **View Designer** from the shortcut menu.</span></span>

2. <span data-ttu-id="92c10-162">**Araç kutusunda** **ValueButtonLib bileşenleri**' ne tıklayın.</span><span class="sxs-lookup"><span data-stu-id="92c10-162">In the **Toolbox**, click **ValueButtonLib Components**.</span></span> <span data-ttu-id="92c10-163">**ValueButton**öğesine çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="92c10-163">Double-click **ValueButton**.</span></span>

     <span data-ttu-id="92c10-164">Formda bir **ValueButton** görünür.</span><span class="sxs-lookup"><span data-stu-id="92c10-164">A **ValueButton** appears on the form.</span></span>

3. <span data-ttu-id="92c10-165">**ValueButton** öğesine sağ tıklayın ve kısayol menüsünden **Özellikler** ' i seçin.</span><span class="sxs-lookup"><span data-stu-id="92c10-165">Right-click the **ValueButton** and select **Properties** from the shortcut menu.</span></span>

4. <span data-ttu-id="92c10-166">**Özellikler** penceresinde, bu denetimin özelliklerini inceleyin.</span><span class="sxs-lookup"><span data-stu-id="92c10-166">In the **Properties** window, examine the properties of this control.</span></span> <span data-ttu-id="92c10-167">Bunlar, ek bir özellik `ButtonValue`olması dışında, standart bir düğme tarafından sunulan özelliklerle özdeş olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="92c10-167">Note that they are identical to the properties exposed by a standard button, except that there is an additional property, `ButtonValue`.</span></span>

5. <span data-ttu-id="92c10-168">Ayarlama `ButtonValue` özelliğini `5`.</span><span class="sxs-lookup"><span data-stu-id="92c10-168">Set the `ButtonValue` property to `5`.</span></span>

6. <span data-ttu-id="92c10-169">Formunuza bir<xref:System.Windows.Forms.Label> denetim eklemek için **araç kutusunun** **tüm Windows Forms** sekmesinde etiket ' e çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="92c10-169">On the **All Windows Forms** tab of the **Toolbox**, double-click **Label** to add a <xref:System.Windows.Forms.Label> control to your form.</span></span>

7. <span data-ttu-id="92c10-170">Etiketi formun merkezine yeniden yerleştir.</span><span class="sxs-lookup"><span data-stu-id="92c10-170">Relocate the label to the center of the form.</span></span>

8. <span data-ttu-id="92c10-171">Çift tıklayın `ValueButton1`.</span><span class="sxs-lookup"><span data-stu-id="92c10-171">Double-click `ValueButton1`.</span></span>

     <span data-ttu-id="92c10-172">**Kod Düzenleyicisi** `ValueButton1_Click` olay olarak açılır.</span><span class="sxs-lookup"><span data-stu-id="92c10-172">The **Code Editor** opens to the `ValueButton1_Click` event.</span></span>

9. <span data-ttu-id="92c10-173">Aşağıdaki kod satırını yazın.</span><span class="sxs-lookup"><span data-stu-id="92c10-173">Type the following line of code.</span></span>

    ```vb
    Label1.Text = CStr(ValueButton1.ButtonValue)
    ```

10. <span data-ttu-id="92c10-174">**Çözüm Gezgini**' de **Test**' e sağ tıklayın ve kısayol menüsünde **Başlangıç projesi olarak ayarla** ' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="92c10-174">In **Solution Explorer**, right-click **Test**, and choose **Set as Startup Project** from the shortcut menu.</span></span>

11. <span data-ttu-id="92c10-175">**Hata Ayıkla** menüsünden **hata ayıklamayı Başlat**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="92c10-175">From the **Debug** menu, select **Start Debugging**.</span></span>

     <span data-ttu-id="92c10-176">`Form1`görüneceği.</span><span class="sxs-lookup"><span data-stu-id="92c10-176">`Form1` appears.</span></span>

12. <span data-ttu-id="92c10-177">Tıklatın `Valuebutton1`.</span><span class="sxs-lookup"><span data-stu-id="92c10-177">Click `Valuebutton1`.</span></span>

     <span data-ttu-id="92c10-178">' 5 ' rakamı `Label1`, devralınan `Label1` denetiminizin `ButtonValue` özelliğinin `ValueButton1_Click` yöntemi aracılığıyla geçirildiğini gösteren içinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="92c10-178">The numeral '5' is displayed in `Label1`, demonstrating that the `ButtonValue` property of your inherited control has been passed to `Label1` through the `ValueButton1_Click` method.</span></span> <span data-ttu-id="92c10-179">`ValueButton` Böylece denetiminiz standart Windows Forms düğmesinin tüm işlevlerini devralır, ancak ek, özel bir özellik sunar.</span><span class="sxs-lookup"><span data-stu-id="92c10-179">Thus your `ValueButton` control inherits all the functionality of the standard Windows Forms button, but exposes an additional, custom property.</span></span>

## <a name="see-also"></a><span data-ttu-id="92c10-180">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="92c10-180">See also</span></span>

- [<span data-ttu-id="92c10-181">İzlenecek yol: Visual Basic ile bileşik denetim yazma</span><span class="sxs-lookup"><span data-stu-id="92c10-181">Walkthrough: Authoring a Composite Control with Visual Basic</span></span>](walkthrough-authoring-a-composite-control-with-visual-basic.md)
- [<span data-ttu-id="92c10-182">Nasıl yapılır: Araç kutusu öğelerini Seç Iletişim kutusunda bir denetim görüntüle</span><span class="sxs-lookup"><span data-stu-id="92c10-182">How to: Display a Control in the Choose Toolbox Items Dialog Box</span></span>](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)
- [<span data-ttu-id="92c10-183">.NET Framework ile Özel Windows Forms Denetimleri Geliştirme</span><span class="sxs-lookup"><span data-stu-id="92c10-183">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](developing-custom-windows-forms-controls.md)
- [<span data-ttu-id="92c10-184">Devralma Temelleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="92c10-184">Inheritance basics (Visual Basic)</span></span>](~/docs/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
