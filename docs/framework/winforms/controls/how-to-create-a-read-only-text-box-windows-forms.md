---
title: "Nasıl yapılır: Salt Okunur Metin Kutusu Oluşturma (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- TextBox control [Windows Forms], read-only
- read-only text boxes
- text boxes [Windows Forms], read-only
ms.assetid: 60baa9ab-fa57-44ad-bb7c-61b05aa64296
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9cf6064442c3b648116f98f98f169dac12e5e88c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-read-only-text-box-windows-forms"></a><span data-ttu-id="7ec1d-102">Nasıl yapılır: Salt Okunur Metin Kutusu Oluşturma (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="7ec1d-102">How to: Create a Read-Only Text Box (Windows Forms)</span></span>
<span data-ttu-id="7ec1d-103">Düzenlenebilir bir Windows Forms metin kutusunda salt okunur denetime dönüştürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7ec1d-103">You can transform an editable Windows Forms text box into a read-only control.</span></span> <span data-ttu-id="7ec1d-104">Örneğin, metin kutusunun genellikle düzenlenebilir ancak uygulama durumu nedeniyle şu anda olmayabilir bir değer görüntüleyebilir.</span><span class="sxs-lookup"><span data-stu-id="7ec1d-104">For example, the text box may display a value that is usually edited but may not be currently, due to the state of the application.</span></span>  
  
### <a name="to-create-a-read-only-text-box"></a><span data-ttu-id="7ec1d-105">Salt okunur metin kutusu oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="7ec1d-105">To create a read-only text box</span></span>  
  
1.  <span data-ttu-id="7ec1d-106">Ayarlama <xref:System.Windows.Forms.TextBox> denetimin <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> özelliğine `true`.</span><span class="sxs-lookup"><span data-stu-id="7ec1d-106">Set the <xref:System.Windows.Forms.TextBox> control's <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> property to `true`.</span></span> <span data-ttu-id="7ec1d-107">Ayarlanan özelliği ile `true`, kullanıcılar, hala kaydırın ve bir metin kutusundaki değişiklikler vermeden vurgulayın.</span><span class="sxs-lookup"><span data-stu-id="7ec1d-107">With the property set to `true`, users can still scroll and highlight text in a text box without allowing changes.</span></span> <span data-ttu-id="7ec1d-108">A **kopya** komuttur işlevsel bir metin kutusunda, ancak **Kes** ve **Yapıştır** komutları değildir.</span><span class="sxs-lookup"><span data-stu-id="7ec1d-108">A **Copy** command is functional in a text box, but **Cut** and **Paste** commands are not.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="7ec1d-109"><xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> Özelliği yalnızca çalışma zamanında kullanıcı etkileşimi etkiler.</span><span class="sxs-lookup"><span data-stu-id="7ec1d-109">The <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> property only affects user interaction at run time.</span></span> <span data-ttu-id="7ec1d-110">Hala metin kutusu içeriğinin program aracılığıyla çalışma zamanında değiştirerek değiştirebilirsiniz <xref:System.Windows.Forms.TextBox.Text%2A> metin kutusunun özelliği.</span><span class="sxs-lookup"><span data-stu-id="7ec1d-110">You can still change text box contents programmatically at run time by changing the <xref:System.Windows.Forms.TextBox.Text%2A> property of the text box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ec1d-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7ec1d-111">See Also</span></span>  
 <xref:System.Windows.Forms.TextBox>  
 [<span data-ttu-id="7ec1d-112">TextBox denetimine genel bakış</span><span class="sxs-lookup"><span data-stu-id="7ec1d-112">TextBox Control Overview</span></span>](../../../../docs/framework/winforms/controls/textbox-control-overview-windows-forms.md)  
 [<span data-ttu-id="7ec1d-113">Nasıl yapılır: Windows Forms TextBox denetiminde ekleme noktasını denetleme</span><span class="sxs-lookup"><span data-stu-id="7ec1d-113">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)  
 [<span data-ttu-id="7ec1d-114">Nasıl yapılır: Windows Forms TextBox denetimi ile parola metin kutusu oluşturma</span><span class="sxs-lookup"><span data-stu-id="7ec1d-114">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)  
 [<span data-ttu-id="7ec1d-115">Nasıl yapılır: dizeye tırnak işaretleri koyma</span><span class="sxs-lookup"><span data-stu-id="7ec1d-115">How to: Put Quotation Marks in a String</span></span>](../../../../docs/framework/winforms/controls/how-to-put-quotation-marks-in-a-string-windows-forms.md)  
 [<span data-ttu-id="7ec1d-116">Nasıl yapılır: metni seçme Windows Forms TextBox denetiminde</span><span class="sxs-lookup"><span data-stu-id="7ec1d-116">How to: Select Text in the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-select-text-in-the-windows-forms-textbox-control.md)  
 [<span data-ttu-id="7ec1d-117">Nasıl yapılır: birden çok satır Windows Forms TextBox denetiminde görünümü</span><span class="sxs-lookup"><span data-stu-id="7ec1d-117">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)  
 [<span data-ttu-id="7ec1d-118">TextBox denetimi</span><span class="sxs-lookup"><span data-stu-id="7ec1d-118">TextBox Control</span></span>](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)
