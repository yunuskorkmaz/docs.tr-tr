---
title: "İzlenecek yol: C# ile beraber Windows Forms Denetimi'nden Devralma"
ms.date: 03/30/2017
helpviewer_keywords:
- inheritance [Windows Forms], custom controls
- inheritance [Windows Forms], control
- Windows Forms controls, inheritance
- inheritance [Windows Forms], walkthroughs
- custom controls [Windows Forms], inheritance
ms.assetid: 09476da0-8d4c-4a4c-b969-649519dfb438
ms.openlocfilehash: c06639ef2f2ced8bd128adea636efe8be1715764
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931016"
---
# <a name="walkthrough-inheriting-from-a-windows-forms-control-with-visual-c"></a><span data-ttu-id="3f074-102">İzlenecek yol: Visual C ile Windows Forms denetiminden devralma\#</span><span class="sxs-lookup"><span data-stu-id="3f074-102">Walkthrough: Inheriting from a Windows Forms Control with Visual C\#</span></span>
<span data-ttu-id="3f074-103">Visual C#ile *Devralma*aracılığıyla güçlü özel denetimler oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3f074-103">With Visual C#, you can create powerful custom controls through *inheritance*.</span></span> <span data-ttu-id="3f074-104">Devralma aracılığıyla standart Windows Forms denetimlerinin tüm devralınan işlevlerini koruyan ancak özel işlevleri de birleştiren denetimler oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3f074-104">Through inheritance you are able to create controls that retain all of the inherent functionality of standard Windows Forms controls but also incorporate custom functionality.</span></span> <span data-ttu-id="3f074-105">Bu kılavuzda, adlı `ValueButton`basit bir devralınmış denetim oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="3f074-105">In this walkthrough, you will create a simple inherited control called `ValueButton`.</span></span> <span data-ttu-id="3f074-106">Bu düğme standart Windows Forms <xref:System.Windows.Forms.Button> denetiminden işlevselliği devralacak ve adlı `ButtonValue`özel bir özelliği kullanıma sunacaktır.</span><span class="sxs-lookup"><span data-stu-id="3f074-106">This button will inherit functionality from the standard Windows Forms <xref:System.Windows.Forms.Button> control, and will expose a custom property called `ButtonValue`.</span></span>

## <a name="creating-the-project"></a><span data-ttu-id="3f074-107">Projeyi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="3f074-107">Creating the Project</span></span>
 <span data-ttu-id="3f074-108">Yeni bir proje oluşturduğunuzda, kök ad alanı, derleme adı ve proje adını ayarlamak ve varsayılan bileşenin doğru ad alanında yer aldığından emin olmak için adını belirtin.</span><span class="sxs-lookup"><span data-stu-id="3f074-108">When you create a new project, you specify its name in order to set the root namespace, assembly name, and project name, and to ensure that the default component will be in the correct namespace.</span></span>

### <a name="to-create-the-valuebuttonlib-control-library-and-the-valuebutton-control"></a><span data-ttu-id="3f074-109">ValueButtonLib denetim kitaplığını ve ValueButton denetimini oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="3f074-109">To create the ValueButtonLib control library and the ValueButton control</span></span>

1. <span data-ttu-id="3f074-110">**Dosya** menüsünde, **Yeni** ' nin üzerine gelin ve ardından **Proje** ' ye tıklayarak **Yeni proje** iletişim kutusunu açın.</span><span class="sxs-lookup"><span data-stu-id="3f074-110">On the **File** menu, point to **New** and then click **Project** to open the **New Project** dialog box.</span></span>

