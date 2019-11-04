---
title: 'Nasıl yapılır: UserControl Sınıfından Devralma'
ms.date: 03/30/2017
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- UserControl class [Windows Forms], inheriting from
- user controls [Windows Forms], creating
- composite controls [Windows Forms], creating
ms.assetid: 67713625-e2e4-4f6a-bce7-0855ee5043d9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 10bb807d012a130ad633b7ce06f99c5abf2cdda1
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458362"
---
# <a name="how-to-inherit-from-the-usercontrol-class"></a><span data-ttu-id="d4c24-102">Nasıl yapılır: UserControl Sınıfından Devralma</span><span class="sxs-lookup"><span data-stu-id="d4c24-102">How to: Inherit from the UserControl Class</span></span>

<span data-ttu-id="d4c24-103">Bir veya daha fazla Windows Forms denetiminin işlevlerini özel kodla birleştirmek için, bir *Kullanıcı denetimi*oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d4c24-103">To combine the functionality of one or more Windows Forms controls with custom code, you can create a *user control*.</span></span> <span data-ttu-id="d4c24-104">Kullanıcı denetimleri, hızlı denetim geliştirmeyi, standart Windows Forms denetim işlevselliğini ve özel özellikler ile yöntemlerin çok yönlülüğünü birleştirir.</span><span class="sxs-lookup"><span data-stu-id="d4c24-104">User controls combine rapid control development, standard Windows Forms control functionality, and the versatility of custom properties and methods.</span></span> <span data-ttu-id="d4c24-105">Bir kullanıcı denetimi oluşturmaya başladığınızda, üzerinde standart Windows Forms denetimleri yerleştirebileceğiniz görünür bir tasarımcı sunulur.</span><span class="sxs-lookup"><span data-stu-id="d4c24-105">When you begin creating a user control, you are presented with a visible designer, upon which you can place standard Windows Forms controls.</span></span> <span data-ttu-id="d4c24-106">Bu denetimler, tüm kendi işlevlerini, ayrıca Standart denetimlerin görünüm ve davranışını (görünüm ve kullanım) korur.</span><span class="sxs-lookup"><span data-stu-id="d4c24-106">These controls retain all of their inherent functionality, as well as the appearance and behavior (look and feel) of standard controls.</span></span> <span data-ttu-id="d4c24-107">Bu denetimler Kullanıcı denetiminde yerleşik olduktan sonra artık kod aracılığıyla kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="d4c24-107">Once these controls are built into the user control, however, they are no longer available to you through code.</span></span> <span data-ttu-id="d4c24-108">Kullanıcı denetimi kendi boyamayı yapar ve ayrıca denetimlerle ilişkili tüm temel işlevleri de işler.</span><span class="sxs-lookup"><span data-stu-id="d4c24-108">The user control does its own painting and also handles all of the basic functionality associated with controls.</span></span>

## <a name="to-create-a-user-control"></a><span data-ttu-id="d4c24-109">Kullanıcı denetimi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="d4c24-109">To create a user control</span></span>

1. <span data-ttu-id="d4c24-110">Visual Studio 'da yeni bir **Windows Denetim Kitaplığı** projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d4c24-110">Create a new **Windows Control Library** project in Visual Studio.</span></span>

   <span data-ttu-id="d4c24-111">Boş bir kullanıcı denetimiyle yeni bir proje oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="d4c24-111">A new project is created with a blank user control.</span></span>

2. <span data-ttu-id="d4c24-112">Denetimleri **araç kutusunun** **Windows Forms** sekmesinden tasarımcı üzerine sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="d4c24-112">Drag controls from the **Windows Forms** tab of the **Toolbox** onto your designer.</span></span>

3. <span data-ttu-id="d4c24-113">Bu denetimler, son kullanıcı denetiminde görünmesini istediğiniz şekilde yerleştirilmelidir ve tasarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d4c24-113">These controls should be positioned and designed as you want them to appear in the final user control.</span></span> <span data-ttu-id="d4c24-114">Geliştiricilerin bileşen denetimlerine erişmesine izin vermek istiyorsanız, bunları ortak olarak bildirmeniz veya yapısal denetimin özelliklerini seçmeli olarak kullanıma sunmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d4c24-114">If you want to allow developers to access the constituent controls, you must declare them as public, or selectively expose properties of the constituent control.</span></span> <span data-ttu-id="d4c24-115">Ayrıntılar için bkz. [nasıl yapılır: yapısal denetimlerin özelliklerini kullanıma](how-to-expose-properties-of-constituent-controls.md)sunma.</span><span class="sxs-lookup"><span data-stu-id="d4c24-115">For details, see [How to: Expose Properties of Constituent Controls](how-to-expose-properties-of-constituent-controls.md).</span></span>

4. <span data-ttu-id="d4c24-116">Denetiminizin dahil olacağı özel yöntemleri veya özellikleri uygulayın.</span><span class="sxs-lookup"><span data-stu-id="d4c24-116">Implement any custom methods or properties that your control will incorporate.</span></span>

5. <span data-ttu-id="d4c24-117">Projeyi derlemek için **F5** tuşuna basın ve denetimi **UserControl Test kapsayıcısında**çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="d4c24-117">Press **F5** to build the project and run your control in the **UserControl Test Container**.</span></span> <span data-ttu-id="d4c24-118">Daha fazla bilgi için bkz. [nasıl yapılır: bir UserControl 'un çalışma zamanı davranışını test etme](how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span><span class="sxs-lookup"><span data-stu-id="d4c24-118">For more information, see [How to: Test the Run-Time Behavior of a UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d4c24-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d4c24-119">See also</span></span>

- [<span data-ttu-id="d4c24-120">Özel Denetim Çeşitleri</span><span class="sxs-lookup"><span data-stu-id="d4c24-120">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
- [<span data-ttu-id="d4c24-121">Nasıl yapılır: Denetim Sınıfından Devralma</span><span class="sxs-lookup"><span data-stu-id="d4c24-121">How to: Inherit from the Control Class</span></span>](how-to-inherit-from-the-control-class.md)
- [<span data-ttu-id="d4c24-122">Nasıl yapılır: Mevcut Windows Forms Denetimlerinden Devralma</span><span class="sxs-lookup"><span data-stu-id="d4c24-122">How to: Inherit from Existing Windows Forms Controls</span></span>](how-to-inherit-from-existing-windows-forms-controls.md)
- [<span data-ttu-id="d4c24-123">Nasıl yapılır: Windows Forms için Denetimler Yazma</span><span class="sxs-lookup"><span data-stu-id="d4c24-123">How to: Author Controls for Windows Forms</span></span>](how-to-author-controls-for-windows-forms.md)
- [<span data-ttu-id="d4c24-124">Visual Basic devralınan olay Işleyicileriyle ilgili sorunları giderme</span><span class="sxs-lookup"><span data-stu-id="d4c24-124">Troubleshoot Inherited Event Handlers in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
- [<span data-ttu-id="d4c24-125">Nasıl yapılır: Bir UserControl Denetiminin Çalışma Zamanı Davranışını Sınama</span><span class="sxs-lookup"><span data-stu-id="d4c24-125">How to: Test the Run-Time Behavior of a UserControl</span></span>](how-to-test-the-run-time-behavior-of-a-usercontrol.md)
