---
title: Araç Ipucu bileşeni gecikmesini değiştirme
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
ms.openlocfilehash: 8ab0b0760e8c82d752eaada19f14cae57fa63fdc
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746582"
---
# <a name="how-to-change-the-delay-of-the-windows-forms-tooltip-component"></a><span data-ttu-id="2f4c7-102">Nasıl yapılır: Windows Forms ToolTip Bileşeninin Gecikmesini Değiştirme</span><span class="sxs-lookup"><span data-stu-id="2f4c7-102">How to: Change the Delay of the Windows Forms ToolTip Component</span></span>
<span data-ttu-id="2f4c7-103">Bir Windows Forms <xref:System.Windows.Forms.ToolTip> bileşeni için ayarlayabileceğiniz birden fazla gecikme değeri vardır.</span><span class="sxs-lookup"><span data-stu-id="2f4c7-103">There are multiple delay values that you can set for a Windows Forms <xref:System.Windows.Forms.ToolTip> component.</span></span> <span data-ttu-id="2f4c7-104">Tüm bu özellikler için ölçü birimi milisaniyedir.</span><span class="sxs-lookup"><span data-stu-id="2f4c7-104">The unit of measure for all these properties is milliseconds.</span></span> <span data-ttu-id="2f4c7-105"><xref:System.Windows.Forms.ToolTip.InitialDelay%2A> özelliği, kullanıcının araç Ipucu dizesinin görünmesi için ilgili denetimi ne kadar süreyle göstermesi gerektiğini belirler.</span><span class="sxs-lookup"><span data-stu-id="2f4c7-105">The <xref:System.Windows.Forms.ToolTip.InitialDelay%2A> property determines how long the user must point at the associated control for the ToolTip string to appear.</span></span> <span data-ttu-id="2f4c7-106"><xref:System.Windows.Forms.ToolTip.ReshowDelay%2A> özelliği, fare Ipucu ile ilişkili bir denetimden diğerine geçirken sonraki araç Ipucu dizelerinin görünmesi için geçen milisaniye sayısını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="2f4c7-106">The <xref:System.Windows.Forms.ToolTip.ReshowDelay%2A> property sets the number of milliseconds it takes for subsequent ToolTip strings to appear as the mouse moves from one ToolTip-associated control to another.</span></span> <span data-ttu-id="2f4c7-107"><xref:System.Windows.Forms.ToolTip.AutoPopDelay%2A> özelliği, ToolTip dizesinin gösterdiği sürenin uzunluğunu belirler.</span><span class="sxs-lookup"><span data-stu-id="2f4c7-107">The <xref:System.Windows.Forms.ToolTip.AutoPopDelay%2A> property determines the length of time the ToolTip string is shown.</span></span> <span data-ttu-id="2f4c7-108">Bu değerleri ayrı ayrı veya <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> özelliğinin değerini ayarlayarak ayarlayabilirsiniz; diğer gecikme özellikleri, <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> özelliğine atanan değere göre ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="2f4c7-108">You can set these values individually, or by setting the value of the <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> property; the other delay properties are set based on the value assigned to the <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> property.</span></span> <span data-ttu-id="2f4c7-109">Örneğin, <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> bir değeri N olarak ayarlandığında <xref:System.Windows.Forms.ToolTip.InitialDelay%2A> N olarak ayarlanır <xref:System.Windows.Forms.ToolTip.ReshowDelay%2A>, beş (veya N/5) bölünen <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> değerine ayarlanır ve <xref:System.Windows.Forms.ToolTip.AutoPopDelay%2A> <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> özelliğinin değeri beş kat olan bir değere ayarlanır (veya 5N).</span><span class="sxs-lookup"><span data-stu-id="2f4c7-109">For example, when <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> is set to a value N, <xref:System.Windows.Forms.ToolTip.InitialDelay%2A> is set to N, <xref:System.Windows.Forms.ToolTip.ReshowDelay%2A> is set to the value of <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> divided by five (or N/5), and <xref:System.Windows.Forms.ToolTip.AutoPopDelay%2A> is set to a value that is five times the value of the <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> property (or 5N).</span></span>  
  
### <a name="to-set-the-delay"></a><span data-ttu-id="2f4c7-110">Gecikmeyi ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="2f4c7-110">To set the delay</span></span>  
  
1. <span data-ttu-id="2f4c7-111">Aşağıdaki özellikleri bu örnekte gösterildiği gibi ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="2f4c7-111">Set the following properties as shown in this example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2f4c7-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2f4c7-112">See also</span></span>

- [<span data-ttu-id="2f4c7-113">ToolTip Bileşenine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="2f4c7-113">ToolTip Component Overview</span></span>](tooltip-component-overview-windows-forms.md)
- [<span data-ttu-id="2f4c7-114">Nasıl yapılır: Tasarım Zamanında Windows Formundaki Denetimler için ToolTips Ayarlama</span><span class="sxs-lookup"><span data-stu-id="2f4c7-114">How to: Set ToolTips for Controls on a Windows Form at Design Time</span></span>](how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time.md)
- [<span data-ttu-id="2f4c7-115">ToolTip Bileşeni</span><span class="sxs-lookup"><span data-stu-id="2f4c7-115">ToolTip Component</span></span>](tooltip-component-windows-forms.md)
