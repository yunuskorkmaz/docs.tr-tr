---
title: 'Nasıl yapılır: Windows Forms ToolTip Bileşeninin Gecikmesini Değiştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- ToolTip component [Windows Forms], delay values
- tooltips [Windows Forms], delay values
- examples [Windows Forms], tooltips
ms.assetid: 08979ba7-dd84-477b-ab17-8d06e759be99
ms.openlocfilehash: cf257cccd272c16c3d7c3d403456265444fc8ac8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59345488"
---
# <a name="how-to-change-the-delay-of-the-windows-forms-tooltip-component"></a><span data-ttu-id="e83da-102">Nasıl yapılır: Windows Forms ToolTip Bileşeninin Gecikmesini Değiştirme</span><span class="sxs-lookup"><span data-stu-id="e83da-102">How to: Change the Delay of the Windows Forms ToolTip Component</span></span>
<span data-ttu-id="e83da-103">Bir Windows Forms için ayarlayabileceğiniz birden fazla gecikme değerleri vardır <xref:System.Windows.Forms.ToolTip> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="e83da-103">There are multiple delay values that you can set for a Windows Forms <xref:System.Windows.Forms.ToolTip> component.</span></span> <span data-ttu-id="e83da-104">Tüm bu özellikler için ölçü birimini milisaniyedir.</span><span class="sxs-lookup"><span data-stu-id="e83da-104">The unit of measure for all these properties is milliseconds.</span></span> <span data-ttu-id="e83da-105"><xref:System.Windows.Forms.ToolTip.InitialDelay%2A> Özelliği belirler ilişkili denetim için görüntülenecek araç ipucu dize, kullanıcının ne kadar süreyle işaret etmelidir.</span><span class="sxs-lookup"><span data-stu-id="e83da-105">The <xref:System.Windows.Forms.ToolTip.InitialDelay%2A> property determines how long the user must point at the associated control for the ToolTip string to appear.</span></span> <span data-ttu-id="e83da-106"><xref:System.Windows.Forms.ToolTip.ReshowDelay%2A> Özelliği bir araç ipucu ilişkili denetimden fareyi hareket ettirdikçe görüntülenecek araç ipucu dizeler sonraki geçen milisaniye sayısını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="e83da-106">The <xref:System.Windows.Forms.ToolTip.ReshowDelay%2A> property sets the number of milliseconds it takes for subsequent ToolTip strings to appear as the mouse moves from one ToolTip-associated control to another.</span></span> <span data-ttu-id="e83da-107"><xref:System.Windows.Forms.ToolTip.AutoPopDelay%2A> Özelliği, araç ipucu dize gösterilir sürenin uzunluğunu belirler.</span><span class="sxs-lookup"><span data-stu-id="e83da-107">The <xref:System.Windows.Forms.ToolTip.AutoPopDelay%2A> property determines the length of time the ToolTip string is shown.</span></span> <span data-ttu-id="e83da-108">Tek tek veya değerini ayarlayarak bu değerleri ayarlayabileceğiniz <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> özelliği; özellikleri için atanan değer baz alınarak ayarlanır gecikme <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="e83da-108">You can set these values individually, or by setting the value of the <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> property; the other delay properties are set based on the value assigned to the <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> property.</span></span> <span data-ttu-id="e83da-109">Örneğin, <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> N değerine ayarlanır <xref:System.Windows.Forms.ToolTip.InitialDelay%2A> N-ayarlanır <xref:System.Windows.Forms.ToolTip.ReshowDelay%2A> değerine ayarlanır <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> beş aralıktaki (veya 5/N) ve <xref:System.Windows.Forms.ToolTip.AutoPopDelay%2A> beş kez değeri olan bir değere ayarlanmış <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> özelliği (veya 5N).</span><span class="sxs-lookup"><span data-stu-id="e83da-109">For example, when <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> is set to a value N, <xref:System.Windows.Forms.ToolTip.InitialDelay%2A> is set to N, <xref:System.Windows.Forms.ToolTip.ReshowDelay%2A> is set to the value of <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> divided by five (or N/5), and <xref:System.Windows.Forms.ToolTip.AutoPopDelay%2A> is set to a value that is five times the value of the <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> property (or 5N).</span></span>  
  
### <a name="to-set-the-delay"></a><span data-ttu-id="e83da-110">Gecikme süresini ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="e83da-110">To set the delay</span></span>  
  
1. <span data-ttu-id="e83da-111">Bu örnekte gösterildiği gibi aşağıdaki özellikleri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="e83da-111">Set the following properties as shown in this example.</span></span>  
  
    ```vb  
    ToolTip1.InitialDelay = 500  
    ToolTip1.ReshowDelay = 100  
    ToolTip1.AutoPopDelay = 5000  
    ```  
  
    ```csharp  
    ToolTip1.InitialDelay = 500;  
    ToolTip1.ReshowDelay = 100;  
    ToolTip1.AutoPopDelay = 5000;  
    ```  
  
    ```cpp  
    toolTip1->InitialDelay = 500;  
    toolTip1->ReshowDelay = 100;  
    toolTip1->AutoPopDelay = 5000;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="e83da-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e83da-112">See also</span></span>

- [<span data-ttu-id="e83da-113">ToolTip Bileşenine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="e83da-113">ToolTip Component Overview</span></span>](tooltip-component-overview-windows-forms.md)
- [<span data-ttu-id="e83da-114">Nasıl yapılır: Tasarım zamanında bir Windows formundaki denetimler için ToolTips ayarlama</span><span class="sxs-lookup"><span data-stu-id="e83da-114">How to: Set ToolTips for Controls on a Windows Form at Design Time</span></span>](how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time.md)
- [<span data-ttu-id="e83da-115">ToolTip Bileşeni</span><span class="sxs-lookup"><span data-stu-id="e83da-115">ToolTip Component</span></span>](tooltip-component-windows-forms.md)
