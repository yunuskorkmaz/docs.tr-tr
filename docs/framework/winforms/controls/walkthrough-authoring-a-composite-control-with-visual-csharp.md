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
ms.openlocfilehash: 3ad9aad026a1a6a1266845736d7651db77fd5d5c
ms.sourcegitcommit: 34dc3c0d0d0a1cc418abff259d9daa8078d00b81
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/19/2020
ms.locfileid: "79546730"
---
# <a name="walkthrough-author-a-composite-control-with-c"></a><span data-ttu-id="1f5c9-102">İzleme: C ile Bileşik Kontrol Yazma\#</span><span class="sxs-lookup"><span data-stu-id="1f5c9-102">Walkthrough: Author a Composite Control with C\#</span></span>

<span data-ttu-id="1f5c9-103">Bileşik denetimler, özel grafik arabirimlerinin oluşturulup yeniden kullanılabileceğini niçin sağlar.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-103">Composite controls provide a means by which custom graphical interfaces can be created and reused.</span></span> <span data-ttu-id="1f5c9-104">Bileşik denetim aslında görsel gösterimi olan bir bileşendir.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-104">A composite control is essentially a component with a visual representation.</span></span> <span data-ttu-id="1f5c9-105">Bu nedenle, kullanıcı girişini doğrulayarak, görüntü özelliklerini değiştirerek veya yazarın gerektirdiği diğer görevleri gerçekleştirerek işlevselliği genişletebilecek bir veya daha fazla Windows Forms denetimi, bileşenleri veya kod bloklarından oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-105">As such, it might consist of one or more Windows Forms controls, components, or blocks of code that can extend functionality by validating user input, modifying display properties, or performing other tasks required by the author.</span></span> <span data-ttu-id="1f5c9-106">Bileşik denetimler, Windows Formlar'a diğer denetimler gibi yerleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-106">Composite controls can be placed on Windows Forms in the same manner as other controls.</span></span> <span data-ttu-id="1f5c9-107">Bu izbin ilk bölümünde, '. `ctlClock`</span><span class="sxs-lookup"><span data-stu-id="1f5c9-107">In the first part of this walkthrough, you create a simple composite control called `ctlClock`.</span></span> <span data-ttu-id="1f5c9-108">Gözden geçirme nin ikinci bölümünde, devralma `ctlClock` yoluyla işlevselliğini genişletirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-108">In the second part of the walkthrough, you extend the functionality of `ctlClock` through inheritance.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="1f5c9-109">Proje oluşturma</span><span class="sxs-lookup"><span data-stu-id="1f5c9-109">Create the Project</span></span>

<span data-ttu-id="1f5c9-110">Yeni bir proje oluşturduğunuzda, kök ad alanını, derleme adını ve proje adını ayarlamak ve varsayılan bileşenin doğru ad alanında olmasını sağlamak için adını belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-110">When you create a new project, you specify its name to set the root namespace, assembly name, and project name, and ensure that the default component will be in the correct namespace.</span></span>

### <a name="to-create-the-ctlclocklib-control-library-and-the-ctlclock-control"></a><span data-ttu-id="1f5c9-111">ctlClockLib denetim kitaplığını ve ctlClock denetimini oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="1f5c9-111">To create the ctlClockLib control library and the ctlClock control</span></span>

1. <span data-ttu-id="1f5c9-112">Visual Studio'da, yeni bir **Windows Forms Control Library** projesi oluşturun ve adını **CtlClockLib**olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-112">In Visual Studio, create a new **Windows Forms Control Library** project, and name it **ctlClockLib**.</span></span>

     <span data-ttu-id="1f5c9-113">Proje adı, `ctlClockLib`varsayılan olarak kök ad alanına da atanır.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-113">The project name, `ctlClockLib`, is also assigned to the root namespace by default.</span></span> <span data-ttu-id="1f5c9-114">Kök ad alanı, derlemedeki bileşenlerin adlarını nitelemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-114">The root namespace is used to qualify the names of components in the assembly.</span></span> <span data-ttu-id="1f5c9-115">Örneğin, iki derleme adlandırılmış `ctlClock`bileşenler sağlıyorsa, bileşeninizi `ctlClock``ctlClockLib.ctlClock.`</span><span class="sxs-lookup"><span data-stu-id="1f5c9-115">For example, if two assemblies provide components named `ctlClock`, you can specify your `ctlClock` component using `ctlClockLib.ctlClock.`</span></span>

2. <span data-ttu-id="1f5c9-116">**Çözüm Gezgini'nde**, **UserControl1.cs**sağ tıklatın ve sonra **Yeniden Adlandır'ı**tıklatın.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-116">In **Solution Explorer**, right-click **UserControl1.cs**, and then click **Rename**.</span></span> <span data-ttu-id="1f5c9-117">Dosya adını `ctlClock.cs`' la değiştirin</span><span class="sxs-lookup"><span data-stu-id="1f5c9-117">Change the file name to `ctlClock.cs`.</span></span> <span data-ttu-id="1f5c9-118">"UserControl1" kod öğesine yapılan tüm başvuruları yeniden adlandırmak isteyip istemediğiniz sorulduğunda **Evet** düğmesini tıklatın.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-118">Click the **Yes** button when you are asked if you want to rename all references to the code element "UserControl1".</span></span>

    > [!NOTE]
    > <span data-ttu-id="1f5c9-119">Varsayılan olarak, bileşik denetim sistem <xref:System.Windows.Forms.UserControl> tarafından sağlanan sınıftan devralır.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-119">By default, a composite control inherits from the <xref:System.Windows.Forms.UserControl> class provided by the system.</span></span> <span data-ttu-id="1f5c9-120">Sınıf, <xref:System.Windows.Forms.UserControl> tüm bileşik denetimler tarafından gerekli işlevselliği sağlar ve standart yöntem ve özellikleri uygular.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-120">The <xref:System.Windows.Forms.UserControl> class provides functionality required by all composite controls, and implements standard methods and properties.</span></span>

3. <span data-ttu-id="1f5c9-121">**Dosya** menüsünde, projeyi kaydetmek için **Tümlerini Kaydet'i** tıklatın.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-121">On the **File** menu, click **Save All** to save the project.</span></span>

## <a name="add-windows-controls-and-components-to-the-composite-control"></a><span data-ttu-id="1f5c9-122">Bileşik Denetime Windows Denetimleri ve Bileşenleri Ekleme</span><span class="sxs-lookup"><span data-stu-id="1f5c9-122">Add Windows Controls and Components to the Composite Control</span></span>