2. <span data-ttu-id="3f074-111">Görsel C# proje listesinden **Windows Forms denetim kitaplığı** proje şablonunu seçin ve ad kutusuna yazın. `ValueButtonLib`</span><span class="sxs-lookup"><span data-stu-id="3f074-111">Select the **Windows Forms Control Library** project template from the list of Visual C# Projects, and type `ValueButtonLib` in the **Name** box.</span></span>

     <span data-ttu-id="3f074-112">Proje adı `ValueButtonLib`, varsayılan olarak kök ad alanına da atanır.</span><span class="sxs-lookup"><span data-stu-id="3f074-112">The project name, `ValueButtonLib`, is also assigned to the root namespace by default.</span></span> <span data-ttu-id="3f074-113">Kök ad alanı, derlemedeki bileşenlerin adlarını nitelemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3f074-113">The root namespace is used to qualify the names of components in the assembly.</span></span> <span data-ttu-id="3f074-114">Örneğin, iki derleme adlı `ValueButton`bileşenler içeriyorsa, `ValueButton` bileşenini kullanarak `ValueButtonLib.ValueButton`belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3f074-114">For example, if two assemblies provide components named `ValueButton`, you can specify your `ValueButton` component using `ValueButtonLib.ValueButton`.</span></span> <span data-ttu-id="3f074-115">Daha fazla bilgi için bkz. [ad alanları](../../../csharp/programming-guide/namespaces/index.md).</span><span class="sxs-lookup"><span data-stu-id="3f074-115">For more information, see [Namespaces](../../../csharp/programming-guide/namespaces/index.md).</span></span>

3. <span data-ttu-id="3f074-116">**Çözüm Gezgini**' de, **UserControl1.cs**' a sağ tıklayıp kısayol menüsünden **Yeniden Adlandır** ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="3f074-116">In **Solution Explorer**, right-click **UserControl1.cs**, then choose **Rename** from the shortcut menu.</span></span> <span data-ttu-id="3f074-117">Dosya adını olarak `ValueButton.cs`değiştirin.</span><span class="sxs-lookup"><span data-stu-id="3f074-117">Change the file name to `ValueButton.cs`.</span></span> <span data-ttu-id="3f074-118">'`UserControl1`' Kod öğesine yapılan tüm başvuruları yeniden adlandırmak Isteyip istemediğiniz sorulduğunda **Evet** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="3f074-118">Click the **Yes** button when you are asked if you want to rename all references to the code element '`UserControl1`'.</span></span>

4. <span data-ttu-id="3f074-119">**Çözüm Gezgini**' de, **ValueButton.cs** ' a sağ tıklayın ve **kodu görüntüle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="3f074-119">In **Solution Explorer**, right-click **ValueButton.cs** and select **View Code**.</span></span>

5. <span data-ttu-id="3f074-120">Bildiri satırını bulun ve bu denetimin devraldığı <xref:System.Windows.Forms.UserControl> türü olarak <xref:System.Windows.Forms.Button>değiştirin. `public partial class ValueButton` `class`</span><span class="sxs-lookup"><span data-stu-id="3f074-120">Locate the `class` statement line, `public partial class ValueButton`, and change the type from which this control inherits from <xref:System.Windows.Forms.UserControl> to <xref:System.Windows.Forms.Button>.</span></span> <span data-ttu-id="3f074-121">Bu, <xref:System.Windows.Forms.Button> devralınan denetiminizin tüm denetim işlevlerini devralmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="3f074-121">This allows your inherited control to inherit all the functionality of the <xref:System.Windows.Forms.Button> control.</span></span>

6. <span data-ttu-id="3f074-122">**Çözüm Gezgini**, tasarımcı tarafından oluşturulan kod dosyasını göstermek için **ValueButton.cs** düğümünü açın, **ValueButton.Designer.cs**.</span><span class="sxs-lookup"><span data-stu-id="3f074-122">In **Solution Explorer**, open the **ValueButton.cs** node to display the designer-generated code file, **ValueButton.Designer.cs**.</span></span> <span data-ttu-id="3f074-123">Bu dosyayı **kod düzenleyicisinde**açın.</span><span class="sxs-lookup"><span data-stu-id="3f074-123">Open this file in the **Code Editor**.</span></span>

