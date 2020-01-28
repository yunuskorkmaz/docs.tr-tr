---
title: Denetimden Devralma
ms.date: 03/30/2017
helpviewer_keywords:
- inheritance [Windows Forms], custom controls
- inheritance [Windows Forms], control
- Windows Forms controls, inheritance
- inheritance [Windows Forms], walkthroughs
- custom controls [Windows Forms], inheritance
ms.assetid: 09476da0-8d4c-4a4c-b969-649519dfb438
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 713ccf97a73ce9684b9124a121369f22751861d0
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740143"
---
# <a name="walkthrough-inherit-from-a-windows-forms-control-with-c"></a><span data-ttu-id="0f66a-102">İzlenecek yol: C\# ile Windows Forms denetiminden devralma</span><span class="sxs-lookup"><span data-stu-id="0f66a-102">Walkthrough: Inherit from a Windows Forms Control with C\#</span></span>

<span data-ttu-id="0f66a-103">İle C# *Devralma*yoluyla güçlü özel denetimler oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0f66a-103">With C#, you can create powerful custom controls through *inheritance*.</span></span> <span data-ttu-id="0f66a-104">Devralma aracılığıyla standart Windows Forms denetimlerinin tüm devralınan işlevlerini koruyan ancak özel işlevleri de birleştiren denetimler oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0f66a-104">Through inheritance you are able to create controls that retain all of the inherent functionality of standard Windows Forms controls but also incorporate custom functionality.</span></span> <span data-ttu-id="0f66a-105">Bu izlenecek yolda, `ValueButton`adlı basit bir devralınmış denetim oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="0f66a-105">In this walkthrough, you will create a simple inherited control called `ValueButton`.</span></span> <span data-ttu-id="0f66a-106">Bu düğme standart Windows Forms <xref:System.Windows.Forms.Button> denetiminden işlevselliği devralacak ve `ButtonValue`adlı özel bir özelliği kullanıma sunacaktır.</span><span class="sxs-lookup"><span data-stu-id="0f66a-106">This button will inherit functionality from the standard Windows Forms <xref:System.Windows.Forms.Button> control, and will expose a custom property called `ButtonValue`.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="0f66a-107">Projeyi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="0f66a-107">Create the Project</span></span>

<span data-ttu-id="0f66a-108">Yeni bir proje oluşturduğunuzda, kök ad alanı, derleme adı ve proje adını ayarlamak ve varsayılan bileşenin doğru ad alanında yer aldığından emin olmak için adını belirtin.</span><span class="sxs-lookup"><span data-stu-id="0f66a-108">When you create a new project, you specify its name in order to set the root namespace, assembly name, and project name, and to ensure that the default component will be in the correct namespace.</span></span>

### <a name="to-create-the-valuebuttonlib-control-library-and-the-valuebutton-control"></a><span data-ttu-id="0f66a-109">ValueButtonLib denetim kitaplığını ve ValueButton denetimini oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="0f66a-109">To create the ValueButtonLib control library and the ValueButton control</span></span>

1. <span data-ttu-id="0f66a-110">Visual Studio 'da yeni bir **Windows Forms denetim kitaplığı** projesi oluşturun ve **ValueButtonLib**olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="0f66a-110">In Visual Studio, create a new **Windows Forms Control Library** project, and name it **ValueButtonLib**.</span></span>

     <span data-ttu-id="0f66a-111">`ValueButtonLib`proje adı, varsayılan olarak kök ad alanına da atanır.</span><span class="sxs-lookup"><span data-stu-id="0f66a-111">The project name, `ValueButtonLib`, is also assigned to the root namespace by default.</span></span> <span data-ttu-id="0f66a-112">Kök ad alanı, derlemedeki bileşenlerin adlarını nitelemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0f66a-112">The root namespace is used to qualify the names of components in the assembly.</span></span> <span data-ttu-id="0f66a-113">Örneğin, iki derleme `ValueButton`adlı bileşenler sağlamışsa, `ValueButtonLib.ValueButton`kullanarak `ValueButton` bileşenini belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0f66a-113">For example, if two assemblies provide components named `ValueButton`, you can specify your `ValueButton` component using `ValueButtonLib.ValueButton`.</span></span> <span data-ttu-id="0f66a-114">Daha fazla bilgi için bkz. [ad alanları](../../../csharp/programming-guide/namespaces/index.md).</span><span class="sxs-lookup"><span data-stu-id="0f66a-114">For more information, see [Namespaces](../../../csharp/programming-guide/namespaces/index.md).</span></span>

