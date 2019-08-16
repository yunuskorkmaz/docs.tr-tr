---
title: "Nasıl yapılır: Windows Forms'a Denetimleri Kilitleme"
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls, locking
- controls [Windows Forms], locking
ms.assetid: 94efe0d2-c14e-4d14-b903-63ea9b07e290
ms.openlocfilehash: cbf82f1481ee9779cec5cfbf3fb057b7ea399a1c
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039900"
---
# <a name="how-to-lock-controls-to-windows-forms"></a><span data-ttu-id="044d6-102">Nasıl yapılır: Windows Forms'a Denetimleri Kilitleme</span><span class="sxs-lookup"><span data-stu-id="044d6-102">How to: Lock Controls to Windows Forms</span></span>
<span data-ttu-id="044d6-103">Windows uygulamanızın kullanıcı arabirimini (UI) tasarladığınızda, denetimleri doğru konumlandırıldıktan sonra kilitleyebilir, böylece diğer özellikleri ayarlarken farkında olmadan taşıyamazsınız veya yeniden boyutlandıramazsınız.</span><span class="sxs-lookup"><span data-stu-id="044d6-103">When you design the user interface (UI) of your Windows application, you can lock the controls once they are positioned correctly, so that you do not inadvertently move or resize them when setting other properties.</span></span>

 <span data-ttu-id="044d6-104">Ayrıca, formdaki tüm denetimleri tek seferde kilitleyebilir ve kilidini açabilir, bu da birçok denetim içeren formlar için faydalıdır veya ayrı denetimlerin kilidini açabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="044d6-104">Additionally, you can lock and unlock all the controls on the form at once, which is helpful for forms with many controls, or you can unlock individual controls.</span></span> <span data-ttu-id="044d6-105">Form üzerinde istediğiniz yere tüm denetimleri yerleştirdikten sonra, hatalı hareketi engellemek için bunları bir yerde kilitleyin.</span><span class="sxs-lookup"><span data-stu-id="044d6-105">Once you have placed all the controls where you want them on the form, lock them all in place to prevent erroneous movement.</span></span>

## <a name="to-lock-a-control"></a><span data-ttu-id="044d6-106">Bir denetimi kilitlemek için</span><span class="sxs-lookup"><span data-stu-id="044d6-106">To lock a control</span></span>

1. <span data-ttu-id="044d6-107">**Özellikler** penceresinde, **kilitli** özelliğine tıklayın ve öğesini seçin `true`.</span><span class="sxs-lookup"><span data-stu-id="044d6-107">In the **Properties** window, click the **Locked** property and select `true`.</span></span> <span data-ttu-id="044d6-108">(Adı çift tıklatmak Özellik ayarında geçiş yapar.)</span><span class="sxs-lookup"><span data-stu-id="044d6-108">(Double-clicking the name toggles the property setting.)</span></span>

     <span data-ttu-id="044d6-109">Alternatif olarak, denetimi sağ tıklatın ve **denetimleri kilitle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="044d6-109">Alternatively, right-click the control and choose **Lock Controls**.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="044d6-110">Denetimleri kilitlemek, bunların tasarım yüzeyinde yeni bir boyuta veya konuma sürüklemesini önler.</span><span class="sxs-lookup"><span data-stu-id="044d6-110">Locking controls prevents them from being dragged to a new size or location on the design surface.</span></span> <span data-ttu-id="044d6-111">Ancak, denetimlerin boyutunu veya konumunu **Özellikler** penceresi veya kod içinde de değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="044d6-111">However, you can still change the size or location of controls by means of the **Properties** window or in code.</span></span>

## <a name="to-lock-all-the-controls-on-a-form"></a><span data-ttu-id="044d6-112">Form üzerindeki tüm denetimleri kilitlemek için</span><span class="sxs-lookup"><span data-stu-id="044d6-112">To lock all the controls on a form</span></span>

1. <span data-ttu-id="044d6-113">**Biçim** menüsünde, **denetimleri kilitle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="044d6-113">From the **Format** menu, choose **Lock Controls**.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="044d6-114">Form bir denetim olduğundan, bu komut formun boyutunu da kilitler.</span><span class="sxs-lookup"><span data-stu-id="044d6-114">This command locks the form's size as well, because a form is a control.</span></span>

## <a name="to-unlock-all-locked-controls-on-a-form"></a><span data-ttu-id="044d6-115">Form üzerindeki tüm kilitli denetimlerin kilidini açmak için</span><span class="sxs-lookup"><span data-stu-id="044d6-115">To unlock all locked controls on a form</span></span>

1. <span data-ttu-id="044d6-116">**Biçim** menüsünde, **denetimleri kilitle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="044d6-116">From the **Format** menu, choose **Lock Controls**.</span></span>

     <span data-ttu-id="044d6-117">Formdaki daha önce kilitlenen tüm denetimlerin kilidi açıldı.</span><span class="sxs-lookup"><span data-stu-id="044d6-117">All previously locked controls on the form are now unlocked.</span></span>

## <a name="to-unlock-locked-controls-individually"></a><span data-ttu-id="044d6-118">Kilitli denetimlerin kilidini ayrı olarak açmak için</span><span class="sxs-lookup"><span data-stu-id="044d6-118">To unlock locked controls individually</span></span>

1. <span data-ttu-id="044d6-119">**Özellikler** penceresinde, **kilitli** özelliğine tıklayın ve öğesini seçin `false`.</span><span class="sxs-lookup"><span data-stu-id="044d6-119">In the **Properties** window, click the **Locked** property and select `false`.</span></span> <span data-ttu-id="044d6-120">(Adı çift tıklatmak Özellik ayarında geçiş yapar.)</span><span class="sxs-lookup"><span data-stu-id="044d6-120">(Double-clicking the name toggles the property setting.)</span></span>

## <a name="see-also"></a><span data-ttu-id="044d6-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="044d6-121">See also</span></span>

- [<span data-ttu-id="044d6-122">Windows Forms Denetimleri</span><span class="sxs-lookup"><span data-stu-id="044d6-122">Windows Forms Controls</span></span>](index.md)
- [<span data-ttu-id="044d6-123">Windows Forms’da Denetimleri Düzenleme</span><span class="sxs-lookup"><span data-stu-id="044d6-123">Arranging Controls on Windows Forms</span></span>](arranging-controls-on-windows-forms.md)
- [<span data-ttu-id="044d6-124">Ayrı Windows Forms Denetimlerini Etiketleme ve Kısayollarını Sunma</span><span class="sxs-lookup"><span data-stu-id="044d6-124">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [<span data-ttu-id="044d6-125">Windows Forms'da Kullanılacak Denetimler</span><span class="sxs-lookup"><span data-stu-id="044d6-125">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
- [<span data-ttu-id="044d6-126">İşleve Göre Windows Forms Denetimleri</span><span class="sxs-lookup"><span data-stu-id="044d6-126">Windows Forms Controls by Function</span></span>](windows-forms-controls-by-function.md)
