---
title: "İzlenecek yol: Visual C# ile beraber Windows Forms Denetimi'nden Devralma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- inheritance [Windows Forms], custom controls
- inheritance [Windows Forms], control
- Windows Forms controls, inheritance
- inheritance [Windows Forms], walkthroughs
- custom controls [Windows Forms], inheritance
ms.assetid: 09476da0-8d4c-4a4c-b969-649519dfb438
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: adc8e4321dccea34b7d3132b2052ee9baa98a868
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="walkthrough-inheriting-from-a-windows-forms-control-with-visual-c"></a><span data-ttu-id="e9c25-102">İzlenecek yol: Visual C# ile beraber Windows Forms Denetimi'nden Devralma</span><span class="sxs-lookup"><span data-stu-id="e9c25-102">Walkthrough: Inheriting from a Windows Forms Control with Visual C#</span></span> #
<span data-ttu-id="e9c25-103">İle [!INCLUDE[csprcslong](../../../../includes/csprcslong-md.md)], güçlü özel denetimlerde oluşturabilirsiniz *devralma*.</span><span class="sxs-lookup"><span data-stu-id="e9c25-103">With [!INCLUDE[csprcslong](../../../../includes/csprcslong-md.md)], you can create powerful custom controls through *inheritance*.</span></span> <span data-ttu-id="e9c25-104">Devralma sayesinde, tüm standart Windows Forms denetimleri devralınmış işlevselliğini korur, ancak ayrıca özel işlevselliğine sahiptir denetimleri oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e9c25-104">Through inheritance you are able to create controls that retain all of the inherent functionality of standard Windows Forms controls but also incorporate custom functionality.</span></span> <span data-ttu-id="e9c25-105">Bu kılavuzda, adlı basit bir devralınan denetim oluşturacak `ValueButton`.</span><span class="sxs-lookup"><span data-stu-id="e9c25-105">In this walkthrough, you will create a simple inherited control called `ValueButton`.</span></span> <span data-ttu-id="e9c25-106">Bu düğme standart Windows formlarının dışında işlevselliği devralır <xref:System.Windows.Forms.Button> denetlemek ve adlı özel bir özellik kullanıma `ButtonValue`.</span><span class="sxs-lookup"><span data-stu-id="e9c25-106">This button will inherit functionality from the standard Windows Forms <xref:System.Windows.Forms.Button> control, and will expose a custom property called `ButtonValue`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e9c25-107">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="e9c25-107">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="e9c25-108">Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="e9c25-108">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="e9c25-109">Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="e9c25-109">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="e9c25-110">Projeyi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="e9c25-110">Creating the Project</span></span>  
 <span data-ttu-id="e9c25-111">Yeni bir proje oluşturduğunuzda, kök ad alanı, derleme adı ve proje adı ayarlamak için ve varsayılan bileşen doğru ad alanında olduğundan emin olmak için adını belirtin.</span><span class="sxs-lookup"><span data-stu-id="e9c25-111">When you create a new project, you specify its name in order to set the root namespace, assembly name, and project name, and to ensure that the default component will be in the correct namespace.</span></span>  
  
#### <a name="to-create-the-valuebuttonlib-control-library-and-the-valuebutton-control"></a><span data-ttu-id="e9c25-112">ValueButtonLib denetim kitaplığı ve ValueButton denetimi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="e9c25-112">To create the ValueButtonLib control library and the ValueButton control</span></span>  
  
1.  <span data-ttu-id="e9c25-113">Üzerinde **dosya** menüsündeki **yeni** ve ardından **proje** açmak için **yeni proje** iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="e9c25-113">On the **File** menu, point to **New** and then click **Project** to open the **New Project** dialog box.</span></span>  
  
