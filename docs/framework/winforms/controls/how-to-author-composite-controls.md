---
title: 'Nasıl yapılır: Bileşik Denetimler Yazma'
ms.date: 03/30/2017
helpviewer_keywords:
- UserControl class [Windows Forms], creating composite controls
- user controls [Windows Forms], creating
- user controls [Windows Forms], inheriting from
- composite controls [Windows Forms], creating
ms.assetid: 79c9cf05-5ab6-4a18-886d-88a64748b098
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 42ea424507b89576df8099fd4849dd2665135a55
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459428"
---
# <a name="how-to-author-composite-controls"></a><span data-ttu-id="17f6c-102">Nasıl yapılır: bileşik denetimler yazma</span><span class="sxs-lookup"><span data-stu-id="17f6c-102">How to: Author composite controls</span></span>

<span data-ttu-id="17f6c-103">Bileşik denetimler birçok şekilde çalıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="17f6c-103">Composite controls can be employed in many ways.</span></span> <span data-ttu-id="17f6c-104">Bunları bir Windows masaüstü uygulaması projesinin parçası olarak yazabilir ve yalnızca projedeki formlarda kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="17f6c-104">You can author them as part of a Windows desktop application project, and use them only on forms in the project.</span></span> <span data-ttu-id="17f6c-105">Ya da bunları bir Windows denetim kitaplığı projesinde yazabilir, projeyi bir derlemede derleyebilir ve diğer projelerdeki denetimleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="17f6c-105">Or you can author them in a Windows Control Library project, compile the project into an assembly, and use the controls in other projects.</span></span> <span data-ttu-id="17f6c-106">Hatta onlardan devralabilir ve Görsel devralmayı kullanarak özel amaçlar için bunları hızlıca özelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="17f6c-106">You can even inherit from them and use visual inheritance to customize them quickly for special purposes.</span></span>

## <a name="to-author-a-composite-control"></a><span data-ttu-id="17f6c-107">Bileşik denetim yazmak için</span><span class="sxs-lookup"><span data-stu-id="17f6c-107">To author a composite control</span></span>

1. <span data-ttu-id="17f6c-108">Visual Studio 'da yeni bir **Windows uygulaması** projesi oluşturun ve bunu **DemoControlHost**olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="17f6c-108">In Visual Studio, create a new **Windows Application** project, and name it **DemoControlHost**.</span></span>

2. <span data-ttu-id="17f6c-109">**Proje** menüsünde **Kullanıcı denetimi Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="17f6c-109">On the **Project** menu, click **Add User Control**.</span></span>

3. <span data-ttu-id="17f6c-110">**Yeni öğe Ekle** iletişim kutusunda, bileşik denetimin sahip olmasını istediğiniz adı sınıf dosyasına (. vb veya. cs dosyası) verin.</span><span class="sxs-lookup"><span data-stu-id="17f6c-110">In the **Add New Item** dialog box, give the class file (.vb or .cs file) the name you want the composite control to have.</span></span>

4. <span data-ttu-id="17f6c-111">Bileşik denetimin sınıf dosyasını oluşturmak için **Ekle** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="17f6c-111">Select the **Add** button to create the class file for the composite control.</span></span>

5. <span data-ttu-id="17f6c-112">**Araç kutusundan** bileşik denetim yüzeyine denetimler ekleyin.</span><span class="sxs-lookup"><span data-stu-id="17f6c-112">Add controls from the **Toolbox** to the composite control surface.</span></span>

6. <span data-ttu-id="17f6c-113">Bileşik denetim veya bileşen denetimleri tarafından oluşturulan olayları işlemek için olay yordamlarına kod koyun.</span><span class="sxs-lookup"><span data-stu-id="17f6c-113">Place code in event procedures, to handle events raised by the composite control or by its constituent controls.</span></span>

7. <span data-ttu-id="17f6c-114">Bileşik denetim için tasarımcıyı kapatın ve istendiğinde dosyayı kaydedin.</span><span class="sxs-lookup"><span data-stu-id="17f6c-114">Close the designer for the composite control, and save the file when you are prompted.</span></span>

8. <span data-ttu-id="17f6c-115">**Yapı** menüsünde **çözüm oluştur**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="17f6c-115">On the **Build** menu, click **Build Solution**.</span></span>

     <span data-ttu-id="17f6c-116">Özel denetimlerin **araç kutusunda**görünmesi için projenin oluşturulması gerekir.</span><span class="sxs-lookup"><span data-stu-id="17f6c-116">The project must be built in order for custom controls to appear in the **Toolbox**.</span></span>

9. <span data-ttu-id="17f6c-117">`Form1`' e denetim örneklerini eklemek için **araç kutusunun** **DemoControlHost** sekmesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="17f6c-117">Use the **DemoControlHost** tab of the **Toolbox** to add instances of your control to `Form1`.</span></span>

## <a name="to-author-a-control-class-library"></a><span data-ttu-id="17f6c-118">Bir denetim sınıfı kitaplığı yazmak için</span><span class="sxs-lookup"><span data-stu-id="17f6c-118">To author a control class library</span></span>

1. <span data-ttu-id="17f6c-119">Yeni bir **Windows Denetim Kitaplığı** projesi açın.</span><span class="sxs-lookup"><span data-stu-id="17f6c-119">Open a new **Windows Control Library** project.</span></span>

     <span data-ttu-id="17f6c-120">Varsayılan olarak, proje bir bileşik denetim içerir.</span><span class="sxs-lookup"><span data-stu-id="17f6c-120">By default, the project contains a composite control.</span></span>

