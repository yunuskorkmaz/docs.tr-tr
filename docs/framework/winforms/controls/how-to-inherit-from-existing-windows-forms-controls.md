---
title: Mevcut Denetimlerden Devralma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- custom controls [Windows Forms], inheritance
ms.assetid: 1e1fc8ea-c615-4cf0-a356-16d6df7444ab
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b0e0053816efde349c7e4d13d03bef5f8801c667
ms.sourcegitcommit: 515469828d0f040e01bde01df6b8e4eb43630b06
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78849386"
---
# <a name="how-to-inherit-from-existing-windows-forms-controls"></a><span data-ttu-id="b1ed9-102">Nasıl yapılır: Mevcut Windows Formları Denetimlerinden Devralma</span><span class="sxs-lookup"><span data-stu-id="b1ed9-102">How to: Inherit from Existing Windows Forms Controls</span></span>

<span data-ttu-id="b1ed9-103">Varolan bir denetimin işlevselliğini genişletmek istiyorsanız, devralma yoluyla varolan denetimden türetilen bir denetim oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b1ed9-103">If you want to extend the functionality of an existing control, you can create a control derived from an existing control through inheritance.</span></span> <span data-ttu-id="b1ed9-104">Varolan bir denetimden devralırken, bu denetimin tüm işlevselliğini ve görsel özelliklerini devralırsınız.</span><span class="sxs-lookup"><span data-stu-id="b1ed9-104">When inheriting from an existing control, you inherit all of the functionality and visual properties of that control.</span></span> <span data-ttu-id="b1ed9-105">Örneğin, devralınan bir denetim <xref:System.Windows.Forms.Button>oluşturuyorsanız, yeni denetiminiz tam olarak standart <xref:System.Windows.Forms.Button> bir denetim gibi görünür ve hareket eder.</span><span class="sxs-lookup"><span data-stu-id="b1ed9-105">For example, if you were creating a control that inherited from <xref:System.Windows.Forms.Button>, your new control would look and act exactly like a standard <xref:System.Windows.Forms.Button> control.</span></span> <span data-ttu-id="b1ed9-106">Daha sonra özel yöntemler ve özellikler uygulanması yoluyla yeni denetimişlevselliğini genişletmek veya değiştirmek olabilir.</span><span class="sxs-lookup"><span data-stu-id="b1ed9-106">You could then extend or modify the functionality of your new control through the implementation of custom methods and properties.</span></span> <span data-ttu-id="b1ed9-107">Bazı denetimlerde, <xref:System.Windows.Forms.Control.OnPaint%2A> metodunu geçersiz kılarak devralınan denetiminizin görsel görünümünü de değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b1ed9-107">In some controls, you can also change the visual appearance of your inherited control by overriding its <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span>

## <a name="to-create-an-inherited-control"></a><span data-ttu-id="b1ed9-108">Devralınan bir denetim oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="b1ed9-108">To create an inherited control</span></span>

1. <span data-ttu-id="b1ed9-109">Visual Studio'da yeni bir **Windows Forms Application** projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b1ed9-109">In Visual Studio, create a new **Windows Forms Application** project.</span></span>

1. <span data-ttu-id="b1ed9-110">**Proje** menüsünden **Yeni Öğe Ekle'yi**seçin.</span><span class="sxs-lookup"><span data-stu-id="b1ed9-110">From the **Project** menu, choose **Add New Item**.</span></span>

    <span data-ttu-id="b1ed9-111">**Yeni Öğe Ekle** iletişim kutusu görünür.</span><span class="sxs-lookup"><span data-stu-id="b1ed9-111">The **Add New Item** dialog box appears.</span></span>

1. <span data-ttu-id="b1ed9-112">Yeni **Öğe Ekle** iletişim kutusunda, **Özel Denetim'i**çift tıklatın.</span><span class="sxs-lookup"><span data-stu-id="b1ed9-112">In the **Add New Item** dialog box, double-click **Custom Control**.</span></span>

    <span data-ttu-id="b1ed9-113">Projenize yeni bir özel denetim eklenir.</span><span class="sxs-lookup"><span data-stu-id="b1ed9-113">A new custom control is added to your project.</span></span>