2.  <span data-ttu-id="e9c25-114">Seçin **Windows Forms Denetim Kitaplığı** proje şablonu listesinden [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] projeleri ve türü `ValueButtonLib` içinde **adı** kutusu.</span><span class="sxs-lookup"><span data-stu-id="e9c25-114">Select the **Windows Forms Control Library** project template from the list of [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] Projects, and type `ValueButtonLib` in the **Name** box.</span></span>  
  
     <span data-ttu-id="e9c25-115">Proje adı `ValueButtonLib`, kök ad alanı için varsayılan olarak da atanmış.</span><span class="sxs-lookup"><span data-stu-id="e9c25-115">The project name, `ValueButtonLib`, is also assigned to the root namespace by default.</span></span> <span data-ttu-id="e9c25-116">Kök ad derleme bileşenlerinde adlarını nitelemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e9c25-116">The root namespace is used to qualify the names of components in the assembly.</span></span> <span data-ttu-id="e9c25-117">Örneğin, iki derleme adlı bileşenleri sağlarsanız `ValueButton`, belirtebilirsiniz, `ValueButton` bileşenini kullanarak `ValueButtonLib.ValueButton`.</span><span class="sxs-lookup"><span data-stu-id="e9c25-117">For example, if two assemblies provide components named `ValueButton`, you can specify your `ValueButton` component using `ValueButtonLib.ValueButton`.</span></span> <span data-ttu-id="e9c25-118">Daha fazla bilgi için bkz: [ad alanları](../../../csharp/programming-guide/namespaces/index.md).</span><span class="sxs-lookup"><span data-stu-id="e9c25-118">For more information, see [Namespaces](../../../csharp/programming-guide/namespaces/index.md).</span></span>  
  
3.  <span data-ttu-id="e9c25-119">İçinde **Çözüm Gezgini**, sağ **UserControl1.cs**, ardından **yeniden adlandırmak** kısayol menüsünden.</span><span class="sxs-lookup"><span data-stu-id="e9c25-119">In **Solution Explorer**, right-click **UserControl1.cs**, then choose **Rename** from the shortcut menu.</span></span> <span data-ttu-id="e9c25-120">Dosya adını değiştirmek `ValueButton.cs`.</span><span class="sxs-lookup"><span data-stu-id="e9c25-120">Change the file name to `ValueButton.cs`.</span></span> <span data-ttu-id="e9c25-121">Tıklatın **Evet** düğmesini tüm başvurularını kod öğesini yeniden adlandırmak istediğiniz sorulduğunda '`UserControl1`'.</span><span class="sxs-lookup"><span data-stu-id="e9c25-121">Click the **Yes** button when you are asked if you want to rename all references to the code element '`UserControl1`'.</span></span>  
  
4.  <span data-ttu-id="e9c25-122">İçinde **Çözüm Gezgini**, sağ **ValueButton.cs** seçip **görünümü kodu**.</span><span class="sxs-lookup"><span data-stu-id="e9c25-122">In **Solution Explorer**, right-click **ValueButton.cs** and select **View Code**.</span></span>  
  
5.  <span data-ttu-id="e9c25-123">Bulun `class` deyimi satır `public partial class ValueButton`, bu denetim devraldığı türünü değiştirip <xref:System.Windows.Forms.UserControl> için <xref:System.Windows.Forms.Button>.</span><span class="sxs-lookup"><span data-stu-id="e9c25-123">Locate the `class` statement line, `public partial class ValueButton`, and change the type from which this control inherits from <xref:System.Windows.Forms.UserControl> to <xref:System.Windows.Forms.Button>.</span></span> <span data-ttu-id="e9c25-124">Bu, tüm işlevselliğini devralmak, devralınan denetimi sağlar <xref:System.Windows.Forms.Button> denetim.</span><span class="sxs-lookup"><span data-stu-id="e9c25-124">This allows your inherited control to inherit all the functionality of the <xref:System.Windows.Forms.Button> control.</span></span>  
  
6.  <span data-ttu-id="e9c25-125">İçinde **Çözüm Gezgini**, açık **ValueButton.cs** Tasarımcısı ile oluşturulan kodun dosyayı görüntülemek için düğümü **ValueButton.Designer.cs**.</span><span class="sxs-lookup"><span data-stu-id="e9c25-125">In **Solution Explorer**, open the **ValueButton.cs** node to display the designer-generated code file, **ValueButton.Designer.cs**.</span></span> <span data-ttu-id="e9c25-126">Bu dosyayı açmak **Kod düzenleyicisinde**.</span><span class="sxs-lookup"><span data-stu-id="e9c25-126">Open this file in the **Code Editor**.</span></span>  
  
