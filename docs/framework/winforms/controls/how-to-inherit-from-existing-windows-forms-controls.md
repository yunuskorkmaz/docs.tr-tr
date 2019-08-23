---
title: 'Nasıl yapılır: Mevcut Windows Forms Denetimlerinden Devralma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- custom controls [Windows Forms], inheritance
ms.assetid: 1e1fc8ea-c615-4cf0-a356-16d6df7444ab
ms.openlocfilehash: 9ac18fae126425126712dafeb80f05663dfc2ebc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966595"
---
# <a name="how-to-inherit-from-existing-windows-forms-controls"></a><span data-ttu-id="e1ea8-102">Nasıl yapılır: Mevcut Windows Forms Denetimlerinden Devralma</span><span class="sxs-lookup"><span data-stu-id="e1ea8-102">How to: Inherit from Existing Windows Forms Controls</span></span>
<span data-ttu-id="e1ea8-103">Varolan bir denetimin işlevselliğini genişletmek istiyorsanız, devralma yoluyla var olan bir denetimden türetilmiş bir denetim oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e1ea8-103">If you want to extend the functionality of an existing control, you can create a control derived from an existing control through inheritance.</span></span> <span data-ttu-id="e1ea8-104">Var olan bir denetimden devralınırken, bu denetimin tüm işlevselliğini ve görsel özelliklerini devralırsınız.</span><span class="sxs-lookup"><span data-stu-id="e1ea8-104">When inheriting from an existing control, you inherit all of the functionality and visual properties of that control.</span></span> <span data-ttu-id="e1ea8-105">Örneğin, öğesinden <xref:System.Windows.Forms.Button>devralınan bir denetim oluşturuyorsanız, yeni denetiminiz bir standart <xref:System.Windows.Forms.Button> denetim gibi görünür ve çalışır.</span><span class="sxs-lookup"><span data-stu-id="e1ea8-105">For example, if you were creating a control that inherited from <xref:System.Windows.Forms.Button>, your new control would look and act exactly like a standard <xref:System.Windows.Forms.Button> control.</span></span> <span data-ttu-id="e1ea8-106">Daha sonra özel yöntemlerin ve özelliklerin uygulanmasıyla yeni denetiminizin işlevselliğini genişletebilir veya değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e1ea8-106">You could then extend or modify the functionality of your new control through the implementation of custom methods and properties.</span></span> <span data-ttu-id="e1ea8-107">Bazı denetimlerde, kendi <xref:System.Windows.Forms.Control.OnPaint%2A> metodunu geçersiz kılarak devralınmış denetiminizin görsel görünümünü de değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e1ea8-107">In some controls, you can also change the visual appearance of your inherited control by overriding its <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span>

## <a name="to-create-an-inherited-control"></a><span data-ttu-id="e1ea8-108">Devralınan bir denetim oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="e1ea8-108">To create an inherited control</span></span>

1. <span data-ttu-id="e1ea8-109">Yeni bir **Windows Forms uygulama** projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e1ea8-109">Create a new **Windows Forms Application** project.</span></span>

2. <span data-ttu-id="e1ea8-110">**Proje** menüsünde **Yeni öğe Ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="e1ea8-110">From the **Project** menu, choose **Add New Item**.</span></span>

     <span data-ttu-id="e1ea8-111">**Yeni Öğe Ekle** iletişim kutusu görünür.</span><span class="sxs-lookup"><span data-stu-id="e1ea8-111">The **Add New Item** dialog box appears.</span></span>

3. <span data-ttu-id="e1ea8-112">**Yeni öğe Ekle** Iletişim kutusunda **özel denetim ' e**çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="e1ea8-112">In the **Add New Item** dialog box, double-click **Custom Control**.</span></span>

     <span data-ttu-id="e1ea8-113">Projenize yeni bir özel denetim eklenir.</span><span class="sxs-lookup"><span data-stu-id="e1ea8-113">A new custom control is added to your project.</span></span>