7. <span data-ttu-id="3f074-124">Yöntemini bulun ve <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> özelliği atayan çizgiyi kaldırın. `InitializeComponent`</span><span class="sxs-lookup"><span data-stu-id="3f074-124">Locate the `InitializeComponent` method and remove the line that assigns the <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> property.</span></span> <span data-ttu-id="3f074-125">Bu özellik <xref:System.Windows.Forms.Button> denetimde yok.</span><span class="sxs-lookup"><span data-stu-id="3f074-125">This property does not exist in the <xref:System.Windows.Forms.Button> control.</span></span>

8. <span data-ttu-id="3f074-126">Projeyi kaydetmek için **Dosya** menüsünden **Tümünü Kaydet** ' i seçin.</span><span class="sxs-lookup"><span data-stu-id="3f074-126">From the **File** menu, choose **Save All** to save the project.</span></span>

    > [!NOTE]
    > <span data-ttu-id="3f074-127">Görsel tasarımcı artık kullanılamıyor.</span><span class="sxs-lookup"><span data-stu-id="3f074-127">A visual designer is no longer available.</span></span> <span data-ttu-id="3f074-128"><xref:System.Windows.Forms.Button> Denetim kendi boyadığı için tasarımcıda görünümünü değiştiremedik.</span><span class="sxs-lookup"><span data-stu-id="3f074-128">Because the <xref:System.Windows.Forms.Button> control does its own painting, you are unable to modify its appearance in the designer.</span></span> <span data-ttu-id="3f074-129">Görsel temsili, kodda değiştirilmediği sürece (yani, <xref:System.Windows.Forms.Button>) devraldığı sınıftan tamamen aynı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="3f074-129">Its visual representation will be exactly the same as that of the class it inherits from (that is, <xref:System.Windows.Forms.Button>) unless modified in the code.</span></span> <span data-ttu-id="3f074-130">Tasarım yüzeyine, UI öğesi içermeyen bileşenler ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3f074-130">You can still add components, which have no UI elements, to the design surface.</span></span>

## <a name="adding-a-property-to-your-inherited-control"></a><span data-ttu-id="3f074-131">Devralınan Denetiecekseniz özellik ekleme</span><span class="sxs-lookup"><span data-stu-id="3f074-131">Adding a Property to Your Inherited Control</span></span>
 <span data-ttu-id="3f074-132">Devralınan Windows Forms denetimlerinin olası bir kullanımı, standart Windows Forms denetimlerinin görünümü ve hisde aynı olan, ancak özel özellikler sunan denetimlerin oluşturulması.</span><span class="sxs-lookup"><span data-stu-id="3f074-132">One possible use of inherited Windows Forms controls is the creation of controls that are identical in look and feel of standard Windows Forms controls, but expose custom properties.</span></span> <span data-ttu-id="3f074-133">Bu bölümde, denetimi adlı `ButtonValue` bir özellik ekleyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="3f074-133">In this section, you will add a property called `ButtonValue` to your control.</span></span>

### <a name="to-add-the-value-property"></a><span data-ttu-id="3f074-134">Değer özelliğini eklemek için</span><span class="sxs-lookup"><span data-stu-id="3f074-134">To add the Value property</span></span>

1. <span data-ttu-id="3f074-135">**Çözüm Gezgini**' de, **ValueButton.cs**' a sağ tıklayın ve ardından kısayol menüsünde **kodu görüntüle** ' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="3f074-135">In **Solution Explorer**, right-click **ValueButton.cs**, and then click **View Code** from the shortcut menu.</span></span>