7.  <span data-ttu-id="e9c25-127">Bulun `InitializeComponent` yöntemi ekleme ve kaldırma atar satır <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="e9c25-127">Locate the `InitializeComponent` method and remove the line that assigns the <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> property.</span></span> <span data-ttu-id="e9c25-128">Bu özellik yok <xref:System.Windows.Forms.Button> denetim.</span><span class="sxs-lookup"><span data-stu-id="e9c25-128">This property does not exist in the <xref:System.Windows.Forms.Button> control.</span></span>  
  
8.  <span data-ttu-id="e9c25-129">Gelen **dosya** menüsünde seçin **Tümünü Kaydet** projeyi kaydetmek için.</span><span class="sxs-lookup"><span data-stu-id="e9c25-129">From the **File** menu, choose **Save All** to save the project.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e9c25-130">Görsel Tasarımcı artık kullanılamıyor.</span><span class="sxs-lookup"><span data-stu-id="e9c25-130">A visual designer is no longer available.</span></span> <span data-ttu-id="e9c25-131">Çünkü <xref:System.Windows.Forms.Button> denetim kendi boyama yok, görünümünü Tasarımcısı'nda değiştiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="e9c25-131">Because the <xref:System.Windows.Forms.Button> control does its own painting, you are unable to modify its appearance in the designer.</span></span> <span data-ttu-id="e9c25-132">Görsel gösterimi tam olarak bunu devraldığı sınıfı, aynı olacaktır (diğer bir deyişle, <xref:System.Windows.Forms.Button>) kodda değişiklik sürece.</span><span class="sxs-lookup"><span data-stu-id="e9c25-132">Its visual representation will be exactly the same as that of the class it inherits from (that is, <xref:System.Windows.Forms.Button>) unless modified in the code.</span></span> <span data-ttu-id="e9c25-133">Tasarım yüzeyine hiçbir kullanıcı Arabirimi öğeleri olan bileşenleri eklemeye devam edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e9c25-133">You can still add components, which have no UI elements, to the design surface.</span></span>  
  
## <a name="adding-a-property-to-your-inherited-control"></a><span data-ttu-id="e9c25-134">Devralınan denetiminizi özellik ekleme</span><span class="sxs-lookup"><span data-stu-id="e9c25-134">Adding a Property to Your Inherited Control</span></span>  
 <span data-ttu-id="e9c25-135">Bir olası devralınan Windows Forms denetimleri, Görünüm ve yapısını standart Windows Forms denetimleri aynıdır, ancak özel özelliklerini ortaya denetimleri oluşturulmasını kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e9c25-135">One possible use of inherited Windows Forms controls is the creation of controls that are identical in look and feel of standard Windows Forms controls, but expose custom properties.</span></span> <span data-ttu-id="e9c25-136">Bu bölümde, adlı bir özellik ekleyecek `ButtonValue` denetiminiz için.</span><span class="sxs-lookup"><span data-stu-id="e9c25-136">In this section, you will add a property called `ButtonValue` to your control.</span></span>  
  
#### <a name="to-add-the-value-property"></a><span data-ttu-id="e9c25-137">Value özelliği eklemek için</span><span class="sxs-lookup"><span data-stu-id="e9c25-137">To add the Value property</span></span>  
  
1.  <span data-ttu-id="e9c25-138">İçinde **Çözüm Gezgini**, sağ **ValueButton.cs**ve ardından **görünümü kodu** kısayol menüsünden.</span><span class="sxs-lookup"><span data-stu-id="e9c25-138">In **Solution Explorer**, right-click **ValueButton.cs**, and then click **View Code** from the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="e9c25-139">Bulun `class` deyimi.</span><span class="sxs-lookup"><span data-stu-id="e9c25-139">Locate the `class` statement.</span></span> <span data-ttu-id="e9c25-140">Hemen sonra `{`, aşağıdaki kodu yazın:</span><span class="sxs-lookup"><span data-stu-id="e9c25-140">Immediately after the `{`, type the following code:</span></span>  
  
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
  
     <span data-ttu-id="e9c25-141">Bu kod yöntemleri olarak ayarlar `ButtonValue` özelliği depolanır ve alınır.</span><span class="sxs-lookup"><span data-stu-id="e9c25-141">This code sets the methods by which the `ButtonValue` property is stored and retrieved.</span></span> <span data-ttu-id="e9c25-142">`get` Deyimi ayarlar özel değişkeninde depolanan değere döndürülen değer `varValue`ve `set` deyimi kullanarak özel değişkenin değerini ayarlar `value` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="e9c25-142">The `get` statement sets the value returned to the value that is stored in the private variable `varValue`, and the `set` statement sets the value of the private variable by use of the `value` keyword.</span></span>  
  
