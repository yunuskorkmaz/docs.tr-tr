---
title: Kullanıcı Arabirimi Olmadan Denetim Ekleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- NonVisualSelection
helpviewer_keywords:
- invisible controls [Windows Forms]
- Windows Forms controls, adding to form
- controls [Windows Forms], nonvisual
- Windows Forms controls, nonvisual
- nonvisual controls [Windows Forms]
ms.assetid: 52134d9c-cff6-4eed-8e2b-3d5eb3bd494e
ms.openlocfilehash: 43f13b4f009fcd6e5d82fa2c00113a77d48877b6
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744747"
---
# <a name="how-to-add-controls-without-a-user-interface-to-windows-forms"></a><span data-ttu-id="96226-102">Nasıl yapılır: Windows Formlarına Kullanıcı Arabirimi Olmadan Denetimler Ekleme</span><span class="sxs-lookup"><span data-stu-id="96226-102">How to: Add Controls Without a User Interface to Windows Forms</span></span>

<span data-ttu-id="96226-103">Görsel olmayan bir denetim (veya bileşen) uygulamanıza işlevsellik sağlar.</span><span class="sxs-lookup"><span data-stu-id="96226-103">A nonvisual control (or component) provides functionality to your application.</span></span> <span data-ttu-id="96226-104">Diğer denetimlerin aksine, bileşenler kullanıcıya Kullanıcı arabirimi sağlamamalıdır ve bu nedenle Windows Form Tasarımcısı yüzeyinde gösterilmemelidir.</span><span class="sxs-lookup"><span data-stu-id="96226-104">Unlike other controls, components do not provide a user interface to the user and thus do not need to be displayed on the Windows Forms Designer surface.</span></span> <span data-ttu-id="96226-105">Forma bir bileşen eklendiğinde Windows Form Tasarımcısı, tüm bileşenlerin görüntülendiği formun alt kısmına yeniden boyutlandırılabilir bir tepsi görüntüler.</span><span class="sxs-lookup"><span data-stu-id="96226-105">When a component is added to a form, the Windows Forms Designer displays a resizable tray at the bottom of the form where all components are displayed.</span></span> <span data-ttu-id="96226-106">Bileşen tepsisine bir denetim eklendikten sonra, bileşeni seçebilir ve form üzerindeki diğer denetimleri yaptığınız gibi özelliklerini ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="96226-106">Once a control has been added to the component tray, you can select the component and set its properties as you would any other control on the form.</span></span>

## <a name="add-a-component-to-a-windows-form"></a><span data-ttu-id="96226-107">Windows formuna bir bileşen ekleme</span><span class="sxs-lookup"><span data-stu-id="96226-107">Add a component to a Windows Form</span></span>

1. <span data-ttu-id="96226-108">Formu Visual Studio 'da açın.</span><span class="sxs-lookup"><span data-stu-id="96226-108">Open the form in Visual Studio.</span></span> <span data-ttu-id="96226-109">Ayrıntılar için bkz. [nasıl yapılır: tasarımcıda Windows Forms görüntüleme](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w5yd62ts(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="96226-109">For details, see [How to: Display Windows Forms in the Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w5yd62ts(v=vs.100)).</span></span>

2. <span data-ttu-id="96226-110">**Araç kutusunda**bir bileşene tıklayın ve onu formunuza sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="96226-110">In the **Toolbox**, click a component and drag it to your form.</span></span>

     <span data-ttu-id="96226-111">Bileşeniniz bileşen tepsisinde görünür.</span><span class="sxs-lookup"><span data-stu-id="96226-111">Your component appears in the component tray.</span></span>

<span data-ttu-id="96226-112">Ayrıca, bileşenler çalışma zamanında bir forma eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="96226-112">Furthermore, components can be added to a form at run time.</span></span> <span data-ttu-id="96226-113">Bu yaygın bir senaryodur, özellikle de bileşenler görsel bir ifade olmadığından, Kullanıcı arabirimine sahip denetimlerin aksine.</span><span class="sxs-lookup"><span data-stu-id="96226-113">This is a common scenario, especially because components do not have a visual expression, unlike controls that have a user interface.</span></span> <span data-ttu-id="96226-114">Aşağıdaki örnekte, çalışma zamanında bir <xref:System.Windows.Forms.Timer> bileşeni eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="96226-114">In the example below, a <xref:System.Windows.Forms.Timer> component is added at run time.</span></span> <span data-ttu-id="96226-115">(Visual Studio 'nun bir dizi farklı Zamanlayıcı içerdiğini unutmayın; bu durumda, bir Windows Forms <xref:System.Windows.Forms.Timer> bileşeni kullanın.</span><span class="sxs-lookup"><span data-stu-id="96226-115">(Note that Visual Studio contains a number of different timers; in this case, use a Windows Forms <xref:System.Windows.Forms.Timer> component.</span></span> <span data-ttu-id="96226-116">Visual Studio 'daki farklı zamanlayıcılar hakkında daha fazla bilgi için bkz. [sunucu tabanlı zamanlayıcılara giriş](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).)</span><span class="sxs-lookup"><span data-stu-id="96226-116">For more information about the different timers in Visual Studio, see [Introduction to Server-Based Timers](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).)</span></span>

