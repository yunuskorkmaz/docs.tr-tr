---
title: 'Nasıl yapılır: Windows Formlarına Denetimler Kilitleme'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls, locking
- controls [Windows Forms], locking
ms.assetid: 94efe0d2-c14e-4d14-b903-63ea9b07e290
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d157ddc8be4b5fa0057241b562e76b566e8dad99
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458347"
---
# <a name="how-to-lock-controls-to-windows-forms"></a><span data-ttu-id="93a66-102">Nasıl yapılır: Windows Forms denetimleri kilitleme</span><span class="sxs-lookup"><span data-stu-id="93a66-102">How to: Lock controls to Windows Forms</span></span>

<span data-ttu-id="93a66-103">Windows uygulamanızın kullanıcı arabirimini (UI) tasarladığınızda, denetimleri doğru konumlandırıldıktan sonra kilitleyebilir, böylece diğer özellikleri ayarlarken farkında olmadan taşıyamazsınız veya yeniden boyutlandıramazsınız.</span><span class="sxs-lookup"><span data-stu-id="93a66-103">When you design the user interface (UI) of your Windows application, you can lock the controls once they are positioned correctly, so that you do not inadvertently move or resize them when setting other properties.</span></span>

<span data-ttu-id="93a66-104">Ayrıca, formdaki tüm denetimleri tek seferde kilitleyebilir ve kilidini açabilir, bu da birçok denetim içeren formlar için faydalıdır veya ayrı denetimlerin kilidini açabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="93a66-104">Additionally, you can lock and unlock all the controls on the form at once, which is helpful for forms with many controls, or you can unlock individual controls.</span></span> <span data-ttu-id="93a66-105">Form üzerinde istediğiniz yere tüm denetimleri yerleştirdikten sonra, hatalı hareketi engellemek için bunları bir yerde kilitleyin.</span><span class="sxs-lookup"><span data-stu-id="93a66-105">Once you have placed all the controls where you want them on the form, lock them all in place to prevent erroneous movement.</span></span>

## <a name="to-lock-a-control"></a><span data-ttu-id="93a66-106">Bir denetimi kilitlemek için</span><span class="sxs-lookup"><span data-stu-id="93a66-106">To lock a control</span></span>

<span data-ttu-id="93a66-107">Visual Studio 'nun **Özellikler** penceresinde **kilitli** özelliğini seçin ve ardından **doğru**öğesini seçin.</span><span class="sxs-lookup"><span data-stu-id="93a66-107">In the **Properties** window of Visual Studio, select the **Locked** property and then select **true**.</span></span> <span data-ttu-id="93a66-108">(Adı çift tıklatmak Özellik ayarında geçiş yapar.)</span><span class="sxs-lookup"><span data-stu-id="93a66-108">(Double-clicking the name toggles the property setting.)</span></span>

<span data-ttu-id="93a66-109">Alternatif olarak, denetimi sağ tıklatın ve **denetimleri kilitle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="93a66-109">Alternatively, right-click the control and choose **Lock Controls**.</span></span>

> [!NOTE]
> <span data-ttu-id="93a66-110">Denetimleri kilitlemek, bunların tasarım yüzeyinde yeni bir boyuta veya konuma sürüklemesini önler.</span><span class="sxs-lookup"><span data-stu-id="93a66-110">Locking controls prevents them from being dragged to a new size or location on the design surface.</span></span> <span data-ttu-id="93a66-111">Ancak, denetimlerin boyutunu veya konumunu **Özellikler** penceresi veya kod içinde de değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="93a66-111">However, you can still change the size or location of controls by means of the **Properties** window or in code.</span></span>

## <a name="to-lock-all-the-controls-on-a-form"></a><span data-ttu-id="93a66-112">Form üzerindeki tüm denetimleri kilitlemek için</span><span class="sxs-lookup"><span data-stu-id="93a66-112">To lock all the controls on a form</span></span>

<span data-ttu-id="93a66-113">**Biçim** menüsünde, **denetimleri kilitle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="93a66-113">From the **Format** menu, choose **Lock Controls**.</span></span>

> [!NOTE]
> <span data-ttu-id="93a66-114">Form bir denetim olduğundan, bu komut formun boyutunu da kilitler.</span><span class="sxs-lookup"><span data-stu-id="93a66-114">This command locks the form's size as well, because a form is a control.</span></span>

## <a name="to-unlock-all-locked-controls-on-a-form"></a><span data-ttu-id="93a66-115">Form üzerindeki tüm kilitli denetimlerin kilidini açmak için</span><span class="sxs-lookup"><span data-stu-id="93a66-115">To unlock all locked controls on a form</span></span>

<span data-ttu-id="93a66-116">**Biçim** menüsünde, **denetimleri kilitle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="93a66-116">From the **Format** menu, choose **Lock Controls**.</span></span>

<span data-ttu-id="93a66-117">Formdaki daha önce kilitlenen tüm denetimlerin kilidi açıldı.</span><span class="sxs-lookup"><span data-stu-id="93a66-117">All previously locked controls on the form are now unlocked.</span></span>

## <a name="to-unlock-locked-controls-individually"></a><span data-ttu-id="93a66-118">Kilitli denetimlerin kilidini ayrı olarak açmak için</span><span class="sxs-lookup"><span data-stu-id="93a66-118">To unlock locked controls individually</span></span>

<span data-ttu-id="93a66-119">**Özellikler** penceresinde **kilitli** özelliğini seçin ve sonra **false**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="93a66-119">In the **Properties** window, select the **Locked** property and then select **false**.</span></span> <span data-ttu-id="93a66-120">(Adı çift tıklatmak Özellik ayarında geçiş yapar.)</span><span class="sxs-lookup"><span data-stu-id="93a66-120">(Double-clicking the name toggles the property setting.)</span></span>

## <a name="see-also"></a><span data-ttu-id="93a66-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="93a66-121">See also</span></span>

- [<span data-ttu-id="93a66-122">Windows Forms Denetimleri</span><span class="sxs-lookup"><span data-stu-id="93a66-122">Windows Forms Controls</span></span>](index.md)
- [<span data-ttu-id="93a66-123">Ayrı Windows Forms Denetimlerini Etiketleme ve Kısayollarını Sunma</span><span class="sxs-lookup"><span data-stu-id="93a66-123">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [<span data-ttu-id="93a66-124">Windows Forms'da Kullanılacak Denetimler</span><span class="sxs-lookup"><span data-stu-id="93a66-124">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
- [<span data-ttu-id="93a66-125">İşleve Göre Windows Forms Denetimleri</span><span class="sxs-lookup"><span data-stu-id="93a66-125">Windows Forms Controls by Function</span></span>](windows-forms-controls-by-function.md)
