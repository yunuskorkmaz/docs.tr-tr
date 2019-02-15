---
title: 'İzlenecek yol: Visual Basic ile bileşik denetim yazma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [Visual Basic]
- user controls [Visual Basic]
- UserControl class [Windows Forms], walkthroughs
- user controls [Windows Forms], creating with Visual Basic
- controls [Windows Forms], composite controls
- composite controls [Windows Forms], creating
- custom controls [Windows Forms], creating
ms.assetid: f50e270e-4db2-409a-8319-6db6ca5c7daf
ms.openlocfilehash: ddc18c571d65d95b8ffc84f9b7d84213e527689b
ms.sourcegitcommit: bef803e2025642df39f2f1e046767d89031e0304
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/15/2019
ms.locfileid: "56305824"
---
# <a name="walkthrough-authoring-a-composite-control-with-visual-basic"></a><span data-ttu-id="43fcc-102">İzlenecek yol: Visual Basic ile bileşik denetim yazma</span><span class="sxs-lookup"><span data-stu-id="43fcc-102">Walkthrough: Authoring a Composite Control with Visual Basic</span></span>
<span data-ttu-id="43fcc-103">Bileşik denetimler, özel bir grafik arabirim oluşturulabilir yeniden ve bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="43fcc-103">Composite controls provide a means by which custom graphical interfaces can be created and reused.</span></span> <span data-ttu-id="43fcc-104">Bileşik Denetim aslında bir görsel bir temsili ile bileşenidir.</span><span class="sxs-lookup"><span data-stu-id="43fcc-104">A composite control is essentially a component with a visual representation.</span></span> <span data-ttu-id="43fcc-105">Bu nedenle, bir veya daha fazla Windows Forms denetimleri, bileşenleri veya kullanıcı girişini doğrulama, görüntü özelliklerini değiştirerek veya yazar tarafından gereken diğer görevleri gerçekleştirme işlevselliğini genişletebildiği kod bloklarını oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="43fcc-105">As such, it might consist of one or more Windows Forms controls, components, or blocks of code that can extend functionality by validating user input, modifying display properties, or performing other tasks required by the author.</span></span> <span data-ttu-id="43fcc-106">Bileşik denetimler, diğer denetimlerle aynı şekilde Windows formlarında yerleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="43fcc-106">Composite controls can be placed on Windows Forms in the same manner as other controls.</span></span> <span data-ttu-id="43fcc-107">Bu kılavuzun ilk bölümünde oluşturduğunuz adlı basit bir bileşik denetim `ctlClock`.</span><span class="sxs-lookup"><span data-stu-id="43fcc-107">In the first part of this walkthrough, you create a simple composite control called `ctlClock`.</span></span> <span data-ttu-id="43fcc-108">İzlenecek yol ikinci kısmında, işlevlerini genişletmek `ctlClock` devralma yoluyla.</span><span class="sxs-lookup"><span data-stu-id="43fcc-108">In the second part of the walkthrough, you extend the functionality of `ctlClock` through inheritance.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="43fcc-109">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="43fcc-109">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="43fcc-110">Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="43fcc-110">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="43fcc-111">Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="43fcc-111">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="43fcc-112">Projeyi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="43fcc-112">Creating the Project</span></span>  
 <span data-ttu-id="43fcc-113">Yeni bir proje oluşturduğunuzda, kök ad alanı, derleme adı ve proje adını ayarlayın ve varsayılan bileşeni doğru ad alanı içinde olmasını sağlamak için adını belirtin.</span><span class="sxs-lookup"><span data-stu-id="43fcc-113">When you create a new project, you specify its name to set the root namespace, assembly name, and project name, and ensure that the default component will be in the correct namespace.</span></span>  
  
#### <a name="to-create-the-ctlclocklib-control-library-and-the-ctlclock-control"></a><span data-ttu-id="43fcc-114">CtlClockLib denetim kitaplığı ve ctlClock denetimi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="43fcc-114">To create the ctlClockLib control library and the ctlClock control</span></span>  
  
1.  <span data-ttu-id="43fcc-115">Üzerinde **dosya** menüsünde **yeni**ve ardından **proje** açmak için **yeni proje** iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="43fcc-115">On the **File** menu, point to **New**, and then click **Project** to open the **New Project** dialog box.</span></span>  
  
2.  <span data-ttu-id="43fcc-116">Visual Basic projelerinin listesinden **Windows Denetim Kitaplığı** proje şablonu, türü `ctlClockLib` içinde **adı** kutusuna ve ardından **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="43fcc-116">From the list of Visual Basic projects, select the **Windows Control Library** project template, type `ctlClockLib` in the **Name** box, and then click **OK**.</span></span>  
  
     <span data-ttu-id="43fcc-117">Proje adı `ctlClockLib`, aynı zamanda kök ad alanı için varsayılan olarak atanır.</span><span class="sxs-lookup"><span data-stu-id="43fcc-117">The project name, `ctlClockLib`, is also assigned to the root namespace by default.</span></span> <span data-ttu-id="43fcc-118">Kök ad alanı, bileşenleri derleme içindeki adlarını nitelemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="43fcc-118">The root namespace is used to qualify the names of components in the assembly.</span></span> <span data-ttu-id="43fcc-119">Örneğin, iki derleme adlı bileşenleri sağlarsanız `ctlClock`, belirtebilirsiniz, `ctlClock` bileşenini kullanma `ctlClockLib.ctlClock.`</span><span class="sxs-lookup"><span data-stu-id="43fcc-119">For example, if two assemblies provide components named `ctlClock`, you can specify your `ctlClock` component using `ctlClockLib.ctlClock.`</span></span>  
  
3.  <span data-ttu-id="43fcc-120">Çözüm Gezgini'nde sağ **UserControl1.vb**ve ardından **Yeniden Adlandır**.</span><span class="sxs-lookup"><span data-stu-id="43fcc-120">In Solution Explorer, right-click **UserControl1.vb**, and then click **Rename**.</span></span> <span data-ttu-id="43fcc-121">İçin dosya adını değiştirerek `ctlClock.vb`.</span><span class="sxs-lookup"><span data-stu-id="43fcc-121">Change the file name to `ctlClock.vb`.</span></span> <span data-ttu-id="43fcc-122">Tıklayın **Evet** yaptığınız kod öğesi "UserControl1" için tüm başvuruları yeniden adlandırmak isteyip istemediğiniz sorulduğunda düğmesi.</span><span class="sxs-lookup"><span data-stu-id="43fcc-122">Click the **Yes** button when you are asked if you want to rename all references to the code element "UserControl1".</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="43fcc-123">Bileşik denetim varsayılan olarak, devralınan <xref:System.Windows.Forms.UserControl> sistem tarafından sağlanan sınıfı.</span><span class="sxs-lookup"><span data-stu-id="43fcc-123">By default, a composite control inherits from the <xref:System.Windows.Forms.UserControl> class provided by the system.</span></span> <span data-ttu-id="43fcc-124"><xref:System.Windows.Forms.UserControl> Sınıfı tüm bileşik denetimler tarafından gerekli işlevselliği sunar ve standart yöntemleri ve özellikleri uygular.</span><span class="sxs-lookup"><span data-stu-id="43fcc-124">The <xref:System.Windows.Forms.UserControl> class provides functionality required by all composite controls, and implements standard methods and properties.</span></span>  
  
4.  <span data-ttu-id="43fcc-125">Üzerinde **dosya** menüsünü tıklatın **Tümünü Kaydet** projeyi kaydetmek için.</span><span class="sxs-lookup"><span data-stu-id="43fcc-125">On the **File** menu, click **Save All** to save the project.</span></span>  
  
