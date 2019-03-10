---
title: 'Nasıl yapılır: Mevcut Windows Formları denetimlerinden devralma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- custom controls [Windows Forms], inheritance
ms.assetid: 1e1fc8ea-c615-4cf0-a356-16d6df7444ab
ms.openlocfilehash: 9b3b5b2420a1121be81bc299dea645051f941cd8
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57707982"
---
# <a name="how-to-inherit-from-existing-windows-forms-controls"></a><span data-ttu-id="f2b2a-102">Nasıl yapılır: Mevcut Windows Formları denetimlerinden devralma</span><span class="sxs-lookup"><span data-stu-id="f2b2a-102">How to: Inherit from Existing Windows Forms Controls</span></span>
<span data-ttu-id="f2b2a-103">Varolan bir denetimi işlevlerini genişletmek istiyorsanız, varolan bir denetimi devralma yoluyla türetilen bir denetim oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f2b2a-103">If you want to extend the functionality of an existing control, you can create a control derived from an existing control through inheritance.</span></span> <span data-ttu-id="f2b2a-104">Varolan bir denetimden devralınırken tüm işlevleri ve denetim görsel özelliklerini devralır.</span><span class="sxs-lookup"><span data-stu-id="f2b2a-104">When inheriting from an existing control, you inherit all of the functionality and visual properties of that control.</span></span> <span data-ttu-id="f2b2a-105">Örneğin, devralınan bir denetim oluşturuyorsanız <xref:System.Windows.Forms.Button>, yeni denetiminizin görünür ve Yasası tam gibi standart <xref:System.Windows.Forms.Button> denetimi.</span><span class="sxs-lookup"><span data-stu-id="f2b2a-105">For example, if you were creating a control that inherited from <xref:System.Windows.Forms.Button>, your new control would look and act exactly like a standard <xref:System.Windows.Forms.Button> control.</span></span> <span data-ttu-id="f2b2a-106">Ardından genişletin veya yeni, denetimin özel yöntemleri ve özellikleri uygulaması aracılığıyla işlevselliğini değiştirmenize.</span><span class="sxs-lookup"><span data-stu-id="f2b2a-106">You could then extend or modify the functionality of your new control through the implementation of custom methods and properties.</span></span> <span data-ttu-id="f2b2a-107">Bazı denetimler, ayrıca, devralınan denetim görsel görünümünü geçersiz kılarak değiştirebilirsiniz, <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f2b2a-107">In some controls, you can also change the visual appearance of your inherited control by overriding its <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f2b2a-108">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="f2b2a-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="f2b2a-109">Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="f2b2a-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="f2b2a-110">Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="f2b2a-110">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-create-an-inherited-control"></a><span data-ttu-id="f2b2a-111">Devralınan bir denetim oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="f2b2a-111">To create an inherited control</span></span>  
  
1.  <span data-ttu-id="f2b2a-112">Yeni bir **Windows Forms uygulaması** proje.</span><span class="sxs-lookup"><span data-stu-id="f2b2a-112">Create a new **Windows Forms Application** project.</span></span>  
  
2.  <span data-ttu-id="f2b2a-113">Gelen **proje** menüsünde seçin **Yeni Öğe Ekle**.</span><span class="sxs-lookup"><span data-stu-id="f2b2a-113">From the **Project** menu, choose **Add New Item**.</span></span>  
  
     <span data-ttu-id="f2b2a-114">**Yeni Öğe Ekle** iletişim kutusu görünür.</span><span class="sxs-lookup"><span data-stu-id="f2b2a-114">The **Add New Item** dialog box appears.</span></span>  
  
3.  <span data-ttu-id="f2b2a-115">İçinde **Yeni Öğe Ekle** iletişim kutusunda, çift **özel denetim**.</span><span class="sxs-lookup"><span data-stu-id="f2b2a-115">In the **Add New Item** dialog box, double-click **Custom Control**.</span></span>  
  
     <span data-ttu-id="f2b2a-116">Yeni özel denetim projenize eklenir.</span><span class="sxs-lookup"><span data-stu-id="f2b2a-116">A new custom control is added to your project.</span></span>  
  
