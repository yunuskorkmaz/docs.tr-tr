---
title: 'İzlenecek yol: Visual Basic İle Bileşik Denetim Yazma'
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
ms.openlocfilehash: cb54ef372e6da551b95f1edf61e3844b9dcba4c7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69950036"
---
# <a name="walkthrough-authoring-a-composite-control-with-visual-basic"></a><span data-ttu-id="f86c0-102">İzlenecek yol: Visual Basic İle Bileşik Denetim Yazma</span><span class="sxs-lookup"><span data-stu-id="f86c0-102">Walkthrough: Authoring a Composite Control with Visual Basic</span></span>
<span data-ttu-id="f86c0-103">Bileşik denetimler, özel grafik arabirimlerinin oluşturulup yeniden kullanılabilmesi için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="f86c0-103">Composite controls provide a means by which custom graphical interfaces can be created and reused.</span></span> <span data-ttu-id="f86c0-104">Bileşik denetim temelde görsel temsili olan bir bileşendir.</span><span class="sxs-lookup"><span data-stu-id="f86c0-104">A composite control is essentially a component with a visual representation.</span></span> <span data-ttu-id="f86c0-105">Bu nedenle, Kullanıcı girişini doğrulayarak, görüntü özelliklerini değiştirerek veya yazar için gereken diğer görevleri gerçekleştirerek işlevselliği genişletebilen bir veya daha fazla Windows Forms denetimi, bileşeni veya kod bloklarında bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="f86c0-105">As such, it might consist of one or more Windows Forms controls, components, or blocks of code that can extend functionality by validating user input, modifying display properties, or performing other tasks required by the author.</span></span> <span data-ttu-id="f86c0-106">Bileşik denetimler Windows Forms diğer denetimlerle aynı şekilde yerleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="f86c0-106">Composite controls can be placed on Windows Forms in the same manner as other controls.</span></span> <span data-ttu-id="f86c0-107">Bu izlenecek yolun ilk bölümünde adlı `ctlClock`basit bir bileşik denetim oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="f86c0-107">In the first part of this walkthrough, you create a simple composite control called `ctlClock`.</span></span> <span data-ttu-id="f86c0-108">İzlenecek yolun ikinci bölümünde, devralma `ctlClock` ile işlevlerini genişletebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f86c0-108">In the second part of the walkthrough, you extend the functionality of `ctlClock` through inheritance.</span></span>

## <a name="creating-the-project"></a><span data-ttu-id="f86c0-109">Projeyi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="f86c0-109">Creating the Project</span></span>
 <span data-ttu-id="f86c0-110">Yeni bir proje oluşturduğunuzda, kök ad alanı, derleme adı ve proje adını ayarlamak için adını belirtin ve varsayılan bileşenin doğru ad alanında yer aldığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="f86c0-110">When you create a new project, you specify its name to set the root namespace, assembly name, and project name, and ensure that the default component will be in the correct namespace.</span></span>

### <a name="to-create-the-ctlclocklib-control-library-and-the-ctlclock-control"></a><span data-ttu-id="f86c0-111">CtlClockLib denetim kitaplığını ve ctlClock denetimini oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="f86c0-111">To create the ctlClockLib control library and the ctlClock control</span></span>

1. <span data-ttu-id="f86c0-112">**Dosya** menüsünde, **Yeni**' nin üzerine gelin ve ardından **Proje** ' ye tıklayarak **Yeni proje** iletişim kutusunu açın.</span><span class="sxs-lookup"><span data-stu-id="f86c0-112">On the **File** menu, point to **New**, and then click **Project** to open the **New Project** dialog box.</span></span>

2. <span data-ttu-id="f86c0-113">Visual Basic projeler listesinden **Windows Denetim Kitaplığı** proje şablonunu seçin, `ctlClockLib` **ad** kutusuna yazın ve ardından **Tamam**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="f86c0-113">From the list of Visual Basic projects, select the **Windows Control Library** project template, type `ctlClockLib` in the **Name** box, and then click **OK**.</span></span>

     <span data-ttu-id="f86c0-114">Proje adı `ctlClockLib`, varsayılan olarak kök ad alanına da atanır.</span><span class="sxs-lookup"><span data-stu-id="f86c0-114">The project name, `ctlClockLib`, is also assigned to the root namespace by default.</span></span> <span data-ttu-id="f86c0-115">Kök ad alanı, derlemedeki bileşenlerin adlarını nitelemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f86c0-115">The root namespace is used to qualify the names of components in the assembly.</span></span> <span data-ttu-id="f86c0-116">Örneğin, iki derleme adlı `ctlClock`bileşenler içeriyorsa, `ctlClock` bileşenini kullanarak`ctlClockLib.ctlClock.`</span><span class="sxs-lookup"><span data-stu-id="f86c0-116">For example, if two assemblies provide components named `ctlClock`, you can specify your `ctlClock` component using `ctlClockLib.ctlClock.`</span></span>

3. <span data-ttu-id="f86c0-117">Çözüm Gezgini, **UserControl1. vb**öğesine sağ tıklayın ve ardından **Yeniden Adlandır**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="f86c0-117">In Solution Explorer, right-click **UserControl1.vb**, and then click **Rename**.</span></span> <span data-ttu-id="f86c0-118">Dosya adını olarak `ctlClock.vb`değiştirin.</span><span class="sxs-lookup"><span data-stu-id="f86c0-118">Change the file name to `ctlClock.vb`.</span></span> <span data-ttu-id="f86c0-119">"UserControl1" kod öğesiyle tüm başvuruları yeniden adlandırmak isteyip istemediğiniz sorulduğunda **Evet** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="f86c0-119">Click the **Yes** button when you are asked if you want to rename all references to the code element "UserControl1".</span></span>

    > [!NOTE]
    > <span data-ttu-id="f86c0-120">Varsayılan olarak, bileşik bir denetim sistem tarafından sunulan <xref:System.Windows.Forms.UserControl> sınıftan devralınır.</span><span class="sxs-lookup"><span data-stu-id="f86c0-120">By default, a composite control inherits from the <xref:System.Windows.Forms.UserControl> class provided by the system.</span></span> <span data-ttu-id="f86c0-121"><xref:System.Windows.Forms.UserControl> Sınıfı, tüm bileşik denetimlerin gerektirdiği işlevselliği sağlar ve standart yöntemler ve özellikler uygular.</span><span class="sxs-lookup"><span data-stu-id="f86c0-121">The <xref:System.Windows.Forms.UserControl> class provides functionality required by all composite controls, and implements standard methods and properties.</span></span>

4. <span data-ttu-id="f86c0-122">Projeyi kaydetmek için **Dosya** menüsünde **Tümünü Kaydet** ' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="f86c0-122">On the **File** menu, click **Save All** to save the project.</span></span>

## <a name="adding-windows-controls-and-components-to-the-composite-control"></a><span data-ttu-id="f86c0-123">Bileşik denetime Windows denetimleri ve bileşenleri ekleme</span><span class="sxs-lookup"><span data-stu-id="f86c0-123">Adding Windows Controls and Components to the Composite Control</span></span>
 <span data-ttu-id="f86c0-124">Görsel arabirim, bileşik denetiminizin temel bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="f86c0-124">A visual interface is an essential part of your composite control.</span></span> <span data-ttu-id="f86c0-125">Bu görsel arabirim, tasarımcı yüzeyine bir veya daha fazla Windows denetimi eklenerek uygulanır.</span><span class="sxs-lookup"><span data-stu-id="f86c0-125">This visual interface is implemented by the addition of one or more Windows controls to the designer surface.</span></span> <span data-ttu-id="f86c0-126">Aşağıdaki gösteride, Windows denetimlerini bileşik denetiminizle birleştirirsiniz ve işlevselliği uygulamak için kod yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f86c0-126">In the following demonstration, you will incorporate Windows controls into your composite control and write code to implement functionality.</span></span>

