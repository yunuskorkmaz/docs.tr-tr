---
title: "Nasıl yapılır: Windows Formları GroupBox Denetimiyle Denetimleri Gruplandırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [Windows Forms], grouping
- GroupBox control [Windows Forms], grouping controls
- Windows Forms controls, grouping
ms.assetid: 0bda316d-bd2a-43aa-ac73-342453303169
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7ecdb7b8682b13f93f59d1de21552abfa91b8f50
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-group-controls-with-the-windows-forms-groupbox-control"></a><span data-ttu-id="899a2-102">Nasıl yapılır: Windows Formları GroupBox Denetimiyle Denetimleri Gruplandırma</span><span class="sxs-lookup"><span data-stu-id="899a2-102">How to: Group Controls with the Windows Forms GroupBox Control</span></span>
<span data-ttu-id="899a2-103">Windows Forms <xref:System.Windows.Forms.GroupBox> denetimleri, diğer denetimler gruplandırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="899a2-103">Windows Forms <xref:System.Windows.Forms.GroupBox> controls are used to group other controls.</span></span> <span data-ttu-id="899a2-104">Denetimleri gruplandırma için üç nedeni vardır:</span><span class="sxs-lookup"><span data-stu-id="899a2-104">There are three reasons to group controls:</span></span>  
  
-   <span data-ttu-id="899a2-105">Görsel Temizle kullanıcı arabirimi için ilgili form öğeleri gruplandırması oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="899a2-105">To create a visual grouping of related form elements for a clear user interface.</span></span>  
  
-   <span data-ttu-id="899a2-106">Programsal gruplandırması (örneğin radyo düğmeleri) oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="899a2-106">To create programmatic grouping (of radio buttons, for example).</span></span>  
  
-   <span data-ttu-id="899a2-107">Denetimlerin bir birim olarak tasarım zamanında taşımak için.</span><span class="sxs-lookup"><span data-stu-id="899a2-107">For moving the controls as a unit at design time.</span></span>  
  
### <a name="to-create-a-group-of-controls"></a><span data-ttu-id="899a2-108">Denetimlerin bir grup oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="899a2-108">To create a group of controls</span></span>  
  
1.  <span data-ttu-id="899a2-109">Çizim bir <xref:System.Windows.Forms.GroupBox> bir form üzerinde denetim.</span><span class="sxs-lookup"><span data-stu-id="899a2-109">Draw a <xref:System.Windows.Forms.GroupBox> control on a form.</span></span>  
  
2.  <span data-ttu-id="899a2-110">Her grup kutusu içinde çizim grup kutusu, diğer denetimler ekleyin.</span><span class="sxs-lookup"><span data-stu-id="899a2-110">Add other controls to the group box, drawing each inside the group box.</span></span>  
  
     <span data-ttu-id="899a2-111">Bir grup kutusunda eklemek istediğiniz varolan denetimleri varsa, tüm denetimler seçin, select panoya Kes <xref:System.Windows.Forms.GroupBox> denetleyen ve bunları grup kutusuna yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="899a2-111">If you have existing controls that you want to enclose in a group box, you can select all the controls, cut them to the Clipboard, select the <xref:System.Windows.Forms.GroupBox> control, and then paste them into the group box.</span></span> <span data-ttu-id="899a2-112">Ayrıca bunları grup kutusuna sürükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="899a2-112">You can also drag them into the group box.</span></span>  
  
3.  <span data-ttu-id="899a2-113">Ayarlama <xref:System.Windows.Forms.GroupBox.Text%2A> uygun bir resim yazısı için Grup kutusu özelliği.</span><span class="sxs-lookup"><span data-stu-id="899a2-113">Set the <xref:System.Windows.Forms.GroupBox.Text%2A> property of the group box to an appropriate caption.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="899a2-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="899a2-114">See Also</span></span>  
 <xref:System.Windows.Forms.GroupBox>  
 [<span data-ttu-id="899a2-115">GroupBox Denetimi</span><span class="sxs-lookup"><span data-stu-id="899a2-115">GroupBox Control</span></span>](../../../../docs/framework/winforms/controls/groupbox-control-windows-forms.md)
