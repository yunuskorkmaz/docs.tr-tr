---
title: "Nasıl yapılır: Denetim Sınıfından Devralma"
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
- Control class [Windows Forms], inheriting from
- custom controls [Windows Forms], inheritance
- OnPaint method [Windows Forms]
- custom controls [Windows Forms], creating
ms.assetid: 46ba0df3-5cf7-443c-a3b4-a72660172476
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f7cbca79cd3541df1db7ace3a7d5f67bf3f2b2ab
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-inherit-from-the-control-class"></a><span data-ttu-id="93e0d-102">Nasıl yapılır: Denetim Sınıfından Devralma</span><span class="sxs-lookup"><span data-stu-id="93e0d-102">How to: Inherit from the Control Class</span></span>
<span data-ttu-id="93e0d-103">Bir Windows formunda kullanmak için tamamen özel bir denetim oluşturmak istiyorsanız, gelen alması gerektiğini <xref:System.Windows.Forms.Control> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="93e0d-103">If you want to create a completely custom control to use on a Windows Form, you should inherit from the <xref:System.Windows.Forms.Control> class.</span></span> <span data-ttu-id="93e0d-104">İçinden devralma sırasında <xref:System.Windows.Forms.Control> sınıfı gerektirir daha fazla planlama ve uygulama gerçekleştirmek, ayrıca, en büyük çeşitli seçenekler ile sağlar.</span><span class="sxs-lookup"><span data-stu-id="93e0d-104">While inheriting from the <xref:System.Windows.Forms.Control> class requires that you perform more planning and implementation, it also provides you with the largest range of options.</span></span> <span data-ttu-id="93e0d-105">İçinden devralma zaman <xref:System.Windows.Forms.Control>, iş denetimleri yapar çok temel işlevleri devralır.</span><span class="sxs-lookup"><span data-stu-id="93e0d-105">When inheriting from <xref:System.Windows.Forms.Control>, you inherit the very basic functionality that makes controls work.</span></span> <span data-ttu-id="93e0d-106">Ndaki işlevselliği <xref:System.Windows.Forms.Control> sınıfı klavye ve fare kullanıcı girişini işleme, denetimin boyutunu ve sınırlarını tanımlar, bir windows tanıtıcı sağlar ve ileti işleme ve güvenlik sağlar.</span><span class="sxs-lookup"><span data-stu-id="93e0d-106">The functionality inherent in the <xref:System.Windows.Forms.Control> class handles user input through the keyboard and mouse, defines the bounds and size of the control, provides a windows handle, and provides message handling and security.</span></span> <span data-ttu-id="93e0d-107">Bu durumda grafik arabiriminin denetiminin gerçek işleme olduğu, tüm boyama dahil değildir ve herhangi belirli kullanıcı etkileşimi işlevselliği dahil etmez.</span><span class="sxs-lookup"><span data-stu-id="93e0d-107">It does not incorporate any painting, which in this case is the actual rendering of the graphical interface of the control, nor does it incorporate any specific user interaction functionality.</span></span> <span data-ttu-id="93e0d-108">Tüm özel kod aracılığıyla bu yönlerinin sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="93e0d-108">You must provide all of these aspects through custom code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="93e0d-109">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="93e0d-109">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="93e0d-110">Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="93e0d-110">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="93e0d-111">Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="93e0d-111">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-create-a-custom-control"></a><span data-ttu-id="93e0d-112">Özel bir denetim oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="93e0d-112">To create a custom control</span></span>  
  
1.  <span data-ttu-id="93e0d-113">Yeni bir **Windows uygulaması** veya **Windows Denetim Kitaplığı** projesi.</span><span class="sxs-lookup"><span data-stu-id="93e0d-113">Create a new **Windows Application** or **Windows Control Library** project.</span></span>  
  
2.  <span data-ttu-id="93e0d-114">Gelen **proje** menüsünde seçin **sınıfı Ekle**.</span><span class="sxs-lookup"><span data-stu-id="93e0d-114">From the **Project** menu, choose **Add Class**.</span></span>  
  
