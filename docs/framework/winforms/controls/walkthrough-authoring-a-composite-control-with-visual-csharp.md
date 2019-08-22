---
title: 'İzlenecek yol: C# ile Bileşik Denetim Yazma'
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [C#]
- user controls [Windows Forms], creating with Visual C#
- UserControl class [Windows Forms], walkthroughs
- user controls [C#]
- custom controls [Windows Forms], creating
ms.assetid: f88481a8-c746-4a36-9479-374ce5f2e91f
ms.openlocfilehash: 12b506e859579a0755c2e9842e792c59968c94a8
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666746"
---
# <a name="walkthrough-authoring-a-composite-control-with-visual-c"></a><span data-ttu-id="27984-102">İzlenecek yol: Visual C ile bileşik denetim yazma\#</span><span class="sxs-lookup"><span data-stu-id="27984-102">Walkthrough: Authoring a Composite Control with Visual C\#</span></span>

<span data-ttu-id="27984-103">Bileşik denetimler, özel grafik arabirimlerinin oluşturulup yeniden kullanılabilmesi için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="27984-103">Composite controls provide a means by which custom graphical interfaces can be created and reused.</span></span> <span data-ttu-id="27984-104">Bileşik denetim temelde görsel temsili olan bir bileşendir.</span><span class="sxs-lookup"><span data-stu-id="27984-104">A composite control is essentially a component with a visual representation.</span></span> <span data-ttu-id="27984-105">Bu nedenle, Kullanıcı girişini doğrulayarak, görüntü özelliklerini değiştirerek veya yazar için gereken diğer görevleri gerçekleştirerek işlevselliği genişletebilen bir veya daha fazla Windows Forms denetimi, bileşeni veya kod bloklarında bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="27984-105">As such, it might consist of one or more Windows Forms controls, components, or blocks of code that can extend functionality by validating user input, modifying display properties, or performing other tasks required by the author.</span></span> <span data-ttu-id="27984-106">Bileşik denetimler Windows Forms diğer denetimlerle aynı şekilde yerleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="27984-106">Composite controls can be placed on Windows Forms in the same manner as other controls.</span></span> <span data-ttu-id="27984-107">Bu izlenecek yolun ilk bölümünde adlı `ctlClock`basit bir bileşik denetim oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="27984-107">In the first part of this walkthrough, you create a simple composite control called `ctlClock`.</span></span> <span data-ttu-id="27984-108">İzlenecek yolun ikinci bölümünde, devralma `ctlClock` ile işlevlerini genişletebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="27984-108">In the second part of the walkthrough, you extend the functionality of `ctlClock` through inheritance.</span></span>

## <a name="creating-the-project"></a><span data-ttu-id="27984-109">Projeyi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="27984-109">Creating the Project</span></span>

<span data-ttu-id="27984-110">Yeni bir proje oluşturduğunuzda, kök ad alanı, derleme adı ve proje adını ayarlamak için adını belirtin ve varsayılan bileşenin doğru ad alanında yer aldığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="27984-110">When you create a new project, you specify its name to set the root namespace, assembly name, and project name, and ensure that the default component will be in the correct namespace.</span></span>

### <a name="to-create-the-ctlclocklib-control-library-and-the-ctlclock-control"></a><span data-ttu-id="27984-111">CtlClockLib denetim kitaplığını ve ctlClock denetimini oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="27984-111">To create the ctlClockLib control library and the ctlClock control</span></span>

1. <span data-ttu-id="27984-112">**Dosya** menüsünde, **Yeni**' nin üzerine gelin ve ardından **Proje** ' ye tıklayarak **Yeni proje** iletişim kutusunu açın.</span><span class="sxs-lookup"><span data-stu-id="27984-112">On the **File** menu, point to **New**, and then click **Project** to open the **New Project** dialog box.</span></span>

2. <span data-ttu-id="27984-113">Görsel C# proje listesinden **Windows Forms denetim kitaplığı** proje şablonu ' nu seçin, `ctlClockLib` **ad** kutusuna yazın ve ardından **Tamam**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="27984-113">From the list of Visual C# projects, select the **Windows Forms Control Library** project template, type `ctlClockLib` in the **Name** box, and then click **OK**.</span></span>

     <span data-ttu-id="27984-114">Proje adı `ctlClockLib`, varsayılan olarak kök ad alanına da atanır.</span><span class="sxs-lookup"><span data-stu-id="27984-114">The project name, `ctlClockLib`, is also assigned to the root namespace by default.</span></span> <span data-ttu-id="27984-115">Kök ad alanı, derlemedeki bileşenlerin adlarını nitelemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="27984-115">The root namespace is used to qualify the names of components in the assembly.</span></span> <span data-ttu-id="27984-116">Örneğin, iki derleme adlı `ctlClock`bileşenler içeriyorsa, `ctlClock` bileşenini kullanarak`ctlClockLib.ctlClock.`</span><span class="sxs-lookup"><span data-stu-id="27984-116">For example, if two assemblies provide components named `ctlClock`, you can specify your `ctlClock` component using `ctlClockLib.ctlClock.`</span></span>

3. <span data-ttu-id="27984-117">Çözüm Gezgini ' de, **UserControl1.cs**' a sağ tıklayın ve ardından **Yeniden Adlandır**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="27984-117">In Solution Explorer, right-click **UserControl1.cs**, and then click **Rename**.</span></span> <span data-ttu-id="27984-118">Dosya adını olarak `ctlClock.cs`değiştirin.</span><span class="sxs-lookup"><span data-stu-id="27984-118">Change the file name to `ctlClock.cs`.</span></span> <span data-ttu-id="27984-119">"UserControl1" kod öğesiyle tüm başvuruları yeniden adlandırmak isteyip istemediğiniz sorulduğunda **Evet** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="27984-119">Click the **Yes** button when you are asked if you want to rename all references to the code element "UserControl1".</span></span>

    > [!NOTE]
    > <span data-ttu-id="27984-120">Varsayılan olarak, bileşik bir denetim sistem tarafından sunulan <xref:System.Windows.Forms.UserControl> sınıftan devralınır.</span><span class="sxs-lookup"><span data-stu-id="27984-120">By default, a composite control inherits from the <xref:System.Windows.Forms.UserControl> class provided by the system.</span></span> <span data-ttu-id="27984-121"><xref:System.Windows.Forms.UserControl> Sınıfı, tüm bileşik denetimlerin gerektirdiği işlevselliği sağlar ve standart yöntemler ve özellikler uygular.</span><span class="sxs-lookup"><span data-stu-id="27984-121">The <xref:System.Windows.Forms.UserControl> class provides functionality required by all composite controls, and implements standard methods and properties.</span></span>

4. <span data-ttu-id="27984-122">Projeyi kaydetmek için **Dosya** menüsünde **Tümünü Kaydet** ' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="27984-122">On the **File** menu, click **Save All** to save the project.</span></span>

## <a name="adding-windows-controls-and-components-to-the-composite-control"></a><span data-ttu-id="27984-123">Bileşik denetime Windows denetimleri ve bileşenleri ekleme</span><span class="sxs-lookup"><span data-stu-id="27984-123">Adding Windows Controls and Components to the Composite Control</span></span>

<span data-ttu-id="27984-124">Görsel arabirim, bileşik denetiminizin temel bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="27984-124">A visual interface is an essential part of your composite control.</span></span> <span data-ttu-id="27984-125">Bu görsel arabirim, tasarımcı yüzeyine bir veya daha fazla Windows denetimi eklenerek uygulanır.</span><span class="sxs-lookup"><span data-stu-id="27984-125">This visual interface is implemented by the addition of one or more Windows controls to the designer surface.</span></span> <span data-ttu-id="27984-126">Aşağıdaki gösteride, Windows denetimlerini bileşik denetiminizle birleştirirsiniz ve işlevselliği uygulamak için kod yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="27984-126">In the following demonstration, you will incorporate Windows controls into your composite control and write code to implement functionality.</span></span>

### <a name="to-add-a-label-and-a-timer-to-your-composite-control"></a><span data-ttu-id="27984-127">Bileşik denetilemenize bir etiket ve süreölçer eklemek için</span><span class="sxs-lookup"><span data-stu-id="27984-127">To add a Label and a Timer to your composite control</span></span>

1. <span data-ttu-id="27984-128">Çözüm Gezgini ' de, **ctlClock.cs**' a sağ tıklayın ve ardından **tasarımcıyı görüntüle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="27984-128">In Solution Explorer, right-click **ctlClock.cs**, and then click **View Designer**.</span></span>

2. <span data-ttu-id="27984-129">**Araç kutusunda** **ortak denetimler** düğümünü genişletin ve ardından **etiket**' e çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="27984-129">In the **Toolbox**, expand the **Common Controls** node, and then double-click **Label**.</span></span>

     <span data-ttu-id="27984-130">Tasarımcı <xref:System.Windows.Forms.Label> yüzeyinde denetimciyle adlandırılmış `label1` bir denetim eklenir.</span><span class="sxs-lookup"><span data-stu-id="27984-130">A <xref:System.Windows.Forms.Label> control named `label1` is added to your control on the designer surface.</span></span>

3. <span data-ttu-id="27984-131">Tasarımcıda **Label1**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="27984-131">In the designer, click **label1**.</span></span> <span data-ttu-id="27984-132">Özellikler penceresi, aşağıdaki özellikleri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="27984-132">In the Properties window, set the following properties.</span></span>

    |<span data-ttu-id="27984-133">Özellik</span><span class="sxs-lookup"><span data-stu-id="27984-133">Property</span></span>|<span data-ttu-id="27984-134">Değiştir</span><span class="sxs-lookup"><span data-stu-id="27984-134">Change to</span></span>|
    |--------------|---------------|
    |<span data-ttu-id="27984-135">**Ad**</span><span class="sxs-lookup"><span data-stu-id="27984-135">**Name**</span></span>|`lblDisplay`|
    |<span data-ttu-id="27984-136">**Metin**</span><span class="sxs-lookup"><span data-stu-id="27984-136">**Text**</span></span>|`(blank space)`|
    |<span data-ttu-id="27984-137">**TextAlign**</span><span class="sxs-lookup"><span data-stu-id="27984-137">**TextAlign**</span></span>|`MiddleCenter`|
    |<span data-ttu-id="27984-138">**Yazı tipi. boyutu**</span><span class="sxs-lookup"><span data-stu-id="27984-138">**Font.Size**</span></span>|`14`|

4. <span data-ttu-id="27984-139">**Araç kutusunda**, **Bileşenler** düğümünü genişletin ve ardından **Zamanlayıcı**' ya çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="27984-139">In the **Toolbox**, expand the **Components** node, and then double-click **Timer**.</span></span>

     <span data-ttu-id="27984-140">Bir <xref:System.Windows.Forms.Timer> bileşen olduğundan, çalışma zamanında görsel temsili yoktur.</span><span class="sxs-lookup"><span data-stu-id="27984-140">Because a <xref:System.Windows.Forms.Timer> is a component, it has no visual representation at run time.</span></span> <span data-ttu-id="27984-141">Bu nedenle, tasarımcı yüzeyindeki denetimlerde görünmez, ancak **Bileşen tasarımcısında** (tasarımcı yüzeyinin altındaki bir tepsi) değil.</span><span class="sxs-lookup"><span data-stu-id="27984-141">Therefore, it does not appear with the controls on the designer surface, but rather in the **Component Designer** (a tray at the bottom of the designer surface).</span></span>

5. <span data-ttu-id="27984-142">**Bileşen tasarımcısında**, **Süreölçer1** <xref:System.Windows.Forms.Timer.Interval%2A> ' a tıklayın ve ardından özelliğini `1000` ve <xref:System.Windows.Forms.Timer.Enabled%2A> özelliğini olarak `true`ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="27984-142">In the **Component Designer**, click **timer1**, and then set the <xref:System.Windows.Forms.Timer.Interval%2A> property to `1000` and the <xref:System.Windows.Forms.Timer.Enabled%2A> property to `true`.</span></span>

     <span data-ttu-id="27984-143"><xref:System.Windows.Forms.Timer.Interval%2A> Özelliği <xref:System.Windows.Forms.Timer> bileşeni işaret eden sıklığı denetler.</span><span class="sxs-lookup"><span data-stu-id="27984-143">The <xref:System.Windows.Forms.Timer.Interval%2A> property controls the frequency with which the <xref:System.Windows.Forms.Timer> component ticks.</span></span> <span data-ttu-id="27984-144">Her zaman `timer1` Tick, `timer1_Tick` olaydaki kodu çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="27984-144">Each time `timer1` ticks, it runs the code in the `timer1_Tick` event.</span></span> <span data-ttu-id="27984-145">Aralık, zaman işaretleri arasındaki milisaniye sayısını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="27984-145">The interval represents the number of milliseconds between ticks.</span></span>

6. <span data-ttu-id="27984-146">**Bileşen tasarımcısında**, için **Süreölçer1** öğesine çift tıklayarak için `timer1_Tick` `ctlClock`olayına gidin.</span><span class="sxs-lookup"><span data-stu-id="27984-146">In the **Component Designer**, double-click **timer1** to go to the `timer1_Tick` event for `ctlClock`.</span></span>

7. <span data-ttu-id="27984-147">Kodu aşağıdaki kod örneğine benzer olacak şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="27984-147">Modify the code so that it resembles the following code sample.</span></span> <span data-ttu-id="27984-148">Erişim değiştiricisini ' dan `private` `protected`' a değiştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="27984-148">Be sure to change the access modifier from `private` to `protected`.</span></span>

    ```csharp
    protected void timer1_Tick(object sender, System.EventArgs e)
    {
        // Causes the label to display the current time.
        lblDisplay.Text = DateTime.Now.ToLongTimeString();
    }
    ```

     <span data-ttu-id="27984-149">Bu kod, geçerli saatin ' de `lblDisplay`görüntülenmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="27984-149">This code will cause the current time to be shown in `lblDisplay`.</span></span> <span data-ttu-id="27984-150">Aralığı `timer1` olarak ayarlandığı için `1000`bu olay her bin milisaniyede bir gerçekleşeceğinden, bu nedenle her saniye geçerli saati güncelliyor.</span><span class="sxs-lookup"><span data-stu-id="27984-150">Because the interval of `timer1` was set to `1000`, this event will occur every thousand milliseconds, thus updating the current time every second.</span></span>

8. <span data-ttu-id="27984-151">Yöntemini `virtual` anahtar sözcüğüyle geçersiz kılınabilir olacak şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="27984-151">Modify the method to be overridable with the `virtual` keyword.</span></span> <span data-ttu-id="27984-152">Daha fazla bilgi için aşağıdaki "Kullanıcı denetiminden devralma" bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="27984-152">For more information, see the  "Inheriting from a User Control" section below.</span></span>

    ```csharp
    protected virtual void timer1_Tick(object sender, System.EventArgs e)
    ```

9. <span data-ttu-id="27984-153">Projeyi kaydetmek için **Dosya** menüsünde **Tümünü Kaydet** ' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="27984-153">On the **File** menu, click **Save All** to save the project.</span></span>

## <a name="adding-properties-to-the-composite-control"></a><span data-ttu-id="27984-154">Bileşik denetime özellikler ekleme</span><span class="sxs-lookup"><span data-stu-id="27984-154">Adding Properties to the Composite Control</span></span>

<span data-ttu-id="27984-155">Saat denetiminiz artık, her biri <xref:System.Windows.Forms.Label> kendi kendine ait <xref:System.Windows.Forms.Timer> özellikler kümesiyle birlikte bir denetimi ve bileşeni kapsüller.</span><span class="sxs-lookup"><span data-stu-id="27984-155">Your clock control now encapsulates a <xref:System.Windows.Forms.Label> control and a <xref:System.Windows.Forms.Timer> component, each with its own set of inherent properties.</span></span> <span data-ttu-id="27984-156">Bu denetimlerin tek tek özelliklerine denetiminizin sonraki kullanıcıları tarafından erişilemese de, uygun kod bloklarını yazarak özel özellikler oluşturabilir ve kullanıma sunabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="27984-156">While the individual properties of these controls will not be accessible to subsequent users of your control, you can create and expose custom properties by writing the appropriate blocks of code.</span></span> <span data-ttu-id="27984-157">Aşağıdaki yordamda, denetime, kullanıcının arka plan ve metin rengini değiştirmesini sağlayan özellikler ekleyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="27984-157">In the following procedure, you will add properties to your control that enable the user to change the color of the background and text.</span></span>

### <a name="to-add-a-property-to-your-composite-control"></a><span data-ttu-id="27984-158">Bileşik denetimi bir özellik eklemek için</span><span class="sxs-lookup"><span data-stu-id="27984-158">To add a property to your composite control</span></span>

1. <span data-ttu-id="27984-159">Çözüm Gezgini ' de, **ctlClock.cs**' a sağ tıklayın ve ardından **kodu görüntüle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="27984-159">In Solution Explorer, right-click **ctlClock.cs**, and then click **View Code**.</span></span>

     <span data-ttu-id="27984-160">Denetiminizin **Kod Düzenleyicisi** açılır.</span><span class="sxs-lookup"><span data-stu-id="27984-160">The **Code Editor** for your control opens.</span></span>

2. <span data-ttu-id="27984-161">`public partial class ctlClock` İfadesini bulun.</span><span class="sxs-lookup"><span data-stu-id="27984-161">Locate the `public partial class ctlClock` statement.</span></span> <span data-ttu-id="27984-162">Açma küme ayracı`{)`altında, aşağıdaki kodu yazın.</span><span class="sxs-lookup"><span data-stu-id="27984-162">Beneath the opening brace (`{)`, type the following code.</span></span>

    ```csharp
    private Color colFColor;
    private Color colBColor;
    ```

     <span data-ttu-id="27984-163">Bu deyimler, oluşturmak üzere olduğunuz özelliklerin değerlerini depolamak için kullanacağınız özel değişkenleri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="27984-163">These statements create the private variables that you will use to store the values for the properties you are about to create.</span></span>

3. <span data-ttu-id="27984-164">2\. adımdaki değişken bildirimlerinin altına aşağıdaki kodu yazın.</span><span class="sxs-lookup"><span data-stu-id="27984-164">Type the following code beneath the variable declarations from step 2.</span></span>

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

     <span data-ttu-id="27984-165">Yukarıdaki kod iki özel özellik `ClockForeColor` yapar ve `ClockBackColor`bu denetimin sonraki kullanıcıları tarafından kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="27984-165">The preceding code makes two custom properties, `ClockForeColor` and `ClockBackColor`, available to subsequent users of this control.</span></span> <span data-ttu-id="27984-166">`get` Ve`set` deyimleri, özellik değerinin depolanmasını ve alınmasını, ayrıca özelliğine uygun işlevselliği uygulamak için de kod sağlar.</span><span class="sxs-lookup"><span data-stu-id="27984-166">The `get` and `set` statements provide for storage and retrieval of the property value, as well as code to implement functionality appropriate to the property.</span></span>

4. <span data-ttu-id="27984-167">Projeyi kaydetmek için **Dosya** menüsünde **Tümünü Kaydet** ' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="27984-167">On the **File** menu, click **Save All** to save the project.</span></span>

## <a name="testing-the-control"></a><span data-ttu-id="27984-168">Denetimi test etme</span><span class="sxs-lookup"><span data-stu-id="27984-168">Testing the Control</span></span>

<span data-ttu-id="27984-169">Denetimler tek başına uygulamalar değildir; Bunlar bir kapsayıcıda barındırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="27984-169">Controls are not stand-alone applications; they must be hosted in a container.</span></span> <span data-ttu-id="27984-170">Denetiminizin çalışma zamanı davranışını test edin ve özelliklerini **UserControl Test kapsayıcısı**ile çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="27984-170">Test your control's run-time behavior and exercise its properties with the **UserControl Test Container**.</span></span> <span data-ttu-id="27984-171">Daha fazla bilgi için [nasıl yapılır: UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md)'un çalışma zamanı davranışını test edin.</span><span class="sxs-lookup"><span data-stu-id="27984-171">For more information, see [How to: Test the Run-Time Behavior of a UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>

### <a name="to-test-your-control"></a><span data-ttu-id="27984-172">Denetiminizi test etmek için</span><span class="sxs-lookup"><span data-stu-id="27984-172">To test your control</span></span>

1. <span data-ttu-id="27984-173">Projeyi derlemek için F5 tuşuna basın ve denetimi **UserControl Test kapsayıcısında**çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="27984-173">Press F5 to build the project and run your control in the **UserControl Test Container**.</span></span>

2. <span data-ttu-id="27984-174">Test kapsayıcısının özellik kılavuzunda, `ClockBackColor` özelliğini bulun ve ardından renk paletini göstermek için özelliği seçin.</span><span class="sxs-lookup"><span data-stu-id="27984-174">In the test container's property grid, locate the `ClockBackColor` property, and then select the property to display the color palette.</span></span>

3. <span data-ttu-id="27984-175">Tıklayarak bir renk seçin.</span><span class="sxs-lookup"><span data-stu-id="27984-175">Choose a color by clicking it.</span></span>

     <span data-ttu-id="27984-176">Denetiminizin arka plan rengi, seçtiğiniz renge değişir.</span><span class="sxs-lookup"><span data-stu-id="27984-176">The background color of your control changes to the color you selected.</span></span>

4. <span data-ttu-id="27984-177">`ClockForeColor` Özelliğin beklendiği gibi çalıştığını doğrulamak için benzer bir olay dizisi kullanın.</span><span class="sxs-lookup"><span data-stu-id="27984-177">Use a similar sequence of events to verify that the `ClockForeColor` property is functioning as expected.</span></span>

     <span data-ttu-id="27984-178">Bu bölümde ve önceki bölümlerde, bileşik denetim biçiminde özel işlevsellik sağlamak için bileşenlerin ve Windows denetimlerinin kod ve paketleme ile nasıl birleştirilebileceği gördünüz.</span><span class="sxs-lookup"><span data-stu-id="27984-178">In this section and the preceding sections, you have seen how components and Windows controls can be combined with code and packaging to provide custom functionality in the form of a composite control.</span></span> <span data-ttu-id="27984-179">Birleşik denetidiklerinizin özelliklerini açığa çıkarmak ve tamamlandıktan sonra denetiminizi test etmek için öğrendiniz.</span><span class="sxs-lookup"><span data-stu-id="27984-179">You have learned to expose properties in your composite control, and how to test your control after it is complete.</span></span> <span data-ttu-id="27984-180">Sonraki bölümde, temel olarak kullanarak `ctlClock` devralınmış bir bileşik denetim oluşturmayı öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="27984-180">In the next section you will learn how to construct an inherited composite control using `ctlClock` as a base.</span></span>

## <a name="inheriting-from-a-composite-control"></a><span data-ttu-id="27984-181">Bileşik denetimden devralma</span><span class="sxs-lookup"><span data-stu-id="27984-181">Inheriting from a Composite Control</span></span>

<span data-ttu-id="27984-182">Önceki bölümlerde, Windows denetimlerini, bileşenleri ve kodu yeniden kullanılabilir bileşik denetimlere nasıl birleştirebileceğinizi öğrendiniz.</span><span class="sxs-lookup"><span data-stu-id="27984-182">In the previous sections, you learned how to combine Windows controls, components, and code into reusable composite controls.</span></span> <span data-ttu-id="27984-183">Bileşik denetiminiz artık diğer denetimlerin derlenme temeli olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="27984-183">Your composite control can now be used as a base upon which other controls can be built.</span></span> <span data-ttu-id="27984-184">Temel sınıftan bir sınıfın türeme işlemi *Devralma*olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="27984-184">The process of deriving a class from a base class is called *inheritance*.</span></span> <span data-ttu-id="27984-185">Bu bölümde, adlı `ctlAlarmClock`bir bileşik denetim oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="27984-185">In this section, you will create a composite control called `ctlAlarmClock`.</span></span> <span data-ttu-id="27984-186">Bu denetim, `ctlClock`üst denetiminden türetilecektir.</span><span class="sxs-lookup"><span data-stu-id="27984-186">This control will be derived from its parent control, `ctlClock`.</span></span> <span data-ttu-id="27984-187">Üst yöntemleri geçersiz kılarak ve yeni yöntemler ve `ctlClock` özellikler ekleyerek işlevselliğini genişletmeyi öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="27984-187">You will learn to extend the functionality of `ctlClock` by overriding parent methods and adding new methods and properties.</span></span>

<span data-ttu-id="27984-188">Devralınan bir denetim oluşturmanın ilk adımı onu üst öğesinden türemektir.</span><span class="sxs-lookup"><span data-stu-id="27984-188">The first step in creating an inherited control is to derive it from its parent.</span></span> <span data-ttu-id="27984-189">Bu eylem, üst denetimin tüm özelliklerine, yöntemlerine ve grafiksel özelliklerine sahip yeni bir denetim oluşturur, ancak yeni veya değiştirilmiş işlevselliğin eklenmesi için temel olarak da davranabilir.</span><span class="sxs-lookup"><span data-stu-id="27984-189">This action creates a new control that has all of the properties, methods, and graphical characteristics of the parent control, but can also act as a base for the addition of new or modified functionality.</span></span>

### <a name="to-create-the-inherited-control"></a><span data-ttu-id="27984-190">Devralınan denetimi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="27984-190">To create the inherited control</span></span>

1. <span data-ttu-id="27984-191">Çözüm Gezgini ' de, **ctlClockLib**' a sağ tıklayın, **Ekle**' nin üzerine gelin ve **Kullanıcı denetimi**' ne tıklayın.</span><span class="sxs-lookup"><span data-stu-id="27984-191">In Solution Explorer, right-click **ctlClockLib**, point to **Add**, and then click **User Control**.</span></span>

     <span data-ttu-id="27984-192">**Yeni Öğe Ekle** iletişim kutusu açılır.</span><span class="sxs-lookup"><span data-stu-id="27984-192">The **Add New Item** dialog box opens.</span></span>

2. <span data-ttu-id="27984-193">**Devralınan Kullanıcı denetimi** şablonunu seçin.</span><span class="sxs-lookup"><span data-stu-id="27984-193">Select the **Inherited User Control** template.</span></span>

3. <span data-ttu-id="27984-194">**Ad** kutusuna yazın `ctlAlarmClock.cs`ve ardından **Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="27984-194">In the **Name** box, type `ctlAlarmClock.cs`, and then click **Add**.</span></span>

     <span data-ttu-id="27984-195">**Devralma Seçicisi** iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="27984-195">The **Inheritance Picker** dialog box appears.</span></span>

4. <span data-ttu-id="27984-196">**Bileşen adı**altında **ctlClock**' ye çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="27984-196">Under **Component Name**, double-click **ctlClock**.</span></span>

5. <span data-ttu-id="27984-197">Çözüm Gezgini, geçerli projelere göz atabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="27984-197">In Solution Explorer, browse through the current projects.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="27984-198">Geçerli projeye **ctlAlarmClock.cs** adlı bir dosya eklendi.</span><span class="sxs-lookup"><span data-stu-id="27984-198">A file called **ctlAlarmClock.cs** has been added to the current project.</span></span>

### <a name="adding-the-alarm-properties"></a><span data-ttu-id="27984-199">Alarm özelliklerini ekleme</span><span class="sxs-lookup"><span data-stu-id="27984-199">Adding the Alarm Properties</span></span>

<span data-ttu-id="27984-200">Özellikler, devralınan bir denetime, Birleşik bir denetime eklendikçe aynı şekilde eklenir.</span><span class="sxs-lookup"><span data-stu-id="27984-200">Properties are added to an inherited control in the same way they are added to a composite control.</span></span> <span data-ttu-id="27984-201">Şimdi, denetimidir için iki özellik eklemek üzere özellik bildirimi söz dizimini kullanacaksınız: `AlarmTime`bu, uyarının bitiş tarihini ve saatini depolayan ve `AlarmSet`alarmın ayarlanmış olup olmadığını belirtecektir.</span><span class="sxs-lookup"><span data-stu-id="27984-201">You will now use the property declaration syntax to add two properties to your control: `AlarmTime`, which will store the value of the date and time the alarm is to go off, and `AlarmSet`, which will indicate whether the alarm is set.</span></span>

#### <a name="to-add-properties-to-your-composite-control"></a><span data-ttu-id="27984-202">Bileşik denetimi özellikler eklemek için</span><span class="sxs-lookup"><span data-stu-id="27984-202">To add properties to your composite control</span></span>

1. <span data-ttu-id="27984-203">Çözüm Gezgini ' de, **ctlAlarmClock**' a sağ tıklayın ve ardından **kodu görüntüle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="27984-203">In Solution Explorer, right-click **ctlAlarmClock**, and then click **View Code**.</span></span>

2. <span data-ttu-id="27984-204">`public class` İfadesini bulun.</span><span class="sxs-lookup"><span data-stu-id="27984-204">Locate the `public class` statement.</span></span> <span data-ttu-id="27984-205">Denetiminizin öğesinden `ctlClockLib.ctlClock`devraldığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="27984-205">Note that your control inherits from `ctlClockLib.ctlClock`.</span></span> <span data-ttu-id="27984-206">Açma küme ayracı (`{)` deyimin altına aşağıdaki kodu yazın.</span><span class="sxs-lookup"><span data-stu-id="27984-206">Beneath the opening brace (`{)` statement, type the following code.</span></span>

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

### <a name="adding-to-the-graphical-interface-of-the-control"></a><span data-ttu-id="27984-207">Denetimin grafik arabirimine ekleme</span><span class="sxs-lookup"><span data-stu-id="27984-207">Adding to the Graphical Interface of the Control</span></span>

<span data-ttu-id="27984-208">Devralınan denetiminizin devraldığı denetimle özdeş bir görsel arabirimi vardır.</span><span class="sxs-lookup"><span data-stu-id="27984-208">Your inherited control has a visual interface that is identical to the control it inherits from.</span></span> <span data-ttu-id="27984-209">Kendi üst denetimiyle aynı bileşen denetimlerine sahip olur, ancak yapısal denetimlerin özellikleri özellikle gösterilmedikleri sürece kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="27984-209">It possesses the same constituent controls as its parent control, but the properties of the constituent controls will not be available unless they were specifically exposed.</span></span> <span data-ttu-id="27984-210">Devralınan bir bileşik denetimin grafik arabirimine, herhangi bir bileşik denetime ekleyeceğiniz şekilde ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="27984-210">You may add to the graphical interface of an inherited composite control in the same manner as you would add to any composite control.</span></span> <span data-ttu-id="27984-211">Alarm saatinizin görsel arabirimine eklemeye devam etmek için, alarm bir işlem olduğunda Flash olacak bir etiket denetimi ekleyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="27984-211">To continue adding to your alarm clock's visual interface, you will add a label control that will flash when the alarm is sounding.</span></span>

#### <a name="to-add-the-label-control"></a><span data-ttu-id="27984-212">Etiket denetimi eklemek için</span><span class="sxs-lookup"><span data-stu-id="27984-212">To add the label control</span></span>

1. <span data-ttu-id="27984-213">Çözüm Gezgini ' de, **ctlAlarmClock**' a sağ tıklayın ve ardından **tasarımcıyı görüntüle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="27984-213">In Solution Explorer, right-click **ctlAlarmClock**, and then click **View Designer**.</span></span>

     <span data-ttu-id="27984-214">İçin `ctlAlarmClock` tasarımcı ana pencerede açılır.</span><span class="sxs-lookup"><span data-stu-id="27984-214">The designer for `ctlAlarmClock` opens in the main window.</span></span>

2. <span data-ttu-id="27984-215">Denetimin görüntüleme bölümüne tıklayın ve Özellikler penceresi görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="27984-215">Click the display portion of the control, and view the Properties window.</span></span>

    > [!NOTE]
    > <span data-ttu-id="27984-216">Tüm özellikler görüntülenirken, soluk olurlar.</span><span class="sxs-lookup"><span data-stu-id="27984-216">While all the properties are displayed, they are dimmed.</span></span> <span data-ttu-id="27984-217">Bu özelliklerin yerel `lblDisplay` olduğunu ve Özellikler penceresi değiştirilemeyeceğini veya erişilmeyeceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="27984-217">This indicates that these properties are native to `lblDisplay` and cannot be modified or accessed in the Properties window.</span></span> <span data-ttu-id="27984-218">Varsayılan olarak, bileşik denetimde `private`bulunan denetimler ve özellikleri herhangi bir şekilde erişilebilir değildir.</span><span class="sxs-lookup"><span data-stu-id="27984-218">By default, controls contained in a composite control are `private`, and their properties are not accessible by any means.</span></span>

    > [!NOTE]
    > <span data-ttu-id="27984-219">Bileşik denetiminizin sonraki kullanıcılarının iç denetimlerine erişimi olmasını istiyorsanız, veya `public` `protected`olarak bildirin.</span><span class="sxs-lookup"><span data-stu-id="27984-219">If you want subsequent users of your composite control to have access to its internal controls, declare them as `public` or `protected`.</span></span> <span data-ttu-id="27984-220">Bu, uygun kodu kullanarak bileşik denetilinizin içindeki denetimlerin özelliklerini ayarlamanıza ve değiştirmenize izin verir.</span><span class="sxs-lookup"><span data-stu-id="27984-220">This will allow you to set and modify properties of controls contained within your composite control by using the appropriate code.</span></span>

3. <span data-ttu-id="27984-221">Bileşik denetimi bir <xref:System.Windows.Forms.Label> denetim ekleyin.</span><span class="sxs-lookup"><span data-stu-id="27984-221">Add a <xref:System.Windows.Forms.Label> control to your composite control.</span></span>

4. <span data-ttu-id="27984-222">Fareyi kullanarak <xref:System.Windows.Forms.Label> denetimi, ekran kutusunun hemen altına sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="27984-222">Using the mouse, drag the <xref:System.Windows.Forms.Label> control immediately beneath the display box.</span></span> <span data-ttu-id="27984-223">Özellikler penceresi, aşağıdaki özellikleri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="27984-223">In the Properties window, set the following properties.</span></span>

    |<span data-ttu-id="27984-224">Özellik</span><span class="sxs-lookup"><span data-stu-id="27984-224">Property</span></span>|<span data-ttu-id="27984-225">Ayar</span><span class="sxs-lookup"><span data-stu-id="27984-225">Setting</span></span>|
    |--------------|-------------|
    |<span data-ttu-id="27984-226">**Ad**</span><span class="sxs-lookup"><span data-stu-id="27984-226">**Name**</span></span>|`lblAlarm`|
    |<span data-ttu-id="27984-227">**Metin**</span><span class="sxs-lookup"><span data-stu-id="27984-227">**Text**</span></span>|<span data-ttu-id="27984-228">**Alarm!**</span><span class="sxs-lookup"><span data-stu-id="27984-228">**Alarm!**</span></span>|
    |<span data-ttu-id="27984-229">**TextAlign**</span><span class="sxs-lookup"><span data-stu-id="27984-229">**TextAlign**</span></span>|`MiddleCenter`|
    |<span data-ttu-id="27984-230">**Görüne**</span><span class="sxs-lookup"><span data-stu-id="27984-230">**Visible**</span></span>|`false`|

### <a name="adding-the-alarm-functionality"></a><span data-ttu-id="27984-231">Alarm Işlevlerini ekleme</span><span class="sxs-lookup"><span data-stu-id="27984-231">Adding the Alarm Functionality</span></span>

<span data-ttu-id="27984-232">Önceki yordamlarda, bileşik denetiminizdeki alarm işlevselliğini etkinleştiren Özellikler ve bir denetim eklediniz.</span><span class="sxs-lookup"><span data-stu-id="27984-232">In the previous procedures, you added properties and a control that will enable alarm functionality in your composite control.</span></span> <span data-ttu-id="27984-233">Bu yordamda, geçerli saati alarm zamanına göre karşılaştırmak için kod ekleyeceksiniz ve aynı ise, bir alarm Flash için de aynı olduğunda.</span><span class="sxs-lookup"><span data-stu-id="27984-233">In this procedure, you will add code to compare the current time to the alarm time and, if they are the same, to flash an alarm.</span></span> <span data-ttu-id="27984-234">`timer1_Tick` `ctlAlarmClock` Yöntemini geçersiz kılarak ve buna ek kod ekleyerek, tüm devralınan işlevlerini `ctlClock`korurken özelliğini genişletebilirsiniz. `ctlClock`</span><span class="sxs-lookup"><span data-stu-id="27984-234">By overriding the `timer1_Tick` method of `ctlClock` and adding additional code to it, you will extend the capability of `ctlAlarmClock` while retaining all of the inherent functionality of `ctlClock`.</span></span>

#### <a name="to-override-the-timer1_tick-method-of-ctlclock"></a><span data-ttu-id="27984-235">CtlClock timer1_Tick yöntemini geçersiz kılmak için</span><span class="sxs-lookup"><span data-stu-id="27984-235">To override the timer1_Tick method of ctlClock</span></span>

1. <span data-ttu-id="27984-236">**Kod düzenleyicisinde**, `private bool blnAlarmSet;` ifadesini bulun.</span><span class="sxs-lookup"><span data-stu-id="27984-236">In the **Code Editor**, locate the `private bool blnAlarmSet;` statement.</span></span> <span data-ttu-id="27984-237">Hemen hemen altına aşağıdaki ifadeyi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="27984-237">Immediately beneath it, add the following statement.</span></span>

    ```csharp
    private bool blnColorTicker;
    ```

2. <span data-ttu-id="27984-238">**Kod Düzenleyicisi**'nde, kapatma küme ayracını (`})` sınıfının sonundaki) bulun.</span><span class="sxs-lookup"><span data-stu-id="27984-238">In the **Code Editor**, locate the closing brace (`})` at the end of the class.</span></span> <span data-ttu-id="27984-239">Küme ayracından hemen önce aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="27984-239">Just before the brace, add the following code.</span></span>

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

     <span data-ttu-id="27984-240">Bu kodun eklenmesi birkaç görevi gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="27984-240">The addition of this code accomplishes several tasks.</span></span> <span data-ttu-id="27984-241">`override` İfade, denetimi temel denetimden devralınan yöntemin yerine bu yöntemi kullanacak şekilde yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="27984-241">The `override` statement directs the control to use this method in place of the method that was inherited from the base control.</span></span> <span data-ttu-id="27984-242">Bu yöntem çağrıldığında, `base.timer1_Tick` ifadeyi çağırarak geçersiz kıldığından, özgün denetimde dahil edilen tüm işlevlerin Bu denetimde yeniden üretildiğinden emin olarak çağrılır.</span><span class="sxs-lookup"><span data-stu-id="27984-242">When this method is called, it calls the method it overrides by invoking the `base.timer1_Tick` statement, ensuring that all of the functionality incorporated in the original control is reproduced in this control.</span></span> <span data-ttu-id="27984-243">Daha sonra alarm işlevselliğini birleştirmek için ek kod çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="27984-243">It then runs additional code to incorporate the alarm functionality.</span></span> <span data-ttu-id="27984-244">Uyarı oluştuğunda yanıp sönen bir etiket denetimi görünür.</span><span class="sxs-lookup"><span data-stu-id="27984-244">A flashing label control will appear when the alarm occurs.</span></span>

     <span data-ttu-id="27984-245">Alarm saati denetiminiz neredeyse tamamlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="27984-245">Your alarm clock control is almost complete.</span></span> <span data-ttu-id="27984-246">Kalan tek şey, devre dışı bırakmak için bir yol uygulamaktır.</span><span class="sxs-lookup"><span data-stu-id="27984-246">The only thing that remains is to implement a way to turn it off.</span></span> <span data-ttu-id="27984-247">Bunu yapmak için `lblAlarm_Click` yöntemine kod ekleyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="27984-247">To do this, you will add code to the `lblAlarm_Click` method.</span></span>

#### <a name="to-implement-the-shutoff-method"></a><span data-ttu-id="27984-248">Shutoff yöntemini uygulamak için</span><span class="sxs-lookup"><span data-stu-id="27984-248">To implement the shutoff method</span></span>

1. <span data-ttu-id="27984-249">Çözüm Gezgini ' de, **ctlAlarmClock.cs**' a sağ tıklayın ve ardından **tasarımcıyı görüntüle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="27984-249">In Solution Explorer, right-click **ctlAlarmClock.cs**, and then click **View Designer**.</span></span>

     <span data-ttu-id="27984-250">Tasarımcı açılır.</span><span class="sxs-lookup"><span data-stu-id="27984-250">The designer opens.</span></span>

2. <span data-ttu-id="27984-251">Denetime düğme ekleyin.</span><span class="sxs-lookup"><span data-stu-id="27984-251">Add a button to the control.</span></span> <span data-ttu-id="27984-252">Düğmenin özelliklerini aşağıdaki gibi ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="27984-252">Set the properties of the button as follows.</span></span>

    |<span data-ttu-id="27984-253">Özellik</span><span class="sxs-lookup"><span data-stu-id="27984-253">Property</span></span>|<span data-ttu-id="27984-254">Değer</span><span class="sxs-lookup"><span data-stu-id="27984-254">Value</span></span>|
    |--------------|-----------|
    |<span data-ttu-id="27984-255">**Ad**</span><span class="sxs-lookup"><span data-stu-id="27984-255">**Name**</span></span>|`btnAlarmOff`|
    |<span data-ttu-id="27984-256">**Metin**</span><span class="sxs-lookup"><span data-stu-id="27984-256">**Text**</span></span>|<span data-ttu-id="27984-257">**Alarmı devre dışı bırak**</span><span class="sxs-lookup"><span data-stu-id="27984-257">**Disable Alarm**</span></span>|

3. <span data-ttu-id="27984-258">Tasarımcı 'da, **btnAlarmOff**' a çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="27984-258">In the designer, double-click **btnAlarmOff**.</span></span>

     <span data-ttu-id="27984-259">**Kod Düzenleyicisi** `private void btnAlarmOff_Click` satıra açılır.</span><span class="sxs-lookup"><span data-stu-id="27984-259">The **Code Editor** opens to the `private void btnAlarmOff_Click` line.</span></span>

4. <span data-ttu-id="27984-260">Bu yöntemi, aşağıdaki koda benzer olacak şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="27984-260">Modify this method so that it resembles the following code.</span></span>

    ```csharp
    private void btnAlarmOff_Click(object sender, System.EventArgs e)
    {
        // Turns off the alarm.
        AlarmSet = false;
        // Hides the flashing label.
        lblAlarm.Visible = false;
    }
    ```

5. <span data-ttu-id="27984-261">Projeyi kaydetmek için **Dosya** menüsünde **Tümünü Kaydet** ' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="27984-261">On the **File** menu, click **Save All** to save the project.</span></span>

### <a name="using-the-inherited-control-on-a-form"></a><span data-ttu-id="27984-262">Bir form üzerinde devralınmış denetimi kullanma</span><span class="sxs-lookup"><span data-stu-id="27984-262">Using the Inherited Control on a Form</span></span>

<span data-ttu-id="27984-263">Devralınan denetiminizi, temel sınıf denetimini `ctlClock`sınadığınız şekilde test edebilirsiniz: Projeyi derlemek için F5 tuşuna basın ve denetimi **UserControl Test kapsayıcısında**çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="27984-263">You can test your inherited control the same way you tested the base class control, `ctlClock`: Press F5 to build the project and run your control in the **UserControl Test Container**.</span></span> <span data-ttu-id="27984-264">Daha fazla bilgi için [nasıl yapılır: UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md)'un çalışma zamanı davranışını test edin.</span><span class="sxs-lookup"><span data-stu-id="27984-264">For more information, see [How to: Test the Run-Time Behavior of a UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>

<span data-ttu-id="27984-265">Denetiminizi kullanmak üzere yerleştirmek için bir form üzerinde barındırmanıza gerek duyarsınız.</span><span class="sxs-lookup"><span data-stu-id="27984-265">To put your control to use, you will need to host it on a form.</span></span> <span data-ttu-id="27984-266">Standart bir bileşik denetimde olduğu gibi, devralınan bir bileşik denetim tek başına olamaz ve bir formda ya da başka bir kapsayıcıda barındırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="27984-266">As with a standard composite control, an inherited composite control cannot stand alone and must be hosted in a form or other container.</span></span> <span data-ttu-id="27984-267">Daha büyük bir işlevsellik derinliğine sahipolduğundan,testetmekiçinekkodgereklidir.`ctlAlarmClock`</span><span class="sxs-lookup"><span data-stu-id="27984-267">Since `ctlAlarmClock` has a greater depth of functionality, additional code is required to test it.</span></span> <span data-ttu-id="27984-268">Bu yordamda, işlevselliğini `ctlAlarmClock`test etmek için basit bir program yazacaksınız.</span><span class="sxs-lookup"><span data-stu-id="27984-268">In this procedure, you will write a simple program to test the functionality of `ctlAlarmClock`.</span></span> <span data-ttu-id="27984-269">`AlarmTime` Özelliğini ayarlamakvegöstermekiçinkodyazacaksınızveonunkendiişlevlerinitestedecektir.`ctlAlarmClock`</span><span class="sxs-lookup"><span data-stu-id="27984-269">You will write code to set and display the `AlarmTime` property of `ctlAlarmClock`, and will test its inherent functions.</span></span>

#### <a name="to-build-and-add-your-control-to-a-test-form"></a><span data-ttu-id="27984-270">Denetimi derlemek ve test formuna eklemek için</span><span class="sxs-lookup"><span data-stu-id="27984-270">To build and add your control to a test form</span></span>

1. <span data-ttu-id="27984-271">Çözüm Gezgini ' de, **ctlClockLib**' a sağ tıklayın ve ardından **Oluştur**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="27984-271">In Solution Explorer, right-click **ctlClockLib**, and then click **Build**.</span></span>

2. <span data-ttu-id="27984-272">Çözüme yeni bir **Windows uygulaması** projesi ekleyin ve bunu `Test`adlandırın.</span><span class="sxs-lookup"><span data-stu-id="27984-272">Add a new **Windows Application** project to the solution, and name it `Test`.</span></span>

3. <span data-ttu-id="27984-273">Çözüm Gezgini, test projeniz için **Başvurular** düğümüne sağ tıklayın.</span><span class="sxs-lookup"><span data-stu-id="27984-273">In Solution Explorer, right-click the **References** node for your test project.</span></span> <span data-ttu-id="27984-274">Başvuru Ekle iletişim kutusunu göstermek için **Başvuru Ekle** ' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="27984-274">Click **Add Reference** to display the **Add Reference** dialog box.</span></span> <span data-ttu-id="27984-275">Etiketli **Projeler**sekmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="27984-275">Click the tab labeled **Projects**.</span></span> <span data-ttu-id="27984-276">Projeniz proje adı altında listelenir. `ctlClockLib`</span><span class="sxs-lookup"><span data-stu-id="27984-276">Your `ctlClockLib` project will be listed under **Project Name**.</span></span> <span data-ttu-id="27984-277">Başvuruyu test projesine eklemek için projeye çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="27984-277">Double-click the project to add the reference to the test project.</span></span>

4. <span data-ttu-id="27984-278">Çözüm Gezgini ' de **Test**' e sağ tıklayın ve ardından **Oluştur**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="27984-278">In Solution Explorer, right-click **Test**, and then click **Build**.</span></span>

5. <span data-ttu-id="27984-279">**Araç kutusunda** **ctlClockLib Components** düğümünü genişletin.</span><span class="sxs-lookup"><span data-stu-id="27984-279">In the **Toolbox**, expand the **ctlClockLib Components** node.</span></span>

6. <span data-ttu-id="27984-280">Formunuza bir kopyasını `ctlAlarmClock` eklemek için ctlAlarmClock öğesine çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="27984-280">Double-click **ctlAlarmClock** to add a copy of `ctlAlarmClock` to your form.</span></span>

7. <span data-ttu-id="27984-281">**Araç kutusunda**, formunuza bir <xref:System.Windows.Forms.DateTimePicker> denetim eklemek için **DateTimePicker** ' ı bulup çift tıklayın ve ardından **etiket**' e çift tıklayarak bir <xref:System.Windows.Forms.Label> denetim ekleyin.</span><span class="sxs-lookup"><span data-stu-id="27984-281">In the **Toolbox**, locate and double-click **DateTimePicker** to add a <xref:System.Windows.Forms.DateTimePicker> control to your form, and then add a <xref:System.Windows.Forms.Label> control by double-clicking **Label**.</span></span>

8. <span data-ttu-id="27984-282">Denetimleri form üzerinde uygun bir yerde konumlandırmak için fareyi kullanın.</span><span class="sxs-lookup"><span data-stu-id="27984-282">Use the mouse to position the controls in a convenient place on the form.</span></span>

9. <span data-ttu-id="27984-283">Bu denetimlerin özelliklerini aşağıdaki şekilde ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="27984-283">Set the properties of these controls in the following manner.</span></span>

    |<span data-ttu-id="27984-284">Denetim</span><span class="sxs-lookup"><span data-stu-id="27984-284">Control</span></span>|<span data-ttu-id="27984-285">Özellik</span><span class="sxs-lookup"><span data-stu-id="27984-285">Property</span></span>|<span data-ttu-id="27984-286">Değer</span><span class="sxs-lookup"><span data-stu-id="27984-286">Value</span></span>|
    |-------------|--------------|-----------|
    |`label1`|<span data-ttu-id="27984-287">**Metin**</span><span class="sxs-lookup"><span data-stu-id="27984-287">**Text**</span></span>|`(blank space)`|
    ||<span data-ttu-id="27984-288">**Ad**</span><span class="sxs-lookup"><span data-stu-id="27984-288">**Name**</span></span>|`lblTest`|
    |`dateTimePicker1`|<span data-ttu-id="27984-289">**Ad**</span><span class="sxs-lookup"><span data-stu-id="27984-289">**Name**</span></span>|`dtpTest`|
    ||<span data-ttu-id="27984-290">**Formatını**</span><span class="sxs-lookup"><span data-stu-id="27984-290">**Format**</span></span>|<xref:System.Windows.Forms.DateTimePickerFormat.Time>|

10. <span data-ttu-id="27984-291">Tasarımcıda **dtpTest**öğesine çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="27984-291">In the designer, double-click **dtpTest**.</span></span>

     <span data-ttu-id="27984-292">**Kod Düzenleyicisi** olarak `private void dtpTest_ValueChanged`açılır.</span><span class="sxs-lookup"><span data-stu-id="27984-292">The **Code Editor** opens to `private void dtpTest_ValueChanged`.</span></span>

11. <span data-ttu-id="27984-293">Kodu aşağıdakine benzer olacak şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="27984-293">Modify the code so that it resembles the following.</span></span>

    ```csharp
    private void dtpTest_ValueChanged(object sender, System.EventArgs e)
    {
        ctlAlarmClock1.AlarmTime = dtpTest.Value;
        ctlAlarmClock1.AlarmSet = true;
        lblTest.Text = "Alarm Time is " +
            ctlAlarmClock1.AlarmTime.ToShortTimeString();
    }
    ```

12. <span data-ttu-id="27984-294">Çözüm Gezgini ' de **Test**' e sağ tıklayın ve ardından **Başlangıç projesi olarak ayarla**' ya tıklayın.</span><span class="sxs-lookup"><span data-stu-id="27984-294">In Solution Explorer, right-click **Test**, and then click **Set as StartUp Project**.</span></span>

13. <span data-ttu-id="27984-295">Üzerinde **hata ayıklama** menüsünü tıklatın **hata ayıklamayı Başlat**.</span><span class="sxs-lookup"><span data-stu-id="27984-295">On the **Debug** menu, click **Start Debugging**.</span></span>

     <span data-ttu-id="27984-296">Test programı başlar.</span><span class="sxs-lookup"><span data-stu-id="27984-296">The test program starts.</span></span> <span data-ttu-id="27984-297">`ctlAlarmClock` Denetimde geçerli saatin güncelleştirildiğini ve başlangıç saatinin <xref:System.Windows.Forms.DateTimePicker> denetimde gösterildiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="27984-297">Note that the current time is updated in the `ctlAlarmClock` control, and that the starting time is shown in the <xref:System.Windows.Forms.DateTimePicker> control.</span></span>

14. <span data-ttu-id="27984-298">Saatin dakikalarının görüntülendiği yere tıklayın. <xref:System.Windows.Forms.DateTimePicker></span><span class="sxs-lookup"><span data-stu-id="27984-298">Click the <xref:System.Windows.Forms.DateTimePicker> where the minutes of the hour are displayed.</span></span>

15. <span data-ttu-id="27984-299">Klavyeyi kullanarak, tarafından `ctlAlarmClock`gösterilen geçerli saatten bir dakika daha büyük bir değer ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="27984-299">Using the keyboard, set a value for minutes that is one minute greater than the current time shown by `ctlAlarmClock`.</span></span>

     <span data-ttu-id="27984-300">Uyarı ayarının zamanı içinde `lblTest`gösterilir.</span><span class="sxs-lookup"><span data-stu-id="27984-300">The time for the alarm setting is shown in `lblTest`.</span></span> <span data-ttu-id="27984-301">Uyarı ayarı zamanına ulaşmak için, görüntülenecek sürenin bekleyin.</span><span class="sxs-lookup"><span data-stu-id="27984-301">Wait for the displayed time to reach the alarm setting time.</span></span> <span data-ttu-id="27984-302">Görünen süre, alarmın ayarlandığı zamana ulaştığında, `lblAlarm` Flash olur.</span><span class="sxs-lookup"><span data-stu-id="27984-302">When the displayed time reaches the time to which the alarm is set, the `lblAlarm` will flash.</span></span>

16. <span data-ttu-id="27984-303">Tıklayarak `btnAlarmOff`uyarıyı kapatın.</span><span class="sxs-lookup"><span data-stu-id="27984-303">Turn off the alarm by clicking `btnAlarmOff`.</span></span> <span data-ttu-id="27984-304">Şimdi uyarıyı sıfırlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="27984-304">You may now reset the alarm.</span></span>

     <span data-ttu-id="27984-305">Bu izlenecek yol, bir dizi temel kavramı kapsamıştır.</span><span class="sxs-lookup"><span data-stu-id="27984-305">This walkthrough has covered a number of key concepts.</span></span> <span data-ttu-id="27984-306">Bir bileşik denetim kapsayıcısına denetimleri ve bileşenleri birleştirerek bileşik bir denetim oluşturmayı öğrendiniz.</span><span class="sxs-lookup"><span data-stu-id="27984-306">You have learned to create a composite control by combining controls and components into a composite control container.</span></span> <span data-ttu-id="27984-307">Denetime Özellik eklemeyi ve özel işlevsellik uygulamak için kod yazmayı öğrendiniz.</span><span class="sxs-lookup"><span data-stu-id="27984-307">You have learned to add properties to your control, and to write code to implement custom functionality.</span></span> <span data-ttu-id="27984-308">Son bölümde, belirli bir bileşik denetimin işlevselliğini devralma yoluyla genişletmeyi ve bu yöntemleri geçersiz kılarak ana bilgisayar yöntemlerinin işlevselliğini değiştirmeyi öğrendiniz.</span><span class="sxs-lookup"><span data-stu-id="27984-308">In the last section, you learned to extend the functionality of a given composite control through inheritance, and to alter the functionality of host methods by overriding those methods.</span></span>

## <a name="see-also"></a><span data-ttu-id="27984-309">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="27984-309">See also</span></span>

- [<span data-ttu-id="27984-310">Özel Denetim Çeşitleri</span><span class="sxs-lookup"><span data-stu-id="27984-310">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
- [<span data-ttu-id="27984-311">Nasıl yapılır: Araç kutusu öğelerini Seç Iletişim kutusunda bir denetim görüntüle</span><span class="sxs-lookup"><span data-stu-id="27984-311">How to: Display a Control in the Choose Toolbox Items Dialog Box</span></span>](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)
- [<span data-ttu-id="27984-312">İzlenecek yol: Görsel ile Windows Forms denetiminden devralmaC#</span><span class="sxs-lookup"><span data-stu-id="27984-312">Walkthrough: Inheriting from a Windows Forms Control with Visual C#</span></span>](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)