## <a name="adding-windows-controls-and-components-to-the-composite-control"></a><span data-ttu-id="43fcc-126">Windows ekleme denetimleri ve bileşenleri bileşik denetim</span><span class="sxs-lookup"><span data-stu-id="43fcc-126">Adding Windows Controls and Components to the Composite Control</span></span>  
 <span data-ttu-id="43fcc-127">Görsel bir arabirim, bileşik denetim önemli bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="43fcc-127">A visual interface is an essential part of your composite control.</span></span> <span data-ttu-id="43fcc-128">Bu görsel arabirim Tasarımcı yüzeyine bir veya daha fazla Windows denetimleri eklenmesini tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="43fcc-128">This visual interface is implemented by the addition of one or more Windows controls to the designer surface.</span></span> <span data-ttu-id="43fcc-129">Aşağıdaki örnekte, Windows denetimleri, bileşik denetime eklemek ve işlevselliği uygulamak için kod yazın.</span><span class="sxs-lookup"><span data-stu-id="43fcc-129">In the following demonstration, you will incorporate Windows controls into your composite control and write code to implement functionality.</span></span>  
  
#### <a name="to-add-a-label-and-a-timer-to-your-composite-control"></a><span data-ttu-id="43fcc-130">Bir etiket ve Zamanlayıcı bileşik denetiminize eklemek için</span><span class="sxs-lookup"><span data-stu-id="43fcc-130">To add a Label and a Timer to your composite control</span></span>  
  
1.  <span data-ttu-id="43fcc-131">Çözüm Gezgini'nde sağ **ctlClock.vb**ve ardından **Görünüm Tasarımcısı**.</span><span class="sxs-lookup"><span data-stu-id="43fcc-131">In Solution Explorer, right-click **ctlClock.vb**, and then click **View Designer**.</span></span>  
  
2.  <span data-ttu-id="43fcc-132">Araç kutusunda genişletin **ortak denetimleri** düğüm gittikten sonra çift tıklayarak **etiket**.</span><span class="sxs-lookup"><span data-stu-id="43fcc-132">In the Toolbox, expand the **Common Controls** node, and then double-click **Label**.</span></span>  
  
     <span data-ttu-id="43fcc-133">A <xref:System.Windows.Forms.Label> adlı Denetim `Label1` Tasarımcı yüzeyinde, denetimi eklenir.</span><span class="sxs-lookup"><span data-stu-id="43fcc-133">A <xref:System.Windows.Forms.Label> control named `Label1` is added to your control on the designer surface.</span></span>  
  
3.  <span data-ttu-id="43fcc-134">Tasarımcıda **Label1**.</span><span class="sxs-lookup"><span data-stu-id="43fcc-134">In the designer, click **Label1**.</span></span> <span data-ttu-id="43fcc-135">Özellikler penceresinde, aşağıdaki özellikleri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="43fcc-135">In the Properties window, set the following properties.</span></span>  
  
    |<span data-ttu-id="43fcc-136">Özellik</span><span class="sxs-lookup"><span data-stu-id="43fcc-136">Property</span></span>|<span data-ttu-id="43fcc-137">Değiştirin</span><span class="sxs-lookup"><span data-stu-id="43fcc-137">Change to</span></span>|  
    |--------------|---------------|  
    |<span data-ttu-id="43fcc-138">**Ad**</span><span class="sxs-lookup"><span data-stu-id="43fcc-138">**Name**</span></span>|`lblDisplay`|  
    |<span data-ttu-id="43fcc-139">**Metin**</span><span class="sxs-lookup"><span data-stu-id="43fcc-139">**Text**</span></span>|`(blank space)`|  
    |<span data-ttu-id="43fcc-140">**TextAlign**</span><span class="sxs-lookup"><span data-stu-id="43fcc-140">**TextAlign**</span></span>|`MiddleCenter`|  
    |<span data-ttu-id="43fcc-141">**Font.Size**</span><span class="sxs-lookup"><span data-stu-id="43fcc-141">**Font.Size**</span></span>|`14`|  
  
4.  <span data-ttu-id="43fcc-142">İçinde **araç kutusu**, genişletme **bileşenleri** düğüm gittikten sonra çift tıklayarak **Zamanlayıcı**.</span><span class="sxs-lookup"><span data-stu-id="43fcc-142">In the **Toolbox**, expand the **Components** node, and then double-click **Timer**.</span></span>  
  
     <span data-ttu-id="43fcc-143">Çünkü bir <xref:System.Windows.Forms.Timer> bir bileşen çalışma zamanında görsel bir temsili sahiptir.</span><span class="sxs-lookup"><span data-stu-id="43fcc-143">Because a <xref:System.Windows.Forms.Timer> is a component, it has no visual representation at run time.</span></span> <span data-ttu-id="43fcc-144">Bu nedenle, denetimlerle Tasarımcı yüzeyine, ancak bunun yerine (tasarımcı yüzeyine alt kısmındaki Tepsisi) Bileşen Tasarımcısı'nda görünmez.</span><span class="sxs-lookup"><span data-stu-id="43fcc-144">Therefore, it does not appear with the controls on the designer surface, but rather in the Component Designer (a tray at the bottom of the designer surface).</span></span>  
  
5.  <span data-ttu-id="43fcc-145">Bileşen Tasarımcısı'nda tıklatın **Süreölçer1**ve ardından <xref:System.Windows.Forms.Timer.Interval%2A> özelliğini `1000` ve <xref:System.Windows.Forms.Timer.Enabled%2A> özelliğini `True`.</span><span class="sxs-lookup"><span data-stu-id="43fcc-145">In the Component Designer, click **Timer1**, and then set the <xref:System.Windows.Forms.Timer.Interval%2A> property to `1000` and the <xref:System.Windows.Forms.Timer.Enabled%2A> property to `True`.</span></span>  
  
     <span data-ttu-id="43fcc-146"><xref:System.Windows.Forms.Timer.Interval%2A> Özellik süreölçer bileşeni ile işaretlerini sıklığını denetler.</span><span class="sxs-lookup"><span data-stu-id="43fcc-146">The <xref:System.Windows.Forms.Timer.Interval%2A> property controls the frequency with which the timer component ticks.</span></span> <span data-ttu-id="43fcc-147">Her zaman `Timer1` saat tıklaması, çalışırken kod `Timer1_Tick` olay.</span><span class="sxs-lookup"><span data-stu-id="43fcc-147">Each time `Timer1` ticks, it runs the code in the `Timer1_Tick` event.</span></span> <span data-ttu-id="43fcc-148">Aralık işaretleri arasındaki milisaniye sayısını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="43fcc-148">The interval represents the number of milliseconds between ticks.</span></span>  
  
6.  <span data-ttu-id="43fcc-149">Bileşen Tasarımcısı'nda çift **Süreölçer1** gitmek için `Timer1_Tick` olayı `ctlClock`.</span><span class="sxs-lookup"><span data-stu-id="43fcc-149">In the Component Designer, double-click **Timer1** to go to the `Timer1_Tick` event for `ctlClock`.</span></span>  
  
7.  <span data-ttu-id="43fcc-150">Kodu aşağıdaki kod örneği benzeyecek şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="43fcc-150">Modify the code so that it resembles the following code sample.</span></span> <span data-ttu-id="43fcc-151">Gelen erişim değiştiricisi değiştirdiğinizden emin olun `Private` için `Protected`.</span><span class="sxs-lookup"><span data-stu-id="43fcc-151">Be sure to change the access modifier from `Private` to `Protected`.</span></span>  
  
    ```vb  
    Protected Sub Timer1_Tick(ByVal sender As Object, ByVal e As _  
        System.EventArgs) Handles Timer1.Tick  
        ' Causes the label to display the current time.    
        lblDisplay.Text = Format(Now, "hh:mm:ss")  
    End Sub  
    ```  
  
     <span data-ttu-id="43fcc-152">Bu kodun geçerli saate göre gösterilecek neden olur `lblDisplay`.</span><span class="sxs-lookup"><span data-stu-id="43fcc-152">This code will cause the current time to be shown in `lblDisplay`.</span></span> <span data-ttu-id="43fcc-153">Çünkü aralığı `Timer1` ayarlandı `1000`, bu olay, böylece her saniye geçerli saati güncelleştiriliyor her bin milisaniye meydana gelir.</span><span class="sxs-lookup"><span data-stu-id="43fcc-153">Because the interval of `Timer1` was set to `1000`, this event will occur every thousand milliseconds, thus updating the current time every second.</span></span>  
  
