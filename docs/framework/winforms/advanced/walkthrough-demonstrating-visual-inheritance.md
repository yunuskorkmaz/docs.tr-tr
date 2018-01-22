---
title: "İzlenecek Yol: Görsel Devralmayı Gösterme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7c5ef33be9841b5c74b6ae2448daf56079489b61
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="walkthrough-demonstrating-visual-inheritance"></a><span data-ttu-id="762f9-102">İzlenecek Yol: Görsel Devralmayı Gösterme</span><span class="sxs-lookup"><span data-stu-id="762f9-102">Walkthrough: Demonstrating Visual Inheritance</span></span>
<span data-ttu-id="762f9-103">Görsel devralma temel form üzerinde denetimleri görmek için ve yeni denetim eklemek için sağlar.</span><span class="sxs-lookup"><span data-stu-id="762f9-103">Visual inheritance enables you to see the controls on the base form and to add new controls.</span></span> <span data-ttu-id="762f9-104">Bu kılavuzda temel form oluşturma ve bir sınıf kitaplığı'na derleyin.</span><span class="sxs-lookup"><span data-stu-id="762f9-104">In this walkthrough you will create a base form and compile it into a class library.</span></span> <span data-ttu-id="762f9-105">Bu sınıf kitaplığı başka bir projeye almak ve temel formundan devralan yeni bir form oluşturun.</span><span class="sxs-lookup"><span data-stu-id="762f9-105">You will import this class library into another project and create a new form that inherits from the base form.</span></span> <span data-ttu-id="762f9-106">Bu gözden geçirme sırasında öğreneceksiniz nasıl yapılır:</span><span class="sxs-lookup"><span data-stu-id="762f9-106">During this walkthrough, you will learn how to:</span></span>  
  
-   <span data-ttu-id="762f9-107">Bir taban formunu içeren bir sınıf kitaplığı projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="762f9-107">Create a class library project containing a base form.</span></span>  
  
-   <span data-ttu-id="762f9-108">Türetilmiş sınıflar temel formunun özelliklere sahip bir düğme değiştirebilirsiniz ekleyin.</span><span class="sxs-lookup"><span data-stu-id="762f9-108">Add a button with properties that derived classes of the base form can modify.</span></span>  
  
-   <span data-ttu-id="762f9-109">Taban form Notlar tarafından değiştirilemez bir düğme ekleyin.</span><span class="sxs-lookup"><span data-stu-id="762f9-109">Add a button that cannot be modified by inheritors of the base form.</span></span>  
  
-   <span data-ttu-id="762f9-110">Öğesinden devralınan bir form içeren bir proje oluşturun `BaseForm`.</span><span class="sxs-lookup"><span data-stu-id="762f9-110">Create a project containing a form that inherits from `BaseForm`.</span></span>  
  
 <span data-ttu-id="762f9-111">Sonuç olarak, bu kılavuzda devralınan bir form üzerinde özel ve korumalı denetimler arasındaki fark gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="762f9-111">Ultimately, this walkthrough will demonstrate the difference between private and protected controls on an inherited form.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="762f9-112">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="762f9-112">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="762f9-113">Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="762f9-113">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="762f9-114">Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="762f9-114">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="762f9-115">Tüm denetimler temel bir formdan görsel devralma destekler.</span><span class="sxs-lookup"><span data-stu-id="762f9-115">Not all controls support visual inheritance from a base form.</span></span> <span data-ttu-id="762f9-116">Bu kılavuzda açıklanan senaryo aşağıdaki denetimleri desteklenmez:</span><span class="sxs-lookup"><span data-stu-id="762f9-116">The following controls do not support the scenario described in this walkthrough:</span></span>  
