---
title: 'Nasıl yapılır: UserControl Sınıfından Devralma'
ms.date: 03/30/2017
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- UserControl class [Windows Forms], inheriting from
- user controls [Windows Forms], creating
- composite controls [Windows Forms], creating
ms.assetid: 67713625-e2e4-4f6a-bce7-0855ee5043d9
ms.openlocfilehash: 69452f24e5c485ce0aba454648b59c50fb0ce1e3
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69037761"
---
# <a name="how-to-inherit-from-the-usercontrol-class"></a><span data-ttu-id="4d9a8-102">Nasıl yapılır: UserControl Sınıfından Devralma</span><span class="sxs-lookup"><span data-stu-id="4d9a8-102">How to: Inherit from the UserControl Class</span></span>
<span data-ttu-id="4d9a8-103">Bir veya daha fazla Windows Forms denetiminin işlevlerini özel kodla birleştirmek için, bir *Kullanıcı denetimi*oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4d9a8-103">To combine the functionality of one or more Windows Forms controls with custom code, you can create a *user control*.</span></span> <span data-ttu-id="4d9a8-104">Kullanıcı denetimleri, hızlı denetim geliştirmeyi, standart Windows Forms denetim işlevselliğini ve özel özellikler ile yöntemlerin çok yönlülüğünü birleştirir.</span><span class="sxs-lookup"><span data-stu-id="4d9a8-104">User controls combine rapid control development, standard Windows Forms control functionality, and the versatility of custom properties and methods.</span></span> <span data-ttu-id="4d9a8-105">Bir kullanıcı denetimi oluşturmaya başladığınızda, üzerinde standart Windows Forms denetimleri yerleştirebileceğiniz görünür bir tasarımcı sunulur.</span><span class="sxs-lookup"><span data-stu-id="4d9a8-105">When you begin creating a user control, you are presented with a visible designer, upon which you can place standard Windows Forms controls.</span></span> <span data-ttu-id="4d9a8-106">Bu denetimler, tüm kendi işlevlerini, ayrıca Standart denetimlerin görünüm ve davranışını (görünüm ve kullanım) korur.</span><span class="sxs-lookup"><span data-stu-id="4d9a8-106">These controls retain all of their inherent functionality, as well as the appearance and behavior (look and feel) of standard controls.</span></span> <span data-ttu-id="4d9a8-107">Bu denetimler Kullanıcı denetiminde yerleşik olduktan sonra artık kod aracılığıyla kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="4d9a8-107">Once these controls are built into the user control, however, they are no longer available to you through code.</span></span> <span data-ttu-id="4d9a8-108">Kullanıcı denetimi kendi boyamayı yapar ve ayrıca denetimlerle ilişkili tüm temel işlevleri de işler.</span><span class="sxs-lookup"><span data-stu-id="4d9a8-108">The user control does its own painting and also handles all of the basic functionality associated with controls.</span></span>

## <a name="to-create-a-user-control"></a><span data-ttu-id="4d9a8-109">Kullanıcı denetimi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="4d9a8-109">To create a user control</span></span>

1. <span data-ttu-id="4d9a8-110">Yeni bir **Windows Denetim Kitaplığı** projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="4d9a8-110">Create a new **Windows Control Library** project.</span></span>

     <span data-ttu-id="4d9a8-111">Boş bir kullanıcı denetimiyle yeni bir proje oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="4d9a8-111">A new project is created with a blank user control.</span></span>

2. <span data-ttu-id="4d9a8-112">Denetimleri **araç kutusunun** **Windows Forms** sekmesinden tasarımcı üzerine sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="4d9a8-112">Drag controls from the **Windows Forms** tab of the **Toolbox** onto your designer.</span></span>

3. <span data-ttu-id="4d9a8-113">Bu denetimler, son kullanıcı denetiminde görünmesini istediğiniz şekilde yerleştirilmelidir ve tasarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4d9a8-113">These controls should be positioned and designed as you want them to appear in the final user control.</span></span> <span data-ttu-id="4d9a8-114">Geliştiricilerin bileşen denetimlerine erişmesine izin vermek istiyorsanız, bunları ortak olarak bildirmeniz veya yapısal denetimin özelliklerini seçmeli olarak kullanıma sunmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="4d9a8-114">If you want to allow developers to access the constituent controls, you must declare them as public, or selectively expose properties of the constituent control.</span></span> <span data-ttu-id="4d9a8-115">Ayrıntılar için bkz [. nasıl yapılır: Bileşen denetimlerinin](how-to-expose-properties-of-constituent-controls.md)özelliklerini kullanıma sunun.</span><span class="sxs-lookup"><span data-stu-id="4d9a8-115">For details, see [How to: Expose Properties of Constituent Controls](how-to-expose-properties-of-constituent-controls.md).</span></span>

4. <span data-ttu-id="4d9a8-116">Denetiminizin dahil olacağı özel yöntemleri veya özellikleri uygulayın.</span><span class="sxs-lookup"><span data-stu-id="4d9a8-116">Implement any custom methods or properties that your control will incorporate.</span></span>

5. <span data-ttu-id="4d9a8-117">Projeyi derlemek için F5 tuşuna basın ve denetimi **UserControl Test kapsayıcısında**çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="4d9a8-117">Press F5 to build the project and run your control in the **UserControl Test Container**.</span></span> <span data-ttu-id="4d9a8-118">Daha fazla bilgi için [nasıl yapılır: UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md)'un çalışma zamanı davranışını test edin.</span><span class="sxs-lookup"><span data-stu-id="4d9a8-118">For more information, see [How to: Test the Run-Time Behavior of a UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4d9a8-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4d9a8-119">See also</span></span>

- [<span data-ttu-id="4d9a8-120">Özel Denetim Çeşitleri</span><span class="sxs-lookup"><span data-stu-id="4d9a8-120">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
- [<span data-ttu-id="4d9a8-121">Nasıl yapılır: Denetim sınıfından devralma</span><span class="sxs-lookup"><span data-stu-id="4d9a8-121">How to: Inherit from the Control Class</span></span>](how-to-inherit-from-the-control-class.md)
- [<span data-ttu-id="4d9a8-122">Nasıl yapılır: Mevcut Windows Forms denetimlerinden devralma</span><span class="sxs-lookup"><span data-stu-id="4d9a8-122">How to: Inherit from Existing Windows Forms Controls</span></span>](how-to-inherit-from-existing-windows-forms-controls.md)
- [<span data-ttu-id="4d9a8-123">Nasıl yapılır: Windows Forms için yazar denetimleri</span><span class="sxs-lookup"><span data-stu-id="4d9a8-123">How to: Author Controls for Windows Forms</span></span>](how-to-author-controls-for-windows-forms.md)
- [<span data-ttu-id="4d9a8-124">Visual Basic devralınan olay Işleyicileriyle ilgili sorunları giderme</span><span class="sxs-lookup"><span data-stu-id="4d9a8-124">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
- [<span data-ttu-id="4d9a8-125">Nasıl yapılır: UserControl 'un çalışma zamanı davranışını test etme</span><span class="sxs-lookup"><span data-stu-id="4d9a8-125">How to: Test the Run-Time Behavior of a UserControl</span></span>](how-to-test-the-run-time-behavior-of-a-usercontrol.md)
