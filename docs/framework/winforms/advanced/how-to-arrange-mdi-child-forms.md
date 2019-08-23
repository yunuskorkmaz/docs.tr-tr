---
title: 'Nasıl yapılır: MDI Alt Formlarını Düzenleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- child forms [Windows Forms], arranging
- MDI [Windows Forms], arranging child forms
ms.assetid: a0786378-3206-4ccc-898e-7d3b38cc5089
ms.openlocfilehash: 7e4d5a80961ae37951251dffa30cb8e75b20be27
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69955112"
---
# <a name="how-to-arrange-mdi-child-forms"></a><span data-ttu-id="53e80-102">Nasıl yapılır: MDI Alt Formlarını Düzenleme</span><span class="sxs-lookup"><span data-stu-id="53e80-102">How to: Arrange MDI Child Forms</span></span>
<span data-ttu-id="53e80-103">Genellikle, uygulamalar, açık MDI alt formlarının yerleşimini denetleyen kutucuk, basamakla ve Düzenle gibi eylemler için menü komutlarına sahip olur.</span><span class="sxs-lookup"><span data-stu-id="53e80-103">Often, applications will have menu commands for actions such as Tile, Cascade, and Arrange, which control the layout of the open MDI child forms.</span></span> <span data-ttu-id="53e80-104">Bir MDI parent formundaki <xref:System.Windows.Forms.Form.LayoutMdi%2A> alt formları yeniden düzenlemek için <xref:System.Windows.Forms.MdiLayout> bir numaralandırma değerlerinden biriyle yöntemini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="53e80-104">You can use the <xref:System.Windows.Forms.Form.LayoutMdi%2A> method with one of the <xref:System.Windows.Forms.MdiLayout> enumeration values to rearrange the child forms in an MDI parent form.</span></span>  
  
 <span data-ttu-id="53e80-105"><xref:System.Windows.Forms.MdiLayout> Sabit listesi değerleri, alt formları yatay veya dikey döşeli olarak basamaklı olarak ya da MDI formunun alt bölümü üzerinde düzenlenmiş alt form simgeleri olarak görüntüler.</span><span class="sxs-lookup"><span data-stu-id="53e80-105">The <xref:System.Windows.Forms.MdiLayout> enumeration values display child forms as cascading, as horizontally or vertically tiled, or as child form icons arranged along the lower portion of the MDI form.</span></span> <span data-ttu-id="53e80-106">Bu değerler, Windows komutları **basamaklı pencereleri**ile aynı etkiye sahiptir, **pencereleri yan yana gösterir**, Windows 'u **yığılmış**ve sırasıyla **Masaüstünü gösterir**.</span><span class="sxs-lookup"><span data-stu-id="53e80-106">These values have the same effect as the Windows commands **Cascade windows**, **Show windows side by side**, **Show windows stacked**, and **Show the desktop**, respectively.</span></span>  
  
 <span data-ttu-id="53e80-107">Genellikle, bu yöntemler bir menü öğesinin <xref:System.Windows.Forms.Control.Click> olayı tarafından çağrılan olay işleyicileri olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="53e80-107">Often, these methods are used as the event handlers called by a menu item's <xref:System.Windows.Forms.Control.Click> event.</span></span> <span data-ttu-id="53e80-108">Bu şekilde, "Cascade Windows" metnini içeren bir menü öğesi, MDI alt pencereleri üzerinde istenen etkiye sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="53e80-108">In this way, a menu item with the text "Cascade Windows" can have the desired effect on the MDI child windows.</span></span>  
  
### <a name="to-arrange-child-forms"></a><span data-ttu-id="53e80-109">Alt formları düzenlemek için</span><span class="sxs-lookup"><span data-stu-id="53e80-109">To arrange child forms</span></span>  
  
1. <span data-ttu-id="53e80-110">Bir yönteminde, MDI parent form <xref:System.Windows.Forms.Form.LayoutMdi%2A> için <xref:System.Windows.Forms.MdiLayout> sabit listesini ayarlamak için yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="53e80-110">In a method, use the <xref:System.Windows.Forms.Form.LayoutMdi%2A> method to set the <xref:System.Windows.Forms.MdiLayout> enumeration for the MDI parent form.</span></span> <span data-ttu-id="53e80-111">Aşağıdaki örnek, MDI parent <xref:System.Windows.Forms.MdiLayout.Cascade?displayProperty=nameWithType> form (`Form1`) öğesinin alt pencereleri için numaralandırma değeri kullanır.</span><span class="sxs-lookup"><span data-stu-id="53e80-111">The following example uses the <xref:System.Windows.Forms.MdiLayout.Cascade?displayProperty=nameWithType> enumeration value for the child windows of the MDI parent form (`Form1`).</span></span> <span data-ttu-id="53e80-112">Sabit listesi, <xref:System.Windows.Forms.Control.Click> **Cascade Windows** menü öğesi olayı için olay işleyicisi sırasında kodda kullanılır.</span><span class="sxs-lookup"><span data-stu-id="53e80-112">The enumeration is used in code during the event handler for the <xref:System.Windows.Forms.Control.Click> event of the **Cascade Windows** menu item.</span></span>  
  
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
    > <span data-ttu-id="53e80-113">Ayrıca, <xref:System.Windows.Forms.MdiLayout> kullanılan sabit listesi değerini değiştirerek pencereleri de döşeyerek simgeler olarak düzenleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="53e80-113">You can also tile windows and arranging windows as icons by changing the <xref:System.Windows.Forms.MdiLayout> enumeration value used.</span></span>  
  
2. <span data-ttu-id="53e80-114">Görsel C#kullanıyorsanız, olay işleyicisini kaydetmek için formun oluşturucusuna aşağıdaki kodu koyun.</span><span class="sxs-lookup"><span data-stu-id="53e80-114">If you’re using Visual C#, place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="53e80-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="53e80-115">See also</span></span>

- [<span data-ttu-id="53e80-116">Çok Belgeli Arabirim (MDI) Uygulamaları</span><span class="sxs-lookup"><span data-stu-id="53e80-116">Multiple-Document Interface (MDI) Applications</span></span>](multiple-document-interface-mdi-applications.md)
- [<span data-ttu-id="53e80-117">Nasıl yapılır: MDI üst formları oluşturma</span><span class="sxs-lookup"><span data-stu-id="53e80-117">How to: Create MDI Parent Forms</span></span>](how-to-create-mdi-parent-forms.md)
- [<span data-ttu-id="53e80-118">Nasıl yapılır: MDI alt formları oluşturma</span><span class="sxs-lookup"><span data-stu-id="53e80-118">How to: Create MDI Child Forms</span></span>](how-to-create-mdi-child-forms.md)
- [<span data-ttu-id="53e80-119">Nasıl yapılır: Etkin MDI alt öğesini belirleme</span><span class="sxs-lookup"><span data-stu-id="53e80-119">How to: Determine the Active MDI Child</span></span>](how-to-determine-the-active-mdi-child.md)
- [<span data-ttu-id="53e80-120">Nasıl yapılır: Etkin MDI alt öğesine veri gönderme</span><span class="sxs-lookup"><span data-stu-id="53e80-120">How to: Send Data to the Active MDI Child</span></span>](how-to-send-data-to-the-active-mdi-child.md)