8.  <span data-ttu-id="43fcc-154">Yöntem geçersiz kılınabilir olacak şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="43fcc-154">Modify the method to be overridable.</span></span> <span data-ttu-id="43fcc-155">Daha fazla bilgi için "Devralan bir kullanıcı denetimi" bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="43fcc-155">For more information, see the "Inheriting from a User Control" section below.</span></span>  
  
    ```vb  
    Protected Overridable Sub Timer1_Tick(ByVal sender As Object, ByVal _  
        e As System.EventArgs) Handles Timer1.Tick  
    ```  
  
9. <span data-ttu-id="43fcc-156">Üzerinde **dosya** menüsünü tıklatın **Tümünü Kaydet** projeyi kaydetmek için.</span><span class="sxs-lookup"><span data-stu-id="43fcc-156">On the **File** menu, click **Save All** to save the project.</span></span>  
  
## <a name="adding-properties-to-the-composite-control"></a><span data-ttu-id="43fcc-157">Bileşik denetime özellik ekleme</span><span class="sxs-lookup"><span data-stu-id="43fcc-157">Adding Properties to the Composite Control</span></span>  
 <span data-ttu-id="43fcc-158">Saat denetiminiz artık kapsülleyen bir <xref:System.Windows.Forms.Label> denetimi ve bir <xref:System.Windows.Forms.Timer> bileşeni, her biri kendi devralınan özellikler kümesi.</span><span class="sxs-lookup"><span data-stu-id="43fcc-158">Your clock control now encapsulates a <xref:System.Windows.Forms.Label> control and a <xref:System.Windows.Forms.Timer> component, each with its own set of inherent properties.</span></span> <span data-ttu-id="43fcc-159">Bu denetimlerin özelliklerini bireysel denetiminizin sonraki kullanıcılar için erişilebilir değil ancak oluşturabilir ve uygun blok kod yazarak özel özellikler kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="43fcc-159">While the individual properties of these controls will not be accessible to subsequent users of your control, you can create and expose custom properties by writing the appropriate blocks of code.</span></span> <span data-ttu-id="43fcc-160">Aşağıdaki yordamda, metin ve arka plan rengini değiştirmek kullanıcının denetiminize özellikler ekleyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="43fcc-160">In the following procedure, you will add properties to your control that enable the user to change the color of the background and text.</span></span>  
  
#### <a name="to-add-a-property-to-your-composite-control"></a><span data-ttu-id="43fcc-161">Bileşik denetiminiz için bir özellik eklemek için</span><span class="sxs-lookup"><span data-stu-id="43fcc-161">To add a property to your composite control</span></span>  
  
1.  <span data-ttu-id="43fcc-162">Çözüm Gezgini'nde sağ **ctlClock.vb**ve ardından **kodu görüntüle**.</span><span class="sxs-lookup"><span data-stu-id="43fcc-162">In Solution Explorer, right-click **ctlClock.vb**, and then click **View Code**.</span></span>  
  
     <span data-ttu-id="43fcc-163">Denetiminiz için kod düzenleyicisi açılır.</span><span class="sxs-lookup"><span data-stu-id="43fcc-163">The Code Editor for your control opens.</span></span>  
  
2.  <span data-ttu-id="43fcc-164">Bulun `Public Class ctlClock` deyimi.</span><span class="sxs-lookup"><span data-stu-id="43fcc-164">Locate the `Public Class ctlClock` statement.</span></span> <span data-ttu-id="43fcc-165">Bunun altında aşağıdaki kodu yazın.</span><span class="sxs-lookup"><span data-stu-id="43fcc-165">Beneath it, type the following code.</span></span>  
  
    ```vb  
    Private colFColor as Color  
    Private colBColor as Color  
    ```  
  
     <span data-ttu-id="43fcc-166">Bu deyimler oluşturmak üzere olduğunuz özelliklerinin değerlerini depolamak için kullanılacak özel değişkenleri oluşturun.</span><span class="sxs-lookup"><span data-stu-id="43fcc-166">These statements create the private variables that you will use to store the values for the properties you are about to create.</span></span>  
  
3.  <span data-ttu-id="43fcc-167">Adım 2 ' değişken bildirimlerini altına aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="43fcc-167">Insert the following code beneath the variable declarations from step 2.</span></span>  
  
    ```vb  
    ' Declares the name and type of the property.  
    Property ClockBackColor() as Color  
        ' Retrieves the value of the private variable colBColor.  
        Get  
            Return colBColor  
        End Get  
        ' Stores the selected value in the private variable colBColor, and   
        ' updates the background color of the label control lblDisplay.  
        Set(ByVal value as Color)  
            colBColor = value  
            lblDisplay.BackColor = colBColor     
        End Set  
  
    End Property  
    ' Provides a similar set of instructions for the foreground color.  
    Property ClockForeColor() as Color  
        Get  
            Return colFColor  
        End Get  
        Set(ByVal value as Color)  
            colFColor = value  
            lblDisplay.ForeColor = colFColor  
        End Set  
    End Property  
    ```  
  
     <span data-ttu-id="43fcc-168">Yukarıdaki kod, iki özel özellikler yapar `ClockForeColor` ve `ClockBackColor`, sonraki kullanıcılara çağırarak bu denetimin `Property` deyimi.</span><span class="sxs-lookup"><span data-stu-id="43fcc-168">The preceding code makes two custom properties, `ClockForeColor` and `ClockBackColor`, available to subsequent users of this control by invoking the `Property` statement.</span></span> <span data-ttu-id="43fcc-169">`Get` Ve `Set` deyimleri, depolama ve alma işlevselliğini uygulamak için kod yanı sıra özellik değeri, özellik için uygun sağlayın.</span><span class="sxs-lookup"><span data-stu-id="43fcc-169">The `Get` and `Set` statements provide for storage and retrieval of the property value, as well as code to implement functionality appropriate to the property.</span></span>  
  
4.  <span data-ttu-id="43fcc-170">Üzerinde **dosya** menüsünü tıklatın **Tümünü Kaydet** projeyi kaydetmek için.</span><span class="sxs-lookup"><span data-stu-id="43fcc-170">On the **File** menu, click **Save All** to save the project.</span></span>  
  
## <a name="testing-the-control"></a><span data-ttu-id="43fcc-171">Denetimini test etme</span><span class="sxs-lookup"><span data-stu-id="43fcc-171">Testing the Control</span></span>  
 <span data-ttu-id="43fcc-172">Denetimler, tek başına projeleri değildir; Bunlar, bir kapsayıcıda barındırılan gerekir.</span><span class="sxs-lookup"><span data-stu-id="43fcc-172">Controls are not stand-alone projects; they must be hosted in a container.</span></span> <span data-ttu-id="43fcc-173">Denetimin çalışma zamanı davranışını sınama ve özellikleriyle birlikte çalışma **UserControl Test kapsayıcısı**.</span><span class="sxs-lookup"><span data-stu-id="43fcc-173">Test your control's run-time behavior and exercise its properties with the **UserControl Test Container**.</span></span> <span data-ttu-id="43fcc-174">Daha fazla bilgi için [nasıl yapılır: Bir UserControl denetiminin çalışma zamanı davranışını sınama](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span><span class="sxs-lookup"><span data-stu-id="43fcc-174">For more information, see [How to: Test the Run-Time Behavior of a UserControl](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>  
  
#### <a name="to-test-your-control"></a><span data-ttu-id="43fcc-175">Denetiminiz test etmek için</span><span class="sxs-lookup"><span data-stu-id="43fcc-175">To test your control</span></span>  
  
1.  <span data-ttu-id="43fcc-176">Projeyi oluşturmak ve denetim çalıştırmak için F5 tuşuna basın **UserControl Test kapsayıcısı**.</span><span class="sxs-lookup"><span data-stu-id="43fcc-176">Press F5 to build the project and run your control in the **UserControl Test Container**.</span></span>  
  
2.  <span data-ttu-id="43fcc-177">Test kapsayıcının özellik kılavuzunda seçin `ClockBackColor` özelliği ve ardından renk paletini görüntülemek için açılan oka tıklayın.</span><span class="sxs-lookup"><span data-stu-id="43fcc-177">In the test container's property grid, select the `ClockBackColor` property, and then click the drop-down arrow to display the color palette.</span></span>  
  