<span data-ttu-id="1f5c9-123">Görsel arayüz, bileşik denetiminizin önemli bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-123">A visual interface is an essential part of your composite control.</span></span> <span data-ttu-id="1f5c9-124">Bu görsel arabirim, tasarımcı yüzeyine bir veya daha fazla Windows denetimi nin eklenmesiyle uygulanır.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-124">This visual interface is implemented by the addition of one or more Windows controls to the designer surface.</span></span> <span data-ttu-id="1f5c9-125">Aşağıdaki gösteride, Windows denetimlerini bileşik denetiminize dahil eder ve işlevselliği uygulamak için kod yazarsınız.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-125">In the following demonstration, you will incorporate Windows controls into your composite control and write code to implement functionality.</span></span>

### <a name="to-add-a-label-and-a-timer-to-your-composite-control"></a><span data-ttu-id="1f5c9-126">Bileşik denetiminize Etiket ve Zamanlayıcı eklemek için</span><span class="sxs-lookup"><span data-stu-id="1f5c9-126">To add a Label and a Timer to your composite control</span></span>

1. <span data-ttu-id="1f5c9-127">**Çözüm Gezgini'nde**, **ctlClock.cs**sağ tıklatın ve ardından **Tasarımcıyı Görüntüle'yi**tıklatın.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-127">In **Solution Explorer**, right-click **ctlClock.cs**, and then click **View Designer**.</span></span>

2. <span data-ttu-id="1f5c9-128">Araç **Kutusunda,** Ortak **Denetimler** düğümlerini genişletin ve ardından **Etiket'i**çift tıklatın.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-128">In the **Toolbox**, expand the **Common Controls** node, and then double-click **Label**.</span></span>

     <span data-ttu-id="1f5c9-129">Tasarımcı <xref:System.Windows.Forms.Label> yüzeyindeki denetiminize adlandırılmış `label1` bir denetim eklenir.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-129">A <xref:System.Windows.Forms.Label> control named `label1` is added to your control on the designer surface.</span></span>

3. <span data-ttu-id="1f5c9-130">Tasarımcıda **label1'e**tıklayın.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-130">In the designer, click **label1**.</span></span> <span data-ttu-id="1f5c9-131">Özellikler penceresinde aşağıdaki özellikleri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-131">In the Properties window, set the following properties.</span></span>

    |<span data-ttu-id="1f5c9-132">Özellik</span><span class="sxs-lookup"><span data-stu-id="1f5c9-132">Property</span></span>|<span data-ttu-id="1f5c9-133">Şununla değiştirin</span><span class="sxs-lookup"><span data-stu-id="1f5c9-133">Change to</span></span>|
    |--------------|---------------|
    |<span data-ttu-id="1f5c9-134">**Adı**</span><span class="sxs-lookup"><span data-stu-id="1f5c9-134">**Name**</span></span>|`lblDisplay`|
    |<span data-ttu-id="1f5c9-135">**Metin**</span><span class="sxs-lookup"><span data-stu-id="1f5c9-135">**Text**</span></span>|`(blank space)`|
    |<span data-ttu-id="1f5c9-136">**Textalign**</span><span class="sxs-lookup"><span data-stu-id="1f5c9-136">**TextAlign**</span></span>|`MiddleCenter`|
    |<span data-ttu-id="1f5c9-137">**Yazı Tipi.Boyut**</span><span class="sxs-lookup"><span data-stu-id="1f5c9-137">**Font.Size**</span></span>|`14`|

4. <span data-ttu-id="1f5c9-138">Araç **Kutusunda,** **Bileşenler** düğümlerini genişletin ve ardından **Zamanlayıcı'yı**çift tıklatın.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-138">In the **Toolbox**, expand the **Components** node, and then double-click **Timer**.</span></span>

     <span data-ttu-id="1f5c9-139">A <xref:System.Windows.Forms.Timer> bir bileşen olduğundan, çalışma zamanında görsel gösterimi yoktur.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-139">Because a <xref:System.Windows.Forms.Timer> is a component, it has no visual representation at run time.</span></span> <span data-ttu-id="1f5c9-140">Bu nedenle, tasarımcı yüzeyindeki denetimlerde değil, Bileşen **Tasarımcısı'nda** (tasarımcı yüzeyinin alt kısmında ki tepsi) görünür.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-140">Therefore, it does not appear with the controls on the designer surface, but rather in the **Component Designer** (a tray at the bottom of the designer surface).</span></span>

5. <span data-ttu-id="1f5c9-141">Bileşen **Tasarımcısı'** nda **timer1'i**tıklatın <xref:System.Windows.Forms.Timer.Interval%2A> ve `1000` sonra <xref:System.Windows.Forms.Timer.Enabled%2A> özelliği `true`ve özelliği .</span><span class="sxs-lookup"><span data-stu-id="1f5c9-141">In the **Component Designer**, click **timer1**, and then set the <xref:System.Windows.Forms.Timer.Interval%2A> property to `1000` and the <xref:System.Windows.Forms.Timer.Enabled%2A> property to `true`.</span></span>

     <span data-ttu-id="1f5c9-142">Özellik, <xref:System.Windows.Forms.Timer.Interval%2A> bileşenin <xref:System.Windows.Forms.Timer> işleme sıklığını denetler.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-142">The <xref:System.Windows.Forms.Timer.Interval%2A> property controls the frequency with which the <xref:System.Windows.Forms.Timer> component ticks.</span></span> <span data-ttu-id="1f5c9-143">Her `timer1` işleninher, `timer1_Tick` olaydaki kodu çalıştırıyor.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-143">Each time `timer1` ticks, it runs the code in the `timer1_Tick` event.</span></span> <span data-ttu-id="1f5c9-144">Aralık, keneler arasındaki milisaniye sayısını gösterir.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-144">The interval represents the number of milliseconds between ticks.</span></span>

6. <span data-ttu-id="1f5c9-145">Bileşen **Tasarımcısı,** çift **tıklatma zamanlayıcı1** `timer1_Tick` için etkinliğe gitmek için `ctlClock`.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-145">In the **Component Designer**, double-click **timer1** to go to the `timer1_Tick` event for `ctlClock`.</span></span>

7. <span data-ttu-id="1f5c9-146">Kodu, aşağıdaki kod örneğine benzeyecek şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-146">Modify the code so that it resembles the following code sample.</span></span> <span data-ttu-id="1f5c9-147">Erişim değiştiriciyi ' den `private` ' `protected`e değiştirdiğinizden emin olun</span><span class="sxs-lookup"><span data-stu-id="1f5c9-147">Be sure to change the access modifier from `private` to `protected`.</span></span>

    ```csharp
    protected void timer1_Tick(object sender, System.EventArgs e)
    {
        // Causes the label to display the current time.
        lblDisplay.Text = DateTime.Now.ToLongTimeString();
    }
    ```

     <span data-ttu-id="1f5c9-148">Bu kod, geçerli saatin 'de `lblDisplay`gösterilmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-148">This code will cause the current time to be shown in `lblDisplay`.</span></span> <span data-ttu-id="1f5c9-149">Aralığı `timer1` ayarlandı çünkü `1000`, Bu olay her bin milisaniye meydana gelecek, böylece her saniye geçerli zamanı güncelleştirerek.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-149">Because the interval of `timer1` was set to `1000`, this event will occur every thousand milliseconds, thus updating the current time every second.</span></span>

