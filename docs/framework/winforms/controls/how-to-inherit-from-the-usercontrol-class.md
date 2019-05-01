---
title: 'Nasıl yapılır: UserControl Sınıfından Devralma'
ms.date: 03/30/2017
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- UserControl class [Windows Forms], inheriting from
- user controls [Windows Forms], creating
- composite controls [Windows Forms], creating
ms.assetid: 67713625-e2e4-4f6a-bce7-0855ee5043d9
ms.openlocfilehash: 5e9bdb6d6628b1c696b7944dc0ea1f4c974c8172
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61941134"
---
# <a name="how-to-inherit-from-the-usercontrol-class"></a><span data-ttu-id="c2d11-102">Nasıl yapılır: UserControl Sınıfından Devralma</span><span class="sxs-lookup"><span data-stu-id="c2d11-102">How to: Inherit from the UserControl Class</span></span>
<span data-ttu-id="c2d11-103">Özel kod gerektirmeyen bir veya daha fazla Windows Forms denetimleri işlevlerini birleştirmek için oluşturabileceğiniz bir *kullanıcı denetimi*.</span><span class="sxs-lookup"><span data-stu-id="c2d11-103">To combine the functionality of one or more Windows Forms controls with custom code, you can create a *user control*.</span></span> <span data-ttu-id="c2d11-104">Kullanıcı denetimleri hızlı denetimi geliştirme birleştirmek, işlevselliği ve özel özellik ve yöntem çok yönlülük standart Windows Forms denetimi.</span><span class="sxs-lookup"><span data-stu-id="c2d11-104">User controls combine rapid control development, standard Windows Forms control functionality, and the versatility of custom properties and methods.</span></span> <span data-ttu-id="c2d11-105">Bir kullanıcı denetimi oluşturma başladığınızda, standart Windows Forms denetimleri yerleştirebilirsiniz görünür Tasarımcısı ile sunulur.</span><span class="sxs-lookup"><span data-stu-id="c2d11-105">When you begin creating a user control, you are presented with a visible designer, upon which you can place standard Windows Forms controls.</span></span> <span data-ttu-id="c2d11-106">Bu denetimler, tüm iç işlevleri yanı sıra görünümünü ve davranışını (Görünüm) standart denetimler korur.</span><span class="sxs-lookup"><span data-stu-id="c2d11-106">These controls retain all of their inherent functionality, as well as the appearance and behavior (look and feel) of standard controls.</span></span> <span data-ttu-id="c2d11-107">Bu denetimler, kullanıcı denetimine oluşturulur, sonra ancak bunlar artık kod kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c2d11-107">Once these controls are built into the user control, however, they are no longer available to you through code.</span></span> <span data-ttu-id="c2d11-108">Kullanıcı denetimi, kendi boyama yapar ve ayrıca temel işlevleri denetimleriyle ilişkili tüm işler.</span><span class="sxs-lookup"><span data-stu-id="c2d11-108">The user control does its own painting and also handles all of the basic functionality associated with controls.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c2d11-109">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="c2d11-109">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="c2d11-110">Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="c2d11-110">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="c2d11-111">Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="c2d11-111">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-create-a-user-control"></a><span data-ttu-id="c2d11-112">Bir kullanıcı denetimi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="c2d11-112">To create a user control</span></span>  
  
1. <span data-ttu-id="c2d11-113">Yeni bir **Windows Denetim Kitaplığı** proje.</span><span class="sxs-lookup"><span data-stu-id="c2d11-113">Create a new **Windows Control Library** project.</span></span>  
  
     <span data-ttu-id="c2d11-114">Boş kullanıcı denetimi ile yeni bir Proje oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="c2d11-114">A new project is created with a blank user control.</span></span>  
  
