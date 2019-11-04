---
title: 'Nasıl yapılır: Windows Formları için Denetimler Yazma'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], creating
- UserControl class [Windows Forms], Windows Forms
- custom controls [Windows Forms], creating
ms.assetid: 7570e982-545b-4c3a-a7c7-55581d313400
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3776e47191d9b10431acbb9a2a7257996e531ba8
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459417"
---
# <a name="how-to-author-controls-for-windows-forms"></a><span data-ttu-id="63ed0-102">Nasıl yapılır: Windows Forms denetimlerini yazma</span><span class="sxs-lookup"><span data-stu-id="63ed0-102">How to: Author controls for Windows Forms</span></span>

<span data-ttu-id="63ed0-103">Denetim, Kullanıcı ve program arasındaki grafik bağlantısını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="63ed0-103">A control represents a graphical link between the user and the program.</span></span> <span data-ttu-id="63ed0-104">Bir denetim, verileri sağlayabilir veya işleyebilir, Kullanıcı girişi kabul edebilir, olaylara yanıt verebilir veya Kullanıcı ve uygulamayı bağlayan herhangi bir sayıda diğer işlevi gerçekleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="63ed0-104">A control can provide or process data, accept user input, respond to events, or perform any number of other functions that connect the user and the application.</span></span> <span data-ttu-id="63ed0-105">Bir denetim temelde grafik arabirimi olan bir bileşen olduğundan, bir bileşenin yaptığı ve Kullanıcı etkileşimi sağlayan herhangi bir işleve de sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="63ed0-105">Because a control is essentially a component with a graphical interface, it can serve any function that a component does, as well as provide user interaction.</span></span> <span data-ttu-id="63ed0-106">Denetimler, belirli amaçlarla kullanılmak üzere oluşturulur ve yazma denetimleri yalnızca başka bir programlama görevi olur.</span><span class="sxs-lookup"><span data-stu-id="63ed0-106">Controls are created to serve specific purposes, and authoring controls is just another programming task.</span></span> <span data-ttu-id="63ed0-107">Bu şekilde, aşağıdaki adımlar denetim yazma sürecine genel bir bakış temsil eder.</span><span class="sxs-lookup"><span data-stu-id="63ed0-107">With that in mind, the following steps represent an overview of the control authoring process.</span></span> <span data-ttu-id="63ed0-108">Bağlantılar, bireysel adımlarla ilgili ek bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="63ed0-108">Links provide additional information on the individual steps.</span></span>

## <a name="to-author-a-control"></a><span data-ttu-id="63ed0-109">Bir denetimi yazmak için</span><span class="sxs-lookup"><span data-stu-id="63ed0-109">To author a control</span></span>

1. <span data-ttu-id="63ed0-110">Denetiminizin ne yapmak istediğinizi veya uygulamanızda hangi parçayı oynaymasını istediğinizi saptayın.</span><span class="sxs-lookup"><span data-stu-id="63ed0-110">Determine what you want your control to accomplish, or what part it will play in your application.</span></span> <span data-ttu-id="63ed0-111">Göz önünde bulundurulması gereken etkenler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="63ed0-111">Factors to consider are:</span></span>

    - <span data-ttu-id="63ed0-112">Ne tür bir grafik arabirimine ihtiyacınız var?</span><span class="sxs-lookup"><span data-stu-id="63ed0-112">What kind of graphical interface do you need?</span></span>

    - <span data-ttu-id="63ed0-113">Bu denetim hangi kullanıcı etkileşimlerini işleyecek?</span><span class="sxs-lookup"><span data-stu-id="63ed0-113">What specific user interactions will this control handle?</span></span>

    - <span data-ttu-id="63ed0-114">Var olan tüm denetimler için gerekli olan işlevsellikdir?</span><span class="sxs-lookup"><span data-stu-id="63ed0-114">Is the functionality you need provided by any existing controls?</span></span>

    - <span data-ttu-id="63ed0-115">Birkaç Windows Forms denetimini birleştirerek ihtiyacınız olan işlevleri alabilir misiniz?</span><span class="sxs-lookup"><span data-stu-id="63ed0-115">Can you get the functionality you need by combining several Windows Forms controls?</span></span>

2. <span data-ttu-id="63ed0-116">Denetiminiz için bir nesne modeline ihtiyacınız varsa, işlevin nesne modeli boyunca nasıl dağıtılacağını ve denetim ile tüm alt nesneler arasındaki işlevselliği nasıl bölmeyeceğini saptayın.</span><span class="sxs-lookup"><span data-stu-id="63ed0-116">If you need an object model for your control, determine how functionality will be distributed throughout the object model, and divide up functionality between the control and any subobjects.</span></span> <span data-ttu-id="63ed0-117">Bir nesne modeli, karmaşık bir denetim planlıyor veya çeşitli işlevler eklemek istiyorsanız yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="63ed0-117">An object model may be useful if you are planning a complex control, or want to incorporate several functionalities.</span></span>

