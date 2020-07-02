---
title: 'Nasıl yapılır: Tasarım Zamanında Windows Formundaki Denetimler için ToolTips Ayarlama'
description: Denetimlerin araç Ipuçlarını programlama yoluyla veya Visual Studio 'daki Windows Form Tasarımcısı ayarlama hakkında bilgi edinin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- tooltips [Windows Forms], for controls
- examples [Windows Forms], tooltips
ms.assetid: c4b60637-4c0a-44c2-a103-f66dff887936
ms.openlocfilehash: 144ba5b6bffb4a538e345f7b2df4a453fc6fd63d
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618031"
---
# <a name="how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time"></a><span data-ttu-id="02f14-103">Nasıl yapılır: tasarım zamanında Windows formundaki denetimler için araç Ipuçları ayarlama</span><span class="sxs-lookup"><span data-stu-id="02f14-103">How to: Set ToolTips for controls on a Windows Form at design time</span></span>

<span data-ttu-id="02f14-104"><xref:System.Windows.Forms.ToolTip>Visual Studio 'da veya Windows Form Tasarımcısı kodda bir dize ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="02f14-104">You can set a <xref:System.Windows.Forms.ToolTip> string in code or in the Windows Forms Designer in Visual Studio.</span></span> <span data-ttu-id="02f14-105">Bileşen hakkında daha fazla bilgi için <xref:System.Windows.Forms.ToolTip> bkz. [ToolTip bileşenine genel bakış](tooltip-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="02f14-105">For more information about the <xref:System.Windows.Forms.ToolTip> component, see [ToolTip Component Overview](tooltip-component-overview-windows-forms.md).</span></span>

## <a name="set-a-tooltip-programmatically"></a><span data-ttu-id="02f14-106">Program aracılığıyla bir araç Ipucu ayarlama</span><span class="sxs-lookup"><span data-stu-id="02f14-106">Set a ToolTip programmatically</span></span>

1. <span data-ttu-id="02f14-107">Araç Ipucunu görüntüleyen denetimi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="02f14-107">Add the control that will display the ToolTip.</span></span>

2. <span data-ttu-id="02f14-108"><xref:System.Windows.Forms.ToolTip.SetToolTip%2A>Bileşenin yöntemini kullanın <xref:System.Windows.Forms.ToolTip> .</span><span class="sxs-lookup"><span data-stu-id="02f14-108">Use the <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> method of the <xref:System.Windows.Forms.ToolTip> component.</span></span>

    ```vb
    ' In this example, Button1 is the control to display the ToolTip.
    ToolTip1.SetToolTip(Button1, "Save changes")
    ```

    ```csharp
    // In this example, button1 is the control to display the ToolTip.
    toolTip1.SetToolTip(button1, "Save changes");
    ```

    ```cpp
    // In this example, button1 is the control to display the ToolTip.
    toolTip1->SetToolTip(button1, "Save changes");
    ```

## <a name="set-a-tooltip-in-the-designer"></a><span data-ttu-id="02f14-109">Tasarımcıda araç Ipucu ayarlama</span><span class="sxs-lookup"><span data-stu-id="02f14-109">Set a ToolTip in the designer</span></span>

1. <span data-ttu-id="02f14-110">Visual Studio 'da <xref:System.Windows.Forms.ToolTip> forma bir bileşen ekleyin.</span><span class="sxs-lookup"><span data-stu-id="02f14-110">In Visual Studio, add a <xref:System.Windows.Forms.ToolTip> component to the form.</span></span>

2. <span data-ttu-id="02f14-111">Araç Ipucunu görüntüleyecek denetimi seçin veya forma ekleyin.</span><span class="sxs-lookup"><span data-stu-id="02f14-111">Select the control that will display the ToolTip, or add it to the form.</span></span>

3. <span data-ttu-id="02f14-112">**Özellikler** penceresinde, **ToolTip1 değerindeki araç ipucunu** uygun bir metin dizesi olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="02f14-112">In the **Properties** window, set the **ToolTip on ToolTip1** value to an appropriate string of text.</span></span>

### <a name="to-remove-a-tooltip-programmatically"></a><span data-ttu-id="02f14-113">Araç Ipucunu programlama yoluyla kaldırma</span><span class="sxs-lookup"><span data-stu-id="02f14-113">To remove a ToolTip programmatically</span></span>

1. <span data-ttu-id="02f14-114"><xref:System.Windows.Forms.ToolTip.SetToolTip%2A>Bileşenin yöntemini kullanın <xref:System.Windows.Forms.ToolTip> .</span><span class="sxs-lookup"><span data-stu-id="02f14-114">Use the <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> method of the <xref:System.Windows.Forms.ToolTip> component.</span></span>

    ```vb
    ' In this example, Button1 is the control displaying the ToolTip.
    ToolTip1.SetToolTip(Button1, Nothing)
    ```

    ```csharp
    // In this example, button1 is the control displaying the ToolTip.
    toolTip1.SetToolTip(button1, null);
    ```

    ```cpp
    // In this example, button1 is the control displaying the ToolTip.
    toolTip1->SetToolTip(button1, NULL);
    ```

## <a name="remove-a-tooltip-in-the-designer"></a><span data-ttu-id="02f14-115">Tasarımcıda araç Ipucunu kaldırma</span><span class="sxs-lookup"><span data-stu-id="02f14-115">Remove a ToolTip in the designer</span></span>

1. <span data-ttu-id="02f14-116">Visual Studio 'da araç Ipucunu görüntüleyen denetimi seçin.</span><span class="sxs-lookup"><span data-stu-id="02f14-116">In Visual Studio, select the control that is displaying the ToolTip.</span></span>

2. <span data-ttu-id="02f14-117">**Özellikler** penceresinde, **ToolTip1 üzerindeki araç ipucunda**bulunan metni silin.</span><span class="sxs-lookup"><span data-stu-id="02f14-117">In the **Properties** window, delete the text in the **ToolTip on ToolTip1**.</span></span>

## <a name="see-also"></a><span data-ttu-id="02f14-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="02f14-118">See also</span></span>

- [<span data-ttu-id="02f14-119">ToolTip Bileşenine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="02f14-119">ToolTip Component Overview</span></span>](tooltip-component-overview-windows-forms.md)
- [<span data-ttu-id="02f14-120">Nasıl yapılır: Windows Forms ToolTip Bileşeninin Gecikmesini Değiştirme</span><span class="sxs-lookup"><span data-stu-id="02f14-120">How to: Change the Delay of the Windows Forms ToolTip Component</span></span>](how-to-change-the-delay-of-the-windows-forms-tooltip-component.md)
- [<span data-ttu-id="02f14-121">ToolTip Bileşeni</span><span class="sxs-lookup"><span data-stu-id="02f14-121">ToolTip Component</span></span>](tooltip-component-windows-forms.md)