2. <span data-ttu-id="3f074-136">`class` İfadesini bulun.</span><span class="sxs-lookup"><span data-stu-id="3f074-136">Locate the `class` statement.</span></span> <span data-ttu-id="3f074-137">Hemen sonra `{`, aşağıdaki kodu yazın:</span><span class="sxs-lookup"><span data-stu-id="3f074-137">Immediately after the `{`, type the following code:</span></span>

    ```csharp
    // Creates the private variable that will store the value of your
    // property.
    private int varValue;
    // Declares the property.
    public int ButtonValue
    {
       // Sets the method for retrieving the value of your property.
       get
       {
          return varValue;
       }
       // Sets the method for setting the value of your property.
       set
       {
          varValue = value;
       }
    }
    ```

     <span data-ttu-id="3f074-138">Bu kod, `ButtonValue` özelliğin depolanacağı ve alındığı yöntemleri ayarlar.</span><span class="sxs-lookup"><span data-stu-id="3f074-138">This code sets the methods by which the `ButtonValue` property is stored and retrieved.</span></span> <span data-ttu-id="3f074-139">İfade, döndürülen değeri özel değişkende `varValue`depolanan değere ayarlar ve `set` ifade ise `value` anahtar sözcüğünün kullanımıyla özel değişkenin değerini ayarlar. `get`</span><span class="sxs-lookup"><span data-stu-id="3f074-139">The `get` statement sets the value returned to the value that is stored in the private variable `varValue`, and the `set` statement sets the value of the private variable by use of the `value` keyword.</span></span>

3. <span data-ttu-id="3f074-140">Projeyi kaydetmek için **Dosya** menüsünden **Tümünü Kaydet** ' i seçin.</span><span class="sxs-lookup"><span data-stu-id="3f074-140">From the **File** menu, choose **Save All** to save the project.</span></span>

## <a name="testing-your-control"></a><span data-ttu-id="3f074-141">Denetiminizi test etme</span><span class="sxs-lookup"><span data-stu-id="3f074-141">Testing Your Control</span></span>
 <span data-ttu-id="3f074-142">Denetimler tek başına projeler değildir; Bunlar bir kapsayıcıda barındırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3f074-142">Controls are not stand-alone projects; they must be hosted in a container.</span></span> <span data-ttu-id="3f074-143">Denetiminizi test etmek için, içinde çalışması için bir test projesi sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="3f074-143">In order to test your control, you must provide a test project for it to run in.</span></span> <span data-ttu-id="3f074-144">Ayrıca, denetimi (derleyerek) oluşturarak denetiminizi test projesi için de erişilebilir yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="3f074-144">You must also make your control accessible to the test project by building (compiling) it.</span></span> <span data-ttu-id="3f074-145">Bu bölümde, denetiminizi oluşturacak ve bir Windows formunda test edersiniz.</span><span class="sxs-lookup"><span data-stu-id="3f074-145">In this section, you will build your control and test it in a Windows Form.</span></span>

### <a name="to-build-your-control"></a><span data-ttu-id="3f074-146">Denetiminizi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="3f074-146">To build your control</span></span>

1. <span data-ttu-id="3f074-147">Üzerinde **derleme** menüsünde tıklatın **Çözümü Derle**.</span><span class="sxs-lookup"><span data-stu-id="3f074-147">On the **Build** menu, click **Build Solution**.</span></span>

     <span data-ttu-id="3f074-148">Derleme, derleyici hataları veya uyarıları olmadan başarılı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3f074-148">The build should be successful with no compiler errors or warnings.</span></span>

### <a name="to-create-a-test-project"></a><span data-ttu-id="3f074-149">Bir test projesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="3f074-149">To create a test project</span></span>

1. <span data-ttu-id="3f074-150">**Dosya** menüsünde, **Ekle** ' nin üzerine gelin ve yeni proje ' ye tıklayarak yeni proje **Ekle** iletişim kutusunu açın.</span><span class="sxs-lookup"><span data-stu-id="3f074-150">On the **File** menu, point to **Add** and then click **New Project** to open the **Add New Project** dialog box.</span></span>

2. <span data-ttu-id="3f074-151">**Görsel C#**  düğümün altında **Windows** düğümünü seçin ve **Windows Forms uygulama**' ya tıklayın.</span><span class="sxs-lookup"><span data-stu-id="3f074-151">Select the **Windows** node, beneath the **Visual C#** node, and click **Windows Forms Application**.</span></span>