2. <span data-ttu-id="0f66a-115">**Çözüm Gezgini**' de, **UserControl1.cs**' a sağ tıklayıp kısayol menüsünden **Yeniden Adlandır** ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="0f66a-115">In **Solution Explorer**, right-click **UserControl1.cs**, then choose **Rename** from the shortcut menu.</span></span> <span data-ttu-id="0f66a-116">Dosya adını **ValueButton.cs**olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="0f66a-116">Change the file name to **ValueButton.cs**.</span></span> <span data-ttu-id="0f66a-117">'`UserControl1`' kod öğesiyle tüm başvuruları yeniden adlandırmak isteyip istemediğiniz sorulduğunda **Evet** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="0f66a-117">Click the **Yes** button when you are asked if you want to rename all references to the code element '`UserControl1`'.</span></span>

3. <span data-ttu-id="0f66a-118">**Çözüm Gezgini**' de, **ValueButton.cs** ' a sağ tıklayın ve **kodu görüntüle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="0f66a-118">In **Solution Explorer**, right-click **ValueButton.cs** and select **View Code**.</span></span>

4. <span data-ttu-id="0f66a-119">`class` bildiri satırını bulun, `public partial class ValueButton`ve bu denetimin devraldığı türü <xref:System.Windows.Forms.UserControl> <xref:System.Windows.Forms.Button>olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="0f66a-119">Locate the `class` statement line, `public partial class ValueButton`, and change the type from which this control inherits from <xref:System.Windows.Forms.UserControl> to <xref:System.Windows.Forms.Button>.</span></span> <span data-ttu-id="0f66a-120">Bu, devralınan denetiminizin <xref:System.Windows.Forms.Button> denetiminin tüm işlevlerini devralmasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="0f66a-120">This allows your inherited control to inherit all the functionality of the <xref:System.Windows.Forms.Button> control.</span></span>

5. <span data-ttu-id="0f66a-121">**Çözüm Gezgini**, tasarımcı tarafından oluşturulan kod dosyasını göstermek için **ValueButton.cs** düğümünü açın, **ValueButton.Designer.cs**.</span><span class="sxs-lookup"><span data-stu-id="0f66a-121">In **Solution Explorer**, open the **ValueButton.cs** node to display the designer-generated code file, **ValueButton.Designer.cs**.</span></span> <span data-ttu-id="0f66a-122">Bu dosyayı **kod düzenleyicisinde**açın.</span><span class="sxs-lookup"><span data-stu-id="0f66a-122">Open this file in the **Code Editor**.</span></span>

6. <span data-ttu-id="0f66a-123">`InitializeComponent` yöntemini bulun ve <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> özelliğini atayan çizgiyi kaldırın.</span><span class="sxs-lookup"><span data-stu-id="0f66a-123">Locate the `InitializeComponent` method and remove the line that assigns the <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> property.</span></span> <span data-ttu-id="0f66a-124">Bu özellik <xref:System.Windows.Forms.Button> denetiminde yok.</span><span class="sxs-lookup"><span data-stu-id="0f66a-124">This property does not exist in the <xref:System.Windows.Forms.Button> control.</span></span>

7. <span data-ttu-id="0f66a-125">Projeyi kaydetmek için **Dosya** menüsünden **Tümünü Kaydet** ' i seçin.</span><span class="sxs-lookup"><span data-stu-id="0f66a-125">From the **File** menu, choose **Save All** to save the project.</span></span>

    > [!NOTE]
    > <span data-ttu-id="0f66a-126">Görsel tasarımcı artık kullanılamıyor.</span><span class="sxs-lookup"><span data-stu-id="0f66a-126">A visual designer is no longer available.</span></span> <span data-ttu-id="0f66a-127"><xref:System.Windows.Forms.Button> denetimi kendi boyadığı için, tasarımcıda görünümünü değiştiremedik.</span><span class="sxs-lookup"><span data-stu-id="0f66a-127">Because the <xref:System.Windows.Forms.Button> control does its own painting, you are unable to modify its appearance in the designer.</span></span> <span data-ttu-id="0f66a-128">Görsel temsili, kodda değiştirilmediği sürece (yani, <xref:System.Windows.Forms.Button>) devraldığı sınıftan tam olarak aynı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="0f66a-128">Its visual representation will be exactly the same as that of the class it inherits from (that is, <xref:System.Windows.Forms.Button>) unless modified in the code.</span></span> <span data-ttu-id="0f66a-129">Tasarım yüzeyine, UI öğesi içermeyen bileşenler ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0f66a-129">You can still add components, which have no UI elements, to the design surface.</span></span>

