---
title: 'Nasıl yapılır: MDI alt formlarını düzenleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- child forms [Windows Forms], arranging
- MDI [Windows Forms], arranging child forms
ms.assetid: a0786378-3206-4ccc-898e-7d3b38cc5089
ms.openlocfilehash: 6e1e4f22aa70d8ee4d4122f9e77427c101b6713f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54540747"
---
# <a name="how-to-arrange-mdi-child-forms"></a><span data-ttu-id="28500-102">Nasıl yapılır: MDI alt formlarını düzenleme</span><span class="sxs-lookup"><span data-stu-id="28500-102">How to: Arrange MDI Child Forms</span></span>
<span data-ttu-id="28500-103">Genellikle, kutucuk, Cascade ve düzenleme, açık MDI alt formlarını yerleşimini denetleyen gibi eylemleri menü komutlarını uygulamanız olacak.</span><span class="sxs-lookup"><span data-stu-id="28500-103">Often, applications will have menu commands for actions such as Tile, Cascade, and Arrange, which control the layout of the open MDI child forms.</span></span> <span data-ttu-id="28500-104">Kullanabileceğiniz <xref:System.Windows.Forms.Form.LayoutMdi%2A> yöntemi biriyle <xref:System.Windows.Forms.MdiLayout> numaralandırma değerlerinden bir MDI alt formları yeniden düzenlemek için ana formu.</span><span class="sxs-lookup"><span data-stu-id="28500-104">You can use the <xref:System.Windows.Forms.Form.LayoutMdi%2A> method with one of the <xref:System.Windows.Forms.MdiLayout> enumeration values to rearrange the child forms in an MDI parent form.</span></span>  
  
 <span data-ttu-id="28500-105"><xref:System.Windows.Forms.MdiLayout> Numaralandırma değerlerinin görüntü alt formları basamaklı yatay veya dikey olarak döşenmiş gibi olarak ya da MDI formunun alt kısmı alt form simgeler olarak.</span><span class="sxs-lookup"><span data-stu-id="28500-105">The <xref:System.Windows.Forms.MdiLayout> enumeration values display child forms as cascading, as horizontally or vertically tiled, or as child form icons arranged along the lower portion of the MDI form.</span></span> <span data-ttu-id="28500-106">Bu değerleri Windows komutları ile aynı etkiye sahip **basamaklı windows**, **windows yan yana göster**, **Göster Yığılmış windows**, ve **masaüstünü gösterir** sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="28500-106">These values have the same effect as the Windows commands **Cascade windows**, **Show windows side by side**, **Show windows stacked**, and **Show the desktop**, respectively.</span></span>  
  
 <span data-ttu-id="28500-107">Genellikle, bu yöntemler bir menü öğesinin tarafından çağrılan olay işleyicileri olarak kullanılan <xref:System.Windows.Forms.Control.Click> olay.</span><span class="sxs-lookup"><span data-stu-id="28500-107">Often, these methods are used as the event handlers called by a menu item's <xref:System.Windows.Forms.Control.Click> event.</span></span> <span data-ttu-id="28500-108">Bu şekilde, bir menü öğesi metni "Cascade Windows" ile MDI alt pencereleri üzerinde istenen etkisi olabilir.</span><span class="sxs-lookup"><span data-stu-id="28500-108">In this way, a menu item with the text "Cascade Windows" can have the desired effect on the MDI child windows.</span></span>  
  
### <a name="to-arrange-child-forms"></a><span data-ttu-id="28500-109">Alt formlarını düzenlemek için</span><span class="sxs-lookup"><span data-stu-id="28500-109">To arrange child forms</span></span>  
  
1.  <span data-ttu-id="28500-110">Bir yöntem kullanmak <xref:System.Windows.Forms.Form.LayoutMdi%2A> ayarlanacak yöntemi <xref:System.Windows.Forms.MdiLayout> MDI üst formu için sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="28500-110">In a method, use the <xref:System.Windows.Forms.Form.LayoutMdi%2A> method to set the <xref:System.Windows.Forms.MdiLayout> enumeration for the MDI parent form.</span></span> <span data-ttu-id="28500-111">Aşağıdaki örnekte <xref:System.Windows.Forms.MdiLayout.Cascade?displayProperty=nameWithType> numaralandırma değeri MDI üst formunun alt pencereler için (`Form1`).</span><span class="sxs-lookup"><span data-stu-id="28500-111">The following example uses the <xref:System.Windows.Forms.MdiLayout.Cascade?displayProperty=nameWithType> enumeration value for the child windows of the MDI parent form (`Form1`).</span></span> <span data-ttu-id="28500-112">Numaralandırma sırasında olay işleyicisi için kod içinde kullanılan <xref:System.Windows.Forms.Control.Click> olayı **Cascade Windows** menü öğesi.</span><span class="sxs-lookup"><span data-stu-id="28500-112">The enumeration is used in code during the event handler for the <xref:System.Windows.Forms.Control.Click> event of the **Cascade Windows** menu item.</span></span>  
  
    ```vb  
    Protected Sub CascadeWindows_Click(ByVal sender As System.Object, ByVal e As System.EventArgs)  
       Me.LayoutMdi(System.Windows.Forms.MdiLayout.Cascade)  
    End Sub  
    ```  
  
    ```csharp  
    protected void CascadeWindows_Click(object sender, System.EventArgs e){  
       this.LayoutMdi(System.Windows.Forms.MdiLayout.Cascade);  
    }  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="28500-113">Ayrıca windows ve windows düzenleyerek simgeler olarak değiştirerek döşeme <xref:System.Windows.Forms.MdiLayout> numaralandırma değeri kullanılır.</span><span class="sxs-lookup"><span data-stu-id="28500-113">You can also tile windows and arranging windows as icons by changing the <xref:System.Windows.Forms.MdiLayout> enumeration value used.</span></span>  
  
2.  <span data-ttu-id="28500-114">Visual kullanıyorsanız C#, formun oluşturucuda olay işleyicisi kaydetmek için aşağıdaki kodu yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="28500-114">If you’re using Visual C#, place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="28500-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="28500-115">See also</span></span>
- [<span data-ttu-id="28500-116">Çok Belgeli Arabirim (MDI) Uygulamaları</span><span class="sxs-lookup"><span data-stu-id="28500-116">Multiple-Document Interface (MDI) Applications</span></span>](../../../../docs/framework/winforms/advanced/multiple-document-interface-mdi-applications.md)
- [<span data-ttu-id="28500-117">Nasıl yapılır: MDI üst formları oluşturma</span><span class="sxs-lookup"><span data-stu-id="28500-117">How to: Create MDI Parent Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)
- [<span data-ttu-id="28500-118">Nasıl yapılır: MDI alt formları oluştur</span><span class="sxs-lookup"><span data-stu-id="28500-118">How to: Create MDI Child Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md)
- [<span data-ttu-id="28500-119">Nasıl yapılır: Etkin MDI alt öğesini belirleme</span><span class="sxs-lookup"><span data-stu-id="28500-119">How to: Determine the Active MDI Child</span></span>](../../../../docs/framework/winforms/advanced/how-to-determine-the-active-mdi-child.md)
- [<span data-ttu-id="28500-120">Nasıl yapılır: Etkin MDI alt öğesine veri gönderme</span><span class="sxs-lookup"><span data-stu-id="28500-120">How to: Send Data to the Active MDI Child</span></span>](../../../../docs/framework/winforms/advanced/how-to-send-data-to-the-active-mdi-child.md)
