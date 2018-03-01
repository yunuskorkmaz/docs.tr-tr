---
title: "CheckBox Denetimine Genel Bakış (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CheckBox
helpviewer_keywords:
- CheckBox control [Windows Forms], about CheckBox control
- data binding [Windows Forms], checkbox controls
- check boxes [Windows Forms], about check boxes
ms.assetid: 085a4e0b-9046-473f-b141-d0edddfb2ebb
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 39645a02cd66d37d61df72028ab129677edb757e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="checkbox-control-overview-windows-forms"></a><span data-ttu-id="1dad7-102">CheckBox Denetimine Genel Bakış (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="1dad7-102">CheckBox Control Overview (Windows Forms)</span></span>
<span data-ttu-id="1dad7-103">Windows Forms <xref:System.Windows.Forms.CheckBox> denetimi, belirli bir koşula açık veya kapalı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="1dad7-103">The Windows Forms <xref:System.Windows.Forms.CheckBox> control indicates whether a particular condition is on or off.</span></span> <span data-ttu-id="1dad7-104">Evet sunmak için yaygın olarak kullanılan/yok veya kullanıcının True/False seçimi.</span><span class="sxs-lookup"><span data-stu-id="1dad7-104">It is commonly used to present a Yes/No or True/False selection to the user.</span></span> <span data-ttu-id="1dad7-105">Kullanıcı bir veya daha fazla seçebileceği birden çok seçenek göstermek için gruplarında onay kutusu denetimleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1dad7-105">You can use check box controls in groups to display multiple choices from which the user can select one or more.</span></span>  
  
 <span data-ttu-id="1dad7-106">Her kullanıcı tarafından yapılan bir seçim göstermek için kullanılan onay kutusu denetimi için radyo düğmesi denetimini benzer.</span><span class="sxs-lookup"><span data-stu-id="1dad7-106">The check box control is similar to the radio button control in that each is used to indicate a selection that is made by the user.</span></span> <span data-ttu-id="1dad7-107">Bunlar, aynı anda yalnızca bir radyo düğmesi grubundaki seçilebilir farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="1dad7-107">They differ in that only one radio button in a group can be selected at a time.</span></span> <span data-ttu-id="1dad7-108">Onay kutusu denetimi ile ancak herhangi bir sayıda onay kutularını seçilmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="1dad7-108">With the check box control, however, any number of check boxes may be selected.</span></span>  
  
 <span data-ttu-id="1dad7-109">Bir onay kutusu, basit veri bağlama kullanarak bir veritabanındaki öğelere bağlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="1dad7-109">A check box may be connected to elements in a database using simple data binding.</span></span> <span data-ttu-id="1dad7-110">Birden çok onay kutularını kullanarak gruplandırılabilir <xref:System.Windows.Forms.GroupBox> denetim.</span><span class="sxs-lookup"><span data-stu-id="1dad7-110">Multiple check boxes may be grouped using the <xref:System.Windows.Forms.GroupBox> control.</span></span> <span data-ttu-id="1dad7-111">Gruplandırılmış denetimleri form Tasarımcısı üzerinde birlikte taşınabildiğinden beri bu görsel görünümünü ve ayrıca kullanıcı arabirimi tasarımı için kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="1dad7-111">This is useful for visual appearance and also for user interface design, since grouped controls can be moved around together on the form designer.</span></span> <span data-ttu-id="1dad7-112">Daha fazla bilgi için bkz: [Windows Forms veri bağlama](../../../../docs/framework/winforms/windows-forms-data-binding.md) ve [GroupBox denetimi](../../../../docs/framework/winforms/controls/groupbox-control-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="1dad7-112">For more information, see [Windows Forms Data Binding](../../../../docs/framework/winforms/windows-forms-data-binding.md) and [GroupBox Control](../../../../docs/framework/winforms/controls/groupbox-control-windows-forms.md).</span></span>  
  
 <span data-ttu-id="1dad7-113"><xref:System.Windows.Forms.CheckBox> Denetimi sahip iki önemli özellikleri <xref:System.Windows.Forms.CheckBox.Checked%2A> ve <xref:System.Windows.Forms.CheckBox.CheckState%2A>.</span><span class="sxs-lookup"><span data-stu-id="1dad7-113">The <xref:System.Windows.Forms.CheckBox> control has two important properties, <xref:System.Windows.Forms.CheckBox.Checked%2A> and <xref:System.Windows.Forms.CheckBox.CheckState%2A>.</span></span> <span data-ttu-id="1dad7-114"><xref:System.Windows.Forms.CheckBox.Checked%2A> Özelliği döndürür ya da `true` veya `false`.</span><span class="sxs-lookup"><span data-stu-id="1dad7-114">The <xref:System.Windows.Forms.CheckBox.Checked%2A> property returns either `true` or `false`.</span></span> <span data-ttu-id="1dad7-115"><xref:System.Windows.Forms.CheckBox.CheckState%2A> Özelliği döndürür ya da <xref:System.Windows.Forms.CheckState.Checked> veya <xref:System.Windows.Forms.CheckState.Unchecked>; veya <xref:System.Windows.Forms.CheckBox.ThreeState%2A> özelliği ayarlanmış `true`, <xref:System.Windows.Forms.CheckBox.CheckState%2A> de döndürebilir <xref:System.Windows.Forms.CheckState.Indeterminate>.</span><span class="sxs-lookup"><span data-stu-id="1dad7-115">The <xref:System.Windows.Forms.CheckBox.CheckState%2A> property returns either <xref:System.Windows.Forms.CheckState.Checked> or <xref:System.Windows.Forms.CheckState.Unchecked>; or, if the <xref:System.Windows.Forms.CheckBox.ThreeState%2A> property is set to `true`, <xref:System.Windows.Forms.CheckBox.CheckState%2A> may also return <xref:System.Windows.Forms.CheckState.Indeterminate>.</span></span> <span data-ttu-id="1dad7-116">Belirsiz durumda kutusu seçeneği kullanılamaz belirtmek için devre dışı bir görünümü görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="1dad7-116">In the indeterminate state, the box is displayed with a dimmed appearance to indicate the option is unavailable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1dad7-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1dad7-117">See Also</span></span>  
 <xref:System.Windows.Forms.CheckBox>  
 [<span data-ttu-id="1dad7-118">Nasıl yapılır: Windows Forms CheckBox Denetimleriyle Seçenekleri Ayarlama</span><span class="sxs-lookup"><span data-stu-id="1dad7-118">How to: Set Options with Windows Forms CheckBox Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-set-options-with-windows-forms-checkbox-controls.md)  
 [<span data-ttu-id="1dad7-119">Nasıl yapılır: Windows Forms CheckBox Tıklamalarına Yanıt Verme</span><span class="sxs-lookup"><span data-stu-id="1dad7-119">How to: Respond to Windows Forms CheckBox Clicks</span></span>](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-checkbox-clicks.md)  
 [<span data-ttu-id="1dad7-120">CheckBox Denetimi</span><span class="sxs-lookup"><span data-stu-id="1dad7-120">CheckBox Control</span></span>](../../../../docs/framework/winforms/controls/checkbox-control-windows-forms.md)
