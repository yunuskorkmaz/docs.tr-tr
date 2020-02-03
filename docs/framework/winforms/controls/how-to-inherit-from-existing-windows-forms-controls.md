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
ms.openlocfilehash: d0025ba136698c0a74a73e64a83fa4f526e44843
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736488"
---
# <a name="how-to-inherit-from-existing-windows-forms-controls"></a><span data-ttu-id="13703-102">Nasıl yapılır: Mevcut Windows Formları Denetimlerinden Devralma</span><span class="sxs-lookup"><span data-stu-id="13703-102">How to: Inherit from Existing Windows Forms Controls</span></span>

<span data-ttu-id="13703-103">Varolan bir denetimin işlevselliğini genişletmek istiyorsanız, devralma yoluyla var olan bir denetimden türetilmiş bir denetim oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="13703-103">If you want to extend the functionality of an existing control, you can create a control derived from an existing control through inheritance.</span></span> <span data-ttu-id="13703-104">Var olan bir denetimden devralınırken, bu denetimin tüm işlevselliğini ve görsel özelliklerini devralırsınız.</span><span class="sxs-lookup"><span data-stu-id="13703-104">When inheriting from an existing control, you inherit all of the functionality and visual properties of that control.</span></span> <span data-ttu-id="13703-105">Örneğin, <xref:System.Windows.Forms.Button>devralınan bir denetim oluşturuyorsanız, yeni denetiminiz standart bir <xref:System.Windows.Forms.Button> denetimi gibi görünür ve aynı şekilde davranır.</span><span class="sxs-lookup"><span data-stu-id="13703-105">For example, if you were creating a control that inherited from <xref:System.Windows.Forms.Button>, your new control would look and act exactly like a standard <xref:System.Windows.Forms.Button> control.</span></span> <span data-ttu-id="13703-106">Daha sonra özel yöntemlerin ve özelliklerin uygulanmasıyla yeni denetiminizin işlevselliğini genişletebilir veya değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="13703-106">You could then extend or modify the functionality of your new control through the implementation of custom methods and properties.</span></span> <span data-ttu-id="13703-107">Bazı denetimlerde, <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemini geçersiz kılarak devralınmış denetiminizin görsel görünümünü de değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="13703-107">In some controls, you can also change the visual appearance of your inherited control by overriding its <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span>

## <a name="to-create-an-inherited-control"></a><span data-ttu-id="13703-108">Devralınan bir denetim oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="13703-108">To create an inherited control</span></span>

1. <span data-ttu-id="13703-109">Visual Studio 'da yeni bir **Windows Forms uygulama** projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="13703-109">In Visual Studio, create a new **Windows Forms Application** project.</span></span>

1. <span data-ttu-id="13703-110">**Proje** menüsünde **Yeni öğe Ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="13703-110">From the **Project** menu, choose **Add New Item**.</span></span>

    <span data-ttu-id="13703-111">**Yeni Öğe Ekle** iletişim kutusu görünür.</span><span class="sxs-lookup"><span data-stu-id="13703-111">The **Add New Item** dialog box appears.</span></span>

1. <span data-ttu-id="13703-112">**Yeni öğe Ekle** Iletişim kutusunda **özel denetim ' e**çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="13703-112">In the **Add New Item** dialog box, double-click **Custom Control**.</span></span>

    <span data-ttu-id="13703-113">Projenize yeni bir özel denetim eklenir.</span><span class="sxs-lookup"><span data-stu-id="13703-113">A new custom control is added to your project.</span></span>

1. <span data-ttu-id="13703-114">Şunu kullanıyorsanız:</span><span class="sxs-lookup"><span data-stu-id="13703-114">If you using:</span></span>

    - <span data-ttu-id="13703-115">Visual Basic, **Çözüm Gezgini**üst kısmında **tüm dosyaları göster**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="13703-115">Visual Basic, at the top of **Solution Explorer**, click **Show All Files**.</span></span> <span data-ttu-id="13703-116">CustomControl1. vb öğesini genişletin ve ardından kod düzenleyicisinde CustomControl1. Designer. vb dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="13703-116">Expand CustomControl1.vb and then open CustomControl1.Designer.vb in the Code Editor.</span></span>
    - <span data-ttu-id="13703-117">C#, kod düzenleyicisinde CustomControl1.cs öğesini açın.</span><span class="sxs-lookup"><span data-stu-id="13703-117">C#, open CustomControl1.cs in the Code Editor.</span></span>

1. <span data-ttu-id="13703-118"><xref:System.Windows.Forms.Control>devralan sınıf bildirimini bulun.</span><span class="sxs-lookup"><span data-stu-id="13703-118">Locate the class declaration, which inherits from <xref:System.Windows.Forms.Control>.</span></span>

1. <span data-ttu-id="13703-119">Taban sınıfını, devralması istediğiniz denetim olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="13703-119">Change the base class to the control that you want to inherit from.</span></span>

     <span data-ttu-id="13703-120">Örneğin, <xref:System.Windows.Forms.Button>devralma yapmak istiyorsanız, sınıf bildirimini aşağıdaki şekilde değiştirin:</span><span class="sxs-lookup"><span data-stu-id="13703-120">For example, if you want to inherit from <xref:System.Windows.Forms.Button>, change the class declaration to the following:</span></span>

    ```vb
    Partial Class CustomControl1
        Inherits System.Windows.Forms.Button
    ```

    ```csharp
    public partial class CustomControl1 : System.Windows.Forms.Button
    ```