1. <span data-ttu-id="b1ed9-114">Kullanıyorsanız:</span><span class="sxs-lookup"><span data-stu-id="b1ed9-114">If you're using:</span></span>

    - <span data-ttu-id="b1ed9-115">Visual Basic, Çözüm **Gezgini'nin**en üstünde, **Tüm Dosyaları Göster'i**tıklatın.</span><span class="sxs-lookup"><span data-stu-id="b1ed9-115">Visual Basic, at the top of **Solution Explorer**, click **Show All Files**.</span></span> <span data-ttu-id="b1ed9-116">CustomControl1.vb'i genişletin ve ardından Code Editor'da CustomControl1.Designer.vb'yi açın.</span><span class="sxs-lookup"><span data-stu-id="b1ed9-116">Expand CustomControl1.vb and then open CustomControl1.Designer.vb in the Code Editor.</span></span>
    - <span data-ttu-id="b1ed9-117">C#, Kod Düzenleyicisi'nde CustomControl1.cs açın.</span><span class="sxs-lookup"><span data-stu-id="b1ed9-117">C#, open CustomControl1.cs in the Code Editor.</span></span>

1. <span data-ttu-id="b1ed9-118">'den <xref:System.Windows.Forms.Control>devralınan sınıf bildirimini bulun</span><span class="sxs-lookup"><span data-stu-id="b1ed9-118">Locate the class declaration, which inherits from <xref:System.Windows.Forms.Control>.</span></span>

1. <span data-ttu-id="b1ed9-119">Taban sınıfı devralmak istediğiniz denetimle değiştirin.</span><span class="sxs-lookup"><span data-stu-id="b1ed9-119">Change the base class to the control that you want to inherit from.</span></span>

     <span data-ttu-id="b1ed9-120">Örneğin, devralmak <xref:System.Windows.Forms.Button>istiyorsanız, sınıf bildirimini aşağıdakiyle değiştirin:</span><span class="sxs-lookup"><span data-stu-id="b1ed9-120">For example, if you want to inherit from <xref:System.Windows.Forms.Button>, change the class declaration to the following:</span></span>

    ```vb
    Partial Class CustomControl1
        Inherits System.Windows.Forms.Button
    ```

    ```csharp
    public partial class CustomControl1 : System.Windows.Forms.Button
    ```

1. <span data-ttu-id="b1ed9-121">Visual Basic kullanıyorsanız, CustomControl1.Designer.vb kaydedin ve kapatın.</span><span class="sxs-lookup"><span data-stu-id="b1ed9-121">If you are using Visual Basic, save and close CustomControl1.Designer.vb.</span></span> <span data-ttu-id="b1ed9-122">Code Editor'da CustomControl1.vb'i açın.</span><span class="sxs-lookup"><span data-stu-id="b1ed9-122">Open CustomControl1.vb in the Code Editor.</span></span>

1. <span data-ttu-id="b1ed9-123">Denetiminizin dahil edeceği özel yöntemler veya özellikler uygulayın.</span><span class="sxs-lookup"><span data-stu-id="b1ed9-123">Implement any custom methods or properties that your control will incorporate.</span></span>