3.  <span data-ttu-id="e9c25-143">Gelen **dosya** menüsünde seçin **Tümünü Kaydet** projeyi kaydetmek için.</span><span class="sxs-lookup"><span data-stu-id="e9c25-143">From the **File** menu, choose **Save All** to save the project.</span></span>  
  
## <a name="testing-your-control"></a><span data-ttu-id="e9c25-144">Denetim test etme</span><span class="sxs-lookup"><span data-stu-id="e9c25-144">Testing Your Control</span></span>  
 <span data-ttu-id="e9c25-145">Denetimleri tek başına projeleri değildir; bir kapsayıcıda barındırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e9c25-145">Controls are not stand-alone projects; they must be hosted in a container.</span></span> <span data-ttu-id="e9c25-146">Denetim test etmek amacıyla çalıştırmak için test projesi için bu sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e9c25-146">In order to test your control, you must provide a test project for it to run in.</span></span> <span data-ttu-id="e9c25-147">Ayrıca, Denetim test projesi için erişilebilir (derleme) oluşturarak yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e9c25-147">You must also make your control accessible to the test project by building (compiling) it.</span></span> <span data-ttu-id="e9c25-148">Bu bölümde, denetiminizi oluşturabilirsiniz ve bir Windows formunda sınayın.</span><span class="sxs-lookup"><span data-stu-id="e9c25-148">In this section, you will build your control and test it in a Windows Form.</span></span>  
  
#### <a name="to-build-your-control"></a><span data-ttu-id="e9c25-149">Denetim oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="e9c25-149">To build your control</span></span>  
  
1.  <span data-ttu-id="e9c25-150">Üzerinde **yapı** menüsünde tıklatın **yapı çözümü**.</span><span class="sxs-lookup"><span data-stu-id="e9c25-150">On the **Build** menu, click **Build Solution**.</span></span>  
  
     <span data-ttu-id="e9c25-151">Yapı hiçbir derleyici hataları veya uyarılarla başarılı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="e9c25-151">The build should be successful with no compiler errors or warnings.</span></span>  
  
#### <a name="to-create-a-test-project"></a><span data-ttu-id="e9c25-152">Bir test projesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="e9c25-152">To create a test project</span></span>  
  
1.  <span data-ttu-id="e9c25-153">Üzerinde **dosya** menüsündeki **Ekle** ve ardından **yeni proje** açmak için **Yeni Proje Ekle** iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="e9c25-153">On the **File** menu, point to **Add** and then click **New Project** to open the **Add New Project** dialog box.</span></span>  
  
2.  <span data-ttu-id="e9c25-154">Seçin **Windows** düğümü, beneath **Visual C#** düğümü ve tıklatın **Windows Forms uygulaması**.</span><span class="sxs-lookup"><span data-stu-id="e9c25-154">Select the **Windows** node, beneath the **Visual C#** node, and click **Windows Forms Application**.</span></span>  
  
3.  <span data-ttu-id="e9c25-155">İçinde **adı** kutusuna `Test`.</span><span class="sxs-lookup"><span data-stu-id="e9c25-155">In the **Name** box, type `Test`.</span></span>  
  
4.  <span data-ttu-id="e9c25-156">İçinde **Çözüm Gezgini**, sağ **başvuruları** , test projeniz için düğümü seçip **Başvuru Ekle** görüntülemek için kısayol menüsünden  **Başvuru ekleme** iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="e9c25-156">In **Solution Explorer**, right-click the **References** node for your test project, then select **Add Reference** from the shortcut menu to display the **Add Reference** dialog box.</span></span>  
  