1. <span data-ttu-id="13703-121">Visual Basic kullanıyorsanız, CustomControl1. Designer. vb dosyasını kaydedin ve kapatın.</span><span class="sxs-lookup"><span data-stu-id="13703-121">If you are using Visual Basic, save and close CustomControl1.Designer.vb.</span></span> <span data-ttu-id="13703-122">Kod Düzenleyicisi 'nde CustomControl1. vb dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="13703-122">Open CustomControl1.vb in the Code Editor.</span></span>

1. <span data-ttu-id="13703-123">Denetiminizin dahil olacağı özel yöntemleri veya özellikleri uygulayın.</span><span class="sxs-lookup"><span data-stu-id="13703-123">Implement any custom methods or properties that your control will incorporate.</span></span>

1. <span data-ttu-id="13703-124">Denetiminizin grafik görünümünü değiştirmek istiyorsanız <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemini geçersiz kılın.</span><span class="sxs-lookup"><span data-stu-id="13703-124">If you want to modify the graphical appearance of your control, override the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span>

    > [!NOTE]
    > <span data-ttu-id="13703-125"><xref:System.Windows.Forms.Control.OnPaint%2A> geçersiz kılmak tüm denetimlerin görünümünü değiştirmenize izin vermez.</span><span class="sxs-lookup"><span data-stu-id="13703-125">Overriding <xref:System.Windows.Forms.Control.OnPaint%2A> will not allow you to modify the appearance of all controls.</span></span> <span data-ttu-id="13703-126">Tüm boyalarını Windows tarafından gerçekleştirilen (örneğin, <xref:System.Windows.Forms.TextBox>) denetimler hiçbir şekilde <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemini çağırmaz ve bu nedenle özel kodu hiçbir şekilde kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="13703-126">Those controls that have all of their painting done by Windows (for example, <xref:System.Windows.Forms.TextBox>) never call their <xref:System.Windows.Forms.Control.OnPaint%2A> method, and thus will never use the custom code.</span></span> <span data-ttu-id="13703-127"><xref:System.Windows.Forms.Control.OnPaint%2A> yönteminin kullanılabilir olup olmadığını görmek için değiştirmek istediğiniz belirli denetim için yardım belgelerine başvurun.</span><span class="sxs-lookup"><span data-stu-id="13703-127">Refer to the Help documentation for the particular control you want to modify to see if the <xref:System.Windows.Forms.Control.OnPaint%2A> method is available.</span></span> <span data-ttu-id="13703-128">Tüm Windows form denetimlerinin listesi için bkz. [Windows Forms Için kullanılacak denetimler](controls-to-use-on-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="13703-128">For a list of all the Windows Form Controls, see [Controls to Use on Windows Forms](controls-to-use-on-windows-forms.md).</span></span> <span data-ttu-id="13703-129">Bir denetimin üye yöntemi olarak listelenen <xref:System.Windows.Forms.Control.OnPaint%2A> yoksa, bu yöntemi geçersiz kılarak görünümünü değiştiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="13703-129">If a control does not have <xref:System.Windows.Forms.Control.OnPaint%2A> listed as a member method, you cannot alter its appearance by overriding this method.</span></span> <span data-ttu-id="13703-130">Özel boyama hakkında daha fazla bilgi için bkz. [özel denetim boyama ve işleme](custom-control-painting-and-rendering.md).</span><span class="sxs-lookup"><span data-stu-id="13703-130">For more information about custom painting, see [Custom Control Painting and Rendering](custom-control-painting-and-rendering.md).</span></span>

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

1. <span data-ttu-id="13703-131">Denetiminizi kaydedin ve test edin.</span><span class="sxs-lookup"><span data-stu-id="13703-131">Save and test your control.</span></span>

## <a name="see-also"></a><span data-ttu-id="13703-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="13703-132">See also</span></span>

- [<span data-ttu-id="13703-133">Özel Denetim Çeşitleri</span><span class="sxs-lookup"><span data-stu-id="13703-133">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
- [<span data-ttu-id="13703-134">Nasıl yapılır: Denetim Sınıfından Devralma</span><span class="sxs-lookup"><span data-stu-id="13703-134">How to: Inherit from the Control Class</span></span>](how-to-inherit-from-the-control-class.md)
- [<span data-ttu-id="13703-135">Nasıl yapılır: UserControl Sınıfından Devralma</span><span class="sxs-lookup"><span data-stu-id="13703-135">How to: Inherit from the UserControl Class</span></span>](how-to-inherit-from-the-usercontrol-class.md)
- [<span data-ttu-id="13703-136">Nasıl yapılır: Windows Forms için Denetimler Yazma</span><span class="sxs-lookup"><span data-stu-id="13703-136">How to: Author Controls for Windows Forms</span></span>](how-to-author-controls-for-windows-forms.md)
- [<span data-ttu-id="13703-137">Visual Basic devralınan olay Işleyicileriyle ilgili sorunları giderme</span><span class="sxs-lookup"><span data-stu-id="13703-137">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
- [<span data-ttu-id="13703-138">İzlenecek yol: Windows Forms denetiminden devralma</span><span class="sxs-lookup"><span data-stu-id="13703-138">Walkthrough: Inheriting from a Windows Forms Control</span></span>](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)