### <a name="to-add-a-label-and-a-timer-to-your-composite-control"></a><span data-ttu-id="f86c0-127">Bileşik denetilemenize bir etiket ve süreölçer eklemek için</span><span class="sxs-lookup"><span data-stu-id="f86c0-127">To add a Label and a Timer to your composite control</span></span>

1. <span data-ttu-id="f86c0-128">Çözüm Gezgini, **ctlClock. vb**öğesine sağ tıklayın ve ardından **tasarımcıyı görüntüle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="f86c0-128">In Solution Explorer, right-click **ctlClock.vb**, and then click **View Designer**.</span></span>

2. <span data-ttu-id="f86c0-129">Araç kutusunda **ortak denetimler** düğümünü genişletin ve ardından **etiket**' e çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="f86c0-129">In the Toolbox, expand the **Common Controls** node, and then double-click **Label**.</span></span>

     <span data-ttu-id="f86c0-130">Tasarımcı <xref:System.Windows.Forms.Label> yüzeyinde denetimciyle adlandırılmış `Label1` bir denetim eklenir.</span><span class="sxs-lookup"><span data-stu-id="f86c0-130">A <xref:System.Windows.Forms.Label> control named `Label1` is added to your control on the designer surface.</span></span>

3. <span data-ttu-id="f86c0-131">Tasarımcıda **Label1**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="f86c0-131">In the designer, click **Label1**.</span></span> <span data-ttu-id="f86c0-132">Özellikler penceresi, aşağıdaki özellikleri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="f86c0-132">In the Properties window, set the following properties.</span></span>

    |<span data-ttu-id="f86c0-133">Özellik</span><span class="sxs-lookup"><span data-stu-id="f86c0-133">Property</span></span>|<span data-ttu-id="f86c0-134">Değiştir</span><span class="sxs-lookup"><span data-stu-id="f86c0-134">Change to</span></span>|
    |--------------|---------------|
    |<span data-ttu-id="f86c0-135">**Ad**</span><span class="sxs-lookup"><span data-stu-id="f86c0-135">**Name**</span></span>|`lblDisplay`|
    |<span data-ttu-id="f86c0-136">**Metin**</span><span class="sxs-lookup"><span data-stu-id="f86c0-136">**Text**</span></span>|`(blank space)`|
    |<span data-ttu-id="f86c0-137">**TextAlign**</span><span class="sxs-lookup"><span data-stu-id="f86c0-137">**TextAlign**</span></span>|`MiddleCenter`|
    |<span data-ttu-id="f86c0-138">**Yazı tipi. boyutu**</span><span class="sxs-lookup"><span data-stu-id="f86c0-138">**Font.Size**</span></span>|`14`|

4. <span data-ttu-id="f86c0-139">**Araç kutusunda**, **Bileşenler** düğümünü genişletin ve ardından **Zamanlayıcı**' ya çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="f86c0-139">In the **Toolbox**, expand the **Components** node, and then double-click **Timer**.</span></span>

     <span data-ttu-id="f86c0-140">Bir <xref:System.Windows.Forms.Timer> bileşen olduğundan, çalışma zamanında görsel temsili yoktur.</span><span class="sxs-lookup"><span data-stu-id="f86c0-140">Because a <xref:System.Windows.Forms.Timer> is a component, it has no visual representation at run time.</span></span> <span data-ttu-id="f86c0-141">Bu nedenle, tasarımcı yüzeyindeki denetimlerde görünmez, ancak bileşen tasarımcısında (tasarımcı yüzeyinin altındaki bir tepsi) değil.</span><span class="sxs-lookup"><span data-stu-id="f86c0-141">Therefore, it does not appear with the controls on the designer surface, but rather in the Component Designer (a tray at the bottom of the designer surface).</span></span>

5. <span data-ttu-id="f86c0-142">Bileşen tasarımcısında, **Süreölçer1**' a tıklayın ve ardından <xref:System.Windows.Forms.Timer.Interval%2A> <xref:System.Windows.Forms.Timer.Enabled%2A> özelliğini `1000` ve özelliğini olarak `True`ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="f86c0-142">In the Component Designer, click **Timer1**, and then set the <xref:System.Windows.Forms.Timer.Interval%2A> property to `1000` and the <xref:System.Windows.Forms.Timer.Enabled%2A> property to `True`.</span></span>

     <span data-ttu-id="f86c0-143"><xref:System.Windows.Forms.Timer.Interval%2A> Özelliği, süreölçer bileşeni işaret eden sıklığı denetler.</span><span class="sxs-lookup"><span data-stu-id="f86c0-143">The <xref:System.Windows.Forms.Timer.Interval%2A> property controls the frequency with which the timer component ticks.</span></span> <span data-ttu-id="f86c0-144">Her zaman `Timer1` Tick, `Timer1_Tick` olaydaki kodu çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="f86c0-144">Each time `Timer1` ticks, it runs the code in the `Timer1_Tick` event.</span></span> <span data-ttu-id="f86c0-145">Aralık, zaman işaretleri arasındaki milisaniye sayısını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f86c0-145">The interval represents the number of milliseconds between ticks.</span></span>

6. <span data-ttu-id="f86c0-146">Bileşen tasarımcısında, için **Süreölçer1** öğesine çift tıklayarak için `Timer1_Tick` `ctlClock`olayına gidin.</span><span class="sxs-lookup"><span data-stu-id="f86c0-146">In the Component Designer, double-click **Timer1** to go to the `Timer1_Tick` event for `ctlClock`.</span></span>

7. <span data-ttu-id="f86c0-147">Kodu aşağıdaki kod örneğine benzer olacak şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="f86c0-147">Modify the code so that it resembles the following code sample.</span></span> <span data-ttu-id="f86c0-148">Erişim değiştiricisini ' dan `Private` `Protected`' a değiştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="f86c0-148">Be sure to change the access modifier from `Private` to `Protected`.</span></span>

    ```vb
    Protected Sub Timer1_Tick(ByVal sender As Object, ByVal e As _
        System.EventArgs) Handles Timer1.Tick
        ' Causes the label to display the current time.
        lblDisplay.Text = Format(Now, "hh:mm:ss")
    End Sub
    ```

     <span data-ttu-id="f86c0-149">Bu kod, geçerli saatin ' de `lblDisplay`görüntülenmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="f86c0-149">This code will cause the current time to be shown in `lblDisplay`.</span></span> <span data-ttu-id="f86c0-150">Aralığı `Timer1` olarak ayarlandığı için `1000`bu olay her bin milisaniyede bir gerçekleşeceğinden, bu nedenle her saniye geçerli saati güncelliyor.</span><span class="sxs-lookup"><span data-stu-id="f86c0-150">Because the interval of `Timer1` was set to `1000`, this event will occur every thousand milliseconds, thus updating the current time every second.</span></span>

