---
title: 'Nasıl yapılır: Windows Forms Etiket Denetimleri ile Erişim Tuşları Oluşturma'
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
ms.openlocfilehash: ff603ee784978a8b2bab2cccd4610fc50b45d477
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59171723"
---
# <a name="how-to-create-access-keys-with-windows-forms-label-controls"></a><span data-ttu-id="bc8fc-102">Nasıl yapılır: Windows Forms Etiket Denetimleri ile Erişim Tuşları Oluşturma</span><span class="sxs-lookup"><span data-stu-id="bc8fc-102">How to: Create Access Keys with Windows Forms Label Controls</span></span>
<span data-ttu-id="bc8fc-103">Windows Forms <xref:System.Windows.Forms.Label> denetimleri, diğer denetimler için erişim anahtarları tanımlamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="bc8fc-103">Windows Forms <xref:System.Windows.Forms.Label> controls can be used to define access keys for other controls.</span></span> <span data-ttu-id="bc8fc-104">Kullanıcı, bir etiket denetiminde bir erişim anahtarı tanımladığınızda, ALT tuşuyla sekme sırasının takip eden denetim odağı taşımak için belirlediğiniz karakter basabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bc8fc-104">When you define an access key in a label control, the user can press the ALT key plus the character you designate to move the focus to the control that follows it in the tab order.</span></span> <span data-ttu-id="bc8fc-105">Etiketleri odağı alamıyor olduğundan, odak sonraki sekme sırasını denetimde otomatik olarak taşır.</span><span class="sxs-lookup"><span data-stu-id="bc8fc-105">Because labels cannot receive focus, focus automatically moves to the next control in the tab order.</span></span> <span data-ttu-id="bc8fc-106">Metin kutuları, birleşik giriş kutuları, liste kutuları ve veri kılavuzları için erişim anahtarlarını atamak için bu tekniği kullanın.</span><span class="sxs-lookup"><span data-stu-id="bc8fc-106">Use this technique to assign access keys to text boxes, combo boxes, list boxes, and data grids.</span></span>  
  
### <a name="to-assign-an-access-key-to-a-control-with-a-label"></a><span data-ttu-id="bc8fc-107">Bir denetimi bir etikete sahip bir erişim anahtarı atamak için</span><span class="sxs-lookup"><span data-stu-id="bc8fc-107">To assign an access key to a control with a label</span></span>  
  
1.  <span data-ttu-id="bc8fc-108">Etiket çizebilir ve diğer denetimi çizin.</span><span class="sxs-lookup"><span data-stu-id="bc8fc-108">Draw the label first, and then draw the other control.</span></span>  
  
     <span data-ttu-id="bc8fc-109">-veya-</span><span class="sxs-lookup"><span data-stu-id="bc8fc-109">-or-</span></span>  
  
     <span data-ttu-id="bc8fc-110">Herhangi bir sırada denetimlerini çizmek ve ayarlama <xref:System.Windows.Forms.Control.TabIndex%2A> diğer denetim küçük etiketin özelliği.</span><span class="sxs-lookup"><span data-stu-id="bc8fc-110">Draw the controls in any order and set the <xref:System.Windows.Forms.Control.TabIndex%2A> property of the label to one less than the other control.</span></span>  
  
2.  <span data-ttu-id="bc8fc-111">Etiketin <xref:System.Windows.Forms.Label.UseMnemonic%2A> özelliğini `true`.</span><span class="sxs-lookup"><span data-stu-id="bc8fc-111">Set the label's <xref:System.Windows.Forms.Label.UseMnemonic%2A> property to `true`.</span></span>  
  
3.  <span data-ttu-id="bc8fc-112">Ve işareti kullanın (&) etiketin <xref:System.Windows.Forms.Label.Text%2A> etiket için erişim tuşu atama özelliği.</span><span class="sxs-lookup"><span data-stu-id="bc8fc-112">Use an ampersand (&) in the label's <xref:System.Windows.Forms.Label.Text%2A> property to assign the access key for the label.</span></span> <span data-ttu-id="bc8fc-113">Daha fazla bilgi için [oluşturma erişim anahtarları için Windows Forms denetimleri](how-to-create-access-keys-for-windows-forms-controls.md).</span><span class="sxs-lookup"><span data-stu-id="bc8fc-113">For more information, see [Creating Access Keys for Windows Forms Controls](how-to-create-access-keys-for-windows-forms-controls.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="bc8fc-114">Yerine bir etiket denetiminde kodlarına görüntülemek erişim anahtarları oluşturmak için bunları kullanmayı isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bc8fc-114">You may want to display ampersands in a label control, rather than use them to create access keys.</span></span> <span data-ttu-id="bc8fc-115">Burada kodlarına verileri içeren bir kayıt alana bir etiket denetimi bağlarsanız bu durum oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="bc8fc-115">This may occur if you bind a label control to a field in a recordset where the data includes ampersands.</span></span> <span data-ttu-id="bc8fc-116">Kodlarına bir etiket denetiminde görüntülenecek kümesi <xref:System.Windows.Forms.Label.UseMnemonic%2A> özelliğini `false`.</span><span class="sxs-lookup"><span data-stu-id="bc8fc-116">To display ampersands in a label control, set the <xref:System.Windows.Forms.Label.UseMnemonic%2A> property to `false`.</span></span> <span data-ttu-id="bc8fc-117">İşaretlerini görüntüleme ve ayrıca bir erişim anahtarı isterseniz <xref:System.Windows.Forms.Label.UseMnemonic%2A> özelliğini `true` ve bir ampersan ile erişim anahtarını belirtin (&) ve ve işareti ile iki kodlarına görüntülenecek.</span><span class="sxs-lookup"><span data-stu-id="bc8fc-117">If you wish to display ampersands and also have an access key, set the <xref:System.Windows.Forms.Label.UseMnemonic%2A> property to `true` and indicate the access key with one ampersand (&) and the ampersand to display with two ampersands.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="bc8fc-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bc8fc-118">See also</span></span>

- [<span data-ttu-id="bc8fc-119">Nasıl yapılır: Windows Forms Etiket Denetimini İçeriğini Sığdıracak Şekilde Boyutlandırma</span><span class="sxs-lookup"><span data-stu-id="bc8fc-119">How to: Size a Windows Forms Label Control to Fit Its Contents</span></span>](how-to-size-a-windows-forms-label-control-to-fit-its-contents.md)
- [<span data-ttu-id="bc8fc-120">Etiket Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="bc8fc-120">Label Control Overview</span></span>](label-control-overview-windows-forms.md)
- [<span data-ttu-id="bc8fc-121">Etiket Denetimi</span><span class="sxs-lookup"><span data-stu-id="bc8fc-121">Label Control</span></span>](label-control-windows-forms.md)