>   
>  <xref:System.Windows.Forms.WebBrowser>  
>   
>  <xref:System.Windows.Forms.ToolStrip>  
>   
>  <xref:System.Windows.Forms.ToolStripPanel>  
>   
>  <xref:System.Windows.Forms.TableLayoutPanel>  
>   
>  <xref:System.Windows.Forms.FlowLayoutPanel>  
>   
>  <xref:System.Windows.Forms.DataGridView>  
>   
>  <span data-ttu-id="762f9-117">Bu devralınan formdaki denetimlerin her zaman kullandığınız değiştiricileri bağımsız olarak salt okunurdur (`private`, `protected`, veya `public`).</span><span class="sxs-lookup"><span data-stu-id="762f9-117">These controls in the inherited form are always read-only regardless of the modifiers you use (`private`, `protected`, or `public`).</span></span>  
  
## <a name="scenario-steps"></a><span data-ttu-id="762f9-118">Senaryo adımları</span><span class="sxs-lookup"><span data-stu-id="762f9-118">Scenario Steps</span></span>  
 <span data-ttu-id="762f9-119">İlk adım, temel form oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="762f9-119">The first step is to create the base form.</span></span>  
  
#### <a name="to-create-a-class-library-project-containing-a-base-form"></a><span data-ttu-id="762f9-120">Bir taban formunu içeren bir sınıf kitaplığı proje oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="762f9-120">To create a class library project containing a base form</span></span>  
  
1.  <span data-ttu-id="762f9-121">Gelen **dosya** menüsünde seçin **yeni**ve ardından **proje** açmak için **yeni proje** iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="762f9-121">From the **File** menu, choose **New**, and then **Project** to open the **New Project** dialog box.</span></span>  
  
2.  <span data-ttu-id="762f9-122">Adlı bir Windows Forms uygulaması oluşturma `BaseFormLibrary`.</span><span class="sxs-lookup"><span data-stu-id="762f9-122">Create a Windows Forms application named `BaseFormLibrary`.</span></span>  
  
3.  <span data-ttu-id="762f9-123">Standart bir Windows Forms uygulaması yerine bir sınıf kitaplığı oluşturmak için **Çözüm Gezgini**, sağ **BaseFormLibrary** proje düğümünü ve ardından **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="762f9-123">To create a class library instead of a standard Windows Forms application, in **Solution Explorer**, right-click the **BaseFormLibrary** project node and then select **Properties**.</span></span>  
  
4.  <span data-ttu-id="762f9-124">Proje özelliklerini değiştirme **çıktı türü** gelen **Windows uygulaması** için **sınıf kitaplığı**.</span><span class="sxs-lookup"><span data-stu-id="762f9-124">In the properties for the project, change the **Output type** from **Windows Application** to **Class Library**.</span></span>  
  
5.  <span data-ttu-id="762f9-125">Gelen **dosya** menüsünde seçin **Tümünü Kaydet** proje ve dosyaları varsayılan konuma kaydetmek için.</span><span class="sxs-lookup"><span data-stu-id="762f9-125">From the **File** menu, choose **Save All** to save the project and files to the default location.</span></span>  
  
 <span data-ttu-id="762f9-126">Sonraki iki yordam, taban formun düğmeleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="762f9-126">The next two procedures add buttons to the base form.</span></span> <span data-ttu-id="762f9-127">Görsel devralma göstermek için düğmeler farklı erişim düzeyleri ayarlayarak erişmenizi sağlayan kendi `Modifiers` özellikleri.</span><span class="sxs-lookup"><span data-stu-id="762f9-127">To demonstrate visual inheritance, you will give the buttons different access levels by setting their `Modifiers` properties.</span></span>  
  
#### <a name="to-add-a-button-that-inheritors-of-the-base-form-can-modify"></a><span data-ttu-id="762f9-128">Taban formun Notlar değiştirebilirsiniz bir düğme eklemek için</span><span class="sxs-lookup"><span data-stu-id="762f9-128">To add a button that inheritors of the base form can modify</span></span>  
  
1.  <span data-ttu-id="762f9-129">Açık **Form1** Tasarımcısı'nda.</span><span class="sxs-lookup"><span data-stu-id="762f9-129">Open **Form1** in the designer.</span></span>  
  
