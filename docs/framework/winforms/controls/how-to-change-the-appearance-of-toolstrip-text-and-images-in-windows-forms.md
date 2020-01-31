---
title: 'Nasıl yapılır: ToolStrip metin ve görüntülerinin görünümünü değiştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStrip control [Windows Forms], appearance
- toolbars [Windows Forms], images
- examples [Windows Forms], toolbars
- toolbars [Windows Forms], appearance
- ToolStrip control [Windows Forms], images
- ToolStrip control [Windows Forms], text
- toolbars [Windows Forms], text
ms.assetid: d62dc9d1-2edd-4dfa-aed7-1335d6e13d86
ms.openlocfilehash: 7816e138e44554683c201895ece1f886ace8bfa6
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746602"
---
# <a name="how-to-change-the-appearance-of-toolstrip-text-and-images-in-windows-forms"></a><span data-ttu-id="729d1-102">Nasıl yapılır: Windows Forms'ta ToolStrip Metni ve Resimlerinin Görünüşünü Değiştirme</span><span class="sxs-lookup"><span data-stu-id="729d1-102">How to: Change the Appearance of ToolStrip Text and Images in Windows Forms</span></span>
<span data-ttu-id="729d1-103">Metin ve görüntülerin <xref:System.Windows.Forms.ToolStripItem> gösterilip gösterilmeyeceğini ve bunların birbirlerine ve <xref:System.Windows.Forms.ToolStrip>göre nasıl hizalandığını kontrol edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="729d1-103">You can control whether text and images are displayed on a <xref:System.Windows.Forms.ToolStripItem> and how they are aligned relative to each other and the <xref:System.Windows.Forms.ToolStrip>.</span></span>  
  
### <a name="to-define-what-is-displayed-on-a-toolstripitem"></a><span data-ttu-id="729d1-104">ToolStripItem üzerinde neyin görüntülendiğini tanımlamak için</span><span class="sxs-lookup"><span data-stu-id="729d1-104">To define what is displayed on a ToolStripItem</span></span>  
  
- <span data-ttu-id="729d1-105"><xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> özelliğini istenen değere ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="729d1-105">Set the <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> property to the desired value.</span></span> <span data-ttu-id="729d1-106">`Image`, `ImageAndText`, `None`ve `Text`olanakları vardır.</span><span class="sxs-lookup"><span data-stu-id="729d1-106">The possibilities are `Image`, `ImageAndText`, `None`, and `Text`.</span></span> <span data-ttu-id="729d1-107">Varsayılan, `ImageAndText` değeridir.</span><span class="sxs-lookup"><span data-stu-id="729d1-107">The default is `ImageAndText`.</span></span>  
  
    ```vb  
    ToolStripButton2.DisplayStyle = _  
        System.Windows.Forms.ToolStripItemDisplayStyle.Image  
    ```  
  
    ```csharp  
    toolStripButton2.DisplayStyle = System.Windows.Forms.ToolStripItemDisplayStyle.Image;  
    ```  
  
### <a name="to-align-text-on-a-toolstripitem"></a><span data-ttu-id="729d1-108">Bir ToolStripItem üzerinde metin hizalamak için</span><span class="sxs-lookup"><span data-stu-id="729d1-108">To align text on a ToolStripItem</span></span>  
  
- <span data-ttu-id="729d1-109"><xref:System.Windows.Forms.ToolStripItem.TextAlign%2A> özelliğini istenen değere ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="729d1-109">Set the <xref:System.Windows.Forms.ToolStripItem.TextAlign%2A> property to the desired value.</span></span> <span data-ttu-id="729d1-110">Bu olanaklar, sol, orta ve sağ ile herhangi bir üst, orta ve alt bileşimdir.</span><span class="sxs-lookup"><span data-stu-id="729d1-110">The possibilities are any combination of top, middle, and bottom with left, center, and right.</span></span> <span data-ttu-id="729d1-111">Varsayılan, `MiddleCenter` değeridir.</span><span class="sxs-lookup"><span data-stu-id="729d1-111">The default is `MiddleCenter`.</span></span>  
  
    ```vb  
    ToolStripSplitButton1.TextAlign = _  
        System.Drawing.ContentAlignment.MiddleRight  
    ```  
  
    ```csharp  
    toolStripSplitButton1.TextAlign = System.Drawing.ContentAlignment.MiddleRight;  
    ```  
  
