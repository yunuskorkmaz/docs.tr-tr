---
title: 'Nasıl yapilir: ToolStrip Öğelerinin Aralığını ve Hizalamasını Değiştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStrip control [Windows Forms], aligning items
- examples [Windows Forms], toolbars
- toolbars [Windows Forms], aligning items
ms.assetid: cd483466-0f49-43df-addf-e2b5fcd64027
ms.openlocfilehash: 550ac1660a077e8d766a01bfa8d102c07f0fbfeb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182238"
---
# <a name="how-to-change-the-spacing-and-alignment-of-toolstrip-items-in-windows-forms"></a><span data-ttu-id="1d886-102">Nasıl yapılır: Windows Forms'ta ToolStrip Öğelerinin Aralık ve Hizalamasını Değiştirme</span><span class="sxs-lookup"><span data-stu-id="1d886-102">How to: Change the Spacing and Alignment of ToolStrip Items in Windows Forms</span></span>
<span data-ttu-id="1d886-103">Denetim, <xref:System.Windows.Forms.ToolStrip> boyutlandırma, denetimlerin birbirine göre aralıkları, <xref:System.Windows.Forms.ToolStripItem> denetimlerin <xref:System.Windows.Forms.ToolStrip>düzenlenmesi ve denetimlerin belirli olması gibi düzen özelliklerini tam <xref:System.Windows.Forms.ToolStrip>olarak destekler.</span><span class="sxs-lookup"><span data-stu-id="1d886-103">The <xref:System.Windows.Forms.ToolStrip> control fully supports layout features such as sizing, the spacing of <xref:System.Windows.Forms.ToolStripItem> controls relative to each other, the arrangement of controls on the <xref:System.Windows.Forms.ToolStrip>, and the spacing of controls relative to the <xref:System.Windows.Forms.ToolStrip>.</span></span>  
  
 <span data-ttu-id="1d886-104">Özelliğin <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> varsayılan değeri `true`olduğundan, <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> özelliği `false`'ne ayarlamadığınız sürece denetimler otomatik olarak boyutlandırılır.</span><span class="sxs-lookup"><span data-stu-id="1d886-104">Because the default value of the <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> property is `true`, controls are sized automatically unless you set the <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> property to `false`.</span></span>  
  
### <a name="to-manually-size-a-toolstripitem"></a><span data-ttu-id="1d886-105">ToolStripItem'i el ile boyutlandırmak için</span><span class="sxs-lookup"><span data-stu-id="1d886-105">To manually size a ToolStripItem</span></span>  
  
1. <span data-ttu-id="1d886-106">İlişkili <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> denetim `false` için özelliği ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="1d886-106">Set the <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> property to `false` for the associated control.</span></span>  
  
    ```vb  
    ToolStripButton1.AutoSize = False  
    ```  
  
    ```csharp  
    toolStripButton1.AutoSize = false;  
    ```  
  
2. <span data-ttu-id="1d886-107"><xref:System.Windows.Forms.ToolStripItem.Size%2A> Özelliği ilişkili <xref:System.Windows.Forms.ToolStripItem>için istediğiniz şekilde ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="1d886-107">Set the <xref:System.Windows.Forms.ToolStripItem.Size%2A> property the way you want for the associated <xref:System.Windows.Forms.ToolStripItem>.</span></span>  
  
### <a name="to-set-the-spacing-of-a-toolstripitem"></a><span data-ttu-id="1d886-108">ToolStripItem'in aralığını ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="1d886-108">To set the spacing of a ToolStripItem</span></span>  
  
1. <span data-ttu-id="1d886-109">İstenilen değerleri pikselolarak ilişkili <xref:System.Windows.Forms.ToolStripItem.Margin%2A> denetimin özelliğine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1d886-109">Insert the desired values, in pixels, into the <xref:System.Windows.Forms.ToolStripItem.Margin%2A> property of the associated control.</span></span>  
  
     <span data-ttu-id="1d886-110"><xref:System.Windows.Forms.ToolStripItem.Margin%2A> Özelliğin değerleri bu sırada madde ve bitişik öğeler arasındaki aralığı belirtir: Sol, Üst, Sağ ve Alt.</span><span class="sxs-lookup"><span data-stu-id="1d886-110">The values of the <xref:System.Windows.Forms.ToolStripItem.Margin%2A> property specify the spacing between the item and adjacent items in this order: Left, Top, Right, and Bottom.</span></span>  
  
    ```vb  
    ToolStripTextBox1.Margin = New System.Windows.Forms.Padding _  
        (3, 0, 3, 0)  
    ```  
  
    ```csharp  
    toolStripTextBox1.Margin = new System.Windows.Forms.Padding
        (3, 0, 3, 0);  
    ```  
  
