---
title: "Nasıl yapılır: Windows Forms Etiket Denetimleri ile Erişim Tuşları Oluşturma"
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
- cpp
helpviewer_keywords:
- controls [Windows Forms], access keys
- dialog box controls [Windows Forms], mnemonics
- access keys [Windows Forms], creating for controls
- Label control [Windows Forms], creating access keys
- mnemonics [Windows Forms], adding to dialog box controls
- mnemonics
- Windows Forms controls, access keys
- UseMnemonic property [Windows Forms], Label control
- keyboard shortcuts [Windows Forms], creating for controls
- access keys [Windows Forms], Windows Forms
ms.assetid: 5ee8f823-80be-4a4f-96a4-412671e2e306
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6a856090a76f484c21c1d9982d67e9fdf21e8451
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-access-keys-with-windows-forms-label-controls"></a><span data-ttu-id="ed41b-102">Nasıl yapılır: Windows Forms Etiket Denetimleri ile Erişim Tuşları Oluşturma</span><span class="sxs-lookup"><span data-stu-id="ed41b-102">How to: Create Access Keys with Windows Forms Label Controls</span></span>
<span data-ttu-id="ed41b-103">Windows Forms <xref:System.Windows.Forms.Label> denetimleri, diğer denetimler için erişim anahtarları tanımlamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ed41b-103">Windows Forms <xref:System.Windows.Forms.Label> controls can be used to define access keys for other controls.</span></span> <span data-ttu-id="ed41b-104">Bir etiket denetiminde bir erişim anahtarı tanımladığınızda, kullanıcı ALT tuşuyla birlikte odağını sekme sırasında izleyen denetime taşıma için belirttiğiniz karakter tuşlarına basabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ed41b-104">When you define an access key in a label control, the user can press the ALT key plus the character you designate to move the focus to the control that follows it in the tab order.</span></span> <span data-ttu-id="ed41b-105">Etiketleri odak alamaz olduğundan odağını sekme sırasında bir sonraki denetime otomatik olarak taşır.</span><span class="sxs-lookup"><span data-stu-id="ed41b-105">Because labels cannot receive focus, focus automatically moves to the next control in the tab order.</span></span> <span data-ttu-id="ed41b-106">Metin kutuları, birleşik giriş kutuları, liste kutuları ile veri kılavuzları erişim tuşları atamak için bu tekniği kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ed41b-106">Use this technique to assign access keys to text boxes, combo boxes, list boxes, and data grids.</span></span>  
  
### <a name="to-assign-an-access-key-to-a-control-with-a-label"></a><span data-ttu-id="ed41b-107">Bir etiket bir denetim için erişim tuşu atamak için</span><span class="sxs-lookup"><span data-stu-id="ed41b-107">To assign an access key to a control with a label</span></span>  
  
1.  <span data-ttu-id="ed41b-108">Etiketin ilk çizim ve diğer denetim çizin.</span><span class="sxs-lookup"><span data-stu-id="ed41b-108">Draw the label first, and then draw the other control.</span></span>  
  
     <span data-ttu-id="ed41b-109">veya</span><span class="sxs-lookup"><span data-stu-id="ed41b-109">-or-</span></span>  
  
     <span data-ttu-id="ed41b-110">Herhangi bir sırada denetimleri çizme ve ayarlayın <xref:System.Windows.Forms.Control.TabIndex%2A> bir diğer denetim değerinden etiketinin özelliği.</span><span class="sxs-lookup"><span data-stu-id="ed41b-110">Draw the controls in any order and set the <xref:System.Windows.Forms.Control.TabIndex%2A> property of the label to one less than the other control.</span></span>  
  
2.  <span data-ttu-id="ed41b-111">Etiketin ayarlamak <xref:System.Windows.Forms.Label.UseMnemonic%2A> özelliğine `true`.</span><span class="sxs-lookup"><span data-stu-id="ed41b-111">Set the label's <xref:System.Windows.Forms.Label.UseMnemonic%2A> property to `true`.</span></span>  
  
