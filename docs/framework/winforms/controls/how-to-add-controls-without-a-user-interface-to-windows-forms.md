---
title: 'Nasıl yapılır: Windows Formlarına Kullanıcı Arabirimi Olmadan Denetimler Ekleme'
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
ms.openlocfilehash: 9458fc7f3344a5692581485a0e5bd462e45551d9
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43881833"
---
# <a name="how-to-add-controls-without-a-user-interface-to-windows-forms"></a><span data-ttu-id="78fc0-102">Nasıl yapılır: Windows Formlarına Kullanıcı Arabirimi Olmadan Denetimler Ekleme</span><span class="sxs-lookup"><span data-stu-id="78fc0-102">How to: Add Controls Without a User Interface to Windows Forms</span></span>
<span data-ttu-id="78fc0-103">Görsel olmayan denetim (veya bileşen) uygulamanıza işlevsellik sağlar.</span><span class="sxs-lookup"><span data-stu-id="78fc0-103">A nonvisual control (or component) provides functionality to your application.</span></span> <span data-ttu-id="78fc0-104">Diğer denetimleri farklı bileşenleri bir kullanıcı arabirimi kullanıcıya sağlamaz ve bu nedenle Windows Form Tasarımcısı yüzeyine görüntülenmesi gerekmez.</span><span class="sxs-lookup"><span data-stu-id="78fc0-104">Unlike other controls, components do not provide a user interface to the user and thus do not need to be displayed on the Windows Forms Designer surface.</span></span> <span data-ttu-id="78fc0-105">Bir forma bir bileşen eklendiğinde Windows Form Tasarımcısı yeniden boyutlandırılabilir Tepsisi tüm bileşenleri görüntülendiği formun alt kısmındaki görüntüler.</span><span class="sxs-lookup"><span data-stu-id="78fc0-105">When a component is added to a form, the Windows Forms Designer displays a resizable tray at the bottom of the form where all components are displayed.</span></span> <span data-ttu-id="78fc0-106">Bir denetim, bileşen tepsisine eklendikten sonra bileşeni seçebilir ve herhangi bir form denetiminde olduğu gibi özelliklerini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="78fc0-106">Once a control has been added to the component tray, you can select the component and set its properties as you would any other control on the form.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="78fc0-107">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="78fc0-107">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="78fc0-108">Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="78fc0-108">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="78fc0-109">Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="78fc0-109">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-add-a-component-to-a-windows-form"></a><span data-ttu-id="78fc0-110">Bir Windows forma bir bileşen eklemek için</span><span class="sxs-lookup"><span data-stu-id="78fc0-110">To add a component to a Windows Form</span></span>  
  
