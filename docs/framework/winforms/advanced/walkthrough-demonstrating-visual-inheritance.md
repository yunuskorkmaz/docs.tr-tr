---
title: 'İzlenecek yol: Görsel Devralmayı Gösterme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- form inheritance [Windows Forms], walkthroughs
- visual inheritance
- inheritance [Windows Forms], walkthroughs
- walkthroughs [Windows Forms], visual inheritance
- Windows Forms, inheritance
ms.assetid: 01966086-3142-450e-8210-3fd4cb33f591
ms.openlocfilehash: 32df98852b28963ffb748895156f7d9977c74b92
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046145"
---
# <a name="walkthrough-demonstrating-visual-inheritance"></a><span data-ttu-id="4168a-102">İzlenecek yol: Görsel Devralmayı Gösterme</span><span class="sxs-lookup"><span data-stu-id="4168a-102">Walkthrough: Demonstrating Visual Inheritance</span></span>

<span data-ttu-id="4168a-103">Görsel devralma, temel formdaki denetimleri görmenizi ve yeni denetimler eklemenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="4168a-103">Visual inheritance enables you to see the controls on the base form and to add new controls.</span></span> <span data-ttu-id="4168a-104">Bu kılavuzda, bir temel form oluşturacak ve onu bir sınıf kitaplığında derleyecaksınız.</span><span class="sxs-lookup"><span data-stu-id="4168a-104">In this walkthrough you will create a base form and compile it into a class library.</span></span> <span data-ttu-id="4168a-105">Bu sınıf kitaplığını başka bir projeye aktarır ve temel formdan devralan yeni bir form oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="4168a-105">You will import this class library into another project and create a new form that inherits from the base form.</span></span> <span data-ttu-id="4168a-106">Bu izlenecek yol sırasında şunları yapmayı öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="4168a-106">During this walkthrough, you will learn how to:</span></span>

- <span data-ttu-id="4168a-107">Temel form içeren bir sınıf kitaplığı projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="4168a-107">Create a class library project containing a base form.</span></span>

- <span data-ttu-id="4168a-108">Temel formun türetilmiş sınıflarının değiştirebileceği özelliklere sahip bir düğme ekleyin.</span><span class="sxs-lookup"><span data-stu-id="4168a-108">Add a button with properties that derived classes of the base form can modify.</span></span>

- <span data-ttu-id="4168a-109">Temel formun ınherıtors tarafından değiştirilemeyen bir düğme ekleyin.</span><span class="sxs-lookup"><span data-stu-id="4168a-109">Add a button that cannot be modified by inheritors of the base form.</span></span>

- <span data-ttu-id="4168a-110">Öğesinden `BaseForm`devralan bir form içeren bir proje oluşturun.</span><span class="sxs-lookup"><span data-stu-id="4168a-110">Create a project containing a form that inherits from `BaseForm`.</span></span>

<span data-ttu-id="4168a-111">Sonuç olarak, Bu anlatım devralınan bir formdaki özel ve korunan denetimler arasındaki farkı gösterir.</span><span class="sxs-lookup"><span data-stu-id="4168a-111">Ultimately, this walkthrough will demonstrate the difference between private and protected controls on an inherited form.</span></span>

> [!CAUTION]
> <span data-ttu-id="4168a-112">Tüm denetimler temel formdan Görsel devralmayı desteklemez.</span><span class="sxs-lookup"><span data-stu-id="4168a-112">Not all controls support visual inheritance from a base form.</span></span> <span data-ttu-id="4168a-113">Aşağıdaki denetimler bu kılavuzda açıklanan senaryoyu desteklemez:</span><span class="sxs-lookup"><span data-stu-id="4168a-113">The following controls do not support the scenario described in this walkthrough:</span></span>
>
> - <xref:System.Windows.Forms.WebBrowser>
>
> - <xref:System.Windows.Forms.ToolStrip>
>
> - <xref:System.Windows.Forms.ToolStripPanel>
>
> - <xref:System.Windows.Forms.TableLayoutPanel>
>
> - <xref:System.Windows.Forms.FlowLayoutPanel>
>
> - <xref:System.Windows.Forms.DataGridView>
>
> <span data-ttu-id="4168a-114">Devralınan form içindeki bu denetimler her zaman, kullandığınız değiştiricilere (`private`, `protected`, veya `public`) bakılmaksızın salt okunurdur.</span><span class="sxs-lookup"><span data-stu-id="4168a-114">These controls in the inherited form are always read-only regardless of the modifiers you use (`private`, `protected`, or `public`).</span></span>