3.  <span data-ttu-id="43fcc-178">Tıklayarak bir renk seçin.</span><span class="sxs-lookup"><span data-stu-id="43fcc-178">Choose a color by clicking it.</span></span>  
  
     <span data-ttu-id="43fcc-179">Denetim arka plan rengi, seçtiğiniz rengine değiştirir.</span><span class="sxs-lookup"><span data-stu-id="43fcc-179">The background color of your control changes to the color you selected.</span></span>  
  
4.  <span data-ttu-id="43fcc-180">Doğrulamak için benzer bir olay dizisi kullanan `ClockForeColor` özelliği beklendiği gibi çalışmıyor.</span><span class="sxs-lookup"><span data-stu-id="43fcc-180">Use a similar sequence of events to verify that the `ClockForeColor` property is functioning as expected.</span></span>  
  
5.  <span data-ttu-id="43fcc-181">Tıklayın **kapatmak** kapatmak için **UserControl Test kapsayıcısı**.</span><span class="sxs-lookup"><span data-stu-id="43fcc-181">Click **Close** to close the **UserControl Test Container**.</span></span>  
  
     <span data-ttu-id="43fcc-182">Bu bölümde ve önceki bölümlerde, bileşenleri ve Windows denetimleri nasıl birleştirileceğini gördünüz kodla ve paketleme bileşik denetim biçiminde özel işlevsellik sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="43fcc-182">In this section and the preceding sections, you have seen how components and Windows controls can be combined with code and packaging to provide custom functionality in the form of a composite control.</span></span> <span data-ttu-id="43fcc-183">Bileşik Denetim ve denetim, tamamlandıktan sonra test etme özellikleri göstermek öğrendiniz.</span><span class="sxs-lookup"><span data-stu-id="43fcc-183">You have learned to expose properties in your composite control, and how to test your control after it is complete.</span></span> <span data-ttu-id="43fcc-184">Sonraki bölümde kullanarak bir devralınan bileşik denetim oluşturmak hakkında bilgi edineceksiniz `ctlClock` temel olarak.</span><span class="sxs-lookup"><span data-stu-id="43fcc-184">In the next section you will learn how to construct an inherited composite control using `ctlClock` as a base.</span></span>  
  
## <a name="inheriting-from-a-composite-control"></a><span data-ttu-id="43fcc-185">Bileşik Denetim devralıyor</span><span class="sxs-lookup"><span data-stu-id="43fcc-185">Inheriting from a Composite Control</span></span>  
 <span data-ttu-id="43fcc-186">Önceki bölümlerde Windows denetimleri, bileşenleri ve kod yeniden kullanılabilir bileşik denetimler birleştirmek öğrendiniz.</span><span class="sxs-lookup"><span data-stu-id="43fcc-186">In the previous sections, you learned how to combine Windows controls, components, and code into reusable composite controls.</span></span> <span data-ttu-id="43fcc-187">Bileşik Denetim artık diğer denetimlerin oluşturulabilir, bir temel olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="43fcc-187">Your composite control can now be used as a base upon which other controls can be built.</span></span> <span data-ttu-id="43fcc-188">Sınıf bir taban sınıftan türetme işlemine denir *devralma*.</span><span class="sxs-lookup"><span data-stu-id="43fcc-188">The process of deriving a class from a base class is called *inheritance*.</span></span> <span data-ttu-id="43fcc-189">Bu bölümde, adlı bileşik denetim oluşturacaksınız `ctlAlarmClock`.</span><span class="sxs-lookup"><span data-stu-id="43fcc-189">In this section, you will create a composite control called `ctlAlarmClock`.</span></span> <span data-ttu-id="43fcc-190">Bu denetim, üst denetiminden elde edilir `ctlClock`.</span><span class="sxs-lookup"><span data-stu-id="43fcc-190">This control will be derived from its parent control, `ctlClock`.</span></span> <span data-ttu-id="43fcc-191">Genişletmek öğreneceksiniz `ctlClock` üst yöntemleri geçersiz kılma ve yeni yöntemleri ve özellikleri ekleme.</span><span class="sxs-lookup"><span data-stu-id="43fcc-191">You will learn to extend the functionality of `ctlClock` by overriding parent methods and adding new methods and properties.</span></span>  
  
 <span data-ttu-id="43fcc-192">Devralınan bir denetim oluşturmanın ilk adımı, üst öğesinden türetilen sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="43fcc-192">The first step in creating an inherited control is to derive it from its parent.</span></span> <span data-ttu-id="43fcc-193">Bu eylem, tüm özellikleri, yöntemleri ve üst denetimin grafik özelliklerine sahip yeni bir denetim oluşturur, ancak yeni veya değiştirilmiş işlevselliği eklenmesi için temel olarak da hareket.</span><span class="sxs-lookup"><span data-stu-id="43fcc-193">This action creates a new control that has all of the properties, methods, and graphical characteristics of the parent control, but can also act as a base for the addition of new or modified functionality.</span></span>  
  
#### <a name="to-create-the-inherited-control"></a><span data-ttu-id="43fcc-194">Devralınan bir denetim oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="43fcc-194">To create the inherited control</span></span>  
  
1.  <span data-ttu-id="43fcc-195">Çözüm Gezgini'nde sağ **ctlClockLib**, işaret **Ekle**ve ardından **kullanıcı denetimi**.</span><span class="sxs-lookup"><span data-stu-id="43fcc-195">In Solution Explorer, right-click **ctlClockLib**, point to **Add**, and then click **User Control**.</span></span>  
  
     <span data-ttu-id="43fcc-196">**Yeni Öğe Ekle** iletişim kutusu açılır.</span><span class="sxs-lookup"><span data-stu-id="43fcc-196">The **Add New Item** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="43fcc-197">Seçin **devralınan kullanıcı denetimi** şablonu.</span><span class="sxs-lookup"><span data-stu-id="43fcc-197">Select the **Inherited User Control** template.</span></span>  
  
3.  <span data-ttu-id="43fcc-198">İçinde **adı** kutusuna `ctlAlarmClock.vb`ve ardından **Ekle**.</span><span class="sxs-lookup"><span data-stu-id="43fcc-198">In the **Name** box, type `ctlAlarmClock.vb`, and then click **Add**.</span></span>  
  
     <span data-ttu-id="43fcc-199">**Devralma Seçici** iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="43fcc-199">The **Inheritance Picker** dialog box appears.</span></span>  
  
4.  <span data-ttu-id="43fcc-200">Altında **bileşen adı**, çift **ctlClock**.</span><span class="sxs-lookup"><span data-stu-id="43fcc-200">Under **Component Name**, double-click **ctlClock**.</span></span>  
  
5.  <span data-ttu-id="43fcc-201">Çözüm Gezgini içinde geçerli projeleri göz atın.</span><span class="sxs-lookup"><span data-stu-id="43fcc-201">In Solution Explorer, browse through the current projects.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="43fcc-202">Dosya adında **ctlAlarmClock.vb** geçerli projeye eklendi.</span><span class="sxs-lookup"><span data-stu-id="43fcc-202">A file called **ctlAlarmClock.vb** has been added to the current project.</span></span>  
  
### <a name="adding-the-alarm-properties"></a><span data-ttu-id="43fcc-203">Uyarı özellikleri ekleme</span><span class="sxs-lookup"><span data-stu-id="43fcc-203">Adding the Alarm Properties</span></span>  
 <span data-ttu-id="43fcc-204">Bileşik denetim için eklenen aynı şekilde, devralınan bir denetim için özellikler eklenir.</span><span class="sxs-lookup"><span data-stu-id="43fcc-204">Properties are added to an inherited control in the same way they are added to a composite control.</span></span> <span data-ttu-id="43fcc-205">Şimdi iki özellik denetiminize eklemek için özellik bildirimi sözdizimi kullanır: `AlarmTime`, tarih ve saat alarma olan kapalı, Git değerini depolar ve `AlarmSet`, hangi uyarı ayarlanıp ayarlanmadığını gösterecektir.</span><span class="sxs-lookup"><span data-stu-id="43fcc-205">You will now use the property declaration syntax to add two properties to your control: `AlarmTime`, which will store the value of the date and time the alarm is to go off, and `AlarmSet`, which will indicate whether the alarm is set.</span></span>  
  