2.  <span data-ttu-id="762f9-130">Üzerinde **tüm Windows Formları** sekmesinde **araç**, çift **düğmesi** forma bir düğme eklemek için.</span><span class="sxs-lookup"><span data-stu-id="762f9-130">On the **All Windows Forms** tab of the **Toolbox**, double-click **Button** to add a button to the form.</span></span> <span data-ttu-id="762f9-131">Fare getirin ve düğmeye yeniden boyutlandırma için kullanın.</span><span class="sxs-lookup"><span data-stu-id="762f9-131">Use the mouse to position and resize the button.</span></span>  
  
3.  <span data-ttu-id="762f9-132">Özellikler penceresinde düğmesinin aşağıdaki özellikleri ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="762f9-132">In the Properties window, set the following properties of the button:</span></span>  
  
    -   <span data-ttu-id="762f9-133">Ayarlama **metin** özelliğine **Say Hello**.</span><span class="sxs-lookup"><span data-stu-id="762f9-133">Set the **Text** property to **Say Hello**.</span></span>  
  
    -   <span data-ttu-id="762f9-134">Ayarlama **(ad)** özelliğine **btnProtected**.</span><span class="sxs-lookup"><span data-stu-id="762f9-134">Set the **(Name)** property to **btnProtected**.</span></span>  
  
    -   <span data-ttu-id="762f9-135">Ayarlama**değiştiricileri** özelliğine **korumalı**.</span><span class="sxs-lookup"><span data-stu-id="762f9-135">Set the**Modifiers** property to **Protected**.</span></span> <span data-ttu-id="762f9-136">Bu devralınan formlar için mümkün kılar **Form1** özelliklerini değiştirmek için **btnProtected**.</span><span class="sxs-lookup"><span data-stu-id="762f9-136">This makes it possible for forms that inherit from **Form1** to modify the properties of **btnProtected**.</span></span>  
  
4.  <span data-ttu-id="762f9-137">Çift **Say Hello** bir olay işleyicisi için Ekle düğmesini **tıklatın** olay.</span><span class="sxs-lookup"><span data-stu-id="762f9-137">Double-click the **Say Hello** button to add an event handler for the **Click** event.</span></span>  
  
5.  <span data-ttu-id="762f9-138">Aşağıdaki kod satırını olay işleyicisine ekleyin:</span><span class="sxs-lookup"><span data-stu-id="762f9-138">Add the following line of code to the event handler:</span></span>  
  
    ```vb  
    MessageBox.Show("Hello, World!")  
    ```  
  
    ```csharp  
    MessageBox.Show("Hello, World!");  
    ```  
  
#### <a name="to-add-a-button-that-cannot-be-modified-by-inheritors-of-the-base-form"></a><span data-ttu-id="762f9-139">Taban form Notlar tarafından değiştirilemez bir düğme eklemek için</span><span class="sxs-lookup"><span data-stu-id="762f9-139">To add a button that cannot be modified by inheritors of the base form</span></span>  
  
1.  <span data-ttu-id="762f9-140">Tıklatarak Tasarım görünümüne geçiş **Form1.vb [tasarım], Form1.cs [Design] veya [tasarım] Form1.jsl** Kod düzenleyicisinde yukarıda ya da F7 tuşlarına basarak sekme.</span><span class="sxs-lookup"><span data-stu-id="762f9-140">Switch to design view by clicking the **Form1.vb [Design], Form1.cs [Design], or Form1.jsl [Design]** tab above the code editor, or by pressing F7.</span></span>  
  
2.  <span data-ttu-id="762f9-141">İkinci düğme ekleme ve özelliklerini şu şekilde ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="762f9-141">Add a second button and set its properties as follows:</span></span>  
  
    -   <span data-ttu-id="762f9-142">Ayarlama **metin** özelliğine **Say güle güle**.</span><span class="sxs-lookup"><span data-stu-id="762f9-142">Set the **Text** property to **Say Goodbye**.</span></span>  
  
    -   <span data-ttu-id="762f9-143">Ayarlama **(ad)** özelliğine **btnPrivate**.</span><span class="sxs-lookup"><span data-stu-id="762f9-143">Set the **(Name)** property to **btnPrivate**.</span></span>  
  
    -   <span data-ttu-id="762f9-144">Ayarlama **değiştiricileri** özelliğine **özel**.</span><span class="sxs-lookup"><span data-stu-id="762f9-144">Set the **Modifiers** property to **Private**.</span></span> <span data-ttu-id="762f9-145">Bu devralınan formlar mümkün kılar **Form1** özelliklerini değiştirmek için **btnPrivate**.</span><span class="sxs-lookup"><span data-stu-id="762f9-145">This makes it impossible for forms that inherit from **Form1** to modify the properties of **btnPrivate**.</span></span>  
  
