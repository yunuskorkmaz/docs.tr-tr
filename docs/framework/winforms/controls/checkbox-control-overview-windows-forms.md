---
title: "CheckBox Denetimine Genel Bakış (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CheckBox
helpviewer_keywords:
- CheckBox control [Windows Forms], about CheckBox control
- data binding [Windows Forms], checkbox controls
- check boxes [Windows Forms], about check boxes
ms.assetid: 085a4e0b-9046-473f-b141-d0edddfb2ebb
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a154a3f639102e3f3e2acd62626379e12bbd1344
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="checkbox-control-overview-windows-forms"></a><span data-ttu-id="131ec-102">CheckBox Denetimine Genel Bakış (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="131ec-102">CheckBox Control Overview (Windows Forms)</span></span>
<span data-ttu-id="131ec-103">Windows Forms <xref:System.Windows.Forms.CheckBox> denetimi, belirli bir koşula açık veya kapalı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="131ec-103">The Windows Forms <xref:System.Windows.Forms.CheckBox> control indicates whether a particular condition is on or off.</span></span> <span data-ttu-id="131ec-104">Evet sunmak için yaygın olarak kullanılan/yok veya kullanıcının True/False seçimi.</span><span class="sxs-lookup"><span data-stu-id="131ec-104">It is commonly used to present a Yes/No or True/False selection to the user.</span></span> <span data-ttu-id="131ec-105">Kullanıcı bir veya daha fazla seçebileceği birden çok seçenek göstermek için gruplarında onay kutusu denetimleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="131ec-105">You can use check box controls in groups to display multiple choices from which the user can select one or more.</span></span>  
  
 <span data-ttu-id="131ec-106">Her kullanıcı tarafından yapılan bir seçim göstermek için kullanılan onay kutusu denetimi için radyo düğmesi denetimini benzer.</span><span class="sxs-lookup"><span data-stu-id="131ec-106">The check box control is similar to the radio button control in that each is used to indicate a selection that is made by the user.</span></span> <span data-ttu-id="131ec-107">Bunlar, aynı anda yalnızca bir radyo düğmesi grubundaki seçilebilir farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="131ec-107">They differ in that only one radio button in a group can be selected at a time.</span></span> <span data-ttu-id="131ec-108">Onay kutusu denetimi ile ancak herhangi bir sayıda onay kutularını seçilmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="131ec-108">With the check box control, however, any number of check boxes may be selected.</span></span>  
  
 <span data-ttu-id="131ec-109">Bir onay kutusu, basit veri bağlama kullanarak bir veritabanındaki öğelere bağlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="131ec-109">A check box may be connected to elements in a database using simple data binding.</span></span> <span data-ttu-id="131ec-110">Birden çok onay kutularını kullanarak gruplandırılabilir <xref:System.Windows.Forms.GroupBox> denetim.</span><span class="sxs-lookup"><span data-stu-id="131ec-110">Multiple check boxes may be grouped using the <xref:System.Windows.Forms.GroupBox> control.</span></span> <span data-ttu-id="131ec-111">Gruplandırılmış denetimleri form Tasarımcısı üzerinde birlikte taşınabildiğinden beri bu görsel görünümünü ve ayrıca kullanıcı arabirimi tasarımı için kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="131ec-111">This is useful for visual appearance and also for user interface design, since grouped controls can be moved around together on the form designer.</span></span> <span data-ttu-id="131ec-112">Daha fazla bilgi için bkz: [Windows Forms veri bağlama](../../../../docs/framework/winforms/windows-forms-data-binding.md) ve [GroupBox denetimi](../../../../docs/framework/winforms/controls/groupbox-control-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="131ec-112">For more information, see [Windows Forms Data Binding](../../../../docs/framework/winforms/windows-forms-data-binding.md) and [GroupBox Control](../../../../docs/framework/winforms/controls/groupbox-control-windows-forms.md).</span></span>  
  
 <span data-ttu-id="131ec-113"><xref:System.Windows.Forms.CheckBox> Denetimi sahip iki önemli özellikleri <xref:System.Windows.Forms.CheckBox.Checked%2A> ve <xref:System.Windows.Forms.CheckBox.CheckState%2A>.</span><span class="sxs-lookup"><span data-stu-id="131ec-113">The <xref:System.Windows.Forms.CheckBox> control has two important properties, <xref:System.Windows.Forms.CheckBox.Checked%2A> and <xref:System.Windows.Forms.CheckBox.CheckState%2A>.</span></span> <span data-ttu-id="131ec-114"><xref:System.Windows.Forms.CheckBox.Checked%2A> Özelliği döndürür ya da `true` veya `false`.</span><span class="sxs-lookup"><span data-stu-id="131ec-114">The <xref:System.Windows.Forms.CheckBox.Checked%2A> property returns either `true` or `false`.</span></span> <span data-ttu-id="131ec-115"><xref:System.Windows.Forms.CheckBox.CheckState%2A> Özelliği döndürür ya da <xref:System.Windows.Forms.CheckState.Checked> veya <xref:System.Windows.Forms.CheckState.Unchecked>; veya <xref:System.Windows.Forms.CheckBox.ThreeState%2A> özelliği ayarlanmış `true`, <xref:System.Windows.Forms.CheckBox.CheckState%2A> de döndürebilir <xref:System.Windows.Forms.CheckState.Indeterminate>.</span><span class="sxs-lookup"><span data-stu-id="131ec-115">The <xref:System.Windows.Forms.CheckBox.CheckState%2A> property returns either <xref:System.Windows.Forms.CheckState.Checked> or <xref:System.Windows.Forms.CheckState.Unchecked>; or, if the <xref:System.Windows.Forms.CheckBox.ThreeState%2A> property is set to `true`, <xref:System.Windows.Forms.CheckBox.CheckState%2A> may also return <xref:System.Windows.Forms.CheckState.Indeterminate>.</span></span> <span data-ttu-id="131ec-116">Belirsiz durumda kutusu seçeneği kullanılamaz belirtmek için devre dışı bir görünümü görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="131ec-116">In the indeterminate state, the box is displayed with a dimmed appearance to indicate the option is unavailable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="131ec-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="131ec-117">See Also</span></span>  
 <xref:System.Windows.Forms.CheckBox>  
 [<span data-ttu-id="131ec-118">Nasıl yapılır: seçenekleri ile Windows Forms CheckBox denetimlerini ayarlama</span><span class="sxs-lookup"><span data-stu-id="131ec-118">How to: Set Options with Windows Forms CheckBox Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-set-options-with-windows-forms-checkbox-controls.md)  
 [<span data-ttu-id="131ec-119">Nasıl yapılır: Windows Forms CheckBox tıklamalarına yanıt verme</span><span class="sxs-lookup"><span data-stu-id="131ec-119">How to: Respond to Windows Forms CheckBox Clicks</span></span>](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-checkbox-clicks.md)  
 [<span data-ttu-id="131ec-120">CheckBox denetimi</span><span class="sxs-lookup"><span data-stu-id="131ec-120">CheckBox Control</span></span>](../../../../docs/framework/winforms/controls/checkbox-control-windows-forms.md)