2. <span data-ttu-id="c2d11-115">Sürükleyin denetimlerden **Windows Forms** sekmesinde **araç kutusu** , tasarımcıya.</span><span class="sxs-lookup"><span data-stu-id="c2d11-115">Drag controls from the **Windows Forms** tab of the **Toolbox** onto your designer.</span></span>  
  
3. <span data-ttu-id="c2d11-116">Bu denetimler konumlandırılır ve son kullanıcı denetimi görünmesini istediğiniz şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="c2d11-116">These controls should be positioned and designed as you want them to appear in the final user control.</span></span> <span data-ttu-id="c2d11-117">Geliştiricilerin bağlı denetimler erişim izin vermek istiyorsanız, bunları ortak olarak bildirmek veya seçmeli olarak bağlı denetimin özelliklerini göstermek.</span><span class="sxs-lookup"><span data-stu-id="c2d11-117">If you want to allow developers to access the constituent controls, you must declare them as public, or selectively expose properties of the constituent control.</span></span> <span data-ttu-id="c2d11-118">Ayrıntılar için bkz [nasıl yapılır: Bağlı denetimlerin özelliklerini açığa](how-to-expose-properties-of-constituent-controls.md).</span><span class="sxs-lookup"><span data-stu-id="c2d11-118">For details, see [How to: Expose Properties of Constituent Controls](how-to-expose-properties-of-constituent-controls.md).</span></span>  
  
4. <span data-ttu-id="c2d11-119">Herhangi bir özel yöntemler veya denetiminiz birleştirecektir özellikleri uygulayın.</span><span class="sxs-lookup"><span data-stu-id="c2d11-119">Implement any custom methods or properties that your control will incorporate.</span></span>  
  
5. <span data-ttu-id="c2d11-120">Projeyi oluşturmak ve denetim çalıştırmak için F5 tuşuna basın **UserControl Test kapsayıcısı**.</span><span class="sxs-lookup"><span data-stu-id="c2d11-120">Press F5 to build the project and run your control in the **UserControl Test Container**.</span></span> <span data-ttu-id="c2d11-121">Daha fazla bilgi için [nasıl yapılır: Bir UserControl denetiminin çalışma zamanı davranışını sınama](how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span><span class="sxs-lookup"><span data-stu-id="c2d11-121">For more information, see [How to: Test the Run-Time Behavior of a UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2d11-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c2d11-122">See also</span></span>

- [<span data-ttu-id="c2d11-123">Özel Denetim Çeşitleri</span><span class="sxs-lookup"><span data-stu-id="c2d11-123">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
- [<span data-ttu-id="c2d11-124">Nasıl yapılır: Denetim sınıfından devralma</span><span class="sxs-lookup"><span data-stu-id="c2d11-124">How to: Inherit from the Control Class</span></span>](how-to-inherit-from-the-control-class.md)
- [<span data-ttu-id="c2d11-125">Nasıl yapılır: Mevcut Windows Formları denetimlerinden devralma</span><span class="sxs-lookup"><span data-stu-id="c2d11-125">How to: Inherit from Existing Windows Forms Controls</span></span>](how-to-inherit-from-existing-windows-forms-controls.md)
- [<span data-ttu-id="c2d11-126">Nasıl yapılır: Windows Forms için yazar denetimleri</span><span class="sxs-lookup"><span data-stu-id="c2d11-126">How to: Author Controls for Windows Forms</span></span>](how-to-author-controls-for-windows-forms.md)
- [<span data-ttu-id="c2d11-127">Basic'de devralınmış olay işleyicileri Visual Basic sorunlarını giderme</span><span class="sxs-lookup"><span data-stu-id="c2d11-127">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
- [<span data-ttu-id="c2d11-128">Nasıl yapılır: Bir UserControl denetiminin çalışma zamanı davranışını sınama</span><span class="sxs-lookup"><span data-stu-id="c2d11-128">How to: Test the Run-Time Behavior of a UserControl</span></span>](how-to-test-the-run-time-behavior-of-a-usercontrol.md)