8. <span data-ttu-id="f86c0-151">Yöntemi geçersiz kılınabilir olacak şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="f86c0-151">Modify the method to be overridable.</span></span> <span data-ttu-id="f86c0-152">Daha fazla bilgi için aşağıdaki "Kullanıcı denetiminden devralma" bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="f86c0-152">For more information, see the "Inheriting from a User Control" section below.</span></span>

    ```vb
    Protected Overridable Sub Timer1_Tick(ByVal sender As Object, ByVal _
        e As System.EventArgs) Handles Timer1.Tick
    ```

9. <span data-ttu-id="f86c0-153">Projeyi kaydetmek için **Dosya** menüsünde **Tümünü Kaydet** ' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="f86c0-153">On the **File** menu, click **Save All** to save the project.</span></span>

## <a name="adding-properties-to-the-composite-control"></a><span data-ttu-id="f86c0-154">Bileşik denetime özellikler ekleme</span><span class="sxs-lookup"><span data-stu-id="f86c0-154">Adding Properties to the Composite Control</span></span>
 <span data-ttu-id="f86c0-155">Saat denetiminiz artık, her biri <xref:System.Windows.Forms.Label> kendi kendine ait <xref:System.Windows.Forms.Timer> özellikler kümesiyle birlikte bir denetimi ve bileşeni kapsüller.</span><span class="sxs-lookup"><span data-stu-id="f86c0-155">Your clock control now encapsulates a <xref:System.Windows.Forms.Label> control and a <xref:System.Windows.Forms.Timer> component, each with its own set of inherent properties.</span></span> <span data-ttu-id="f86c0-156">Bu denetimlerin tek tek özelliklerine denetiminizin sonraki kullanıcıları tarafından erişilemese de, uygun kod bloklarını yazarak özel özellikler oluşturabilir ve kullanıma sunabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f86c0-156">While the individual properties of these controls will not be accessible to subsequent users of your control, you can create and expose custom properties by writing the appropriate blocks of code.</span></span> <span data-ttu-id="f86c0-157">Aşağıdaki yordamda, denetime, kullanıcının arka plan ve metin rengini değiştirmesini sağlayan özellikler ekleyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="f86c0-157">In the following procedure, you will add properties to your control that enable the user to change the color of the background and text.</span></span>

### <a name="to-add-a-property-to-your-composite-control"></a><span data-ttu-id="f86c0-158">Bileşik denetimi bir özellik eklemek için</span><span class="sxs-lookup"><span data-stu-id="f86c0-158">To add a property to your composite control</span></span>

1. <span data-ttu-id="f86c0-159">Çözüm Gezgini, **ctlClock. vb**öğesine sağ tıklayın ve ardından **kodu görüntüle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="f86c0-159">In Solution Explorer, right-click **ctlClock.vb**, and then click **View Code**.</span></span>

     <span data-ttu-id="f86c0-160">Denetiminizin kod Düzenleyicisi açılır.</span><span class="sxs-lookup"><span data-stu-id="f86c0-160">The Code Editor for your control opens.</span></span>

2. <span data-ttu-id="f86c0-161">`Public Class ctlClock` İfadesini bulun.</span><span class="sxs-lookup"><span data-stu-id="f86c0-161">Locate the `Public Class ctlClock` statement.</span></span> <span data-ttu-id="f86c0-162">Bunun altına aşağıdaki kodu yazın.</span><span class="sxs-lookup"><span data-stu-id="f86c0-162">Beneath it, type the following code.</span></span>

    ```vb
    Private colFColor as Color
    Private colBColor as Color
    ```

     <span data-ttu-id="f86c0-163">Bu deyimler, oluşturmak üzere olduğunuz özelliklerin değerlerini depolamak için kullanacağınız özel değişkenleri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f86c0-163">These statements create the private variables that you will use to store the values for the properties you are about to create.</span></span>

3. <span data-ttu-id="f86c0-164">2\. adımdaki değişken bildirimlerinin altına aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f86c0-164">Insert the following code beneath the variable declarations from step 2.</span></span>

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

     <span data-ttu-id="f86c0-165">Yukarıdaki kod iki özel özellik `ClockForeColor` yapar ve `ClockBackColor`, `Property` bu denetimin sonraki kullanıcıları tarafından bu şekilde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f86c0-165">The preceding code makes two custom properties, `ClockForeColor` and `ClockBackColor`, available to subsequent users of this control by invoking the `Property` statement.</span></span> <span data-ttu-id="f86c0-166">`Get` Ve`Set` deyimleri, özellik değerinin depolanmasını ve alınmasını, ayrıca özelliğine uygun işlevselliği uygulamak için de kod sağlar.</span><span class="sxs-lookup"><span data-stu-id="f86c0-166">The `Get` and `Set` statements provide for storage and retrieval of the property value, as well as code to implement functionality appropriate to the property.</span></span>

4. <span data-ttu-id="f86c0-167">Projeyi kaydetmek için **Dosya** menüsünde **Tümünü Kaydet** ' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="f86c0-167">On the **File** menu, click **Save All** to save the project.</span></span>

## <a name="testing-the-control"></a><span data-ttu-id="f86c0-168">Denetimi test etme</span><span class="sxs-lookup"><span data-stu-id="f86c0-168">Testing the Control</span></span>
 <span data-ttu-id="f86c0-169">Denetimler tek başına projeler değildir; Bunlar bir kapsayıcıda barındırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f86c0-169">Controls are not stand-alone projects; they must be hosted in a container.</span></span> <span data-ttu-id="f86c0-170">Denetiminizin çalışma zamanı davranışını test edin ve özelliklerini **UserControl Test kapsayıcısı**ile çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="f86c0-170">Test your control's run-time behavior and exercise its properties with the **UserControl Test Container**.</span></span> <span data-ttu-id="f86c0-171">Daha fazla bilgi için [nasıl yapılır: UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md)'un çalışma zamanı davranışını test edin.</span><span class="sxs-lookup"><span data-stu-id="f86c0-171">For more information, see [How to: Test the Run-Time Behavior of a UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>

### <a name="to-test-your-control"></a><span data-ttu-id="f86c0-172">Denetiminizi test etmek için</span><span class="sxs-lookup"><span data-stu-id="f86c0-172">To test your control</span></span>

1. <span data-ttu-id="f86c0-173">Projeyi derlemek için F5 tuşuna basın ve denetimi **UserControl Test kapsayıcısında**çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="f86c0-173">Press F5 to build the project and run your control in the **UserControl Test Container**.</span></span>

2. <span data-ttu-id="f86c0-174">Test kapsayıcısının özellik kılavuzunda, `ClockBackColor` özelliğini seçin ve ardından renk paletini göstermek için aşağı açılan oka tıklayın.</span><span class="sxs-lookup"><span data-stu-id="f86c0-174">In the test container's property grid, select the `ClockBackColor` property, and then click the drop-down arrow to display the color palette.</span></span>

3. <span data-ttu-id="f86c0-175">Tıklayarak bir renk seçin.</span><span class="sxs-lookup"><span data-stu-id="f86c0-175">Choose a color by clicking it.</span></span>

     <span data-ttu-id="f86c0-176">Denetiminizin arka plan rengi, seçtiğiniz renge değişir.</span><span class="sxs-lookup"><span data-stu-id="f86c0-176">The background color of your control changes to the color you selected.</span></span>

4. <span data-ttu-id="f86c0-177">`ClockForeColor` Özelliğin beklendiği gibi çalıştığını doğrulamak için benzer bir olay dizisi kullanın.</span><span class="sxs-lookup"><span data-stu-id="f86c0-177">Use a similar sequence of events to verify that the `ClockForeColor` property is functioning as expected.</span></span>

