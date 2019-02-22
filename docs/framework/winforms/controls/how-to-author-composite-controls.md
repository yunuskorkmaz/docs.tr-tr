---
title: 'Nasıl yapılır: Bileşik denetimler yazma'
ms.date: 03/30/2017
helpviewer_keywords:
- UserControl class [Windows Forms], creating composite controls
- user controls [Windows Forms], creating
- user controls [Windows Forms], inheriting from
- composite controls [Windows Forms], creating
ms.assetid: 79c9cf05-5ab6-4a18-886d-88a64748b098
ms.openlocfilehash: b2ccbfaf8305270116e3a85578e3e560ed0b4836
ms.sourcegitcommit: 07c4368273b446555cb2c85397ea266b39d5fe50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56584219"
---
# <a name="how-to-author-composite-controls"></a><span data-ttu-id="fd6c5-102">Nasıl yapılır: Bileşik denetimler yazma</span><span class="sxs-lookup"><span data-stu-id="fd6c5-102">How to: Author Composite Controls</span></span>
<span data-ttu-id="fd6c5-103">Bileşik denetimler, birçok bakımdan çalıştırılacağı.</span><span class="sxs-lookup"><span data-stu-id="fd6c5-103">Composite controls can be employed in many ways.</span></span> <span data-ttu-id="fd6c5-104">Bir Windows masaüstü uygulaması projesi bir parçası olarak bunları yazar ve bunları yalnızca projedeki formlarında kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fd6c5-104">You can author them as part of a Windows desktop application project, and use them only on forms in the project.</span></span> <span data-ttu-id="fd6c5-105">Veya bunları Windows Denetim Kitaplığı projesinde yazar, projenin bir derlemeye derlemek ve diğer projelerde denetimleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="fd6c5-105">Or you can author them in a Windows Control Library project, compile the project into an assembly, and use the controls in other projects.</span></span> <span data-ttu-id="fd6c5-106">Bile, bunları devralır ve bunları hızlı bir şekilde özel amaçlarla özelleştirmek için görsel devralma kullanın.</span><span class="sxs-lookup"><span data-stu-id="fd6c5-106">You can even inherit from them, and use visual inheritance to customize them quickly for special purposes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fd6c5-107">Web formlarında kullanmak üzere bileşik denetim yazma istiyorsanız [özel ASP.NET sunucu denetimleri geliştirme](https://docs.microsoft.com/previous-versions/aspnet/zt27tfhy(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="fd6c5-107">If you want to author a composite control to use on Web Forms, see [Developing Custom ASP.NET Server Controls](https://docs.microsoft.com/previous-versions/aspnet/zt27tfhy(v=vs.100)).</span></span>  
>   
>  <span data-ttu-id="fd6c5-108">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="fd6c5-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="fd6c5-109">Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="fd6c5-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="fd6c5-110">Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="fd6c5-110">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-author-a-composite-control"></a><span data-ttu-id="fd6c5-111">Bileşik denetim yazma</span><span class="sxs-lookup"><span data-stu-id="fd6c5-111">To author a composite control</span></span>  
  
1.  <span data-ttu-id="fd6c5-112">Yeni bir **Windows uygulama** adlı proje `DemoControlHost`.</span><span class="sxs-lookup"><span data-stu-id="fd6c5-112">Open a new **Windows Application** project called `DemoControlHost`.</span></span>  
  
2.  <span data-ttu-id="fd6c5-113">Üzerinde **proje** menüsünü tıklatın **kullanıcı denetimi Ekle**.</span><span class="sxs-lookup"><span data-stu-id="fd6c5-113">On the **Project** menu, click **Add User Control**.</span></span>  
  
3.  <span data-ttu-id="fd6c5-114">İçinde **Yeni Öğe Ekle** iletişim kutusu, sınıf dosyası (.vb veya .cs dosyası) bileşik denetime sahip olmasını istediğiniz adı verin.</span><span class="sxs-lookup"><span data-stu-id="fd6c5-114">In the **Add New Item** dialog box, give the class file (.vb or .cs file) the name you want the composite control to have.</span></span>  
  
4.  <span data-ttu-id="fd6c5-115">Seçin **Ekle** bileşik denetim için sınıf dosyası oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="fd6c5-115">Select the **Add** button to create the class file for the composite control.</span></span>  
  
5.  <span data-ttu-id="fd6c5-116">Ekleme denetimlerini **araç kutusu** bileşik denetim yüzeyine bırakın.</span><span class="sxs-lookup"><span data-stu-id="fd6c5-116">Add controls from the **Toolbox** to the composite control surface.</span></span>  
  
6.  <span data-ttu-id="fd6c5-117">Olay yordamlar, bileşik denetim veya onun bağlı denetimler tarafından başlatılan olayları işlemek için kod yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="fd6c5-117">Place code in event procedures, to handle events raised by the composite control or by its constituent controls.</span></span>  
  
7.  <span data-ttu-id="fd6c5-118">Bileşik denetim için tasarımcı kapatın ve sorulduğunda dosyayı kaydedin.</span><span class="sxs-lookup"><span data-stu-id="fd6c5-118">Close the designer for the composite control, and save the file when you are prompted.</span></span>  
  
8.  <span data-ttu-id="fd6c5-119">Üzerinde **derleme** menüsünde tıklatın **Çözümü Derle**.</span><span class="sxs-lookup"><span data-stu-id="fd6c5-119">On the **Build** menu, click **Build Solution**.</span></span>  
  
     <span data-ttu-id="fd6c5-120">Sırada görünmesini özel denetimler için projenin derlenmesi **araç kutusu**.</span><span class="sxs-lookup"><span data-stu-id="fd6c5-120">The project must be built in order for custom controls to appear in the **Toolbox**.</span></span>  
  
9. <span data-ttu-id="fd6c5-121">Kullanım **DemoControlHost** sekmesinde **araç kutusu** denetiminize örneklerini eklemek için `Form1`.</span><span class="sxs-lookup"><span data-stu-id="fd6c5-121">Use the **DemoControlHost** tab of the **Toolbox** to add instances of your control to `Form1`.</span></span>  
  
### <a name="to-author-a-control-class-library"></a><span data-ttu-id="fd6c5-122">Bir denetim sınıf kitaplığı oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="fd6c5-122">To author a control class library</span></span>  
  
1.  <span data-ttu-id="fd6c5-123">Yeni bir **Windows Denetim Kitaplığı** proje.</span><span class="sxs-lookup"><span data-stu-id="fd6c5-123">Open a new **Windows Control Library** project.</span></span>  
  
     <span data-ttu-id="fd6c5-124">Varsayılan olarak, projeyi bileşik denetim içerir.</span><span class="sxs-lookup"><span data-stu-id="fd6c5-124">By default, the project contains a composite control.</span></span>  
  
2.  <span data-ttu-id="fd6c5-125">Denetimleri ve yukarıdaki yordamda anlatıldığı gibi kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="fd6c5-125">Add controls and code as described in the procedure above.</span></span>  
  
3.  <span data-ttu-id="fd6c5-126">İstemediğiniz değiştirmek ve ayarlamak için sınıflar devralan bir denetim seçin **değiştiriciler** bu denetimin özellik **özel**.</span><span class="sxs-lookup"><span data-stu-id="fd6c5-126">Choose a control you do not want inheriting classes to change, and set the **Modifiers** property of this control to **Private**.</span></span>  
  
4.  <span data-ttu-id="fd6c5-127">DLL oluşturun.</span><span class="sxs-lookup"><span data-stu-id="fd6c5-127">Build the DLL.</span></span>  
  
### <a name="to-inherit-from-a-composite-control-in-a-control-class-library"></a><span data-ttu-id="fd6c5-128">Bileşik Denetim denetim Sınıf Kitaplığı'nda devralınacak</span><span class="sxs-lookup"><span data-stu-id="fd6c5-128">To inherit from a composite control in a control class library</span></span>  
  
1.  <span data-ttu-id="fd6c5-129">Üzerinde **dosya** menüsünde **Ekle** seçip **yeni proje** yeni bir **Windows uygulama** çözüme bir proje.</span><span class="sxs-lookup"><span data-stu-id="fd6c5-129">On the **File** menu, point to **Add** and select **New Project** to add a new **Windows Application** project to the solution.</span></span>  
  
2.  <span data-ttu-id="fd6c5-130">İçinde **Çözüm Gezgini**, sağ **başvuruları** yeni klasör projesini ve ardından **Başvuru Ekle** açmak için **Add Reference**iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="fd6c5-130">In **Solution Explorer**, right-click the **References** folder for the new project and choose **Add Reference** to open the **Add Reference** dialog box.</span></span>  
  
3.  <span data-ttu-id="fd6c5-131">Seçin **projeleri** sekmesini ve Denetim Kitaplığı projenize çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="fd6c5-131">Select the **Projects** tab and double-click your control library project.</span></span>  
  
4.  <span data-ttu-id="fd6c5-132">Üzerinde **derleme** menüsünde tıklatın **Çözümü Derle**.</span><span class="sxs-lookup"><span data-stu-id="fd6c5-132">On the **Build** menu, click **Build Solution**.</span></span>  
  
5.  <span data-ttu-id="fd6c5-133">İçinde **Çözüm Gezgini**, Denetim Kitaplığı projenize sağ tıklayıp **Yeni Öğe Ekle** kısayol menüsünden.</span><span class="sxs-lookup"><span data-stu-id="fd6c5-133">In **Solution Explorer**, right-click your control library project and select **Add New Item** from the shortcut menu.</span></span>  
  
6.  <span data-ttu-id="fd6c5-134">Seçin **devralınan kullanıcı denetimi** şablondan **Yeni Öğe Ekle** iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="fd6c5-134">Select the **Inherited User Control** template from the **Add New Item** dialog box.</span></span>  
  
7.  <span data-ttu-id="fd6c5-135">İçinde **devralma Seçici** iletişim kutusunda, istediğiniz devralınacak denetimi çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="fd6c5-135">In the **Inheritance Picker** dialog box, double-click the control you want to inherit from.</span></span>  
  
     <span data-ttu-id="fd6c5-136">Yeni bir denetim projenize eklenir.</span><span class="sxs-lookup"><span data-stu-id="fd6c5-136">A new control is added to your project.</span></span>  
  
8.  <span data-ttu-id="fd6c5-137">Yeni denetim için görsel tasarımcı açın ve ek bağlı denetimler ekleme.</span><span class="sxs-lookup"><span data-stu-id="fd6c5-137">Open the visual designer for the new control and add additional constituent controls.</span></span>  
  
     <span data-ttu-id="fd6c5-138">Bileşik Denetim DLL dosyanız içinde öğesinden devralınan bağlı denetimler görebilir ve denetimlerin özelliklerini değiştirebilir, **değiştiriciler** özelliği **genel**.</span><span class="sxs-lookup"><span data-stu-id="fd6c5-138">You can see the constituent controls that were inherited from the composite control in your DLL, and you can alter the properties of controls whose **Modifiers** property is **Public**.</span></span> <span data-ttu-id="fd6c5-139">Denetimin özelliklerini değiştiremezsiniz, **değiştiriciler** özelliği **özel**.</span><span class="sxs-lookup"><span data-stu-id="fd6c5-139">You cannot change the properties of the control whose **Modifiers** property is **Private**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd6c5-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fd6c5-140">See also</span></span>
- [<span data-ttu-id="fd6c5-141">İzlenecek yol: Visual Basic ile bileşik denetim yazma</span><span class="sxs-lookup"><span data-stu-id="fd6c5-141">Walkthrough: Authoring a Composite Control with Visual Basic</span></span>](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-basic.md)
- [<span data-ttu-id="fd6c5-142">İzlenecek yol: Visual C# ile bileşik denetim yazma</span><span class="sxs-lookup"><span data-stu-id="fd6c5-142">Walkthrough: Authoring a Composite Control with Visual C#</span></span>](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-csharp.md)
- [<span data-ttu-id="fd6c5-143">İzlenecek yol: Visual Basic ile Windows Forms Denetimi'nden devralma</span><span class="sxs-lookup"><span data-stu-id="fd6c5-143">Walkthrough: Inheriting from a Windows Forms Control with Visual Basic</span></span>](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic.md)
- [<span data-ttu-id="fd6c5-144">İzlenecek yol: Visual C# ile Windows Forms Denetimi'nden devralma</span><span class="sxs-lookup"><span data-stu-id="fd6c5-144">Walkthrough: Inheriting from a Windows Forms Control with Visual C#</span></span>](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)
- [<span data-ttu-id="fd6c5-145">Denetim Türü Önerileri</span><span class="sxs-lookup"><span data-stu-id="fd6c5-145">Control Type Recommendations</span></span>](../../../../docs/framework/winforms/controls/control-type-recommendations.md)
- [<span data-ttu-id="fd6c5-146">Nasıl yapılır: Windows Forms için yazar denetimleri</span><span class="sxs-lookup"><span data-stu-id="fd6c5-146">How to: Author Controls for Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-author-controls-for-windows-forms.md)
- [<span data-ttu-id="fd6c5-147">Özel Denetim Çeşitleri</span><span class="sxs-lookup"><span data-stu-id="fd6c5-147">Varieties of Custom Controls</span></span>](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)