8. <span data-ttu-id="1f5c9-150">Yöntemi anahtar kelimeyle geçersiz kılınacak şekilde değiştirin. `virtual`</span><span class="sxs-lookup"><span data-stu-id="1f5c9-150">Modify the method to be overridable with the `virtual` keyword.</span></span> <span data-ttu-id="1f5c9-151">Daha fazla bilgi için aşağıdaki "Kullanıcı Denetiminden Devralma" bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-151">For more information, see the  "Inheriting from a User Control" section below.</span></span>

    ```csharp
    protected virtual void timer1_Tick(object sender, System.EventArgs e)
    ```

9. <span data-ttu-id="1f5c9-152">**Dosya** menüsünde, projeyi kaydetmek için **Tümlerini Kaydet'i** tıklatın.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-152">On the **File** menu, click **Save All** to save the project.</span></span>

## <a name="add-properties-to-the-composite-control"></a><span data-ttu-id="1f5c9-153">Bileşik Denetime Özellikler Ekleme</span><span class="sxs-lookup"><span data-stu-id="1f5c9-153">Add Properties to the Composite Control</span></span>

<span data-ttu-id="1f5c9-154">Saat denetiminiz artık her biri <xref:System.Windows.Forms.Label> kendi <xref:System.Windows.Forms.Timer> doğal özelliklerine sahip bir denetim ve bileşeni kapsüller.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-154">Your clock control now encapsulates a <xref:System.Windows.Forms.Label> control and a <xref:System.Windows.Forms.Timer> component, each with its own set of inherent properties.</span></span> <span data-ttu-id="1f5c9-155">Bu denetimlerin tek tek özellikleri denetiminizin sonraki kullanıcıları tarafından erişilemese de, uygun kod bloklarını yazarak özel özellikler oluşturabilir ve ortaya çıkarabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-155">While the individual properties of these controls will not be accessible to subsequent users of your control, you can create and expose custom properties by writing the appropriate blocks of code.</span></span> <span data-ttu-id="1f5c9-156">Aşağıdaki yordamda, denetiminize kullanıcının arka plan ve metnin rengini değiştirmesini sağlayan özellikler eklersiniz.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-156">In the following procedure, you will add properties to your control that enable the user to change the color of the background and text.</span></span>

### <a name="to-add-a-property-to-your-composite-control"></a><span data-ttu-id="1f5c9-157">Bileşik denetiminize özellik eklemek için</span><span class="sxs-lookup"><span data-stu-id="1f5c9-157">To add a property to your composite control</span></span>

1. <span data-ttu-id="1f5c9-158">**Çözüm Gezgini'nde**, **ctlClock.cs**sağ tıklatın ve ardından **Kodu Görüntüle'yi**tıklatın.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-158">In **Solution Explorer**, right-click **ctlClock.cs**, and then click **View Code**.</span></span>

     <span data-ttu-id="1f5c9-159">Denetiminiz için **Kod Düzenleyicisi** açılır.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-159">The **Code Editor** for your control opens.</span></span>