3.  <span data-ttu-id="762f9-146">Çift **Say güle güle** bir olay işleyicisi için Ekle düğmesini **tıklatın** olay.</span><span class="sxs-lookup"><span data-stu-id="762f9-146">Double-click the **Say Goodbye** button to add an event handler for the **Click** event.</span></span> <span data-ttu-id="762f9-147">Aşağıdaki kod satırını olay yordamında koyun:</span><span class="sxs-lookup"><span data-stu-id="762f9-147">Place the following line of code in the event procedure:</span></span>  
  
    ```vb  
    MessageBox.Show("Goodbye!")  
    ```  
  
    ```csharp  
    MessageBox.Show("Goodbye!");  
    ```  
  
4.  <span data-ttu-id="762f9-148">Gelen **yapı** menüsünde seçin **yapı BaseForm Kitaplığı** sınıf kitaplığı oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="762f9-148">From the **Build** menu, choose **Build BaseForm Library** to build the class library.</span></span>  
  
     <span data-ttu-id="762f9-149">Kitaplığı oluşturulduktan sonra yeni oluşturduğunuz formundan devralan yeni bir proje oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="762f9-149">Once the library is built, you can create a new project that inherits from the form you just created.</span></span>  
  
#### <a name="to-create-a-project-containing-a-form-that-inherits-from-the-base-form"></a><span data-ttu-id="762f9-150">Temel formundan devralan bir form içeren bir proje oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="762f9-150">To create a project containing a form that inherits from the base form</span></span>  
  
1.  <span data-ttu-id="762f9-151">Gelen **dosya** menüsünde seçin **Ekle** ve ardından **yeni proje** açmak için **Yeni Proje Ekle** iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="762f9-151">From the **File** menu, choose **Add** and then **New Project** to open the **Add New Project** dialog box.</span></span>  
  
2.  <span data-ttu-id="762f9-152">Adlı bir Windows Forms uygulaması oluşturma `InheritanceTest`.</span><span class="sxs-lookup"><span data-stu-id="762f9-152">Create a Windows Forms application named `InheritanceTest`.</span></span>  
  
#### <a name="to-add-an-inherited-form"></a><span data-ttu-id="762f9-153">Devralınan bir form eklemek için</span><span class="sxs-lookup"><span data-stu-id="762f9-153">To add an inherited form</span></span>  
  
1.  <span data-ttu-id="762f9-154">İçinde **Çözüm Gezgini**, sağ **InheritanceTest** proje, select **Ekle**ve ardından**yeni öğe**.</span><span class="sxs-lookup"><span data-stu-id="762f9-154">In **Solution Explorer**, right-click the **InheritanceTest** project, select **Add**, and then select**New Item**.</span></span>  
  
2.  <span data-ttu-id="762f9-155">İçinde **Yeni Öğe Ekle** iletişim kutusunda **Windows Forms** (kategori listesi varsa) kategori ve ardından **devralınan Form** şablonu.</span><span class="sxs-lookup"><span data-stu-id="762f9-155">In the **Add New Item** dialog box, select the **Windows Forms** category (if you have a list of categories) and then select the **Inherited Form** template.</span></span>  
  
3.  <span data-ttu-id="762f9-156">Varsayılan adı bırakın `Form2` ve ardından **Ekle**.</span><span class="sxs-lookup"><span data-stu-id="762f9-156">Leave the default name of `Form2` and then click **Add**.</span></span>  
  
