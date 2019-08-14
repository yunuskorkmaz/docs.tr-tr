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
ms.openlocfilehash: eb3d453a22ecdc40e7d0cac019e784bf74bb372e
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68972326"
---
# <a name="walkthrough-authoring-a-composite-control-with-visual-c"></a><span data-ttu-id="7ef7a-102">İzlenecek yol: Visual C ile bileşik denetim yazma\#</span><span class="sxs-lookup"><span data-stu-id="7ef7a-102">Walkthrough: Authoring a Composite Control with Visual C\#</span></span>

<span data-ttu-id="7ef7a-103">Bileşik denetimler, özel grafik arabirimlerinin oluşturulup yeniden kullanılabilmesi için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-103">Composite controls provide a means by which custom graphical interfaces can be created and reused.</span></span> <span data-ttu-id="7ef7a-104">Bileşik denetim temelde görsel temsili olan bir bileşendir.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-104">A composite control is essentially a component with a visual representation.</span></span> <span data-ttu-id="7ef7a-105">Bu nedenle, Kullanıcı girişini doğrulayarak, görüntü özelliklerini değiştirerek veya yazar için gereken diğer görevleri gerçekleştirerek işlevselliği genişletebilen bir veya daha fazla Windows Forms denetimi, bileşeni veya kod bloklarında bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-105">As such, it might consist of one or more Windows Forms controls, components, or blocks of code that can extend functionality by validating user input, modifying display properties, or performing other tasks required by the author.</span></span> <span data-ttu-id="7ef7a-106">Bileşik denetimler Windows Forms diğer denetimlerle aynı şekilde yerleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-106">Composite controls can be placed on Windows Forms in the same manner as other controls.</span></span> <span data-ttu-id="7ef7a-107">Bu izlenecek yolun ilk bölümünde adlı `ctlClock`basit bir bileşik denetim oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-107">In the first part of this walkthrough, you create a simple composite control called `ctlClock`.</span></span> <span data-ttu-id="7ef7a-108">İzlenecek yolun ikinci bölümünde, devralma `ctlClock` ile işlevlerini genişletebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-108">In the second part of the walkthrough, you extend the functionality of `ctlClock` through inheritance.</span></span>