## <a name="add-a-property-to-your-inherited-control"></a><span data-ttu-id="0f66a-130">Devralınan denetimi bir özellik ekleyin</span><span class="sxs-lookup"><span data-stu-id="0f66a-130">Add a Property to Your Inherited Control</span></span>

<span data-ttu-id="0f66a-131">Devralınan Windows Forms denetimlerinin olası bir kullanımı, standart Windows Forms denetimlerinin görünümü ve hisde aynı olan, ancak özel özellikler sunan denetimlerin oluşturulması.</span><span class="sxs-lookup"><span data-stu-id="0f66a-131">One possible use of inherited Windows Forms controls is the creation of controls that are identical in look and feel of standard Windows Forms controls, but expose custom properties.</span></span> <span data-ttu-id="0f66a-132">Bu bölümde, denetimi `ButtonValue` adlı bir özellik ekleyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="0f66a-132">In this section, you will add a property called `ButtonValue` to your control.</span></span>

### <a name="to-add-the-value-property"></a><span data-ttu-id="0f66a-133">Değer özelliğini eklemek için</span><span class="sxs-lookup"><span data-stu-id="0f66a-133">To add the Value property</span></span>

1. <span data-ttu-id="0f66a-134">**Çözüm Gezgini**' de, **ValueButton.cs**' a sağ tıklayın ve ardından kısayol menüsünde **kodu görüntüle** ' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="0f66a-134">In **Solution Explorer**, right-click **ValueButton.cs**, and then click **View Code** from the shortcut menu.</span></span>

2. <span data-ttu-id="0f66a-135">`class` ifadesini bulun.</span><span class="sxs-lookup"><span data-stu-id="0f66a-135">Locate the `class` statement.</span></span> <span data-ttu-id="0f66a-136">`{`hemen sonra aşağıdaki kodu yazın:</span><span class="sxs-lookup"><span data-stu-id="0f66a-136">Immediately after the `{`, type the following code:</span></span>

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

     <span data-ttu-id="0f66a-137">Bu kod, `ButtonValue` özelliğinin depolandığı ve alındığı yöntemleri belirler.</span><span class="sxs-lookup"><span data-stu-id="0f66a-137">This code sets the methods by which the `ButtonValue` property is stored and retrieved.</span></span> <span data-ttu-id="0f66a-138">`get` ifade, özel değişken `varValue`depolanan değere döndürülen değeri ayarlar ve `set` ifade, `value` anahtar sözcüğünün kullanımıyla özel değişkenin değerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="0f66a-138">The `get` statement sets the value returned to the value that is stored in the private variable `varValue`, and the `set` statement sets the value of the private variable by use of the `value` keyword.</span></span>

3. <span data-ttu-id="0f66a-139">Projeyi kaydetmek için **Dosya** menüsünden **Tümünü Kaydet** ' i seçin.</span><span class="sxs-lookup"><span data-stu-id="0f66a-139">From the **File** menu, choose **Save All** to save the project.</span></span>

## <a name="test-the-control"></a><span data-ttu-id="0f66a-140">Denetimi test etme</span><span class="sxs-lookup"><span data-stu-id="0f66a-140">Test the control</span></span>

<span data-ttu-id="0f66a-141">Denetimler tek başına projeler değildir; Bunlar bir kapsayıcıda barındırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0f66a-141">Controls are not stand-alone projects; they must be hosted in a container.</span></span> <span data-ttu-id="0f66a-142">Denetiminizi test etmek için, içinde çalışması için bir test projesi sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="0f66a-142">In order to test your control, you must provide a test project for it to run in.</span></span> <span data-ttu-id="0f66a-143">Ayrıca, denetimi (derleyerek) oluşturarak denetiminizi test projesi için de erişilebilir yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="0f66a-143">You must also make your control accessible to the test project by building (compiling) it.</span></span> <span data-ttu-id="0f66a-144">Bu bölümde, denetiminizi oluşturacak ve bir Windows formunda test edersiniz.</span><span class="sxs-lookup"><span data-stu-id="0f66a-144">In this section, you will build your control and test it in a Windows Form.</span></span>

### <a name="to-build-your-control"></a><span data-ttu-id="0f66a-145">Denetiminizi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="0f66a-145">To build your control</span></span>

