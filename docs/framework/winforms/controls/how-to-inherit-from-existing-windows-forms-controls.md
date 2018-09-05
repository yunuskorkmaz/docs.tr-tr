---
title: 'Nasıl yapılır: Mevcut Windows Formları Denetimlerinden Devralma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- custom controls [Windows Forms], inheritance
ms.assetid: 1e1fc8ea-c615-4cf0-a356-16d6df7444ab
ms.openlocfilehash: f19b207c840994ffa3aa364135583b5daeb26827
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43542290"
---
# <a name="how-to-inherit-from-existing-windows-forms-controls"></a><span data-ttu-id="9691b-102">Nasıl yapılır: Mevcut Windows Formları Denetimlerinden Devralma</span><span class="sxs-lookup"><span data-stu-id="9691b-102">How to: Inherit from Existing Windows Forms Controls</span></span>
<span data-ttu-id="9691b-103">Varolan bir denetimi işlevlerini genişletmek istiyorsanız, varolan bir denetimi devralma yoluyla türetilen bir denetim oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9691b-103">If you want to extend the functionality of an existing control, you can create a control derived from an existing control through inheritance.</span></span> <span data-ttu-id="9691b-104">Varolan bir denetimden devralınırken tüm işlevleri ve denetim görsel özelliklerini devralır.</span><span class="sxs-lookup"><span data-stu-id="9691b-104">When inheriting from an existing control, you inherit all of the functionality and visual properties of that control.</span></span> <span data-ttu-id="9691b-105">Örneğin, devralınan bir denetim oluşturuyorsanız <xref:System.Windows.Forms.Button>, yeni denetiminizin görünür ve Yasası tam gibi standart <xref:System.Windows.Forms.Button> denetimi.</span><span class="sxs-lookup"><span data-stu-id="9691b-105">For example, if you were creating a control that inherited from <xref:System.Windows.Forms.Button>, your new control would look and act exactly like a standard <xref:System.Windows.Forms.Button> control.</span></span> <span data-ttu-id="9691b-106">Ardından genişletin veya yeni, denetimin özel yöntemleri ve özellikleri uygulaması aracılığıyla işlevselliğini değiştirmenize.</span><span class="sxs-lookup"><span data-stu-id="9691b-106">You could then extend or modify the functionality of your new control through the implementation of custom methods and properties.</span></span> <span data-ttu-id="9691b-107">Bazı denetimler, ayrıca, devralınan denetim görsel görünümünü geçersiz kılarak değiştirebilirsiniz, <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="9691b-107">In some controls, you can also change the visual appearance of your inherited control by overriding its <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9691b-108">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="9691b-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="9691b-109">Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="9691b-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="9691b-110">Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="9691b-110">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-create-an-inherited-control"></a><span data-ttu-id="9691b-111">Devralınan bir denetim oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="9691b-111">To create an inherited control</span></span>  
  
1.  <span data-ttu-id="9691b-112">Yeni bir **Windows Forms uygulaması** proje.</span><span class="sxs-lookup"><span data-stu-id="9691b-112">Create a new **Windows Forms Application** project.</span></span>  
  
2.  <span data-ttu-id="9691b-113">Gelen **proje** menüsünde seçin **Yeni Öğe Ekle**.</span><span class="sxs-lookup"><span data-stu-id="9691b-113">From the **Project** menu, choose **Add New Item**.</span></span>  
  
     <span data-ttu-id="9691b-114">**Yeni Öğe Ekle** iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="9691b-114">The **Add New Item** dialog box appears.</span></span>  
  
3.  <span data-ttu-id="9691b-115">İçinde **Yeni Öğe Ekle** iletişim kutusunda, çift **özel denetim**.</span><span class="sxs-lookup"><span data-stu-id="9691b-115">In the **Add New Item** dialog box, double-click **Custom Control**.</span></span>  
  
     <span data-ttu-id="9691b-116">Yeni özel denetim projenize eklenir.</span><span class="sxs-lookup"><span data-stu-id="9691b-116">A new custom control is added to your project.</span></span>  
  