> [!CAUTION]
> <span data-ttu-id="96226-117">Bileşenlere genellikle bileşenin etkin bir şekilde çalışması için ayarlanması gereken denetimine özgü özellikler vardır.</span><span class="sxs-lookup"><span data-stu-id="96226-117">Components often have control-specific properties that must be set for the component to function effectively.</span></span> <span data-ttu-id="96226-118">Aşağıdaki <xref:System.Windows.Forms.Timer> bileşeni söz konusu olduğunda, `Interval` özelliğini ayarlarsınız.</span><span class="sxs-lookup"><span data-stu-id="96226-118">In the case of the <xref:System.Windows.Forms.Timer> component below, you set the `Interval` property.</span></span> <span data-ttu-id="96226-119">Projenize bileşen eklerken, bu bileşen için gerekli özellikleri ayarlamış olduğunuzdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="96226-119">Be sure, when adding components to your project, that you set the properties necessary for that component.</span></span>

## <a name="add-a-component-to-a-windows-form-programmatically"></a><span data-ttu-id="96226-120">Windows formuna programlı bir bileşen ekleme</span><span class="sxs-lookup"><span data-stu-id="96226-120">Add a component to a Windows Form programmatically</span></span>

1. <span data-ttu-id="96226-121">Kodda <xref:System.Windows.Forms.Timer> sınıfının bir örneğini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="96226-121">Create an instance of the <xref:System.Windows.Forms.Timer> class in code.</span></span>

2. <span data-ttu-id="96226-122">Zamanlayıcının zaman işaretleri arasındaki süreyi öğrenmek için `Interval` özelliğini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="96226-122">Set the `Interval` property to determine the time between ticks of the timer.</span></span>

3. <span data-ttu-id="96226-123">Bileşeniniz için diğer tüm gerekli özellikleri yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="96226-123">Configure any other necessary properties for your component.</span></span>

     <span data-ttu-id="96226-124">Aşağıdaki kod, `Interval` özelliği ayarlanmış bir <xref:System.Windows.Forms.Timer> oluşturulmasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="96226-124">The following code shows the creation of a <xref:System.Windows.Forms.Timer> with its `Interval` property set.</span></span>

    ```vb
    Public Sub CreateTimer()
       Dim timerKeepTrack As New System.Windows.Forms.Timer
       timerKeepTrack.Interval = 1000
    End Sub
    ```

    ```csharp
    public void createTimer()
    {
       System.Windows.Forms.Timer timerKeepTrack = new
           System.Windows.Forms.Timer();
       timerKeepTrack.Interval = 1000;
    }
    ```

    ```cpp
    public:
       void createTimer()
       {
          System::Windows::Forms::Timer^ timerKeepTrack = gcnew
             System::Windows::Forms::Timer();
          timerKeepTrack->Interval = 1000;
       }
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="96226-125">Kötü amaçlı bir UserControl 'e başvurarak yerel bilgisayarınızı ağ üzerinden bir güvenlik riskine maruz kalabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="96226-125">You might expose your local computer to a security risk through the network by referencing a malicious UserControl.</span></span> <span data-ttu-id="96226-126">Bu durum yalnızca zararlı bir kişinin zararlı bir denetim oluşturan bir sorun olduğu ve bunu projenize yanlışlıkla ekleyerek bir sorun olacaktır.</span><span class="sxs-lookup"><span data-stu-id="96226-126">This would only be a concern in the case of a malicious person creating a damaging custom control, followed by you mistakenly adding it to your project.</span></span>

## <a name="see-also"></a><span data-ttu-id="96226-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="96226-127">See also</span></span>

- [<span data-ttu-id="96226-128">Windows Forms Denetimleri</span><span class="sxs-lookup"><span data-stu-id="96226-128">Windows Forms Controls</span></span>](index.md)
- [<span data-ttu-id="96226-129">Nasıl yapılır: Windows Forms’a Denetimler Ekleme</span><span class="sxs-lookup"><span data-stu-id="96226-129">How to: Add Controls to Windows Forms</span></span>](how-to-add-controls-to-windows-forms.md)
- [<span data-ttu-id="96226-130">Nasıl yapılır: Windows Forms’a ActiveX Denetimleri Ekleme</span><span class="sxs-lookup"><span data-stu-id="96226-130">How to: Add ActiveX Controls to Windows Forms</span></span>](how-to-add-activex-controls-to-windows-forms.md)
- [<span data-ttu-id="96226-131">Windows Forms’a Denetimler Yerleştirme</span><span class="sxs-lookup"><span data-stu-id="96226-131">Putting Controls on Windows Forms</span></span>](putting-controls-on-windows-forms.md)
- [<span data-ttu-id="96226-132">Ayrı Windows Forms Denetimlerini Etiketleme ve Kısayollarını Sunma</span><span class="sxs-lookup"><span data-stu-id="96226-132">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [<span data-ttu-id="96226-133">Windows Forms'da Kullanılacak Denetimler</span><span class="sxs-lookup"><span data-stu-id="96226-133">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
- [<span data-ttu-id="96226-134">İşleve Göre Windows Forms Denetimleri</span><span class="sxs-lookup"><span data-stu-id="96226-134">Windows Forms Controls by Function</span></span>](windows-forms-controls-by-function.md)