4.  <span data-ttu-id="f2b2a-117">Varsa, Visual Basic kullanarak en üstündeki **Çözüm Gezgini**, tıklayın **tüm dosyaları göster**.</span><span class="sxs-lookup"><span data-stu-id="f2b2a-117">If you using Visual Basic, at the top of **Solution Explorer**, click **Show All Files**.</span></span> <span data-ttu-id="f2b2a-118">CustomControl1.vb genişletin ve ardından CustomControl1.Designer.vb kod Düzenleyicisi'nde açın.</span><span class="sxs-lookup"><span data-stu-id="f2b2a-118">Expand CustomControl1.vb and then open CustomControl1.Designer.vb in the Code Editor.</span></span>  
  
5.  <span data-ttu-id="f2b2a-119">C# kullanıyorsanız CustomControl1.cs Kod Düzenleyicisi'nde açın.</span><span class="sxs-lookup"><span data-stu-id="f2b2a-119">If you are using C#, open CustomControl1.cs in the Code Editor.</span></span>  
  
6.  <span data-ttu-id="f2b2a-120">Öğesinden devralan sınıf bildiriminin bulun <xref:System.Windows.Forms.Control>.</span><span class="sxs-lookup"><span data-stu-id="f2b2a-120">Locate the class declaration, which inherits from <xref:System.Windows.Forms.Control>.</span></span>  
  
7.  <span data-ttu-id="f2b2a-121">Verileri devralmak istediğiniz denetlemek için temel sınıf değiştirin.</span><span class="sxs-lookup"><span data-stu-id="f2b2a-121">Change the base class to the control that you want to inherit from.</span></span>  
  
     <span data-ttu-id="f2b2a-122">Örneğin devralınacak istiyorsanız <xref:System.Windows.Forms.Button>, sınıf bildiriminin aşağıdakiyle değiştirin:</span><span class="sxs-lookup"><span data-stu-id="f2b2a-122">For example, if you want to inherit from <xref:System.Windows.Forms.Button>, change the class declaration to the following:</span></span>  
  
    ```vb  
    Partial Class CustomControl1  
        Inherits System.Windows.Forms.Button  
    ```  
  
    ```csharp  
    public partial class CustomControl1 : System.Windows.Forms.Button  
    ```  
  
8.  <span data-ttu-id="f2b2a-123">Visual Basic kullanıyorsanız, kaydedin ve CustomControl1.Designer.vb kapatın.</span><span class="sxs-lookup"><span data-stu-id="f2b2a-123">If you are using Visual Basic, save and close CustomControl1.Designer.vb.</span></span> <span data-ttu-id="f2b2a-124">CustomControl1.vb kod Düzenleyicisi'nde açın.</span><span class="sxs-lookup"><span data-stu-id="f2b2a-124">Open CustomControl1.vb in the Code Editor.</span></span>  
  
9. <span data-ttu-id="f2b2a-125">Herhangi bir özel yöntemler veya denetiminiz birleştirecektir özellikleri uygulayın.</span><span class="sxs-lookup"><span data-stu-id="f2b2a-125">Implement any custom methods or properties that your control will incorporate.</span></span>  
  