1.  <span data-ttu-id="78fc0-111">Formu açın.</span><span class="sxs-lookup"><span data-stu-id="78fc0-111">Open the form.</span></span> <span data-ttu-id="78fc0-112">Ayrıntılar için bkz [nasıl yapılır: görüntü Windows Forms Tasarımcısı'nda](https://msdn.microsoft.com/library/bf3f1e5b-ea07-4529-85c6-6af3ded0cec5).</span><span class="sxs-lookup"><span data-stu-id="78fc0-112">For details, see [How to: Display Windows Forms in the Designer](https://msdn.microsoft.com/library/bf3f1e5b-ea07-4529-85c6-6af3ded0cec5).</span></span>  
  
2.  <span data-ttu-id="78fc0-113">İçinde **araç kutusu**bir bileşene tıklayın ve formunuza sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="78fc0-113">In the **Toolbox**, click a component and drag it to your form.</span></span>  
  
     <span data-ttu-id="78fc0-114">Bileşen, bileşen tepsisinde görünür.</span><span class="sxs-lookup"><span data-stu-id="78fc0-114">Your component appears in the component tray.</span></span>  
  
 <span data-ttu-id="78fc0-115">Ayrıca, bileşenler çalışma zamanında bir forma eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="78fc0-115">Furthermore, components can be added to a form at run time.</span></span> <span data-ttu-id="78fc0-116">Özellikle bileşenleri farklı bir kullanıcı arabirimi denetimleri bir görsel ifade olmadığı için yaygın bir senaryo budur.</span><span class="sxs-lookup"><span data-stu-id="78fc0-116">This is a common scenario, especially because components do not have a visual expression, unlike controls that have a user interface.</span></span> <span data-ttu-id="78fc0-117">Aşağıdaki örnekte bir <xref:System.Windows.Forms.Timer> bileşen çalışma zamanında eklenir.</span><span class="sxs-lookup"><span data-stu-id="78fc0-117">In the example below, a <xref:System.Windows.Forms.Timer> component is added at run time.</span></span> <span data-ttu-id="78fc0-118">(Visual Studio birkaç farklı zamanlayıcılar içerdiğine dikkat edin; bu durumda, bir Windows Forms kullanın <xref:System.Windows.Forms.Timer> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="78fc0-118">(Note that Visual Studio contains a number of different timers; in this case, use a Windows Forms <xref:System.Windows.Forms.Timer> component.</span></span> <span data-ttu-id="78fc0-119">Visual Studio'da farklı zamanlayıcılar hakkında daha fazla bilgi için bkz. [sunucu tabanlı zamanlayıcılar giriş](https://msdn.microsoft.com/library/adc0bc0a-a519-4812-bafc-fb9d1a5801fc).)</span><span class="sxs-lookup"><span data-stu-id="78fc0-119">For more information about the different timers in Visual Studio, see [Introduction to Server-Based Timers](https://msdn.microsoft.com/library/adc0bc0a-a519-4812-bafc-fb9d1a5801fc).)</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="78fc0-120">Bileşenler genellikle etkili bir şekilde çalışması bileşeni için ayarlanmalıdır denetime özgü özelikleri sahiptir.</span><span class="sxs-lookup"><span data-stu-id="78fc0-120">Components often have control-specific properties that must be set for the component to function effectively.</span></span> <span data-ttu-id="78fc0-121">Durumunda, <xref:System.Windows.Forms.Timer> aşağıdaki bileşen, ayarladığınız `Interval` özelliği.</span><span class="sxs-lookup"><span data-stu-id="78fc0-121">In the case of the <xref:System.Windows.Forms.Timer> component below, you set the `Interval` property.</span></span> <span data-ttu-id="78fc0-122">Bileşenlerin özellikleri söz konusu bileşen için gerekli olarak ayarlayın, projenize eklerken emin olun.</span><span class="sxs-lookup"><span data-stu-id="78fc0-122">Be sure, when adding components to your project, that you set the properties necessary for that component.</span></span>  
  
#### <a name="to-add-a-component-to-a-windows-form-programmatically"></a><span data-ttu-id="78fc0-123">Bir Windows forma programsal olarak bir bileşen eklemek için</span><span class="sxs-lookup"><span data-stu-id="78fc0-123">To add a component to a Windows Form programmatically</span></span>  
  
1.  <span data-ttu-id="78fc0-124">Bir örneğini oluşturmak <xref:System.Windows.Forms.Timer> kod sınıfı.</span><span class="sxs-lookup"><span data-stu-id="78fc0-124">Create an instance of the <xref:System.Windows.Forms.Timer> class in code.</span></span>  
  
2.  <span data-ttu-id="78fc0-125">Ayarlama `Interval` Zamanlayıcının işaretleri arasındaki süreyi belirlemek için özellik.</span><span class="sxs-lookup"><span data-stu-id="78fc0-125">Set the `Interval` property to determine the time between ticks of the timer.</span></span>  
  
3.  <span data-ttu-id="78fc0-126">Bileşeniniz için gerekli diğer özellikleri yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="78fc0-126">Configure any other necessary properties for your component.</span></span>  
  
     <span data-ttu-id="78fc0-127">Aşağıdaki kod oluşturma işlemini gösterir. bir <xref:System.Windows.Forms.Timer> ile kendi `Interval` özellik kümesi.</span><span class="sxs-lookup"><span data-stu-id="78fc0-127">The following code shows the creation of a <xref:System.Windows.Forms.Timer> with its `Interval` property set.</span></span>  
  
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
    >  <span data-ttu-id="78fc0-128">Yerel bir güvenlik riski ağ üzerinden bilgisayarınıza kötü amaçlı bir UserControl başvurarak doğurabilir.</span><span class="sxs-lookup"><span data-stu-id="78fc0-128">You might expose your local computer to a security risk through the network by referencing a malicious UserControl.</span></span> <span data-ttu-id="78fc0-129">Bu, yalnızca, yanlışlıkla bunu projenize ekleyerek ardından zararlı olabilecek özel bir denetim oluşturulamaz kötü amaçlı bir kişinin söz konusu olduğunda önemli hale gelir.</span><span class="sxs-lookup"><span data-stu-id="78fc0-129">This would only be a concern in the case of a malicious person creating a damaging custom control, followed by you mistakenly adding it to your project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78fc0-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="78fc0-130">See Also</span></span>  
 [<span data-ttu-id="78fc0-131">Windows Forms Denetimleri</span><span class="sxs-lookup"><span data-stu-id="78fc0-131">Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/index.md)  
 [<span data-ttu-id="78fc0-132">Nasıl yapılır: Windows Forms’a Denetimler Ekleme</span><span class="sxs-lookup"><span data-stu-id="78fc0-132">How to: Add Controls to Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)  
 [<span data-ttu-id="78fc0-133">Nasıl yapılır: Windows Forms’a ActiveX Denetimleri Ekleme</span><span class="sxs-lookup"><span data-stu-id="78fc0-133">How to: Add ActiveX Controls to Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-add-activex-controls-to-windows-forms.md)  
 [<span data-ttu-id="78fc0-134">Nasıl yapılır: Windows Forms Arasında Denetimleri Kopyalama</span><span class="sxs-lookup"><span data-stu-id="78fc0-134">How to: Copy Controls Between Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-copy-controls-between-windows-forms.md)  
 [<span data-ttu-id="78fc0-135">Windows Forms’a Denetimler Yerleştirme</span><span class="sxs-lookup"><span data-stu-id="78fc0-135">Putting Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/putting-controls-on-windows-forms.md)  
 [<span data-ttu-id="78fc0-136">Ayrı Windows Forms Denetimlerini Etiketleme ve Kısayollarını Sunma</span><span class="sxs-lookup"><span data-stu-id="78fc0-136">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)  
 [<span data-ttu-id="78fc0-137">Windows Forms'da Kullanılacak Denetimler</span><span class="sxs-lookup"><span data-stu-id="78fc0-137">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 [<span data-ttu-id="78fc0-138">İşleve Göre Windows Forms Denetimleri</span><span class="sxs-lookup"><span data-stu-id="78fc0-138">Windows Forms Controls by Function</span></span>](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)
