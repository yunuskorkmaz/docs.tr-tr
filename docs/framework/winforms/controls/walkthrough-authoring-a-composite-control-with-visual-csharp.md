---
title: 'İzlenecek yol: Visual C# İle Bileşik Denetim Yazma'
ms.date: 03/30/2017
dev_langs:
- CSharp
helpviewer_keywords:
- custom controls [C#]
- user controls [Windows Forms], creating with Visual C#
- UserControl class [Windows Forms], walkthroughs
- user controls [C#]
- custom controls [Windows Forms], creating
ms.assetid: f88481a8-c746-4a36-9479-374ce5f2e91f
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c1d9be77550b1255a24120c68f20d25640e0ebdf
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460634"
---
# <a name="walkthrough-author-a-composite-control-with-c"></a><span data-ttu-id="d4a66-102">İzlenecek yol: C\# ile bileşik denetim yazma</span><span class="sxs-lookup"><span data-stu-id="d4a66-102">Walkthrough: Author a Composite Control with C\#</span></span>

<span data-ttu-id="d4a66-103">Bileşik denetimler, özel grafik arabirimlerinin oluşturulup yeniden kullanılabilmesi için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="d4a66-103">Composite controls provide a means by which custom graphical interfaces can be created and reused.</span></span> <span data-ttu-id="d4a66-104">Bileşik denetim temelde görsel temsili olan bir bileşendir.</span><span class="sxs-lookup"><span data-stu-id="d4a66-104">A composite control is essentially a component with a visual representation.</span></span> <span data-ttu-id="d4a66-105">Bu nedenle, Kullanıcı girişini doğrulayarak, görüntü özelliklerini değiştirerek veya yazar için gereken diğer görevleri gerçekleştirerek işlevselliği genişletebilen bir veya daha fazla Windows Forms denetimi, bileşeni veya kod bloklarında bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="d4a66-105">As such, it might consist of one or more Windows Forms controls, components, or blocks of code that can extend functionality by validating user input, modifying display properties, or performing other tasks required by the author.</span></span> <span data-ttu-id="d4a66-106">Bileşik denetimler Windows Forms diğer denetimlerle aynı şekilde yerleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="d4a66-106">Composite controls can be placed on Windows Forms in the same manner as other controls.</span></span> <span data-ttu-id="d4a66-107">Bu izlenecek yolun ilk bölümünde `ctlClock`adlı basit bir bileşik denetim oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="d4a66-107">In the first part of this walkthrough, you create a simple composite control called `ctlClock`.</span></span> <span data-ttu-id="d4a66-108">İzlenecek yolun ikinci bölümünde devralma yoluyla `ctlClock` işlevlerini uzatamazsınız.</span><span class="sxs-lookup"><span data-stu-id="d4a66-108">In the second part of the walkthrough, you extend the functionality of `ctlClock` through inheritance.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="d4a66-109">Projeyi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="d4a66-109">Create the Project</span></span>

<span data-ttu-id="d4a66-110">Yeni bir proje oluşturduğunuzda, kök ad alanı, derleme adı ve proje adını ayarlamak için adını belirtin ve varsayılan bileşenin doğru ad alanında yer aldığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="d4a66-110">When you create a new project, you specify its name to set the root namespace, assembly name, and project name, and ensure that the default component will be in the correct namespace.</span></span>

### <a name="to-create-the-ctlclocklib-control-library-and-the-ctlclock-control"></a><span data-ttu-id="d4a66-111">CtlClockLib denetim kitaplığını ve ctlClock denetimini oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="d4a66-111">To create the ctlClockLib control library and the ctlClock control</span></span>

1. <span data-ttu-id="d4a66-112">Visual Studio 'da yeni bir **Windows Forms denetim kitaplığı** projesi oluşturun ve **ctlClockLib**olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="d4a66-112">In Visual Studio, create a new **Windows Forms Control Library** project, and name it **ctlClockLib**.</span></span>

     <span data-ttu-id="d4a66-113">`ctlClockLib`proje adı, varsayılan olarak kök ad alanına da atanır.</span><span class="sxs-lookup"><span data-stu-id="d4a66-113">The project name, `ctlClockLib`, is also assigned to the root namespace by default.</span></span> <span data-ttu-id="d4a66-114">Kök ad alanı, derlemedeki bileşenlerin adlarını nitelemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d4a66-114">The root namespace is used to qualify the names of components in the assembly.</span></span> <span data-ttu-id="d4a66-115">Örneğin, iki derleme `ctlClock`adlı bileşenler sağlamışsa, `ctlClock` bileşeninizi `ctlClockLib.ctlClock.` kullanarak belirtebilirsiniz</span><span class="sxs-lookup"><span data-stu-id="d4a66-115">For example, if two assemblies provide components named `ctlClock`, you can specify your `ctlClock` component using `ctlClockLib.ctlClock.`</span></span>

2. <span data-ttu-id="d4a66-116">**Çözüm Gezgini**' de, **UserControl1.cs**' a sağ tıklayın ve ardından **Yeniden Adlandır**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d4a66-116">In **Solution Explorer**, right-click **UserControl1.cs**, and then click **Rename**.</span></span> <span data-ttu-id="d4a66-117">Dosya adını `ctlClock.cs`değiştirin.</span><span class="sxs-lookup"><span data-stu-id="d4a66-117">Change the file name to `ctlClock.cs`.</span></span> <span data-ttu-id="d4a66-118">"UserControl1" kod öğesiyle tüm başvuruları yeniden adlandırmak isteyip istemediğiniz sorulduğunda **Evet** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d4a66-118">Click the **Yes** button when you are asked if you want to rename all references to the code element "UserControl1".</span></span>

    > [!NOTE]
    > <span data-ttu-id="d4a66-119">Varsayılan olarak, bileşik bir denetim sistem tarafından sunulan <xref:System.Windows.Forms.UserControl> sınıfından devralır.</span><span class="sxs-lookup"><span data-stu-id="d4a66-119">By default, a composite control inherits from the <xref:System.Windows.Forms.UserControl> class provided by the system.</span></span> <span data-ttu-id="d4a66-120"><xref:System.Windows.Forms.UserControl> sınıfı tüm bileşik denetimlerin gerektirdiği işlevselliği sağlar ve standart yöntemler ve özellikler uygular.</span><span class="sxs-lookup"><span data-stu-id="d4a66-120">The <xref:System.Windows.Forms.UserControl> class provides functionality required by all composite controls, and implements standard methods and properties.</span></span>

3. <span data-ttu-id="d4a66-121">Projeyi kaydetmek için **Dosya** menüsünde **Tümünü Kaydet** ' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d4a66-121">On the **File** menu, click **Save All** to save the project.</span></span>

## <a name="add-windows-controls-and-components-to-the-composite-control"></a><span data-ttu-id="d4a66-122">Bileşik denetime Windows denetimleri ve bileşenleri ekleme</span><span class="sxs-lookup"><span data-stu-id="d4a66-122">Add Windows Controls and Components to the Composite Control</span></span>

<span data-ttu-id="d4a66-123">Görsel arabirim, bileşik denetiminizin temel bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="d4a66-123">A visual interface is an essential part of your composite control.</span></span> <span data-ttu-id="d4a66-124">Bu görsel arabirim, tasarımcı yüzeyine bir veya daha fazla Windows denetimi eklenerek uygulanır.</span><span class="sxs-lookup"><span data-stu-id="d4a66-124">This visual interface is implemented by the addition of one or more Windows controls to the designer surface.</span></span> <span data-ttu-id="d4a66-125">Aşağıdaki gösteride, Windows denetimlerini bileşik denetiminizle birleştirirsiniz ve işlevselliği uygulamak için kod yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d4a66-125">In the following demonstration, you will incorporate Windows controls into your composite control and write code to implement functionality.</span></span>

### <a name="to-add-a-label-and-a-timer-to-your-composite-control"></a><span data-ttu-id="d4a66-126">Bileşik denetilemenize bir etiket ve süreölçer eklemek için</span><span class="sxs-lookup"><span data-stu-id="d4a66-126">To add a Label and a Timer to your composite control</span></span>

1. <span data-ttu-id="d4a66-127">**Çözüm Gezgini**' de, **ctlClock.cs**' a sağ tıklayın ve ardından **tasarımcıyı görüntüle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d4a66-127">In **Solution Explorer**, right-click **ctlClock.cs**, and then click **View Designer**.</span></span>

2. <span data-ttu-id="d4a66-128">**Araç kutusunda** **ortak denetimler** düğümünü genişletin ve ardından **etiket**' e çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d4a66-128">In the **Toolbox**, expand the **Common Controls** node, and then double-click **Label**.</span></span>

     <span data-ttu-id="d4a66-129">Tasarımcı yüzeyine `label1` adlı <xref:System.Windows.Forms.Label> bir denetim denetime eklenir.</span><span class="sxs-lookup"><span data-stu-id="d4a66-129">A <xref:System.Windows.Forms.Label> control named `label1` is added to your control on the designer surface.</span></span>

3. <span data-ttu-id="d4a66-130">Tasarımcıda **Label1**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d4a66-130">In the designer, click **label1**.</span></span> <span data-ttu-id="d4a66-131">Özellikler penceresi, aşağıdaki özellikleri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d4a66-131">In the Properties window, set the following properties.</span></span>

    |<span data-ttu-id="d4a66-132">Özellik</span><span class="sxs-lookup"><span data-stu-id="d4a66-132">Property</span></span>|<span data-ttu-id="d4a66-133">Değiştir</span><span class="sxs-lookup"><span data-stu-id="d4a66-133">Change to</span></span>|
    |--------------|---------------|
    |<span data-ttu-id="d4a66-134">**Ad**</span><span class="sxs-lookup"><span data-stu-id="d4a66-134">**Name**</span></span>|`lblDisplay`|
    |<span data-ttu-id="d4a66-135">**Metin**</span><span class="sxs-lookup"><span data-stu-id="d4a66-135">**Text**</span></span>|`(blank space)`|
    |<span data-ttu-id="d4a66-136">**TextAlign**</span><span class="sxs-lookup"><span data-stu-id="d4a66-136">**TextAlign**</span></span>|`MiddleCenter`|
    |<span data-ttu-id="d4a66-137">**Yazı tipi. boyutu**</span><span class="sxs-lookup"><span data-stu-id="d4a66-137">**Font.Size**</span></span>|`14`|

4. <span data-ttu-id="d4a66-138">**Araç kutusunda**, **Bileşenler** düğümünü genişletin ve ardından **Zamanlayıcı**' ya çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d4a66-138">In the **Toolbox**, expand the **Components** node, and then double-click **Timer**.</span></span>

     <span data-ttu-id="d4a66-139"><xref:System.Windows.Forms.Timer> bir bileşen olduğundan, çalışma zamanında görsel temsili yoktur.</span><span class="sxs-lookup"><span data-stu-id="d4a66-139">Because a <xref:System.Windows.Forms.Timer> is a component, it has no visual representation at run time.</span></span> <span data-ttu-id="d4a66-140">Bu nedenle, tasarımcı yüzeyindeki denetimlerde görünmez, ancak **Bileşen tasarımcısında** (tasarımcı yüzeyinin altındaki bir tepsi) değil.</span><span class="sxs-lookup"><span data-stu-id="d4a66-140">Therefore, it does not appear with the controls on the designer surface, but rather in the **Component Designer** (a tray at the bottom of the designer surface).</span></span>

5. <span data-ttu-id="d4a66-141">**Bileşen tasarımcısında**, **Süreölçer1**' a tıklayın ve ardından <xref:System.Windows.Forms.Timer.Interval%2A> özelliğini `1000` ve <xref:System.Windows.Forms.Timer.Enabled%2A> özelliğini `true`olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d4a66-141">In the **Component Designer**, click **timer1**, and then set the <xref:System.Windows.Forms.Timer.Interval%2A> property to `1000` and the <xref:System.Windows.Forms.Timer.Enabled%2A> property to `true`.</span></span>

     <span data-ttu-id="d4a66-142"><xref:System.Windows.Forms.Timer.Interval%2A> özelliği, <xref:System.Windows.Forms.Timer> bileşeni işaret eden sıklığı denetler.</span><span class="sxs-lookup"><span data-stu-id="d4a66-142">The <xref:System.Windows.Forms.Timer.Interval%2A> property controls the frequency with which the <xref:System.Windows.Forms.Timer> component ticks.</span></span> <span data-ttu-id="d4a66-143">Her zaman `timer1` her seferinde, `timer1_Tick` olayında kodu çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="d4a66-143">Each time `timer1` ticks, it runs the code in the `timer1_Tick` event.</span></span> <span data-ttu-id="d4a66-144">Aralık, zaman işaretleri arasındaki milisaniye sayısını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d4a66-144">The interval represents the number of milliseconds between ticks.</span></span>

6. <span data-ttu-id="d4a66-145">**Bileşen tasarımcısında**, `ctlClock`için `timer1_Tick` olayına gitmek için **Süreölçer1** öğesine çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d4a66-145">In the **Component Designer**, double-click **timer1** to go to the `timer1_Tick` event for `ctlClock`.</span></span>

7. <span data-ttu-id="d4a66-146">Kodu aşağıdaki kod örneğine benzer olacak şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="d4a66-146">Modify the code so that it resembles the following code sample.</span></span> <span data-ttu-id="d4a66-147">`private` erişim değiştiricisini `protected`olarak değiştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="d4a66-147">Be sure to change the access modifier from `private` to `protected`.</span></span>

    ```csharp
    protected void timer1_Tick(object sender, System.EventArgs e)
    {
        // Causes the label to display the current time.
        lblDisplay.Text = DateTime.Now.ToLongTimeString();
    }
    ```

     <span data-ttu-id="d4a66-148">Bu kod, geçerli saatin `lblDisplay`görüntülenmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="d4a66-148">This code will cause the current time to be shown in `lblDisplay`.</span></span> <span data-ttu-id="d4a66-149">`timer1` aralığı `1000`olarak ayarlandığı için, bu olay her bin milisaniyede bir gerçekleşeceğinden, bu nedenle her saniye geçerli saati güncelliyor.</span><span class="sxs-lookup"><span data-stu-id="d4a66-149">Because the interval of `timer1` was set to `1000`, this event will occur every thousand milliseconds, thus updating the current time every second.</span></span>

8. <span data-ttu-id="d4a66-150">Yöntemi, `virtual` anahtar sözcüğüyle geçersiz kılınabilir olacak şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="d4a66-150">Modify the method to be overridable with the `virtual` keyword.</span></span> <span data-ttu-id="d4a66-151">Daha fazla bilgi için aşağıdaki "Kullanıcı denetiminden devralma" bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="d4a66-151">For more information, see the  "Inheriting from a User Control" section below.</span></span>

    ```csharp
    protected virtual void timer1_Tick(object sender, System.EventArgs e)
    ```

9. <span data-ttu-id="d4a66-152">Projeyi kaydetmek için **Dosya** menüsünde **Tümünü Kaydet** ' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d4a66-152">On the **File** menu, click **Save All** to save the project.</span></span>

## <a name="add-properties-to-the-composite-control"></a><span data-ttu-id="d4a66-153">Bileşik denetime özellikler ekleme</span><span class="sxs-lookup"><span data-stu-id="d4a66-153">Add Properties to the Composite Control</span></span>

<span data-ttu-id="d4a66-154">Saat denetiminiz artık, her biri kendi kendine ait özellikler kümesiyle bir <xref:System.Windows.Forms.Label> denetimini ve <xref:System.Windows.Forms.Timer> bileşenini kapsüller.</span><span class="sxs-lookup"><span data-stu-id="d4a66-154">Your clock control now encapsulates a <xref:System.Windows.Forms.Label> control and a <xref:System.Windows.Forms.Timer> component, each with its own set of inherent properties.</span></span> <span data-ttu-id="d4a66-155">Bu denetimlerin tek tek özelliklerine denetiminizin sonraki kullanıcıları tarafından erişilemese de, uygun kod bloklarını yazarak özel özellikler oluşturabilir ve kullanıma sunabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d4a66-155">While the individual properties of these controls will not be accessible to subsequent users of your control, you can create and expose custom properties by writing the appropriate blocks of code.</span></span> <span data-ttu-id="d4a66-156">Aşağıdaki yordamda, denetime, kullanıcının arka plan ve metin rengini değiştirmesini sağlayan özellikler ekleyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="d4a66-156">In the following procedure, you will add properties to your control that enable the user to change the color of the background and text.</span></span>

### <a name="to-add-a-property-to-your-composite-control"></a><span data-ttu-id="d4a66-157">Bileşik denetimi bir özellik eklemek için</span><span class="sxs-lookup"><span data-stu-id="d4a66-157">To add a property to your composite control</span></span>

1. <span data-ttu-id="d4a66-158">**Çözüm Gezgini**' de, **ctlClock.cs**' a sağ tıklayın ve ardından **kodu görüntüle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d4a66-158">In **Solution Explorer**, right-click **ctlClock.cs**, and then click **View Code**.</span></span>

     <span data-ttu-id="d4a66-159">Denetiminizin **Kod Düzenleyicisi** açılır.</span><span class="sxs-lookup"><span data-stu-id="d4a66-159">The **Code Editor** for your control opens.</span></span>

2. <span data-ttu-id="d4a66-160">`public partial class ctlClock` ifadesini bulun.</span><span class="sxs-lookup"><span data-stu-id="d4a66-160">Locate the `public partial class ctlClock` statement.</span></span> <span data-ttu-id="d4a66-161">Açma küme ayracı (`{)`) altında aşağıdaki kodu yazın.</span><span class="sxs-lookup"><span data-stu-id="d4a66-161">Beneath the opening brace (`{)`, type the following code.</span></span>

    ```csharp
    private Color colFColor;
    private Color colBColor;
    ```

     <span data-ttu-id="d4a66-162">Bu deyimler, oluşturmak üzere olduğunuz özelliklerin değerlerini depolamak için kullanacağınız özel değişkenleri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d4a66-162">These statements create the private variables that you will use to store the values for the properties you are about to create.</span></span>

3. <span data-ttu-id="d4a66-163">Aşağıdaki kodu adım 2 ' den değişken bildirimlerinin altına girin veya yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="d4a66-163">Enter or paste the following code beneath the variable declarations from step 2.</span></span>

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

     <span data-ttu-id="d4a66-164">Yukarıdaki kod, bu denetimin sonraki kullanıcıları tarafından kullanılabilen `ClockForeColor` ve `ClockBackColor`iki özel özellik oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d4a66-164">The preceding code makes two custom properties, `ClockForeColor` and `ClockBackColor`, available to subsequent users of this control.</span></span> <span data-ttu-id="d4a66-165">`get` ve `set` deyimleri, özellik değerini depolamak ve almak için, özelliği de özelliğine uygun işlevselliği uygulamak için de kod sağlar.</span><span class="sxs-lookup"><span data-stu-id="d4a66-165">The `get` and `set` statements provide for storage and retrieval of the property value, as well as code to implement functionality appropriate to the property.</span></span>

4. <span data-ttu-id="d4a66-166">Projeyi kaydetmek için **Dosya** menüsünde **Tümünü Kaydet** ' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d4a66-166">On the **File** menu, click **Save All** to save the project.</span></span>

## <a name="test-the-control"></a><span data-ttu-id="d4a66-167">Denetimi test etme</span><span class="sxs-lookup"><span data-stu-id="d4a66-167">Test the Control</span></span>

<span data-ttu-id="d4a66-168">Denetimler tek başına uygulamalar değildir; Bunlar bir kapsayıcıda barındırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d4a66-168">Controls are not stand-alone applications; they must be hosted in a container.</span></span> <span data-ttu-id="d4a66-169">Denetiminizin çalışma zamanı davranışını test edin ve özelliklerini **UserControl Test kapsayıcısı**ile çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="d4a66-169">Test your control's run-time behavior and exercise its properties with the **UserControl Test Container**.</span></span> <span data-ttu-id="d4a66-170">Daha fazla bilgi için bkz. [nasıl yapılır: bir UserControl 'un çalışma zamanı davranışını test etme](how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span><span class="sxs-lookup"><span data-stu-id="d4a66-170">For more information, see [How to: Test the Run-Time Behavior of a UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>

### <a name="to-test-your-control"></a><span data-ttu-id="d4a66-171">Denetiminizi test etmek için</span><span class="sxs-lookup"><span data-stu-id="d4a66-171">To test your control</span></span>

1. <span data-ttu-id="d4a66-172">Projeyi derlemek için **F5** tuşuna basın ve denetimi **UserControl Test kapsayıcısında**çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="d4a66-172">Press **F5** to build the project and run your control in the **UserControl Test Container**.</span></span>

2. <span data-ttu-id="d4a66-173">Test kapsayıcısının özellik kılavuzunda `ClockBackColor` özelliğini bulun ve ardından renk paletini göstermek için özelliği seçin.</span><span class="sxs-lookup"><span data-stu-id="d4a66-173">In the test container's property grid, locate the `ClockBackColor` property, and then select the property to display the color palette.</span></span>

3. <span data-ttu-id="d4a66-174">Tıklayarak bir renk seçin.</span><span class="sxs-lookup"><span data-stu-id="d4a66-174">Choose a color by clicking it.</span></span>

   <span data-ttu-id="d4a66-175">Denetiminizin arka plan rengi, seçtiğiniz renge değişir.</span><span class="sxs-lookup"><span data-stu-id="d4a66-175">The background color of your control changes to the color you selected.</span></span>

4. <span data-ttu-id="d4a66-176">`ClockForeColor` özelliğinin beklendiği gibi çalıştığını doğrulamak için benzer bir olay dizisi kullanın.</span><span class="sxs-lookup"><span data-stu-id="d4a66-176">Use a similar sequence of events to verify that the `ClockForeColor` property is functioning as expected.</span></span>

   <span data-ttu-id="d4a66-177">Bu bölümde ve önceki bölümlerde, bileşik denetim biçiminde özel işlevsellik sağlamak için bileşenlerin ve Windows denetimlerinin kod ve paketleme ile nasıl birleştirilebileceği gördünüz.</span><span class="sxs-lookup"><span data-stu-id="d4a66-177">In this section and the preceding sections, you have seen how components and Windows controls can be combined with code and packaging to provide custom functionality in the form of a composite control.</span></span> <span data-ttu-id="d4a66-178">Birleşik denetidiklerinizin özelliklerini açığa çıkarmak ve tamamlandıktan sonra denetiminizi test etmek için öğrendiniz.</span><span class="sxs-lookup"><span data-stu-id="d4a66-178">You have learned to expose properties in your composite control, and how to test your control after it is complete.</span></span> <span data-ttu-id="d4a66-179">Sonraki bölümde, temel olarak `ctlClock` kullanarak devralınan bileşik denetim oluşturmayı öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="d4a66-179">In the next section you will learn how to construct an inherited composite control using `ctlClock` as a base.</span></span>

## <a name="inherit-from-a-composite-control"></a><span data-ttu-id="d4a66-180">Bileşik denetimden devralma</span><span class="sxs-lookup"><span data-stu-id="d4a66-180">Inherit from a Composite Control</span></span>

<span data-ttu-id="d4a66-181">Önceki bölümlerde, Windows denetimlerini, bileşenleri ve kodu yeniden kullanılabilir bileşik denetimlere nasıl birleştirebileceğinizi öğrendiniz.</span><span class="sxs-lookup"><span data-stu-id="d4a66-181">In the previous sections, you learned how to combine Windows controls, components, and code into reusable composite controls.</span></span> <span data-ttu-id="d4a66-182">Bileşik denetiminiz artık diğer denetimlerin derlenme temeli olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d4a66-182">Your composite control can now be used as a base upon which other controls can be built.</span></span> <span data-ttu-id="d4a66-183">Temel sınıftan bir sınıfın türeme işlemi *Devralma*olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="d4a66-183">The process of deriving a class from a base class is called *inheritance*.</span></span> <span data-ttu-id="d4a66-184">Bu bölümde `ctlAlarmClock`adlı bir bileşik denetim oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="d4a66-184">In this section, you will create a composite control called `ctlAlarmClock`.</span></span> <span data-ttu-id="d4a66-185">Bu denetim, `ctlClock`üst denetiminden türetilecektir.</span><span class="sxs-lookup"><span data-stu-id="d4a66-185">This control will be derived from its parent control, `ctlClock`.</span></span> <span data-ttu-id="d4a66-186">Üst yöntemleri geçersiz kılarak ve yeni yöntemler ve özellikler ekleyerek `ctlClock` işlevselliğini genişletmeyi öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="d4a66-186">You will learn to extend the functionality of `ctlClock` by overriding parent methods and adding new methods and properties.</span></span>

<span data-ttu-id="d4a66-187">Devralınan bir denetim oluşturmanın ilk adımı onu üst öğesinden türemektir.</span><span class="sxs-lookup"><span data-stu-id="d4a66-187">The first step in creating an inherited control is to derive it from its parent.</span></span> <span data-ttu-id="d4a66-188">Bu eylem, üst denetimin tüm özelliklerine, yöntemlerine ve grafiksel özelliklerine sahip yeni bir denetim oluşturur, ancak yeni veya değiştirilmiş işlevselliğin eklenmesi için temel olarak da davranabilir.</span><span class="sxs-lookup"><span data-stu-id="d4a66-188">This action creates a new control that has all of the properties, methods, and graphical characteristics of the parent control, but can also act as a base for the addition of new or modified functionality.</span></span>

### <a name="to-create-the-inherited-control"></a><span data-ttu-id="d4a66-189">Devralınan denetimi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="d4a66-189">To create the inherited control</span></span>

1. <span data-ttu-id="d4a66-190">**Çözüm Gezgini**' de, **ctlClockLib**' a sağ tıklayın, **Ekle**' nin üzerine gelin ve **Kullanıcı denetimi**' ne tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d4a66-190">In **Solution Explorer**, right-click **ctlClockLib**, point to **Add**, and then click **User Control**.</span></span>

     <span data-ttu-id="d4a66-191">**Yeni öğe Ekle** iletişim kutusu açılır.</span><span class="sxs-lookup"><span data-stu-id="d4a66-191">The **Add New Item** dialog box opens.</span></span>

2. <span data-ttu-id="d4a66-192">**Devralınan Kullanıcı denetimi** şablonunu seçin.</span><span class="sxs-lookup"><span data-stu-id="d4a66-192">Select the **Inherited User Control** template.</span></span>

3. <span data-ttu-id="d4a66-193">**Ad** kutusuna `ctlAlarmClock.cs`yazın ve ardından **Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d4a66-193">In the **Name** box, type `ctlAlarmClock.cs`, and then click **Add**.</span></span>

     <span data-ttu-id="d4a66-194">**Devralma Seçicisi** iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="d4a66-194">The **Inheritance Picker** dialog box appears.</span></span>

4. <span data-ttu-id="d4a66-195">**Bileşen adı**altında **ctlClock**' ye çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d4a66-195">Under **Component Name**, double-click **ctlClock**.</span></span>

5. <span data-ttu-id="d4a66-196">**Çözüm Gezgini**, geçerli projelere göz atabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d4a66-196">In **Solution Explorer**, browse through the current projects.</span></span>

    > [!NOTE]
    > <span data-ttu-id="d4a66-197">Geçerli projeye **ctlAlarmClock.cs** adlı bir dosya eklendi.</span><span class="sxs-lookup"><span data-stu-id="d4a66-197">A file called **ctlAlarmClock.cs** has been added to the current project.</span></span>

### <a name="add-the-alarm-properties"></a><span data-ttu-id="d4a66-198">Alarm özelliklerini ekleme</span><span class="sxs-lookup"><span data-stu-id="d4a66-198">Add the Alarm Properties</span></span>

<span data-ttu-id="d4a66-199">Özellikler, devralınan bir denetime, Birleşik bir denetime eklendikçe aynı şekilde eklenir.</span><span class="sxs-lookup"><span data-stu-id="d4a66-199">Properties are added to an inherited control in the same way they are added to a composite control.</span></span> <span data-ttu-id="d4a66-200">Şimdi, denetimizin için iki özellik eklemek üzere özellik bildirimi sözdizimini kullanacaksınız: `AlarmTime`, alarmın bitiş tarihini ve saatini depolayan ve alarmın ayarlandığını belirten `AlarmSet`.</span><span class="sxs-lookup"><span data-stu-id="d4a66-200">You will now use the property declaration syntax to add two properties to your control: `AlarmTime`, which will store the value of the date and time the alarm is to go off, and `AlarmSet`, which will indicate whether the alarm is set.</span></span>

#### <a name="to-add-properties-to-your-composite-control"></a><span data-ttu-id="d4a66-201">Bileşik denetimi özellikler eklemek için</span><span class="sxs-lookup"><span data-stu-id="d4a66-201">To add properties to your composite control</span></span>

1. <span data-ttu-id="d4a66-202">**Çözüm Gezgini**' de, **ctlAlarmClock**' a sağ tıklayın ve ardından **kodu görüntüle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d4a66-202">In **Solution Explorer**, right-click **ctlAlarmClock**, and then click **View Code**.</span></span>

2. <span data-ttu-id="d4a66-203">`public class` ifadesini bulun.</span><span class="sxs-lookup"><span data-stu-id="d4a66-203">Locate the `public class` statement.</span></span> <span data-ttu-id="d4a66-204">Denetiminizin `ctlClockLib.ctlClock`devraldığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="d4a66-204">Note that your control inherits from `ctlClockLib.ctlClock`.</span></span> <span data-ttu-id="d4a66-205">Açma küme ayracı (`{)` deyimin altına aşağıdaki kodu yazın.</span><span class="sxs-lookup"><span data-stu-id="d4a66-205">Beneath the opening brace (`{)` statement, type the following code.</span></span>

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

### <a name="add-to-the-graphical-interface-of-the-control"></a><span data-ttu-id="d4a66-206">Denetimin grafik arabirimine Ekle</span><span class="sxs-lookup"><span data-stu-id="d4a66-206">Add to the Graphical Interface of the Control</span></span>

<span data-ttu-id="d4a66-207">Devralınan denetiminizin devraldığı denetimle özdeş bir görsel arabirimi vardır.</span><span class="sxs-lookup"><span data-stu-id="d4a66-207">Your inherited control has a visual interface that is identical to the control it inherits from.</span></span> <span data-ttu-id="d4a66-208">Kendi üst denetimiyle aynı bileşen denetimlerine sahip olur, ancak yapısal denetimlerin özellikleri özellikle gösterilmedikleri sürece kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="d4a66-208">It possesses the same constituent controls as its parent control, but the properties of the constituent controls will not be available unless they were specifically exposed.</span></span> <span data-ttu-id="d4a66-209">Devralınan bir bileşik denetimin grafik arabirimine, herhangi bir bileşik denetime ekleyeceğiniz şekilde ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d4a66-209">You may add to the graphical interface of an inherited composite control in the same manner as you would add to any composite control.</span></span> <span data-ttu-id="d4a66-210">Alarm saatinizin görsel arabirimine eklemeye devam etmek için, alarm bir işlem olduğunda Flash olacak bir etiket denetimi ekleyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="d4a66-210">To continue adding to your alarm clock's visual interface, you will add a label control that will flash when the alarm is sounding.</span></span>

#### <a name="to-add-the-label-control"></a><span data-ttu-id="d4a66-211">Etiket denetimi eklemek için</span><span class="sxs-lookup"><span data-stu-id="d4a66-211">To add the label control</span></span>

1. <span data-ttu-id="d4a66-212">**Çözüm Gezgini**' de, **ctlAlarmClock**' a sağ tıklayın ve ardından **tasarımcıyı görüntüle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d4a66-212">In **Solution Explorer**, right-click **ctlAlarmClock**, and then click **View Designer**.</span></span>

     <span data-ttu-id="d4a66-213">`ctlAlarmClock` Tasarımcısı ana pencerede açılır.</span><span class="sxs-lookup"><span data-stu-id="d4a66-213">The designer for `ctlAlarmClock` opens in the main window.</span></span>

2. <span data-ttu-id="d4a66-214">Denetimin görüntüleme bölümüne tıklayın ve Özellikler penceresi görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="d4a66-214">Click the display portion of the control, and view the Properties window.</span></span>

    > [!NOTE]
    > <span data-ttu-id="d4a66-215">Tüm özellikler görüntülenirken, soluk olurlar.</span><span class="sxs-lookup"><span data-stu-id="d4a66-215">While all the properties are displayed, they are dimmed.</span></span> <span data-ttu-id="d4a66-216">Bu özelliklerin `lblDisplay` yerel olduğunu ve Özellikler penceresi değiştirilemeyeceğini veya erişilmeyeceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="d4a66-216">This indicates that these properties are native to `lblDisplay` and cannot be modified or accessed in the Properties window.</span></span> <span data-ttu-id="d4a66-217">Varsayılan olarak, bileşik denetimde bulunan denetimler `private`ve özellikleri herhangi bir şekilde erişilebilir değildir.</span><span class="sxs-lookup"><span data-stu-id="d4a66-217">By default, controls contained in a composite control are `private`, and their properties are not accessible by any means.</span></span>

    > [!NOTE]
    > <span data-ttu-id="d4a66-218">Bileşik denetiminizin sonraki kullanıcılarının iç denetimlerine erişimi olmasını istiyorsanız, bunları `public` veya `protected`olarak bildirin.</span><span class="sxs-lookup"><span data-stu-id="d4a66-218">If you want subsequent users of your composite control to have access to its internal controls, declare them as `public` or `protected`.</span></span> <span data-ttu-id="d4a66-219">Bu, uygun kodu kullanarak bileşik denetilinizin içindeki denetimlerin özelliklerini ayarlamanıza ve değiştirmenize izin verir.</span><span class="sxs-lookup"><span data-stu-id="d4a66-219">This will allow you to set and modify properties of controls contained within your composite control by using the appropriate code.</span></span>

3. <span data-ttu-id="d4a66-220">Bileşik denetimi denetim <xref:System.Windows.Forms.Label> ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d4a66-220">Add a <xref:System.Windows.Forms.Label> control to your composite control.</span></span>

4. <span data-ttu-id="d4a66-221">Fareyi kullanarak, <xref:System.Windows.Forms.Label> denetimini ekran kutusunun hemen altına sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="d4a66-221">Using the mouse, drag the <xref:System.Windows.Forms.Label> control immediately beneath the display box.</span></span> <span data-ttu-id="d4a66-222">Özellikler penceresi, aşağıdaki özellikleri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d4a66-222">In the Properties window, set the following properties.</span></span>

    |<span data-ttu-id="d4a66-223">Özellik</span><span class="sxs-lookup"><span data-stu-id="d4a66-223">Property</span></span>|<span data-ttu-id="d4a66-224">Ayar</span><span class="sxs-lookup"><span data-stu-id="d4a66-224">Setting</span></span>|
    |--------------|-------------|
    |<span data-ttu-id="d4a66-225">**Ad**</span><span class="sxs-lookup"><span data-stu-id="d4a66-225">**Name**</span></span>|`lblAlarm`|
    |<span data-ttu-id="d4a66-226">**Metin**</span><span class="sxs-lookup"><span data-stu-id="d4a66-226">**Text**</span></span>|<span data-ttu-id="d4a66-227">**Alarm!**</span><span class="sxs-lookup"><span data-stu-id="d4a66-227">**Alarm!**</span></span>|
    |<span data-ttu-id="d4a66-228">**TextAlign**</span><span class="sxs-lookup"><span data-stu-id="d4a66-228">**TextAlign**</span></span>|`MiddleCenter`|
    |<span data-ttu-id="d4a66-229">**Görüne**</span><span class="sxs-lookup"><span data-stu-id="d4a66-229">**Visible**</span></span>|`false`|

### <a name="add-the-alarm-functionality"></a><span data-ttu-id="d4a66-230">Alarm Işlevlerini ekleme</span><span class="sxs-lookup"><span data-stu-id="d4a66-230">Add the Alarm Functionality</span></span>

<span data-ttu-id="d4a66-231">Önceki yordamlarda, bileşik denetiminizdeki alarm işlevselliğini etkinleştiren Özellikler ve bir denetim eklediniz.</span><span class="sxs-lookup"><span data-stu-id="d4a66-231">In the previous procedures, you added properties and a control that will enable alarm functionality in your composite control.</span></span> <span data-ttu-id="d4a66-232">Bu yordamda, geçerli saati alarm zamanına göre karşılaştırmak için kod ekleyeceksiniz ve aynı ise, bir alarm Flash için de aynı olduğunda.</span><span class="sxs-lookup"><span data-stu-id="d4a66-232">In this procedure, you will add code to compare the current time to the alarm time and, if they are the same, to flash an alarm.</span></span> <span data-ttu-id="d4a66-233">`ctlClock` `timer1_Tick` yöntemini geçersiz kılarak ve buna ek kod ekleyerek, `ctlClock`tüm özelliklerini korurken `ctlAlarmClock` özelliğini genişletebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d4a66-233">By overriding the `timer1_Tick` method of `ctlClock` and adding additional code to it, you will extend the capability of `ctlAlarmClock` while retaining all of the inherent functionality of `ctlClock`.</span></span>

#### <a name="to-override-the-timer1_tick-method-of-ctlclock"></a><span data-ttu-id="d4a66-234">CtlClock timer1_Tick yöntemini geçersiz kılmak için</span><span class="sxs-lookup"><span data-stu-id="d4a66-234">To override the timer1_Tick method of ctlClock</span></span>

1. <span data-ttu-id="d4a66-235">**Kod düzenleyicisinde**`private bool blnAlarmSet;` ifadesini bulun.</span><span class="sxs-lookup"><span data-stu-id="d4a66-235">In the **Code Editor**, locate the `private bool blnAlarmSet;` statement.</span></span> <span data-ttu-id="d4a66-236">Hemen hemen altına aşağıdaki ifadeyi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d4a66-236">Immediately beneath it, add the following statement.</span></span>

    ```csharp
    private bool blnColorTicker;
    ```

2. <span data-ttu-id="d4a66-237">**Kod Düzenleyicisi**'nde, sınıfın sonundaki kapanış ayracını (`})` bulun.</span><span class="sxs-lookup"><span data-stu-id="d4a66-237">In the **Code Editor**, locate the closing brace (`})` at the end of the class.</span></span> <span data-ttu-id="d4a66-238">Küme ayracından hemen önce aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d4a66-238">Just before the brace, add the following code.</span></span>

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

     <span data-ttu-id="d4a66-239">Bu kodun eklenmesi birkaç görevi gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="d4a66-239">The addition of this code accomplishes several tasks.</span></span> <span data-ttu-id="d4a66-240">`override` ifade, denetimi temel denetimden devralınan yöntemin yerine bu yöntemi kullanacak şekilde yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="d4a66-240">The `override` statement directs the control to use this method in place of the method that was inherited from the base control.</span></span> <span data-ttu-id="d4a66-241">Bu yöntem çağrıldığında, özgün denetimde dahil edilen tüm işlevlerin Bu denetimde yeniden üretildiğinden emin olmak için `base.timer1_Tick` ifadesini çağırarak geçersiz kıldığından yöntemi çağırır.</span><span class="sxs-lookup"><span data-stu-id="d4a66-241">When this method is called, it calls the method it overrides by invoking the `base.timer1_Tick` statement, ensuring that all of the functionality incorporated in the original control is reproduced in this control.</span></span> <span data-ttu-id="d4a66-242">Daha sonra alarm işlevselliğini birleştirmek için ek kod çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="d4a66-242">It then runs additional code to incorporate the alarm functionality.</span></span> <span data-ttu-id="d4a66-243">Uyarı oluştuğunda yanıp sönen bir etiket denetimi görünür.</span><span class="sxs-lookup"><span data-stu-id="d4a66-243">A flashing label control will appear when the alarm occurs.</span></span>

     <span data-ttu-id="d4a66-244">Alarm saati denetiminiz neredeyse tamamlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="d4a66-244">Your alarm clock control is almost complete.</span></span> <span data-ttu-id="d4a66-245">Kalan tek şey, devre dışı bırakmak için bir yol uygulamaktır.</span><span class="sxs-lookup"><span data-stu-id="d4a66-245">The only thing that remains is to implement a way to turn it off.</span></span> <span data-ttu-id="d4a66-246">Bunu yapmak için `lblAlarm_Click` yöntemine kod ekleyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="d4a66-246">To do this, you will add code to the `lblAlarm_Click` method.</span></span>

#### <a name="to-implement-the-shutoff-method"></a><span data-ttu-id="d4a66-247">Shutoff yöntemini uygulamak için</span><span class="sxs-lookup"><span data-stu-id="d4a66-247">To implement the shutoff method</span></span>

1. <span data-ttu-id="d4a66-248">**Çözüm Gezgini**' de, **ctlAlarmClock.cs**' a sağ tıklayın ve ardından **tasarımcıyı görüntüle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d4a66-248">In **Solution Explorer**, right-click **ctlAlarmClock.cs**, and then click **View Designer**.</span></span>

     <span data-ttu-id="d4a66-249">Tasarımcı açılır.</span><span class="sxs-lookup"><span data-stu-id="d4a66-249">The designer opens.</span></span>

2. <span data-ttu-id="d4a66-250">Denetime düğme ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d4a66-250">Add a button to the control.</span></span> <span data-ttu-id="d4a66-251">Düğmenin özelliklerini aşağıdaki gibi ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d4a66-251">Set the properties of the button as follows.</span></span>

    |<span data-ttu-id="d4a66-252">Özellik</span><span class="sxs-lookup"><span data-stu-id="d4a66-252">Property</span></span>|<span data-ttu-id="d4a66-253">Değer</span><span class="sxs-lookup"><span data-stu-id="d4a66-253">Value</span></span>|
    |--------------|-----------|
    |<span data-ttu-id="d4a66-254">**Ad**</span><span class="sxs-lookup"><span data-stu-id="d4a66-254">**Name**</span></span>|`btnAlarmOff`|
    |<span data-ttu-id="d4a66-255">**Metin**</span><span class="sxs-lookup"><span data-stu-id="d4a66-255">**Text**</span></span>|<span data-ttu-id="d4a66-256">**Alarmı devre dışı bırak**</span><span class="sxs-lookup"><span data-stu-id="d4a66-256">**Disable Alarm**</span></span>|

3. <span data-ttu-id="d4a66-257">Tasarımcı 'da, **btnAlarmOff**' a çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d4a66-257">In the designer, double-click **btnAlarmOff**.</span></span>

     <span data-ttu-id="d4a66-258">**Kod düzenleyicisi** `private void btnAlarmOff_Click` satırı olarak açılır.</span><span class="sxs-lookup"><span data-stu-id="d4a66-258">The **Code Editor** opens to the `private void btnAlarmOff_Click` line.</span></span>

4. <span data-ttu-id="d4a66-259">Bu yöntemi, aşağıdaki koda benzer olacak şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="d4a66-259">Modify this method so that it resembles the following code.</span></span>

    ```csharp
    private void btnAlarmOff_Click(object sender, System.EventArgs e)
    {
        // Turns off the alarm.
        AlarmSet = false;
        // Hides the flashing label.
        lblAlarm.Visible = false;
    }
    ```

5. <span data-ttu-id="d4a66-260">Projeyi kaydetmek için **Dosya** menüsünde **Tümünü Kaydet** ' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d4a66-260">On the **File** menu, click **Save All** to save the project.</span></span>

### <a name="use-the-inherited-control-on-a-form"></a><span data-ttu-id="d4a66-261">Bir form üzerinde devralınan denetimi kullanma</span><span class="sxs-lookup"><span data-stu-id="d4a66-261">Use the Inherited Control on a Form</span></span>

<span data-ttu-id="d4a66-262">Devralınan denetiminizi, temel sınıf denetimini sınadığınız şekilde test edebilirsiniz, `ctlClock`: **F5** tuşuna basarak projeyi oluşturun ve denetiminizi **UserControl Test kapsayıcısında**çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="d4a66-262">You can test your inherited control the same way you tested the base class control, `ctlClock`: Press **F5** to build the project and run your control in the **UserControl Test Container**.</span></span> <span data-ttu-id="d4a66-263">Daha fazla bilgi için bkz. [nasıl yapılır: bir UserControl 'un çalışma zamanı davranışını test etme](how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span><span class="sxs-lookup"><span data-stu-id="d4a66-263">For more information, see [How to: Test the Run-Time Behavior of a UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>

<span data-ttu-id="d4a66-264">Denetiminizi kullanmak üzere yerleştirmek için bir form üzerinde barındırmanıza gerek duyarsınız.</span><span class="sxs-lookup"><span data-stu-id="d4a66-264">To put your control to use, you will need to host it on a form.</span></span> <span data-ttu-id="d4a66-265">Standart bir bileşik denetimde olduğu gibi, devralınan bir bileşik denetim tek başına olamaz ve bir formda ya da başka bir kapsayıcıda barındırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d4a66-265">As with a standard composite control, an inherited composite control cannot stand alone and must be hosted in a form or other container.</span></span> <span data-ttu-id="d4a66-266">`ctlAlarmClock` daha kapsamlı bir işlevselliğe sahip olduğundan, test etmek için ek kod gereklidir.</span><span class="sxs-lookup"><span data-stu-id="d4a66-266">Since `ctlAlarmClock` has a greater depth of functionality, additional code is required to test it.</span></span> <span data-ttu-id="d4a66-267">Bu yordamda, `ctlAlarmClock`işlevlerini test etmek için basit bir program yazacaksınız.</span><span class="sxs-lookup"><span data-stu-id="d4a66-267">In this procedure, you will write a simple program to test the functionality of `ctlAlarmClock`.</span></span> <span data-ttu-id="d4a66-268">`ctlAlarmClock``AlarmTime` özelliğini ayarlamak ve göstermek için kod yazacaksınız ve onun kendisine ait işlevlerini test edecektir.</span><span class="sxs-lookup"><span data-stu-id="d4a66-268">You will write code to set and display the `AlarmTime` property of `ctlAlarmClock`, and will test its inherent functions.</span></span>

#### <a name="to-build-and-add-your-control-to-a-test-form"></a><span data-ttu-id="d4a66-269">Denetimi derlemek ve test formuna eklemek için</span><span class="sxs-lookup"><span data-stu-id="d4a66-269">To build and add your control to a test form</span></span>

1. <span data-ttu-id="d4a66-270">**Çözüm Gezgini**' de, **ctlClockLib**' a sağ tıklayın ve ardından **Oluştur**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d4a66-270">In **Solution Explorer**, right-click **ctlClockLib**, and then click **Build**.</span></span>

2. <span data-ttu-id="d4a66-271">Çözüme yeni bir **Windows uygulaması** projesi ekleyin ve **Test**edin.</span><span class="sxs-lookup"><span data-stu-id="d4a66-271">Add a new **Windows Application** project to the solution, and name it **Test**.</span></span>

3. <span data-ttu-id="d4a66-272">**Çözüm Gezgini**, test projeniz için **Başvurular** düğümüne sağ tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d4a66-272">In **Solution Explorer**, right-click the **References** node for your test project.</span></span> <span data-ttu-id="d4a66-273">**Başvuru Ekle iletişim kutusunu** göstermek Için **Başvuru Ekle** ' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d4a66-273">Click **Add Reference** to display the **Add Reference** dialog box.</span></span> <span data-ttu-id="d4a66-274">Etiketli **Projeler**sekmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d4a66-274">Click the tab labeled **Projects**.</span></span> <span data-ttu-id="d4a66-275">`ctlClockLib` projeniz **Proje adı**altında listelenecektir.</span><span class="sxs-lookup"><span data-stu-id="d4a66-275">Your `ctlClockLib` project will be listed under **Project Name**.</span></span> <span data-ttu-id="d4a66-276">Başvuruyu test projesine eklemek için projeye çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d4a66-276">Double-click the project to add the reference to the test project.</span></span>

4. <span data-ttu-id="d4a66-277">**Çözüm Gezgini**' de **Test**' e sağ tıklayın ve ardından **Oluştur**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d4a66-277">In **Solution Explorer**, right-click **Test**, and then click **Build**.</span></span>

5. <span data-ttu-id="d4a66-278">**Araç kutusunda** **ctlClockLib Components** düğümünü genişletin.</span><span class="sxs-lookup"><span data-stu-id="d4a66-278">In the **Toolbox**, expand the **ctlClockLib Components** node.</span></span>

6. <span data-ttu-id="d4a66-279">Formunuza bir `ctlAlarmClock` kopyası eklemek için **ctlAlarmClock** öğesine çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d4a66-279">Double-click **ctlAlarmClock** to add a copy of `ctlAlarmClock` to your form.</span></span>

7. <span data-ttu-id="d4a66-280">**Araç kutusunda** **DateTimePicker** ' ı bulup çift tıklatarak formunuza bir <xref:System.Windows.Forms.DateTimePicker> denetimi ekleyin ve ardından **etikete**çift tıklayarak bir <xref:System.Windows.Forms.Label> denetimi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d4a66-280">In the **Toolbox**, locate and double-click **DateTimePicker** to add a <xref:System.Windows.Forms.DateTimePicker> control to your form, and then add a <xref:System.Windows.Forms.Label> control by double-clicking **Label**.</span></span>

8. <span data-ttu-id="d4a66-281">Denetimleri form üzerinde uygun bir yerde konumlandırmak için fareyi kullanın.</span><span class="sxs-lookup"><span data-stu-id="d4a66-281">Use the mouse to position the controls in a convenient place on the form.</span></span>

9. <span data-ttu-id="d4a66-282">Bu denetimlerin özelliklerini aşağıdaki şekilde ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d4a66-282">Set the properties of these controls in the following manner.</span></span>

    |<span data-ttu-id="d4a66-283">Denetim</span><span class="sxs-lookup"><span data-stu-id="d4a66-283">Control</span></span>|<span data-ttu-id="d4a66-284">Özellik</span><span class="sxs-lookup"><span data-stu-id="d4a66-284">Property</span></span>|<span data-ttu-id="d4a66-285">Değer</span><span class="sxs-lookup"><span data-stu-id="d4a66-285">Value</span></span>|
    |-------------|--------------|-----------|
    |`label1`|<span data-ttu-id="d4a66-286">**Metin**</span><span class="sxs-lookup"><span data-stu-id="d4a66-286">**Text**</span></span>|`(blank space)`|
    ||<span data-ttu-id="d4a66-287">**Ad**</span><span class="sxs-lookup"><span data-stu-id="d4a66-287">**Name**</span></span>|`lblTest`|
    |`dateTimePicker1`|<span data-ttu-id="d4a66-288">**Ad**</span><span class="sxs-lookup"><span data-stu-id="d4a66-288">**Name**</span></span>|`dtpTest`|
    ||<span data-ttu-id="d4a66-289">**Formatını**</span><span class="sxs-lookup"><span data-stu-id="d4a66-289">**Format**</span></span>|<xref:System.Windows.Forms.DateTimePickerFormat.Time>|

10. <span data-ttu-id="d4a66-290">Tasarımcıda **dtpTest**öğesine çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d4a66-290">In the designer, double-click **dtpTest**.</span></span>

     <span data-ttu-id="d4a66-291">`private void dtpTest_ValueChanged`için **Kod Düzenleyicisi** açılır.</span><span class="sxs-lookup"><span data-stu-id="d4a66-291">The **Code Editor** opens to `private void dtpTest_ValueChanged`.</span></span>

11. <span data-ttu-id="d4a66-292">Kodu aşağıdakine benzer olacak şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="d4a66-292">Modify the code so that it resembles the following.</span></span>

    ```csharp
    private void dtpTest_ValueChanged(object sender, System.EventArgs e)
    {
        ctlAlarmClock1.AlarmTime = dtpTest.Value;
        ctlAlarmClock1.AlarmSet = true;
        lblTest.Text = "Alarm Time is " +
            ctlAlarmClock1.AlarmTime.ToShortTimeString();
    }
    ```

12. <span data-ttu-id="d4a66-293">**Çözüm Gezgini**' de **Test**' e sağ tıklayın ve ardından **Başlangıç projesi olarak ayarla**' ya tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d4a66-293">In **Solution Explorer**, right-click **Test**, and then click **Set as StartUp Project**.</span></span>

13. <span data-ttu-id="d4a66-294">**Hata Ayıkla** menüsünde, **hata ayıklamayı Başlat**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d4a66-294">On the **Debug** menu, click **Start Debugging**.</span></span>

     <span data-ttu-id="d4a66-295">Test programı başlar.</span><span class="sxs-lookup"><span data-stu-id="d4a66-295">The test program starts.</span></span> <span data-ttu-id="d4a66-296">`ctlAlarmClock` denetiminde geçerli saatin güncelleştirildiğini ve <xref:System.Windows.Forms.DateTimePicker> denetiminde başlangıç zamanının gösterildiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="d4a66-296">Note that the current time is updated in the `ctlAlarmClock` control, and that the starting time is shown in the <xref:System.Windows.Forms.DateTimePicker> control.</span></span>

14. <span data-ttu-id="d4a66-297">Saatin dakikalarının görüntülendiği <xref:System.Windows.Forms.DateTimePicker> tıklatın.</span><span class="sxs-lookup"><span data-stu-id="d4a66-297">Click the <xref:System.Windows.Forms.DateTimePicker> where the minutes of the hour are displayed.</span></span>

15. <span data-ttu-id="d4a66-298">Klavyeyi kullanarak, `ctlAlarmClock`tarafından gösterilen geçerli zamandan bir dakika daha büyük bir değer ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d4a66-298">Using the keyboard, set a value for minutes that is one minute greater than the current time shown by `ctlAlarmClock`.</span></span>

     <span data-ttu-id="d4a66-299">Uyarı ayarının saati `lblTest`gösterilir.</span><span class="sxs-lookup"><span data-stu-id="d4a66-299">The time for the alarm setting is shown in `lblTest`.</span></span> <span data-ttu-id="d4a66-300">Uyarı ayarı zamanına ulaşmak için, görüntülenecek sürenin bekleyin.</span><span class="sxs-lookup"><span data-stu-id="d4a66-300">Wait for the displayed time to reach the alarm setting time.</span></span> <span data-ttu-id="d4a66-301">Görünen süre, alarmın ayarlandığı zamana ulaştığında, `lblAlarm` yanıp sönecektir.</span><span class="sxs-lookup"><span data-stu-id="d4a66-301">When the displayed time reaches the time to which the alarm is set, the `lblAlarm` will flash.</span></span>

16. <span data-ttu-id="d4a66-302">`btnAlarmOff`' ye tıklayarak uyarıyı kapatın.</span><span class="sxs-lookup"><span data-stu-id="d4a66-302">Turn off the alarm by clicking `btnAlarmOff`.</span></span> <span data-ttu-id="d4a66-303">Şimdi uyarıyı sıfırlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d4a66-303">You may now reset the alarm.</span></span>

<span data-ttu-id="d4a66-304">Bu makalede bir dizi temel kavram ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="d4a66-304">This article has covered a number of key concepts.</span></span> <span data-ttu-id="d4a66-305">Bir bileşik denetim kapsayıcısına denetimleri ve bileşenleri birleştirerek bileşik bir denetim oluşturmayı öğrendiniz.</span><span class="sxs-lookup"><span data-stu-id="d4a66-305">You have learned to create a composite control by combining controls and components into a composite control container.</span></span> <span data-ttu-id="d4a66-306">Denetime Özellik eklemeyi ve özel işlevsellik uygulamak için kod yazmayı öğrendiniz.</span><span class="sxs-lookup"><span data-stu-id="d4a66-306">You have learned to add properties to your control, and to write code to implement custom functionality.</span></span> <span data-ttu-id="d4a66-307">Son bölümde, belirli bir bileşik denetimin işlevselliğini devralma yoluyla genişletmeyi ve bu yöntemleri geçersiz kılarak ana bilgisayar yöntemlerinin işlevselliğini değiştirmeyi öğrendiniz.</span><span class="sxs-lookup"><span data-stu-id="d4a66-307">In the last section, you learned to extend the functionality of a given composite control through inheritance, and to alter the functionality of host methods by overriding those methods.</span></span>

## <a name="see-also"></a><span data-ttu-id="d4a66-308">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d4a66-308">See also</span></span>

- [<span data-ttu-id="d4a66-309">Özel Denetim Çeşitleri</span><span class="sxs-lookup"><span data-stu-id="d4a66-309">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
- [<span data-ttu-id="d4a66-310">Nasıl yapılır: Araç Kutusu Öğelerini Seç İletişim Kutusunda bir Denetimi Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="d4a66-310">How to: Display a Control in the Choose Toolbox Items Dialog Box</span></span>](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)
- [<span data-ttu-id="d4a66-311">İzlenecek yol: Visual C# ile beraber Windows Forms Denetimi'nden Devralma</span><span class="sxs-lookup"><span data-stu-id="d4a66-311">Walkthrough: Inheriting from a Windows Forms Control with Visual C#</span></span>](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)