##### <a name="to-add-properties-to-your-composite-control"></a><span data-ttu-id="43fcc-206">Özellikler birleşik denetiminize eklemek için</span><span class="sxs-lookup"><span data-stu-id="43fcc-206">To add properties to your composite control</span></span>  
  
1.  <span data-ttu-id="43fcc-207">Çözüm Gezgini'nde sağ **ctlAlarmClock**ve ardından **kodu görüntüle**.</span><span class="sxs-lookup"><span data-stu-id="43fcc-207">In Solution Explorer, right-click **ctlAlarmClock**, and then click **View Code**.</span></span>  
  
2.  <span data-ttu-id="43fcc-208">Sınıf bildirimi olarak görünür ctlAlarmClock denetimi için bulun `Public Class ctlAlarmClock`.</span><span class="sxs-lookup"><span data-stu-id="43fcc-208">Locate the class declaration for the ctlAlarmClock control, which appears as `Public Class ctlAlarmClock`.</span></span>  <span data-ttu-id="43fcc-209">Sınıf bildiriminde aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="43fcc-209">In the class declaration, insert the following code.</span></span>  
  
    ```vb  
    Private dteAlarmTime As Date  
    Private blnAlarmSet As Boolean  
    ' These properties will be declared as Public to allow future   
    ' developers to access them.  
    Public Property AlarmTime() As Date  
        Get  
            Return dteAlarmTime  
        End Get  
        Set(ByVal value as Date)  
            dteAlarmTime = value  
        End Set  
    End Property  
    Public Property AlarmSet() As Boolean  
        Get  
            Return blnAlarmSet  
        End Get  
        Set(ByVal value as Boolean)  
            blnAlarmSet = value  
        End Set  
    End Property  
    ```  
  
### <a name="adding-to-the-graphical-interface-of-the-control"></a><span data-ttu-id="43fcc-210">Grafik arabirimine denetimi ekleme</span><span class="sxs-lookup"><span data-stu-id="43fcc-210">Adding to the Graphical Interface of the Control</span></span>  
 <span data-ttu-id="43fcc-211">Devralınan denetim devraldığı denetlemek için aynı olan görsel bir arabirim sahiptir.</span><span class="sxs-lookup"><span data-stu-id="43fcc-211">Your inherited control has a visual interface that is identical to the control it inherits from.</span></span> <span data-ttu-id="43fcc-212">Aynı bağlı denetimler, üst denetim olarak sahiptir, ancak özel olarak sunulan sürece bağlı denetimlerin özelliklerini kullanılabilir olmayacak.</span><span class="sxs-lookup"><span data-stu-id="43fcc-212">It possesses the same constituent controls as its parent control, but the properties of the constituent controls will not be available unless they were specifically exposed.</span></span> <span data-ttu-id="43fcc-213">Herhangi bir bileşik denetimi olduğu gibi aynı şekilde devralınan bir bileşik denetim grafik arabirimine ekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="43fcc-213">You may add to the graphical interface of an inherited composite control in the same manner as you would add to any composite control.</span></span> <span data-ttu-id="43fcc-214">Uyarı Saatin görsel arabirim olarak eklemeye devam etmek için alarm uyarabilir yükleyen yanar etiket denetimi ekleyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="43fcc-214">To continue adding to your alarm clock's visual interface, you will add a label control that will flash when the alarm is sounding.</span></span>  
  
##### <a name="to-add-the-label-control"></a><span data-ttu-id="43fcc-215">Etiket denetimi eklemek için</span><span class="sxs-lookup"><span data-stu-id="43fcc-215">To add the label control</span></span>  
  
1.  <span data-ttu-id="43fcc-216">Çözüm Gezgini'nde sağ **ctlAlarmClock**, tıklatıp **Görünüm Tasarımcısı**.</span><span class="sxs-lookup"><span data-stu-id="43fcc-216">In Solution Explorer, right-click **ctlAlarmClock**, and click **View Designer**.</span></span>  
  
     <span data-ttu-id="43fcc-217">Tasarımcı için `ctlAlarmClock` ana penceresinde açılır.</span><span class="sxs-lookup"><span data-stu-id="43fcc-217">The designer for `ctlAlarmClock` opens in the main window.</span></span>  
  
2.  <span data-ttu-id="43fcc-218">Tıklayın `lblDisplay` (denetiminin görünen kısmı) ve Özellikler penceresini görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="43fcc-218">Click `lblDisplay` (the display portion of the control), and view the Properties window.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="43fcc-219">Tüm özellikler görüntülenir, ancak bunlar soluklaştırılır.</span><span class="sxs-lookup"><span data-stu-id="43fcc-219">While all the properties are displayed, they are dimmed.</span></span> <span data-ttu-id="43fcc-220">Bu, bu özellikleri için yerel gösterir `lblDisplay` ve değiştirilemez veya Özellikler penceresinde erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="43fcc-220">This indicates that these properties are native to `lblDisplay` and cannot be modified or accessed in the Properties window.</span></span> <span data-ttu-id="43fcc-221">Varsayılan olarak, bu bileşik denetiminde bulunan denetimlerdir `Private`, ve bunların özelliklerini herhangi bir yolla erişilebilir değildir.</span><span class="sxs-lookup"><span data-stu-id="43fcc-221">By default, controls contained in a composite control are `Private`, and their properties are not accessible by any means.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="43fcc-222">Bileşik denetiminizin sonraki kullanıcıların kendi iç denetimleri erişmesini isterseniz, bunları olarak bildirin `Public` veya `Protected`.</span><span class="sxs-lookup"><span data-stu-id="43fcc-222">If you want subsequent users of your composite control to have access to its internal controls, declare them as `Public` or `Protected`.</span></span> <span data-ttu-id="43fcc-223">Bu, ayarlamak ve uygun kodu kullanarak bileşik denetiminizin içinde yer alan denetimlerin özelliklerini değiştirmek olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="43fcc-223">This will allow you to set and modify properties of controls contained within your composite control by using the appropriate code.</span></span>  
  
3.  <span data-ttu-id="43fcc-224">Ekleme bir <xref:System.Windows.Forms.Label> denetimi için bileşik denetim.</span><span class="sxs-lookup"><span data-stu-id="43fcc-224">Add a <xref:System.Windows.Forms.Label> control to your composite control.</span></span>  
  
4.  <span data-ttu-id="43fcc-225">Fareyle sürükleyin <xref:System.Windows.Forms.Label> görüntüleme kutusunun hemen altındaki denetimi.</span><span class="sxs-lookup"><span data-stu-id="43fcc-225">Using the mouse, drag the <xref:System.Windows.Forms.Label> control immediately beneath the display box.</span></span> <span data-ttu-id="43fcc-226">Özellikler penceresinde, aşağıdaki özellikleri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="43fcc-226">In the Properties window, set the following properties.</span></span>  
  
    |<span data-ttu-id="43fcc-227">Özellik</span><span class="sxs-lookup"><span data-stu-id="43fcc-227">Property</span></span>|<span data-ttu-id="43fcc-228">Ayar</span><span class="sxs-lookup"><span data-stu-id="43fcc-228">Setting</span></span>|  
    |--------------|-------------|  
    |<span data-ttu-id="43fcc-229">**Ad**</span><span class="sxs-lookup"><span data-stu-id="43fcc-229">**Name**</span></span>|`lblAlarm`|  
    |<span data-ttu-id="43fcc-230">**Metin**</span><span class="sxs-lookup"><span data-stu-id="43fcc-230">**Text**</span></span>|<span data-ttu-id="43fcc-231">**Uyarı!**</span><span class="sxs-lookup"><span data-stu-id="43fcc-231">**Alarm!**</span></span>|  
    |<span data-ttu-id="43fcc-232">**TextAlign**</span><span class="sxs-lookup"><span data-stu-id="43fcc-232">**TextAlign**</span></span>|`MiddleCenter`|  
    |<span data-ttu-id="43fcc-233">**Görünür**</span><span class="sxs-lookup"><span data-stu-id="43fcc-233">**Visible**</span></span>|`False`|  
  