3.  <span data-ttu-id="ed41b-112">Ve işareti kullanın (&) etiketin <xref:System.Windows.Forms.Label.Text%2A> etiketi için erişim anahtarı atamak için özellik.</span><span class="sxs-lookup"><span data-stu-id="ed41b-112">Use an ampersand (&) in the label's <xref:System.Windows.Forms.Label.Text%2A> property to assign the access key for the label.</span></span> <span data-ttu-id="ed41b-113">Daha fazla bilgi için bkz: [oluşturma erişim anahtarları için Windows Forms denetimleri](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md).</span><span class="sxs-lookup"><span data-stu-id="ed41b-113">For more information, see [Creating Access Keys for Windows Forms Controls](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ed41b-114">Yerine bir etiket denetimi ve işaretlerini görüntüleme erişim tuşları oluşturma için onları kullanmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ed41b-114">You may want to display ampersands in a label control, rather than use them to create access keys.</span></span> <span data-ttu-id="ed41b-115">Etiket denetimi nerede ve işaretlerini verileri içeren bir kayıt kümesindeki alan bağlarsanız bu durum oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="ed41b-115">This may occur if you bind a label control to a field in a recordset where the data includes ampersands.</span></span> <span data-ttu-id="ed41b-116">Etiket denetimi ve işaretlerini görüntülemek için ayarlanmış <xref:System.Windows.Forms.Label.UseMnemonic%2A> özelliğine `false`.</span><span class="sxs-lookup"><span data-stu-id="ed41b-116">To display ampersands in a label control, set the <xref:System.Windows.Forms.Label.UseMnemonic%2A> property to `false`.</span></span> <span data-ttu-id="ed41b-117">Ve işaretlerini görüntüleme ve ayrıca bir erişim anahtarı isterseniz, <xref:System.Windows.Forms.Label.UseMnemonic%2A> özelliğine `true` ve bir ampersan erişim anahtarıyla belirtin (&) ve ve işareti ile iki ve işaretlerini görüntüleme.</span><span class="sxs-lookup"><span data-stu-id="ed41b-117">If you wish to display ampersands and also have an access key, set the <xref:System.Windows.Forms.Label.UseMnemonic%2A> property to `true` and indicate the access key with one ampersand (&) and the ampersand to display with two ampersands.</span></span>  
  
    ```vb  
    Label1.UseMnemonic = True  
    Label1.Text = "&Print"  
    Label2.UseMnemonic = True  
    Label2.Text = "&Copy && Paste"  
    ```  
  
    ```csharp  
    label1.UseMnemonic = true;  
    label1.Text = "&Print";  
    label2.UseMnemonic = true;  
    label2.Text = "&Copy && Paste";  
    ```  
  
    ```cpp  
    label1->UseMnemonic = true;  
    label1->Text = "&Print";  
    label2->UseMnemonic = true;  
    label2->Text = "&Copy && Paste";  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="ed41b-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ed41b-118">See Also</span></span>  
 [<span data-ttu-id="ed41b-119">Nasıl yapılır: Windows Forms Etiket Denetimini İçeriğini Sığdıracak Şekilde Boyutlandırma</span><span class="sxs-lookup"><span data-stu-id="ed41b-119">How to: Size a Windows Forms Label Control to Fit Its Contents</span></span>](../../../../docs/framework/winforms/controls/how-to-size-a-windows-forms-label-control-to-fit-its-contents.md)  
 [<span data-ttu-id="ed41b-120">Etiket Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="ed41b-120">Label Control Overview</span></span>](../../../../docs/framework/winforms/controls/label-control-overview-windows-forms.md)  
 [<span data-ttu-id="ed41b-121">Etiket Denetimi</span><span class="sxs-lookup"><span data-stu-id="ed41b-121">Label Control</span></span>](../../../../docs/framework/winforms/controls/label-control-windows-forms.md)