### <a name="to-align-an-image-on-a-toolstripitem"></a><span data-ttu-id="729d1-112">ToolStripItem üzerinde bir görüntüyü hizalamak için</span><span class="sxs-lookup"><span data-stu-id="729d1-112">To align an image on a ToolStripItem</span></span>  
  
- <span data-ttu-id="729d1-113"><xref:System.Windows.Forms.ToolStripItem.ImageAlign%2A> özelliğini istenen değere ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="729d1-113">Set the <xref:System.Windows.Forms.ToolStripItem.ImageAlign%2A> property to the desired value.</span></span> <span data-ttu-id="729d1-114">Bu olanaklar, sol, orta ve sağ ile herhangi bir üst, orta ve alt bileşimdir.</span><span class="sxs-lookup"><span data-stu-id="729d1-114">The possibilities are any combination of top, middle, and bottom with left, center, and right.</span></span> <span data-ttu-id="729d1-115">Varsayılan, `MiddleLeft` değeridir.</span><span class="sxs-lookup"><span data-stu-id="729d1-115">The default is `MiddleLeft`.</span></span>  
  
    ```vb  
    ToolStripSplitButton1.ImageAlign = _  
        System.Drawing.ContentAlignment.MiddleRight  
    ```  
  
    ```csharp  
    toolStripSplitButton1.ImageAlign = System.Drawing.ContentAlignment.MiddleRight;  
    ```  
  
### <a name="to-define-how-toolstripitem-text-and-images-are-displayed-relative-to-each-other"></a><span data-ttu-id="729d1-116">ToolStripItem metninin ve görüntülerinin birbirlerine göre nasıl görüntülendiğini tanımlamak için</span><span class="sxs-lookup"><span data-stu-id="729d1-116">To define how ToolStripItem text and images are displayed relative to each other</span></span>  
  
- <span data-ttu-id="729d1-117"><xref:System.Windows.Forms.ToolStripItem.TextImageRelation%2A> özelliğini istenen değere ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="729d1-117">Set the <xref:System.Windows.Forms.ToolStripItem.TextImageRelation%2A> property to the desired value.</span></span> <span data-ttu-id="729d1-118">`ImageAboveText`, `ImageBeforeText`, `Overlay`, `TextAboveImage`ve `TextBeforeImage`olanakları vardır.</span><span class="sxs-lookup"><span data-stu-id="729d1-118">The possibilities are `ImageAboveText`, `ImageBeforeText`, `Overlay`, `TextAboveImage`, and `TextBeforeImage`.</span></span> <span data-ttu-id="729d1-119">Varsayılan, `ImageBeforeText` değeridir.</span><span class="sxs-lookup"><span data-stu-id="729d1-119">The default is `ImageBeforeText`.</span></span>  
  
    ```vb  
    ToolStripButton1.TextImageRelation = _  
        System.Windows.Forms.TextImageRelation.ImageAboveText  
    ```  
  
    ```csharp  
    toolStripButton1.TextImageRelation = System.Windows.Forms.TextImageRelation.ImageAboveText;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="729d1-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="729d1-120">See also</span></span>

- <xref:System.Windows.Forms.ToolStrip>
- [<span data-ttu-id="729d1-121">ToolStrip Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="729d1-121">ToolStrip Control Overview</span></span>](toolstrip-control-overview-windows-forms.md)
- [<span data-ttu-id="729d1-122">ToolStrip Denetim, Mimarisi</span><span class="sxs-lookup"><span data-stu-id="729d1-122">ToolStrip Control Architecture</span></span>](toolstrip-control-architecture.md)
- [<span data-ttu-id="729d1-123">ToolStrip Teknoloji Özeti</span><span class="sxs-lookup"><span data-stu-id="729d1-123">ToolStrip Technology Summary</span></span>](toolstrip-technology-summary.md)
