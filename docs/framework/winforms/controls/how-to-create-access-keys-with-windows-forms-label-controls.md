---
title: Etiket denetimleriyle erişim tuşları oluşturma
ms.date: 03/30/2017
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
ms.openlocfilehash: 800afc03e71435e2721456b93bb9704af01f714a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76731059"
---
# <a name="how-to-create-access-keys-with-windows-forms-label-controls"></a><span data-ttu-id="043bf-102">Nasıl yapılır: Windows Forms Etiket Denetimleri ile Erişim Tuşları Oluşturma</span><span class="sxs-lookup"><span data-stu-id="043bf-102">How to: Create Access Keys with Windows Forms Label Controls</span></span>
<span data-ttu-id="043bf-103">Windows Forms <xref:System.Windows.Forms.Label> denetimleri, diğer denetimler için erişim anahtarlarını tanımlamak üzere kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="043bf-103">Windows Forms <xref:System.Windows.Forms.Label> controls can be used to define access keys for other controls.</span></span> <span data-ttu-id="043bf-104">Bir etiket denetiminde bir erişim anahtarı tanımladığınızda, Kullanıcı ALT tuşuna ve odağı sekme düzeninde takip eden denetime taşımak için belirlediğiniz karaktere basabilir.</span><span class="sxs-lookup"><span data-stu-id="043bf-104">When you define an access key in a label control, the user can press the ALT key plus the character you designate to move the focus to the control that follows it in the tab order.</span></span> <span data-ttu-id="043bf-105">Etiketler odağı alamadığı için odak otomatik olarak sekme sırasında bir sonraki denetime taşınır.</span><span class="sxs-lookup"><span data-stu-id="043bf-105">Because labels cannot receive focus, focus automatically moves to the next control in the tab order.</span></span> <span data-ttu-id="043bf-106">Metin kutularına, Birleşik giriş kutularına, liste kutularına ve veri kılavuzlarına erişim tuşları atamak için bu tekniği kullanın.</span><span class="sxs-lookup"><span data-stu-id="043bf-106">Use this technique to assign access keys to text boxes, combo boxes, list boxes, and data grids.</span></span>  
  
### <a name="to-assign-an-access-key-to-a-control-with-a-label"></a><span data-ttu-id="043bf-107">Etikete sahip bir denetime erişim anahtarı atamak için</span><span class="sxs-lookup"><span data-stu-id="043bf-107">To assign an access key to a control with a label</span></span>  
  
1. <span data-ttu-id="043bf-108">Önce etiketi çizin, sonra diğer denetimi çizin.</span><span class="sxs-lookup"><span data-stu-id="043bf-108">Draw the label first, and then draw the other control.</span></span>  
  
     <span data-ttu-id="043bf-109">veya</span><span class="sxs-lookup"><span data-stu-id="043bf-109">-or-</span></span>  
  
     <span data-ttu-id="043bf-110">Denetimleri herhangi bir sırada çizin ve etiketin <xref:System.Windows.Forms.Control.TabIndex%2A> özelliğini diğer denetimden daha az bir olacak şekilde ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="043bf-110">Draw the controls in any order and set the <xref:System.Windows.Forms.Control.TabIndex%2A> property of the label to one less than the other control.</span></span>  
  
2. <span data-ttu-id="043bf-111">Etiketin <xref:System.Windows.Forms.Label.UseMnemonic%2A> özelliğini `true`olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="043bf-111">Set the label's <xref:System.Windows.Forms.Label.UseMnemonic%2A> property to `true`.</span></span>  
  
3. <span data-ttu-id="043bf-112">Etiketin <xref:System.Windows.Forms.Label.Text%2A> özelliğindeki bir ve işareti (&) kullanın.</span><span class="sxs-lookup"><span data-stu-id="043bf-112">Use an ampersand (&) in the label's <xref:System.Windows.Forms.Label.Text%2A> property to assign the access key for the label.</span></span> <span data-ttu-id="043bf-113">Daha fazla bilgi için bkz. [Windows Forms denetimleri Için erişim tuşları oluşturma](how-to-create-access-keys-for-windows-forms-controls.md).</span><span class="sxs-lookup"><span data-stu-id="043bf-113">For more information, see [Creating Access Keys for Windows Forms Controls](how-to-create-access-keys-for-windows-forms-controls.md).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="043bf-114">Etiketleri, erişim tuşları oluşturmak için kullanmak yerine bir etiket denetiminde göstermek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="043bf-114">You may want to display ampersands in a label control, rather than use them to create access keys.</span></span> <span data-ttu-id="043bf-115">Bu durum, bir etiket denetimini, verilerin dahil edildiği bir kayıt kümesindeki bir alana bağlarsanız meydana gelebilir.</span><span class="sxs-lookup"><span data-stu-id="043bf-115">This may occur if you bind a label control to a field in a recordset where the data includes ampersands.</span></span> <span data-ttu-id="043bf-116">Etiketleri bir etiket denetiminde göstermek için <xref:System.Windows.Forms.Label.UseMnemonic%2A> özelliğini `false`olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="043bf-116">To display ampersands in a label control, set the <xref:System.Windows.Forms.Label.UseMnemonic%2A> property to `false`.</span></span> <span data-ttu-id="043bf-117">Birlikte bulunan DS 'yi ve ayrıca bir erişim anahtarınız göstermek istiyorsanız, <xref:System.Windows.Forms.Label.UseMnemonic%2A> özelliğini `true` olarak ayarlayın ve erişim anahtarını bir ve işareti (&) ile, iki ile birlikte görüntülenecek şekilde belirtin.</span><span class="sxs-lookup"><span data-stu-id="043bf-117">If you wish to display ampersands and also have an access key, set the <xref:System.Windows.Forms.Label.UseMnemonic%2A> property to `true` and indicate the access key with one ampersand (&) and the ampersand to display with two ampersands.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="043bf-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="043bf-118">See also</span></span>

- [<span data-ttu-id="043bf-119">Nasıl yapılır: Windows Forms Etiket Denetimini İçeriğini Sığdıracak Şekilde Boyutlandırma</span><span class="sxs-lookup"><span data-stu-id="043bf-119">How to: Size a Windows Forms Label Control to Fit Its Contents</span></span>](how-to-size-a-windows-forms-label-control-to-fit-its-contents.md)
- [<span data-ttu-id="043bf-120">Etiket Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="043bf-120">Label Control Overview</span></span>](label-control-overview-windows-forms.md)
- [<span data-ttu-id="043bf-121">Etiket Denetimi</span><span class="sxs-lookup"><span data-stu-id="043bf-121">Label Control</span></span>](label-control-windows-forms.md)