3. <span data-ttu-id="63ed0-118">İhtiyacınız olan denetimin türünü (örneğin, Kullanıcı denetimi, özel denetim, devralınan Windows Forms denetimi) saptayın.</span><span class="sxs-lookup"><span data-stu-id="63ed0-118">Determine the type of control (for example, user control, custom control, inherited Windows Forms control) you need.</span></span> <span data-ttu-id="63ed0-119">Ayrıntılar için bkz. [Denetim türü önerileri](control-type-recommendations.md) ve [Özel denetimlerin varielikler](varieties-of-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="63ed0-119">For details, see [Control Type Recommendations](control-type-recommendations.md) and [Varieties of Custom Controls](varieties-of-custom-controls.md).</span></span>

4. <span data-ttu-id="63ed0-120">İşlevselliği, denetimin ve alt nesnelerin ya da yan yapılarının özellikleri, yöntemleri ve olayları olarak Express ve uygun erişim düzeyleri (örneğin, genel, korumalı vb.) atayın.</span><span class="sxs-lookup"><span data-stu-id="63ed0-120">Express functionality as properties, methods, and events of the control and its subobjects or subsidiary structures, and assign appropriate access levels (for example, public, protected, and so on).</span></span>

5. <span data-ttu-id="63ed0-121">Denetiminiz için özel boyama gerekiyorsa, bunun için kod ekleyin.</span><span class="sxs-lookup"><span data-stu-id="63ed0-121">If you need custom painting for your control, add code for it.</span></span> <span data-ttu-id="63ed0-122">Ayrıntılar için bkz. [özel denetim boyama ve işleme](custom-control-painting-and-rendering.md).</span><span class="sxs-lookup"><span data-stu-id="63ed0-122">For details, see [Custom Control Painting and Rendering](custom-control-painting-and-rendering.md).</span></span>

6. <span data-ttu-id="63ed0-123">Denetiminiz <xref:System.Windows.Forms.UserControl>devralırsa, çalışma zamanı davranışını denetim projesini oluşturup **UserControl Test kapsayıcısında**çalıştırarak test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="63ed0-123">If your control inherits from <xref:System.Windows.Forms.UserControl>, you can test its runtime behavior by building the control project and running it in the **UserControl Test Container**.</span></span> <span data-ttu-id="63ed0-124">Daha fazla bilgi için bkz. [nasıl yapılır: bir UserControl 'un çalışma zamanı davranışını test etme](how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span><span class="sxs-lookup"><span data-stu-id="63ed0-124">For more information, see [How to: Test the Run-Time Behavior of a UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>

7. <span data-ttu-id="63ed0-125">Ayrıca, Windows uygulaması gibi yeni bir proje oluşturarak ve bir kapsayıcıya yerleştirerek denetiminizi test edebilir ve hatalarını ayıklayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="63ed0-125">You can also test and debug your control by creating a new project, such as a Windows Application, and placing it into a container.</span></span> <span data-ttu-id="63ed0-126">Bu işlem, [Izlenecek yol: Birleşik denetim yazma bir](walkthrough-authoring-a-composite-control-with-visual-csharp.md)parçası olarak gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="63ed0-126">This process is demonstrated as part of [Walkthrough: Authoring a Composite Control](walkthrough-authoring-a-composite-control-with-visual-csharp.md).</span></span>

8. <span data-ttu-id="63ed0-127">Her bir özelliği eklerken, yeni işlevselliği uygulamak için test projenize özellikler ekleyin.</span><span class="sxs-lookup"><span data-stu-id="63ed0-127">As you add each feature, add features to your test project to exercise the new functionality.</span></span>

9. <span data-ttu-id="63ed0-128">, Tasarımı iyileştirerek tekrarlayın.</span><span class="sxs-lookup"><span data-stu-id="63ed0-128">Repeat, refining the design.</span></span>

10. <span data-ttu-id="63ed0-129">Denetiminizi paketleyin ve dağıtın.</span><span class="sxs-lookup"><span data-stu-id="63ed0-129">Package and deploy your control.</span></span> <span data-ttu-id="63ed0-130">Ayrıntılar için bkz. [Visual Studio 'da dağıtıma ilk bakış](/visualstudio/deployment/deploying-applications-services-and-components).</span><span class="sxs-lookup"><span data-stu-id="63ed0-130">For details, see [First look at deployment in Visual Studio](/visualstudio/deployment/deploying-applications-services-and-components).</span></span>

## <a name="see-also"></a><span data-ttu-id="63ed0-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="63ed0-131">See also</span></span>

- [<span data-ttu-id="63ed0-132">Nasıl yapılır: UserControl Sınıfından Devralma</span><span class="sxs-lookup"><span data-stu-id="63ed0-132">How to: Inherit from the UserControl Class</span></span>](how-to-inherit-from-the-usercontrol-class.md)
- [<span data-ttu-id="63ed0-133">Nasıl yapılır: Denetim Sınıfından Devralma</span><span class="sxs-lookup"><span data-stu-id="63ed0-133">How to: Inherit from the Control Class</span></span>](how-to-inherit-from-the-control-class.md)
- [<span data-ttu-id="63ed0-134">Nasıl yapılır: Mevcut Windows Forms Denetimlerinden Devralma</span><span class="sxs-lookup"><span data-stu-id="63ed0-134">How to: Inherit from Existing Windows Forms Controls</span></span>](how-to-inherit-from-existing-windows-forms-controls.md)
- [<span data-ttu-id="63ed0-135">Nasıl yapılır: Bir UserControl Denetiminin Çalışma Zamanı Davranışını Sınama</span><span class="sxs-lookup"><span data-stu-id="63ed0-135">How to: Test the Run-Time Behavior of a UserControl</span></span>](how-to-test-the-run-time-behavior-of-a-usercontrol.md)
- [<span data-ttu-id="63ed0-136">Özel Denetim Çeşitleri</span><span class="sxs-lookup"><span data-stu-id="63ed0-136">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
