---
title: 'Nasıl yapılır: Salt Okunur Metin Kutusu Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- TextBox control [Windows Forms], read-only
- read-only text boxes
- text boxes [Windows Forms], read-only
ms.assetid: 60baa9ab-fa57-44ad-bb7c-61b05aa64296
ms.openlocfilehash: 17ae9524009c687cd62fb315f842e188e120ac68
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76731278"
---
# <a name="how-to-create-a-read-only-text-box-windows-forms"></a><span data-ttu-id="f0efe-102">Nasıl yapılır: Salt Okunur Metin Kutusu Oluşturma (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="f0efe-102">How to: Create a Read-Only Text Box (Windows Forms)</span></span>

<span data-ttu-id="f0efe-103">Düzenlenebilir bir Windows Forms metin kutusunu salt bir denetimin içine dönüştürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f0efe-103">You can transform an editable Windows Forms text box into a read-only control.</span></span> <span data-ttu-id="f0efe-104">Örneğin, metin kutusu genellikle düzenlenmiş bir değer görüntüleyebilir, ancak şu anda uygulamanın durumu nedeniyle olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="f0efe-104">For example, the text box may display a value that is usually edited but may not be currently, due to the state of the application.</span></span>

## <a name="to-create-a-read-only-text-box"></a><span data-ttu-id="f0efe-105">Salt okunurdur metin kutusu oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="f0efe-105">To create a read-only text box</span></span>

1. <span data-ttu-id="f0efe-106"><xref:System.Windows.Forms.TextBox> denetiminin <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> özelliğini `true`olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="f0efe-106">Set the <xref:System.Windows.Forms.TextBox> control's <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> property to `true`.</span></span> <span data-ttu-id="f0efe-107">Özelliği `true`olarak ayarlandığında, kullanıcılar değişikliklere izin vermeden metin kutusunda metin kaydırma ve vurgulamaya devam edebilir.</span><span class="sxs-lookup"><span data-stu-id="f0efe-107">With the property set to `true`, users can still scroll and highlight text in a text box without allowing changes.</span></span> <span data-ttu-id="f0efe-108">Bir **kopyalama** komutu metin kutusunda çalışır, ancak **Kes** ve **Yapıştır** komutları değildir.</span><span class="sxs-lookup"><span data-stu-id="f0efe-108">A **Copy** command is functional in a text box, but **Cut** and **Paste** commands are not.</span></span>

    > [!NOTE]
    > <span data-ttu-id="f0efe-109"><xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> özelliği yalnızca çalışma zamanında kullanıcı etkileşimini etkiler.</span><span class="sxs-lookup"><span data-stu-id="f0efe-109">The <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> property only affects user interaction at run time.</span></span> <span data-ttu-id="f0efe-110">Metin kutusunun <xref:System.Windows.Forms.TextBox.Text%2A> özelliğini değiştirerek metin kutusu içeriğini çalışma zamanında programlı bir şekilde değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f0efe-110">You can still change text box contents programmatically at run time by changing the <xref:System.Windows.Forms.TextBox.Text%2A> property of the text box.</span></span>

## <a name="see-also"></a><span data-ttu-id="f0efe-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f0efe-111">See also</span></span>

- <xref:System.Windows.Forms.TextBox>
- [<span data-ttu-id="f0efe-112">TextBox Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="f0efe-112">TextBox Control Overview</span></span>](textbox-control-overview-windows-forms.md)
- [<span data-ttu-id="f0efe-113">Nasıl yapılır: Windows Forms TextBox Denetiminde Ekleme Noktasını Belirleme</span><span class="sxs-lookup"><span data-stu-id="f0efe-113">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [<span data-ttu-id="f0efe-114">Nasıl yapılır: Windows Forms TextBox Denetimi ile Parola Metin Kutusu Oluşturma</span><span class="sxs-lookup"><span data-stu-id="f0efe-114">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="f0efe-115">Nasıl yapılır: Dizeye Tırnak İşaretleri Koyma</span><span class="sxs-lookup"><span data-stu-id="f0efe-115">How to: Put Quotation Marks in a String</span></span>](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [<span data-ttu-id="f0efe-116">Nasıl yapılır: Windows Forms TextBox Denetiminde Metni Seçme</span><span class="sxs-lookup"><span data-stu-id="f0efe-116">How to: Select Text in the Windows Forms TextBox Control</span></span>](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="f0efe-117">Nasıl yapılır: Windows Forms TextBox Denetiminde Birden Fazla Çizgiyi Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="f0efe-117">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="f0efe-118">TextBox Denetimi</span><span class="sxs-lookup"><span data-stu-id="f0efe-118">TextBox Control</span></span>](textbox-control-windows-forms.md)