5.  <span data-ttu-id="e9c25-157">Etiketli sekmesini **projeleri**.</span><span class="sxs-lookup"><span data-stu-id="e9c25-157">Click the tab labeled **Projects**.</span></span> <span data-ttu-id="e9c25-158">`ValueButtonLib` Proje altında listelenir **proje adı**.</span><span class="sxs-lookup"><span data-stu-id="e9c25-158">Your `ValueButtonLib` project will be listed under **Project Name**.</span></span> <span data-ttu-id="e9c25-159">Projeyi test projesinin başvuru eklemek için çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="e9c25-159">Double-click the project to add the reference to the test project.</span></span>  
  
6.  <span data-ttu-id="e9c25-160">İçinde **Çözüm Gezgini** sağ **Test** seçip **yapı**.</span><span class="sxs-lookup"><span data-stu-id="e9c25-160">In **Solution Explorer,** right-click **Test** and select **Build**.</span></span>  
  
#### <a name="to-add-your-control-to-the-form"></a><span data-ttu-id="e9c25-161">Forma denetim ekleme</span><span class="sxs-lookup"><span data-stu-id="e9c25-161">To add your control to the form</span></span>  
  
1.  <span data-ttu-id="e9c25-162">İçinde **Çözüm Gezgini**, sağ **Form1.cs** ve **Görünüm Tasarımcısı** kısayol menüsünden.</span><span class="sxs-lookup"><span data-stu-id="e9c25-162">In **Solution Explorer**, right-click **Form1.cs** and choose **View Designer** from the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="e9c25-163">İçinde **araç**, tıklatın **ValueButtonLib bileşenleri**.</span><span class="sxs-lookup"><span data-stu-id="e9c25-163">In the **Toolbox**, click **ValueButtonLib Components**.</span></span> <span data-ttu-id="e9c25-164">Çift **ValueButton**.</span><span class="sxs-lookup"><span data-stu-id="e9c25-164">Double-click **ValueButton**.</span></span>  
  
     <span data-ttu-id="e9c25-165">A **ValueButton** formda görünür.</span><span class="sxs-lookup"><span data-stu-id="e9c25-165">A **ValueButton** appears on the form.</span></span>  
  
3.  <span data-ttu-id="e9c25-166">Sağ **ValueButton** seçip **özellikleri** kısayol menüsünden.</span><span class="sxs-lookup"><span data-stu-id="e9c25-166">Right-click the **ValueButton** and select **Properties** from the shortcut menu.</span></span>  
  
4.  <span data-ttu-id="e9c25-167">İçinde **özellikleri** penceresinde, bu denetim özelliklerini inceleyin.</span><span class="sxs-lookup"><span data-stu-id="e9c25-167">In the **Properties** window, examine the properties of this control.</span></span> <span data-ttu-id="e9c25-168">Bir ek özellik olmasını dışında bunların özdeş standart bir düğme tarafından kullanıma sunulan özellikler için olduğunu unutmayın `ButtonValue`.</span><span class="sxs-lookup"><span data-stu-id="e9c25-168">Note that they are identical to the properties exposed by a standard button, except that there is an additional property, `ButtonValue`.</span></span>  
  
5.  <span data-ttu-id="e9c25-169">Ayarlama `ButtonValue` özelliğine `5`.</span><span class="sxs-lookup"><span data-stu-id="e9c25-169">Set the `ButtonValue` property to `5`.</span></span>  
  
6.  <span data-ttu-id="e9c25-170">İçinde **tüm Windows Forms** sekmesinde **araç kutusu**, çift **etiket** eklemek için bir <xref:System.Windows.Forms.Label> Formunuza denetim.</span><span class="sxs-lookup"><span data-stu-id="e9c25-170">In the **All Windows Forms** tab of the **Toolbox**, double-click **Label** to add a <xref:System.Windows.Forms.Label> control to your form.</span></span>  
  
