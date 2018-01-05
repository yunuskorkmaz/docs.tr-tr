---
title: "Nasıl yapılır: Windows Formlarına Denetimler Kilitleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms controls, locking
- controls [Windows Forms], locking
ms.assetid: 94efe0d2-c14e-4d14-b903-63ea9b07e290
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a0bd0f8dcde95dcbb5ef8fcf398256b6931859c7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-lock-controls-to-windows-forms"></a><span data-ttu-id="9b3d6-102">Nasıl yapılır: Windows Formlarına Denetimler Kilitleme</span><span class="sxs-lookup"><span data-stu-id="9b3d6-102">How to: Lock Controls to Windows Forms</span></span>
<span data-ttu-id="9b3d6-103">Windows uygulamanızın kullanıcı arabirimi (UI) tasarlarken, böylece istemeden taşıdığınızda veya diğer özellikleri ayarlanırken yeniden boyutlandırmak, doğru yer almasını sonra denetimleri kilitleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9b3d6-103">When you design the user interface (UI) of your Windows application, you can lock the controls once they are positioned correctly, so that you do not inadvertently move or resize them when setting other properties.</span></span>  
  
 <span data-ttu-id="9b3d6-104">Ayrıca, kilitleme ve tüm form üzerinde denetimleri birçok denetimleri ile formlar için yararlı olan aynı anda kilidini açma veya ayrı ayrı denetimler kilidini açabilir.</span><span class="sxs-lookup"><span data-stu-id="9b3d6-104">Additionally, you can lock and unlock all the controls on the form at once, which is helpful for forms with many controls, or you can unlock individual controls.</span></span> <span data-ttu-id="9b3d6-105">Form üzerinde istediğiniz yere tüm denetimler yerleştirdiğiniz sonra bunları hatalı taşıma önlemek için tüm yerinde kilitleyin.</span><span class="sxs-lookup"><span data-stu-id="9b3d6-105">Once you have placed all the controls where you want them on the form, lock them all in place to prevent erroneous movement.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9b3d6-106">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="9b3d6-106">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="9b3d6-107">Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="9b3d6-107">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="9b3d6-108">Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="9b3d6-108">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-lock-a-control"></a><span data-ttu-id="9b3d6-109">Bir denetim kilitlemek için</span><span class="sxs-lookup"><span data-stu-id="9b3d6-109">To lock a control</span></span>  
  
1.  <span data-ttu-id="9b3d6-110">İçinde **özellikleri** penceresinde tıklatın **kilitli** özelliği ve seçin `true`.</span><span class="sxs-lookup"><span data-stu-id="9b3d6-110">In the **Properties** window, click the **Locked** property and select `true`.</span></span> <span data-ttu-id="9b3d6-111">(Ad çift özellik ayarı değiştirir.)</span><span class="sxs-lookup"><span data-stu-id="9b3d6-111">(Double-clicking the name toggles the property setting.)</span></span>  
  
     <span data-ttu-id="9b3d6-112">Alternatif olarak, denetimi sağ tıklatın ve seçin **kilit denetimleri**.</span><span class="sxs-lookup"><span data-stu-id="9b3d6-112">Alternatively, right-click the control and choose **Lock Controls**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="9b3d6-113">Denetimler kilitleme, bunları tasarım yüzeyine bir yeni boyutunu veya konumunu sürüklenmesini önleyerek engeller.</span><span class="sxs-lookup"><span data-stu-id="9b3d6-113">Locking controls prevents them from being dragged to a new size or location on the design surface.</span></span> <span data-ttu-id="9b3d6-114">Ancak, yine boyutunu veya denetimleri yoluyla konumunu değiştirebilirsiniz **özellikleri** penceresi veya kod.</span><span class="sxs-lookup"><span data-stu-id="9b3d6-114">However, you can still change the size or location of controls by means of the **Properties** window or in code.</span></span>  
  
### <a name="to-lock-all-the-controls-on-a-form"></a><span data-ttu-id="9b3d6-115">Formdaki tüm denetimler kilitlemek için</span><span class="sxs-lookup"><span data-stu-id="9b3d6-115">To lock all the controls on a form</span></span>  
  
1.  <span data-ttu-id="9b3d6-116">Gelen **biçimi** menüsünde seçin **kilit denetimleri**.</span><span class="sxs-lookup"><span data-stu-id="9b3d6-116">From the **Format** menu, choose **Lock Controls**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="9b3d6-117">Bir form denetim olduğundan bu komut formun boyutu de kilitler.</span><span class="sxs-lookup"><span data-stu-id="9b3d6-117">This command locks the form's size as well, because a form is a control.</span></span>  
  
### <a name="to-unlock-all-locked-controls-on-a-form"></a><span data-ttu-id="9b3d6-118">Tüm kilidini açmak için bir form üzerinde denetimleri kilitli</span><span class="sxs-lookup"><span data-stu-id="9b3d6-118">To unlock all locked controls on a form</span></span>  
  
1.  <span data-ttu-id="9b3d6-119">Gelen **biçimi** menüsünde seçin **kilit denetimleri**.</span><span class="sxs-lookup"><span data-stu-id="9b3d6-119">From the **Format** menu, choose **Lock Controls**.</span></span>  
  
     <span data-ttu-id="9b3d6-120">Tüm daha önce kilitli denetimleri form üzerinde sunulmuştur kilidi.</span><span class="sxs-lookup"><span data-stu-id="9b3d6-120">All previously locked controls on the form are now unlocked.</span></span>  
  
### <a name="to-unlock-locked-controls-individually"></a><span data-ttu-id="9b3d6-121">Kilitli denetimleri tek tek kilidini açmak için</span><span class="sxs-lookup"><span data-stu-id="9b3d6-121">To unlock locked controls individually</span></span>  
  
1.  <span data-ttu-id="9b3d6-122">İçinde **özellikleri** penceresinde tıklatın **kilitli** özelliği ve seçin `false`.</span><span class="sxs-lookup"><span data-stu-id="9b3d6-122">In the **Properties** window, click the **Locked** property and select `false`.</span></span> <span data-ttu-id="9b3d6-123">(Ad çift özellik ayarı değiştirir.)</span><span class="sxs-lookup"><span data-stu-id="9b3d6-123">(Double-clicking the name toggles the property setting.)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b3d6-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9b3d6-124">See Also</span></span>  
 [<span data-ttu-id="9b3d6-125">Windows Forms Denetimleri</span><span class="sxs-lookup"><span data-stu-id="9b3d6-125">Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/index.md)  
 [<span data-ttu-id="9b3d6-126">Windows Forms’da Denetimleri Düzenleme</span><span class="sxs-lookup"><span data-stu-id="9b3d6-126">Arranging Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [<span data-ttu-id="9b3d6-127">Ayrı Windows Forms Denetimlerini Etiketleme ve Kısayollarını Sunma</span><span class="sxs-lookup"><span data-stu-id="9b3d6-127">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)  
 [<span data-ttu-id="9b3d6-128">Windows Forms'da Kullanılacak Denetimler</span><span class="sxs-lookup"><span data-stu-id="9b3d6-128">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 [<span data-ttu-id="9b3d6-129">İşleve Göre Windows Forms Denetimleri</span><span class="sxs-lookup"><span data-stu-id="9b3d6-129">Windows Forms Controls by Function</span></span>](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)