4.  <span data-ttu-id="9691b-117">Varsa, Visual Basic kullanarak en üstündeki **Çözüm Gezgini**, tıklayın **tüm dosyaları göster**.</span><span class="sxs-lookup"><span data-stu-id="9691b-117">If you using Visual Basic, at the top of **Solution Explorer**, click **Show All Files**.</span></span> <span data-ttu-id="9691b-118">CustomControl1.vb genişletin ve ardından CustomControl1.Designer.vb kod Düzenleyicisi'nde açın.</span><span class="sxs-lookup"><span data-stu-id="9691b-118">Expand CustomControl1.vb and then open CustomControl1.Designer.vb in the Code Editor.</span></span>  
  
5.  <span data-ttu-id="9691b-119">C# kullanıyorsanız CustomControl1.cs Kod Düzenleyicisi'nde açın.</span><span class="sxs-lookup"><span data-stu-id="9691b-119">If you are using C#, open CustomControl1.cs in the Code Editor.</span></span>  
  
6.  <span data-ttu-id="9691b-120">Öğesinden devralan sınıf bildiriminin bulun <xref:System.Windows.Forms.Control>.</span><span class="sxs-lookup"><span data-stu-id="9691b-120">Locate the class declaration, which inherits from <xref:System.Windows.Forms.Control>.</span></span>  
  
7.  <span data-ttu-id="9691b-121">Verileri devralmak istediğiniz denetlemek için temel sınıf değiştirin.</span><span class="sxs-lookup"><span data-stu-id="9691b-121">Change the base class to the control that you want to inherit from.</span></span>  
  
     <span data-ttu-id="9691b-122">Örneğin devralınacak istiyorsanız <xref:System.Windows.Forms.Button>, sınıf bildiriminin aşağıdakiyle değiştirin:</span><span class="sxs-lookup"><span data-stu-id="9691b-122">For example, if you want to inherit from <xref:System.Windows.Forms.Button>, change the class declaration to the following:</span></span>  
  
    ```vb  
    Partial Class CustomControl1  
        Inherits System.Windows.Forms.Button  
    ```  
  
    ```csharp  
    public partial class CustomControl1 : System.Windows.Forms.Button  
    ```  
  
8.  <span data-ttu-id="9691b-123">Visual Basic kullanıyorsanız, kaydedin ve CustomControl1.Designer.vb kapatın.</span><span class="sxs-lookup"><span data-stu-id="9691b-123">If you are using Visual Basic, save and close CustomControl1.Designer.vb.</span></span> <span data-ttu-id="9691b-124">CustomControl1.vb kod Düzenleyicisi'nde açın.</span><span class="sxs-lookup"><span data-stu-id="9691b-124">Open CustomControl1.vb in the Code Editor.</span></span>  
  
9. <span data-ttu-id="9691b-125">Herhangi bir özel yöntemler veya denetiminiz birleştirecektir özellikleri uygulayın.</span><span class="sxs-lookup"><span data-stu-id="9691b-125">Implement any custom methods or properties that your control will incorporate.</span></span>  
  