1. <span data-ttu-id="b1ed9-124">Denetiminizin grafik görünümünü değiştirmek istiyorsanız, <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemi geçersiz kılın.</span><span class="sxs-lookup"><span data-stu-id="b1ed9-124">If you want to modify the graphical appearance of your control, override the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span>

    > [!NOTE]
    > <span data-ttu-id="b1ed9-125">Geçersiz <xref:System.Windows.Forms.Control.OnPaint%2A> kılma, tüm denetimlerin görünümünü değiştirmenize izin vermez.</span><span class="sxs-lookup"><span data-stu-id="b1ed9-125">Overriding <xref:System.Windows.Forms.Control.OnPaint%2A> will not allow you to modify the appearance of all controls.</span></span> <span data-ttu-id="b1ed9-126">Tüm resimlerini Windows tarafından yapılan bu denetimler <xref:System.Windows.Forms.TextBox>(örneğin,) asla kendi yöntemlerini <xref:System.Windows.Forms.Control.OnPaint%2A> aramaz ve bu nedenle özel kodu asla kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="b1ed9-126">Those controls that have all of their painting done by Windows (for example, <xref:System.Windows.Forms.TextBox>) never call their <xref:System.Windows.Forms.Control.OnPaint%2A> method, and thus will never use the custom code.</span></span> <span data-ttu-id="b1ed9-127"><xref:System.Windows.Forms.Control.OnPaint%2A> Yöntemin kullanılabilir olup olmadığını görmek için değiştirmek istediğiniz özel denetim için Yardım belgelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="b1ed9-127">Refer to the Help documentation for the particular control you want to modify to see if the <xref:System.Windows.Forms.Control.OnPaint%2A> method is available.</span></span> <span data-ttu-id="b1ed9-128">Tüm Windows Form Denetimlerinin listesi için [Windows Formlarında Kullanılacak Denetimler](controls-to-use-on-windows-forms.md)bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="b1ed9-128">For a list of all the Windows Form Controls, see [Controls to Use on Windows Forms](controls-to-use-on-windows-forms.md).</span></span> <span data-ttu-id="b1ed9-129">Denetim üye yöntemi <xref:System.Windows.Forms.Control.OnPaint%2A> olarak listelenmemişse, bu yöntemi geçersiz kılarak görünümünü değiştiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="b1ed9-129">If a control does not have <xref:System.Windows.Forms.Control.OnPaint%2A> listed as a member method, you cannot alter its appearance by overriding this method.</span></span> <span data-ttu-id="b1ed9-130">Özel boyama hakkında daha fazla bilgi için [Bkz. Özel Denetim Boyama ve Oluşturma.](custom-control-painting-and-rendering.md)</span><span class="sxs-lookup"><span data-stu-id="b1ed9-130">For more information about custom painting, see [Custom Control Painting and Rendering](custom-control-painting-and-rendering.md).</span></span>

    ```vb
    Protected Overrides Sub OnPaint(ByVal e As _
       System.Windows.Forms.PaintEventArgs)
       MyBase.OnPaint(e)
       ' Insert code to do custom painting.
       ' If you want to completely change the appearance of your control,
       ' do not call MyBase.OnPaint(e).
    End Sub
    ```

    ```csharp
    protected override void OnPaint(PaintEventArgs pe)
    {
       base.OnPaint(pe);
       // Insert code to do custom painting.
       // If you want to completely change the appearance of your control,
       // do not call base.OnPaint(pe).
    }
    ```

1. <span data-ttu-id="b1ed9-131">Kaydedin ve kontrol test edin.</span><span class="sxs-lookup"><span data-stu-id="b1ed9-131">Save and test your control.</span></span>

## <a name="see-also"></a><span data-ttu-id="b1ed9-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b1ed9-132">See also</span></span>

- [<span data-ttu-id="b1ed9-133">Özel Denetim Çeşitleri</span><span class="sxs-lookup"><span data-stu-id="b1ed9-133">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
- [<span data-ttu-id="b1ed9-134">Nasıl yapılır: Denetim Sınıfından Devralma</span><span class="sxs-lookup"><span data-stu-id="b1ed9-134">How to: Inherit from the Control Class</span></span>](how-to-inherit-from-the-control-class.md)
- [<span data-ttu-id="b1ed9-135">Nasıl yapılır: UserControl Sınıfından Devralma</span><span class="sxs-lookup"><span data-stu-id="b1ed9-135">How to: Inherit from the UserControl Class</span></span>](how-to-inherit-from-the-usercontrol-class.md)
- [<span data-ttu-id="b1ed9-136">Nasıl yapılır: Windows Forms için Denetimler Yazma</span><span class="sxs-lookup"><span data-stu-id="b1ed9-136">How to: Author Controls for Windows Forms</span></span>](how-to-author-controls-for-windows-forms.md)
- [<span data-ttu-id="b1ed9-137">Visual Basic'de Devralınmış Olay İşleyicileri İle İlgili Sorun Giderme</span><span class="sxs-lookup"><span data-stu-id="b1ed9-137">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
- [<span data-ttu-id="b1ed9-138">Walkthrough: Windows Forms Denetiminden Devralma</span><span class="sxs-lookup"><span data-stu-id="b1ed9-138">Walkthrough: Inheriting from a Windows Forms Control</span></span>](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)