### <a name="adding-the-alarm-functionality"></a><span data-ttu-id="43fcc-234">Uyarı işlevsellik ekleme</span><span class="sxs-lookup"><span data-stu-id="43fcc-234">Adding the Alarm Functionality</span></span>  
 <span data-ttu-id="43fcc-235">Önceki yordamlarda, özellikleri ve bileşik denetim uyarısı işlevselliği sağlayan bir denetimi eklendi.</span><span class="sxs-lookup"><span data-stu-id="43fcc-235">In the previous procedures, you added properties and a control that will enable alarm functionality in your composite control.</span></span> <span data-ttu-id="43fcc-236">Bu yordamda, alarm saati geçerli saate karşılaştırmak için kod ekleyeceksiniz ve aynı, ses ve bir uyarı flash olmaları durumunda.</span><span class="sxs-lookup"><span data-stu-id="43fcc-236">In this procedure, you will add code to compare the current time to the alarm time and, if they are the same, to sound and flash an alarm.</span></span> <span data-ttu-id="43fcc-237">Geçersiz kılma tarafından `Timer1_Tick` yöntemi `ctlClock` ve ek kod ekleme, yeteneğini genişletecek `ctlAlarmClock` tüm devralınan işlevselliğini korurken `ctlClock`.</span><span class="sxs-lookup"><span data-stu-id="43fcc-237">By overriding the `Timer1_Tick` method of `ctlClock` and adding additional code to it, you will extend the capability of `ctlAlarmClock` while retaining all of the inherent functionality of `ctlClock`.</span></span>  
  
##### <a name="to-override-the-timer1tick-method-of-ctlclock"></a><span data-ttu-id="43fcc-238">CtlClock Timer1_Tick yöntemi geçersiz kılmak için</span><span class="sxs-lookup"><span data-stu-id="43fcc-238">To override the Timer1_Tick method of ctlClock</span></span>  
  
1.  <span data-ttu-id="43fcc-239">Çözüm Gezgini'nde sağ **ctlAlarmClock.vb**ve ardından **kodu görüntüle**.</span><span class="sxs-lookup"><span data-stu-id="43fcc-239">In Solution Explorer, right-click **ctlAlarmClock.vb**, and then click **View Code**.</span></span>  
  
2.  <span data-ttu-id="43fcc-240">Bulun `Private blnAlarmSet As Boolean` deyimi.</span><span class="sxs-lookup"><span data-stu-id="43fcc-240">Locate the `Private blnAlarmSet As Boolean` statement.</span></span> <span data-ttu-id="43fcc-241">Hemen altında aşağıdaki deyimi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="43fcc-241">Immediately beneath it, add the following statement.</span></span>  
  
    ```vb  
    Dim blnColorTicker as Boolean  
    ```  
  
3.  <span data-ttu-id="43fcc-242">Bulun `End Class` sayfanın alt kısmındaki deyimi.</span><span class="sxs-lookup"><span data-stu-id="43fcc-242">Locate the `End Class` statement at the bottom of the page.</span></span> <span data-ttu-id="43fcc-243">Hemen önce `End Class` deyimi, aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="43fcc-243">Just before the `End Class` statement, add the following code.</span></span>  
  
    ```vb  
    Protected Overrides Sub Timer1_Tick(ByVal sender As Object, ByVal e _  
        As System.EventArgs)  
        ' Calls the Timer1_Tick method of ctlClock.  
        MyBase.Timer1_Tick(sender, e)  
        ' Checks to see if the Alarm is set.  
        If AlarmSet = False Then  
            Exit Sub  
        End If  
        ' If the date, hour, and minute of the alarm time are the same as  
        ' now, flash and beep an alarm.   
        If AlarmTime.Date = Now.Date And AlarmTime.Hour = Now.Hour And _  
            AlarmTime.Minute = Now.Minute Then  
            ' Sounds an audible beep.  
            Beep()  
            ' Sets lblAlarmVisible to True, and changes the background color based on the   
            ' value of blnColorTicker. The background color of the label will   
            ' flash once per tick of the clock.  
            lblAlarm.Visible = True  
            If blnColorTicker = False Then  
                lblAlarm.BackColor = Color.PeachPuff  
                blnColorTicker = True  
            Else  
                lblAlarm.BackColor = Color.Plum  
                blnColorTicker = False  
            End If  
        Else  
            ' Once the alarm has sounded for a minute, the label is made   
            ' invisible again.  
            lblAlarm.Visible = False  
        End If  
    End Sub  
    ```  
  
     <span data-ttu-id="43fcc-244">Bu kodu eklenmesi birkaç görev gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="43fcc-244">The addition of this code accomplishes several tasks.</span></span> <span data-ttu-id="43fcc-245">`Overrides` Deyimi temel denetiminden devralındı yöntemi yerine bu yöntemi kullanmak için denetimi yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="43fcc-245">The `Overrides` statement directs the control to use this method in place of the method that was inherited from the base control.</span></span> <span data-ttu-id="43fcc-246">Bu yöntem çağrıldığında, onu geçersiz kılar çağırarak yöntemini çağırır `MyBase.Timer1_Tick` deyimi, tüm işlevlerin özgün denetiminde dahil sağlayarak bu denetimde çoğaltılamaz.</span><span class="sxs-lookup"><span data-stu-id="43fcc-246">When this method is called, it calls the method it overrides by invoking the `MyBase.Timer1_Tick` statement, ensuring that all of the functionality incorporated in the original control is reproduced in this control.</span></span> <span data-ttu-id="43fcc-247">Ardından, uyarı işlevselliği eklemek için ek kod çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="43fcc-247">It then runs additional code to incorporate the alarm functionality.</span></span> <span data-ttu-id="43fcc-248">Uyarı oluşur ve sesli bir bip sesi heard yanıp sönen bir etiket denetimi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="43fcc-248">A flashing label control will appear when the alarm occurs, and an audible beep will be heard.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="43fcc-249">Devralınan bir olay işleyicisi geçersiz kıldıkları için olay ile belirtmek gerekmez `Handles` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="43fcc-249">Because you are overriding an inherited event handler, you do not have to specify the event with the `Handles` keyword.</span></span> <span data-ttu-id="43fcc-250">Olay zaten ölçekledikçe.</span><span class="sxs-lookup"><span data-stu-id="43fcc-250">The event is already hooked up.</span></span> <span data-ttu-id="43fcc-251">Geçersiz kıldıkları şey işleyicisinin uygulaması.</span><span class="sxs-lookup"><span data-stu-id="43fcc-251">All you are overriding is the implementation of the handler.</span></span>  
  
     <span data-ttu-id="43fcc-252">Uyarı saat denetiminiz hemen tamamlanır.</span><span class="sxs-lookup"><span data-stu-id="43fcc-252">Your alarm clock control is almost complete.</span></span> <span data-ttu-id="43fcc-253">Kalan tek şey, devre dışı bırakmak için bir yol uygulamaktır.</span><span class="sxs-lookup"><span data-stu-id="43fcc-253">The only thing that remains is to implement a way to turn it off.</span></span> <span data-ttu-id="43fcc-254">Bunu yapmak için kod ekleyeceksiniz `lblAlarm_Click` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="43fcc-254">To do this, you will add code to the `lblAlarm_Click` method.</span></span>  
  
##### <a name="to-implement-the-shutoff-method"></a><span data-ttu-id="43fcc-255">Kesici yöntemi uygulamak için</span><span class="sxs-lookup"><span data-stu-id="43fcc-255">To implement the shutoff method</span></span>  
  
1.  <span data-ttu-id="43fcc-256">Çözüm Gezgini'nde sağ **ctlAlarmClock.vb**ve ardından **Görünüm Tasarımcısı**.</span><span class="sxs-lookup"><span data-stu-id="43fcc-256">In Solution Explorer, right-click **ctlAlarmClock.vb**, and then click **View Designer**.</span></span>  
  