<span data-ttu-id="0f66a-146">Üzerinde **derleme** menüsünde tıklatın **Çözümü Derle**.</span><span class="sxs-lookup"><span data-stu-id="0f66a-146">On the **Build** menu, click **Build Solution**.</span></span> <span data-ttu-id="0f66a-147">Derleme, derleyici hataları veya uyarıları olmadan başarılı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0f66a-147">The build should be successful with no compiler errors or warnings.</span></span>

### <a name="to-create-a-test-project"></a><span data-ttu-id="0f66a-148">Bir test projesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="0f66a-148">To create a test project</span></span>

1. <span data-ttu-id="0f66a-149">**Dosya** menüsünde, **Ekle** ' nin üzerine gelin **ve yeni proje ' ye** tıklayarak yeni proje **Ekle** iletişim kutusunu açın.</span><span class="sxs-lookup"><span data-stu-id="0f66a-149">On the **File** menu, point to **Add** and then click **New Project** to open the **Add New Project** dialog box.</span></span>

2. <span data-ttu-id="0f66a-150">**Görsel C#**  düğümün altında **Windows** düğümünü seçin ve **Windows Forms uygulama**' ya tıklayın.</span><span class="sxs-lookup"><span data-stu-id="0f66a-150">Select the **Windows** node, beneath the **Visual C#** node, and click **Windows Forms Application**.</span></span>

3. <span data-ttu-id="0f66a-151">**Ad** kutusuna **Test**girin.</span><span class="sxs-lookup"><span data-stu-id="0f66a-151">In the **Name** box, enter **Test**.</span></span>

4. <span data-ttu-id="0f66a-152">**Çözüm Gezgini**, test projeniz için **Başvurular** düğümüne sağ tıklayın ve ardından kısayol menüsünden **Başvuru Ekle** ' yi seçerek **Başvuru Ekle** iletişim kutusunu görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="0f66a-152">In **Solution Explorer**, right-click the **References** node for your test project, then select **Add Reference** from the shortcut menu to display the **Add Reference** dialog box.</span></span>

5. <span data-ttu-id="0f66a-153">Etiketli **Projeler**sekmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="0f66a-153">Click the tab labeled **Projects**.</span></span> <span data-ttu-id="0f66a-154">ValueButtonLib projeniz **Proje adı**altında listelenecektir.</span><span class="sxs-lookup"><span data-stu-id="0f66a-154">Your ValueButtonLib project will be listed under **Project Name**.</span></span> <span data-ttu-id="0f66a-155">Başvuruyu test projesine eklemek için projeye çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="0f66a-155">Double-click the project to add the reference to the test project.</span></span>

6. <span data-ttu-id="0f66a-156">**Çözüm Gezgini** ' de **Test** ' e sağ tıklayın ve **Oluştur**' u seçin.</span><span class="sxs-lookup"><span data-stu-id="0f66a-156">In **Solution Explorer,** right-click **Test** and select **Build**.</span></span>

### <a name="to-add-your-control-to-the-form"></a><span data-ttu-id="0f66a-157">Formunuza denetim eklemek için</span><span class="sxs-lookup"><span data-stu-id="0f66a-157">To add your control to the form</span></span>

1. <span data-ttu-id="0f66a-158">**Çözüm Gezgini**' de, **Form1.cs** ' ye sağ tıklayıp kısayol menüsünden **tasarımcıyı görüntüle** ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="0f66a-158">In **Solution Explorer**, right-click **Form1.cs** and choose **View Designer** from the shortcut menu.</span></span>

2. <span data-ttu-id="0f66a-159">**Araç kutusunda** **ValueButtonLib bileşenleri**' ni seçin.</span><span class="sxs-lookup"><span data-stu-id="0f66a-159">In the **Toolbox**, select **ValueButtonLib Components**.</span></span> <span data-ttu-id="0f66a-160">**ValueButton**öğesine çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="0f66a-160">Double-click **ValueButton**.</span></span>

     <span data-ttu-id="0f66a-161">Formda bir **ValueButton** görünür.</span><span class="sxs-lookup"><span data-stu-id="0f66a-161">A **ValueButton** appears on the form.</span></span>

3. <span data-ttu-id="0f66a-162">**ValueButton** öğesine sağ tıklayın ve kısayol menüsünden **Özellikler** ' i seçin.</span><span class="sxs-lookup"><span data-stu-id="0f66a-162">Right-click the **ValueButton** and select **Properties** from the shortcut menu.</span></span>