2. <span data-ttu-id="1f5c9-160">İfadeyi `public partial class ctlClock` bulun.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-160">Locate the `public partial class ctlClock` statement.</span></span> <span data-ttu-id="1f5c9-161">Açılış ayracının`{)`altında ( , aşağıdaki kodu yazın.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-161">Beneath the opening brace (`{)`, type the following code.</span></span>

    ```csharp
    private Color colFColor;
    private Color colBColor;
    ```

     <span data-ttu-id="1f5c9-162">Bu ifadeler, oluşturmak üzere olduğunuz özelliklerin değerlerini depolamak için kullanacağınız özel değişkenleri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-162">These statements create the private variables that you will use to store the values for the properties you are about to create.</span></span>

3. <span data-ttu-id="1f5c9-163">Adım 2'den değişken bildirimleri altında aşağıdaki kodu girin veya yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-163">Enter or paste the following code beneath the variable declarations from step 2.</span></span>

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

     <span data-ttu-id="1f5c9-164">Önceki kod iki özel özellik `ClockForeColor` `ClockBackColor`yapar ve bu denetimin sonraki kullanıcıları tarafından kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-164">The preceding code makes two custom properties, `ClockForeColor` and `ClockBackColor`, available to subsequent users of this control.</span></span> <span data-ttu-id="1f5c9-165">Ve `get` `set` ifadeler depolama ve özellik değerinin alınması yanı sıra özellik için uygun işlevselliği uygulamak için kod sağlar.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-165">The `get` and `set` statements provide for storage and retrieval of the property value, as well as code to implement functionality appropriate to the property.</span></span>

4. <span data-ttu-id="1f5c9-166">**Dosya** menüsünde, projeyi kaydetmek için **Tümlerini Kaydet'i** tıklatın.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-166">On the **File** menu, click **Save All** to save the project.</span></span>

## <a name="test-the-control"></a><span data-ttu-id="1f5c9-167">Denetimi Test Edin</span><span class="sxs-lookup"><span data-stu-id="1f5c9-167">Test the Control</span></span>

<span data-ttu-id="1f5c9-168">Denetimler tek başına uygulamalar değildir; bir konteynerde barındırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-168">Controls are not stand-alone applications; they must be hosted in a container.</span></span> <span data-ttu-id="1f5c9-169">Denetiminizin çalışma zamanı davranışını test edin ve **özelliklerini UserControl Test Kapsayıcısı**ile çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-169">Test your control's run-time behavior and exercise its properties with the **UserControl Test Container**.</span></span> <span data-ttu-id="1f5c9-170">Daha fazla bilgi için [bkz: UserControl'un Çalışma Zamanı Davranışını Test Edin.](how-to-test-the-run-time-behavior-of-a-usercontrol.md)</span><span class="sxs-lookup"><span data-stu-id="1f5c9-170">For more information, see [How to: Test the Run-Time Behavior of a UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>

### <a name="to-test-your-control"></a><span data-ttu-id="1f5c9-171">Denetiminizi test etmek için</span><span class="sxs-lookup"><span data-stu-id="1f5c9-171">To test your control</span></span>

1. <span data-ttu-id="1f5c9-172">Projeyi oluşturmak ve denetiminizi **UserControl Test**Konteyneri'nde çalıştırmak için **F5** tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-172">Press **F5** to build the project and run your control in the **UserControl Test Container**.</span></span>

2. <span data-ttu-id="1f5c9-173">Test kapsayıcısının özellik ızgarasında, `ClockBackColor` özelliği bulun ve ardından renk paletini görüntülemek için özelliği seçin.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-173">In the test container's property grid, locate the `ClockBackColor` property, and then select the property to display the color palette.</span></span>

3. <span data-ttu-id="1f5c9-174">Tıklatarak bir renk seçin.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-174">Choose a color by clicking it.</span></span>

   <span data-ttu-id="1f5c9-175">Denetiminizin arka plan rengi seçtiğiniz renge dönüşür.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-175">The background color of your control changes to the color you selected.</span></span>

4. <span data-ttu-id="1f5c9-176">`ClockForeColor` Özelliğin beklendiği gibi çalıştığını doğrulamak için benzer bir olaylar dizisi kullanın.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-176">Use a similar sequence of events to verify that the `ClockForeColor` property is functioning as expected.</span></span>

   <span data-ttu-id="1f5c9-177">Bu bölümde ve önceki bölümlerde, bileşenlerin ve Windows denetimlerinin bileşik denetim biçiminde özel işlevsellik sağlamak için kod ve paketlemeyle nasıl birleştirilebildiğini gördünüz.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-177">In this section and the preceding sections, you have seen how components and Windows controls can be combined with code and packaging to provide custom functionality in the form of a composite control.</span></span> <span data-ttu-id="1f5c9-178">Bileşik denetiminizdeki özellikleri ve denetiminizi tamamlandıktan sonra nasıl sınayabileceğinizi öğrendiniz.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-178">You have learned to expose properties in your composite control, and how to test your control after it is complete.</span></span> <span data-ttu-id="1f5c9-179">Bir sonraki bölümde, temel olarak kullanarak `ctlClock` devralınan bir bileşik denetimin nasıl oluşturacağınızı öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-179">In the next section you will learn how to construct an inherited composite control using `ctlClock` as a base.</span></span>

## <a name="inherit-from-a-composite-control"></a><span data-ttu-id="1f5c9-180">Bileşik Denetimden Devralma</span><span class="sxs-lookup"><span data-stu-id="1f5c9-180">Inherit from a Composite Control</span></span>

<span data-ttu-id="1f5c9-181">Önceki bölümlerde, Windows denetimlerini, bileşenlerini ve kodu yeniden kullanılabilir bileşik denetimlerde nasıl birleştirdiğinizi öğrendiniz.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-181">In the previous sections, you learned how to combine Windows controls, components, and code into reusable composite controls.</span></span> <span data-ttu-id="1f5c9-182">Kompozit denetiminiz artık diğer denetimlerin üzerine inşa edilebilen bir üs olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-182">Your composite control can now be used as a base upon which other controls can be built.</span></span> <span data-ttu-id="1f5c9-183">Bir taban sınıftan bir sınıf türetme *işlemine devralma*denir.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-183">The process of deriving a class from a base class is called *inheritance*.</span></span> <span data-ttu-id="1f5c9-184">Bu bölümde, '. `ctlAlarmClock`</span><span class="sxs-lookup"><span data-stu-id="1f5c9-184">In this section, you will create a composite control called `ctlAlarmClock`.</span></span> <span data-ttu-id="1f5c9-185">Bu denetim, üst denetiminden `ctlClock`türetilecek.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-185">This control will be derived from its parent control, `ctlClock`.</span></span> <span data-ttu-id="1f5c9-186">Üst yöntemleri geçersiz `ctlClock` kılarak ve yeni yöntemler ve özellikler ekleyerek işlevselliğini genişletmeyi öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-186">You will learn to extend the functionality of `ctlClock` by overriding parent methods and adding new methods and properties.</span></span>

<span data-ttu-id="1f5c9-187">Devralınan bir denetim oluşturmanın ilk adımı, onu üst öğesinden elde etmektir.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-187">The first step in creating an inherited control is to derive it from its parent.</span></span> <span data-ttu-id="1f5c9-188">Bu eylem, üst denetimin tüm özelliklerine, yöntemlerine ve grafik özelliklerine sahip, ancak yeni veya değiştirilmiş işlevselliğin eklenmesi için bir temel olarak da hareket edebilen yeni bir denetim oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-188">This action creates a new control that has all of the properties, methods, and graphical characteristics of the parent control, but can also act as a base for the addition of new or modified functionality.</span></span>

### <a name="to-create-the-inherited-control"></a><span data-ttu-id="1f5c9-189">Devralınan denetimi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="1f5c9-189">To create the inherited control</span></span>

1. <span data-ttu-id="1f5c9-190">**Çözüm Gezgini'nde**, **ctlClockLib'e**sağ tıklayın , **Ekle'ye**işaret edin ve ardından **Kullanıcı Denetimi'ni**tıklatın.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-190">In **Solution Explorer**, right-click **ctlClockLib**, point to **Add**, and then click **User Control**.</span></span>

     <span data-ttu-id="1f5c9-191">**Yeni Öğe Ekle** iletişim kutusu açılır.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-191">The **Add New Item** dialog box opens.</span></span>

2. <span data-ttu-id="1f5c9-192">**Devralınan Kullanıcı Denetimi** şablonu'nu seçin.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-192">Select the **Inherited User Control** template.</span></span>

3. <span data-ttu-id="1f5c9-193">**Ad** kutusuna, `ctlAlarmClock.cs`''yı yazın ve sonra **Ekle'yi**tıklatın.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-193">In the **Name** box, type `ctlAlarmClock.cs`, and then click **Add**.</span></span>

     <span data-ttu-id="1f5c9-194">**Kalıtım Seçici** iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-194">The **Inheritance Picker** dialog box appears.</span></span>

4. <span data-ttu-id="1f5c9-195">**Bileşen Adı**altında , çift tıklayın **ctlClock**.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-195">Under **Component Name**, double-click **ctlClock**.</span></span>

5. <span data-ttu-id="1f5c9-196">**Solution**Explorer'da, geçerli projelere göz atın.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-196">In **Solution Explorer**, browse through the current projects.</span></span>

    > [!NOTE]
    > <span data-ttu-id="1f5c9-197">Geçerli projeye **ctlAlarmClock.cs** adlı bir dosya eklendi.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-197">A file called **ctlAlarmClock.cs** has been added to the current project.</span></span>

### <a name="add-the-alarm-properties"></a><span data-ttu-id="1f5c9-198">Alarm Özelliklerini Ekle</span><span class="sxs-lookup"><span data-stu-id="1f5c9-198">Add the Alarm Properties</span></span>

<span data-ttu-id="1f5c9-199">Özellikler, bir bileşik denetime eklendikleri şekilde devralınan denetime eklenir.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-199">Properties are added to an inherited control in the same way they are added to a composite control.</span></span> <span data-ttu-id="1f5c9-200">Şimdi, denetiminize iki özellik eklemek için özellik bildirimi `AlarmTime`sözdizimini kullanacaksınız: alarmın çalma tarihi ve saatinin değerini depolayacak ve `AlarmSet`alarmın ayarlanıp ayarlanmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-200">You will now use the property declaration syntax to add two properties to your control: `AlarmTime`, which will store the value of the date and time the alarm is to go off, and `AlarmSet`, which will indicate whether the alarm is set.</span></span>

#### <a name="to-add-properties-to-your-composite-control"></a><span data-ttu-id="1f5c9-201">Bileşik denetiminize özellikler eklemek için</span><span class="sxs-lookup"><span data-stu-id="1f5c9-201">To add properties to your composite control</span></span>

1. <span data-ttu-id="1f5c9-202">**Çözüm Gezgini'nde** **ctlAlarmClock'a**sağ tıklayın ve ardından **Kodu Görüntüle'yi**tıklatın.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-202">In **Solution Explorer**, right-click **ctlAlarmClock**, and then click **View Code**.</span></span>

2. <span data-ttu-id="1f5c9-203">İfadeyi `public class` bulun.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-203">Locate the `public class` statement.</span></span> <span data-ttu-id="1f5c9-204">Denetiminizin 'den `ctlClockLib.ctlClock`devraldığına dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-204">Note that your control inherits from `ctlClockLib.ctlClock`.</span></span> <span data-ttu-id="1f5c9-205">Açılış ayracının`{)` altında (deyim, aşağıdaki kodu yazın).</span><span class="sxs-lookup"><span data-stu-id="1f5c9-205">Beneath the opening brace (`{)` statement, type the following code.</span></span>

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

### <a name="add-to-the-graphical-interface-of-the-control"></a><span data-ttu-id="1f5c9-206">Denetimin Grafik Arabirimine Ekle</span><span class="sxs-lookup"><span data-stu-id="1f5c9-206">Add to the Graphical Interface of the Control</span></span>

<span data-ttu-id="1f5c9-207">Devralınan denetiminiz, devraldığı denetimle aynı görsel bir arabirime sahiptir.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-207">Your inherited control has a visual interface that is identical to the control it inherits from.</span></span> <span data-ttu-id="1f5c9-208">Ana denetimiyle aynı kurucu denetimlere sahiptir, ancak özellikle maruz kalmadıkça kurucu denetimlerin özellikleri kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-208">It possesses the same constituent controls as its parent control, but the properties of the constituent controls will not be available unless they were specifically exposed.</span></span> <span data-ttu-id="1f5c9-209">Kalıtsal bir bileşik denetimin grafik arabirimine, herhangi bir bileşik denetime eklediğiniz şekilde ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-209">You may add to the graphical interface of an inherited composite control in the same manner as you would add to any composite control.</span></span> <span data-ttu-id="1f5c9-210">Çalar saatinizin görsel arabirimine eklemeye devam etmek için, alarm çalarken yanıp sönen bir etiket denetimi eklersiniz.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-210">To continue adding to your alarm clock's visual interface, you will add a label control that will flash when the alarm is sounding.</span></span>

#### <a name="to-add-the-label-control"></a><span data-ttu-id="1f5c9-211">Etiket denetimini eklemek için</span><span class="sxs-lookup"><span data-stu-id="1f5c9-211">To add the label control</span></span>

1. <span data-ttu-id="1f5c9-212">**Çözüm Gezgini'nde** **ctlAlarmClock'u**sağ tıklatın ve ardından **Tasarımcıyı Görüntüle'yi**tıklatın.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-212">In **Solution Explorer**, right-click **ctlAlarmClock**, and then click **View Designer**.</span></span>

     <span data-ttu-id="1f5c9-213">Tasarımcı ana `ctlAlarmClock` pencerede açılır.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-213">The designer for `ctlAlarmClock` opens in the main window.</span></span>

2. <span data-ttu-id="1f5c9-214">Denetimin görüntü bölümünü tıklatın ve Özellikler penceresini görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-214">Click the display portion of the control, and view the Properties window.</span></span>

    > [!NOTE]
    > <span data-ttu-id="1f5c9-215">Tüm özellikler görüntülenirken, soluk olarak görüntülenirler.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-215">While all the properties are displayed, they are dimmed.</span></span> <span data-ttu-id="1f5c9-216">Bu, bu özelliklerin `lblDisplay` özellikler penceresine özgü olduğunu ve değiştirilemeyeceğini veya erişilemeyeceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-216">This indicates that these properties are native to `lblDisplay` and cannot be modified or accessed in the Properties window.</span></span> <span data-ttu-id="1f5c9-217">Varsayılan olarak, bileşik denetimde `private`bulunan denetimler ve özellikleri hiçbir şekilde erişilebilir değildir.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-217">By default, controls contained in a composite control are `private`, and their properties are not accessible by any means.</span></span>

    > [!NOTE]
    > <span data-ttu-id="1f5c9-218">Bileşik denetiminizin sonraki kullanıcılarının iç denetimlerine erişebilmesini `public` istiyorsanız, bunları 'veya ' olarak `protected`bildirin</span><span class="sxs-lookup"><span data-stu-id="1f5c9-218">If you want subsequent users of your composite control to have access to its internal controls, declare them as `public` or `protected`.</span></span> <span data-ttu-id="1f5c9-219">Bu, uygun kodu kullanarak bileşik denetiminizde bulunan denetimlerin özelliklerini ayarlamanızı ve değiştirmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-219">This will allow you to set and modify properties of controls contained within your composite control by using the appropriate code.</span></span>

3. <span data-ttu-id="1f5c9-220">Bileşik <xref:System.Windows.Forms.Label> denetiminize bir denetim ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-220">Add a <xref:System.Windows.Forms.Label> control to your composite control.</span></span>

4. <span data-ttu-id="1f5c9-221">Fareyi kullanarak, <xref:System.Windows.Forms.Label> denetimi ekran kutusunun hemen altına sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-221">Using the mouse, drag the <xref:System.Windows.Forms.Label> control immediately beneath the display box.</span></span> <span data-ttu-id="1f5c9-222">Özellikler penceresinde aşağıdaki özellikleri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-222">In the Properties window, set the following properties.</span></span>

    |<span data-ttu-id="1f5c9-223">Özellik</span><span class="sxs-lookup"><span data-stu-id="1f5c9-223">Property</span></span>|<span data-ttu-id="1f5c9-224">Ayar</span><span class="sxs-lookup"><span data-stu-id="1f5c9-224">Setting</span></span>|
    |--------------|-------------|
    |<span data-ttu-id="1f5c9-225">**Adı**</span><span class="sxs-lookup"><span data-stu-id="1f5c9-225">**Name**</span></span>|`lblAlarm`|
    |<span data-ttu-id="1f5c9-226">**Metin**</span><span class="sxs-lookup"><span data-stu-id="1f5c9-226">**Text**</span></span>|<span data-ttu-id="1f5c9-227">**Alarm!**</span><span class="sxs-lookup"><span data-stu-id="1f5c9-227">**Alarm!**</span></span>|
    |<span data-ttu-id="1f5c9-228">**Textalign**</span><span class="sxs-lookup"><span data-stu-id="1f5c9-228">**TextAlign**</span></span>|`MiddleCenter`|
    |<span data-ttu-id="1f5c9-229">**Visible**</span><span class="sxs-lookup"><span data-stu-id="1f5c9-229">**Visible**</span></span>|`false`|

### <a name="add-the-alarm-functionality"></a><span data-ttu-id="1f5c9-230">Alarm İşlevselliği Ekle</span><span class="sxs-lookup"><span data-stu-id="1f5c9-230">Add the Alarm Functionality</span></span>

<span data-ttu-id="1f5c9-231">Önceki yordamlarda, bileşik denetiminizde alarm işlevselliği sağlayacak özellikler ve denetim eklediniz.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-231">In the previous procedures, you added properties and a control that will enable alarm functionality in your composite control.</span></span> <span data-ttu-id="1f5c9-232">Bu yordamda, geçerli saati alarm süresiyle karşılaştırmak ve aynıysalar bir alarmı yanıp sarılacak kod eklersiniz.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-232">In this procedure, you will add code to compare the current time to the alarm time and, if they are the same, to flash an alarm.</span></span> <span data-ttu-id="1f5c9-233">`timer1_Tick` Yöntemini geçersiz kılarak `ctlClock` ve buna ek kod ekleyerek, `ctlAlarmClock` `ctlClock`tüm doğal işlevselliğini korurken yeteneğini genişletirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-233">By overriding the `timer1_Tick` method of `ctlClock` and adding additional code to it, you will extend the capability of `ctlAlarmClock` while retaining all of the inherent functionality of `ctlClock`.</span></span>

#### <a name="to-override-the-timer1_tick-method-of-ctlclock"></a><span data-ttu-id="1f5c9-234">ctlClock timer1_Tick yöntemini geçersiz kılmak için</span><span class="sxs-lookup"><span data-stu-id="1f5c9-234">To override the timer1_Tick method of ctlClock</span></span>

1. <span data-ttu-id="1f5c9-235">`private bool blnAlarmSet;` Kod **Düzenleyicisi'nde,** deyimi bulun.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-235">In the **Code Editor**, locate the `private bool blnAlarmSet;` statement.</span></span> <span data-ttu-id="1f5c9-236">Hemen altında, aşağıdaki ifadeyi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-236">Immediately beneath it, add the following statement.</span></span>

    ```csharp
    private bool blnColorTicker;
    ```

2. <span data-ttu-id="1f5c9-237">Kod **Düzenleyicisi'nde**kapanış`})` ayracını (sınıfın sonunda) bulun.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-237">In the **Code Editor**, locate the closing brace (`})` at the end of the class.</span></span> <span data-ttu-id="1f5c9-238">Ayraçtan hemen önce, aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-238">Just before the brace, add the following code.</span></span>

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

     <span data-ttu-id="1f5c9-239">Bu kodun eklenmesi birkaç görevi gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-239">The addition of this code accomplishes several tasks.</span></span> <span data-ttu-id="1f5c9-240">İfade, `override` temel denetimden devralınan yöntem yerine bu yöntemi kullanma denetimini yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-240">The `override` statement directs the control to use this method in place of the method that was inherited from the base control.</span></span> <span data-ttu-id="1f5c9-241">Bu yöntem çağrıldığında, `base.timer1_Tick` deyimi çağırarak geçersiz kılarak geçersiz kıldığında, özgün denetime dahil edilen tüm işlevlerin bu denetimde çoğaltılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-241">When this method is called, it calls the method it overrides by invoking the `base.timer1_Tick` statement, ensuring that all of the functionality incorporated in the original control is reproduced in this control.</span></span> <span data-ttu-id="1f5c9-242">Daha sonra alarm işlevselliğini birleştirmek için ek kod çalışır.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-242">It then runs additional code to incorporate the alarm functionality.</span></span> <span data-ttu-id="1f5c9-243">Alarm oluştuğunda yanıp sönen bir etiket denetimi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-243">A flashing label control will appear when the alarm occurs.</span></span>

     <span data-ttu-id="1f5c9-244">Çalar saat kontrolünüz neredeyse tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-244">Your alarm clock control is almost complete.</span></span> <span data-ttu-id="1f5c9-245">Geriye kalan tek şey onu kapatmak için bir yol uygulamaktır.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-245">The only thing that remains is to implement a way to turn it off.</span></span> <span data-ttu-id="1f5c9-246">Bunu yapmak için yönteme `lblAlarm_Click` kod eklersiniz.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-246">To do this, you will add code to the `lblAlarm_Click` method.</span></span>

#### <a name="to-implement-the-shutoff-method"></a><span data-ttu-id="1f5c9-247">Kapatma yöntemini uygulamak için</span><span class="sxs-lookup"><span data-stu-id="1f5c9-247">To implement the shutoff method</span></span>

1. <span data-ttu-id="1f5c9-248">**Solution Explorer'da**, **ctlAlarmClock.cs**sağ tıklatın ve ardından **Tasarımcıyı Görüntüle'yi**tıklatın.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-248">In **Solution Explorer**, right-click **ctlAlarmClock.cs**, and then click **View Designer**.</span></span>

     <span data-ttu-id="1f5c9-249">Tasarımcı açılıyor.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-249">The designer opens.</span></span>

2. <span data-ttu-id="1f5c9-250">Denetime bir düğme ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-250">Add a button to the control.</span></span> <span data-ttu-id="1f5c9-251">Düğmenin özelliklerini aşağıdaki gibi ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-251">Set the properties of the button as follows.</span></span>

    |<span data-ttu-id="1f5c9-252">Özellik</span><span class="sxs-lookup"><span data-stu-id="1f5c9-252">Property</span></span>|<span data-ttu-id="1f5c9-253">Değer</span><span class="sxs-lookup"><span data-stu-id="1f5c9-253">Value</span></span>|
    |--------------|-----------|
    |<span data-ttu-id="1f5c9-254">**Adı**</span><span class="sxs-lookup"><span data-stu-id="1f5c9-254">**Name**</span></span>|`btnAlarmOff`|
    |<span data-ttu-id="1f5c9-255">**Metin**</span><span class="sxs-lookup"><span data-stu-id="1f5c9-255">**Text**</span></span>|<span data-ttu-id="1f5c9-256">**Alarmı Devre Dışı**</span><span class="sxs-lookup"><span data-stu-id="1f5c9-256">**Disable Alarm**</span></span>|

3. <span data-ttu-id="1f5c9-257">Tasarımcı olarak, çift tıklayın **btnAlarmOff**.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-257">In the designer, double-click **btnAlarmOff**.</span></span>

     <span data-ttu-id="1f5c9-258">**Kod Düzenleyicisi** `private void btnAlarmOff_Click` satıra açılır.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-258">The **Code Editor** opens to the `private void btnAlarmOff_Click` line.</span></span>

4. <span data-ttu-id="1f5c9-259">Bu yöntemi, aşağıdaki koda benzeyecek şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-259">Modify this method so that it resembles the following code.</span></span>

    ```csharp
    private void btnAlarmOff_Click(object sender, System.EventArgs e)
    {
        // Turns off the alarm.
        AlarmSet = false;
        // Hides the flashing label.
        lblAlarm.Visible = false;
    }
    ```

5. <span data-ttu-id="1f5c9-260">**Dosya** menüsünde, projeyi kaydetmek için **Tümlerini Kaydet'i** tıklatın.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-260">On the **File** menu, click **Save All** to save the project.</span></span>

### <a name="use-the-inherited-control-on-a-form"></a><span data-ttu-id="1f5c9-261">Formda Devralınan Denetimi Kullanma</span><span class="sxs-lookup"><span data-stu-id="1f5c9-261">Use the Inherited Control on a Form</span></span>

<span data-ttu-id="1f5c9-262">Devralınan denetiminizi, temel sınıf denetimini test `ctlClock`ettiğiniz gibi test edebilirsiniz: Projeyi oluşturmak ve denetiminizi **UserControl Test**Kapsayıcısı'nda çalıştırmak için **F5** tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-262">You can test your inherited control the same way you tested the base class control, `ctlClock`: Press **F5** to build the project and run your control in the **UserControl Test Container**.</span></span> <span data-ttu-id="1f5c9-263">Daha fazla bilgi için [bkz: UserControl'un Çalışma Zamanı Davranışını Test Edin.](how-to-test-the-run-time-behavior-of-a-usercontrol.md)</span><span class="sxs-lookup"><span data-stu-id="1f5c9-263">For more information, see [How to: Test the Run-Time Behavior of a UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>

<span data-ttu-id="1f5c9-264">Denetiminizi kullanmak için kullanmak için bir formda barındırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-264">To put your control to use, you will need to host it on a form.</span></span> <span data-ttu-id="1f5c9-265">Standart bileşik denetimde olduğu gibi, devralınan bileşik denetim tek başına duramaz ve bir form veya başka bir kapsayıcıda barındırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-265">As with a standard composite control, an inherited composite control cannot stand alone and must be hosted in a form or other container.</span></span> <span data-ttu-id="1f5c9-266">Daha `ctlAlarmClock` fazla işlevsellik derinliği olduğundan, bunu sınamak için ek kod gereklidir.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-266">Since `ctlAlarmClock` has a greater depth of functionality, additional code is required to test it.</span></span> <span data-ttu-id="1f5c9-267">Bu yordamda, işlevselliğini test etmek için `ctlAlarmClock`basit bir program yazacaktır.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-267">In this procedure, you will write a simple program to test the functionality of `ctlAlarmClock`.</span></span> <span data-ttu-id="1f5c9-268">'nin özelliğini `AlarmTime` `ctlAlarmClock`ayarlamak ve görüntülemek için kod yazar sınız ve doğal işlevlerini sınarsınız.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-268">You will write code to set and display the `AlarmTime` property of `ctlAlarmClock`, and will test its inherent functions.</span></span>

#### <a name="to-build-and-add-your-control-to-a-test-form"></a><span data-ttu-id="1f5c9-269">Denetiminizi oluşturmak ve bir test formuna eklemek için</span><span class="sxs-lookup"><span data-stu-id="1f5c9-269">To build and add your control to a test form</span></span>

1. <span data-ttu-id="1f5c9-270">**Çözüm Gezgini'nde** **ctlClockLib'i**sağ tıklatın ve ardından **Oluştur'u**tıklatın.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-270">In **Solution Explorer**, right-click **ctlClockLib**, and then click **Build**.</span></span>

2. <span data-ttu-id="1f5c9-271">Çözüme yeni bir **Windows Forms Application** projesi ekleyin ve **test**adını.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-271">Add a new **Windows Forms Application** project to the solution, and name it **Test**.</span></span>

3. <span data-ttu-id="1f5c9-272">**Çözüm Gezgini'nde,** test projeniz için **Başvurular** düğümüne sağ tıklayın.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-272">In **Solution Explorer**, right-click the **References** node for your test project.</span></span> <span data-ttu-id="1f5c9-273">**Başvuru Ekle** iletişim kutusunu görüntülemek için Başvuru **Ekle'yi** tıklatın.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-273">Click **Add Reference** to display the **Add Reference** dialog box.</span></span> <span data-ttu-id="1f5c9-274">**Projeler**etiketli sekmeyi tıklatın.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-274">Click the tab labeled **Projects**.</span></span> <span data-ttu-id="1f5c9-275">Projeniz `ctlClockLib` **Proje Adı**altında listelenecektir.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-275">Your `ctlClockLib` project will be listed under **Project Name**.</span></span> <span data-ttu-id="1f5c9-276">Test projesine başvuru eklemek için projeyi çift tıklatın.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-276">Double-click the project to add the reference to the test project.</span></span>

4. <span data-ttu-id="1f5c9-277">**Çözüm Gezgini'nde**, **Test'i**sağ tıklatın ve sonra **Oluştur'u**tıklatın.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-277">In **Solution Explorer**, right-click **Test**, and then click **Build**.</span></span>

5. <span data-ttu-id="1f5c9-278">**Toolbox'ta** **ctlClockLib Components** düğümlerini genişletin.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-278">In the **Toolbox**, expand the **ctlClockLib Components** node.</span></span>

6. <span data-ttu-id="1f5c9-279">Formunuza bir kopyasını eklemek `ctlAlarmClock` için **ctlAlarmClock'u** çift tıklatın.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-279">Double-click **ctlAlarmClock** to add a copy of `ctlAlarmClock` to your form.</span></span>

7. <span data-ttu-id="1f5c9-280">Araç **Kutusu'nda,** formunuza bir <xref:System.Windows.Forms.DateTimePicker> denetim eklemek için **DateTimePicker'ı** bulun <xref:System.Windows.Forms.Label> ve çift tıklatın ve ardından **Etiket'i**çift tıklatarak bir denetim ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-280">In the **Toolbox**, locate and double-click **DateTimePicker** to add a <xref:System.Windows.Forms.DateTimePicker> control to your form, and then add a <xref:System.Windows.Forms.Label> control by double-clicking **Label**.</span></span>

8. <span data-ttu-id="1f5c9-281">Formüzerinde uygun bir yerde kontrolleri konumlandırmak için fareyi kullanın.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-281">Use the mouse to position the controls in a convenient place on the form.</span></span>

9. <span data-ttu-id="1f5c9-282">Bu denetimlerin özelliklerini aşağıdaki şekilde ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-282">Set the properties of these controls in the following manner.</span></span>

    |<span data-ttu-id="1f5c9-283">Denetim</span><span class="sxs-lookup"><span data-stu-id="1f5c9-283">Control</span></span>|<span data-ttu-id="1f5c9-284">Özellik</span><span class="sxs-lookup"><span data-stu-id="1f5c9-284">Property</span></span>|<span data-ttu-id="1f5c9-285">Değer</span><span class="sxs-lookup"><span data-stu-id="1f5c9-285">Value</span></span>|
    |-------------|--------------|-----------|
    |`label1`|<span data-ttu-id="1f5c9-286">**Metin**</span><span class="sxs-lookup"><span data-stu-id="1f5c9-286">**Text**</span></span>|`(blank space)`|
    ||<span data-ttu-id="1f5c9-287">**Adı**</span><span class="sxs-lookup"><span data-stu-id="1f5c9-287">**Name**</span></span>|`lblTest`|
    |`dateTimePicker1`|<span data-ttu-id="1f5c9-288">**Adı**</span><span class="sxs-lookup"><span data-stu-id="1f5c9-288">**Name**</span></span>|`dtpTest`|
    ||<span data-ttu-id="1f5c9-289">**Biçimlendir**</span><span class="sxs-lookup"><span data-stu-id="1f5c9-289">**Format**</span></span>|<xref:System.Windows.Forms.DateTimePickerFormat.Time>|

10. <span data-ttu-id="1f5c9-290">Tasarımcı, **çift dtpTest**tıklayın.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-290">In the designer, double-click **dtpTest**.</span></span>

     <span data-ttu-id="1f5c9-291">**Kod Düzenleyicisi'** ye `private void dtpTest_ValueChanged`'</span><span class="sxs-lookup"><span data-stu-id="1f5c9-291">The **Code Editor** opens to `private void dtpTest_ValueChanged`.</span></span>

11. <span data-ttu-id="1f5c9-292">Kodu aşağıdakilere benzeyecek şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-292">Modify the code so that it resembles the following.</span></span>

    ```csharp
    private void dtpTest_ValueChanged(object sender, System.EventArgs e)
    {
        ctlAlarmClock1.AlarmTime = dtpTest.Value;
        ctlAlarmClock1.AlarmSet = true;
        lblTest.Text = "Alarm Time is " +
            ctlAlarmClock1.AlarmTime.ToShortTimeString();
    }
    ```

12. <span data-ttu-id="1f5c9-293">**Çözüm Gezgini'nde**, **Test'i**sağ tıklatın ve ardından Başlangıç Projesi **olarak ayarla'yı**tıklatın.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-293">In **Solution Explorer**, right-click **Test**, and then click **Set as StartUp Project**.</span></span>

13. <span data-ttu-id="1f5c9-294">**Hata ayıkla** menüsünde **Hata Ayıklamayı Başlat**’a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-294">On the **Debug** menu, click **Start Debugging**.</span></span>

     <span data-ttu-id="1f5c9-295">Test programı başlıyor.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-295">The test program starts.</span></span> <span data-ttu-id="1f5c9-296">Geçerli saatin `ctlAlarmClock` denetimde güncelleştirilediğini ve başlangıç zamanının <xref:System.Windows.Forms.DateTimePicker> denetimde gösterildiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-296">Note that the current time is updated in the `ctlAlarmClock` control, and that the starting time is shown in the <xref:System.Windows.Forms.DateTimePicker> control.</span></span>

14. <span data-ttu-id="1f5c9-297">Saat <xref:System.Windows.Forms.DateTimePicker> dakikalarının görüntülendiği yeri tıklatın.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-297">Click the <xref:System.Windows.Forms.DateTimePicker> where the minutes of the hour are displayed.</span></span>

15. <span data-ttu-id="1f5c9-298">Klavyeyi kullanarak, dakikalar için bir değer `ctlAlarmClock`ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-298">Using the keyboard, set a value for minutes that is one minute greater than the current time shown by `ctlAlarmClock`.</span></span>

     <span data-ttu-id="1f5c9-299">Alarm ayarı için zaman `lblTest`' içinde gösterilir.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-299">The time for the alarm setting is shown in `lblTest`.</span></span> <span data-ttu-id="1f5c9-300">Alarm ayar süresine ulaşmak için görüntülenen zamanı bekleyin.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-300">Wait for the displayed time to reach the alarm setting time.</span></span> <span data-ttu-id="1f5c9-301">Görüntülenen süre alarmın ayarlandığı zamana ulaştığında, `lblAlarm` görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-301">When the displayed time reaches the time to which the alarm is set, the `lblAlarm` will flash.</span></span>

16. <span data-ttu-id="1f5c9-302">Tıklayarak `btnAlarmOff`alarmı kapatın.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-302">Turn off the alarm by clicking `btnAlarmOff`.</span></span> <span data-ttu-id="1f5c9-303">Artık alarmı sıfırlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-303">You may now reset the alarm.</span></span>

<span data-ttu-id="1f5c9-304">Bu makalede, bir dizi temel kavram ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-304">This article has covered a number of key concepts.</span></span> <span data-ttu-id="1f5c9-305">Denetimleri ve bileşenleri bir bileşik denetim kapsayıcısı içinde birleştirerek bileşik denetim oluşturmayı öğrendiniz.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-305">You have learned to create a composite control by combining controls and components into a composite control container.</span></span> <span data-ttu-id="1f5c9-306">Denetiminize özellikler eklemeyi ve özel işlevselliği uygulamak için kod yazmayı öğrendiniz.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-306">You have learned to add properties to your control, and to write code to implement custom functionality.</span></span> <span data-ttu-id="1f5c9-307">Son bölümde, belirli bir bileşik denetimin işlevselliğini devralma yoluyla genişletmeyi ve bu yöntemleri geçersiz kılarak ana bilgisayar yöntemlerinin işlevselliğini değiştirmeyi öğrendiniz.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-307">In the last section, you learned to extend the functionality of a given composite control through inheritance, and to alter the functionality of host methods by overriding those methods.</span></span>

## <a name="see-also"></a><span data-ttu-id="1f5c9-308">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1f5c9-308">See also</span></span>

- [<span data-ttu-id="1f5c9-309">Özel Denetim Çeşitleri</span><span class="sxs-lookup"><span data-stu-id="1f5c9-309">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
- [<span data-ttu-id="1f5c9-310">Nasıl yapılır: Araç Kutusu Öğelerini Seç İletişim Kutusunda bir Denetimi Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="1f5c9-310">How to: Display a Control in the Choose Toolbox Items Dialog Box</span></span>](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)
- [<span data-ttu-id="1f5c9-311">İzlenecek yol: Visual C# ile beraber Windows Forms Denetimi'nden Devralma</span><span class="sxs-lookup"><span data-stu-id="1f5c9-311">Walkthrough: Inheriting from a Windows Forms Control with Visual C#</span></span>](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)
