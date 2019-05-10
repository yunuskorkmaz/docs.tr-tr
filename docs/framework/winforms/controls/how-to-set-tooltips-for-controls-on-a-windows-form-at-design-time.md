---
title: 'Nasıl yapılır: Tasarım Zamanında Windows Formundaki Denetimler için ToolTips Ayarlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- tooltips [Windows Forms], for controls
- examples [Windows Forms], tooltips
ms.assetid: c4b60637-4c0a-44c2-a103-f66dff887936
ms.openlocfilehash: 0d6725fc1a00826870e6400bffce63a1788e802c
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211694"
---
# <a name="how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time"></a><span data-ttu-id="d8e9e-102">Nasıl yapılır: Tasarım zamanında bir Windows formundaki denetimler için ToolTips ayarlama</span><span class="sxs-lookup"><span data-stu-id="d8e9e-102">How to: Set ToolTips for controls on a Windows Form at design time</span></span>

<span data-ttu-id="d8e9e-103">Ayarlayabileceğiniz bir <xref:System.Windows.Forms.ToolTip> kod ya da Windows Form Tasarımcısı'nda Visual Studio dize.</span><span class="sxs-lookup"><span data-stu-id="d8e9e-103">You can set a <xref:System.Windows.Forms.ToolTip> string in code or in the Windows Forms Designer in Visual Studio.</span></span> <span data-ttu-id="d8e9e-104">Hakkında daha fazla bilgi için <xref:System.Windows.Forms.ToolTip> bileşeni Bkz [ToolTip bileşenine genel bakış](tooltip-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="d8e9e-104">For more information about the <xref:System.Windows.Forms.ToolTip> component, see [ToolTip Component Overview](tooltip-component-overview-windows-forms.md).</span></span>

## <a name="set-a-tooltip-programmatically"></a><span data-ttu-id="d8e9e-105">Bir araç ipucu programlı olarak ayarlama</span><span class="sxs-lookup"><span data-stu-id="d8e9e-105">Set a ToolTip programmatically</span></span>

1. <span data-ttu-id="d8e9e-106">Araç İpucu görüntüleyen denetimi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d8e9e-106">Add the control that will display the ToolTip.</span></span>

2. <span data-ttu-id="d8e9e-107">Kullanım <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> yöntemi <xref:System.Windows.Forms.ToolTip> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="d8e9e-107">Use the <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> method of the <xref:System.Windows.Forms.ToolTip> component.</span></span>

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

## <a name="set-a-tooltip-in-the-designer"></a><span data-ttu-id="d8e9e-108">Bir araç ipucu Tasarımcısı'nda ayarlayın</span><span class="sxs-lookup"><span data-stu-id="d8e9e-108">Set a ToolTip in the designer</span></span>

1. <span data-ttu-id="d8e9e-109">Visual Studio'da ekleme bir <xref:System.Windows.Forms.ToolTip> forma bileşen.</span><span class="sxs-lookup"><span data-stu-id="d8e9e-109">In Visual Studio, add a <xref:System.Windows.Forms.ToolTip> component to the form.</span></span>

2. <span data-ttu-id="d8e9e-110">Araç ipucunu görüntülemek veya forma ekler denetimi seçin.</span><span class="sxs-lookup"><span data-stu-id="d8e9e-110">Select the control that will display the ToolTip, or add it to the form.</span></span>

3. <span data-ttu-id="d8e9e-111">İçinde **özellikleri** penceresinde **ToolTip1 araç ipucu** uygun bir metin dizesi değeri.</span><span class="sxs-lookup"><span data-stu-id="d8e9e-111">In the **Properties** window, set the **ToolTip on ToolTip1** value to an appropriate string of text.</span></span>

### <a name="to-remove-a-tooltip-programmatically"></a><span data-ttu-id="d8e9e-112">Bir araç ipucu programlı bir şekilde kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="d8e9e-112">To remove a ToolTip programmatically</span></span>

1. <span data-ttu-id="d8e9e-113">Kullanım <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> yöntemi <xref:System.Windows.Forms.ToolTip> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="d8e9e-113">Use the <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> method of the <xref:System.Windows.Forms.ToolTip> component.</span></span>

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

## <a name="remove-a-tooltip-in-the-designer"></a><span data-ttu-id="d8e9e-114">Tasarımcıda bir araç ipucu Kaldır</span><span class="sxs-lookup"><span data-stu-id="d8e9e-114">Remove a ToolTip in the designer</span></span>

1. <span data-ttu-id="d8e9e-115">Visual Studio'da araç ipucu görüntüleyen bir denetimi seçin.</span><span class="sxs-lookup"><span data-stu-id="d8e9e-115">In Visual Studio, select the control that is displaying the ToolTip.</span></span>

2. <span data-ttu-id="d8e9e-116">İçinde **özellikleri** penceresi, metni silmek **ToolTip1 araç ipucu**.</span><span class="sxs-lookup"><span data-stu-id="d8e9e-116">In the **Properties** window, delete the text in the **ToolTip on ToolTip1**.</span></span>

## <a name="see-also"></a><span data-ttu-id="d8e9e-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d8e9e-117">See also</span></span>

- [<span data-ttu-id="d8e9e-118">ToolTip Bileşenine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="d8e9e-118">ToolTip Component Overview</span></span>](tooltip-component-overview-windows-forms.md)
- [<span data-ttu-id="d8e9e-119">Nasıl yapılır: Windows Forms ToolTip bileşeninin gecikmesini değiştirme</span><span class="sxs-lookup"><span data-stu-id="d8e9e-119">How to: Change the Delay of the Windows Forms ToolTip Component</span></span>](how-to-change-the-delay-of-the-windows-forms-tooltip-component.md)
- [<span data-ttu-id="d8e9e-120">ToolTip Bileşeni</span><span class="sxs-lookup"><span data-stu-id="d8e9e-120">ToolTip Component</span></span>](tooltip-component-windows-forms.md)
