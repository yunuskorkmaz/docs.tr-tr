---
title: "Nasıl yapılır: MDI Alt Formlarını Düzenleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- child forms [Windows Forms], arranging
- MDI [Windows Forms], arranging child forms
ms.assetid: a0786378-3206-4ccc-898e-7d3b38cc5089
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5273327c283f873352f62462cc4be59e4b34351f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-arrange-mdi-child-forms"></a><span data-ttu-id="03bdc-102">Nasıl yapılır: MDI Alt Formlarını Düzenleme</span><span class="sxs-lookup"><span data-stu-id="03bdc-102">How to: Arrange MDI Child Forms</span></span>
<span data-ttu-id="03bdc-103">Genellikle, uygulamaları kutucuğu, Cascade ve Yerleştir, açık MDI alt formları düzenini denetleyen gibi eylemleri menü komutlarını sahip olur.</span><span class="sxs-lookup"><span data-stu-id="03bdc-103">Often, applications will have menu commands for actions such as Tile, Cascade, and Arrange, which control the layout of the open MDI child forms.</span></span> <span data-ttu-id="03bdc-104">Kullanabileceğiniz <xref:System.Windows.Forms.Form.LayoutMdi%2A> biriyle yöntemi <xref:System.Windows.Forms.MdiLayout> MDI alt formları yeniden düzenlemek için numaralandırma değerlerinin ana formu.</span><span class="sxs-lookup"><span data-stu-id="03bdc-104">You can use the <xref:System.Windows.Forms.Form.LayoutMdi%2A> method with one of the <xref:System.Windows.Forms.MdiLayout> enumeration values to rearrange the child forms in an MDI parent form.</span></span>  
  
 <span data-ttu-id="03bdc-105"><xref:System.Windows.Forms.MdiLayout> Numaralandırma değerlerinin görüntü alt formları, yatay veya dikey olarak döşenir gibi basamaklı olarak ya da MDI Formu alt kısmı düzenlenmiş alt form simgeler.</span><span class="sxs-lookup"><span data-stu-id="03bdc-105">The <xref:System.Windows.Forms.MdiLayout> enumeration values display child forms as cascading, as horizontally or vertically tiled, or as child form icons arranged along the lower portion of the MDI form.</span></span> <span data-ttu-id="03bdc-106">Bu değerleri Windows komutları aynı etkiye sahip **basamaklı windows**, **windows yan yana göster**, **Göster Yığılmış windows**, ve **masaüstünü gösterir** sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="03bdc-106">These values have the same effect as the Windows commands **Cascade windows**, **Show windows side by side**, **Show windows stacked**, and **Show the desktop**, respectively.</span></span>  
  
 <span data-ttu-id="03bdc-107">Genellikle, bu yöntemleri menü öğesinin tarafından çağrılan olay işleyicileri olarak kullanılan <xref:System.Windows.Forms.Control.Click> olay.</span><span class="sxs-lookup"><span data-stu-id="03bdc-107">Often, these methods are used as the event handlers called by a menu item's <xref:System.Windows.Forms.Control.Click> event.</span></span> <span data-ttu-id="03bdc-108">Bu şekilde, bir menü öğesi "Pencereleri Basamakla" metni ile MDI alt pencereleri istenen etkisi olabilir.</span><span class="sxs-lookup"><span data-stu-id="03bdc-108">In this way, a menu item with the text "Cascade Windows" can have the desired effect on the MDI child windows.</span></span>  
  
### <a name="to-arrange-child-forms"></a><span data-ttu-id="03bdc-109">Alt formlar düzenlemek için</span><span class="sxs-lookup"><span data-stu-id="03bdc-109">To arrange child forms</span></span>  
  
1.  <span data-ttu-id="03bdc-110">Bir yöntem kullanmak <xref:System.Windows.Forms.Form.LayoutMdi%2A> ayarlamak için yöntemin <xref:System.Windows.Forms.MdiLayout> MDI üst form için numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="03bdc-110">In a method, use the <xref:System.Windows.Forms.Form.LayoutMdi%2A> method to set the <xref:System.Windows.Forms.MdiLayout> enumeration for the MDI parent form.</span></span> <span data-ttu-id="03bdc-111">Aşağıdaki örnek kullanır <xref:System.Windows.Forms.MdiLayout.Cascade?displayProperty=nameWithType> MDI üst formun alt windows için numaralandırma değeri (`Form1`).</span><span class="sxs-lookup"><span data-stu-id="03bdc-111">The following example uses the <xref:System.Windows.Forms.MdiLayout.Cascade?displayProperty=nameWithType> enumeration value for the child windows of the MDI parent form (`Form1`).</span></span> <span data-ttu-id="03bdc-112">Numaralandırma sırasında olay işleyicisi için kod içinde kullanılan <xref:System.Windows.Forms.Control.Click> olayı **Pencereleri Basamakla** menü öğesi.</span><span class="sxs-lookup"><span data-stu-id="03bdc-112">The enumeration is used in code during the event handler for the <xref:System.Windows.Forms.Control.Click> event of the **Cascade Windows** menu item.</span></span>  
  
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
    >  <span data-ttu-id="03bdc-113">Aynı zamanda windows ve düzenleyerek windows simgeler olarak değiştirerek döşeme <xref:System.Windows.Forms.MdiLayout> numaralandırma değeri kullanılır.</span><span class="sxs-lookup"><span data-stu-id="03bdc-113">You can also tile windows and arranging windows as icons by changing the <xref:System.Windows.Forms.MdiLayout> enumeration value used.</span></span>  
  
2.  <span data-ttu-id="03bdc-114">Visual C# kullanıyorsanız aşağıdaki kodu olay işleyicisi kaydetmek için formun oluşturucuda yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="03bdc-114">If you’re using Visual C#, place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="03bdc-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="03bdc-115">See Also</span></span>  
 [<span data-ttu-id="03bdc-116">Birden çok belge arabirimi (MDI) uygulamaları</span><span class="sxs-lookup"><span data-stu-id="03bdc-116">Multiple-Document Interface (MDI) Applications</span></span>](../../../../docs/framework/winforms/advanced/multiple-document-interface-mdi-applications.md)  
 [<span data-ttu-id="03bdc-117">Nasıl yapılır: MDI üst formları oluşturma</span><span class="sxs-lookup"><span data-stu-id="03bdc-117">How to: Create MDI Parent Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)  
 [<span data-ttu-id="03bdc-118">Nasıl yapılır: MDI alt formları oluşturma</span><span class="sxs-lookup"><span data-stu-id="03bdc-118">How to: Create MDI Child Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md)  
 [<span data-ttu-id="03bdc-119">Nasıl yapılır: etkin MDI alt öğesini belirleme</span><span class="sxs-lookup"><span data-stu-id="03bdc-119">How to: Determine the Active MDI Child</span></span>](../../../../docs/framework/winforms/advanced/how-to-determine-the-active-mdi-child.md)  
 [<span data-ttu-id="03bdc-120">Nasıl yapılır: etkin MDI alt öğesine veri gönderme</span><span class="sxs-lookup"><span data-stu-id="03bdc-120">How to: Send Data to the Active MDI Child</span></span>](../../../../docs/framework/winforms/advanced/how-to-send-data-to-the-active-mdi-child.md)