4. <span data-ttu-id="0f66a-163">**Özellikler** penceresinde, bu denetimin özelliklerini inceleyin.</span><span class="sxs-lookup"><span data-stu-id="0f66a-163">In the **Properties** window, examine the properties of this control.</span></span> <span data-ttu-id="0f66a-164">Bunlar, bir standart düğme tarafından sunulan özelliklerle aynıdır, ancak ek bir özellik, ButtonValue olur.</span><span class="sxs-lookup"><span data-stu-id="0f66a-164">Note that they are identical to the properties exposed by a standard button, except that there is an additional property, ButtonValue.</span></span>

5. <span data-ttu-id="0f66a-165">**ButtonValue** özelliğini **5**olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="0f66a-165">Set the **ButtonValue** property to **5**.</span></span>

6. <span data-ttu-id="0f66a-166">Formunuza bir <xref:System.Windows.Forms.Label> denetimi eklemek için **araç kutusunun** **tüm Windows Forms** sekmesinde **etiket** ' e çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="0f66a-166">In the **All Windows Forms** tab of the **Toolbox**, double-click **Label** to add a <xref:System.Windows.Forms.Label> control to your form.</span></span>

7. <span data-ttu-id="0f66a-167">Etiketi formun merkezine yeniden yerleştir.</span><span class="sxs-lookup"><span data-stu-id="0f66a-167">Relocate the label to the center of the form.</span></span>

8. <span data-ttu-id="0f66a-168">`valueButton1`çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="0f66a-168">Double-click `valueButton1`.</span></span>

     <span data-ttu-id="0f66a-169">**Kod düzenleyicisi** `valueButton1_Click` olayına açılır.</span><span class="sxs-lookup"><span data-stu-id="0f66a-169">The **Code Editor** opens to the `valueButton1_Click` event.</span></span>

9. <span data-ttu-id="0f66a-170">Aşağıdaki kod satırını ekleyin.</span><span class="sxs-lookup"><span data-stu-id="0f66a-170">Insert the following line of code.</span></span>

    ```csharp
    label1.Text = valueButton1.ButtonValue.ToString();
    ```

10. <span data-ttu-id="0f66a-171">**Çözüm Gezgini**' de **Test**' e sağ tıklayın ve kısayol menüsünde **Başlangıç projesi olarak ayarla** ' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="0f66a-171">In **Solution Explorer**, right-click **Test**, and choose **Set as Startup Project** from the shortcut menu.</span></span>

11. <span data-ttu-id="0f66a-172">**Hata Ayıkla** menüsünden **hata ayıklamayı Başlat**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="0f66a-172">From the **Debug** menu, select **Start Debugging**.</span></span>

     <span data-ttu-id="0f66a-173">`Form1` görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="0f66a-173">`Form1` appears.</span></span>

12. <span data-ttu-id="0f66a-174">Tıklatın `valueButton1`.</span><span class="sxs-lookup"><span data-stu-id="0f66a-174">Click `valueButton1`.</span></span>

     <span data-ttu-id="0f66a-175">' 5 ' rakamı, devralınan denetiminizin `ButtonValue` özelliğinin `valueButton1_Click` yöntemi aracılığıyla `label1` geçtiğini gösteren `label1`görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="0f66a-175">The numeral '5' is displayed in `label1`, demonstrating that the `ButtonValue` property of your inherited control has been passed to `label1` through the `valueButton1_Click` method.</span></span> <span data-ttu-id="0f66a-176">Bu nedenle `ValueButton` denetiminiz standart Windows Forms düğmesinin tüm işlevlerini devralır, ancak ek, özel bir özellik sunar.</span><span class="sxs-lookup"><span data-stu-id="0f66a-176">Thus your `ValueButton` control inherits all the functionality of the standard Windows Forms button, but exposes an additional, custom property.</span></span>

## <a name="see-also"></a><span data-ttu-id="0f66a-177">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0f66a-177">See also</span></span>

- [<span data-ttu-id="0f66a-178">Nasıl yapılır: Araç Kutusu Öğelerini Seç İletişim Kutusunda bir Denetimi Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="0f66a-178">How to: Display a Control in the Choose Toolbox Items Dialog Box</span></span>](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)
- [<span data-ttu-id="0f66a-179">İzlenecek yol: Visual C# İle Bileşik Denetim Yazma</span><span class="sxs-lookup"><span data-stu-id="0f66a-179">Walkthrough: Authoring a Composite Control with Visual C#</span></span>](walkthrough-authoring-a-composite-control-with-visual-csharp.md)