3.  <span data-ttu-id="93e0d-115">İçinde **Yeni Öğe Ekle** iletişim kutusu, tıklatın **özel denetimi**.</span><span class="sxs-lookup"><span data-stu-id="93e0d-115">In the **Add New Item** dialog box, click **Custom Control**.</span></span>  
  
     <span data-ttu-id="93e0d-116">Yeni bir özel denetim projenize eklenir.</span><span class="sxs-lookup"><span data-stu-id="93e0d-116">A new custom control is added to your project.</span></span>  
  
4.  <span data-ttu-id="93e0d-117">Basın açmak için F7 **Kod düzenleyicisinde** özel denetim için.</span><span class="sxs-lookup"><span data-stu-id="93e0d-117">Press F7 to open the **Code Editor** for your custom control.</span></span>  
  
5.  <span data-ttu-id="93e0d-118">Bulun <xref:System.Windows.Forms.Control.OnPaint%2A> yapılan bir çağrı dışında boş olur yöntemi <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemi temel sınıf.</span><span class="sxs-lookup"><span data-stu-id="93e0d-118">Locate the <xref:System.Windows.Forms.Control.OnPaint%2A> method, which will be empty except for a call to the <xref:System.Windows.Forms.Control.OnPaint%2A> method of the base class.</span></span>  
  
6.  <span data-ttu-id="93e0d-119">Kodu denetimi için istediğiniz herhangi bir özel boyama içerecek şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="93e0d-119">Modify the code to incorporate any custom painting you want for your control.</span></span>  
  
     <span data-ttu-id="93e0d-120">Grafik denetimleri için işlemek için kod yazma hakkında daha fazla bilgi için bkz: [özel denetim boyama ve işleme](../../../../docs/framework/winforms/controls/custom-control-painting-and-rendering.md).</span><span class="sxs-lookup"><span data-stu-id="93e0d-120">For information about writing code to render graphics for controls, see [Custom Control Painting and Rendering](../../../../docs/framework/winforms/controls/custom-control-painting-and-rendering.md).</span></span>  
  
7.  <span data-ttu-id="93e0d-121">Tüm özel yöntemler, özellikler veya denetiminizi dahil olayların uygulayın.</span><span class="sxs-lookup"><span data-stu-id="93e0d-121">Implement any custom methods, properties, or events that your control will incorporate.</span></span>  
  
8.  <span data-ttu-id="93e0d-122">Kaydet ve denetiminizin sınayın.</span><span class="sxs-lookup"><span data-stu-id="93e0d-122">Save and test your control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93e0d-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="93e0d-123">See Also</span></span>  
 [<span data-ttu-id="93e0d-124">Özel Denetim Çeşitleri</span><span class="sxs-lookup"><span data-stu-id="93e0d-124">Varieties of Custom Controls</span></span>](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)  
 [<span data-ttu-id="93e0d-125">Nasıl yapılır: UserControl Sınıfından Devralma</span><span class="sxs-lookup"><span data-stu-id="93e0d-125">How to: Inherit from the UserControl Class</span></span>](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-usercontrol-class.md)  
 [<span data-ttu-id="93e0d-126">Nasıl yapılır: Mevcut Windows Forms Denetimlerinden Devralma</span><span class="sxs-lookup"><span data-stu-id="93e0d-126">How to: Inherit from Existing Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-inherit-from-existing-windows-forms-controls.md)  
 [<span data-ttu-id="93e0d-127">Nasıl yapılır: Windows Forms için Denetimler Yazma</span><span class="sxs-lookup"><span data-stu-id="93e0d-127">How to: Author Controls for Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-author-controls-for-windows-forms.md)  
 [<span data-ttu-id="93e0d-128">Devralınmış olay işleyicileri Visual Basic sorunlarını giderme</span><span class="sxs-lookup"><span data-stu-id="93e0d-128">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)  
 [<span data-ttu-id="93e0d-129">Tasarım Zamanında Windows Forms Denetimleri Geliştirme</span><span class="sxs-lookup"><span data-stu-id="93e0d-129">Developing Windows Forms Controls at Design Time</span></span>](../../../../docs/framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)