3. <span data-ttu-id="3f074-152">**Ad** kutusuna yazın `Test`.</span><span class="sxs-lookup"><span data-stu-id="3f074-152">In the **Name** box, type `Test`.</span></span>

4. <span data-ttu-id="3f074-153">**Çözüm Gezgini**, test projeniz için **Başvurular** düğümüne sağ tıklayın ve ardından kısayol menüsünden **Başvuru Ekle** ' yi seçerek **Başvuru Ekle** iletişim kutusunu görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="3f074-153">In **Solution Explorer**, right-click the **References** node for your test project, then select **Add Reference** from the shortcut menu to display the **Add Reference** dialog box.</span></span>

5. <span data-ttu-id="3f074-154">Etiketli **Projeler**sekmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="3f074-154">Click the tab labeled **Projects**.</span></span> <span data-ttu-id="3f074-155">Projeniz proje adı altında listelenir. `ValueButtonLib`</span><span class="sxs-lookup"><span data-stu-id="3f074-155">Your `ValueButtonLib` project will be listed under **Project Name**.</span></span> <span data-ttu-id="3f074-156">Başvuruyu test projesine eklemek için projeye çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="3f074-156">Double-click the project to add the reference to the test project.</span></span>

6. <span data-ttu-id="3f074-157">**Çözüm Gezgini** ' de **Test** ' e sağ tıklayın ve **Oluştur**' u seçin.</span><span class="sxs-lookup"><span data-stu-id="3f074-157">In **Solution Explorer,** right-click **Test** and select **Build**.</span></span>

### <a name="to-add-your-control-to-the-form"></a><span data-ttu-id="3f074-158">Formunuza denetim eklemek için</span><span class="sxs-lookup"><span data-stu-id="3f074-158">To add your control to the form</span></span>

1. <span data-ttu-id="3f074-159">**Çözüm Gezgini**' de, **Form1.cs** ' ye sağ tıklayıp kısayol menüsünden **tasarımcıyı görüntüle** ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="3f074-159">In **Solution Explorer**, right-click **Form1.cs** and choose **View Designer** from the shortcut menu.</span></span>

2. <span data-ttu-id="3f074-160">**Araç kutusunda** **ValueButtonLib bileşenleri**' ne tıklayın.</span><span class="sxs-lookup"><span data-stu-id="3f074-160">In the **Toolbox**, click **ValueButtonLib Components**.</span></span> <span data-ttu-id="3f074-161">**ValueButton**öğesine çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="3f074-161">Double-click **ValueButton**.</span></span>

     <span data-ttu-id="3f074-162">Formda bir **ValueButton** görünür.</span><span class="sxs-lookup"><span data-stu-id="3f074-162">A **ValueButton** appears on the form.</span></span>

3. <span data-ttu-id="3f074-163">**ValueButton** öğesine sağ tıklayın ve kısayol menüsünden **Özellikler** ' i seçin.</span><span class="sxs-lookup"><span data-stu-id="3f074-163">Right-click the **ValueButton** and select **Properties** from the shortcut menu.</span></span>

4. <span data-ttu-id="3f074-164">**Özellikler** penceresinde, bu denetimin özelliklerini inceleyin.</span><span class="sxs-lookup"><span data-stu-id="3f074-164">In the **Properties** window, examine the properties of this control.</span></span> <span data-ttu-id="3f074-165">Bunlar, ek bir özellik `ButtonValue`olması dışında, standart bir düğme tarafından sunulan özelliklerle özdeş olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="3f074-165">Note that they are identical to the properties exposed by a standard button, except that there is an additional property, `ButtonValue`.</span></span>

5. <span data-ttu-id="3f074-166">Ayarlama `ButtonValue` özelliğini `5`.</span><span class="sxs-lookup"><span data-stu-id="3f074-166">Set the `ButtonValue` property to `5`.</span></span>