5. <span data-ttu-id="f86c0-178">**UserControl Test kapsayıcısını**kapatmak için **Kapat** ' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="f86c0-178">Click **Close** to close the **UserControl Test Container**.</span></span>

     <span data-ttu-id="f86c0-179">Bu bölümde ve önceki bölümlerde, bileşik denetim biçiminde özel işlevsellik sağlamak için bileşenlerin ve Windows denetimlerinin kod ve paketleme ile nasıl birleştirilebileceği gördünüz.</span><span class="sxs-lookup"><span data-stu-id="f86c0-179">In this section and the preceding sections, you have seen how components and Windows controls can be combined with code and packaging to provide custom functionality in the form of a composite control.</span></span> <span data-ttu-id="f86c0-180">Birleşik denetidiklerinizin özelliklerini açığa çıkarmak ve tamamlandıktan sonra denetiminizi test etmek için öğrendiniz.</span><span class="sxs-lookup"><span data-stu-id="f86c0-180">You have learned to expose properties in your composite control, and how to test your control after it is complete.</span></span> <span data-ttu-id="f86c0-181">Sonraki bölümde, temel olarak kullanarak `ctlClock` devralınmış bir bileşik denetim oluşturmayı öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="f86c0-181">In the next section you will learn how to construct an inherited composite control using `ctlClock` as a base.</span></span>

## <a name="inheriting-from-a-composite-control"></a><span data-ttu-id="f86c0-182">Bileşik denetimden devralma</span><span class="sxs-lookup"><span data-stu-id="f86c0-182">Inheriting from a Composite Control</span></span>
 <span data-ttu-id="f86c0-183">Önceki bölümlerde, Windows denetimlerini, bileşenleri ve kodu yeniden kullanılabilir bileşik denetimlere nasıl birleştirebileceğinizi öğrendiniz.</span><span class="sxs-lookup"><span data-stu-id="f86c0-183">In the previous sections, you learned how to combine Windows controls, components, and code into reusable composite controls.</span></span> <span data-ttu-id="f86c0-184">Bileşik denetiminiz artık diğer denetimlerin derlenme temeli olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f86c0-184">Your composite control can now be used as a base upon which other controls can be built.</span></span> <span data-ttu-id="f86c0-185">Temel sınıftan bir sınıfın türeme işlemi *Devralma*olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="f86c0-185">The process of deriving a class from a base class is called *inheritance*.</span></span> <span data-ttu-id="f86c0-186">Bu bölümde, adlı `ctlAlarmClock`bir bileşik denetim oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="f86c0-186">In this section, you will create a composite control called `ctlAlarmClock`.</span></span> <span data-ttu-id="f86c0-187">Bu denetim, `ctlClock`üst denetiminden türetilecektir.</span><span class="sxs-lookup"><span data-stu-id="f86c0-187">This control will be derived from its parent control, `ctlClock`.</span></span> <span data-ttu-id="f86c0-188">Üst yöntemleri geçersiz kılarak ve yeni yöntemler ve `ctlClock` özellikler ekleyerek işlevselliğini genişletmeyi öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="f86c0-188">You will learn to extend the functionality of `ctlClock` by overriding parent methods and adding new methods and properties.</span></span>

 <span data-ttu-id="f86c0-189">Devralınan bir denetim oluşturmanın ilk adımı onu üst öğesinden türemektir.</span><span class="sxs-lookup"><span data-stu-id="f86c0-189">The first step in creating an inherited control is to derive it from its parent.</span></span> <span data-ttu-id="f86c0-190">Bu eylem, üst denetimin tüm özelliklerine, yöntemlerine ve grafiksel özelliklerine sahip yeni bir denetim oluşturur, ancak yeni veya değiştirilmiş işlevselliğin eklenmesi için temel olarak da davranabilir.</span><span class="sxs-lookup"><span data-stu-id="f86c0-190">This action creates a new control that has all of the properties, methods, and graphical characteristics of the parent control, but can also act as a base for the addition of new or modified functionality.</span></span>

### <a name="to-create-the-inherited-control"></a><span data-ttu-id="f86c0-191">Devralınan denetimi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="f86c0-191">To create the inherited control</span></span>

1. <span data-ttu-id="f86c0-192">Çözüm Gezgini ' de, **ctlClockLib**' a sağ tıklayın, **Ekle**' nin üzerine gelin ve **Kullanıcı denetimi**' ne tıklayın.</span><span class="sxs-lookup"><span data-stu-id="f86c0-192">In Solution Explorer, right-click **ctlClockLib**, point to **Add**, and then click **User Control**.</span></span>

     <span data-ttu-id="f86c0-193">**Yeni Öğe Ekle** iletişim kutusu açılır.</span><span class="sxs-lookup"><span data-stu-id="f86c0-193">The **Add New Item** dialog box opens.</span></span>

2. <span data-ttu-id="f86c0-194">**Devralınan Kullanıcı denetimi** şablonunu seçin.</span><span class="sxs-lookup"><span data-stu-id="f86c0-194">Select the **Inherited User Control** template.</span></span>

3. <span data-ttu-id="f86c0-195">**Ad** kutusuna yazın `ctlAlarmClock.vb`ve ardından **Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="f86c0-195">In the **Name** box, type `ctlAlarmClock.vb`, and then click **Add**.</span></span>

     <span data-ttu-id="f86c0-196">**Devralma Seçicisi** iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="f86c0-196">The **Inheritance Picker** dialog box appears.</span></span>

4. <span data-ttu-id="f86c0-197">**Bileşen adı**altında **ctlClock**' ye çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="f86c0-197">Under **Component Name**, double-click **ctlClock**.</span></span>

5. <span data-ttu-id="f86c0-198">Çözüm Gezgini, geçerli projelere göz atabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f86c0-198">In Solution Explorer, browse through the current projects.</span></span>

    > [!NOTE]
    > <span data-ttu-id="f86c0-199">Geçerli projeye **ctlAlarmClock. vb** adlı bir dosya eklendi.</span><span class="sxs-lookup"><span data-stu-id="f86c0-199">A file called **ctlAlarmClock.vb** has been added to the current project.</span></span>

### <a name="adding-the-alarm-properties"></a><span data-ttu-id="f86c0-200">Alarm özelliklerini ekleme</span><span class="sxs-lookup"><span data-stu-id="f86c0-200">Adding the Alarm Properties</span></span>
 <span data-ttu-id="f86c0-201">Özellikler, devralınan bir denetime, Birleşik bir denetime eklendikçe aynı şekilde eklenir.</span><span class="sxs-lookup"><span data-stu-id="f86c0-201">Properties are added to an inherited control in the same way they are added to a composite control.</span></span> <span data-ttu-id="f86c0-202">Şimdi, denetimidir için iki özellik eklemek üzere özellik bildirimi söz dizimini kullanacaksınız: `AlarmTime`bu, uyarının bitiş tarihini ve saatini depolayan ve `AlarmSet`alarmın ayarlanmış olup olmadığını belirtecektir.</span><span class="sxs-lookup"><span data-stu-id="f86c0-202">You will now use the property declaration syntax to add two properties to your control: `AlarmTime`, which will store the value of the date and time the alarm is to go off, and `AlarmSet`, which will indicate whether the alarm is set.</span></span>