> [!NOTE]
> <span data-ttu-id="7ef7a-109">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-109">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="7ef7a-110">Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-110">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="7ef7a-111">Daha fazla bilgi için bkz. [Visual STUDIO IDE 'Yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="7ef7a-111">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>

## <a name="creating-the-project"></a><span data-ttu-id="7ef7a-112">Projeyi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="7ef7a-112">Creating the Project</span></span>

<span data-ttu-id="7ef7a-113">Yeni bir proje oluşturduğunuzda, kök ad alanı, derleme adı ve proje adını ayarlamak için adını belirtin ve varsayılan bileşenin doğru ad alanında yer aldığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-113">When you create a new project, you specify its name to set the root namespace, assembly name, and project name, and ensure that the default component will be in the correct namespace.</span></span>

### <a name="to-create-the-ctlclocklib-control-library-and-the-ctlclock-control"></a><span data-ttu-id="7ef7a-114">CtlClockLib denetim kitaplığını ve ctlClock denetimini oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="7ef7a-114">To create the ctlClockLib control library and the ctlClock control</span></span>

1. <span data-ttu-id="7ef7a-115">**Dosya** menüsünde, **Yeni**' nin üzerine gelin ve ardından **Proje** ' ye tıklayarak **Yeni proje** iletişim kutusunu açın.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-115">On the **File** menu, point to **New**, and then click **Project** to open the **New Project** dialog box.</span></span>

2. <span data-ttu-id="7ef7a-116">Görsel C# proje listesinden **Windows Forms denetim kitaplığı** proje şablonu ' nu seçin, `ctlClockLib` **ad** kutusuna yazın ve ardından **Tamam**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-116">From the list of Visual C# projects, select the **Windows Forms Control Library** project template, type `ctlClockLib` in the **Name** box, and then click **OK**.</span></span>

     <span data-ttu-id="7ef7a-117">Proje adı `ctlClockLib`, varsayılan olarak kök ad alanına da atanır.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-117">The project name, `ctlClockLib`, is also assigned to the root namespace by default.</span></span> <span data-ttu-id="7ef7a-118">Kök ad alanı, derlemedeki bileşenlerin adlarını nitelemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-118">The root namespace is used to qualify the names of components in the assembly.</span></span> <span data-ttu-id="7ef7a-119">Örneğin, iki derleme adlı `ctlClock`bileşenler içeriyorsa, `ctlClock` bileşenini kullanarak`ctlClockLib.ctlClock.`</span><span class="sxs-lookup"><span data-stu-id="7ef7a-119">For example, if two assemblies provide components named `ctlClock`, you can specify your `ctlClock` component using `ctlClockLib.ctlClock.`</span></span>

3. <span data-ttu-id="7ef7a-120">Çözüm Gezgini ' de, **UserControl1.cs**' a sağ tıklayın ve ardından **Yeniden Adlandır**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-120">In Solution Explorer, right-click **UserControl1.cs**, and then click **Rename**.</span></span> <span data-ttu-id="7ef7a-121">Dosya adını olarak `ctlClock.cs`değiştirin.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-121">Change the file name to `ctlClock.cs`.</span></span> <span data-ttu-id="7ef7a-122">"UserControl1" kod öğesiyle tüm başvuruları yeniden adlandırmak isteyip istemediğiniz sorulduğunda **Evet** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-122">Click the **Yes** button when you are asked if you want to rename all references to the code element "UserControl1".</span></span>

    > [!NOTE]
    > <span data-ttu-id="7ef7a-123">Varsayılan olarak, bileşik bir denetim sistem tarafından sunulan <xref:System.Windows.Forms.UserControl> sınıftan devralınır.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-123">By default, a composite control inherits from the <xref:System.Windows.Forms.UserControl> class provided by the system.</span></span> <span data-ttu-id="7ef7a-124"><xref:System.Windows.Forms.UserControl> Sınıfı, tüm bileşik denetimlerin gerektirdiği işlevselliği sağlar ve standart yöntemler ve özellikler uygular.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-124">The <xref:System.Windows.Forms.UserControl> class provides functionality required by all composite controls, and implements standard methods and properties.</span></span>

4. <span data-ttu-id="7ef7a-125">Projeyi kaydetmek için **Dosya** menüsünde **Tümünü Kaydet** ' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-125">On the **File** menu, click **Save All** to save the project.</span></span>

## <a name="adding-windows-controls-and-components-to-the-composite-control"></a><span data-ttu-id="7ef7a-126">Bileşik denetime Windows denetimleri ve bileşenleri ekleme</span><span class="sxs-lookup"><span data-stu-id="7ef7a-126">Adding Windows Controls and Components to the Composite Control</span></span>

<span data-ttu-id="7ef7a-127">Görsel arabirim, bileşik denetiminizin temel bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-127">A visual interface is an essential part of your composite control.</span></span> <span data-ttu-id="7ef7a-128">Bu görsel arabirim, tasarımcı yüzeyine bir veya daha fazla Windows denetimi eklenerek uygulanır.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-128">This visual interface is implemented by the addition of one or more Windows controls to the designer surface.</span></span> <span data-ttu-id="7ef7a-129">Aşağıdaki gösteride, Windows denetimlerini bileşik denetiminizle birleştirirsiniz ve işlevselliği uygulamak için kod yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-129">In the following demonstration, you will incorporate Windows controls into your composite control and write code to implement functionality.</span></span>

### <a name="to-add-a-label-and-a-timer-to-your-composite-control"></a><span data-ttu-id="7ef7a-130">Bileşik denetilemenize bir etiket ve süreölçer eklemek için</span><span class="sxs-lookup"><span data-stu-id="7ef7a-130">To add a Label and a Timer to your composite control</span></span>

1. <span data-ttu-id="7ef7a-131">Çözüm Gezgini ' de, **ctlClock.cs**' a sağ tıklayın ve ardından **tasarımcıyı görüntüle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-131">In Solution Explorer, right-click **ctlClock.cs**, and then click **View Designer**.</span></span>

2. <span data-ttu-id="7ef7a-132">**Araç kutusunda** **ortak denetimler** düğümünü genişletin ve ardından **etiket**' e çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-132">In the **Toolbox**, expand the **Common Controls** node, and then double-click **Label**.</span></span>

     <span data-ttu-id="7ef7a-133">Tasarımcı <xref:System.Windows.Forms.Label> yüzeyinde denetimciyle adlandırılmış `label1` bir denetim eklenir.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-133">A <xref:System.Windows.Forms.Label> control named `label1` is added to your control on the designer surface.</span></span>

3. <span data-ttu-id="7ef7a-134">Tasarımcıda **Label1**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-134">In the designer, click **label1**.</span></span> <span data-ttu-id="7ef7a-135">Özellikler penceresi, aşağıdaki özellikleri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-135">In the Properties window, set the following properties.</span></span>

    |<span data-ttu-id="7ef7a-136">Özellik</span><span class="sxs-lookup"><span data-stu-id="7ef7a-136">Property</span></span>|<span data-ttu-id="7ef7a-137">Değiştir</span><span class="sxs-lookup"><span data-stu-id="7ef7a-137">Change to</span></span>|
    |--------------|---------------|
    |<span data-ttu-id="7ef7a-138">**Ad**</span><span class="sxs-lookup"><span data-stu-id="7ef7a-138">**Name**</span></span>|`lblDisplay`|
    |<span data-ttu-id="7ef7a-139">**Metin**</span><span class="sxs-lookup"><span data-stu-id="7ef7a-139">**Text**</span></span>|`(blank space)`|
    |<span data-ttu-id="7ef7a-140">**TextAlign**</span><span class="sxs-lookup"><span data-stu-id="7ef7a-140">**TextAlign**</span></span>|`MiddleCenter`|
    |<span data-ttu-id="7ef7a-141">**Yazı tipi. boyutu**</span><span class="sxs-lookup"><span data-stu-id="7ef7a-141">**Font.Size**</span></span>|`14`|

4. <span data-ttu-id="7ef7a-142">**Araç kutusunda**, **Bileşenler** düğümünü genişletin ve ardından **Zamanlayıcı**' ya çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-142">In the **Toolbox**, expand the **Components** node, and then double-click **Timer**.</span></span>

     <span data-ttu-id="7ef7a-143">Bir <xref:System.Windows.Forms.Timer> bileşen olduğundan, çalışma zamanında görsel temsili yoktur.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-143">Because a <xref:System.Windows.Forms.Timer> is a component, it has no visual representation at run time.</span></span> <span data-ttu-id="7ef7a-144">Bu nedenle, tasarımcı yüzeyindeki denetimlerde görünmez, ancak **Bileşen tasarımcısında** (tasarımcı yüzeyinin altındaki bir tepsi) değil.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-144">Therefore, it does not appear with the controls on the designer surface, but rather in the **Component Designer** (a tray at the bottom of the designer surface).</span></span>

5. <span data-ttu-id="7ef7a-145">**Bileşen tasarımcısında**, **Süreölçer1** <xref:System.Windows.Forms.Timer.Interval%2A> ' a tıklayın ve ardından özelliğini `1000` ve <xref:System.Windows.Forms.Timer.Enabled%2A> özelliğini olarak `true`ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-145">In the **Component Designer**, click **timer1**, and then set the <xref:System.Windows.Forms.Timer.Interval%2A> property to `1000` and the <xref:System.Windows.Forms.Timer.Enabled%2A> property to `true`.</span></span>

     <span data-ttu-id="7ef7a-146"><xref:System.Windows.Forms.Timer.Interval%2A> Özelliği <xref:System.Windows.Forms.Timer> bileşeni işaret eden sıklığı denetler.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-146">The <xref:System.Windows.Forms.Timer.Interval%2A> property controls the frequency with which the <xref:System.Windows.Forms.Timer> component ticks.</span></span> <span data-ttu-id="7ef7a-147">Her zaman `timer1` Tick, `timer1_Tick` olaydaki kodu çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-147">Each time `timer1` ticks, it runs the code in the `timer1_Tick` event.</span></span> <span data-ttu-id="7ef7a-148">Aralık, zaman işaretleri arasındaki milisaniye sayısını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-148">The interval represents the number of milliseconds between ticks.</span></span>

6. <span data-ttu-id="7ef7a-149">**Bileşen tasarımcısında**, için **Süreölçer1** öğesine çift tıklayarak için `timer1_Tick` `ctlClock`olayına gidin.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-149">In the **Component Designer**, double-click **timer1** to go to the `timer1_Tick` event for `ctlClock`.</span></span>

7. <span data-ttu-id="7ef7a-150">Kodu aşağıdaki kod örneğine benzer olacak şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-150">Modify the code so that it resembles the following code sample.</span></span> <span data-ttu-id="7ef7a-151">Erişim değiştiricisini ' dan `private` `protected`' a değiştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-151">Be sure to change the access modifier from `private` to `protected`.</span></span>

    ```csharp
    protected void timer1_Tick(object sender, System.EventArgs e)
    {
        // Causes the label to display the current time.
        lblDisplay.Text = DateTime.Now.ToLongTimeString();
    }
    ```

     <span data-ttu-id="7ef7a-152">Bu kod, geçerli saatin ' de `lblDisplay`görüntülenmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-152">This code will cause the current time to be shown in `lblDisplay`.</span></span> <span data-ttu-id="7ef7a-153">Aralığı `timer1` olarak ayarlandığı için `1000`bu olay her bin milisaniyede bir gerçekleşeceğinden, bu nedenle her saniye geçerli saati güncelliyor.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-153">Because the interval of `timer1` was set to `1000`, this event will occur every thousand milliseconds, thus updating the current time every second.</span></span>

8. <span data-ttu-id="7ef7a-154">Yöntemini `virtual` anahtar sözcüğüyle geçersiz kılınabilir olacak şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-154">Modify the method to be overridable with the `virtual` keyword.</span></span> <span data-ttu-id="7ef7a-155">Daha fazla bilgi için aşağıdaki "Kullanıcı denetiminden devralma" bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-155">For more information, see the  "Inheriting from a User Control" section below.</span></span>

    ```csharp
    protected virtual void timer1_Tick(object sender, System.EventArgs e)
    ```

9. <span data-ttu-id="7ef7a-156">Projeyi kaydetmek için **Dosya** menüsünde **Tümünü Kaydet** ' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-156">On the **File** menu, click **Save All** to save the project.</span></span>

## <a name="adding-properties-to-the-composite-control"></a><span data-ttu-id="7ef7a-157">Bileşik denetime özellikler ekleme</span><span class="sxs-lookup"><span data-stu-id="7ef7a-157">Adding Properties to the Composite Control</span></span>

<span data-ttu-id="7ef7a-158">Saat denetiminiz artık, her biri <xref:System.Windows.Forms.Label> kendi kendine ait <xref:System.Windows.Forms.Timer> özellikler kümesiyle birlikte bir denetimi ve bileşeni kapsüller.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-158">Your clock control now encapsulates a <xref:System.Windows.Forms.Label> control and a <xref:System.Windows.Forms.Timer> component, each with its own set of inherent properties.</span></span> <span data-ttu-id="7ef7a-159">Bu denetimlerin tek tek özelliklerine denetiminizin sonraki kullanıcıları tarafından erişilemese de, uygun kod bloklarını yazarak özel özellikler oluşturabilir ve kullanıma sunabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-159">While the individual properties of these controls will not be accessible to subsequent users of your control, you can create and expose custom properties by writing the appropriate blocks of code.</span></span> <span data-ttu-id="7ef7a-160">Aşağıdaki yordamda, denetime, kullanıcının arka plan ve metin rengini değiştirmesini sağlayan özellikler ekleyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-160">In the following procedure, you will add properties to your control that enable the user to change the color of the background and text.</span></span>

### <a name="to-add-a-property-to-your-composite-control"></a><span data-ttu-id="7ef7a-161">Bileşik denetimi bir özellik eklemek için</span><span class="sxs-lookup"><span data-stu-id="7ef7a-161">To add a property to your composite control</span></span>

1. <span data-ttu-id="7ef7a-162">Çözüm Gezgini ' de, **ctlClock.cs**' a sağ tıklayın ve ardından **kodu görüntüle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-162">In Solution Explorer, right-click **ctlClock.cs**, and then click **View Code**.</span></span>

     <span data-ttu-id="7ef7a-163">Denetiminizin **Kod Düzenleyicisi** açılır.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-163">The **Code Editor** for your control opens.</span></span>

2. <span data-ttu-id="7ef7a-164">`public partial class ctlClock` İfadesini bulun.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-164">Locate the `public partial class ctlClock` statement.</span></span> <span data-ttu-id="7ef7a-165">Açma küme ayracı`{)`altında, aşağıdaki kodu yazın.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-165">Beneath the opening brace (`{)`, type the following code.</span></span>

    ```csharp
    private Color colFColor;
    private Color colBColor;
    ```

     <span data-ttu-id="7ef7a-166">Bu deyimler, oluşturmak üzere olduğunuz özelliklerin değerlerini depolamak için kullanacağınız özel değişkenleri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-166">These statements create the private variables that you will use to store the values for the properties you are about to create.</span></span>

3. <span data-ttu-id="7ef7a-167">2\. adımdaki değişken bildirimlerinin altına aşağıdaki kodu yazın.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-167">Type the following code beneath the variable declarations from step 2.</span></span>

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

     <span data-ttu-id="7ef7a-168">Yukarıdaki kod iki özel özellik `ClockForeColor` yapar ve `ClockBackColor`bu denetimin sonraki kullanıcıları tarafından kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-168">The preceding code makes two custom properties, `ClockForeColor` and `ClockBackColor`, available to subsequent users of this control.</span></span> <span data-ttu-id="7ef7a-169">`get` Ve`set` deyimleri, özellik değerinin depolanmasını ve alınmasını, ayrıca özelliğine uygun işlevselliği uygulamak için de kod sağlar.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-169">The `get` and `set` statements provide for storage and retrieval of the property value, as well as code to implement functionality appropriate to the property.</span></span>

4. <span data-ttu-id="7ef7a-170">Projeyi kaydetmek için **Dosya** menüsünde **Tümünü Kaydet** ' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-170">On the **File** menu, click **Save All** to save the project.</span></span>

## <a name="testing-the-control"></a><span data-ttu-id="7ef7a-171">Denetimi test etme</span><span class="sxs-lookup"><span data-stu-id="7ef7a-171">Testing the Control</span></span>

<span data-ttu-id="7ef7a-172">Denetimler tek başına uygulamalar değildir; Bunlar bir kapsayıcıda barındırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-172">Controls are not stand-alone applications; they must be hosted in a container.</span></span> <span data-ttu-id="7ef7a-173">Denetiminizin çalışma zamanı davranışını test edin ve özelliklerini **UserControl Test kapsayıcısı**ile çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-173">Test your control's run-time behavior and exercise its properties with the **UserControl Test Container**.</span></span> <span data-ttu-id="7ef7a-174">Daha fazla bilgi için [nasıl yapılır: UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md)'un çalışma zamanı davranışını test edin.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-174">For more information, see [How to: Test the Run-Time Behavior of a UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>

### <a name="to-test-your-control"></a><span data-ttu-id="7ef7a-175">Denetiminizi test etmek için</span><span class="sxs-lookup"><span data-stu-id="7ef7a-175">To test your control</span></span>

1. <span data-ttu-id="7ef7a-176">Projeyi derlemek için F5 tuşuna basın ve denetimi **UserControl Test kapsayıcısında**çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-176">Press F5 to build the project and run your control in the **UserControl Test Container**.</span></span>

2. <span data-ttu-id="7ef7a-177">Test kapsayıcısının özellik kılavuzunda, `ClockBackColor` özelliğini bulun ve ardından renk paletini göstermek için özelliği seçin.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-177">In the test container's property grid, locate the `ClockBackColor` property, and then select the property to display the color palette.</span></span>

3. <span data-ttu-id="7ef7a-178">Tıklayarak bir renk seçin.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-178">Choose a color by clicking it.</span></span>

     <span data-ttu-id="7ef7a-179">Denetiminizin arka plan rengi, seçtiğiniz renge değişir.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-179">The background color of your control changes to the color you selected.</span></span>

4. <span data-ttu-id="7ef7a-180">`ClockForeColor` Özelliğin beklendiği gibi çalıştığını doğrulamak için benzer bir olay dizisi kullanın.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-180">Use a similar sequence of events to verify that the `ClockForeColor` property is functioning as expected.</span></span>

     <span data-ttu-id="7ef7a-181">Bu bölümde ve önceki bölümlerde, bileşik denetim biçiminde özel işlevsellik sağlamak için bileşenlerin ve Windows denetimlerinin kod ve paketleme ile nasıl birleştirilebileceği gördünüz.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-181">In this section and the preceding sections, you have seen how components and Windows controls can be combined with code and packaging to provide custom functionality in the form of a composite control.</span></span> <span data-ttu-id="7ef7a-182">Birleşik denetidiklerinizin özelliklerini açığa çıkarmak ve tamamlandıktan sonra denetiminizi test etmek için öğrendiniz.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-182">You have learned to expose properties in your composite control, and how to test your control after it is complete.</span></span> <span data-ttu-id="7ef7a-183">Sonraki bölümde, temel olarak kullanarak `ctlClock` devralınmış bir bileşik denetim oluşturmayı öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-183">In the next section you will learn how to construct an inherited composite control using `ctlClock` as a base.</span></span>

## <a name="inheriting-from-a-composite-control"></a><span data-ttu-id="7ef7a-184">Bileşik denetimden devralma</span><span class="sxs-lookup"><span data-stu-id="7ef7a-184">Inheriting from a Composite Control</span></span>

<span data-ttu-id="7ef7a-185">Önceki bölümlerde, Windows denetimlerini, bileşenleri ve kodu yeniden kullanılabilir bileşik denetimlere nasıl birleştirebileceğinizi öğrendiniz.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-185">In the previous sections, you learned how to combine Windows controls, components, and code into reusable composite controls.</span></span> <span data-ttu-id="7ef7a-186">Bileşik denetiminiz artık diğer denetimlerin derlenme temeli olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-186">Your composite control can now be used as a base upon which other controls can be built.</span></span> <span data-ttu-id="7ef7a-187">Temel sınıftan bir sınıfın türeme işlemi *Devralma*olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-187">The process of deriving a class from a base class is called *inheritance*.</span></span> <span data-ttu-id="7ef7a-188">Bu bölümde, adlı `ctlAlarmClock`bir bileşik denetim oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-188">In this section, you will create a composite control called `ctlAlarmClock`.</span></span> <span data-ttu-id="7ef7a-189">Bu denetim, `ctlClock`üst denetiminden türetilecektir.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-189">This control will be derived from its parent control, `ctlClock`.</span></span> <span data-ttu-id="7ef7a-190">Üst yöntemleri geçersiz kılarak ve yeni yöntemler ve `ctlClock` özellikler ekleyerek işlevselliğini genişletmeyi öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-190">You will learn to extend the functionality of `ctlClock` by overriding parent methods and adding new methods and properties.</span></span>

<span data-ttu-id="7ef7a-191">Devralınan bir denetim oluşturmanın ilk adımı onu üst öğesinden türemektir.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-191">The first step in creating an inherited control is to derive it from its parent.</span></span> <span data-ttu-id="7ef7a-192">Bu eylem, üst denetimin tüm özelliklerine, yöntemlerine ve grafiksel özelliklerine sahip yeni bir denetim oluşturur, ancak yeni veya değiştirilmiş işlevselliğin eklenmesi için temel olarak da davranabilir.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-192">This action creates a new control that has all of the properties, methods, and graphical characteristics of the parent control, but can also act as a base for the addition of new or modified functionality.</span></span>

### <a name="to-create-the-inherited-control"></a><span data-ttu-id="7ef7a-193">Devralınan denetimi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="7ef7a-193">To create the inherited control</span></span>

1. <span data-ttu-id="7ef7a-194">Çözüm Gezgini ' de, **ctlClockLib**' a sağ tıklayın, **Ekle**' nin üzerine gelin ve **Kullanıcı denetimi**' ne tıklayın.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-194">In Solution Explorer, right-click **ctlClockLib**, point to **Add**, and then click **User Control**.</span></span>

     <span data-ttu-id="7ef7a-195">**Yeni Öğe Ekle** iletişim kutusu açılır.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-195">The **Add New Item** dialog box opens.</span></span>

2. <span data-ttu-id="7ef7a-196">**Devralınan Kullanıcı denetimi** şablonunu seçin.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-196">Select the **Inherited User Control** template.</span></span>

3. <span data-ttu-id="7ef7a-197">**Ad** kutusuna yazın `ctlAlarmClock.cs`ve ardından **Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-197">In the **Name** box, type `ctlAlarmClock.cs`, and then click **Add**.</span></span>

     <span data-ttu-id="7ef7a-198">**Devralma Seçicisi** iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-198">The **Inheritance Picker** dialog box appears.</span></span>

4. <span data-ttu-id="7ef7a-199">**Bileşen adı**altında **ctlClock**' ye çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-199">Under **Component Name**, double-click **ctlClock**.</span></span>

5. <span data-ttu-id="7ef7a-200">Çözüm Gezgini, geçerli projelere göz atabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-200">In Solution Explorer, browse through the current projects.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="7ef7a-201">Geçerli projeye **ctlAlarmClock.cs** adlı bir dosya eklendi.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-201">A file called **ctlAlarmClock.cs** has been added to the current project.</span></span>

### <a name="adding-the-alarm-properties"></a><span data-ttu-id="7ef7a-202">Alarm özelliklerini ekleme</span><span class="sxs-lookup"><span data-stu-id="7ef7a-202">Adding the Alarm Properties</span></span>

<span data-ttu-id="7ef7a-203">Özellikler, devralınan bir denetime, Birleşik bir denetime eklendikçe aynı şekilde eklenir.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-203">Properties are added to an inherited control in the same way they are added to a composite control.</span></span> <span data-ttu-id="7ef7a-204">Şimdi, denetimidir için iki özellik eklemek üzere özellik bildirimi söz dizimini kullanacaksınız: `AlarmTime`bu, uyarının bitiş tarihini ve saatini depolayan ve `AlarmSet`alarmın ayarlanmış olup olmadığını belirtecektir.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-204">You will now use the property declaration syntax to add two properties to your control: `AlarmTime`, which will store the value of the date and time the alarm is to go off, and `AlarmSet`, which will indicate whether the alarm is set.</span></span>

#### <a name="to-add-properties-to-your-composite-control"></a><span data-ttu-id="7ef7a-205">Bileşik denetimi özellikler eklemek için</span><span class="sxs-lookup"><span data-stu-id="7ef7a-205">To add properties to your composite control</span></span>

1. <span data-ttu-id="7ef7a-206">Çözüm Gezgini ' de, **ctlAlarmClock**' a sağ tıklayın ve ardından **kodu görüntüle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-206">In Solution Explorer, right-click **ctlAlarmClock**, and then click **View Code**.</span></span>

2. <span data-ttu-id="7ef7a-207">`public class` İfadesini bulun.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-207">Locate the `public class` statement.</span></span> <span data-ttu-id="7ef7a-208">Denetiminizin öğesinden `ctlClockLib.ctlClock`devraldığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-208">Note that your control inherits from `ctlClockLib.ctlClock`.</span></span> <span data-ttu-id="7ef7a-209">Açma küme ayracı (`{)` deyimin altına aşağıdaki kodu yazın.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-209">Beneath the opening brace (`{)` statement, type the following code.</span></span>

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

### <a name="adding-to-the-graphical-interface-of-the-control"></a><span data-ttu-id="7ef7a-210">Denetimin grafik arabirimine ekleme</span><span class="sxs-lookup"><span data-stu-id="7ef7a-210">Adding to the Graphical Interface of the Control</span></span>

<span data-ttu-id="7ef7a-211">Devralınan denetiminizin devraldığı denetimle özdeş bir görsel arabirimi vardır.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-211">Your inherited control has a visual interface that is identical to the control it inherits from.</span></span> <span data-ttu-id="7ef7a-212">Kendi üst denetimiyle aynı bileşen denetimlerine sahip olur, ancak yapısal denetimlerin özellikleri özellikle gösterilmedikleri sürece kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-212">It possesses the same constituent controls as its parent control, but the properties of the constituent controls will not be available unless they were specifically exposed.</span></span> <span data-ttu-id="7ef7a-213">Devralınan bir bileşik denetimin grafik arabirimine, herhangi bir bileşik denetime ekleyeceğiniz şekilde ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-213">You may add to the graphical interface of an inherited composite control in the same manner as you would add to any composite control.</span></span> <span data-ttu-id="7ef7a-214">Alarm saatinizin görsel arabirimine eklemeye devam etmek için, alarm bir işlem olduğunda Flash olacak bir etiket denetimi ekleyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-214">To continue adding to your alarm clock's visual interface, you will add a label control that will flash when the alarm is sounding.</span></span>

#### <a name="to-add-the-label-control"></a><span data-ttu-id="7ef7a-215">Etiket denetimi eklemek için</span><span class="sxs-lookup"><span data-stu-id="7ef7a-215">To add the label control</span></span>

1. <span data-ttu-id="7ef7a-216">Çözüm Gezgini ' de, **ctlAlarmClock**' a sağ tıklayın ve ardından **tasarımcıyı görüntüle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-216">In Solution Explorer, right-click **ctlAlarmClock**, and then click **View Designer**.</span></span>

     <span data-ttu-id="7ef7a-217">İçin `ctlAlarmClock` tasarımcı ana pencerede açılır.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-217">The designer for `ctlAlarmClock` opens in the main window.</span></span>

2. <span data-ttu-id="7ef7a-218">Denetimin görüntüleme bölümüne tıklayın ve Özellikler penceresi görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-218">Click the display portion of the control, and view the Properties window.</span></span>

    > [!NOTE]
    > <span data-ttu-id="7ef7a-219">Tüm özellikler görüntülenirken, soluk olurlar.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-219">While all the properties are displayed, they are dimmed.</span></span> <span data-ttu-id="7ef7a-220">Bu özelliklerin yerel `lblDisplay` olduğunu ve Özellikler penceresi değiştirilemeyeceğini veya erişilmeyeceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-220">This indicates that these properties are native to `lblDisplay` and cannot be modified or accessed in the Properties window.</span></span> <span data-ttu-id="7ef7a-221">Varsayılan olarak, bileşik denetimde `private`bulunan denetimler ve özellikleri herhangi bir şekilde erişilebilir değildir.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-221">By default, controls contained in a composite control are `private`, and their properties are not accessible by any means.</span></span>

    > [!NOTE]
    > <span data-ttu-id="7ef7a-222">Bileşik denetiminizin sonraki kullanıcılarının iç denetimlerine erişimi olmasını istiyorsanız, veya `public` `protected`olarak bildirin.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-222">If you want subsequent users of your composite control to have access to its internal controls, declare them as `public` or `protected`.</span></span> <span data-ttu-id="7ef7a-223">Bu, uygun kodu kullanarak bileşik denetilinizin içindeki denetimlerin özelliklerini ayarlamanıza ve değiştirmenize izin verir.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-223">This will allow you to set and modify properties of controls contained within your composite control by using the appropriate code.</span></span>

3. <span data-ttu-id="7ef7a-224">Bileşik denetimi bir <xref:System.Windows.Forms.Label> denetim ekleyin.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-224">Add a <xref:System.Windows.Forms.Label> control to your composite control.</span></span>

4. <span data-ttu-id="7ef7a-225">Fareyi kullanarak <xref:System.Windows.Forms.Label> denetimi, ekran kutusunun hemen altına sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-225">Using the mouse, drag the <xref:System.Windows.Forms.Label> control immediately beneath the display box.</span></span> <span data-ttu-id="7ef7a-226">Özellikler penceresi, aşağıdaki özellikleri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-226">In the Properties window, set the following properties.</span></span>

    |<span data-ttu-id="7ef7a-227">Özellik</span><span class="sxs-lookup"><span data-stu-id="7ef7a-227">Property</span></span>|<span data-ttu-id="7ef7a-228">Ayar</span><span class="sxs-lookup"><span data-stu-id="7ef7a-228">Setting</span></span>|
    |--------------|-------------|
    |<span data-ttu-id="7ef7a-229">**Ad**</span><span class="sxs-lookup"><span data-stu-id="7ef7a-229">**Name**</span></span>|`lblAlarm`|
    |<span data-ttu-id="7ef7a-230">**Metin**</span><span class="sxs-lookup"><span data-stu-id="7ef7a-230">**Text**</span></span>|<span data-ttu-id="7ef7a-231">**Alarm!**</span><span class="sxs-lookup"><span data-stu-id="7ef7a-231">**Alarm!**</span></span>|
    |<span data-ttu-id="7ef7a-232">**TextAlign**</span><span class="sxs-lookup"><span data-stu-id="7ef7a-232">**TextAlign**</span></span>|`MiddleCenter`|
    |<span data-ttu-id="7ef7a-233">**Görüne**</span><span class="sxs-lookup"><span data-stu-id="7ef7a-233">**Visible**</span></span>|`false`|

### <a name="adding-the-alarm-functionality"></a><span data-ttu-id="7ef7a-234">Alarm Işlevlerini ekleme</span><span class="sxs-lookup"><span data-stu-id="7ef7a-234">Adding the Alarm Functionality</span></span>

<span data-ttu-id="7ef7a-235">Önceki yordamlarda, bileşik denetiminizdeki alarm işlevselliğini etkinleştiren Özellikler ve bir denetim eklediniz.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-235">In the previous procedures, you added properties and a control that will enable alarm functionality in your composite control.</span></span> <span data-ttu-id="7ef7a-236">Bu yordamda, geçerli saati alarm zamanına göre karşılaştırmak için kod ekleyeceksiniz ve aynı ise, bir alarm Flash için de aynı olduğunda.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-236">In this procedure, you will add code to compare the current time to the alarm time and, if they are the same, to flash an alarm.</span></span> <span data-ttu-id="7ef7a-237">`timer1_Tick` `ctlAlarmClock` Yöntemini geçersiz kılarak ve buna ek kod ekleyerek, tüm devralınan işlevlerini `ctlClock`korurken özelliğini genişletebilirsiniz. `ctlClock`</span><span class="sxs-lookup"><span data-stu-id="7ef7a-237">By overriding the `timer1_Tick` method of `ctlClock` and adding additional code to it, you will extend the capability of `ctlAlarmClock` while retaining all of the inherent functionality of `ctlClock`.</span></span>

#### <a name="to-override-the-timer1_tick-method-of-ctlclock"></a><span data-ttu-id="7ef7a-238">CtlClock timer1_Tick yöntemini geçersiz kılmak için</span><span class="sxs-lookup"><span data-stu-id="7ef7a-238">To override the timer1_Tick method of ctlClock</span></span>

1. <span data-ttu-id="7ef7a-239">**Kod düzenleyicisinde**, `private bool blnAlarmSet;` ifadesini bulun.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-239">In the **Code Editor**, locate the `private bool blnAlarmSet;` statement.</span></span> <span data-ttu-id="7ef7a-240">Hemen hemen altına aşağıdaki ifadeyi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-240">Immediately beneath it, add the following statement.</span></span>

    ```csharp
    private bool blnColorTicker;
    ```

2. <span data-ttu-id="7ef7a-241">**Kod Düzenleyicisi**'nde, kapatma küme ayracını (`})` sınıfının sonundaki) bulun.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-241">In the **Code Editor**, locate the closing brace (`})` at the end of the class.</span></span> <span data-ttu-id="7ef7a-242">Küme ayracından hemen önce aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-242">Just before the brace, add the following code.</span></span>

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

     <span data-ttu-id="7ef7a-243">Bu kodun eklenmesi birkaç görevi gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-243">The addition of this code accomplishes several tasks.</span></span> <span data-ttu-id="7ef7a-244">`override` İfade, denetimi temel denetimden devralınan yöntemin yerine bu yöntemi kullanacak şekilde yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-244">The `override` statement directs the control to use this method in place of the method that was inherited from the base control.</span></span> <span data-ttu-id="7ef7a-245">Bu yöntem çağrıldığında, `base.timer1_Tick` ifadeyi çağırarak geçersiz kıldığından, özgün denetimde dahil edilen tüm işlevlerin Bu denetimde yeniden üretildiğinden emin olarak çağrılır.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-245">When this method is called, it calls the method it overrides by invoking the `base.timer1_Tick` statement, ensuring that all of the functionality incorporated in the original control is reproduced in this control.</span></span> <span data-ttu-id="7ef7a-246">Daha sonra alarm işlevselliğini birleştirmek için ek kod çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-246">It then runs additional code to incorporate the alarm functionality.</span></span> <span data-ttu-id="7ef7a-247">Uyarı oluştuğunda yanıp sönen bir etiket denetimi görünür.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-247">A flashing label control will appear when the alarm occurs.</span></span>

     <span data-ttu-id="7ef7a-248">Alarm saati denetiminiz neredeyse tamamlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-248">Your alarm clock control is almost complete.</span></span> <span data-ttu-id="7ef7a-249">Kalan tek şey, devre dışı bırakmak için bir yol uygulamaktır.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-249">The only thing that remains is to implement a way to turn it off.</span></span> <span data-ttu-id="7ef7a-250">Bunu yapmak için `lblAlarm_Click` yöntemine kod ekleyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-250">To do this, you will add code to the `lblAlarm_Click` method.</span></span>

#### <a name="to-implement-the-shutoff-method"></a><span data-ttu-id="7ef7a-251">Shutoff yöntemini uygulamak için</span><span class="sxs-lookup"><span data-stu-id="7ef7a-251">To implement the shutoff method</span></span>

1. <span data-ttu-id="7ef7a-252">Çözüm Gezgini ' de, **ctlAlarmClock.cs**' a sağ tıklayın ve ardından **tasarımcıyı görüntüle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-252">In Solution Explorer, right-click **ctlAlarmClock.cs**, and then click **View Designer**.</span></span>

     <span data-ttu-id="7ef7a-253">Tasarımcı açılır.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-253">The designer opens.</span></span>

2. <span data-ttu-id="7ef7a-254">Denetime düğme ekleyin.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-254">Add a button to the control.</span></span> <span data-ttu-id="7ef7a-255">Düğmenin özelliklerini aşağıdaki gibi ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-255">Set the properties of the button as follows.</span></span>

    |<span data-ttu-id="7ef7a-256">Özellik</span><span class="sxs-lookup"><span data-stu-id="7ef7a-256">Property</span></span>|<span data-ttu-id="7ef7a-257">Değer</span><span class="sxs-lookup"><span data-stu-id="7ef7a-257">Value</span></span>|
    |--------------|-----------|
    |<span data-ttu-id="7ef7a-258">**Ad**</span><span class="sxs-lookup"><span data-stu-id="7ef7a-258">**Name**</span></span>|`btnAlarmOff`|
    |<span data-ttu-id="7ef7a-259">**Metin**</span><span class="sxs-lookup"><span data-stu-id="7ef7a-259">**Text**</span></span>|<span data-ttu-id="7ef7a-260">**Alarmı devre dışı bırak**</span><span class="sxs-lookup"><span data-stu-id="7ef7a-260">**Disable Alarm**</span></span>|

3. <span data-ttu-id="7ef7a-261">Tasarımcı 'da, **btnAlarmOff**' a çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-261">In the designer, double-click **btnAlarmOff**.</span></span>

     <span data-ttu-id="7ef7a-262">**Kod Düzenleyicisi** `private void btnAlarmOff_Click` satıra açılır.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-262">The **Code Editor** opens to the `private void btnAlarmOff_Click` line.</span></span>

4. <span data-ttu-id="7ef7a-263">Bu yöntemi, aşağıdaki koda benzer olacak şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-263">Modify this method so that it resembles the following code.</span></span>

    ```csharp
    private void btnAlarmOff_Click(object sender, System.EventArgs e)
    {
        // Turns off the alarm.
        AlarmSet = false;
        // Hides the flashing label.
        lblAlarm.Visible = false;
    }
    ```

5. <span data-ttu-id="7ef7a-264">Projeyi kaydetmek için **Dosya** menüsünde **Tümünü Kaydet** ' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-264">On the **File** menu, click **Save All** to save the project.</span></span>

### <a name="using-the-inherited-control-on-a-form"></a><span data-ttu-id="7ef7a-265">Bir form üzerinde devralınmış denetimi kullanma</span><span class="sxs-lookup"><span data-stu-id="7ef7a-265">Using the Inherited Control on a Form</span></span>

<span data-ttu-id="7ef7a-266">Devralınan denetiminizi, temel sınıf denetimini `ctlClock`sınadığınız şekilde test edebilirsiniz: Projeyi derlemek için F5 tuşuna basın ve denetimi **UserControl Test kapsayıcısında**çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-266">You can test your inherited control the same way you tested the base class control, `ctlClock`: Press F5 to build the project and run your control in the **UserControl Test Container**.</span></span> <span data-ttu-id="7ef7a-267">Daha fazla bilgi için [nasıl yapılır: UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md)'un çalışma zamanı davranışını test edin.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-267">For more information, see [How to: Test the Run-Time Behavior of a UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>

<span data-ttu-id="7ef7a-268">Denetiminizi kullanmak üzere yerleştirmek için bir form üzerinde barındırmanıza gerek duyarsınız.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-268">To put your control to use, you will need to host it on a form.</span></span> <span data-ttu-id="7ef7a-269">Standart bir bileşik denetimde olduğu gibi, devralınan bir bileşik denetim tek başına olamaz ve bir formda ya da başka bir kapsayıcıda barındırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-269">As with a standard composite control, an inherited composite control cannot stand alone and must be hosted in a form or other container.</span></span> <span data-ttu-id="7ef7a-270">Daha büyük bir işlevsellik derinliğine sahipolduğundan,testetmekiçinekkodgereklidir.`ctlAlarmClock`</span><span class="sxs-lookup"><span data-stu-id="7ef7a-270">Since `ctlAlarmClock` has a greater depth of functionality, additional code is required to test it.</span></span> <span data-ttu-id="7ef7a-271">Bu yordamda, işlevselliğini `ctlAlarmClock`test etmek için basit bir program yazacaksınız.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-271">In this procedure, you will write a simple program to test the functionality of `ctlAlarmClock`.</span></span> <span data-ttu-id="7ef7a-272">`AlarmTime` Özelliğini ayarlamakvegöstermekiçinkodyazacaksınızveonunkendiişlevlerinitestedecektir.`ctlAlarmClock`</span><span class="sxs-lookup"><span data-stu-id="7ef7a-272">You will write code to set and display the `AlarmTime` property of `ctlAlarmClock`, and will test its inherent functions.</span></span>

#### <a name="to-build-and-add-your-control-to-a-test-form"></a><span data-ttu-id="7ef7a-273">Denetimi derlemek ve test formuna eklemek için</span><span class="sxs-lookup"><span data-stu-id="7ef7a-273">To build and add your control to a test form</span></span>

1. <span data-ttu-id="7ef7a-274">Çözüm Gezgini ' de, **ctlClockLib**' a sağ tıklayın ve ardından **Oluştur**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-274">In Solution Explorer, right-click **ctlClockLib**, and then click **Build**.</span></span>

2. <span data-ttu-id="7ef7a-275">Çözüme yeni bir **Windows uygulaması** projesi ekleyin ve bunu `Test`adlandırın.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-275">Add a new **Windows Application** project to the solution, and name it `Test`.</span></span>

3. <span data-ttu-id="7ef7a-276">Çözüm Gezgini, test projeniz için **Başvurular** düğümüne sağ tıklayın.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-276">In Solution Explorer, right-click the **References** node for your test project.</span></span> <span data-ttu-id="7ef7a-277">Başvuru Ekle iletişim kutusunu göstermek için **Başvuru Ekle** ' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-277">Click **Add Reference** to display the **Add Reference** dialog box.</span></span> <span data-ttu-id="7ef7a-278">Etiketli **Projeler**sekmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-278">Click the tab labeled **Projects**.</span></span> <span data-ttu-id="7ef7a-279">Projeniz proje adı altında listelenir. `ctlClockLib`</span><span class="sxs-lookup"><span data-stu-id="7ef7a-279">Your `ctlClockLib` project will be listed under **Project Name**.</span></span> <span data-ttu-id="7ef7a-280">Başvuruyu test projesine eklemek için projeye çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-280">Double-click the project to add the reference to the test project.</span></span>

4. <span data-ttu-id="7ef7a-281">Çözüm Gezgini ' de **Test**' e sağ tıklayın ve ardından **Oluştur**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-281">In Solution Explorer, right-click **Test**, and then click **Build**.</span></span>

5. <span data-ttu-id="7ef7a-282">**Araç kutusunda** **ctlClockLib Components** düğümünü genişletin.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-282">In the **Toolbox**, expand the **ctlClockLib Components** node.</span></span>

6. <span data-ttu-id="7ef7a-283">Formunuza bir kopyasını `ctlAlarmClock` eklemek için ctlAlarmClock öğesine çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-283">Double-click **ctlAlarmClock** to add a copy of `ctlAlarmClock` to your form.</span></span>

7. <span data-ttu-id="7ef7a-284">**Araç kutusunda**, formunuza bir <xref:System.Windows.Forms.DateTimePicker> denetim eklemek için **DateTimePicker** ' ı bulup çift tıklayın ve ardından **etiket**' e çift tıklayarak bir <xref:System.Windows.Forms.Label> denetim ekleyin.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-284">In the **Toolbox**, locate and double-click **DateTimePicker** to add a <xref:System.Windows.Forms.DateTimePicker> control to your form, and then add a <xref:System.Windows.Forms.Label> control by double-clicking **Label**.</span></span>

8. <span data-ttu-id="7ef7a-285">Denetimleri form üzerinde uygun bir yerde konumlandırmak için fareyi kullanın.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-285">Use the mouse to position the controls in a convenient place on the form.</span></span>

9. <span data-ttu-id="7ef7a-286">Bu denetimlerin özelliklerini aşağıdaki şekilde ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-286">Set the properties of these controls in the following manner.</span></span>

    |<span data-ttu-id="7ef7a-287">Denetim</span><span class="sxs-lookup"><span data-stu-id="7ef7a-287">Control</span></span>|<span data-ttu-id="7ef7a-288">Özellik</span><span class="sxs-lookup"><span data-stu-id="7ef7a-288">Property</span></span>|<span data-ttu-id="7ef7a-289">Değer</span><span class="sxs-lookup"><span data-stu-id="7ef7a-289">Value</span></span>|
    |-------------|--------------|-----------|
    |`label1`|<span data-ttu-id="7ef7a-290">**Metin**</span><span class="sxs-lookup"><span data-stu-id="7ef7a-290">**Text**</span></span>|`(blank space)`|
    ||<span data-ttu-id="7ef7a-291">**Ad**</span><span class="sxs-lookup"><span data-stu-id="7ef7a-291">**Name**</span></span>|`lblTest`|
    |`dateTimePicker1`|<span data-ttu-id="7ef7a-292">**Ad**</span><span class="sxs-lookup"><span data-stu-id="7ef7a-292">**Name**</span></span>|`dtpTest`|
    ||<span data-ttu-id="7ef7a-293">**Formatını**</span><span class="sxs-lookup"><span data-stu-id="7ef7a-293">**Format**</span></span>|<xref:System.Windows.Forms.DateTimePickerFormat.Time>|

10. <span data-ttu-id="7ef7a-294">Tasarımcıda **dtpTest**öğesine çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-294">In the designer, double-click **dtpTest**.</span></span>

     <span data-ttu-id="7ef7a-295">**Kod Düzenleyicisi** olarak `private void dtpTest_ValueChanged`açılır.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-295">The **Code Editor** opens to `private void dtpTest_ValueChanged`.</span></span>

11. <span data-ttu-id="7ef7a-296">Kodu aşağıdakine benzer olacak şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-296">Modify the code so that it resembles the following.</span></span>

    ```csharp
    private void dtpTest_ValueChanged(object sender, System.EventArgs e)
    {
        ctlAlarmClock1.AlarmTime = dtpTest.Value;
        ctlAlarmClock1.AlarmSet = true;
        lblTest.Text = "Alarm Time is " +
            ctlAlarmClock1.AlarmTime.ToShortTimeString();
    }
    ```

12. <span data-ttu-id="7ef7a-297">Çözüm Gezgini ' de **Test**' e sağ tıklayın ve ardından **Başlangıç projesi olarak ayarla**' ya tıklayın.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-297">In Solution Explorer, right-click **Test**, and then click **Set as StartUp Project**.</span></span>

13. <span data-ttu-id="7ef7a-298">Üzerinde **hata ayıklama** menüsünü tıklatın **hata ayıklamayı Başlat**.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-298">On the **Debug** menu, click **Start Debugging**.</span></span>

     <span data-ttu-id="7ef7a-299">Test programı başlar.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-299">The test program starts.</span></span> <span data-ttu-id="7ef7a-300">`ctlAlarmClock` Denetimde geçerli saatin güncelleştirildiğini ve başlangıç saatinin <xref:System.Windows.Forms.DateTimePicker> denetimde gösterildiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-300">Note that the current time is updated in the `ctlAlarmClock` control, and that the starting time is shown in the <xref:System.Windows.Forms.DateTimePicker> control.</span></span>

14. <span data-ttu-id="7ef7a-301">Saatin dakikalarının görüntülendiği yere tıklayın. <xref:System.Windows.Forms.DateTimePicker></span><span class="sxs-lookup"><span data-stu-id="7ef7a-301">Click the <xref:System.Windows.Forms.DateTimePicker> where the minutes of the hour are displayed.</span></span>

15. <span data-ttu-id="7ef7a-302">Klavyeyi kullanarak, tarafından `ctlAlarmClock`gösterilen geçerli saatten bir dakika daha büyük bir değer ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-302">Using the keyboard, set a value for minutes that is one minute greater than the current time shown by `ctlAlarmClock`.</span></span>

     <span data-ttu-id="7ef7a-303">Uyarı ayarının zamanı içinde `lblTest`gösterilir.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-303">The time for the alarm setting is shown in `lblTest`.</span></span> <span data-ttu-id="7ef7a-304">Uyarı ayarı zamanına ulaşmak için, görüntülenecek sürenin bekleyin.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-304">Wait for the displayed time to reach the alarm setting time.</span></span> <span data-ttu-id="7ef7a-305">Görünen süre, alarmın ayarlandığı zamana ulaştığında, `lblAlarm` Flash olur.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-305">When the displayed time reaches the time to which the alarm is set, the `lblAlarm` will flash.</span></span>

16. <span data-ttu-id="7ef7a-306">Tıklayarak `btnAlarmOff`uyarıyı kapatın.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-306">Turn off the alarm by clicking `btnAlarmOff`.</span></span> <span data-ttu-id="7ef7a-307">Şimdi uyarıyı sıfırlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-307">You may now reset the alarm.</span></span>

     <span data-ttu-id="7ef7a-308">Bu izlenecek yol, bir dizi temel kavramı kapsamıştır.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-308">This walkthrough has covered a number of key concepts.</span></span> <span data-ttu-id="7ef7a-309">Bir bileşik denetim kapsayıcısına denetimleri ve bileşenleri birleştirerek bileşik bir denetim oluşturmayı öğrendiniz.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-309">You have learned to create a composite control by combining controls and components into a composite control container.</span></span> <span data-ttu-id="7ef7a-310">Denetime Özellik eklemeyi ve özel işlevsellik uygulamak için kod yazmayı öğrendiniz.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-310">You have learned to add properties to your control, and to write code to implement custom functionality.</span></span> <span data-ttu-id="7ef7a-311">Son bölümde, belirli bir bileşik denetimin işlevselliğini devralma yoluyla genişletmeyi ve bu yöntemleri geçersiz kılarak ana bilgisayar yöntemlerinin işlevselliğini değiştirmeyi öğrendiniz.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-311">In the last section, you learned to extend the functionality of a given composite control through inheritance, and to alter the functionality of host methods by overriding those methods.</span></span>

## <a name="see-also"></a><span data-ttu-id="7ef7a-312">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7ef7a-312">See also</span></span>

- [<span data-ttu-id="7ef7a-313">Özel Denetim Çeşitleri</span><span class="sxs-lookup"><span data-stu-id="7ef7a-313">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
- [<span data-ttu-id="7ef7a-314">Nasıl yapılır: Araç kutusu öğelerini Seç Iletişim kutusunda bir denetim görüntüle</span><span class="sxs-lookup"><span data-stu-id="7ef7a-314">How to: Display a Control in the Choose Toolbox Items Dialog Box</span></span>](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)
- [<span data-ttu-id="7ef7a-315">İzlenecek yol: Görsel ile Windows Forms denetiminden devralmaC#</span><span class="sxs-lookup"><span data-stu-id="7ef7a-315">Walkthrough: Inheriting from a Windows Forms Control with Visual C#</span></span>](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)