2. <span data-ttu-id="17f6c-121">Yukarıdaki yordamda açıklandığı gibi denetimleri ve kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="17f6c-121">Add controls and code as described in the procedure above.</span></span>

3. <span data-ttu-id="17f6c-122">Sınıfların değiştirilmesini istemediğiniz bir denetim seçin ve bu denetimin **değiştiriciler** özelliğini **özel**olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="17f6c-122">Choose a control you do not want inheriting classes to change, and set the **Modifiers** property of this control to **Private**.</span></span>

4. <span data-ttu-id="17f6c-123">DLL 'yi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="17f6c-123">Build the DLL.</span></span>

## <a name="to-inherit-from-a-composite-control-in-a-control-class-library"></a><span data-ttu-id="17f6c-124">Bir denetim sınıfı kitaplığındaki bileşik denetimden devralması için</span><span class="sxs-lookup"><span data-stu-id="17f6c-124">To inherit from a composite control in a control class library</span></span>

1. <span data-ttu-id="17f6c-125">Çözüme yeni bir **Windows uygulaması** projesi eklemek için **Dosya** menüsünde, **Ekle** ' ye gelin ve **Yeni proje** ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="17f6c-125">On the **File** menu, point to **Add** and select **New Project** to add a new **Windows Application** project to the solution.</span></span>

2. <span data-ttu-id="17f6c-126">**Çözüm Gezgini**' de, yeni proje için **Başvurular** klasörüne sağ tıklayın **ve başvuru Ekle Iletişim kutusunu** açmak için **Başvuru Ekle** ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="17f6c-126">In **Solution Explorer**, right-click the **References** folder for the new project and choose **Add Reference** to open the **Add Reference** dialog box.</span></span>

3. <span data-ttu-id="17f6c-127">**Projeler** sekmesini seçin ve denetim kitaplığı projenize çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="17f6c-127">Select the **Projects** tab and double-click your control library project.</span></span>

4. <span data-ttu-id="17f6c-128">**Yapı** menüsünde **çözüm oluştur**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="17f6c-128">On the **Build** menu, click **Build Solution**.</span></span>

5. <span data-ttu-id="17f6c-129">**Çözüm Gezgini**, denetim kitaplığı projenize sağ tıklayıp kısayol menüsünden **Yeni öğe Ekle** ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="17f6c-129">In **Solution Explorer**, right-click your control library project and select **Add New Item** from the shortcut menu.</span></span>

6. <span data-ttu-id="17f6c-130">**Yeni öğe Ekle** Iletişim kutusundan **devralınan Kullanıcı denetimi** şablonunu seçin.</span><span class="sxs-lookup"><span data-stu-id="17f6c-130">Select the **Inherited User Control** template from the **Add New Item** dialog box.</span></span>

7. <span data-ttu-id="17f6c-131">**Devralma Seçicisi** iletişim kutusunda, devralmak istediğiniz denetime çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="17f6c-131">In the **Inheritance Picker** dialog box, double-click the control you want to inherit from.</span></span>

     <span data-ttu-id="17f6c-132">Projenize yeni bir denetim eklenir.</span><span class="sxs-lookup"><span data-stu-id="17f6c-132">A new control is added to your project.</span></span>

8. <span data-ttu-id="17f6c-133">Yeni denetim için görsel tasarımcıyı açın ve ek bileşen denetimleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="17f6c-133">Open the visual designer for the new control and add additional constituent controls.</span></span>

     <span data-ttu-id="17f6c-134">DLL 'inizdeki bileşik denetimden devralınan yapısal denetimleri görebilir ve **değiştiriciler** özelliği **ortak**olan denetimlerin özelliklerini değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="17f6c-134">You can see the constituent controls that were inherited from the composite control in your DLL, and you can alter the properties of controls whose **Modifiers** property is **Public**.</span></span> <span data-ttu-id="17f6c-135">**Değiştiriciler** özelliği **özel**olan denetimin özelliklerini değiştiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="17f6c-135">You cannot change the properties of the control whose **Modifiers** property is **Private**.</span></span>

## <a name="see-also"></a><span data-ttu-id="17f6c-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="17f6c-136">See also</span></span>

- [<span data-ttu-id="17f6c-137">İzlenecek yol: bileşik denetim yazma</span><span class="sxs-lookup"><span data-stu-id="17f6c-137">Walkthrough: Authoring a Composite Control</span></span>](walkthrough-authoring-a-composite-control-with-visual-csharp.md)
- [<span data-ttu-id="17f6c-138">İzlenecek yol: Windows Forms denetiminden devralma</span><span class="sxs-lookup"><span data-stu-id="17f6c-138">Walkthrough: Inheriting from a Windows Forms Control</span></span>](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)
- [<span data-ttu-id="17f6c-139">Denetim Türü Önerileri</span><span class="sxs-lookup"><span data-stu-id="17f6c-139">Control Type Recommendations</span></span>](control-type-recommendations.md)
- [<span data-ttu-id="17f6c-140">Nasıl yapılır: Windows Forms için Denetimler Yazma</span><span class="sxs-lookup"><span data-stu-id="17f6c-140">How to: Author Controls for Windows Forms</span></span>](how-to-author-controls-for-windows-forms.md)
- [<span data-ttu-id="17f6c-141">Özel Denetim Çeşitleri</span><span class="sxs-lookup"><span data-stu-id="17f6c-141">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