#### <a name="to-add-properties-to-your-composite-control"></a><span data-ttu-id="f86c0-203">Bileşik denetimi özellikler eklemek için</span><span class="sxs-lookup"><span data-stu-id="f86c0-203">To add properties to your composite control</span></span>

1. <span data-ttu-id="f86c0-204">Çözüm Gezgini ' de, **ctlAlarmClock**' a sağ tıklayın ve ardından **kodu görüntüle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="f86c0-204">In Solution Explorer, right-click **ctlAlarmClock**, and then click **View Code**.</span></span>

2. <span data-ttu-id="f86c0-205">Olarak `Public Class ctlAlarmClock`görünen ctlAlarmClock denetimi için sınıf bildirimini bulun.</span><span class="sxs-lookup"><span data-stu-id="f86c0-205">Locate the class declaration for the ctlAlarmClock control, which appears as `Public Class ctlAlarmClock`.</span></span>  <span data-ttu-id="f86c0-206">Sınıf bildiriminde aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f86c0-206">In the class declaration, insert the following code.</span></span>

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

### <a name="adding-to-the-graphical-interface-of-the-control"></a><span data-ttu-id="f86c0-207">Denetimin grafik arabirimine ekleme</span><span class="sxs-lookup"><span data-stu-id="f86c0-207">Adding to the Graphical Interface of the Control</span></span>
 <span data-ttu-id="f86c0-208">Devralınan denetiminizin devraldığı denetimle özdeş bir görsel arabirimi vardır.</span><span class="sxs-lookup"><span data-stu-id="f86c0-208">Your inherited control has a visual interface that is identical to the control it inherits from.</span></span> <span data-ttu-id="f86c0-209">Kendi üst denetimiyle aynı bileşen denetimlerine sahip olur, ancak yapısal denetimlerin özellikleri özellikle gösterilmedikleri sürece kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="f86c0-209">It possesses the same constituent controls as its parent control, but the properties of the constituent controls will not be available unless they were specifically exposed.</span></span> <span data-ttu-id="f86c0-210">Devralınan bir bileşik denetimin grafik arabirimine, herhangi bir bileşik denetime ekleyeceğiniz şekilde ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f86c0-210">You may add to the graphical interface of an inherited composite control in the same manner as you would add to any composite control.</span></span> <span data-ttu-id="f86c0-211">Alarm saatinizin görsel arabirimine eklemeye devam etmek için, alarm bir işlem olduğunda Flash olacak bir etiket denetimi ekleyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="f86c0-211">To continue adding to your alarm clock's visual interface, you will add a label control that will flash when the alarm is sounding.</span></span>

#### <a name="to-add-the-label-control"></a><span data-ttu-id="f86c0-212">Etiket denetimi eklemek için</span><span class="sxs-lookup"><span data-stu-id="f86c0-212">To add the label control</span></span>

1. <span data-ttu-id="f86c0-213">Çözüm Gezgini ' de, **ctlAlarmClock**' a sağ tıklayın ve **Tasarımcı görüntüle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="f86c0-213">In Solution Explorer, right-click **ctlAlarmClock**, and click **View Designer**.</span></span>

     <span data-ttu-id="f86c0-214">İçin `ctlAlarmClock` tasarımcı ana pencerede açılır.</span><span class="sxs-lookup"><span data-stu-id="f86c0-214">The designer for `ctlAlarmClock` opens in the main window.</span></span>

2. <span data-ttu-id="f86c0-215">( `lblDisplay` Denetimin görüntüleme bölümü) öğesine tıklayın ve Özellikler penceresi görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="f86c0-215">Click `lblDisplay` (the display portion of the control), and view the Properties window.</span></span>

    > [!NOTE]
    > <span data-ttu-id="f86c0-216">Tüm özellikler görüntülenirken, soluk olurlar.</span><span class="sxs-lookup"><span data-stu-id="f86c0-216">While all the properties are displayed, they are dimmed.</span></span> <span data-ttu-id="f86c0-217">Bu özelliklerin yerel `lblDisplay` olduğunu ve Özellikler penceresi değiştirilemeyeceğini veya erişilmeyeceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="f86c0-217">This indicates that these properties are native to `lblDisplay` and cannot be modified or accessed in the Properties window.</span></span> <span data-ttu-id="f86c0-218">Varsayılan olarak, bileşik denetimde `Private`bulunan denetimler ve özellikleri herhangi bir şekilde erişilebilir değildir.</span><span class="sxs-lookup"><span data-stu-id="f86c0-218">By default, controls contained in a composite control are `Private`, and their properties are not accessible by any means.</span></span>

    > [!NOTE]
    > <span data-ttu-id="f86c0-219">Bileşik denetiminizin sonraki kullanıcılarının iç denetimlerine erişimi olmasını istiyorsanız, veya `Public` `Protected`olarak bildirin.</span><span class="sxs-lookup"><span data-stu-id="f86c0-219">If you want subsequent users of your composite control to have access to its internal controls, declare them as `Public` or `Protected`.</span></span> <span data-ttu-id="f86c0-220">Bu, uygun kodu kullanarak bileşik denetilinizin içindeki denetimlerin özelliklerini ayarlamanıza ve değiştirmenize izin verir.</span><span class="sxs-lookup"><span data-stu-id="f86c0-220">This will allow you to set and modify properties of controls contained within your composite control by using the appropriate code.</span></span>

3. <span data-ttu-id="f86c0-221">Bileşik denetimi bir <xref:System.Windows.Forms.Label> denetim ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f86c0-221">Add a <xref:System.Windows.Forms.Label> control to your composite control.</span></span>

4. <span data-ttu-id="f86c0-222">Fareyi kullanarak <xref:System.Windows.Forms.Label> denetimi, ekran kutusunun hemen altına sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="f86c0-222">Using the mouse, drag the <xref:System.Windows.Forms.Label> control immediately beneath the display box.</span></span> <span data-ttu-id="f86c0-223">Özellikler penceresi, aşağıdaki özellikleri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="f86c0-223">In the Properties window, set the following properties.</span></span>

    |<span data-ttu-id="f86c0-224">Özellik</span><span class="sxs-lookup"><span data-stu-id="f86c0-224">Property</span></span>|<span data-ttu-id="f86c0-225">Ayar</span><span class="sxs-lookup"><span data-stu-id="f86c0-225">Setting</span></span>|
    |--------------|-------------|
    |<span data-ttu-id="f86c0-226">**Ad**</span><span class="sxs-lookup"><span data-stu-id="f86c0-226">**Name**</span></span>|`lblAlarm`|
    |<span data-ttu-id="f86c0-227">**Metin**</span><span class="sxs-lookup"><span data-stu-id="f86c0-227">**Text**</span></span>|<span data-ttu-id="f86c0-228">**Alarm!**</span><span class="sxs-lookup"><span data-stu-id="f86c0-228">**Alarm!**</span></span>|
    |<span data-ttu-id="f86c0-229">**TextAlign**</span><span class="sxs-lookup"><span data-stu-id="f86c0-229">**TextAlign**</span></span>|`MiddleCenter`|
    |<span data-ttu-id="f86c0-230">**Görüne**</span><span class="sxs-lookup"><span data-stu-id="f86c0-230">**Visible**</span></span>|`False`|

