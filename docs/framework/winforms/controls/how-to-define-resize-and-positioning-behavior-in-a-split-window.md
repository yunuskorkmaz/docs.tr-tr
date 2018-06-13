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
ms.openlocfilehash: 015e93fb551b8d48b8a57662b8def61c3cb46c2a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33531641"
---
# <a name="how-to-define-resize-and-positioning-behavior-in-a-split-window"></a><span data-ttu-id="71c9e-102">Nasıl yapılır: Bölünmüş Pencerede Yeniden Boyutlandırma ve Konumlama Davranışını Tanımlama</span><span class="sxs-lookup"><span data-stu-id="71c9e-102">How to: Define Resize and Positioning Behavior in a Split Window</span></span>
<span data-ttu-id="71c9e-103">Bölmelerden <xref:System.Windows.Forms.SplitContainer> denetim ödünç kendilerini iyi duruma yeniden boyutlandırılabilir ve kullanıcılar tarafından yönetilebilir.</span><span class="sxs-lookup"><span data-stu-id="71c9e-103">The panels of the <xref:System.Windows.Forms.SplitContainer> control lend themselves well to being resized and manipulated by users.</span></span> <span data-ttu-id="71c9e-104">Ancak, olacaktır istediğinizde Bölümlendirici programlı olarak denetlemek için kez — burada yer alır ve ne derece taşınabilmesi.</span><span class="sxs-lookup"><span data-stu-id="71c9e-104">However, there will be times when you will want to programmatically control the splitter—where it is positioned and to what degree it can be moved.</span></span>  
  
 <span data-ttu-id="71c9e-105"><xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> Özelliği ve diğer özellikleri <xref:System.Windows.Forms.SplitContainer> denetim gereksinimlerinize uygun olarak, kullanıcı arabiriminizi davranışını üzerinde Tam Denetim verin.</span><span class="sxs-lookup"><span data-stu-id="71c9e-105">The <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> property and the other properties on the <xref:System.Windows.Forms.SplitContainer> control give you precise control over the behavior of your user interface to suit your needs.</span></span> <span data-ttu-id="71c9e-106">Bu özellikler aşağıdaki tabloda listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="71c9e-106">These properties are listed in the following table.</span></span>  
  
|<span data-ttu-id="71c9e-107">Ad</span><span class="sxs-lookup"><span data-stu-id="71c9e-107">Name</span></span>|<span data-ttu-id="71c9e-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="71c9e-108">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="71c9e-109"><xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> Özelliği</span><span class="sxs-lookup"><span data-stu-id="71c9e-109"><xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> property</span></span>|<span data-ttu-id="71c9e-110">Bölümlendirici klavye veya fare yoluyla taşınabilir olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="71c9e-110">Determines if the splitter is movable by means of the keyboard or mouse.</span></span>|  
|<span data-ttu-id="71c9e-111"><xref:System.Windows.Forms.SplitContainer.SplitterDistance%2A> Özelliği</span><span class="sxs-lookup"><span data-stu-id="71c9e-111"><xref:System.Windows.Forms.SplitContainer.SplitterDistance%2A> property</span></span>|<span data-ttu-id="71c9e-112">Taşınabilir Bölümlendirici çubuğuna sol veya üst kenarından piksel cinsinden uzaklığı belirler.</span><span class="sxs-lookup"><span data-stu-id="71c9e-112">Determines the distance in pixels from the left or upper edge to the movable splitter bar.</span></span>|  
|<span data-ttu-id="71c9e-113"><xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> Özelliği</span><span class="sxs-lookup"><span data-stu-id="71c9e-113"><xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> property</span></span>|<span data-ttu-id="71c9e-114">Bölümlendirici kullanıcı tarafından taşınabilmesi piksel cinsinden minimum uzaklığını belirler.</span><span class="sxs-lookup"><span data-stu-id="71c9e-114">Determines the minimum distance, in pixels, that the splitter can be moved by the user.</span></span>|  
  
 <span data-ttu-id="71c9e-115">Aşağıdaki örnek değiştirir <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> özelliği bir "Bölümlendirici tutturma" efekti; oluşturmak için kullanıcı Bölümlendirici sürüklendiğinde varsayılan 1 yerine 10 piksel birimlerinde artırır.</span><span class="sxs-lookup"><span data-stu-id="71c9e-115">The example below modifies the <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> property to create a "snapping splitter" effect; when the user drags the splitter, it increments in units of 10 pixels rather than the default 1.</span></span>  
  
### <a name="to-define-splitcontainer-resize-behavior"></a><span data-ttu-id="71c9e-116">SplitContainer yeniden boyutlandırma davranışını tanımlamak için</span><span class="sxs-lookup"><span data-stu-id="71c9e-116">To define SplitContainer resize behavior</span></span>  
  
1.  <span data-ttu-id="71c9e-117">Bir yordamda ayarladığınız <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> istenen boyuta özelliğine böylece Bölümlendirici 'tutturma' davranışını elde edilir.</span><span class="sxs-lookup"><span data-stu-id="71c9e-117">In a procedure, set the <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> property to the desired size, so that the 'snapping' behavior of the splitter is achieved.</span></span>  
  
     <span data-ttu-id="71c9e-118">Aşağıdaki kod örneğinde, formun içinde <xref:System.Windows.Forms.Form.Load> olay, içinde Bölümlendirici <xref:System.Windows.Forms.SplitContainer> denetim sürüklendiğinde 10 piksel atlamak için ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="71c9e-118">In the following code example, within the form's <xref:System.Windows.Forms.Form.Load> event, the splitter within the <xref:System.Windows.Forms.SplitContainer> control is set to jump 10 pixels when dragged.</span></span>  
  
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
  
     <span data-ttu-id="71c9e-119">(Visual C#) Aşağıdaki kod, olay işleyicisi kaydetmek için formun oluşturucuda yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="71c9e-119">(Visual C#) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.Load += new System.EventHandler(this.Form1_Load);  
    ```  
  
     <span data-ttu-id="71c9e-120">Bölümlendirici biraz sola veya sağa hareket anlaşılabilir hiçbir etkisi olmaz; Ancak, fare işaretçisini herhangi bir yönde 10 piksel gittiğinde Bölümlendirici yeni konuma Daya.</span><span class="sxs-lookup"><span data-stu-id="71c9e-120">Moving the splitter slightly to the left or right will have no discernible effect; however, when the mouse pointer goes 10 pixels in either direction, the splitter will snap to the new position.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71c9e-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="71c9e-121">See Also</span></span>  
 <xref:System.Windows.Forms.SplitContainer>  
 <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A>