4.  <span data-ttu-id="762f9-157">İçinde **devralma Seçici** iletişim kutusunda **Form1** gelen **BaseFormLibrary** projesi devralınmalıdır tıklatıp form olarak **Tamam** .</span><span class="sxs-lookup"><span data-stu-id="762f9-157">In the **Inheritance Picker** dialog box, select **Form1** from the **BaseFormLibrary** project as the form to inherit from and click **OK**.</span></span>  
  
     <span data-ttu-id="762f9-158">Bu bir form oluşturur **InheritanceTest** biçiminde türetilen proje **BaseFormLibrary**.</span><span class="sxs-lookup"><span data-stu-id="762f9-158">This creates a form in the **InheritanceTest** project that derives from the form in **BaseFormLibrary**.</span></span>  
  
5.  <span data-ttu-id="762f9-159">Devralınan formunu açın (**Form2**) zaten açık değilse, çift tıklatarak Tasarımcısı'nda.</span><span class="sxs-lookup"><span data-stu-id="762f9-159">Open the inherited form (**Form2**) in the designer by double-clicking it, if it is not already open.</span></span>  
  
     <span data-ttu-id="762f9-160">Tasarımcısı'nda bir simge devralınan düğmeleri sahip (![VisualBasicInheritanceSymbol ekran görüntüsü](../../../../docs/framework/winforms/advanced/media/vbinheritanceglyph.gif "vbInheritanceGlyph")) bunlar devralınır gösteren kendi üst köşedeki.</span><span class="sxs-lookup"><span data-stu-id="762f9-160">In the designer, the inherited buttons have a symbol (![VisualBasicInheritanceSymbol screenshot](../../../../docs/framework/winforms/advanced/media/vbinheritanceglyph.gif "vbInheritanceGlyph")) in their upper corner, indicating they are inherited.</span></span>  
  
6.  <span data-ttu-id="762f9-161">Seçin **Say Hello** düğmesine tıklayın ve yeniden boyutlandırma inceleyin.</span><span class="sxs-lookup"><span data-stu-id="762f9-161">Select the **Say Hello** button and observe the resize handles.</span></span> <span data-ttu-id="762f9-162">Bu düğme korunduğu için Notlar taşıyabilir, yeniden boyutlandırabilir, resim yazısını değiştirmek ve başka değişiklikler yapmayın.</span><span class="sxs-lookup"><span data-stu-id="762f9-162">Because this button is protected, the inheritors can move it, resize it, change its caption, and make other modifications.</span></span>  
  
7.  <span data-ttu-id="762f9-163">Özel seçin **Say güle güle** düğmesi ve yeniden boyutlandırma yok dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="762f9-163">Select the private **Say Goodbye** button, and notice that it does not have resize handles.</span></span> <span data-ttu-id="762f9-164">Buna ek olarak **özellikleri** penceresinde, bu düğmenin özelliklerini gri bunlar değiştirilemez belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="762f9-164">Additionally, in the **Properties** window, the properties of this button are grayed to indicate they cannot be modified.</span></span>  
  
8.  <span data-ttu-id="762f9-165">Kullanıyorsanız [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="762f9-165">If you are using [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)]:</span></span>  
  
    1.  <span data-ttu-id="762f9-166">İçinde **Çözüm Gezgini**, sağ **Form1** içinde **InheritanceTest** proje ve ardından **silmek**.</span><span class="sxs-lookup"><span data-stu-id="762f9-166">In **Solution Explorer**, right-click **Form1** in the **InheritanceTest** project and then choose **Delete**.</span></span> <span data-ttu-id="762f9-167">Görüntülenen ileti kutusunda tıklatın **Tamam** silme işlemini onaylayın.</span><span class="sxs-lookup"><span data-stu-id="762f9-167">In the message box that appears, click **OK** to confirm the deletion.</span></span>  
  
    2.  <span data-ttu-id="762f9-168">Program.cs dosyasını açın ve satırı değiştirin `Application.Run(new Form1());` için `Application.Run(new Form2());`.</span><span class="sxs-lookup"><span data-stu-id="762f9-168">Open the Program.cs file and change the line `Application.Run(new Form1());` to `Application.Run(new Form2());`.</span></span>  
  
