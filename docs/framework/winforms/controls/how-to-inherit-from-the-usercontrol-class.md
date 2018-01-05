---
title: "Nasıl yapılır: UserControl Sınıfından Devralma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- UserControl class [Windows Forms], inheriting from
- user controls [Windows Forms], creating
- composite controls [Windows Forms], creating
ms.assetid: 67713625-e2e4-4f6a-bce7-0855ee5043d9
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c8d04eb3c0f9ad3ef9f316bf156a9cc9568e7f8d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-inherit-from-the-usercontrol-class"></a><span data-ttu-id="25d6c-102">Nasıl yapılır: UserControl Sınıfından Devralma</span><span class="sxs-lookup"><span data-stu-id="25d6c-102">How to: Inherit from the UserControl Class</span></span>
<span data-ttu-id="25d6c-103">Özel kod ile bir veya daha fazla Windows Forms denetimleri işlevselliğini birleştirmek için oluşturabileceğiniz bir *kullanıcı denetimi*.</span><span class="sxs-lookup"><span data-stu-id="25d6c-103">To combine the functionality of one or more Windows Forms controls with custom code, you can create a *user control*.</span></span> <span data-ttu-id="25d6c-104">Kullanıcı denetimleri hızlı denetimi geliştirme birleştirmek, işlevsellik ve özel özellikler ve yöntemler yönlülük standart Windows Forms denetimi.</span><span class="sxs-lookup"><span data-stu-id="25d6c-104">User controls combine rapid control development, standard Windows Forms control functionality, and the versatility of custom properties and methods.</span></span> <span data-ttu-id="25d6c-105">Bir kullanıcı denetimi oluşturma başladığınızda,, standart Windows Forms denetimleri yerleştirebileceğiniz görünür tasarımcı ile birlikte sunulur.</span><span class="sxs-lookup"><span data-stu-id="25d6c-105">When you begin creating a user control, you are presented with a visible designer, upon which you can place standard Windows Forms controls.</span></span> <span data-ttu-id="25d6c-106">Bu denetimler tüm devralınmış işlevselliklerini yanı sıra görünümünü ve standart denetimler (Görünüm) davranışını korur.</span><span class="sxs-lookup"><span data-stu-id="25d6c-106">These controls retain all of their inherent functionality, as well as the appearance and behavior (look and feel) of standard controls.</span></span> <span data-ttu-id="25d6c-107">Bu denetimleri içinde kullanıcı denetimini yerleşiktir sonra ancak bunlar artık kod üzerinden kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="25d6c-107">Once these controls are built into the user control, however, they are no longer available to you through code.</span></span> <span data-ttu-id="25d6c-108">Kullanıcı denetimi kendi boyama yapar ve ayrıca tüm denetimleriyle ilişkili temel işlevleri yürütür.</span><span class="sxs-lookup"><span data-stu-id="25d6c-108">The user control does its own painting and also handles all of the basic functionality associated with controls.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="25d6c-109">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="25d6c-109">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="25d6c-110">Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="25d6c-110">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="25d6c-111">Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="25d6c-111">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-create-a-user-control"></a><span data-ttu-id="25d6c-112">Bir kullanıcı denetimi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="25d6c-112">To create a user control</span></span>  
  
1.  <span data-ttu-id="25d6c-113">Yeni bir **Windows Denetim Kitaplığı** projesi.</span><span class="sxs-lookup"><span data-stu-id="25d6c-113">Create a new **Windows Control Library** project.</span></span>  
  
     <span data-ttu-id="25d6c-114">Yeni bir proje boş kullanıcı denetimi ile oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="25d6c-114">A new project is created with a blank user control.</span></span>  
  
2.  <span data-ttu-id="25d6c-115">Sürükleme denetimlerden **Windows Forms** sekmesinde **araç** , tasarımcıya.</span><span class="sxs-lookup"><span data-stu-id="25d6c-115">Drag controls from the **Windows Forms** tab of the **Toolbox** onto your designer.</span></span>  
  
3.  <span data-ttu-id="25d6c-116">Bu denetimler konumlandırılmış ve son kullanıcı denetiminde görünmesini istediğiniz şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="25d6c-116">These controls should be positioned and designed as you want them to appear in the final user control.</span></span> <span data-ttu-id="25d6c-117">Bağlı denetimler erişmek geliştiricilere izin vermek istiyorsanız, ortak olarak bildirme veya bağlı denetimi özellikleri, seçmeli olarak kullanıma gerekir.</span><span class="sxs-lookup"><span data-stu-id="25d6c-117">If you want to allow developers to access the constituent controls, you must declare them as public, or selectively expose properties of the constituent control.</span></span> <span data-ttu-id="25d6c-118">Ayrıntılar için bkz [nasıl yapılır: destekçi denetimleri özellikleri kullanıma](../../../../docs/framework/winforms/controls/how-to-expose-properties-of-constituent-controls.md).</span><span class="sxs-lookup"><span data-stu-id="25d6c-118">For details, see [How to: Expose Properties of Constituent Controls](../../../../docs/framework/winforms/controls/how-to-expose-properties-of-constituent-controls.md).</span></span>  
  
4.  <span data-ttu-id="25d6c-119">Herhangi bir özel yöntemler veya denetiminizi dahil özellikler uygular.</span><span class="sxs-lookup"><span data-stu-id="25d6c-119">Implement any custom methods or properties that your control will incorporate.</span></span>  
  
5.  <span data-ttu-id="25d6c-120">Projeyi derlemek ve denetiminizin çalıştırmak için F5 tuşuna basın **UserControl Test kapsayıcısı**.</span><span class="sxs-lookup"><span data-stu-id="25d6c-120">Press F5 to build the project and run your control in the **UserControl Test Container**.</span></span> <span data-ttu-id="25d6c-121">Daha fazla bilgi için bkz: [nasıl yapılır: bir UserControl denetiminin çalışma zamanı davranışını sınama](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span><span class="sxs-lookup"><span data-stu-id="25d6c-121">For more information, see [How to: Test the Run-Time Behavior of a UserControl](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25d6c-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="25d6c-122">See Also</span></span>  
 [<span data-ttu-id="25d6c-123">Özel Denetim Çeşitleri</span><span class="sxs-lookup"><span data-stu-id="25d6c-123">Varieties of Custom Controls</span></span>](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)  
 [<span data-ttu-id="25d6c-124">Nasıl yapılır: Denetim Sınıfından Devralma</span><span class="sxs-lookup"><span data-stu-id="25d6c-124">How to: Inherit from the Control Class</span></span>](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-control-class.md)  
 [<span data-ttu-id="25d6c-125">Nasıl yapılır: Mevcut Windows Forms Denetimlerinden Devralma</span><span class="sxs-lookup"><span data-stu-id="25d6c-125">How to: Inherit from Existing Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-inherit-from-existing-windows-forms-controls.md)  
 [<span data-ttu-id="25d6c-126">Nasıl yapılır: Windows Forms için Denetimler Yazma</span><span class="sxs-lookup"><span data-stu-id="25d6c-126">How to: Author Controls for Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-author-controls-for-windows-forms.md)  
 [<span data-ttu-id="25d6c-127">Devralınmış olay işleyicileri Visual Basic sorunlarını giderme</span><span class="sxs-lookup"><span data-stu-id="25d6c-127">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)  
 [<span data-ttu-id="25d6c-128">Nasıl yapılır: Bir UserControl Denetiminin Çalışma Zamanı Davranışını Sınama</span><span class="sxs-lookup"><span data-stu-id="25d6c-128">How to: Test the Run-Time Behavior of a UserControl</span></span>](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md)
