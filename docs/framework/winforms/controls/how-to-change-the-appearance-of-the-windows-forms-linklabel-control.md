---
title: LinkLabel Denetimigörünümünü Değiştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- LinkLabel properties
- LinkLabel control [Windows Forms], changing appearance of links
- links [Windows Forms], changing appearance
- examples [Windows Forms], LinkLabel control
- LinkLabel control [Windows Forms], examples
ms.assetid: fdc5854f-5162-4457-8cbe-1042feb2d132
ms.openlocfilehash: df66991289373a05fc7c27b7768a96643e3bbae0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142136"
---
# <a name="how-to-change-the-appearance-of-the-windows-forms-linklabel-control"></a><span data-ttu-id="e5df8-102">Nasıl yapılır: Windows Forms LinkLabel Denetiminin Görünüşünü Değiştirme</span><span class="sxs-lookup"><span data-stu-id="e5df8-102">How to: Change the Appearance of the Windows Forms LinkLabel Control</span></span>
<span data-ttu-id="e5df8-103"><xref:System.Windows.Forms.LinkLabel> Denetim tarafından görüntülenen metni çeşitli amaçlara uyacak şekilde değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e5df8-103">You can change the text displayed by the <xref:System.Windows.Forms.LinkLabel> control to suit a variety of purposes.</span></span> <span data-ttu-id="e5df8-104">Örneğin, metnin altı çizili belirli bir renkte görünmesi için metin ayarlayarak metnin tıklanabileceğini kullanıcıya belirtmek yaygın bir uygulamadır.</span><span class="sxs-lookup"><span data-stu-id="e5df8-104">For example, it is common practice to indicate to the user that text can be clicked by setting the text to appear in a specific color with an underline.</span></span> <span data-ttu-id="e5df8-105">Kullanıcı metni tıklattıktan sonra renk farklı bir renge dönüşür.</span><span class="sxs-lookup"><span data-stu-id="e5df8-105">After the user clicks the text, the color changes to a different color.</span></span> <span data-ttu-id="e5df8-106">Bu davranışı denetlemek için beş farklı özellik <xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A> <xref:System.Windows.Forms.LinkLabel.LinkArea%2A>ayarlayabilirsiniz: , , <xref:System.Windows.Forms.LinkLabel.LinkColor%2A> <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>, ve <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> özellikleri.</span><span class="sxs-lookup"><span data-stu-id="e5df8-106">To control this behavior, you can set five different properties: the <xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A>, <xref:System.Windows.Forms.LinkLabel.LinkArea%2A>, <xref:System.Windows.Forms.LinkLabel.LinkColor%2A>, <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>, and <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> properties.</span></span>  
  
### <a name="to-change-the-appearance-of-a-linklabel-control"></a><span data-ttu-id="e5df8-107">Bir LinkLabel denetiminin görünümünü değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="e5df8-107">To change the appearance of a LinkLabel control</span></span>  
  
1. <span data-ttu-id="e5df8-108"><xref:System.Windows.Forms.LinkLabel.LinkColor%2A> Ve <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A> özellikleri istediğiniz renklere ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="e5df8-108">Set the <xref:System.Windows.Forms.LinkLabel.LinkColor%2A> and <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A> properties to the colors you want.</span></span>  
  
     <span data-ttu-id="e5df8-109">Bu, **Özellikler** penceresinde programlı olarak veya tasarım zamanında yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="e5df8-109">This can be done either programmatically or at design time in the **Properties** window.</span></span>  
  
    ```vb  
    ' You can set the color using decimal values for red, green, and blue  
    LinkLabel1.LinkColor = Color.FromArgb(0, 0, 255)  
    ' Or you can set the color using defined constants  
    LinkLabel1.VisitedLinkColor = Color.Purple  
    ```  
  
    ```csharp  
    // You can set the color using decimal values for red, green, and blue  
    linkLabel1.LinkColor = Color.FromArgb(0, 0, 255);  
    // Or you can set the color using defined constants  
    linkLabel1.VisitedLinkColor = Color.Purple;  
    ```  
  
    ```cpp  
    // You can set the color using decimal values for red, green, and blue  
    linkLabel1->LinkColor = Color::FromArgb(0, 0, 255);  
    // Or you can set the color using defined constants  
    linkLabel1->VisitedLinkColor = Color::Purple;  
    ```  
  
2. <span data-ttu-id="e5df8-110"><xref:System.Windows.Forms.LinkLabel.Text%2A> Özelliği uygun bir alt yazı yla ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="e5df8-110">Set the <xref:System.Windows.Forms.LinkLabel.Text%2A> property to an appropriate caption.</span></span>  
  
     <span data-ttu-id="e5df8-111">Bu, **Özellikler** penceresinde programlı olarak veya tasarım zamanında yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="e5df8-111">This can be done either programmatically or at design time in the **Properties** window.</span></span>  
  
    ```vb  
    LinkLabel1.Text = "Click here to see more."  
    ```  
  
    ```csharp  
    linkLabel1.Text = "Click here to see more.";  
    ```  
  
    ```cpp  
    linkLabel1->Text = "Click here to see more.";  
    ```  
  
