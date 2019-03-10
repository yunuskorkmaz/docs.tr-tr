---
title: 'Nasıl yapılır: Windows Forms denetimleri kilitleme'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls, locking
- controls [Windows Forms], locking
ms.assetid: 94efe0d2-c14e-4d14-b903-63ea9b07e290
ms.openlocfilehash: cff3b0a3ba547c15e7b1c896bde49931a6a3c742
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57702652"
---
# <a name="how-to-lock-controls-to-windows-forms"></a><span data-ttu-id="bdb44-102">Nasıl yapılır: Windows Forms denetimleri kilitleme</span><span class="sxs-lookup"><span data-stu-id="bdb44-102">How to: Lock Controls to Windows Forms</span></span>
<span data-ttu-id="bdb44-103">Windows uygulamanızın kullanıcı arabirimini (UI) tasarlarken, böylece istemeden taşıdığınızda veya diğer özellikleri ayarlarken yeniden boyutlandırabilir, doğru konumlandırılır sonra denetimleri kilitleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bdb44-103">When you design the user interface (UI) of your Windows application, you can lock the controls once they are positioned correctly, so that you do not inadvertently move or resize them when setting other properties.</span></span>  
  
 <span data-ttu-id="bdb44-104">Ayrıca, kilitlemek ve tüm form üzerinde denetimleri pek çok denetimi olan formlarda yardımcı olan tek bir seferde kilidini veya tek denetimleri kilidini açabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bdb44-104">Additionally, you can lock and unlock all the controls on the form at once, which is helpful for forms with many controls, or you can unlock individual controls.</span></span> <span data-ttu-id="bdb44-105">Tüm denetimleri form üzerinde istediğiniz yere yerleştirdikten sonra bunları hatalı hareketini önlemek için tüm kilitleme.</span><span class="sxs-lookup"><span data-stu-id="bdb44-105">Once you have placed all the controls where you want them on the form, lock them all in place to prevent erroneous movement.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bdb44-106">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="bdb44-106">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="bdb44-107">Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="bdb44-107">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="bdb44-108">Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="bdb44-108">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-lock-a-control"></a><span data-ttu-id="bdb44-109">Bir denetim kilitlemek için</span><span class="sxs-lookup"><span data-stu-id="bdb44-109">To lock a control</span></span>  
  
1.  <span data-ttu-id="bdb44-110">İçinde **özellikleri** penceresinde tıklayın **kilitli** özelliğini tıklatın ve `true`.</span><span class="sxs-lookup"><span data-stu-id="bdb44-110">In the **Properties** window, click the **Locked** property and select `true`.</span></span> <span data-ttu-id="bdb44-111">(Adına çift özellik ayarı değiştirir.)</span><span class="sxs-lookup"><span data-stu-id="bdb44-111">(Double-clicking the name toggles the property setting.)</span></span>  
  
     <span data-ttu-id="bdb44-112">Alternatif olarak, denetime sağ tıklayın ve seçin **kilit denetimleri**.</span><span class="sxs-lookup"><span data-stu-id="bdb44-112">Alternatively, right-click the control and choose **Lock Controls**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="bdb44-113">Denetimleri kilitleme, bunları tasarım yüzeyine bir yeni boyut veya konum sürüklenen öğesinden engeller.</span><span class="sxs-lookup"><span data-stu-id="bdb44-113">Locking controls prevents them from being dragged to a new size or location on the design surface.</span></span> <span data-ttu-id="bdb44-114">Ancak, yine de denetimleri yoluyla konumunu ve boyutunu değiştirebilirsiniz **özellikleri** penceresi veya kod.</span><span class="sxs-lookup"><span data-stu-id="bdb44-114">However, you can still change the size or location of controls by means of the **Properties** window or in code.</span></span>  
  
### <a name="to-lock-all-the-controls-on-a-form"></a><span data-ttu-id="bdb44-115">Bir formda tüm denetimler kilitlemek için</span><span class="sxs-lookup"><span data-stu-id="bdb44-115">To lock all the controls on a form</span></span>  
  
1.  <span data-ttu-id="bdb44-116">Gelen **biçimi** menüsünde seçin **kilit denetimleri**.</span><span class="sxs-lookup"><span data-stu-id="bdb44-116">From the **Format** menu, choose **Lock Controls**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="bdb44-117">Bir form denetim olduğundan bu komut formun boyutunu da kilitler.</span><span class="sxs-lookup"><span data-stu-id="bdb44-117">This command locks the form's size as well, because a form is a control.</span></span>  
  
### <a name="to-unlock-all-locked-controls-on-a-form"></a><span data-ttu-id="bdb44-118">Formdaki denetimler kilitli tümünün kilidini aç</span><span class="sxs-lookup"><span data-stu-id="bdb44-118">To unlock all locked controls on a form</span></span>  
  
1.  <span data-ttu-id="bdb44-119">Gelen **biçimi** menüsünde seçin **kilit denetimleri**.</span><span class="sxs-lookup"><span data-stu-id="bdb44-119">From the **Format** menu, choose **Lock Controls**.</span></span>  
  
     <span data-ttu-id="bdb44-120">Formdaki tüm daha önce kilitli denetimleri sunulmuştur kilidi.</span><span class="sxs-lookup"><span data-stu-id="bdb44-120">All previously locked controls on the form are now unlocked.</span></span>  
  
### <a name="to-unlock-locked-controls-individually"></a><span data-ttu-id="bdb44-121">Tek tek denetimler kilitli kilidini aç</span><span class="sxs-lookup"><span data-stu-id="bdb44-121">To unlock locked controls individually</span></span>  
  
1.  <span data-ttu-id="bdb44-122">İçinde **özellikleri** penceresinde tıklayın **kilitli** özelliğini tıklatın ve `false`.</span><span class="sxs-lookup"><span data-stu-id="bdb44-122">In the **Properties** window, click the **Locked** property and select `false`.</span></span> <span data-ttu-id="bdb44-123">(Adına çift özellik ayarı değiştirir.)</span><span class="sxs-lookup"><span data-stu-id="bdb44-123">(Double-clicking the name toggles the property setting.)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bdb44-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bdb44-124">See also</span></span>
- [<span data-ttu-id="bdb44-125">Windows Forms Denetimleri</span><span class="sxs-lookup"><span data-stu-id="bdb44-125">Windows Forms Controls</span></span>](index.md)
- [<span data-ttu-id="bdb44-126">Windows Forms’da Denetimleri Düzenleme</span><span class="sxs-lookup"><span data-stu-id="bdb44-126">Arranging Controls on Windows Forms</span></span>](arranging-controls-on-windows-forms.md)
- [<span data-ttu-id="bdb44-127">Ayrı Windows Forms Denetimlerini Etiketleme ve Kısayollarını Sunma</span><span class="sxs-lookup"><span data-stu-id="bdb44-127">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [<span data-ttu-id="bdb44-128">Windows Forms'da Kullanılacak Denetimler</span><span class="sxs-lookup"><span data-stu-id="bdb44-128">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
- [<span data-ttu-id="bdb44-129">İşleve Göre Windows Forms Denetimleri</span><span class="sxs-lookup"><span data-stu-id="bdb44-129">Windows Forms Controls by Function</span></span>](windows-forms-controls-by-function.md)