## <a name="create-a-class-library-project-containing-a-base-form"></a><span data-ttu-id="4168a-115">Temel form içeren bir sınıf kitaplığı projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="4168a-115">Create a class library project containing a base form</span></span>

1. <span data-ttu-id="4168a-116">Visual Studio 'da, **Dosya** menüsünden **Yeni** > **Proje** ' yi seçerek **Yeni proje** iletişim kutusunu açın.</span><span class="sxs-lookup"><span data-stu-id="4168a-116">In Visual Studio, from the **File** menu, choose **New** > **Project** to open the **New Project** dialog box.</span></span>

2. <span data-ttu-id="4168a-117">Adlı `BaseFormLibrary`bir Windows Forms uygulaması oluşturun.</span><span class="sxs-lookup"><span data-stu-id="4168a-117">Create a Windows Forms application named `BaseFormLibrary`.</span></span>

3. <span data-ttu-id="4168a-118">Standart bir Windows Forms uygulaması yerine bir sınıf kitaplığı oluşturmak için, **Çözüm Gezgini**, **BaseFormLibrary** proje düğümüne sağ tıklayın ve ardından **Özellikler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="4168a-118">To create a class library instead of a standard Windows Forms application, in **Solution Explorer**, right-click the **BaseFormLibrary** project node and then select **Properties**.</span></span>

4. <span data-ttu-id="4168a-119">Projenin özelliklerinde, **çıkış türünü** **Windows uygulamasından** **sınıf kitaplığı**olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="4168a-119">In the properties for the project, change the **Output type** from **Windows Application** to **Class Library**.</span></span>

5. <span data-ttu-id="4168a-120">**Dosya** menüsünde **Tümünü Kaydet** ' i seçerek projeyi ve dosyaları varsayılan konuma kaydedin.</span><span class="sxs-lookup"><span data-stu-id="4168a-120">From the **File** menu, choose **Save All** to save the project and files to the default location.</span></span>

<span data-ttu-id="4168a-121">Sonraki iki yordam, temel forma düğme ekler.</span><span class="sxs-lookup"><span data-stu-id="4168a-121">The next two procedures add buttons to the base form.</span></span> <span data-ttu-id="4168a-122">Görsel devralmayı göstermek için, `Modifiers` özelliklerini ayarlayarak düğmelere farklı erişim düzeyleri verirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4168a-122">To demonstrate visual inheritance, you will give the buttons different access levels by setting their `Modifiers` properties.</span></span>

## <a name="add-a-button-that-inheritors-of-the-base-form-can-modify"></a><span data-ttu-id="4168a-123">Temel formun devralanıların değiştirebileceği bir düğme Ekle</span><span class="sxs-lookup"><span data-stu-id="4168a-123">Add a button that inheritors of the base form can modify</span></span>

1. <span data-ttu-id="4168a-124">Tasarımcıda **Form1** ' i açın.</span><span class="sxs-lookup"><span data-stu-id="4168a-124">Open **Form1** in the designer.</span></span>

2. <span data-ttu-id="4168a-125">Forma düğme eklemek için **araç kutusunun** **tüm Windows Forms** sekmesinde **düğme** ' ye çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="4168a-125">On the **All Windows Forms** tab of the **Toolbox**, double-click **Button** to add a button to the form.</span></span> <span data-ttu-id="4168a-126">Düğmeyi konumlandırmak ve yeniden boyutlandırmak için fareyi kullanın.</span><span class="sxs-lookup"><span data-stu-id="4168a-126">Use the mouse to position and resize the button.</span></span>

3. <span data-ttu-id="4168a-127">Özellikler penceresi, düğmenin aşağıdaki özelliklerini ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="4168a-127">In the Properties window, set the following properties of the button:</span></span>

    - <span data-ttu-id="4168a-128">**Text** özelliğini **Hello**olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="4168a-128">Set the **Text** property to **Say Hello**.</span></span>

    - <span data-ttu-id="4168a-129">**(Name)** özelliğini **btnProtected**olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="4168a-129">Set the **(Name)** property to **btnProtected**.</span></span>

    - <span data-ttu-id="4168a-130">**Değiştiriciler** özelliğini **korumalı**olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="4168a-130">Set the **Modifiers** property to **Protected**.</span></span> <span data-ttu-id="4168a-131">Bu, **Form1** 'ten kalıtımla alan formların **btnProtected**'nin özelliklerini değiştirmesine olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="4168a-131">This makes it possible for forms that inherit from **Form1** to modify the properties of **btnProtected**.</span></span>

