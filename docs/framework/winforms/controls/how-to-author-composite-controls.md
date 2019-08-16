---
title: 'Nasıl yapılır: Bileşik Denetimler Yazma'
ms.date: 03/30/2017
helpviewer_keywords:
- UserControl class [Windows Forms], creating composite controls
- user controls [Windows Forms], creating
- user controls [Windows Forms], inheriting from
- composite controls [Windows Forms], creating
ms.assetid: 79c9cf05-5ab6-4a18-886d-88a64748b098
ms.openlocfilehash: 7b0ee8efa62175e2ced2a810ca6dd76e8adc103b
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039890"
---
# <a name="how-to-author-composite-controls"></a><span data-ttu-id="cd1c1-102">Nasıl yapılır: Bileşik Denetimler Yazma</span><span class="sxs-lookup"><span data-stu-id="cd1c1-102">How to: Author Composite Controls</span></span>

<span data-ttu-id="cd1c1-103">Bileşik denetimler birçok şekilde çalıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="cd1c1-103">Composite controls can be employed in many ways.</span></span> <span data-ttu-id="cd1c1-104">Bunları bir Windows masaüstü uygulaması projesinin parçası olarak yazabilir ve yalnızca projedeki formlarda kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cd1c1-104">You can author them as part of a Windows desktop application project, and use them only on forms in the project.</span></span> <span data-ttu-id="cd1c1-105">Ya da bunları bir Windows denetim kitaplığı projesinde yazabilir, projeyi bir derlemede derleyebilir ve diğer projelerdeki denetimleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cd1c1-105">Or you can author them in a Windows Control Library project, compile the project into an assembly, and use the controls in other projects.</span></span> <span data-ttu-id="cd1c1-106">Hatta onlardan devralabilir ve Görsel devralmayı kullanarak özel amaçlar için bunları hızlıca özelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cd1c1-106">You can even inherit from them and use visual inheritance to customize them quickly for special purposes.</span></span>