### <a name="to-align-a-toolstripitem-to-the-right-side-of-the-toolstrip"></a><span data-ttu-id="1d886-111">ToolStripItem'i ToolStrip'in sağ tarafına hizalamak için</span><span class="sxs-lookup"><span data-stu-id="1d886-111">To align a ToolStripItem to the right side of the ToolStrip</span></span>  
  
1. <span data-ttu-id="1d886-112">İlişkili <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> denetim <xref:System.Windows.Forms.ToolStripItemAlignment.Right> için özelliği ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="1d886-112">Set the <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> property to <xref:System.Windows.Forms.ToolStripItemAlignment.Right> for the associated control.</span></span> <span data-ttu-id="1d886-113">Varsayılan olarak, <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> denetimleri sol tarafa hizalayan <xref:System.Windows.Forms.ToolStripItemAlignment.Left> <xref:System.Windows.Forms.ToolStrip>, olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="1d886-113">By default, <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> is set to <xref:System.Windows.Forms.ToolStripItemAlignment.Left>, which aligns controls to the left side of the <xref:System.Windows.Forms.ToolStrip>.</span></span>  
  
    ```vb  
    ToolStripSplitButton1.Alignment = _  
        System.Windows.Forms.ToolStripItemAlignment.Right  
    ```  
  
    ```csharp  
    toolStripSplitButton1.Alignment =
        System.Windows.Forms.ToolStripItemAlignment.Right;  
    ```  
  
### <a name="to-arrange-toolstrip-items-on-the-toolstrip"></a><span data-ttu-id="1d886-114">ToolStrip'teki ToolStrip öğelerini düzenlemek için</span><span class="sxs-lookup"><span data-stu-id="1d886-114">To arrange ToolStrip items on the ToolStrip</span></span>  
  
- <span data-ttu-id="1d886-115"><xref:System.Windows.Forms.ToolStrip.LayoutStyle%2A> Özelliği istediğiniz değere <xref:System.Windows.Forms.ToolStripLayoutStyle> ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="1d886-115">Set the <xref:System.Windows.Forms.ToolStrip.LayoutStyle%2A> property to the value of <xref:System.Windows.Forms.ToolStripLayoutStyle> that you want.</span></span>  
  
    ```vb  
    ToolStripDropDown1.LayoutStyle = _  
        System.Windows.Forms.ToolStripLayoutStyle.Flow  
    ```  
  
    ```csharp  
    toolStripDropDown1.LayoutStyle =
        System.Windows.Forms.ToolStripLayoutStyle.Flow;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="1d886-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1d886-116">See also</span></span>

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.Control.Layout>
- <xref:System.Windows.Forms.ToolStrip.LayoutCompleted>
- <xref:System.Windows.Forms.ToolStrip.LayoutSettings%2A>
- <xref:System.Windows.Forms.ToolStripItem.TextImageRelation%2A>
- <xref:System.Windows.Forms.ToolStripItem.Placement%2A>
- <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A>
- [<span data-ttu-id="1d886-117">ToolStrip Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="1d886-117">ToolStrip Control Overview</span></span>](toolstrip-control-overview-windows-forms.md)
- [<span data-ttu-id="1d886-118">ToolStrip Denetim, Mimarisi</span><span class="sxs-lookup"><span data-stu-id="1d886-118">ToolStrip Control Architecture</span></span>](toolstrip-control-architecture.md)
- [<span data-ttu-id="1d886-119">ToolStrip Teknoloiji Özeti</span><span class="sxs-lookup"><span data-stu-id="1d886-119">ToolStrip Technology Summary</span></span>](toolstrip-technology-summary.md)