### <a name="adding-the-alarm-functionality"></a><span data-ttu-id="f86c0-231">Alarm Işlevlerini ekleme</span><span class="sxs-lookup"><span data-stu-id="f86c0-231">Adding the Alarm Functionality</span></span>
 <span data-ttu-id="f86c0-232">Önceki yordamlarda, bileşik denetiminizdeki alarm işlevselliğini etkinleştiren Özellikler ve bir denetim eklediniz.</span><span class="sxs-lookup"><span data-stu-id="f86c0-232">In the previous procedures, you added properties and a control that will enable alarm functionality in your composite control.</span></span> <span data-ttu-id="f86c0-233">Bu yordamda, geçerli saati alarm zamanına göre karşılaştırmak için kod ekleyeceksiniz ve aynı ise, bir alarm Sound ve Flash 'a göre yanıp sönecektir.</span><span class="sxs-lookup"><span data-stu-id="f86c0-233">In this procedure, you will add code to compare the current time to the alarm time and, if they are the same, to sound and flash an alarm.</span></span> <span data-ttu-id="f86c0-234">`Timer1_Tick` `ctlAlarmClock` Yöntemini geçersiz kılarak ve buna ek kod ekleyerek, tüm devralınan işlevlerini `ctlClock`korurken özelliğini genişletebilirsiniz. `ctlClock`</span><span class="sxs-lookup"><span data-stu-id="f86c0-234">By overriding the `Timer1_Tick` method of `ctlClock` and adding additional code to it, you will extend the capability of `ctlAlarmClock` while retaining all of the inherent functionality of `ctlClock`.</span></span>

#### <a name="to-override-the-timer1_tick-method-of-ctlclock"></a><span data-ttu-id="f86c0-235">CtlClock Timer1_Tick yöntemini geçersiz kılmak için</span><span class="sxs-lookup"><span data-stu-id="f86c0-235">To override the Timer1_Tick method of ctlClock</span></span>

1. <span data-ttu-id="f86c0-236">Çözüm Gezgini, **ctlAlarmClock. vb**öğesine sağ tıklayın ve ardından **kodu görüntüle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="f86c0-236">In Solution Explorer, right-click **ctlAlarmClock.vb**, and then click **View Code**.</span></span>

2. <span data-ttu-id="f86c0-237">`Private blnAlarmSet As Boolean` İfadesini bulun.</span><span class="sxs-lookup"><span data-stu-id="f86c0-237">Locate the `Private blnAlarmSet As Boolean` statement.</span></span> <span data-ttu-id="f86c0-238">Hemen hemen altına aşağıdaki ifadeyi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f86c0-238">Immediately beneath it, add the following statement.</span></span>

    ```vb
    Dim blnColorTicker as Boolean
    ```

3. <span data-ttu-id="f86c0-239">Sayfanın alt kısmındaki ifadesini bulun. `End Class`</span><span class="sxs-lookup"><span data-stu-id="f86c0-239">Locate the `End Class` statement at the bottom of the page.</span></span> <span data-ttu-id="f86c0-240">`End Class` Deyimden hemen önce aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f86c0-240">Just before the `End Class` statement, add the following code.</span></span>

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

     <span data-ttu-id="f86c0-241">Bu kodun eklenmesi birkaç görevi gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="f86c0-241">The addition of this code accomplishes several tasks.</span></span> <span data-ttu-id="f86c0-242">`Overrides` İfade, denetimi temel denetimden devralınan yöntemin yerine bu yöntemi kullanacak şekilde yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="f86c0-242">The `Overrides` statement directs the control to use this method in place of the method that was inherited from the base control.</span></span> <span data-ttu-id="f86c0-243">Bu yöntem çağrıldığında, `MyBase.Timer1_Tick` ifadeyi çağırarak geçersiz kıldığından, özgün denetimde dahil edilen tüm işlevlerin Bu denetimde yeniden üretildiğinden emin olarak çağrılır.</span><span class="sxs-lookup"><span data-stu-id="f86c0-243">When this method is called, it calls the method it overrides by invoking the `MyBase.Timer1_Tick` statement, ensuring that all of the functionality incorporated in the original control is reproduced in this control.</span></span> <span data-ttu-id="f86c0-244">Daha sonra alarm işlevselliğini birleştirmek için ek kod çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="f86c0-244">It then runs additional code to incorporate the alarm functionality.</span></span> <span data-ttu-id="f86c0-245">Uyarı oluştuğunda yanıp sönen bir etiket denetimi görünür ve duyulabilir bir bip sesi duyacaktır.</span><span class="sxs-lookup"><span data-stu-id="f86c0-245">A flashing label control will appear when the alarm occurs, and an audible beep will be heard.</span></span>

    > [!NOTE]
    > <span data-ttu-id="f86c0-246">Devralınan bir olay işleyicisini geçersiz kıldığından, olayı `Handles` anahtar sözcüğüyle belirtmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="f86c0-246">Because you are overriding an inherited event handler, you do not have to specify the event with the `Handles` keyword.</span></span> <span data-ttu-id="f86c0-247">Olay zaten kullanıma açıldı.</span><span class="sxs-lookup"><span data-stu-id="f86c0-247">The event is already hooked up.</span></span> <span data-ttu-id="f86c0-248">Geçersiz kılmanın tamamı, işleyicinin uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="f86c0-248">All you are overriding is the implementation of the handler.</span></span>

     <span data-ttu-id="f86c0-249">Alarm saati denetiminiz neredeyse tamamlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="f86c0-249">Your alarm clock control is almost complete.</span></span> <span data-ttu-id="f86c0-250">Kalan tek şey, devre dışı bırakmak için bir yol uygulamaktır.</span><span class="sxs-lookup"><span data-stu-id="f86c0-250">The only thing that remains is to implement a way to turn it off.</span></span> <span data-ttu-id="f86c0-251">Bunu yapmak için `lblAlarm_Click` yöntemine kod ekleyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="f86c0-251">To do this, you will add code to the `lblAlarm_Click` method.</span></span>

#### <a name="to-implement-the-shutoff-method"></a><span data-ttu-id="f86c0-252">Shutoff yöntemini uygulamak için</span><span class="sxs-lookup"><span data-stu-id="f86c0-252">To implement the shutoff method</span></span>

1. <span data-ttu-id="f86c0-253">Çözüm Gezgini, **ctlAlarmClock. vb**öğesine sağ tıklayın ve ardından **tasarımcıyı görüntüle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="f86c0-253">In Solution Explorer, right-click **ctlAlarmClock.vb**, and then click **View Designer**.</span></span>

2. <span data-ttu-id="f86c0-254">Tasarımcıda **lblAlarm**öğesine çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="f86c0-254">In the designer, double-click **lblAlarm**.</span></span> <span data-ttu-id="f86c0-255">**Kod Düzenleyicisi** `Private Sub lblAlarm_Click` satıra açılır.</span><span class="sxs-lookup"><span data-stu-id="f86c0-255">The **Code Editor** opens to the `Private Sub lblAlarm_Click` line.</span></span>

3. <span data-ttu-id="f86c0-256">Bu yöntemi, aşağıdaki koda benzer olacak şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="f86c0-256">Modify this method so that it resembles the following code.</span></span>

    ```vb
    Private Sub lblAlarm_Click(ByVal sender As Object, ByVal e As _
     System.EventArgs) Handles lblAlarm.Click
        ' Turns off the alarm.
        AlarmSet = False
        ' Hides the flashing label.
        lblAlarm.Visible = False
    End Sub
    ```

4. <span data-ttu-id="f86c0-257">Projeyi kaydetmek için **Dosya** menüsünde **Tümünü Kaydet** ' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="f86c0-257">On the **File** menu, click **Save All** to save the project.</span></span>