3. <span data-ttu-id="e5df8-112">Alt <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> yazının hangi bölümünün bağlantı olarak gösterileceğini belirlemek için özelliği ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="e5df8-112">Set the <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> property to determine which part of the caption will be indicated as a link.</span></span>  
  
     <span data-ttu-id="e5df8-113">Değer, <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> iki sayı, <xref:System.Windows.Forms.LinkArea> başlangıç karakter konumu ve karakter sayısı içeren bir ile gösterilir.</span><span class="sxs-lookup"><span data-stu-id="e5df8-113">The <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> value is represented with a <xref:System.Windows.Forms.LinkArea> containing two numbers, the starting character position and the number of characters.</span></span> <span data-ttu-id="e5df8-114">Bu, **Özellikler** penceresinde programlı olarak veya tasarım zamanında yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="e5df8-114">This can be done either programmatically or at design time in the **Properties** window.</span></span>  
  
    ```vb  
    LinkLabel1.LinkArea = new LinkArea(6,4)  
    ```  
  
    ```csharp  
    linkLabel1.LinkArea = new LinkArea(6,4);  
    ```  
  
    ```cpp  
    linkLabel1->LinkArea = LinkArea(6,4);  
    ```  
  
4. <span data-ttu-id="e5df8-115"><xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A> Özelliği <xref:System.Windows.Forms.LinkBehavior.AlwaysUnderline>, <xref:System.Windows.Forms.LinkBehavior.HoverUnderline>veya <xref:System.Windows.Forms.LinkBehavior.NeverUnderline>.</span><span class="sxs-lookup"><span data-stu-id="e5df8-115">Set the <xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A> property to <xref:System.Windows.Forms.LinkBehavior.AlwaysUnderline>, <xref:System.Windows.Forms.LinkBehavior.HoverUnderline>, or <xref:System.Windows.Forms.LinkBehavior.NeverUnderline>.</span></span>  
  
     <span data-ttu-id="e5df8-116"><xref:System.Windows.Forms.LinkBehavior.HoverUnderline>Ayarlanırsa, alt yazının belirlediği <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> bölüm yalnızca işaretçi üzerinde yse altı çizilir.</span><span class="sxs-lookup"><span data-stu-id="e5df8-116">If it is set to <xref:System.Windows.Forms.LinkBehavior.HoverUnderline>, the part of the caption determined by <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> will only be underlined when the pointer rests on it.</span></span>  
  
5. <span data-ttu-id="e5df8-117">Olay <xref:System.Windows.Forms.LinkLabel.LinkClicked> işleyicisi, <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> özelliği `true`' ye ayarla.</span><span class="sxs-lookup"><span data-stu-id="e5df8-117">In the <xref:System.Windows.Forms.LinkLabel.LinkClicked> event handler, set the <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> property to `true`.</span></span>  
  
     <span data-ttu-id="e5df8-118">Bir bağlantı ziyaret edildiğinde, görünümünü genellikle renk olarak bir şekilde değiştirmek yaygın bir uygulamadır.</span><span class="sxs-lookup"><span data-stu-id="e5df8-118">When a link has been visited, it is common practice to change its appearance in some way, usually by color.</span></span> <span data-ttu-id="e5df8-119"><xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A> Metin, özellik tarafından belirtilen renge değişecektir.</span><span class="sxs-lookup"><span data-stu-id="e5df8-119">The text will change to the color specified by the <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A> property.</span></span>  
  
    ```vb  
    Protected Sub LinkLabel1_LinkClicked (ByVal sender As Object, _  
       ByVal e As EventArgs) Handles LinkLabel1.LinkClicked  
       ' Change the color of the link text  
       ' by setting LinkVisited to True.  
       LinkLabel1.LinkVisited = True  
       ' Then do whatever other action is appropriate  
    End Sub  
    ```  
  
    ```csharp  
    protected void LinkLabel1_LinkClicked(object sender, System.EventArgs e)  
    {  
       // Change the color of the link text by setting LinkVisited
       // to True.  
       linkLabel1.LinkVisited = true;  
       // Then do whatever other action is appropriate  
    }  
    ```  
  
    ```cpp  
    private:  
       System::Void linkLabel1_LinkClicked(System::Object ^  sender,  
          System::Windows::Forms::LinkLabelLinkClickedEventArgs ^  e)  
       {  
          // Change the color of the link text by setting LinkVisited
          // to True.  
          linkLabel1->LinkVisited = true;  
          // Then do whatever other action is appropriate  
       }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="e5df8-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e5df8-120">See also</span></span>

- <xref:System.Windows.Forms.LinkLabel.LinkArea%2A>
- <xref:System.Windows.Forms.LinkLabel.LinkColor%2A>
- <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>
- <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A>
- [<span data-ttu-id="e5df8-121">LinkLabel Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="e5df8-121">LinkLabel Control Overview</span></span>](linklabel-control-overview-windows-forms.md)
- [<span data-ttu-id="e5df8-122">Nasıl yapılır: Windows Forms LinkLabel Denetimi ile Bir Nesneye veya Web Sayfasına Bağlama</span><span class="sxs-lookup"><span data-stu-id="e5df8-122">How to: Link to an Object or Web Page with the Windows Forms LinkLabel Control</span></span>](link-to-an-object-or-web-page-with-wf-linklabel-control.md)
- [<span data-ttu-id="e5df8-123">LinkLabel Denetimi</span><span class="sxs-lookup"><span data-stu-id="e5df8-123">LinkLabel Control</span></span>](linklabel-control-windows-forms.md)