7.  <span data-ttu-id="e9c25-171">Etiket formu merkezine taşımanızı.</span><span class="sxs-lookup"><span data-stu-id="e9c25-171">Relocate the label to the center of the form.</span></span>  
  
8.  <span data-ttu-id="e9c25-172">Çift `valueButton1`.</span><span class="sxs-lookup"><span data-stu-id="e9c25-172">Double-click `valueButton1`.</span></span>  
  
     <span data-ttu-id="e9c25-173">**Kod düzenleyicisinde** açılır `valueButton1_Click` olay.</span><span class="sxs-lookup"><span data-stu-id="e9c25-173">The **Code Editor** opens to the `valueButton1_Click` event.</span></span>  
  
9. <span data-ttu-id="e9c25-174">Aşağıdaki kod satırını ekleyin.</span><span class="sxs-lookup"><span data-stu-id="e9c25-174">Insert the following line of code.</span></span>  
  
    ```csharp  
    label1.Text = valueButton1.ButtonValue.ToString();  
    ```  
  
10. <span data-ttu-id="e9c25-175">İçinde **Çözüm Gezgini**, sağ **Test**ve seçin **başlangıç projesi olarak ayarla** kısayol menüsünden.</span><span class="sxs-lookup"><span data-stu-id="e9c25-175">In **Solution Explorer**, right-click **Test**, and choose **Set as Startup Project** from the shortcut menu.</span></span>  
  
11. <span data-ttu-id="e9c25-176">Gelen **hata ayıklama** menüsünde, select **hata ayıklamayı Başlat**.</span><span class="sxs-lookup"><span data-stu-id="e9c25-176">From the **Debug** menu, select **Start Debugging**.</span></span>  
  
     <span data-ttu-id="e9c25-177">`Form1`görünür.</span><span class="sxs-lookup"><span data-stu-id="e9c25-177">`Form1` appears.</span></span>  
  
12. <span data-ttu-id="e9c25-178">Tıklatın `valueButton1`.</span><span class="sxs-lookup"><span data-stu-id="e9c25-178">Click `valueButton1`.</span></span>  
  
     <span data-ttu-id="e9c25-179">'5' rakamı görüntülenen `label1`, gösteren, `ButtonValue` devralınan denetiminizin özelliği için geçirilmiş `label1` aracılığıyla `valueButton1_Click` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e9c25-179">The numeral '5' is displayed in `label1`, demonstrating that the `ButtonValue` property of your inherited control has been passed to `label1` through the `valueButton1_Click` method.</span></span> <span data-ttu-id="e9c25-180">Bu nedenle, `ValueButton` denetimi standart Windows Forms düğme tüm işlevselliğini devralır, ancak ek, özel bir özellik sunar.</span><span class="sxs-lookup"><span data-stu-id="e9c25-180">Thus your `ValueButton` control inherits all the functionality of the standard Windows Forms button, but exposes an additional, custom property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9c25-181">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e9c25-181">See Also</span></span>  
 [<span data-ttu-id="e9c25-182">Bileşenleri ile programlama</span><span class="sxs-lookup"><span data-stu-id="e9c25-182">Programming with Components</span></span>](http://msdn.microsoft.com/library/d4d4fcb4-e0b8-46b3-b679-7ee0026eb9e3)  
 [<span data-ttu-id="e9c25-183">Bileşen geliştirme izlenecek yollar</span><span class="sxs-lookup"><span data-stu-id="e9c25-183">Component Authoring Walkthroughs</span></span>](http://msdn.microsoft.com/library/c414cca9-2489-4208-8b38-954586d91c13)  
 [<span data-ttu-id="e9c25-184">Nasıl yapılır: Araç Kutusu Öğelerini Seç İletişim Kutusunda bir Denetimi Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="e9c25-184">How to: Display a Control in the Choose Toolbox Items Dialog Box</span></span>](../../../../docs/framework/winforms/controls/how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)  
 [<span data-ttu-id="e9c25-185">İzlenecek yol: Visual C# İle Bileşik Denetim Yazma</span><span class="sxs-lookup"><span data-stu-id="e9c25-185">Walkthrough: Authoring a Composite Control with Visual C#</span></span>](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-csharp.md)