4. <span data-ttu-id="e1ea8-114">Visual Basic kullanıyorsanız, **Çözüm Gezgini**üst kısmında **tüm dosyaları göster**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="e1ea8-114">If you using Visual Basic, at the top of **Solution Explorer**, click **Show All Files**.</span></span> <span data-ttu-id="e1ea8-115">CustomControl1. vb öğesini genişletin ve ardından kod düzenleyicisinde CustomControl1. Designer. vb dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="e1ea8-115">Expand CustomControl1.vb and then open CustomControl1.Designer.vb in the Code Editor.</span></span>

5. <span data-ttu-id="e1ea8-116">Kullanıyorsanız C#, kod düzenleyicisi 'nde CustomControl1.cs öğesini açın.</span><span class="sxs-lookup"><span data-stu-id="e1ea8-116">If you are using C#, open CustomControl1.cs in the Code Editor.</span></span>

6. <span data-ttu-id="e1ea8-117">Öğesinden <xref:System.Windows.Forms.Control>devralan sınıf bildirimini bulun.</span><span class="sxs-lookup"><span data-stu-id="e1ea8-117">Locate the class declaration, which inherits from <xref:System.Windows.Forms.Control>.</span></span>

7. <span data-ttu-id="e1ea8-118">Taban sınıfını, devralması istediğiniz denetim olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="e1ea8-118">Change the base class to the control that you want to inherit from.</span></span>

     <span data-ttu-id="e1ea8-119">Örneğin, öğesinden <xref:System.Windows.Forms.Button>devralma yapmak istiyorsanız, sınıf bildirimini aşağıdaki şekilde değiştirin:</span><span class="sxs-lookup"><span data-stu-id="e1ea8-119">For example, if you want to inherit from <xref:System.Windows.Forms.Button>, change the class declaration to the following:</span></span>

    ```vb
    Partial Class CustomControl1
        Inherits System.Windows.Forms.Button
    ```

    ```csharp
    public partial class CustomControl1 : System.Windows.Forms.Button
    ```

8. <span data-ttu-id="e1ea8-120">Visual Basic kullanıyorsanız, CustomControl1. Designer. vb dosyasını kaydedin ve kapatın.</span><span class="sxs-lookup"><span data-stu-id="e1ea8-120">If you are using Visual Basic, save and close CustomControl1.Designer.vb.</span></span> <span data-ttu-id="e1ea8-121">Kod Düzenleyicisi 'nde CustomControl1. vb dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="e1ea8-121">Open CustomControl1.vb in the Code Editor.</span></span>

9. <span data-ttu-id="e1ea8-122">Denetiminizin dahil olacağı özel yöntemleri veya özellikleri uygulayın.</span><span class="sxs-lookup"><span data-stu-id="e1ea8-122">Implement any custom methods or properties that your control will incorporate.</span></span>