2.  <span data-ttu-id="43fcc-257">Tasarımcıda çift **lblAlarm**.</span><span class="sxs-lookup"><span data-stu-id="43fcc-257">In the designer, double-click **lblAlarm**.</span></span> <span data-ttu-id="43fcc-258">**Kod Düzenleyicisi** açılır `Private Sub lblAlarm_Click` satır.</span><span class="sxs-lookup"><span data-stu-id="43fcc-258">The **Code Editor** opens to the `Private Sub lblAlarm_Click` line.</span></span>  
  
3.  <span data-ttu-id="43fcc-259">Bu yöntem, aşağıdaki koda benzer şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="43fcc-259">Modify this method so that it resembles the following code.</span></span>  
  
    ```vb  
    Private Sub lblAlarm_Click(ByVal sender As Object, ByVal e As _  
     System.EventArgs) Handles lblAlarm.Click  
        ' Turns off the alarm.  
        AlarmSet = False  
        ' Hides the flashing label.  
        lblAlarm.Visible = False  
    End Sub  
    ```  
  
4.  <span data-ttu-id="43fcc-260">Üzerinde **dosya** menüsünü tıklatın **Tümünü Kaydet** projeyi kaydetmek için.</span><span class="sxs-lookup"><span data-stu-id="43fcc-260">On the **File** menu, click **Save All** to save the project.</span></span>  
  