6. <span data-ttu-id="3f074-167">Formunuza bir<xref:System.Windows.Forms.Label> denetim eklemek için **araç kutusunun** **tüm Windows Forms** sekmesinde etiket ' e çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="3f074-167">In the **All Windows Forms** tab of the **Toolbox**, double-click **Label** to add a <xref:System.Windows.Forms.Label> control to your form.</span></span>

7. <span data-ttu-id="3f074-168">Etiketi formun merkezine yeniden yerleştir.</span><span class="sxs-lookup"><span data-stu-id="3f074-168">Relocate the label to the center of the form.</span></span>

8. <span data-ttu-id="3f074-169">Çift tıklayın `valueButton1`.</span><span class="sxs-lookup"><span data-stu-id="3f074-169">Double-click `valueButton1`.</span></span>

     <span data-ttu-id="3f074-170">**Kod Düzenleyicisi** `valueButton1_Click` olay olarak açılır.</span><span class="sxs-lookup"><span data-stu-id="3f074-170">The **Code Editor** opens to the `valueButton1_Click` event.</span></span>

9. <span data-ttu-id="3f074-171">Aşağıdaki kod satırını ekleyin.</span><span class="sxs-lookup"><span data-stu-id="3f074-171">Insert the following line of code.</span></span>

    ```csharp
    label1.Text = valueButton1.ButtonValue.ToString();
    ```

10. <span data-ttu-id="3f074-172">**Çözüm Gezgini**' de **Test**' e sağ tıklayın ve kısayol menüsünde **Başlangıç projesi olarak ayarla** ' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="3f074-172">In **Solution Explorer**, right-click **Test**, and choose **Set as Startup Project** from the shortcut menu.</span></span>

11. <span data-ttu-id="3f074-173">**Hata Ayıkla** menüsünden **hata ayıklamayı Başlat**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="3f074-173">From the **Debug** menu, select **Start Debugging**.</span></span>

     <span data-ttu-id="3f074-174">`Form1`görüneceği.</span><span class="sxs-lookup"><span data-stu-id="3f074-174">`Form1` appears.</span></span>

12. <span data-ttu-id="3f074-175">Tıklatın `valueButton1`.</span><span class="sxs-lookup"><span data-stu-id="3f074-175">Click `valueButton1`.</span></span>

     <span data-ttu-id="3f074-176">' 5 ' rakamı `label1`, devralınan `label1` denetiminizin `ButtonValue` özelliğinin `valueButton1_Click` yöntemi aracılığıyla geçirildiğini gösteren içinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="3f074-176">The numeral '5' is displayed in `label1`, demonstrating that the `ButtonValue` property of your inherited control has been passed to `label1` through the `valueButton1_Click` method.</span></span> <span data-ttu-id="3f074-177">`ValueButton` Böylece denetiminiz standart Windows Forms düğmesinin tüm işlevlerini devralır, ancak ek, özel bir özellik sunar.</span><span class="sxs-lookup"><span data-stu-id="3f074-177">Thus your `ValueButton` control inherits all the functionality of the standard Windows Forms button, but exposes an additional, custom property.</span></span>

## <a name="see-also"></a><span data-ttu-id="3f074-178">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3f074-178">See also</span></span>

- [<span data-ttu-id="3f074-179">Nasıl yapılır: Araç kutusu öğelerini Seç Iletişim kutusunda bir denetim görüntüle</span><span class="sxs-lookup"><span data-stu-id="3f074-179">How to: Display a Control in the Choose Toolbox Items Dialog Box</span></span>](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)
- [<span data-ttu-id="3f074-180">İzlenecek yol: Visual ile bileşik denetim yazmaC#</span><span class="sxs-lookup"><span data-stu-id="3f074-180">Walkthrough: Authoring a Composite Control with Visual C#</span></span>](walkthrough-authoring-a-composite-control-with-visual-csharp.md)
