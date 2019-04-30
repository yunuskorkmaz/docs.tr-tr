---
title: 'Nasıl yapılır: Bölünmüş Pencerede Yeniden Boyutlandırma ve Konumlama Davranışını Tanımlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- split windows [Windows Forms], resizing
- splitter windows [Windows Forms], resizing
- SplitContainer control [Windows Forms], resizing
ms.assetid: 9bf73f36-ed2d-4a02-b15a-0770eff4fdfa
ms.openlocfilehash: 8cdcfdfaa135a92ed6a6e96d4a72de2c97f2493d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61757631"
---
# <a name="how-to-define-resize-and-positioning-behavior-in-a-split-window"></a><span data-ttu-id="ba6a0-102">Nasıl yapılır: Bölünmüş Pencerede Yeniden Boyutlandırma ve Konumlama Davranışını Tanımlama</span><span class="sxs-lookup"><span data-stu-id="ba6a0-102">How to: Define Resize and Positioning Behavior in a Split Window</span></span>
<span data-ttu-id="ba6a0-103">Bölmelerden <xref:System.Windows.Forms.SplitContainer> denetim kiralamak kendileri de olmak için yeniden boyutlandırılabilir ve kullanıcılar tarafından yönetilebilir.</span><span class="sxs-lookup"><span data-stu-id="ba6a0-103">The panels of the <xref:System.Windows.Forms.SplitContainer> control lend themselves well to being resized and manipulated by users.</span></span> <span data-ttu-id="ba6a0-104">Ancak, olacaktır istediğinizde Bölümlendirici programlı olarak denetlemek için bir kez — burada yer alır ve ne derece taşınabilir.</span><span class="sxs-lookup"><span data-stu-id="ba6a0-104">However, there will be times when you will want to programmatically control the splitter—where it is positioned and to what degree it can be moved.</span></span>  
  
 <span data-ttu-id="ba6a0-105"><xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> Özelliği ve diğer özellikleri <xref:System.Windows.Forms.SplitContainer> denetim gereksinimlerinize uyacak şekilde, kullanıcı arabiriminin davranışı üzerinde kesin denetim verir.</span><span class="sxs-lookup"><span data-stu-id="ba6a0-105">The <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> property and the other properties on the <xref:System.Windows.Forms.SplitContainer> control give you precise control over the behavior of your user interface to suit your needs.</span></span> <span data-ttu-id="ba6a0-106">Bu özellikler aşağıdaki tabloda listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="ba6a0-106">These properties are listed in the following table.</span></span>  
  
|<span data-ttu-id="ba6a0-107">Ad</span><span class="sxs-lookup"><span data-stu-id="ba6a0-107">Name</span></span>|<span data-ttu-id="ba6a0-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ba6a0-108">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="ba6a0-109"><xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> Özelliği</span><span class="sxs-lookup"><span data-stu-id="ba6a0-109"><xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> property</span></span>|<span data-ttu-id="ba6a0-110">Bölümlendirici klavye veya fare yoluyla taşınabilir olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="ba6a0-110">Determines if the splitter is movable by means of the keyboard or mouse.</span></span>|  
|<span data-ttu-id="ba6a0-111"><xref:System.Windows.Forms.SplitContainer.SplitterDistance%2A> Özelliği</span><span class="sxs-lookup"><span data-stu-id="ba6a0-111"><xref:System.Windows.Forms.SplitContainer.SplitterDistance%2A> property</span></span>|<span data-ttu-id="ba6a0-112">Taşınabilir ayırıcıyı için sol veya üst kenarından piksel cinsinden uzaklığı belirler.</span><span class="sxs-lookup"><span data-stu-id="ba6a0-112">Determines the distance in pixels from the left or upper edge to the movable splitter bar.</span></span>|  
|<span data-ttu-id="ba6a0-113"><xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> Özelliği</span><span class="sxs-lookup"><span data-stu-id="ba6a0-113"><xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> property</span></span>|<span data-ttu-id="ba6a0-114">Bölümlendirici kullanıcı tarafından taşınabilir piksel cinsinden en düşük bir uzaklık belirler.</span><span class="sxs-lookup"><span data-stu-id="ba6a0-114">Determines the minimum distance, in pixels, that the splitter can be moved by the user.</span></span>|  
  
 <span data-ttu-id="ba6a0-115">Aşağıdaki örnekte değiştirir <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> özelliği bir "Bölücü Yaslama" etkisi; oluşturmak için bir kullanıcı bir ayırıcıyı sürüklediğinde, 1 varsayılan değer yerine 10 piksel birimleri cinsinden artırır.</span><span class="sxs-lookup"><span data-stu-id="ba6a0-115">The example below modifies the <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> property to create a "snapping splitter" effect; when the user drags the splitter, it increments in units of 10 pixels rather than the default 1.</span></span>  
  
### <a name="to-define-splitcontainer-resize-behavior"></a><span data-ttu-id="ba6a0-116">SplitContainer yeniden boyutlandırma davranışını tanımlamak için</span><span class="sxs-lookup"><span data-stu-id="ba6a0-116">To define SplitContainer resize behavior</span></span>  
  
1. <span data-ttu-id="ba6a0-117">Bir yordamda <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> özelliğini istenen boyut, böylece ayırıcı 'Yaslama' davranışını elde edilir.</span><span class="sxs-lookup"><span data-stu-id="ba6a0-117">In a procedure, set the <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> property to the desired size, so that the 'snapping' behavior of the splitter is achieved.</span></span>  
  
     <span data-ttu-id="ba6a0-118">Aşağıdaki kod örneğinde, formun içinde <xref:System.Windows.Forms.Form.Load> olay, bölümlendirici içinde <xref:System.Windows.Forms.SplitContainer> denetim sürüklendiğinde 10 piksel atlamak için ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="ba6a0-118">In the following code example, within the form's <xref:System.Windows.Forms.Form.Load> event, the splitter within the <xref:System.Windows.Forms.SplitContainer> control is set to jump 10 pixels when dragged.</span></span>  
  
    ```vb  
    Private Sub Form1_Load(ByVal sender As System.Object, _  
        ByVal e As System.EventArgs) Handles MyBase.Load  
        Dim splitSnapper as new SplitContainer()  
        splitSnapper.SplitterIncrement = 10  
        splitSnapper.Dock = DockStyle.Fill  
        splitSnapper.Parent = me  
    End Sub  
    ```  
  
    ```csharp  
    private void Form1_Load(System.Object sender, System.EventArgs e)  
    {  
        SplitContainer splitSnapper = new SplitContainer();  
        splitSnapper.SplitterIncrement = 10;  
        splitSnapper.Dock = DockStyle.Fill;  
        splitSnapper.Parent = this;  
    }  
    ```  
  
     <span data-ttu-id="ba6a0-119">(Visual C#) Aşağıdaki kod, olay işleyicisi kaydetmek için formun oluşturucuda yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="ba6a0-119">(Visual C#) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.Load += new System.EventHandler(this.Form1_Load);  
    ```  
  
     <span data-ttu-id="ba6a0-120">Bölümlendirici biraz sola veya sağa hareket anlaşılabilir etkisi olmayacak; Ancak, fare işaretçisini herhangi bir yönde 10 piksel gittiğinde, bölümlendirici yeni konumuna yaslanacak.</span><span class="sxs-lookup"><span data-stu-id="ba6a0-120">Moving the splitter slightly to the left or right will have no discernible effect; however, when the mouse pointer goes 10 pixels in either direction, the splitter will snap to the new position.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba6a0-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ba6a0-121">See also</span></span>

- <xref:System.Windows.Forms.SplitContainer>
- <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A>
