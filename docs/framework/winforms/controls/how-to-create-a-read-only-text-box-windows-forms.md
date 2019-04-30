---
title: 'Nasıl yapılır: Salt okunur metin kutusu (Windows Forms) oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- TextBox control [Windows Forms], read-only
- read-only text boxes
- text boxes [Windows Forms], read-only
ms.assetid: 60baa9ab-fa57-44ad-bb7c-61b05aa64296
ms.openlocfilehash: 72dc188993474ad4b39f0cfa74cadffdb99ff46f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61746897"
---
# <a name="how-to-create-a-read-only-text-box-windows-forms"></a><span data-ttu-id="4fccd-102">Nasıl yapılır: Salt okunur metin kutusu (Windows Forms) oluşturma</span><span class="sxs-lookup"><span data-stu-id="4fccd-102">How to: Create a Read-Only Text Box (Windows Forms)</span></span>
<span data-ttu-id="4fccd-103">Düzenlenebilir bir Windows Forms metin kutusunda salt okunur denetimine dönüştürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4fccd-103">You can transform an editable Windows Forms text box into a read-only control.</span></span> <span data-ttu-id="4fccd-104">Örneğin, metin kutusuna bir değer genellikle düzenlenebilir ancak şu anda uygulamanın durumu nedeniyle olmayabilir görüntüleyebilir.</span><span class="sxs-lookup"><span data-stu-id="4fccd-104">For example, the text box may display a value that is usually edited but may not be currently, due to the state of the application.</span></span>  
  
### <a name="to-create-a-read-only-text-box"></a><span data-ttu-id="4fccd-105">Bir salt okunur metin kutusu oluşturma</span><span class="sxs-lookup"><span data-stu-id="4fccd-105">To create a read-only text box</span></span>  
  
1. <span data-ttu-id="4fccd-106">Ayarlama <xref:System.Windows.Forms.TextBox> denetimin <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> özelliğini `true`.</span><span class="sxs-lookup"><span data-stu-id="4fccd-106">Set the <xref:System.Windows.Forms.TextBox> control's <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> property to `true`.</span></span> <span data-ttu-id="4fccd-107">Ayarlanan özelliği ile `true`, kullanıcılar hala kaydırın ve metin kutusundaki değişiklikler vermeden vurgulayın.</span><span class="sxs-lookup"><span data-stu-id="4fccd-107">With the property set to `true`, users can still scroll and highlight text in a text box without allowing changes.</span></span> <span data-ttu-id="4fccd-108">A **kopyalama** komut işlevsel bir metin kutusunda, ancak **Kes** ve **Yapıştır** komutları değildir.</span><span class="sxs-lookup"><span data-stu-id="4fccd-108">A **Copy** command is functional in a text box, but **Cut** and **Paste** commands are not.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4fccd-109"><xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> Özelliği yalnızca çalışma zamanında kullanıcı etkileşimi etkiler.</span><span class="sxs-lookup"><span data-stu-id="4fccd-109">The <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> property only affects user interaction at run time.</span></span> <span data-ttu-id="4fccd-110">Yine de metin kutusu içeriklerinin program aracılığıyla çalışma zamanında değiştirerek değiştirebilirsiniz <xref:System.Windows.Forms.TextBox.Text%2A> metin kutusunun özelliği.</span><span class="sxs-lookup"><span data-stu-id="4fccd-110">You can still change text box contents programmatically at run time by changing the <xref:System.Windows.Forms.TextBox.Text%2A> property of the text box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4fccd-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4fccd-111">See also</span></span>

- <xref:System.Windows.Forms.TextBox>
- [<span data-ttu-id="4fccd-112">TextBox Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="4fccd-112">TextBox Control Overview</span></span>](textbox-control-overview-windows-forms.md)
- [<span data-ttu-id="4fccd-113">Nasıl yapılır: Windows Forms TextBox denetiminde ekleme noktasını belirleme</span><span class="sxs-lookup"><span data-stu-id="4fccd-113">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [<span data-ttu-id="4fccd-114">Nasıl yapılır: Windows Forms TextBox denetimi ile parola metin kutusu oluşturma</span><span class="sxs-lookup"><span data-stu-id="4fccd-114">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="4fccd-115">Nasıl yapılır: Dizeye tırnak işaretleri koyma</span><span class="sxs-lookup"><span data-stu-id="4fccd-115">How to: Put Quotation Marks in a String</span></span>](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [<span data-ttu-id="4fccd-116">Nasıl yapılır: Windows Forms TextBox denetiminde metni Seç</span><span class="sxs-lookup"><span data-stu-id="4fccd-116">How to: Select Text in the Windows Forms TextBox Control</span></span>](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="4fccd-117">Nasıl yapılır: Windows Forms TextBox denetiminde birden çok satır görüntüleme</span><span class="sxs-lookup"><span data-stu-id="4fccd-117">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="4fccd-118">TextBox Denetimi</span><span class="sxs-lookup"><span data-stu-id="4fccd-118">TextBox Control</span></span>](textbox-control-windows-forms.md)