4. <span data-ttu-id="4168a-132">Tıklama olayına bir olay işleyicisi eklemek için, **Merhaba** **'** a çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="4168a-132">Double-click the **Say Hello** button to add an event handler for the **Click** event.</span></span>

5. <span data-ttu-id="4168a-133">Aşağıdaki kod satırını olay işleyicisine ekleyin:</span><span class="sxs-lookup"><span data-stu-id="4168a-133">Add the following line of code to the event handler:</span></span>

    ```vb
    MessageBox.Show("Hello, World!")
    ```

    ```csharp
    MessageBox.Show("Hello, World!");
    ```

## <a name="add-a-button-that-cannot-be-modified-by-inheritors-of-the-base-form"></a><span data-ttu-id="4168a-134">Temel formun ınherıtors tarafından değiştirilemeyen bir düğme ekleyin</span><span class="sxs-lookup"><span data-stu-id="4168a-134">Add a button that cannot be modified by inheritors of the base form</span></span>

1. <span data-ttu-id="4168a-135">Kod düzenleyicisinin üzerindeki **Form1. vb [Design], Form1.cs [Design] veya Form1. jsl [Design** ] sekmesine tıklayarak ya da F7 tuşuna basarak Tasarım görünümüne geçiş yapın.</span><span class="sxs-lookup"><span data-stu-id="4168a-135">Switch to design view by clicking the **Form1.vb [Design], Form1.cs [Design], or Form1.jsl [Design]** tab above the code editor, or by pressing F7.</span></span>

2. <span data-ttu-id="4168a-136">İkinci bir düğme ekleyin ve özelliklerini aşağıdaki gibi ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="4168a-136">Add a second button and set its properties as follows:</span></span>

    - <span data-ttu-id="4168a-137">**Metin** özelliğini, **güle söylemek**için ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="4168a-137">Set the **Text** property to **Say Goodbye**.</span></span>

    - <span data-ttu-id="4168a-138">**(Ad)** özelliğini **btnPrivate**olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="4168a-138">Set the **(Name)** property to **btnPrivate**.</span></span>

    - <span data-ttu-id="4168a-139">**Değiştiriciler** özelliğini **özel**olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="4168a-139">Set the **Modifiers** property to **Private**.</span></span> <span data-ttu-id="4168a-140">Bu, **Form1** 'ten kalıtımla alan formların **btnPrivate**özelliklerinin değiştirilmesini olanaksız hale getirir.</span><span class="sxs-lookup"><span data-stu-id="4168a-140">This makes it impossible for forms that inherit from **Form1** to modify the properties of **btnPrivate**.</span></span>

3. <span data-ttu-id="4168a-141">**Tıklama** olayına bir olay işleyicisi eklemek için **söyleyin** düğmesine çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="4168a-141">Double-click the **Say Goodbye** button to add an event handler for the **Click** event.</span></span> <span data-ttu-id="4168a-142">Aşağıdaki kod satırını olay yordamına yerleştirin:</span><span class="sxs-lookup"><span data-stu-id="4168a-142">Place the following line of code in the event procedure:</span></span>

    ```vb
    MessageBox.Show("Goodbye!")
    ```

    ```csharp
    MessageBox.Show("Goodbye!");
    ```

4. <span data-ttu-id="4168a-143">Sınıf kitaplığını derlemek için **Build (oluştur** ) menüsünde **BaseForm kitaplığı** ' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="4168a-143">From the **Build** menu, choose **Build BaseForm Library** to build the class library.</span></span>

     <span data-ttu-id="4168a-144">Kitaplık derlendikten sonra, yeni oluşturduğunuz formdan devralan yeni bir proje oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4168a-144">Once the library is built, you can create a new project that inherits from the form you just created.</span></span>

## <a name="create-a-project-containing-a-form-that-inherits-from-the-base-form"></a><span data-ttu-id="4168a-145">Temel formdan devralan form içeren bir proje oluşturma</span><span class="sxs-lookup"><span data-stu-id="4168a-145">Create a project containing a form that inherits from the base form</span></span>

1. <span data-ttu-id="4168a-146">**Yeni Proje Ekle** iletişim kutusunu açmak için **Dosya** menüsünden **Ekle** ve **Yeni proje** ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="4168a-146">From the **File** menu, choose **Add** and then **New Project** to open the **Add New Project** dialog box.</span></span>

2. <span data-ttu-id="4168a-147">Adlı `InheritanceTest`bir Windows Forms uygulaması oluşturun.</span><span class="sxs-lookup"><span data-stu-id="4168a-147">Create a Windows Forms application named `InheritanceTest`.</span></span>

