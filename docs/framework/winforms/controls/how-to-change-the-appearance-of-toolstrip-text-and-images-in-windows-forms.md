---
title: "Nasıl yapılır: ToolStrip metni ve görüntülerinin Windows Forms'ta görünüşünü değiştirme"
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
ms.openlocfilehash: cd15e581e646f53ed56af654917c7543bf18617e
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57705408"
---
# <a name="how-to-change-the-appearance-of-toolstrip-text-and-images-in-windows-forms"></a><span data-ttu-id="5dbb5-102">Nasıl yapılır: ToolStrip metni ve görüntülerinin Windows Forms'ta görünüşünü değiştirme</span><span class="sxs-lookup"><span data-stu-id="5dbb5-102">How to: Change the Appearance of ToolStrip Text and Images in Windows Forms</span></span>
<span data-ttu-id="5dbb5-103">Metin ve görüntüleri üzerinde görüntülenip görüntülenmeyeceğini denetleyebileceğiniz bir <xref:System.Windows.Forms.ToolStripItem> ve nasıl birbirlerine göreli hizalandığını ve <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="5dbb5-103">You can control whether text and images are displayed on a <xref:System.Windows.Forms.ToolStripItem> and how they are aligned relative to each other and the <xref:System.Windows.Forms.ToolStrip>.</span></span>  
  
### <a name="to-define-what-is-displayed-on-a-toolstripitem"></a><span data-ttu-id="5dbb5-104">Üzerinde ToolStripItem görüntülenenleri tanımlamak için</span><span class="sxs-lookup"><span data-stu-id="5dbb5-104">To define what is displayed on a ToolStripItem</span></span>  
  
-   <span data-ttu-id="5dbb5-105">Ayarlama <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> özelliğini istediğiniz değer.</span><span class="sxs-lookup"><span data-stu-id="5dbb5-105">Set the <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> property to the desired value.</span></span> <span data-ttu-id="5dbb5-106">Olasılıklar `Image`, `ImageAndText`, `None`, ve `Text`.</span><span class="sxs-lookup"><span data-stu-id="5dbb5-106">The possibilities are `Image`, `ImageAndText`, `None`, and `Text`.</span></span> <span data-ttu-id="5dbb5-107">Varsayılan, `ImageAndText` değeridir.</span><span class="sxs-lookup"><span data-stu-id="5dbb5-107">The default is `ImageAndText`.</span></span>  
  
    ```vb  
    ToolStripButton2.DisplayStyle = _  
        System.Windows.Forms.ToolStripItemDisplayStyle.Image  
    ```  
  
    ```csharp  
    toolStripButton2.DisplayStyle = System.Windows.Forms.ToolStripItemDisplayStyle.Image;  
    ```  
  
### <a name="to-align-text-on-a-toolstripitem"></a><span data-ttu-id="5dbb5-108">ToolStripItem metni hizalama</span><span class="sxs-lookup"><span data-stu-id="5dbb5-108">To align text on a ToolStripItem</span></span>  
  
-   <span data-ttu-id="5dbb5-109">Ayarlama <xref:System.Windows.Forms.ToolStripItem.TextAlign%2A> özelliğini istediğiniz değer.</span><span class="sxs-lookup"><span data-stu-id="5dbb5-109">Set the <xref:System.Windows.Forms.ToolStripItem.TextAlign%2A> property to the desired value.</span></span> <span data-ttu-id="5dbb5-110">Olasılıkları üstünde, Orta ve alt sol, Orta ve sağ ile herhangi bir birleşimini şunlardır.</span><span class="sxs-lookup"><span data-stu-id="5dbb5-110">The possibilities are any combination of top, middle, and bottom with left, center, and right.</span></span> <span data-ttu-id="5dbb5-111">Varsayılan, `MiddleCenter` değeridir.</span><span class="sxs-lookup"><span data-stu-id="5dbb5-111">The default is `MiddleCenter`.</span></span>  
  
    ```vb  
    ToolStripSplitButton1.TextAlign = _  
        System.Drawing.ContentAlignment.MiddleRight  
    ```  
  
    ```csharp  
    toolStripSplitButton1.TextAlign = System.Drawing.ContentAlignment.MiddleRight;  
    ```  
  
