---
title: "Nasıl yapılır: Bileşik Denetimler Yazma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UserControl class [Windows Forms], creating composite controls
- user controls [Windows Forms], creating
- user controls [Windows Forms], inheriting from
- composite controls [Windows Forms], creating
ms.assetid: 79c9cf05-5ab6-4a18-886d-88a64748b098
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 72c68568f0178956d6154f0b3a070e69b6ff0502
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-author-composite-controls"></a><span data-ttu-id="5f9b5-102">Nasıl yapılır: Bileşik Denetimler Yazma</span><span class="sxs-lookup"><span data-stu-id="5f9b5-102">How to: Author Composite Controls</span></span>
<span data-ttu-id="5f9b5-103">Bileşik denetimler birçok yolla değişiklik.</span><span class="sxs-lookup"><span data-stu-id="5f9b5-103">Composite controls can be employed in many ways.</span></span> <span data-ttu-id="5f9b5-104">Windows masaüstü uygulaması projesi parçası olarak bunları yazar ve bunları yalnızca projesinde formlarda kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5f9b5-104">You can author them as part of a Windows desktop application project, and use them only on forms in the project.</span></span> <span data-ttu-id="5f9b5-105">Veya Windows Denetim Kitaplığı projede yazar, bir derlemeye Projeyi derlemek ve diğer projelerinde denetimleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="5f9b5-105">Or you can author them in a Windows Control Library project, compile the project into an assembly, and use the controls in other projects.</span></span> <span data-ttu-id="5f9b5-106">Bile, bunları devralır ve görsel devralma bunları hızlı bir şekilde özel amaçlarla özelleştirmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="5f9b5-106">You can even inherit from them, and use visual inheritance to customize them quickly for special purposes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5f9b5-107">Web Forms kullanmak için bkz: bileşik denetim yazma istiyorsanız [özel ASP.NET sunucu denetimleri geliştirme](http://msdn.microsoft.com/library/fbe26c16-cff4-4089-b3dd-877411f0c0ef).</span><span class="sxs-lookup"><span data-stu-id="5f9b5-107">If you want to author a composite control to use on Web Forms, see [Developing Custom ASP.NET Server Controls](http://msdn.microsoft.com/library/fbe26c16-cff4-4089-b3dd-877411f0c0ef).</span></span>  
>   
>  <span data-ttu-id="5f9b5-108">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="5f9b5-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="5f9b5-109">Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="5f9b5-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="5f9b5-110">Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="5f9b5-110">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-author-a-composite-control"></a><span data-ttu-id="5f9b5-111">Bileşik denetim yazma</span><span class="sxs-lookup"><span data-stu-id="5f9b5-111">To author a composite control</span></span>  
  
1.  <span data-ttu-id="5f9b5-112">Yeni bir **Windows uygulaması** adlı proje `DemoControlHost`.</span><span class="sxs-lookup"><span data-stu-id="5f9b5-112">Open a new **Windows Application** project called `DemoControlHost`.</span></span>  
  
2.  <span data-ttu-id="5f9b5-113">Üzerinde **proje**menüsünde tıklatın **kullanıcı denetimi Ekle**.</span><span class="sxs-lookup"><span data-stu-id="5f9b5-113">On the **Project**menu, click **Add User Control**.</span></span>  
  
3.  <span data-ttu-id="5f9b5-114">İçinde **Yeni Öğe Ekle** iletişim kutusu, sınıf dosya (.vb veya .cs dosyası) için bileşik denetim istediğiniz adı verin.</span><span class="sxs-lookup"><span data-stu-id="5f9b5-114">In the **Add New Item** dialog box, give the class file (.vb or .cs file) the name you want the composite control to have.</span></span>  
  
4.  <span data-ttu-id="5f9b5-115">Tıklatın **Ekle** bileşik denetim için sınıf dosyası oluşturmak için düğmesi.</span><span class="sxs-lookup"><span data-stu-id="5f9b5-115">Click the **Add** button to create the class file for the composite control.</span></span>  
  
5.  <span data-ttu-id="5f9b5-116">Denetimleri ekleme **araç** bileşik denetim yüzeye.</span><span class="sxs-lookup"><span data-stu-id="5f9b5-116">Add controls from the **Toolbox** to the composite control surface.</span></span>  
  
6.  <span data-ttu-id="5f9b5-117">Bileşik denetim veya onun bağlı denetimler tarafından başlatılan olayları işlemek için olay yordamları kodu yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="5f9b5-117">Place code in event procedures, to handle events raised by the composite control or by its constituent controls.</span></span>  
  
7.  <span data-ttu-id="5f9b5-118">Bileşik Denetim Tasarımcı kapatın ve sorulduğunda, dosyayı kaydedin.</span><span class="sxs-lookup"><span data-stu-id="5f9b5-118">Close the designer for the composite control, and save the file when you are prompted.</span></span>  
  
8.  <span data-ttu-id="5f9b5-119">Üzerinde **yapı** menüsünde tıklatın **yapı çözümü**.</span><span class="sxs-lookup"><span data-stu-id="5f9b5-119">On the **Build** menu, click **Build Solution**.</span></span>  
  
     <span data-ttu-id="5f9b5-120">Proje görünmesi özel denetimler için sırada oluşturulmalıdır **araç**.</span><span class="sxs-lookup"><span data-stu-id="5f9b5-120">The project must be built in order for custom controls to appear in the **Toolbox**.</span></span>  
  
9. <span data-ttu-id="5f9b5-121">Kullanım **DemoControlHost** sekmesinde **araç** denetiminize örneklerini eklemek için `Form1`.</span><span class="sxs-lookup"><span data-stu-id="5f9b5-121">Use the **DemoControlHost** tab of the **Toolbox** to add instances of your control to `Form1`.</span></span>  
  
### <a name="to-author-a-control-class-library"></a><span data-ttu-id="5f9b5-122">Yazar denetim sınıf kitaplığı</span><span class="sxs-lookup"><span data-stu-id="5f9b5-122">To author a control class library</span></span>  
  
1.  <span data-ttu-id="5f9b5-123">Yeni bir **Windows Denetim Kitaplığı** projesi.</span><span class="sxs-lookup"><span data-stu-id="5f9b5-123">Open a new **Windows Control Library** project.</span></span>  
  
     <span data-ttu-id="5f9b5-124">Varsayılan olarak, projeyi bileşik denetim içerir.</span><span class="sxs-lookup"><span data-stu-id="5f9b5-124">By default, the project contains a composite control.</span></span>  
  
2.  <span data-ttu-id="5f9b5-125">Denetimleri ve yukarıdaki yordamda açıklandığı şekilde kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="5f9b5-125">Add controls and code as described in the procedure above.</span></span>  
  
3.  <span data-ttu-id="5f9b5-126">İstemiyorsanız değiştirin ve ayarlamak için sınıflar devralan bir denetim seçin **değiştiricileri** bu denetimin özelliğini **özel**.</span><span class="sxs-lookup"><span data-stu-id="5f9b5-126">Choose a control you do not want inheriting classes to change, and set the **Modifiers** property of this control to **Private**.</span></span>  
  
4.  <span data-ttu-id="5f9b5-127">Dll dosyasını oluşturun.</span><span class="sxs-lookup"><span data-stu-id="5f9b5-127">Build the DLL.</span></span>  
  
### <a name="to-inherit-from-a-composite-control-in-a-control-class-library"></a><span data-ttu-id="5f9b5-128">Bir denetim Sınıf Kitaplığı'nda bileşik denetim devralmak için</span><span class="sxs-lookup"><span data-stu-id="5f9b5-128">To inherit from a composite control in a control class library</span></span>  
  
1.  <span data-ttu-id="5f9b5-129">Üzerinde **dosya** menüsündeki **Ekle** seçip **yeni proje** yeni eklemek için **Windows uygulaması** çözüme proje.</span><span class="sxs-lookup"><span data-stu-id="5f9b5-129">On the **File** menu, point to **Add** and select **New Project** to add a new **Windows Application** project to the solution.</span></span>  
  
2.  <span data-ttu-id="5f9b5-130">İçinde **Çözüm Gezgini**, sağ **başvuruları** yeni klasör proje ve seçin **Başvuru Ekle** açmak için **Başvuru Ekle**iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="5f9b5-130">In **Solution Explorer**, right-click the **References** folder for the new project and choose **Add Reference** to open the **Add Reference** dialog box.</span></span>  
  
3.  <span data-ttu-id="5f9b5-131">Seçin **projeleri** sekmesinde ve denetim kitaplığı projenizin çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="5f9b5-131">Select the **Projects** tab and double-click your control library project.</span></span>  
  
4.  <span data-ttu-id="5f9b5-132">Üzerinde **yapı** menüsünde tıklatın **yapı çözümü**.</span><span class="sxs-lookup"><span data-stu-id="5f9b5-132">On the **Build** menu, click **Build Solution**.</span></span>  
  
5.  <span data-ttu-id="5f9b5-133">İçinde **Çözüm Gezgini**, Denetim kitaplığını projenize sağ tıklayın ve seçin **Yeni Öğe Ekle** kısayol menüsünden.</span><span class="sxs-lookup"><span data-stu-id="5f9b5-133">In **Solution Explorer**, right-click your control library project and select **Add New Item** from the shortcut menu.</span></span>  
  
6.  <span data-ttu-id="5f9b5-134">Seçin **devralınan kullanıcı denetimi** şablondan **Yeni Öğe Ekle** iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="5f9b5-134">Select the **Inherited User Control** template from the **Add New Item** dialog box.</span></span>  
  
7.  <span data-ttu-id="5f9b5-135">İçinde **devralma Seçici** iletişim kutusunda, istediğiniz devralmak için denetimi çift tıklatın.</span><span class="sxs-lookup"><span data-stu-id="5f9b5-135">In the **Inheritance Picker** dialog box, double-click the control you want to inherit from.</span></span>  
  
     <span data-ttu-id="5f9b5-136">Yeni bir denetim projenize eklenir.</span><span class="sxs-lookup"><span data-stu-id="5f9b5-136">A new control is added to your project.</span></span>  
  
8.  <span data-ttu-id="5f9b5-137">Yeni denetim için görsel tasarımcı açın ve ek bağlı denetimler ekleyin.</span><span class="sxs-lookup"><span data-stu-id="5f9b5-137">Open the visual designer for the new control and add additional constituent controls.</span></span>  
  
     <span data-ttu-id="5f9b5-138">DLL bileşik denetiminden devralındığını bağlı denetimler görebilir ve denetimlerin özelliklerini değiştirebilir, **değiştiricileri** özelliği **ortak**.</span><span class="sxs-lookup"><span data-stu-id="5f9b5-138">You can see the constituent controls that were inherited from the composite control in your DLL, and you can alter the properties of controls whose **Modifiers** property is **Public**.</span></span> <span data-ttu-id="5f9b5-139">Denetim özelliklerini değiştiremezsiniz, **değiştiricileri** özelliği **özel**.</span><span class="sxs-lookup"><span data-stu-id="5f9b5-139">You cannot change the properties of the control whose **Modifiers** property is **Private**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f9b5-140">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5f9b5-140">See Also</span></span>  
 [<span data-ttu-id="5f9b5-141">İzlenecek yol: Visual Basic ile bileşik denetim yazma</span><span class="sxs-lookup"><span data-stu-id="5f9b5-141">Walkthrough: Authoring a Composite Control with Visual Basic</span></span>](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-basic.md)  
 [<span data-ttu-id="5f9b5-142">İzlenecek yol: Visual C# ile bileşik denetim yazma</span><span class="sxs-lookup"><span data-stu-id="5f9b5-142">Walkthrough: Authoring a Composite Control with Visual C#</span></span>](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-csharp.md)  
 [<span data-ttu-id="5f9b5-143">İzlenecek yol: Visual Basic ile beraber Windows Forms Denetimi'nden devralma</span><span class="sxs-lookup"><span data-stu-id="5f9b5-143">Walkthrough: Inheriting from a Windows Forms Control with Visual Basic</span></span>](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic.md)  
 [<span data-ttu-id="5f9b5-144">İzlenecek yol: Visual C# ile bir Windows Forms Denetimi'nden devralma</span><span class="sxs-lookup"><span data-stu-id="5f9b5-144">Walkthrough: Inheriting from a Windows Forms Control with Visual C#</span></span>](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)  
 [<span data-ttu-id="5f9b5-145">Denetim türü önerileri</span><span class="sxs-lookup"><span data-stu-id="5f9b5-145">Control Type Recommendations</span></span>](../../../../docs/framework/winforms/controls/control-type-recommendations.md)  
 [<span data-ttu-id="5f9b5-146">Nasıl yapılır: Windows formları için denetimler yazma</span><span class="sxs-lookup"><span data-stu-id="5f9b5-146">How to: Author Controls for Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-author-controls-for-windows-forms.md)  
 [<span data-ttu-id="5f9b5-147">Özel denetim çeşitleri</span><span class="sxs-lookup"><span data-stu-id="5f9b5-147">Varieties of Custom Controls</span></span>](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)