10. <span data-ttu-id="f2b2a-126">Grafik görünümünü değiştirmek istiyorsanız, geçersiz kılma <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f2b2a-126">If you want to modify the graphical appearance of your control, override the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f2b2a-127">Geçersiz kılma <xref:System.Windows.Forms.Control.OnPaint%2A> tüm denetimlerin görünümünü değiştirmenizi izin vermez.</span><span class="sxs-lookup"><span data-stu-id="f2b2a-127">Overriding <xref:System.Windows.Forms.Control.OnPaint%2A> will not allow you to modify the appearance of all controls.</span></span> <span data-ttu-id="f2b2a-128">Kendi boyama Windows tarafından yapılan tüm bu denetimler (örneğin, <xref:System.Windows.Forms.TextBox>) hiçbir zaman çağrısı kendi <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemi ve dolayısıyla kullanım özel kod hiçbir zaman.</span><span class="sxs-lookup"><span data-stu-id="f2b2a-128">Those controls that have all of their painting done by Windows (for example, <xref:System.Windows.Forms.TextBox>) never call their <xref:System.Windows.Forms.Control.OnPaint%2A> method, and thus will never use the custom code.</span></span> <span data-ttu-id="f2b2a-129">Olmadığını görmek için değiştirmek istediğiniz belirli denetim için Yardım belgelerine başvurun <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemi kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f2b2a-129">Refer to the Help documentation for the particular control you want to modify to see if the <xref:System.Windows.Forms.Control.OnPaint%2A> method is available.</span></span> <span data-ttu-id="f2b2a-130">Tüm Windows Form denetimleri listesi için bkz. [Windows Forms'da kullanılacak denetimler](controls-to-use-on-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="f2b2a-130">For a list of all the Windows Form Controls, see [Controls to Use on Windows Forms](controls-to-use-on-windows-forms.md).</span></span> <span data-ttu-id="f2b2a-131">Bir denetim yoksa <xref:System.Windows.Forms.Control.OnPaint%2A> üye yöntemi olarak listelenen, görünümünü bu yöntemi geçersiz kılarak değiştirilemiyor.</span><span class="sxs-lookup"><span data-stu-id="f2b2a-131">If a control does not have <xref:System.Windows.Forms.Control.OnPaint%2A> listed as a member method, you cannot alter its appearance by overriding this method.</span></span> <span data-ttu-id="f2b2a-132">Özel boyama hakkında daha fazla bilgi için bkz: [özel denetim boyama ve işleme](custom-control-painting-and-rendering.md).</span><span class="sxs-lookup"><span data-stu-id="f2b2a-132">For more information about custom painting, see [Custom Control Painting and Rendering](custom-control-painting-and-rendering.md).</span></span>  
  
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
  
11. <span data-ttu-id="f2b2a-133">Kaydet ve denetim test edin.</span><span class="sxs-lookup"><span data-stu-id="f2b2a-133">Save and test your control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2b2a-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f2b2a-134">See also</span></span>
- [<span data-ttu-id="f2b2a-135">Özel Denetim Çeşitleri</span><span class="sxs-lookup"><span data-stu-id="f2b2a-135">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
- [<span data-ttu-id="f2b2a-136">Nasıl yapılır: Denetim sınıfından devralma</span><span class="sxs-lookup"><span data-stu-id="f2b2a-136">How to: Inherit from the Control Class</span></span>](how-to-inherit-from-the-control-class.md)
- [<span data-ttu-id="f2b2a-137">Nasıl yapılır: UserControl sınıfından devralma</span><span class="sxs-lookup"><span data-stu-id="f2b2a-137">How to: Inherit from the UserControl Class</span></span>](how-to-inherit-from-the-usercontrol-class.md)
- [<span data-ttu-id="f2b2a-138">Nasıl yapılır: Windows Forms için yazar denetimleri</span><span class="sxs-lookup"><span data-stu-id="f2b2a-138">How to: Author Controls for Windows Forms</span></span>](how-to-author-controls-for-windows-forms.md)
- [<span data-ttu-id="f2b2a-139">Basic'de devralınmış olay işleyicileri Visual Basic sorunlarını giderme</span><span class="sxs-lookup"><span data-stu-id="f2b2a-139">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
- [<span data-ttu-id="f2b2a-140">İzlenecek yol: Visual Basic ile Windows Forms Denetimi'nden devralma</span><span class="sxs-lookup"><span data-stu-id="f2b2a-140">Walkthrough: Inheriting from a Windows Forms Control with Visual Basic</span></span>](walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic.md)
- [<span data-ttu-id="f2b2a-141">İzlenecek yol: Visual C# ile Windows Forms Denetimi'nden devralma</span><span class="sxs-lookup"><span data-stu-id="f2b2a-141">Walkthrough: Inheriting from a Windows Forms Control with Visual C#</span></span>](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)