### <a name="to-align-an-image-on-a-toolstripitem"></a><span data-ttu-id="5dbb5-112">Görüntünün üzerinde ToolStripItem hizalamak için</span><span class="sxs-lookup"><span data-stu-id="5dbb5-112">To align an image on a ToolStripItem</span></span>  
  
-   <span data-ttu-id="5dbb5-113">Ayarlama <xref:System.Windows.Forms.ToolStripItem.ImageAlign%2A> özelliğini istediğiniz değer.</span><span class="sxs-lookup"><span data-stu-id="5dbb5-113">Set the <xref:System.Windows.Forms.ToolStripItem.ImageAlign%2A> property to the desired value.</span></span> <span data-ttu-id="5dbb5-114">Olasılıkları üstünde, Orta ve alt sol, Orta ve sağ ile herhangi bir birleşimini şunlardır.</span><span class="sxs-lookup"><span data-stu-id="5dbb5-114">The possibilities are any combination of top, middle, and bottom with left, center, and right.</span></span> <span data-ttu-id="5dbb5-115">Varsayılan, `MiddleLeft` değeridir.</span><span class="sxs-lookup"><span data-stu-id="5dbb5-115">The default is `MiddleLeft`.</span></span>  
  
    ```vb  
    ToolStripSplitButton1.ImageAlign = _  
        System.Drawing.ContentAlignment.MiddleRight  
    ```  
  
    ```csharp  
    toolStripSplitButton1.ImageAlign = System.Drawing.ContentAlignment.MiddleRight;  
    ```  
  
### <a name="to-define-how-toolstripitem-text-and-images-are-displayed-relative-to-each-other"></a><span data-ttu-id="5dbb5-116">ToolStripItem metin ve görüntüleri birbirine göre nasıl görüntüleneceğini tanımlamak için</span><span class="sxs-lookup"><span data-stu-id="5dbb5-116">To define how ToolStripItem text and images are displayed relative to each other</span></span>  
  
-   <span data-ttu-id="5dbb5-117">Ayarlama <xref:System.Windows.Forms.ToolStripItem.TextImageRelation%2A> özelliğini istediğiniz değer.</span><span class="sxs-lookup"><span data-stu-id="5dbb5-117">Set the <xref:System.Windows.Forms.ToolStripItem.TextImageRelation%2A> property to the desired value.</span></span> <span data-ttu-id="5dbb5-118">Olasılıklar `ImageAboveText`, `ImageBeforeText`, `Overlay`, `TextAboveImage`, ve `TextBeforeImage`.</span><span class="sxs-lookup"><span data-stu-id="5dbb5-118">The possibilities are `ImageAboveText`, `ImageBeforeText`, `Overlay`, `TextAboveImage`, and `TextBeforeImage`.</span></span> <span data-ttu-id="5dbb5-119">Varsayılan, `ImageBeforeText` değeridir.</span><span class="sxs-lookup"><span data-stu-id="5dbb5-119">The default is `ImageBeforeText`.</span></span>  
  
    ```vb  
    ToolStripButton1.TextImageRelation = _  
        System.Windows.Forms.TextImageRelation.ImageAboveText  
    ```  
  
    ```csharp  
    toolStripButton1.TextImageRelation = System.Windows.Forms.TextImageRelation.ImageAboveText;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="5dbb5-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5dbb5-120">See also</span></span>
- <xref:System.Windows.Forms.ToolStrip>
- [<span data-ttu-id="5dbb5-121">ToolStrip Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="5dbb5-121">ToolStrip Control Overview</span></span>](toolstrip-control-overview-windows-forms.md)
- [<span data-ttu-id="5dbb5-122">ToolStrip Denetim, Mimarisi</span><span class="sxs-lookup"><span data-stu-id="5dbb5-122">ToolStrip Control Architecture</span></span>](toolstrip-control-architecture.md)
- [<span data-ttu-id="5dbb5-123">ToolStrip Teknoloji Özeti</span><span class="sxs-lookup"><span data-stu-id="5dbb5-123">ToolStrip Technology Summary</span></span>](toolstrip-technology-summary.md)