9. <span data-ttu-id="762f9-169">İçinde **Çözüm Gezgini**, sağ **InheritanceTest** proje ve seçin **başlangıç projesi olarak ayarla**.</span><span class="sxs-lookup"><span data-stu-id="762f9-169">In **Solution Explorer**, right-click the **InheritanceTest** project and select **Set As Startup Project**.</span></span>  
  
10. <span data-ttu-id="762f9-170">İçinde **Çözüm Gezgini**, sağ **InheritanceTest** proje ve seçin **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="762f9-170">In **Solution Explorer**, right-click the **InheritanceTest** project and select **Properties**.</span></span>  
  
11. <span data-ttu-id="762f9-171">İçinde **InheritanceTest** özellik sayfaları, ayarlamak **Başlangıç nesnesi** devralınan biçiminde için (**Form2**).</span><span class="sxs-lookup"><span data-stu-id="762f9-171">In the **InheritanceTest** property pages, set the **Startup object** to be the inherited form (**Form2**).</span></span>  
  
12. <span data-ttu-id="762f9-172">Uygulamayı çalıştırın ve devralınan form davranışını izlemek için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="762f9-172">Press F5 to run the application, and observe the behavior of the inherited form.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="762f9-173">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="762f9-173">Next Steps</span></span>  
 <span data-ttu-id="762f9-174">Kullanıcı denetimleri için devralma kadar aynı şekilde çalışır.</span><span class="sxs-lookup"><span data-stu-id="762f9-174">Inheritance for user controls works in much the same way.</span></span> <span data-ttu-id="762f9-175">Yeni bir sınıf kitaplığı projesi açın ve bir kullanıcı denetimi ekle.</span><span class="sxs-lookup"><span data-stu-id="762f9-175">Open a new class library project and add a user control.</span></span> <span data-ttu-id="762f9-176">Bağlı denetimler üzerindeki yerleştirin ve projeyi derleyin.</span><span class="sxs-lookup"><span data-stu-id="762f9-176">Place constituent controls on it and compile the project.</span></span> <span data-ttu-id="762f9-177">Başka bir yeni sınıf kitaplığı proje açın ve derlenmiş sınıf kitaplığına bir başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="762f9-177">Open another new class library project and add a reference to the compiled class library.</span></span> <span data-ttu-id="762f9-178">Ayrıca, devralınan bir denetim eklemeyi deneyin (aracılığıyla **yeni öğeler eklemek** iletişim kutusu) projeye ve kullanarak **devralma Seçici**.</span><span class="sxs-lookup"><span data-stu-id="762f9-178">Also, try adding an inherited control (through the **Add New Items** dialog box) to the project and using the **Inheritance Picker**.</span></span> <span data-ttu-id="762f9-179">Bir kullanıcı denetimi ekleme ve değiştirme `Inherits` (`:` içinde [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)]) ifadesi.</span><span class="sxs-lookup"><span data-stu-id="762f9-179">Add a user control, and change the `Inherits` (`:` in [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)]) statement.</span></span> <span data-ttu-id="762f9-180">Daha fazla bilgi için bkz: [nasıl yapılır: Windows Forms devral](../../../../docs/framework/winforms/advanced/how-to-inherit-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="762f9-180">For more information, see [How to: Inherit Windows Forms](../../../../docs/framework/winforms/advanced/how-to-inherit-windows-forms.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="762f9-181">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="762f9-181">See Also</span></span>  
 [<span data-ttu-id="762f9-182">Nasıl yapılır: Windows Forms’u Devralma</span><span class="sxs-lookup"><span data-stu-id="762f9-182">How to: Inherit Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-inherit-windows-forms.md)  
 [<span data-ttu-id="762f9-183">Windows Forms Görsel Devralma</span><span class="sxs-lookup"><span data-stu-id="762f9-183">Windows Forms Visual Inheritance</span></span>](../../../../docs/framework/winforms/advanced/windows-forms-visual-inheritance.md)  
 [<span data-ttu-id="762f9-184">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="762f9-184">Windows Forms</span></span>](../../../../docs/framework/winforms/index.md)