> [!NOTE]
> <span data-ttu-id="cd1c1-107">Web Forms üzerinde kullanmak için bir bileşik denetim yazmak istiyorsanız bkz. [özel ASP.NET Server denetimleri geliştirme](https://docs.microsoft.com/previous-versions/aspnet/zt27tfhy(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="cd1c1-107">If you want to author a composite control to use on Web Forms, see [Developing Custom ASP.NET Server Controls](https://docs.microsoft.com/previous-versions/aspnet/zt27tfhy(v=vs.100)).</span></span>

## <a name="to-author-a-composite-control"></a><span data-ttu-id="cd1c1-108">Bileşik denetim yazmak için</span><span class="sxs-lookup"><span data-stu-id="cd1c1-108">To author a composite control</span></span>

1. <span data-ttu-id="cd1c1-109">Visual Studio 'da adlı `DemoControlHost`yeni bir **Windows uygulaması** projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="cd1c1-109">In Visual Studio, create a new **Windows Application** project called `DemoControlHost`.</span></span>

2. <span data-ttu-id="cd1c1-110">**Proje** menüsünde **Kullanıcı denetimi Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="cd1c1-110">On the **Project** menu, click **Add User Control**.</span></span>

3. <span data-ttu-id="cd1c1-111">**Yeni öğe Ekle** iletişim kutusunda, bileşik denetimin sahip olmasını istediğiniz adı sınıf dosyasına (. vb veya. cs dosyası) verin.</span><span class="sxs-lookup"><span data-stu-id="cd1c1-111">In the **Add New Item** dialog box, give the class file (.vb or .cs file) the name you want the composite control to have.</span></span>

4. <span data-ttu-id="cd1c1-112">Bileşik denetimin sınıf dosyasını oluşturmak için **Ekle** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="cd1c1-112">Select the **Add** button to create the class file for the composite control.</span></span>

5. <span data-ttu-id="cd1c1-113">**Araç kutusundan** bileşik denetim yüzeyine denetimler ekleyin.</span><span class="sxs-lookup"><span data-stu-id="cd1c1-113">Add controls from the **Toolbox** to the composite control surface.</span></span>

6. <span data-ttu-id="cd1c1-114">Bileşik denetim veya bileşen denetimleri tarafından oluşturulan olayları işlemek için olay yordamlarına kod koyun.</span><span class="sxs-lookup"><span data-stu-id="cd1c1-114">Place code in event procedures, to handle events raised by the composite control or by its constituent controls.</span></span>

7. <span data-ttu-id="cd1c1-115">Bileşik denetim için tasarımcıyı kapatın ve istendiğinde dosyayı kaydedin.</span><span class="sxs-lookup"><span data-stu-id="cd1c1-115">Close the designer for the composite control, and save the file when you are prompted.</span></span>

8. <span data-ttu-id="cd1c1-116">Üzerinde **derleme** menüsünde tıklatın **Çözümü Derle**.</span><span class="sxs-lookup"><span data-stu-id="cd1c1-116">On the **Build** menu, click **Build Solution**.</span></span>

     <span data-ttu-id="cd1c1-117">Özel denetimlerin **araç kutusunda**görünmesi için projenin oluşturulması gerekir.</span><span class="sxs-lookup"><span data-stu-id="cd1c1-117">The project must be built in order for custom controls to appear in the **Toolbox**.</span></span>

9. <span data-ttu-id="cd1c1-118">Denetiminizin örneklerini öğesine `Form1`eklemek Için **araç kutusunun** **DemoControlHost** sekmesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="cd1c1-118">Use the **DemoControlHost** tab of the **Toolbox** to add instances of your control to `Form1`.</span></span>

## <a name="to-author-a-control-class-library"></a><span data-ttu-id="cd1c1-119">Bir denetim sınıfı kitaplığı yazmak için</span><span class="sxs-lookup"><span data-stu-id="cd1c1-119">To author a control class library</span></span>

1. <span data-ttu-id="cd1c1-120">Yeni bir **Windows Denetim Kitaplığı** projesi açın.</span><span class="sxs-lookup"><span data-stu-id="cd1c1-120">Open a new **Windows Control Library** project.</span></span>

     <span data-ttu-id="cd1c1-121">Varsayılan olarak, proje bir bileşik denetim içerir.</span><span class="sxs-lookup"><span data-stu-id="cd1c1-121">By default, the project contains a composite control.</span></span>

2. <span data-ttu-id="cd1c1-122">Yukarıdaki yordamda açıklandığı gibi denetimleri ve kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="cd1c1-122">Add controls and code as described in the procedure above.</span></span>

3. <span data-ttu-id="cd1c1-123">Sınıfların değiştirilmesini istemediğiniz bir denetim seçin ve bu denetimin **değiştiriciler** özelliğini **özel**olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="cd1c1-123">Choose a control you do not want inheriting classes to change, and set the **Modifiers** property of this control to **Private**.</span></span>

4. <span data-ttu-id="cd1c1-124">DLL 'yi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="cd1c1-124">Build the DLL.</span></span>

## <a name="to-inherit-from-a-composite-control-in-a-control-class-library"></a><span data-ttu-id="cd1c1-125">Bir denetim sınıfı kitaplığındaki bileşik denetimden devralması için</span><span class="sxs-lookup"><span data-stu-id="cd1c1-125">To inherit from a composite control in a control class library</span></span>

1. <span data-ttu-id="cd1c1-126">Çözüme yeni bir **Windows uygulaması** projesi eklemek için **Dosya** menüsünde, **Ekle** ' ye gelin ve **Yeni proje** ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="cd1c1-126">On the **File** menu, point to **Add** and select **New Project** to add a new **Windows Application** project to the solution.</span></span>

2. <span data-ttu-id="cd1c1-127">**Çözüm Gezgini**' de, yeni proje için **Başvurular** klasörüne sağ tıklayın ve başvuru Ekle Iletişim kutusunu açmak için **Başvuru Ekle** ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="cd1c1-127">In **Solution Explorer**, right-click the **References** folder for the new project and choose **Add Reference** to open the **Add Reference** dialog box.</span></span>

3. <span data-ttu-id="cd1c1-128">**Projeler** sekmesini seçin ve denetim kitaplığı projenize çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="cd1c1-128">Select the **Projects** tab and double-click your control library project.</span></span>

4. <span data-ttu-id="cd1c1-129">Üzerinde **derleme** menüsünde tıklatın **Çözümü Derle**.</span><span class="sxs-lookup"><span data-stu-id="cd1c1-129">On the **Build** menu, click **Build Solution**.</span></span>

5. <span data-ttu-id="cd1c1-130">**Çözüm Gezgini**, denetim kitaplığı projenize sağ tıklayıp kısayol menüsünden **Yeni öğe Ekle** ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="cd1c1-130">In **Solution Explorer**, right-click your control library project and select **Add New Item** from the shortcut menu.</span></span>

6. <span data-ttu-id="cd1c1-131">**Yeni öğe Ekle** Iletişim kutusundan **devralınan Kullanıcı denetimi** şablonunu seçin.</span><span class="sxs-lookup"><span data-stu-id="cd1c1-131">Select the **Inherited User Control** template from the **Add New Item** dialog box.</span></span>

7. <span data-ttu-id="cd1c1-132">**Devralma Seçicisi** iletişim kutusunda, devralmak istediğiniz denetime çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="cd1c1-132">In the **Inheritance Picker** dialog box, double-click the control you want to inherit from.</span></span>

     <span data-ttu-id="cd1c1-133">Projenize yeni bir denetim eklenir.</span><span class="sxs-lookup"><span data-stu-id="cd1c1-133">A new control is added to your project.</span></span>

8. <span data-ttu-id="cd1c1-134">Yeni denetim için görsel tasarımcıyı açın ve ek bileşen denetimleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="cd1c1-134">Open the visual designer for the new control and add additional constituent controls.</span></span>

     <span data-ttu-id="cd1c1-135">DLL 'inizdeki bileşik denetimden devralınan yapısal denetimleri görebilir ve **değiştiriciler** özelliği **ortak**olan denetimlerin özelliklerini değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cd1c1-135">You can see the constituent controls that were inherited from the composite control in your DLL, and you can alter the properties of controls whose **Modifiers** property is **Public**.</span></span> <span data-ttu-id="cd1c1-136">**Değiştiriciler** özelliği **özel**olan denetimin özelliklerini değiştiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="cd1c1-136">You cannot change the properties of the control whose **Modifiers** property is **Private**.</span></span>

## <a name="see-also"></a><span data-ttu-id="cd1c1-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cd1c1-137">See also</span></span>

- [<span data-ttu-id="cd1c1-138">İzlenecek yol: Visual Basic ile bileşik denetim yazma</span><span class="sxs-lookup"><span data-stu-id="cd1c1-138">Walkthrough: Authoring a Composite Control with Visual Basic</span></span>](walkthrough-authoring-a-composite-control-with-visual-basic.md)
- [<span data-ttu-id="cd1c1-139">İzlenecek yol: Visual ile bileşik denetim yazmaC#</span><span class="sxs-lookup"><span data-stu-id="cd1c1-139">Walkthrough: Authoring a Composite Control with Visual C#</span></span>](walkthrough-authoring-a-composite-control-with-visual-csharp.md)
- [<span data-ttu-id="cd1c1-140">İzlenecek yol: Visual Basic ile Windows Forms denetiminden devralma</span><span class="sxs-lookup"><span data-stu-id="cd1c1-140">Walkthrough: Inheriting from a Windows Forms Control with Visual Basic</span></span>](walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic.md)
- [<span data-ttu-id="cd1c1-141">İzlenecek yol: Görsel ile Windows Forms denetiminden devralmaC#</span><span class="sxs-lookup"><span data-stu-id="cd1c1-141">Walkthrough: Inheriting from a Windows Forms Control with Visual C#</span></span>](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)
- [<span data-ttu-id="cd1c1-142">Denetim Türü Önerileri</span><span class="sxs-lookup"><span data-stu-id="cd1c1-142">Control Type Recommendations</span></span>](control-type-recommendations.md)
- [<span data-ttu-id="cd1c1-143">Nasıl yapılır: Windows Forms için yazar denetimleri</span><span class="sxs-lookup"><span data-stu-id="cd1c1-143">How to: Author Controls for Windows Forms</span></span>](how-to-author-controls-for-windows-forms.md)
- [<span data-ttu-id="cd1c1-144">Özel Denetim Çeşitleri</span><span class="sxs-lookup"><span data-stu-id="cd1c1-144">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