10. <span data-ttu-id="9691b-126">Grafik görünümünü değiştirmek istiyorsanız, geçersiz kılma <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="9691b-126">If you want to modify the graphical appearance of your control, override the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="9691b-127">Geçersiz kılma <xref:System.Windows.Forms.Control.OnPaint%2A> tüm denetimlerin görünümünü değiştirmenizi izin vermez.</span><span class="sxs-lookup"><span data-stu-id="9691b-127">Overriding <xref:System.Windows.Forms.Control.OnPaint%2A> will not allow you to modify the appearance of all controls.</span></span> <span data-ttu-id="9691b-128">Kendi boyama Windows tarafından yapılan tüm bu denetimler (örneğin, <xref:System.Windows.Forms.TextBox>) hiçbir zaman çağrısı kendi <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemi ve dolayısıyla kullanım özel kod hiçbir zaman.</span><span class="sxs-lookup"><span data-stu-id="9691b-128">Those controls that have all of their painting done by Windows (for example, <xref:System.Windows.Forms.TextBox>) never call their <xref:System.Windows.Forms.Control.OnPaint%2A> method, and thus will never use the custom code.</span></span> <span data-ttu-id="9691b-129">Olmadığını görmek için değiştirmek istediğiniz belirli denetim için Yardım belgelerine başvurun <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemi kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9691b-129">Refer to the Help documentation for the particular control you want to modify to see if the <xref:System.Windows.Forms.Control.OnPaint%2A> method is available.</span></span> <span data-ttu-id="9691b-130">Tüm Windows Form denetimleri listesi için bkz. [Windows Forms'da kullanılacak denetimler](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="9691b-130">For a list of all the Windows Form Controls, see [Controls to Use on Windows Forms](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md).</span></span> <span data-ttu-id="9691b-131">Bir denetim yoksa <xref:System.Windows.Forms.Control.OnPaint%2A> üye yöntemi olarak listelenen, görünümünü bu yöntemi geçersiz kılarak değiştirilemiyor.</span><span class="sxs-lookup"><span data-stu-id="9691b-131">If a control does not have <xref:System.Windows.Forms.Control.OnPaint%2A> listed as a member method, you cannot alter its appearance by overriding this method.</span></span> <span data-ttu-id="9691b-132">Özel boyama hakkında daha fazla bilgi için bkz: [özel denetim boyama ve işleme](../../../../docs/framework/winforms/controls/custom-control-painting-and-rendering.md).</span><span class="sxs-lookup"><span data-stu-id="9691b-132">For more information about custom painting, see [Custom Control Painting and Rendering](../../../../docs/framework/winforms/controls/custom-control-painting-and-rendering.md).</span></span>  
  
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
  
11. <span data-ttu-id="9691b-133">Kaydet ve denetim test edin.</span><span class="sxs-lookup"><span data-stu-id="9691b-133">Save and test your control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9691b-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9691b-134">See Also</span></span>  
 [<span data-ttu-id="9691b-135">Özel Denetim Çeşitleri</span><span class="sxs-lookup"><span data-stu-id="9691b-135">Varieties of Custom Controls</span></span>](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)  
 [<span data-ttu-id="9691b-136">Nasıl yapılır: Denetim Sınıfından Devralma</span><span class="sxs-lookup"><span data-stu-id="9691b-136">How to: Inherit from the Control Class</span></span>](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-control-class.md)  
 [<span data-ttu-id="9691b-137">Nasıl yapılır: UserControl Sınıfından Devralma</span><span class="sxs-lookup"><span data-stu-id="9691b-137">How to: Inherit from the UserControl Class</span></span>](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-usercontrol-class.md)  
 [<span data-ttu-id="9691b-138">Nasıl yapılır: Windows Forms için Denetimler Yazma</span><span class="sxs-lookup"><span data-stu-id="9691b-138">How to: Author Controls for Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-author-controls-for-windows-forms.md)  
 [<span data-ttu-id="9691b-139">Basic'de devralınmış olay işleyicileri Visual Basic sorunlarını giderme</span><span class="sxs-lookup"><span data-stu-id="9691b-139">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)  
 [<span data-ttu-id="9691b-140">İzlenecek yol: Visual Basic ile beraber Windows Forms Denetimi'nden Devralma</span><span class="sxs-lookup"><span data-stu-id="9691b-140">Walkthrough: Inheriting from a Windows Forms Control with Visual Basic</span></span>](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic.md)  
 [<span data-ttu-id="9691b-141">İzlenecek yol: Visual C# ile beraber Windows Forms Denetimi'nden Devralma</span><span class="sxs-lookup"><span data-stu-id="9691b-141">Walkthrough: Inheriting from a Windows Forms Control with Visual C#</span></span>](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)