### <a name="using-the-inherited-control-on-a-form"></a><span data-ttu-id="43fcc-261">Devralınan Form denetimi kullanma</span><span class="sxs-lookup"><span data-stu-id="43fcc-261">Using the Inherited Control on a Form</span></span>  
 <span data-ttu-id="43fcc-262">Devralınan denetim temel sınıf denetim test aynı şekilde test edebilirsiniz `ctlClock`: Projeyi oluşturmak ve denetim çalıştırmak için F5 tuşuna basın **UserControl Test kapsayıcısı**.</span><span class="sxs-lookup"><span data-stu-id="43fcc-262">You can test your inherited control the same way you tested the base class control, `ctlClock`: Press F5 to build the project and run your control in the **UserControl Test Container**.</span></span> <span data-ttu-id="43fcc-263">Daha fazla bilgi için [nasıl yapılır: Bir UserControl denetiminin çalışma zamanı davranışını sınama](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span><span class="sxs-lookup"><span data-stu-id="43fcc-263">For more information, see [How to: Test the Run-Time Behavior of a UserControl](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>  
  
 <span data-ttu-id="43fcc-264">Denetiminizi kullanmak için koymak için bir form üzerinde barındırmak gerekir.</span><span class="sxs-lookup"><span data-stu-id="43fcc-264">To put your control to use, you will need to host it on a form.</span></span> <span data-ttu-id="43fcc-265">Devralınan bir bileşik denetim standart bileşik denetim gibi tek başına duramaz ve bir form veya diğer kapsayıcı içinde barındırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="43fcc-265">As with a standard composite control, an inherited composite control cannot stand alone and must be hosted in a form or other container.</span></span> <span data-ttu-id="43fcc-266">Bu yana `ctlAlarmClock` daha derinlemesine sahip, işlevselliğini test etmek için ek kod gereklidir.</span><span class="sxs-lookup"><span data-stu-id="43fcc-266">Since `ctlAlarmClock` has a greater depth of functionality, additional code is required to test it.</span></span> <span data-ttu-id="43fcc-267">Bu yordamda işlevselliğini test etmek için basit bir program yazacak `ctlAlarmClock`.</span><span class="sxs-lookup"><span data-stu-id="43fcc-267">In this procedure, you will write a simple program to test the functionality of `ctlAlarmClock`.</span></span> <span data-ttu-id="43fcc-268">Ayarlayın ve görüntülemek için kod yazacaksınız `AlarmTime` özelliği `ctlAlarmClock`ve iç işlevleri test eder.</span><span class="sxs-lookup"><span data-stu-id="43fcc-268">You will write code to set and display the `AlarmTime` property of `ctlAlarmClock`, and will test its inherent functions.</span></span>  
  
##### <a name="to-build-and-add-your-control-to-a-test-form"></a><span data-ttu-id="43fcc-269">Derleme ve test forma denetim ekleme</span><span class="sxs-lookup"><span data-stu-id="43fcc-269">To build and add your control to a test form</span></span>  
  
1.  <span data-ttu-id="43fcc-270">Çözüm Gezgini'nde sağ **ctlClockLib**ve ardından **yapı**.</span><span class="sxs-lookup"><span data-stu-id="43fcc-270">In Solution Explorer, right-click **ctlClockLib**, and then click **Build**.</span></span>  
  
2.  <span data-ttu-id="43fcc-271">Üzerinde **dosya** menüsünde **Ekle**ve ardından **yeni proje**.</span><span class="sxs-lookup"><span data-stu-id="43fcc-271">On the **File** menu, point to **Add**, and then click **New Project**.</span></span>  
  
3.  <span data-ttu-id="43fcc-272">Yeni bir **Windows uygulama** çözüme proje ve adlandırın `Test`.</span><span class="sxs-lookup"><span data-stu-id="43fcc-272">Add a new **Windows Application** project to the solution, and name it `Test`.</span></span>  
  
     <span data-ttu-id="43fcc-273">**Test** proje çözüm Gezgini'ne eklenir.</span><span class="sxs-lookup"><span data-stu-id="43fcc-273">The **Test** project is added to Solution Explorer.</span></span>  
  
4.  <span data-ttu-id="43fcc-274">Çözüm Gezgini'nde sağ `Test` proje düğümünü ve ardından **Başvuru Ekle** görüntülenecek **Başvuru Ekle** iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="43fcc-274">In Solution Explorer, right-click the `Test` project node, and then click **Add Reference** to display the **Add Reference** dialog box.</span></span>  
  
5.  <span data-ttu-id="43fcc-275">Etiketli sekmesini **projeleri**.</span><span class="sxs-lookup"><span data-stu-id="43fcc-275">Click the tab labeled **Projects**.</span></span> <span data-ttu-id="43fcc-276">Proje **ctlClockLib** altında listelenen **proje adı**.</span><span class="sxs-lookup"><span data-stu-id="43fcc-276">The project **ctlClockLib** will be listed under **Project Name**.</span></span> <span data-ttu-id="43fcc-277">Çift **ctlClockLib** test projesine başvuru eklenemiyor.</span><span class="sxs-lookup"><span data-stu-id="43fcc-277">Double-click **ctlClockLib** to add the reference to the test project.</span></span>  
  
6.  <span data-ttu-id="43fcc-278">Çözüm Gezgini'nde sağ **Test**ve ardından **yapı**.</span><span class="sxs-lookup"><span data-stu-id="43fcc-278">In Solution Explorer, right-click **Test**, and then click **Build**.</span></span>  
  
7.  <span data-ttu-id="43fcc-279">İçinde **araç kutusu**, genişletme **ctlClockLib bileşenleri** düğümü.</span><span class="sxs-lookup"><span data-stu-id="43fcc-279">In the **Toolbox**, expand the **ctlClockLib Components** node.</span></span>  
  
8.  <span data-ttu-id="43fcc-280">Çift **ctlAlarmClock** örneğini eklemek için `ctlAlarmClock` formunuza.</span><span class="sxs-lookup"><span data-stu-id="43fcc-280">Double-click **ctlAlarmClock** to add an instance of `ctlAlarmClock` to your form.</span></span>  
  
9. <span data-ttu-id="43fcc-281">İçinde **araç kutusu**, bulun ve çift **DateTimePicker** eklemek için bir <xref:System.Windows.Forms.DateTimePicker> Formunuza denetim ve ardından eklemek bir <xref:System.Windows.Forms.Label> denetimi çift tıklayarak **etiketi**.</span><span class="sxs-lookup"><span data-stu-id="43fcc-281">In the **Toolbox**, locate and double-click **DateTimePicker** to add a <xref:System.Windows.Forms.DateTimePicker> control to your form, and then add a <xref:System.Windows.Forms.Label> control by double-clicking **Label**.</span></span>  
  
10. <span data-ttu-id="43fcc-282">Fare bir kullanışlı yerde form üzerinde denetimleri konumlandırmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="43fcc-282">Use the mouse to position the controls in a convenient place on the form.</span></span>  
  
11. <span data-ttu-id="43fcc-283">Bu denetimin özelliklerini şu şekilde ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="43fcc-283">Set the properties of these controls in the following manner.</span></span>  
  
    |<span data-ttu-id="43fcc-284">Denetim</span><span class="sxs-lookup"><span data-stu-id="43fcc-284">Control</span></span>|<span data-ttu-id="43fcc-285">Özellik</span><span class="sxs-lookup"><span data-stu-id="43fcc-285">Property</span></span>|<span data-ttu-id="43fcc-286">Değer</span><span class="sxs-lookup"><span data-stu-id="43fcc-286">Value</span></span>|  
    |-------------|--------------|-----------|  
    |`label1`|<span data-ttu-id="43fcc-287">**Metin**</span><span class="sxs-lookup"><span data-stu-id="43fcc-287">**Text**</span></span>|`(blank space)`|  
    ||<span data-ttu-id="43fcc-288">**Ad**</span><span class="sxs-lookup"><span data-stu-id="43fcc-288">**Name**</span></span>|`lblTest`|  
    |`dateTimePicker1`|<span data-ttu-id="43fcc-289">**Ad**</span><span class="sxs-lookup"><span data-stu-id="43fcc-289">**Name**</span></span>|`dtpTest`|  
    ||<span data-ttu-id="43fcc-290">**Biçim**</span><span class="sxs-lookup"><span data-stu-id="43fcc-290">**Format**</span></span>|<xref:System.Windows.Forms.DateTimePickerFormat.Time>|  
  
12. <span data-ttu-id="43fcc-291">Tasarımcıda çift **dtpTest**.</span><span class="sxs-lookup"><span data-stu-id="43fcc-291">In the designer, double-click **dtpTest**.</span></span>  
  
     <span data-ttu-id="43fcc-292">**Kod Düzenleyicisi** açılır `Private Sub dtpTest_ValueChanged`.</span><span class="sxs-lookup"><span data-stu-id="43fcc-292">The **Code Editor** opens to `Private Sub dtpTest_ValueChanged`.</span></span>  
  
13. <span data-ttu-id="43fcc-293">Kodu aşağıdakine benzer şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="43fcc-293">Modify the code so that it resembles the following.</span></span>  
  
    ```vb  
    Private Sub dtpTest_ValueChanged(ByVal sender As Object, ByVal e As _  
        System.EventArgs) Handles dtpTest.ValueChanged  
        ctlAlarmClock1.AlarmTime = dtpTest.Value  
        ctlAlarmClock1.AlarmSet = True  
        lblTest.Text = "Alarm Time is " & Format(ctlAlarmClock1.AlarmTime, _  
            "hh:mm")  
    End Sub  
    ```  
  
14. <span data-ttu-id="43fcc-294">Çözüm Gezgini'nde sağ **Test**ve ardından **başlangıç projesi olarak ayarla**.</span><span class="sxs-lookup"><span data-stu-id="43fcc-294">In Solution Explorer, right-click **Test**, and then click **Set as StartUp Project**.</span></span>  
  
15. <span data-ttu-id="43fcc-295">Üzerinde **hata ayıklama** menüsünü tıklatın **hata ayıklamayı Başlat**.</span><span class="sxs-lookup"><span data-stu-id="43fcc-295">On the **Debug** menu, click **Start Debugging**.</span></span>  
  
     <span data-ttu-id="43fcc-296">Test program başlar.</span><span class="sxs-lookup"><span data-stu-id="43fcc-296">The test program starts.</span></span> <span data-ttu-id="43fcc-297">Geçerli saat içinde güncelleştirilir Not `ctlAlarmClock` denetimi ve başlangıç saatini gösterildiği <xref:System.Windows.Forms.DateTimePicker> denetimi.</span><span class="sxs-lookup"><span data-stu-id="43fcc-297">Note that the current time is updated in the `ctlAlarmClock` control, and that the starting time is shown in the <xref:System.Windows.Forms.DateTimePicker> control.</span></span>  
  
16. <span data-ttu-id="43fcc-298">Tıklayın <xref:System.Windows.Forms.DateTimePicker> saat, dakika burada görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="43fcc-298">Click the <xref:System.Windows.Forms.DateTimePicker> where the minutes of the hour are displayed.</span></span>  
  
17. <span data-ttu-id="43fcc-299">Klavyeyi kullanarak, bir dakika tarafından gösterilen geçerli saatten büyük bir değer dakika ayarlamak `ctlAlarmClock`.</span><span class="sxs-lookup"><span data-stu-id="43fcc-299">Using the keyboard, set a value for minutes that is one minute greater than the current time shown by `ctlAlarmClock`.</span></span>  
  
     <span data-ttu-id="43fcc-300">Uyarı ayar için zaman gösterilen `lblTest`.</span><span class="sxs-lookup"><span data-stu-id="43fcc-300">The time for the alarm setting is shown in `lblTest`.</span></span> <span data-ttu-id="43fcc-301">Uyarı ayarını zaman ulaşmak görüntülenen saat için bekleyin.</span><span class="sxs-lookup"><span data-stu-id="43fcc-301">Wait for the displayed time to reach the alarm setting time.</span></span> <span data-ttu-id="43fcc-302">Görüntülenen tarihten uyarı ayarlanan saate ulaştığında bir bip sesi ve `lblAlarm` flash.</span><span class="sxs-lookup"><span data-stu-id="43fcc-302">When the displayed time reaches the time to which the alarm is set, the beep will sound and `lblAlarm` will flash.</span></span>  
  
18. <span data-ttu-id="43fcc-303">Alarmın tıklatarak açın `lblAlarm`.</span><span class="sxs-lookup"><span data-stu-id="43fcc-303">Turn off the alarm by clicking `lblAlarm`.</span></span> <span data-ttu-id="43fcc-304">Uyarı artık sıfırlayabilir.</span><span class="sxs-lookup"><span data-stu-id="43fcc-304">You may now reset the alarm.</span></span>  
  
     <span data-ttu-id="43fcc-305">Bu izlenecek yol, bir dizi temel kavramları kapsamında.</span><span class="sxs-lookup"><span data-stu-id="43fcc-305">This walkthrough has covered a number of key concepts.</span></span> <span data-ttu-id="43fcc-306">Bileşik Denetim kapsayıcıya denetimleri ve Bileşenleri'ni birleştirerek bileşik denetim oluşturulacağını öğrendiniz.</span><span class="sxs-lookup"><span data-stu-id="43fcc-306">You have learned to create a composite control by combining controls and components into a composite control container.</span></span> <span data-ttu-id="43fcc-307">Özellikleri denetiminize eklemek ve özel işlevselliği uygulamak üzere kod yazmak için öğrendiniz.</span><span class="sxs-lookup"><span data-stu-id="43fcc-307">You have learned to add properties to your control, and to write code to implement custom functionality.</span></span> <span data-ttu-id="43fcc-308">Son bölümde, devralma yoluyla belirli bir bileşik denetim işlevlerini genişletmek ve bu yöntemi geçersiz kılarak konak yöntemleri işlevlerini değiştirmek için öğrendiniz.</span><span class="sxs-lookup"><span data-stu-id="43fcc-308">In the last section, you learned to extend the functionality of a given composite control through inheritance, and to alter the functionality of host methods by overriding those methods.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43fcc-309">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="43fcc-309">See also</span></span>
- [<span data-ttu-id="43fcc-310">Özel Denetim Çeşitleri</span><span class="sxs-lookup"><span data-stu-id="43fcc-310">Varieties of Custom Controls</span></span>](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)
- [<span data-ttu-id="43fcc-311">Nasıl yapılır: Bileşik denetimler yazma</span><span class="sxs-lookup"><span data-stu-id="43fcc-311">How to: Author Composite Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-author-composite-controls.md)
- [<span data-ttu-id="43fcc-312">Nasıl yapılır: Bir denetimi görüntüleme araç kutusu öğelerini Seç iletişim kutusu</span><span class="sxs-lookup"><span data-stu-id="43fcc-312">How to: Display a Control in the Choose Toolbox Items Dialog Box</span></span>](../../../../docs/framework/winforms/controls/how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)