## <a name="add-an-inherited-form"></a><span data-ttu-id="4168a-148">Devralınan form ekleme</span><span class="sxs-lookup"><span data-stu-id="4168a-148">Add an inherited form</span></span>

1. <span data-ttu-id="4168a-149">**Çözüm Gezgini**, **InheritanceTest** projesine sağ tıklayın, **Ekle**' yi seçin ve ardından **Yeni öğe**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="4168a-149">In **Solution Explorer**, right-click the **InheritanceTest** project, select **Add**, and then select **New Item**.</span></span>

2. <span data-ttu-id="4168a-150">**Yeni öğe Ekle** iletişim kutusunda **Windows Forms** kategorisini seçin (kategori listeniz varsa) ve ardından **devralınan form** şablonunu seçin.</span><span class="sxs-lookup"><span data-stu-id="4168a-150">In the **Add New Item** dialog box, select the **Windows Forms** category (if you have a list of categories) and then select the **Inherited Form** template.</span></span>

3. <span data-ttu-id="4168a-151">Varsayılan adını `Form2` bırakın ve **Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="4168a-151">Leave the default name of `Form2` and then click **Add**.</span></span>

4. <span data-ttu-id="4168a-152">**Devralma Seçicisi** iletişim kutusunda, **BaseFormLibrary** projesinden öğesinden devralınacak form olarak **Form1** ' i seçin ve **Tamam**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="4168a-152">In the **Inheritance Picker** dialog box, select **Form1** from the **BaseFormLibrary** project as the form to inherit from and click **OK**.</span></span>

     <span data-ttu-id="4168a-153">Bu, **BaseFormLibrary**biçimindeki formdan türetilen **InheritanceTest** projesinde bir form oluşturur.</span><span class="sxs-lookup"><span data-stu-id="4168a-153">This creates a form in the **InheritanceTest** project that derives from the form in **BaseFormLibrary**.</span></span>

5. <span data-ttu-id="4168a-154">Zaten açık değilse, tasarımcıda devralınan formu (**Form2**) çift tıklayarak açın.</span><span class="sxs-lookup"><span data-stu-id="4168a-154">Open the inherited form (**Form2**) in the designer by double-clicking it, if it is not already open.</span></span>

    <span data-ttu-id="4168a-155">Tasarımcıda, devralınan düğmelerin bir sembolü vardır (</span><span class="sxs-lookup"><span data-stu-id="4168a-155">In the designer, the inherited buttons have a symbol (</span></span>![Visual Basic devralma sembolünün ekran görüntüsü.](./media/walkthrough-demonstrating-visual-inheritance/visual-basic-inheritance-glyph.gif)<span data-ttu-id="4168a-157">) üst köşede devralındığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="4168a-157">) in their upper corner, indicating they are inherited.</span></span>

6. <span data-ttu-id="4168a-158">**Merhaba deyin** düğmesini seçin ve yeniden boyutlandırma tutamaçlarını gözlemleyin.</span><span class="sxs-lookup"><span data-stu-id="4168a-158">Select the **Say Hello** button and observe the resize handles.</span></span> <span data-ttu-id="4168a-159">Bu düğme korunduğundan, devracılar onu taşıyabilir, yeniden boyutlandırabilir, resim yazısını değiştirebilir ve başka değişiklikler yapabilir.</span><span class="sxs-lookup"><span data-stu-id="4168a-159">Because this button is protected, the inheritors can move it, resize it, change its caption, and make other modifications.</span></span>

7. <span data-ttu-id="4168a-160">Özel **söyleyin** düğmesini seçin ve yeniden boyutlandırma tutamaçları olmadığına dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="4168a-160">Select the private **Say Goodbye** button, and notice that it does not have resize handles.</span></span> <span data-ttu-id="4168a-161">Ayrıca, **Özellikler** penceresinde bu düğmenin özellikleri, değiştirilmeyeceğini belirtmek için gridir.</span><span class="sxs-lookup"><span data-stu-id="4168a-161">Additionally, in the **Properties** window, the properties of this button are grayed to indicate they cannot be modified.</span></span>

