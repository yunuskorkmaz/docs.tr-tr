---
title: 'İzlenecek yol: Visual C# İle Bileşik Denetim Yazma'
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [C#]
- user controls [Windows Forms], creating with Visual C#
- UserControl class [Windows Forms], walkthroughs
- user controls [C#]
- custom controls [Windows Forms], creating
ms.assetid: f88481a8-c746-4a36-9479-374ce5f2e91f
ms.openlocfilehash: 5f8384140b813400e106ad959684264304541c93
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "44038133"
---
# <a name="walkthrough-authoring-a-composite-control-with-visual-c"></a><span data-ttu-id="f2db1-102">İzlenecek yol: Visual C# İle Bileşik Denetim Yazma</span><span class="sxs-lookup"><span data-stu-id="f2db1-102">Walkthrough: Authoring a Composite Control with Visual C#</span></span> #
<span data-ttu-id="f2db1-103">Bileşik denetimler, özel bir grafik arabirim oluşturulabilir yeniden ve bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="f2db1-103">Composite controls provide a means by which custom graphical interfaces can be created and reused.</span></span> <span data-ttu-id="f2db1-104">Bileşik Denetim aslında bir görsel bir temsili ile bileşenidir.</span><span class="sxs-lookup"><span data-stu-id="f2db1-104">A composite control is essentially a component with a visual representation.</span></span> <span data-ttu-id="f2db1-105">Bu nedenle, bir veya daha fazla Windows Forms denetimleri, bileşenleri veya kullanıcı girişini doğrulama, görüntü özelliklerini değiştirerek veya yazar tarafından gereken diğer görevleri gerçekleştirme işlevselliğini genişletebildiği kod bloklarını oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="f2db1-105">As such, it might consist of one or more Windows Forms controls, components, or blocks of code that can extend functionality by validating user input, modifying display properties, or performing other tasks required by the author.</span></span> <span data-ttu-id="f2db1-106">Bileşik denetimler, diğer denetimlerle aynı şekilde Windows formlarında yerleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="f2db1-106">Composite controls can be placed on Windows Forms in the same manner as other controls.</span></span> <span data-ttu-id="f2db1-107">Bu kılavuzun ilk bölümünde oluşturduğunuz adlı basit bir bileşik denetim `ctlClock`.</span><span class="sxs-lookup"><span data-stu-id="f2db1-107">In the first part of this walkthrough, you create a simple composite control called `ctlClock`.</span></span> <span data-ttu-id="f2db1-108">İzlenecek yol ikinci kısmında, işlevlerini genişletmek `ctlClock` devralma yoluyla.</span><span class="sxs-lookup"><span data-stu-id="f2db1-108">In the second part of the walkthrough, you extend the functionality of `ctlClock` through inheritance.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f2db1-109">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="f2db1-109">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="f2db1-110">Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="f2db1-110">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="f2db1-111">Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="f2db1-111">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="f2db1-112">Projeyi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="f2db1-112">Creating the Project</span></span>  
 <span data-ttu-id="f2db1-113">Yeni bir proje oluşturduğunuzda, kök ad alanı, derleme adı ve proje adını ayarlayın ve varsayılan bileşeni doğru ad alanı içinde olmasını sağlamak için adını belirtin.</span><span class="sxs-lookup"><span data-stu-id="f2db1-113">When you create a new project, you specify its name to set the root namespace, assembly name, and project name, and ensure that the default component will be in the correct namespace.</span></span>  
  
#### <a name="to-create-the-ctlclocklib-control-library-and-the-ctlclock-control"></a><span data-ttu-id="f2db1-114">CtlClockLib denetim kitaplığı ve ctlClock denetimi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="f2db1-114">To create the ctlClockLib control library and the ctlClock control</span></span>  
  
1.  <span data-ttu-id="f2db1-115">Üzerinde **dosya** menüsünde **yeni**ve ardından **proje** açmak için **yeni proje** iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="f2db1-115">On the **File** menu, point to **New**, and then click **Project** to open the **New Project** dialog box.</span></span>  
  
2.  <span data-ttu-id="f2db1-116">Visual C# projelerinin listesinden **Windows Forms Denetim Kitaplığı** proje şablonu, türü `ctlClockLib` içinde **adı** kutusuna ve ardından **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="f2db1-116">From the list of Visual C# projects, select the **Windows Forms Control Library** project template, type `ctlClockLib` in the **Name** box, and then click **OK**.</span></span>  
  
     <span data-ttu-id="f2db1-117">Proje adı `ctlClockLib`, aynı zamanda kök ad alanı için varsayılan olarak atanır.</span><span class="sxs-lookup"><span data-stu-id="f2db1-117">The project name, `ctlClockLib`, is also assigned to the root namespace by default.</span></span> <span data-ttu-id="f2db1-118">Kök ad alanı, bileşenleri derleme içindeki adlarını nitelemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f2db1-118">The root namespace is used to qualify the names of components in the assembly.</span></span> <span data-ttu-id="f2db1-119">Örneğin, iki derleme adlı bileşenleri sağlarsanız `ctlClock`, belirtebilirsiniz, `ctlClock` bileşenini kullanma `ctlClockLib.ctlClock.`</span><span class="sxs-lookup"><span data-stu-id="f2db1-119">For example, if two assemblies provide components named `ctlClock`, you can specify your `ctlClock` component using `ctlClockLib.ctlClock.`</span></span>  
  
3.  <span data-ttu-id="f2db1-120">Çözüm Gezgini'nde sağ **UserControl1.cs**ve ardından **Yeniden Adlandır**.</span><span class="sxs-lookup"><span data-stu-id="f2db1-120">In Solution Explorer, right-click **UserControl1.cs**, and then click **Rename**.</span></span> <span data-ttu-id="f2db1-121">İçin dosya adını değiştirerek `ctlClock.cs`.</span><span class="sxs-lookup"><span data-stu-id="f2db1-121">Change the file name to `ctlClock.cs`.</span></span> <span data-ttu-id="f2db1-122">Tıklayın **Evet** yaptığınız kod öğesi "UserControl1" için tüm başvuruları yeniden adlandırmak isteyip istemediğiniz sorulduğunda düğmesi.</span><span class="sxs-lookup"><span data-stu-id="f2db1-122">Click the **Yes** button when you are asked if you want to rename all references to the code element "UserControl1".</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f2db1-123">Bileşik denetim varsayılan olarak, devralınan <xref:System.Windows.Forms.UserControl> sistem tarafından sağlanan sınıfı.</span><span class="sxs-lookup"><span data-stu-id="f2db1-123">By default, a composite control inherits from the <xref:System.Windows.Forms.UserControl> class provided by the system.</span></span> <span data-ttu-id="f2db1-124"><xref:System.Windows.Forms.UserControl> Sınıfı tüm bileşik denetimler tarafından gerekli işlevselliği sunar ve standart yöntemleri ve özellikleri uygular.</span><span class="sxs-lookup"><span data-stu-id="f2db1-124">The <xref:System.Windows.Forms.UserControl> class provides functionality required by all composite controls, and implements standard methods and properties.</span></span>  
  
4.  <span data-ttu-id="f2db1-125">Üzerinde **dosya** menüsünü tıklatın **Tümünü Kaydet** projeyi kaydetmek için.</span><span class="sxs-lookup"><span data-stu-id="f2db1-125">On the **File** menu, click **Save All** to save the project.</span></span>  
  
## <a name="adding-windows-controls-and-components-to-the-composite-control"></a><span data-ttu-id="f2db1-126">Windows ekleme denetimleri ve bileşenleri bileşik denetim</span><span class="sxs-lookup"><span data-stu-id="f2db1-126">Adding Windows Controls and Components to the Composite Control</span></span>  
 <span data-ttu-id="f2db1-127">Görsel bir arabirim, bileşik denetim önemli bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="f2db1-127">A visual interface is an essential part of your composite control.</span></span> <span data-ttu-id="f2db1-128">Bu görsel arabirim Tasarımcı yüzeyine bir veya daha fazla Windows denetimleri eklenmesini tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="f2db1-128">This visual interface is implemented by the addition of one or more Windows controls to the designer surface.</span></span> <span data-ttu-id="f2db1-129">Aşağıdaki örnekte, Windows denetimleri, bileşik denetime eklemek ve işlevselliği uygulamak için kod yazın.</span><span class="sxs-lookup"><span data-stu-id="f2db1-129">In the following demonstration, you will incorporate Windows controls into your composite control and write code to implement functionality.</span></span>  
  
#### <a name="to-add-a-label-and-a-timer-to-your-composite-control"></a><span data-ttu-id="f2db1-130">Bir etiket ve Zamanlayıcı bileşik denetiminize eklemek için</span><span class="sxs-lookup"><span data-stu-id="f2db1-130">To add a Label and a Timer to your composite control</span></span>  
  
1.  <span data-ttu-id="f2db1-131">Çözüm Gezgini'nde sağ **ctlClock.cs**ve ardından **Görünüm Tasarımcısı**.</span><span class="sxs-lookup"><span data-stu-id="f2db1-131">In Solution Explorer, right-click **ctlClock.cs**, and then click **View Designer**.</span></span>  
  
2.  <span data-ttu-id="f2db1-132">İçinde **araç kutusu**, genişletme **ortak denetimleri** düğüm gittikten sonra çift tıklayarak **etiket**.</span><span class="sxs-lookup"><span data-stu-id="f2db1-132">In the **Toolbox**, expand the **Common Controls** node, and then double-click **Label**.</span></span>  
  
     <span data-ttu-id="f2db1-133">A <xref:System.Windows.Forms.Label> adlı Denetim `label1` Tasarımcı yüzeyinde, denetimi eklenir.</span><span class="sxs-lookup"><span data-stu-id="f2db1-133">A <xref:System.Windows.Forms.Label> control named `label1` is added to your control on the designer surface.</span></span>  
  
3.  <span data-ttu-id="f2db1-134">Tasarımcıda **label1**.</span><span class="sxs-lookup"><span data-stu-id="f2db1-134">In the designer, click **label1**.</span></span> <span data-ttu-id="f2db1-135">Özellikler penceresinde, aşağıdaki özellikleri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="f2db1-135">In the Properties window, set the following properties.</span></span>  
  
    |<span data-ttu-id="f2db1-136">Özellik</span><span class="sxs-lookup"><span data-stu-id="f2db1-136">Property</span></span>|<span data-ttu-id="f2db1-137">Değiştirin</span><span class="sxs-lookup"><span data-stu-id="f2db1-137">Change to</span></span>|  
    |--------------|---------------|  
    |<span data-ttu-id="f2db1-138">**Ad**</span><span class="sxs-lookup"><span data-stu-id="f2db1-138">**Name**</span></span>|`lblDisplay`|  
    |<span data-ttu-id="f2db1-139">**Metin**</span><span class="sxs-lookup"><span data-stu-id="f2db1-139">**Text**</span></span>|`(blank space)`|  
    |<span data-ttu-id="f2db1-140">**TextAlign**</span><span class="sxs-lookup"><span data-stu-id="f2db1-140">**TextAlign**</span></span>|`MiddleCenter`|  
    |<span data-ttu-id="f2db1-141">**Font.Size**</span><span class="sxs-lookup"><span data-stu-id="f2db1-141">**Font.Size**</span></span>|`14`|  
  
4.  <span data-ttu-id="f2db1-142">İçinde **araç kutusu**, genişletme **bileşenleri** düğüm gittikten sonra çift tıklayarak **Zamanlayıcı**.</span><span class="sxs-lookup"><span data-stu-id="f2db1-142">In the **Toolbox**, expand the **Components** node, and then double-click **Timer**.</span></span>  
  
     <span data-ttu-id="f2db1-143">Çünkü bir <xref:System.Windows.Forms.Timer> bir bileşen çalışma zamanında görsel bir temsili sahiptir.</span><span class="sxs-lookup"><span data-stu-id="f2db1-143">Because a <xref:System.Windows.Forms.Timer> is a component, it has no visual representation at run time.</span></span> <span data-ttu-id="f2db1-144">Bu nedenle, bu Tasarımcı yüzeyine denetimler ile ancak bunun yerine görünmez **Bileşen Tasarımcısı** (tasarımcı yüzeyine alt kısmındaki Tepsisi).</span><span class="sxs-lookup"><span data-stu-id="f2db1-144">Therefore, it does not appear with the controls on the designer surface, but rather in the **Component Designer** (a tray at the bottom of the designer surface).</span></span>  
  
5.  <span data-ttu-id="f2db1-145">İçinde **Bileşen Tasarımcısı**, tıklayın **Süreölçer1**ve ardından <xref:System.Windows.Forms.Timer.Interval%2A> özelliğini `1000` ve <xref:System.Windows.Forms.Timer.Enabled%2A> özelliğini `true`.</span><span class="sxs-lookup"><span data-stu-id="f2db1-145">In the **Component Designer**, click **timer1**, and then set the <xref:System.Windows.Forms.Timer.Interval%2A> property to `1000` and the <xref:System.Windows.Forms.Timer.Enabled%2A> property to `true`.</span></span>  
  
     <span data-ttu-id="f2db1-146"><xref:System.Windows.Forms.Timer.Interval%2A> Özelliği sıklığı denetleyen <xref:System.Windows.Forms.Timer> bileşen işaretleri.</span><span class="sxs-lookup"><span data-stu-id="f2db1-146">The <xref:System.Windows.Forms.Timer.Interval%2A> property controls the frequency with which the <xref:System.Windows.Forms.Timer> component ticks.</span></span> <span data-ttu-id="f2db1-147">Her zaman `timer1` saat tıklaması, çalışırken kod `timer1_Tick` olay.</span><span class="sxs-lookup"><span data-stu-id="f2db1-147">Each time `timer1` ticks, it runs the code in the `timer1_Tick` event.</span></span> <span data-ttu-id="f2db1-148">Aralık işaretleri arasındaki milisaniye sayısını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f2db1-148">The interval represents the number of milliseconds between ticks.</span></span>  
  
6.  <span data-ttu-id="f2db1-149">İçinde **Bileşen Tasarımcısı**, çift **Süreölçer1** gitmek için `timer1_Tick` olayı `ctlClock`.</span><span class="sxs-lookup"><span data-stu-id="f2db1-149">In the **Component Designer**, double-click **timer1** to go to the `timer1_Tick` event for `ctlClock`.</span></span>  
  
7.  <span data-ttu-id="f2db1-150">Kodu aşağıdaki kod örneği benzeyecek şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="f2db1-150">Modify the code so that it resembles the following code sample.</span></span> <span data-ttu-id="f2db1-151">Gelen erişim değiştiricisi değiştirdiğinizden emin olun `private` için `protected`.</span><span class="sxs-lookup"><span data-stu-id="f2db1-151">Be sure to change the access modifier from `private` to `protected`.</span></span>  
  
    ```csharp  
    protected void timer1_Tick(object sender, System.EventArgs e)  
    {  
        // Causes the label to display the current time.  
        lblDisplay.Text = DateTime.Now.ToLongTimeString();   
    }  
    ```  
  
     <span data-ttu-id="f2db1-152">Bu kodun geçerli saate göre gösterilecek neden olur `lblDisplay`.</span><span class="sxs-lookup"><span data-stu-id="f2db1-152">This code will cause the current time to be shown in `lblDisplay`.</span></span> <span data-ttu-id="f2db1-153">Çünkü aralığı `timer1` ayarlandı `1000`, bu olay, böylece her saniye geçerli saati güncelleştiriliyor her bin milisaniye meydana gelir.</span><span class="sxs-lookup"><span data-stu-id="f2db1-153">Because the interval of `timer1` was set to `1000`, this event will occur every thousand milliseconds, thus updating the current time every second.</span></span>  
  
8.  <span data-ttu-id="f2db1-154">İle geçersiz kılınabilir olmasını yöntemi Değiştir `virtual` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="f2db1-154">Modify the method to be overridable with the `virtual` keyword.</span></span> <span data-ttu-id="f2db1-155">Daha fazla bilgi için "Devralan bir kullanıcı denetimi" bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="f2db1-155">For more information, see the  "Inheriting from a User Control" section below.</span></span>  
  
    ```csharp  
    protected virtual void timer1_Tick(object sender, System.EventArgs e)  
    ```  
  
9. <span data-ttu-id="f2db1-156">Üzerinde **dosya** menüsünü tıklatın **Tümünü Kaydet** projeyi kaydetmek için.</span><span class="sxs-lookup"><span data-stu-id="f2db1-156">On the **File** menu, click **Save All** to save the project.</span></span>  
  
## <a name="adding-properties-to-the-composite-control"></a><span data-ttu-id="f2db1-157">Bileşik denetime özellik ekleme</span><span class="sxs-lookup"><span data-stu-id="f2db1-157">Adding Properties to the Composite Control</span></span>  
 <span data-ttu-id="f2db1-158">Saat denetiminiz artık kapsülleyen bir <xref:System.Windows.Forms.Label> denetimi ve bir <xref:System.Windows.Forms.Timer> bileşeni, her biri kendi devralınan özellikler kümesi.</span><span class="sxs-lookup"><span data-stu-id="f2db1-158">Your clock control now encapsulates a <xref:System.Windows.Forms.Label> control and a <xref:System.Windows.Forms.Timer> component, each with its own set of inherent properties.</span></span> <span data-ttu-id="f2db1-159">Bu denetimlerin özelliklerini bireysel denetiminizin sonraki kullanıcılar için erişilebilir değil ancak oluşturabilir ve uygun blok kod yazarak özel özellikler kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="f2db1-159">While the individual properties of these controls will not be accessible to subsequent users of your control, you can create and expose custom properties by writing the appropriate blocks of code.</span></span> <span data-ttu-id="f2db1-160">Aşağıdaki yordamda, metin ve arka plan rengini değiştirmek kullanıcının denetiminize özellikler ekleyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="f2db1-160">In the following procedure, you will add properties to your control that enable the user to change the color of the background and text.</span></span>  
  
#### <a name="to-add-a-property-to-your-composite-control"></a><span data-ttu-id="f2db1-161">Bileşik denetiminiz için bir özellik eklemek için</span><span class="sxs-lookup"><span data-stu-id="f2db1-161">To add a property to your composite control</span></span>  
  
1.  <span data-ttu-id="f2db1-162">Çözüm Gezgini'nde sağ **ctlClock.cs**ve ardından **kodu görüntüle**.</span><span class="sxs-lookup"><span data-stu-id="f2db1-162">In Solution Explorer, right-click **ctlClock.cs**, and then click **View Code**.</span></span>  
  
     <span data-ttu-id="f2db1-163">**Kod Düzenleyicisi** denetiminiz açılır.</span><span class="sxs-lookup"><span data-stu-id="f2db1-163">The **Code Editor** for your control opens.</span></span>  
  
2.  <span data-ttu-id="f2db1-164">Bulun `public partial class ctlClock` deyimi.</span><span class="sxs-lookup"><span data-stu-id="f2db1-164">Locate the `public partial class ctlClock` statement.</span></span> <span data-ttu-id="f2db1-165">Açılış ayracından altında (`{)`, aşağıdaki kodu yazın.</span><span class="sxs-lookup"><span data-stu-id="f2db1-165">Beneath the opening brace (`{)`, type the following code.</span></span>  
  
    ```csharp  
    private Color colFColor;  
    private Color colBColor;  
    ```  
  
     <span data-ttu-id="f2db1-166">Bu deyimler oluşturmak üzere olduğunuz özelliklerinin değerlerini depolamak için kullanılacak özel değişkenleri oluşturun.</span><span class="sxs-lookup"><span data-stu-id="f2db1-166">These statements create the private variables that you will use to store the values for the properties you are about to create.</span></span>  
  
3.  <span data-ttu-id="f2db1-167">2. adımda bir değişken bildirimlerini altına aşağıdaki kodu yazın.</span><span class="sxs-lookup"><span data-stu-id="f2db1-167">Type the following code beneath the variable declarations from step 2.</span></span>  
  
    ```csharp  
    // Declares the name and type of the property.  
    public Color ClockBackColor  
    {  
        // Retrieves the value of the private variable colBColor.  
        get  
        {  
            return colBColor;  
        }  
        // Stores the selected value in the private variable colBColor, and   
        // updates the background color of the label control lblDisplay.  
        set  
        {  
            colBColor = value;  
            lblDisplay.BackColor = colBColor;     
        }  
    }  
    // Provides a similar set of instructions for the foreground color.  
    public Color ClockForeColor  
    {  
        get  
        {  
            return colFColor;  
        }  
        set  
        {  
            colFColor = value;  
            lblDisplay.ForeColor = colFColor;  
        }  
    }  
    ```  
  
     <span data-ttu-id="f2db1-168">Yukarıdaki kod, iki özel özellikler yapar `ClockForeColor` ve `ClockBackColor`, bu denetimin sonraki kullanıcılar tarafından kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f2db1-168">The preceding code makes two custom properties, `ClockForeColor` and `ClockBackColor`, available to subsequent users of this control.</span></span> <span data-ttu-id="f2db1-169">`get` Ve `set` deyimleri, depolama ve alma işlevselliğini uygulamak için kod yanı sıra özellik değeri, özellik için uygun sağlayın.</span><span class="sxs-lookup"><span data-stu-id="f2db1-169">The `get` and `set` statements provide for storage and retrieval of the property value, as well as code to implement functionality appropriate to the property.</span></span>  
  
4.  <span data-ttu-id="f2db1-170">Üzerinde **dosya** menüsünü tıklatın **Tümünü Kaydet** projeyi kaydetmek için.</span><span class="sxs-lookup"><span data-stu-id="f2db1-170">On the **File** menu, click **Save All** to save the project.</span></span>  
  
## <a name="testing-the-control"></a><span data-ttu-id="f2db1-171">Denetimini test etme</span><span class="sxs-lookup"><span data-stu-id="f2db1-171">Testing the Control</span></span>  
 <span data-ttu-id="f2db1-172">Denetimleri, tek başına uygulamalar değildir; Bunlar, bir kapsayıcıda barındırılan gerekir.</span><span class="sxs-lookup"><span data-stu-id="f2db1-172">Controls are not stand-alone applications; they must be hosted in a container.</span></span> <span data-ttu-id="f2db1-173">Denetimin çalışma zamanı davranışını sınama ve özellikleriyle birlikte çalışma **UserControl Test kapsayıcısı**.</span><span class="sxs-lookup"><span data-stu-id="f2db1-173">Test your control's run-time behavior and exercise its properties with the **UserControl Test Container**.</span></span> <span data-ttu-id="f2db1-174">Daha fazla bilgi için [nasıl yapılır: bir UserControl denetiminin çalışma zamanı davranışını sınama](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span><span class="sxs-lookup"><span data-stu-id="f2db1-174">For more information, see [How to: Test the Run-Time Behavior of a UserControl](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>  
  
#### <a name="to-test-your-control"></a><span data-ttu-id="f2db1-175">Denetiminiz test etmek için</span><span class="sxs-lookup"><span data-stu-id="f2db1-175">To test your control</span></span>  
  
1.  <span data-ttu-id="f2db1-176">Projeyi oluşturmak ve denetim çalıştırmak için F5 tuşuna basın **UserControl Test kapsayıcısı**.</span><span class="sxs-lookup"><span data-stu-id="f2db1-176">Press F5 to build the project and run your control in the **UserControl Test Container**.</span></span>  
  
2.  <span data-ttu-id="f2db1-177">Test kapsayıcının özellik kılavuzunda bulun `ClockBackColor` özelliği ve renk paletini görüntülenecek özelliği seçin.</span><span class="sxs-lookup"><span data-stu-id="f2db1-177">In the test container's property grid, locate the `ClockBackColor` property, and then select the property to display the color palette.</span></span>  
  
3.  <span data-ttu-id="f2db1-178">Tıklayarak bir renk seçin.</span><span class="sxs-lookup"><span data-stu-id="f2db1-178">Choose a color by clicking it.</span></span>  
  
     <span data-ttu-id="f2db1-179">Denetim arka plan rengi, seçtiğiniz rengine değiştirir.</span><span class="sxs-lookup"><span data-stu-id="f2db1-179">The background color of your control changes to the color you selected.</span></span>  
  
4.  <span data-ttu-id="f2db1-180">Doğrulamak için benzer bir olay dizisi kullanan `ClockForeColor` özelliği beklendiği gibi çalışmıyor.</span><span class="sxs-lookup"><span data-stu-id="f2db1-180">Use a similar sequence of events to verify that the `ClockForeColor` property is functioning as expected.</span></span>  
  
     <span data-ttu-id="f2db1-181">Bu bölümde ve önceki bölümlerde, bileşenleri ve Windows denetimleri nasıl birleştirileceğini gördünüz kodla ve paketleme bileşik denetim biçiminde özel işlevsellik sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="f2db1-181">In this section and the preceding sections, you have seen how components and Windows controls can be combined with code and packaging to provide custom functionality in the form of a composite control.</span></span> <span data-ttu-id="f2db1-182">Bileşik Denetim ve denetim, tamamlandıktan sonra test etme özellikleri göstermek öğrendiniz.</span><span class="sxs-lookup"><span data-stu-id="f2db1-182">You have learned to expose properties in your composite control, and how to test your control after it is complete.</span></span> <span data-ttu-id="f2db1-183">Sonraki bölümde kullanarak bir devralınan bileşik denetim oluşturmak hakkında bilgi edineceksiniz `ctlClock` temel olarak.</span><span class="sxs-lookup"><span data-stu-id="f2db1-183">In the next section you will learn how to construct an inherited composite control using `ctlClock` as a base.</span></span>  
  
## <a name="inheriting-from-a-composite-control"></a><span data-ttu-id="f2db1-184">Bileşik Denetim devralıyor</span><span class="sxs-lookup"><span data-stu-id="f2db1-184">Inheriting from a Composite Control</span></span>  
 <span data-ttu-id="f2db1-185">Önceki bölümlerde Windows denetimleri, bileşenleri ve kod yeniden kullanılabilir bileşik denetimler birleştirmek öğrendiniz.</span><span class="sxs-lookup"><span data-stu-id="f2db1-185">In the previous sections, you learned how to combine Windows controls, components, and code into reusable composite controls.</span></span> <span data-ttu-id="f2db1-186">Bileşik Denetim artık diğer denetimlerin oluşturulabilir, bir temel olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f2db1-186">Your composite control can now be used as a base upon which other controls can be built.</span></span> <span data-ttu-id="f2db1-187">Sınıf bir taban sınıftan türetme işlemine denir *devralma*.</span><span class="sxs-lookup"><span data-stu-id="f2db1-187">The process of deriving a class from a base class is called *inheritance*.</span></span> <span data-ttu-id="f2db1-188">Bu bölümde, adlı bileşik denetim oluşturacaksınız `ctlAlarmClock`.</span><span class="sxs-lookup"><span data-stu-id="f2db1-188">In this section, you will create a composite control called `ctlAlarmClock`.</span></span> <span data-ttu-id="f2db1-189">Bu denetim, üst denetiminden elde edilir `ctlClock`.</span><span class="sxs-lookup"><span data-stu-id="f2db1-189">This control will be derived from its parent control, `ctlClock`.</span></span> <span data-ttu-id="f2db1-190">Genişletmek öğreneceksiniz `ctlClock` üst yöntemleri geçersiz kılma ve yeni yöntemleri ve özellikleri ekleme.</span><span class="sxs-lookup"><span data-stu-id="f2db1-190">You will learn to extend the functionality of `ctlClock` by overriding parent methods and adding new methods and properties.</span></span>  
  
 <span data-ttu-id="f2db1-191">Devralınan bir denetim oluşturmanın ilk adımı, üst öğesinden türetilen sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="f2db1-191">The first step in creating an inherited control is to derive it from its parent.</span></span> <span data-ttu-id="f2db1-192">Bu eylem, tüm özellikleri, yöntemleri ve üst denetimin grafik özelliklerine sahip yeni bir denetim oluşturur, ancak yeni veya değiştirilmiş işlevselliği eklenmesi için temel olarak da hareket.</span><span class="sxs-lookup"><span data-stu-id="f2db1-192">This action creates a new control that has all of the properties, methods, and graphical characteristics of the parent control, but can also act as a base for the addition of new or modified functionality.</span></span>  
  
#### <a name="to-create-the-inherited-control"></a><span data-ttu-id="f2db1-193">Devralınan bir denetim oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="f2db1-193">To create the inherited control</span></span>  
  
1.  <span data-ttu-id="f2db1-194">Çözüm Gezgini'nde sağ **ctlClockLib**, işaret **Ekle**ve ardından **kullanıcı denetimi**.</span><span class="sxs-lookup"><span data-stu-id="f2db1-194">In Solution Explorer, right-click **ctlClockLib**, point to **Add**, and then click **User Control**.</span></span>  
  
     <span data-ttu-id="f2db1-195">**Yeni Öğe Ekle** iletişim kutusu açılır.</span><span class="sxs-lookup"><span data-stu-id="f2db1-195">The **Add New Item** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="f2db1-196">Seçin **devralınan kullanıcı denetimi** şablonu.</span><span class="sxs-lookup"><span data-stu-id="f2db1-196">Select the **Inherited User Control** template.</span></span>  
  
3.  <span data-ttu-id="f2db1-197">İçinde **adı** kutusuna `ctlAlarmClock.cs`ve ardından **Ekle**.</span><span class="sxs-lookup"><span data-stu-id="f2db1-197">In the **Name** box, type `ctlAlarmClock.cs`, and then click **Add**.</span></span>  
  
     <span data-ttu-id="f2db1-198">**Devralma Seçici** iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="f2db1-198">The **Inheritance Picker** dialog box appears.</span></span>  
  
4.  <span data-ttu-id="f2db1-199">Altında **bileşen adı**, çift **ctlClock**.</span><span class="sxs-lookup"><span data-stu-id="f2db1-199">Under **Component Name**, double-click **ctlClock**.</span></span>  
  
5.  <span data-ttu-id="f2db1-200">Çözüm Gezgini içinde geçerli projeleri göz atın.</span><span class="sxs-lookup"><span data-stu-id="f2db1-200">In Solution Explorer, browse through the current projects.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f2db1-201">Dosya adında **ctlAlarmClock.cs** geçerli projeye eklendi.</span><span class="sxs-lookup"><span data-stu-id="f2db1-201">A file called **ctlAlarmClock.cs** has been added to the current project.</span></span>  
  
### <a name="adding-the-alarm-properties"></a><span data-ttu-id="f2db1-202">Uyarı özellikleri ekleme</span><span class="sxs-lookup"><span data-stu-id="f2db1-202">Adding the Alarm Properties</span></span>  
 <span data-ttu-id="f2db1-203">Bileşik denetim için eklenen aynı şekilde, devralınan bir denetim için özellikler eklenir.</span><span class="sxs-lookup"><span data-stu-id="f2db1-203">Properties are added to an inherited control in the same way they are added to a composite control.</span></span> <span data-ttu-id="f2db1-204">Şimdi iki özellik denetiminize eklemek için özellik bildirimi sözdizimi kullanır: `AlarmTime`, tarih ve saat alarma olan kapalı, Git değerini depolar ve `AlarmSet`, hangi uyarı ayarlanıp ayarlanmadığını gösterecektir.</span><span class="sxs-lookup"><span data-stu-id="f2db1-204">You will now use the property declaration syntax to add two properties to your control: `AlarmTime`, which will store the value of the date and time the alarm is to go off, and `AlarmSet`, which will indicate whether the alarm is set.</span></span>  
  
##### <a name="to-add-properties-to-your-composite-control"></a><span data-ttu-id="f2db1-205">Özellikler birleşik denetiminize eklemek için</span><span class="sxs-lookup"><span data-stu-id="f2db1-205">To add properties to your composite control</span></span>  
  
1.  <span data-ttu-id="f2db1-206">Çözüm Gezgini'nde sağ **ctlAlarmClock**ve ardından **kodu görüntüle**.</span><span class="sxs-lookup"><span data-stu-id="f2db1-206">In Solution Explorer, right-click **ctlAlarmClock**, and then click **View Code**.</span></span>  
  
2.  <span data-ttu-id="f2db1-207">Bulun `public class` deyimi.</span><span class="sxs-lookup"><span data-stu-id="f2db1-207">Locate the `public class` statement.</span></span> <span data-ttu-id="f2db1-208">Denetiminiz devralınan Not `ctlClockLib.ctlClock`.</span><span class="sxs-lookup"><span data-stu-id="f2db1-208">Note that your control inherits from `ctlClockLib.ctlClock`.</span></span> <span data-ttu-id="f2db1-209">Açılış ayracından altında (`{)` deyimi, aşağıdaki kodu yazın.</span><span class="sxs-lookup"><span data-stu-id="f2db1-209">Beneath the opening brace (`{)` statement, type the following code.</span></span>  
  
    ```csharp  
    private DateTime dteAlarmTime;  
    private bool blnAlarmSet;  
    // These properties will be declared as public to allow future   
    // developers to access them.  
    public DateTime AlarmTime  
    {  
        get  
        {  
            return dteAlarmTime;  
        }  
        set  
        {  
            dteAlarmTime = value;  
        }  
    }  
    public bool AlarmSet  
    {  
        get  
        {  
            return blnAlarmSet;  
        }  
        set  
        {  
            blnAlarmSet = value;  
        }  
    }  
    ```  
  
### <a name="adding-to-the-graphical-interface-of-the-control"></a><span data-ttu-id="f2db1-210">Grafik arabirimine denetimi ekleme</span><span class="sxs-lookup"><span data-stu-id="f2db1-210">Adding to the Graphical Interface of the Control</span></span>  
 <span data-ttu-id="f2db1-211">Devralınan denetim devraldığı denetlemek için aynı olan görsel bir arabirim sahiptir.</span><span class="sxs-lookup"><span data-stu-id="f2db1-211">Your inherited control has a visual interface that is identical to the control it inherits from.</span></span> <span data-ttu-id="f2db1-212">Aynı bağlı denetimler, üst denetim olarak sahiptir, ancak özel olarak sunulan sürece bağlı denetimlerin özelliklerini kullanılabilir olmayacak.</span><span class="sxs-lookup"><span data-stu-id="f2db1-212">It possesses the same constituent controls as its parent control, but the properties of the constituent controls will not be available unless they were specifically exposed.</span></span> <span data-ttu-id="f2db1-213">Herhangi bir bileşik denetimi olduğu gibi aynı şekilde devralınan bir bileşik denetim grafik arabirimine ekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="f2db1-213">You may add to the graphical interface of an inherited composite control in the same manner as you would add to any composite control.</span></span> <span data-ttu-id="f2db1-214">Uyarı Saatin görsel arabirim olarak eklemeye devam etmek için alarm uyarabilir yükleyen yanar etiket denetimi ekleyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="f2db1-214">To continue adding to your alarm clock's visual interface, you will add a label control that will flash when the alarm is sounding.</span></span>  
  
##### <a name="to-add-the-label-control"></a><span data-ttu-id="f2db1-215">Etiket denetimi eklemek için</span><span class="sxs-lookup"><span data-stu-id="f2db1-215">To add the label control</span></span>  
  
1.  <span data-ttu-id="f2db1-216">Çözüm Gezgini'nde sağ **ctlAlarmClock**ve ardından **Görünüm Tasarımcısı**.</span><span class="sxs-lookup"><span data-stu-id="f2db1-216">In Solution Explorer, right-click **ctlAlarmClock**, and then click **View Designer**.</span></span>  
  
     <span data-ttu-id="f2db1-217">Tasarımcı için `ctlAlarmClock` ana penceresinde açılır.</span><span class="sxs-lookup"><span data-stu-id="f2db1-217">The designer for `ctlAlarmClock` opens in the main window.</span></span>  
  
2.  <span data-ttu-id="f2db1-218">Denetimin görüntüleme kısmına tıklayın ve Özellikler penceresini görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="f2db1-218">Click the display portion of the control, and view the Properties window.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f2db1-219">Tüm özellikler görüntülenir, ancak bunlar soluklaştırılır.</span><span class="sxs-lookup"><span data-stu-id="f2db1-219">While all the properties are displayed, they are dimmed.</span></span> <span data-ttu-id="f2db1-220">Bu, bu özellikleri için yerel gösterir `lblDisplay` ve değiştirilemez veya Özellikler penceresinde erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="f2db1-220">This indicates that these properties are native to `lblDisplay` and cannot be modified or accessed in the Properties window.</span></span> <span data-ttu-id="f2db1-221">Varsayılan olarak, bu bileşik denetiminde bulunan denetimlerdir `private`, ve bunların özelliklerini herhangi bir yolla erişilebilir değildir.</span><span class="sxs-lookup"><span data-stu-id="f2db1-221">By default, controls contained in a composite control are `private`, and their properties are not accessible by any means.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f2db1-222">Bileşik denetiminizin sonraki kullanıcıların kendi iç denetimleri erişmesini isterseniz, bunları olarak bildirin `public` veya `protected`.</span><span class="sxs-lookup"><span data-stu-id="f2db1-222">If you want subsequent users of your composite control to have access to its internal controls, declare them as `public` or `protected`.</span></span> <span data-ttu-id="f2db1-223">Bu, ayarlamak ve uygun kodu kullanarak bileşik denetiminizin içinde yer alan denetimlerin özelliklerini değiştirmek olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="f2db1-223">This will allow you to set and modify properties of controls contained within your composite control by using the appropriate code.</span></span>  
  
3.  <span data-ttu-id="f2db1-224">Ekleme bir <xref:System.Windows.Forms.Label> denetimi için bileşik denetim.</span><span class="sxs-lookup"><span data-stu-id="f2db1-224">Add a <xref:System.Windows.Forms.Label> control to your composite control.</span></span>  
  
4.  <span data-ttu-id="f2db1-225">Fareyle sürükleyin <xref:System.Windows.Forms.Label> görüntüleme kutusunun hemen altındaki denetimi.</span><span class="sxs-lookup"><span data-stu-id="f2db1-225">Using the mouse, drag the <xref:System.Windows.Forms.Label> control immediately beneath the display box.</span></span> <span data-ttu-id="f2db1-226">Özellikler penceresinde, aşağıdaki özellikleri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="f2db1-226">In the Properties window, set the following properties.</span></span>  
  
    |<span data-ttu-id="f2db1-227">Özellik</span><span class="sxs-lookup"><span data-stu-id="f2db1-227">Property</span></span>|<span data-ttu-id="f2db1-228">Ayar</span><span class="sxs-lookup"><span data-stu-id="f2db1-228">Setting</span></span>|  
    |--------------|-------------|  
    |<span data-ttu-id="f2db1-229">**Ad**</span><span class="sxs-lookup"><span data-stu-id="f2db1-229">**Name**</span></span>|`lblAlarm`|  
    |<span data-ttu-id="f2db1-230">**Metin**</span><span class="sxs-lookup"><span data-stu-id="f2db1-230">**Text**</span></span>|<span data-ttu-id="f2db1-231">**Uyarı!**</span><span class="sxs-lookup"><span data-stu-id="f2db1-231">**Alarm!**</span></span>|  
    |<span data-ttu-id="f2db1-232">**TextAlign**</span><span class="sxs-lookup"><span data-stu-id="f2db1-232">**TextAlign**</span></span>|`MiddleCenter`|  
    |<span data-ttu-id="f2db1-233">**Görünür**</span><span class="sxs-lookup"><span data-stu-id="f2db1-233">**Visible**</span></span>|`false`|  
  
### <a name="adding-the-alarm-functionality"></a><span data-ttu-id="f2db1-234">Uyarı işlevsellik ekleme</span><span class="sxs-lookup"><span data-stu-id="f2db1-234">Adding the Alarm Functionality</span></span>  
 <span data-ttu-id="f2db1-235">Önceki yordamlarda, özellikleri ve bileşik denetim uyarısı işlevselliği sağlayan bir denetimi eklendi.</span><span class="sxs-lookup"><span data-stu-id="f2db1-235">In the previous procedures, you added properties and a control that will enable alarm functionality in your composite control.</span></span> <span data-ttu-id="f2db1-236">Bu yordamda, alarm saati geçerli saate karşılaştırmak için kod ekleyeceksiniz ve aynı alarm Flash olmaları durumunda.</span><span class="sxs-lookup"><span data-stu-id="f2db1-236">In this procedure, you will add code to compare the current time to the alarm time and, if they are the same, to flash an alarm.</span></span> <span data-ttu-id="f2db1-237">Geçersiz kılma tarafından `timer1_Tick` yöntemi `ctlClock` ve ek kod ekleme, yeteneğini genişletecek `ctlAlarmClock` tüm devralınan işlevselliğini korurken `ctlClock`.</span><span class="sxs-lookup"><span data-stu-id="f2db1-237">By overriding the `timer1_Tick` method of `ctlClock` and adding additional code to it, you will extend the capability of `ctlAlarmClock` while retaining all of the inherent functionality of `ctlClock`.</span></span>  
  
##### <a name="to-override-the-timer1tick-method-of-ctlclock"></a><span data-ttu-id="f2db1-238">CtlClock timer1_Tick yöntemi geçersiz kılmak için</span><span class="sxs-lookup"><span data-stu-id="f2db1-238">To override the timer1_Tick method of ctlClock</span></span>  
  
1.  <span data-ttu-id="f2db1-239">İçinde **Kod Düzenleyicisi**, bulun `private bool blnAlarmSet;` deyimi.</span><span class="sxs-lookup"><span data-stu-id="f2db1-239">In the **Code Editor**, locate the `private bool blnAlarmSet;` statement.</span></span> <span data-ttu-id="f2db1-240">Hemen altında aşağıdaki deyimi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f2db1-240">Immediately beneath it, add the following statement.</span></span>  
  
    ```csharp  
    private bool blnColorTicker;  
    ```  
  
2.  <span data-ttu-id="f2db1-241">İçinde **Kod Düzenleyicisi**, kapatma küme ayracından bulun (`})` sınıfı sonunda.</span><span class="sxs-lookup"><span data-stu-id="f2db1-241">In the **Code Editor**, locate the closing brace (`})` at the end of the class.</span></span> <span data-ttu-id="f2db1-242">Küme ayracı hemen önce aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f2db1-242">Just before the brace, add the following code.</span></span>  
  
    ```csharp  
    protected override void timer1_Tick(object sender, System.EventArgs e)  
    {  
        // Calls the Timer1_Tick method of ctlClock.  
        base.timer1_Tick(sender, e);  
        // Checks to see if the alarm is set.  
        if (AlarmSet == false)  
            return;  
        else  
            // If the date, hour, and minute of the alarm time are the same as  
            // the current time, flash an alarm.   
        {  
            if (AlarmTime.Date == DateTime.Now.Date && AlarmTime.Hour ==   
                DateTime.Now.Hour && AlarmTime.Minute == DateTime.Now.Minute)  
            {  
                // Sets lblAlarmVisible to true, and changes the background color based on  
                // the value of blnColorTicker. The background color of the label   
                // will flash once per tick of the clock.  
                lblAlarm.Visible = true;  
                if (blnColorTicker == false)   
                {  
                    lblAlarm.BackColor = Color.Red;  
                    blnColorTicker = true;  
                }  
                else  
                {  
                    lblAlarm.BackColor = Color.Blue;  
                    blnColorTicker = false;  
                }  
            }  
            else  
            {  
                // Once the alarm has sounded for a minute, the label is made   
                // invisible again.  
                lblAlarm.Visible = false;  
            }  
        }  
    }  
    ```  
  
     <span data-ttu-id="f2db1-243">Bu kodu eklenmesi birkaç görev gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="f2db1-243">The addition of this code accomplishes several tasks.</span></span> <span data-ttu-id="f2db1-244">`override` Deyimi temel denetiminden devralındı yöntemi yerine bu yöntemi kullanmak için denetimi yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="f2db1-244">The `override` statement directs the control to use this method in place of the method that was inherited from the base control.</span></span> <span data-ttu-id="f2db1-245">Bu yöntem çağrıldığında, onu geçersiz kılar çağırarak yöntemini çağırır `base.timer1_Tick` deyimi, tüm işlevlerin özgün denetiminde dahil sağlayarak bu denetimde çoğaltılamaz.</span><span class="sxs-lookup"><span data-stu-id="f2db1-245">When this method is called, it calls the method it overrides by invoking the `base.timer1_Tick` statement, ensuring that all of the functionality incorporated in the original control is reproduced in this control.</span></span> <span data-ttu-id="f2db1-246">Ardından, uyarı işlevselliği eklemek için ek kod çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="f2db1-246">It then runs additional code to incorporate the alarm functionality.</span></span> <span data-ttu-id="f2db1-247">Uyarı oluştuğunda, yanıp sönen bir etiket denetimi görünür.</span><span class="sxs-lookup"><span data-stu-id="f2db1-247">A flashing label control will appear when the alarm occurs.</span></span>  
  
     <span data-ttu-id="f2db1-248">Uyarı saat denetiminiz hemen tamamlanır.</span><span class="sxs-lookup"><span data-stu-id="f2db1-248">Your alarm clock control is almost complete.</span></span> <span data-ttu-id="f2db1-249">Kalan tek şey, devre dışı bırakmak için bir yol uygulamaktır.</span><span class="sxs-lookup"><span data-stu-id="f2db1-249">The only thing that remains is to implement a way to turn it off.</span></span> <span data-ttu-id="f2db1-250">Bunu yapmak için kod ekleyeceksiniz `lblAlarm_Click` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f2db1-250">To do this, you will add code to the `lblAlarm_Click` method.</span></span>  
  
##### <a name="to-implement-the-shutoff-method"></a><span data-ttu-id="f2db1-251">Kesici yöntemi uygulamak için</span><span class="sxs-lookup"><span data-stu-id="f2db1-251">To implement the shutoff method</span></span>  
  
1.  <span data-ttu-id="f2db1-252">Çözüm Gezgini'nde sağ **ctlAlarmClock.cs**ve ardından **Görünüm Tasarımcısı**.</span><span class="sxs-lookup"><span data-stu-id="f2db1-252">In Solution Explorer, right-click **ctlAlarmClock.cs**, and then click **View Designer**.</span></span>  
  
     <span data-ttu-id="f2db1-253">Tasarımcısı açılır.</span><span class="sxs-lookup"><span data-stu-id="f2db1-253">The designer opens.</span></span>  
  
2.  <span data-ttu-id="f2db1-254">Bir düğme denetimi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f2db1-254">Add a button to the control.</span></span> <span data-ttu-id="f2db1-255">Düğmenin özelliklerini şu şekilde ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="f2db1-255">Set the properties of the button as follows.</span></span>  
  
    |<span data-ttu-id="f2db1-256">Özellik</span><span class="sxs-lookup"><span data-stu-id="f2db1-256">Property</span></span>|<span data-ttu-id="f2db1-257">Değer</span><span class="sxs-lookup"><span data-stu-id="f2db1-257">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="f2db1-258">**Ad**</span><span class="sxs-lookup"><span data-stu-id="f2db1-258">**Name**</span></span>|`btnAlarmOff`|  
    |<span data-ttu-id="f2db1-259">**Metin**</span><span class="sxs-lookup"><span data-stu-id="f2db1-259">**Text**</span></span>|<span data-ttu-id="f2db1-260">**Uyarı devre dışı bırak**</span><span class="sxs-lookup"><span data-stu-id="f2db1-260">**Disable Alarm**</span></span>|  
  
3.  <span data-ttu-id="f2db1-261">Tasarımcıda çift **btnAlarmOff**.</span><span class="sxs-lookup"><span data-stu-id="f2db1-261">In the designer, double-click **btnAlarmOff**.</span></span>  
  
     <span data-ttu-id="f2db1-262">**Kod Düzenleyicisi** açılır `private void btnAlarmOff_Click` satır.</span><span class="sxs-lookup"><span data-stu-id="f2db1-262">The **Code Editor** opens to the `private void btnAlarmOff_Click` line.</span></span>  
  
4.  <span data-ttu-id="f2db1-263">Bu yöntem, aşağıdaki koda benzer şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="f2db1-263">Modify this method so that it resembles the following code.</span></span>  
  
    ```csharp  
    private void btnAlarmOff_Click(object sender, System.EventArgs e)  
    {  
        // Turns off the alarm.  
        AlarmSet = false;  
        // Hides the flashing label.  
        lblAlarm.Visible = false;  
    }  
    ```  
  
5.  <span data-ttu-id="f2db1-264">Üzerinde **dosya** menüsünü tıklatın **Tümünü Kaydet** projeyi kaydetmek için.</span><span class="sxs-lookup"><span data-stu-id="f2db1-264">On the **File** menu, click **Save All** to save the project.</span></span>  
  
### <a name="using-the-inherited-control-on-a-form"></a><span data-ttu-id="f2db1-265">Devralınan Form denetimi kullanma</span><span class="sxs-lookup"><span data-stu-id="f2db1-265">Using the Inherited Control on a Form</span></span>  
 <span data-ttu-id="f2db1-266">Devralınan denetim temel sınıf denetim test aynı şekilde test edebilirsiniz `ctlClock`: F5 tuşuna basarak projeyi oluşturun ve denetim Çalıştır **UserControl Test kapsayıcısı**.</span><span class="sxs-lookup"><span data-stu-id="f2db1-266">You can test your inherited control the same way you tested the base class control, `ctlClock`: Press F5 to build the project and run your control in the **UserControl Test Container**.</span></span> <span data-ttu-id="f2db1-267">Daha fazla bilgi için [nasıl yapılır: bir UserControl denetiminin çalışma zamanı davranışını sınama](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span><span class="sxs-lookup"><span data-stu-id="f2db1-267">For more information, see [How to: Test the Run-Time Behavior of a UserControl](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>  
  
 <span data-ttu-id="f2db1-268">Denetiminizi kullanmak için koymak için bir form üzerinde barındırmak gerekir.</span><span class="sxs-lookup"><span data-stu-id="f2db1-268">To put your control to use, you will need to host it on a form.</span></span> <span data-ttu-id="f2db1-269">Devralınan bir bileşik denetim standart bileşik denetim gibi tek başına duramaz ve bir form veya diğer kapsayıcı içinde barındırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f2db1-269">As with a standard composite control, an inherited composite control cannot stand alone and must be hosted in a form or other container.</span></span> <span data-ttu-id="f2db1-270">Bu yana `ctlAlarmClock` daha derinlemesine sahip, işlevselliğini test etmek için ek kod gereklidir.</span><span class="sxs-lookup"><span data-stu-id="f2db1-270">Since `ctlAlarmClock` has a greater depth of functionality, additional code is required to test it.</span></span> <span data-ttu-id="f2db1-271">Bu yordamda işlevselliğini test etmek için basit bir program yazacak `ctlAlarmClock`.</span><span class="sxs-lookup"><span data-stu-id="f2db1-271">In this procedure, you will write a simple program to test the functionality of `ctlAlarmClock`.</span></span> <span data-ttu-id="f2db1-272">Ayarlayın ve görüntülemek için kod yazacaksınız `AlarmTime` özelliği `ctlAlarmClock`ve iç işlevleri test eder.</span><span class="sxs-lookup"><span data-stu-id="f2db1-272">You will write code to set and display the `AlarmTime` property of `ctlAlarmClock`, and will test its inherent functions.</span></span>  
  
##### <a name="to-build-and-add-your-control-to-a-test-form"></a><span data-ttu-id="f2db1-273">Derleme ve test forma denetim ekleme</span><span class="sxs-lookup"><span data-stu-id="f2db1-273">To build and add your control to a test form</span></span>  
  
1.  <span data-ttu-id="f2db1-274">Çözüm Gezgini'nde sağ **ctlClockLib**ve ardından **yapı**.</span><span class="sxs-lookup"><span data-stu-id="f2db1-274">In Solution Explorer, right-click **ctlClockLib**, and then click **Build**.</span></span>  
  
2.  <span data-ttu-id="f2db1-275">Yeni bir **Windows uygulama** çözüme proje ve adlandırın `Test`.</span><span class="sxs-lookup"><span data-stu-id="f2db1-275">Add a new **Windows Application** project to the solution, and name it `Test`.</span></span>  
  
3.  <span data-ttu-id="f2db1-276">Çözüm Gezgini'nde sağ **başvuruları** test projeniz için düğüm.</span><span class="sxs-lookup"><span data-stu-id="f2db1-276">In Solution Explorer, right-click the **References** node for your test project.</span></span> <span data-ttu-id="f2db1-277">Tıklayın **Başvuru Ekle** görüntülenecek **Başvuru Ekle** iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="f2db1-277">Click **Add Reference** to display the **Add Reference** dialog box.</span></span> <span data-ttu-id="f2db1-278">Etiketli sekmesini **projeleri**.</span><span class="sxs-lookup"><span data-stu-id="f2db1-278">Click the tab labeled **Projects**.</span></span> <span data-ttu-id="f2db1-279">`ctlClockLib` Projesi altında listelenir **proje adı**.</span><span class="sxs-lookup"><span data-stu-id="f2db1-279">Your `ctlClockLib` project will be listed under **Project Name**.</span></span> <span data-ttu-id="f2db1-280">Projeyi test projesinin başvuru eklemek için çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="f2db1-280">Double-click the project to add the reference to the test project.</span></span>  
  
4.  <span data-ttu-id="f2db1-281">Çözüm Gezgini'nde sağ **Test**ve ardından **yapı**.</span><span class="sxs-lookup"><span data-stu-id="f2db1-281">In Solution Explorer, right-click **Test**, and then click **Build**.</span></span>  
  
5.  <span data-ttu-id="f2db1-282">İçinde **araç kutusu**, genişletme **ctlClockLib bileşenleri** düğümü.</span><span class="sxs-lookup"><span data-stu-id="f2db1-282">In the **Toolbox**, expand the **ctlClockLib Components** node.</span></span>  
  
6.  <span data-ttu-id="f2db1-283">Çift **ctlAlarmClock** bir kopyasını eklemek için `ctlAlarmClock` formunuza.</span><span class="sxs-lookup"><span data-stu-id="f2db1-283">Double-click **ctlAlarmClock** to add a copy of `ctlAlarmClock` to your form.</span></span>  
  
7.  <span data-ttu-id="f2db1-284">İçinde **araç kutusu**, bulun ve çift **DateTimePicker** eklemek için bir <xref:System.Windows.Forms.DateTimePicker> Formunuza denetim ve ardından eklemek bir <xref:System.Windows.Forms.Label> denetimi çift tıklayarak **etiketi**.</span><span class="sxs-lookup"><span data-stu-id="f2db1-284">In the **Toolbox**, locate and double-click **DateTimePicker** to add a <xref:System.Windows.Forms.DateTimePicker> control to your form, and then add a <xref:System.Windows.Forms.Label> control by double-clicking **Label**.</span></span>  
  
8.  <span data-ttu-id="f2db1-285">Fare bir kullanışlı yerde form üzerinde denetimleri konumlandırmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="f2db1-285">Use the mouse to position the controls in a convenient place on the form.</span></span>  
  
9. <span data-ttu-id="f2db1-286">Bu denetimin özelliklerini şu şekilde ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="f2db1-286">Set the properties of these controls in the following manner.</span></span>  
  
    |<span data-ttu-id="f2db1-287">Denetim</span><span class="sxs-lookup"><span data-stu-id="f2db1-287">Control</span></span>|<span data-ttu-id="f2db1-288">Özellik</span><span class="sxs-lookup"><span data-stu-id="f2db1-288">Property</span></span>|<span data-ttu-id="f2db1-289">Değer</span><span class="sxs-lookup"><span data-stu-id="f2db1-289">Value</span></span>|  
    |-------------|--------------|-----------|  
    |`label1`|<span data-ttu-id="f2db1-290">**Metin**</span><span class="sxs-lookup"><span data-stu-id="f2db1-290">**Text**</span></span>|`(blank space)`|  
    ||<span data-ttu-id="f2db1-291">**Ad**</span><span class="sxs-lookup"><span data-stu-id="f2db1-291">**Name**</span></span>|`lblTest`|  
    |`dateTimePicker1`|<span data-ttu-id="f2db1-292">**Ad**</span><span class="sxs-lookup"><span data-stu-id="f2db1-292">**Name**</span></span>|`dtpTest`|  
    ||<span data-ttu-id="f2db1-293">**Biçim**</span><span class="sxs-lookup"><span data-stu-id="f2db1-293">**Format**</span></span>|<xref:System.Windows.Forms.DateTimePickerFormat.Time>|  
  
10. <span data-ttu-id="f2db1-294">Tasarımcıda çift **dtpTest**.</span><span class="sxs-lookup"><span data-stu-id="f2db1-294">In the designer, double-click **dtpTest**.</span></span>  
  
     <span data-ttu-id="f2db1-295">**Kod Düzenleyicisi** açılır `private void dtpTest_ValueChanged`.</span><span class="sxs-lookup"><span data-stu-id="f2db1-295">The **Code Editor** opens to `private void dtpTest_ValueChanged`.</span></span>  
  
11. <span data-ttu-id="f2db1-296">Kodu aşağıdakine benzer şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="f2db1-296">Modify the code so that it resembles the following.</span></span>  
  
    ```csharp  
    private void dtpTest_ValueChanged(object sender, System.EventArgs e)  
    {  
        ctlAlarmClock1.AlarmTime = dtpTest.Value;  
        ctlAlarmClock1.AlarmSet = true;  
        lblTest.Text = "Alarm Time is " +  
            ctlAlarmClock1.AlarmTime.ToShortTimeString();  
    }  
    ```  
  
12. <span data-ttu-id="f2db1-297">Çözüm Gezgini'nde sağ **Test**ve ardından **başlangıç projesi olarak ayarla**.</span><span class="sxs-lookup"><span data-stu-id="f2db1-297">In Solution Explorer, right-click **Test**, and then click **Set as StartUp Project**.</span></span>  
  
13. <span data-ttu-id="f2db1-298">Üzerinde **hata ayıklama** menüsünü tıklatın **hata ayıklamayı Başlat**.</span><span class="sxs-lookup"><span data-stu-id="f2db1-298">On the **Debug** menu, click **Start Debugging**.</span></span>  
  
     <span data-ttu-id="f2db1-299">Test program başlar.</span><span class="sxs-lookup"><span data-stu-id="f2db1-299">The test program starts.</span></span> <span data-ttu-id="f2db1-300">Geçerli saat içinde güncelleştirilir Not `ctlAlarmClock` denetimi ve başlangıç saatini gösterildiği <xref:System.Windows.Forms.DateTimePicker> denetimi.</span><span class="sxs-lookup"><span data-stu-id="f2db1-300">Note that the current time is updated in the `ctlAlarmClock` control, and that the starting time is shown in the <xref:System.Windows.Forms.DateTimePicker> control.</span></span>  
  
14. <span data-ttu-id="f2db1-301">Tıklayın <xref:System.Windows.Forms.DateTimePicker> saat, dakika burada görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="f2db1-301">Click the <xref:System.Windows.Forms.DateTimePicker> where the minutes of the hour are displayed.</span></span>  
  
15. <span data-ttu-id="f2db1-302">Klavyeyi kullanarak, bir dakika tarafından gösterilen geçerli saatten büyük bir değer dakika ayarlamak `ctlAlarmClock`.</span><span class="sxs-lookup"><span data-stu-id="f2db1-302">Using the keyboard, set a value for minutes that is one minute greater than the current time shown by `ctlAlarmClock`.</span></span>  
  
     <span data-ttu-id="f2db1-303">Uyarı ayar için zaman gösterilen `lblTest`.</span><span class="sxs-lookup"><span data-stu-id="f2db1-303">The time for the alarm setting is shown in `lblTest`.</span></span> <span data-ttu-id="f2db1-304">Uyarı ayarını zaman ulaşmak görüntülenen saat için bekleyin.</span><span class="sxs-lookup"><span data-stu-id="f2db1-304">Wait for the displayed time to reach the alarm setting time.</span></span> <span data-ttu-id="f2db1-305">Görüntülenen saat için uyarı ayarlanır, bir zaman geldiğinde `lblAlarm` flash.</span><span class="sxs-lookup"><span data-stu-id="f2db1-305">When the displayed time reaches the time to which the alarm is set, the `lblAlarm` will flash.</span></span>  
  
16. <span data-ttu-id="f2db1-306">Alarmın tıklatarak açın `btnAlarmOff`.</span><span class="sxs-lookup"><span data-stu-id="f2db1-306">Turn off the alarm by clicking `btnAlarmOff`.</span></span> <span data-ttu-id="f2db1-307">Uyarı artık sıfırlayabilir.</span><span class="sxs-lookup"><span data-stu-id="f2db1-307">You may now reset the alarm.</span></span>  
  
     <span data-ttu-id="f2db1-308">Bu izlenecek yol, bir dizi temel kavramları kapsamında.</span><span class="sxs-lookup"><span data-stu-id="f2db1-308">This walkthrough has covered a number of key concepts.</span></span> <span data-ttu-id="f2db1-309">Bileşik Denetim kapsayıcıya denetimleri ve Bileşenleri'ni birleştirerek bileşik denetim oluşturulacağını öğrendiniz.</span><span class="sxs-lookup"><span data-stu-id="f2db1-309">You have learned to create a composite control by combining controls and components into a composite control container.</span></span> <span data-ttu-id="f2db1-310">Özellikleri denetiminize eklemek ve özel işlevselliği uygulamak üzere kod yazmak için öğrendiniz.</span><span class="sxs-lookup"><span data-stu-id="f2db1-310">You have learned to add properties to your control, and to write code to implement custom functionality.</span></span> <span data-ttu-id="f2db1-311">Son bölümde, devralma yoluyla belirli bir bileşik denetim işlevlerini genişletmek ve bu yöntemi geçersiz kılarak konak yöntemleri işlevlerini değiştirmek için öğrendiniz.</span><span class="sxs-lookup"><span data-stu-id="f2db1-311">In the last section, you learned to extend the functionality of a given composite control through inheritance, and to alter the functionality of host methods by overriding those methods.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2db1-312">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f2db1-312">See Also</span></span>  
 [<span data-ttu-id="f2db1-313">Özel Denetim Çeşitleri</span><span class="sxs-lookup"><span data-stu-id="f2db1-313">Varieties of Custom Controls</span></span>](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)  
 [<span data-ttu-id="f2db1-314">Bileşenler ile programlama</span><span class="sxs-lookup"><span data-stu-id="f2db1-314">Programming with Components</span></span>](https://msdn.microsoft.com/library/d4d4fcb4-e0b8-46b3-b679-7ee0026eb9e3)  
 [<span data-ttu-id="f2db1-315">Bileşen yazma izlenecek yolları</span><span class="sxs-lookup"><span data-stu-id="f2db1-315">Component Authoring Walkthroughs</span></span>](https://msdn.microsoft.com/library/c414cca9-2489-4208-8b38-954586d91c13)  
 [<span data-ttu-id="f2db1-316">Nasıl yapılır: Araç Kutusu Öğelerini Seç İletişim Kutusunda bir Denetimi Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="f2db1-316">How to: Display a Control in the Choose Toolbox Items Dialog Box</span></span>](../../../../docs/framework/winforms/controls/how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)  
 [<span data-ttu-id="f2db1-317">İzlenecek yol: Visual C# ile beraber Windows Forms Denetimi'nden Devralma</span><span class="sxs-lookup"><span data-stu-id="f2db1-317">Walkthrough: Inheriting from a Windows Forms Control with Visual C#</span></span>](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)