### <a name="using-the-inherited-control-on-a-form"></a><span data-ttu-id="f86c0-258">Bir form üzerinde devralınmış denetimi kullanma</span><span class="sxs-lookup"><span data-stu-id="f86c0-258">Using the Inherited Control on a Form</span></span>
 <span data-ttu-id="f86c0-259">Devralınan denetiminizi, temel sınıf denetimini `ctlClock`sınadığınız şekilde test edebilirsiniz: Projeyi derlemek için F5 tuşuna basın ve denetimi **UserControl Test kapsayıcısında**çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="f86c0-259">You can test your inherited control the same way you tested the base class control, `ctlClock`: Press F5 to build the project and run your control in the **UserControl Test Container**.</span></span> <span data-ttu-id="f86c0-260">Daha fazla bilgi için [nasıl yapılır: UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md)'un çalışma zamanı davranışını test edin.</span><span class="sxs-lookup"><span data-stu-id="f86c0-260">For more information, see [How to: Test the Run-Time Behavior of a UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>

 <span data-ttu-id="f86c0-261">Denetiminizi kullanmak üzere yerleştirmek için bir form üzerinde barındırmanıza gerek duyarsınız.</span><span class="sxs-lookup"><span data-stu-id="f86c0-261">To put your control to use, you will need to host it on a form.</span></span> <span data-ttu-id="f86c0-262">Standart bir bileşik denetimde olduğu gibi, devralınan bir bileşik denetim tek başına olamaz ve bir formda ya da başka bir kapsayıcıda barındırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f86c0-262">As with a standard composite control, an inherited composite control cannot stand alone and must be hosted in a form or other container.</span></span> <span data-ttu-id="f86c0-263">Daha büyük bir işlevsellik derinliğine sahipolduğundan,testetmekiçinekkodgereklidir.`ctlAlarmClock`</span><span class="sxs-lookup"><span data-stu-id="f86c0-263">Since `ctlAlarmClock` has a greater depth of functionality, additional code is required to test it.</span></span> <span data-ttu-id="f86c0-264">Bu yordamda, işlevselliğini `ctlAlarmClock`test etmek için basit bir program yazacaksınız.</span><span class="sxs-lookup"><span data-stu-id="f86c0-264">In this procedure, you will write a simple program to test the functionality of `ctlAlarmClock`.</span></span> <span data-ttu-id="f86c0-265">`AlarmTime` Özelliğini ayarlamakvegöstermekiçinkodyazacaksınızveonunkendiişlevlerinitestedecektir.`ctlAlarmClock`</span><span class="sxs-lookup"><span data-stu-id="f86c0-265">You will write code to set and display the `AlarmTime` property of `ctlAlarmClock`, and will test its inherent functions.</span></span>

#### <a name="to-build-and-add-your-control-to-a-test-form"></a><span data-ttu-id="f86c0-266">Denetimi derlemek ve test formuna eklemek için</span><span class="sxs-lookup"><span data-stu-id="f86c0-266">To build and add your control to a test form</span></span>

1. <span data-ttu-id="f86c0-267">Çözüm Gezgini ' de, **ctlClockLib**' a sağ tıklayın ve ardından **Oluştur**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="f86c0-267">In Solution Explorer, right-click **ctlClockLib**, and then click **Build**.</span></span>

2. <span data-ttu-id="f86c0-268">**Dosya** menüsünde, **Ekle**' nin üzerine gelin ve ardından **Yeni proje**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="f86c0-268">On the **File** menu, point to **Add**, and then click **New Project**.</span></span>

3. <span data-ttu-id="f86c0-269">Çözüme yeni bir **Windows uygulaması** projesi ekleyin ve bunu `Test`adlandırın.</span><span class="sxs-lookup"><span data-stu-id="f86c0-269">Add a new **Windows Application** project to the solution, and name it `Test`.</span></span>

     <span data-ttu-id="f86c0-270">**Test** projesi Çözüm Gezgini eklenir.</span><span class="sxs-lookup"><span data-stu-id="f86c0-270">The **Test** project is added to Solution Explorer.</span></span>

4. <span data-ttu-id="f86c0-271">Çözüm Gezgini, `Test` proje düğümüne sağ tıklayın ve ardından Başvuru Ekle ' ye tıklayarak **Başvuru Ekle** iletişim kutusunu görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="f86c0-271">In Solution Explorer, right-click the `Test` project node, and then click **Add Reference** to display the **Add Reference** dialog box.</span></span>

5. <span data-ttu-id="f86c0-272">Etiketli **Projeler**sekmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="f86c0-272">Click the tab labeled **Projects**.</span></span> <span data-ttu-id="f86c0-273">Proje **ctlClockLib** proje **adı**altında listelenir.</span><span class="sxs-lookup"><span data-stu-id="f86c0-273">The project **ctlClockLib** will be listed under **Project Name**.</span></span> <span data-ttu-id="f86c0-274">Başvuruyu test projesine eklemek için **ctlClockLib** öğesine çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="f86c0-274">Double-click **ctlClockLib** to add the reference to the test project.</span></span>

6. <span data-ttu-id="f86c0-275">Çözüm Gezgini ' de **Test**' e sağ tıklayın ve ardından **Oluştur**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="f86c0-275">In Solution Explorer, right-click **Test**, and then click **Build**.</span></span>

7. <span data-ttu-id="f86c0-276">**Araç kutusunda** **ctlClockLib Components** düğümünü genişletin.</span><span class="sxs-lookup"><span data-stu-id="f86c0-276">In the **Toolbox**, expand the **ctlClockLib Components** node.</span></span>

8. <span data-ttu-id="f86c0-277">Formunuza bir örnek `ctlAlarmClock` eklemek için ctlAlarmClock öğesine çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="f86c0-277">Double-click **ctlAlarmClock** to add an instance of `ctlAlarmClock` to your form.</span></span>

9. <span data-ttu-id="f86c0-278">**Araç kutusunda**, formunuza bir <xref:System.Windows.Forms.DateTimePicker> denetim eklemek için **DateTimePicker** ' ı bulup çift tıklayın ve ardından **etiket**' e çift tıklayarak bir <xref:System.Windows.Forms.Label> denetim ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f86c0-278">In the **Toolbox**, locate and double-click **DateTimePicker** to add a <xref:System.Windows.Forms.DateTimePicker> control to your form, and then add a <xref:System.Windows.Forms.Label> control by double-clicking **Label**.</span></span>

10. <span data-ttu-id="f86c0-279">Denetimleri form üzerinde uygun bir yerde konumlandırmak için fareyi kullanın.</span><span class="sxs-lookup"><span data-stu-id="f86c0-279">Use the mouse to position the controls in a convenient place on the form.</span></span>