10. <span data-ttu-id="e1ea8-123">Denetiminizin grafik görünümünü değiştirmek istiyorsanız, <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemini geçersiz kılın.</span><span class="sxs-lookup"><span data-stu-id="e1ea8-123">If you want to modify the graphical appearance of your control, override the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span>

    > [!NOTE]
    > <span data-ttu-id="e1ea8-124">Geçersiz <xref:System.Windows.Forms.Control.OnPaint%2A> kılma, tüm denetimlerin görünümünü değiştirmenize izin vermez.</span><span class="sxs-lookup"><span data-stu-id="e1ea8-124">Overriding <xref:System.Windows.Forms.Control.OnPaint%2A> will not allow you to modify the appearance of all controls.</span></span> <span data-ttu-id="e1ea8-125">Tüm boyama pencerelerinin Windows tarafından (örneğin, <xref:System.Windows.Forms.TextBox>) yaptığı denetimler hiçbir şekilde <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemini çağırmaz ve bu nedenle özel kodu hiçbir şey kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="e1ea8-125">Those controls that have all of their painting done by Windows (for example, <xref:System.Windows.Forms.TextBox>) never call their <xref:System.Windows.Forms.Control.OnPaint%2A> method, and thus will never use the custom code.</span></span> <span data-ttu-id="e1ea8-126"><xref:System.Windows.Forms.Control.OnPaint%2A> Yöntemin kullanılabilir olup olmadığını görmek için değiştirmek istediğiniz belirli denetim için yardım belgelerine başvurun.</span><span class="sxs-lookup"><span data-stu-id="e1ea8-126">Refer to the Help documentation for the particular control you want to modify to see if the <xref:System.Windows.Forms.Control.OnPaint%2A> method is available.</span></span> <span data-ttu-id="e1ea8-127">Tüm Windows form denetimlerinin listesi için bkz. [Windows Forms Için kullanılacak denetimler](controls-to-use-on-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="e1ea8-127">For a list of all the Windows Form Controls, see [Controls to Use on Windows Forms](controls-to-use-on-windows-forms.md).</span></span> <span data-ttu-id="e1ea8-128">Bir denetim <xref:System.Windows.Forms.Control.OnPaint%2A> üye yöntemi olarak listelenmiyorsa, bu yöntemi geçersiz kılarak görünümünü değiştiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="e1ea8-128">If a control does not have <xref:System.Windows.Forms.Control.OnPaint%2A> listed as a member method, you cannot alter its appearance by overriding this method.</span></span> <span data-ttu-id="e1ea8-129">Özel boyama hakkında daha fazla bilgi için bkz. [özel denetim boyama ve işleme](custom-control-painting-and-rendering.md).</span><span class="sxs-lookup"><span data-stu-id="e1ea8-129">For more information about custom painting, see [Custom Control Painting and Rendering](custom-control-painting-and-rendering.md).</span></span>

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

11. <span data-ttu-id="e1ea8-130">Denetiminizi kaydedin ve test edin.</span><span class="sxs-lookup"><span data-stu-id="e1ea8-130">Save and test your control.</span></span>

## <a name="see-also"></a><span data-ttu-id="e1ea8-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e1ea8-131">See also</span></span>

- [<span data-ttu-id="e1ea8-132">Özel Denetim Çeşitleri</span><span class="sxs-lookup"><span data-stu-id="e1ea8-132">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
- [<span data-ttu-id="e1ea8-133">Nasıl yapılır: Denetim sınıfından devralma</span><span class="sxs-lookup"><span data-stu-id="e1ea8-133">How to: Inherit from the Control Class</span></span>](how-to-inherit-from-the-control-class.md)
- [<span data-ttu-id="e1ea8-134">Nasıl yapılır: UserControl sınıfından devralma</span><span class="sxs-lookup"><span data-stu-id="e1ea8-134">How to: Inherit from the UserControl Class</span></span>](how-to-inherit-from-the-usercontrol-class.md)
- [<span data-ttu-id="e1ea8-135">Nasıl yapılır: Windows Forms için yazar denetimleri</span><span class="sxs-lookup"><span data-stu-id="e1ea8-135">How to: Author Controls for Windows Forms</span></span>](how-to-author-controls-for-windows-forms.md)
- [<span data-ttu-id="e1ea8-136">Visual Basic devralınan olay Işleyicileriyle ilgili sorunları giderme</span><span class="sxs-lookup"><span data-stu-id="e1ea8-136">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
- [<span data-ttu-id="e1ea8-137">İzlenecek yol: Visual Basic ile Windows Forms denetiminden devralma</span><span class="sxs-lookup"><span data-stu-id="e1ea8-137">Walkthrough: Inheriting from a Windows Forms Control with Visual Basic</span></span>](walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic.md)
- [<span data-ttu-id="e1ea8-138">İzlenecek yol: Görsel ile Windows Forms denetiminden devralmaC#</span><span class="sxs-lookup"><span data-stu-id="e1ea8-138">Walkthrough: Inheriting from a Windows Forms Control with Visual C#</span></span>](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)