8. <span data-ttu-id="4168a-162">Görsel C#kullanıyorsanız:</span><span class="sxs-lookup"><span data-stu-id="4168a-162">If you are using Visual C#:</span></span>

    1. <span data-ttu-id="4168a-163">**Çözüm Gezgini**, **InheritanceTest** projesinde **Form1** öğesine sağ tıklayın ve ardından **Sil**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="4168a-163">In **Solution Explorer**, right-click **Form1** in the **InheritanceTest** project and then choose **Delete**.</span></span> <span data-ttu-id="4168a-164">Görüntülenen ileti kutusunda, silme işlemini onaylamak için **Tamam** ' ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="4168a-164">In the message box that appears, click **OK** to confirm the deletion.</span></span>

    2. <span data-ttu-id="4168a-165">Program.cs dosyasını açın ve satırı `Application.Run(new Form1());` olarak `Application.Run(new Form2());`değiştirin.</span><span class="sxs-lookup"><span data-stu-id="4168a-165">Open the Program.cs file and change the line `Application.Run(new Form1());` to `Application.Run(new Form2());`.</span></span>

9. <span data-ttu-id="4168a-166">**Çözüm Gezgini**, **InheritanceTest** projesine sağ tıklayın ve **Başlangıç projesi olarak ayarla**' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="4168a-166">In **Solution Explorer**, right-click the **InheritanceTest** project and select **Set As Startup Project**.</span></span>

10. <span data-ttu-id="4168a-167">**Çözüm Gezgini**, **InheritanceTest** projesine sağ tıklayın ve **Özellikler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="4168a-167">In **Solution Explorer**, right-click the **InheritanceTest** project and select **Properties**.</span></span>

11. <span data-ttu-id="4168a-168">**InheritanceTest** özelliği sayfalarında, **Başlangıç nesnesini** devralınan form (**Form2**) olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="4168a-168">In the **InheritanceTest** property pages, set the **Startup object** to be the inherited form (**Form2**).</span></span>

12. <span data-ttu-id="4168a-169">**F5** tuşuna basarak uygulamayı çalıştırın ve devralınan formun davranışını gözlemleyin.</span><span class="sxs-lookup"><span data-stu-id="4168a-169">Press **F5** to run the application, and observe the behavior of the inherited form.</span></span>

## <a name="next-steps"></a><span data-ttu-id="4168a-170">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="4168a-170">Next steps</span></span>

<span data-ttu-id="4168a-171">Kullanıcı denetimleri için devralma de aynı şekilde çalışmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4168a-171">Inheritance for user controls works in much the same way.</span></span> <span data-ttu-id="4168a-172">Yeni bir sınıf kitaplığı projesi açın ve bir kullanıcı denetimi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="4168a-172">Open a new class library project and add a user control.</span></span> <span data-ttu-id="4168a-173">Bileşen denetimlerini üzerine yerleştirin ve projeyi derleyin.</span><span class="sxs-lookup"><span data-stu-id="4168a-173">Place constituent controls on it and compile the project.</span></span> <span data-ttu-id="4168a-174">Başka bir yeni sınıf kitaplığı projesi açın ve derlenen sınıf kitaplığına bir başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="4168a-174">Open another new class library project and add a reference to the compiled class library.</span></span> <span data-ttu-id="4168a-175">Ayrıca, projeye devralınan bir denetim eklemeyi ( **yeni öğeler Ekle** iletişim kutusu aracılığıyla) ve **Devralma seçicisini**kullanmayı deneyin.</span><span class="sxs-lookup"><span data-stu-id="4168a-175">Also, try adding an inherited control (through the **Add New Items** dialog box) to the project and using the **Inheritance Picker**.</span></span> <span data-ttu-id="4168a-176">Bir kullanıcı denetimi ekleyin ve `Inherits` (`:` görsel C#olarak) ekstresini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="4168a-176">Add a user control, and change the `Inherits` (`:` in Visual C#) statement.</span></span> <span data-ttu-id="4168a-177">Daha fazla bilgi için [nasıl yapılır: Windows Forms](how-to-inherit-windows-forms.md)devralma.</span><span class="sxs-lookup"><span data-stu-id="4168a-177">For more information, see [How to: Inherit Windows Forms](how-to-inherit-windows-forms.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4168a-178">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4168a-178">See also</span></span>

- [<span data-ttu-id="4168a-179">Nasıl yapılır: Windows Forms devralma</span><span class="sxs-lookup"><span data-stu-id="4168a-179">How to: Inherit Windows Forms</span></span>](how-to-inherit-windows-forms.md)
- [<span data-ttu-id="4168a-180">Windows Forms Görsel Devralma</span><span class="sxs-lookup"><span data-stu-id="4168a-180">Windows Forms Visual Inheritance</span></span>](windows-forms-visual-inheritance.md)
- [<span data-ttu-id="4168a-181">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4168a-181">Windows Forms</span></span>](../index.md)