11. <span data-ttu-id="f86c0-280">Bu denetimlerin özelliklerini aşağıdaki şekilde ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="f86c0-280">Set the properties of these controls in the following manner.</span></span>

    |<span data-ttu-id="f86c0-281">Denetim</span><span class="sxs-lookup"><span data-stu-id="f86c0-281">Control</span></span>|<span data-ttu-id="f86c0-282">Özellik</span><span class="sxs-lookup"><span data-stu-id="f86c0-282">Property</span></span>|<span data-ttu-id="f86c0-283">Değer</span><span class="sxs-lookup"><span data-stu-id="f86c0-283">Value</span></span>|
    |-------------|--------------|-----------|
    |`label1`|<span data-ttu-id="f86c0-284">**Metin**</span><span class="sxs-lookup"><span data-stu-id="f86c0-284">**Text**</span></span>|`(blank space)`|
    ||<span data-ttu-id="f86c0-285">**Ad**</span><span class="sxs-lookup"><span data-stu-id="f86c0-285">**Name**</span></span>|`lblTest`|
    |`dateTimePicker1`|<span data-ttu-id="f86c0-286">**Ad**</span><span class="sxs-lookup"><span data-stu-id="f86c0-286">**Name**</span></span>|`dtpTest`|
    ||<span data-ttu-id="f86c0-287">**Formatını**</span><span class="sxs-lookup"><span data-stu-id="f86c0-287">**Format**</span></span>|<xref:System.Windows.Forms.DateTimePickerFormat.Time>|

12. <span data-ttu-id="f86c0-288">Tasarımcıda **dtpTest**öğesine çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="f86c0-288">In the designer, double-click **dtpTest**.</span></span>

     <span data-ttu-id="f86c0-289">**Kod Düzenleyicisi** olarak `Private Sub dtpTest_ValueChanged`açılır.</span><span class="sxs-lookup"><span data-stu-id="f86c0-289">The **Code Editor** opens to `Private Sub dtpTest_ValueChanged`.</span></span>

13. <span data-ttu-id="f86c0-290">Kodu aşağıdakine benzer olacak şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="f86c0-290">Modify the code so that it resembles the following.</span></span>

    ```vb
    Private Sub dtpTest_ValueChanged(ByVal sender As Object, ByVal e As _
        System.EventArgs) Handles dtpTest.ValueChanged
        ctlAlarmClock1.AlarmTime = dtpTest.Value
        ctlAlarmClock1.AlarmSet = True
        lblTest.Text = "Alarm Time is " & Format(ctlAlarmClock1.AlarmTime, _
            "hh:mm")
    End Sub
    ```

14. <span data-ttu-id="f86c0-291">Çözüm Gezgini ' de **Test**' e sağ tıklayın ve ardından **Başlangıç projesi olarak ayarla**' ya tıklayın.</span><span class="sxs-lookup"><span data-stu-id="f86c0-291">In Solution Explorer, right-click **Test**, and then click **Set as StartUp Project**.</span></span>

15. <span data-ttu-id="f86c0-292">Üzerinde **hata ayıklama** menüsünü tıklatın **hata ayıklamayı Başlat**.</span><span class="sxs-lookup"><span data-stu-id="f86c0-292">On the **Debug** menu, click **Start Debugging**.</span></span>

     <span data-ttu-id="f86c0-293">Test programı başlar.</span><span class="sxs-lookup"><span data-stu-id="f86c0-293">The test program starts.</span></span> <span data-ttu-id="f86c0-294">`ctlAlarmClock` Denetimde geçerli saatin güncelleştirildiğini ve başlangıç saatinin <xref:System.Windows.Forms.DateTimePicker> denetimde gösterildiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="f86c0-294">Note that the current time is updated in the `ctlAlarmClock` control, and that the starting time is shown in the <xref:System.Windows.Forms.DateTimePicker> control.</span></span>

16. <span data-ttu-id="f86c0-295">Saatin dakikalarının görüntülendiği yere tıklayın. <xref:System.Windows.Forms.DateTimePicker></span><span class="sxs-lookup"><span data-stu-id="f86c0-295">Click the <xref:System.Windows.Forms.DateTimePicker> where the minutes of the hour are displayed.</span></span>

17. <span data-ttu-id="f86c0-296">Klavyeyi kullanarak, tarafından `ctlAlarmClock`gösterilen geçerli saatten bir dakika daha büyük bir değer ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="f86c0-296">Using the keyboard, set a value for minutes that is one minute greater than the current time shown by `ctlAlarmClock`.</span></span>

     <span data-ttu-id="f86c0-297">Uyarı ayarının zamanı içinde `lblTest`gösterilir.</span><span class="sxs-lookup"><span data-stu-id="f86c0-297">The time for the alarm setting is shown in `lblTest`.</span></span> <span data-ttu-id="f86c0-298">Uyarı ayarı zamanına ulaşmak için, görüntülenecek sürenin bekleyin.</span><span class="sxs-lookup"><span data-stu-id="f86c0-298">Wait for the displayed time to reach the alarm setting time.</span></span> <span data-ttu-id="f86c0-299">Görünen süre, alarmın ayarlandığı zamana ulaştığında, bip sesi bırakılır ve `lblAlarm` yanıp sönecektir.</span><span class="sxs-lookup"><span data-stu-id="f86c0-299">When the displayed time reaches the time to which the alarm is set, the beep will sound and `lblAlarm` will flash.</span></span>

18. <span data-ttu-id="f86c0-300">Tıklayarak `lblAlarm`uyarıyı kapatın.</span><span class="sxs-lookup"><span data-stu-id="f86c0-300">Turn off the alarm by clicking `lblAlarm`.</span></span> <span data-ttu-id="f86c0-301">Şimdi uyarıyı sıfırlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f86c0-301">You may now reset the alarm.</span></span>

     <span data-ttu-id="f86c0-302">Bu izlenecek yol, bir dizi temel kavramı kapsamıştır.</span><span class="sxs-lookup"><span data-stu-id="f86c0-302">This walkthrough has covered a number of key concepts.</span></span> <span data-ttu-id="f86c0-303">Bir bileşik denetim kapsayıcısına denetimleri ve bileşenleri birleştirerek bileşik bir denetim oluşturmayı öğrendiniz.</span><span class="sxs-lookup"><span data-stu-id="f86c0-303">You have learned to create a composite control by combining controls and components into a composite control container.</span></span> <span data-ttu-id="f86c0-304">Denetime Özellik eklemeyi ve özel işlevsellik uygulamak için kod yazmayı öğrendiniz.</span><span class="sxs-lookup"><span data-stu-id="f86c0-304">You have learned to add properties to your control, and to write code to implement custom functionality.</span></span> <span data-ttu-id="f86c0-305">Son bölümde, belirli bir bileşik denetimin işlevselliğini devralma yoluyla genişletmeyi ve bu yöntemleri geçersiz kılarak ana bilgisayar yöntemlerinin işlevselliğini değiştirmeyi öğrendiniz.</span><span class="sxs-lookup"><span data-stu-id="f86c0-305">In the last section, you learned to extend the functionality of a given composite control through inheritance, and to alter the functionality of host methods by overriding those methods.</span></span>

## <a name="see-also"></a><span data-ttu-id="f86c0-306">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f86c0-306">See also</span></span>

- [<span data-ttu-id="f86c0-307">Özel Denetim Çeşitleri</span><span class="sxs-lookup"><span data-stu-id="f86c0-307">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
- [<span data-ttu-id="f86c0-308">Nasıl yapılır: Bileşik denetimleri yaz</span><span class="sxs-lookup"><span data-stu-id="f86c0-308">How to: Author Composite Controls</span></span>](how-to-author-composite-controls.md)
- [<span data-ttu-id="f86c0-309">Nasıl yapılır: Araç kutusu öğelerini Seç Iletişim kutusunda bir denetim görüntüle</span><span class="sxs-lookup"><span data-stu-id="f86c0-309">How to: Display a Control in the Choose Toolbox Items Dialog Box</span></span>](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)
